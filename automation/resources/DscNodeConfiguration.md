Definition of the dsc node configuration.
API Version: 2022-08-08.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create node configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dscNodeConfiguration = new AzureNative.Automation.DscNodeConfiguration("dscNodeConfiguration", new()
    {
        AutomationAccountName = "myAutomationAccount20",
        Configuration = new AzureNative.Automation.Inputs.DscConfigurationAssociationPropertyArgs
        {
            Name = "configName",
        },
        IncrementNodeConfigurationBuild = true,
        Name = "configName.nodeConfigName",
        NodeConfigurationName = "configName.nodeConfigName",
        ResourceGroupName = "rg",
        Source = new AzureNative.Automation.Inputs.ContentSourceArgs
        {
            Hash = new AzureNative.Automation.Inputs.ContentHashArgs
            {
                Algorithm = "sha256",
                Value = "6DE256A57F01BFA29B88696D5E77A383D6E61484C7686E8DB955FA10ACE9FFE5",
            },
            Type = "embeddedContent",
            Value = @"
instance of MSFT_RoleResource as $MSFT_RoleResource1ref
{
ResourceID = ""[WindowsFeature]IIS"";
 Ensure = ""Present"";
 SourceInfo = ""::3::32::WindowsFeature"";
 Name = ""Web-Server"";
 ModuleName = ""PsDesiredStateConfiguration"";

ModuleVersion = ""1.0"";
 ConfigurationName = ""configName"";
};
instance of OMI_ConfigurationDocument

                    {
 Version=""2.0.0"";
 
                        MinimumCompatibleVersion = ""1.0.0"";
 
                        CompatibleVersionAdditionalProperties= {""Omi_BaseResource:ConfigurationName""};
 
                        Author=""weijiel"";
 
                        GenerationDate=""03/30/2017 13:40:25"";
 
                        GenerationHost=""TEST-BACKEND"";
 
                        Name=""configName"";

                    };
",
            Version = "1.0",
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
		_, err := automation.NewDscNodeConfiguration(ctx, "dscNodeConfiguration", &automation.DscNodeConfigurationArgs{
			AutomationAccountName: pulumi.String("myAutomationAccount20"),
			Configuration: &automation.DscConfigurationAssociationPropertyArgs{
				Name: pulumi.String("configName"),
			},
			IncrementNodeConfigurationBuild: pulumi.Bool(true),
			Name:                            pulumi.String("configName.nodeConfigName"),
			NodeConfigurationName:           pulumi.String("configName.nodeConfigName"),
			ResourceGroupName:               pulumi.String("rg"),
			Source: &automation.ContentSourceArgs{
				Hash: &automation.ContentHashArgs{
					Algorithm: pulumi.String("sha256"),
					Value:     pulumi.String("6DE256A57F01BFA29B88696D5E77A383D6E61484C7686E8DB955FA10ACE9FFE5"),
				},
				Type:    pulumi.String("embeddedContent"),
				Value:   pulumi.String("\ninstance of MSFT_RoleResource as $MSFT_RoleResource1ref\n{\nResourceID = \"[WindowsFeature]IIS\";\n Ensure = \"Present\";\n SourceInfo = \"::3::32::WindowsFeature\";\n Name = \"Web-Server\";\n ModuleName = \"PsDesiredStateConfiguration\";\n\nModuleVersion = \"1.0\";\n ConfigurationName = \"configName\";\n};\ninstance of OMI_ConfigurationDocument\n\n                    {\n Version=\"2.0.0\";\n \n                        MinimumCompatibleVersion = \"1.0.0\";\n \n                        CompatibleVersionAdditionalProperties= {\"Omi_BaseResource:ConfigurationName\"};\n \n                        Author=\"weijiel\";\n \n                        GenerationDate=\"03/30/2017 13:40:25\";\n \n                        GenerationHost=\"TEST-BACKEND\";\n \n                        Name=\"configName\";\n\n                    };\n"),
				Version: pulumi.String("1.0"),
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
import com.pulumi.azurenative.automation.DscNodeConfiguration;
import com.pulumi.azurenative.automation.DscNodeConfigurationArgs;
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
        var dscNodeConfiguration = new DscNodeConfiguration("dscNodeConfiguration", DscNodeConfigurationArgs.builder()        
            .automationAccountName("myAutomationAccount20")
            .configuration(Map.of("name", "configName"))
            .incrementNodeConfigurationBuild(true)
            .name("configName.nodeConfigName")
            .nodeConfigurationName("configName.nodeConfigName")
            .resourceGroupName("rg")
            .source(Map.ofEntries(
                Map.entry("hash", Map.ofEntries(
                    Map.entry("algorithm", "sha256"),
                    Map.entry("value", "6DE256A57F01BFA29B88696D5E77A383D6E61484C7686E8DB955FA10ACE9FFE5")
                )),
                Map.entry("type", "embeddedContent"),
                Map.entry("value", """

instance of MSFT_RoleResource as $MSFT_RoleResource1ref
{
ResourceID = "[WindowsFeature]IIS";
 Ensure = "Present";
 SourceInfo = "::3::32::WindowsFeature";
 Name = "Web-Server";
 ModuleName = "PsDesiredStateConfiguration";

ModuleVersion = "1.0";
 ConfigurationName = "configName";
};
instance of OMI_ConfigurationDocument

                    {
 Version="2.0.0";
 
                        MinimumCompatibleVersion = "1.0.0";
 
                        CompatibleVersionAdditionalProperties= {"Omi_BaseResource:ConfigurationName"};
 
                        Author="weijiel";
 
                        GenerationDate="03/30/2017 13:40:25";
 
                        GenerationHost="TEST-BACKEND";
 
                        Name="configName";

                    };
                """),
                Map.entry("version", "1.0")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dscNodeConfiguration = new azure_native.automation.DscNodeConfiguration("dscNodeConfiguration", {
    automationAccountName: "myAutomationAccount20",
    configuration: {
        name: "configName",
    },
    incrementNodeConfigurationBuild: true,
    name: "configName.nodeConfigName",
    nodeConfigurationName: "configName.nodeConfigName",
    resourceGroupName: "rg",
    source: {
        hash: {
            algorithm: "sha256",
            value: "6DE256A57F01BFA29B88696D5E77A383D6E61484C7686E8DB955FA10ACE9FFE5",
        },
        type: "embeddedContent",
        value: `
instance of MSFT_RoleResource as $MSFT_RoleResource1ref
{
ResourceID = "[WindowsFeature]IIS";
 Ensure = "Present";
 SourceInfo = "::3::32::WindowsFeature";
 Name = "Web-Server";
 ModuleName = "PsDesiredStateConfiguration";

ModuleVersion = "1.0";
 ConfigurationName = "configName";
};
instance of OMI_ConfigurationDocument

                    {
 Version="2.0.0";
 
                        MinimumCompatibleVersion = "1.0.0";
 
                        CompatibleVersionAdditionalProperties= {"Omi_BaseResource:ConfigurationName"};
 
                        Author="weijiel";
 
                        GenerationDate="03/30/2017 13:40:25";
 
                        GenerationHost="TEST-BACKEND";
 
                        Name="configName";

                    };
`,
        version: "1.0",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dsc_node_configuration = azure_native.automation.DscNodeConfiguration("dscNodeConfiguration",
    automation_account_name="myAutomationAccount20",
    configuration=azure_native.automation.DscConfigurationAssociationPropertyArgs(
        name="configName",
    ),
    increment_node_configuration_build=True,
    name="configName.nodeConfigName",
    node_configuration_name="configName.nodeConfigName",
    resource_group_name="rg",
    source=azure_native.automation.ContentSourceArgs(
        hash=azure_native.automation.ContentHashArgs(
            algorithm="sha256",
            value="6DE256A57F01BFA29B88696D5E77A383D6E61484C7686E8DB955FA10ACE9FFE5",
        ),
        type="embeddedContent",
        value="""
instance of MSFT_RoleResource as $MSFT_RoleResource1ref
{
ResourceID = "[WindowsFeature]IIS";
 Ensure = "Present";
 SourceInfo = "::3::32::WindowsFeature";
 Name = "Web-Server";
 ModuleName = "PsDesiredStateConfiguration";

ModuleVersion = "1.0";
 ConfigurationName = "configName";
};
instance of OMI_ConfigurationDocument

                    {
 Version="2.0.0";
 
                        MinimumCompatibleVersion = "1.0.0";
 
                        CompatibleVersionAdditionalProperties= {"Omi_BaseResource:ConfigurationName"};
 
                        Author="weijiel";
 
                        GenerationDate="03/30/2017 13:40:25";
 
                        GenerationHost="TEST-BACKEND";
 
                        Name="configName";

                    };
""",
        version="1.0",
    ))

```

```yaml
resources:
  dscNodeConfiguration:
    type: azure-native:automation:DscNodeConfiguration
    properties:
      automationAccountName: myAutomationAccount20
      configuration:
        name: configName
      incrementNodeConfigurationBuild: true
      name: configName.nodeConfigName
      nodeConfigurationName: configName.nodeConfigName
      resourceGroupName: rg
      source:
        hash:
          algorithm: sha256
          value: 6DE256A57F01BFA29B88696D5E77A383D6E61484C7686E8DB955FA10ACE9FFE5
        type: embeddedContent
        value: "\r\ninstance of MSFT_RoleResource as $MSFT_RoleResource1ref\r\n{\r\nResourceID = \"[WindowsFeature]IIS\";\r\n Ensure = \"Present\";\r\n SourceInfo = \"::3::32::WindowsFeature\";\r\n Name = \"Web-Server\";\r\n ModuleName = \"PsDesiredStateConfiguration\";\r\n\r\nModuleVersion = \"1.0\";\r\r\n ConfigurationName = \"configName\";\r\r\n};\r\ninstance of OMI_ConfigurationDocument\r\n\r\r\n                    {\r\n Version=\"2.0.0\";\r\n \r\r\n                        MinimumCompatibleVersion = \"1.0.0\";\r\n \r\r\n                        CompatibleVersionAdditionalProperties= {\"Omi_BaseResource:ConfigurationName\"};\r\n \r\r\n                        Author=\"weijiel\";\r\n \r\r\n                        GenerationDate=\"03/30/2017 13:40:25\";\r\n \r\r\n                        GenerationHost=\"TEST-BACKEND\";\r\n \r\r\n                        Name=\"configName\";\r\n\r\r\n                    };\r\n"
        version: '1.0'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:DscNodeConfiguration configName.nodeConfigName /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/myAutomationAccount20/nodeConfigurations/configName.nodeConfigName 
```
