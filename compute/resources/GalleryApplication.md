Specifies information about the gallery Application Definition that you want to create or update.
API Version: 2022-03-03.
Previous API Version: 2020-09-30. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a simple gallery Application.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var galleryApplication = new AzureNative.Compute.GalleryApplication("galleryApplication", new()
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
        Description = "This is the gallery application description.",
        Eula = "This is the gallery application EULA.",
        GalleryApplicationName = "myGalleryApplicationName",
        GalleryName = "myGalleryName",
        Location = "West US",
        PrivacyStatementUri = "myPrivacyStatementUri}",
        ReleaseNoteUri = "myReleaseNoteUri",
        ResourceGroupName = "myResourceGroup",
        SupportedOSType = AzureNative.Compute.OperatingSystemTypes.Windows,
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewGalleryApplication(ctx, "galleryApplication", &compute.GalleryApplicationArgs{
			CustomActions: []compute.GalleryApplicationCustomActionArgs{
				{
					Description: pulumi.String("This is the custom action description."),
					Name:        pulumi.String("myCustomAction"),
					Parameters: compute.GalleryApplicationCustomActionParameterArray{
						{
							DefaultValue: pulumi.String("default value of parameter."),
							Description:  pulumi.String("This is the description of the parameter"),
							Name:         pulumi.String("myCustomActionParameter"),
							Required:     pulumi.Bool(false),
							Type:         compute.GalleryApplicationCustomActionParameterTypeString,
						},
					},
					Script: pulumi.String("myCustomActionScript"),
				},
			},
			Description:            pulumi.String("This is the gallery application description."),
			Eula:                   pulumi.String("This is the gallery application EULA."),
			GalleryApplicationName: pulumi.String("myGalleryApplicationName"),
			GalleryName:            pulumi.String("myGalleryName"),
			Location:               pulumi.String("West US"),
			PrivacyStatementUri:    pulumi.String("myPrivacyStatementUri}"),
			ReleaseNoteUri:         pulumi.String("myReleaseNoteUri"),
			ResourceGroupName:      pulumi.String("myResourceGroup"),
			SupportedOSType:        compute.OperatingSystemTypesWindows,
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
import com.pulumi.azurenative.compute.GalleryApplication;
import com.pulumi.azurenative.compute.GalleryApplicationArgs;
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
        var galleryApplication = new GalleryApplication("galleryApplication", GalleryApplicationArgs.builder()        
            .customActions(Map.ofEntries(
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
            ))
            .description("This is the gallery application description.")
            .eula("This is the gallery application EULA.")
            .galleryApplicationName("myGalleryApplicationName")
            .galleryName("myGalleryName")
            .location("West US")
            .privacyStatementUri("myPrivacyStatementUri}")
            .releaseNoteUri("myReleaseNoteUri")
            .resourceGroupName("myResourceGroup")
            .supportedOSType("Windows")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const galleryApplication = new azure_native.compute.GalleryApplication("galleryApplication", {
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
    description: "This is the gallery application description.",
    eula: "This is the gallery application EULA.",
    galleryApplicationName: "myGalleryApplicationName",
    galleryName: "myGalleryName",
    location: "West US",
    privacyStatementUri: "myPrivacyStatementUri}",
    releaseNoteUri: "myReleaseNoteUri",
    resourceGroupName: "myResourceGroup",
    supportedOSType: azure_native.compute.OperatingSystemTypes.Windows,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery_application = azure_native.compute.GalleryApplication("galleryApplication",
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
    description="This is the gallery application description.",
    eula="This is the gallery application EULA.",
    gallery_application_name="myGalleryApplicationName",
    gallery_name="myGalleryName",
    location="West US",
    privacy_statement_uri="myPrivacyStatementUri}",
    release_note_uri="myReleaseNoteUri",
    resource_group_name="myResourceGroup",
    supported_os_type=azure_native.compute.OperatingSystemTypes.WINDOWS)

```

```yaml
resources:
  galleryApplication:
    type: azure-native:compute:GalleryApplication
    properties:
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
      description: This is the gallery application description.
      eula: This is the gallery application EULA.
      galleryApplicationName: myGalleryApplicationName
      galleryName: myGalleryName
      location: West US
      privacyStatementUri: myPrivacyStatementUri}
      releaseNoteUri: myReleaseNoteUri
      resourceGroupName: myResourceGroup
      supportedOSType: Windows

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:GalleryApplication myGalleryApplicationName /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/myGalleryName/applications/myGalleryApplicationName 
```
