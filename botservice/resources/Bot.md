Bot resource definition
API Version: 2022-09-15.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Bot
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var bot = new AzureNative.BotService.Bot("bot", new()
    {
        Kind = "sdk",
        Location = "West US",
        Properties = new AzureNative.BotService.Inputs.BotPropertiesArgs
        {
            CmekKeyVaultUrl = "https://myCmekKey",
            Description = "The description of the bot",
            DeveloperAppInsightKey = "appinsightskey",
            DeveloperAppInsightsApiKey = "appinsightsapikey",
            DeveloperAppInsightsApplicationId = "appinsightsappid",
            DisableLocalAuth = true,
            DisplayName = "The Name of the bot",
            Endpoint = "http://mybot.coffee",
            IconUrl = "http://myicon",
            IsCmekEnabled = true,
            LuisAppIds = new[]
            {
                "luisappid1",
                "luisappid2",
            },
            LuisKey = "luiskey",
            MsaAppId = "exampleappid",
            MsaAppMSIResourceId = "/subscriptions/foo/resourcegroups/bar/providers/microsoft.managedidentity/userassignedidentities/sampleId",
            MsaAppTenantId = "exampleapptenantid",
            MsaAppType = "UserAssignedMSI",
            PublicNetworkAccess = "Enabled",
            SchemaTransformationVersion = "1.0",
        },
        ResourceGroupName = "OneResourceGroupName",
        ResourceName = "samplebotname",
        Sku = new AzureNative.BotService.Inputs.SkuArgs
        {
            Name = "S1",
        },
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
    });

});


```

```go
package main

import (
	botservice "github.com/pulumi/pulumi-azure-native-sdk/botservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := botservice.NewBot(ctx, "bot", &botservice.BotArgs{
			Kind:     pulumi.String("sdk"),
			Location: pulumi.String("West US"),
			Properties: &botservice.BotPropertiesArgs{
				CmekKeyVaultUrl:                   pulumi.String("https://myCmekKey"),
				Description:                       pulumi.String("The description of the bot"),
				DeveloperAppInsightKey:            pulumi.String("appinsightskey"),
				DeveloperAppInsightsApiKey:        pulumi.String("appinsightsapikey"),
				DeveloperAppInsightsApplicationId: pulumi.String("appinsightsappid"),
				DisableLocalAuth:                  pulumi.Bool(true),
				DisplayName:                       pulumi.String("The Name of the bot"),
				Endpoint:                          pulumi.String("http://mybot.coffee"),
				IconUrl:                           pulumi.String("http://myicon"),
				IsCmekEnabled:                     pulumi.Bool(true),
				LuisAppIds: pulumi.StringArray{
					pulumi.String("luisappid1"),
					pulumi.String("luisappid2"),
				},
				LuisKey:                     pulumi.String("luiskey"),
				MsaAppId:                    pulumi.String("exampleappid"),
				MsaAppMSIResourceId:         pulumi.String("/subscriptions/foo/resourcegroups/bar/providers/microsoft.managedidentity/userassignedidentities/sampleId"),
				MsaAppTenantId:              pulumi.String("exampleapptenantid"),
				MsaAppType:                  pulumi.String("UserAssignedMSI"),
				PublicNetworkAccess:         pulumi.String("Enabled"),
				SchemaTransformationVersion: pulumi.String("1.0"),
			},
			ResourceGroupName: pulumi.String("OneResourceGroupName"),
			ResourceName:      pulumi.String("samplebotname"),
			Sku: &botservice.SkuArgs{
				Name: pulumi.String("S1"),
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
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
import com.pulumi.azurenative.botservice.Bot;
import com.pulumi.azurenative.botservice.BotArgs;
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
        var bot = new Bot("bot", BotArgs.builder()        
            .kind("sdk")
            .location("West US")
            .properties(Map.ofEntries(
                Map.entry("cmekKeyVaultUrl", "https://myCmekKey"),
                Map.entry("description", "The description of the bot"),
                Map.entry("developerAppInsightKey", "appinsightskey"),
                Map.entry("developerAppInsightsApiKey", "appinsightsapikey"),
                Map.entry("developerAppInsightsApplicationId", "appinsightsappid"),
                Map.entry("disableLocalAuth", true),
                Map.entry("displayName", "The Name of the bot"),
                Map.entry("endpoint", "http://mybot.coffee"),
                Map.entry("iconUrl", "http://myicon"),
                Map.entry("isCmekEnabled", true),
                Map.entry("luisAppIds",                 
                    "luisappid1",
                    "luisappid2"),
                Map.entry("luisKey", "luiskey"),
                Map.entry("msaAppId", "exampleappid"),
                Map.entry("msaAppMSIResourceId", "/subscriptions/foo/resourcegroups/bar/providers/microsoft.managedidentity/userassignedidentities/sampleId"),
                Map.entry("msaAppTenantId", "exampleapptenantid"),
                Map.entry("msaAppType", "UserAssignedMSI"),
                Map.entry("publicNetworkAccess", "Enabled"),
                Map.entry("schemaTransformationVersion", "1.0")
            ))
            .resourceGroupName("OneResourceGroupName")
            .resourceName("samplebotname")
            .sku(Map.of("name", "S1"))
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const bot = new azure_native.botservice.Bot("bot", {
    kind: "sdk",
    location: "West US",
    properties: {
        cmekKeyVaultUrl: "https://myCmekKey",
        description: "The description of the bot",
        developerAppInsightKey: "appinsightskey",
        developerAppInsightsApiKey: "appinsightsapikey",
        developerAppInsightsApplicationId: "appinsightsappid",
        disableLocalAuth: true,
        displayName: "The Name of the bot",
        endpoint: "http://mybot.coffee",
        iconUrl: "http://myicon",
        isCmekEnabled: true,
        luisAppIds: [
            "luisappid1",
            "luisappid2",
        ],
        luisKey: "luiskey",
        msaAppId: "exampleappid",
        msaAppMSIResourceId: "/subscriptions/foo/resourcegroups/bar/providers/microsoft.managedidentity/userassignedidentities/sampleId",
        msaAppTenantId: "exampleapptenantid",
        msaAppType: "UserAssignedMSI",
        publicNetworkAccess: "Enabled",
        schemaTransformationVersion: "1.0",
    },
    resourceGroupName: "OneResourceGroupName",
    resourceName: "samplebotname",
    sku: {
        name: "S1",
    },
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

bot = azure_native.botservice.Bot("bot",
    kind="sdk",
    location="West US",
    properties=azure_native.botservice.BotPropertiesArgs(
        cmek_key_vault_url="https://myCmekKey",
        description="The description of the bot",
        developer_app_insight_key="appinsightskey",
        developer_app_insights_api_key="appinsightsapikey",
        developer_app_insights_application_id="appinsightsappid",
        disable_local_auth=True,
        display_name="The Name of the bot",
        endpoint="http://mybot.coffee",
        icon_url="http://myicon",
        is_cmek_enabled=True,
        luis_app_ids=[
            "luisappid1",
            "luisappid2",
        ],
        luis_key="luiskey",
        msa_app_id="exampleappid",
        msa_app_msi_resource_id="/subscriptions/foo/resourcegroups/bar/providers/microsoft.managedidentity/userassignedidentities/sampleId",
        msa_app_tenant_id="exampleapptenantid",
        msa_app_type="UserAssignedMSI",
        public_network_access="Enabled",
        schema_transformation_version="1.0",
    ),
    resource_group_name="OneResourceGroupName",
    resource_name_="samplebotname",
    sku=azure_native.botservice.SkuArgs(
        name="S1",
    ),
    tags={
        "tag1": "value1",
        "tag2": "value2",
    })

```

```yaml
resources:
  bot:
    type: azure-native:botservice:Bot
    properties:
      kind: sdk
      location: West US
      properties:
        cmekKeyVaultUrl: https://myCmekKey
        description: The description of the bot
        developerAppInsightKey: appinsightskey
        developerAppInsightsApiKey: appinsightsapikey
        developerAppInsightsApplicationId: appinsightsappid
        disableLocalAuth: true
        displayName: The Name of the bot
        endpoint: http://mybot.coffee
        iconUrl: http://myicon
        isCmekEnabled: true
        luisAppIds:
          - luisappid1
          - luisappid2
        luisKey: luiskey
        msaAppId: exampleappid
        msaAppMSIResourceId: /subscriptions/foo/resourcegroups/bar/providers/microsoft.managedidentity/userassignedidentities/sampleId
        msaAppTenantId: exampleapptenantid
        msaAppType: UserAssignedMSI
        publicNetworkAccess: Enabled
        schemaTransformationVersion: '1.0'
      resourceGroupName: OneResourceGroupName
      resourceName: samplebotname
      sku:
        name: S1
      tags:
        tag1: value1
        tag2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:botservice:Bot samplebotname /subscriptions/subscription-id/resourceGroups/OneResourceGroupName/providers/Microsoft.BotService/botServices/samplebotname 
```
