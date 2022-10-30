# actions-use-ruby-tools

![actions-use-ruby-tools](https://github.com/tecolicom/actions-use-ruby-tools/actions/workflows/test.yml/badge.svg)

This GitHub action install ruby packages and cache them for later
use.  When executed next time with same package list, and any other
environment are not changed, installed files are extracted from the
cached archive.

When valid cached archive is not found, all packages are installed by
`gem` command.  Incremental installation is not supported.

This actions assumes `gem` command is already installed.  So please
install it before calling if not available.  Installation is done by
root privilege.

Installed files are taken by comparing directory before and after
installation.  So it takes time to find them if many files are already
installed before command execution.

Document is not installed by default.  If you want to install
document, set `document` parameter `true`;

Output is same as
[`@actions/cache`](https://github.com/actions/cache).

## Usage

```yaml
# inputs:
#   tools:    { required: true,  type: string }
#   cache:    { required: false, type: string, default: yes }
#   key:      { required: false, type: string }
#   document: { required: false, type: string, default: false }

- uses: tecolicom/actions-use-ruby-tools@v1
  with:

    # ruby packages
    tools: ''

    # Cache strategy
    #
    # yes:      activate cache
    # no:       no cache
    # workflow: effective within same workflow (mainly for test)
    #
    cache: yes

    # Additional cache key
    key: ''

    # Document install
    # Default: flase
    document: ''
```

## Example

```yaml
- uses: tecolicom/actions-use-ruby-tools@v1
  with:
    tools: sinatra
```

## See Also

### [tecolicom/actions](https://github.com/tecolicom/actions)

### [`@tecolicom/actions-install-and-cache`](https://github.com/tecolicom/actions-install-and-cache)

This action is just a glue for
[`@actions-install-and-cache`](https://github.com/tecolicom/actions-install-and-cache).
