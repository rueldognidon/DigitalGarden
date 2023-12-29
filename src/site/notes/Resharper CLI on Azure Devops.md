---
{"dg-publish":true,"permalink":"/resharper-cli-on-azure-devops/"}
---

#Resharper #Jetbrains #SoftwareDevelopment #CleanCode 

How to add static code analysis to your AzureDevo

``` YAML
- task: PowerShell@2
  displayName: "Resharper CLI Code Analysis"
  inputs:
    targetType: 'inline'
    script: |
      # Write your PowerShell commands here.
      dotnet new tool-manifest
      dotnet tool install JetBrains.Resharper.GlobalTools
      dotnet jb inspectcode Your.Project.App.sln --severity=WARNING --format=Sarif --output=resharperCli.sarif --verbose=WARN
    workingDirectory: '$(Build.SourcesDirectory)/src/Your.Project.App/'

- task: PublishBuildArtifacts@1
  displayName: "Upload Resharper CLI Code Analysis Result"
  inputs:
    PathtoPublish: '$(Build.SourcesDirectory)/src/Your.Project.App/resharperCli.sarif'
    ArtifactName: 'CodeAnalysisLogs'
```

To view the result on AzureDevops Pipeline:

[SARIF SAST Scans Tab - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=sariftools.scans)

