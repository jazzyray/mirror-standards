# Troubleshooting {service_name} service

Synopsis: a document describing the steps and processes required to resolve known operating and service problems for the {service_name} service. 

# Table of Contents

1. [Introduction](#introduction)
	* [Service Overview](#service_overview)
		* [Context Diagram](#context_diagram) 
		* [Important endpoints](#important_endpoints)
			* [Endpoint {n}](#endpoint_n)
			* [Health](#health)
			* [Good to Go](#gtg)
			* [About](#about) 
	* [Alive](#alive)
	* [References](#references) 
2. [Prerequisites](#prerequisites) 
3. [Resolving Known Error Conditions](#resolve)
	* [Condition {n}](#condition_n)
		* [Solution {n}](#solution_n)
		* [Verification {n}](#verification_n) 
4. [Appendix {n}](#appendix_n)

<a name="introduction"></a>
# Introduction
This document intends to help, users, developers and testers when troubleshooting the {service_name} service. It [outlines](#service_overview) the service, the [important endpoints](#important_endpoints) and [context](#context_diagram) in which the service must reside. The user of this document must have the [prerequisite](#prerequisites) skill level in order that the document is effective.

[Known error conditions](#resolve) and mitigation solutions are documented.

<a name="service_overview"></a>
## {Service_Name} Service Overview
{A short description of the service and its context within the overall system architecture goes here. It must mention and describe all its dependencies and nothing more.}

NOTE: The content here must reflect the message body text response from the {service_name} /about endpoint.

|                   |                                                    | 
|:----------------- |:---------------------------------------------------|
| Description       | API/Service description goes here                  |                                     
| Entry Point URL.  | http://{env}.subdomain.domain/service-context      |

<a name="context_diagram"></a>
### Optional Context Diagram 
{optional context diagram of the service and its immediate dependencies goes here}
{The included image should be published as a jpeg/png}

Must be included if the service has any out of process dependencies.

<a name="important_endpoints"></a>
### Important endpoints
{A description of the important endpoints which the {service_name} service facilitates. These must describe the most common endpoint features required to support most system architectures. It should not exhaustive}

<a name="endpoint_n"></a>
#### Endpoint {n}
{Description of the endpoint goes here}

| Verb              | URL template | Mime Type         | Supported Status Codes |
|:----------------- |:-------------|:------------------|:----------------------:|
|                   | /x/y/z       | x                 | 200                    |

##### Example curl request
``` curl -v http://some/url```

#### OK Response
The resultant response should be described here:

```{}```

Spec for /endpoint/x here {[link]}

#### Example request (n)
```curl command goes here```
```expected response goes here```
{Description of the response goes here}

<a name="health"></a>
#### Health endpoint
{This section must describe the /health endpoint its output and the values contained therein}

Returns JSON data summarising the current health status of the application. The status code must always be a 200 unless the /health endpoint itself is in error. 

| Verb              | URL template | Mime Type         | Supported Status Codes |
|:----------------- |:-------------|:------------------|:----------------------:|
| GET               | /health      |: application/json | 200                    |

#### Healthy Response
The resultant JSON must include status for all out of process service dependencies including:

* Databases; graphdb, elastic etc.
* Services; other API services
* Messaging; JMS and others..

```
{
  "status": "ERROR",
  "graphdb": "OK",
  "elastic": "ERROR"
}
```

Spec for /health here (@TODO)

<a name="gtg"></a>
#### Good To Go endpoint
{This section must describe the /__gtg endpoint its outputs and the values contained therein}

The /__gtg endpoint should be based on the health check status results. One or more errors imply that the service is not good to go.

The endpoint emits a 200 OK response if the application is considered as healthy, and 503 Service Unavailable if it is unhealthy. 

This endpoint is intended to be used to make routing decisions and provide operations personnel simple access to service availability.

| Verb              | URL template | Mime Type         | Supported Status Codes |
|:----------------- |:-------------|:------------------|:----------------------:|
| GET               | /__gtg       |: application/json | 200                    |

#### Good to go Response
The resultant JSON must include an aggregated status for all out of process service dependencies.
OK only when all health checks are 200.

```
{
  "gtg": "OK"
}
```

Spec for /__gtg here (@TODO)

<a name="about"></a>
#### About
Returns JSON data describing the application, providing links to all relevant supporting operational documentation resources including this document.

It must include the running version.

Spec for /about here (@TODO)

```
{
  "build.date": "2016-01-19 08:30",
  "description": "the about description should reflect the service overview section of this document",
  "trouble": "<URL to trouble.md>", 
  "version": "1.0.5"
}
```

<a name="alive"></a>
## Alive
This document must evolve and live directly with the code. It should be named trouble.md and must reside in the root folder of the service. Operations and Devops must review the document to ensure that it describes the desired process required to restore service and mitigate erroneous state.

<a name="references"></a>
## References
This document should be referenced directly from appropriate erroneous HTTP status code message body content. Thus providing a resolution path to mitigate errors and in some cases restore service.

<a name="prerequisites"></a>
# Prerequisites
Users, developers and testers who wish to effectively troubleshoot the {service_name} service must be at least moderately experienced with the following:

e.g

* Experience and understanding of REST curl/postman
* Basic shell experience Bash 
* etc..

<a name="resolve"></a>
# Resolving Known Error Conditions

<a name="condition_n"></a>
## Condition {n}
Describe the problem/condition, cause and solution for this type of condition/error.

| #                 | Detail                                           | 
|:----------------- |:-------------------------------------------------|
| Problem           | Description of the problem                       | 
| Cause             | Description of the cause of the problem          |
| Manifestation {1} | Error condition manifestation (e.g log message)  |
| Manifestation {n} | Error condition manifestation (e.g status code)  |   

<a name="solution_n"></a>
### Solution
{Step by Step instructions to mitigate/resolve condition go here}

* ```command one```  
* ```command two```
* screenshot one
* ```command three```
* etc..

<a name="verification_n"></a>
### Verification
{Step by Step instructions to ensure that the mitigation/resolution is a success}

```command one e.g curl http:\\{host}\__gtg == 200```        

<a name="appendix_n"></a>
# Appendix <n>
Description of referenced documents and links.

| #                 | Title                        | Location | Author  |
|:----------------- |:-----------------------------|----------|---------|
|                   | Title                        | URL      | someone |

