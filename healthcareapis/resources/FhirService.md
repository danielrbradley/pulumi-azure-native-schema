The description of Fhir Service
API Version: 2022-12-01.
Previous API Version: 2022-05-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a Fhir Service
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var fhirService = new AzureNative.HealthcareApis.FhirService("fhirService", new()
    {
        AccessPolicies = new[]
        {
            new AzureNative.HealthcareApis.Inputs.FhirServiceAccessPolicyEntryArgs
            {
                ObjectId = "c487e7d1-3210-41a3-8ccc-e9372b78da47",
            },
            new AzureNative.HealthcareApis.Inputs.FhirServiceAccessPolicyEntryArgs
            {
                ObjectId = "5b307da8-43d4-492b-8b66-b0294ade872f",
            },
        },
        AcrConfiguration = new AzureNative.HealthcareApis.Inputs.FhirServiceAcrConfigurationArgs
        {
            LoginServers = new[]
            {
                "test1.azurecr.io",
            },
        },
        AuthenticationConfiguration = new AzureNative.HealthcareApis.Inputs.FhirServiceAuthenticationConfigurationArgs
        {
            Audience = "https://azurehealthcareapis.com",
            Authority = "https://login.microsoftonline.com/abfde7b2-df0f-47e6-aabf-2462b07508dc",
            SmartProxyEnabled = true,
        },
        CorsConfiguration = new AzureNative.HealthcareApis.Inputs.FhirServiceCorsConfigurationArgs
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
        ExportConfiguration = new AzureNative.HealthcareApis.Inputs.FhirServiceExportConfigurationArgs
        {
            StorageAccountName = "existingStorageAccount",
        },
        FhirServiceName = "fhirservice1",
        Identity = new AzureNative.HealthcareApis.Inputs.ServiceManagedIdentityIdentityArgs
        {
            Type = "SystemAssigned",
        },
        ImplementationGuidesConfiguration = new AzureNative.HealthcareApis.Inputs.ImplementationGuidesConfigurationArgs
        {
            UsCoreMissingData = false,
        },
        ImportConfiguration = new AzureNative.HealthcareApis.Inputs.FhirServiceImportConfigurationArgs
        {
            Enabled = false,
            InitialImportMode = false,
            IntegrationDataStore = "existingStorageAccount",
        },
        Kind = "fhir-R4",
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
		_, err := healthcareapis.NewFhirService(ctx, "fhirService", &healthcareapis.FhirServiceArgs{
			AccessPolicies: []healthcareapis.FhirServiceAccessPolicyEntryArgs{
				{
					ObjectId: pulumi.String("c487e7d1-3210-41a3-8ccc-e9372b78da47"),
				},
				{
					ObjectId: pulumi.String("5b307da8-43d4-492b-8b66-b0294ade872f"),
				},
			},
			AcrConfiguration: &healthcareapis.FhirServiceAcrConfigurationArgs{
				LoginServers: pulumi.StringArray{
					pulumi.String("test1.azurecr.io"),
				},
			},
			AuthenticationConfiguration: &healthcareapis.FhirServiceAuthenticationConfigurationArgs{
				Audience:          pulumi.String("https://azurehealthcareapis.com"),
				Authority:         pulumi.String("https://login.microsoftonline.com/abfde7b2-df0f-47e6-aabf-2462b07508dc"),
				SmartProxyEnabled: pulumi.Bool(true),
			},
			CorsConfiguration: &healthcareapis.FhirServiceCorsConfigurationArgs{
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
			ExportConfiguration: &healthcareapis.FhirServiceExportConfigurationArgs{
				StorageAccountName: pulumi.String("existingStorageAccount"),
			},
			FhirServiceName: pulumi.String("fhirservice1"),
			Identity: &healthcareapis.ServiceManagedIdentityIdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			ImplementationGuidesConfiguration: &healthcareapis.ImplementationGuidesConfigurationArgs{
				UsCoreMissingData: pulumi.Bool(false),
			},
			ImportConfiguration: &healthcareapis.FhirServiceImportConfigurationArgs{
				Enabled:              pulumi.Bool(false),
				InitialImportMode:    pulumi.Bool(false),
				IntegrationDataStore: pulumi.String("existingStorageAccount"),
			},
			Kind:              pulumi.String("fhir-R4"),
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
import com.pulumi.azurenative.healthcareapis.FhirService;
import com.pulumi.azurenative.healthcareapis.FhirServiceArgs;
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
        var fhirService = new FhirService("fhirService", FhirServiceArgs.builder()        
            .accessPolicies(            
                Map.of("objectId", "c487e7d1-3210-41a3-8ccc-e9372b78da47"),
                Map.of("objectId", "5b307da8-43d4-492b-8b66-b0294ade872f"))
            .acrConfiguration(Map.of("loginServers", "test1.azurecr.io"))
            .authenticationConfiguration(Map.ofEntries(
                Map.entry("audience", "https://azurehealthcareapis.com"),
                Map.entry("authority", "https://login.microsoftonline.com/abfde7b2-df0f-47e6-aabf-2462b07508dc"),
                Map.entry("smartProxyEnabled", true)
            ))
            .corsConfiguration(Map.ofEntries(
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
            ))
            .exportConfiguration(Map.of("storageAccountName", "existingStorageAccount"))
            .fhirServiceName("fhirservice1")
            .identity(Map.of("type", "SystemAssigned"))
            .implementationGuidesConfiguration(Map.of("usCoreMissingData", false))
            .importConfiguration(Map.ofEntries(
                Map.entry("enabled", false),
                Map.entry("initialImportMode", false),
                Map.entry("integrationDataStore", "existingStorageAccount")
            ))
            .kind("fhir-R4")
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

const fhirService = new azure_native.healthcareapis.FhirService("fhirService", {
    accessPolicies: [
        {
            objectId: "c487e7d1-3210-41a3-8ccc-e9372b78da47",
        },
        {
            objectId: "5b307da8-43d4-492b-8b66-b0294ade872f",
        },
    ],
    acrConfiguration: {
        loginServers: ["test1.azurecr.io"],
    },
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
    exportConfiguration: {
        storageAccountName: "existingStorageAccount",
    },
    fhirServiceName: "fhirservice1",
    identity: {
        type: "SystemAssigned",
    },
    implementationGuidesConfiguration: {
        usCoreMissingData: false,
    },
    importConfiguration: {
        enabled: false,
        initialImportMode: false,
        integrationDataStore: "existingStorageAccount",
    },
    kind: "fhir-R4",
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

fhir_service = azure_native.healthcareapis.FhirService("fhirService",
    access_policies=[
        azure_native.healthcareapis.FhirServiceAccessPolicyEntryArgs(
            object_id="c487e7d1-3210-41a3-8ccc-e9372b78da47",
        ),
        azure_native.healthcareapis.FhirServiceAccessPolicyEntryArgs(
            object_id="5b307da8-43d4-492b-8b66-b0294ade872f",
        ),
    ],
    acr_configuration=azure_native.healthcareapis.FhirServiceAcrConfigurationArgs(
        login_servers=["test1.azurecr.io"],
    ),
    authentication_configuration=azure_native.healthcareapis.FhirServiceAuthenticationConfigurationArgs(
        audience="https://azurehealthcareapis.com",
        authority="https://login.microsoftonline.com/abfde7b2-df0f-47e6-aabf-2462b07508dc",
        smart_proxy_enabled=True,
    ),
    cors_configuration=azure_native.healthcareapis.FhirServiceCorsConfigurationArgs(
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
    export_configuration=azure_native.healthcareapis.FhirServiceExportConfigurationArgs(
        storage_account_name="existingStorageAccount",
    ),
    fhir_service_name="fhirservice1",
    identity=azure_native.healthcareapis.ServiceManagedIdentityIdentityArgs(
        type="SystemAssigned",
    ),
    implementation_guides_configuration=azure_native.healthcareapis.ImplementationGuidesConfigurationArgs(
        us_core_missing_data=False,
    ),
    import_configuration=azure_native.healthcareapis.FhirServiceImportConfigurationArgs(
        enabled=False,
        initial_import_mode=False,
        integration_data_store="existingStorageAccount",
    ),
    kind="fhir-R4",
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
  fhirService:
    type: azure-native:healthcareapis:FhirService
    properties:
      accessPolicies:
        - objectId: c487e7d1-3210-41a3-8ccc-e9372b78da47
        - objectId: 5b307da8-43d4-492b-8b66-b0294ade872f
      acrConfiguration:
        loginServers:
          - test1.azurecr.io
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
      exportConfiguration:
        storageAccountName: existingStorageAccount
      fhirServiceName: fhirservice1
      identity:
        type: SystemAssigned
      implementationGuidesConfiguration:
        usCoreMissingData: false
      importConfiguration:
        enabled: false
        initialImportMode: false
        integrationDataStore: existingStorageAccount
      kind: fhir-R4
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
$ pulumi import azure-native:healthcareapis:FhirService fhirservice1 /subscriptions/subid/resourceGroups/testRG/providers/Microsoft.HealthcareApis/workspaces/workspace1/fhirservices/fhirservice1 
```
