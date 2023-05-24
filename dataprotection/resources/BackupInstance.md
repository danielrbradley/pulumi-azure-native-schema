BackupInstance Resource
API Version: 2023-01-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create BackupInstance
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var backupInstance = new AzureNative.DataProtection.BackupInstance("backupInstance", new()
    {
        BackupInstanceName = "testInstance1",
        Properties = new AzureNative.DataProtection.Inputs.BackupInstanceArgs
        {
            DataSourceInfo = new AzureNative.DataProtection.Inputs.DatasourceArgs
            {
                DatasourceType = "Microsoft.DBforPostgreSQL/servers/databases",
                ObjectType = "Datasource",
                ResourceID = "/subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest/providers/Microsoft.DBforPostgreSQL/servers/viveksipgtest/databases/testdb",
                ResourceLocation = "",
                ResourceName = "testdb",
                ResourceType = "Microsoft.DBforPostgreSQL/servers/databases",
                ResourceUri = "",
            },
            DataSourceSetInfo = new AzureNative.DataProtection.Inputs.DatasourceSetArgs
            {
                DatasourceType = "Microsoft.DBforPostgreSQL/servers/databases",
                ObjectType = "DatasourceSet",
                ResourceID = "/subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest/providers/Microsoft.DBforPostgreSQL/servers/viveksipgtest",
                ResourceLocation = "",
                ResourceName = "viveksipgtest",
                ResourceType = "Microsoft.DBforPostgreSQL/servers",
                ResourceUri = "",
            },
            DatasourceAuthCredentials = 
            {
                { "objectType", "SecretStoreBasedAuthCredentials" },
                { "secretStoreResource", new AzureNative.DataProtection.Inputs.SecretStoreResourceArgs
                {
                    SecretStoreType = "AzureKeyVault",
                    Uri = "https://samplevault.vault.azure.net/secrets/credentials",
                } },
            },
            FriendlyName = "harshitbi2",
            ObjectType = "BackupInstance",
            PolicyInfo = new AzureNative.DataProtection.Inputs.PolicyInfoArgs
            {
                PolicyId = "/subscriptions/04cf684a-d41f-4550-9f70-7708a3a2283b/resourceGroups/000pikumar/providers/Microsoft.DataProtection/Backupvaults/PratikPrivatePreviewVault1/backupPolicies/PratikPolicy1",
                PolicyParameters = new AzureNative.DataProtection.Inputs.PolicyParametersArgs
                {
                    DataStoreParametersList = new[]
                    {
                        
                        {
                            { "dataStoreType", "OperationalStore" },
                            { "objectType", "AzureOperationalStoreParameters" },
                            { "resourceGroupId", "/subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest" },
                        },
                    },
                },
            },
            ValidationType = "ShallowValidation",
        },
        ResourceGroupName = "000pikumar",
        Tags = 
        {
            { "key1", "val1" },
        },
        VaultName = "PratikPrivatePreviewVault1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.dataprotection.BackupInstance;
import com.pulumi.azurenative.dataprotection.BackupInstanceArgs;
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
        var backupInstance = new BackupInstance("backupInstance", BackupInstanceArgs.builder()        
            .backupInstanceName("testInstance1")
            .properties(Map.ofEntries(
                Map.entry("dataSourceInfo", Map.ofEntries(
                    Map.entry("datasourceType", "Microsoft.DBforPostgreSQL/servers/databases"),
                    Map.entry("objectType", "Datasource"),
                    Map.entry("resourceID", "/subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest/providers/Microsoft.DBforPostgreSQL/servers/viveksipgtest/databases/testdb"),
                    Map.entry("resourceLocation", ""),
                    Map.entry("resourceName", "testdb"),
                    Map.entry("resourceType", "Microsoft.DBforPostgreSQL/servers/databases"),
                    Map.entry("resourceUri", "")
                )),
                Map.entry("dataSourceSetInfo", Map.ofEntries(
                    Map.entry("datasourceType", "Microsoft.DBforPostgreSQL/servers/databases"),
                    Map.entry("objectType", "DatasourceSet"),
                    Map.entry("resourceID", "/subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest/providers/Microsoft.DBforPostgreSQL/servers/viveksipgtest"),
                    Map.entry("resourceLocation", ""),
                    Map.entry("resourceName", "viveksipgtest"),
                    Map.entry("resourceType", "Microsoft.DBforPostgreSQL/servers"),
                    Map.entry("resourceUri", "")
                )),
                Map.entry("datasourceAuthCredentials", Map.ofEntries(
                    Map.entry("objectType", "SecretStoreBasedAuthCredentials"),
                    Map.entry("secretStoreResource", Map.ofEntries(
                        Map.entry("secretStoreType", "AzureKeyVault"),
                        Map.entry("uri", "https://samplevault.vault.azure.net/secrets/credentials")
                    ))
                )),
                Map.entry("friendlyName", "harshitbi2"),
                Map.entry("objectType", "BackupInstance"),
                Map.entry("policyInfo", Map.ofEntries(
                    Map.entry("policyId", "/subscriptions/04cf684a-d41f-4550-9f70-7708a3a2283b/resourceGroups/000pikumar/providers/Microsoft.DataProtection/Backupvaults/PratikPrivatePreviewVault1/backupPolicies/PratikPolicy1"),
                    Map.entry("policyParameters", Map.of("dataStoreParametersList", Map.ofEntries(
                        Map.entry("dataStoreType", "OperationalStore"),
                        Map.entry("objectType", "AzureOperationalStoreParameters"),
                        Map.entry("resourceGroupId", "/subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest")
                    )))
                )),
                Map.entry("validationType", "ShallowValidation")
            ))
            .resourceGroupName("000pikumar")
            .tags(Map.of("key1", "val1"))
            .vaultName("PratikPrivatePreviewVault1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const backupInstance = new azure_native.dataprotection.BackupInstance("backupInstance", {
    backupInstanceName: "testInstance1",
    properties: {
        dataSourceInfo: {
            datasourceType: "Microsoft.DBforPostgreSQL/servers/databases",
            objectType: "Datasource",
            resourceID: "/subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest/providers/Microsoft.DBforPostgreSQL/servers/viveksipgtest/databases/testdb",
            resourceLocation: "",
            resourceName: "testdb",
            resourceType: "Microsoft.DBforPostgreSQL/servers/databases",
            resourceUri: "",
        },
        dataSourceSetInfo: {
            datasourceType: "Microsoft.DBforPostgreSQL/servers/databases",
            objectType: "DatasourceSet",
            resourceID: "/subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest/providers/Microsoft.DBforPostgreSQL/servers/viveksipgtest",
            resourceLocation: "",
            resourceName: "viveksipgtest",
            resourceType: "Microsoft.DBforPostgreSQL/servers",
            resourceUri: "",
        },
        datasourceAuthCredentials: {
            objectType: "SecretStoreBasedAuthCredentials",
            secretStoreResource: {
                secretStoreType: "AzureKeyVault",
                uri: "https://samplevault.vault.azure.net/secrets/credentials",
            },
        },
        friendlyName: "harshitbi2",
        objectType: "BackupInstance",
        policyInfo: {
            policyId: "/subscriptions/04cf684a-d41f-4550-9f70-7708a3a2283b/resourceGroups/000pikumar/providers/Microsoft.DataProtection/Backupvaults/PratikPrivatePreviewVault1/backupPolicies/PratikPolicy1",
            policyParameters: {
                dataStoreParametersList: [{
                    dataStoreType: "OperationalStore",
                    objectType: "AzureOperationalStoreParameters",
                    resourceGroupId: "/subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest",
                }],
            },
        },
        validationType: "ShallowValidation",
    },
    resourceGroupName: "000pikumar",
    tags: {
        key1: "val1",
    },
    vaultName: "PratikPrivatePreviewVault1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

backup_instance = azure_native.dataprotection.BackupInstance("backupInstance",
    backup_instance_name="testInstance1",
    properties=azure_native.dataprotection.BackupInstanceResponseArgs(
        data_source_info=azure_native.dataprotection.DatasourceArgs(
            datasource_type="Microsoft.DBforPostgreSQL/servers/databases",
            object_type="Datasource",
            resource_id="/subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest/providers/Microsoft.DBforPostgreSQL/servers/viveksipgtest/databases/testdb",
            resource_location="",
            resource_name="testdb",
            resource_type="Microsoft.DBforPostgreSQL/servers/databases",
            resource_uri="",
        ),
        data_source_set_info=azure_native.dataprotection.DatasourceSetArgs(
            datasource_type="Microsoft.DBforPostgreSQL/servers/databases",
            object_type="DatasourceSet",
            resource_id="/subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest/providers/Microsoft.DBforPostgreSQL/servers/viveksipgtest",
            resource_location="",
            resource_name="viveksipgtest",
            resource_type="Microsoft.DBforPostgreSQL/servers",
            resource_uri="",
        ),
        datasource_auth_credentials=azure_native.dataprotection.SecretStoreBasedAuthCredentialsResponseArgs(
            object_type="SecretStoreBasedAuthCredentials",
            secret_store_resource=azure_native.dataprotection.SecretStoreResourceArgs(
                secret_store_type="AzureKeyVault",
                uri="https://samplevault.vault.azure.net/secrets/credentials",
            ),
        ),
        friendly_name="harshitbi2",
        object_type="BackupInstance",
        policy_info={
            "policyId": "/subscriptions/04cf684a-d41f-4550-9f70-7708a3a2283b/resourceGroups/000pikumar/providers/Microsoft.DataProtection/Backupvaults/PratikPrivatePreviewVault1/backupPolicies/PratikPolicy1",
            "policyParameters": {
                "dataStoreParametersList": [azure_native.dataprotection.AzureOperationalStoreParametersResponseArgs(
                    data_store_type="OperationalStore",
                    object_type="AzureOperationalStoreParameters",
                    resource_group_id="/subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest",
                )],
            },
        },
        validation_type="ShallowValidation",
    ),
    resource_group_name="000pikumar",
    tags={
        "key1": "val1",
    },
    vault_name="PratikPrivatePreviewVault1")

```

```yaml
resources:
  backupInstance:
    type: azure-native:dataprotection:BackupInstance
    properties:
      backupInstanceName: testInstance1
      properties:
        dataSourceInfo:
          datasourceType: Microsoft.DBforPostgreSQL/servers/databases
          objectType: Datasource
          resourceID: /subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest/providers/Microsoft.DBforPostgreSQL/servers/viveksipgtest/databases/testdb
          resourceLocation:
          resourceName: testdb
          resourceType: Microsoft.DBforPostgreSQL/servers/databases
          resourceUri:
        dataSourceSetInfo:
          datasourceType: Microsoft.DBforPostgreSQL/servers/databases
          objectType: DatasourceSet
          resourceID: /subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest/providers/Microsoft.DBforPostgreSQL/servers/viveksipgtest
          resourceLocation:
          resourceName: viveksipgtest
          resourceType: Microsoft.DBforPostgreSQL/servers
          resourceUri:
        datasourceAuthCredentials:
          objectType: SecretStoreBasedAuthCredentials
          secretStoreResource:
            secretStoreType: AzureKeyVault
            uri: https://samplevault.vault.azure.net/secrets/credentials
        friendlyName: harshitbi2
        objectType: BackupInstance
        policyInfo:
          policyId: /subscriptions/04cf684a-d41f-4550-9f70-7708a3a2283b/resourceGroups/000pikumar/providers/Microsoft.DataProtection/Backupvaults/PratikPrivatePreviewVault1/backupPolicies/PratikPolicy1
          policyParameters:
            dataStoreParametersList:
              - dataStoreType: OperationalStore
                objectType: AzureOperationalStoreParameters
                resourceGroupId: /subscriptions/f75d8d8b-6735-4697-82e1-1a7a3ff0d5d4/resourceGroups/viveksipgtest
        validationType: ShallowValidation
      resourceGroupName: 000pikumar
      tags:
        key1: val1
      vaultName: PratikPrivatePreviewVault1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dataprotection:BackupInstance harshitbi2 /subscriptions/04cf684a-d41f-4550-9f70-7708a3a2283b/resourceGroups/000pikumar/providers/Microsoft.DataProtection/backupVaults/PratikPrivatePreviewVault1/backupInstances/harshitbi2 
```
