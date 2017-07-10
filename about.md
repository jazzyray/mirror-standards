# About Service Standard

Synopsis: Ontotext DSP services must provide a standard operational about mechanism. All RESTful services must provide an /\__about endpoint. The endpoint will enable the client to inspect and understand what features the service instance intends to provide. It also needs to provide links to its troubleshooting guide, build number and running version. The /\__about endpoint is expected to return a 200 OK status only. The complementary [/health](health.md) endpoint should be used to inspect the aggregate health and health of all external dependencies. The [/__gtg](gtg.md) endpoint should be used to check operational status either "Good to Go" or "Service Unavailable".

# Table of Contents

1. [Introduction](#introduction)
2. [Model](#model)
3. [REST specification](#rest_spec)

<a name="introduction"></a>
# Introduction

The /\__about endpoint is used to provide a description of the running service, its main features, a link to the operational troubleshooting guide, the version and buildnumber. 

The version property is particularly important for clients. Advertising the version number allows clients to check that they are able to function correctly using the current running version.

The service returns a 200 only.

<a name="model"></a>
# Model

Returns JSON data describing the application, providing links to all relevant supporting operational documentation resources including this document.

It must include the running version.

```
{
  "build.date": "2016-01-19 08:30",
  "description": "The about description should reflect the service overview section of the associated trouble.md document",
  "trouble": "<URL to trouble.md>", 
  "version": "1.0.5"
}
```

The about model may be extended on a per service basis to provide other additional information which is required by clients.

<a name="rest_spec"></a>
# REST Specification

The /__gtg endpoint must adhere to the following basic RESTful standard:

| Verb              | URL template | Parameters        | Mime Type         | Supported Status Codes |
|:----------------- |:-------------|:------------------|:------------------|:-----------------------|
| GET               | /\__about       |                   | application/json  | 200                    |


The response body must follow that described in [model](#model)

## Status Codes

### 200 - OK

The about endpoint has succeed.
