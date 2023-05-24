The relationship resource format.
API Version: 2017-04-26.
Previous API Version: 2017-04-26. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Relationships_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var relationship = new AzureNative.CustomerInsights.Relationship("relationship", new()
    {
        Cardinality = AzureNative.CustomerInsights.CardinalityTypes.OneToOne,
        Description = 
        {
            { "en-us", "Relationship Description" },
        },
        DisplayName = 
        {
            { "en-us", "Relationship DisplayName" },
        },
        Fields = new[] {},
        HubName = "sdkTestHub",
        ProfileType = "testProfile2326994",
        RelatedProfileType = "testProfile2326994",
        RelationshipName = "SomeRelationship",
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
		_, err := customerinsights.NewRelationship(ctx, "relationship", &customerinsights.RelationshipArgs{
			Cardinality: customerinsights.CardinalityTypesOneToOne,
			Description: pulumi.StringMap{
				"en-us": pulumi.String("Relationship Description"),
			},
			DisplayName: pulumi.StringMap{
				"en-us": pulumi.String("Relationship DisplayName"),
			},
			Fields:             customerinsights.PropertyDefinitionArray{},
			HubName:            pulumi.String("sdkTestHub"),
			ProfileType:        pulumi.String("testProfile2326994"),
			RelatedProfileType: pulumi.String("testProfile2326994"),
			RelationshipName:   pulumi.String("SomeRelationship"),
			ResourceGroupName:  pulumi.String("TestHubRG"),
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
import com.pulumi.azurenative.customerinsights.Relationship;
import com.pulumi.azurenative.customerinsights.RelationshipArgs;
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
        var relationship = new Relationship("relationship", RelationshipArgs.builder()        
            .cardinality("OneToOne")
            .description(Map.of("en-us", "Relationship Description"))
            .displayName(Map.of("en-us", "Relationship DisplayName"))
            .fields()
            .hubName("sdkTestHub")
            .profileType("testProfile2326994")
            .relatedProfileType("testProfile2326994")
            .relationshipName("SomeRelationship")
            .resourceGroupName("TestHubRG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const relationship = new azure_native.customerinsights.Relationship("relationship", {
    cardinality: azure_native.customerinsights.CardinalityTypes.OneToOne,
    description: {
        "en-us": "Relationship Description",
    },
    displayName: {
        "en-us": "Relationship DisplayName",
    },
    fields: [],
    hubName: "sdkTestHub",
    profileType: "testProfile2326994",
    relatedProfileType: "testProfile2326994",
    relationshipName: "SomeRelationship",
    resourceGroupName: "TestHubRG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

relationship = azure_native.customerinsights.Relationship("relationship",
    cardinality=azure_native.customerinsights.CardinalityTypes.ONE_TO_ONE,
    description={
        "en-us": "Relationship Description",
    },
    display_name={
        "en-us": "Relationship DisplayName",
    },
    fields=[],
    hub_name="sdkTestHub",
    profile_type="testProfile2326994",
    related_profile_type="testProfile2326994",
    relationship_name="SomeRelationship",
    resource_group_name="TestHubRG")

```

```yaml
resources:
  relationship:
    type: azure-native:customerinsights:Relationship
    properties:
      cardinality: OneToOne
      description:
        en-us: Relationship Description
      displayName:
        en-us: Relationship DisplayName
      fields: []
      hubName: sdkTestHub
      profileType: testProfile2326994
      relatedProfileType: testProfile2326994
      relationshipName: SomeRelationship
      resourceGroupName: TestHubRG

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:customerinsights:Relationship sdkTestHub/testProfile2326994 /subscriptions/c909e979-ef71-4def-a970-bc7c154db8c5/resourceGroups/TestHubRG/providers/Microsoft.CustomerInsights/hubs/sdkTestHub/relationships/SomeRelationship 
```
