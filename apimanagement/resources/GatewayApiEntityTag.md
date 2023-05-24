API details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateGatewayApi
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gatewayApiEntityTag = new AzureNative.ApiManagement.GatewayApiEntityTag("gatewayApiEntityTag", new()
    {
        ApiId = "echo-api",
        GatewayId = "gw1",
        ProvisioningState = AzureNative.ApiManagement.ProvisioningState.Created,
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewGatewayApiEntityTag(ctx, "gatewayApiEntityTag", &apimanagement.GatewayApiEntityTagArgs{
			ApiId:             pulumi.String("echo-api"),
			GatewayId:         pulumi.String("gw1"),
			ProvisioningState: apimanagement.ProvisioningStateCreated,
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
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
import com.pulumi.azurenative.apimanagement.GatewayApiEntityTag;
import com.pulumi.azurenative.apimanagement.GatewayApiEntityTagArgs;
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
        var gatewayApiEntityTag = new GatewayApiEntityTag("gatewayApiEntityTag", GatewayApiEntityTagArgs.builder()        
            .apiId("echo-api")
            .gatewayId("gw1")
            .provisioningState("created")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gatewayApiEntityTag = new azure_native.apimanagement.GatewayApiEntityTag("gatewayApiEntityTag", {
    apiId: "echo-api",
    gatewayId: "gw1",
    provisioningState: azure_native.apimanagement.ProvisioningState.Created,
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gateway_api_entity_tag = azure_native.apimanagement.GatewayApiEntityTag("gatewayApiEntityTag",
    api_id="echo-api",
    gateway_id="gw1",
    provisioning_state=azure_native.apimanagement.ProvisioningState.CREATED,
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  gatewayApiEntityTag:
    type: azure-native:apimanagement:GatewayApiEntityTag
    properties:
      apiId: echo-api
      gatewayId: gw1
      provisioningState: created
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:GatewayApiEntityTag echo-api /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/gateways/gw1/apis/echo-api 
```
