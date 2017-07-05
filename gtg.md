# Good to Go Health Standard

Synopsis: Ontotext DSP services must provide a standard operation health status mechanism. All RESTful services must provide a /__gtg endpoint. The endpoint will enable client to inspect the operational health of the service instance. The /__gtg endpoint is expected to return a simple status only and not provide information of dependent service status. The /health endpoint should be used to inspect the aggregate health from all external dependencies.

# Table of Contents

1. [Introduction](#introduction)
2. [Model](#model)
3. [REST specification](#rest_spec)

<a name="introduction"></a>
# Introduction
The /__gtg endpoint is used to check the operational status of a service. The service returns a 200 for an operational service instance and a 503 "Service unavailable" for a service instance which should be taken out of service. This endpoint should be used for routing at proxy layers such as application load balancers and health status checking alerting.

If any health-check status is in ERROR status the /__gtg endpoint must respond with a 503.

It is expected that this service uses cached health-check status by default. Invoking all health checks would be a performance overhead which is normally unacceptable.

<a name="model"></a>
# Model

{ "gtg": "OK|UNAVAILABLE" }

<a name="rest_spec"></a>
# REST Specification

The /__gtg endpoint must adhere to the following basic RESTful standard:

| Verb              | URL template | Parameters        | Mime Type         | Supported Status Codes |
|:----------------- |:-------------|:------------------|:------------------|:-----------------------|
| GET               | /__gtg       | cache             | application/json  | 200 503                |


The response body must follow that described in [model](#model)

## Query Parameters
cache: flag which indicates to use cached health check results (default is true). This is useful directly after deployment and forcing health refresh. 

E.g. /__gtg?cache=false will force a re-run off all the services health checks.