Definition of the configuration type.
API Version: 2022-08-08.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update Configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dscConfiguration = new AzureNative.Automation.DscConfiguration("dscConfiguration", new()
    {
        AutomationAccountName = "myAutomationAccount18",
        ConfigurationName = "SetupServer",
        Description = "sample configuration",
        Location = "East US 2",
        Name = "SetupServer",
        ResourceGroupName = "rg",
        Source = new AzureNative.Automation.Inputs.ContentSourceArgs
        {
            Hash = new AzureNative.Automation.Inputs.ContentHashArgs
            {
                Algorithm = "sha256",
                Value = "A9E5DB56BA21513F61E0B3868816FDC6D4DF5131F5617D7FF0D769674BD5072F",
            },
            Type = "embeddedContent",
            Value = @"Configuration SetupServer {
    Node localhost {
                               WindowsFeature IIS {
                               Name = ""Web-Server"";
            Ensure = ""Present""
        }
    }
}",
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
		_, err := automation.NewDscConfiguration(ctx, "dscConfiguration", &automation.DscConfigurationArgs{
			AutomationAccountName: pulumi.String("myAutomationAccount18"),
			ConfigurationName:     pulumi.String("SetupServer"),
			Description:           pulumi.String("sample configuration"),
			Location:              pulumi.String("East US 2"),
			Name:                  pulumi.String("SetupServer"),
			ResourceGroupName:     pulumi.String("rg"),
			Source: automation.ContentSourceResponse{
				Hash: &automation.ContentHashArgs{
					Algorithm: pulumi.String("sha256"),
					Value:     pulumi.String("A9E5DB56BA21513F61E0B3868816FDC6D4DF5131F5617D7FF0D769674BD5072F"),
				},
				Type:  pulumi.String("embeddedContent"),
				Value: pulumi.String("Configuration SetupServer {\n    Node localhost {\n                               WindowsFeature IIS {\n                               Name = \"Web-Server\";\n            Ensure = \"Present\"\n        }\n    }\n}"),
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
import com.pulumi.azurenative.automation.DscConfiguration;
import com.pulumi.azurenative.automation.DscConfigurationArgs;
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
        var dscConfiguration = new DscConfiguration("dscConfiguration", DscConfigurationArgs.builder()        
            .automationAccountName("myAutomationAccount18")
            .configurationName("SetupServer")
            .description("sample configuration")
            .location("East US 2")
            .name("SetupServer")
            .resourceGroupName("rg")
            .source(Map.ofEntries(
                Map.entry("hash", Map.ofEntries(
                    Map.entry("algorithm", "sha256"),
                    Map.entry("value", "A9E5DB56BA21513F61E0B3868816FDC6D4DF5131F5617D7FF0D769674BD5072F")
                )),
                Map.entry("type", "embeddedContent"),
                Map.entry("value", """
Configuration SetupServer {
    Node localhost {
                               WindowsFeature IIS {
                               Name = "Web-Server";
            Ensure = "Present"
        }
    }
}                """)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dscConfiguration = new azure_native.automation.DscConfiguration("dscConfiguration", {
    automationAccountName: "myAutomationAccount18",
    configurationName: "SetupServer",
    description: "sample configuration",
    location: "East US 2",
    name: "SetupServer",
    resourceGroupName: "rg",
    source: {
        hash: {
            algorithm: "sha256",
            value: "A9E5DB56BA21513F61E0B3868816FDC6D4DF5131F5617D7FF0D769674BD5072F",
        },
        type: "embeddedContent",
        value: `Configuration SetupServer {
    Node localhost {
                               WindowsFeature IIS {
                               Name = "Web-Server";
            Ensure = "Present"
        }
    }
}`,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dsc_configuration = azure_native.automation.DscConfiguration("dscConfiguration",
    automation_account_name="myAutomationAccount18",
    configuration_name="SetupServer",
    description="sample configuration",
    location="East US 2",
    name="SetupServer",
    resource_group_name="rg",
    source=azure_native.automation.ContentSourceResponseArgs(
        hash=azure_native.automation.ContentHashArgs(
            algorithm="sha256",
            value="A9E5DB56BA21513F61E0B3868816FDC6D4DF5131F5617D7FF0D769674BD5072F",
        ),
        type="embeddedContent",
        value="""Configuration SetupServer {
    Node localhost {
                               WindowsFeature IIS {
                               Name = "Web-Server";
            Ensure = "Present"
        }
    }
}""",
    ))

```

```yaml
resources:
  dscConfiguration:
    type: azure-native:automation:DscConfiguration
    properties:
      automationAccountName: myAutomationAccount18
      configurationName: SetupServer
      description: sample configuration
      location: East US 2
      name: SetupServer
      resourceGroupName: rg
      source:
        hash:
          algorithm: sha256
          value: A9E5DB56BA21513F61E0B3868816FDC6D4DF5131F5617D7FF0D769674BD5072F
        type: embeddedContent
        value: "Configuration SetupServer {\r\n    Node localhost {\r\n                               WindowsFeature IIS {\r\n                               Name = \"Web-Server\";\r\n            Ensure = \"Present\"\r\n        }\r\n    }\r\n}"

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:DscConfiguration SetupServer /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/myAutomationAccount33/configurations/SetupServer 
```
