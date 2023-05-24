Represents an incident in Azure Security Insights.
API Version: 2023-02-01.
Previous API Version: 2020-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates an incident.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var incident = new AzureNative.SecurityInsights.Incident("incident", new()
    {
        Classification = "FalsePositive",
        ClassificationComment = "Not a malicious activity",
        ClassificationReason = "IncorrectAlertLogic",
        Description = "This is a demo incident",
        FirstActivityTimeUtc = "2019-01-01T13:00:30Z",
        IncidentId = "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
        LastActivityTimeUtc = "2019-01-01T13:05:30Z",
        Owner = new AzureNative.SecurityInsights.Inputs.IncidentOwnerInfoArgs
        {
            ObjectId = "2046feea-040d-4a46-9e2b-91c2941bfa70",
        },
        ResourceGroupName = "myRg",
        Severity = "High",
        Status = "Closed",
        Title = "My incident",
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
		_, err := securityinsights.NewIncident(ctx, "incident", &securityinsights.IncidentArgs{
			Classification:        pulumi.String("FalsePositive"),
			ClassificationComment: pulumi.String("Not a malicious activity"),
			ClassificationReason:  pulumi.String("IncorrectAlertLogic"),
			Description:           pulumi.String("This is a demo incident"),
			FirstActivityTimeUtc:  pulumi.String("2019-01-01T13:00:30Z"),
			IncidentId:            pulumi.String("73e01a99-5cd7-4139-a149-9f2736ff2ab5"),
			LastActivityTimeUtc:   pulumi.String("2019-01-01T13:05:30Z"),
			Owner: &securityinsights.IncidentOwnerInfoArgs{
				ObjectId: pulumi.String("2046feea-040d-4a46-9e2b-91c2941bfa70"),
			},
			ResourceGroupName: pulumi.String("myRg"),
			Severity:          pulumi.String("High"),
			Status:            pulumi.String("Closed"),
			Title:             pulumi.String("My incident"),
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
import com.pulumi.azurenative.securityinsights.Incident;
import com.pulumi.azurenative.securityinsights.IncidentArgs;
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
        var incident = new Incident("incident", IncidentArgs.builder()        
            .classification("FalsePositive")
            .classificationComment("Not a malicious activity")
            .classificationReason("IncorrectAlertLogic")
            .description("This is a demo incident")
            .firstActivityTimeUtc("2019-01-01T13:00:30Z")
            .incidentId("73e01a99-5cd7-4139-a149-9f2736ff2ab5")
            .lastActivityTimeUtc("2019-01-01T13:05:30Z")
            .owner(Map.of("objectId", "2046feea-040d-4a46-9e2b-91c2941bfa70"))
            .resourceGroupName("myRg")
            .severity("High")
            .status("Closed")
            .title("My incident")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const incident = new azure_native.securityinsights.Incident("incident", {
    classification: "FalsePositive",
    classificationComment: "Not a malicious activity",
    classificationReason: "IncorrectAlertLogic",
    description: "This is a demo incident",
    firstActivityTimeUtc: "2019-01-01T13:00:30Z",
    incidentId: "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    lastActivityTimeUtc: "2019-01-01T13:05:30Z",
    owner: {
        objectId: "2046feea-040d-4a46-9e2b-91c2941bfa70",
    },
    resourceGroupName: "myRg",
    severity: "High",
    status: "Closed",
    title: "My incident",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

incident = azure_native.securityinsights.Incident("incident",
    classification="FalsePositive",
    classification_comment="Not a malicious activity",
    classification_reason="IncorrectAlertLogic",
    description="This is a demo incident",
    first_activity_time_utc="2019-01-01T13:00:30Z",
    incident_id="73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    last_activity_time_utc="2019-01-01T13:05:30Z",
    owner=azure_native.securityinsights.IncidentOwnerInfoArgs(
        object_id="2046feea-040d-4a46-9e2b-91c2941bfa70",
    ),
    resource_group_name="myRg",
    severity="High",
    status="Closed",
    title="My incident",
    workspace_name="myWorkspace")

```

```yaml
resources:
  incident:
    type: azure-native:securityinsights:Incident
    properties:
      classification: FalsePositive
      classificationComment: Not a malicious activity
      classificationReason: IncorrectAlertLogic
      description: This is a demo incident
      firstActivityTimeUtc: 2019-01-01T13:00:30Z
      incidentId: 73e01a99-5cd7-4139-a149-9f2736ff2ab5
      lastActivityTimeUtc: 2019-01-01T13:05:30Z
      owner:
        objectId: 2046feea-040d-4a46-9e2b-91c2941bfa70
      resourceGroupName: myRg
      severity: High
      status: Closed
      title: My incident
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:Incident 73e01a99-5cd7-4139-a149-9f2736ff2ab5 /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/incidents/73e01a99-5cd7-4139-a149-9f2736ff2ab5 
```
