The link resource format.
API Version: 2017-04-26.
Previous API Version: 2017-04-26. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Links_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var link = new AzureNative.CustomerInsights.Link("link", new()
    {
        Description = 
        {
            { "en-us", "Link Description" },
        },
        DisplayName = 
        {
            { "en-us", "Link DisplayName" },
        },
        HubName = "sdkTestHub",
        LinkName = "linkTest4806",
        Mappings = new[]
        {
            new AzureNative.CustomerInsights.Inputs.TypePropertiesMappingArgs
            {
                LinkType = AzureNative.CustomerInsights.LinkTypes.UpdateAlways,
                SourcePropertyName = "testInteraction1949",
                TargetPropertyName = "testProfile1446",
            },
        },
        ParticipantPropertyReferences = new[]
        {
            new AzureNative.CustomerInsights.Inputs.ParticipantPropertyReferenceArgs
            {
                SourcePropertyName = "testInteraction1949",
                TargetPropertyName = "ProfileId",
            },
        },
        ResourceGroupName = "TestHubRG",
        SourceEntityType = AzureNative.CustomerInsights.EntityType.Interaction,
        SourceEntityTypeName = "testInteraction1949",
        TargetEntityType = AzureNative.CustomerInsights.EntityType.Profile,
        TargetEntityTypeName = "testProfile1446",
    });

});


```

```go
package main

import (
	customerinsights "github.com/pulumi/pulumi-azure-native-sdk/customerinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := customerinsights.NewLink(ctx, "link", &customerinsights.LinkArgs{
			Description: pulumi.StringMap{
				"en-us": pulumi.String("Link Description"),
			},
			DisplayName: pulumi.StringMap{
				"en-us": pulumi.String("Link DisplayName"),
			},
			HubName:  pulumi.String("sdkTestHub"),
			LinkName: pulumi.String("linkTest4806"),
			Mappings: []customerinsights.TypePropertiesMappingArgs{
				{
					LinkType:           customerinsights.LinkTypesUpdateAlways,
					SourcePropertyName: pulumi.String("testInteraction1949"),
					TargetPropertyName: pulumi.String("testProfile1446"),
				},
			},
			ParticipantPropertyReferences: []customerinsights.ParticipantPropertyReferenceArgs{
				{
					SourcePropertyName: pulumi.String("testInteraction1949"),
					TargetPropertyName: pulumi.String("ProfileId"),
				},
			},
			ResourceGroupName:    pulumi.String("TestHubRG"),
			SourceEntityType:     customerinsights.EntityTypeInteraction,
			SourceEntityTypeName: pulumi.String("testInteraction1949"),
			TargetEntityType:     customerinsights.EntityTypeProfile,
			TargetEntityTypeName: pulumi.String("testProfile1446"),
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
import com.pulumi.azurenative.customerinsights.Link;
import com.pulumi.azurenative.customerinsights.LinkArgs;
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
        var link = new Link("link", LinkArgs.builder()        
            .description(Map.of("en-us", "Link Description"))
            .displayName(Map.of("en-us", "Link DisplayName"))
            .hubName("sdkTestHub")
            .linkName("linkTest4806")
            .mappings(Map.ofEntries(
                Map.entry("linkType", "UpdateAlways"),
                Map.entry("sourcePropertyName", "testInteraction1949"),
                Map.entry("targetPropertyName", "testProfile1446")
            ))
            .participantPropertyReferences(Map.ofEntries(
                Map.entry("sourcePropertyName", "testInteraction1949"),
                Map.entry("targetPropertyName", "ProfileId")
            ))
            .resourceGroupName("TestHubRG")
            .sourceEntityType("Interaction")
            .sourceEntityTypeName("testInteraction1949")
            .targetEntityType("Profile")
            .targetEntityTypeName("testProfile1446")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const link = new azure_native.customerinsights.Link("link", {
    description: {
        "en-us": "Link Description",
    },
    displayName: {
        "en-us": "Link DisplayName",
    },
    hubName: "sdkTestHub",
    linkName: "linkTest4806",
    mappings: [{
        linkType: azure_native.customerinsights.LinkTypes.UpdateAlways,
        sourcePropertyName: "testInteraction1949",
        targetPropertyName: "testProfile1446",
    }],
    participantPropertyReferences: [{
        sourcePropertyName: "testInteraction1949",
        targetPropertyName: "ProfileId",
    }],
    resourceGroupName: "TestHubRG",
    sourceEntityType: azure_native.customerinsights.EntityType.Interaction,
    sourceEntityTypeName: "testInteraction1949",
    targetEntityType: azure_native.customerinsights.EntityType.Profile,
    targetEntityTypeName: "testProfile1446",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

link = azure_native.customerinsights.Link("link",
    description={
        "en-us": "Link Description",
    },
    display_name={
        "en-us": "Link DisplayName",
    },
    hub_name="sdkTestHub",
    link_name="linkTest4806",
    mappings=[azure_native.customerinsights.TypePropertiesMappingArgs(
        link_type=azure_native.customerinsights.LinkTypes.UPDATE_ALWAYS,
        source_property_name="testInteraction1949",
        target_property_name="testProfile1446",
    )],
    participant_property_references=[azure_native.customerinsights.ParticipantPropertyReferenceArgs(
        source_property_name="testInteraction1949",
        target_property_name="ProfileId",
    )],
    resource_group_name="TestHubRG",
    source_entity_type=azure_native.customerinsights.EntityType.INTERACTION,
    source_entity_type_name="testInteraction1949",
    target_entity_type=azure_native.customerinsights.EntityType.PROFILE,
    target_entity_type_name="testProfile1446")

```

```yaml
resources:
  link:
    type: azure-native:customerinsights:Link
    properties:
      description:
        en-us: Link Description
      displayName:
        en-us: Link DisplayName
      hubName: sdkTestHub
      linkName: linkTest4806
      mappings:
        - linkType: UpdateAlways
          sourcePropertyName: testInteraction1949
          targetPropertyName: testProfile1446
      participantPropertyReferences:
        - sourcePropertyName: testInteraction1949
          targetPropertyName: ProfileId
      resourceGroupName: TestHubRG
      sourceEntityType: Interaction
      sourceEntityTypeName: testInteraction1949
      targetEntityType: Profile
      targetEntityTypeName: testProfile1446

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:customerinsights:Link azSdkTestHub/linkTest4806 /subscriptions/c909e979-ef71-4def-a970-bc7c154db8c5/resourceGroups/TestHubRG/providers/Microsoft.CustomerInsights/hubs/azSdkTestHub/links/linkTest4806 
```
