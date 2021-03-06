# Release Process

Declaring formal releases requires peer review.

* A reviewer of a pull request should recommend a new version number (patch, minor or major).
* Once your change is merged feel free to bump the version as recommended by the reviewer.
* A new version number should not be cut without peer review unless done by the project maintainer.

## Publishing a new version

Before new release, add a summary of changes since last version to (CHANGELOG.rst)[./CHANGELOG.rst].

```
pip install twine zest.releaser[recommended]
prerelease
release
git push upstream master --follow-tags
# remove prev distros, or else twine would try to upload them
rm -rf dist
python setup.py sdist
twine upload --repository pypi --verbose dist/*
postrelease
git push
```
