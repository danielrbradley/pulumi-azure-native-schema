An Asset.
API Version: 2022-08-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create an Asset
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var asset = new AzureNative.Media.Asset("asset", new()
    {
        AccountName = "contosomedia",
        AssetName = "ClimbingMountLogan",
        Description = "A documentary showing the ascent of Mount Logan",
        ResourceGroupName = "contosorg",
        StorageAccountName = "storage0",
    });

});


```

```go
package main

import (
	media "github.com/pulumi/pulumi-azure-native-sdk/media"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := media.NewAsset(ctx, "asset", &media.AssetArgs{
			AccountName:        pulumi.String("contosomedia"),
			AssetName:          pulumi.String("ClimbingMountLogan"),
			Description:        pulumi.String("A documentary showing the ascent of Mount Logan"),
			ResourceGroupName:  pulumi.String("contosorg"),
			StorageAccountName: pulumi.String("storage0"),
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
import com.pulumi.azurenative.media.Asset;
import com.pulumi.azurenative.media.AssetArgs;
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
        var asset = new Asset("asset", AssetArgs.builder()        
            .accountName("contosomedia")
            .assetName("ClimbingMountLogan")
            .description("A documentary showing the ascent of Mount Logan")
            .resourceGroupName("contosorg")
            .storageAccountName("storage0")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const asset = new azure_native.media.Asset("asset", {
    accountName: "contosomedia",
    assetName: "ClimbingMountLogan",
    description: "A documentary showing the ascent of Mount Logan",
    resourceGroupName: "contosorg",
    storageAccountName: "storage0",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

asset = azure_native.media.Asset("asset",
    account_name="contosomedia",
    asset_name="ClimbingMountLogan",
    description="A documentary showing the ascent of Mount Logan",
    resource_group_name="contosorg",
    storage_account_name="storage0")

```

```yaml
resources:
  asset:
    type: azure-native:media:Asset
    properties:
      accountName: contosomedia
      assetName: ClimbingMountLogan
      description: A documentary showing the ascent of Mount Logan
      resourceGroupName: contosorg
      storageAccountName: storage0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:media:Asset ClimbingMountLogan /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosorg/providers/Microsoft.Media/mediaservices/contosomedia/assets/ClimbingMountLogan 
```
