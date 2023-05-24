The relationship link resource format.
API Version: 2017-04-26.
Previous API Version: 2017-04-26. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RelationshipLinks_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var relationshipLink = new AzureNative.CustomerInsights.RelationshipLink("relationshipLink", new()
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
        InteractionType = "testInteraction4332",
        ProfilePropertyReferences = new[]
        {
            new AzureNative.CustomerInsights.Inputs.ParticipantProfilePropertyReferenceArgs
            {
                InteractionPropertyName = "profile1",
                ProfilePropertyName = "ProfileId",
            },
        },
        RelatedProfilePropertyReferences = new[]
        {
            new AzureNative.CustomerInsights.Inputs.ParticipantProfilePropertyReferenceArgs
            {
                InteractionPropertyName = "profile1",
                ProfilePropertyName = "ProfileId",
            },
        },
        RelationshipLinkName = "Somelink",
        RelationshipName = "testProfile2326994",
        ResourceGroupName = "TestHubRG",
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
		_, err := customerinsights.NewRelationshipLink(ctx, "relationshipLink", &customerinsights.RelationshipLinkArgs{
			Description: pulumi.StringMap{
				"en-us": pulumi.String("Link Description"),
			},
			DisplayName: pulumi.StringMap{
				"en-us": pulumi.String("Link DisplayName"),
			},
			HubName:         pulumi.String("sdkTestHub"),
			InteractionType: pulumi.String("testInteraction4332"),
			ProfilePropertyReferences: []customerinsights.ParticipantProfilePropertyReferenceArgs{
				{
					InteractionPropertyName: pulumi.String("profile1"),
					ProfilePropertyName:     pulumi.String("ProfileId"),
				},
			},
			RelatedProfilePropertyReferences: []customerinsights.ParticipantProfilePropertyReferenceArgs{
				{
					InteractionPropertyName: pulumi.String("profile1"),
					ProfilePropertyName:     pulumi.String("ProfileId"),
				},
			},
			RelationshipLinkName: pulumi.String("Somelink"),
			RelationshipName:     pulumi.String("testProfile2326994"),
			ResourceGroupName:    pulumi.String("TestHubRG"),
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
import com.pulumi.azurenative.customerinsights.RelationshipLink;
import com.pulumi.azurenative.customerinsights.RelationshipLinkArgs;
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
        var relationshipLink = new RelationshipLink("relationshipLink", RelationshipLinkArgs.builder()        
            .description(Map.of("en-us", "Link Description"))
            .displayName(Map.of("en-us", "Link DisplayName"))
            .hubName("sdkTestHub")
            .interactionType("testInteraction4332")
            .profilePropertyReferences(Map.ofEntries(
                Map.entry("interactionPropertyName", "profile1"),
                Map.entry("profilePropertyName", "ProfileId")
            ))
            .relatedProfilePropertyReferences(Map.ofEntries(
                Map.entry("interactionPropertyName", "profile1"),
                Map.entry("profilePropertyName", "ProfileId")
            ))
            .relationshipLinkName("Somelink")
            .relationshipName("testProfile2326994")
            .resourceGroupName("TestHubRG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const relationshipLink = new azure_native.customerinsights.RelationshipLink("relationshipLink", {
    description: {
        "en-us": "Link Description",
    },
    displayName: {
        "en-us": "Link DisplayName",
    },
    hubName: "sdkTestHub",
    interactionType: "testInteraction4332",
    profilePropertyReferences: [{
        interactionPropertyName: "profile1",
        profilePropertyName: "ProfileId",
    }],
    relatedProfilePropertyReferences: [{
        interactionPropertyName: "profile1",
        profilePropertyName: "ProfileId",
    }],
    relationshipLinkName: "Somelink",
    relationshipName: "testProfile2326994",
    resourceGroupName: "TestHubRG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

relationship_link = azure_native.customerinsights.RelationshipLink("relationshipLink",
    description={
        "en-us": "Link Description",
    },
    display_name={
        "en-us": "Link DisplayName",
    },
    hub_name="sdkTestHub",
    interaction_type="testInteraction4332",
    profile_property_references=[azure_native.customerinsights.ParticipantProfilePropertyReferenceArgs(
        interaction_property_name="profile1",
        profile_property_name="ProfileId",
    )],
    related_profile_property_references=[azure_native.customerinsights.ParticipantProfilePropertyReferenceArgs(
        interaction_property_name="profile1",
        profile_property_name="ProfileId",
    )],
    relationship_link_name="Somelink",
    relationship_name="testProfile2326994",
    resource_group_name="TestHubRG")

```

```yaml
resources:
  relationshipLink:
    type: azure-native:customerinsights:RelationshipLink
    properties:
      description:
        en-us: Link Description
      displayName:
        en-us: Link DisplayName
      hubName: sdkTestHub
      interactionType: testInteraction4332
      profilePropertyReferences:
        - interactionPropertyName: profile1
          profilePropertyName: ProfileId
      relatedProfilePropertyReferences:
        - interactionPropertyName: profile1
          profilePropertyName: ProfileId
      relationshipLinkName: Somelink
      relationshipName: testProfile2326994
      resourceGroupName: TestHubRG

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:customerinsights:RelationshipLink sdkTestHub/Somelink /subscriptions/c909e979-ef71-4def-a970-bc7c154db8c5/resourceGroups/TestHubRG/providers/Microsoft.CustomerInsights/hubs/sdkTestHub/relationshipLinks/Somelink 
```
