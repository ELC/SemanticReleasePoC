# SemanticReleasePoC

Steps:

On the pre-commit:

Run Commitizen to verify proper syntax

On the PR run:

This creates a changelog but does not commit. We manually add the modified files and commit

```
semantic-release -v version --no-vcs-release --no-commit
git add --all
gir commit --ammend
git push --force
```


On merge run:

This creates a commit AND a tag

```
semantic-release version --vv --no-vcs-release
```