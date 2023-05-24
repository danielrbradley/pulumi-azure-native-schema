ADP Data Pool
API Version: 2021-11-01-preview.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put Data Pool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataPool = new AzureNative.AutonomousDevelopmentPlatform.DataPool("dataPool", new()
    {
        AccountName = "sampleacct",
        DataPoolName = "sampledp",
        Locations = new[]
        {
            new AzureNative.AutonomousDevelopmentPlatform.Inputs.DataPoolLocationArgs
            {
                Encryption = new AzureNative.AutonomousDevelopmentPlatform.Inputs.DataPoolEncryptionArgs
                {
                    KeyName = "key1",
                    KeyVaultUri = "https://vaulturi",
                    KeyVersion = "123",
                    UserAssignedIdentity = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/id1",
                },
                Name = "westus",
            },
        },
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
		_, err := autonomousdevelopmentplatform.NewDataPool(ctx, "dataPool", &autonomousdevelopmentplatform.DataPoolArgs{
			AccountName:  pulumi.String("sampleacct"),
			DataPoolName: pulumi.String("sampledp"),
			Locations: []autonomousdevelopmentplatform.DataPoolLocationArgs{
				{
					Encryption: {
						KeyName:              pulumi.String("key1"),
						KeyVaultUri:          pulumi.String("https://vaulturi"),
						KeyVersion:           pulumi.String("123"),
						UserAssignedIdentity: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/id1"),
					},
					Name: pulumi.String("westus"),
				},
			},
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
import com.pulumi.azurenative.autonomousdevelopmentplatform.DataPool;
import com.pulumi.azurenative.autonomousdevelopmentplatform.DataPoolArgs;
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
        var dataPool = new DataPool("dataPool", DataPoolArgs.builder()        
            .accountName("sampleacct")
            .dataPoolName("sampledp")
            .locations(Map.ofEntries(
                Map.entry("encryption", Map.ofEntries(
                    Map.entry("keyName", "key1"),
                    Map.entry("keyVaultUri", "https://vaulturi"),
                    Map.entry("keyVersion", "123"),
                    Map.entry("userAssignedIdentity", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/id1")
                )),
                Map.entry("name", "westus")
            ))
            .resourceGroupName("adpClient")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataPool = new azure_native.autonomousdevelopmentplatform.DataPool("dataPool", {
    accountName: "sampleacct",
    dataPoolName: "sampledp",
    locations: [{
        encryption: {
            keyName: "key1",
            keyVaultUri: "https://vaulturi",
            keyVersion: "123",
            userAssignedIdentity: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/id1",
        },
        name: "westus",
    }],
    resourceGroupName: "adpClient",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

data_pool = azure_native.autonomousdevelopmentplatform.DataPool("dataPool",
    account_name="sampleacct",
    data_pool_name="sampledp",
    locations=[{
        "encryption": azure_native.autonomousdevelopmentplatform.DataPoolEncryptionArgs(
            key_name="key1",
            key_vault_uri="https://vaulturi",
            key_version="123",
            user_assigned_identity="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/id1",
        ),
        "name": "westus",
    }],
    resource_group_name="adpClient")

```

```yaml
resources:
  dataPool:
    type: azure-native:autonomousdevelopmentplatform:DataPool
    properties:
      accountName: sampleacct
      dataPoolName: sampledp
      locations:
        - encryption:
            keyName: key1
            keyVaultUri: https://vaulturi
            keyVersion: '123'
            userAssignedIdentity: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/id1
          name: westus
      resourceGroupName: adpClient

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:autonomousdevelopmentplatform:DataPool dp1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.AutonomousDevelopmentPlatform/accounts/adp1/dataPools/dp1 
```
