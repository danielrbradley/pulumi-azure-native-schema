Modeling resource details.
API Version: 2022-02-01.
Previous API Version: 2022-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update Modeling resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var modeling = new AzureNative.RecommendationsService.Modeling("modeling", new()
    {
        AccountName = "sampleAccount",
        Location = "West US",
        ModelingName = "c1",
        Properties = new AzureNative.RecommendationsService.Inputs.ModelingResourcePropertiesArgs
        {
            Features = "Standard",
            Frequency = "High",
            InputData = new AzureNative.RecommendationsService.Inputs.ModelingInputDataArgs
            {
                ConnectionString = "https://storageAccount.blob.core.windows.net/container/root",
            },
            Size = "Medium",
        },
        ResourceGroupName = "rg",
        Tags = 
        {
            { "Environment", "Prod" },
        },
    });

});


```

```go
package main

import (
	recommendationsservice "github.com/pulumi/pulumi-azure-native-sdk/recommendationsservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recommendationsservice.NewModeling(ctx, "modeling", &recommendationsservice.ModelingArgs{
			AccountName:  pulumi.String("sampleAccount"),
			Location:     pulumi.String("West US"),
			ModelingName: pulumi.String("c1"),
			Properties: recommendationsservice.ModelingResourceResponseProperties{
				Features:  pulumi.String("Standard"),
				Frequency: pulumi.String("High"),
				InputData: &recommendationsservice.ModelingInputDataArgs{
					ConnectionString: pulumi.String("https://storageAccount.blob.core.windows.net/container/root"),
				},
				Size: pulumi.String("Medium"),
			},
			ResourceGroupName: pulumi.String("rg"),
			Tags: pulumi.StringMap{
				"Environment": pulumi.String("Prod"),
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
import com.pulumi.azurenative.recommendationsservice.Modeling;
import com.pulumi.azurenative.recommendationsservice.ModelingArgs;
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
        var modeling = new Modeling("modeling", ModelingArgs.builder()        
            .accountName("sampleAccount")
            .location("West US")
            .modelingName("c1")
            .properties(Map.ofEntries(
                Map.entry("features", "Standard"),
                Map.entry("frequency", "High"),
                Map.entry("inputData", Map.of("connectionString", "https://storageAccount.blob.core.windows.net/container/root")),
                Map.entry("size", "Medium")
            ))
            .resourceGroupName("rg")
            .tags(Map.of("Environment", "Prod"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const modeling = new azure_native.recommendationsservice.Modeling("modeling", {
    accountName: "sampleAccount",
    location: "West US",
    modelingName: "c1",
    properties: {
        features: "Standard",
        frequency: "High",
        inputData: {
            connectionString: "https://storageAccount.blob.core.windows.net/container/root",
        },
        size: "Medium",
    },
    resourceGroupName: "rg",
    tags: {
        Environment: "Prod",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

modeling = azure_native.recommendationsservice.Modeling("modeling",
    account_name="sampleAccount",
    location="West US",
    modeling_name="c1",
    properties=azure_native.recommendationsservice.ModelingResourceResponsePropertiesArgs(
        features="Standard",
        frequency="High",
        input_data=azure_native.recommendationsservice.ModelingInputDataArgs(
            connection_string="https://storageAccount.blob.core.windows.net/container/root",
        ),
        size="Medium",
    ),
    resource_group_name="rg",
    tags={
        "Environment": "Prod",
    })

```

```yaml
resources:
  modeling:
    type: azure-native:recommendationsservice:Modeling
    properties:
      accountName: sampleAccount
      location: West US
      modelingName: c1
      properties:
        features: Standard
        frequency: High
        inputData:
          connectionString: https://storageAccount.blob.core.windows.net/container/root
        size: Medium
      resourceGroupName: rg
      tags:
        Environment: Prod

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recommendationsservice:Modeling c1 /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/rg/providers/Microsoft.RecommendationsService/accounts/sampleAccount/modeling/c1 
```
