The container for solution.
API Version: 2015-11-01-preview.
Previous API Version: 2015-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SolutionCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementAssociation = new AzureNative.OperationsManagement.ManagementAssociation("managementAssociation", new()
    {
        Location = "East US",
        ManagementAssociationName = "managementAssociation1",
        Properties = new AzureNative.OperationsManagement.Inputs.ManagementAssociationPropertiesArgs
        {
            ApplicationId = "/subscriptions/sub1/resourcegroups/rg1/providers/Microsoft.Appliance/Appliances/appliance1",
        },
        ProviderName = "providerName",
        ResourceGroupName = "rg1",
        ResourceName = "resourceName",
        ResourceType = "resourceType",
    });

});


```

```go
package main

import (
	operationsmanagement "github.com/pulumi/pulumi-azure-native-sdk/operationsmanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := operationsmanagement.NewManagementAssociation(ctx, "managementAssociation", &operationsmanagement.ManagementAssociationArgs{
			Location:                  pulumi.String("East US"),
			ManagementAssociationName: pulumi.String("managementAssociation1"),
			Properties: &operationsmanagement.ManagementAssociationPropertiesArgs{
				ApplicationId: pulumi.String("/subscriptions/sub1/resourcegroups/rg1/providers/Microsoft.Appliance/Appliances/appliance1"),
			},
			ProviderName:      pulumi.String("providerName"),
			ResourceGroupName: pulumi.String("rg1"),
			ResourceName:      pulumi.String("resourceName"),
			ResourceType:      pulumi.String("resourceType"),
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
import com.pulumi.azurenative.operationsmanagement.ManagementAssociation;
import com.pulumi.azurenative.operationsmanagement.ManagementAssociationArgs;
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
        var managementAssociation = new ManagementAssociation("managementAssociation", ManagementAssociationArgs.builder()        
            .location("East US")
            .managementAssociationName("managementAssociation1")
            .properties(Map.of("applicationId", "/subscriptions/sub1/resourcegroups/rg1/providers/Microsoft.Appliance/Appliances/appliance1"))
            .providerName("providerName")
            .resourceGroupName("rg1")
            .resourceName("resourceName")
            .resourceType("resourceType")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementAssociation = new azure_native.operationsmanagement.ManagementAssociation("managementAssociation", {
    location: "East US",
    managementAssociationName: "managementAssociation1",
    properties: {
        applicationId: "/subscriptions/sub1/resourcegroups/rg1/providers/Microsoft.Appliance/Appliances/appliance1",
    },
    providerName: "providerName",
    resourceGroupName: "rg1",
    resourceName: "resourceName",
    resourceType: "resourceType",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_association = azure_native.operationsmanagement.ManagementAssociation("managementAssociation",
    location="East US",
    management_association_name="managementAssociation1",
    properties=azure_native.operationsmanagement.ManagementAssociationPropertiesArgs(
        application_id="/subscriptions/sub1/resourcegroups/rg1/providers/Microsoft.Appliance/Appliances/appliance1",
    ),
    provider_name="providerName",
    resource_group_name="rg1",
    resource_name_="resourceName",
    resource_type="resourceType")

```

```yaml
resources:
  managementAssociation:
    type: azure-native:operationsmanagement:ManagementAssociation
    properties:
      location: East US
      managementAssociationName: managementAssociation1
      properties:
        applicationId: /subscriptions/sub1/resourcegroups/rg1/providers/Microsoft.Appliance/Appliances/appliance1
      providerName: providerName
      resourceGroupName: rg1
      resourceName: resourceName
      resourceType: resourceType

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:operationsmanagement:ManagementAssociation managementAssociation1 /subscriptions/subid/resourcegroups/rg1/providers/Microsoft.OperationalInsights/workspaces/ws1/Microsoft.OperationsManagement/ManagementAssociations/managementAssociation1 
```
