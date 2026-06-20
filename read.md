<!-- trigger:
- main

pool:
  name: 'MyLocalPool'

steps:
- checkout: self

- script: mvn clean test
  displayName: 'Build and Run Unit Tests'

- task: PublishTestResults@2
  inputs:
    testResultsFiles: '**/surefire-reports/TEST-*.xml'
    testResultsFormat: 'JUnit'
    failTaskOnMissingResultsFile: true
  displayName: 'Publish Test Results'

- task: PublishBuildArtifacts@1
  inputs:
    PathtoPublish: 'target'
    ArtifactName: 'drop'
    publishLocation: 'Container'
  displayName: 'Publish Build Artifacts' -->