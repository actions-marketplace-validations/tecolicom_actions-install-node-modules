# actions-install-node-modules

![actions-install-node-modules](https://github.com/tecolicom/actions-install-node-modules/actions/workflows/test.yml/badge.svg)

This GitHub action searches lock files under the specified root
directory, install modules and cache all `node_modules` directory for
later use.  When executed next time with same package configurations,
and any other environment are not changed, installed modules are
extracted from the cached archive.

At this time, installation is done by next commands.

```yaml
package-lock.json:
    npm install
yarn.lock:
    yarn --check-files --frozen-lockfile --non-interactive
```

Output is same as [`@actions/cache`](https://github.com/actions/cache).

## Usage

```yaml
# inputs:
#   root:  { required: false, type: string, default: . }
#   cache: { required: false, type: string, default: yes }
#   key:   { required: false, type: string }

- uses: tecolicom/actions-use-perl-modules@v1
  with:

    # root directory
    root: .

    # Cache strategy
    #
    # yes:      activate cache
    # no:       no cache
    # workflow: effective within same workflow (mainly for test)
    #
    cache: yes

    # Additional cache key
    key: ''
```

## Example

```yaml
- uses: tecolicom/actions-install-node-modules@v1
  with:
    root: ./Script/lib/node
```

## See Also

### [tecolicom/actions](https://github.com/tecolicom/actions)
