Resource information with extended details.
API Version: 2023-02-01.
Previous API Version: 2021-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a new managed HSM Pool or update an existing managed HSM Pool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedHsm = new AzureNative.KeyVault.ManagedHsm("managedHsm", new()
    {
        Location = "westus",
        Name = "hsm1",
        Properties = new AzureNative.KeyVault.Inputs.ManagedHsmPropertiesArgs
        {
            EnablePurgeProtection = false,
            EnableSoftDelete = true,
            InitialAdminObjectIds = new[]
            {
                "00000000-0000-0000-0000-000000000000",
            },
            SoftDeleteRetentionInDays = 90,
            TenantId = "00000000-0000-0000-0000-000000000000",
        },
        ResourceGroupName = "hsm-group",
        Sku = new AzureNative.KeyVault.Inputs.ManagedHsmSkuArgs
        {
            Family = "B",
            Name = AzureNative.KeyVault.ManagedHsmSkuName.Standard_B1,
        },
        Tags = 
        {
            { "Dept", "hsm" },
            { "Environment", "dogfood" },
        },
    });

});


```

```go
package main

import (
	keyvault "github.com/pulumi/pulumi-azure-native-sdk/keyvault"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := keyvault.NewManagedHsm(ctx, "managedHsm", &keyvault.ManagedHsmArgs{
			Location: pulumi.String("westus"),
			Name:     pulumi.String("hsm1"),
			Properties: &keyvault.ManagedHsmPropertiesArgs{
				EnablePurgeProtection: pulumi.Bool(false),
				EnableSoftDelete:      pulumi.Bool(true),
				InitialAdminObjectIds: pulumi.StringArray{
					pulumi.String("00000000-0000-0000-0000-000000000000"),
				},
				SoftDeleteRetentionInDays: pulumi.Int(90),
				TenantId:                  pulumi.String("00000000-0000-0000-0000-000000000000"),
			},
			ResourceGroupName: pulumi.String("hsm-group"),
			Sku: &keyvault.ManagedHsmSkuArgs{
				Family: pulumi.String("B"),
				Name:   keyvault.ManagedHsmSkuName_Standard_B1,
			},
			Tags: pulumi.StringMap{
				"Dept":        pulumi.String("hsm"),
				"Environment": pulumi.String("dogfood"),
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
import com.pulumi.azurenative.keyvault.ManagedHsm;
import com.pulumi.azurenative.keyvault.ManagedHsmArgs;
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
        var managedHsm = new ManagedHsm("managedHsm", ManagedHsmArgs.builder()        
            .location("westus")
            .name("hsm1")
            .properties(Map.ofEntries(
                Map.entry("enablePurgeProtection", false),
                Map.entry("enableSoftDelete", true),
                Map.entry("initialAdminObjectIds", "00000000-0000-0000-0000-000000000000"),
                Map.entry("softDeleteRetentionInDays", 90),
                Map.entry("tenantId", "00000000-0000-0000-0000-000000000000")
            ))
            .resourceGroupName("hsm-group")
            .sku(Map.ofEntries(
                Map.entry("family", "B"),
                Map.entry("name", "Standard_B1")
            ))
            .tags(Map.ofEntries(
                Map.entry("Dept", "hsm"),
                Map.entry("Environment", "dogfood")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedHsm = new azure_native.keyvault.ManagedHsm("managedHsm", {
    location: "westus",
    name: "hsm1",
    properties: {
        enablePurgeProtection: false,
        enableSoftDelete: true,
        initialAdminObjectIds: ["00000000-0000-0000-0000-000000000000"],
        softDeleteRetentionInDays: 90,
        tenantId: "00000000-0000-0000-0000-000000000000",
    },
    resourceGroupName: "hsm-group",
    sku: {
        family: "B",
        name: azure_native.keyvault.ManagedHsmSkuName.Standard_B1,
    },
    tags: {
        Dept: "hsm",
        Environment: "dogfood",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_hsm = azure_native.keyvault.ManagedHsm("managedHsm",
    location="westus",
    name="hsm1",
    properties=azure_native.keyvault.ManagedHsmPropertiesArgs(
        enable_purge_protection=False,
        enable_soft_delete=True,
        initial_admin_object_ids=["00000000-0000-0000-0000-000000000000"],
        soft_delete_retention_in_days=90,
        tenant_id="00000000-0000-0000-0000-000000000000",
    ),
    resource_group_name="hsm-group",
    sku=azure_native.keyvault.ManagedHsmSkuArgs(
        family="B",
        name=azure_native.keyvault.ManagedHsmSkuName.STANDARD_B1,
    ),
    tags={
        "Dept": "hsm",
        "Environment": "dogfood",
    })

```

```yaml
resources:
  managedHsm:
    type: azure-native:keyvault:ManagedHsm
    properties:
      location: westus
      name: hsm1
      properties:
        enablePurgeProtection: false
        enableSoftDelete: true
        initialAdminObjectIds:
          - 00000000-0000-0000-0000-000000000000
        softDeleteRetentionInDays: 90
        tenantId: 00000000-0000-0000-0000-000000000000
      resourceGroupName: hsm-group
      sku:
        family: B
        name: Standard_B1
      tags:
        Dept: hsm
        Environment: dogfood

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:keyvault:ManagedHsm hsm1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.KeyVault/managedHSMs/hsm1 
```
