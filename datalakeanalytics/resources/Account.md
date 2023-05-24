A Data Lake Analytics account object, containing all information associated with the named Data Lake Analytics account.
API Version: 2019-11-01-preview.
Previous API Version: 2016-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates the specified Data Lake Analytics account. This supplies the user with computation services for Data Lake Analytics workloads.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.DataLakeAnalytics.Account("account", new()
    {
        AccountName = "contosoadla",
        ComputePolicies = new[]
        {
            new AzureNative.DataLakeAnalytics.Inputs.CreateComputePolicyWithAccountParametersArgs
            {
                MaxDegreeOfParallelismPerJob = 1,
                MinPriorityPerJob = 1,
                Name = "test_policy",
                ObjectId = "34adfa4f-cedf-4dc0-ba29-b6d1a69ab345",
                ObjectType = "User",
            },
        },
        DataLakeStoreAccounts = new[]
        {
            new AzureNative.DataLakeAnalytics.Inputs.AddDataLakeStoreWithAccountParametersArgs
            {
                Name = "test_adls",
                Suffix = "test_suffix",
            },
        },
        DefaultDataLakeStoreAccount = "test_adls",
        FirewallAllowAzureIps = AzureNative.DataLakeAnalytics.FirewallAllowAzureIpsState.Enabled,
        FirewallRules = new[]
        {
            new AzureNative.DataLakeAnalytics.Inputs.CreateFirewallRuleWithAccountParametersArgs
            {
                EndIpAddress = "2.2.2.2",
                Name = "test_rule",
                StartIpAddress = "1.1.1.1",
            },
        },
        FirewallState = AzureNative.DataLakeAnalytics.FirewallState.Enabled,
        Location = "eastus2",
        MaxDegreeOfParallelism = 30,
        MaxDegreeOfParallelismPerJob = 1,
        MaxJobCount = 3,
        MinPriorityPerJob = 1,
        NewTier = AzureNative.DataLakeAnalytics.TierType.Consumption,
        QueryStoreRetention = 30,
        ResourceGroupName = "contosorg",
        StorageAccounts = new[]
        {
            new AzureNative.DataLakeAnalytics.Inputs.AddStorageAccountWithAccountParametersArgs
            {
                AccessKey = "34adfa4f-cedf-4dc0-ba29-b6d1a69ab346",
                Name = "test_storage",
                Suffix = "test_suffix",
            },
        },
        Tags = 
        {
            { "test_key", "test_value" },
        },
    });

});


```

```go
package main

import (
	datalakeanalytics "github.com/pulumi/pulumi-azure-native-sdk/datalakeanalytics"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datalakeanalytics.NewAccount(ctx, "account", &datalakeanalytics.AccountArgs{
			AccountName: pulumi.String("contosoadla"),
			ComputePolicies: []datalakeanalytics.CreateComputePolicyWithAccountParametersArgs{
				{
					MaxDegreeOfParallelismPerJob: pulumi.Int(1),
					MinPriorityPerJob:            pulumi.Int(1),
					Name:                         pulumi.String("test_policy"),
					ObjectId:                     pulumi.String("34adfa4f-cedf-4dc0-ba29-b6d1a69ab345"),
					ObjectType:                   pulumi.String("User"),
				},
			},
			DataLakeStoreAccounts: []datalakeanalytics.AddDataLakeStoreWithAccountParametersArgs{
				{
					Name:   pulumi.String("test_adls"),
					Suffix: pulumi.String("test_suffix"),
				},
			},
			DefaultDataLakeStoreAccount: pulumi.String("test_adls"),
			FirewallAllowAzureIps:       datalakeanalytics.FirewallAllowAzureIpsStateEnabled,
			FirewallRules: []datalakeanalytics.CreateFirewallRuleWithAccountParametersArgs{
				{
					EndIpAddress:   pulumi.String("2.2.2.2"),
					Name:           pulumi.String("test_rule"),
					StartIpAddress: pulumi.String("1.1.1.1"),
				},
			},
			FirewallState:                datalakeanalytics.FirewallStateEnabled,
			Location:                     pulumi.String("eastus2"),
			MaxDegreeOfParallelism:       pulumi.Int(30),
			MaxDegreeOfParallelismPerJob: pulumi.Int(1),
			MaxJobCount:                  pulumi.Int(3),
			MinPriorityPerJob:            pulumi.Int(1),
			NewTier:                      datalakeanalytics.TierTypeConsumption,
			QueryStoreRetention:          pulumi.Int(30),
			ResourceGroupName:            pulumi.String("contosorg"),
			StorageAccounts: []datalakeanalytics.AddStorageAccountWithAccountParametersArgs{
				{
					AccessKey: pulumi.String("34adfa4f-cedf-4dc0-ba29-b6d1a69ab346"),
					Name:      pulumi.String("test_storage"),
					Suffix:    pulumi.String("test_suffix"),
				},
			},
			Tags: pulumi.StringMap{
				"test_key": pulumi.String("test_value"),
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
import com.pulumi.azurenative.datalakeanalytics.Account;
import com.pulumi.azurenative.datalakeanalytics.AccountArgs;
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
            .computePolicies(Map.ofEntries(
                Map.entry("maxDegreeOfParallelismPerJob", 1),
                Map.entry("minPriorityPerJob", 1),
                Map.entry("name", "test_policy"),
                Map.entry("objectId", "34adfa4f-cedf-4dc0-ba29-b6d1a69ab345"),
                Map.entry("objectType", "User")
            ))
            .dataLakeStoreAccounts(Map.ofEntries(
                Map.entry("name", "test_adls"),
                Map.entry("suffix", "test_suffix")
            ))
            .defaultDataLakeStoreAccount("test_adls")
            .firewallAllowAzureIps("Enabled")
            .firewallRules(Map.ofEntries(
                Map.entry("endIpAddress", "2.2.2.2"),
                Map.entry("name", "test_rule"),
                Map.entry("startIpAddress", "1.1.1.1")
            ))
            .firewallState("Enabled")
            .location("eastus2")
            .maxDegreeOfParallelism(30)
            .maxDegreeOfParallelismPerJob(1)
            .maxJobCount(3)
            .minPriorityPerJob(1)
            .newTier("Consumption")
            .queryStoreRetention(30)
            .resourceGroupName("contosorg")
            .storageAccounts(Map.ofEntries(
                Map.entry("accessKey", "34adfa4f-cedf-4dc0-ba29-b6d1a69ab346"),
                Map.entry("name", "test_storage"),
                Map.entry("suffix", "test_suffix")
            ))
            .tags(Map.of("test_key", "test_value"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.datalakeanalytics.Account("account", {
    accountName: "contosoadla",
    computePolicies: [{
        maxDegreeOfParallelismPerJob: 1,
        minPriorityPerJob: 1,
        name: "test_policy",
        objectId: "34adfa4f-cedf-4dc0-ba29-b6d1a69ab345",
        objectType: "User",
    }],
    dataLakeStoreAccounts: [{
        name: "test_adls",
        suffix: "test_suffix",
    }],
    defaultDataLakeStoreAccount: "test_adls",
    firewallAllowAzureIps: azure_native.datalakeanalytics.FirewallAllowAzureIpsState.Enabled,
    firewallRules: [{
        endIpAddress: "2.2.2.2",
        name: "test_rule",
        startIpAddress: "1.1.1.1",
    }],
    firewallState: azure_native.datalakeanalytics.FirewallState.Enabled,
    location: "eastus2",
    maxDegreeOfParallelism: 30,
    maxDegreeOfParallelismPerJob: 1,
    maxJobCount: 3,
    minPriorityPerJob: 1,
    newTier: azure_native.datalakeanalytics.TierType.Consumption,
    queryStoreRetention: 30,
    resourceGroupName: "contosorg",
    storageAccounts: [{
        accessKey: "34adfa4f-cedf-4dc0-ba29-b6d1a69ab346",
        name: "test_storage",
        suffix: "test_suffix",
    }],
    tags: {
        test_key: "test_value",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.datalakeanalytics.Account("account",
    account_name="contosoadla",
    compute_policies=[azure_native.datalakeanalytics.CreateComputePolicyWithAccountParametersArgs(
        max_degree_of_parallelism_per_job=1,
        min_priority_per_job=1,
        name="test_policy",
        object_id="34adfa4f-cedf-4dc0-ba29-b6d1a69ab345",
        object_type="User",
    )],
    data_lake_store_accounts=[azure_native.datalakeanalytics.AddDataLakeStoreWithAccountParametersArgs(
        name="test_adls",
        suffix="test_suffix",
    )],
    default_data_lake_store_account="test_adls",
    firewall_allow_azure_ips=azure_native.datalakeanalytics.FirewallAllowAzureIpsState.ENABLED,
    firewall_rules=[azure_native.datalakeanalytics.CreateFirewallRuleWithAccountParametersArgs(
        end_ip_address="2.2.2.2",
        name="test_rule",
        start_ip_address="1.1.1.1",
    )],
    firewall_state=azure_native.datalakeanalytics.FirewallState.ENABLED,
    location="eastus2",
    max_degree_of_parallelism=30,
    max_degree_of_parallelism_per_job=1,
    max_job_count=3,
    min_priority_per_job=1,
    new_tier=azure_native.datalakeanalytics.TierType.CONSUMPTION,
    query_store_retention=30,
    resource_group_name="contosorg",
    storage_accounts=[azure_native.datalakeanalytics.AddStorageAccountWithAccountParametersArgs(
        access_key="34adfa4f-cedf-4dc0-ba29-b6d1a69ab346",
        name="test_storage",
        suffix="test_suffix",
    )],
    tags={
        "test_key": "test_value",
    })

```

```yaml
resources:
  account:
    type: azure-native:datalakeanalytics:Account
    properties:
      accountName: contosoadla
      computePolicies:
        - maxDegreeOfParallelismPerJob: 1
          minPriorityPerJob: 1
          name: test_policy
          objectId: 34adfa4f-cedf-4dc0-ba29-b6d1a69ab345
          objectType: User
      dataLakeStoreAccounts:
        - name: test_adls
          suffix: test_suffix
      defaultDataLakeStoreAccount: test_adls
      firewallAllowAzureIps: Enabled
      firewallRules:
        - endIpAddress: 2.2.2.2
          name: test_rule
          startIpAddress: 1.1.1.1
      firewallState: Enabled
      location: eastus2
      maxDegreeOfParallelism: 30
      maxDegreeOfParallelismPerJob: 1
      maxJobCount: 3
      minPriorityPerJob: 1
      newTier: Consumption
      queryStoreRetention: 30
      resourceGroupName: contosorg
      storageAccounts:
        - accessKey: 34adfa4f-cedf-4dc0-ba29-b6d1a69ab346
          name: test_storage
          suffix: test_suffix
      tags:
        test_key: test_value

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datalakeanalytics:Account test_account /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rgaba12041/providers/Microsoft.DataLakeAnalytics/accounts/testaba15818 
```
