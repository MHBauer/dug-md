

### Kubernetes Context Object

*`platform` Property Value*: `kubernetes`

The following properties are defined for usage within a Kubernetes deployment:

- `namespace`
The name of the Kubernetes namespace in which the
Service Instance will be visible. This property MUST be a non-empty
string serialized as follows:

```
"namespace": "namespace-name-here"
```

For example:
```
"namespace": "testing"
```

- `clusterID`
The unique identifier for the Kubernetes cluster from which the request
was sent. This property MUST be a non-empty string serialized as follows:

```
"clusterID": "id-goes-here"
```
For example:
```
"clusterID": "644e1dd7-2a7f-18fb-b8ed-ed78c3f92c2b"
```

The following table specifies which properties MUST appear in each API:

| Request API | Properties |
| --- | --- |
| `PUT /v2/service_instances/:instance_id` | `namespace`, `clusterID` |
| `PATCH /v2/service_instances/:instance_id` | `namespace`, `clusterID` |
| `PUT /v2/service_instances/:instance_id/service_bindings/:binding_id` | `namespace`, `clusterID` |

Example:

The following example shows a `context` property that might appear as
part of a Kubernetes API call:
  ```
  "context": {
    "platform": "kubernetes",
    "namespace": "development",
    "clusterID": "8263feba-9b8a-23ae-99ed-abcd1234feda"
  }
  ```

## Bind Resource Object

In the [Open Service Broker API specification](spec.md), requests to
[create a Service Binding](spec.md#binding) can contain a `bind_resource`
object in which Platforms MAY choose to add additional fields.

### Cloud Foundry Bind Resource Object

The following properties are defined for usage within a Cloud Foundry
deployment:

- `space_guid`  
  This OPTIONAL property is the GUID of a space that a Service Binding is
  associated with. If present, this property MUST be a non-empty string
  serialized as follows:
  ```
  "space_guid": "space-guid-here"
  ```
  For example:
  ```
  "space_guid": "15823972-c216-4ba5-9f3f-e75b0b891297"
  ```

The following example shows a `bind_resource` object that might appear as part
of a Cloud Foundry API call:
  ```
  "bind_resource": {
    "app_guid": "5e76c9bf-d5e3-46bf-9877-6d8dddfc8a45",
    "space_guid": "15823972-c216-4ba5-9f3f-e75b0b891297"
  }
  ```
