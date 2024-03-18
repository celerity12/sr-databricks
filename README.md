  
[![New Relic Experimental header](https://github.com/newrelic/opensource-website/raw/main/src/images/categories/Experimental.png)](https://opensource.newrelic.com/oss-category/#new-relic-experimental)

![GitHub forks](https://img.shields.io/github/forks/newrelic-experimental/sr-databricks?style=social)
![GitHub stars](https://img.shields.io/github/stars/newrelic-experimental/sr-databricks?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/newrelic-experimental/sr-databricks?style=social)

![GitHub all releases](https://img.shields.io/github/downloads/newrelic-experimental/sr-databricks/total)
![GitHub release (latest by date)](https://img.shields.io/github/v/release/newrelic-experimental/sr-databricks)
![GitHub last commit](https://img.shields.io/github/last-commit/newrelic-experimental/sr-databricks)
![GitHub Release Date](https://img.shields.io/github/release-date/newrelic-experimental/sr-databricks)

![GitHub issues](https://img.shields.io/github/issues/newrelic-experimental/sr-databricks)
![GitHub issues closed](https://img.shields.io/github/issues-closed/newrelic-experimental/sr-databricks)
![GitHub pull requests](https://img.shields.io/github/issues-pr/newrelic-experimental/sr-databricks)
![GitHub pull requests closed](https://img.shields.io/github/issues-pr-closed/newrelic-experimental/sr-databricks)

# Databricks integration for New Relic
  
## Installation

Import the [install-nr.py](/install-nr.py) notebook into your workspace and execute it.

This will produce the initialization script that would download, install and configure this integration upon cluster initialization.

The file is written to this path

- **dbfs:/newrelic/sr-databricks-init.sh**

Add this initialization script to the list of initialization files for every cluster manager that needs to be monitored.

The following environment variables should be defined in your databricks cluster configuration for the initialization script to create the correct configuration

1. NEWRELIC_ACCOUNT_ID
2. NEWRELIC_LICENSE_KEY
3. NEWRELIC_TAGS:
    - (optional) tags to be added to every newrelic event
    - dirctionary of key value pairs separated by comma for example
      - `{"team": "FieldEngineering", "project": "DatabricksMonitoring", "cost_center": "12345"}`
      - DO NOT wrapp the dictionary in quotes
4. NEWRELIC_ENDPOINT_REGION
    - Use "US" for US datacenter and "EU" for EU datacenter
    - If your New Relic account is in the US datacenter the variable is optional

## Configuration

The install script produces the configuration in the **config.yml** file. The following properties are filled in from environment variables or files.

### General Configuration

- **run_as_service**: True or False. If True, the integration runs as a daemon service every poll interval, otherwise it runs just once.
- **poll_interval**: The interval in seconds at which to fetch metrics from databricks
- **log_level**: info, debug, warning, critical or error
- **log_file**: log file

### Spark Connection Configuration

- **cluster_name**: name of the cluster  
- **cluster_mode**: driver_mode or standalone
- **driver_host**: spark web UI url
- **conf_ui_port**: spark web UI port
- **master_ui_port**: spark master UI port

### New Relic Connection Configuration

- **api_endpoint**: Full URL for the New Relic Event API collector or short cuts "US" and "EU"
- **account_id**: New Relic account id
- **api_key**: New Relic license key

### Other Configuration

- **labels**: (optional) labels are tags added to every newrelic event

## Support

New Relic has open-sourced this project. This project is provided AS-IS WITHOUT WARRANTY OR DEDICATED SUPPORT. Issues and contributions should be reported to the project here on GitHub.

We encourage you to bring your experiences and questions to the [Explorers Hub](https://discuss.newrelic.com) where our community members collaborate on solutions and new ideas.

## Contributing

We encourage your contributions to improve [Project Name]! Keep in mind when you submit your pull request, you'll need to sign the CLA via the click-through using CLA-Assistant. You only have to sign the CLA one time per project. If you have any questions, or to execute our corporate CLA, required if your contribution is on behalf of a company, please drop us an email at <opensource@newrelic.com>.

**A note about vulnerabilities**
As noted in our [security policy](../../security/policy), New Relic is committed to the privacy and security of our customers and their data. We believe that providing coordinated disclosure by security researchers and engaging with the security community are important means to achieve our security goals.

If you believe you have found a security vulnerability in this project or any of New Relic's products or websites, we welcome and greatly appreciate you reporting it to New Relic through [HackerOne](https://hackerone.com/newrelic).

## License

*sr-databricks* is licensed under the [Apache 2.0](http://apache.org/licenses/LICENSE-2.0.txt) License.

*sr-databricks* also uses source code from third-party libraries. You can find full details on which libraries are used and the terms under which they are licensed in the third-party notices document.
