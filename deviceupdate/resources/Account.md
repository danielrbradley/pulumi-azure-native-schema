Device Update account details.
API Version: 2022-10-01.
Previous API Version: 2020-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates Account
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.DeviceUpdate.Account("account", new()
    {
        AccountName = "contoso",
        Location = "westus2",
        ResourceGroupName = "test-rg",
    });

});


```

```go
package main

import (
	deviceupdate "github.com/pulumi/pulumi-azure-native-sdk/deviceupdate"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := deviceupdate.NewAccount(ctx, "account", &deviceupdate.AccountArgs{
			AccountName:       pulumi.String("contoso"),
			Location:          pulumi.String("westus2"),
			ResourceGroupName: pulumi.String("test-rg"),
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
import com.pulumi.azurenative.deviceupdate.Account;
import com.pulumi.azurenative.deviceupdate.AccountArgs;
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
            .accountName("contoso")
            .location("westus2")
            .resourceGroupName("test-rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.deviceupdate.Account("account", {
    accountName: "contoso",
    location: "westus2",
    resourceGroupName: "test-rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.deviceupdate.Account("account",
    account_name="contoso",
    location="westus2",
    resource_group_name="test-rg")

```

```yaml
resources:
  account:
    type: azure-native:deviceupdate:Account
    properties:
      accountName: contoso
      location: westus2
      resourceGroupName: test-rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:deviceupdate:Account contoso /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DeviceUpdate/accounts/contoso 
```
