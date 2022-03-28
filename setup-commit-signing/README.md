# Setup GPG Commit Signing GitHub Action

An action that sets up GPG commit signing. Based on [Homebrew's action of the same name](https://github.com/Homebrew/actions/tree/master/setup-commit-signing).

## Usage

```yaml
- name: Set up GPG commit signing
  id: set-up-commit-signing
  uses: borksh/actions/setup-commit-signing@master
  with:
    signing_key: ${{ secrets.GPG_SIGNING_KEY }}
```

When committing changes, ensure that the value of the environment variable `BORK_GPG_PASSPHRASE` is set to the signing key's passphrase.

```yaml
- name: Add and commit changes
  run: |
    git add file.txt
    git commit -m "Updated file.txt"
  env:
    HOMEBREW_GPG_PASSPHRASE: ${{ secrets.GPG_PASSPHRASE }}
```
