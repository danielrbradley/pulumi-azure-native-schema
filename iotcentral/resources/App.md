The IoT Central application.
API Version: 2021-06-01.
Previous API Version: 2021-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Apps_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var app = new AzureNative.IoTCentral.App("app", new()
    {
        DisplayName = "My IoT Central App",
        Identity = new AzureNative.IoTCentral.Inputs.SystemAssignedServiceIdentityArgs
        {
            Type = "SystemAssigned",
        },
        Location = "westus",
        ResourceGroupName = "resRg",
        ResourceName = "myIoTCentralApp",
        Sku = new AzureNative.IoTCentral.Inputs.AppSkuInfoArgs
        {
            Name = "ST2",
        },
        Subdomain = "my-iot-central-app",
        Template = "iotc-pnp-preview@1.0.0",
    });

});


```

```go
package main

import (
	iotcentral "github.com/pulumi/pulumi-azure-native-sdk/iotcentral"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := iotcentral.NewApp(ctx, "app", &iotcentral.AppArgs{
			DisplayName: pulumi.String("My IoT Central App"),
			Identity: &iotcentral.SystemAssignedServiceIdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("resRg"),
			ResourceName:      pulumi.String("myIoTCentralApp"),
			Sku: &iotcentral.AppSkuInfoArgs{
				Name: pulumi.String("ST2"),
			},
			Subdomain: pulumi.String("my-iot-central-app"),
			Template:  pulumi.String("iotc-pnp-preview@1.0.0"),
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
import com.pulumi.azurenative.iotcentral.App;
import com.pulumi.azurenative.iotcentral.AppArgs;
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
        var app = new App("app", AppArgs.builder()        
            .displayName("My IoT Central App")
            .identity(Map.of("type", "SystemAssigned"))
            .location("westus")
            .resourceGroupName("resRg")
            .resourceName("myIoTCentralApp")
            .sku(Map.of("name", "ST2"))
            .subdomain("my-iot-central-app")
            .template("iotc-pnp-preview@1.0.0")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const app = new azure_native.iotcentral.App("app", {
    displayName: "My IoT Central App",
    identity: {
        type: "SystemAssigned",
    },
    location: "westus",
    resourceGroupName: "resRg",
    resourceName: "myIoTCentralApp",
    sku: {
        name: "ST2",
    },
    subdomain: "my-iot-central-app",
    template: "iotc-pnp-preview@1.0.0",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

app = azure_native.iotcentral.App("app",
    display_name="My IoT Central App",
    identity=azure_native.iotcentral.SystemAssignedServiceIdentityArgs(
        type="SystemAssigned",
    ),
    location="westus",
    resource_group_name="resRg",
    resource_name_="myIoTCentralApp",
    sku=azure_native.iotcentral.AppSkuInfoArgs(
        name="ST2",
    ),
    subdomain="my-iot-central-app",
    template="iotc-pnp-preview@1.0.0")

```

```yaml
resources:
  app:
    type: azure-native:iotcentral:App
    properties:
      displayName: My IoT Central App
      identity:
        type: SystemAssigned
      location: westus
      resourceGroupName: resRg
      resourceName: myIoTCentralApp
      sku:
        name: ST2
      subdomain: my-iot-central-app
      template: iotc-pnp-preview@1.0.0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:iotcentral:App myIoTCentralApp /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.IoTCentral/IoTApps/myIoTCentralApp 
```
