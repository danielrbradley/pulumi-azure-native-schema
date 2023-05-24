Class representing a cluster principal assignment.
API Version: 2022-12-29.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### KustoClusterPrincipalAssignmentsCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var clusterPrincipalAssignment = new AzureNative.Kusto.ClusterPrincipalAssignment("clusterPrincipalAssignment", new()
    {
        ClusterName = "kustoCluster",
        PrincipalAssignmentName = "kustoprincipal1",
        PrincipalId = "87654321-1234-1234-1234-123456789123",
        PrincipalType = "App",
        ResourceGroupName = "kustorptest",
        Role = "AllDatabasesAdmin",
        TenantId = "12345678-1234-1234-1234-123456789123",
    });

});


```

```go
package main

import (
	kusto "github.com/pulumi/pulumi-azure-native-sdk/kusto"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := kusto.NewClusterPrincipalAssignment(ctx, "clusterPrincipalAssignment", &kusto.ClusterPrincipalAssignmentArgs{
			ClusterName:             pulumi.String("kustoCluster"),
			PrincipalAssignmentName: pulumi.String("kustoprincipal1"),
			PrincipalId:             pulumi.String("87654321-1234-1234-1234-123456789123"),
			PrincipalType:           pulumi.String("App"),
			ResourceGroupName:       pulumi.String("kustorptest"),
			Role:                    pulumi.String("AllDatabasesAdmin"),
			TenantId:                pulumi.String("12345678-1234-1234-1234-123456789123"),
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
import com.pulumi.azurenative.kusto.ClusterPrincipalAssignment;
import com.pulumi.azurenative.kusto.ClusterPrincipalAssignmentArgs;
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
        var clusterPrincipalAssignment = new ClusterPrincipalAssignment("clusterPrincipalAssignment", ClusterPrincipalAssignmentArgs.builder()        
            .clusterName("kustoCluster")
            .principalAssignmentName("kustoprincipal1")
            .principalId("87654321-1234-1234-1234-123456789123")
            .principalType("App")
            .resourceGroupName("kustorptest")
            .role("AllDatabasesAdmin")
            .tenantId("12345678-1234-1234-1234-123456789123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const clusterPrincipalAssignment = new azure_native.kusto.ClusterPrincipalAssignment("clusterPrincipalAssignment", {
    clusterName: "kustoCluster",
    principalAssignmentName: "kustoprincipal1",
    principalId: "87654321-1234-1234-1234-123456789123",
    principalType: "App",
    resourceGroupName: "kustorptest",
    role: "AllDatabasesAdmin",
    tenantId: "12345678-1234-1234-1234-123456789123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster_principal_assignment = azure_native.kusto.ClusterPrincipalAssignment("clusterPrincipalAssignment",
    cluster_name="kustoCluster",
    principal_assignment_name="kustoprincipal1",
    principal_id="87654321-1234-1234-1234-123456789123",
    principal_type="App",
    resource_group_name="kustorptest",
    role="AllDatabasesAdmin",
    tenant_id="12345678-1234-1234-1234-123456789123")

```

```yaml
resources:
  clusterPrincipalAssignment:
    type: azure-native:kusto:ClusterPrincipalAssignment
    properties:
      clusterName: kustoCluster
      principalAssignmentName: kustoprincipal1
      principalId: 87654321-1234-1234-1234-123456789123
      principalType: App
      resourceGroupName: kustorptest
      role: AllDatabasesAdmin
      tenantId: 12345678-1234-1234-1234-123456789123

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:kusto:ClusterPrincipalAssignment kustoCluster/kustoprincipal1 /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster/PrincipalAssignments/kustoprincipal1 
```
