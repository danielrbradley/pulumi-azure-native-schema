Definition of the source control.
API Version: 2022-08-08.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a source control
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sourceControl = new AzureNative.Automation.SourceControl("sourceControl", new()
    {
        AutoSync = true,
        AutomationAccountName = "sampleAccount9",
        Branch = "master",
        Description = "my description",
        FolderPath = "/folderOne/folderTwo",
        PublishRunbook = true,
        RepoUrl = "https://sampleUser.visualstudio.com/myProject/_git/myRepository",
        ResourceGroupName = "rg",
        SecurityToken = new AzureNative.Automation.Inputs.SourceControlSecurityTokenPropertiesArgs
        {
            AccessToken = "******",
            TokenType = "PersonalAccessToken",
        },
        SourceControlName = "sampleSourceControl",
        SourceType = "VsoGit",
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
		_, err := automation.NewSourceControl(ctx, "sourceControl", &automation.SourceControlArgs{
			AutoSync:              pulumi.Bool(true),
			AutomationAccountName: pulumi.String("sampleAccount9"),
			Branch:                pulumi.String("master"),
			Description:           pulumi.String("my description"),
			FolderPath:            pulumi.String("/folderOne/folderTwo"),
			PublishRunbook:        pulumi.Bool(true),
			RepoUrl:               pulumi.String("https://sampleUser.visualstudio.com/myProject/_git/myRepository"),
			ResourceGroupName:     pulumi.String("rg"),
			SecurityToken: &automation.SourceControlSecurityTokenPropertiesArgs{
				AccessToken: pulumi.String("******"),
				TokenType:   pulumi.String("PersonalAccessToken"),
			},
			SourceControlName: pulumi.String("sampleSourceControl"),
			SourceType:        pulumi.String("VsoGit"),
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
import com.pulumi.azurenative.automation.SourceControl;
import com.pulumi.azurenative.automation.SourceControlArgs;
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
        var sourceControl = new SourceControl("sourceControl", SourceControlArgs.builder()        
            .autoSync(true)
            .automationAccountName("sampleAccount9")
            .branch("master")
            .description("my description")
            .folderPath("/folderOne/folderTwo")
            .publishRunbook(true)
            .repoUrl("https://sampleUser.visualstudio.com/myProject/_git/myRepository")
            .resourceGroupName("rg")
            .securityToken(Map.ofEntries(
                Map.entry("accessToken", "******"),
                Map.entry("tokenType", "PersonalAccessToken")
            ))
            .sourceControlName("sampleSourceControl")
            .sourceType("VsoGit")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sourceControl = new azure_native.automation.SourceControl("sourceControl", {
    autoSync: true,
    automationAccountName: "sampleAccount9",
    branch: "master",
    description: "my description",
    folderPath: "/folderOne/folderTwo",
    publishRunbook: true,
    repoUrl: "https://sampleUser.visualstudio.com/myProject/_git/myRepository",
    resourceGroupName: "rg",
    securityToken: {
        accessToken: "******",
        tokenType: "PersonalAccessToken",
    },
    sourceControlName: "sampleSourceControl",
    sourceType: "VsoGit",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

source_control = azure_native.automation.SourceControl("sourceControl",
    auto_sync=True,
    automation_account_name="sampleAccount9",
    branch="master",
    description="my description",
    folder_path="/folderOne/folderTwo",
    publish_runbook=True,
    repo_url="https://sampleUser.visualstudio.com/myProject/_git/myRepository",
    resource_group_name="rg",
    security_token=azure_native.automation.SourceControlSecurityTokenPropertiesArgs(
        access_token="******",
        token_type="PersonalAccessToken",
    ),
    source_control_name="sampleSourceControl",
    source_type="VsoGit")

```

```yaml
resources:
  sourceControl:
    type: azure-native:automation:SourceControl
    properties:
      autoSync: true
      automationAccountName: sampleAccount9
      branch: master
      description: my description
      folderPath: /folderOne/folderTwo
      publishRunbook: true
      repoUrl: https://sampleUser.visualstudio.com/myProject/_git/myRepository
      resourceGroupName: rg
      securityToken:
        accessToken: '******'
        tokenType: PersonalAccessToken
      sourceControlName: sampleSourceControl
      sourceType: VsoGit

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:SourceControl sampleSourceControl /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/sampleAccount9/sourcecontrols/sampleSourceControl 
```
