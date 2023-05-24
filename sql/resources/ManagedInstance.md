An Azure SQL managed instance.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create managed instance with all properties
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedInstance = new AzureNative.Sql.ManagedInstance("managedInstance", new()
    {
        AdministratorLogin = "dummylogin",
        AdministratorLoginPassword = "PLACEHOLDER",
        Administrators = new AzureNative.Sql.Inputs.ManagedInstanceExternalAdministratorArgs
        {
            AzureADOnlyAuthentication = true,
            Login = "bob@contoso.com",
            PrincipalType = "User",
            Sid = "00000011-1111-2222-2222-123456789111",
            TenantId = "00000011-1111-2222-2222-123456789111",
        },
        Collation = "SQL_Latin1_General_CP1_CI_AS",
        DnsZonePartner = "/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Sql/managedInstances/testinstance",
        InstancePoolId = "/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Sql/instancePools/pool1",
        LicenseType = "LicenseIncluded",
        Location = "Japan East",
        MaintenanceConfigurationId = "/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_JapanEast_MI_1",
        ManagedInstanceName = "testinstance",
        MinimalTlsVersion = "1.2",
        ProxyOverride = "Redirect",
        PublicDataEndpointEnabled = false,
        RequestedBackupStorageRedundancy = "Geo",
        ResourceGroupName = "testrg",
        ServicePrincipal = new AzureNative.Sql.Inputs.ServicePrincipalArgs
        {
            Type = "SystemAssigned",
        },
        Sku = new AzureNative.Sql.Inputs.SkuArgs
        {
            Name = "GP_Gen5",
            Tier = "GeneralPurpose",
        },
        StorageSizeInGB = 1024,
        SubnetId = "/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1",
        Tags = 
        {
            { "tagKey1", "TagValue1" },
        },
        TimezoneId = "UTC",
        VCores = 8,
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewManagedInstance(ctx, "managedInstance", &sql.ManagedInstanceArgs{
			AdministratorLogin:         pulumi.String("dummylogin"),
			AdministratorLoginPassword: pulumi.String("PLACEHOLDER"),
			Administrators: &sql.ManagedInstanceExternalAdministratorArgs{
				AzureADOnlyAuthentication: pulumi.Bool(true),
				Login:                     pulumi.String("bob@contoso.com"),
				PrincipalType:             pulumi.String("User"),
				Sid:                       pulumi.String("00000011-1111-2222-2222-123456789111"),
				TenantId:                  pulumi.String("00000011-1111-2222-2222-123456789111"),
			},
			Collation:                        pulumi.String("SQL_Latin1_General_CP1_CI_AS"),
			DnsZonePartner:                   pulumi.String("/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Sql/managedInstances/testinstance"),
			InstancePoolId:                   pulumi.String("/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Sql/instancePools/pool1"),
			LicenseType:                      pulumi.String("LicenseIncluded"),
			Location:                         pulumi.String("Japan East"),
			MaintenanceConfigurationId:       pulumi.String("/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_JapanEast_MI_1"),
			ManagedInstanceName:              pulumi.String("testinstance"),
			MinimalTlsVersion:                pulumi.String("1.2"),
			ProxyOverride:                    pulumi.String("Redirect"),
			PublicDataEndpointEnabled:        pulumi.Bool(false),
			RequestedBackupStorageRedundancy: pulumi.String("Geo"),
			ResourceGroupName:                pulumi.String("testrg"),
			ServicePrincipal: &sql.ServicePrincipalArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			Sku: &sql.SkuArgs{
				Name: pulumi.String("GP_Gen5"),
				Tier: pulumi.String("GeneralPurpose"),
			},
			StorageSizeInGB: pulumi.Int(1024),
			SubnetId:        pulumi.String("/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1"),
			Tags: pulumi.StringMap{
				"tagKey1": pulumi.String("TagValue1"),
			},
			TimezoneId: pulumi.String("UTC"),
			VCores:     pulumi.Int(8),
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
import com.pulumi.azurenative.sql.ManagedInstance;
import com.pulumi.azurenative.sql.ManagedInstanceArgs;
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
        var managedInstance = new ManagedInstance("managedInstance", ManagedInstanceArgs.builder()        
            .administratorLogin("dummylogin")
            .administratorLoginPassword("PLACEHOLDER")
            .administrators(Map.ofEntries(
                Map.entry("azureADOnlyAuthentication", true),
                Map.entry("login", "bob@contoso.com"),
                Map.entry("principalType", "User"),
                Map.entry("sid", "00000011-1111-2222-2222-123456789111"),
                Map.entry("tenantId", "00000011-1111-2222-2222-123456789111")
            ))
            .collation("SQL_Latin1_General_CP1_CI_AS")
            .dnsZonePartner("/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Sql/managedInstances/testinstance")
            .instancePoolId("/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Sql/instancePools/pool1")
            .licenseType("LicenseIncluded")
            .location("Japan East")
            .maintenanceConfigurationId("/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_JapanEast_MI_1")
            .managedInstanceName("testinstance")
            .minimalTlsVersion("1.2")
            .proxyOverride("Redirect")
            .publicDataEndpointEnabled(false)
            .requestedBackupStorageRedundancy("Geo")
            .resourceGroupName("testrg")
            .servicePrincipal(Map.of("type", "SystemAssigned"))
            .sku(Map.ofEntries(
                Map.entry("name", "GP_Gen5"),
                Map.entry("tier", "GeneralPurpose")
            ))
            .storageSizeInGB(1024)
            .subnetId("/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1")
            .tags(Map.of("tagKey1", "TagValue1"))
            .timezoneId("UTC")
            .vCores(8)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedInstance = new azure_native.sql.ManagedInstance("managedInstance", {
    administratorLogin: "dummylogin",
    administratorLoginPassword: "PLACEHOLDER",
    administrators: {
        azureADOnlyAuthentication: true,
        login: "bob@contoso.com",
        principalType: "User",
        sid: "00000011-1111-2222-2222-123456789111",
        tenantId: "00000011-1111-2222-2222-123456789111",
    },
    collation: "SQL_Latin1_General_CP1_CI_AS",
    dnsZonePartner: "/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Sql/managedInstances/testinstance",
    instancePoolId: "/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Sql/instancePools/pool1",
    licenseType: "LicenseIncluded",
    location: "Japan East",
    maintenanceConfigurationId: "/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_JapanEast_MI_1",
    managedInstanceName: "testinstance",
    minimalTlsVersion: "1.2",
    proxyOverride: "Redirect",
    publicDataEndpointEnabled: false,
    requestedBackupStorageRedundancy: "Geo",
    resourceGroupName: "testrg",
    servicePrincipal: {
        type: "SystemAssigned",
    },
    sku: {
        name: "GP_Gen5",
        tier: "GeneralPurpose",
    },
    storageSizeInGB: 1024,
    subnetId: "/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1",
    tags: {
        tagKey1: "TagValue1",
    },
    timezoneId: "UTC",
    vCores: 8,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_instance = azure_native.sql.ManagedInstance("managedInstance",
    administrator_login="dummylogin",
    administrator_login_password="PLACEHOLDER",
    administrators=azure_native.sql.ManagedInstanceExternalAdministratorArgs(
        azure_ad_only_authentication=True,
        login="bob@contoso.com",
        principal_type="User",
        sid="00000011-1111-2222-2222-123456789111",
        tenant_id="00000011-1111-2222-2222-123456789111",
    ),
    collation="SQL_Latin1_General_CP1_CI_AS",
    dns_zone_partner="/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Sql/managedInstances/testinstance",
    instance_pool_id="/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Sql/instancePools/pool1",
    license_type="LicenseIncluded",
    location="Japan East",
    maintenance_configuration_id="/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_JapanEast_MI_1",
    managed_instance_name="testinstance",
    minimal_tls_version="1.2",
    proxy_override="Redirect",
    public_data_endpoint_enabled=False,
    requested_backup_storage_redundancy="Geo",
    resource_group_name="testrg",
    service_principal=azure_native.sql.ServicePrincipalArgs(
        type="SystemAssigned",
    ),
    sku=azure_native.sql.SkuArgs(
        name="GP_Gen5",
        tier="GeneralPurpose",
    ),
    storage_size_in_gb=1024,
    subnet_id="/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1",
    tags={
        "tagKey1": "TagValue1",
    },
    timezone_id="UTC",
    v_cores=8)

```

```yaml
resources:
  managedInstance:
    type: azure-native:sql:ManagedInstance
    properties:
      administratorLogin: dummylogin
      administratorLoginPassword: PLACEHOLDER
      administrators:
        azureADOnlyAuthentication: true
        login: bob@contoso.com
        principalType: User
        sid: 00000011-1111-2222-2222-123456789111
        tenantId: 00000011-1111-2222-2222-123456789111
      collation: SQL_Latin1_General_CP1_CI_AS
      dnsZonePartner: /subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Sql/managedInstances/testinstance
      instancePoolId: /subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Sql/instancePools/pool1
      licenseType: LicenseIncluded
      location: Japan East
      maintenanceConfigurationId: /subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_JapanEast_MI_1
      managedInstanceName: testinstance
      minimalTlsVersion: '1.2'
      proxyOverride: Redirect
      publicDataEndpointEnabled: false
      requestedBackupStorageRedundancy: Geo
      resourceGroupName: testrg
      servicePrincipal:
        type: SystemAssigned
      sku:
        name: GP_Gen5
        tier: GeneralPurpose
      storageSizeInGB: 1024
      subnetId: /subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1
      tags:
        tagKey1: TagValue1
      timezoneId: UTC
      vCores: 8

```

{{% /example %}}
{{% example %}}
### Create managed instance with minimal properties
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedInstance = new AzureNative.Sql.ManagedInstance("managedInstance", new()
    {
        AdministratorLogin = "dummylogin",
        AdministratorLoginPassword = "PLACEHOLDER",
        LicenseType = "LicenseIncluded",
        Location = "Japan East",
        ManagedInstanceName = "testinstance",
        ResourceGroupName = "testrg",
        Sku = new AzureNative.Sql.Inputs.SkuArgs
        {
            Name = "GP_Gen4",
            Tier = "GeneralPurpose",
        },
        StorageSizeInGB = 1024,
        SubnetId = "/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1",
        VCores = 8,
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewManagedInstance(ctx, "managedInstance", &sql.ManagedInstanceArgs{
			AdministratorLogin:         pulumi.String("dummylogin"),
			AdministratorLoginPassword: pulumi.String("PLACEHOLDER"),
			LicenseType:                pulumi.String("LicenseIncluded"),
			Location:                   pulumi.String("Japan East"),
			ManagedInstanceName:        pulumi.String("testinstance"),
			ResourceGroupName:          pulumi.String("testrg"),
			Sku: &sql.SkuArgs{
				Name: pulumi.String("GP_Gen4"),
				Tier: pulumi.String("GeneralPurpose"),
			},
			StorageSizeInGB: pulumi.Int(1024),
			SubnetId:        pulumi.String("/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1"),
			VCores:          pulumi.Int(8),
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
import com.pulumi.azurenative.sql.ManagedInstance;
import com.pulumi.azurenative.sql.ManagedInstanceArgs;
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
        var managedInstance = new ManagedInstance("managedInstance", ManagedInstanceArgs.builder()        
            .administratorLogin("dummylogin")
            .administratorLoginPassword("PLACEHOLDER")
            .licenseType("LicenseIncluded")
            .location("Japan East")
            .managedInstanceName("testinstance")
            .resourceGroupName("testrg")
            .sku(Map.ofEntries(
                Map.entry("name", "GP_Gen4"),
                Map.entry("tier", "GeneralPurpose")
            ))
            .storageSizeInGB(1024)
            .subnetId("/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1")
            .vCores(8)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedInstance = new azure_native.sql.ManagedInstance("managedInstance", {
    administratorLogin: "dummylogin",
    administratorLoginPassword: "PLACEHOLDER",
    licenseType: "LicenseIncluded",
    location: "Japan East",
    managedInstanceName: "testinstance",
    resourceGroupName: "testrg",
    sku: {
        name: "GP_Gen4",
        tier: "GeneralPurpose",
    },
    storageSizeInGB: 1024,
    subnetId: "/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1",
    vCores: 8,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_instance = azure_native.sql.ManagedInstance("managedInstance",
    administrator_login="dummylogin",
    administrator_login_password="PLACEHOLDER",
    license_type="LicenseIncluded",
    location="Japan East",
    managed_instance_name="testinstance",
    resource_group_name="testrg",
    sku=azure_native.sql.SkuArgs(
        name="GP_Gen4",
        tier="GeneralPurpose",
    ),
    storage_size_in_gb=1024,
    subnet_id="/subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1",
    v_cores=8)

```

```yaml
resources:
  managedInstance:
    type: azure-native:sql:ManagedInstance
    properties:
      administratorLogin: dummylogin
      administratorLoginPassword: PLACEHOLDER
      licenseType: LicenseIncluded
      location: Japan East
      managedInstanceName: testinstance
      resourceGroupName: testrg
      sku:
        name: GP_Gen4
        tier: GeneralPurpose
      storageSizeInGB: 1024
      subnetId: /subscriptions/20D7082A-0FC7-4468-82BD-542694D5042B/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1
      vCores: 8

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ManagedInstance testinstance /subscriptions/20d7082a-0fc7-4468-82bd-542694d5042b/resourceGroups/testrg/providers/Microsoft.Sql/managedInstances/testinstance 
```
