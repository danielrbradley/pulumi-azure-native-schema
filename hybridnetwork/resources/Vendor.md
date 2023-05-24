Vendor resource.
API Version: 2021-05-01.
Previous API Version: 2020-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update Vendor resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vendor = new AzureNative.HybridNetwork.Vendor("vendor", new()
    {
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
		_, err := hybridnetwork.NewVendor(ctx, "vendor", &hybridnetwork.VendorArgs{
			VendorName: pulumi.String("TestVendor"),
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
import com.pulumi.azurenative.hybridnetwork.Vendor;
import com.pulumi.azurenative.hybridnetwork.VendorArgs;
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
        var vendor = new Vendor("vendor", VendorArgs.builder()        
            .vendorName("TestVendor")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vendor = new azure_native.hybridnetwork.Vendor("vendor", {vendorName: "TestVendor"});

```

```python
import pulumi
import pulumi_azure_native as azure_native

vendor = azure_native.hybridnetwork.Vendor("vendor", vendor_name="TestVendor")

```

```yaml
resources:
  vendor:
    type: azure-native:hybridnetwork:Vendor
    properties:
      vendorName: TestVendor

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridnetwork:Vendor TestVendor /subscriptions/subid/providers/Microsoft.HybridNetwork/vendors/TestVendor 
```
