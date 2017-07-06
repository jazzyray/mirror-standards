# Standards and Templates

This is a repository of standards documents and templates.

## Standards
Standards documents are intend to provide mandated consistency across DSP.

The standards documents:

* [/health](health.md); All DSP services must include a health endpoint. This provides health status for the service and all dependent services. Health response are linked to a troubleshooting guide. Troubleshooting guides/steps provide mitigation steps to restore "healthy" status. 
* [/gtg](gtg.md); All DSP services must include a good to go endpoint. This endpoint provide operational status for monitoring and routing decisions.
* [/about](about.md); All DSP services must include a about endpoint. This endpoint provides a description of the service, build number and version. The version should be used by clients to ensure version compatibility.
* [troubleshooting](trouble.md); All DSP services must include a troubleshooting guide. The troubleshooting guide intends to cover known error conditions and mitigation steps to resolve service. Erroneous [/health](health.md) responses must include links to the trouble.md.


## Templates

Template documents are intended to provide blueprints for various architectural and development documentation.
Standardising on templated documents improves consistency.

The template documents:

* [architecture](architecture_template.md); The architecture template should be used to document architectural designs, requirements, slas, kpis. It follows the C4 architectural design methodology.
