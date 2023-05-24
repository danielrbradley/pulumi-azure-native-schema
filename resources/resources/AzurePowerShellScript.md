Object model for the Azure PowerShell script.
API Version: 2020-10-01.
Previous API Version: 2020-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DeploymentScriptsCreateNoUserManagedIdentity
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azurePowerShellScript = new AzureNative.Resources.AzurePowerShellScript("azurePowerShellScript", new()
    {
        Arguments = "-Location 'westus' -Name \"*rg2\"",
        AzPowerShellVersion = "1.7.0",
        CleanupPreference = "Always",
        Kind = "AzurePowerShell",
        Location = "westus",
        ResourceGroupName = "script-rg",
        RetentionInterval = "PT7D",
        ScriptContent = "Param([string]$Location,[string]$Name) $deploymentScriptOutputs['test'] = 'value' Get-AzResourceGroup -Location $Location -Name $Name",
        ScriptName = "MyDeploymentScript",
        SupportingScriptUris = new[]
        {
            "https://uri1.to.supporting.script",
            "https://uri2.to.supporting.script",
        },
        Timeout = "PT1H",
    });

});


```

```go
package main

import (
	resources "github.com/pulumi/pulumi-azure-native-sdk/resources"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := resources.NewAzurePowerShellScript(ctx, "azurePowerShellScript", &resources.AzurePowerShellScriptArgs{
			Arguments:           pulumi.String("-Location 'westus' -Name \"*rg2\""),
			AzPowerShellVersion: pulumi.String("1.7.0"),
			CleanupPreference:   pulumi.String("Always"),
			Kind:                pulumi.String("AzurePowerShell"),
			Location:            pulumi.String("westus"),
			ResourceGroupName:   pulumi.String("script-rg"),
			RetentionInterval:   pulumi.String("PT7D"),
			ScriptContent:       pulumi.String("Param([string]$Location,[string]$Name) $deploymentScriptOutputs['test'] = 'value' Get-AzResourceGroup -Location $Location -Name $Name"),
			ScriptName:          pulumi.String("MyDeploymentScript"),
			SupportingScriptUris: pulumi.StringArray{
				pulumi.String("https://uri1.to.supporting.script"),
				pulumi.String("https://uri2.to.supporting.script"),
			},
			Timeout: pulumi.String("PT1H"),
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
import com.pulumi.azurenative.resources.AzurePowerShellScript;
import com.pulumi.azurenative.resources.AzurePowerShellScriptArgs;
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
        var azurePowerShellScript = new AzurePowerShellScript("azurePowerShellScript", AzurePowerShellScriptArgs.builder()        
            .arguments("-Location 'westus' -Name \"*rg2\"")
            .azPowerShellVersion("1.7.0")
            .cleanupPreference("Always")
            .kind("AzurePowerShell")
            .location("westus")
            .resourceGroupName("script-rg")
            .retentionInterval("PT7D")
            .scriptContent("Param([string]$Location,[string]$Name) $deploymentScriptOutputs['test'] = 'value' Get-AzResourceGroup -Location $Location -Name $Name")
            .scriptName("MyDeploymentScript")
            .supportingScriptUris(            
                "https://uri1.to.supporting.script",
                "https://uri2.to.supporting.script")
            .timeout("PT1H")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azurePowerShellScript = new azure_native.resources.AzurePowerShellScript("azurePowerShellScript", {
    arguments: "-Location 'westus' -Name \"*rg2\"",
    azPowerShellVersion: "1.7.0",
    cleanupPreference: "Always",
    kind: "AzurePowerShell",
    location: "westus",
    resourceGroupName: "script-rg",
    retentionInterval: "PT7D",
    scriptContent: "Param([string]$Location,[string]$Name) $deploymentScriptOutputs['test'] = 'value' Get-AzResourceGroup -Location $Location -Name $Name",
    scriptName: "MyDeploymentScript",
    supportingScriptUris: [
        "https://uri1.to.supporting.script",
        "https://uri2.to.supporting.script",
    ],
    timeout: "PT1H",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_power_shell_script = azure_native.resources.AzurePowerShellScript("azurePowerShellScript",
    arguments="-Location 'westus' -Name \"*rg2\"",
    az_power_shell_version="1.7.0",
    cleanup_preference="Always",
    kind="AzurePowerShell",
    location="westus",
    resource_group_name="script-rg",
    retention_interval="PT7D",
    script_content="Param([string]$Location,[string]$Name) $deploymentScriptOutputs['test'] = 'value' Get-AzResourceGroup -Location $Location -Name $Name",
    script_name="MyDeploymentScript",
    supporting_script_uris=[
        "https://uri1.to.supporting.script",
        "https://uri2.to.supporting.script",
    ],
    timeout="PT1H")

```

```yaml
resources:
  azurePowerShellScript:
    type: azure-native:resources:AzurePowerShellScript
    properties:
      arguments: -Location 'westus' -Name "*rg2"
      azPowerShellVersion: 1.7.0
      cleanupPreference: Always
      kind: AzurePowerShell
      location: westus
      resourceGroupName: script-rg
      retentionInterval: PT7D
      scriptContent: Param([string]$Location,[string]$Name) $deploymentScriptOutputs['test'] = 'value' Get-AzResourceGroup -Location $Location -Name $Name
      scriptName: MyDeploymentScript
      supportingScriptUris:
        - https://uri1.to.supporting.script
        - https://uri2.to.supporting.script
      timeout: PT1H

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:resources:AzurePowerShellScript myresource1 /subscriptions/{subscriptionId}/resourcegroups/{resourceGroupName}/providers/Microsoft.Resources/deploymentScripts/{scriptName} 
```
