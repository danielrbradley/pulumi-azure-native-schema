Definition of the runbook type.
API Version: 2022-08-08.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update runbook and publish it
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var runbook = new AzureNative.Automation.Runbook("runbook", new()
    {
        AutomationAccountName = "ContoseAutomationAccount",
        Description = "Description of the Runbook",
        Location = "East US 2",
        LogActivityTrace = 1,
        LogProgress = true,
        LogVerbose = false,
        Name = "Get-AzureVMTutorial",
        PublishContentLink = new AzureNative.Automation.Inputs.ContentLinkArgs
        {
            ContentHash = new AzureNative.Automation.Inputs.ContentHashArgs
            {
                Algorithm = "SHA256",
                Value = "115775B8FF2BE672D8A946BD0B489918C724DDE15A440373CA54461D53010A80",
            },
            Uri = "https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/101-automation-runbook-getvms/Runbooks/Get-AzureVMTutorial.ps1",
        },
        ResourceGroupName = "rg",
        RunbookName = "Get-AzureVMTutorial",
        RunbookType = "PowerShellWorkflow",
        Tags = 
        {
            { "tag01", "value01" },
            { "tag02", "value02" },
        },
    });

});


```

```go
package main

import (
	automation "github.com/pulumi/pulumi-azure-native-sdk/automation"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := automation.NewRunbook(ctx, "runbook", &automation.RunbookArgs{
			AutomationAccountName: pulumi.String("ContoseAutomationAccount"),
			Description:           pulumi.String("Description of the Runbook"),
			Location:              pulumi.String("East US 2"),
			LogActivityTrace:      pulumi.Int(1),
			LogProgress:           pulumi.Bool(true),
			LogVerbose:            pulumi.Bool(false),
			Name:                  pulumi.String("Get-AzureVMTutorial"),
			PublishContentLink: automation.ContentLinkResponse{
				ContentHash: &automation.ContentHashArgs{
					Algorithm: pulumi.String("SHA256"),
					Value:     pulumi.String("115775B8FF2BE672D8A946BD0B489918C724DDE15A440373CA54461D53010A80"),
				},
				Uri: pulumi.String("https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/101-automation-runbook-getvms/Runbooks/Get-AzureVMTutorial.ps1"),
			},
			ResourceGroupName: pulumi.String("rg"),
			RunbookName:       pulumi.String("Get-AzureVMTutorial"),
			RunbookType:       pulumi.String("PowerShellWorkflow"),
			Tags: pulumi.StringMap{
				"tag01": pulumi.String("value01"),
				"tag02": pulumi.String("value02"),
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
import com.pulumi.azurenative.automation.Runbook;
import com.pulumi.azurenative.automation.RunbookArgs;
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
        var runbook = new Runbook("runbook", RunbookArgs.builder()        
            .automationAccountName("ContoseAutomationAccount")
            .description("Description of the Runbook")
            .location("East US 2")
            .logActivityTrace(1)
            .logProgress(true)
            .logVerbose(false)
            .name("Get-AzureVMTutorial")
            .publishContentLink(Map.ofEntries(
                Map.entry("contentHash", Map.ofEntries(
                    Map.entry("algorithm", "SHA256"),
                    Map.entry("value", "115775B8FF2BE672D8A946BD0B489918C724DDE15A440373CA54461D53010A80")
                )),
                Map.entry("uri", "https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/101-automation-runbook-getvms/Runbooks/Get-AzureVMTutorial.ps1")
            ))
            .resourceGroupName("rg")
            .runbookName("Get-AzureVMTutorial")
            .runbookType("PowerShellWorkflow")
            .tags(Map.ofEntries(
                Map.entry("tag01", "value01"),
                Map.entry("tag02", "value02")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const runbook = new azure_native.automation.Runbook("runbook", {
    automationAccountName: "ContoseAutomationAccount",
    description: "Description of the Runbook",
    location: "East US 2",
    logActivityTrace: 1,
    logProgress: true,
    logVerbose: false,
    name: "Get-AzureVMTutorial",
    publishContentLink: {
        contentHash: {
            algorithm: "SHA256",
            value: "115775B8FF2BE672D8A946BD0B489918C724DDE15A440373CA54461D53010A80",
        },
        uri: "https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/101-automation-runbook-getvms/Runbooks/Get-AzureVMTutorial.ps1",
    },
    resourceGroupName: "rg",
    runbookName: "Get-AzureVMTutorial",
    runbookType: "PowerShellWorkflow",
    tags: {
        tag01: "value01",
        tag02: "value02",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

runbook = azure_native.automation.Runbook("runbook",
    automation_account_name="ContoseAutomationAccount",
    description="Description of the Runbook",
    location="East US 2",
    log_activity_trace=1,
    log_progress=True,
    log_verbose=False,
    name="Get-AzureVMTutorial",
    publish_content_link=azure_native.automation.ContentLinkResponseArgs(
        content_hash=azure_native.automation.ContentHashArgs(
            algorithm="SHA256",
            value="115775B8FF2BE672D8A946BD0B489918C724DDE15A440373CA54461D53010A80",
        ),
        uri="https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/101-automation-runbook-getvms/Runbooks/Get-AzureVMTutorial.ps1",
    ),
    resource_group_name="rg",
    runbook_name="Get-AzureVMTutorial",
    runbook_type="PowerShellWorkflow",
    tags={
        "tag01": "value01",
        "tag02": "value02",
    })

```

```yaml
resources:
  runbook:
    type: azure-native:automation:Runbook
    properties:
      automationAccountName: ContoseAutomationAccount
      description: Description of the Runbook
      location: East US 2
      logActivityTrace: 1
      logProgress: true
      logVerbose: false
      name: Get-AzureVMTutorial
      publishContentLink:
        contentHash:
          algorithm: SHA256
          value: 115775B8FF2BE672D8A946BD0B489918C724DDE15A440373CA54461D53010A80
        uri: https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/101-automation-runbook-getvms/Runbooks/Get-AzureVMTutorial.ps1
      resourceGroupName: rg
      runbookName: Get-AzureVMTutorial
      runbookType: PowerShellWorkflow
      tags:
        tag01: value01
        tag02: value02

```

{{% /example %}}
{{% example %}}
### Create runbook as draft
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var runbook = new AzureNative.Automation.Runbook("runbook", new()
    {
        AutomationAccountName = "ContoseAutomationAccount",
        Description = "Description of the Runbook",
        Draft = null,
        Location = "East US 2",
        LogProgress = false,
        LogVerbose = false,
        Name = "Get-AzureVMTutorial",
        ResourceGroupName = "rg",
        RunbookName = "Get-AzureVMTutorial",
        RunbookType = "PowerShellWorkflow",
        Tags = 
        {
            { "tag01", "value01" },
            { "tag02", "value02" },
        },
    });

});


```

```go
package main

import (
	automation "github.com/pulumi/pulumi-azure-native-sdk/automation"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := automation.NewRunbook(ctx, "runbook", &automation.RunbookArgs{
			AutomationAccountName: pulumi.String("ContoseAutomationAccount"),
			Description:           pulumi.String("Description of the Runbook"),
			Draft:                 nil,
			Location:              pulumi.String("East US 2"),
			LogProgress:           pulumi.Bool(false),
			LogVerbose:            pulumi.Bool(false),
			Name:                  pulumi.String("Get-AzureVMTutorial"),
			ResourceGroupName:     pulumi.String("rg"),
			RunbookName:           pulumi.String("Get-AzureVMTutorial"),
			RunbookType:           pulumi.String("PowerShellWorkflow"),
			Tags: pulumi.StringMap{
				"tag01": pulumi.String("value01"),
				"tag02": pulumi.String("value02"),
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
import com.pulumi.azurenative.automation.Runbook;
import com.pulumi.azurenative.automation.RunbookArgs;
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
        var runbook = new Runbook("runbook", RunbookArgs.builder()        
            .automationAccountName("ContoseAutomationAccount")
            .description("Description of the Runbook")
            .draft()
            .location("East US 2")
            .logProgress(false)
            .logVerbose(false)
            .name("Get-AzureVMTutorial")
            .resourceGroupName("rg")
            .runbookName("Get-AzureVMTutorial")
            .runbookType("PowerShellWorkflow")
            .tags(Map.ofEntries(
                Map.entry("tag01", "value01"),
                Map.entry("tag02", "value02")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const runbook = new azure_native.automation.Runbook("runbook", {
    automationAccountName: "ContoseAutomationAccount",
    description: "Description of the Runbook",
    draft: {},
    location: "East US 2",
    logProgress: false,
    logVerbose: false,
    name: "Get-AzureVMTutorial",
    resourceGroupName: "rg",
    runbookName: "Get-AzureVMTutorial",
    runbookType: "PowerShellWorkflow",
    tags: {
        tag01: "value01",
        tag02: "value02",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

runbook = azure_native.automation.Runbook("runbook",
    automation_account_name="ContoseAutomationAccount",
    description="Description of the Runbook",
    draft=azure_native.automation.RunbookDraftArgs(),
    location="East US 2",
    log_progress=False,
    log_verbose=False,
    name="Get-AzureVMTutorial",
    resource_group_name="rg",
    runbook_name="Get-AzureVMTutorial",
    runbook_type="PowerShellWorkflow",
    tags={
        "tag01": "value01",
        "tag02": "value02",
    })

```

```yaml
resources:
  runbook:
    type: azure-native:automation:Runbook
    properties:
      automationAccountName: ContoseAutomationAccount
      description: Description of the Runbook
      draft: {}
      location: East US 2
      logProgress: false
      logVerbose: false
      name: Get-AzureVMTutorial
      resourceGroupName: rg
      runbookName: Get-AzureVMTutorial
      runbookType: PowerShellWorkflow
      tags:
        tag01: value01
        tag02: value02

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:Runbook Get-AzureVMTutorial /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/ContoseAutomationAccount/runbooks/Get-AzureVMTutorial 
```
