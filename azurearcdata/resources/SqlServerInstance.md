A SqlServerInstance.
API Version: 2023-03-15-preview.
Previous API Version: 2021-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Updates a SQL Server Instance tags.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlServerInstance = new AzureNative.AzureArcData.SqlServerInstance("sqlServerInstance", new()
    {
        Location = "northeurope",
        Properties = new AzureNative.AzureArcData.Inputs.SqlServerInstancePropertiesArgs
        {
            AzureDefenderStatus = "Protected",
            AzureDefenderStatusLastUpdated = "2020-01-02T17:18:19.1234567Z",
            Collation = "collation",
            ContainerResourceId = "Resource id of hosting Arc Machine",
            Cores = "4",
            CurrentVersion = "2012",
            Edition = "Developer",
            HostType = "Physical Server",
            InstanceName = "name of instance",
            LicenseType = "Free",
            PatchLevel = "patchlevel",
            ProductId = "sql id",
            Status = "Registered",
            TcpDynamicPorts = "1433",
            TcpStaticPorts = "1433",
            VCore = "4",
            Version = "SQL Server 2012",
        },
        ResourceGroupName = "testrg",
        SqlServerInstanceName = "testsqlServerInstance",
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
		_, err := azurearcdata.NewSqlServerInstance(ctx, "sqlServerInstance", &azurearcdata.SqlServerInstanceArgs{
			Location: pulumi.String("northeurope"),
			Properties: &azurearcdata.SqlServerInstancePropertiesArgs{
				AzureDefenderStatus:            pulumi.String("Protected"),
				AzureDefenderStatusLastUpdated: pulumi.String("2020-01-02T17:18:19.1234567Z"),
				Collation:                      pulumi.String("collation"),
				ContainerResourceId:            pulumi.String("Resource id of hosting Arc Machine"),
				Cores:                          pulumi.String("4"),
				CurrentVersion:                 pulumi.String("2012"),
				Edition:                        pulumi.String("Developer"),
				HostType:                       pulumi.String("Physical Server"),
				InstanceName:                   pulumi.String("name of instance"),
				LicenseType:                    pulumi.String("Free"),
				PatchLevel:                     pulumi.String("patchlevel"),
				ProductId:                      pulumi.String("sql id"),
				Status:                         pulumi.String("Registered"),
				TcpDynamicPorts:                pulumi.String("1433"),
				TcpStaticPorts:                 pulumi.String("1433"),
				VCore:                          pulumi.String("4"),
				Version:                        pulumi.String("SQL Server 2012"),
			},
			ResourceGroupName:     pulumi.String("testrg"),
			SqlServerInstanceName: pulumi.String("testsqlServerInstance"),
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
import com.pulumi.azurenative.azurearcdata.SqlServerInstance;
import com.pulumi.azurenative.azurearcdata.SqlServerInstanceArgs;
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
        var sqlServerInstance = new SqlServerInstance("sqlServerInstance", SqlServerInstanceArgs.builder()        
            .location("northeurope")
            .properties(Map.ofEntries(
                Map.entry("azureDefenderStatus", "Protected"),
                Map.entry("azureDefenderStatusLastUpdated", "2020-01-02T17:18:19.1234567Z"),
                Map.entry("collation", "collation"),
                Map.entry("containerResourceId", "Resource id of hosting Arc Machine"),
                Map.entry("cores", "4"),
                Map.entry("currentVersion", "2012"),
                Map.entry("edition", "Developer"),
                Map.entry("hostType", "Physical Server"),
                Map.entry("instanceName", "name of instance"),
                Map.entry("licenseType", "Free"),
                Map.entry("patchLevel", "patchlevel"),
                Map.entry("productId", "sql id"),
                Map.entry("status", "Registered"),
                Map.entry("tcpDynamicPorts", "1433"),
                Map.entry("tcpStaticPorts", "1433"),
                Map.entry("vCore", "4"),
                Map.entry("version", "SQL Server 2012")
            ))
            .resourceGroupName("testrg")
            .sqlServerInstanceName("testsqlServerInstance")
            .tags(Map.of("mytag", "myval"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlServerInstance = new azure_native.azurearcdata.SqlServerInstance("sqlServerInstance", {
    location: "northeurope",
    properties: {
        azureDefenderStatus: "Protected",
        azureDefenderStatusLastUpdated: "2020-01-02T17:18:19.1234567Z",
        collation: "collation",
        containerResourceId: "Resource id of hosting Arc Machine",
        cores: "4",
        currentVersion: "2012",
        edition: "Developer",
        hostType: "Physical Server",
        instanceName: "name of instance",
        licenseType: "Free",
        patchLevel: "patchlevel",
        productId: "sql id",
        status: "Registered",
        tcpDynamicPorts: "1433",
        tcpStaticPorts: "1433",
        vCore: "4",
        version: "SQL Server 2012",
    },
    resourceGroupName: "testrg",
    sqlServerInstanceName: "testsqlServerInstance",
    tags: {
        mytag: "myval",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_server_instance = azure_native.azurearcdata.SqlServerInstance("sqlServerInstance",
    location="northeurope",
    properties=azure_native.azurearcdata.SqlServerInstancePropertiesArgs(
        azure_defender_status="Protected",
        azure_defender_status_last_updated="2020-01-02T17:18:19.1234567Z",
        collation="collation",
        container_resource_id="Resource id of hosting Arc Machine",
        cores="4",
        current_version="2012",
        edition="Developer",
        host_type="Physical Server",
        instance_name="name of instance",
        license_type="Free",
        patch_level="patchlevel",
        product_id="sql id",
        status="Registered",
        tcp_dynamic_ports="1433",
        tcp_static_ports="1433",
        v_core="4",
        version="SQL Server 2012",
    ),
    resource_group_name="testrg",
    sql_server_instance_name="testsqlServerInstance",
    tags={
        "mytag": "myval",
    })

```

```yaml
resources:
  sqlServerInstance:
    type: azure-native:azurearcdata:SqlServerInstance
    properties:
      location: northeurope
      properties:
        azureDefenderStatus: Protected
        azureDefenderStatusLastUpdated: 2020-01-02T17:18:19.1234567Z
        collation: collation
        containerResourceId: Resource id of hosting Arc Machine
        cores: '4'
        currentVersion: '2012'
        edition: Developer
        hostType: Physical Server
        instanceName: name of instance
        licenseType: Free
        patchLevel: patchlevel
        productId: sql id
        status: Registered
        tcpDynamicPorts: '1433'
        tcpStaticPorts: '1433'
        vCore: '4'
        version: SQL Server 2012
      resourceGroupName: testrg
      sqlServerInstanceName: testsqlServerInstance
      tags:
        mytag: myval

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurearcdata:SqlServerInstance testsqlServerInstance /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/SqlServerInstances/testsqlServerInstance 
```
