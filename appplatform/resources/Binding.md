Binding resource payload
API Version: 2022-12-01.
Previous API Version: 2020-07-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Bindings_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var binding = new AzureNative.AppPlatform.Binding("binding", new()
    {
        AppName = "myapp",
        BindingName = "mybinding",
        Properties = new AzureNative.AppPlatform.Inputs.BindingResourcePropertiesArgs
        {
            BindingParameters = 
            {
                { "apiType", "SQL" },
                { "databaseName", "db1" },
            },
            Key = "xxxx",
            ResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.DocumentDB/databaseAccounts/my-cosmosdb-1",
        },
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
    });

});


```

```go
package main

import (
	appplatform "github.com/pulumi/pulumi-azure-native-sdk/appplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appplatform.NewBinding(ctx, "binding", &appplatform.BindingArgs{
			AppName:     pulumi.String("myapp"),
			BindingName: pulumi.String("mybinding"),
			Properties: &appplatform.BindingResourcePropertiesArgs{
				BindingParameters: pulumi.StringMap{
					"apiType":      pulumi.String("SQL"),
					"databaseName": pulumi.String("db1"),
				},
				Key:        pulumi.String("xxxx"),
				ResourceId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.DocumentDB/databaseAccounts/my-cosmosdb-1"),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ServiceName:       pulumi.String("myservice"),
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
import com.pulumi.azurenative.appplatform.Binding;
import com.pulumi.azurenative.appplatform.BindingArgs;
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
        var binding = new Binding("binding", BindingArgs.builder()        
            .appName("myapp")
            .bindingName("mybinding")
            .properties(Map.ofEntries(
                Map.entry("bindingParameters", Map.ofEntries(
                    Map.entry("apiType", "SQL"),
                    Map.entry("databaseName", "db1")
                )),
                Map.entry("key", "xxxx"),
                Map.entry("resourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.DocumentDB/databaseAccounts/my-cosmosdb-1")
            ))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const binding = new azure_native.appplatform.Binding("binding", {
    appName: "myapp",
    bindingName: "mybinding",
    properties: {
        bindingParameters: {
            apiType: "SQL",
            databaseName: "db1",
        },
        key: "xxxx",
        resourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.DocumentDB/databaseAccounts/my-cosmosdb-1",
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

binding = azure_native.appplatform.Binding("binding",
    app_name="myapp",
    binding_name="mybinding",
    properties=azure_native.appplatform.BindingResourcePropertiesArgs(
        binding_parameters={
            "apiType": "SQL",
            "databaseName": "db1",
        },
        key="xxxx",
        resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.DocumentDB/databaseAccounts/my-cosmosdb-1",
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice")

```

```yaml
resources:
  binding:
    type: azure-native:appplatform:Binding
    properties:
      appName: myapp
      bindingName: mybinding
      properties:
        bindingParameters:
          apiType: SQL
          databaseName: db1
        key: xxxx
        resourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.DocumentDB/databaseAccounts/my-cosmosdb-1
      resourceGroupName: myResourceGroup
      serviceName: myservice

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:Binding mybinding /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/apps/myapp/bindings/mybinding 
```
