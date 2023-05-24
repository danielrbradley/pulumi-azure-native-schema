Represents an instance of a DFP instance resource.
API Version: 2021-02-01-preview.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create instance
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var instanceDetails = new AzureNative.Dynamics365Fraudprotection.InstanceDetails("instanceDetails", new()
    {
        Administration = new AzureNative.Dynamics365Fraudprotection.Inputs.DFPInstanceAdministratorsArgs
        {
            Members = new[]
            {
                "azsdktest@microsoft.com",
                "azsdktest2@microsoft.com",
            },
        },
        InstanceName = "azsdktest",
        Location = "West US",
        ResourceGroupName = "TestRG",
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
	dynamics365fraudprotection "github.com/pulumi/pulumi-azure-native-sdk/dynamics365fraudprotection"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dynamics365fraudprotection.NewInstanceDetails(ctx, "instanceDetails", &dynamics365fraudprotection.InstanceDetailsArgs{
			Administration: &dynamics365fraudprotection.DFPInstanceAdministratorsArgs{
				Members: pulumi.StringArray{
					pulumi.String("azsdktest@microsoft.com"),
					pulumi.String("azsdktest2@microsoft.com"),
				},
			},
			InstanceName:      pulumi.String("azsdktest"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("TestRG"),
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
import com.pulumi.azurenative.dynamics365fraudprotection.InstanceDetails;
import com.pulumi.azurenative.dynamics365fraudprotection.InstanceDetailsArgs;
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
        var instanceDetails = new InstanceDetails("instanceDetails", InstanceDetailsArgs.builder()        
            .administration(Map.of("members",             
                "azsdktest@microsoft.com",
                "azsdktest2@microsoft.com"))
            .instanceName("azsdktest")
            .location("West US")
            .resourceGroupName("TestRG")
            .tags(Map.of("testKey", "testValue"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const instanceDetails = new azure_native.dynamics365fraudprotection.InstanceDetails("instanceDetails", {
    administration: {
        members: [
            "azsdktest@microsoft.com",
            "azsdktest2@microsoft.com",
        ],
    },
    instanceName: "azsdktest",
    location: "West US",
    resourceGroupName: "TestRG",
    tags: {
        testKey: "testValue",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

instance_details = azure_native.dynamics365fraudprotection.InstanceDetails("instanceDetails",
    administration=azure_native.dynamics365fraudprotection.DFPInstanceAdministratorsArgs(
        members=[
            "azsdktest@microsoft.com",
            "azsdktest2@microsoft.com",
        ],
    ),
    instance_name="azsdktest",
    location="West US",
    resource_group_name="TestRG",
    tags={
        "testKey": "testValue",
    })

```

```yaml
resources:
  instanceDetails:
    type: azure-native:dynamics365fraudprotection:InstanceDetails
    properties:
      administration:
        members:
          - azsdktest@microsoft.com
          - azsdktest2@microsoft.com
      instanceName: azsdktest
      location: West US
      resourceGroupName: TestRG
      tags:
        testKey: testValue

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dynamics365fraudprotection:InstanceDetails azsdktest /subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.Dynamics365Fraudprotection/instances/azsdktest 
```
