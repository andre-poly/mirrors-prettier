# ~~archived~~

~~prettier made some changes that breaks plugins entirely~~

Forked from [archived repository](https://github.com/pre-commit/mirrors-prettier).

Requires manual steps for adding a new Prettier version:

1. Edit `.pre-commit-hooks.yaml` to change Prettier version specified in `additional_dependencies`
2. Commit and tag with the matching version number
   ```shell
   git tag -a v0.0.0 -m v0.0.0
   git push origin --tags
   ```

___


prettier mirror
===============

Mirror of prettier package for pre-commit.

For pre-commit: see https://github.com/pre-commit/pre-commit

For prettier: see https://github.com/prettier/prettier


### Using prettier with pre-commit

Add this to your `.pre-commit-config.yaml`:

```yaml
-   repo: https://github.com/pre-commit/mirrors-prettier
    rev: ''  # Use the sha / tag you want to point at
    hooks:
    -   id: prettier
```

*note*: only prettier versions >= 2.1.0 are supported

When using plugins with `prettier` you'll need to declare them under
`additional_dependencies`. For example:

```yaml
-   repo: https://github.com/pre-commit/mirrors-prettier
    rev: ''  # Use the sha / tag you want to point at
    hooks:
    -   id: prettier
        additional_dependencies:
        -   prettier@2.1.2
        -   '@prettier/plugin-xml@0.12.0'
```

By default, all files are passed to `prettier`, if you want to limit the
file list, adjust `types` / `types_or` / `files`:

```yaml
    -   id: prettier
        types_or: [css, javascript]
```
