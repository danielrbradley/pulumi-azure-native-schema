The diagnostic setting resource.
API Version: 2017-04-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### BatchAccountDelete
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var diagnosticSetting = new AzureNative.AadIam.DiagnosticSetting("diagnosticSetting", new()
    {
        EventHubAuthorizationRuleId = "/subscriptions/1a66ce04-b633-4a0b-b2bc-a912ec8986a6/resourceGroups/montest/providers/microsoft.eventhub/namespaces/mynamespace/eventhubs/myeventhub/authorizationrules/myrule",
        EventHubName = "myeventhub",
        Logs = new[]
        {
            new AzureNative.AadIam.Inputs.LogSettingsArgs
            {
                Category = "AuditLogs",
                Enabled = true,
                RetentionPolicy = new AzureNative.AadIam.Inputs.RetentionPolicyArgs
                {
                    Days = 0,
                    Enabled = false,
                },
            },
        },
        Name = "mysetting",
        StorageAccountId = "/subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/apptest/providers/Microsoft.Storage/storageAccounts/appteststorage1",
        WorkspaceId = "",
    });

});


```

```go
package main

import (
	aadiam "github.com/pulumi/pulumi-azure-native-sdk/aadiam"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := aadiam.NewDiagnosticSetting(ctx, "diagnosticSetting", &aadiam.DiagnosticSettingArgs{
			EventHubAuthorizationRuleId: pulumi.String("/subscriptions/1a66ce04-b633-4a0b-b2bc-a912ec8986a6/resourceGroups/montest/providers/microsoft.eventhub/namespaces/mynamespace/eventhubs/myeventhub/authorizationrules/myrule"),
			EventHubName:                pulumi.String("myeventhub"),
			Logs: []aadiam.LogSettingsArgs{
				{
					Category: pulumi.String("AuditLogs"),
					Enabled:  pulumi.Bool(true),
					RetentionPolicy: {
						Days:    pulumi.Int(0),
						Enabled: pulumi.Bool(false),
					},
				},
			},
			Name:             pulumi.String("mysetting"),
			StorageAccountId: pulumi.String("/subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/apptest/providers/Microsoft.Storage/storageAccounts/appteststorage1"),
			WorkspaceId:      pulumi.String(""),
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
import com.pulumi.azurenative.aadiam.DiagnosticSetting;
import com.pulumi.azurenative.aadiam.DiagnosticSettingArgs;
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
        var diagnosticSetting = new DiagnosticSetting("diagnosticSetting", DiagnosticSettingArgs.builder()        
            .eventHubAuthorizationRuleId("/subscriptions/1a66ce04-b633-4a0b-b2bc-a912ec8986a6/resourceGroups/montest/providers/microsoft.eventhub/namespaces/mynamespace/eventhubs/myeventhub/authorizationrules/myrule")
            .eventHubName("myeventhub")
            .logs(Map.ofEntries(
                Map.entry("category", "AuditLogs"),
                Map.entry("enabled", true),
                Map.entry("retentionPolicy", Map.ofEntries(
                    Map.entry("days", 0),
                    Map.entry("enabled", false)
                ))
            ))
            .name("mysetting")
            .storageAccountId("/subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/apptest/providers/Microsoft.Storage/storageAccounts/appteststorage1")
            .workspaceId("")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const diagnosticSetting = new azure_native.aadiam.DiagnosticSetting("diagnosticSetting", {
    eventHubAuthorizationRuleId: "/subscriptions/1a66ce04-b633-4a0b-b2bc-a912ec8986a6/resourceGroups/montest/providers/microsoft.eventhub/namespaces/mynamespace/eventhubs/myeventhub/authorizationrules/myrule",
    eventHubName: "myeventhub",
    logs: [{
        category: "AuditLogs",
        enabled: true,
        retentionPolicy: {
            days: 0,
            enabled: false,
        },
    }],
    name: "mysetting",
    storageAccountId: "/subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/apptest/providers/Microsoft.Storage/storageAccounts/appteststorage1",
    workspaceId: "",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

diagnostic_setting = azure_native.aadiam.DiagnosticSetting("diagnosticSetting",
    event_hub_authorization_rule_id="/subscriptions/1a66ce04-b633-4a0b-b2bc-a912ec8986a6/resourceGroups/montest/providers/microsoft.eventhub/namespaces/mynamespace/eventhubs/myeventhub/authorizationrules/myrule",
    event_hub_name="myeventhub",
    logs=[{
        "category": "AuditLogs",
        "enabled": True,
        "retentionPolicy": azure_native.aadiam.RetentionPolicyArgs(
            days=0,
            enabled=False,
        ),
    }],
    name="mysetting",
    storage_account_id="/subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/apptest/providers/Microsoft.Storage/storageAccounts/appteststorage1",
    workspace_id="")

```

```yaml
resources:
  diagnosticSetting:
    type: azure-native:aadiam:DiagnosticSetting
    properties:
      eventHubAuthorizationRuleId: /subscriptions/1a66ce04-b633-4a0b-b2bc-a912ec8986a6/resourceGroups/montest/providers/microsoft.eventhub/namespaces/mynamespace/eventhubs/myeventhub/authorizationrules/myrule
      eventHubName: myeventhub
      logs:
        - category: AuditLogs
          enabled: true
          retentionPolicy:
            days: 0
            enabled: false
      name: mysetting
      storageAccountId: /subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/apptest/providers/Microsoft.Storage/storageAccounts/appteststorage1
      workspaceId:

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:aadiam:DiagnosticSetting mysetting providers/microsoft.aadiam/diagnosticSettings/mysetting 
```
