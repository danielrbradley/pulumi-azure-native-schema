The profile resource format.
API Version: 2017-04-26.
Previous API Version: 2017-04-26. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Profiles_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var profile = new AzureNative.CustomerInsights.Profile("profile", new()
    {
        ApiEntitySetName = "TestProfileType396",
        Fields = new[]
        {
            new AzureNative.CustomerInsights.Inputs.PropertyDefinitionArgs
            {
                FieldName = "Id",
                FieldType = "Edm.String",
                IsArray = false,
                IsRequired = true,
            },
            new AzureNative.CustomerInsights.Inputs.PropertyDefinitionArgs
            {
                FieldName = "ProfileId",
                FieldType = "Edm.String",
                IsArray = false,
                IsRequired = true,
            },
            new AzureNative.CustomerInsights.Inputs.PropertyDefinitionArgs
            {
                FieldName = "LastName",
                FieldType = "Edm.String",
                IsArray = false,
                IsRequired = true,
            },
            new AzureNative.CustomerInsights.Inputs.PropertyDefinitionArgs
            {
                FieldName = "TestProfileType396",
                FieldType = "Edm.String",
                IsArray = false,
                IsRequired = true,
            },
            new AzureNative.CustomerInsights.Inputs.PropertyDefinitionArgs
            {
                FieldName = "SavingAccountBalance",
                FieldType = "Edm.Int32",
                IsArray = false,
                IsRequired = true,
            },
        },
        HubName = "sdkTestHub",
        LargeImage = "\\\\Images\\\\LargeImage",
        MediumImage = "\\\\Images\\\\MediumImage",
        ProfileName = "TestProfileType396",
        ResourceGroupName = "TestHubRG",
        SchemaItemTypeLink = "SchemaItemTypeLink",
        SmallImage = "\\\\Images\\\\smallImage",
        StrongIds = new[]
        {
            new AzureNative.CustomerInsights.Inputs.StrongIdArgs
            {
                KeyPropertyNames = new[]
                {
                    "Id",
                    "SavingAccountBalance",
                },
                StrongIdName = "Id",
            },
            new AzureNative.CustomerInsights.Inputs.StrongIdArgs
            {
                KeyPropertyNames = new[]
                {
                    "ProfileId",
                    "LastName",
                },
                StrongIdName = "ProfileId",
            },
        },
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
		_, err := customerinsights.NewProfile(ctx, "profile", &customerinsights.ProfileArgs{
			ApiEntitySetName: pulumi.String("TestProfileType396"),
			Fields: []customerinsights.PropertyDefinitionArgs{
				{
					FieldName:  pulumi.String("Id"),
					FieldType:  pulumi.String("Edm.String"),
					IsArray:    pulumi.Bool(false),
					IsRequired: pulumi.Bool(true),
				},
				{
					FieldName:  pulumi.String("ProfileId"),
					FieldType:  pulumi.String("Edm.String"),
					IsArray:    pulumi.Bool(false),
					IsRequired: pulumi.Bool(true),
				},
				{
					FieldName:  pulumi.String("LastName"),
					FieldType:  pulumi.String("Edm.String"),
					IsArray:    pulumi.Bool(false),
					IsRequired: pulumi.Bool(true),
				},
				{
					FieldName:  pulumi.String("TestProfileType396"),
					FieldType:  pulumi.String("Edm.String"),
					IsArray:    pulumi.Bool(false),
					IsRequired: pulumi.Bool(true),
				},
				{
					FieldName:  pulumi.String("SavingAccountBalance"),
					FieldType:  pulumi.String("Edm.Int32"),
					IsArray:    pulumi.Bool(false),
					IsRequired: pulumi.Bool(true),
				},
			},
			HubName:            pulumi.String("sdkTestHub"),
			LargeImage:         pulumi.String("\\\\Images\\\\LargeImage"),
			MediumImage:        pulumi.String("\\\\Images\\\\MediumImage"),
			ProfileName:        pulumi.String("TestProfileType396"),
			ResourceGroupName:  pulumi.String("TestHubRG"),
			SchemaItemTypeLink: pulumi.String("SchemaItemTypeLink"),
			SmallImage:         pulumi.String("\\\\Images\\\\smallImage"),
			StrongIds: []customerinsights.StrongIdArgs{
				{
					KeyPropertyNames: pulumi.StringArray{
						pulumi.String("Id"),
						pulumi.String("SavingAccountBalance"),
					},
					StrongIdName: pulumi.String("Id"),
				},
				{
					KeyPropertyNames: pulumi.StringArray{
						pulumi.String("ProfileId"),
						pulumi.String("LastName"),
					},
					StrongIdName: pulumi.String("ProfileId"),
				},
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
import com.pulumi.azurenative.customerinsights.Profile;
import com.pulumi.azurenative.customerinsights.ProfileArgs;
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
        var profile = new Profile("profile", ProfileArgs.builder()        
            .apiEntitySetName("TestProfileType396")
            .fields(            
                Map.ofEntries(
                    Map.entry("fieldName", "Id"),
                    Map.entry("fieldType", "Edm.String"),
                    Map.entry("isArray", false),
                    Map.entry("isRequired", true)
                ),
                Map.ofEntries(
                    Map.entry("fieldName", "ProfileId"),
                    Map.entry("fieldType", "Edm.String"),
                    Map.entry("isArray", false),
                    Map.entry("isRequired", true)
                ),
                Map.ofEntries(
                    Map.entry("fieldName", "LastName"),
                    Map.entry("fieldType", "Edm.String"),
                    Map.entry("isArray", false),
                    Map.entry("isRequired", true)
                ),
                Map.ofEntries(
                    Map.entry("fieldName", "TestProfileType396"),
                    Map.entry("fieldType", "Edm.String"),
                    Map.entry("isArray", false),
                    Map.entry("isRequired", true)
                ),
                Map.ofEntries(
                    Map.entry("fieldName", "SavingAccountBalance"),
                    Map.entry("fieldType", "Edm.Int32"),
                    Map.entry("isArray", false),
                    Map.entry("isRequired", true)
                ))
            .hubName("sdkTestHub")
            .largeImage("\\\\Images\\\\LargeImage")
            .mediumImage("\\\\Images\\\\MediumImage")
            .profileName("TestProfileType396")
            .resourceGroupName("TestHubRG")
            .schemaItemTypeLink("SchemaItemTypeLink")
            .smallImage("\\\\Images\\\\smallImage")
            .strongIds(            
                Map.ofEntries(
                    Map.entry("keyPropertyNames",                     
                        "Id",
                        "SavingAccountBalance"),
                    Map.entry("strongIdName", "Id")
                ),
                Map.ofEntries(
                    Map.entry("keyPropertyNames",                     
                        "ProfileId",
                        "LastName"),
                    Map.entry("strongIdName", "ProfileId")
                ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const profile = new azure_native.customerinsights.Profile("profile", {
    apiEntitySetName: "TestProfileType396",
    fields: [
        {
            fieldName: "Id",
            fieldType: "Edm.String",
            isArray: false,
            isRequired: true,
        },
        {
            fieldName: "ProfileId",
            fieldType: "Edm.String",
            isArray: false,
            isRequired: true,
        },
        {
            fieldName: "LastName",
            fieldType: "Edm.String",
            isArray: false,
            isRequired: true,
        },
        {
            fieldName: "TestProfileType396",
            fieldType: "Edm.String",
            isArray: false,
            isRequired: true,
        },
        {
            fieldName: "SavingAccountBalance",
            fieldType: "Edm.Int32",
            isArray: false,
            isRequired: true,
        },
    ],
    hubName: "sdkTestHub",
    largeImage: "\\\\Images\\\\LargeImage",
    mediumImage: "\\\\Images\\\\MediumImage",
    profileName: "TestProfileType396",
    resourceGroupName: "TestHubRG",
    schemaItemTypeLink: "SchemaItemTypeLink",
    smallImage: "\\\\Images\\\\smallImage",
    strongIds: [
        {
            keyPropertyNames: [
                "Id",
                "SavingAccountBalance",
            ],
            strongIdName: "Id",
        },
        {
            keyPropertyNames: [
                "ProfileId",
                "LastName",
            ],
            strongIdName: "ProfileId",
        },
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

profile = azure_native.customerinsights.Profile("profile",
    api_entity_set_name="TestProfileType396",
    fields=[
        azure_native.customerinsights.PropertyDefinitionArgs(
            field_name="Id",
            field_type="Edm.String",
            is_array=False,
            is_required=True,
        ),
        azure_native.customerinsights.PropertyDefinitionArgs(
            field_name="ProfileId",
            field_type="Edm.String",
            is_array=False,
            is_required=True,
        ),
        azure_native.customerinsights.PropertyDefinitionArgs(
            field_name="LastName",
            field_type="Edm.String",
            is_array=False,
            is_required=True,
        ),
        azure_native.customerinsights.PropertyDefinitionArgs(
            field_name="TestProfileType396",
            field_type="Edm.String",
            is_array=False,
            is_required=True,
        ),
        azure_native.customerinsights.PropertyDefinitionArgs(
            field_name="SavingAccountBalance",
            field_type="Edm.Int32",
            is_array=False,
            is_required=True,
        ),
    ],
    hub_name="sdkTestHub",
    large_image="\\\\Images\\\\LargeImage",
    medium_image="\\\\Images\\\\MediumImage",
    profile_name="TestProfileType396",
    resource_group_name="TestHubRG",
    schema_item_type_link="SchemaItemTypeLink",
    small_image="\\\\Images\\\\smallImage",
    strong_ids=[
        azure_native.customerinsights.StrongIdArgs(
            key_property_names=[
                "Id",
                "SavingAccountBalance",
            ],
            strong_id_name="Id",
        ),
        azure_native.customerinsights.StrongIdArgs(
            key_property_names=[
                "ProfileId",
                "LastName",
            ],
            strong_id_name="ProfileId",
        ),
    ])

```

```yaml
resources:
  profile:
    type: azure-native:customerinsights:Profile
    properties:
      apiEntitySetName: TestProfileType396
      fields:
        - fieldName: Id
          fieldType: Edm.String
          isArray: false
          isRequired: true
        - fieldName: ProfileId
          fieldType: Edm.String
          isArray: false
          isRequired: true
        - fieldName: LastName
          fieldType: Edm.String
          isArray: false
          isRequired: true
        - fieldName: TestProfileType396
          fieldType: Edm.String
          isArray: false
          isRequired: true
        - fieldName: SavingAccountBalance
          fieldType: Edm.Int32
          isArray: false
          isRequired: true
      hubName: sdkTestHub
      largeImage: \\Images\\LargeImage
      mediumImage: \\Images\\MediumImage
      profileName: TestProfileType396
      resourceGroupName: TestHubRG
      schemaItemTypeLink: SchemaItemTypeLink
      smallImage: \\Images\\smallImage
      strongIds:
        - keyPropertyNames:
            - Id
            - SavingAccountBalance
          strongIdName: Id
        - keyPropertyNames:
            - ProfileId
            - LastName
          strongIdName: ProfileId

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:customerinsights:Profile azSdkTestHub/TestProfileType396 /subscriptions/c909e979-ef71-4def-a970-bc7c154db8c5/resourceGroups/TestHubRG/providers/Microsoft.CustomerInsights/hubs/azSdkTestHub/profiles/TestProfileType396 
```
