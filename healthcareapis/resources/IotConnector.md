IoT Connector definition.
API Version: 2022-12-01.
Previous API Version: 2022-05-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create an IoT Connector
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var iotConnector = new AzureNative.HealthcareApis.IotConnector("iotConnector", new()
    {
        DeviceMapping = new AzureNative.HealthcareApis.Inputs.IotMappingPropertiesArgs
        {
            Content = 
            {
                { "template", new[]
                {
                    
                    {
                        { "template", 
                        {
                            { "deviceIdExpression", "$.deviceid" },
                            { "timestampExpression", "$.measurementdatetime" },
                            { "typeMatchExpression", "$..[?(@heartrate)]" },
                            { "typeName", "heartrate" },
                            { "values", new[]
                            {
                                
                                {
                                    { "required", "true" },
                                    { "valueExpression", "$.heartrate" },
                                    { "valueName", "hr" },
                                },
                            } },
                        } },
                        { "templateType", "JsonPathContent" },
                    },
                } },
                { "templateType", "CollectionContent" },
            },
        },
        Identity = new AzureNative.HealthcareApis.Inputs.ServiceManagedIdentityIdentityArgs
        {
            Type = "SystemAssigned",
        },
        IngestionEndpointConfiguration = new AzureNative.HealthcareApis.Inputs.IotEventHubIngestionEndpointConfigurationArgs
        {
            ConsumerGroup = "ConsumerGroupA",
            EventHubName = "MyEventHubName",
            FullyQualifiedEventHubNamespace = "myeventhub.servicesbus.windows.net",
        },
        IotConnectorName = "blue",
        Location = "westus",
        ResourceGroupName = "testRG",
        Tags = 
        {
            { "additionalProp1", "string" },
            { "additionalProp2", "string" },
            { "additionalProp3", "string" },
        },
        WorkspaceName = "workspace1",
    });

});


```

```go
package main

import (
	healthcareapis "github.com/pulumi/pulumi-azure-native-sdk/healthcareapis"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := healthcareapis.NewIotConnector(ctx, "iotConnector", &healthcareapis.IotConnectorArgs{
			DeviceMapping: &healthcareapis.IotMappingPropertiesArgs{
				Content: pulumi.Any{
					Template: []map[string]interface{}{
						map[string]interface{}{
							"template": map[string]interface{}{
								"deviceIdExpression":  "$.deviceid",
								"timestampExpression": "$.measurementdatetime",
								"typeMatchExpression": "$..[?(@heartrate)]",
								"typeName":            "heartrate",
								"values": []map[string]interface{}{
									map[string]interface{}{
										"required":        "true",
										"valueExpression": "$.heartrate",
										"valueName":       "hr",
									},
								},
							},
							"templateType": "JsonPathContent",
						},
					},
					TemplateType: "CollectionContent",
				},
			},
			Identity: &healthcareapis.ServiceManagedIdentityIdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			IngestionEndpointConfiguration: &healthcareapis.IotEventHubIngestionEndpointConfigurationArgs{
				ConsumerGroup:                   pulumi.String("ConsumerGroupA"),
				EventHubName:                    pulumi.String("MyEventHubName"),
				FullyQualifiedEventHubNamespace: pulumi.String("myeventhub.servicesbus.windows.net"),
			},
			IotConnectorName:  pulumi.String("blue"),
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("testRG"),
			Tags: pulumi.StringMap{
				"additionalProp1": pulumi.String("string"),
				"additionalProp2": pulumi.String("string"),
				"additionalProp3": pulumi.String("string"),
			},
			WorkspaceName: pulumi.String("workspace1"),
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
import com.pulumi.azurenative.healthcareapis.IotConnector;
import com.pulumi.azurenative.healthcareapis.IotConnectorArgs;
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
        var iotConnector = new IotConnector("iotConnector", IotConnectorArgs.builder()        
            .deviceMapping(Map.of("content", Map.ofEntries(
                Map.entry("template", IotMappingPropertiesArgs.builder()
                    .template(%!v(PANIC=Format method: runtime error: invalid memory address or nil pointer dereference))
                    .templateType("JsonPathContent")
                    .build()),
                Map.entry("templateType", "CollectionContent")
            )))
            .identity(Map.of("type", "SystemAssigned"))
            .ingestionEndpointConfiguration(Map.ofEntries(
                Map.entry("consumerGroup", "ConsumerGroupA"),
                Map.entry("eventHubName", "MyEventHubName"),
                Map.entry("fullyQualifiedEventHubNamespace", "myeventhub.servicesbus.windows.net")
            ))
            .iotConnectorName("blue")
            .location("westus")
            .resourceGroupName("testRG")
            .tags(Map.ofEntries(
                Map.entry("additionalProp1", "string"),
                Map.entry("additionalProp2", "string"),
                Map.entry("additionalProp3", "string")
            ))
            .workspaceName("workspace1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const iotConnector = new azure_native.healthcareapis.IotConnector("iotConnector", {
    deviceMapping: {
        content: {
            template: [{
                template: {
                    deviceIdExpression: "$.deviceid",
                    timestampExpression: "$.measurementdatetime",
                    typeMatchExpression: "$..[?(@heartrate)]",
                    typeName: "heartrate",
                    values: [{
                        required: "true",
                        valueExpression: "$.heartrate",
                        valueName: "hr",
                    }],
                },
                templateType: "JsonPathContent",
            }],
            templateType: "CollectionContent",
        },
    },
    identity: {
        type: "SystemAssigned",
    },
    ingestionEndpointConfiguration: {
        consumerGroup: "ConsumerGroupA",
        eventHubName: "MyEventHubName",
        fullyQualifiedEventHubNamespace: "myeventhub.servicesbus.windows.net",
    },
    iotConnectorName: "blue",
    location: "westus",
    resourceGroupName: "testRG",
    tags: {
        additionalProp1: "string",
        additionalProp2: "string",
        additionalProp3: "string",
    },
    workspaceName: "workspace1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

iot_connector = azure_native.healthcareapis.IotConnector("iotConnector",
    device_mapping=azure_native.healthcareapis.IotMappingPropertiesArgs(
        content={
            "template": [{
                "template": {
                    "deviceIdExpression": "$.deviceid",
                    "timestampExpression": "$.measurementdatetime",
                    "typeMatchExpression": "$..[?(@heartrate)]",
                    "typeName": "heartrate",
                    "values": [{
                        "required": "true",
                        "valueExpression": "$.heartrate",
                        "valueName": "hr",
                    }],
                },
                "templateType": "JsonPathContent",
            }],
            "templateType": "CollectionContent",
        },
    ),
    identity=azure_native.healthcareapis.ServiceManagedIdentityIdentityArgs(
        type="SystemAssigned",
    ),
    ingestion_endpoint_configuration=azure_native.healthcareapis.IotEventHubIngestionEndpointConfigurationArgs(
        consumer_group="ConsumerGroupA",
        event_hub_name="MyEventHubName",
        fully_qualified_event_hub_namespace="myeventhub.servicesbus.windows.net",
    ),
    iot_connector_name="blue",
    location="westus",
    resource_group_name="testRG",
    tags={
        "additionalProp1": "string",
        "additionalProp2": "string",
        "additionalProp3": "string",
    },
    workspace_name="workspace1")

```

```yaml
resources:
  iotConnector:
    type: azure-native:healthcareapis:IotConnector
    properties:
      deviceMapping:
        content:
          template:
            - template:
                deviceIdExpression: $.deviceid
                timestampExpression: $.measurementdatetime
                typeMatchExpression: $..[?(@heartrate)]
                typeName: heartrate
                values:
                  - required: 'true'
                    valueExpression: $.heartrate
                    valueName: hr
              templateType: JsonPathContent
          templateType: CollectionContent
      identity:
        type: SystemAssigned
      ingestionEndpointConfiguration:
        consumerGroup: ConsumerGroupA
        eventHubName: MyEventHubName
        fullyQualifiedEventHubNamespace: myeventhub.servicesbus.windows.net
      iotConnectorName: blue
      location: westus
      resourceGroupName: testRG
      tags:
        additionalProp1: string
        additionalProp2: string
        additionalProp3: string
      workspaceName: workspace1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:healthcareapis:IotConnector blue /subscriptions/subid/resourceGroups/testRG/providers/Microsoft.HealthcareApis/workspaces/workspace1/iotconnectors/blue 
```
