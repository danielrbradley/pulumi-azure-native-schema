Data Lake Store account information.
API Version: 2016-11-01.
Previous API Version: 2016-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates the specified Data Lake Store account
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.DataLakeStore.Account("account", new()
    {
        AccountName = "contosoadla",
        DefaultGroup = "test_default_group",
        EncryptionConfig = new AzureNative.DataLakeStore.Inputs.EncryptionConfigArgs
        {
            KeyVaultMetaInfo = new AzureNative.DataLakeStore.Inputs.KeyVaultMetaInfoArgs
            {
                EncryptionKeyName = "test_encryption_key_name",
                EncryptionKeyVersion = "encryption_key_version",
                KeyVaultResourceId = "34adfa4f-cedf-4dc0-ba29-b6d1a69ab345",
            },
            Type = AzureNative.DataLakeStore.EncryptionConfigType.UserManaged,
        },
        EncryptionState = AzureNative.DataLakeStore.EncryptionState.Enabled,
        FirewallAllowAzureIps = AzureNative.DataLakeStore.FirewallAllowAzureIpsState.Enabled,
        FirewallRules = new[]
        {
            new AzureNative.DataLakeStore.Inputs.CreateFirewallRuleWithAccountParametersArgs
            {
                EndIpAddress = "2.2.2.2",
                Name = "test_rule",
                StartIpAddress = "1.1.1.1",
            },
        },
        FirewallState = AzureNative.DataLakeStore.FirewallState.Enabled,
        Identity = new AzureNative.DataLakeStore.Inputs.EncryptionIdentityArgs
        {
            Type = AzureNative.DataLakeStore.EncryptionIdentityType.SystemAssigned,
        },
        Location = "eastus2",
        NewTier = AzureNative.DataLakeStore.TierType.Consumption,
        ResourceGroupName = "contosorg",
        Tags = 
        {
            { "test_key", "test_value" },
        },
        TrustedIdProviderState = AzureNative.DataLakeStore.TrustedIdProviderState.Enabled,
        TrustedIdProviders = new[]
        {
            new AzureNative.DataLakeStore.Inputs.CreateTrustedIdProviderWithAccountParametersArgs
            {
                IdProvider = "https://sts.windows.net/ea9ec534-a3e3-4e45-ad36-3afc5bb291c1",
                Name = "test_trusted_id_provider_name",
            },
        },
    });

});


```

```go
package main

import (
	datalakestore "github.com/pulumi/pulumi-azure-native-sdk/datalakestore"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datalakestore.NewAccount(ctx, "account", &datalakestore.AccountArgs{
			AccountName:  pulumi.String("contosoadla"),
			DefaultGroup: pulumi.String("test_default_group"),
			EncryptionConfig: datalakestore.EncryptionConfigResponse{
				KeyVaultMetaInfo: &datalakestore.KeyVaultMetaInfoArgs{
					EncryptionKeyName:    pulumi.String("test_encryption_key_name"),
					EncryptionKeyVersion: pulumi.String("encryption_key_version"),
					KeyVaultResourceId:   pulumi.String("34adfa4f-cedf-4dc0-ba29-b6d1a69ab345"),
				},
				Type: datalakestore.EncryptionConfigTypeUserManaged,
			},
			EncryptionState:       datalakestore.EncryptionStateEnabled,
			FirewallAllowAzureIps: datalakestore.FirewallAllowAzureIpsStateEnabled,
			FirewallRules: []datalakestore.CreateFirewallRuleWithAccountParametersArgs{
				{
					EndIpAddress:   pulumi.String("2.2.2.2"),
					Name:           pulumi.String("test_rule"),
					StartIpAddress: pulumi.String("1.1.1.1"),
				},
			},
			FirewallState: datalakestore.FirewallStateEnabled,
			Identity: &datalakestore.EncryptionIdentityArgs{
				Type: datalakestore.EncryptionIdentityTypeSystemAssigned,
			},
			Location:          pulumi.String("eastus2"),
			NewTier:           datalakestore.TierTypeConsumption,
			ResourceGroupName: pulumi.String("contosorg"),
			Tags: pulumi.StringMap{
				"test_key": pulumi.String("test_value"),
			},
			TrustedIdProviderState: datalakestore.TrustedIdProviderStateEnabled,
			TrustedIdProviders: []datalakestore.CreateTrustedIdProviderWithAccountParametersArgs{
				{
					IdProvider: pulumi.String("https://sts.windows.net/ea9ec534-a3e3-4e45-ad36-3afc5bb291c1"),
					Name:       pulumi.String("test_trusted_id_provider_name"),
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
import com.pulumi.azurenative.datalakestore.Account;
import com.pulumi.azurenative.datalakestore.AccountArgs;
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
            .accountName("contosoadla")
            .defaultGroup("test_default_group")
            .encryptionConfig(Map.ofEntries(
                Map.entry("keyVaultMetaInfo", Map.ofEntries(
                    Map.entry("encryptionKeyName", "test_encryption_key_name"),
                    Map.entry("encryptionKeyVersion", "encryption_key_version"),
                    Map.entry("keyVaultResourceId", "34adfa4f-cedf-4dc0-ba29-b6d1a69ab345")
                )),
                Map.entry("type", "UserManaged")
            ))
            .encryptionState("Enabled")
            .firewallAllowAzureIps("Enabled")
            .firewallRules(Map.ofEntries(
                Map.entry("endIpAddress", "2.2.2.2"),
                Map.entry("name", "test_rule"),
                Map.entry("startIpAddress", "1.1.1.1")
            ))
            .firewallState("Enabled")
            .identity(Map.of("type", "SystemAssigned"))
            .location("eastus2")
            .newTier("Consumption")
            .resourceGroupName("contosorg")
            .tags(Map.of("test_key", "test_value"))
            .trustedIdProviderState("Enabled")
            .trustedIdProviders(Map.ofEntries(
                Map.entry("idProvider", "https://sts.windows.net/ea9ec534-a3e3-4e45-ad36-3afc5bb291c1"),
                Map.entry("name", "test_trusted_id_provider_name")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.datalakestore.Account("account", {
    accountName: "contosoadla",
    defaultGroup: "test_default_group",
    encryptionConfig: {
        keyVaultMetaInfo: {
            encryptionKeyName: "test_encryption_key_name",
            encryptionKeyVersion: "encryption_key_version",
            keyVaultResourceId: "34adfa4f-cedf-4dc0-ba29-b6d1a69ab345",
        },
        type: azure_native.datalakestore.EncryptionConfigType.UserManaged,
    },
    encryptionState: azure_native.datalakestore.EncryptionState.Enabled,
    firewallAllowAzureIps: azure_native.datalakestore.FirewallAllowAzureIpsState.Enabled,
    firewallRules: [{
        endIpAddress: "2.2.2.2",
        name: "test_rule",
        startIpAddress: "1.1.1.1",
    }],
    firewallState: azure_native.datalakestore.FirewallState.Enabled,
    identity: {
        type: azure_native.datalakestore.EncryptionIdentityType.SystemAssigned,
    },
    location: "eastus2",
    newTier: azure_native.datalakestore.TierType.Consumption,
    resourceGroupName: "contosorg",
    tags: {
        test_key: "test_value",
    },
    trustedIdProviderState: azure_native.datalakestore.TrustedIdProviderState.Enabled,
    trustedIdProviders: [{
        idProvider: "https://sts.windows.net/ea9ec534-a3e3-4e45-ad36-3afc5bb291c1",
        name: "test_trusted_id_provider_name",
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.datalakestore.Account("account",
    account_name="contosoadla",
    default_group="test_default_group",
    encryption_config=azure_native.datalakestore.EncryptionConfigResponseArgs(
        key_vault_meta_info=azure_native.datalakestore.KeyVaultMetaInfoArgs(
            encryption_key_name="test_encryption_key_name",
            encryption_key_version="encryption_key_version",
            key_vault_resource_id="34adfa4f-cedf-4dc0-ba29-b6d1a69ab345",
        ),
        type=azure_native.datalakestore.EncryptionConfigType.USER_MANAGED,
    ),
    encryption_state=azure_native.datalakestore.EncryptionState.ENABLED,
    firewall_allow_azure_ips=azure_native.datalakestore.FirewallAllowAzureIpsState.ENABLED,
    firewall_rules=[azure_native.datalakestore.CreateFirewallRuleWithAccountParametersArgs(
        end_ip_address="2.2.2.2",
        name="test_rule",
        start_ip_address="1.1.1.1",
    )],
    firewall_state=azure_native.datalakestore.FirewallState.ENABLED,
    identity=azure_native.datalakestore.EncryptionIdentityArgs(
        type=azure_native.datalakestore.EncryptionIdentityType.SYSTEM_ASSIGNED,
    ),
    location="eastus2",
    new_tier=azure_native.datalakestore.TierType.CONSUMPTION,
    resource_group_name="contosorg",
    tags={
        "test_key": "test_value",
    },
    trusted_id_provider_state=azure_native.datalakestore.TrustedIdProviderState.ENABLED,
    trusted_id_providers=[azure_native.datalakestore.CreateTrustedIdProviderWithAccountParametersArgs(
        id_provider="https://sts.windows.net/ea9ec534-a3e3-4e45-ad36-3afc5bb291c1",
        name="test_trusted_id_provider_name",
    )])

```

```yaml
resources:
  account:
    type: azure-native:datalakestore:Account
    properties:
      accountName: contosoadla
      defaultGroup: test_default_group
      encryptionConfig:
        keyVaultMetaInfo:
          encryptionKeyName: test_encryption_key_name
          encryptionKeyVersion: encryption_key_version
          keyVaultResourceId: 34adfa4f-cedf-4dc0-ba29-b6d1a69ab345
        type: UserManaged
      encryptionState: Enabled
      firewallAllowAzureIps: Enabled
      firewallRules:
        - endIpAddress: 2.2.2.2
          name: test_rule
          startIpAddress: 1.1.1.1
      firewallState: Enabled
      identity:
        type: SystemAssigned
      location: eastus2
      newTier: Consumption
      resourceGroupName: contosorg
      tags:
        test_key: test_value
      trustedIdProviderState: Enabled
      trustedIdProviders:
        - idProvider: https://sts.windows.net/ea9ec534-a3e3-4e45-ad36-3afc5bb291c1
          name: test_trusted_id_provider_name

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datalakestore:Account contosoadla 34adfa4f-cedf-4dc0-ba29-b6d1a69ab345 
```
