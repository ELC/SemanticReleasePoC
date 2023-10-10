# SemanticReleasePoC

Steps:

On the PR run:

This creates a changelog but does not commit. We manually add the modified files and commit

```
semantic-release -v version --no-vcs-release --no-commit
git add --all
gir commit -m "chore(version): update version and changelog [skip ci]"
git push
```

On merge run:

This creates a commit AND a tag

```
semantic-release version --vv --no-vcs-release
```