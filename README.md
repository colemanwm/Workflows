# Workflows
This is our Workflows repo - DO NOT PUT ANYTHING CONFIDENTIAL OR IDENTIFYING IN THIS REPO

Currently this repo contains the public Workflow task for pushing to an organization's private Nuget feed

<h1>Private Nuget Package Feed</h1>
To use:
  The project must have the following properties defined in the csproj file, in the PropertyGroup tag:
  
   
    <GeneratePackageOnBuild>False</GeneratePackageOnBuild>
    
    <Version>$(VersionSuffix)</Version>
    
    <Authors>Coleman Worldwide Moving</Authors>
    
    <Company>Coleman Worldwide Moving</Company>
    
    <PackageProjectUrl>[repo url]</PackageProjectUrl>
    
    <RepositoryUrl>[repo url]</RepositoryUrl>
    
    <RepositoryType>git</RepositoryType>
    
    <GenerateDocumentationFile>true</GenerateDocumentationFile>
    
    <IncludeSymbols>true</IncludeSymbols>
    
    <SymbolPackageFormat>snupkg</SymbolPackageFormat>
    
  In the repo that will become the Nuget Package, create an action that contains the code from PrivateGithubNuget.yml
  
    Fill in the name for the CSProj file as well as the folder that contains it (use blank if the project file is in the root directory)
    
    Add a Personal Access Token to the repo as a secret, call it NUGET_AUTH_TOKEN
    
  The action will automatically run when changes are pushed into the master or main branch (specified at the top of the yml file you created).

<h1>Automatic release management</h1>

There is also the ability to create automatic releases by pushing a tag with the correct syntax to the repo. It calls an action within this repo, when a tag is created using version syntax.

<h2>Setup</h2>

First, copy the code from Release.yml as an action into your repo

Fill in the parameters - read the docs!

Save/commit the file

<h2>Use</h2>
Within visual studio or git command line, create and push a tag using the following syntax:

  For production releases:
  
    v0.0.0
    
  For beta and other prerelease versions:
  
    v0.0.0-alpha
    
    v0.0.0-beta
    
    v0.0.0-rc
