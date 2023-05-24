The description of the service.
API Version: 2022-12-01.
Previous API Version: 2022-05-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update a service with all parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.HealthcareApis.Service("service", new()
    {
        Identity = new AzureNative.HealthcareApis.Inputs.ServicesResourceIdentityArgs
        {
            Type = "SystemAssigned",
        },
        Kind = AzureNative.HealthcareApis.Kind.Fhir_R4,
        Location = "westus2",
        Properties = new AzureNative.HealthcareApis.Inputs.ServicesPropertiesArgs
        {
            AccessPolicies = new[]
            {
                new AzureNative.HealthcareApis.Inputs.ServiceAccessPolicyEntryArgs
                {
                    ObjectId = "c487e7d1-3210-41a3-8ccc-e9372b78da47",
                },
                new AzureNative.HealthcareApis.Inputs.ServiceAccessPolicyEntryArgs
                {
                    ObjectId = "5b307da8-43d4-492b-8b66-b0294ade872f",
                },
            },
            AuthenticationConfiguration = new AzureNative.HealthcareApis.Inputs.ServiceAuthenticationConfigurationInfoArgs
            {
                Audience = "https://azurehealthcareapis.com",
                Authority = "https://login.microsoftonline.com/abfde7b2-df0f-47e6-aabf-2462b07508dc",
                SmartProxyEnabled = true,
            },
            CorsConfiguration = new AzureNative.HealthcareApis.Inputs.ServiceCorsConfigurationInfoArgs
            {
                AllowCredentials = false,
                Headers = new[]
                {
                    "*",
                },
                MaxAge = 1440,
                Methods = new[]
                {
                    "DELETE",
                    "GET",
                    "OPTIONS",
                    "PATCH",
                    "POST",
                    "PUT",
                },
                Origins = new[]
                {
                    "*",
                },
            },
            CosmosDbConfiguration = new AzureNative.HealthcareApis.Inputs.ServiceCosmosDbConfigurationInfoArgs
            {
                KeyVaultKeyUri = "https://my-vault.vault.azure.net/keys/my-key",
                OfferThroughput = 1000,
            },
            ExportConfiguration = new AzureNative.HealthcareApis.Inputs.ServiceExportConfigurationInfoArgs
            {
                StorageAccountName = "existingStorageAccount",
            },
            PrivateEndpointConnections = new[] {},
            PublicNetworkAccess = "Disabled",
        },
        ResourceGroupName = "rg1",
        ResourceName = "service1",
        Tags = null,
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
		_, err := healthcareapis.NewService(ctx, "service", &healthcareapis.ServiceArgs{
			Identity: &healthcareapis.ServicesResourceIdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			Kind:     healthcareapis.Kind_Fhir_R4,
			Location: pulumi.String("westus2"),
			Properties: healthcareapis.ServicesPropertiesResponse{
				AccessPolicies: healthcareapis.ServiceAccessPolicyEntryArray{
					&healthcareapis.ServiceAccessPolicyEntryArgs{
						ObjectId: pulumi.String("c487e7d1-3210-41a3-8ccc-e9372b78da47"),
					},
					&healthcareapis.ServiceAccessPolicyEntryArgs{
						ObjectId: pulumi.String("5b307da8-43d4-492b-8b66-b0294ade872f"),
					},
				},
				AuthenticationConfiguration: &healthcareapis.ServiceAuthenticationConfigurationInfoArgs{
					Audience:          pulumi.String("https://azurehealthcareapis.com"),
					Authority:         pulumi.String("https://login.microsoftonline.com/abfde7b2-df0f-47e6-aabf-2462b07508dc"),
					SmartProxyEnabled: pulumi.Bool(true),
				},
				CorsConfiguration: &healthcareapis.ServiceCorsConfigurationInfoArgs{
					AllowCredentials: pulumi.Bool(false),
					Headers: pulumi.StringArray{
						pulumi.String("*"),
					},
					MaxAge: pulumi.Int(1440),
					Methods: pulumi.StringArray{
						pulumi.String("DELETE"),
						pulumi.String("GET"),
						pulumi.String("OPTIONS"),
						pulumi.String("PATCH"),
						pulumi.String("POST"),
						pulumi.String("PUT"),
					},
					Origins: pulumi.StringArray{
						pulumi.String("*"),
					},
				},
				CosmosDbConfiguration: &healthcareapis.ServiceCosmosDbConfigurationInfoArgs{
					KeyVaultKeyUri:  pulumi.String("https://my-vault.vault.azure.net/keys/my-key"),
					OfferThroughput: pulumi.Int(1000),
				},
				ExportConfiguration: &healthcareapis.ServiceExportConfigurationInfoArgs{
					StorageAccountName: pulumi.String("existingStorageAccount"),
				},
				PrivateEndpointConnections: healthcareapis.PrivateEndpointConnectionTypeArray{},
				PublicNetworkAccess:        pulumi.String("Disabled"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			ResourceName:      pulumi.String("service1"),
			Tags:              nil,
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
import com.pulumi.azurenative.healthcareapis.Service;
import com.pulumi.azurenative.healthcareapis.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .identity(Map.of("type", "SystemAssigned"))
            .kind("fhir-R4")
            .location("westus2")
            .properties(Map.ofEntries(
                Map.entry("accessPolicies",                 
                    Map.of("objectId", "c487e7d1-3210-41a3-8ccc-e9372b78da47"),
                    Map.of("objectId", "5b307da8-43d4-492b-8b66-b0294ade872f")),
                Map.entry("authenticationConfiguration", Map.ofEntries(
                    Map.entry("audience", "https://azurehealthcareapis.com"),
                    Map.entry("authority", "https://login.microsoftonline.com/abfde7b2-df0f-47e6-aabf-2462b07508dc"),
                    Map.entry("smartProxyEnabled", true)
                )),
                Map.entry("corsConfiguration", Map.ofEntries(
                    Map.entry("allowCredentials", false),
                    Map.entry("headers", "*"),
                    Map.entry("maxAge", 1440),
                    Map.entry("methods",                     
                        "DELETE",
                        "GET",
                        "OPTIONS",
                        "PATCH",
                        "POST",
                        "PUT"),
                    Map.entry("origins", "*")
                )),
                Map.entry("cosmosDbConfiguration", Map.ofEntries(
                    Map.entry("keyVaultKeyUri", "https://my-vault.vault.azure.net/keys/my-key"),
                    Map.entry("offerThroughput", 1000)
                )),
                Map.entry("exportConfiguration", Map.of("storageAccountName", "existingStorageAccount")),
                Map.entry("privateEndpointConnections", ),
                Map.entry("publicNetworkAccess", "Disabled")
            ))
            .resourceGroupName("rg1")
            .resourceName("service1")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.healthcareapis.Service("service", {
    identity: {
        type: "SystemAssigned",
    },
    kind: azure_native.healthcareapis.Kind.Fhir_R4,
    location: "westus2",
    properties: {
        accessPolicies: [
            {
                objectId: "c487e7d1-3210-41a3-8ccc-e9372b78da47",
            },
            {
                objectId: "5b307da8-43d4-492b-8b66-b0294ade872f",
            },
        ],
        authenticationConfiguration: {
            audience: "https://azurehealthcareapis.com",
            authority: "https://login.microsoftonline.com/abfde7b2-df0f-47e6-aabf-2462b07508dc",
            smartProxyEnabled: true,
        },
        corsConfiguration: {
            allowCredentials: false,
            headers: ["*"],
            maxAge: 1440,
            methods: [
                "DELETE",
                "GET",
                "OPTIONS",
                "PATCH",
                "POST",
                "PUT",
            ],
            origins: ["*"],
        },
        cosmosDbConfiguration: {
            keyVaultKeyUri: "https://my-vault.vault.azure.net/keys/my-key",
            offerThroughput: 1000,
        },
        exportConfiguration: {
            storageAccountName: "existingStorageAccount",
        },
        privateEndpointConnections: [],
        publicNetworkAccess: "Disabled",
    },
    resourceGroupName: "rg1",
    resourceName: "service1",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.healthcareapis.Service("service",
    identity=azure_native.healthcareapis.ServicesResourceIdentityArgs(
        type="SystemAssigned",
    ),
    kind=azure_native.healthcareapis.Kind.FHIR_R4,
    location="westus2",
    properties=azure_native.healthcareapis.ServicesPropertiesResponseArgs(
        access_policies=[
            azure_native.healthcareapis.ServiceAccessPolicyEntryArgs(
                object_id="c487e7d1-3210-41a3-8ccc-e9372b78da47",
            ),
            azure_native.healthcareapis.ServiceAccessPolicyEntryArgs(
                object_id="5b307da8-43d4-492b-8b66-b0294ade872f",
            ),
        ],
        authentication_configuration=azure_native.healthcareapis.ServiceAuthenticationConfigurationInfoArgs(
            audience="https://azurehealthcareapis.com",
            authority="https://login.microsoftonline.com/abfde7b2-df0f-47e6-aabf-2462b07508dc",
            smart_proxy_enabled=True,
        ),
        cors_configuration=azure_native.healthcareapis.ServiceCorsConfigurationInfoArgs(
            allow_credentials=False,
            headers=["*"],
            max_age=1440,
            methods=[
                "DELETE",
                "GET",
                "OPTIONS",
                "PATCH",
                "POST",
                "PUT",
            ],
            origins=["*"],
        ),
        cosmos_db_configuration=azure_native.healthcareapis.ServiceCosmosDbConfigurationInfoArgs(
            key_vault_key_uri="https://my-vault.vault.azure.net/keys/my-key",
            offer_throughput=1000,
        ),
        export_configuration=azure_native.healthcareapis.ServiceExportConfigurationInfoArgs(
            storage_account_name="existingStorageAccount",
        ),
        private_endpoint_connections=[],
        public_network_access="Disabled",
    ),
    resource_group_name="rg1",
    resource_name_="service1",
    tags={})

```

```yaml
resources:
  service:
    type: azure-native:healthcareapis:Service
    properties:
      identity:
        type: SystemAssigned
      kind: fhir-R4
      location: westus2
      properties:
        accessPolicies:
          - objectId: c487e7d1-3210-41a3-8ccc-e9372b78da47
          - objectId: 5b307da8-43d4-492b-8b66-b0294ade872f
        authenticationConfiguration:
          audience: https://azurehealthcareapis.com
          authority: https://login.microsoftonline.com/abfde7b2-df0f-47e6-aabf-2462b07508dc
          smartProxyEnabled: true
        corsConfiguration:
          allowCredentials: false
          headers:
            - '*'
          maxAge: 1440
          methods:
            - DELETE
            - GET
            - OPTIONS
            - PATCH
            - POST
            - PUT
          origins:
            - '*'
        cosmosDbConfiguration:
          keyVaultKeyUri: https://my-vault.vault.azure.net/keys/my-key
          offerThroughput: 1000
        exportConfiguration:
          storageAccountName: existingStorageAccount
        privateEndpointConnections: []
        publicNetworkAccess: Disabled
      resourceGroupName: rg1
      resourceName: service1
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create or Update a service with minimum parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.HealthcareApis.Service("service", new()
    {
        Kind = AzureNative.HealthcareApis.Kind.Fhir_R4,
        Location = "westus2",
        Properties = new AzureNative.HealthcareApis.Inputs.ServicesPropertiesArgs
        {
            AccessPolicies = new[]
            {
                new AzureNative.HealthcareApis.Inputs.ServiceAccessPolicyEntryArgs
                {
                    ObjectId = "c487e7d1-3210-41a3-8ccc-e9372b78da47",
                },
            },
        },
        ResourceGroupName = "rg1",
        ResourceName = "service2",
        Tags = null,
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
		_, err := healthcareapis.NewService(ctx, "service", &healthcareapis.ServiceArgs{
			Kind:     healthcareapis.Kind_Fhir_R4,
			Location: pulumi.String("westus2"),
			Properties: healthcareapis.ServicesPropertiesResponse{
				AccessPolicies: healthcareapis.ServiceAccessPolicyEntryArray{
					&healthcareapis.ServiceAccessPolicyEntryArgs{
						ObjectId: pulumi.String("c487e7d1-3210-41a3-8ccc-e9372b78da47"),
					},
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			ResourceName:      pulumi.String("service2"),
			Tags:              nil,
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
import com.pulumi.azurenative.healthcareapis.Service;
import com.pulumi.azurenative.healthcareapis.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .kind("fhir-R4")
            .location("westus2")
            .properties(Map.of("accessPolicies", Map.of("objectId", "c487e7d1-3210-41a3-8ccc-e9372b78da47")))
            .resourceGroupName("rg1")
            .resourceName("service2")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.healthcareapis.Service("service", {
    kind: azure_native.healthcareapis.Kind.Fhir_R4,
    location: "westus2",
    properties: {
        accessPolicies: [{
            objectId: "c487e7d1-3210-41a3-8ccc-e9372b78da47",
        }],
    },
    resourceGroupName: "rg1",
    resourceName: "service2",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.healthcareapis.Service("service",
    kind=azure_native.healthcareapis.Kind.FHIR_R4,
    location="westus2",
    properties=azure_native.healthcareapis.ServicesPropertiesResponseArgs(
        access_policies=[azure_native.healthcareapis.ServiceAccessPolicyEntryArgs(
            object_id="c487e7d1-3210-41a3-8ccc-e9372b78da47",
        )],
    ),
    resource_group_name="rg1",
    resource_name_="service2",
    tags={})

```

```yaml
resources:
  service:
    type: azure-native:healthcareapis:Service
    properties:
      kind: fhir-R4
      location: westus2
      properties:
        accessPolicies:
          - objectId: c487e7d1-3210-41a3-8ccc-e9372b78da47
      resourceGroupName: rg1
      resourceName: service2
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:healthcareapis:Service service2 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.HealthcareApis/services/service2 
```
