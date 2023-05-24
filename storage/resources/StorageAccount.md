The storage account.
API Version: 2022-09-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NfsV3AccountCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageAccount = new AzureNative.Storage.StorageAccount("storageAccount", new()
    {
        AccountName = "sto4445",
        EnableHttpsTrafficOnly = false,
        EnableNfsV3 = true,
        IsHnsEnabled = true,
        Kind = "BlockBlobStorage",
        Location = "eastus",
        NetworkRuleSet = new AzureNative.Storage.Inputs.NetworkRuleSetArgs
        {
            Bypass = "AzureServices",
            DefaultAction = AzureNative.Storage.DefaultAction.Allow,
            IpRules = new[] {},
            VirtualNetworkRules = new[]
            {
                new AzureNative.Storage.Inputs.VirtualNetworkRuleArgs
                {
                    VirtualNetworkResourceId = "/subscriptions/{subscription-id}/resourceGroups/res9101/providers/Microsoft.Network/virtualNetworks/net123/subnets/subnet12",
                },
            },
        },
        ResourceGroupName = "res9101",
        Sku = new AzureNative.Storage.Inputs.SkuArgs
        {
            Name = "Premium_LRS",
        },
    });

});


```

```go
package main

import (
	storage "github.com/pulumi/pulumi-azure-native-sdk/storage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storage.NewStorageAccount(ctx, "storageAccount", &storage.StorageAccountArgs{
			AccountName:            pulumi.String("sto4445"),
			EnableHttpsTrafficOnly: pulumi.Bool(false),
			EnableNfsV3:            pulumi.Bool(true),
			IsHnsEnabled:           pulumi.Bool(true),
			Kind:                   pulumi.String("BlockBlobStorage"),
			Location:               pulumi.String("eastus"),
			NetworkRuleSet: storage.NetworkRuleSetResponse{
				Bypass:        pulumi.String("AzureServices"),
				DefaultAction: storage.DefaultActionAllow,
				IpRules:       storage.IPRuleArray{},
				VirtualNetworkRules: storage.VirtualNetworkRuleArray{
					&storage.VirtualNetworkRuleArgs{
						VirtualNetworkResourceId: pulumi.String("/subscriptions/{subscription-id}/resourceGroups/res9101/providers/Microsoft.Network/virtualNetworks/net123/subnets/subnet12"),
					},
				},
			},
			ResourceGroupName: pulumi.String("res9101"),
			Sku: &storage.SkuArgs{
				Name: pulumi.String("Premium_LRS"),
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
import com.pulumi.azurenative.storage.StorageAccount;
import com.pulumi.azurenative.storage.StorageAccountArgs;
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
        var storageAccount = new StorageAccount("storageAccount", StorageAccountArgs.builder()        
            .accountName("sto4445")
            .enableHttpsTrafficOnly(false)
            .enableNfsV3(true)
            .isHnsEnabled(true)
            .kind("BlockBlobStorage")
            .location("eastus")
            .networkRuleSet(Map.ofEntries(
                Map.entry("bypass", "AzureServices"),
                Map.entry("defaultAction", "Allow"),
                Map.entry("ipRules", ),
                Map.entry("virtualNetworkRules", Map.of("virtualNetworkResourceId", "/subscriptions/{subscription-id}/resourceGroups/res9101/providers/Microsoft.Network/virtualNetworks/net123/subnets/subnet12"))
            ))
            .resourceGroupName("res9101")
            .sku(Map.of("name", "Premium_LRS"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageAccount = new azure_native.storage.StorageAccount("storageAccount", {
    accountName: "sto4445",
    enableHttpsTrafficOnly: false,
    enableNfsV3: true,
    isHnsEnabled: true,
    kind: "BlockBlobStorage",
    location: "eastus",
    networkRuleSet: {
        bypass: "AzureServices",
        defaultAction: azure_native.storage.DefaultAction.Allow,
        ipRules: [],
        virtualNetworkRules: [{
            virtualNetworkResourceId: "/subscriptions/{subscription-id}/resourceGroups/res9101/providers/Microsoft.Network/virtualNetworks/net123/subnets/subnet12",
        }],
    },
    resourceGroupName: "res9101",
    sku: {
        name: "Premium_LRS",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_account = azure_native.storage.StorageAccount("storageAccount",
    account_name="sto4445",
    enable_https_traffic_only=False,
    enable_nfs_v3=True,
    is_hns_enabled=True,
    kind="BlockBlobStorage",
    location="eastus",
    network_rule_set=azure_native.storage.NetworkRuleSetResponseArgs(
        bypass="AzureServices",
        default_action=azure_native.storage.DefaultAction.ALLOW,
        ip_rules=[],
        virtual_network_rules=[azure_native.storage.VirtualNetworkRuleArgs(
            virtual_network_resource_id="/subscriptions/{subscription-id}/resourceGroups/res9101/providers/Microsoft.Network/virtualNetworks/net123/subnets/subnet12",
        )],
    ),
    resource_group_name="res9101",
    sku=azure_native.storage.SkuArgs(
        name="Premium_LRS",
    ))

```

```yaml
resources:
  storageAccount:
    type: azure-native:storage:StorageAccount
    properties:
      accountName: sto4445
      enableHttpsTrafficOnly: false
      enableNfsV3: true
      isHnsEnabled: true
      kind: BlockBlobStorage
      location: eastus
      networkRuleSet:
        bypass: AzureServices
        defaultAction: Allow
        ipRules: []
        virtualNetworkRules:
          - virtualNetworkResourceId: /subscriptions/{subscription-id}/resourceGroups/res9101/providers/Microsoft.Network/virtualNetworks/net123/subnets/subnet12
      resourceGroupName: res9101
      sku:
        name: Premium_LRS

```

{{% /example %}}
{{% example %}}
### StorageAccountCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageAccount = new AzureNative.Storage.StorageAccount("storageAccount", new()
    {
        AccountName = "sto4445",
        AllowBlobPublicAccess = false,
        AllowSharedKeyAccess = true,
        DefaultToOAuthAuthentication = false,
        Encryption = new AzureNative.Storage.Inputs.EncryptionArgs
        {
            KeySource = "Microsoft.Storage",
            RequireInfrastructureEncryption = false,
            Services = new AzureNative.Storage.Inputs.EncryptionServicesArgs
            {
                Blob = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
                File = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
            },
        },
        ExtendedLocation = new AzureNative.Storage.Inputs.ExtendedLocationArgs
        {
            Name = "losangeles001",
            Type = "EdgeZone",
        },
        IsHnsEnabled = true,
        IsSftpEnabled = true,
        KeyPolicy = new AzureNative.Storage.Inputs.KeyPolicyArgs
        {
            KeyExpirationPeriodInDays = 20,
        },
        Kind = "Storage",
        Location = "eastus",
        MinimumTlsVersion = "TLS1_2",
        ResourceGroupName = "res9101",
        RoutingPreference = new AzureNative.Storage.Inputs.RoutingPreferenceArgs
        {
            PublishInternetEndpoints = true,
            PublishMicrosoftEndpoints = true,
            RoutingChoice = "MicrosoftRouting",
        },
        SasPolicy = new AzureNative.Storage.Inputs.SasPolicyArgs
        {
            ExpirationAction = "Log",
            SasExpirationPeriod = "1.15:59:59",
        },
        Sku = new AzureNative.Storage.Inputs.SkuArgs
        {
            Name = "Standard_GRS",
        },
        Tags = 
        {
            { "key1", "value1" },
            { "key2", "value2" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.storage.StorageAccount;
import com.pulumi.azurenative.storage.StorageAccountArgs;
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
        var storageAccount = new StorageAccount("storageAccount", StorageAccountArgs.builder()        
            .accountName("sto4445")
            .allowBlobPublicAccess(false)
            .allowSharedKeyAccess(true)
            .defaultToOAuthAuthentication(false)
            .encryption(Map.ofEntries(
                Map.entry("keySource", "Microsoft.Storage"),
                Map.entry("requireInfrastructureEncryption", false),
                Map.entry("services", Map.ofEntries(
                    Map.entry("blob", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    )),
                    Map.entry("file", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    ))
                ))
            ))
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "losangeles001"),
                Map.entry("type", "EdgeZone")
            ))
            .isHnsEnabled(true)
            .isSftpEnabled(true)
            .keyPolicy(Map.of("keyExpirationPeriodInDays", 20))
            .kind("Storage")
            .location("eastus")
            .minimumTlsVersion("TLS1_2")
            .resourceGroupName("res9101")
            .routingPreference(Map.ofEntries(
                Map.entry("publishInternetEndpoints", true),
                Map.entry("publishMicrosoftEndpoints", true),
                Map.entry("routingChoice", "MicrosoftRouting")
            ))
            .sasPolicy(Map.ofEntries(
                Map.entry("expirationAction", "Log"),
                Map.entry("sasExpirationPeriod", "1.15:59:59")
            ))
            .sku(Map.of("name", "Standard_GRS"))
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageAccount = new azure_native.storage.StorageAccount("storageAccount", {
    accountName: "sto4445",
    allowBlobPublicAccess: false,
    allowSharedKeyAccess: true,
    defaultToOAuthAuthentication: false,
    encryption: {
        keySource: "Microsoft.Storage",
        requireInfrastructureEncryption: false,
        services: {
            blob: {
                enabled: true,
                keyType: "Account",
            },
            file: {
                enabled: true,
                keyType: "Account",
            },
        },
    },
    extendedLocation: {
        name: "losangeles001",
        type: "EdgeZone",
    },
    isHnsEnabled: true,
    isSftpEnabled: true,
    keyPolicy: {
        keyExpirationPeriodInDays: 20,
    },
    kind: "Storage",
    location: "eastus",
    minimumTlsVersion: "TLS1_2",
    resourceGroupName: "res9101",
    routingPreference: {
        publishInternetEndpoints: true,
        publishMicrosoftEndpoints: true,
        routingChoice: "MicrosoftRouting",
    },
    sasPolicy: {
        expirationAction: "Log",
        sasExpirationPeriod: "1.15:59:59",
    },
    sku: {
        name: "Standard_GRS",
    },
    tags: {
        key1: "value1",
        key2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_account = azure_native.storage.StorageAccount("storageAccount",
    account_name="sto4445",
    allow_blob_public_access=False,
    allow_shared_key_access=True,
    default_to_o_auth_authentication=False,
    encryption=azure_native.storage.EncryptionResponseArgs(
        key_source="Microsoft.Storage",
        require_infrastructure_encryption=False,
        services={
            "blob": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
            "file": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
        },
    ),
    extended_location=azure_native.storage.ExtendedLocationArgs(
        name="losangeles001",
        type="EdgeZone",
    ),
    is_hns_enabled=True,
    is_sftp_enabled=True,
    key_policy=azure_native.storage.KeyPolicyArgs(
        key_expiration_period_in_days=20,
    ),
    kind="Storage",
    location="eastus",
    minimum_tls_version="TLS1_2",
    resource_group_name="res9101",
    routing_preference=azure_native.storage.RoutingPreferenceArgs(
        publish_internet_endpoints=True,
        publish_microsoft_endpoints=True,
        routing_choice="MicrosoftRouting",
    ),
    sas_policy=azure_native.storage.SasPolicyArgs(
        expiration_action="Log",
        sas_expiration_period="1.15:59:59",
    ),
    sku=azure_native.storage.SkuArgs(
        name="Standard_GRS",
    ),
    tags={
        "key1": "value1",
        "key2": "value2",
    })

```

```yaml
resources:
  storageAccount:
    type: azure-native:storage:StorageAccount
    properties:
      accountName: sto4445
      allowBlobPublicAccess: false
      allowSharedKeyAccess: true
      defaultToOAuthAuthentication: false
      encryption:
        keySource: Microsoft.Storage
        requireInfrastructureEncryption: false
        services:
          blob:
            enabled: true
            keyType: Account
          file:
            enabled: true
            keyType: Account
      extendedLocation:
        name: losangeles001
        type: EdgeZone
      isHnsEnabled: true
      isSftpEnabled: true
      keyPolicy:
        keyExpirationPeriodInDays: 20
      kind: Storage
      location: eastus
      minimumTlsVersion: TLS1_2
      resourceGroupName: res9101
      routingPreference:
        publishInternetEndpoints: true
        publishMicrosoftEndpoints: true
        routingChoice: MicrosoftRouting
      sasPolicy:
        expirationAction: Log
        sasExpirationPeriod: 1.15:59:59
      sku:
        name: Standard_GRS
      tags:
        key1: value1
        key2: value2

```

{{% /example %}}
{{% example %}}
### StorageAccountCreateAllowedCopyScopeToAAD
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageAccount = new AzureNative.Storage.StorageAccount("storageAccount", new()
    {
        AccountName = "sto4445",
        AllowBlobPublicAccess = false,
        AllowSharedKeyAccess = true,
        AllowedCopyScope = "AAD",
        Encryption = new AzureNative.Storage.Inputs.EncryptionArgs
        {
            KeySource = "Microsoft.Storage",
            RequireInfrastructureEncryption = false,
            Services = new AzureNative.Storage.Inputs.EncryptionServicesArgs
            {
                Blob = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
                File = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
            },
        },
        IsHnsEnabled = true,
        KeyPolicy = new AzureNative.Storage.Inputs.KeyPolicyArgs
        {
            KeyExpirationPeriodInDays = 20,
        },
        Kind = "Storage",
        Location = "eastus",
        MinimumTlsVersion = "TLS1_2",
        ResourceGroupName = "res9101",
        RoutingPreference = new AzureNative.Storage.Inputs.RoutingPreferenceArgs
        {
            PublishInternetEndpoints = true,
            PublishMicrosoftEndpoints = true,
            RoutingChoice = "MicrosoftRouting",
        },
        SasPolicy = new AzureNative.Storage.Inputs.SasPolicyArgs
        {
            ExpirationAction = "Log",
            SasExpirationPeriod = "1.15:59:59",
        },
        Sku = new AzureNative.Storage.Inputs.SkuArgs
        {
            Name = "Standard_GRS",
        },
        Tags = 
        {
            { "key1", "value1" },
            { "key2", "value2" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.storage.StorageAccount;
import com.pulumi.azurenative.storage.StorageAccountArgs;
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
        var storageAccount = new StorageAccount("storageAccount", StorageAccountArgs.builder()        
            .accountName("sto4445")
            .allowBlobPublicAccess(false)
            .allowSharedKeyAccess(true)
            .allowedCopyScope("AAD")
            .encryption(Map.ofEntries(
                Map.entry("keySource", "Microsoft.Storage"),
                Map.entry("requireInfrastructureEncryption", false),
                Map.entry("services", Map.ofEntries(
                    Map.entry("blob", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    )),
                    Map.entry("file", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    ))
                ))
            ))
            .isHnsEnabled(true)
            .keyPolicy(Map.of("keyExpirationPeriodInDays", 20))
            .kind("Storage")
            .location("eastus")
            .minimumTlsVersion("TLS1_2")
            .resourceGroupName("res9101")
            .routingPreference(Map.ofEntries(
                Map.entry("publishInternetEndpoints", true),
                Map.entry("publishMicrosoftEndpoints", true),
                Map.entry("routingChoice", "MicrosoftRouting")
            ))
            .sasPolicy(Map.ofEntries(
                Map.entry("expirationAction", "Log"),
                Map.entry("sasExpirationPeriod", "1.15:59:59")
            ))
            .sku(Map.of("name", "Standard_GRS"))
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageAccount = new azure_native.storage.StorageAccount("storageAccount", {
    accountName: "sto4445",
    allowBlobPublicAccess: false,
    allowSharedKeyAccess: true,
    allowedCopyScope: "AAD",
    encryption: {
        keySource: "Microsoft.Storage",
        requireInfrastructureEncryption: false,
        services: {
            blob: {
                enabled: true,
                keyType: "Account",
            },
            file: {
                enabled: true,
                keyType: "Account",
            },
        },
    },
    isHnsEnabled: true,
    keyPolicy: {
        keyExpirationPeriodInDays: 20,
    },
    kind: "Storage",
    location: "eastus",
    minimumTlsVersion: "TLS1_2",
    resourceGroupName: "res9101",
    routingPreference: {
        publishInternetEndpoints: true,
        publishMicrosoftEndpoints: true,
        routingChoice: "MicrosoftRouting",
    },
    sasPolicy: {
        expirationAction: "Log",
        sasExpirationPeriod: "1.15:59:59",
    },
    sku: {
        name: "Standard_GRS",
    },
    tags: {
        key1: "value1",
        key2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_account = azure_native.storage.StorageAccount("storageAccount",
    account_name="sto4445",
    allow_blob_public_access=False,
    allow_shared_key_access=True,
    allowed_copy_scope="AAD",
    encryption=azure_native.storage.EncryptionResponseArgs(
        key_source="Microsoft.Storage",
        require_infrastructure_encryption=False,
        services={
            "blob": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
            "file": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
        },
    ),
    is_hns_enabled=True,
    key_policy=azure_native.storage.KeyPolicyArgs(
        key_expiration_period_in_days=20,
    ),
    kind="Storage",
    location="eastus",
    minimum_tls_version="TLS1_2",
    resource_group_name="res9101",
    routing_preference=azure_native.storage.RoutingPreferenceArgs(
        publish_internet_endpoints=True,
        publish_microsoft_endpoints=True,
        routing_choice="MicrosoftRouting",
    ),
    sas_policy=azure_native.storage.SasPolicyArgs(
        expiration_action="Log",
        sas_expiration_period="1.15:59:59",
    ),
    sku=azure_native.storage.SkuArgs(
        name="Standard_GRS",
    ),
    tags={
        "key1": "value1",
        "key2": "value2",
    })

```

```yaml
resources:
  storageAccount:
    type: azure-native:storage:StorageAccount
    properties:
      accountName: sto4445
      allowBlobPublicAccess: false
      allowSharedKeyAccess: true
      allowedCopyScope: AAD
      encryption:
        keySource: Microsoft.Storage
        requireInfrastructureEncryption: false
        services:
          blob:
            enabled: true
            keyType: Account
          file:
            enabled: true
            keyType: Account
      isHnsEnabled: true
      keyPolicy:
        keyExpirationPeriodInDays: 20
      kind: Storage
      location: eastus
      minimumTlsVersion: TLS1_2
      resourceGroupName: res9101
      routingPreference:
        publishInternetEndpoints: true
        publishMicrosoftEndpoints: true
        routingChoice: MicrosoftRouting
      sasPolicy:
        expirationAction: Log
        sasExpirationPeriod: 1.15:59:59
      sku:
        name: Standard_GRS
      tags:
        key1: value1
        key2: value2

```

{{% /example %}}
{{% example %}}
### StorageAccountCreateAllowedCopyScopeToPrivateLink
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageAccount = new AzureNative.Storage.StorageAccount("storageAccount", new()
    {
        AccountName = "sto4445",
        AllowBlobPublicAccess = false,
        AllowSharedKeyAccess = true,
        AllowedCopyScope = "PrivateLink",
        Encryption = new AzureNative.Storage.Inputs.EncryptionArgs
        {
            KeySource = "Microsoft.Storage",
            RequireInfrastructureEncryption = false,
            Services = new AzureNative.Storage.Inputs.EncryptionServicesArgs
            {
                Blob = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
                File = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
            },
        },
        IsHnsEnabled = true,
        KeyPolicy = new AzureNative.Storage.Inputs.KeyPolicyArgs
        {
            KeyExpirationPeriodInDays = 20,
        },
        Kind = "Storage",
        Location = "eastus",
        MinimumTlsVersion = "TLS1_2",
        ResourceGroupName = "res9101",
        RoutingPreference = new AzureNative.Storage.Inputs.RoutingPreferenceArgs
        {
            PublishInternetEndpoints = true,
            PublishMicrosoftEndpoints = true,
            RoutingChoice = "MicrosoftRouting",
        },
        SasPolicy = new AzureNative.Storage.Inputs.SasPolicyArgs
        {
            ExpirationAction = "Log",
            SasExpirationPeriod = "1.15:59:59",
        },
        Sku = new AzureNative.Storage.Inputs.SkuArgs
        {
            Name = "Standard_GRS",
        },
        Tags = 
        {
            { "key1", "value1" },
            { "key2", "value2" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.storage.StorageAccount;
import com.pulumi.azurenative.storage.StorageAccountArgs;
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
        var storageAccount = new StorageAccount("storageAccount", StorageAccountArgs.builder()        
            .accountName("sto4445")
            .allowBlobPublicAccess(false)
            .allowSharedKeyAccess(true)
            .allowedCopyScope("PrivateLink")
            .encryption(Map.ofEntries(
                Map.entry("keySource", "Microsoft.Storage"),
                Map.entry("requireInfrastructureEncryption", false),
                Map.entry("services", Map.ofEntries(
                    Map.entry("blob", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    )),
                    Map.entry("file", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    ))
                ))
            ))
            .isHnsEnabled(true)
            .keyPolicy(Map.of("keyExpirationPeriodInDays", 20))
            .kind("Storage")
            .location("eastus")
            .minimumTlsVersion("TLS1_2")
            .resourceGroupName("res9101")
            .routingPreference(Map.ofEntries(
                Map.entry("publishInternetEndpoints", true),
                Map.entry("publishMicrosoftEndpoints", true),
                Map.entry("routingChoice", "MicrosoftRouting")
            ))
            .sasPolicy(Map.ofEntries(
                Map.entry("expirationAction", "Log"),
                Map.entry("sasExpirationPeriod", "1.15:59:59")
            ))
            .sku(Map.of("name", "Standard_GRS"))
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageAccount = new azure_native.storage.StorageAccount("storageAccount", {
    accountName: "sto4445",
    allowBlobPublicAccess: false,
    allowSharedKeyAccess: true,
    allowedCopyScope: "PrivateLink",
    encryption: {
        keySource: "Microsoft.Storage",
        requireInfrastructureEncryption: false,
        services: {
            blob: {
                enabled: true,
                keyType: "Account",
            },
            file: {
                enabled: true,
                keyType: "Account",
            },
        },
    },
    isHnsEnabled: true,
    keyPolicy: {
        keyExpirationPeriodInDays: 20,
    },
    kind: "Storage",
    location: "eastus",
    minimumTlsVersion: "TLS1_2",
    resourceGroupName: "res9101",
    routingPreference: {
        publishInternetEndpoints: true,
        publishMicrosoftEndpoints: true,
        routingChoice: "MicrosoftRouting",
    },
    sasPolicy: {
        expirationAction: "Log",
        sasExpirationPeriod: "1.15:59:59",
    },
    sku: {
        name: "Standard_GRS",
    },
    tags: {
        key1: "value1",
        key2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_account = azure_native.storage.StorageAccount("storageAccount",
    account_name="sto4445",
    allow_blob_public_access=False,
    allow_shared_key_access=True,
    allowed_copy_scope="PrivateLink",
    encryption=azure_native.storage.EncryptionResponseArgs(
        key_source="Microsoft.Storage",
        require_infrastructure_encryption=False,
        services={
            "blob": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
            "file": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
        },
    ),
    is_hns_enabled=True,
    key_policy=azure_native.storage.KeyPolicyArgs(
        key_expiration_period_in_days=20,
    ),
    kind="Storage",
    location="eastus",
    minimum_tls_version="TLS1_2",
    resource_group_name="res9101",
    routing_preference=azure_native.storage.RoutingPreferenceArgs(
        publish_internet_endpoints=True,
        publish_microsoft_endpoints=True,
        routing_choice="MicrosoftRouting",
    ),
    sas_policy=azure_native.storage.SasPolicyArgs(
        expiration_action="Log",
        sas_expiration_period="1.15:59:59",
    ),
    sku=azure_native.storage.SkuArgs(
        name="Standard_GRS",
    ),
    tags={
        "key1": "value1",
        "key2": "value2",
    })

```

```yaml
resources:
  storageAccount:
    type: azure-native:storage:StorageAccount
    properties:
      accountName: sto4445
      allowBlobPublicAccess: false
      allowSharedKeyAccess: true
      allowedCopyScope: PrivateLink
      encryption:
        keySource: Microsoft.Storage
        requireInfrastructureEncryption: false
        services:
          blob:
            enabled: true
            keyType: Account
          file:
            enabled: true
            keyType: Account
      isHnsEnabled: true
      keyPolicy:
        keyExpirationPeriodInDays: 20
      kind: Storage
      location: eastus
      minimumTlsVersion: TLS1_2
      resourceGroupName: res9101
      routingPreference:
        publishInternetEndpoints: true
        publishMicrosoftEndpoints: true
        routingChoice: MicrosoftRouting
      sasPolicy:
        expirationAction: Log
        sasExpirationPeriod: 1.15:59:59
      sku:
        name: Standard_GRS
      tags:
        key1: value1
        key2: value2

```

{{% /example %}}
{{% example %}}
### StorageAccountCreateDisallowPublicNetworkAccess
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageAccount = new AzureNative.Storage.StorageAccount("storageAccount", new()
    {
        AccountName = "sto4445",
        AllowBlobPublicAccess = false,
        AllowSharedKeyAccess = true,
        Encryption = new AzureNative.Storage.Inputs.EncryptionArgs
        {
            KeySource = "Microsoft.Storage",
            RequireInfrastructureEncryption = false,
            Services = new AzureNative.Storage.Inputs.EncryptionServicesArgs
            {
                Blob = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
                File = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
            },
        },
        ExtendedLocation = new AzureNative.Storage.Inputs.ExtendedLocationArgs
        {
            Name = "losangeles001",
            Type = "EdgeZone",
        },
        IsHnsEnabled = true,
        KeyPolicy = new AzureNative.Storage.Inputs.KeyPolicyArgs
        {
            KeyExpirationPeriodInDays = 20,
        },
        Kind = "Storage",
        Location = "eastus",
        MinimumTlsVersion = "TLS1_2",
        PublicNetworkAccess = "Disabled",
        ResourceGroupName = "res9101",
        RoutingPreference = new AzureNative.Storage.Inputs.RoutingPreferenceArgs
        {
            PublishInternetEndpoints = true,
            PublishMicrosoftEndpoints = true,
            RoutingChoice = "MicrosoftRouting",
        },
        SasPolicy = new AzureNative.Storage.Inputs.SasPolicyArgs
        {
            ExpirationAction = "Log",
            SasExpirationPeriod = "1.15:59:59",
        },
        Sku = new AzureNative.Storage.Inputs.SkuArgs
        {
            Name = "Standard_GRS",
        },
        Tags = 
        {
            { "key1", "value1" },
            { "key2", "value2" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.storage.StorageAccount;
import com.pulumi.azurenative.storage.StorageAccountArgs;
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
        var storageAccount = new StorageAccount("storageAccount", StorageAccountArgs.builder()        
            .accountName("sto4445")
            .allowBlobPublicAccess(false)
            .allowSharedKeyAccess(true)
            .encryption(Map.ofEntries(
                Map.entry("keySource", "Microsoft.Storage"),
                Map.entry("requireInfrastructureEncryption", false),
                Map.entry("services", Map.ofEntries(
                    Map.entry("blob", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    )),
                    Map.entry("file", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    ))
                ))
            ))
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "losangeles001"),
                Map.entry("type", "EdgeZone")
            ))
            .isHnsEnabled(true)
            .keyPolicy(Map.of("keyExpirationPeriodInDays", 20))
            .kind("Storage")
            .location("eastus")
            .minimumTlsVersion("TLS1_2")
            .publicNetworkAccess("Disabled")
            .resourceGroupName("res9101")
            .routingPreference(Map.ofEntries(
                Map.entry("publishInternetEndpoints", true),
                Map.entry("publishMicrosoftEndpoints", true),
                Map.entry("routingChoice", "MicrosoftRouting")
            ))
            .sasPolicy(Map.ofEntries(
                Map.entry("expirationAction", "Log"),
                Map.entry("sasExpirationPeriod", "1.15:59:59")
            ))
            .sku(Map.of("name", "Standard_GRS"))
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageAccount = new azure_native.storage.StorageAccount("storageAccount", {
    accountName: "sto4445",
    allowBlobPublicAccess: false,
    allowSharedKeyAccess: true,
    encryption: {
        keySource: "Microsoft.Storage",
        requireInfrastructureEncryption: false,
        services: {
            blob: {
                enabled: true,
                keyType: "Account",
            },
            file: {
                enabled: true,
                keyType: "Account",
            },
        },
    },
    extendedLocation: {
        name: "losangeles001",
        type: "EdgeZone",
    },
    isHnsEnabled: true,
    keyPolicy: {
        keyExpirationPeriodInDays: 20,
    },
    kind: "Storage",
    location: "eastus",
    minimumTlsVersion: "TLS1_2",
    publicNetworkAccess: "Disabled",
    resourceGroupName: "res9101",
    routingPreference: {
        publishInternetEndpoints: true,
        publishMicrosoftEndpoints: true,
        routingChoice: "MicrosoftRouting",
    },
    sasPolicy: {
        expirationAction: "Log",
        sasExpirationPeriod: "1.15:59:59",
    },
    sku: {
        name: "Standard_GRS",
    },
    tags: {
        key1: "value1",
        key2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_account = azure_native.storage.StorageAccount("storageAccount",
    account_name="sto4445",
    allow_blob_public_access=False,
    allow_shared_key_access=True,
    encryption=azure_native.storage.EncryptionResponseArgs(
        key_source="Microsoft.Storage",
        require_infrastructure_encryption=False,
        services={
            "blob": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
            "file": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
        },
    ),
    extended_location=azure_native.storage.ExtendedLocationArgs(
        name="losangeles001",
        type="EdgeZone",
    ),
    is_hns_enabled=True,
    key_policy=azure_native.storage.KeyPolicyArgs(
        key_expiration_period_in_days=20,
    ),
    kind="Storage",
    location="eastus",
    minimum_tls_version="TLS1_2",
    public_network_access="Disabled",
    resource_group_name="res9101",
    routing_preference=azure_native.storage.RoutingPreferenceArgs(
        publish_internet_endpoints=True,
        publish_microsoft_endpoints=True,
        routing_choice="MicrosoftRouting",
    ),
    sas_policy=azure_native.storage.SasPolicyArgs(
        expiration_action="Log",
        sas_expiration_period="1.15:59:59",
    ),
    sku=azure_native.storage.SkuArgs(
        name="Standard_GRS",
    ),
    tags={
        "key1": "value1",
        "key2": "value2",
    })

```

```yaml
resources:
  storageAccount:
    type: azure-native:storage:StorageAccount
    properties:
      accountName: sto4445
      allowBlobPublicAccess: false
      allowSharedKeyAccess: true
      encryption:
        keySource: Microsoft.Storage
        requireInfrastructureEncryption: false
        services:
          blob:
            enabled: true
            keyType: Account
          file:
            enabled: true
            keyType: Account
      extendedLocation:
        name: losangeles001
        type: EdgeZone
      isHnsEnabled: true
      keyPolicy:
        keyExpirationPeriodInDays: 20
      kind: Storage
      location: eastus
      minimumTlsVersion: TLS1_2
      publicNetworkAccess: Disabled
      resourceGroupName: res9101
      routingPreference:
        publishInternetEndpoints: true
        publishMicrosoftEndpoints: true
        routingChoice: MicrosoftRouting
      sasPolicy:
        expirationAction: Log
        sasExpirationPeriod: 1.15:59:59
      sku:
        name: Standard_GRS
      tags:
        key1: value1
        key2: value2

```

{{% /example %}}
{{% example %}}
### StorageAccountCreateDnsEndpointTypeToAzureDnsZone
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageAccount = new AzureNative.Storage.StorageAccount("storageAccount", new()
    {
        AccountName = "sto4445",
        AllowBlobPublicAccess = false,
        AllowSharedKeyAccess = true,
        DefaultToOAuthAuthentication = false,
        DnsEndpointType = "AzureDnsZone",
        Encryption = new AzureNative.Storage.Inputs.EncryptionArgs
        {
            KeySource = "Microsoft.Storage",
            RequireInfrastructureEncryption = false,
            Services = new AzureNative.Storage.Inputs.EncryptionServicesArgs
            {
                Blob = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
                File = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
            },
        },
        ExtendedLocation = new AzureNative.Storage.Inputs.ExtendedLocationArgs
        {
            Name = "losangeles001",
            Type = "EdgeZone",
        },
        IsHnsEnabled = true,
        IsSftpEnabled = true,
        KeyPolicy = new AzureNative.Storage.Inputs.KeyPolicyArgs
        {
            KeyExpirationPeriodInDays = 20,
        },
        Kind = "Storage",
        Location = "eastus",
        MinimumTlsVersion = "TLS1_2",
        ResourceGroupName = "res9101",
        RoutingPreference = new AzureNative.Storage.Inputs.RoutingPreferenceArgs
        {
            PublishInternetEndpoints = true,
            PublishMicrosoftEndpoints = true,
            RoutingChoice = "MicrosoftRouting",
        },
        SasPolicy = new AzureNative.Storage.Inputs.SasPolicyArgs
        {
            ExpirationAction = "Log",
            SasExpirationPeriod = "1.15:59:59",
        },
        Sku = new AzureNative.Storage.Inputs.SkuArgs
        {
            Name = "Standard_GRS",
        },
        Tags = 
        {
            { "key1", "value1" },
            { "key2", "value2" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.storage.StorageAccount;
import com.pulumi.azurenative.storage.StorageAccountArgs;
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
        var storageAccount = new StorageAccount("storageAccount", StorageAccountArgs.builder()        
            .accountName("sto4445")
            .allowBlobPublicAccess(false)
            .allowSharedKeyAccess(true)
            .defaultToOAuthAuthentication(false)
            .dnsEndpointType("AzureDnsZone")
            .encryption(Map.ofEntries(
                Map.entry("keySource", "Microsoft.Storage"),
                Map.entry("requireInfrastructureEncryption", false),
                Map.entry("services", Map.ofEntries(
                    Map.entry("blob", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    )),
                    Map.entry("file", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    ))
                ))
            ))
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "losangeles001"),
                Map.entry("type", "EdgeZone")
            ))
            .isHnsEnabled(true)
            .isSftpEnabled(true)
            .keyPolicy(Map.of("keyExpirationPeriodInDays", 20))
            .kind("Storage")
            .location("eastus")
            .minimumTlsVersion("TLS1_2")
            .resourceGroupName("res9101")
            .routingPreference(Map.ofEntries(
                Map.entry("publishInternetEndpoints", true),
                Map.entry("publishMicrosoftEndpoints", true),
                Map.entry("routingChoice", "MicrosoftRouting")
            ))
            .sasPolicy(Map.ofEntries(
                Map.entry("expirationAction", "Log"),
                Map.entry("sasExpirationPeriod", "1.15:59:59")
            ))
            .sku(Map.of("name", "Standard_GRS"))
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageAccount = new azure_native.storage.StorageAccount("storageAccount", {
    accountName: "sto4445",
    allowBlobPublicAccess: false,
    allowSharedKeyAccess: true,
    defaultToOAuthAuthentication: false,
    dnsEndpointType: "AzureDnsZone",
    encryption: {
        keySource: "Microsoft.Storage",
        requireInfrastructureEncryption: false,
        services: {
            blob: {
                enabled: true,
                keyType: "Account",
            },
            file: {
                enabled: true,
                keyType: "Account",
            },
        },
    },
    extendedLocation: {
        name: "losangeles001",
        type: "EdgeZone",
    },
    isHnsEnabled: true,
    isSftpEnabled: true,
    keyPolicy: {
        keyExpirationPeriodInDays: 20,
    },
    kind: "Storage",
    location: "eastus",
    minimumTlsVersion: "TLS1_2",
    resourceGroupName: "res9101",
    routingPreference: {
        publishInternetEndpoints: true,
        publishMicrosoftEndpoints: true,
        routingChoice: "MicrosoftRouting",
    },
    sasPolicy: {
        expirationAction: "Log",
        sasExpirationPeriod: "1.15:59:59",
    },
    sku: {
        name: "Standard_GRS",
    },
    tags: {
        key1: "value1",
        key2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_account = azure_native.storage.StorageAccount("storageAccount",
    account_name="sto4445",
    allow_blob_public_access=False,
    allow_shared_key_access=True,
    default_to_o_auth_authentication=False,
    dns_endpoint_type="AzureDnsZone",
    encryption=azure_native.storage.EncryptionResponseArgs(
        key_source="Microsoft.Storage",
        require_infrastructure_encryption=False,
        services={
            "blob": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
            "file": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
        },
    ),
    extended_location=azure_native.storage.ExtendedLocationArgs(
        name="losangeles001",
        type="EdgeZone",
    ),
    is_hns_enabled=True,
    is_sftp_enabled=True,
    key_policy=azure_native.storage.KeyPolicyArgs(
        key_expiration_period_in_days=20,
    ),
    kind="Storage",
    location="eastus",
    minimum_tls_version="TLS1_2",
    resource_group_name="res9101",
    routing_preference=azure_native.storage.RoutingPreferenceArgs(
        publish_internet_endpoints=True,
        publish_microsoft_endpoints=True,
        routing_choice="MicrosoftRouting",
    ),
    sas_policy=azure_native.storage.SasPolicyArgs(
        expiration_action="Log",
        sas_expiration_period="1.15:59:59",
    ),
    sku=azure_native.storage.SkuArgs(
        name="Standard_GRS",
    ),
    tags={
        "key1": "value1",
        "key2": "value2",
    })

```

```yaml
resources:
  storageAccount:
    type: azure-native:storage:StorageAccount
    properties:
      accountName: sto4445
      allowBlobPublicAccess: false
      allowSharedKeyAccess: true
      defaultToOAuthAuthentication: false
      dnsEndpointType: AzureDnsZone
      encryption:
        keySource: Microsoft.Storage
        requireInfrastructureEncryption: false
        services:
          blob:
            enabled: true
            keyType: Account
          file:
            enabled: true
            keyType: Account
      extendedLocation:
        name: losangeles001
        type: EdgeZone
      isHnsEnabled: true
      isSftpEnabled: true
      keyPolicy:
        keyExpirationPeriodInDays: 20
      kind: Storage
      location: eastus
      minimumTlsVersion: TLS1_2
      resourceGroupName: res9101
      routingPreference:
        publishInternetEndpoints: true
        publishMicrosoftEndpoints: true
        routingChoice: MicrosoftRouting
      sasPolicy:
        expirationAction: Log
        sasExpirationPeriod: 1.15:59:59
      sku:
        name: Standard_GRS
      tags:
        key1: value1
        key2: value2

```

{{% /example %}}
{{% example %}}
### StorageAccountCreateDnsEndpointTypeToStandard
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageAccount = new AzureNative.Storage.StorageAccount("storageAccount", new()
    {
        AccountName = "sto4445",
        AllowBlobPublicAccess = false,
        AllowSharedKeyAccess = true,
        DefaultToOAuthAuthentication = false,
        DnsEndpointType = "Standard",
        Encryption = new AzureNative.Storage.Inputs.EncryptionArgs
        {
            KeySource = "Microsoft.Storage",
            RequireInfrastructureEncryption = false,
            Services = new AzureNative.Storage.Inputs.EncryptionServicesArgs
            {
                Blob = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
                File = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
            },
        },
        ExtendedLocation = new AzureNative.Storage.Inputs.ExtendedLocationArgs
        {
            Name = "losangeles001",
            Type = "EdgeZone",
        },
        IsHnsEnabled = true,
        IsSftpEnabled = true,
        KeyPolicy = new AzureNative.Storage.Inputs.KeyPolicyArgs
        {
            KeyExpirationPeriodInDays = 20,
        },
        Kind = "Storage",
        Location = "eastus",
        MinimumTlsVersion = "TLS1_2",
        ResourceGroupName = "res9101",
        RoutingPreference = new AzureNative.Storage.Inputs.RoutingPreferenceArgs
        {
            PublishInternetEndpoints = true,
            PublishMicrosoftEndpoints = true,
            RoutingChoice = "MicrosoftRouting",
        },
        SasPolicy = new AzureNative.Storage.Inputs.SasPolicyArgs
        {
            ExpirationAction = "Log",
            SasExpirationPeriod = "1.15:59:59",
        },
        Sku = new AzureNative.Storage.Inputs.SkuArgs
        {
            Name = "Standard_GRS",
        },
        Tags = 
        {
            { "key1", "value1" },
            { "key2", "value2" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.storage.StorageAccount;
import com.pulumi.azurenative.storage.StorageAccountArgs;
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
        var storageAccount = new StorageAccount("storageAccount", StorageAccountArgs.builder()        
            .accountName("sto4445")
            .allowBlobPublicAccess(false)
            .allowSharedKeyAccess(true)
            .defaultToOAuthAuthentication(false)
            .dnsEndpointType("Standard")
            .encryption(Map.ofEntries(
                Map.entry("keySource", "Microsoft.Storage"),
                Map.entry("requireInfrastructureEncryption", false),
                Map.entry("services", Map.ofEntries(
                    Map.entry("blob", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    )),
                    Map.entry("file", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    ))
                ))
            ))
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "losangeles001"),
                Map.entry("type", "EdgeZone")
            ))
            .isHnsEnabled(true)
            .isSftpEnabled(true)
            .keyPolicy(Map.of("keyExpirationPeriodInDays", 20))
            .kind("Storage")
            .location("eastus")
            .minimumTlsVersion("TLS1_2")
            .resourceGroupName("res9101")
            .routingPreference(Map.ofEntries(
                Map.entry("publishInternetEndpoints", true),
                Map.entry("publishMicrosoftEndpoints", true),
                Map.entry("routingChoice", "MicrosoftRouting")
            ))
            .sasPolicy(Map.ofEntries(
                Map.entry("expirationAction", "Log"),
                Map.entry("sasExpirationPeriod", "1.15:59:59")
            ))
            .sku(Map.of("name", "Standard_GRS"))
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageAccount = new azure_native.storage.StorageAccount("storageAccount", {
    accountName: "sto4445",
    allowBlobPublicAccess: false,
    allowSharedKeyAccess: true,
    defaultToOAuthAuthentication: false,
    dnsEndpointType: "Standard",
    encryption: {
        keySource: "Microsoft.Storage",
        requireInfrastructureEncryption: false,
        services: {
            blob: {
                enabled: true,
                keyType: "Account",
            },
            file: {
                enabled: true,
                keyType: "Account",
            },
        },
    },
    extendedLocation: {
        name: "losangeles001",
        type: "EdgeZone",
    },
    isHnsEnabled: true,
    isSftpEnabled: true,
    keyPolicy: {
        keyExpirationPeriodInDays: 20,
    },
    kind: "Storage",
    location: "eastus",
    minimumTlsVersion: "TLS1_2",
    resourceGroupName: "res9101",
    routingPreference: {
        publishInternetEndpoints: true,
        publishMicrosoftEndpoints: true,
        routingChoice: "MicrosoftRouting",
    },
    sasPolicy: {
        expirationAction: "Log",
        sasExpirationPeriod: "1.15:59:59",
    },
    sku: {
        name: "Standard_GRS",
    },
    tags: {
        key1: "value1",
        key2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_account = azure_native.storage.StorageAccount("storageAccount",
    account_name="sto4445",
    allow_blob_public_access=False,
    allow_shared_key_access=True,
    default_to_o_auth_authentication=False,
    dns_endpoint_type="Standard",
    encryption=azure_native.storage.EncryptionResponseArgs(
        key_source="Microsoft.Storage",
        require_infrastructure_encryption=False,
        services={
            "blob": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
            "file": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
        },
    ),
    extended_location=azure_native.storage.ExtendedLocationArgs(
        name="losangeles001",
        type="EdgeZone",
    ),
    is_hns_enabled=True,
    is_sftp_enabled=True,
    key_policy=azure_native.storage.KeyPolicyArgs(
        key_expiration_period_in_days=20,
    ),
    kind="Storage",
    location="eastus",
    minimum_tls_version="TLS1_2",
    resource_group_name="res9101",
    routing_preference=azure_native.storage.RoutingPreferenceArgs(
        publish_internet_endpoints=True,
        publish_microsoft_endpoints=True,
        routing_choice="MicrosoftRouting",
    ),
    sas_policy=azure_native.storage.SasPolicyArgs(
        expiration_action="Log",
        sas_expiration_period="1.15:59:59",
    ),
    sku=azure_native.storage.SkuArgs(
        name="Standard_GRS",
    ),
    tags={
        "key1": "value1",
        "key2": "value2",
    })

```

```yaml
resources:
  storageAccount:
    type: azure-native:storage:StorageAccount
    properties:
      accountName: sto4445
      allowBlobPublicAccess: false
      allowSharedKeyAccess: true
      defaultToOAuthAuthentication: false
      dnsEndpointType: Standard
      encryption:
        keySource: Microsoft.Storage
        requireInfrastructureEncryption: false
        services:
          blob:
            enabled: true
            keyType: Account
          file:
            enabled: true
            keyType: Account
      extendedLocation:
        name: losangeles001
        type: EdgeZone
      isHnsEnabled: true
      isSftpEnabled: true
      keyPolicy:
        keyExpirationPeriodInDays: 20
      kind: Storage
      location: eastus
      minimumTlsVersion: TLS1_2
      resourceGroupName: res9101
      routingPreference:
        publishInternetEndpoints: true
        publishMicrosoftEndpoints: true
        routingChoice: MicrosoftRouting
      sasPolicy:
        expirationAction: Log
        sasExpirationPeriod: 1.15:59:59
      sku:
        name: Standard_GRS
      tags:
        key1: value1
        key2: value2

```

{{% /example %}}
{{% example %}}
### StorageAccountCreateEnablePublicNetworkAccess
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageAccount = new AzureNative.Storage.StorageAccount("storageAccount", new()
    {
        AccountName = "sto4445",
        AllowBlobPublicAccess = false,
        AllowSharedKeyAccess = true,
        Encryption = new AzureNative.Storage.Inputs.EncryptionArgs
        {
            KeySource = "Microsoft.Storage",
            RequireInfrastructureEncryption = false,
            Services = new AzureNative.Storage.Inputs.EncryptionServicesArgs
            {
                Blob = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
                File = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
            },
        },
        ExtendedLocation = new AzureNative.Storage.Inputs.ExtendedLocationArgs
        {
            Name = "losangeles001",
            Type = "EdgeZone",
        },
        IsHnsEnabled = true,
        KeyPolicy = new AzureNative.Storage.Inputs.KeyPolicyArgs
        {
            KeyExpirationPeriodInDays = 20,
        },
        Kind = "Storage",
        Location = "eastus",
        MinimumTlsVersion = "TLS1_2",
        PublicNetworkAccess = "Enabled",
        ResourceGroupName = "res9101",
        RoutingPreference = new AzureNative.Storage.Inputs.RoutingPreferenceArgs
        {
            PublishInternetEndpoints = true,
            PublishMicrosoftEndpoints = true,
            RoutingChoice = "MicrosoftRouting",
        },
        SasPolicy = new AzureNative.Storage.Inputs.SasPolicyArgs
        {
            ExpirationAction = "Log",
            SasExpirationPeriod = "1.15:59:59",
        },
        Sku = new AzureNative.Storage.Inputs.SkuArgs
        {
            Name = "Standard_GRS",
        },
        Tags = 
        {
            { "key1", "value1" },
            { "key2", "value2" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.storage.StorageAccount;
import com.pulumi.azurenative.storage.StorageAccountArgs;
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
        var storageAccount = new StorageAccount("storageAccount", StorageAccountArgs.builder()        
            .accountName("sto4445")
            .allowBlobPublicAccess(false)
            .allowSharedKeyAccess(true)
            .encryption(Map.ofEntries(
                Map.entry("keySource", "Microsoft.Storage"),
                Map.entry("requireInfrastructureEncryption", false),
                Map.entry("services", Map.ofEntries(
                    Map.entry("blob", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    )),
                    Map.entry("file", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    ))
                ))
            ))
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "losangeles001"),
                Map.entry("type", "EdgeZone")
            ))
            .isHnsEnabled(true)
            .keyPolicy(Map.of("keyExpirationPeriodInDays", 20))
            .kind("Storage")
            .location("eastus")
            .minimumTlsVersion("TLS1_2")
            .publicNetworkAccess("Enabled")
            .resourceGroupName("res9101")
            .routingPreference(Map.ofEntries(
                Map.entry("publishInternetEndpoints", true),
                Map.entry("publishMicrosoftEndpoints", true),
                Map.entry("routingChoice", "MicrosoftRouting")
            ))
            .sasPolicy(Map.ofEntries(
                Map.entry("expirationAction", "Log"),
                Map.entry("sasExpirationPeriod", "1.15:59:59")
            ))
            .sku(Map.of("name", "Standard_GRS"))
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageAccount = new azure_native.storage.StorageAccount("storageAccount", {
    accountName: "sto4445",
    allowBlobPublicAccess: false,
    allowSharedKeyAccess: true,
    encryption: {
        keySource: "Microsoft.Storage",
        requireInfrastructureEncryption: false,
        services: {
            blob: {
                enabled: true,
                keyType: "Account",
            },
            file: {
                enabled: true,
                keyType: "Account",
            },
        },
    },
    extendedLocation: {
        name: "losangeles001",
        type: "EdgeZone",
    },
    isHnsEnabled: true,
    keyPolicy: {
        keyExpirationPeriodInDays: 20,
    },
    kind: "Storage",
    location: "eastus",
    minimumTlsVersion: "TLS1_2",
    publicNetworkAccess: "Enabled",
    resourceGroupName: "res9101",
    routingPreference: {
        publishInternetEndpoints: true,
        publishMicrosoftEndpoints: true,
        routingChoice: "MicrosoftRouting",
    },
    sasPolicy: {
        expirationAction: "Log",
        sasExpirationPeriod: "1.15:59:59",
    },
    sku: {
        name: "Standard_GRS",
    },
    tags: {
        key1: "value1",
        key2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_account = azure_native.storage.StorageAccount("storageAccount",
    account_name="sto4445",
    allow_blob_public_access=False,
    allow_shared_key_access=True,
    encryption=azure_native.storage.EncryptionResponseArgs(
        key_source="Microsoft.Storage",
        require_infrastructure_encryption=False,
        services={
            "blob": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
            "file": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
        },
    ),
    extended_location=azure_native.storage.ExtendedLocationArgs(
        name="losangeles001",
        type="EdgeZone",
    ),
    is_hns_enabled=True,
    key_policy=azure_native.storage.KeyPolicyArgs(
        key_expiration_period_in_days=20,
    ),
    kind="Storage",
    location="eastus",
    minimum_tls_version="TLS1_2",
    public_network_access="Enabled",
    resource_group_name="res9101",
    routing_preference=azure_native.storage.RoutingPreferenceArgs(
        publish_internet_endpoints=True,
        publish_microsoft_endpoints=True,
        routing_choice="MicrosoftRouting",
    ),
    sas_policy=azure_native.storage.SasPolicyArgs(
        expiration_action="Log",
        sas_expiration_period="1.15:59:59",
    ),
    sku=azure_native.storage.SkuArgs(
        name="Standard_GRS",
    ),
    tags={
        "key1": "value1",
        "key2": "value2",
    })

```

```yaml
resources:
  storageAccount:
    type: azure-native:storage:StorageAccount
    properties:
      accountName: sto4445
      allowBlobPublicAccess: false
      allowSharedKeyAccess: true
      encryption:
        keySource: Microsoft.Storage
        requireInfrastructureEncryption: false
        services:
          blob:
            enabled: true
            keyType: Account
          file:
            enabled: true
            keyType: Account
      extendedLocation:
        name: losangeles001
        type: EdgeZone
      isHnsEnabled: true
      keyPolicy:
        keyExpirationPeriodInDays: 20
      kind: Storage
      location: eastus
      minimumTlsVersion: TLS1_2
      publicNetworkAccess: Enabled
      resourceGroupName: res9101
      routingPreference:
        publishInternetEndpoints: true
        publishMicrosoftEndpoints: true
        routingChoice: MicrosoftRouting
      sasPolicy:
        expirationAction: Log
        sasExpirationPeriod: 1.15:59:59
      sku:
        name: Standard_GRS
      tags:
        key1: value1
        key2: value2

```

{{% /example %}}
{{% example %}}
### StorageAccountCreatePremiumBlockBlobStorage
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageAccount = new AzureNative.Storage.StorageAccount("storageAccount", new()
    {
        AccountName = "sto4445",
        AllowSharedKeyAccess = true,
        Encryption = new AzureNative.Storage.Inputs.EncryptionArgs
        {
            KeySource = "Microsoft.Storage",
            RequireInfrastructureEncryption = false,
            Services = new AzureNative.Storage.Inputs.EncryptionServicesArgs
            {
                Blob = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
                File = new AzureNative.Storage.Inputs.EncryptionServiceArgs
                {
                    Enabled = true,
                    KeyType = "Account",
                },
            },
        },
        Kind = "BlockBlobStorage",
        Location = "eastus",
        MinimumTlsVersion = "TLS1_2",
        ResourceGroupName = "res9101",
        Sku = new AzureNative.Storage.Inputs.SkuArgs
        {
            Name = "Premium_LRS",
        },
        Tags = 
        {
            { "key1", "value1" },
            { "key2", "value2" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.storage.StorageAccount;
import com.pulumi.azurenative.storage.StorageAccountArgs;
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
        var storageAccount = new StorageAccount("storageAccount", StorageAccountArgs.builder()        
            .accountName("sto4445")
            .allowSharedKeyAccess(true)
            .encryption(Map.ofEntries(
                Map.entry("keySource", "Microsoft.Storage"),
                Map.entry("requireInfrastructureEncryption", false),
                Map.entry("services", Map.ofEntries(
                    Map.entry("blob", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    )),
                    Map.entry("file", Map.ofEntries(
                        Map.entry("enabled", true),
                        Map.entry("keyType", "Account")
                    ))
                ))
            ))
            .kind("BlockBlobStorage")
            .location("eastus")
            .minimumTlsVersion("TLS1_2")
            .resourceGroupName("res9101")
            .sku(Map.of("name", "Premium_LRS"))
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageAccount = new azure_native.storage.StorageAccount("storageAccount", {
    accountName: "sto4445",
    allowSharedKeyAccess: true,
    encryption: {
        keySource: "Microsoft.Storage",
        requireInfrastructureEncryption: false,
        services: {
            blob: {
                enabled: true,
                keyType: "Account",
            },
            file: {
                enabled: true,
                keyType: "Account",
            },
        },
    },
    kind: "BlockBlobStorage",
    location: "eastus",
    minimumTlsVersion: "TLS1_2",
    resourceGroupName: "res9101",
    sku: {
        name: "Premium_LRS",
    },
    tags: {
        key1: "value1",
        key2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_account = azure_native.storage.StorageAccount("storageAccount",
    account_name="sto4445",
    allow_shared_key_access=True,
    encryption=azure_native.storage.EncryptionResponseArgs(
        key_source="Microsoft.Storage",
        require_infrastructure_encryption=False,
        services={
            "blob": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
            "file": azure_native.storage.EncryptionServiceArgs(
                enabled=True,
                key_type="Account",
            ),
        },
    ),
    kind="BlockBlobStorage",
    location="eastus",
    minimum_tls_version="TLS1_2",
    resource_group_name="res9101",
    sku=azure_native.storage.SkuArgs(
        name="Premium_LRS",
    ),
    tags={
        "key1": "value1",
        "key2": "value2",
    })

```

```yaml
resources:
  storageAccount:
    type: azure-native:storage:StorageAccount
    properties:
      accountName: sto4445
      allowSharedKeyAccess: true
      encryption:
        keySource: Microsoft.Storage
        requireInfrastructureEncryption: false
        services:
          blob:
            enabled: true
            keyType: Account
          file:
            enabled: true
            keyType: Account
      kind: BlockBlobStorage
      location: eastus
      minimumTlsVersion: TLS1_2
      resourceGroupName: res9101
      sku:
        name: Premium_LRS
      tags:
        key1: value1
        key2: value2

```

{{% /example %}}
{{% example %}}
### StorageAccountCreateWithImmutabilityPolicy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageAccount = new AzureNative.Storage.StorageAccount("storageAccount", new()
    {
        AccountName = "sto4445",
        ExtendedLocation = new AzureNative.Storage.Inputs.ExtendedLocationArgs
        {
            Name = "losangeles001",
            Type = "EdgeZone",
        },
        ImmutableStorageWithVersioning = new AzureNative.Storage.Inputs.ImmutableStorageAccountArgs
        {
            Enabled = true,
            ImmutabilityPolicy = new AzureNative.Storage.Inputs.AccountImmutabilityPolicyPropertiesArgs
            {
                AllowProtectedAppendWrites = true,
                ImmutabilityPeriodSinceCreationInDays = 15,
                State = "Unlocked",
            },
        },
        Kind = "Storage",
        Location = "eastus",
        ResourceGroupName = "res9101",
        Sku = new AzureNative.Storage.Inputs.SkuArgs
        {
            Name = "Standard_GRS",
        },
    });

});


```

```go
package main

import (
	storage "github.com/pulumi/pulumi-azure-native-sdk/storage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storage.NewStorageAccount(ctx, "storageAccount", &storage.StorageAccountArgs{
			AccountName: pulumi.String("sto4445"),
			ExtendedLocation: &storage.ExtendedLocationArgs{
				Name: pulumi.String("losangeles001"),
				Type: pulumi.String("EdgeZone"),
			},
			ImmutableStorageWithVersioning: storage.ImmutableStorageAccountResponse{
				Enabled: pulumi.Bool(true),
				ImmutabilityPolicy: &storage.AccountImmutabilityPolicyPropertiesArgs{
					AllowProtectedAppendWrites:            pulumi.Bool(true),
					ImmutabilityPeriodSinceCreationInDays: pulumi.Int(15),
					State:                                 pulumi.String("Unlocked"),
				},
			},
			Kind:              pulumi.String("Storage"),
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("res9101"),
			Sku: &storage.SkuArgs{
				Name: pulumi.String("Standard_GRS"),
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
import com.pulumi.azurenative.storage.StorageAccount;
import com.pulumi.azurenative.storage.StorageAccountArgs;
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
        var storageAccount = new StorageAccount("storageAccount", StorageAccountArgs.builder()        
            .accountName("sto4445")
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "losangeles001"),
                Map.entry("type", "EdgeZone")
            ))
            .immutableStorageWithVersioning(Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("immutabilityPolicy", Map.ofEntries(
                    Map.entry("allowProtectedAppendWrites", true),
                    Map.entry("immutabilityPeriodSinceCreationInDays", 15),
                    Map.entry("state", "Unlocked")
                ))
            ))
            .kind("Storage")
            .location("eastus")
            .resourceGroupName("res9101")
            .sku(Map.of("name", "Standard_GRS"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageAccount = new azure_native.storage.StorageAccount("storageAccount", {
    accountName: "sto4445",
    extendedLocation: {
        name: "losangeles001",
        type: "EdgeZone",
    },
    immutableStorageWithVersioning: {
        enabled: true,
        immutabilityPolicy: {
            allowProtectedAppendWrites: true,
            immutabilityPeriodSinceCreationInDays: 15,
            state: "Unlocked",
        },
    },
    kind: "Storage",
    location: "eastus",
    resourceGroupName: "res9101",
    sku: {
        name: "Standard_GRS",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_account = azure_native.storage.StorageAccount("storageAccount",
    account_name="sto4445",
    extended_location=azure_native.storage.ExtendedLocationArgs(
        name="losangeles001",
        type="EdgeZone",
    ),
    immutable_storage_with_versioning=azure_native.storage.ImmutableStorageAccountResponseArgs(
        enabled=True,
        immutability_policy=azure_native.storage.AccountImmutabilityPolicyPropertiesArgs(
            allow_protected_append_writes=True,
            immutability_period_since_creation_in_days=15,
            state="Unlocked",
        ),
    ),
    kind="Storage",
    location="eastus",
    resource_group_name="res9101",
    sku=azure_native.storage.SkuArgs(
        name="Standard_GRS",
    ))

```

```yaml
resources:
  storageAccount:
    type: azure-native:storage:StorageAccount
    properties:
      accountName: sto4445
      extendedLocation:
        name: losangeles001
        type: EdgeZone
      immutableStorageWithVersioning:
        enabled: true
        immutabilityPolicy:
          allowProtectedAppendWrites: true
          immutabilityPeriodSinceCreationInDays: 15
          state: Unlocked
      kind: Storage
      location: eastus
      resourceGroupName: res9101
      sku:
        name: Standard_GRS

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storage:StorageAccount sto4445 /subscriptions/{subscription-id}/resourceGroups/res9101/providers/Microsoft.Storage/storageAccounts/sto4445 
```
