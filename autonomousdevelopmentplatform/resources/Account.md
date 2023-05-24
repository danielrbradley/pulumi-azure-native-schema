ADP account
API Version: 2021-11-01-preview.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put account
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.AutonomousDevelopmentPlatform.Account("account", new()
    {
        AccountName = "sampleacct",
        Location = "Global",
        ResourceGroupName = "adpClient",
    });

});


```

```go
package main

import (
	autonomousdevelopmentplatform "github.com/pulumi/pulumi-azure-native-sdk/autonomousdevelopmentplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := autonomousdevelopmentplatform.NewAccount(ctx, "account", &autonomousdevelopmentplatform.AccountArgs{
			AccountName:       pulumi.String("sampleacct"),
			Location:          pulumi.String("Global"),
			ResourceGroupName: pulumi.String("adpClient"),
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
import com.pulumi.azurenative.autonomousdevelopmentplatform.Account;
import com.pulumi.azurenative.autonomousdevelopmentplatform.AccountArgs;
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
            .accountName("sampleacct")
            .location("Global")
            .resourceGroupName("adpClient")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.autonomousdevelopmentplatform.Account("account", {
    accountName: "sampleacct",
    location: "Global",
    resourceGroupName: "adpClient",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.autonomousdevelopmentplatform.Account("account",
    account_name="sampleacct",
    location="Global",
    resource_group_name="adpClient")

```

```yaml
resources:
  account:
    type: azure-native:autonomousdevelopmentplatform:Account
    properties:
      accountName: sampleacct
      location: Global
      resourceGroupName: adpClient

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:autonomousdevelopmentplatform:Account adp1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.AutonomousDevelopmentPlatform/accounts/adp1 
```
