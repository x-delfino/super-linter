# Super-Linter

Super-linter is a ready-to-run collection of linters and code analyzers, to
help validate your source code.

The goal of super-linter is to help you establish best practices and consistent
formatting across multiple programming languages, and ensure developers are
adhering to those conventions.

Super-linter analyzes source code files using several tools, and reports the
issues that those tools find as console output, and as
[GitHub Actions status checks](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/collaborating-on-repositories-with-code-quality-features/about-status-checks).
You can also [run super-linter outside GitHub Actions](#run-super-linter-outside-github-actions).

Super-linter is licensed under a
[MIT License](https://github.com/super-linter/super-linter/blob/main/LICENSE).

[![Super-Linter](https://github.com/super-linter/super-linter/actions/workflows/cd.yml/badge.svg)](https://github.com/marketplace/actions/super-linter)

Here are some notable Super-linter features:

- **MIT License**: Super-linter is licensed under a [MIT License](LICENSE).
- **Independent project**: Super-linter is maintained by a team of independent
  developers and is not commercially backed by any entity that might influence
  the course of the project.
- **Widely used**: Super-linter is the
  [most widely used](https://github.com/super-linter/super-linter/network/dependents)
  and [forked](https://github.com/super-linter/super-linter/forks) project of
  this kind.
- **Runs linters in parallel**: Since `v6`, Super-linter parallelizes
  running all the included linters, leading to scanning massive code
  repositories in seconds.
- **Highly curated set of linters**: Avoid including linters that implement
  overlapping checks, reducing bloat, scanning times, and container image size.
- **Run on GitHub Actions or other environments**: Super-linter runs
  [on GitHub Actions](#get-started) and
  [other runtime environments](#run-using-a-container-runtime-engine), with the
  only dependency of an OCI-compatible container runtime engine, such as Docker.
- **Lean codebase**: Super-linter doesn't reinvent the wheel, and builds on top
  of established tools and standards, such as
  [GNU Parallel](https://www.gnu.org/software/parallel/).
- **Extensive test suite**: Super-linter includes and extensive test suite that
  covers every single linter and analyzer that Super-linter ships.
- **Original design**: to the best of our knowledge, Super-linter is the first
  open-source, fully-containerized linting suite. Other projects borrow ideas
  and design choices from Super-linter (and we're cool with that :).

## Supported linters and code analyzers

Super-linter supports the following tools:

| _Language_                       | _Linter_                                                                                                                                                                                                                |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Ansible**                      | [ansible-lint](https://github.com/ansible/ansible-lint)                                                                                                                                                                 |
| **AWS CloudFormation templates** | [cfn-lint](https://github.com/aws-cloudformation/cfn-python-lint/)                                                                                                                                                      |
| **Azure Resource Manager (ARM)** | [arm-ttk](https://github.com/azure/arm-ttk)                                                                                                                                                                             |
| **C++**                          | [cpp-lint](https://github.com/cpplint/cpplint) / [clang-format](https://clang.llvm.org/docs/ClangFormatStyleOptions.html)                                                                                               |
| **C#**                           | [dotnet format](https://github.com/dotnet/format) / [clang-format](https://clang.llvm.org/docs/ClangFormatStyleOptions.html)                                                                                            |
| **CSS**                          | [stylelint](https://stylelint.io/)                                                                                                                                                                                      |
| **Clojure**                      | [clj-kondo](https://github.com/borkdude/clj-kondo)                                                                                                                                                                      |
| **CoffeeScript**                 | [coffeelint](https://coffeelint.github.io/)                                                                                                                                                                             |
| **Copy/paste detection**         | [jscpd](https://github.com/kucherenko/jscpd)                                                                                                                                                                            |
| **Dart**                         | [dartanalyzer](https://dart.dev/guides/language/analysis-options)                                                                                                                                                       |
| **Dockerfile**                   | [hadolint](https://github.com/hadolint/hadolint)                                                                                                                                                                        |
| **EditorConfig**                 | [editorconfig-checker](https://github.com/editorconfig-checker/editorconfig-checker)                                                                                                                                    |
| **ENV**                          | [dotenv-linter](https://github.com/dotenv-linter/dotenv-linter)                                                                                                                                                         |
| **Gherkin**                      | [gherkin-lint](https://github.com/vsiakka/gherkin-lint)                                                                                                                                                                 |
| **GitHub Actions**               | [actionlint](https://github.com/rhysd/actionlint)                                                                                                                                                                       |
| **Golang**                       | [golangci-lint](https://github.com/golangci/golangci-lint)                                                                                                                                                              |
| **GoReleaser**                   | [GoReleaser](https://github.com/goreleaser/goreleaser)                                                                                                                                                                       |
| **Groovy**                       | [npm-groovy-lint](https://github.com/nvuillam/npm-groovy-lint)                                                                                                                                                          |
| **HTML**                         | [HTMLHint](https://github.com/htmlhint/HTMLHint)                                                                                                                                                                        |
| **Java**                         | [checkstyle](https://checkstyle.org) / [google-java-format](https://github.com/google/google-java-format)                                                                                                               |
| **JavaScript**                   | [ESLint](https://eslint.org/) / [standard js](https://standardjs.com/)                                                                                                                                                  |
| **JSON**                         | [eslint-plugin-json](https://www.npmjs.com/package/eslint-plugin-json)                                                                                                                                                  |
| **JSONC**                        | [eslint-plugin-jsonc](https://www.npmjs.com/package/eslint-plugin-jsonc)                                                                                                                                                |
| Infrastructure as code           | [Checkov](https://www.checkov.io/)                                                                                                                                                                                      |
| **Kubernetes**                   | [kubeconform](https://github.com/yannh/kubeconform)                                                                                                                                                                     |
| **Kotlin**                       | [ktlint](https://github.com/pinterest/ktlint)                                                                                                                                                                           |
| **LaTeX**                        | [ChkTex](https://www.nongnu.org/chktex/)                                                                                                                                                                                |
| **Lua**                          | [luacheck](https://github.com/luarocks/luacheck)                                                                                                                                                                        |
| **Markdown**                     | [markdownlint](https://github.com/igorshubovych/markdownlint-cli#readme)                                                                                                                                                |
| **Natural language**             | [textlint](https://textlint.github.io/)                                                                                                                                                                                 |
| **OpenAPI**                      | [spectral](https://github.com/stoplightio/spectral)                                                                                                                                                                     |
| **Perl**                         | [perlcritic](https://metacpan.org/pod/Perl::Critic)                                                                                                                                                                     |
| **PHP**                          | [PHP built-in linter](https://www.php.net/manual/en/features.commandline.options.php) / [PHP CodeSniffer](https://github.com/PHPCSStandards/PHP_CodeSniffer) / [PHPStan](https://phpstan.org/) / [Psalm](https://psalm.dev/) |
| **PowerShell**                   | [PSScriptAnalyzer](https://github.com/PowerShell/Psscriptanalyzer)                                                                                                                                                      |
| **Protocol Buffers**             | [protolint](https://github.com/yoheimuta/protolint)                                                                                                                                                                     |
| **Python3**                      | [pylint](https://pylint.pycqa.org/) / [flake8](https://flake8.pycqa.org/en/latest/) / [black](https://github.com/psf/black) / [isort](https://pypi.org/project/isort/) / [ruff](https://github.com/astral-sh/ruff)                                                 |
| **R**                            | [lintr](https://github.com/jimhester/lintr)                                                                                                                                                                             |
| **Raku**                         | [Raku](https://raku.org)                                                                                                                                                                                                |
| **Renovate**                     | [renovate-config-validator](https://docs.renovatebot.com/config-validation/)                                                                                                                                            |
| **Ruby**                         | [RuboCop](https://github.com/rubocop-hq/rubocop)                                                                                                                                                                        |
| **Rust**                         | [Rustfmt](https://github.com/rust-lang/rustfmt) / [Clippy](https://github.com/rust-lang/rust-clippy)                                                                                                                    |
| **Scala**                        | [scalafmt](https://github.com/scalameta/scalafmt)                                                                                                                                                                       |
| **Secrets**                      | [GitLeaks](https://github.com/zricethezav/gitleaks)                                                                                                                                                                     |
| **Shell**                        | [ShellCheck](https://github.com/koalaman/shellcheck) / `executable bit check` / [shfmt](https://github.com/mvdan/sh)                                                                                                    |
| **Snakemake**                    | [snakefmt](https://github.com/snakemake/snakefmt/) / [snakemake --lint](https://snakemake.readthedocs.io/en/stable/snakefiles/writing_snakefiles.html#best-practices)                                                   |
| **SQL**                          | [sql-lint](https://github.com/joereynolds/sql-lint) / [sqlfluff](https://github.com/sqlfluff/sqlfluff)                                                                                                                  |
| **Tekton**                       | [tekton-lint](https://github.com/IBM/tekton-lint)                                                                                                                                                                       |
| **Terraform**                    | [fmt](https://developer.hashicorp.com/terraform/cli/commands/fmt) / [tflint](https://github.com/terraform-linters/tflint) / [terrascan](https://github.com/accurics/terrascan)                                          |
| **Terragrunt**                   | [terragrunt](https://github.com/gruntwork-io/terragrunt)                                                                                                                                                                |
| **TypeScript**                   | [ESLint](https://eslint.org/) / [standard js](https://standardjs.com/)                                                                                                                                                  |
| **XML**                          | [LibXML](http://xmlsoft.org/)                                                                                                                                                                                           |
| **YAML**                         | [YamlLint](https://github.com/adrienverge/yamllint)                                                                                                                                                                     |

## Get started

More in-depth [tutorial](https://www.youtube.com/watch?v=EDAmFKO4Zt0&t=118s) available

To run super-linter as a GitHub Action, you do the following:

1. Create a new [GitHub Actions workflow](https://docs.github.com/en/actions/using-workflows/about-workflows#about-workflows) in your repository with the following content:

    ```yaml
    ---
    name: Lint

    on:  # yamllint disable-line rule:truthy
      push: null
      pull_request: null

    permissions: { }

    jobs:
      build:
        name: Lint
        runs-on: ubuntu-latest

        permissions:
          contents: read
          packages: read
          # To report GitHub Actions status checks
          statuses: write

        steps:
          - name: Checkout code
            uses: actions/checkout@v4
            with:
              # super-linter needs the full git history to get the
              # list of files that changed across commits
              fetch-depth: 0

          - name: Super-linter
            uses: super-linter/super-linter@v6.5.1  # x-release-please-version
            env:
              # To report GitHub Actions status checks
              GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
    ...
    ```

1. Commit that file to a new branch.
1. Push the new commit to the remote repository.
1. Create a new pull request to observe the results.

## Upgrade to newer super-linter versions

For more information about upgrading super-linter to a new major version, see
the [upgrade guide](docs/upgrade-guide.md).

## Add Super-Linter badge in your repository README

You can show Super-Linter status with a badge in your repository README:

Example:

```markdown
[![Super-Linter](https://github.com/<OWNER>/<REPOSITORY>/actions/workflows/<WORKFLOW_FILE_NAME>/badge.svg)](https://github.com/marketplace/actions/super-linter)
```

For more information, see
[Adding a workflow status badge](https://docs.github.com/en/actions/monitoring-and-troubleshooting-workflows/adding-a-workflow-status-badge).

## Super-linter variants

Super-Linter provides several variants:

- `standard`: `super-linter/super-linter@[VERSION]`: includes all supported linters.
- `slim`: `super-linter/super-linter/slim@[VERSION]`: includes all supported linters except:

  - `rust` linters
  - `dotenv` linters
  - `armttk` linters
  - `pwsh` linters
  - `c#` linters

## Configure super-linter

You can configure super-linter using the following environment variables:

| **Environment variable**                        | **Default Value**               | **Description**                                                                                                                                                                                                      |
|-------------------------------------------------|---------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **ANSIBLE_CONFIG_FILE**                         | `.ansible-lint.yml`             | Filename for [Ansible-lint configuration](https://ansible.readthedocs.io/projects/lint/configuring/) (ex: `.ansible-lint`, `.ansible-lint.yml`)                                                                      |
| **ANSIBLE_DIRECTORY**                           | `/ansible`                      | Flag to set the root directory for Ansible file location(s), relative to `DEFAULT_WORKSPACE`. Set to `.` to use the top-level of the `DEFAULT_WORKSPACE`.                                                            |
| **BASH_EXEC_IGNORE_LIBRARIES**                  | `false`                         | If set to `true`, shell files with a file extension and no shebang line are ignored when checking if the executable bit is set.                                                                                      |
| **BASH_FILE_NAME**                              | `.shellcheckrc`                 | Filename for [Shellcheck](https://github.com/koalaman/shellcheck/blob/master/shellcheck.1.md#rc-files)                                                                                                               |
| **BASH_SEVERITY**                               | `style`                         | Specify the minimum severity of errors to consider in shellcheck. Valid values in order of severity are error, warning, info and style.                                                                              |
| **CHECKOV_FILE_NAME**                           | `.checkov.yaml`                 | Configuration filename for Checkov.                                                                                                                                                                                  |
| **CLANG_FORMAT_FILE_NAME**                      | `.clang-format`                 | Configuration filename for [clang-format](https://clang.llvm.org/docs/ClangFormatStyleOptions.html).                                                                                                                 |
| **CREATE_LOG_FILE**                             | `false`                         | If set to `true`, it creates the log file. You can set the log filename using the `LOG_FILE` environment variable. This overrides any existing log files.                                                            |
| **CSS_FILE_NAME**                               | `.stylelintrc.json`             | Filename for [Stylelint configuration](https://github.com/stylelint/stylelint) (ex: `.stylelintrc.yml`, `.stylelintrc.yaml`)                                                                                         |
| **DEFAULT_BRANCH**                              | Default repository branch when running on GitHub Actions, `master` otherwise | The name of the repository default branch. There's no need to configure this variable when running on GitHub Actions                                                    |
| **DEFAULT_WORKSPACE**                           | `/tmp/lint`                     | The location containing files to lint if you are running locally. Defaults to `GITHUB_WORKSPACE` when running in GitHub Actions. There's no need to configure this variable when running on GitHub Actions.          |
| **DISABLE_ERRORS**                              | `false`                         | Flag to have the linter complete with exit code 0 even if errors were detected.                                                                                                                                      |
| **DOCKERFILE_HADOLINT_FILE_NAME**               | `.hadolint.yaml`                | Filename for [hadolint configuration](https://github.com/hadolint/hadolint) (ex: `.hadolintlintrc.yaml`)                                                                                                             |
| **EDITORCONFIG_FILE_NAME**                      | `.ecrc`                         | Filename for [editorconfig-checker configuration](https://github.com/editorconfig-checker/editorconfig-checker)                                                                                                      |
| **ENABLE_GITHUB_ACTIONS_GROUP_TITLE**           | `false` if `RUN_LOCAL=true`, `true` otherwise | Flag to enable [GitHub Actions log grouping](https://docs.github.com/en/actions/using-workflows/workflow-commands-for-github-actions#grouping-log-lines).                                              |
| **FILTER_REGEX_EXCLUDE**                        | not set                         | Regular expression defining which files will be excluded from linting  (ex: `.*src/test.*`). Not setting this variable means to process all files.                                                                   |
| **FILTER_REGEX_INCLUDE**                        | not set                         | Regular expression defining which files will be processed by linters (ex: `.*src/.*`). Not setting this variable means to process all files. `FILTER_REGEX_INCLUDE` is evaluated before `FILTER_REGEX_EXCLUDE`.      |
| **GITHUB_ACTIONS_CONFIG_FILE**                  | `actionlint.yml`                | Filename for [Actionlint configuration](https://github.com/rhysd/actionlint/blob/main/docs/config.md) (ex: `actionlint.yml`)                                                                                         |
| **GITHUB_ACTIONS_COMMAND_ARGS**                 | `null`                          | Additional arguments passed to `actionlint` command. Useful to [ignore some errors](https://github.com/rhysd/actionlint/blob/main/docs/usage.md#ignore-some-errors)                                                  |
| **GITHUB_CUSTOM_API_URL**                       | `https://api.${GITHUB_DOMAIN}`  | Specify a custom GitHub API URL in case GitHub Enterprise is used: e.g. `https://github.myenterprise.com/api/v3`                                                                                                     |
| **GITHUB_DOMAIN**                               | `github.com`                    | Specify a custom GitHub domain in case GitHub Enterprise is used: e.g. `github.myenterprise.com`                                                                                                                     |
| **GITLEAKS_CONFIG_FILE**                        | `.gitleaks.toml`                | Filename for [GitLeaks configuration](https://github.com/zricethezav/gitleaks#configuration) (ex: `.gitleaks.toml`)                                                                                                  |
| **IGNORE_GENERATED_FILES**                      | `false`                         | If set to `true`, super-linter will ignore all the files with `@generated` marker but without `@not-generated` marker.                                                                                               |
| **IGNORE_GITIGNORED_FILES**                     | `false`                         | If set to `true`, super-linter will ignore all the files that are ignored by Git.                                                                                                                                    |
| **JAVA_FILE_NAME**                              | `sun_checks.xml`                | Filename for [Checkstyle configuration](https://checkstyle.sourceforge.io/config.html). Checkstyle embeds several configuration files, such as `sun_checks.xml`, `google_checks.xml` that you can use without providing your own configuration file. |
| **JAVASCRIPT_DEFAULT_STYLE**                    | `standard`                      | Flag to set the default style of JavaScript. Available options: **standard**/**prettier**                                                                                                                            |
| **JAVASCRIPT_ES_CONFIG_FILE**                   | `.eslintrc.yml`                 | Filename for [ESLint configuration](https://eslint.org/docs/user-guide/configuring#configuration-file-formats) (ex: `.eslintrc.yml`, `.eslintrc.json`)                                                               |
| **JSCPD_CONFIG_FILE**                           | `.jscpd.json`                   | Filename for JSCPD configuration                                                                                                                                                                                     |
| **KUBERNETES_KUBECONFORM_OPTIONS**              | `null`                          | Additional arguments to pass to the command-line when running **Kubernetes Kubeconform** (Example: --ignore-missing-schemas)                                                                                         |
| **LINTER_RULES_PATH**                           | `.github/linters`               | Directory for all linter configuration rules.                                                                                                                                                                        |
| **LOG_FILE**                                    | `super-linter.log`              | The filename for outputting logs. All output is sent to the log file regardless of `LOG_LEVEL`.                                                                                                                      |
| **LOG_LEVEL**                                   | `INFO`                          | How much output the script will generate to the console. One of `ERROR`, `WARN`, `NOTICE`, `INFO`, or `DEBUG`.                                                                                                       |
| **MARKDOWN_CONFIG_FILE**                        | `.markdown-lint.yml`            | Filename for [Markdownlint configuration](https://github.com/DavidAnson/markdownlint#optionsconfig) (ex: `.markdown-lint.yml`, `.markdownlint.json`, `.markdownlint.yaml`)                                           |
| **MARKDOWN_CUSTOM_RULE_GLOBS**                  | `.markdown-lint/rules,rules/**` | Comma-separated list of [file globs](https://github.com/igorshubovych/markdownlint-cli#globbing) matching [custom Markdownlint rule files](https://github.com/DavidAnson/markdownlint/blob/main/doc/CustomRules.md). |
| **MULTI_STATUS**                                | `true`                          | A status API is made for each language that is linted to make visual parsing easier.                                                                                                                                 |
| **NATURAL_LANGUAGE_CONFIG_FILE**                | `.textlintrc`                   | Filename for [textlint configuration](https://textlint.github.io/docs/getting-started.html#configuration) (ex: `.textlintrc`)                                                                                        |
| **PERL_PERLCRITIC_OPTIONS**                     | `null`                          | Additional arguments to pass to the command-line when running **perlcritic** (Example: --theme community)                                                                                                            |
| **PHP_CONFIG_FILE**                             | `php.ini`                       | Filename for [PHP Configuration](https://www.php.net/manual/en/configuration.file.php) (ex: `php.ini`)                                                                                                               |
| **PHP_PHPCS_FILE_NAME**                         | `phpcs.xml`                     | Filename for [PHP CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer) (ex: `.phpcs.xml`, `.phpcs.xml.dist`)                                                                                                   |
| **PROTOBUF_CONFIG_FILE**                        | `.protolintrc.yml`              | Filename for [protolint configuration](https://github.com/yoheimuta/protolint/blob/master/_example/config/.protolint.yaml) (ex: `.protolintrc.yml`)                                                                  |
| **PYTHON_BLACK_CONFIG_FILE**                    | `.python-black`                 | Filename for [black configuration](https://github.com/psf/black/blob/main/docs/guides/using_black_with_other_tools.md#black-compatible-configurations) (ex: `.isort.cfg`, `pyproject.toml`)                          |
| **PYTHON_FLAKE8_CONFIG_FILE**                   | `.flake8`                       | Filename for [flake8 configuration](https://flake8.pycqa.org/en/latest/user/configuration.html) (ex: `.flake8`, `tox.ini`)                                                                                           |
| **PYTHON_ISORT_CONFIG_FILE**                    | `.isort.cfg`                    | Filename for [isort configuration](https://pycqa.github.io/isort/docs/configuration/config_files.html) (ex: `.isort.cfg`, `pyproject.toml`)                                                                          |
| **PYTHON_MYPY_CONFIG_FILE**                     | `.mypy.ini`                     | Filename for [mypy configuration](https://mypy.readthedocs.io/en/stable/config_file.html) (ex: `.mypy.ini`, `setup.config`)                                                                                          |
| **PYTHON_PYLINT_CONFIG_FILE**                   | `.python-lint`                  | Filename for [pylint configuration](https://pylint.pycqa.org/en/latest/user_guide/run.html?highlight=rcfile#command-line-options) (ex: `.python-lint`, `.pylintrc`)                                                  |
| **PYTHON_RUFF_CONFIG_FILE**                     | `.ruff.toml`                    | Filename for [ruff configuration](https://docs.astral.sh/ruff/configuration/)                                                                                                                                        |
| **RENOVATE_SHAREABLE_CONFIG_PRESET_FILE_NAMES** | not set                         | Comma-separated filenames for [renovate shareable config preset](https://docs.renovatebot.com/config-presets/) (ex: `default.json`)                                                                                  |
| **RUBY_CONFIG_FILE**                            | `.ruby-lint.yml`                | Filename for [rubocop configuration](https://docs.rubocop.org/rubocop/configuration.html) (ex: `.ruby-lint.yml`, `.rubocop.yml`)                                                                                     |
| **SCALAFMT_CONFIG_FILE**                        | `.scalafmt.conf`                | Filename for [scalafmt configuration](https://scalameta.org/scalafmt/docs/configuration.html) (ex: `.scalafmt.conf`)                                                                                                 |
| **SNAKEMAKE_SNAKEFMT_CONFIG_FILE**              | `.snakefmt.toml`                | Filename for [Snakemake configuration](https://github.com/snakemake/snakefmt#configuration) (ex: `pyproject.toml`, `.snakefmt.toml`)                                                                                 |
| **SSL_CERT_SECRET**                             | `none`                          | SSL cert to add to the **Super-Linter** trust store. This is needed for users on `self-hosted` runners or need to inject the cert for security standards (ex. ${{ secrets.SSL_CERT }})                               |
| **SSH_KEY**                                     | `none`                          | SSH key that has access to your private repositories                                                                                                                                                                 |
| **SSH_SETUP_GITHUB**                            | `false`                         | If set to `true`, adds the `github.com` SSH key to `known_hosts`. This is ignored if `SSH_KEY` is provided - i.e. the `github.com` SSH key is always added if `SSH_KEY` is provided                                  |
| **SSH_INSECURE_NO_VERIFY_GITHUB_KEY**           | `false`                         | **INSECURE -** If set to `true`, does not verify the fingerprint of the github.com SSH key before adding this. This is not recommended!                                                                              |
| **SQL_CONFIG_FILE**                             | `.sql-config.json`              | Filename for [SQL-Lint configuration](https://sql-lint.readthedocs.io/en/latest/files/configuration.html) (ex: `sql-config.json` , `.config.json`)                                                                   |
| **SQLFLUFF_CONFIG_FILE**                        | `/.sqlfluff`                    | Filename for [SQLFLUFF configuration](https://docs.sqlfluff.com/en/stable/configuration.html) (ex: `/.sqlfluff`, `pyproject.toml`)                                                                                   |
| **SUPPRESS_FILE_TYPE_WARN**                     | `false`                         | If set to `true`, will hide warning messages about files without their proper extensions. Default is `false`                                                                                                         |
| **SUPPRESS_POSSUM**                             | `false`                         | If set to `true`, will hide the ASCII possum at top of log output. Default is `false`                                                                                                                                |
| **TERRAFORM_TERRASCAN_CONFIG_FILE**             | `terrascan.toml`                | Filename for [terrascan configuration](https://github.com/accurics/terrascan) (ex: `terrascan.toml`)                                                                                                                 |
| **TERRAFORM_TFLINT_CONFIG_FILE**                | `.tflint.hcl`                   | Filename for [tfLint configuration](https://github.com/terraform-linters/tflint) (ex: `.tflint.hcl`)                                                                                                                 |
| **TYPESCRIPT_DEFAULT_STYLE**                    | `ts-standard`                   | Flag to set the default style of TypeScript. Available options: **ts-standard**/**prettier**                                                                                                                         |
| **TYPESCRIPT_ES_CONFIG_FILE**                   | `.eslintrc.yml`                 | Filename for [ESLint configuration](https://eslint.org/docs/user-guide/configuring#configuration-file-formats) (ex: `.eslintrc.yml`, `.eslintrc.json`)                                                               |
| **TYPESCRIPT_STANDARD_TSCONFIG_FILE**           | `${DEFAULT_WORKSPACE}/tsconfig.json` | Path to the [TypeScript project configuration](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) in [ts-standard](https://github.com/standard/ts-standard). The path is relative to `DEFAULT_WORKSPACE` |
| **USE_FIND_ALGORITHM**                          | `false`                         | By default, we use `git diff` to find all files in the workspace and what has been updated, this would enable the Linux `find` method instead to find all files to lint                                              |
| **VALIDATE_ALL_CODEBASE**                       | `true`                          | Will parse the entire repository and find all files to validate across all types. **NOTE:** When set to `false`, only **new** or **edited** files will be parsed for validation.                                     |
| **VALIDATE_ANSIBLE**                            | `true`                          | Flag to enable or disable the linting process of the Ansible language.                                                                                                                                               |
| **VALIDATE_ARM**                                | `true`                          | Flag to enable or disable the linting process of the ARM language.                                                                                                                                                   |
| **VALIDATE_BASH**                               | `true`                          | Flag to enable or disable the linting process of the Bash language.                                                                                                                                                  |
| **VALIDATE_BASH_EXEC**                          | `true`                          | Flag to enable or disable the linting process of the Bash language to validate if file is stored as executable.                                                                                                      |
| **VALIDATE_CPP**                                | `true`                          | Flag to enable or disable the linting process of the C++ language.                                                                                                                                                   |
| **VALIDATE_CHECKOV**                            | `true`                          | Flag to enable or disable the linting process with Checkov                                                                                                                                                           |
| **VALIDATE_CLANG_FORMAT**                       | `true`                          | Flag to enable or disable the linting process of the C++/C language with clang-format.                                                                                                                               |
| **VALIDATE_CLOJURE**                            | `true`                          | Flag to enable or disable the linting process of the Clojure language.                                                                                                                                               |
| **VALIDATE_CLOUDFORMATION**                     | `true`                          | Flag to enable or disable the linting process of the AWS Cloud Formation language.                                                                                                                                   |
| **VALIDATE_COFFEESCRIPT**                       | `true`                          | Flag to enable or disable the linting process of the Coffeescript language.                                                                                                                                          |
| **VALIDATE_CSHARP**                             | `true`                          | Flag to enable or disable the linting process of the C# language.                                                                                                                                                    |
| **VALIDATE_CSS**                                | `true`                          | Flag to enable or disable the linting process of the CSS language.                                                                                                                                                   |
| **VALIDATE_DART**                               | `true`                          | Flag to enable or disable the linting process of the Dart language.                                                                                                                                                  |
| **VALIDATE_DOCKERFILE_HADOLINT**                | `true`                          | Flag to enable or disable the linting process of the Docker language.                                                                                                                                                |
| **VALIDATE_EDITORCONFIG**                       | `true`                          | Flag to enable or disable the linting process with the EditorConfig.                                                                                                                                                 |
| **VALIDATE_ENV**                                | `true`                          | Flag to enable or disable the linting process of the ENV language.                                                                                                                                                   |
| **VALIDATE_GHERKIN**                            | `true`                          | Flag to enable or disable the linting process of the Gherkin language.                                                                                                                                               |
| **VALIDATE_GITHUB_ACTIONS**                     | `true`                          | Flag to enable or disable the linting process of the GitHub Actions.                                                                                                                                                 |
| **VALIDATE_GITLEAKS**                           | `true`                          | Flag to enable or disable the linting process of the secrets.                                                                                                                                                        |
| **VALIDATE_GO**                                 | `true`                          | Flag to enable or disable the linting process of the individual Golang files. Set this to `false` if you want to lint Go modules. See the `VALIDATE_GO_MODULES` variable.                                            |
| **VALIDATE_GO_MODULES**                         | `true`                          | Flag to enable or disable the linting process of Go modules. Super-linter considers a directory to be a Go module if it contains a file named `go.mod`.                                                              |
| **VALIDATE_GO_RELEASER**                        | `true`                          | Flag to enable or disable the linting process of the GoReleaser config file.                                                                                                                                         |
| **VALIDATE_GOOGLE_JAVA_FORMAT**                 | `true`                          | Flag to enable or disable the linting process of the Java language. (Utilizing: google-java-format)                                                                                                                  |
| **VALIDATE_GROOVY**                             | `true`                          | Flag to enable or disable the linting process of the language.                                                                                                                                                       |
| **VALIDATE_HTML**                               | `true`                          | Flag to enable or disable the linting process of the HTML language.                                                                                                                                                  |
| **VALIDATE_JAVA**                               | `true`                          | Flag to enable or disable the linting process of the Java language. (Utilizing: checkstyle)                                                                                                                          |
| **VALIDATE_JAVASCRIPT_ES**                      | `true`                          | Flag to enable or disable the linting process of the JavaScript language. (Utilizing: ESLint)                                                                                                                        |
| **VALIDATE_JAVASCRIPT_STANDARD**                | `true`                          | Flag to enable or disable the linting process of the JavaScript language. (Utilizing: standard)                                                                                                                      |
| **VALIDATE_JSCPD**                              | `true`                          | Flag to enable or disable the JSCPD.                                                                                                                                                                                 |
| **VALIDATE_JSON**                               | `true`                          | Flag to enable or disable the linting process of the JSON language.                                                                                                                                                  |
| **VALIDATE_JSX**                                | `true`                          | Flag to enable or disable the linting process for jsx files (Utilizing: ESLint)                                                                                                                                      |
| **VALIDATE_KOTLIN**                             | `true`                          | Flag to enable or disable the linting process of the Kotlin language.                                                                                                                                                |
| **VALIDATE_KUBERNETES_KUBECONFORM**             | `true`                          | Flag to enable or disable the linting process of Kubernetes descriptors with Kubeconform                                                                                                                             |
| **VALIDATE_LATEX**                              | `true`                          | Flag to enable or disable the linting process of the LaTeX language.                                                                                                                                                 |
| **VALIDATE_LUA**                                | `true`                          | Flag to enable or disable the linting process of the language.                                                                                                                                                       |
| **VALIDATE_MARKDOWN**                           | `true`                          | Flag to enable or disable the linting process of the Markdown language.                                                                                                                                              |
| **VALIDATE_NATURAL_LANGUAGE**                   | `true`                          | Flag to enable or disable the linting process of the natural language.                                                                                                                                               |
| **VALIDATE_OPENAPI**                            | `true`                          | Flag to enable or disable the linting process of the OpenAPI language.                                                                                                                                               |
| **VALIDATE_PERL**                               | `true`                          | Flag to enable or disable the linting process of the Perl language.                                                                                                                                                  |
| **VALIDATE_PHP**                                | `true`                          | Flag to enable or disable the linting process of the PHP language. (Utilizing: PHP built-in linter) (keep for backward compatibility)                                                                                |
| **VALIDATE_PHP_BUILTIN**                        | `true`                          | Flag to enable or disable the linting process of the PHP language. (Utilizing: PHP built-in linter)                                                                                                                  |
| **VALIDATE_PHP_PHPCS**                          | `true`                          | Flag to enable or disable the linting process of the PHP language. (Utilizing: PHP CodeSniffer)                                                                                                                      |
| **VALIDATE_PHP_PHPSTAN**                        | `true`                          | Flag to enable or disable the linting process of the PHP language. (Utilizing: PHPStan)                                                                                                                              |
| **VALIDATE_PHP_PSALM**                          | `true`                          | Flag to enable or disable the linting process of the PHP language. (Utilizing: PSalm)                                                                                                                                |
| **VALIDATE_POWERSHELL**                         | `true`                          | Flag to enable or disable the linting process of the Powershell language.                                                                                                                                            |
| **VALIDATE_PROTOBUF**                           | `true`                          | Flag to enable or disable the linting process of the Protobuf language.                                                                                                                                              |
| **VALIDATE_PYTHON**                             | `true`                          | Flag to enable or disable the linting process of the Python language. (Utilizing: pylint) (keep for backward compatibility)                                                                                          |
| **VALIDATE_PYTHON_BLACK**                       | `true`                          | Flag to enable or disable the linting process of the Python language. (Utilizing: black)                                                                                                                             |
| **VALIDATE_PYTHON_FLAKE8**                      | `true`                          | Flag to enable or disable the linting process of the Python language. (Utilizing: flake8)                                                                                                                            |
| **VALIDATE_PYTHON_ISORT**                       | `true`                          | Flag to enable or disable the linting process of the Python language. (Utilizing: isort)                                                                                                                             |
| **VALIDATE_PYTHON_MYPY**                        | `true`                          | Flag to enable or disable the linting process of the Python language. (Utilizing: mypy)                                                                                                                              |
| **VALIDATE_PYTHON_PYLINT**                      | `true`                          | Flag to enable or disable the linting process of the Python language. (Utilizing: pylint)                                                                                                                            |
| **VALIDATE_PYTHON_RUFF**                        | `true`                          | Flag to enable or disable the linting process of the Python language. (Utilizing: ruff)                                                                                                                              |
| **VALIDATE_R**                                  | `true`                          | Flag to enable or disable the linting process of the R language.                                                                                                                                                     |
| **VALIDATE_RAKU**                               | `true`                          | Flag to enable or disable the linting process of the Raku language.                                                                                                                                                  |
| **VALIDATE_RENOVATE**                           | `true`                          | Flag to enable or disable the linting process of the Renovate configuration files.                                                                                                                                   |
| **VALIDATE_RUBY**                               | `true`                          | Flag to enable or disable the linting process of the Ruby language.                                                                                                                                                  |
| **VALIDATE_RUST_2015**                          | `true`                          | Flag to enable or disable the linting process of the Rust language. (edition: 2015)                                                                                                                                  |
| **VALIDATE_RUST_2018**                          | `true`                          | Flag to enable or disable the linting process of Rust language. (edition: 2018)                                                                                                                                      |
| **VALIDATE_RUST_2021**                          | `true`                          | Flag to enable or disable the linting process of Rust language. (edition: 2021)                                                                                                                                      |
| **VALIDATE_RUST_CLIPPY**                        | `true`                          | Flag to enable or disable the clippy linting process of Rust language.                                                                                                                                               |
| **VALIDATE_SCALAFMT**                           | `true`                          | Flag to enable or disable the linting process of Scala language. (Utilizing: scalafmt --test)                                                                                                                        |
| **VALIDATE_SHELL_SHFMT**                        | `true`                          | Flag to enable or disable the linting process of Shell scripts. (Utilizing: shfmt)                                                                                                                                   |
| **VALIDATE_SNAKEMAKE_LINT**                     | `true`                          | Flag to enable or disable the linting process of Snakefiles. (Utilizing: snakemake --lint)                                                                                                                           |
| **VALIDATE_SNAKEMAKE_SNAKEFMT**                 | `true`                          | Flag to enable or disable the linting process of Snakefiles. (Utilizing: snakefmt)                                                                                                                                   |
| **VALIDATE_STATES**                             | `true`                          | Flag to enable or disable the linting process for AWS States Language.                                                                                                                                               |
| **VALIDATE_SQL**                                | `true`                          | Flag to enable or disable the linting process of the SQL language.                                                                                                                                                   |
| **VALIDATE_SQLFLUFF**                           | `true`                          | Flag to enable or disable the linting process of the SQL language. (Utilizing: sqlfuff)                                                                                                                              |
| **VALIDATE_TEKTON**                             | `true`                          | Flag to enable or disable the linting process of the Tekton language.                                                                                                                                                |
| **VALIDATE_TERRAFORM_FMT**                      | `true`                          | Flag to enable or disable the formatting process of the Terraform files.                                                                                                                                             |
| **VALIDATE_TERRAFORM_TERRASCAN**                | `true`                          | Flag to enable or disable the linting process of the Terraform language for security related issues.                                                                                                                 |
| **VALIDATE_TERRAFORM_TFLINT**                   | `true`                          | Flag to enable or disable the linting process of the Terraform language. (Utilizing tflint)                                                                                                                          |
| **VALIDATE_TERRAGRUNT**                         | `true`                          | Flag to enable or disable the linting process for Terragrunt files.                                                                                                                                                  |
| **VALIDATE_TSX**                                | `true`                          | Flag to enable or disable the linting process for tsx files (Utilizing: ESLint)                                                                                                                                      |
| **VALIDATE_TYPESCRIPT_ES**                      | `true`                          | Flag to enable or disable the linting process of the TypeScript language. (Utilizing: ESLint)                                                                                                                        |
| **VALIDATE_TYPESCRIPT_STANDARD**                | `true`                          | Flag to enable or disable the linting process of the TypeScript language. (Utilizing: ts-standard)                                                                                                                   |
| **VALIDATE_XML**                                | `true`                          | Flag to enable or disable the linting process of the XML language.                                                                                                                                                   |
| **VALIDATE_YAML**                               | `true`                          | Flag to enable or disable the linting process of the YAML language.                                                                                                                                                  |
| **YAML_CONFIG_FILE**                            | `.yaml-lint.yml`                | Filename for [Yamllint configuration](https://yamllint.readthedocs.io/en/stable/configuration.html) (ex: `.yaml-lint.yml`, `.yamllint.yml`)                                                                          |
| **YAML_ERROR_ON_WARNING**                       | `false`                         | Flag to enable or disable the error on warning for Yamllint.                                                                                                                                                         |

The `VALIDATE_[LANGUAGE]` variables work as follows:

- super-linter runs all supported linters by default.
- If you set any of the `VALIDATE_[LANGUAGE]` variables to `true`, super-linter defaults to leaving any unset variable to false (only validate those languages).
- If you set any of the `VALIDATE_[LANGUAGE]` variables to `false`, super-linter defaults to leaving any unset variable to true (only exclude those languages).
- If you set any of the `VALIDATE_[LANGUAGE]` variables to both `true` and `false`, super-linter fails reporting an error.

For more information about reusing super-linter configuration across
environments, see
[Share Environment variables between environments](docs/run-linter-locally.md#share-environment-variables-between-environments).

## Configure linters

Super-linter provides default configurations for some linters in the [`TEMPLATES/`](TEMPLATES/)
directory. You can customize the configuration for the linters that support
this by placing your own configuration files in the `LINTER_RULES_PATH`
directory. `LINTER_RULES_PATH` is relative to the `DEFAULT_WORKSPACE` directory.

Super-linter supports customizing the name of these configuration files. For
more information, refer to [Configure super-linter](#configure-super-linter).

For example, you can configure super-linter to load configuration files from the
`config/lint` directory in your repository:

```yaml
  env:
    LINTER_RULES_PATH: `config/lint`
```

Some of the linters that super-linter provides can be configured to disable
certain rules or checks, and to ignore certain files or part of them.

For more information about how to configure each linter, review
[their own documentation](#supported-linters-and-code-analyzers).

## Include or exclude files from checks

If you need to include or exclude directories from being checked, you can use
two environment variables: `FILTER_REGEX_INCLUDE` and `FILTER_REGEX_EXCLUDE`.

For example:

- Lint only the `src` folder: `FILTER_REGEX_INCLUDE: .*src/.*`
- Do not lint files inside test folder: `FILTER_REGEX_EXCLUDE: .*test/.*`
- Do not lint JavaScript files inside test folder: `FILTER_REGEX_EXCLUDE: .*test/.*.js`

<!-- This `README.md` has both markers in the text, so it is considered not generated. -->
Additionally, if you set `IGNORE_GENERATED_FILES` to `true`, super-linter
ignores any file with `@generated` string in it, unless the file
also has `@not-generated` marker. For example, super-linter considers a file
with the following contents as generated:

```bash
#!/bin/sh
echo "@generated"
```

while considers this file as not generated:

```bash
#!/bin/sh
echo "@generated" # @not-generated
```

Finally, you can set `IGNORE_GITIGNORED_FILES` to `true` to ignore a file if Git
ignores it too.

## Run Super-Linter outside GitHub Actions

You don't need GitHub Actions to run super-linter. It supports several runtime
environments.

### Run using a container runtime engine

You can run super-linter outside GitHub Actions. For example, you can run
super-linter from a shell:

```bash
docker run \
  -e LOG_LEVEL=DEBUG \
  -e RUN_LOCAL=true \
  -v /path/to/local/codebase:/tmp/lint \
  ghcr.io/super-linter/super-linter:latest
```

For more information, see
[Run super-linter outside GitHub Actions](https://github.com/super-linter/super-linter/blob/main/docs/run-linter-locally.md).

## Use your own SSH key and certificate

If you need to use your own SSH key to authenticate against private
repositories, you can use the `SSH_KEY` environment variable. The value of that
environment variable is expected to be be the private key of an SSH keypair that
has access to your private repositories.

For example, you can configure this private key as an
[Encrypted Secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets)
and access it with the `secrets` parameter from your GitHub Actions workflow:

```yaml
  env:
    SSH_KEY: ${{ secrets.SSH_PRIVATE_KEY }}
```

If you need to inject a SSL certificate into the trust store, you can use the
`SSL_CERT_SECRET` variable. The value of that variable is expected to be the
path to the files that contains a CA that can be used to valide the certificate:

```yaml
  env:
    SSL_CERT_SECRET: ${{ secrets.ROOT_CA }}
```

## How to contribute

If you would like to help contribute to super-linter, see
[CONTRIBUTING](https://github.com/super-linter/super-linter/blob/main/.github/CONTRIBUTING.md).
