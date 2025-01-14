# DBT for DOT:

## Directory Structure

The [DBT folder](dot/dbt) contains DBT models, macros, custom tests, and project files. While most of these files are generated by DOT from the configured entities and tests in the dot schema, it's important to note that any DBT command requires the actual files as inputs.

**Core Subdirectories:**

- **macros**: Contains Jinja macros to support organized code and custom schema tests.
- **models**: The core of the DBT project, this directory includes both SQL files for models and YAML files for schema tests. These files are generated by DOT from `dot.configured_entities` for the SQL models and from `dot.configured_tests` for the test YAML files.
- **tests**: Custom SQL tests, generated by DOT from `dot.configured_tests`, for tests of the "custom_sql" type.

**Non-version-controlled Directories (created during DBT runs):**

- **target**: Compiled SQL used to create models and tests.
- **dbt_modules**: DBT plugins (e.g., `dbt_utils`) installed via `dbt deps`.
- **logs**: Logs created by DBT (not used elsewhere in this stack).

**Scripts:**

- **[__dbt.py](dot/utils/dbt.py)**: Utilities that manage the execution of DBT jobs, generate views containing rows flagged by failing tests, create test coverage reports for the DBT side of the stack, and update test results in the DB.

**Config Files:**

- **dbt_project.yml**: Defines paths to important DBT assets (including those listed above) and project-specific variables. This file is not under version control, as it is either generated by the tool or copied from the project-specific configuration.
- **packages.yml**: Specifies the DBT plugins used.

---

### Running Tests on DBT

The following commands are used by the tool to run tests:

- **Run all tests**: `dbt test -m core`
- **Run all tests for patients only**: `dbt test -m patient`
- **Run schema tests for patients only**: `dbt test --schema -m patient`
- **Run data tests for patients only**: `dbt test --data -m patient`

---

### Updating Models

The models in the core folder are a direct dump of the DB `dot.configured_entities`. Currently, most of the entities are full-table copies of the raw data.

**Reference Command:**

- **Update all models**: `dbt run -m core`

---

### Writing New Tests

As the number of tests increases, it’s important to keep them organized. Wherever possible, schema tests should be implemented using simple test types in `dot.configured_tests` (such as `not_null`, `unique`, `relationships`, `accepted_values`, etc.), as this minimizes the need for additional SQL. The [dbt_utils extension](https://github.com/fishtown-analytics/dbt-utils), already set up in this project, can be useful for writing more complex versions of these tests.

For tests requiring custom SQL, a new `custom_sql` row should be added to `dot.configured_tests`, which will then generate a file in the `tests/core` directory.

---

### Making Sense of Failed Test Results

The DOT performs several steps to generate test results:

1. It runs `dbt test` to execute the tests.
2. It autogenerates model code only for the tests that have failed. These models will produce views when run.
3. The end result is a new set of data sources (prefixed with "tr_") containing all rows that violate a test.
4. These failing rows are also loaded into the `dot.test_results` table.

You can use `run_everything.sh` as a quick way to run the necessary DBT commands in sequence, ensuring that all dependencies and assumptions are in place.

Note that the code generated for these models is git-ignored because it is based on compiled SQL and contains specific database names rather than DBT references.

---

### Native DBT Documentation

DBT supports auto-generated documentation, but these docs are relatively limited for this project, especially since they do not provide a way to identify the specific records causing test failures. Therefore, custom code has been written to generate a report that better addresses the Community Health DOT use case.

If you want to explore the native DBT docs, they can be generated using the command:

- `dbt docs generate`

To view them, run:

- `dbt docs serve`

This will start a local web server, allowing you to explore the documentation in your browser.

---

### Boilerplate Resources

The following resources were automatically generated by `dbt init` and are helpful for learning more about DBT:

- [Learn more about DBT in the docs](https://docs.getdbt.com/docs/introduction/) – Official documentation to get started with DBT.
- [Check out Discourse](https://discourse.getdbt.com/) – A community forum for commonly asked questions and answers.
- [Join the chat on Slack](http://slack.getdbt.com/) – Engage in live discussions and get support.
- [Find DBT events near you](https://events.getdbt.com) – Discover upcoming DBT events and meetups.
- [The DBT blog](https://blog.getdbt.com/) – Stay updated with the latest news and best practices from the DBT community.

---

### Great Expectations

#### Directory Structure

The [great_expectations](dot/great_expectations) folder (located at `dot/great_expectations`) is a [Great Expectations](https://greatexpectations.io/) project. It contains several important subdirectories and files, as described below.

**Core Directories:**

- **expectations**: Contains JSON files that define the tests to be run. These are similar to the YAML files used for schema tests in DBT. These files are not stored in version control and are instead generated by the tool from `dot.configured_tests`.
- **notebooks**: Jupyter notebooks automatically created by Great Expectations during setup. These provide a convenient front-end interface for editing the JSON files in the expectations folder. For more details, refer to the Great Expectations documentation on using notebooks.
- **plugins**: Contains additional code for customizing the Great Expectations project. The most important file here is `custom_expectations.py`, where tests requiring custom Python code are added as methods under the `CustomSqlAlchemyDataset` class. This is similar to the custom SQL tests in DBT but written in Python.

**Non-version-Controlled Directories (Automatically Created by Great Expectations):**

- **uncommitted**: A directory used to store files that should not be version-controlled, such as logs and database connection details.

#### Utility Scripts and Config Files:

- **__great_expectations.py**: A utility script to automatically run Great Expectations tests and generate coverage reports. Great Expectations' CLI commands are more verbose and harder to remember compared to DBT's.

**Config Files (not version-controlled):**

- **batch_config.json**: Defines datasources, test suites, and tables to include when running Great Expectations.
- **great_expectations.yml**: The main configuration file for Great Expectations, similar to `dbt_project.yml` in DBT.

---

### Terminology

- **Expectation**: A function that accepts one or more parameters, defined in Python.
- **Test**: An instance of an expectation with a specific set of parameters, defined in a JSON file.
- **Out-Of-The-Box (OOTB) Expectations**: Built-in expectations provided by the Great Expectations library.

---

### Structuring Tests

Tests in Great Expectations are defined in JSON files, similar to how DBT schema tests are defined in YAML. These JSON files live in the `great_expectations/expectations/<FILE>.json` directory. While OOTB tests can be used directly, custom tests are often necessary.

#### Custom vs OOTB Expectations:

**OOTB Expectations:**
- Can operate only on tables specified in the `batch_config.json` file (additional configuration may be needed).
- Can be used in conjunction with views defined in DBT.
- Can be defined directly in the JSON file.

**Custom Expectations:**
- Can operate on any tables passed as a parameter, not limited to the tables in `batch_config.json`.
- Are added as decorated methods in `plugins/custom_expectations.py`.
- Can run arbitrary Python/Pandas code, even though this feature is not well-documented in the official Great Expectations docs.
- Once added to `custom_expectations.py`, custom tests are defined in the same way as OOTB tests, via JSON files.

---

### Notes on Output Format

OOTB expectations have various outputs that might not conform to the format expected by your Data Integrity framework. Whenever possible, it is recommended to use DBT tests instead.

### Managing Mixed Expectations

If you need to use a combination of OOTB and custom expectations, it is suggested to keep them in two separate suites for easier management and to avoid potential conflicts.



_For further reference on advanced topics related to DOT, you can consult the [Advanced Topics](https://github.com/wvelebanks/Data-Observation-Toolkit/blob/cb6796d15e46c209e8d08b0d3984bfb6cb9d262d/documentation_DOT/AdavanceTopics.md#adding-more-projects-to-airflow) guide._