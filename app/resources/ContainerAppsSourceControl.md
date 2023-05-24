Container App SourceControl.
API Version: 2022-10-01.
Previous API Version: 2022-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update Container App SourceControl
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var containerAppsSourceControl = new AzureNative.App.ContainerAppsSourceControl("containerAppsSourceControl", new()
    {
        Branch = "master",
        ContainerAppName = "testcanadacentral",
        GithubActionConfiguration = new AzureNative.App.Inputs.GithubActionConfigurationArgs
        {
            AzureCredentials = new AzureNative.App.Inputs.AzureCredentialsArgs
            {
                ClientId = "<clientid>",
                ClientSecret = "<clientsecret>",
                TenantId = "<tenantid>",
            },
            ContextPath = "./",
            Image = "image/tag",
            RegistryInfo = new AzureNative.App.Inputs.RegistryInfoArgs
            {
                RegistryPassword = "<registrypassword>",
                RegistryUrl = "xwang971reg.azurecr.io",
                RegistryUserName = "xwang971reg",
            },
        },
        RepoUrl = "https://github.com/xwang971/ghatest",
        ResourceGroupName = "workerapps-rg-xj",
        SourceControlName = "current",
    });

});


```

```go
package main

import (
	app "github.com/pulumi/pulumi-azure-native-sdk/app"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := app.NewContainerAppsSourceControl(ctx, "containerAppsSourceControl", &app.ContainerAppsSourceControlArgs{
			Branch:           pulumi.String("master"),
			ContainerAppName: pulumi.String("testcanadacentral"),
			GithubActionConfiguration: app.GithubActionConfigurationResponse{
				AzureCredentials: &app.AzureCredentialsArgs{
					ClientId:     pulumi.String("<clientid>"),
					ClientSecret: pulumi.String("<clientsecret>"),
					TenantId:     pulumi.String("<tenantid>"),
				},
				ContextPath: pulumi.String("./"),
				Image:       pulumi.String("image/tag"),
				RegistryInfo: &app.RegistryInfoArgs{
					RegistryPassword: pulumi.String("<registrypassword>"),
					RegistryUrl:      pulumi.String("xwang971reg.azurecr.io"),
					RegistryUserName: pulumi.String("xwang971reg"),
				},
			},
			RepoUrl:           pulumi.String("https://github.com/xwang971/ghatest"),
			ResourceGroupName: pulumi.String("workerapps-rg-xj"),
			SourceControlName: pulumi.String("current"),
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
import com.pulumi.azurenative.app.ContainerAppsSourceControl;
import com.pulumi.azurenative.app.ContainerAppsSourceControlArgs;
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
        var containerAppsSourceControl = new ContainerAppsSourceControl("containerAppsSourceControl", ContainerAppsSourceControlArgs.builder()        
            .branch("master")
            .containerAppName("testcanadacentral")
            .githubActionConfiguration(Map.ofEntries(
                Map.entry("azureCredentials", Map.ofEntries(
                    Map.entry("clientId", "<clientid>"),
                    Map.entry("clientSecret", "<clientsecret>"),
                    Map.entry("tenantId", "<tenantid>")
                )),
                Map.entry("contextPath", "./"),
                Map.entry("image", "image/tag"),
                Map.entry("registryInfo", Map.ofEntries(
                    Map.entry("registryPassword", "<registrypassword>"),
                    Map.entry("registryUrl", "xwang971reg.azurecr.io"),
                    Map.entry("registryUserName", "xwang971reg")
                ))
            ))
            .repoUrl("https://github.com/xwang971/ghatest")
            .resourceGroupName("workerapps-rg-xj")
            .sourceControlName("current")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const containerAppsSourceControl = new azure_native.app.ContainerAppsSourceControl("containerAppsSourceControl", {
    branch: "master",
    containerAppName: "testcanadacentral",
    githubActionConfiguration: {
        azureCredentials: {
            clientId: "<clientid>",
            clientSecret: "<clientsecret>",
            tenantId: "<tenantid>",
        },
        contextPath: "./",
        image: "image/tag",
        registryInfo: {
            registryPassword: "<registrypassword>",
            registryUrl: "xwang971reg.azurecr.io",
            registryUserName: "xwang971reg",
        },
    },
    repoUrl: "https://github.com/xwang971/ghatest",
    resourceGroupName: "workerapps-rg-xj",
    sourceControlName: "current",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

container_apps_source_control = azure_native.app.ContainerAppsSourceControl("containerAppsSourceControl",
    branch="master",
    container_app_name="testcanadacentral",
    github_action_configuration=azure_native.app.GithubActionConfigurationResponseArgs(
        azure_credentials=azure_native.app.AzureCredentialsArgs(
            client_id="<clientid>",
            client_secret="<clientsecret>",
            tenant_id="<tenantid>",
        ),
        context_path="./",
        image="image/tag",
        registry_info=azure_native.app.RegistryInfoArgs(
            registry_password="<registrypassword>",
            registry_url="xwang971reg.azurecr.io",
            registry_user_name="xwang971reg",
        ),
    ),
    repo_url="https://github.com/xwang971/ghatest",
    resource_group_name="workerapps-rg-xj",
    source_control_name="current")

```

```yaml
resources:
  containerAppsSourceControl:
    type: azure-native:app:ContainerAppsSourceControl
    properties:
      branch: master
      containerAppName: testcanadacentral
      githubActionConfiguration:
        azureCredentials:
          clientId: <clientid>
          clientSecret: <clientsecret>
          tenantId: <tenantid>
        contextPath: ./
        image: image/tag
        registryInfo:
          registryPassword: <registrypassword>
          registryUrl: xwang971reg.azurecr.io
          registryUserName: xwang971reg
      repoUrl: https://github.com/xwang971/ghatest
      resourceGroupName: workerapps-rg-xj
      sourceControlName: current

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:app:ContainerAppsSourceControl current /subscriptions/651f8027-33e8-4ec4-97b4-f6e9f3dc8744/resourceGroups/workerapps-rg-xj/providers/Microsoft.App/containerApps/myapp/sourcecontrols/current 
```
