The endpoint for the target resource.
API Version: 2022-05-01-preview.
Previous API Version: 2022-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### HybridConnectivityEndpointsPutCustom
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var endpoint = new AzureNative.HybridConnectivity.Endpoint("endpoint", new()
    {
        EndpointName = "custom",
        ResourceId = "/subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.Relay/namespaces/custom-relay-namespace",
        ResourceUri = "subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine",
        Type = "custom",
    });

});


```

```go
package main

import (
	hybridconnectivity "github.com/pulumi/pulumi-azure-native-sdk/hybridconnectivity"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridconnectivity.NewEndpoint(ctx, "endpoint", &hybridconnectivity.EndpointArgs{
			EndpointName: pulumi.String("custom"),
			ResourceId:   pulumi.String("/subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.Relay/namespaces/custom-relay-namespace"),
			ResourceUri:  pulumi.String("subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine"),
			Type:         pulumi.String("custom"),
		})
		if err != nil {
			return err
		}
		return nil
	})
}

```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hybridconnectivity.Endpoint;
import com.pulumi.azurenative.hybridconnectivity.EndpointArgs;
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.io.File;
import java.nio.file.Files;
import java.nio.file.Paths;

public class App {
    public static void main(String[] args) {
        Pulumi.run(App::stack);
    }

    public static void stack(Context ctx) {
        var endpoint = new Endpoint("endpoint", EndpointArgs.builder()        
            .endpointName("custom")
            .resourceId("/subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.Relay/namespaces/custom-relay-namespace")
            .resourceUri("subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine")
            .type("custom")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const endpoint = new azure_native.hybridconnectivity.Endpoint("endpoint", {
    endpointName: "custom",
    resourceId: "/subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.Relay/namespaces/custom-relay-namespace",
    resourceUri: "subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine",
    type: "custom",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

endpoint = azure_native.hybridconnectivity.Endpoint("endpoint",
    endpoint_name="custom",
    resource_id="/subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.Relay/namespaces/custom-relay-namespace",
    resource_uri="subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine",
    type="custom")

```

```yaml
resources:
  endpoint:
    type: azure-native:hybridconnectivity:Endpoint
    properties:
      endpointName: custom
      resourceId: /subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.Relay/namespaces/custom-relay-namespace
      resourceUri: subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine
      type: custom

```

{{% /example %}}
{{% example %}}
### HybridConnectivityEndpointsPutDefault
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var endpoint = new AzureNative.HybridConnectivity.Endpoint("endpoint", new()
    {
        EndpointName = "default",
        ResourceUri = "subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine",
        Type = "default",
    });

});


```

```go
package main

import (
	hybridconnectivity "github.com/pulumi/pulumi-azure-native-sdk/hybridconnectivity"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridconnectivity.NewEndpoint(ctx, "endpoint", &hybridconnectivity.EndpointArgs{
			EndpointName: pulumi.String("default"),
			ResourceUri:  pulumi.String("subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine"),
			Type:         pulumi.String("default"),
		})
		if err != nil {
			return err
		}
		return nil
	})
}

```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hybridconnectivity.Endpoint;
import com.pulumi.azurenative.hybridconnectivity.EndpointArgs;
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.io.File;
import java.nio.file.Files;
import java.nio.file.Paths;

public class App {
    public static void main(String[] args) {
        Pulumi.run(App::stack);
    }

    public static void stack(Context ctx) {
        var endpoint = new Endpoint("endpoint", EndpointArgs.builder()        
            .endpointName("default")
            .resourceUri("subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine")
            .type("default")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const endpoint = new azure_native.hybridconnectivity.Endpoint("endpoint", {
    endpointName: "default",
    resourceUri: "subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine",
    type: "default",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

endpoint = azure_native.hybridconnectivity.Endpoint("endpoint",
    endpoint_name="default",
    resource_uri="subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine",
    type="default")

```

```yaml
resources:
  endpoint:
    type: azure-native:hybridconnectivity:Endpoint
    properties:
      endpointName: default
      resourceUri: subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine
      type: default

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridconnectivity:Endpoint default /subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine/providers/Microsoft.HybridConnectivity/endpoints/default 
```
