Bot channel resource definition
API Version: 2022-09-15.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Connection Setting
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var botConnection = new AzureNative.BotService.BotConnection("botConnection", new()
    {
        ConnectionName = "sampleConnection",
        Location = "West US",
        Properties = new AzureNative.BotService.Inputs.ConnectionSettingPropertiesArgs
        {
            ClientId = "sampleclientid",
            ClientSecret = "samplesecret",
            Parameters = new[]
            {
                new AzureNative.BotService.Inputs.ConnectionSettingParameterArgs
                {
                    Key = "key1",
                    Value = "value1",
                },
                new AzureNative.BotService.Inputs.ConnectionSettingParameterArgs
                {
                    Key = "key2",
                    Value = "value2",
                },
            },
            Scopes = "samplescope",
            ServiceProviderId = "serviceproviderid",
        },
        ResourceGroupName = "OneResourceGroupName",
        ResourceName = "samplebotname",
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
		_, err := botservice.NewBotConnection(ctx, "botConnection", &botservice.BotConnectionArgs{
			ConnectionName: pulumi.String("sampleConnection"),
			Location:       pulumi.String("West US"),
			Properties: botservice.ConnectionSettingPropertiesResponse{
				ClientId:     pulumi.String("sampleclientid"),
				ClientSecret: pulumi.String("samplesecret"),
				Parameters: botservice.ConnectionSettingParameterArray{
					&botservice.ConnectionSettingParameterArgs{
						Key:   pulumi.String("key1"),
						Value: pulumi.String("value1"),
					},
					&botservice.ConnectionSettingParameterArgs{
						Key:   pulumi.String("key2"),
						Value: pulumi.String("value2"),
					},
				},
				Scopes:            pulumi.String("samplescope"),
				ServiceProviderId: pulumi.String("serviceproviderid"),
			},
			ResourceGroupName: pulumi.String("OneResourceGroupName"),
			ResourceName:      pulumi.String("samplebotname"),
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
import com.pulumi.azurenative.botservice.BotConnection;
import com.pulumi.azurenative.botservice.BotConnectionArgs;
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
        var botConnection = new BotConnection("botConnection", BotConnectionArgs.builder()        
            .connectionName("sampleConnection")
            .location("West US")
            .properties(Map.ofEntries(
                Map.entry("clientId", "sampleclientid"),
                Map.entry("clientSecret", "samplesecret"),
                Map.entry("parameters",                 
                    Map.ofEntries(
                        Map.entry("key", "key1"),
                        Map.entry("value", "value1")
                    ),
                    Map.ofEntries(
                        Map.entry("key", "key2"),
                        Map.entry("value", "value2")
                    )),
                Map.entry("scopes", "samplescope"),
                Map.entry("serviceProviderId", "serviceproviderid")
            ))
            .resourceGroupName("OneResourceGroupName")
            .resourceName("samplebotname")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const botConnection = new azure_native.botservice.BotConnection("botConnection", {
    connectionName: "sampleConnection",
    location: "West US",
    properties: {
        clientId: "sampleclientid",
        clientSecret: "samplesecret",
        parameters: [
            {
                key: "key1",
                value: "value1",
            },
            {
                key: "key2",
                value: "value2",
            },
        ],
        scopes: "samplescope",
        serviceProviderId: "serviceproviderid",
    },
    resourceGroupName: "OneResourceGroupName",
    resourceName: "samplebotname",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

bot_connection = azure_native.botservice.BotConnection("botConnection",
    connection_name="sampleConnection",
    location="West US",
    properties=azure_native.botservice.ConnectionSettingPropertiesResponseArgs(
        client_id="sampleclientid",
        client_secret="samplesecret",
        parameters=[
            azure_native.botservice.ConnectionSettingParameterArgs(
                key="key1",
                value="value1",
            ),
            azure_native.botservice.ConnectionSettingParameterArgs(
                key="key2",
                value="value2",
            ),
        ],
        scopes="samplescope",
        service_provider_id="serviceproviderid",
    ),
    resource_group_name="OneResourceGroupName",
    resource_name_="samplebotname")

```

```yaml
resources:
  botConnection:
    type: azure-native:botservice:BotConnection
    properties:
      connectionName: sampleConnection
      location: West US
      properties:
        clientId: sampleclientid
        clientSecret: samplesecret
        parameters:
          - key: key1
            value: value1
          - key: key2
            value: value2
        scopes: samplescope
        serviceProviderId: serviceproviderid
      resourceGroupName: OneResourceGroupName
      resourceName: samplebotname

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:botservice:BotConnection sampleConnection /subscriptions/subscription-id/resourceGroups/OneResourceGroupName/providers/Microsoft.BotService/botServices/samplebotname/connections/sampleConnection 
```
