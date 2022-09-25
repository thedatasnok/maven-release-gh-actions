# maven-release-gh-actions

This project aims to demonstrate how to use the Maven Release plugin in conjunction with GitHub Actions to publish releases of applications to GitHub.


Each release will be based on the develop branch, which is then in turn merged into the main branch. 


Upon merge there will be a new tag pushed to the main branch of the repository, triggering a the release Action to begin.


The changes to the main branch will be merged back into the develop branch, and the version will be bumped for the next possible release.


There are two workflows to support this: 
- [publish][publish]
- [stage][stage]


The [stage][stage] workflow is responsible for making the changes to the pom.xml and versioning, while the [publish][publish] workflow does everything related to publishing the package.


[publish]: .github/workflows/publish.yml
[stage]: .github/workflows/stage.yml
