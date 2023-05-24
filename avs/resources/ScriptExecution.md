An instance of a script executed by a user - custom or AVS
API Version: 2022-05-01.
Previous API Version: 2021-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ScriptExecutions_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scriptExecution = new AzureNative.AVS.ScriptExecution("scriptExecution", new()
    {
        HiddenParameters = new[]
        {
            new AzureNative.AVS.Inputs.ScriptSecureStringExecutionParameterArgs
            {
                Name = "Password",
                SecureValue = "PlaceholderPassword",
                Type = "SecureValue",
            },
        },
        Parameters = new[]
        {
            new AzureNative.AVS.Inputs.ScriptStringExecutionParameterArgs
            {
                Name = "DomainName",
                Type = "Value",
                Value = "placeholderDomain.local",
            },
            new AzureNative.AVS.Inputs.ScriptStringExecutionParameterArgs
            {
                Name = "BaseUserDN",
                Type = "Value",
                Value = "DC=placeholder, DC=placeholder",
            },
        },
        PrivateCloudName = "cloud1",
        ResourceGroupName = "group1",
        Retention = "P0Y0M60DT0H60M60S",
        ScriptCmdletId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/scriptPackages/AVS.PowerCommands@1.0.0/scriptCmdlets/New-SsoExternalIdentitySource",
        ScriptExecutionName = "addSsoServer",
        Timeout = "P0Y0M0DT0H60M60S",
    });

});


```

```go
package main

import (
	avs "github.com/pulumi/pulumi-azure-native-sdk/avs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := avs.NewScriptExecution(ctx, "scriptExecution", &avs.ScriptExecutionArgs{
			HiddenParameters: pulumi.AnyArray{
				avs.ScriptSecureStringExecutionParameter{
					Name:        "Password",
					SecureValue: "PlaceholderPassword",
					Type:        "SecureValue",
				},
			},
			Parameters: pulumi.AnyArray{
				avs.ScriptStringExecutionParameter{
					Name:  "DomainName",
					Type:  "Value",
					Value: "placeholderDomain.local",
				},
				avs.ScriptStringExecutionParameter{
					Name:  "BaseUserDN",
					Type:  "Value",
					Value: "DC=placeholder, DC=placeholder",
				},
			},
			PrivateCloudName:    pulumi.String("cloud1"),
			ResourceGroupName:   pulumi.String("group1"),
			Retention:           pulumi.String("P0Y0M60DT0H60M60S"),
			ScriptCmdletId:      pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/scriptPackages/AVS.PowerCommands@1.0.0/scriptCmdlets/New-SsoExternalIdentitySource"),
			ScriptExecutionName: pulumi.String("addSsoServer"),
			Timeout:             pulumi.String("P0Y0M0DT0H60M60S"),
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
import com.pulumi.azurenative.avs.ScriptExecution;
import com.pulumi.azurenative.avs.ScriptExecutionArgs;
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
        var scriptExecution = new ScriptExecution("scriptExecution", ScriptExecutionArgs.builder()        
            .hiddenParameters(Map.ofEntries(
                Map.entry("name", "Password"),
                Map.entry("secureValue", "PlaceholderPassword"),
                Map.entry("type", "SecureValue")
            ))
            .parameters(            
                Map.ofEntries(
                    Map.entry("name", "DomainName"),
                    Map.entry("type", "Value"),
                    Map.entry("value", "placeholderDomain.local")
                ),
                Map.ofEntries(
                    Map.entry("name", "BaseUserDN"),
                    Map.entry("type", "Value"),
                    Map.entry("value", "DC=placeholder, DC=placeholder")
                ))
            .privateCloudName("cloud1")
            .resourceGroupName("group1")
            .retention("P0Y0M60DT0H60M60S")
            .scriptCmdletId("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/scriptPackages/AVS.PowerCommands@1.0.0/scriptCmdlets/New-SsoExternalIdentitySource")
            .scriptExecutionName("addSsoServer")
            .timeout("P0Y0M0DT0H60M60S")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scriptExecution = new azure_native.avs.ScriptExecution("scriptExecution", {
    hiddenParameters: [{
        name: "Password",
        secureValue: "PlaceholderPassword",
        type: "SecureValue",
    }],
    parameters: [
        {
            name: "DomainName",
            type: "Value",
            value: "placeholderDomain.local",
        },
        {
            name: "BaseUserDN",
            type: "Value",
            value: "DC=placeholder, DC=placeholder",
        },
    ],
    privateCloudName: "cloud1",
    resourceGroupName: "group1",
    retention: "P0Y0M60DT0H60M60S",
    scriptCmdletId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/scriptPackages/AVS.PowerCommands@1.0.0/scriptCmdlets/New-SsoExternalIdentitySource",
    scriptExecutionName: "addSsoServer",
    timeout: "P0Y0M0DT0H60M60S",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

script_execution = azure_native.avs.ScriptExecution("scriptExecution",
    hidden_parameters=[azure_native.avs.ScriptSecureStringExecutionParameterArgs(
        name="Password",
        secure_value="PlaceholderPassword",
        type="SecureValue",
    )],
    parameters=[
        azure_native.avs.ScriptStringExecutionParameterArgs(
            name="DomainName",
            type="Value",
            value="placeholderDomain.local",
        ),
        azure_native.avs.ScriptStringExecutionParameterArgs(
            name="BaseUserDN",
            type="Value",
            value="DC=placeholder, DC=placeholder",
        ),
    ],
    private_cloud_name="cloud1",
    resource_group_name="group1",
    retention="P0Y0M60DT0H60M60S",
    script_cmdlet_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/scriptPackages/AVS.PowerCommands@1.0.0/scriptCmdlets/New-SsoExternalIdentitySource",
    script_execution_name="addSsoServer",
    timeout="P0Y0M0DT0H60M60S")

```

```yaml
resources:
  scriptExecution:
    type: azure-native:avs:ScriptExecution
    properties:
      hiddenParameters:
        - name: Password
          secureValue: PlaceholderPassword
          type: SecureValue
      parameters:
        - name: DomainName
          type: Value
          value: placeholderDomain.local
        - name: BaseUserDN
          type: Value
          value: DC=placeholder, DC=placeholder
      privateCloudName: cloud1
      resourceGroupName: group1
      retention: P0Y0M60DT0H60M60S
      scriptCmdletId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/scriptPackages/AVS.PowerCommands@1.0.0/scriptCmdlets/New-SsoExternalIdentitySource
      scriptExecutionName: addSsoServer
      timeout: P0Y0M0DT0H60M60S

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:ScriptExecution addSsoServer /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/scriptExecutions/addSsoServer 
```
