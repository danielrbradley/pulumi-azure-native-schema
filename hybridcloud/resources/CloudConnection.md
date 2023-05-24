Resource which represents the managed network connection between Azure Gateways and remote cloud gateways.
API Version: 2023-01-01-preview.
Previous API Version: 2023-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a Cloud Connection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cloudConnection = new AzureNative.HybridCloud.CloudConnection("cloudConnection", new()
    {
        CloudConnectionName = "cloudconnection1",
        CloudConnector = new AzureNative.HybridCloud.Inputs.ResourceReferenceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/demo-rg/providers/Microsoft.HybridCloud/cloudConnectors/123456789012",
        },
        Location = "West US",
        RemoteResourceId = "arn:aws:ec2:us-east-1:123456789012:VPNGateway/vgw-043da592550819c8a",
        ResourceGroupName = "demo-rg",
        SharedKey = "password123",
        VirtualHub = new AzureNative.HybridCloud.Inputs.ResourceReferenceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/demo-rg/providers/Microsoft.Network/VirtualHubs/testHub",
        },
    });

});


```

```go
package main

import (
	hybridcloud "github.com/pulumi/pulumi-azure-native-sdk/hybridcloud"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridcloud.NewCloudConnection(ctx, "cloudConnection", &hybridcloud.CloudConnectionArgs{
			CloudConnectionName: pulumi.String("cloudconnection1"),
			CloudConnector: &hybridcloud.ResourceReferenceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/demo-rg/providers/Microsoft.HybridCloud/cloudConnectors/123456789012"),
			},
			Location:          pulumi.String("West US"),
			RemoteResourceId:  pulumi.String("arn:aws:ec2:us-east-1:123456789012:VPNGateway/vgw-043da592550819c8a"),
			ResourceGroupName: pulumi.String("demo-rg"),
			SharedKey:         pulumi.String("password123"),
			VirtualHub: &hybridcloud.ResourceReferenceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/demo-rg/providers/Microsoft.Network/VirtualHubs/testHub"),
			},
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
import com.pulumi.azurenative.hybridcloud.CloudConnection;
import com.pulumi.azurenative.hybridcloud.CloudConnectionArgs;
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
        var cloudConnection = new CloudConnection("cloudConnection", CloudConnectionArgs.builder()        
            .cloudConnectionName("cloudconnection1")
            .cloudConnector(Map.of("id", "/subscriptions/subid/resourceGroups/demo-rg/providers/Microsoft.HybridCloud/cloudConnectors/123456789012"))
            .location("West US")
            .remoteResourceId("arn:aws:ec2:us-east-1:123456789012:VPNGateway/vgw-043da592550819c8a")
            .resourceGroupName("demo-rg")
            .sharedKey("password123")
            .virtualHub(Map.of("id", "/subscriptions/subid/resourceGroups/demo-rg/providers/Microsoft.Network/VirtualHubs/testHub"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cloudConnection = new azure_native.hybridcloud.CloudConnection("cloudConnection", {
    cloudConnectionName: "cloudconnection1",
    cloudConnector: {
        id: "/subscriptions/subid/resourceGroups/demo-rg/providers/Microsoft.HybridCloud/cloudConnectors/123456789012",
    },
    location: "West US",
    remoteResourceId: "arn:aws:ec2:us-east-1:123456789012:VPNGateway/vgw-043da592550819c8a",
    resourceGroupName: "demo-rg",
    sharedKey: "password123",
    virtualHub: {
        id: "/subscriptions/subid/resourceGroups/demo-rg/providers/Microsoft.Network/VirtualHubs/testHub",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cloud_connection = azure_native.hybridcloud.CloudConnection("cloudConnection",
    cloud_connection_name="cloudconnection1",
    cloud_connector=azure_native.hybridcloud.ResourceReferenceArgs(
        id="/subscriptions/subid/resourceGroups/demo-rg/providers/Microsoft.HybridCloud/cloudConnectors/123456789012",
    ),
    location="West US",
    remote_resource_id="arn:aws:ec2:us-east-1:123456789012:VPNGateway/vgw-043da592550819c8a",
    resource_group_name="demo-rg",
    shared_key="password123",
    virtual_hub=azure_native.hybridcloud.ResourceReferenceArgs(
        id="/subscriptions/subid/resourceGroups/demo-rg/providers/Microsoft.Network/VirtualHubs/testHub",
    ))

```

```yaml
resources:
  cloudConnection:
    type: azure-native:hybridcloud:CloudConnection
    properties:
      cloudConnectionName: cloudconnection1
      cloudConnector:
        id: /subscriptions/subid/resourceGroups/demo-rg/providers/Microsoft.HybridCloud/cloudConnectors/123456789012
      location: West US
      remoteResourceId: arn:aws:ec2:us-east-1:123456789012:VPNGateway/vgw-043da592550819c8a
      resourceGroupName: demo-rg
      sharedKey: password123
      virtualHub:
        id: /subscriptions/subid/resourceGroups/demo-rg/providers/Microsoft.Network/VirtualHubs/testHub

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridcloud:CloudConnection cloudconnection1 /subscriptions/subid/resourceGroups/demo-rg/providers/Microsoft.HybridCloud/cloudConnections/cloudConnection1 
```
