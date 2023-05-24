Specifies information about the gallery Application Version that you want to create or update.
API Version: 2022-03-03.
Previous API Version: 2020-09-30. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a simple gallery Application Version.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var galleryApplicationVersion = new AzureNative.Compute.GalleryApplicationVersion("galleryApplicationVersion", new()
    {
        GalleryApplicationName = "myGalleryApplicationName",
        GalleryApplicationVersionName = "1.0.0",
        GalleryName = "myGalleryName",
        Location = "West US",
        PublishingProfile = new AzureNative.Compute.Inputs.GalleryApplicationVersionPublishingProfileArgs
        {
            CustomActions = new[]
            {
                new AzureNative.Compute.Inputs.GalleryApplicationCustomActionArgs
                {
                    Description = "This is the custom action description.",
                    Name = "myCustomAction",
                    Parameters = new[]
                    {
                        new AzureNative.Compute.Inputs.GalleryApplicationCustomActionParameterArgs
                        {
                            DefaultValue = "default value of parameter.",
                            Description = "This is the description of the parameter",
                            Name = "myCustomActionParameter",
                            Required = false,
                            Type = AzureNative.Compute.GalleryApplicationCustomActionParameterType.String,
                        },
                    },
                    Script = "myCustomActionScript",
                },
            },
            EndOfLifeDate = "2019-07-01T07:00:00Z",
            ManageActions = new AzureNative.Compute.Inputs.UserArtifactManageArgs
            {
                Install = "powershell -command \"Expand-Archive -Path package.zip -DestinationPath C:\\package\"",
                Remove = "del C:\\package ",
            },
            ReplicaCount = 1,
            Source = new AzureNative.Compute.Inputs.UserArtifactSourceArgs
            {
                MediaLink = "https://mystorageaccount.blob.core.windows.net/mycontainer/package.zip?{sasKey}",
            },
            StorageAccountType = "Standard_LRS",
            TargetRegions = new[]
            {
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    ExcludeFromLatest = false,
                    Name = "West US",
                    RegionalReplicaCount = 1,
                    StorageAccountType = "Standard_LRS",
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        SafetyProfile = new AzureNative.Compute.Inputs.GalleryApplicationVersionSafetyProfileArgs
        {
            AllowDeletionOfReplicatedLocations = false,
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.GalleryApplicationVersion;
import com.pulumi.azurenative.compute.GalleryApplicationVersionArgs;
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
        var galleryApplicationVersion = new GalleryApplicationVersion("galleryApplicationVersion", GalleryApplicationVersionArgs.builder()        
            .galleryApplicationName("myGalleryApplicationName")
            .galleryApplicationVersionName("1.0.0")
            .galleryName("myGalleryName")
            .location("West US")
            .publishingProfile(Map.ofEntries(
                Map.entry("customActions", Map.ofEntries(
                    Map.entry("description", "This is the custom action description."),
                    Map.entry("name", "myCustomAction"),
                    Map.entry("parameters", Map.ofEntries(
                        Map.entry("defaultValue", "default value of parameter."),
                        Map.entry("description", "This is the description of the parameter"),
                        Map.entry("name", "myCustomActionParameter"),
                        Map.entry("required", false),
                        Map.entry("type", "String")
                    )),
                    Map.entry("script", "myCustomActionScript")
                )),
                Map.entry("endOfLifeDate", "2019-07-01T07:00:00Z"),
                Map.entry("manageActions", Map.ofEntries(
                    Map.entry("install", "powershell -command \"Expand-Archive -Path package.zip -DestinationPath C:\\package\""),
                    Map.entry("remove", "del C:\\package ")
                )),
                Map.entry("replicaCount", 1),
                Map.entry("source", Map.of("mediaLink", "https://mystorageaccount.blob.core.windows.net/mycontainer/package.zip?{sasKey}")),
                Map.entry("storageAccountType", "Standard_LRS"),
                Map.entry("targetRegions", Map.ofEntries(
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "West US"),
                    Map.entry("regionalReplicaCount", 1),
                    Map.entry("storageAccountType", "Standard_LRS")
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .safetyProfile(Map.of("allowDeletionOfReplicatedLocations", false))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const galleryApplicationVersion = new azure_native.compute.GalleryApplicationVersion("galleryApplicationVersion", {
    galleryApplicationName: "myGalleryApplicationName",
    galleryApplicationVersionName: "1.0.0",
    galleryName: "myGalleryName",
    location: "West US",
    publishingProfile: {
        customActions: [{
            description: "This is the custom action description.",
            name: "myCustomAction",
            parameters: [{
                defaultValue: "default value of parameter.",
                description: "This is the description of the parameter",
                name: "myCustomActionParameter",
                required: false,
                type: azure_native.compute.GalleryApplicationCustomActionParameterType.String,
            }],
            script: "myCustomActionScript",
        }],
        endOfLifeDate: "2019-07-01T07:00:00Z",
        manageActions: {
            install: "powershell -command \"Expand-Archive -Path package.zip -DestinationPath C:\\package\"",
            remove: "del C:\\package ",
        },
        replicaCount: 1,
        source: {
            mediaLink: "https://mystorageaccount.blob.core.windows.net/mycontainer/package.zip?{sasKey}",
        },
        storageAccountType: "Standard_LRS",
        targetRegions: [{
            excludeFromLatest: false,
            name: "West US",
            regionalReplicaCount: 1,
            storageAccountType: "Standard_LRS",
        }],
    },
    resourceGroupName: "myResourceGroup",
    safetyProfile: {
        allowDeletionOfReplicatedLocations: false,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery_application_version = azure_native.compute.GalleryApplicationVersion("galleryApplicationVersion",
    gallery_application_name="myGalleryApplicationName",
    gallery_application_version_name="1.0.0",
    gallery_name="myGalleryName",
    location="West US",
    publishing_profile=azure_native.compute.GalleryApplicationVersionPublishingProfileResponseArgs(
        custom_actions=[{
            "description": "This is the custom action description.",
            "name": "myCustomAction",
            "parameters": [azure_native.compute.GalleryApplicationCustomActionParameterArgs(
                default_value="default value of parameter.",
                description="This is the description of the parameter",
                name="myCustomActionParameter",
                required=False,
                type=azure_native.compute.GalleryApplicationCustomActionParameterType.STRING,
            )],
            "script": "myCustomActionScript",
        }],
        end_of_life_date="2019-07-01T07:00:00Z",
        manage_actions=azure_native.compute.UserArtifactManageArgs(
            install="powershell -command \"Expand-Archive -Path package.zip -DestinationPath C:\\package\"",
            remove="del C:\\package ",
        ),
        replica_count=1,
        source=azure_native.compute.UserArtifactSourceArgs(
            media_link="https://mystorageaccount.blob.core.windows.net/mycontainer/package.zip?{sasKey}",
        ),
        storage_account_type="Standard_LRS",
        target_regions=[azure_native.compute.TargetRegionArgs(
            exclude_from_latest=False,
            name="West US",
            regional_replica_count=1,
            storage_account_type="Standard_LRS",
        )],
    ),
    resource_group_name="myResourceGroup",
    safety_profile=azure_native.compute.GalleryApplicationVersionSafetyProfileArgs(
        allow_deletion_of_replicated_locations=False,
    ))

```

```yaml
resources:
  galleryApplicationVersion:
    type: azure-native:compute:GalleryApplicationVersion
    properties:
      galleryApplicationName: myGalleryApplicationName
      galleryApplicationVersionName: 1.0.0
      galleryName: myGalleryName
      location: West US
      publishingProfile:
        customActions:
          - description: This is the custom action description.
            name: myCustomAction
            parameters:
              - defaultValue: default value of parameter.
                description: This is the description of the parameter
                name: myCustomActionParameter
                required: false
                type: String
            script: myCustomActionScript
        endOfLifeDate: 2019-07-01T07:00:00Z
        manageActions:
          install: powershell -command "Expand-Archive -Path package.zip -DestinationPath C:\package"
          remove: 'del C:\package '
        replicaCount: 1
        source:
          mediaLink: https://mystorageaccount.blob.core.windows.net/mycontainer/package.zip?{sasKey}
        storageAccountType: Standard_LRS
        targetRegions:
          - excludeFromLatest: false
            name: West US
            regionalReplicaCount: 1
            storageAccountType: Standard_LRS
      resourceGroupName: myResourceGroup
      safetyProfile:
        allowDeletionOfReplicatedLocations: false

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:GalleryApplicationVersion 1.0.0 /subscriptions/01523d7c-60da-455e-adef-521b547922c4/resourceGroups/galleryPsTestRg98/providers/Microsoft.Compute/galleries/galleryPsTestGallery6165/applications/galleryPsTestGalleryApplication7825/versions/1.0.0 
```
