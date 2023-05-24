Resource information, as returned by the resource provider.
API Version: 2023-02-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update Recovery Services vault
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vault = new AzureNative.RecoveryServices.Vault("vault", new()
    {
        Identity = new AzureNative.RecoveryServices.Inputs.IdentityDataArgs
        {
            Type = "SystemAssigned",
        },
        Location = "West US",
        Properties = new AzureNative.RecoveryServices.Inputs.VaultPropertiesArgs
        {
            PublicNetworkAccess = "Enabled",
        },
        ResourceGroupName = "Default-RecoveryServices-ResourceGroup",
        Sku = new AzureNative.RecoveryServices.Inputs.SkuArgs
        {
            Name = "Standard",
        },
        VaultName = "swaggerExample",
    });

});


```

```go
package main

import (
	recoveryservices "github.com/pulumi/pulumi-azure-native-sdk/recoveryservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recoveryservices.NewVault(ctx, "vault", &recoveryservices.VaultArgs{
			Identity: &recoveryservices.IdentityDataArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			Location: pulumi.String("West US"),
			Properties: &recoveryservices.VaultPropertiesArgs{
				PublicNetworkAccess: pulumi.String("Enabled"),
			},
			ResourceGroupName: pulumi.String("Default-RecoveryServices-ResourceGroup"),
			Sku: &recoveryservices.SkuArgs{
				Name: pulumi.String("Standard"),
			},
			VaultName: pulumi.String("swaggerExample"),
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
import com.pulumi.azurenative.recoveryservices.Vault;
import com.pulumi.azurenative.recoveryservices.VaultArgs;
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
        var vault = new Vault("vault", VaultArgs.builder()        
            .identity(Map.of("type", "SystemAssigned"))
            .location("West US")
            .properties(Map.of("publicNetworkAccess", "Enabled"))
            .resourceGroupName("Default-RecoveryServices-ResourceGroup")
            .sku(Map.of("name", "Standard"))
            .vaultName("swaggerExample")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vault = new azure_native.recoveryservices.Vault("vault", {
    identity: {
        type: "SystemAssigned",
    },
    location: "West US",
    properties: {
        publicNetworkAccess: "Enabled",
    },
    resourceGroupName: "Default-RecoveryServices-ResourceGroup",
    sku: {
        name: "Standard",
    },
    vaultName: "swaggerExample",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

vault = azure_native.recoveryservices.Vault("vault",
    identity=azure_native.recoveryservices.IdentityDataArgs(
        type="SystemAssigned",
    ),
    location="West US",
    properties=azure_native.recoveryservices.VaultPropertiesArgs(
        public_network_access="Enabled",
    ),
    resource_group_name="Default-RecoveryServices-ResourceGroup",
    sku=azure_native.recoveryservices.SkuArgs(
        name="Standard",
    ),
    vault_name="swaggerExample")

```

```yaml
resources:
  vault:
    type: azure-native:recoveryservices:Vault
    properties:
      identity:
        type: SystemAssigned
      location: West US
      properties:
        publicNetworkAccess: Enabled
      resourceGroupName: Default-RecoveryServices-ResourceGroup
      sku:
        name: Standard
      vaultName: swaggerExample

```

{{% /example %}}
{{% example %}}
### Create or Update Vault With Monitoring Setting
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vault = new AzureNative.RecoveryServices.Vault("vault", new()
    {
        Identity = new AzureNative.RecoveryServices.Inputs.IdentityDataArgs
        {
            Type = "SystemAssigned",
        },
        Location = "West US",
        Properties = new AzureNative.RecoveryServices.Inputs.VaultPropertiesArgs
        {
            MonitoringSettings = new AzureNative.RecoveryServices.Inputs.MonitoringSettingsArgs
            {
                AzureMonitorAlertSettings = new AzureNative.RecoveryServices.Inputs.AzureMonitorAlertSettingsArgs
                {
                    AlertsForAllJobFailures = "Enabled",
                },
                ClassicAlertSettings = new AzureNative.RecoveryServices.Inputs.ClassicAlertSettingsArgs
                {
                    AlertsForCriticalOperations = "Disabled",
                },
            },
            PublicNetworkAccess = "Enabled",
        },
        ResourceGroupName = "Default-RecoveryServices-ResourceGroup",
        Sku = new AzureNative.RecoveryServices.Inputs.SkuArgs
        {
            Name = "Standard",
        },
        VaultName = "swaggerExample",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.recoveryservices.Vault;
import com.pulumi.azurenative.recoveryservices.VaultArgs;
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
        var vault = new Vault("vault", VaultArgs.builder()        
            .identity(Map.of("type", "SystemAssigned"))
            .location("West US")
            .properties(Map.ofEntries(
                Map.entry("monitoringSettings", Map.ofEntries(
                    Map.entry("azureMonitorAlertSettings", Map.of("alertsForAllJobFailures", "Enabled")),
                    Map.entry("classicAlertSettings", Map.of("alertsForCriticalOperations", "Disabled"))
                )),
                Map.entry("publicNetworkAccess", "Enabled")
            ))
            .resourceGroupName("Default-RecoveryServices-ResourceGroup")
            .sku(Map.of("name", "Standard"))
            .vaultName("swaggerExample")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vault = new azure_native.recoveryservices.Vault("vault", {
    identity: {
        type: "SystemAssigned",
    },
    location: "West US",
    properties: {
        monitoringSettings: {
            azureMonitorAlertSettings: {
                alertsForAllJobFailures: "Enabled",
            },
            classicAlertSettings: {
                alertsForCriticalOperations: "Disabled",
            },
        },
        publicNetworkAccess: "Enabled",
    },
    resourceGroupName: "Default-RecoveryServices-ResourceGroup",
    sku: {
        name: "Standard",
    },
    vaultName: "swaggerExample",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

vault = azure_native.recoveryservices.Vault("vault",
    identity=azure_native.recoveryservices.IdentityDataArgs(
        type="SystemAssigned",
    ),
    location="West US",
    properties=azure_native.recoveryservices.VaultPropertiesResponseArgs(
        monitoring_settings={
            "azureMonitorAlertSettings": azure_native.recoveryservices.AzureMonitorAlertSettingsArgs(
                alerts_for_all_job_failures="Enabled",
            ),
            "classicAlertSettings": azure_native.recoveryservices.ClassicAlertSettingsArgs(
                alerts_for_critical_operations="Disabled",
            ),
        },
        public_network_access="Enabled",
    ),
    resource_group_name="Default-RecoveryServices-ResourceGroup",
    sku=azure_native.recoveryservices.SkuArgs(
        name="Standard",
    ),
    vault_name="swaggerExample")

```

```yaml
resources:
  vault:
    type: azure-native:recoveryservices:Vault
    properties:
      identity:
        type: SystemAssigned
      location: West US
      properties:
        monitoringSettings:
          azureMonitorAlertSettings:
            alertsForAllJobFailures: Enabled
          classicAlertSettings:
            alertsForCriticalOperations: Disabled
        publicNetworkAccess: Enabled
      resourceGroupName: Default-RecoveryServices-ResourceGroup
      sku:
        name: Standard
      vaultName: swaggerExample

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:Vault swaggerExample /subscriptions/77777777-b0c6-47a2-b37c-d8e65a629c18/resourceGroups/Default-RecoveryServices-ResourceGroup/providers/Microsoft.RecoveryServices/vaults/swaggerExample 
```
