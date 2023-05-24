Represents an incident comment
API Version: 2023-02-01.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates an incident comment.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var incidentComment = new AzureNative.SecurityInsights.IncidentComment("incidentComment", new()
    {
        IncidentCommentId = "4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014",
        IncidentId = "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
        Message = "Some message",
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
		_, err := securityinsights.NewIncidentComment(ctx, "incidentComment", &securityinsights.IncidentCommentArgs{
			IncidentCommentId: pulumi.String("4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014"),
			IncidentId:        pulumi.String("73e01a99-5cd7-4139-a149-9f2736ff2ab5"),
			Message:           pulumi.String("Some message"),
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
import com.pulumi.azurenative.securityinsights.IncidentComment;
import com.pulumi.azurenative.securityinsights.IncidentCommentArgs;
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
        var incidentComment = new IncidentComment("incidentComment", IncidentCommentArgs.builder()        
            .incidentCommentId("4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014")
            .incidentId("73e01a99-5cd7-4139-a149-9f2736ff2ab5")
            .message("Some message")
            .resourceGroupName("myRg")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const incidentComment = new azure_native.securityinsights.IncidentComment("incidentComment", {
    incidentCommentId: "4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014",
    incidentId: "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    message: "Some message",
    resourceGroupName: "myRg",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

incident_comment = azure_native.securityinsights.IncidentComment("incidentComment",
    incident_comment_id="4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014",
    incident_id="73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    message="Some message",
    resource_group_name="myRg",
    workspace_name="myWorkspace")

```

```yaml
resources:
  incidentComment:
    type: azure-native:securityinsights:IncidentComment
    properties:
      incidentCommentId: 4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014
      incidentId: 73e01a99-5cd7-4139-a149-9f2736ff2ab5
      message: Some message
      resourceGroupName: myRg
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:IncidentComment 4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014 /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalIinsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/incidents/73e01a99-5cd7-4139-a149-9f2736ff2ab5/comments/4bb36b7b-26ff-4d1c-9cbe-0d8ab3da0014 
```
