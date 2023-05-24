A SQL virtual machine group.
API Version: 2022-02-01.
Previous API Version: 2017-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates a SQL virtual machine group.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlVirtualMachineGroup = new AzureNative.SqlVirtualMachine.SqlVirtualMachineGroup("sqlVirtualMachineGroup", new()
    {
        Location = "northeurope",
        ResourceGroupName = "testrg",
        SqlImageOffer = "SQL2016-WS2016",
        SqlImageSku = "Enterprise",
        SqlVirtualMachineGroupName = "testvmgroup",
        Tags = 
        {
            { "mytag", "myval" },
        },
        WsfcDomainProfile = new AzureNative.SqlVirtualMachine.Inputs.WsfcDomainProfileArgs
        {
            ClusterBootstrapAccount = "testrpadmin",
            ClusterOperatorAccount = "testrp@testdomain.com",
            ClusterSubnetType = "MultiSubnet",
            DomainFqdn = "testdomain.com",
            OuPath = "OU=WSCluster,DC=testdomain,DC=com",
            SqlServiceAccount = "sqlservice@testdomain.com",
            StorageAccountPrimaryKey = "<primary storage access key>",
            StorageAccountUrl = "https://storgact.blob.core.windows.net/",
        },
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
		_, err := sqlvirtualmachine.NewSqlVirtualMachineGroup(ctx, "sqlVirtualMachineGroup", &sqlvirtualmachine.SqlVirtualMachineGroupArgs{
			Location:                   pulumi.String("northeurope"),
			ResourceGroupName:          pulumi.String("testrg"),
			SqlImageOffer:              pulumi.String("SQL2016-WS2016"),
			SqlImageSku:                pulumi.String("Enterprise"),
			SqlVirtualMachineGroupName: pulumi.String("testvmgroup"),
			Tags: pulumi.StringMap{
				"mytag": pulumi.String("myval"),
			},
			WsfcDomainProfile: &sqlvirtualmachine.WsfcDomainProfileArgs{
				ClusterBootstrapAccount:  pulumi.String("testrpadmin"),
				ClusterOperatorAccount:   pulumi.String("testrp@testdomain.com"),
				ClusterSubnetType:        pulumi.String("MultiSubnet"),
				DomainFqdn:               pulumi.String("testdomain.com"),
				OuPath:                   pulumi.String("OU=WSCluster,DC=testdomain,DC=com"),
				SqlServiceAccount:        pulumi.String("sqlservice@testdomain.com"),
				StorageAccountPrimaryKey: pulumi.String("<primary storage access key>"),
				StorageAccountUrl:        pulumi.String("https://storgact.blob.core.windows.net/"),
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
import com.pulumi.azurenative.sqlvirtualmachine.SqlVirtualMachineGroup;
import com.pulumi.azurenative.sqlvirtualmachine.SqlVirtualMachineGroupArgs;
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
        var sqlVirtualMachineGroup = new SqlVirtualMachineGroup("sqlVirtualMachineGroup", SqlVirtualMachineGroupArgs.builder()        
            .location("northeurope")
            .resourceGroupName("testrg")
            .sqlImageOffer("SQL2016-WS2016")
            .sqlImageSku("Enterprise")
            .sqlVirtualMachineGroupName("testvmgroup")
            .tags(Map.of("mytag", "myval"))
            .wsfcDomainProfile(Map.ofEntries(
                Map.entry("clusterBootstrapAccount", "testrpadmin"),
                Map.entry("clusterOperatorAccount", "testrp@testdomain.com"),
                Map.entry("clusterSubnetType", "MultiSubnet"),
                Map.entry("domainFqdn", "testdomain.com"),
                Map.entry("ouPath", "OU=WSCluster,DC=testdomain,DC=com"),
                Map.entry("sqlServiceAccount", "sqlservice@testdomain.com"),
                Map.entry("storageAccountPrimaryKey", "<primary storage access key>"),
                Map.entry("storageAccountUrl", "https://storgact.blob.core.windows.net/")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlVirtualMachineGroup = new azure_native.sqlvirtualmachine.SqlVirtualMachineGroup("sqlVirtualMachineGroup", {
    location: "northeurope",
    resourceGroupName: "testrg",
    sqlImageOffer: "SQL2016-WS2016",
    sqlImageSku: "Enterprise",
    sqlVirtualMachineGroupName: "testvmgroup",
    tags: {
        mytag: "myval",
    },
    wsfcDomainProfile: {
        clusterBootstrapAccount: "testrpadmin",
        clusterOperatorAccount: "testrp@testdomain.com",
        clusterSubnetType: "MultiSubnet",
        domainFqdn: "testdomain.com",
        ouPath: "OU=WSCluster,DC=testdomain,DC=com",
        sqlServiceAccount: "sqlservice@testdomain.com",
        storageAccountPrimaryKey: "<primary storage access key>",
        storageAccountUrl: "https://storgact.blob.core.windows.net/",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_virtual_machine_group = azure_native.sqlvirtualmachine.SqlVirtualMachineGroup("sqlVirtualMachineGroup",
    location="northeurope",
    resource_group_name="testrg",
    sql_image_offer="SQL2016-WS2016",
    sql_image_sku="Enterprise",
    sql_virtual_machine_group_name="testvmgroup",
    tags={
        "mytag": "myval",
    },
    wsfc_domain_profile=azure_native.sqlvirtualmachine.WsfcDomainProfileArgs(
        cluster_bootstrap_account="testrpadmin",
        cluster_operator_account="testrp@testdomain.com",
        cluster_subnet_type="MultiSubnet",
        domain_fqdn="testdomain.com",
        ou_path="OU=WSCluster,DC=testdomain,DC=com",
        sql_service_account="sqlservice@testdomain.com",
        storage_account_primary_key="<primary storage access key>",
        storage_account_url="https://storgact.blob.core.windows.net/",
    ))

```

```yaml
resources:
  sqlVirtualMachineGroup:
    type: azure-native:sqlvirtualmachine:SqlVirtualMachineGroup
    properties:
      location: northeurope
      resourceGroupName: testrg
      sqlImageOffer: SQL2016-WS2016
      sqlImageSku: Enterprise
      sqlVirtualMachineGroupName: testvmgroup
      tags:
        mytag: myval
      wsfcDomainProfile:
        clusterBootstrapAccount: testrpadmin
        clusterOperatorAccount: testrp@testdomain.com
        clusterSubnetType: MultiSubnet
        domainFqdn: testdomain.com
        ouPath: OU=WSCluster,DC=testdomain,DC=com
        sqlServiceAccount: sqlservice@testdomain.com
        storageAccountPrimaryKey: <primary storage access key>
        storageAccountUrl: https://storgact.blob.core.windows.net/

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sqlvirtualmachine:SqlVirtualMachineGroup testvmgroup /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachineGroups/testvmgroup 
```
