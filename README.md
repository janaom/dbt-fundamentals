
✅ [Introduction to dbt](https://github.com/janaom/dbt-fundamentals/blob/main/README.md#introduction-to-dbt)

✅ [Intermediate dbt](https://github.com/janaom/dbt-fundamentals/blob/main/README.md#intermediate-dbt)



# Introduction to dbt
--------------------

Start running `dbt` command.
```shell
repl:~/workspace$ dbt
Usage: dbt [OPTIONS] COMMAND [ARGS]...

  An ELT tool for managing your SQL transformations and data models. For more
  documentation on these commands, visit: docs.getdbt.com

Options:
  --cache-selected-only / --no-cache-selected-only
                                  At start of run, populate relational cache
                                  only for schemas containing selected nodes,
                                  or for all schemas of interest.
  -d, --debug / --no-debug        Display debug logging during dbt execution.
                                  Useful for debugging and making bug reports.
  -x, --fail-fast / --no-fail-fast
                                  Stop execution on first failure.
  --log-cache-events / --no-log-cache-events
                                  Enable verbose logging for relational cache
                                  events to help when debugging.
  --log-format [text|debug|json|default]
                                  Specify the format of logging to the console
                                  and the log file. Use --log-format-file to
                                  configure the format for the log file
                                  differently than the console.
  --log-format-file [text|debug|json|default]
                                  Specify the format of logging to the log
                                  file by overriding the default value and the
                                  general --log-format setting.
  --log-level [debug|info|warn|error|none]
                                  Specify the minimum severity of events that
                                  are logged to the console and the log file.
                                  Use --log-level-file to configure the
                                  severity for the log file differently than
                                  the console.
  --log-level-file [debug|info|warn|error|none]
                                  Specify the minimum severity of events that
                                  are logged to the log file by overriding the
                                  default value and the general --log-level
                                  setting.
  --log-path PATH                 Configure the 'log-path'. Only applies this
                                  setting for the current run. Overrides the
                                  'DBT_LOG_PATH' if it is set.
  --partial-parse / --no-partial-parse
                                  Allow for partial parsing by looking for and
                                  writing to a pickle file in the target
                                  directory. This overrides the user
                                  configuration file.
  --populate-cache / --no-populate-cache
                                  At start of run, use `show` or
                                  `information_schema` queries to populate a
                                  relational cache, which can speed up
                                  subsequent materializations.
  --print / --no-print            Output all {{ print() }} macro calls.
  --printer-width INTEGER         Sets the width of terminal output
  -q, --quiet / --no-quiet        Suppress all non-error logging to stdout.
                                  Does not affect {{ print() }} macro calls.
  -r, --record-timing-info PATH   When this option is passed, dbt will output
                                  low-level timing stats to the specified
                                  file. Example: `--record-timing-info
                                  output.profile`
  --send-anonymous-usage-stats / --no-send-anonymous-usage-stats
                                  Send anonymous usage stats to dbt Labs.
  --static-parser / --no-static-parser
                                  Use the static parser.
  --use-colors / --no-use-colors  Specify whether log output is colorized in
                                  the console and the log file. Use --use-
                                  colors-file/--no-use-colors-file to colorize
                                  the log file differently than the console.
  --use-colors-file / --no-use-colors-file
                                  Specify whether log file output is colorized
                                  by overriding the default value and the
                                  general --use-colors/--no-use-colors
                                  setting.
  --use-experimental-parser / --no-use-experimental-parser
                                  Enable experimental parsing features.
  -V, -v, --version               Show version information and exit
  --version-check / --no-version-check
                                  If set, ensure the installed dbt version
                                  matches the require-dbt-version specified in
                                  the dbt_project.yml file (if any).
                                  Otherwise, allow them to differ.
  --warn-error                    If dbt would normally warn, instead raise an
                                  exception. Examples include --select that
                                  selects nothing, deprecations,
                                  configurations with no associated models,
                                  invalid test configurations, and missing
                                  sources/refs in tests.
  --warn-error-options WARNERROROPTIONSTYPE
                                  If dbt would normally warn, instead raise an
                                  exception based on include/exclude
                                  configuration. Examples include --select
                                  that selects nothing, deprecations,
                                  configurations with no associated models,
                                  invalid test configurations, and missing
                                  sources/refs in tests. This argument should
                                  be a YAML string, with keys 'include' or
                                  'exclude'. eg. '{"include": "all",
                                  "exclude": ["NoNodesForSelectionCriteria"]}'
  --write-json / --no-write-json  Whether or not to write the manifest.json
                                  and run_results.json files to the target
                                  directory
  -h, --help                      Show this message and exit.

Commands:
  build          Run all seeds, models, snapshots, and tests in DAG order
  clean          Delete all folders in the clean-targets list (usually...
  compile        Generates executable SQL from source, model, test, and...
  debug          Test the database connection and show information for...
  deps           Pull the most recent version of the dependencies listed...
  docs           Generate or serve the documentation website for your...
  init           Initialize a new dbt project.
  list           List the resources in your project
  parse          Parses the project and provides information on performance
  run            Compile SQL and execute against the current target...
  run-operation  Run the named macro with any supplied arguments.
  seed           Load data from csv files into your data warehouse.
  show           Generates executable SQL for a named resource or inline...
  snapshot       Execute snapshots defined in your project
  source         Manage your project's sources
  test           Runs tests on data in deployed models.

  Specify one of these sub-commands and you can find more help from there.
```

dbt, also known as the data build tool, is designed to simplify the management of data warehouses and transform the data within. This is primarily the T, or transformation, within ELT (or sometimes ETL) processes. It allows for easy transition between data warehouse types, such as Snowflake, BigQuery, Postgres, or in this course, DuckDB. dbt also provides the ability to use SQL across teams of multiple users, simplifying interaction. In addition, dbt translates between SQL dialects as appropriate to connect to different data sources and warehouses. 

dbt mainly uses SQL to define data models and transform them. Here, a data model is just a way to organize your data. For example, it might organize your data into tables, views, or other database objects, and defines the relationships between them. For example, in an e-commerce context, a data model might link sales data to product details, and payment records. Such a data model allows for efficient analysis and reporting. As such, you should be fairly knowledgeable of SQL to get the most out of using dbt. dbt can define the relationships between data models and manage the dependencies that arise when using them. Consider if we had one model for customers and a second for orders; these can be linked easily with dbt. The dbt tool also performs the transformation process (or processes) as defined by the user. A basic example is converting the raw data from log files into database tables. Finally, dbt can also test and verify the data matches user-defined quality requirements. We'll cover all of these in later videos. 

dbt is open-source, also known as dbt-core, primarily available as a command-line tool, available for all main operating systems such as Mac, Windows, and Linux. There is also a managed version of dbt known as dbt Cloud that we won't cover in this course. dbt and has many commands and sub commands we'll cover later. For now the two commands we need are `dbt -v` and `dbt -h` for help. 

To create a project within dbt, we use the dbt init subcommand. When running `dbt init`, it asks two questions: the project name and which database or data warehouse type you'd like to use. Using `dbt init <projectname>`, it only asks for the database type. dbt init creates the top-level project folder, subfolders and configuration files for the project. Here is an example running dbt init with a project name of test_project and duckdb as our database type.

<img width="1132" height="553" alt="image" src="https://github.com/user-attachments/assets/823e7ab1-e198-405a-b46d-6aa9245df602" />

The next thing to understand about dbt projects is the profile. Within dbt, a profile is like a deployment scenario. This can include development, staging or testing, and production. A dbt project can have multiple profiles, allowing for different warehouse configurations per deployment scenario. These profiles (or configurations) are defined in the `profiles.yml` file, which must be created for new projects. This is an example profiles.yml file with two deployment types (dev and prod). The option target defines the default, in this case, dev. You may also wonder why to select DuckDB vs Snowflake. DuckDB is useful for development and testing locally, while Snowflake would be better used in production as other users will likely need to access the data. 

<img width="1141" height="430" alt="image" src="https://github.com/user-attachments/assets/40f4d451-de9e-4ca7-b692-53ab374fb31e" />

You may be wondering what YAML is. YAML stands for Yet Another Markup Language. It is a text based file format, where whitespace indentation matters, much like Python. YAML is used in many development scenarios for configuration, due to its relatively human-readable format. Writing or modifying YAML can be tricky, as you must maintain indentation as illustrated. In the profiles.yml example, dev: and prod: are at the same level of indentation. A YAML skeleton will be provided in this course, but be aware of the formatting requirements when creating one from scratch. 

<img width="1134" height="442" alt="image" src="https://github.com/user-attachments/assets/95158639-6568-4ed4-a36c-12586e5d2f2b" />


## Instructions

Run the appropriate dbt sub-command in the terminal window to initialize the project, using the information found in the ProjectInfo.txt file.
Using the Linux command to change directory, change to the newly created project directory in the terminal window.
Verify there are currently six main sub-directories (analyses, macros, models, seeds, snapshots, and tests).

```shell
repl:~/workspace$ dbt init
15:28:29  Running with dbt=1.5.1
Enter a name for your project (letters, digits, underscore): nyc_yellow_taxi
Which database would you like to use?
[1] duckdb

(Don't see the one you want? https://docs.getdbt.com/docs/available-adapters)

Enter a number: 1
15:28:50  No sample profile found for duckdb.
15:28:50  
Your new dbt project "nyc_yellow_taxi" was created!

For more information on how to configure the profiles.yml file,
please consult the dbt documentation here:

  https://docs.getdbt.com/docs/configure-your-profile

One more thing:

Need help? Don't hesitate to reach out to us via GitHub issues or on Slack:

  https://community.getdbt.com/

Happy modeling!

repl:~/workspace$ ls
logs  nyc_yellow_taxi  ProjectInfo.txt
repl:~/workspace$ cd nyc_yellow_taxi/
repl:~/workspace/nyc_yellow_taxi$ ls -la
total 12
drwxr-sr-x 8 repl repl  151 Jun 19  2023 .
drwxr-xr-x 1 repl repl   64 Aug 12 17:28 ..
drwxr-sr-x 2 repl repl   22 Jun 19  2023 analyses
-rw-r--r-- 1 repl repl 1277 Aug 12 17:28 dbt_project.yml
-rw-r--r-- 1 repl repl   29 Jun 19  2023 .gitignore
drwxr-sr-x 2 repl repl   22 Jun 19  2023 macros
drwxr-sr-x 3 repl repl   21 Jun 19  2023 models
-rw-r--r-- 1 repl repl  571 Jun 19  2023 README.md
drwxr-sr-x 2 repl repl   22 Jun 19  2023 seeds
drwxr-sr-x 2 repl repl   22 Jun 19  2023 snapshots
drwxr-sr-x 2 repl repl   22 Jun 19  2023 tests
repl:~/workspace/nyc_yellow_taxi$
```

## Instructions

    Open the nyc_yellow_taxi/profiles.yml file in the editor window.
    Modify the project name (the first line) to nyc_yellow_taxi.
    Change the type: to duckdb.
    In the terminal, use the command `dbt debug` to verify there are no errors.
    When finished, submit the exercise.

```python
#dbt_project.yml

# Modify the project name
nyc_yellow_taxi:
  outputs:
    dev:
      # Change the database type
      type: duckdb
      path: dbt.duckdb
  target: dev

repl:~/workspace/nyc_yellow_taxi$ dbt debug
15:31:27  Running with dbt=1.5.1
15:31:27  dbt version: 1.5.1
15:31:27  python version: 3.9.7
15:31:27  python path: /usr/bin/python3.9
15:31:27  os info: Linux-5.10.226-214.880.amzn2.x86_64-x86_64-with-glibc2.27
15:31:27  Using profiles.yml file at /home/repl/workspace/nyc_yellow_taxi/profiles.yml
15:31:27  Using dbt_project.yml file at /home/repl/workspace/nyc_yellow_taxi/dbt_project.yml
15:31:27  Configuration:
15:31:27    profiles.yml file [OK found and valid]
15:31:27    dbt_project.yml file [OK found and valid]
15:31:27  Required dependencies:
15:31:27   - git [OK found]

15:31:27  Connection:
15:31:27    database: dbt
15:31:27    schema: main
15:31:27    path: dbt.duckdb
15:31:27    Connection test: [OK connection ok]

15:31:27  All checks passed!
```

A workflow for dbt depends somewhat on the user's needs, but typically follows as First, create the project using dbt init (or copy a working project from another location) Next, define or update its configuration in the profiles.yml file. We've already done these steps. The next step is where you'll spend most of your time developing with dbt; defining and using data models. We'll go over what a model represents soon. For now, think of it as the transformed version(s) of your raw data stored within the data warehouse. Models need to be executed using the dbt run subcommand. This command takes the source SQL code you've written, translates it as necessary for your deployment target (aka, profile), and executes the transformation process. Once complete, you'll need to verify and test your data and, if necessary, troubleshoot any issues. Finally, this process is repeated as necessary, typically going back to the model level when a new data source is required.

<img width="1026" height="392" alt="image" src="https://github.com/user-attachments/assets/5f50ac97-e1ab-44a6-81d4-a83cfec90260" />

`dbt run` is the subcommand that performs the data transformations and pushes updates to the warehouse. It should be executed whenever there are model changes, or when the data process needs to be materialized. Make sure to analyze the output of the dbt run command - it provides many details on the success or failures of each step in the dbt process. Please note that materialized has a specific meaning in dbt. It means to execute the transformations on the source data and place the results into tables or views. Finally we see an example of dbt run and some of its output. The output will vary based on project but typically shows some version information and then details as it processes the models within.

<img width="1101" height="555" alt="image" src="https://github.com/user-attachments/assets/e2f1b6f2-b4c3-4d05-8837-712c836ee073" />

One thing to remember is the difference between tables and views within a database or data warehouse. There are a lot of technical implementation details, but generally, a table is an object within a database or warehouse that holds data. These objects take up space within the database depending on the size of the data inserted. The content of a table is only updated when a specific command changes said data. Views behave like a table and are queryable but hold no information. As such, they take up very little space within the database itself. A view is usually defined as a select query against another table or tables. The content in the response is generated with each query. We don't cover the implementation details here but are introducing them as dbt can create tables or views depending on the configurations you define. The actual implementation details for tables and views will depend on the database in question.

<img width="1103" height="441" alt="image" src="https://github.com/user-attachments/assets/adbe35b5-de6c-4577-a6e7-6ae78d737a3c" />

Example of python test 'datacheck' in one task:
```python
#!/usr/bin/env python3
import duckdb
con = duckdb.connect('dbt.duckdb', read_only=True)
print(con.sql('select * from taxi_rides_raw limit 10'))
print(con.sql('select count(*) as total_rides from taxi_rides_raw'))
if (con.execute('select count(*) as total_rides from taxi_rides_raw').fetchall()[0][0] == 300000):
  with open('/home/repl/workspace/successful_data_check', 'w') as f:
    f.write('300000')
```
running by ./datacheck

<img width="984" height="458" alt="image" src="https://github.com/user-attachments/assets/8c363412-eb1c-4a6e-914b-1886b4a5fecf" />

Let's now discuss the idea of a dbt model, what it is, and how it's used within dbt.

Before getting into how dbt uses models, let's discuss the general definition of a data model. There is no hard definition of a data model—its meaning depends on the context. At its core, a data model defines the logical organization and interpretation of a dataset whether a database table, Dataframe, or so forth. This could be a group of orders, customers, or the details of earthquakes in a given region. The data model also represents how a set of data and its components relate to each other. For example, various features of an animal, including number of legs, does it fly, etc, and how that information is maintained within the dataset. A primary purpose of a data model is to help users collaborate and understand the data in a common way.

<img width="927" height="307" alt="image" src="https://github.com/user-attachments/assets/71c776d9-d681-4687-9b68-8039caa0fced" />

A model in dbt represents something more specific than a basic data model - it represents the various transformations performed on the raw source datasets. These transformations are typically written in SQL, though newer versions of dbt can use Python for models / transformations. We won't be covering Python models in this course. Each model contains a SELECT query, transforming the source data as desired. These queries are saved in a text file, with a .sql extension. dbt automatically uses these files when tasked with operations, such as dbt run.

<img width="1090" height="373" alt="image" src="https://github.com/user-attachments/assets/7367aef7-1433-46ba-90e6-22291721de3b" />

Let's discuss the basics of creating a model in dbt. First, we create a directory under the models directory of your dbt project. This directory can be named anything, but may be referenced later, so it's best to keep it consistent. Next, a dot sql file is created as a text file. This can be done at the command line with a tool like touch, or via a text editor. We add the appropriate SQL statement to the text file. In this case, we select the first_name and last_name columns from the table source_table. Finally, execute `dbt run` to materialize the model.

<img width="1110" height="462" alt="image" src="https://github.com/user-attachments/assets/2819e791-3abe-4457-bb6b-fb2ac2a04a71" />

Before continuing, let's discuss the Parquet format. Parquet is a columnar, binary format used to efficiently store data. It is widespread for sharing and distributing datasets. Columnar is in contrast to row-based formats like database tables. DuckDB can read Parquet files, without needing to import the data first. This is done using the read_parquet function in a SQL query. For example, SELECT * FROM read_parquet filename.parquet. You can also reference the Parquet file directly using single quotes.

<img width="1089" height="389" alt="image" src="https://github.com/user-attachments/assets/358a5866-fee2-4533-9f8f-57a9f62a19ba" />

As we've discussed why you'd need to update your models, let's look at a potential workflow used when updating a dbt project. The first step is checking out a dbt project from your source control system, such as git. An example would be git clone dbt_project then opening the dbt_project folder. Git isn't required for dbt, but it is advantageous doing so as you can easily track changes / updates / modifications. Once you have the current project source, you'll find the appropriate model file in question and update the query contents. This could be updating the query directly, creating a subquery, or otherwise modifying the .sql file contents. After updating the models, you'll need to apply these changes to the project. This is often done by executing dbt run. Occasionally, larger changes need a full refresh of the model, which can be done by adding dash-f to the dbt run command. If you see an error in your update or the results don't appear as expected, you can try the full refresh option. Depending on your data and models, it might take longer to run than a simple update. Finally, once updates have been made and verified to work, you'll check the changes into source control to keep the process easy in the future.

<img width="1080" height="488" alt="image" src="https://github.com/user-attachments/assets/0c6453b3-4629-49e8-934c-2c38591514f7" />

In addition to directly updating .sql files for dbt models, you can also make changes in some YAML / .yml files. Typically these updates would be in two types of files, either the dbt_project.yml file or a model_properties.yml file.

<img width="1108" height="556" alt="image" src="https://github.com/user-attachments/assets/440a4bd7-bb38-4f85-b264-092c7e9fd93b" />

The dbt_project.yml file contains settings that relate to the full project. This includes items such as the project name, version, and directory locations. The materialization settings for a model can also reside here, though settings in this file are applied globally. These include whether models are created as tables / views / etc in the data warehouse. Note that there is one dbt_project.yml file per project.

<img width="936" height="353" alt="image" src="https://github.com/user-attachments/assets/1ce0ff67-abbb-4c36-b3d6-9500f06ae750" />

The model_properties.yml file is specific to settings for model information. This includes description, documentation details, and much more. Refer to the dbt documentation for more information. One interesting note is the file can actually be named anything as long as it exists somewhere in the models/ subdirectory and ends in a .yml extension. You can have as many of these .yml files as needed.

<img width="1094" height="381" alt="image" src="https://github.com/user-attachments/assets/bc38c277-5822-4da4-ac80-64849a73e11f" />

Another example of `./datacheck` test

```python
#!/usr/bin/env python3
import duckdb
con = duckdb.connect('dbt.duckdb', read_only=True)
print(con.sql('select * from total_creditcard_riders_by_day'))
if (con.execute('select * as total_rides from total_creditcard_riders_by_day').fetchall()[0][1] == 54743):
  with open('/home/repl/workspace/successful_data_check', 'w') as f:
    f.write('54743')
```

To actually generate the documentation, dbt provides a subcommand, dbt docs. The dbt docs subcommand has a few subcommands of its own. This includes the help option, dbt docs -h, which gives a description of the commands available for dbt docs. Let's talk about the primary one, dbt docs generate. This will traverse the content of our project, automatically creating the documentation website and formatting it into a static website. Given this documentation will update as we add models, tests, and so on, we should run this command after generating the project with dbt run. 

<img width="1153" height="362" alt="image" src="https://github.com/user-attachments/assets/25bbf44a-d53b-4101-910e-db0d396992d4" />

To access the generated documentation, we'll need a web browser and the documentation to be hosted somewhere. There are several options for hosting the documentation depending on our needs. These can include using the other subcommand for dbt docs, the dbt docs serve subcommand. This starts a webserver on the local system and provides access to the documentation. Note that while convenient, this should only be used locally during development as it is not designed with security in mind. The other option for hosting the documentation is using another hosting service. This can include dbt cloud, Amazon's S3, any modern web server including Nginx, Apache, and so forth. 

<img width="1152" height="582" alt="image" src="https://github.com/user-attachments/assets/642b2598-2853-4e78-a875-fd7c17cb480a" />

<img width="1172" height="483" alt="image" src="https://github.com/user-attachments/assets/39b00e19-c206-4b1b-aba5-bd3de29e8bf4" />

We're going to soon talk about hierarchical models in dbt, but first we must discuss a templating language called Jinja. We're going to use Jinja to simplify the creation of our dbt models and other objects. 

So what is a template? While the word has many uses, for our purposes it's easiest to define a template as a defined format that allows dbt to substitute information automatically. Most often, templates are simply text files that can be modified in most editors. We'll go over the details more in a moment, but a template is designed to simplify access and re-use. 

We'll be using a specific templating language with dbt - one called Jinja. If you're not familiar with it, Jinja is a simple text-based templating system used in many tools beyond just dbt, such as Django and Flask. To define a Jinja template, simply put the desired content between two opening and closing curly braces within your text files. When dbt is run, it will replace the contents of the braces with the correct result. The dbt tool has many Jinja functions available for use in projects. This allows for more dynamic usage of dbt, such as with different source and destination data locations. In addition, Jinja also supports using for loops to simplify coding. 

<img width="1044" height="467" alt="image" src="https://github.com/user-attachments/assets/5319946b-e7fc-42b4-8eb3-def80568d4e9" />

There are many Jinja functions in dbt. This includes ref, which you'll use in the next lesson, to access models by name. The config command is an easy way to access config settings, and the docs command allows access to various documentation content. There are many other Jinja templates made available for dbt projects, including mathematical calculations and loop structures. 

<img width="1111" height="331" alt="image" src="https://github.com/user-attachments/assets/c6fb1e2f-6ffc-4f18-b059-9ac5985684ae" />

Let's consider a quick example illustrating some Jinja basics. Let's first look at a query written directly in SQL. 
You can see that we're looking for three different columns: start_date, update_date, and end_date. We wrap each of these with a COALESCE statement, give a default date, and rename it to the intended column name. You'll notice that we have a lot of repetition in the code with only the column name changing. Let's now look at using Jinja and a for loop to recreate this query. We still have the SELECT and FROM statements, but you'll notice that the actual columns are no longer present. We construct a for loop where we iterate through the list of column names and substitute them where you see the column variables in the COALESCE statement. This effectively generates the same query as above. 

<img width="1156" height="578" alt="image" src="https://github.com/user-attachments/assets/6c889657-d79c-4f87-9712-5b11157ef8af" />

An example:

```sql
select
{% for column_name in ['fare_amount', 'tip_amount', 'tolls_amount', 'total_amount'] %}
  {{column_name}}{% if not loop.last %},{% endif %}
{% endfor %}
from taxi_rides_raw
```

First, what is a hierarchy in dbt? A hierarchy represents the dependencies within a dbt project, meaning the relationship between source and transformed data. This is also known as a DAG, or a directed acyclic graph. It's sometimes known as a lineage graph. Note that while a DAG is a common concept in data engineering tools, such as Spark or Airflow, we're referring to a DAG specifically as implemented in dbt. The primary purpose of a DAG or hierarchy is it allows models to be built and updated with their dependencies in mind. dbt must determine the order that models be built and run accordingly. 

<img width="1145" height="395" alt="image" src="https://github.com/user-attachments/assets/7536c7fd-73b9-43e7-ae13-51d638c2f5a9" />

Here, avg_fare_per_day and total_creditcard_riders_per_day are two tables that, in turn, depend on the taxi_rides_raw table. Knowing this hierarchy, dbt will build the taxi_rides_raw table first to make certain the data is available to build the other downstream tables. Without the lineage graph - or this hierarchy -, the tables would be built in alphabetical order, which would fail when attempting to build the avg_fare_per_day model as taxi_rides_raw would not yet be built. 

<img width="1152" height="430" alt="image" src="https://github.com/user-attachments/assets/79b8e132-9873-4694-9031-bbb2855d7f36" />

The next question is how are hierarchies defined in dbt? We can use the Jinja template language to define the model dependencies. This is done within the model definition file, meaning the .sql file. Most often, we define the hierarchies using the ref function within a Jinja template. To actually define a dependency, we simply replace the table name in our query with two opening curly braces, then ref open parenthesis single quote model name end quote close parenthesis, followed by two closing braces in our SQL query. The next step is to use dbt run, which will materialize the models. dbt will replace the ref templates with the actual table names in the generated SQL file. 

<img width="1051" height="428" alt="image" src="https://github.com/user-attachments/assets/2808fc2e-15a4-44f0-833e-6c1ef27f8961" />

A quick example illustrates the change - in the first query, we're directly using the name of the table. While this works, we may run into issues if the table is not created yet. To add the dependency, you'll notice we use Jinja to change the table name from taxi_rides_raw to {{ ref('taxi_rides_raw') }}. 

<img width="1155" height="227" alt="image" src="https://github.com/user-attachments/assets/868ea3f0-965d-4524-868a-2c3d2848f9bc" />



```python
-- Update SQL to use Jinja reference
select 
   date_part('day', tpep_pickup_datetime) as day,
   count(*) as total_riders
-- Update the line below to use a Jinja function
from taxi_rides_raw
where payment_type = 1
group by day


repl:~/workspace/nyc_yellow_taxi$ dbt run
17:51:12  Running with dbt=1.5.1
17:51:12  Unable to do partial parsing because saved manifest not found. Starting full parse.
17:51:13  Found 2 models, 0 tests, 0 snapshots, 0 analyses, 313 macros, 0 operations, 0 seed files, 0 sources, 0 exposures, 0 metrics, 0 groups
17:51:13  
17:51:13  Concurrency: 1 threads (target='dev')
17:51:13  
17:51:13  1 of 2 START sql view model main.creditcard_riders_by_day ...................... [RUN]
17:51:13  1 of 2 ERROR creating sql view model main.creditcard_riders_by_day ............. [ERROR in 0.07s]
17:51:13  2 of 2 START sql view model main.taxi_rides_raw ................................ [RUN]
17:51:13  2 of 2 OK created sql view model main.taxi_rides_raw ........................... [OK in 0.07s]
17:51:13  
17:51:13  Finished running 2 view models in 0 hours 0 minutes and 0.23 seconds (0.23s).
17:51:13  
17:51:13  Completed with 1 error and 0 warnings:
17:51:13  
17:51:13  Runtime Error in model creditcard_riders_by_day (models/taxi_rides/creditcard_riders_by_day.sql)
17:51:13    Catalog Error: Table with name taxi_rides_raw does not exist!
17:51:13    Did you mean "temp.information_schema.tables"?
17:51:13  
17:51:13  Done. PASS=1 WARN=0 ERROR=1 SKIP=0 TOTAL=2

##Made changes
-- Update SQL to use Jinja reference
select 
   date_part('day', tpep_pickup_datetime) as day,
   count(*) as total_riders
-- Update the line below to use a Jinja function
from {{ ref('taxi_rides_raw') }}
where payment_type = 1
group by day

repl:~/workspace/nyc_yellow_taxi$ dbt run -f
17:54:04  Running with dbt=1.5.1
17:54:04  Found 2 models, 0 tests, 0 snapshots, 0 analyses, 313 macros, 0 operations, 0 seed files, 0 sources, 0 exposures, 0 metrics, 0 groups
17:54:04  
17:54:04  Concurrency: 1 threads (target='dev')
17:54:04  
17:54:04  1 of 2 START sql view model main.taxi_rides_raw ................................ [RUN]
17:54:04  1 of 2 OK created sql view model main.taxi_rides_raw ........................... [OK in 0.14s]
17:54:04  2 of 2 START sql view model main.creditcard_riders_by_day ...................... [RUN]
17:54:04  2 of 2 OK created sql view model main.creditcard_riders_by_day ................. [OK in 0.05s]
17:54:04  
17:54:04  Finished running 2 view models in 0 hours 0 minutes and 0.28 seconds (0.28s).
17:54:04  
17:54:04  Completed successfully
17:54:04  
17:54:04  Done. PASS=2 WARN=0 ERROR=0 SKIP=0 TOTAL=2
repl:~/workspace/nyc_yellow_taxi$ 
```

# Intermediate dbt

------------------------

We're going to first discuss testing in dbt and what that entails. Let's get started! 

What is a test? In dbt, a test is an assertion or validation of various dbt objects. This includes models, which we introduced in the Introductory dbt course. It can also apply to other dbt objects such as sources and seeds, which we'll discuss later. Tests are used to verify our data is as expected. This includes tests for null values, verifying the values are in range, or the relationships between data. We can also create custom tests for validating specific logic. 

<img width="971" height="444" alt="image" src="https://github.com/user-attachments/assets/64828399-c513-46fc-b442-8dbc1a9d4932" />

There are three kinds of tests in dbt. The first is built-in, which are 4 pre-defined tests available for use. We'll cover these further in a moment. The other two types are singular and generic. We'll cover those later. 

<img width="925" height="389" alt="image" src="https://github.com/user-attachments/assets/35dafb39-fb6f-4d75-a524-4919e4d113d6" />

dbt's four built-in tests are: Unique, which verifies all values in a column are unique. not_null, which verifies all values in a column are not null. accepted_values verifies all values are within a specific list. These values are listed in a values: option. relationships, which also takes a to: and field: option. It verifies connection of an object to a specific table or column.

<img width="1149" height="444" alt="image" src="https://github.com/user-attachments/assets/ac943420-5454-40dd-9f50-645e42a9933c" />

Model tests are defined in a YAML file within the models directory - other tests are defined in their respective directories. We will name this file model_properties.yml. This .yml file can be named differently based on your preferences. The actual tests are defined under the tests subheading, under the column name option within the YAML. Let's consider an example defining tests on two columns of the taxi_rides_raw model. The tpep_pickup_datetime has a not_null test. The payment_type column has a not_null and an accepted values test. We're verifying the values are between 1 and 6. 

<img width="1153" height="575" alt="image" src="https://github.com/user-attachments/assets/2986096b-b6cd-4ead-905d-e1c058232cee" />

To run tests in dbt, use `dbt test` for the entire project or `dbt test --select modelname` to test a specific model, e.g., `dbt test --select customers`. The command output indicates which tests pass or fail. Note to find why a test fails, we need a few more steps. 

<img width="1132" height="487" alt="image" src="https://github.com/user-attachments/assets/a6107c69-8eb5-4735-a52f-4f21edcb96f9" />

To find the specific issues in our data, we need to use the compiled SQL code. This normally resides in the target/compiled/projectname/models/model_properties.yml directory. For our example, it's the target/compiled/nyc_yellow_taxi/models/model_properties.yml/ directory. Find the .sql file that matches the failed test or tests. Copy the contents into your database client and check how many rows exist with the issue. You can manually remove the data or update your model scripts to handle the issue— the latter is usually more sustainable. Afterward, rerun dbt run and dbt test to confirm the fix. 

<img width="1134" height="359" alt="image" src="https://github.com/user-attachments/assets/be71304a-7792-4f5f-afa8-c922ed2209e0" />

## Exercise: Defining tests on a model

After learning about tests within dbt, your manager has asked you to implement some quality tests on the data used by the marketing department. It seems some entries are appearing without values, while others have a value, but do not match up with what's expected in the data.

Specifically, the issues with the columns are as follows:

```python
    payment_type
        Should not be null.
        Column values need to be between 1 and 6.
```

    Update the model_properties.yml file below to include the two appropriate tests for the payment_type column.
    Generate your models with dbt run.
    Test your data with the appropriate command.

## Solution

```yaml
#model_properties.yml file

version: 2

models:
- name: taxi_rides_raw
  columns:
    - name: fare_amount
      tests:
        - not_null
    # Enter the name of the column
    - name: payment_type
    # Define the two tests
      tests:
        - not_null
        - accepted_values:
            values: [1, 2, 3, 4, 5, 6]
```

```python
repl:~/workspace/nyc_yellow_taxi$ dbt run
16:36:46  Running with dbt=1.9.4
16:36:47  Registered adapter: duckdb=1.9.3
16:36:47  Unable to do partial parsing because saved manifest not found. Starting full parse.
16:36:50  [WARNING]: Configuration paths exist in your dbt_project.yml file which do not apply to any resources.
There are 1 unused configuration paths:
- models.nyc_yellow_taxi
16:36:50  Found 1 model, 3 data tests, 428 macros
16:36:50  
16:36:50  Concurrency: 1 threads (target='dev')
16:36:50  
16:36:50  1 of 1 START sql view model main.taxi_rides_raw ................................ [RUN]
16:36:50  1 of 1 OK created sql view model main.taxi_rides_raw ........................... [OK in 0.15s]
16:36:50  
16:36:50  Finished running 1 view model in 0 hours 0 minutes and 0.56 seconds (0.56s).
16:36:50  
16:36:50  Completed successfully
16:36:50  
16:36:50  Done. PASS=1 WARN=0 ERROR=0 SKIP=0 TOTAL=1
repl:~/workspace/nyc_yellow_taxi$ dbt test
16:37:37  Running with dbt=1.9.4
16:37:38  Registered adapter: duckdb=1.9.3
16:37:38  [WARNING]: Configuration paths exist in your dbt_project.yml file which do not apply to any resources.
There are 1 unused configuration paths:
- models.nyc_yellow_taxi
16:37:39  Found 1 model, 3 data tests, 428 macros
16:37:39  
16:37:39  Concurrency: 1 threads (target='dev')
16:37:39  
16:37:39  1 of 3 START test accepted_values_taxi_rides_raw_payment_type__1__2__3__4__5__6  [RUN]
16:37:39  1 of 3 PASS accepted_values_taxi_rides_raw_payment_type__1__2__3__4__5__6 ...... [PASS in 0.09s]
16:37:39  2 of 3 START test not_null_taxi_rides_raw_fare_amount .......................... [RUN]
16:37:39  2 of 3 PASS not_null_taxi_rides_raw_fare_amount ................................ [PASS in 0.05s]
16:37:39  3 of 3 START test not_null_taxi_rides_raw_payment_type ......................... [RUN]
16:37:39  3 of 3 PASS not_null_taxi_rides_raw_payment_type ............................... [PASS in 0.02s]
16:37:39  
16:37:39  Finished running 3 data tests in 0 hours 0 minutes and 0.35 seconds (0.35s).
16:37:39  
16:37:39  Completed successfully
16:37:39  
16:37:39  Done. PASS=3 WARN=0 ERROR=0 SKIP=0 TOTAL=3
repl:~/workspace/nyc_yellow_taxi$ 
```
