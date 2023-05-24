An Azure Video Indexer account.
API Version: 2022-08-01.
Previous API Version: 2021-10-18-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put example #9
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.VideoIndexer.Account("account", new()
    {
        AccountName = "contosto-videoanalyzer",
        ResourceGroupName = "contosto-videoanalyzer-rg",
    });

});


```

```go
package main

import (
	videoindexer "github.com/pulumi/pulumi-azure-native-sdk/videoindexer"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := videoindexer.NewAccount(ctx, "account", &videoindexer.AccountArgs{
			AccountName:       pulumi.String("contosto-videoanalyzer"),
			ResourceGroupName: pulumi.String("contosto-videoanalyzer-rg"),
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
import com.pulumi.azurenative.videoindexer.Account;
import com.pulumi.azurenative.videoindexer.AccountArgs;
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
            .accountName("contosto-videoanalyzer")
            .resourceGroupName("contosto-videoanalyzer-rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.videoindexer.Account("account", {
    accountName: "contosto-videoanalyzer",
    resourceGroupName: "contosto-videoanalyzer-rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.videoindexer.Account("account",
    account_name="contosto-videoanalyzer",
    resource_group_name="contosto-videoanalyzer-rg")

```

```yaml
resources:
  account:
    type: azure-native:videoindexer:Account
    properties:
      accountName: contosto-videoanalyzer
      resourceGroupName: contosto-videoanalyzer-rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:videoindexer:Account contosto-videoanalyzer /subscriptions/586d4f48-8f08-4a4e-96b7-e1892d6dba9e/resourceGroups/contoso-videoanalyzer-rg/providers/Microsoft.VideoIndexer/accounts/contosto-videoanalyzer 
```
