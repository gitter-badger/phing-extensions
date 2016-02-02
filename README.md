# Phing Extensions
A set of Phing extensions.

# Overview
This collection of Phing extensions provides:

  * LastCommitTimeTask
  * ReadSemanticVersionTask
  * RemoveEmptyDirectoriesTask
  * SetDirectoryMTimeTask
     
## LastCommitTimeTask
LastCommitTimeTask sets the modification time of files to the last commit time in Git. 
       
#### Parameters
| Name        | Type   | Description                                                                            | Default | Required |
| ------------| ------ | -------------------------------------------------------------------------------------- | ------- | -------- |
| Dir         | string | The directory were under which the sources are located. Typically the build directory. |         | Yes      |     
| HaltOnError | bool   | If true the build fails on errors, otherwise this task generates error events.         | True    | No       |                  
                             
#### Example
```XML
<LastCommitTimeTask dir="build"/>
```

## ReadSemanticVersionTask
ReadSemanticVersionTask asks the user for [Semantic version](http://semver.org/) and validates 
the given input is a valid [Semantic version](http://semver.org/). The version and its parts are published
under supplied properties for further usage in the Phing build script. 

#### Parameters
| Name               | Type   | Description                                                                       | Default | Required |
| ------------------ | ------ | --------------------------------------------------------------------------------- | ------- | -------- |
| File               | string | Filename for storing the entered SemanticVersion.                                 |         | No       |     
| HaltOnError        | bool   | If true the build fails on errors, otherwise this task generates error events.    | True    | No       |                  
| VersionProperty    | string | The name of the property for publishing the version (e.g. 1.2.3-alpha.1).         |         | No       |                            
| ReleaseProperty    | string | The name of the property for publishing the major, minor, and patch version (e.g. 1.2.3). |         | No       |                            
| MajorProperty      | string | The name of the property for publishing the major version (e.g. 1).               |         | No       |                          
| MinorProperty      | string | The name of the property for publishing the minor version (e.g. 2).               |         | No       |                          
| PatchProperty      | string | The name of the property for publishing the patch version (e.g. 3).               |         | No       |                          
| PreReleaseProperty | string | The name of the property for publishing the pre-release version (e.g. alpha.1).   |         | No       |                               
#### Example
```XML
<ReadSemanticVersion File=".version"  VersionProperty="VERSION"/>
<echo message="${VERSION}"/>
```

## RemoveEmptyDirectoriesTask
RemoveEmptyDirectoriesTask removes recursively empty directories under a parent directory. 

#### Parameters
| Name         | Type   | Description                                                                    | Default | Required |
| ------------ | ------ | ------------------------------------------------------------------------------ | ------- | -------- |
| Dir          | string | The parent directory under which empty directories must be removed.            |         | True     |
| RemoveParent | bool   | If true the parent directory is removed as well if it is empty.                | False   | No       |    
| HaltOnError  | bool   | If true the build fails on errors, otherwise this task generates error events. | True    | No       |                  

#### Example
```XML
<RemoveEmptyDirectoriesTask Dir="build/www/js"  RemoveParent="false"/>
```

## SetDirectoryMTimeTask
SetDirectoryMTimeTask sets recursively the modification time of directories to the maximum modification time of its 
entries.

#### Parameters
| Name         | Type   | Description                                                                    | Default | Required |
| ------------ | ------ | ------------------------------------------------------------------------------ | ------- | -------- |
| Dir          | string | The parent directory.                                                          |         | True     |
| HaltOnError  | bool   | If true the build fails on errors, otherwise this task generates error events. | True    | No       |                  

#### Example
```XML
<SetDirectoryMTimeTask Dir="build"/>
```

# Installation
We recommend to install setbased/phing via [Composer](https://getcomposer.org/):

```json
{
  "require-dev": {
    "setbased/phing-extensions": "2.*"
  }
}
```
