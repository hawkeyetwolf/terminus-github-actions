[![Actively Maintained](https://img.shields.io/badge/Pantheon-Actively_Maintained-yellow?logo=pantheon&color=FFDC28)](https://pantheon.io/docs/oss-support-levels#actively-maintained-support)

# Terminus GitHub Actions

A GitHub Action for quickly installing and configuring the Pantheon CLI tool,
[Terminus](https://github.com/pantheon-systems/terminus).

## Usage

In order to avoid deprecation warnings, it's recommended to use the
[`setup-php`](https://github.com/shivammathur/setup-php) action rather than rely
on the version of PHP that is installed by default on GH runners.

```yaml
steps:
  - name: Setup PHP
    uses: shivammathur/setup-php@v2
    with:
      php-version: '7.4'

  - name: Install Terminus
    uses: pantheon-systems/terminus-github-actions@main
    with:
      pantheon-machine-token: ${{ secrets.PANTHEON_MACHINE_TOKEN }}

  - name: List sites
    run: terminus site:list
```

By default, this action installs the latest version of Terminus that has been
released on GitHub. You can provide a specific version of Terminus to install
using the `terminus-version` input:

```yaml
steps:
  - name: Setup PHP
    uses: shivammathur/setup-php@v2
    with:
      php-version: '7.4'

  - name: Install Terminus
    uses: pantheon-systems/terminus-github-actions@main
    with:
      pantheon-machine-token: ${{ secrets.PANTHEON_MACHINE_TOKEN }}
      terminus-version: 2.6.5

  - name: List sites
    run: terminus site:list
```

Please note that in order to run commands that require SSH (e.g. drush or wp-cli), you will need to setup a SSH key. There are plenty of options available in the [Github Actions Marketplace](https://github.com/marketplace?type=actions&query=ssh+key+). We recommend you to choose one of them and use them in your pipeline.

## Credits

Big thanks to <a href="https://github.com/G-Rath">Gareth Jones</a> and <a href="https://www.ackama.com/">Ackama</a> for the initial development work.
