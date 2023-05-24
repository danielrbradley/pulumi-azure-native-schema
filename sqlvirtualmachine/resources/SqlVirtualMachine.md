A SQL virtual machine.
API Version: 2022-02-01.
Previous API Version: 2017-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates a SQL virtual machine and joins it to a SQL virtual machine group.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlVirtualMachine = new AzureNative.SqlVirtualMachine.SqlVirtualMachine("sqlVirtualMachine", new()
    {
        Location = "northeurope",
        ResourceGroupName = "testrg",
        SqlVirtualMachineGroupResourceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachineGroups/testvmgroup",
        SqlVirtualMachineName = "testvm",
        VirtualMachineResourceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm2",
        WsfcDomainCredentials = new AzureNative.SqlVirtualMachine.Inputs.WsfcDomainCredentialsArgs
        {
            ClusterBootstrapAccountPassword = "<Password>",
            ClusterOperatorAccountPassword = "<Password>",
            SqlServiceAccountPassword = "<Password>",
        },
        WsfcStaticIp = "10.0.0.7",
    });

});


```

```go
package main

import (
	sqlvirtualmachine "github.com/pulumi/pulumi-azure-native-sdk/sqlvirtualmachine"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sqlvirtualmachine.NewSqlVirtualMachine(ctx, "sqlVirtualMachine", &sqlvirtualmachine.SqlVirtualMachineArgs{
			Location:                         pulumi.String("northeurope"),
			ResourceGroupName:                pulumi.String("testrg"),
			SqlVirtualMachineGroupResourceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachineGroups/testvmgroup"),
			SqlVirtualMachineName:            pulumi.String("testvm"),
			VirtualMachineResourceId:         pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm2"),
			WsfcDomainCredentials: &sqlvirtualmachine.WsfcDomainCredentialsArgs{
				ClusterBootstrapAccountPassword: pulumi.String("<Password>"),
				ClusterOperatorAccountPassword:  pulumi.String("<Password>"),
				SqlServiceAccountPassword:       pulumi.String("<Password>"),
			},
			WsfcStaticIp: pulumi.String("10.0.0.7"),
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
import com.pulumi.azurenative.sqlvirtualmachine.SqlVirtualMachine;
import com.pulumi.azurenative.sqlvirtualmachine.SqlVirtualMachineArgs;
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
        var sqlVirtualMachine = new SqlVirtualMachine("sqlVirtualMachine", SqlVirtualMachineArgs.builder()        
            .location("northeurope")
            .resourceGroupName("testrg")
            .sqlVirtualMachineGroupResourceId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachineGroups/testvmgroup")
            .sqlVirtualMachineName("testvm")
            .virtualMachineResourceId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm2")
            .wsfcDomainCredentials(Map.ofEntries(
                Map.entry("clusterBootstrapAccountPassword", "<Password>"),
                Map.entry("clusterOperatorAccountPassword", "<Password>"),
                Map.entry("sqlServiceAccountPassword", "<Password>")
            ))
            .wsfcStaticIp("10.0.0.7")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlVirtualMachine = new azure_native.sqlvirtualmachine.SqlVirtualMachine("sqlVirtualMachine", {
    location: "northeurope",
    resourceGroupName: "testrg",
    sqlVirtualMachineGroupResourceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachineGroups/testvmgroup",
    sqlVirtualMachineName: "testvm",
    virtualMachineResourceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm2",
    wsfcDomainCredentials: {
        clusterBootstrapAccountPassword: "<Password>",
        clusterOperatorAccountPassword: "<Password>",
        sqlServiceAccountPassword: "<Password>",
    },
    wsfcStaticIp: "10.0.0.7",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_virtual_machine = azure_native.sqlvirtualmachine.SqlVirtualMachine("sqlVirtualMachine",
    location="northeurope",
    resource_group_name="testrg",
    sql_virtual_machine_group_resource_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachineGroups/testvmgroup",
    sql_virtual_machine_name="testvm",
    virtual_machine_resource_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm2",
    wsfc_domain_credentials=azure_native.sqlvirtualmachine.WsfcDomainCredentialsArgs(
        cluster_bootstrap_account_password="<Password>",
        cluster_operator_account_password="<Password>",
        sql_service_account_password="<Password>",
    ),
    wsfc_static_ip="10.0.0.7")

```

```yaml
resources:
  sqlVirtualMachine:
    type: azure-native:sqlvirtualmachine:SqlVirtualMachine
    properties:
      location: northeurope
      resourceGroupName: testrg
      sqlVirtualMachineGroupResourceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachineGroups/testvmgroup
      sqlVirtualMachineName: testvm
      virtualMachineResourceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm2
      wsfcDomainCredentials:
        clusterBootstrapAccountPassword: <Password>
        clusterOperatorAccountPassword: <Password>
        sqlServiceAccountPassword: <Password>
      wsfcStaticIp: 10.0.0.7

```

{{% /example %}}
{{% example %}}
### Creates or updates a SQL virtual machine for Automated Back up Settings with Weekly and Days of the week to run the back up.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlVirtualMachine = new AzureNative.SqlVirtualMachine.SqlVirtualMachine("sqlVirtualMachine", new()
    {
        AutoBackupSettings = new AzureNative.SqlVirtualMachine.Inputs.AutoBackupSettingsArgs
        {
            BackupScheduleType = "Manual",
            BackupSystemDbs = true,
            DaysOfWeek = new[]
            {
                "Monday",
                "Friday",
            },
            Enable = true,
            EnableEncryption = true,
            FullBackupFrequency = "Weekly",
            FullBackupStartTime = 6,
            FullBackupWindowHours = 11,
            LogBackupFrequency = 10,
            Password = "<Password>",
            RetentionPeriod = 17,
            StorageAccessKey = "<primary storage access key>",
            StorageAccountUrl = "https://teststorage.blob.core.windows.net/",
            StorageContainerName = "testcontainer",
        },
        AutoPatchingSettings = new AzureNative.SqlVirtualMachine.Inputs.AutoPatchingSettingsArgs
        {
            DayOfWeek = AzureNative.SqlVirtualMachine.DayOfWeek.Sunday,
            Enable = true,
            MaintenanceWindowDuration = 60,
            MaintenanceWindowStartingHour = 2,
        },
        KeyVaultCredentialSettings = new AzureNative.SqlVirtualMachine.Inputs.KeyVaultCredentialSettingsArgs
        {
            Enable = false,
        },
        Location = "northeurope",
        ResourceGroupName = "testrg",
        ServerConfigurationsManagementSettings = new AzureNative.SqlVirtualMachine.Inputs.ServerConfigurationsManagementSettingsArgs
        {
            AdditionalFeaturesServerConfigurations = new AzureNative.SqlVirtualMachine.Inputs.AdditionalFeaturesServerConfigurationsArgs
            {
                IsRServicesEnabled = false,
            },
            SqlConnectivityUpdateSettings = new AzureNative.SqlVirtualMachine.Inputs.SqlConnectivityUpdateSettingsArgs
            {
                ConnectivityType = "PRIVATE",
                Port = 1433,
                SqlAuthUpdatePassword = "<password>",
                SqlAuthUpdateUserName = "sqllogin",
            },
            SqlStorageUpdateSettings = new AzureNative.SqlVirtualMachine.Inputs.SqlStorageUpdateSettingsArgs
            {
                DiskConfigurationType = "NEW",
                DiskCount = 1,
                StartingDeviceId = 2,
            },
            SqlWorkloadTypeUpdateSettings = new AzureNative.SqlVirtualMachine.Inputs.SqlWorkloadTypeUpdateSettingsArgs
            {
                SqlWorkloadType = "OLTP",
            },
        },
        SqlImageSku = "Enterprise",
        SqlManagement = "Full",
        SqlServerLicenseType = "PAYG",
        SqlVirtualMachineName = "testvm",
        VirtualMachineResourceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm",
    });

});


```

```go
package main

import (
	sqlvirtualmachine "github.com/pulumi/pulumi-azure-native-sdk/sqlvirtualmachine"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sqlvirtualmachine.NewSqlVirtualMachine(ctx, "sqlVirtualMachine", &sqlvirtualmachine.SqlVirtualMachineArgs{
			AutoBackupSettings: &sqlvirtualmachine.AutoBackupSettingsArgs{
				BackupScheduleType: pulumi.String("Manual"),
				BackupSystemDbs:    pulumi.Bool(true),
				DaysOfWeek: pulumi.StringArray{
					pulumi.String("Monday"),
					pulumi.String("Friday"),
				},
				Enable:                pulumi.Bool(true),
				EnableEncryption:      pulumi.Bool(true),
				FullBackupFrequency:   pulumi.String("Weekly"),
				FullBackupStartTime:   pulumi.Int(6),
				FullBackupWindowHours: pulumi.Int(11),
				LogBackupFrequency:    pulumi.Int(10),
				Password:              pulumi.String("<Password>"),
				RetentionPeriod:       pulumi.Int(17),
				StorageAccessKey:      pulumi.String("<primary storage access key>"),
				StorageAccountUrl:     pulumi.String("https://teststorage.blob.core.windows.net/"),
				StorageContainerName:  pulumi.String("testcontainer"),
			},
			AutoPatchingSettings: &sqlvirtualmachine.AutoPatchingSettingsArgs{
				DayOfWeek:                     sqlvirtualmachine.DayOfWeekSunday,
				Enable:                        pulumi.Bool(true),
				MaintenanceWindowDuration:     pulumi.Int(60),
				MaintenanceWindowStartingHour: pulumi.Int(2),
			},
			KeyVaultCredentialSettings: &sqlvirtualmachine.KeyVaultCredentialSettingsArgs{
				Enable: pulumi.Bool(false),
			},
			Location:          pulumi.String("northeurope"),
			ResourceGroupName: pulumi.String("testrg"),
			ServerConfigurationsManagementSettings: sqlvirtualmachine.ServerConfigurationsManagementSettingsResponse{
				AdditionalFeaturesServerConfigurations: &sqlvirtualmachine.AdditionalFeaturesServerConfigurationsArgs{
					IsRServicesEnabled: pulumi.Bool(false),
				},
				SqlConnectivityUpdateSettings: &sqlvirtualmachine.SqlConnectivityUpdateSettingsArgs{
					ConnectivityType:      pulumi.String("PRIVATE"),
					Port:                  pulumi.Int(1433),
					SqlAuthUpdatePassword: pulumi.String("<password>"),
					SqlAuthUpdateUserName: pulumi.String("sqllogin"),
				},
				SqlStorageUpdateSettings: &sqlvirtualmachine.SqlStorageUpdateSettingsArgs{
					DiskConfigurationType: pulumi.String("NEW"),
					DiskCount:             pulumi.Int(1),
					StartingDeviceId:      pulumi.Int(2),
				},
				SqlWorkloadTypeUpdateSettings: &sqlvirtualmachine.SqlWorkloadTypeUpdateSettingsArgs{
					SqlWorkloadType: pulumi.String("OLTP"),
				},
			},
			SqlImageSku:              pulumi.String("Enterprise"),
			SqlManagement:            pulumi.String("Full"),
			SqlServerLicenseType:     pulumi.String("PAYG"),
			SqlVirtualMachineName:    pulumi.String("testvm"),
			VirtualMachineResourceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm"),
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
import com.pulumi.azurenative.sqlvirtualmachine.SqlVirtualMachine;
import com.pulumi.azurenative.sqlvirtualmachine.SqlVirtualMachineArgs;
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
        var sqlVirtualMachine = new SqlVirtualMachine("sqlVirtualMachine", SqlVirtualMachineArgs.builder()        
            .autoBackupSettings(Map.ofEntries(
                Map.entry("backupScheduleType", "Manual"),
                Map.entry("backupSystemDbs", true),
                Map.entry("daysOfWeek",                 
                    "Monday",
                    "Friday"),
                Map.entry("enable", true),
                Map.entry("enableEncryption", true),
                Map.entry("fullBackupFrequency", "Weekly"),
                Map.entry("fullBackupStartTime", 6),
                Map.entry("fullBackupWindowHours", 11),
                Map.entry("logBackupFrequency", 10),
                Map.entry("password", "<Password>"),
                Map.entry("retentionPeriod", 17),
                Map.entry("storageAccessKey", "<primary storage access key>"),
                Map.entry("storageAccountUrl", "https://teststorage.blob.core.windows.net/"),
                Map.entry("storageContainerName", "testcontainer")
            ))
            .autoPatchingSettings(Map.ofEntries(
                Map.entry("dayOfWeek", "Sunday"),
                Map.entry("enable", true),
                Map.entry("maintenanceWindowDuration", 60),
                Map.entry("maintenanceWindowStartingHour", 2)
            ))
            .keyVaultCredentialSettings(Map.of("enable", false))
            .location("northeurope")
            .resourceGroupName("testrg")
            .serverConfigurationsManagementSettings(Map.ofEntries(
                Map.entry("additionalFeaturesServerConfigurations", Map.of("isRServicesEnabled", false)),
                Map.entry("sqlConnectivityUpdateSettings", Map.ofEntries(
                    Map.entry("connectivityType", "PRIVATE"),
                    Map.entry("port", 1433),
                    Map.entry("sqlAuthUpdatePassword", "<password>"),
                    Map.entry("sqlAuthUpdateUserName", "sqllogin")
                )),
                Map.entry("sqlStorageUpdateSettings", Map.ofEntries(
                    Map.entry("diskConfigurationType", "NEW"),
                    Map.entry("diskCount", 1),
                    Map.entry("startingDeviceId", 2)
                )),
                Map.entry("sqlWorkloadTypeUpdateSettings", Map.of("sqlWorkloadType", "OLTP"))
            ))
            .sqlImageSku("Enterprise")
            .sqlManagement("Full")
            .sqlServerLicenseType("PAYG")
            .sqlVirtualMachineName("testvm")
            .virtualMachineResourceId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlVirtualMachine = new azure_native.sqlvirtualmachine.SqlVirtualMachine("sqlVirtualMachine", {
    autoBackupSettings: {
        backupScheduleType: "Manual",
        backupSystemDbs: true,
        daysOfWeek: [
            "Monday",
            "Friday",
        ],
        enable: true,
        enableEncryption: true,
        fullBackupFrequency: "Weekly",
        fullBackupStartTime: 6,
        fullBackupWindowHours: 11,
        logBackupFrequency: 10,
        password: "<Password>",
        retentionPeriod: 17,
        storageAccessKey: "<primary storage access key>",
        storageAccountUrl: "https://teststorage.blob.core.windows.net/",
        storageContainerName: "testcontainer",
    },
    autoPatchingSettings: {
        dayOfWeek: azure_native.sqlvirtualmachine.DayOfWeek.Sunday,
        enable: true,
        maintenanceWindowDuration: 60,
        maintenanceWindowStartingHour: 2,
    },
    keyVaultCredentialSettings: {
        enable: false,
    },
    location: "northeurope",
    resourceGroupName: "testrg",
    serverConfigurationsManagementSettings: {
        additionalFeaturesServerConfigurations: {
            isRServicesEnabled: false,
        },
        sqlConnectivityUpdateSettings: {
            connectivityType: "PRIVATE",
            port: 1433,
            sqlAuthUpdatePassword: "<password>",
            sqlAuthUpdateUserName: "sqllogin",
        },
        sqlStorageUpdateSettings: {
            diskConfigurationType: "NEW",
            diskCount: 1,
            startingDeviceId: 2,
        },
        sqlWorkloadTypeUpdateSettings: {
            sqlWorkloadType: "OLTP",
        },
    },
    sqlImageSku: "Enterprise",
    sqlManagement: "Full",
    sqlServerLicenseType: "PAYG",
    sqlVirtualMachineName: "testvm",
    virtualMachineResourceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_virtual_machine = azure_native.sqlvirtualmachine.SqlVirtualMachine("sqlVirtualMachine",
    auto_backup_settings=azure_native.sqlvirtualmachine.AutoBackupSettingsArgs(
        backup_schedule_type="Manual",
        backup_system_dbs=True,
        days_of_week=[
            "Monday",
            "Friday",
        ],
        enable=True,
        enable_encryption=True,
        full_backup_frequency="Weekly",
        full_backup_start_time=6,
        full_backup_window_hours=11,
        log_backup_frequency=10,
        password="<Password>",
        retention_period=17,
        storage_access_key="<primary storage access key>",
        storage_account_url="https://teststorage.blob.core.windows.net/",
        storage_container_name="testcontainer",
    ),
    auto_patching_settings=azure_native.sqlvirtualmachine.AutoPatchingSettingsArgs(
        day_of_week=azure_native.sqlvirtualmachine.DayOfWeek.SUNDAY,
        enable=True,
        maintenance_window_duration=60,
        maintenance_window_starting_hour=2,
    ),
    key_vault_credential_settings=azure_native.sqlvirtualmachine.KeyVaultCredentialSettingsArgs(
        enable=False,
    ),
    location="northeurope",
    resource_group_name="testrg",
    server_configurations_management_settings=azure_native.sqlvirtualmachine.ServerConfigurationsManagementSettingsResponseArgs(
        additional_features_server_configurations=azure_native.sqlvirtualmachine.AdditionalFeaturesServerConfigurationsArgs(
            is_r_services_enabled=False,
        ),
        sql_connectivity_update_settings=azure_native.sqlvirtualmachine.SqlConnectivityUpdateSettingsArgs(
            connectivity_type="PRIVATE",
            port=1433,
            sql_auth_update_password="<password>",
            sql_auth_update_user_name="sqllogin",
        ),
        sql_storage_update_settings=azure_native.sqlvirtualmachine.SqlStorageUpdateSettingsArgs(
            disk_configuration_type="NEW",
            disk_count=1,
            starting_device_id=2,
        ),
        sql_workload_type_update_settings=azure_native.sqlvirtualmachine.SqlWorkloadTypeUpdateSettingsArgs(
            sql_workload_type="OLTP",
        ),
    ),
    sql_image_sku="Enterprise",
    sql_management="Full",
    sql_server_license_type="PAYG",
    sql_virtual_machine_name="testvm",
    virtual_machine_resource_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm")

```

```yaml
resources:
  sqlVirtualMachine:
    type: azure-native:sqlvirtualmachine:SqlVirtualMachine
    properties:
      autoBackupSettings:
        backupScheduleType: Manual
        backupSystemDbs: true
        daysOfWeek:
          - Monday
          - Friday
        enable: true
        enableEncryption: true
        fullBackupFrequency: Weekly
        fullBackupStartTime: 6
        fullBackupWindowHours: 11
        logBackupFrequency: 10
        password: <Password>
        retentionPeriod: 17
        storageAccessKey: <primary storage access key>
        storageAccountUrl: https://teststorage.blob.core.windows.net/
        storageContainerName: testcontainer
      autoPatchingSettings:
        dayOfWeek: Sunday
        enable: true
        maintenanceWindowDuration: 60
        maintenanceWindowStartingHour: 2
      keyVaultCredentialSettings:
        enable: false
      location: northeurope
      resourceGroupName: testrg
      serverConfigurationsManagementSettings:
        additionalFeaturesServerConfigurations:
          isRServicesEnabled: false
        sqlConnectivityUpdateSettings:
          connectivityType: PRIVATE
          port: 1433
          sqlAuthUpdatePassword: <password>
          sqlAuthUpdateUserName: sqllogin
        sqlStorageUpdateSettings:
          diskConfigurationType: NEW
          diskCount: 1
          startingDeviceId: 2
        sqlWorkloadTypeUpdateSettings:
          sqlWorkloadType: OLTP
      sqlImageSku: Enterprise
      sqlManagement: Full
      sqlServerLicenseType: PAYG
      sqlVirtualMachineName: testvm
      virtualMachineResourceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm

```

{{% /example %}}
{{% example %}}
### Creates or updates a SQL virtual machine for Storage Configuration Settings to EXTEND Data, Log or TempDB storage pool.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlVirtualMachine = new AzureNative.SqlVirtualMachine.SqlVirtualMachine("sqlVirtualMachine", new()
    {
        Location = "northeurope",
        ResourceGroupName = "testrg",
        SqlVirtualMachineName = "testvm",
        StorageConfigurationSettings = new AzureNative.SqlVirtualMachine.Inputs.StorageConfigurationSettingsArgs
        {
            DiskConfigurationType = "EXTEND",
            SqlDataSettings = new AzureNative.SqlVirtualMachine.Inputs.SQLStorageSettingsArgs
            {
                Luns = new[]
                {
                    2,
                },
            },
        },
        VirtualMachineResourceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm",
    });

});


```

```go
package main

import (
	sqlvirtualmachine "github.com/pulumi/pulumi-azure-native-sdk/sqlvirtualmachine"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sqlvirtualmachine.NewSqlVirtualMachine(ctx, "sqlVirtualMachine", &sqlvirtualmachine.SqlVirtualMachineArgs{
			Location:              pulumi.String("northeurope"),
			ResourceGroupName:     pulumi.String("testrg"),
			SqlVirtualMachineName: pulumi.String("testvm"),
			StorageConfigurationSettings: sqlvirtualmachine.StorageConfigurationSettingsResponse{
				DiskConfigurationType: pulumi.String("EXTEND"),
				SqlDataSettings: &sqlvirtualmachine.SQLStorageSettingsArgs{
					Luns: pulumi.IntArray{
						pulumi.Int(2),
					},
				},
			},
			VirtualMachineResourceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm"),
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
import com.pulumi.azurenative.sqlvirtualmachine.SqlVirtualMachine;
import com.pulumi.azurenative.sqlvirtualmachine.SqlVirtualMachineArgs;
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
        var sqlVirtualMachine = new SqlVirtualMachine("sqlVirtualMachine", SqlVirtualMachineArgs.builder()        
            .location("northeurope")
            .resourceGroupName("testrg")
            .sqlVirtualMachineName("testvm")
            .storageConfigurationSettings(Map.ofEntries(
                Map.entry("diskConfigurationType", "EXTEND"),
                Map.entry("sqlDataSettings", Map.of("luns", 2))
            ))
            .virtualMachineResourceId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlVirtualMachine = new azure_native.sqlvirtualmachine.SqlVirtualMachine("sqlVirtualMachine", {
    location: "northeurope",
    resourceGroupName: "testrg",
    sqlVirtualMachineName: "testvm",
    storageConfigurationSettings: {
        diskConfigurationType: "EXTEND",
        sqlDataSettings: {
            luns: [2],
        },
    },
    virtualMachineResourceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_virtual_machine = azure_native.sqlvirtualmachine.SqlVirtualMachine("sqlVirtualMachine",
    location="northeurope",
    resource_group_name="testrg",
    sql_virtual_machine_name="testvm",
    storage_configuration_settings=azure_native.sqlvirtualmachine.StorageConfigurationSettingsResponseArgs(
        disk_configuration_type="EXTEND",
        sql_data_settings=azure_native.sqlvirtualmachine.SQLStorageSettingsArgs(
            luns=[2],
        ),
    ),
    virtual_machine_resource_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm")

```

```yaml
resources:
  sqlVirtualMachine:
    type: azure-native:sqlvirtualmachine:SqlVirtualMachine
    properties:
      location: northeurope
      resourceGroupName: testrg
      sqlVirtualMachineName: testvm
      storageConfigurationSettings:
        diskConfigurationType: EXTEND
        sqlDataSettings:
          luns:
            - 2
      virtualMachineResourceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm

```

{{% /example %}}
{{% example %}}
### Creates or updates a SQL virtual machine for Storage Configuration Settings to NEW Data, Log and TempDB storage pool.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlVirtualMachine = new AzureNative.SqlVirtualMachine.SqlVirtualMachine("sqlVirtualMachine", new()
    {
        Location = "northeurope",
        ResourceGroupName = "testrg",
        SqlVirtualMachineName = "testvm",
        StorageConfigurationSettings = new AzureNative.SqlVirtualMachine.Inputs.StorageConfigurationSettingsArgs
        {
            DiskConfigurationType = "NEW",
            SqlDataSettings = new AzureNative.SqlVirtualMachine.Inputs.SQLStorageSettingsArgs
            {
                DefaultFilePath = "F:\\folderpath\\",
                Luns = new[]
                {
                    0,
                },
            },
            SqlLogSettings = new AzureNative.SqlVirtualMachine.Inputs.SQLStorageSettingsArgs
            {
                DefaultFilePath = "G:\\folderpath\\",
                Luns = new[]
                {
                    1,
                },
            },
            SqlSystemDbOnDataDisk = true,
            SqlTempDbSettings = new AzureNative.SqlVirtualMachine.Inputs.SQLTempDbSettingsArgs
            {
                DataFileCount = 8,
                DataFileSize = 256,
                DataGrowth = 512,
                DefaultFilePath = "D:\\TEMP",
                LogFileSize = 256,
                LogGrowth = 512,
            },
            StorageWorkloadType = "OLTP",
        },
        VirtualMachineResourceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm",
    });

});


```

```go
package main

import (
	sqlvirtualmachine "github.com/pulumi/pulumi-azure-native-sdk/sqlvirtualmachine"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sqlvirtualmachine.NewSqlVirtualMachine(ctx, "sqlVirtualMachine", &sqlvirtualmachine.SqlVirtualMachineArgs{
			Location:              pulumi.String("northeurope"),
			ResourceGroupName:     pulumi.String("testrg"),
			SqlVirtualMachineName: pulumi.String("testvm"),
			StorageConfigurationSettings: sqlvirtualmachine.StorageConfigurationSettingsResponse{
				DiskConfigurationType: pulumi.String("NEW"),
				SqlDataSettings: &sqlvirtualmachine.SQLStorageSettingsArgs{
					DefaultFilePath: pulumi.String("F:\\folderpath\\"),
					Luns: pulumi.IntArray{
						pulumi.Int(0),
					},
				},
				SqlLogSettings: &sqlvirtualmachine.SQLStorageSettingsArgs{
					DefaultFilePath: pulumi.String("G:\\folderpath\\"),
					Luns: pulumi.IntArray{
						pulumi.Int(1),
					},
				},
				SqlSystemDbOnDataDisk: pulumi.Bool(true),
				SqlTempDbSettings: &sqlvirtualmachine.SQLTempDbSettingsArgs{
					DataFileCount:   pulumi.Int(8),
					DataFileSize:    pulumi.Int(256),
					DataGrowth:      pulumi.Int(512),
					DefaultFilePath: pulumi.String("D:\\TEMP"),
					LogFileSize:     pulumi.Int(256),
					LogGrowth:       pulumi.Int(512),
				},
				StorageWorkloadType: pulumi.String("OLTP"),
			},
			VirtualMachineResourceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm"),
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
import com.pulumi.azurenative.sqlvirtualmachine.SqlVirtualMachine;
import com.pulumi.azurenative.sqlvirtualmachine.SqlVirtualMachineArgs;
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
        var sqlVirtualMachine = new SqlVirtualMachine("sqlVirtualMachine", SqlVirtualMachineArgs.builder()        
            .location("northeurope")
            .resourceGroupName("testrg")
            .sqlVirtualMachineName("testvm")
            .storageConfigurationSettings(Map.ofEntries(
                Map.entry("diskConfigurationType", "NEW"),
                Map.entry("sqlDataSettings", Map.ofEntries(
                    Map.entry("defaultFilePath", "F:\\folderpath\\"),
                    Map.entry("luns", 0)
                )),
                Map.entry("sqlLogSettings", Map.ofEntries(
                    Map.entry("defaultFilePath", "G:\\folderpath\\"),
                    Map.entry("luns", 1)
                )),
                Map.entry("sqlSystemDbOnDataDisk", true),
                Map.entry("sqlTempDbSettings", Map.ofEntries(
                    Map.entry("dataFileCount", 8),
                    Map.entry("dataFileSize", 256),
                    Map.entry("dataGrowth", 512),
                    Map.entry("defaultFilePath", "D:\\TEMP"),
                    Map.entry("logFileSize", 256),
                    Map.entry("logGrowth", 512)
                )),
                Map.entry("storageWorkloadType", "OLTP")
            ))
            .virtualMachineResourceId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlVirtualMachine = new azure_native.sqlvirtualmachine.SqlVirtualMachine("sqlVirtualMachine", {
    location: "northeurope",
    resourceGroupName: "testrg",
    sqlVirtualMachineName: "testvm",
    storageConfigurationSettings: {
        diskConfigurationType: "NEW",
        sqlDataSettings: {
            defaultFilePath: "F:\\folderpath\\",
            luns: [0],
        },
        sqlLogSettings: {
            defaultFilePath: "G:\\folderpath\\",
            luns: [1],
        },
        sqlSystemDbOnDataDisk: true,
        sqlTempDbSettings: {
            dataFileCount: 8,
            dataFileSize: 256,
            dataGrowth: 512,
            defaultFilePath: "D:\\TEMP",
            logFileSize: 256,
            logGrowth: 512,
        },
        storageWorkloadType: "OLTP",
    },
    virtualMachineResourceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_virtual_machine = azure_native.sqlvirtualmachine.SqlVirtualMachine("sqlVirtualMachine",
    location="northeurope",
    resource_group_name="testrg",
    sql_virtual_machine_name="testvm",
    storage_configuration_settings=azure_native.sqlvirtualmachine.StorageConfigurationSettingsResponseArgs(
        disk_configuration_type="NEW",
        sql_data_settings=azure_native.sqlvirtualmachine.SQLStorageSettingsArgs(
            default_file_path="F:\\folderpath\\",
            luns=[0],
        ),
        sql_log_settings=azure_native.sqlvirtualmachine.SQLStorageSettingsArgs(
            default_file_path="G:\\folderpath\\",
            luns=[1],
        ),
        sql_system_db_on_data_disk=True,
        sql_temp_db_settings=azure_native.sqlvirtualmachine.SQLTempDbSettingsArgs(
            data_file_count=8,
            data_file_size=256,
            data_growth=512,
            default_file_path="D:\\TEMP",
            log_file_size=256,
            log_growth=512,
        ),
        storage_workload_type="OLTP",
    ),
    virtual_machine_resource_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm")

```

```yaml
resources:
  sqlVirtualMachine:
    type: azure-native:sqlvirtualmachine:SqlVirtualMachine
    properties:
      location: northeurope
      resourceGroupName: testrg
      sqlVirtualMachineName: testvm
      storageConfigurationSettings:
        diskConfigurationType: NEW
        sqlDataSettings:
          defaultFilePath: F:\folderpath\
          luns:
            - 0
        sqlLogSettings:
          defaultFilePath: G:\folderpath\
          luns:
            - 1
        sqlSystemDbOnDataDisk: true
        sqlTempDbSettings:
          dataFileCount: 8
          dataFileSize: 256
          dataGrowth: 512
          defaultFilePath: D:\TEMP
          logFileSize: 256
          logGrowth: 512
        storageWorkloadType: OLTP
      virtualMachineResourceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm

```

{{% /example %}}
{{% example %}}
### Creates or updates a SQL virtual machine with max parameters.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlVirtualMachine = new AzureNative.SqlVirtualMachine.SqlVirtualMachine("sqlVirtualMachine", new()
    {
        AssessmentSettings = new AzureNative.SqlVirtualMachine.Inputs.AssessmentSettingsArgs
        {
            Enable = true,
            RunImmediately = true,
            Schedule = new AzureNative.SqlVirtualMachine.Inputs.ScheduleArgs
            {
                DayOfWeek = AzureNative.SqlVirtualMachine.AssessmentDayOfWeek.Sunday,
                Enable = true,
                StartTime = "23:17",
                WeeklyInterval = 1,
            },
        },
        AutoBackupSettings = new AzureNative.SqlVirtualMachine.Inputs.AutoBackupSettingsArgs
        {
            BackupScheduleType = "Manual",
            BackupSystemDbs = true,
            Enable = true,
            EnableEncryption = true,
            FullBackupFrequency = "Daily",
            FullBackupStartTime = 6,
            FullBackupWindowHours = 11,
            LogBackupFrequency = 10,
            Password = "<Password>",
            RetentionPeriod = 17,
            StorageAccessKey = "<primary storage access key>",
            StorageAccountUrl = "https://teststorage.blob.core.windows.net/",
            StorageContainerName = "testcontainer",
        },
        AutoPatchingSettings = new AzureNative.SqlVirtualMachine.Inputs.AutoPatchingSettingsArgs
        {
            DayOfWeek = AzureNative.SqlVirtualMachine.DayOfWeek.Sunday,
            Enable = true,
            MaintenanceWindowDuration = 60,
            MaintenanceWindowStartingHour = 2,
        },
        KeyVaultCredentialSettings = new AzureNative.SqlVirtualMachine.Inputs.KeyVaultCredentialSettingsArgs
        {
            Enable = false,
        },
        Location = "northeurope",
        ResourceGroupName = "testrg",
        ServerConfigurationsManagementSettings = new AzureNative.SqlVirtualMachine.Inputs.ServerConfigurationsManagementSettingsArgs
        {
            AdditionalFeaturesServerConfigurations = new AzureNative.SqlVirtualMachine.Inputs.AdditionalFeaturesServerConfigurationsArgs
            {
                IsRServicesEnabled = false,
            },
            SqlConnectivityUpdateSettings = new AzureNative.SqlVirtualMachine.Inputs.SqlConnectivityUpdateSettingsArgs
            {
                ConnectivityType = "PRIVATE",
                Port = 1433,
                SqlAuthUpdatePassword = "<password>",
                SqlAuthUpdateUserName = "sqllogin",
            },
            SqlInstanceSettings = new AzureNative.SqlVirtualMachine.Inputs.SQLInstanceSettingsArgs
            {
                Collation = "SQL_Latin1_General_CP1_CI_AS",
                IsIfiEnabled = true,
                IsLpimEnabled = true,
                IsOptimizeForAdHocWorkloadsEnabled = true,
                MaxDop = 8,
                MaxServerMemoryMB = 128,
                MinServerMemoryMB = 0,
            },
            SqlStorageUpdateSettings = new AzureNative.SqlVirtualMachine.Inputs.SqlStorageUpdateSettingsArgs
            {
                DiskConfigurationType = "NEW",
                DiskCount = 1,
                StartingDeviceId = 2,
            },
            SqlWorkloadTypeUpdateSettings = new AzureNative.SqlVirtualMachine.Inputs.SqlWorkloadTypeUpdateSettingsArgs
            {
                SqlWorkloadType = "OLTP",
            },
        },
        SqlImageSku = "Enterprise",
        SqlManagement = "Full",
        SqlServerLicenseType = "PAYG",
        SqlVirtualMachineName = "testvm",
        VirtualMachineResourceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm",
    });

});


```

```go
package main

import (
	sqlvirtualmachine "github.com/pulumi/pulumi-azure-native-sdk/sqlvirtualmachine"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sqlvirtualmachine.NewSqlVirtualMachine(ctx, "sqlVirtualMachine", &sqlvirtualmachine.SqlVirtualMachineArgs{
			AssessmentSettings: sqlvirtualmachine.AssessmentSettingsResponse{
				Enable:         pulumi.Bool(true),
				RunImmediately: pulumi.Bool(true),
				Schedule: &sqlvirtualmachine.ScheduleArgs{
					DayOfWeek:      sqlvirtualmachine.AssessmentDayOfWeekSunday,
					Enable:         pulumi.Bool(true),
					StartTime:      pulumi.String("23:17"),
					WeeklyInterval: pulumi.Int(1),
				},
			},
			AutoBackupSettings: &sqlvirtualmachine.AutoBackupSettingsArgs{
				BackupScheduleType:    pulumi.String("Manual"),
				BackupSystemDbs:       pulumi.Bool(true),
				Enable:                pulumi.Bool(true),
				EnableEncryption:      pulumi.Bool(true),
				FullBackupFrequency:   pulumi.String("Daily"),
				FullBackupStartTime:   pulumi.Int(6),
				FullBackupWindowHours: pulumi.Int(11),
				LogBackupFrequency:    pulumi.Int(10),
				Password:              pulumi.String("<Password>"),
				RetentionPeriod:       pulumi.Int(17),
				StorageAccessKey:      pulumi.String("<primary storage access key>"),
				StorageAccountUrl:     pulumi.String("https://teststorage.blob.core.windows.net/"),
				StorageContainerName:  pulumi.String("testcontainer"),
			},
			AutoPatchingSettings: &sqlvirtualmachine.AutoPatchingSettingsArgs{
				DayOfWeek:                     sqlvirtualmachine.DayOfWeekSunday,
				Enable:                        pulumi.Bool(true),
				MaintenanceWindowDuration:     pulumi.Int(60),
				MaintenanceWindowStartingHour: pulumi.Int(2),
			},
			KeyVaultCredentialSettings: &sqlvirtualmachine.KeyVaultCredentialSettingsArgs{
				Enable: pulumi.Bool(false),
			},
			Location:          pulumi.String("northeurope"),
			ResourceGroupName: pulumi.String("testrg"),
			ServerConfigurationsManagementSettings: sqlvirtualmachine.ServerConfigurationsManagementSettingsResponse{
				AdditionalFeaturesServerConfigurations: &sqlvirtualmachine.AdditionalFeaturesServerConfigurationsArgs{
					IsRServicesEnabled: pulumi.Bool(false),
				},
				SqlConnectivityUpdateSettings: &sqlvirtualmachine.SqlConnectivityUpdateSettingsArgs{
					ConnectivityType:      pulumi.String("PRIVATE"),
					Port:                  pulumi.Int(1433),
					SqlAuthUpdatePassword: pulumi.String("<password>"),
					SqlAuthUpdateUserName: pulumi.String("sqllogin"),
				},
				SqlInstanceSettings: &sqlvirtualmachine.SQLInstanceSettingsArgs{
					Collation:                          pulumi.String("SQL_Latin1_General_CP1_CI_AS"),
					IsIfiEnabled:                       pulumi.Bool(true),
					IsLpimEnabled:                      pulumi.Bool(true),
					IsOptimizeForAdHocWorkloadsEnabled: pulumi.Bool(true),
					MaxDop:                             pulumi.Int(8),
					MaxServerMemoryMB:                  pulumi.Int(128),
					MinServerMemoryMB:                  pulumi.Int(0),
				},
				SqlStorageUpdateSettings: &sqlvirtualmachine.SqlStorageUpdateSettingsArgs{
					DiskConfigurationType: pulumi.String("NEW"),
					DiskCount:             pulumi.Int(1),
					StartingDeviceId:      pulumi.Int(2),
				},
				SqlWorkloadTypeUpdateSettings: &sqlvirtualmachine.SqlWorkloadTypeUpdateSettingsArgs{
					SqlWorkloadType: pulumi.String("OLTP"),
				},
			},
			SqlImageSku:              pulumi.String("Enterprise"),
			SqlManagement:            pulumi.String("Full"),
			SqlServerLicenseType:     pulumi.String("PAYG"),
			SqlVirtualMachineName:    pulumi.String("testvm"),
			VirtualMachineResourceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm"),
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
import com.pulumi.azurenative.sqlvirtualmachine.SqlVirtualMachine;
import com.pulumi.azurenative.sqlvirtualmachine.SqlVirtualMachineArgs;
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
        var sqlVirtualMachine = new SqlVirtualMachine("sqlVirtualMachine", SqlVirtualMachineArgs.builder()        
            .assessmentSettings(Map.ofEntries(
                Map.entry("enable", true),
                Map.entry("runImmediately", true),
                Map.entry("schedule", Map.ofEntries(
                    Map.entry("dayOfWeek", "Sunday"),
                    Map.entry("enable", true),
                    Map.entry("startTime", "23:17"),
                    Map.entry("weeklyInterval", 1)
                ))
            ))
            .autoBackupSettings(Map.ofEntries(
                Map.entry("backupScheduleType", "Manual"),
                Map.entry("backupSystemDbs", true),
                Map.entry("enable", true),
                Map.entry("enableEncryption", true),
                Map.entry("fullBackupFrequency", "Daily"),
                Map.entry("fullBackupStartTime", 6),
                Map.entry("fullBackupWindowHours", 11),
                Map.entry("logBackupFrequency", 10),
                Map.entry("password", "<Password>"),
                Map.entry("retentionPeriod", 17),
                Map.entry("storageAccessKey", "<primary storage access key>"),
                Map.entry("storageAccountUrl", "https://teststorage.blob.core.windows.net/"),
                Map.entry("storageContainerName", "testcontainer")
            ))
            .autoPatchingSettings(Map.ofEntries(
                Map.entry("dayOfWeek", "Sunday"),
                Map.entry("enable", true),
                Map.entry("maintenanceWindowDuration", 60),
                Map.entry("maintenanceWindowStartingHour", 2)
            ))
            .keyVaultCredentialSettings(Map.of("enable", false))
            .location("northeurope")
            .resourceGroupName("testrg")
            .serverConfigurationsManagementSettings(Map.ofEntries(
                Map.entry("additionalFeaturesServerConfigurations", Map.of("isRServicesEnabled", false)),
                Map.entry("sqlConnectivityUpdateSettings", Map.ofEntries(
                    Map.entry("connectivityType", "PRIVATE"),
                    Map.entry("port", 1433),
                    Map.entry("sqlAuthUpdatePassword", "<password>"),
                    Map.entry("sqlAuthUpdateUserName", "sqllogin")
                )),
                Map.entry("sqlInstanceSettings", Map.ofEntries(
                    Map.entry("collation", "SQL_Latin1_General_CP1_CI_AS"),
                    Map.entry("isIfiEnabled", true),
                    Map.entry("isLpimEnabled", true),
                    Map.entry("isOptimizeForAdHocWorkloadsEnabled", true),
                    Map.entry("maxDop", 8),
                    Map.entry("maxServerMemoryMB", 128),
                    Map.entry("minServerMemoryMB", 0)
                )),
                Map.entry("sqlStorageUpdateSettings", Map.ofEntries(
                    Map.entry("diskConfigurationType", "NEW"),
                    Map.entry("diskCount", 1),
                    Map.entry("startingDeviceId", 2)
                )),
                Map.entry("sqlWorkloadTypeUpdateSettings", Map.of("sqlWorkloadType", "OLTP"))
            ))
            .sqlImageSku("Enterprise")
            .sqlManagement("Full")
            .sqlServerLicenseType("PAYG")
            .sqlVirtualMachineName("testvm")
            .virtualMachineResourceId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlVirtualMachine = new azure_native.sqlvirtualmachine.SqlVirtualMachine("sqlVirtualMachine", {
    assessmentSettings: {
        enable: true,
        runImmediately: true,
        schedule: {
            dayOfWeek: azure_native.sqlvirtualmachine.AssessmentDayOfWeek.Sunday,
            enable: true,
            startTime: "23:17",
            weeklyInterval: 1,
        },
    },
    autoBackupSettings: {
        backupScheduleType: "Manual",
        backupSystemDbs: true,
        enable: true,
        enableEncryption: true,
        fullBackupFrequency: "Daily",
        fullBackupStartTime: 6,
        fullBackupWindowHours: 11,
        logBackupFrequency: 10,
        password: "<Password>",
        retentionPeriod: 17,
        storageAccessKey: "<primary storage access key>",
        storageAccountUrl: "https://teststorage.blob.core.windows.net/",
        storageContainerName: "testcontainer",
    },
    autoPatchingSettings: {
        dayOfWeek: azure_native.sqlvirtualmachine.DayOfWeek.Sunday,
        enable: true,
        maintenanceWindowDuration: 60,
        maintenanceWindowStartingHour: 2,
    },
    keyVaultCredentialSettings: {
        enable: false,
    },
    location: "northeurope",
    resourceGroupName: "testrg",
    serverConfigurationsManagementSettings: {
        additionalFeaturesServerConfigurations: {
            isRServicesEnabled: false,
        },
        sqlConnectivityUpdateSettings: {
            connectivityType: "PRIVATE",
            port: 1433,
            sqlAuthUpdatePassword: "<password>",
            sqlAuthUpdateUserName: "sqllogin",
        },
        sqlInstanceSettings: {
            collation: "SQL_Latin1_General_CP1_CI_AS",
            isIfiEnabled: true,
            isLpimEnabled: true,
            isOptimizeForAdHocWorkloadsEnabled: true,
            maxDop: 8,
            maxServerMemoryMB: 128,
            minServerMemoryMB: 0,
        },
        sqlStorageUpdateSettings: {
            diskConfigurationType: "NEW",
            diskCount: 1,
            startingDeviceId: 2,
        },
        sqlWorkloadTypeUpdateSettings: {
            sqlWorkloadType: "OLTP",
        },
    },
    sqlImageSku: "Enterprise",
    sqlManagement: "Full",
    sqlServerLicenseType: "PAYG",
    sqlVirtualMachineName: "testvm",
    virtualMachineResourceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_virtual_machine = azure_native.sqlvirtualmachine.SqlVirtualMachine("sqlVirtualMachine",
    assessment_settings=azure_native.sqlvirtualmachine.AssessmentSettingsResponseArgs(
        enable=True,
        run_immediately=True,
        schedule=azure_native.sqlvirtualmachine.ScheduleArgs(
            day_of_week=azure_native.sqlvirtualmachine.AssessmentDayOfWeek.SUNDAY,
            enable=True,
            start_time="23:17",
            weekly_interval=1,
        ),
    ),
    auto_backup_settings=azure_native.sqlvirtualmachine.AutoBackupSettingsArgs(
        backup_schedule_type="Manual",
        backup_system_dbs=True,
        enable=True,
        enable_encryption=True,
        full_backup_frequency="Daily",
        full_backup_start_time=6,
        full_backup_window_hours=11,
        log_backup_frequency=10,
        password="<Password>",
        retention_period=17,
        storage_access_key="<primary storage access key>",
        storage_account_url="https://teststorage.blob.core.windows.net/",
        storage_container_name="testcontainer",
    ),
    auto_patching_settings=azure_native.sqlvirtualmachine.AutoPatchingSettingsArgs(
        day_of_week=azure_native.sqlvirtualmachine.DayOfWeek.SUNDAY,
        enable=True,
        maintenance_window_duration=60,
        maintenance_window_starting_hour=2,
    ),
    key_vault_credential_settings=azure_native.sqlvirtualmachine.KeyVaultCredentialSettingsArgs(
        enable=False,
    ),
    location="northeurope",
    resource_group_name="testrg",
    server_configurations_management_settings=azure_native.sqlvirtualmachine.ServerConfigurationsManagementSettingsResponseArgs(
        additional_features_server_configurations=azure_native.sqlvirtualmachine.AdditionalFeaturesServerConfigurationsArgs(
            is_r_services_enabled=False,
        ),
        sql_connectivity_update_settings=azure_native.sqlvirtualmachine.SqlConnectivityUpdateSettingsArgs(
            connectivity_type="PRIVATE",
            port=1433,
            sql_auth_update_password="<password>",
            sql_auth_update_user_name="sqllogin",
        ),
        sql_instance_settings=azure_native.sqlvirtualmachine.SQLInstanceSettingsArgs(
            collation="SQL_Latin1_General_CP1_CI_AS",
            is_ifi_enabled=True,
            is_lpim_enabled=True,
            is_optimize_for_ad_hoc_workloads_enabled=True,
            max_dop=8,
            max_server_memory_mb=128,
            min_server_memory_mb=0,
        ),
        sql_storage_update_settings=azure_native.sqlvirtualmachine.SqlStorageUpdateSettingsArgs(
            disk_configuration_type="NEW",
            disk_count=1,
            starting_device_id=2,
        ),
        sql_workload_type_update_settings=azure_native.sqlvirtualmachine.SqlWorkloadTypeUpdateSettingsArgs(
            sql_workload_type="OLTP",
        ),
    ),
    sql_image_sku="Enterprise",
    sql_management="Full",
    sql_server_license_type="PAYG",
    sql_virtual_machine_name="testvm",
    virtual_machine_resource_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm")

```

```yaml
resources:
  sqlVirtualMachine:
    type: azure-native:sqlvirtualmachine:SqlVirtualMachine
    properties:
      assessmentSettings:
        enable: true
        runImmediately: true
        schedule:
          dayOfWeek: Sunday
          enable: true
          startTime: 23:17
          weeklyInterval: 1
      autoBackupSettings:
        backupScheduleType: Manual
        backupSystemDbs: true
        enable: true
        enableEncryption: true
        fullBackupFrequency: Daily
        fullBackupStartTime: 6
        fullBackupWindowHours: 11
        logBackupFrequency: 10
        password: <Password>
        retentionPeriod: 17
        storageAccessKey: <primary storage access key>
        storageAccountUrl: https://teststorage.blob.core.windows.net/
        storageContainerName: testcontainer
      autoPatchingSettings:
        dayOfWeek: Sunday
        enable: true
        maintenanceWindowDuration: 60
        maintenanceWindowStartingHour: 2
      keyVaultCredentialSettings:
        enable: false
      location: northeurope
      resourceGroupName: testrg
      serverConfigurationsManagementSettings:
        additionalFeaturesServerConfigurations:
          isRServicesEnabled: false
        sqlConnectivityUpdateSettings:
          connectivityType: PRIVATE
          port: 1433
          sqlAuthUpdatePassword: <password>
          sqlAuthUpdateUserName: sqllogin
        sqlInstanceSettings:
          collation: SQL_Latin1_General_CP1_CI_AS
          isIfiEnabled: true
          isLpimEnabled: true
          isOptimizeForAdHocWorkloadsEnabled: true
          maxDop: 8
          maxServerMemoryMB: 128
          minServerMemoryMB: 0
        sqlStorageUpdateSettings:
          diskConfigurationType: NEW
          diskCount: 1
          startingDeviceId: 2
        sqlWorkloadTypeUpdateSettings:
          sqlWorkloadType: OLTP
      sqlImageSku: Enterprise
      sqlManagement: Full
      sqlServerLicenseType: PAYG
      sqlVirtualMachineName: testvm
      virtualMachineResourceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm

```

{{% /example %}}
{{% example %}}
### Creates or updates a SQL virtual machine with min parameters.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlVirtualMachine = new AzureNative.SqlVirtualMachine.SqlVirtualMachine("sqlVirtualMachine", new()
    {
        Location = "northeurope",
        ResourceGroupName = "testrg",
        SqlVirtualMachineName = "testvm",
        VirtualMachineResourceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm",
    });

});


```

```go
package main

import (
	sqlvirtualmachine "github.com/pulumi/pulumi-azure-native-sdk/sqlvirtualmachine"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sqlvirtualmachine.NewSqlVirtualMachine(ctx, "sqlVirtualMachine", &sqlvirtualmachine.SqlVirtualMachineArgs{
			Location:                 pulumi.String("northeurope"),
			ResourceGroupName:        pulumi.String("testrg"),
			SqlVirtualMachineName:    pulumi.String("testvm"),
			VirtualMachineResourceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm"),
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
import com.pulumi.azurenative.sqlvirtualmachine.SqlVirtualMachine;
import com.pulumi.azurenative.sqlvirtualmachine.SqlVirtualMachineArgs;
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
        var sqlVirtualMachine = new SqlVirtualMachine("sqlVirtualMachine", SqlVirtualMachineArgs.builder()        
            .location("northeurope")
            .resourceGroupName("testrg")
            .sqlVirtualMachineName("testvm")
            .virtualMachineResourceId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlVirtualMachine = new azure_native.sqlvirtualmachine.SqlVirtualMachine("sqlVirtualMachine", {
    location: "northeurope",
    resourceGroupName: "testrg",
    sqlVirtualMachineName: "testvm",
    virtualMachineResourceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_virtual_machine = azure_native.sqlvirtualmachine.SqlVirtualMachine("sqlVirtualMachine",
    location="northeurope",
    resource_group_name="testrg",
    sql_virtual_machine_name="testvm",
    virtual_machine_resource_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm")

```

```yaml
resources:
  sqlVirtualMachine:
    type: azure-native:sqlvirtualmachine:SqlVirtualMachine
    properties:
      location: northeurope
      resourceGroupName: testrg
      sqlVirtualMachineName: testvm
      virtualMachineResourceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Compute/virtualMachines/testvm

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sqlvirtualmachine:SqlVirtualMachine testvm /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm 
```
