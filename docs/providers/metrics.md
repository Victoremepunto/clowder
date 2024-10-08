# Metrics Provider

The **Metrics Provider** is responsible for creating the Service for the
metrics port and adding the port to the container template on the deployment.

## ClowdApp Configuration

There is no configuration for this provider.

## ClowdEnv Configuration

The **Metrics Provider** will run in one of the following modes. These are set up
by the ClowdEnvironment. Depending on the environment you are running you may
or may not have access to change this mode. More information on provider
configuration is at the bottom of this page.

### operator

In operator mode, the **Metrics Provider** will set the port and path to the
values specified in the ClowdEnvironment.

ClowdEnv Config options available:

- `port`
- `path`

## Generated App Configuration

The Metrics configuration appears in the cdappconfig.json with the following
structure.

### JSON structure

```json
{
  "metricsPort": 9000,
  "metricsPath": "/metrics"
}
```

### Client access

For supported languages, the metrics configuration is access via the following
attribute names.

| Language   | Attribute Name              |
|------------|-----------------------------|
| Python     | `LoadedConfig.metricsPort`  |
| Go         | `LoadedConfig.MetricsPort`  |
| Javascript | `LoadedConfig.metricsPort`  |
| Ruby       | `LoadedConfig.metricsPort`  |


### ClowdEnv Configuration

The **Metrics Provider** can be configured to set the metrics port and path as
follows in this example.

```yaml
apiVersion: cloud.redhat.com/v1alpha1
kind: ClowdEnvironment
metadata:
  name: myenv
spec:
  # Other Env Config
  providers:
    metrics:
      mode: operator
      path: /metrics
      port: 9000
```
