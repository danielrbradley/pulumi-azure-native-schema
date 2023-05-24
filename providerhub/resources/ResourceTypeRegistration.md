
API Version: 2020-11-20.
Previous API Version: 2020-11-20. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ResourceTypeRegistrations_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var resourceTypeRegistration = new AzureNative.ProviderHub.ResourceTypeRegistration("resourceTypeRegistration", new()
    {
        Properties = new AzureNative.ProviderHub.Inputs.ResourceTypeRegistrationPropertiesArgs
        {
            Endpoints = new[]
            {
                new AzureNative.ProviderHub.Inputs.ResourceTypeEndpointArgs
                {
                    ApiVersions = new[]
                    {
                        "2020-06-01-preview",
                    },
                    Locations = new[]
                    {
                        "West US",
                        "East US",
                        "North Europe",
                    },
                    RequiredFeatures = new[]
                    {
                        "<feature flag>",
                    },
                },
            },
            Regionality = "Regional",
            RoutingType = "Default",
            SwaggerSpecifications = new[]
            {
                new AzureNative.ProviderHub.Inputs.SwaggerSpecificationArgs
                {
                    ApiVersions = new[]
                    {
                        "2020-06-01-preview",
                    },
                    SwaggerSpecFolderUri = "https://github.com/Azure/azure-rest-api-specs/blob/feature/azure/contoso/specification/contoso/resource-manager/Microsoft.SampleRP/",
                },
            },
        },
        ProviderNamespace = "Microsoft.Contoso",
        ResourceType = "employees",
    });

});


```

```go
package main

import (
	providerhub "github.com/pulumi/pulumi-azure-native-sdk/providerhub"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := providerhub.NewResourceTypeRegistration(ctx, "resourceTypeRegistration", &providerhub.ResourceTypeRegistrationArgs{
			Properties: providerhub.ResourceTypeRegistrationResponseProperties{
				Endpoints: providerhub.ResourceTypeEndpointArray{
					&providerhub.ResourceTypeEndpointArgs{
						ApiVersions: pulumi.StringArray{
							pulumi.String("2020-06-01-preview"),
						},
						Locations: pulumi.StringArray{
							pulumi.String("West US"),
							pulumi.String("East US"),
							pulumi.String("North Europe"),
						},
						RequiredFeatures: pulumi.StringArray{
							pulumi.String("<feature flag>"),
						},
					},
				},
				Regionality: pulumi.String("Regional"),
				RoutingType: pulumi.String("Default"),
				SwaggerSpecifications: providerhub.SwaggerSpecificationArray{
					&providerhub.SwaggerSpecificationArgs{
						ApiVersions: pulumi.StringArray{
							pulumi.String("2020-06-01-preview"),
						},
						SwaggerSpecFolderUri: pulumi.String("https://github.com/Azure/azure-rest-api-specs/blob/feature/azure/contoso/specification/contoso/resource-manager/Microsoft.SampleRP/"),
					},
				},
			},
			ProviderNamespace: pulumi.String("Microsoft.Contoso"),
			ResourceType:      pulumi.String("employees"),
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
import com.pulumi.azurenative.providerhub.ResourceTypeRegistration;
import com.pulumi.azurenative.providerhub.ResourceTypeRegistrationArgs;
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
        var resourceTypeRegistration = new ResourceTypeRegistration("resourceTypeRegistration", ResourceTypeRegistrationArgs.builder()        
            .properties(Map.ofEntries(
                Map.entry("endpoints", Map.ofEntries(
                    Map.entry("apiVersions", "2020-06-01-preview"),
                    Map.entry("locations",                     
                        "West US",
                        "East US",
                        "North Europe"),
                    Map.entry("requiredFeatures", "<feature flag>")
                )),
                Map.entry("regionality", "Regional"),
                Map.entry("routingType", "Default"),
                Map.entry("swaggerSpecifications", Map.ofEntries(
                    Map.entry("apiVersions", "2020-06-01-preview"),
                    Map.entry("swaggerSpecFolderUri", "https://github.com/Azure/azure-rest-api-specs/blob/feature/azure/contoso/specification/contoso/resource-manager/Microsoft.SampleRP/")
                ))
            ))
            .providerNamespace("Microsoft.Contoso")
            .resourceType("employees")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const resourceTypeRegistration = new azure_native.providerhub.ResourceTypeRegistration("resourceTypeRegistration", {
    properties: {
        endpoints: [{
            apiVersions: ["2020-06-01-preview"],
            locations: [
                "West US",
                "East US",
                "North Europe",
            ],
            requiredFeatures: ["<feature flag>"],
        }],
        regionality: "Regional",
        routingType: "Default",
        swaggerSpecifications: [{
            apiVersions: ["2020-06-01-preview"],
            swaggerSpecFolderUri: "https://github.com/Azure/azure-rest-api-specs/blob/feature/azure/contoso/specification/contoso/resource-manager/Microsoft.SampleRP/",
        }],
    },
    providerNamespace: "Microsoft.Contoso",
    resourceType: "employees",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

resource_type_registration = azure_native.providerhub.ResourceTypeRegistration("resourceTypeRegistration",
    properties=azure_native.providerhub.ResourceTypeRegistrationResponsePropertiesArgs(
        endpoints=[azure_native.providerhub.ResourceTypeEndpointArgs(
            api_versions=["2020-06-01-preview"],
            locations=[
                "West US",
                "East US",
                "North Europe",
            ],
            required_features=["<feature flag>"],
        )],
        regionality="Regional",
        routing_type="Default",
        swagger_specifications=[azure_native.providerhub.SwaggerSpecificationArgs(
            api_versions=["2020-06-01-preview"],
            swagger_spec_folder_uri="https://github.com/Azure/azure-rest-api-specs/blob/feature/azure/contoso/specification/contoso/resource-manager/Microsoft.SampleRP/",
        )],
    ),
    provider_namespace="Microsoft.Contoso",
    resource_type="employees")

```

```yaml
resources:
  resourceTypeRegistration:
    type: azure-native:providerhub:ResourceTypeRegistration
    properties:
      properties:
        endpoints:
          - apiVersions:
              - 2020-06-01-preview
            locations:
              - West US
              - East US
              - North Europe
            requiredFeatures:
              - <feature flag>
        regionality: Regional
        routingType: Default
        swaggerSpecifications:
          - apiVersions:
              - 2020-06-01-preview
            swaggerSpecFolderUri: https://github.com/Azure/azure-rest-api-specs/blob/feature/azure/contoso/specification/contoso/resource-manager/Microsoft.SampleRP/
      providerNamespace: Microsoft.Contoso
      resourceType: employees

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:providerhub:ResourceTypeRegistration employees /subscriptions/{subscriptionId}/providers/Microsoft.ProviderHub/providerRegistrations/{providerNamespace}/resourcetypeRegistrations/{resourceType} 
```
