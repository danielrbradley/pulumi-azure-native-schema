Azure Data Catalog.
API Version: 2016-03-30.
Previous API Version: 2016-03-30. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Azure Data Catalog Service
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var adcCatalog = new AzureNative.DataCatalog.ADCCatalog("adcCatalog", new()
    {
        Admins = new[]
        {
            new AzureNative.DataCatalog.Inputs.PrincipalsArgs
            {
                ObjectId = "99999999-9999-9999-999999999999",
                Upn = "myupn@microsoft.com",
            },
        },
        CatalogName = "exampleCatalog",
        EnableAutomaticUnitAdjustment = false,
        Location = "North US",
        ResourceGroupName = "exampleResourceGroup",
        Sku = "Standard",
        Tags = 
        {
            { "mykey", "myvalue" },
            { "mykey2", "myvalue2" },
        },
        Units = 1,
        Users = new[]
        {
            new AzureNative.DataCatalog.Inputs.PrincipalsArgs
            {
                ObjectId = "99999999-9999-9999-999999999999",
                Upn = "myupn@microsoft.com",
            },
        },
    });

});


```

```go
package main

import (
	datacatalog "github.com/pulumi/pulumi-azure-native-sdk/datacatalog"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datacatalog.NewADCCatalog(ctx, "adcCatalog", &datacatalog.ADCCatalogArgs{
			Admins: []datacatalog.PrincipalsArgs{
				{
					ObjectId: pulumi.String("99999999-9999-9999-999999999999"),
					Upn:      pulumi.String("myupn@microsoft.com"),
				},
			},
			CatalogName:                   pulumi.String("exampleCatalog"),
			EnableAutomaticUnitAdjustment: pulumi.Bool(false),
			Location:                      pulumi.String("North US"),
			ResourceGroupName:             pulumi.String("exampleResourceGroup"),
			Sku:                           pulumi.String("Standard"),
			Tags: pulumi.StringMap{
				"mykey":  pulumi.String("myvalue"),
				"mykey2": pulumi.String("myvalue2"),
			},
			Units: pulumi.Int(1),
			Users: []datacatalog.PrincipalsArgs{
				{
					ObjectId: pulumi.String("99999999-9999-9999-999999999999"),
					Upn:      pulumi.String("myupn@microsoft.com"),
				},
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
import com.pulumi.azurenative.datacatalog.ADCCatalog;
import com.pulumi.azurenative.datacatalog.ADCCatalogArgs;
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
        var adcCatalog = new ADCCatalog("adcCatalog", ADCCatalogArgs.builder()        
            .admins(Map.ofEntries(
                Map.entry("objectId", "99999999-9999-9999-999999999999"),
                Map.entry("upn", "myupn@microsoft.com")
            ))
            .catalogName("exampleCatalog")
            .enableAutomaticUnitAdjustment(false)
            .location("North US")
            .resourceGroupName("exampleResourceGroup")
            .sku("Standard")
            .tags(Map.ofEntries(
                Map.entry("mykey", "myvalue"),
                Map.entry("mykey2", "myvalue2")
            ))
            .units(1)
            .users(Map.ofEntries(
                Map.entry("objectId", "99999999-9999-9999-999999999999"),
                Map.entry("upn", "myupn@microsoft.com")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const adcCatalog = new azure_native.datacatalog.ADCCatalog("adcCatalog", {
    admins: [{
        objectId: "99999999-9999-9999-999999999999",
        upn: "myupn@microsoft.com",
    }],
    catalogName: "exampleCatalog",
    enableAutomaticUnitAdjustment: false,
    location: "North US",
    resourceGroupName: "exampleResourceGroup",
    sku: "Standard",
    tags: {
        mykey: "myvalue",
        mykey2: "myvalue2",
    },
    units: 1,
    users: [{
        objectId: "99999999-9999-9999-999999999999",
        upn: "myupn@microsoft.com",
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adc_catalog = azure_native.datacatalog.ADCCatalog("adcCatalog",
    admins=[azure_native.datacatalog.PrincipalsArgs(
        object_id="99999999-9999-9999-999999999999",
        upn="myupn@microsoft.com",
    )],
    catalog_name="exampleCatalog",
    enable_automatic_unit_adjustment=False,
    location="North US",
    resource_group_name="exampleResourceGroup",
    sku="Standard",
    tags={
        "mykey": "myvalue",
        "mykey2": "myvalue2",
    },
    units=1,
    users=[azure_native.datacatalog.PrincipalsArgs(
        object_id="99999999-9999-9999-999999999999",
        upn="myupn@microsoft.com",
    )])

```

```yaml
resources:
  adcCatalog:
    type: azure-native:datacatalog:ADCCatalog
    properties:
      admins:
        - objectId: 99999999-9999-9999-999999999999
          upn: myupn@microsoft.com
      catalogName: exampleCatalog
      enableAutomaticUnitAdjustment: false
      location: North US
      resourceGroupName: exampleResourceGroup
      sku: Standard
      tags:
        mykey: myvalue
        mykey2: myvalue2
      units: 1
      users:
        - objectId: 99999999-9999-9999-999999999999
          upn: myupn@microsoft.com

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datacatalog:ADCCatalog exampleCatalog /subscriptions/12345678-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataCatalog/catalogs/exampleCatalog 
```
