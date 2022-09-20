# Workflows
This is our Workflows repo - DO NOT PUT ANYTHING CONFIDENTIAL OR IDENTIFYING IN THIS REPO

Currently this repo contains the public Workflow task for pushing to an organization's private Nuget feed

To use:
  The project must have the following properties defined in the csproj file, in the PropertyGroup tag:
  
    <RepositoryUrl>[URL to the github repo]</RepositoryUrl>
    
    <PackageId>[package id for nuget - no spaces]</PackageId>
    
    <GenerateDocumentationFile>True</GenerateDocumentationFile>
    
    <IncludeSymbols>true</IncludeSymbols>
    
    <SymbolPackageFormat>snupkg</SymbolPackageFormat>
    
  In the repo that will become the Nuget Package, create an action that contains the code from PrivateGithubNuget.yml
  
    Fill in the name for the CSProj file as well as the folder that contains it (use blank if the project file is in the root directory)
    
    Add a Personal Access Token to the repo as a secret, call it NUGET_AUTH_TOKEN
    
  The action will automatically run when changes are pushed into the master or main branch (specified at the top of the yml file you created).
