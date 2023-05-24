Represents a relation between two resources
API Version: 2023-02-01.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates an incident relation.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var incidentRelation = new AzureNative.SecurityInsights.IncidentRelation("incidentRelation", new()
    {
        IncidentId = "afbd324f-6c48-459c-8710-8d1e1cd03812",
        RelatedResourceId = "/subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/bookmarks/2216d0e1-91e3-4902-89fd-d2df8c535096",
        RelationName = "4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014",
        ResourceGroupName = "myRg",
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	securityinsights "github.com/pulumi/pulumi-azure-native-sdk/securityinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := securityinsights.NewIncidentRelation(ctx, "incidentRelation", &securityinsights.IncidentRelationArgs{
			IncidentId:        pulumi.String("afbd324f-6c48-459c-8710-8d1e1cd03812"),
			RelatedResourceId: pulumi.String("/subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/bookmarks/2216d0e1-91e3-4902-89fd-d2df8c535096"),
			RelationName:      pulumi.String("4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014"),
			ResourceGroupName: pulumi.String("myRg"),
			WorkspaceName:     pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.IncidentRelation;
import com.pulumi.azurenative.securityinsights.IncidentRelationArgs;
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
        var incidentRelation = new IncidentRelation("incidentRelation", IncidentRelationArgs.builder()        
            .incidentId("afbd324f-6c48-459c-8710-8d1e1cd03812")
            .relatedResourceId("/subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/bookmarks/2216d0e1-91e3-4902-89fd-d2df8c535096")
            .relationName("4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014")
            .resourceGroupName("myRg")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const incidentRelation = new azure_native.securityinsights.IncidentRelation("incidentRelation", {
    incidentId: "afbd324f-6c48-459c-8710-8d1e1cd03812",
    relatedResourceId: "/subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/bookmarks/2216d0e1-91e3-4902-89fd-d2df8c535096",
    relationName: "4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014",
    resourceGroupName: "myRg",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

incident_relation = azure_native.securityinsights.IncidentRelation("incidentRelation",
    incident_id="afbd324f-6c48-459c-8710-8d1e1cd03812",
    related_resource_id="/subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/bookmarks/2216d0e1-91e3-4902-89fd-d2df8c535096",
    relation_name="4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014",
    resource_group_name="myRg",
    workspace_name="myWorkspace")

```

```yaml
resources:
  incidentRelation:
    type: azure-native:securityinsights:IncidentRelation
    properties:
      incidentId: afbd324f-6c48-459c-8710-8d1e1cd03812
      relatedResourceId: /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/bookmarks/2216d0e1-91e3-4902-89fd-d2df8c535096
      relationName: 4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014
      resourceGroupName: myRg
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:IncidentRelation 4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014 /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/incidents/afbd324f-6c48-459c-8710-8d1e1cd03812/relations/4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014 
```
