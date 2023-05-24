Account details
API Version: 2022-09-22-preview.
Previous API Version: 2022-09-22-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Account resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.GraphServices.Account("account", new()
    {
        Properties = new AzureNative.GraphServices.Inputs.AccountResourcePropertiesArgs
        {
            AppId = "11111111-aaaa-1111-bbbb-111111111111",
        },
        ResourceGroupName = "testResourceGroupGRAM",
        ResourceName = "11111111-aaaa-1111-bbbb-1111111111111",
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
    });

});


```

```go
package main

import (
	graphservices "github.com/pulumi/pulumi-azure-native-sdk/graphservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := graphservices.NewAccount(ctx, "account", &graphservices.AccountArgs{
			Properties: &graphservices.AccountResourcePropertiesArgs{
				AppId: pulumi.String("11111111-aaaa-1111-bbbb-111111111111"),
			},
			ResourceGroupName: pulumi.String("testResourceGroupGRAM"),
			ResourceName:      pulumi.String("11111111-aaaa-1111-bbbb-1111111111111"),
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
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
import com.pulumi.azurenative.graphservices.Account;
import com.pulumi.azurenative.graphservices.AccountArgs;
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
        var account = new Account("account", AccountArgs.builder()        
            .properties(Map.of("appId", "11111111-aaaa-1111-bbbb-111111111111"))
            .resourceGroupName("testResourceGroupGRAM")
            .resourceName("11111111-aaaa-1111-bbbb-1111111111111")
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.graphservices.Account("account", {
    properties: {
        appId: "11111111-aaaa-1111-bbbb-111111111111",
    },
    resourceGroupName: "testResourceGroupGRAM",
    resourceName: "11111111-aaaa-1111-bbbb-1111111111111",
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.graphservices.Account("account",
    properties=azure_native.graphservices.AccountResourcePropertiesArgs(
        app_id="11111111-aaaa-1111-bbbb-111111111111",
    ),
    resource_group_name="testResourceGroupGRAM",
    resource_name_="11111111-aaaa-1111-bbbb-1111111111111",
    tags={
        "tag1": "value1",
        "tag2": "value2",
    })

```

```yaml
resources:
  account:
    type: azure-native:graphservices:Account
    properties:
      properties:
        appId: 11111111-aaaa-1111-bbbb-111111111111
      resourceGroupName: testResourceGroupGRAM
      resourceName: 11111111-aaaa-1111-bbbb-1111111111111
      tags:
        tag1: value1
        tag2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:graphservices:Account 11111111-aaaa-1111-bbbb-111111111111 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/testResourceGroupGRAM/providers/Microsoft.GraphServices/accounts/11111111-aaaa-1111-bbbb-111111111111 
```
