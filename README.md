## About this repo

This repo is for Tile Developer Guide content.

## Which branch to use?

<p class="note">
<span class="note__title">Note</span>
If you are using the Provide instructions in your PRs, indicate which branches you want Docs to apply your commits to.
</p>

| Branch name | Use for… | URL |
|-------------| ---------|-----|
| master      | This is the "edge" build, for Ops Manager v3.1. | https://docs-staging.vmware.com/en/draft/Tile-Developer-Guide/3.1/tile-dev-guide/index.html |
| 3.0       | Ops Manager Tile Dev Guide v3.0  | https://docs.vmware.com/en/Tile-Developer-Guide/3.0/tile-dev-guide/index.html |
| 2.10      | Ops Manager Tile Dev Guide v2.10 | https://docs.vmware.com/en/Tile-Developer-Guide/2.10/tile-dev-guide/index.html |


## Terminology List

List of terms that VMware wants to use consistently in the doc:

+ The Tile Dashboard–for the UI/product as a whole. For example, "Log in to the Tile Dashboard. [MB 2018.07.11]
+ Tile Dashboard CI–for the subsystem of the Tile Dashboard that does the automated testing. For example, "Tile Dashboard CI runs any post-deploy errands that your tile has defined." [MB 2018.07.11]

## Releasing a New Minor Version

Because **master** is the latest and greatest documentation, the process is to cut a **x.x** branch
for the version that **master** was targeting during that time.

After this point, **master** is the target for the next version of this product.

## Partials

Cross-product partials for these docs are single sourced from the [Docs Partials](https://github.com/pivotal-cf/docs-partials) repository.

## Contributing to Documentation

If there is some documentation to add for an unreleased patch version of these docs, create a branch off of the live branch
you intend to edit and create a pull request against that branch.
After the version that change is targeting is released, the pull request can be merged and be live
the next time a documentation deployment occurs.

If the documentation is meant to be target several released versions, you must:

- create a pull request for each individual minor version
- or ask the technical writer to cherry-pick to particular branches/versions.

For instructions on how to create a pull request on a branch and instructions on how to create a
pull request using a fork, see
[Creating a PR](https://docs-wiki.sc2-04-pcf1-apps.oc.vmware.com/wiki/external/create-pr.html)
in the documentation team wiki.

## Publishing Docs

- [docworks](https://docworks.vmware.com/) is the main tool for managing docs used by writers.
- [docsdash](https://docsdash.vmware.com/) is a deployment UI which manages the promotion from
staging to pre-prod to production. The process below describes how to upload our docs to staging,
replacing the publication with the same version.

### Prepare Markdown Files

- Markdown files live in this repo.
- Images should live in an `images` directory at the same level and linked with a relative link.
- Each page requires an entry in [config/toc.md](config/toc.md) for the table of contents.
- Variables live in [config/template_variables.yml](config/template_variables.yml).

### In Docsdash

1. Wait about 1 minute for processing to complete after uploading.
2. Go to https://docsdash.vmware.com/deployment-stage

   There should be an entry with a blue link which says `Documentation` and points to staging.

### Promoting to Pre-Prod and Prod

**Prerequisite** Needs additional privileges - reach out to a manager on the docs team [#tanzu-docs](https://vmware.slack.com/archives/C055V2M0H) or ask a writer to do this step for you.

1. Go to Staging publications in docsdash
  https://docsdash.vmware.com/deployment-stage

2. Select a publication ( that it's the latest version)

3. Click "Deploy selected to Pre-Prod" and wait for the pop to turn green (refresh if necessary after about 10s)

4. Go to Pre-Prod list
  https://docsdash.vmware.com/deployment-pre-prod

5. Select a publication

6. Click "Sign off for Release"

7. Wait for your user name to show up in the "Signed off by" column

8. Select the publication again

9. Click "Deploy selected to Prod"

## Troubleshooting Markdown

| Problem | List displays as a paragraph |
|---------|-----------|
| Symptom:| Bulleted or numbered lists look fine on GitHub but display as a single paragraph in HTML.|
| Solution: | Add a blank line after the stem sentence and before the first item in the list or convert from Markdown to HTML|

| Problem | List numbering is broken: every item is `1.` |
|---------|-----------|
| Symptom:| Each numbered item in a list is a `1.` instead of `1.`, `2.`, `3.`, etc|
| Solution: | Try removing any blank newlines within each step.|
