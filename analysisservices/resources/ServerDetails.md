Represents an instance of an Analysis Services resource.
API Version: 2017-08-01.
Previous API Version: 2017-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a server.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serverDetails = new AzureNative.AnalysisServices.ServerDetails("serverDetails", new()
    {
        AsAdministrators = new AzureNative.AnalysisServices.Inputs.ServerAdministratorsArgs
        {
            Members = new[]
            {
                "azsdktest@microsoft.com",
                "azsdktest2@microsoft.com",
            },
        },
        Location = "West US",
        ResourceGroupName = "TestRG",
        ServerName = "azsdktest",
        Sku = new AzureNative.AnalysisServices.Inputs.ResourceSkuArgs
        {
            Capacity = 1,
            Name = "S1",
            Tier = "Standard",
        },
        Tags = 
        {
            { "testKey", "testValue" },
        },
    });

});


```

```go
package main

import (
	analysisservices "github.com/pulumi/pulumi-azure-native-sdk/analysisservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := analysisservices.NewServerDetails(ctx, "serverDetails", &analysisservices.ServerDetailsArgs{
			AsAdministrators: &analysisservices.ServerAdministratorsArgs{
				Members: pulumi.StringArray{
					pulumi.String("azsdktest@microsoft.com"),
					pulumi.String("azsdktest2@microsoft.com"),
				},
			},
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("TestRG"),
			ServerName:        pulumi.String("azsdktest"),
			Sku: &analysisservices.ResourceSkuArgs{
				Capacity: pulumi.Int(1),
				Name:     pulumi.String("S1"),
				Tier:     pulumi.String("Standard"),
			},
			Tags: pulumi.StringMap{
				"testKey": pulumi.String("testValue"),
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
import com.pulumi.azurenative.analysisservices.ServerDetails;
import com.pulumi.azurenative.analysisservices.ServerDetailsArgs;
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
        var serverDetails = new ServerDetails("serverDetails", ServerDetailsArgs.builder()        
            .asAdministrators(Map.of("members",             
                "azsdktest@microsoft.com",
                "azsdktest2@microsoft.com"))
            .location("West US")
            .resourceGroupName("TestRG")
            .serverName("azsdktest")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("name", "S1"),
                Map.entry("tier", "Standard")
            ))
            .tags(Map.of("testKey", "testValue"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverDetails = new azure_native.analysisservices.ServerDetails("serverDetails", {
    asAdministrators: {
        members: [
            "azsdktest@microsoft.com",
            "azsdktest2@microsoft.com",
        ],
    },
    location: "West US",
    resourceGroupName: "TestRG",
    serverName: "azsdktest",
    sku: {
        capacity: 1,
        name: "S1",
        tier: "Standard",
    },
    tags: {
        testKey: "testValue",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_details = azure_native.analysisservices.ServerDetails("serverDetails",
    as_administrators=azure_native.analysisservices.ServerAdministratorsArgs(
        members=[
            "azsdktest@microsoft.com",
            "azsdktest2@microsoft.com",
        ],
    ),
    location="West US",
    resource_group_name="TestRG",
    server_name="azsdktest",
    sku=azure_native.analysisservices.ResourceSkuArgs(
        capacity=1,
        name="S1",
        tier="Standard",
    ),
    tags={
        "testKey": "testValue",
    })

```

```yaml
resources:
  serverDetails:
    type: azure-native:analysisservices:ServerDetails
    properties:
      asAdministrators:
        members:
          - azsdktest@microsoft.com
          - azsdktest2@microsoft.com
      location: West US
      resourceGroupName: TestRG
      serverName: azsdktest
      sku:
        capacity: 1
        name: S1
        tier: Standard
      tags:
        testKey: testValue

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:analysisservices:ServerDetails azsdktest /subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.AnalysisServices/servers/azsdktest 
```
