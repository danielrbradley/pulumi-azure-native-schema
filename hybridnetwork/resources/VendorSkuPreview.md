Customer subscription which can use a sku.
API Version: 2021-05-01.
Previous API Version: 2020-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update preview subscription of vendor sku sub resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vendorSkuPreview = new AzureNative.HybridNetwork.VendorSkuPreview("vendorSkuPreview", new()
    {
        PreviewSubscription = "previewSub",
        SkuName = "TestSku",
        VendorName = "TestVendor",
    });

});


```

```go
package main

import (
	hybridnetwork "github.com/pulumi/pulumi-azure-native-sdk/hybridnetwork"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridnetwork.NewVendorSkuPreview(ctx, "vendorSkuPreview", &hybridnetwork.VendorSkuPreviewArgs{
			PreviewSubscription: pulumi.String("previewSub"),
			SkuName:             pulumi.String("TestSku"),
			VendorName:          pulumi.String("TestVendor"),
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
import com.pulumi.azurenative.hybridnetwork.VendorSkuPreview;
import com.pulumi.azurenative.hybridnetwork.VendorSkuPreviewArgs;
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
        var vendorSkuPreview = new VendorSkuPreview("vendorSkuPreview", VendorSkuPreviewArgs.builder()        
            .previewSubscription("previewSub")
            .skuName("TestSku")
            .vendorName("TestVendor")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vendorSkuPreview = new azure_native.hybridnetwork.VendorSkuPreview("vendorSkuPreview", {
    previewSubscription: "previewSub",
    skuName: "TestSku",
    vendorName: "TestVendor",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

vendor_sku_preview = azure_native.hybridnetwork.VendorSkuPreview("vendorSkuPreview",
    preview_subscription="previewSub",
    sku_name="TestSku",
    vendor_name="TestVendor")

```

```yaml
resources:
  vendorSkuPreview:
    type: azure-native:hybridnetwork:VendorSkuPreview
    properties:
      previewSubscription: previewSub
      skuName: TestSku
      vendorName: TestVendor

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridnetwork:VendorSkuPreview previewSub /subscriptions/subid/providers/Microsoft.HybridNetwork/vendors/TestVendor/vendorskus/TestSku/previewsubscriptions/previewSub 
```
