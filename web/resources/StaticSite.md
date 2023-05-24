Static Site ARM resource.
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a static site
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var staticSite = new AzureNative.Web.StaticSite("staticSite", new()
    {
        Branch = "master",
        BuildProperties = new AzureNative.Web.Inputs.StaticSiteBuildPropertiesArgs
        {
            ApiLocation = "api",
            AppArtifactLocation = "build",
            AppLocation = "app",
        },
        Location = "West US 2",
        Name = "testStaticSite0",
        RepositoryToken = "repoToken123",
        RepositoryUrl = "https://github.com/username/RepoName",
        ResourceGroupName = "rg",
        Sku = new AzureNative.Web.Inputs.SkuDescriptionArgs
        {
            Name = "Basic",
            Tier = "Basic",
        },
    });

});


```

```go
package main

import (
	web "github.com/pulumi/pulumi-azure-native-sdk/web"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := web.NewStaticSite(ctx, "staticSite", &web.StaticSiteArgs{
			Branch: pulumi.String("master"),
			BuildProperties: &web.StaticSiteBuildPropertiesArgs{
				ApiLocation:         pulumi.String("api"),
				AppArtifactLocation: pulumi.String("build"),
				AppLocation:         pulumi.String("app"),
			},
			Location:          pulumi.String("West US 2"),
			Name:              pulumi.String("testStaticSite0"),
			RepositoryToken:   pulumi.String("repoToken123"),
			RepositoryUrl:     pulumi.String("https://github.com/username/RepoName"),
			ResourceGroupName: pulumi.String("rg"),
			Sku: &web.SkuDescriptionArgs{
				Name: pulumi.String("Basic"),
				Tier: pulumi.String("Basic"),
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
import com.pulumi.azurenative.web.StaticSite;
import com.pulumi.azurenative.web.StaticSiteArgs;
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
        var staticSite = new StaticSite("staticSite", StaticSiteArgs.builder()        
            .branch("master")
            .buildProperties(Map.ofEntries(
                Map.entry("apiLocation", "api"),
                Map.entry("appArtifactLocation", "build"),
                Map.entry("appLocation", "app")
            ))
            .location("West US 2")
            .name("testStaticSite0")
            .repositoryToken("repoToken123")
            .repositoryUrl("https://github.com/username/RepoName")
            .resourceGroupName("rg")
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Basic")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const staticSite = new azure_native.web.StaticSite("staticSite", {
    branch: "master",
    buildProperties: {
        apiLocation: "api",
        appArtifactLocation: "build",
        appLocation: "app",
    },
    location: "West US 2",
    name: "testStaticSite0",
    repositoryToken: "repoToken123",
    repositoryUrl: "https://github.com/username/RepoName",
    resourceGroupName: "rg",
    sku: {
        name: "Basic",
        tier: "Basic",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

static_site = azure_native.web.StaticSite("staticSite",
    branch="master",
    build_properties=azure_native.web.StaticSiteBuildPropertiesArgs(
        api_location="api",
        app_artifact_location="build",
        app_location="app",
    ),
    location="West US 2",
    name="testStaticSite0",
    repository_token="repoToken123",
    repository_url="https://github.com/username/RepoName",
    resource_group_name="rg",
    sku=azure_native.web.SkuDescriptionArgs(
        name="Basic",
        tier="Basic",
    ))

```

```yaml
resources:
  staticSite:
    type: azure-native:web:StaticSite
    properties:
      branch: master
      buildProperties:
        apiLocation: api
        appArtifactLocation: build
        appLocation: app
      location: West US 2
      name: testStaticSite0
      repositoryToken: repoToken123
      repositoryUrl: https://github.com/username/RepoName
      resourceGroupName: rg
      sku:
        name: Basic
        tier: Basic

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:StaticSite testStaticSite0 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.Web/staticSites/testStaticSite0 
```
