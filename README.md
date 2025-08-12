
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

```shell
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
