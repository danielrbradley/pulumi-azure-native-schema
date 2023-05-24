A SqlAvailabilityGroup.
API Version: 2023-03-15-preview.

{{% examples %}}
## Example Usage
{{% example %}}
### Updates a SQL Availability Group tags.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlAvailabilityGroup = new AzureNative.AzureArcData.SqlAvailabilityGroup("sqlAvailabilityGroup", new()
    {
        Location = "northeurope",
        Properties = new AzureNative.AzureArcData.Inputs.SqlAvailabilityGroupPropertiesArgs
        {
            AvailabilityGroupId = "00000000-1111-2222-3333-444444444444",
            AvailabilityGroupName = "myAvailabilityGroup",
            BasicFeatures = false,
            ClusterTypeDesc = "WSFC",
            CollectionTimestamp = "2022-05-05T16:26:33.883Z",
            DbFailover = true,
            DtcSupport = false,
            InstanceName = "testInstance",
            IsContained = false,
            IsDistributed = false,
            RequiredSynchronizedSecondariesCommit = 0,
            Version = 0,
        },
        ResourceGroupName = "testrg",
        SqlAvailabilityGroupName = "testsqlAvailabilityGroup",
        Tags = 
        {
            { "mytag", "myval" },
        },
    });

});


```

```go
package main

import (
	azurearcdata "github.com/pulumi/pulumi-azure-native-sdk/azurearcdata"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azurearcdata.NewSqlAvailabilityGroup(ctx, "sqlAvailabilityGroup", &azurearcdata.SqlAvailabilityGroupArgs{
			Location: pulumi.String("northeurope"),
			Properties: &azurearcdata.SqlAvailabilityGroupPropertiesArgs{
				AvailabilityGroupId:                   pulumi.String("00000000-1111-2222-3333-444444444444"),
				AvailabilityGroupName:                 pulumi.String("myAvailabilityGroup"),
				BasicFeatures:                         pulumi.Bool(false),
				ClusterTypeDesc:                       pulumi.String("WSFC"),
				CollectionTimestamp:                   pulumi.String("2022-05-05T16:26:33.883Z"),
				DbFailover:                            pulumi.Bool(true),
				DtcSupport:                            pulumi.Bool(false),
				InstanceName:                          pulumi.String("testInstance"),
				IsContained:                           pulumi.Bool(false),
				IsDistributed:                         pulumi.Bool(false),
				RequiredSynchronizedSecondariesCommit: pulumi.Int(0),
				Version:                               pulumi.Int(0),
			},
			ResourceGroupName:        pulumi.String("testrg"),
			SqlAvailabilityGroupName: pulumi.String("testsqlAvailabilityGroup"),
			Tags: pulumi.StringMap{
				"mytag": pulumi.String("myval"),
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
import com.pulumi.azurenative.azurearcdata.SqlAvailabilityGroup;
import com.pulumi.azurenative.azurearcdata.SqlAvailabilityGroupArgs;
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
        var sqlAvailabilityGroup = new SqlAvailabilityGroup("sqlAvailabilityGroup", SqlAvailabilityGroupArgs.builder()        
            .location("northeurope")
            .properties(Map.ofEntries(
                Map.entry("availabilityGroupId", "00000000-1111-2222-3333-444444444444"),
                Map.entry("availabilityGroupName", "myAvailabilityGroup"),
                Map.entry("basicFeatures", false),
                Map.entry("clusterTypeDesc", "WSFC"),
                Map.entry("collectionTimestamp", "2022-05-05T16:26:33.883Z"),
                Map.entry("dbFailover", true),
                Map.entry("dtcSupport", false),
                Map.entry("instanceName", "testInstance"),
                Map.entry("isContained", false),
                Map.entry("isDistributed", false),
                Map.entry("requiredSynchronizedSecondariesCommit", 0),
                Map.entry("version", 0)
            ))
            .resourceGroupName("testrg")
            .sqlAvailabilityGroupName("testsqlAvailabilityGroup")
            .tags(Map.of("mytag", "myval"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlAvailabilityGroup = new azure_native.azurearcdata.SqlAvailabilityGroup("sqlAvailabilityGroup", {
    location: "northeurope",
    properties: {
        availabilityGroupId: "00000000-1111-2222-3333-444444444444",
        availabilityGroupName: "myAvailabilityGroup",
        basicFeatures: false,
        clusterTypeDesc: "WSFC",
        collectionTimestamp: "2022-05-05T16:26:33.883Z",
        dbFailover: true,
        dtcSupport: false,
        instanceName: "testInstance",
        isContained: false,
        isDistributed: false,
        requiredSynchronizedSecondariesCommit: 0,
        version: 0,
    },
    resourceGroupName: "testrg",
    sqlAvailabilityGroupName: "testsqlAvailabilityGroup",
    tags: {
        mytag: "myval",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_availability_group = azure_native.azurearcdata.SqlAvailabilityGroup("sqlAvailabilityGroup",
    location="northeurope",
    properties=azure_native.azurearcdata.SqlAvailabilityGroupPropertiesArgs(
        availability_group_id="00000000-1111-2222-3333-444444444444",
        availability_group_name="myAvailabilityGroup",
        basic_features=False,
        cluster_type_desc="WSFC",
        collection_timestamp="2022-05-05T16:26:33.883Z",
        db_failover=True,
        dtc_support=False,
        instance_name="testInstance",
        is_contained=False,
        is_distributed=False,
        required_synchronized_secondaries_commit=0,
        version=0,
    ),
    resource_group_name="testrg",
    sql_availability_group_name="testsqlAvailabilityGroup",
    tags={
        "mytag": "myval",
    })

```

```yaml
resources:
  sqlAvailabilityGroup:
    type: azure-native:azurearcdata:SqlAvailabilityGroup
    properties:
      location: northeurope
      properties:
        availabilityGroupId: 00000000-1111-2222-3333-444444444444
        availabilityGroupName: myAvailabilityGroup
        basicFeatures: false
        clusterTypeDesc: WSFC
        collectionTimestamp: 2022-05-05T16:26:33.883Z
        dbFailover: true
        dtcSupport: false
        instanceName: testInstance
        isContained: false
        isDistributed: false
        requiredSynchronizedSecondariesCommit: 0
        version: 0
      resourceGroupName: testrg
      sqlAvailabilityGroupName: testsqlAvailabilityGroup
      tags:
        mytag: myval

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurearcdata:SqlAvailabilityGroup testsqlServerInstance /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/sqlAvailabilityGroups/testsqlAvailabilityGroup 
```
