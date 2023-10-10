# SemanticReleasePoC

Steps:

On the pre-commit:

Install pre-commits with

```
pre-commit install --hook-type commit-msg
```

Run Commitizen to verify proper syntax with each commit

On the PR CICD run:

This creates a changelog but does not commit. We manually add the modified files
and commit. This ensures that the modified branch gets always the latest
changelog and a rule will ignore the `chore*` commits in the changelog to avoid
meaningless entries.

```
semantic-release -v version --no-vcs-release --no-commit
git add --all
git commit -m "chore(release): bump version and update changelog"
git push --force
```

On merge CICD run:

Compute the proper version number and create a tag after publishing the package

```
version_number=$(semantic-release -v version --print)
git tag $version_number
git push origin --tags
```
