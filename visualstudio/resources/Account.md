The response to an account resource GET request.
API Version: 2017-11-01-preview.
Previous API Version: 2014-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create an account resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.VisualStudio.Account("account", new()
    {
        AccountName = "Example",
        Location = "Central US",
        OperationType = "create",
        Properties = null,
        ResourceGroupName = "VS-Example-Group",
        ResourceName = "Example",
        Tags = null,
    });

});


```

```go
package main

import (
	visualstudio "github.com/pulumi/pulumi-azure-native-sdk/visualstudio"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := visualstudio.NewAccount(ctx, "account", &visualstudio.AccountArgs{
			AccountName:       pulumi.String("Example"),
			Location:          pulumi.String("Central US"),
			OperationType:     pulumi.String("create"),
			Properties:        nil,
			ResourceGroupName: pulumi.String("VS-Example-Group"),
			ResourceName:      pulumi.String("Example"),
			Tags:              nil,
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
import com.pulumi.azurenative.visualstudio.Account;
import com.pulumi.azurenative.visualstudio.AccountArgs;
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
            .accountName("Example")
            .location("Central US")
            .operationType("create")
            .properties()
            .resourceGroupName("VS-Example-Group")
            .resourceName("Example")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.visualstudio.Account("account", {
    accountName: "Example",
    location: "Central US",
    operationType: "create",
    properties: {},
    resourceGroupName: "VS-Example-Group",
    resourceName: "Example",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.visualstudio.Account("account",
    account_name="Example",
    location="Central US",
    operation_type="create",
    properties={},
    resource_group_name="VS-Example-Group",
    resource_name_="Example",
    tags={})

```

```yaml
resources:
  account:
    type: azure-native:visualstudio:Account
    properties:
      accountName: Example
      location: Central US
      operationType: create
      properties: {}
      resourceGroupName: VS-Example-Group
      resourceName: Example
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:visualstudio:Account VS-Example-Group /subscriptions/0de7f055-dbea-498d-8e9e-da287eedca90/resourceGroups/VS-Example-Group/providers/Microsoft.VisualStudio/account/Example 
```
