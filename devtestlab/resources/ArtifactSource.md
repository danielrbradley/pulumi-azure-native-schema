Properties of an artifact source.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ArtifactSources_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var artifactSource = new AzureNative.DevTestLab.ArtifactSource("artifactSource", new()
    {
        ArmTemplateFolderPath = "{armTemplateFolderPath}",
        BranchRef = "{branchRef}",
        DisplayName = "{displayName}",
        FolderPath = "{folderPath}",
        LabName = "{labName}",
        Name = "{artifactSourceName}",
        ResourceGroupName = "resourceGroupName",
        SecurityToken = "{securityToken}",
        SourceType = "{VsoGit|GitHub|StorageAccount}",
        Status = "{Enabled|Disabled}",
        Tags = 
        {
            { "tagName1", "tagValue1" },
        },
        Uri = "{artifactSourceUri}",
    });

});


```

```go
package main

import (
	devtestlab "github.com/pulumi/pulumi-azure-native-sdk/devtestlab"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devtestlab.NewArtifactSource(ctx, "artifactSource", &devtestlab.ArtifactSourceArgs{
			ArmTemplateFolderPath: pulumi.String("{armTemplateFolderPath}"),
			BranchRef:             pulumi.String("{branchRef}"),
			DisplayName:           pulumi.String("{displayName}"),
			FolderPath:            pulumi.String("{folderPath}"),
			LabName:               pulumi.String("{labName}"),
			Name:                  pulumi.String("{artifactSourceName}"),
			ResourceGroupName:     pulumi.String("resourceGroupName"),
			SecurityToken:         pulumi.String("{securityToken}"),
			SourceType:            pulumi.String("{VsoGit|GitHub|StorageAccount}"),
			Status:                pulumi.String("{Enabled|Disabled}"),
			Tags: pulumi.StringMap{
				"tagName1": pulumi.String("tagValue1"),
			},
			Uri: pulumi.String("{artifactSourceUri}"),
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
import com.pulumi.azurenative.devtestlab.ArtifactSource;
import com.pulumi.azurenative.devtestlab.ArtifactSourceArgs;
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
        var artifactSource = new ArtifactSource("artifactSource", ArtifactSourceArgs.builder()        
            .armTemplateFolderPath("{armTemplateFolderPath}")
            .branchRef("{branchRef}")
            .displayName("{displayName}")
            .folderPath("{folderPath}")
            .labName("{labName}")
            .name("{artifactSourceName}")
            .resourceGroupName("resourceGroupName")
            .securityToken("{securityToken}")
            .sourceType("{VsoGit|GitHub|StorageAccount}")
            .status("{Enabled|Disabled}")
            .tags(Map.of("tagName1", "tagValue1"))
            .uri("{artifactSourceUri}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const artifactSource = new azure_native.devtestlab.ArtifactSource("artifactSource", {
    armTemplateFolderPath: "{armTemplateFolderPath}",
    branchRef: "{branchRef}",
    displayName: "{displayName}",
    folderPath: "{folderPath}",
    labName: "{labName}",
    name: "{artifactSourceName}",
    resourceGroupName: "resourceGroupName",
    securityToken: "{securityToken}",
    sourceType: "{VsoGit|GitHub|StorageAccount}",
    status: "{Enabled|Disabled}",
    tags: {
        tagName1: "tagValue1",
    },
    uri: "{artifactSourceUri}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

artifact_source = azure_native.devtestlab.ArtifactSource("artifactSource",
    arm_template_folder_path="{armTemplateFolderPath}",
    branch_ref="{branchRef}",
    display_name="{displayName}",
    folder_path="{folderPath}",
    lab_name="{labName}",
    name="{artifactSourceName}",
    resource_group_name="resourceGroupName",
    security_token="{securityToken}",
    source_type="{VsoGit|GitHub|StorageAccount}",
    status="{Enabled|Disabled}",
    tags={
        "tagName1": "tagValue1",
    },
    uri="{artifactSourceUri}")

```

```yaml
resources:
  artifactSource:
    type: azure-native:devtestlab:ArtifactSource
    properties:
      armTemplateFolderPath: '{armTemplateFolderPath}'
      branchRef: '{branchRef}'
      displayName: '{displayName}'
      folderPath: '{folderPath}'
      labName: '{labName}'
      name: '{artifactSourceName}'
      resourceGroupName: resourceGroupName
      securityToken: '{securityToken}'
      sourceType: '{VsoGit|GitHub|StorageAccount}'
      status: '{Enabled|Disabled}'
      tags:
        tagName1: tagValue1
      uri: '{artifactSourceUri}'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:ArtifactSource {artifactSourceName} /subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/artifactsources/{artifactSourceName} 
```
