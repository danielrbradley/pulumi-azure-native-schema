App Service plan.
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Or Update App Service plan
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var appServicePlan = new AzureNative.Web.AppServicePlan("appServicePlan", new()
    {
        Kind = "app",
        Location = "East US",
        Name = "testsf6141",
        ResourceGroupName = "testrg123",
        Sku = new AzureNative.Web.Inputs.SkuDescriptionArgs
        {
            Capacity = 1,
            Family = "P",
            Name = "P1",
            Size = "P1",
            Tier = "Premium",
        },
    });

});


```

```go
package main

import (
	web "github.com/pulumi/pulumi-azure-native-sdk/web"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := web.NewAppServicePlan(ctx, "appServicePlan", &web.AppServicePlanArgs{
			Kind:              pulumi.String("app"),
			Location:          pulumi.String("East US"),
			Name:              pulumi.String("testsf6141"),
			ResourceGroupName: pulumi.String("testrg123"),
			Sku: &web.SkuDescriptionArgs{
				Capacity: pulumi.Int(1),
				Family:   pulumi.String("P"),
				Name:     pulumi.String("P1"),
				Size:     pulumi.String("P1"),
				Tier:     pulumi.String("Premium"),
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
import com.pulumi.azurenative.web.AppServicePlan;
import com.pulumi.azurenative.web.AppServicePlanArgs;
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
        var appServicePlan = new AppServicePlan("appServicePlan", AppServicePlanArgs.builder()        
            .kind("app")
            .location("East US")
            .name("testsf6141")
            .resourceGroupName("testrg123")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("family", "P"),
                Map.entry("name", "P1"),
                Map.entry("size", "P1"),
                Map.entry("tier", "Premium")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const appServicePlan = new azure_native.web.AppServicePlan("appServicePlan", {
    kind: "app",
    location: "East US",
    name: "testsf6141",
    resourceGroupName: "testrg123",
    sku: {
        capacity: 1,
        family: "P",
        name: "P1",
        size: "P1",
        tier: "Premium",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

app_service_plan = azure_native.web.AppServicePlan("appServicePlan",
    kind="app",
    location="East US",
    name="testsf6141",
    resource_group_name="testrg123",
    sku=azure_native.web.SkuDescriptionArgs(
        capacity=1,
        family="P",
        name="P1",
        size="P1",
        tier="Premium",
    ))

```

```yaml
resources:
  appServicePlan:
    type: azure-native:web:AppServicePlan
    properties:
      kind: app
      location: East US
      name: testsf6141
      resourceGroupName: testrg123
      sku:
        capacity: 1
        family: P
        name: P1
        size: P1
        tier: Premium

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:AppServicePlan testsf6141 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/serverfarms/testsf6141 
```
