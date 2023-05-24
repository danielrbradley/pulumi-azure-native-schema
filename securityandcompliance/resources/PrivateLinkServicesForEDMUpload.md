The description of the service.
API Version: 2021-03-08.
Previous API Version: 2021-03-08. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var privateLinkServicesForEDMUpload = new AzureNative.SecurityAndCompliance.PrivateLinkServicesForEDMUpload("privateLinkServicesForEDMUpload", new()
    {
        Identity = new AzureNative.SecurityAndCompliance.Inputs.ServicesResourceIdentityArgs
        {
            Type = "SystemAssigned",
        },
        Kind = AzureNative.SecurityAndCompliance.Kind.Fhir_R4,
        Location = "westus2",
        Properties = new AzureNative.SecurityAndCompliance.Inputs.ServicesPropertiesArgs
        {
            AccessPolicies = new[]
            {
                new AzureNative.SecurityAndCompliance.Inputs.ServiceAccessPolicyEntryArgs
                {
                    ObjectId = "c487e7d1-3210-41a3-8ccc-e9372b78da47",
                },
                new AzureNative.SecurityAndCompliance.Inputs.ServiceAccessPolicyEntryArgs
                {
                    ObjectId = "5b307da8-43d4-492b-8b66-b0294ade872f",
                },
            },
            AuthenticationConfiguration = new AzureNative.SecurityAndCompliance.Inputs.ServiceAuthenticationConfigurationInfoArgs
            {
                Audience = "https://azurehealthcareapis.com",
                Authority = "https://login.microsoftonline.com/abfde7b2-df0f-47e6-aabf-2462b07508dc",
                SmartProxyEnabled = true,
            },
            CorsConfiguration = new AzureNative.SecurityAndCompliance.Inputs.ServiceCorsConfigurationInfoArgs
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
            CosmosDbConfiguration = new AzureNative.SecurityAndCompliance.Inputs.ServiceCosmosDbConfigurationInfoArgs
            {
                KeyVaultKeyUri = "https://my-vault.vault.azure.net/keys/my-key",
                OfferThroughput = 1000,
            },
            ExportConfiguration = new AzureNative.SecurityAndCompliance.Inputs.ServiceExportConfigurationInfoArgs
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
	securityandcompliance "github.com/pulumi/pulumi-azure-native-sdk/securityandcompliance"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := securityandcompliance.NewPrivateLinkServicesForEDMUpload(ctx, "privateLinkServicesForEDMUpload", &securityandcompliance.PrivateLinkServicesForEDMUploadArgs{
			Identity: &securityandcompliance.ServicesResourceIdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			Kind:     securityandcompliance.Kind_Fhir_R4,
			Location: pulumi.String("westus2"),
			Properties: securityandcompliance.ServicesPropertiesResponse{
				AccessPolicies: securityandcompliance.ServiceAccessPolicyEntryArray{
					&securityandcompliance.ServiceAccessPolicyEntryArgs{
						ObjectId: pulumi.String("c487e7d1-3210-41a3-8ccc-e9372b78da47"),
					},
					&securityandcompliance.ServiceAccessPolicyEntryArgs{
						ObjectId: pulumi.String("5b307da8-43d4-492b-8b66-b0294ade872f"),
					},
				},
				AuthenticationConfiguration: &securityandcompliance.ServiceAuthenticationConfigurationInfoArgs{
					Audience:          pulumi.String("https://azurehealthcareapis.com"),
					Authority:         pulumi.String("https://login.microsoftonline.com/abfde7b2-df0f-47e6-aabf-2462b07508dc"),
					SmartProxyEnabled: pulumi.Bool(true),
				},
				CorsConfiguration: &securityandcompliance.ServiceCorsConfigurationInfoArgs{
					AllowCredentials: pulumi.Bool(false),
					Headers: pulumi.StringArray{
						pulumi.String("*"),
					},
					MaxAge: pulumi.Float64(1440),
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
				CosmosDbConfiguration: &securityandcompliance.ServiceCosmosDbConfigurationInfoArgs{
					KeyVaultKeyUri:  pulumi.String("https://my-vault.vault.azure.net/keys/my-key"),
					OfferThroughput: pulumi.Float64(1000),
				},
				ExportConfiguration: &securityandcompliance.ServiceExportConfigurationInfoArgs{
					StorageAccountName: pulumi.String("existingStorageAccount"),
				},
				PrivateEndpointConnections: securityandcompliance.PrivateEndpointConnectionArray{},
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
import com.pulumi.azurenative.securityandcompliance.PrivateLinkServicesForEDMUpload;
import com.pulumi.azurenative.securityandcompliance.PrivateLinkServicesForEDMUploadArgs;
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
        var privateLinkServicesForEDMUpload = new PrivateLinkServicesForEDMUpload("privateLinkServicesForEDMUpload", PrivateLinkServicesForEDMUploadArgs.builder()        
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

const privateLinkServicesForEDMUpload = new azure_native.securityandcompliance.PrivateLinkServicesForEDMUpload("privateLinkServicesForEDMUpload", {
    identity: {
        type: "SystemAssigned",
    },
    kind: azure_native.securityandcompliance.Kind.Fhir_R4,
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

private_link_services_for_edm_upload = azure_native.securityandcompliance.PrivateLinkServicesForEDMUpload("privateLinkServicesForEDMUpload",
    identity=azure_native.securityandcompliance.ServicesResourceIdentityArgs(
        type="SystemAssigned",
    ),
    kind=azure_native.securityandcompliance.Kind.FHIR_R4,
    location="westus2",
    properties=azure_native.securityandcompliance.ServicesPropertiesResponseArgs(
        access_policies=[
            azure_native.securityandcompliance.ServiceAccessPolicyEntryArgs(
                object_id="c487e7d1-3210-41a3-8ccc-e9372b78da47",
            ),
            azure_native.securityandcompliance.ServiceAccessPolicyEntryArgs(
                object_id="5b307da8-43d4-492b-8b66-b0294ade872f",
            ),
        ],
        authentication_configuration=azure_native.securityandcompliance.ServiceAuthenticationConfigurationInfoArgs(
            audience="https://azurehealthcareapis.com",
            authority="https://login.microsoftonline.com/abfde7b2-df0f-47e6-aabf-2462b07508dc",
            smart_proxy_enabled=True,
        ),
        cors_configuration=azure_native.securityandcompliance.ServiceCorsConfigurationInfoArgs(
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
        cosmos_db_configuration=azure_native.securityandcompliance.ServiceCosmosDbConfigurationInfoArgs(
            key_vault_key_uri="https://my-vault.vault.azure.net/keys/my-key",
            offer_throughput=1000,
        ),
        export_configuration=azure_native.securityandcompliance.ServiceExportConfigurationInfoArgs(
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
  privateLinkServicesForEDMUpload:
    type: azure-native:securityandcompliance:PrivateLinkServicesForEDMUpload
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
    var privateLinkServicesForEDMUpload = new AzureNative.SecurityAndCompliance.PrivateLinkServicesForEDMUpload("privateLinkServicesForEDMUpload", new()
    {
        Kind = AzureNative.SecurityAndCompliance.Kind.Fhir_R4,
        Location = "westus2",
        Properties = new AzureNative.SecurityAndCompliance.Inputs.ServicesPropertiesArgs
        {
            AccessPolicies = new[]
            {
                new AzureNative.SecurityAndCompliance.Inputs.ServiceAccessPolicyEntryArgs
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
	securityandcompliance "github.com/pulumi/pulumi-azure-native-sdk/securityandcompliance"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := securityandcompliance.NewPrivateLinkServicesForEDMUpload(ctx, "privateLinkServicesForEDMUpload", &securityandcompliance.PrivateLinkServicesForEDMUploadArgs{
			Kind:     securityandcompliance.Kind_Fhir_R4,
			Location: pulumi.String("westus2"),
			Properties: securityandcompliance.ServicesPropertiesResponse{
				AccessPolicies: securityandcompliance.ServiceAccessPolicyEntryArray{
					&securityandcompliance.ServiceAccessPolicyEntryArgs{
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
import com.pulumi.azurenative.securityandcompliance.PrivateLinkServicesForEDMUpload;
import com.pulumi.azurenative.securityandcompliance.PrivateLinkServicesForEDMUploadArgs;
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
        var privateLinkServicesForEDMUpload = new PrivateLinkServicesForEDMUpload("privateLinkServicesForEDMUpload", PrivateLinkServicesForEDMUploadArgs.builder()        
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

const privateLinkServicesForEDMUpload = new azure_native.securityandcompliance.PrivateLinkServicesForEDMUpload("privateLinkServicesForEDMUpload", {
    kind: azure_native.securityandcompliance.Kind.Fhir_R4,
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

private_link_services_for_edm_upload = azure_native.securityandcompliance.PrivateLinkServicesForEDMUpload("privateLinkServicesForEDMUpload",
    kind=azure_native.securityandcompliance.Kind.FHIR_R4,
    location="westus2",
    properties=azure_native.securityandcompliance.ServicesPropertiesResponseArgs(
        access_policies=[azure_native.securityandcompliance.ServiceAccessPolicyEntryArgs(
            object_id="c487e7d1-3210-41a3-8ccc-e9372b78da47",
        )],
    ),
    resource_group_name="rg1",
    resource_name_="service2",
    tags={})

```

```yaml
resources:
  privateLinkServicesForEDMUpload:
    type: azure-native:securityandcompliance:PrivateLinkServicesForEDMUpload
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
$ pulumi import azure-native:securityandcompliance:PrivateLinkServicesForEDMUpload service2 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.SecurityAndCompliance/privateLinkServicesForEDMUpload/service2 
```
