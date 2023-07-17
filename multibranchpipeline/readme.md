### Multi Branch Pipeline
* A Multi branch pipeline is a concept of automatic building creative Jenkins pipeline based on the git branches.
* Tt can automatically discover new branches in the source control and automatically create a pipeline for that branch.
* when the pipeline builds starts, Jenkins uses the Jenkinsfile in that branch for that build stages
* We can also choose to exclude selected branches with regular expression.
* SCM can be GitHub, Bitbucket or Gitlab.
