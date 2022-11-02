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

## Generating an SSH key
Maven Release utilizes the ssh agent to push changes to the configured SCM. 
For some reason this will not work in a CI context, and as a result of this we need to set up a Deploy key for the repository.
The deploy key needs write access to the repository.

1. Generate an SSH key for the repository using:

   `ssh-keygen -t ed25519 -a 100 -f ./ghactions -C "git@github.com:thedatasnok/maven-release-gh-actions.git"`

   (replace the part after github.com to whatever the repository is)


2. Create a deploy key with the public key of the generated SSH key.

3. Create a repository secret with the private key of the generated SSH key, named `SSH_PRIVATE_KEY`.

Make sure to not stage the private key in the repository. 


[publish]: .github/workflows/publish.yml
[stage]: .github/workflows/stage.yml
[stage-manual]: .github/workflows/stage-manual.yml
