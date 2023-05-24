API connection
API Version: 2016-06-01.
Previous API Version: 2016-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Replace a connection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var connection = new AzureNative.Web.Connection("connection", new()
    {
        ConnectionName = "testManagedApi",
        Properties = new AzureNative.Web.Inputs.ApiConnectionDefinitionPropertiesArgs
        {
            Api = new AzureNative.Web.Inputs.ApiReferenceArgs
            {
                Id = "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/providers/Microsoft.Web/locations/centralus/managedApis/testManagedApi",
            },
            CustomParameterValues = null,
            DisplayName = "testManagedApi",
            ParameterValues = null,
        },
        ResourceGroupName = "testResourceGroup",
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
		_, err := web.NewConnection(ctx, "connection", &web.ConnectionArgs{
			ConnectionName: pulumi.String("testManagedApi"),
			Properties: web.ApiConnectionDefinitionResponseProperties{
				Api: &web.ApiReferenceArgs{
					Id: pulumi.String("/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/providers/Microsoft.Web/locations/centralus/managedApis/testManagedApi"),
				},
				CustomParameterValues: nil,
				DisplayName:           pulumi.String("testManagedApi"),
				ParameterValues:       nil,
			},
			ResourceGroupName: pulumi.String("testResourceGroup"),
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
import com.pulumi.azurenative.web.Connection;
import com.pulumi.azurenative.web.ConnectionArgs;
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
        var connection = new Connection("connection", ConnectionArgs.builder()        
            .connectionName("testManagedApi")
            .properties(Map.ofEntries(
                Map.entry("api", Map.of("id", "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/providers/Microsoft.Web/locations/centralus/managedApis/testManagedApi")),
                Map.entry("customParameterValues", ),
                Map.entry("displayName", "testManagedApi"),
                Map.entry("parameterValues", )
            ))
            .resourceGroupName("testResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const connection = new azure_native.web.Connection("connection", {
    connectionName: "testManagedApi",
    properties: {
        api: {
            id: "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/providers/Microsoft.Web/locations/centralus/managedApis/testManagedApi",
        },
        customParameterValues: {},
        displayName: "testManagedApi",
        parameterValues: {},
    },
    resourceGroupName: "testResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

connection = azure_native.web.Connection("connection",
    connection_name="testManagedApi",
    properties=azure_native.web.ApiConnectionDefinitionResponsePropertiesArgs(
        api=azure_native.web.ApiReferenceArgs(
            id="/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/providers/Microsoft.Web/locations/centralus/managedApis/testManagedApi",
        ),
        custom_parameter_values={},
        display_name="testManagedApi",
        parameter_values={},
    ),
    resource_group_name="testResourceGroup")

```

```yaml
resources:
  connection:
    type: azure-native:web:Connection
    properties:
      connectionName: testManagedApi
      properties:
        api:
          id: /subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/providers/Microsoft.Web/locations/centralus/managedApis/testManagedApi
        customParameterValues: {}
        displayName: testManagedApi
        parameterValues: {}
      resourceGroupName: testResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:Connection testManagedApi-1 /subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Web/connections/testManagedApi-1 
```
