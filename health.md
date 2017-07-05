# Service Health Standard

Synopsis: Ontotext DSP services must provide a standard health checking mechanism. All RESTful services must provide a /health endpoint. The endpoint will enable clients to inspect a running service instance. The /health endpoint is expected to aggregate health from all external dependencies. The set of checks must provide a client with enough information to determine if the service instance is able to handle requests. Error conditions should be linked to troubleshooting/run-book mitigation documentation. 

# Table of Contents

1. [Introduction](#introduction)
2. [Model](#model)
3. [REST specification](#rest_spec)

<a name="introduction"></a>
# Introduction

The /health endpoint is used to check the health/status of the running application. It provides clients with operational information. Health information and links to mitigation steps should be used to restore service. /health should not be used by monitoring software to check if the service is operational. The /__gtg endpoint documented here should provide service availability status.

The /health endpoint must aggregate the health of all its dependencies and provide a service instance level health status.

The /health endpoint must performs various checks, such as:

* status of the connections to the other services used by the service instance
* status of databases used by the service. Including the database ability to provide the correct data for the service in a timely manner.
* status of database schema versions
* status of search indices used by the service. Including the indices ability to provide the correct data for the service in a timely manner
* status of dependent services 
* the status of the host, e.g. disk space
* the status of the network, e.g. port access
* etc..

Optional: 
/health information should be a simple ‘status’ when accessed over an unauthenticated connection or full message details when authenticated. 
By default the /health endpoint should not be sensitive or restricted.

<a name="model"></a>
# Model
The /health endpoint must return application/json for a successful health check. The following is the basic JSON structure expected for a health check response:

```
{
	"status": "OK|ERROR",
	"health-checks": [{
		"status": "OK|ERROR",
		"severity": "The severity level of the health check if it is in ERROR state. Must be one of 1 (high), 2 (medium), 3 (low)",
		"id": "The unique ID of the health check",
		"name": "The name of the health check",
		"type": "The type of the check. service|graphdb|elastic|jms|cpu|disk-space|memory|network etc... Where each type will have additional properties.",
		"impact": "The impact of the health check",
		"troubleshooting": "The URL#fragment to trouble.md mitigation steps",
		"description": "What is the healthcheck doing"
	}]
} 
```

Healthchecks should be pluggable and reusable across services. So a ElasticSearch health-check should be re-usable in many services.

As an example a minimal /health implementation with an ElasticSearch health-check might look something like the following.
Each health-check should be configurable. In this case the ElasticSearch index is configured to check a number of indices. Checking and supporting inspection of availability, fields, cluster status etc.:

```
{
	"status": "OK",
	"health-checks": [{
		"status": "OK",
		"id": "12345",
		"name": "search-api-elastic-index-health-check",
		"type": "elastic",
		"impact": "Search unavailable",
		"troubleshooting": "https://gitlab.ontotext.com/SAS/standards_templates/blob/master/trouble.md#condition_n",
		"description": "Check search service elastic search indices",
		"indices": [{
			"status": "OK",
			"id": "The index id",
			"clusterName": "The name of the cluster",
			"numberOfNodes": "The number of nodes",
			"numberOfDataNodes": "The number of data nodes",
			"activePrimaryShards": "The number of active primary shards",
			"activeShards": "The number of active shards",
			"relocatingShards": "Relocating shards",
			"initializingShards": "Initializing shards",
			"unassignedShards": "Unassigned shards"
		}]
	}]
} 
```

<a name="rest_spec"></a>
# REST specification
The /health endpoint must adhere to the following basic RESTful standard:

| Verb              | URL template | Mime Type         | Supported Status Codes |
|:----------------- |:-------------|:------------------|:----------------------:|
| GET               | /health      |  application/json | 200                    |

The response body must follow that described in [model](#model)

