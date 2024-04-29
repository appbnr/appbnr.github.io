# Bundle Metadata Specification

Every application bundle contains a metadata file `package.yml`. 

## Generic details

```
schemaVersion: 1.0.0

code: demo
name: Demo application
description: Appbnr profile
developer: appbnr
visibility: Private
copyright: © 2023 Appbnr Technologies Limited
defaultBasePath: profile

release:
  version: 0.0.1
  summary: Test release

```

| Field | Required | Description |
|-------|----------|-------------|
| schemaVersion | true | `1.0.0` |
| code | true | unique application code created for one developer |
| name | true | a one line name for this app |
| description | true | a long description to describe this app |
| copyright | true | copy right line |
| visibility |  | how this bundle can be found by users |
| defaultBasePath |  | default installation path for this app |
| release |  | see [release](#release) section |
| odm |  | see [odm](#odm) section |

## Release 

```
release:
  version: 0.0.1
  summary: Test release
```

| Field | Required | Description |
|-------|----------|-------------|
| version | true | `0.0.1` |
| summary | true | short summary of this release |

## ODM

```
odm:
  objects:
    - ...
```
| Field | Required | Description |
|-------|----------|-------------|
| objects |  | List of [odm objects](#odm-object) for this app |

### ODM Object
```
odm:
  object:
    - typeCode: client
      fields:
        strings: [name]
        numbers: [num_of_employees]
      classification:
        level: Confidential
```

| Field | Required | Description |
|-------|----------|-------------|
| typeCode | true  | uniquely identify this object |
| fields | true | fields definition |
| fields.strings | | list of names of string fields |
| fields.numbers | | list of names of number fields |
| classification | | information classification of this type |
| classification.level | | default classification for all fields |