IoT Connector FHIR destination definition.
API Version: 2022-12-01.
Previous API Version: 2022-05-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an Iot Connector FHIR destination
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var iotConnectorFhirDestination = new AzureNative.HealthcareApis.IotConnectorFhirDestination("iotConnectorFhirDestination", new()
    {
        FhirDestinationName = "dest1",
        FhirMapping = new AzureNative.HealthcareApis.Inputs.IotMappingPropertiesArgs
        {
            Content = 
            {
                { "template", new[]
                {
                    
                    {
                        { "template", 
                        {
                            { "codes", new[]
                            {
                                
                                {
                                    { "code", "8867-4" },
                                    { "display", "Heart rate" },
                                    { "system", "http://loinc.org" },
                                },
                            } },
                            { "periodInterval", 60 },
                            { "typeName", "heartrate" },
                            { "value", 
                            {
                                { "defaultPeriod", 5000 },
                                { "unit", "count/min" },
                                { "valueName", "hr" },
                                { "valueType", "SampledData" },
                            } },
                        } },
                        { "templateType", "CodeValueFhir" },
                    },
                } },
                { "templateType", "CollectionFhirTemplate" },
            },
        },
        FhirServiceResourceId = "subscriptions/11111111-2222-3333-4444-555566667777/resourceGroups/myrg/providers/Microsoft.HealthcareApis/workspaces/myworkspace/fhirservices/myfhirservice",
        IotConnectorName = "blue",
        Location = "westus",
        ResourceGroupName = "testRG",
        ResourceIdentityResolutionType = "Create",
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
		_, err := healthcareapis.NewIotConnectorFhirDestination(ctx, "iotConnectorFhirDestination", &healthcareapis.IotConnectorFhirDestinationArgs{
			FhirDestinationName: pulumi.String("dest1"),
			FhirMapping: &healthcareapis.IotMappingPropertiesArgs{
				Content: pulumi.Any{
					Template: []map[string]interface{}{
						map[string]interface{}{
							"template": map[string]interface{}{
								"codes": []map[string]interface{}{
									map[string]interface{}{
										"code":    "8867-4",
										"display": "Heart rate",
										"system":  "http://loinc.org",
									},
								},
								"periodInterval": 60,
								"typeName":       "heartrate",
								"value": map[string]interface{}{
									"defaultPeriod": 5000,
									"unit":          "count/min",
									"valueName":     "hr",
									"valueType":     "SampledData",
								},
							},
							"templateType": "CodeValueFhir",
						},
					},
					TemplateType: "CollectionFhirTemplate",
				},
			},
			FhirServiceResourceId:          pulumi.String("subscriptions/11111111-2222-3333-4444-555566667777/resourceGroups/myrg/providers/Microsoft.HealthcareApis/workspaces/myworkspace/fhirservices/myfhirservice"),
			IotConnectorName:               pulumi.String("blue"),
			Location:                       pulumi.String("westus"),
			ResourceGroupName:              pulumi.String("testRG"),
			ResourceIdentityResolutionType: pulumi.String("Create"),
			WorkspaceName:                  pulumi.String("workspace1"),
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
import com.pulumi.azurenative.healthcareapis.IotConnectorFhirDestination;
import com.pulumi.azurenative.healthcareapis.IotConnectorFhirDestinationArgs;
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
        var iotConnectorFhirDestination = new IotConnectorFhirDestination("iotConnectorFhirDestination", IotConnectorFhirDestinationArgs.builder()        
            .fhirDestinationName("dest1")
            .fhirMapping(Map.of("content", Map.ofEntries(
                Map.entry("template", IotMappingPropertiesArgs.builder()
                    .template(%!v(PANIC=Format method: runtime error: invalid memory address or nil pointer dereference))
                    .templateType("CodeValueFhir")
                    .build()),
                Map.entry("templateType", "CollectionFhirTemplate")
            )))
            .fhirServiceResourceId("subscriptions/11111111-2222-3333-4444-555566667777/resourceGroups/myrg/providers/Microsoft.HealthcareApis/workspaces/myworkspace/fhirservices/myfhirservice")
            .iotConnectorName("blue")
            .location("westus")
            .resourceGroupName("testRG")
            .resourceIdentityResolutionType("Create")
            .workspaceName("workspace1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const iotConnectorFhirDestination = new azure_native.healthcareapis.IotConnectorFhirDestination("iotConnectorFhirDestination", {
    fhirDestinationName: "dest1",
    fhirMapping: {
        content: {
            template: [{
                template: {
                    codes: [{
                        code: "8867-4",
                        display: "Heart rate",
                        system: "http://loinc.org",
                    }],
                    periodInterval: 60,
                    typeName: "heartrate",
                    value: {
                        defaultPeriod: 5000,
                        unit: "count/min",
                        valueName: "hr",
                        valueType: "SampledData",
                    },
                },
                templateType: "CodeValueFhir",
            }],
            templateType: "CollectionFhirTemplate",
        },
    },
    fhirServiceResourceId: "subscriptions/11111111-2222-3333-4444-555566667777/resourceGroups/myrg/providers/Microsoft.HealthcareApis/workspaces/myworkspace/fhirservices/myfhirservice",
    iotConnectorName: "blue",
    location: "westus",
    resourceGroupName: "testRG",
    resourceIdentityResolutionType: "Create",
    workspaceName: "workspace1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

iot_connector_fhir_destination = azure_native.healthcareapis.IotConnectorFhirDestination("iotConnectorFhirDestination",
    fhir_destination_name="dest1",
    fhir_mapping=azure_native.healthcareapis.IotMappingPropertiesArgs(
        content={
            "template": [{
                "template": {
                    "codes": [{
                        "code": "8867-4",
                        "display": "Heart rate",
                        "system": "http://loinc.org",
                    }],
                    "periodInterval": 60,
                    "typeName": "heartrate",
                    "value": {
                        "defaultPeriod": 5000,
                        "unit": "count/min",
                        "valueName": "hr",
                        "valueType": "SampledData",
                    },
                },
                "templateType": "CodeValueFhir",
            }],
            "templateType": "CollectionFhirTemplate",
        },
    ),
    fhir_service_resource_id="subscriptions/11111111-2222-3333-4444-555566667777/resourceGroups/myrg/providers/Microsoft.HealthcareApis/workspaces/myworkspace/fhirservices/myfhirservice",
    iot_connector_name="blue",
    location="westus",
    resource_group_name="testRG",
    resource_identity_resolution_type="Create",
    workspace_name="workspace1")

```

```yaml
resources:
  iotConnectorFhirDestination:
    type: azure-native:healthcareapis:IotConnectorFhirDestination
    properties:
      fhirDestinationName: dest1
      fhirMapping:
        content:
          template:
            - template:
                codes:
                  - code: 8867-4
                    display: Heart rate
                    system: http://loinc.org
                periodInterval: 60
                typeName: heartrate
                value:
                  defaultPeriod: 5000
                  unit: count/min
                  valueName: hr
                  valueType: SampledData
              templateType: CodeValueFhir
          templateType: CollectionFhirTemplate
      fhirServiceResourceId: subscriptions/11111111-2222-3333-4444-555566667777/resourceGroups/myrg/providers/Microsoft.HealthcareApis/workspaces/myworkspace/fhirservices/myfhirservice
      iotConnectorName: blue
      location: westus
      resourceGroupName: testRG
      resourceIdentityResolutionType: Create
      workspaceName: workspace1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:healthcareapis:IotConnectorFhirDestination dest1 /subscriptions/subid/resourceGroups/testRG/providers/Microsoft.HealthcareApis/workspaces/workspace1/iotconnectors/blue/fhirdestinations/dest1 
```
