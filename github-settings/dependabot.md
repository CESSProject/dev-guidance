# dependabot

Dependabot is a service provided by GitHub that automatically monitors and updates the dependencies of code repositories.

The complete help documentation can be found at [dependabot](https://docs.github.com/en/code-security/dependabot).

## Why use it?

For eligible dependencies, Dependabot will automatically generate a pull request for upgrades.

So in fact, using Dependabot is about leveraging the maintainer's obsession, prompting them to actively update or reject new versions of dependency libraries.

The automatically generated pull request will include

- Release notes  
- Changelog  
- Commits  

Wait for additional information to assist the maintainers in making decisions.

When maintaining multiple codebases that have dependencies on each other, Dependabot can also alert the maintainers.

In addition to regular version updates, Dependabot also detects security updates and generates alerts (Dependabot alerts).

## How to use it

To enable it, simply add a `dependabot.yml` configuration file that meets the format requirements in the `.github/` directory at the root of the code repository.

The format of the configuration file refers to: [Configuration options for the dependabot.yml file](https://docs.github.com/en/code-security/dependabot/dependabot-version-updates/configuration-options-for-the-dependabot.yml-file).

### Important Configuration Items

For example, with this configuration file:

```yaml
version: 2
updates:
  - package-ecosystem: "cargo"
    directory: "/"
    schedule:
      interval: "weekly"
    ignore:
    # these need to be updated together, so dependabot PRs
    # are just noise. So, ignore them:
    - dependency-name: sp-core
    - dependency-name: sp-keyring
    - dependency-name: sp-runtime
    - dependency-name: sp-crypto-hashing
    - dependency-name: sp-version
  - package-ecosystem: github-actions
    directory: '/'
    schedule:
      interval: weekly
```

- `package-ecosystem: "cargo"`
  The content of this item determines which dependency manager will be used, and currently, [package managers](https://docs.github.com/en/code-security/dependabot/dependabot-version-updates/configuration-options-for-the-dependabot.yml-file#package-ecosystem) are supported.

- `directory: "/cess"`
  The content of this item determines the root directory of the library to be monitored, which is a relative path based on the root directory of the code repository.

- `schedule:`
  The content of this item determines the frequency of monitoring.

- `allow / ignore`:
  The content of this item is equivalent to the whitelist/blacklist of dependencies during the monitoring process.
  