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
