Extension resource.
API Version: 2021-09-01-preview.
Previous API Version: 2020-05-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Extensions_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var extension = new AzureNative.AgFoodPlatform.Extension("extension", new()
    {
        ExtensionId = "provider.extension",
        FarmBeatsResourceName = "examples-farmbeatsResourceName",
        ResourceGroupName = "examples-rg",
    });

});


```

```go
package main

import (
	agfoodplatform "github.com/pulumi/pulumi-azure-native-sdk/agfoodplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := agfoodplatform.NewExtension(ctx, "extension", &agfoodplatform.ExtensionArgs{
			ExtensionId:           pulumi.String("provider.extension"),
			FarmBeatsResourceName: pulumi.String("examples-farmbeatsResourceName"),
			ResourceGroupName:     pulumi.String("examples-rg"),
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
import com.pulumi.azurenative.agfoodplatform.Extension;
import com.pulumi.azurenative.agfoodplatform.ExtensionArgs;
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
        var extension = new Extension("extension", ExtensionArgs.builder()        
            .extensionId("provider.extension")
            .farmBeatsResourceName("examples-farmbeatsResourceName")
            .resourceGroupName("examples-rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const extension = new azure_native.agfoodplatform.Extension("extension", {
    extensionId: "provider.extension",
    farmBeatsResourceName: "examples-farmbeatsResourceName",
    resourceGroupName: "examples-rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

extension = azure_native.agfoodplatform.Extension("extension",
    extension_id="provider.extension",
    farm_beats_resource_name="examples-farmbeatsResourceName",
    resource_group_name="examples-rg")

```

```yaml
resources:
  extension:
    type: azure-native:agfoodplatform:Extension
    properties:
      extensionId: provider.extension
      farmBeatsResourceName: examples-farmbeatsResourceName
      resourceGroupName: examples-rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:agfoodplatform:Extension provider.extension /subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.AgFoodPlatform/farmBeats/examples-farmbeatsResourceName/extensions/provider.extension 
```
