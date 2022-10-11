# maven-release-gh-actions

This project aims to demonstrate how to use the Maven Release plugin in conjunction with GitHub Actions to publish releases of applications to GitHub.


Each release will be based on the develop branch, using the Maven Release plugin to do changes to [pom.xml](pom.xml) which also generates a tag associated with the given release version. 

The maven release is handled by the [stage] and [stage-manual] workflows


The tag reference is then used to trigger the [publish] action.


The [publish action][publish] merges the given tag into the main branch, packages the JAR and publishes it as an artifact associated with a release by the tag reference given by the staged release. 


There are three workflows to support this: 
- [Publish release][publish]
- [Stage with bump version][stage]
- [Stage with manually assigned versions][stage-manual]


[publish]: .github/workflows/publish.yml
[stage]: .github/workflows/stage.yml
[stage-manual]: .github/workflows/stage-manual.yml
