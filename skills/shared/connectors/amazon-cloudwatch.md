# Amazon CloudWatch

## Purpose
Connector-specific rules for Amazon CloudWatch Request nodes.

## When to use
Use this document when the requested ACE flow includes an Amazon CloudWatch Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Amazon CloudWatch Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_amazoncloudwatch.msgnode`
- `applicationConnectorType="amazoncloudwatch"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Amazon CloudWatch Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Amazon CloudWatch Request nodes:

- `displayName="Create log group"` `action="CREATE"` `businessObject="loggroup"`
- `displayName="Retrieve log groups"` `action="RETRIEVEALL"` `businessObject="loggroup"`
- `displayName="Delete log group"` `action="DELETEALL"` `businessObject="loggroup"`
- `displayName="Create log stream"` `action="CREATE"` `businessObject="logstream"`
- `displayName="Retrieve log streams"` `action="RETRIEVEALL"` `businessObject="logstream"`
- `displayName="Delete log stream"` `action="DELETEALL"` `businessObject="logstream"`
- `displayName="Retrieve filtered log events"` `action="RETRIEVEALL"` `businessObject="filteredlogevents"`
- `displayName="Retrieve log events"` `action="RETRIEVEALL"` `businessObject="logevents"`
- `displayName="Create multiple log events"` `action="PUTLOGEVENTS"` `businessObject="logevents"`
- `displayName="Update or create metric alarm"` `action="UPSERTWITHWHERE"` `businessObject="metricalarms"`
- `displayName="Retrieve metric alarms"` `action="RETRIEVEALL"` `businessObject="metricalarms"`
- `displayName="Delete metric alarm"` `action="DELETEALL"` `businessObject="metricalarms"`
- `displayName="Enable metric alarm"` `action="ENABLEMETRICALARM"` `businessObject="metricalarms"`
- `displayName="Disable metric alarm"` `action="DISABLEMETRICALARM"` `businessObject="metricalarms"`
- `displayName="Retrieve export tasks"` `action="RETRIEVEALL"` `businessObject="exporttask"`
- `displayName="Create export task"` `action="CREATE"` `businessObject="exporttask"`
- `displayName="Retrieve composite alarms"` `action="RETRIEVEALL"` `businessObject="compositealarms"`
- `displayName="Update or create composite alarm"` `action="UPSERTWITHWHERE"` `businessObject="compositealarms"`
- `displayName="Enable composite alarm"` `action="ENABLECOMPOSITEALARM"` `businessObject="compositealarms"`
- `displayName="Disable composite alarm"` `action="DISABLECOMPOSITEALARM"` `businessObject="compositealarms"`
- `displayName="Retrieve metrics"` `action="RETRIEVEALL"` `businessObject="metrices"`
- `displayName="Publish custom metric data"` `action="UPSERTWITHWHERE"` `businessObject="metrices"`
- `displayName="Retrieve metric streams"` `action="RETRIEVEALL"` `businessObject="metricstream"`
- `displayName="Update or create metric stream"` `action="UPSERTWITHWHERE"` `businessObject="metricstream"`
- `displayName="Delete metric stream"` `action="DELETEALL"` `businessObject="metricstream"`
- `displayName="Start metric stream"` `action="STARTMETRICSTREAM"` `businessObject="metricstream"`
- `displayName="Stop metric stream"` `action="STOPMETRICSTREAM"` `businessObject="metricstream"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AmazonCloudWatch1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="AmazonCloudWatch1" policyTemplate="online_v1_aws_basic_pki" policyType="amazoncloudwatch" shortDescription="" version="">
     <credentialName>AmazonCloudWatchCredential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>AWS_BASIC_PKI</authenticationMethod>
     <region/>
     <roleArn/>
     <oidcServerUrl/>
     <profileArn/>
     <trustAnchorArn/>
     <proxyId/>
  </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
