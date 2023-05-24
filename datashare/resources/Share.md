A share data transfer object.
API Version: 2021-08-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Shares_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var share = new AzureNative.DataShare.Share("share", new()
    {
        AccountName = "Account1",
        Description = "share description",
        ResourceGroupName = "SampleResourceGroup",
        ShareKind = "CopyBased",
        ShareName = "Share1",
        Terms = "Confidential",
    });

});


```

```go
package main

import (
	datashare "github.com/pulumi/pulumi-azure-native-sdk/datashare"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datashare.NewShare(ctx, "share", &datashare.ShareArgs{
			AccountName:       pulumi.String("Account1"),
			Description:       pulumi.String("share description"),
			ResourceGroupName: pulumi.String("SampleResourceGroup"),
			ShareKind:         pulumi.String("CopyBased"),
			ShareName:         pulumi.String("Share1"),
			Terms:             pulumi.String("Confidential"),
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
import com.pulumi.azurenative.datashare.Share;
import com.pulumi.azurenative.datashare.ShareArgs;
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
        var share = new Share("share", ShareArgs.builder()        
            .accountName("Account1")
            .description("share description")
            .resourceGroupName("SampleResourceGroup")
            .shareKind("CopyBased")
            .shareName("Share1")
            .terms("Confidential")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const share = new azure_native.datashare.Share("share", {
    accountName: "Account1",
    description: "share description",
    resourceGroupName: "SampleResourceGroup",
    shareKind: "CopyBased",
    shareName: "Share1",
    terms: "Confidential",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

share = azure_native.datashare.Share("share",
    account_name="Account1",
    description="share description",
    resource_group_name="SampleResourceGroup",
    share_kind="CopyBased",
    share_name="Share1",
    terms="Confidential")

```

```yaml
resources:
  share:
    type: azure-native:datashare:Share
    properties:
      accountName: Account1
      description: share description
      resourceGroupName: SampleResourceGroup
      shareKind: CopyBased
      shareName: Share1
      terms: Confidential

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datashare:Share Share1 /subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.DataShare/accounts/Account1/shares/Share1 
```
