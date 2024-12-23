![License](https://img.shields.io/badge/License-MIT-blue.svg)   ![Airflow Version](https://img.shields.io/badge/Airflow-2.2.4-blue)  ![Docker Image Version](https://img.shields.io/docker/v/apache/airflow/latest)  


# The Data Observation Toolkit (DOT)
In 2019, the United Nations Statistical Commission highlighted the critical role of accurate health data, stating, _“Every misclassified or unrecorded death is a lost opportunity to ensure other mothers and babies do not die in the same way. When it comes to health, better data can be a matter of life and death.”_ In response, **DataKind** developed DOT to increase trust in public health data, which is essential for equitable, data-driven health service delivery and optimized policy responses. DOT was created in collaboration with our global network of frontline health partners, including Ministries of Health, frontline health workers, and funders, all working together to strengthen health systems worldwide.
You can read more of this initiative in the articles below:
  -	[Pathways to Increasing Trust in Public Health Data](https://chance.amstat.org/2021/09/pathways/ "Pathways to Increasing Trust in Public Health Data")
  -	[Empowering Health Worker and Community Health Systems: Data Integrity and the Future of Intelligent Community Health Systems in Uganda](https://www.datakind.org/blog/empowering-health-workers-and-community-health-systems "Empowering Health Worker and Community Health Systems: Data Integrity and the Future of Intelligent Community Health Systems in Uganda")
  -	[Harnessing the power of data science in healthcare](https://anchor.fm/medxtekafrica/episodes/Ep19---Harnessing-the-power-of-data-science-in-healthcare-e1iijkm "Harnessing the power of data science in healthcare")
  -	[How Data Empowers Health Workers—and Powers Health Systems](https://chwi.jnj.com/news-insights/how-data-empowers-health-workers-and-powers-health-systems "How Data Empowers Health Workers—and Powers Health Systems")

The **Data Observation Toolkit (DOT)** is designed to monitor data and flag potential issues related to data integrity. It can identify problems such as missing or duplicate data, inconsistencies, outliers, and even domain-specific issues like missed follow-up medical treatments after diagnosis. DOT features a user-friendly interface for easily configuring powerful tools like the **DBT** and **Great Expectations** libraries, along with a built-in database for storing and classifying monitoring results.
The primary goal of DOT is to make data monitoring more accessible, allowing users to ensure high-quality data without requiring extensive technical expertise. – Below is a high overview of the tool and how is architected:
 <figure style="text-align:center;">
   <figcaption> DOT high overview </figcaption>
   <img src="https://github.com/wvelebanks/Data-Observation-Toolkit/blob/e650c78dc73b3842766d87d74f56701adb4019ff/images/dot.png" alt=" dot_overview " />
</figure>

<figure style="text-align:center;">
   <figcaption>DOT Architecture</figcaption>
   <img src="https://github.com/wvelebanks/Data-Observation-Toolkit/blob/e650c78dc73b3842766d87d74f56701adb4019ff/images/dot_architecture.png" alt="dot_acrh" />
</figure>

### General Configuration Pre-requisites:
To run DOT you will need to:
1.	Install Python [3.8.9](https://www.python.org/downloads/release/python-389/)  
2.	Install the necessary python packages by running the following commands in your terminal ([Additional information Mac/Linux terminal](https://support.apple.com/guide/terminal/open-or-quit-terminal-apd5265185d-f365-44cb-8b09-71a064a42125/mac#:~:text=On%20your%20Mac%2C%20do%20one,%2C%20then%20double%2Dclick%20Terminal.), [additional information Windows terminal](https://learn.microsoft.com/en-us/windows/terminal/)):
     - `pip install gdown`
     - `pip install python-on-whales`
3.	Install [Docker desktop](https://www.docker.com/products/docker-desktop/). First make sure you have checked the [Docker prerequisites](https://github.com/datakind/medic_data_integrity/tree/main/docker#pre-requisites). We recommend using at least 4GB memory which can be set in the docker preferences, but this can vary depending on the volume of data being tested
4.	If running on a Mac M1/M2 chip, install [Rosetta](https://support.apple.com/en-us/HT211861) and set export DOCKER_DEFAULT_PLATFORM=linux/amd64 in the terminal where you will run the instructions below
5.	(Windows Users only) Need to install WSL for Linux on Windows Pcs

Alternatively, you can use the provided  [environment.yml](./environment.yml) if you have [miniconda](https://docs.conda.io/en/latest/miniconda.html)  installed.

_After completing the software prerequisites for your operating system, **download or clone the DOT repository** to your computer. **You will need this repository for all the setups listed below.**_

 ### Configuration (work in progress)
The following sections provide step-by-step instructions for configuring various components of DOT:
-	[Getting Started with DOT](https://github.com/wvelebanks/Data-Observation-Toolkit/blob/07a44ca01526679912a04e0f20bb6364134cdaf7/documentation_DOT/gettingstartedDOT.md)
-	[Setting Up the Docker Environment and Running DOT](https://github.com/wvelebanks/Data-Observation-Toolkit/blob/e95231bdaf4c8410633b298ac246173b061dbe52/documentation_DOT/setuandrunDOTonDocker.md)
-	[Deploying DOT to Airflow](https://github.com/wvelebanks/Data-Observation-Toolkit/blob/72a3bb7a36fbfc69b621180fd52034dc99d1ee86/documentation_DOT/airflowdeployment.md)
- [Configuring the DOT Database](https://github.com/wvelebanks/Data-Observation-Toolkit/blob/b70d3e044858387443698354b0c4253a6b618b17/documentation_DOT/configuringDOTdb.md)
- [DBT for DOT](https://github.com/wvelebanks/Data-Observation-Toolkit/blob/3c59ddd5c284bc07dc8428e039655827cb736ad5/documentation_DOT/DBTforDOT.md)
- [Configuring DOT](https://github.com/wvelebanks/Data-Observation-Toolkit/blob/a22c4858caf890bd3fbb4a6d98e9aa12c38cbd4e/documentation_DOT/configuringDOT.md)
-	[Developing the Appsmith UI](https://github.com/wvelebanks/Data-Observation-Toolkit/blob/d9845f8228bb147af7f28f7a300a68012e9b51ed/documentation_DOT/developingappsmith.md)
-	[Advanced Topics](https://github.com/wvelebanks/Data-Observation-Toolkit/blob/cb6796d15e46c209e8d08b0d3984bfb6cb9d262d/documentation_DOT/AdavanceTopics.md#adding-more-projects-to-airflow)


### Sample data
Explore [these comprehensive datasets](https://drive.google.com/drive/folders/12tyTqYNNNpDZxQKMQqv7FVOCq18LCurQ?usp=sharing), including global COVID-19 data, U.S. childhood obesity records, and datasets ranging from 1,000 to over a million patient entries, along with a synthetic dataset demonstrating DOT's capabilities with frontline health data.

## Guidelines for adding new tests
*	Existing tests are at [the self-tests folder](dot/self_tests/unit)
*	All tests extend the [test base class](dot/self_tests/unit/base_self_test_class.py) that
    -	facilitates the import of modules under test
    -	recreates a directory in the file system for the test outputs
    -	provides a number of function for supporting tests that access the database, mocking the config files to point to the test [dot_config.yml](dot/self_tests/data/base_self_test/dot_config.yml), (re)creates a schema for DOT configuration and loads it with test data, etc.

## Code quality
We have instituted a pair of tools to ensure the code base will remain at an acceptable quality as it is shared and developed in the community.
1.	The [formulaic python formatter “black”](https://pypi.org/project/black/). As described by its authors it is deterministic and fast but can be modified. We use the default settings, most notably formatting to a character limit of 88 per line.
2.	The [code linter pylint](https://pylint.org/). This follows the [PEP8](https://peps.python.org/pep-0008/) style standard. PEP8 formatting standards are taken care of in black, with the exception that the default pylint line length is 80. Pylint is also modifiable and a standard set of exclusion to the PEP8 standard we have chosen are found [here](https://github.com/datakind/medic_data_integrity/blob/main/.pylintrc). We chose the default score of 7 as the minimum score for pylint to be shared.
The combination of black and pylint can be incorporated into the git process using a pre-commit hook by running setup_hooks.sh


_For detailed information on advanced configuration options and guidelines for contributing to the project, please refer to the [CONTRIBUTING.md](./CONTRIBUTING.md) document._

#
#

----------


## Setting up the DOT User Interface

The above steps will start the DOT user interface, which will allow you to manage DOT and see results. You need to
do a few steps the first time you use it ...

1. Go to [http://localhost:82/](http://localhost:82)
2. Click the button and register to create a login (keep note of the password)
3. Once created, click 'Build my own' on the next popup
4. Click app smith icon top-left to go back tom homepage
5. Top-right next to the new button, click on the '...' and select *import*
6. Select *Import from file* and navigate to file `./docker/appsmith/DOT App V2.json`
7. You will be prompted to enter details for the database connection. You can set these as required, but if using the
   DOT dockerized Postgres database, the parameters are:
    - `Host address: dot-db`
    - `Port: 5432`
    - `Database name: dot_db`
    - `Authentication > User name: postgres`
    - `Authentication > Password: <THE PASSWORD YOU USED WHEN BUILDING DOT>`

You should now see the DOT user interface in developer mode (ie you could edit it). To run in end-user mode:

1. Click button top-right click the 'Deploy' button. This should open a new tab with the user interface in all its glory!

Note: If you want to remove Appsmith information on the deployed app, add `?embed=True` at the end
of the deployed app URL.

## Viewing test results

Your test results will be in the `dot-db` container. You can view the results by opening a shell in the dot-db container:

`docker exec -it dot-db /bin/bash`

Then running the psql client locally in that container:

`psql -U postgres -d dot_db`


Or if you prefer a database client (like [DBeaver](https://dbeaver.io)), you can use their settings:
```
host=localhost
port=5433 
database=dot_db
user=postgres
password=<the POSTGRES_PASSWORD you set above>
```

Note: The host and port are set in the [docker-compose.yml](./docker/docker-compose.yml)

To see some raw results you can run `SELECT * from dot.test_results LIMIT 100;`. Some more advanced queries are provided below.

# Some useful DOT database queries 

The following queries might be useful for visualizing the DOT DB schema and data:

### Statistics on failed tests

```
SELECT
   tr.run_id,
   ct.test_type,
   COUNT(*)
FROM
   dot.test_results tr,
   dot.configured_tests ct 
WHERE
   tr.test_id = ct.test_id
GROUP BY
   tr.run_id,
   ct.test_type
ORDER BY
   ct.test_type
```

Same, but adding in test description and entity names in grouping ...

```
SELECT
   tr.run_id,
   tr.view_name, 
   ct.test_type,
   ct.description,
   ce.entity_name,
   COUNT(*)
FROM
   dot.test_results tr,
   dot.configured_tests ct,
   dot.configured_entities ce 
WHERE
   tr.test_id = ct.test_id AND
   ce.entity_id = ct.entity_id
GROUP BY
   tr.run_id,
   tr.view_name, 
   ct.test_type,
   ct.description,
   ce.entity_name
ORDER BY
   tr.run_id,
   tr.view_name, 
   ct.test_type,
   ct.description,
   ce.entity_name

```

### Linking DOT Data scenarios with configured tests

```
SELECT 
   s.*,
   ct.*
FROM
   dot.scenarios s,
   dot.configured_tests ct 
WHERE 
   s.scenario_id=ct.scenario_id
```

### Linking configured tests to test results

```
SELECT 
   s.*,
   ct.*,
   ce.entity_name,
   tr.*
FROM
   dot.scenarios s,
   dot.configured_tests ct,
   dot.test_results_summary tr,
   dot.configured_entities ce
WHERE 
   s.scenario_id=ct.scenario_id AND
   tr.test_id=ct.test_id AND
   ce.entity_id = ct.entity_id
LIMIT 10
```

### Deactivating all tests except one dbt and one great expectation

`update dot.configured_tests set test_activated=false where test_id not in ('7db8742b-c20b-3060-93e2-614e35da2d4b','0f26d515-a70f-3758-8266-8da326d90eb6')`

### Seeing the raw data for failed tests

dot.test_results column `view_name` provides the name of the DB view which holds the data for failed tests. Additionally,
columns `id_column_name` and `id_column_value` provide the columns to match in the DB entity view, ie the data that was
tested. Finally, you can query to get the underlying data for each test using function `get_dot_data_record`

```
SELECT 
   tr.test_id,
   tr.status,
   dot.get_test_result_data_record(ce.entity_name, tr.id_column_name, 
   tr.id_column_value,'public_tests')
FROM
   dot.scenarios s,
   dot.configured_tests ct,
   dot.configured_entities ce,
   dot.test_results tr
WHERE 
   s.scenario_id=ct.scenario_id AND
   tr.test_id=ct.test_id and 
   ce.entity_id=ct.entity_id
LIMIT 10
```

Where the function parameters are:

- Test entity name
- Test result ID column name (in entity view)
- Test Result ID column value
- Test results schema name

This returns a json record for the data that was tested. **Note:** If using the airflow environment, change `public_tests`
to the schema where the data is, for example `data_flights_db`.

# Configuring DOT

The following sections provide instructions for adding entities and tests to DOT directly in the DOT database. You can 
also use the DOT user interface for tests, for more details please see section see section [The DOT User Interface](#the-dot-user-interface). If you want to test DOT with health related data, please feel free to use this [fabricated dataset] (https://docs.google.com/spreadsheets/d/1l6inpa6ykgUewC-MJkgrQwwc8HjUiTLLJFEDBtAMDB4/edit#gid=31188808) which resembles appointment information and contains some quality issues which DOT can highlight. 
## How to add new entities
The DOT will run tests against user-defined views onto the underlying data. These views are called "entities" and defined in table `dot.configured_entities`:


| Column | Description                                                               |
| :----------- |:--------------------------------------------------------------------------|
| entity_id | Name of the entity e.g. ancview_danger_sign                               |
| entity_category | Category of the entity e.g. anc => needs to be in `dot.entity_categories` |
| entity_definition | String for the SQL query that defines the entity                          |

For example, this would be an insert command to create `ancview_danger_sign`:

```postgres-sql
INSERT INTO dot.configured_entities (project_id,entity_id,entity_category,entity_definition,date_added,date_modified,last_updated_by) VALUES('Project1', 
'ancview_danger_sign', 'anc', '{{ config(materialized=''view'') }}
{% set schema = <schema> %}

select *
from {{ schema }}.ancview_danger_sign');

```

All entities use Jinja macro statements - the parts between `{ ... }` - which the DOT uses to create the entity 
materialized views in the correct database location. Use the above format for any new entities you create.

The SQL for the view definition can be more complex than the example above, combining data from multiple underlying 
tables or views. For example: 

```postgres-sql
{{ config(materialized=''view'') }}
{% set schema = <schema> %}

select ap.*,
        ap.lmp as lmp_date,
        DATE_PART(''day'', reported - lmp) as days_since_lmp
from {{ schema }}.ancview_pregnancy ap

```

When you add a new entity to the configuration, take a look to the existing `dot.entity_categories` to associate your new entity
to one of them. If you need to add a new category, the table `dot.entity_categories` has the following columns:
| Column | Description |
| :----------- | :----------- |
| entity_category | Category of the entity e.g. anc |
| description | A description of the category |

An example of an insert statement would be:
`INSERT INTO dot.entity_categories VALUES('anc', 'antenatal care');`

## How to configure tests  
Tests are defined in the table `dot.configured_tests`. Each test has an associated `test_type`, a list of which can be 
found in table `dot.test_types` (see section "DOT Database Schema" below for more details on the full schema).

To use one of these test types for a new test, insert a new row in `dot.configured_tests`.

Here are the columns included in a test:
| Column | Description |
| :----------- | :----------- |
test_activated | Whether the test is activated or not
project_id | ID of the project, for example "`ScanProject1`"
test_id | UUID of the test
scenario_id | ID of the scenario
priority | Priority level
description | Description of the test
impact | Why the test is important
proposed_remediation | How the issue in this test might be solved
entity | The entity against which the test runs (check `entities` below)
test_type | Test type
column_name | The column in the table against which the test runs
column_description | Description of the above column
test_parameters | Any parameters the test takes in
date_added | Date when the test was added
date_modified | Date when the test was last modified
last_updated_by | Person who last updated the test

The UUID in the above example will get overwritten with an automatically generated value. Also, your test must be unique 
for the project. If you get a key violation it's probably because that test already exists.

#### Test validation

Any insert of update of configured tests will call database function `dot.test_validation`, as defined in 
[./db/dot/1-schema.sql](./db/dot/1-schema.sql). This function performs some basic validation to ensure test parameters
are in an expected format. It is not infallable, if there are any issues with test parameters and tests do not execute,
you can confirm this by looking at columns `test_status` and `test_status_message` in `dot.test_results_summary`.

#### Example `INSERT` statements for adding a new test for each test type:

**Note:** In all of the following examples, the UUID in the insert statement will be replaced with an automatically 
generated one.

1. `relationship`
    <br><br>
    ```
    'INSERT INTO dot.configured_tests VALUES(TRUE, 'ScanProject1', '0cdc9702-91e0-3499-b6f0-4dec12ad0f08', 'ASSESS-1', 3, '', '', 
    '', 'ancview_pregnancy', 'relationships', 'uuid', '', 
    $${"name": "danger_signs_with_no_pregnancy", "to": "ref('dot_model__ancview_danger_sign')", "field": "pregnancy_uuid"}$$, 
    '2021-12-23 19:00:00.000 -0500', '2021-12-23 19:00:00.000 -0500', 'your-name');
    ```
2. `unique`
    <br><br>
    ```
    INSERT INTO dot.configured_tests VALUES(TRUE, 'ScanProject1', '52d7352e-56ee-3084-9c67-e5ab24afc3a3', 'DUPLICATE-1', 3, '', 
    '', '', 'ancview_pregnancy', 'unique', 'uuid', 'alternative index?', '', 
    '2021-12-23 19:00:00.000 -0500', '2021-12-23 19:00:00.000 -0500', 'your-name');
    ```
3. `not_negative_string_column`
    <br><br>
    ```
    INSERT INTO dot.configured_tests VALUES(TRUE, 'ScanProject1', '8aca2bee-9e95-3f8a-90e9-153714e05367', 'INCONSISTENT-1', 3, 
    '', '', '', 'ancview_pregnancy', 'not_negative_string_column', 'patient_age_in_years', '', 
    $${"name": "patient_age_in_years"}$$, '2021-12-23 19:00:00.000 -0500', '2021-12-23 19:00:00.000 -0500', 'your-name');
    ```
4. `not_null`
    <br><br>
    ```
    INSERT INTO dot.configured_tests VALUES(TRUE, 'ScanProject1', '549c0575-e64c-3605-85a9-70356a23c4d2', 'MISSING-1', 3, '', 
    '', '', 'ancview_pregnancy', 'not_null', 'patient_id', '', '', '2021-12-23 19:00:00.000 -0500', '2021-12-23 19:00:00.000 -0500', 'your-name');
    ```
5. `accepted_values`
    <br><br>
    ```
    INSERT INTO dot.configured_tests VALUES(TRUE, 'ScanProject1', '935e6b61-b664-3eab-9d67-97c2c9c2bec0', 'INCONSISTENT-1', 3, 
    '', '', '', 'ancview_pregnancy', 'accepted_values', 'fp_method_being_used', '', 
    $${"values": ['oral mini-pill (progestogen)', 'male condom', 'female sterilization', 'iud', 'oral combination pill', 'implants', 'injectible']}$$, 
    '2021-12-23 19:00:00.000 -0500', '2021-12-23 19:00:00.000 -0500', 'your-name');
    ```
6. `possible_duplicate_forms`
    <br><br>
    ```
    INSERT INTO dot.configured_tests VALUES(TRUE, 'ScanProject1', '7f78de0e-8268-3da6-8845-9a445457cc9a', 'DUPLICATE-1', 3, '', 
    '', '', 'ancview_pregnancy', 'possible_duplicate_forms', '', '', 
    $${"table_specific_reported_date": "delivery_date", "table_specific_patient_uuid": "patient_id", "table_specific_uuid": "uuid"}$$, '2021-12-23 19:00:00.000 -0500', '2021-12-23 19:00:00.000 -0500', 'your-name');
    ```
7. `associated_columns_not_null`
    <br><br>
    ```
    INSERT INTO dot.configured_tests VALUES(TRUE, 'ScanProject1', 'd74fc600-31c3-307d-9501-5b7f6b09aff5', 'MISSING-1', 3, '', 
    '', '', 'ancview_pregnancy', 'associated_columns_not_null', 'diarrhea_dx', 'diarrhea diagnosis', 
    $${"name": "diarrhea_dx_has_duration", "col_value": True, "associated_columns": ['max_symptom_duration']}$$, 
    '2021-12-23 19:00:00.000 -0500', '2021-12-23 19:00:00.000 -0500', 'your-name');
    ```
8. `expect_similar_means_across_reporters`
    <br><br>
    ```
    INSERT INTO dot.configured_tests VALUES(TRUE, 'ScanProject1', '0cdc9702-91e0-3499-b6f0-4dec12ad0f08', 'BIAS-1', 3, 
    'Test for miscalibrated thermometer', '', '', 'ancview_pregnancy', 'expect_similar_means_across_reporters', 
    'child_temperature_pre_chw', '', '{"key": "reported_by","quantity": "child_temperature_pre_chw",
    "form_name": "dot_model__iccmview_assessment","id_column": "reported_by"}', '2022-01-19 20:00:00.000 -0500', 
    '2022-01-19 20:00:00.000 -0500', 'your-name');
    ```
9. `expression_is_true`
    <br><br>
    ```
    INSERT INTO dot.configured_tests VALUES(TRUE, 'ScanProject1', '3081f033-e8f4-4f3b-aea8-36f8c5df05dc', 'INCONSISTENT-1', 3, 
    'Wrong treatment/dosage arising from wrong age of children (WT-1)', '', '', 'ancview_pregnancy', 
    'expression_is_true', '', '', 
    $${"name": "t_under_24_months_wrong_dosage", "expression": "malaria_act_dosage is not null", "condition": "(patient_age_in_months<24) and (malaria_give_act is not null)"}$$,
    '2022-02-14 19:00:00.000 -0500', '2022-02-14 19:00:00.000 -0500', 'your-name');
    ```
10. `custom_sql`
<br><br>
Custom SQL queries require special case because they must have `primary_table` and `primary_table_id_field` specified within the SQL query as shown below:
    ```
    INSERT INTO dot.configured_tests VALUES(TRUE, 'ScanProject1', 'c4a3da8f-32f4-4e9b-b135-354de203ca90', 'TREAT-1', 6, 'Test for new family planning method (NFP-1)', '', '', 'ancview_pregnancy', 'custom_sql', '', '',
format('{%s: %s}',
    to_json('query'::text),
    to_json($query$
        select
            a.patient_id,
            a.reported,
            a.fp_method_being_used,
            'dot_model__fpview_registration' as primary_table,
            'patient_id' as primary_table_id_field
        from {{ ref('dot_model__fpview_registration') }} a
            inner join
            (
                select distinct
                patient_id,
                max(reported) reported
                from {{ ref('dot_model__fpview_registration') }}
                where fp_method_being_used in ('vasectomie','female sterilization')
                group by patient_id
            ) b on a.patient_id = b.patient_id and a.reported > b.reported
            and fp_method_being_used not in ('vasectomie','female sterilization')
            and fp_method_being_used not like '%condom%'
    $query$::text)
    )::json,'2021-12-23 19:00:00.000 -0500', '2021-12-23 19:00:00.000 -0500', 'Leah');    
    ```


### Activating/Deactivating existing tests

Note that it's possible to deactivate tests, which can sometimes be useful for testing. To do this simply 
set `test_activated=False` in table `dot.configured_tests`. For example:
 
 
` update dot.configured_tests set test_activated=false where test_id not in ('7db8742b-c20b-3060-93e2-614e35da2d4b','0f26d515-a70f-3758-8266-8da326d90eb6'); `

## Developing the Appsmith UI

Clicking 'Edit' on the imported app gives you the ability to edit the app. See the [appsmith help site](https://docs.appsmith.com) for more information 
on this.

Key things to note:

- All validation, defaulting, tool tips are controlled via the Database as much as possible. See the 'Queries' section
- Of particular note is that the test_parameters JSON generates a form. This was done once, be aware it will remove many 
  settings if you click regenerate. I have a feature request open with appsmith to create fields with default types, 
  values and validation functions, but for now we are adding new fields manually. Note that you might be able to 
  reinstate the logic en masse by looking at the raw appsmith app JSON file

## Updating to latest version of Appsmith

Appsmith release bug fixes and enhancements. By default the DOT docker build will do this automatically. To do this manually:

1. In `./docker` run `docker compose -f docker-compose-with-appsmith-ui.yml stop`
2. `docker rm appsmith`
3. In a clean directory: `curl -L https://bit.ly/32jBNin -o $PWD/docker-compose.yml`
4. `docker-compose pull && docker-compose rm -fsv appsmith && docker-compose up -d`
5. Back in `./docker` run `docker compose -f docker-compose-with-appsmith-ui.yml up -d`

Note, these will remove your saved configuration and app, so be sure to make note of these before doing the above
steps.

# Advanced topics

## The DOT DB Schema
The DOT Database schema is defined as follows:

![ER diagram](./images/db_schema.png)

Tables are defined as follows:

| Table | Description |
| :----------- | :----------- |
| projects | Defines the projects the DOT can be run for. Typically a project is associated with a single source database where the data resides |
| configured_entities | Holds entities, which are the views onto underlying data the DOT will test |
| entity_categories | Category of each entity, for example "Pre-natal care". Useful for segmenting DOT results by category.
| configured_tests | the table which defines what tests to run for each project
| scenarios | The DOT Taxonomy scenario for each test |
| test_types | The available test types for each test, eg null, unique, custom_sql |
| scenario_test_types | The test types that apply for any given scenario |
| test_parameters_interface | JSON object defining Interface parameters required for each test type. Note: Not currently used but will be in future |
| run_log | Log of DOT runs, with stop/start times and failure message |
| test_results | Main test results table, indicating test fails |
| test_results_summary | Aggregated test results for each run |
| remediation_log | Record of remediation actions. (Note: Not yet implemented) |

The test_results table includes fields to link back to the data tested. This can be a fixed table or view, but also a 
custom SQL query. Given this, there is a useful Postgres function which will retreive a JSON record for the data tested,
see 'Seeing the raw data for failed tests' above.
 


## How to visualize the results using Superset

At time of writing Superset setup isn't fully automated, so once your Docker containers are running the first time, 
run these commands:

```
docker exec -it superset superset fab create-admin  --username admin  --firstname Superset  --lastname Admin   --email admin@superset.com  --password admin
docker exec -it superset superset db upgrade
docker exec -it superset superset init
```

You can ignore the warnings about CACHE_TYPE being null.

Once complete, open the following URL in a browser:

[http://localhost:8080/login/](http://localhost:8080/login/)

**Note**: Some of the team have observed that Google Chrome works a better than Safari.

... and login with **admin/admin**.

Once in, connect to the DOT database:

1. In super select *data > databases* from top menu
2. On the right click the '+ Database' button
3. Choose PostgresSQL
4. Use these DB parameters:
   - Host: dot_db
   - Database: dot_db
   - Display name: dot_db
   - Port: 5432
   - User: postgres
   - Password: <Whatever password you used for POSTGRES_PASSWORD when building the Docker environment>

Once set up, you can create datasets for any of the DOT tables ...

1. Select *Data > Datasets+
2. Click '+ DATASET' button
3. Select the tables(s) you want from the DOT database, for example test_results

Now you have datasets, you can [create charts](https://superset.apache.org/docs/creating-charts-dashboards/first-dashboard#adding-a-new-table) 

IMPORTANT! If superset dashboards and using Docker, be sure to export your dashboard so you don't lose
work if rebuilding your Docker environment.



### Running the DOT in Airflow (Demo)

A DAG has been included which copies data from the uploaded DB dump into the DOT DB 'data_ScanProject1' schema, and then runs 
the toolkit against this data. To do this ...

1. Go to [http://localhost:8083](http://localhost:8083/home)
2. Log in with airflow/airflow
3. Click on 'DAGs' in top menu
4. Search for 'dot' in top-right search box (be sure to hit return twice)
5. Toggle DAG 'run_dot_project' to Active (far left toggle on row)
6. Click play icon under 'Actions', this will start the run

To see progress, and/or logs ...

7. Click on one of the circles under 'Runs', eg 'running', or 'completed'
8. Click on top 'Dag Id'
9. Click on task and then 'Log', you should now see logs

To use Airflow CLI for debugging a task (assuming you are getting object ancview_danger_sign):
 
 1. `docker exec -it docker-airflow-worker-1 /bin/bash`
 2. `airflow tasks test run_dot_project sync_object_flight_data  2022-03-01`

Or to run just DOT stage ...

`airflow tasks test run_dot_project run_dot  2022-03-01`


### Running the DOT in Airflow (Connecting to external databases)

The following instructions illustrate how to use a local airflow environment, connecting with external databases for the data and DOT.

**NOTE:** These are for illustrative purposes only. If using Airflow in production it's important that it is set up correctly
and does not expose a http connection to the internet, and also has adequate network security (firewal, strong password, etc)

1. Edit [./dot/dot_config.yml] and set the correct parameters for your external dot_db
2. Create a section for your data databases and set connection parameters
3. If you have a DAG json file `dot_projects.json` already, deploy it into `./airflow/dags`
4. Run steps 1-11 in [Configuring/Building Airflow Docker environment](#Configuring/Building Airflow Docker environment)
5. Run steps 12 and 13, but use the values for your external databases you configured in `dot_config.yml`

You will need to configure DOT tests and the DAG json file appropriately for your installation.


#### Adding more projects

If configuring Airflow in production, you will need to adjust `./docker/dot/dot_config.yml` accordingly. You can also 
add new projects by extending the projects array in the [Airflow configuration JSON](https://github.com/datakind/Data-Observation-Toolkit/blob/master/docker/airflow/dags/dot_projects.json)

## How the DOT works 

The Data Observation Toolkit (DOT) uses the open source projects [DBT](https://docs.getdbt.com/docs/introduction/) and [Great Expectations](https://greatexpectations.io/)
as a framework for the definition, development and execution of the data tests.

Most tests are developed on DBT, leveraging its support for base tests for column not nulls, foreign key checks, and 
a few more, all of which can be expressed as entries on a YAML file. Additionally, making use of its custom tests, 
many complex tests involving a set of columns of one or two tables can be expressed using DBT, written with SQL/Jinja 
statements. 

Great Expectations adds the possibility of implementing tests in python, and are used for checks that cannot be
expressed in SQL, for example tests that inspect the statistical distribution of the data.

### DBT

#### Directory structure

The [DBT folder](dot/dbt) contains DBT models, macros, custom tests, and project files. Most of these files are 
actually written by the DOT itself from the configured entities and tests in the `dot` schema, but note that any
DBT command needs the actual files as inputs.

- Core subdirectories
  - __macros:__ Jinja macros to support organized code and custom schema tests
  - __models:__ This is the core of the DBT project; it contains both SQL for models and yml files for schema tests,
which are written by the tool from `dot.configured_entities`, for the SQL for models, and from `dot.configured_tests`,
for the tests' yml files
  - __tests:__ Custom SQL tests, written by the tool from `dot.configured_tests`, for the test of type "custom_sql"

- Non-version controlled directories (that are created via the dbt runs)
  - __target:__ Compiled sql used to create models and tests
  - __dbt_modules:__ DBT plugins (e.g. dbt_utils) installed via `dbt deps`
  - __logs:__ Logs created by dbt (not used elsewhere in this stack)

- Scripts
  - [__dbt.py:__](dot/utils/dbt.py) Utilities that manage the run of DBT jobs, which create views containing rows 
flagged by failing tests, creates a test coverage reports of the DBT side of the stack and updates tests results
to the DB

- Config files
  - __dbt_project.yml:__ Defines paths to important DBT assest (including those listed above) and project-specific 
variables -not in version control, it is either generated by the tool or copied from the project-specific configuration
  - __packages.yml:__ Indicates DBT plugins used

#### Running tests

Commands for reference -these are actually run by the tool.
- Run all tests: `dbt test -m core`  
- Run all tests for patients only: `dbt test -m patient`  
- Run schema tests for patients only `dbt test --schema -m patient`  
- Run data tests for patients only `dbt test --data -m patient`  

#### Updating models

The models in the `core` folder are a dump of the DB `dot.configured_entities`. Right now, most of the entites are just
full table copies of the raw data. Reference commands:
- Update all models: `dbt run -m core`

#### Writing new tests

Since we'll have lots of tests we want to run, it's important to keep them organized.
Wherever possible, schema tests should be implemented with simple test types in `dot.configured_tests` 
(such as not_null, unique, relationships, accepted_values, etc, that go to a yml associated to the the `schema.yml`) 
because it minimizes the need for adding lots of additional SQL. You may find the (already set up on this project) 
[`dbt_utils` extension](https://github.com/fishtown-analytics/dbt-utils) 
useful for writing more complex versions of these kinds of tests.

For tests requiring custom SQL, a new custom_sql row should be created in `dot.configured_tests`, which in turn creates
a file in `tests/core`.

For more details on implementing tests in dbt please refer to the [dbt section](dot/dbt/README.md) in the DOT.

#### Making sense of failed test results

The DOT runs a number of steps for generating test results:
- it runs `dbt test` to run the tests
- it autogenerates model code for only the tests that have failed; these models will produce views when run
- the end results will be a new set of data sources (prefixed with "tr_") containing all the rows violating a test
- these failing rows are also loaded into the table `dot.test_results`

You should use `run_everything.sh` as a quick way to run the right dbt commands in sequence and guarantee that the right
dependencies/assumptions are in place to make things work.

Note that the code generated for these models is gitignored because they're based on compiled SQL and contain specific 
database names instead of dbt references.

It should also be noted that DBT does support auto-generated documentation out of the box. HOWEVER, these docs are 
fairly limited in their usefulness for this project, especially since they don't provide a way to find the specific 
records that are causing a test to fail. This is why we have written new code to generate report that better address 
the community health DOT use case.

In the event that you do want to explore the native DBT docs, they can be created via `dbt docs generate`. To view them,
running `dbt docs serve` will fire up a local web server so you can explore them in a browser.

#### Boilerplate Resources

These were listed automatically by `dbt init` and are helpful general resources for learning more about DBT

- Learn more about dbt [in the docs](https://docs.getdbt.com/docs/introduction/)
- Check out [Discourse](https://discourse.getdbt.com/) for commonly asked questions and answers
- Join the [chat](http://slack.getdbt.com/) on Slack for live discussions and support
- Find [dbt events](https://events.getdbt.com) near you
- Check out [the blog](https://blog.getdbt.com/) for the latest news on dbt's development and best practices

### Great Expectations

#### Directory structure

The [great_expectations folder](dot/great_expectations) is a [Great Expectations](https://greatexpectations.io/) project.

- Core directories
  - __expectations:__ JSON files indicating the tests to be run (similar to yml files containing schema tests in DBT);
these are not in version control, but generated by the tool from `dot.configured_tests`
  - __notebooks:__ Jupyter notebooks automatically created by Great Expectations during setup to allow for a more 
convenient front-end to edit the JSON files in `expectations` (check out the flow described by the 
[Great Expectations documentation](https://docs.greatexpectations.io/en/latest/how_to_guides/creating_and_editing_expectations/how_to_edit_an_expectation_suite_using_a_disposable_notebook.html))
  - __plugins:__ Additional code for customizing this Great Expectations project. Most important in here is `custom_expectations.py`, which is where tests requiring arbitrary python should be added as methods under the `CustomSqlAlchemyDataset` class (somewhat similar to the custom SQL tests in DBT, except written in python).

- Non-version controlled directories (automatically created by Great Expectations)
  - __uncommitted:__ Generic place to capture all Great Expecations files that should not be version controlled, 
including logs and database connection details

  - Scripts
    - [__great_expectations.py:__](dot/utils/great_expectations.py) Utility script to automatically run GE tests 
and create coverage reports. GE's CLI commands for this are much more verbose and more difficult to remember than DBTs.

  - Config files -not in version control, these are either managed by the tool or set in the project-dependent config
    - __batch_config.json:__ Defines datasources, test suites, and tables to be included when running Great Expectations
    - __great_expectations.yml:__ Main config file for Great Expectations (similar to `dbt_project.yml`)
    
#### Terminology

- An expectation is a particular function accepting one or multiple parameters (defined in Python)
- A test is an instance of an expectation, with a specific set of parameters (defined in a JSON file)
- Out Of The Box (OOTB) expectations are provided by Great Expectations and built-in with the library's codebase.

#### Structuring tests

- Tests are defined in JSON, akin to dbt schema tests in yaml
  - These live in a suite called `great_expectations/expectations/<FILE>.json`

- Tests could be used OOTB, but most of the time are written custom
  - Custom expectations can operate on any tables passed as a parameter, but OOTB expectations will only be applied on 
the selected table in batch_config.json (see extra notes below for details)
  - OOTB tests can use views defined in DBT
  - OOTB tests can be defined directly in the JSON file
  - Custom expectations need to be added as decorated methods in `plugins/custom_expectations.py`
    - Custom tests can run arbitrary python/pandas (even though this isn't well-documented in the GE published docs)
      - Once added to in custom_expectations.py, tests can be defined in the JSON file similarly to OOTB tests
    - OOTB tests have a variety of outputs and therefore might not conform to the format expected by the 
Data Integrity framework -whenever possible, use DBT tests instead

If a mix of OOTB and custom expectations are needed, it is suggested to keep them in two suites of tests to manage 
their differences efficiently

#### Extra notes

The Data Observation Toolkit (DOT) works with a few assumptions in terms of what an expectation should accept and return.

1. We create views out of the DOT results with Postgresql-specific syntax. If you're using any other database engine, 
please adapt the query in [great_expectations.py](dot/utils/great_expectations.py).

2. An expectation accepts both column names and table names as arguments. Great Expectations generally has 
table-agnostic suites running on specific single tables, but we're changing this model a bit because data integrity 
queries often depend on more than one table. Therefore, a default empty dataset is added in the `batch_config.json` 
for all custom expectations, and a relevant table name should be passed to the expectation in the suite definition. 
The default dataset won't be read at all and is used as a placeholder.

3. Custom expectations are found in custom_expectations.py under plugins, it is recommended to follow their format and 
to add your own custom expectations as methods of that same class.

4. The toolkit's post-processing step expects a few specific field in the output of the expectations 
(refer to example custom expectations to see how they're implemented)

## Developing DOT

The DOT is open source so we encourage any development is done as part of that intiative. For reference this would 
include code quality standards and self-tests, some details of which are provided below.

### Self-tests

The DOT runs some self-tests to check that its functions are running fine. If you are contributing to the project
by adding a new feature or solving a bug, please follow the following guidelines:
- find the existing tests applicable to the area that you are modifying
- add a few more relevant tests for your bugfix/improvement
- implement your changes until the test pass

#### Running self-tests

##### Using Docker

The Docker build provided above to run DOT, also includes self-test. So once you have the container running, all you
need to do is ..

1. `exec -it dot /bin/bash`
2. `pytest dot/self_tests/unit`

##### On your local machine

Assuming you would like to run the tests locally, as preparation steps, you will need to:
- Create a local env for python via either venv or conda
- Make sure your Python version aligns with that in `.github/workflows/lint.yml`
- Create a conda environment using the `environment.yml` file at the root directory
- Prepare a postgres database that the tests can use (e.g. you can deploy a docker container and use it as a database
only, or you could use a local instance of a Postgres DB)
- Prepare a [dot_config.yml](dot/self_tests/data/base_self_test/dot_config.yml) at directory 
`dot/self_tests/data/base_self_test` with the same structure as the [dot_config.yml](dot/config/example/dot_config.yml) 
for the DOT; should look like something as follows (note that the config below points to DB in the docker container):
```
dot:
  save_passed_tests: False
  output_schema_suffix: tests
dot_db:
  type: postgres
  host: localhost
  user: postgres
  pass: "{{ env_var('POSTGRES_PASSWORD') }}"
  port: 5433
  dbname: dot_db
  schema: self_tests_dot
  threads: 4
ScanProjec1_db:
  type: postgres
  host: localhost
  user: postgres
  pass: "{{ env_var('POSTGRES_PASSWORD') }}"
  port: 5433
  dbname: dot_db
  schema: self_tests_public
  threads: 4
```

And finally you can run the tests from a terminal as follows:
```
pytest dot/self_tests/unit
```




