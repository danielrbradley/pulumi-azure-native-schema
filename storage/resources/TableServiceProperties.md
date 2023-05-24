The properties of a storage account’s Table service.
API Version: 2022-09-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### TableServicesPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var tableServiceProperties = new AzureNative.Storage.TableServiceProperties("tableServiceProperties", new()
    {
        AccountName = "sto8607",
        Cors = new AzureNative.Storage.Inputs.CorsRulesArgs
        {
            CorsRules = new[]
            {
                new AzureNative.Storage.Inputs.CorsRuleArgs
                {
                    AllowedHeaders = new[]
                    {
                        "x-ms-meta-abc",
                        "x-ms-meta-data*",
                        "x-ms-meta-target*",
                    },
                    AllowedMethods = new[]
                    {
                        "GET",
                        "HEAD",
                        "POST",
                        "OPTIONS",
                        "MERGE",
                        "PUT",
                    },
                    AllowedOrigins = new[]
                    {
                        "http://www.contoso.com",
                        "http://www.fabrikam.com",
                    },
                    ExposedHeaders = new[]
                    {
                        "x-ms-meta-*",
                    },
                    MaxAgeInSeconds = 100,
                },
                new AzureNative.Storage.Inputs.CorsRuleArgs
                {
                    AllowedHeaders = new[]
                    {
                        "*",
                    },
                    AllowedMethods = new[]
                    {
                        "GET",
                    },
                    AllowedOrigins = new[]
                    {
                        "*",
                    },
                    ExposedHeaders = new[]
                    {
                        "*",
                    },
                    MaxAgeInSeconds = 2,
                },
                new AzureNative.Storage.Inputs.CorsRuleArgs
                {
                    AllowedHeaders = new[]
                    {
                        "x-ms-meta-12345675754564*",
                    },
                    AllowedMethods = new[]
                    {
                        "GET",
                        "PUT",
                    },
                    AllowedOrigins = new[]
                    {
                        "http://www.abc23.com",
                        "https://www.fabrikam.com/*",
                    },
                    ExposedHeaders = new[]
                    {
                        "x-ms-meta-abc",
                        "x-ms-meta-data*",
                        "x-ms-meta-target*",
                    },
                    MaxAgeInSeconds = 2000,
                },
            },
        },
        ResourceGroupName = "res4410",
        TableServiceName = "default",
    });

});


```

```go
package main

import (
	storage "github.com/pulumi/pulumi-azure-native-sdk/storage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storage.NewTableServiceProperties(ctx, "tableServiceProperties", &storage.TableServicePropertiesArgs{
			AccountName: pulumi.String("sto8607"),
			Cors: storage.CorsRulesResponse{
				CorsRules: storage.CorsRuleArray{
					&storage.CorsRuleArgs{
						AllowedHeaders: pulumi.StringArray{
							pulumi.String("x-ms-meta-abc"),
							pulumi.String("x-ms-meta-data*"),
							pulumi.String("x-ms-meta-target*"),
						},
						AllowedMethods: pulumi.StringArray{
							pulumi.String("GET"),
							pulumi.String("HEAD"),
							pulumi.String("POST"),
							pulumi.String("OPTIONS"),
							pulumi.String("MERGE"),
							pulumi.String("PUT"),
						},
						AllowedOrigins: pulumi.StringArray{
							pulumi.String("http://www.contoso.com"),
							pulumi.String("http://www.fabrikam.com"),
						},
						ExposedHeaders: pulumi.StringArray{
							pulumi.String("x-ms-meta-*"),
						},
						MaxAgeInSeconds: pulumi.Int(100),
					},
					&storage.CorsRuleArgs{
						AllowedHeaders: pulumi.StringArray{
							pulumi.String("*"),
						},
						AllowedMethods: pulumi.StringArray{
							pulumi.String("GET"),
						},
						AllowedOrigins: pulumi.StringArray{
							pulumi.String("*"),
						},
						ExposedHeaders: pulumi.StringArray{
							pulumi.String("*"),
						},
						MaxAgeInSeconds: pulumi.Int(2),
					},
					&storage.CorsRuleArgs{
						AllowedHeaders: pulumi.StringArray{
							pulumi.String("x-ms-meta-12345675754564*"),
						},
						AllowedMethods: pulumi.StringArray{
							pulumi.String("GET"),
							pulumi.String("PUT"),
						},
						AllowedOrigins: pulumi.StringArray{
							pulumi.String("http://www.abc23.com"),
							pulumi.String("https://www.fabrikam.com/*"),
						},
						ExposedHeaders: pulumi.StringArray{
							pulumi.String("x-ms-meta-abc"),
							pulumi.String("x-ms-meta-data*"),
							pulumi.String("x-ms-meta-target*"),
						},
						MaxAgeInSeconds: pulumi.Int(2000),
					},
				},
			},
			ResourceGroupName: pulumi.String("res4410"),
			TableServiceName:  pulumi.String("default"),
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
import com.pulumi.azurenative.storage.TableServiceProperties;
import com.pulumi.azurenative.storage.TableServicePropertiesArgs;
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
        var tableServiceProperties = new TableServiceProperties("tableServiceProperties", TableServicePropertiesArgs.builder()        
            .accountName("sto8607")
            .cors(Map.of("corsRules",             
                Map.ofEntries(
                    Map.entry("allowedHeaders",                     
                        "x-ms-meta-abc",
                        "x-ms-meta-data*",
                        "x-ms-meta-target*"),
                    Map.entry("allowedMethods",                     
                        "GET",
                        "HEAD",
                        "POST",
                        "OPTIONS",
                        "MERGE",
                        "PUT"),
                    Map.entry("allowedOrigins",                     
                        "http://www.contoso.com",
                        "http://www.fabrikam.com"),
                    Map.entry("exposedHeaders", "x-ms-meta-*"),
                    Map.entry("maxAgeInSeconds", 100)
                ),
                Map.ofEntries(
                    Map.entry("allowedHeaders", "*"),
                    Map.entry("allowedMethods", "GET"),
                    Map.entry("allowedOrigins", "*"),
                    Map.entry("exposedHeaders", "*"),
                    Map.entry("maxAgeInSeconds", 2)
                ),
                Map.ofEntries(
                    Map.entry("allowedHeaders", "x-ms-meta-12345675754564*"),
                    Map.entry("allowedMethods",                     
                        "GET",
                        "PUT"),
                    Map.entry("allowedOrigins",                     
                        "http://www.abc23.com",
                        "https://www.fabrikam.com/*"),
                    Map.entry("exposedHeaders",                     
                        "x-ms-meta-abc",
                        "x-ms-meta-data*",
                        "x-ms-meta-target*"),
                    Map.entry("maxAgeInSeconds", 2000)
                )))
            .resourceGroupName("res4410")
            .tableServiceName("default")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const tableServiceProperties = new azure_native.storage.TableServiceProperties("tableServiceProperties", {
    accountName: "sto8607",
    cors: {
        corsRules: [
            {
                allowedHeaders: [
                    "x-ms-meta-abc",
                    "x-ms-meta-data*",
                    "x-ms-meta-target*",
                ],
                allowedMethods: [
                    "GET",
                    "HEAD",
                    "POST",
                    "OPTIONS",
                    "MERGE",
                    "PUT",
                ],
                allowedOrigins: [
                    "http://www.contoso.com",
                    "http://www.fabrikam.com",
                ],
                exposedHeaders: ["x-ms-meta-*"],
                maxAgeInSeconds: 100,
            },
            {
                allowedHeaders: ["*"],
                allowedMethods: ["GET"],
                allowedOrigins: ["*"],
                exposedHeaders: ["*"],
                maxAgeInSeconds: 2,
            },
            {
                allowedHeaders: ["x-ms-meta-12345675754564*"],
                allowedMethods: [
                    "GET",
                    "PUT",
                ],
                allowedOrigins: [
                    "http://www.abc23.com",
                    "https://www.fabrikam.com/*",
                ],
                exposedHeaders: [
                    "x-ms-meta-abc",
                    "x-ms-meta-data*",
                    "x-ms-meta-target*",
                ],
                maxAgeInSeconds: 2000,
            },
        ],
    },
    resourceGroupName: "res4410",
    tableServiceName: "default",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

table_service_properties = azure_native.storage.TableServiceProperties("tableServiceProperties",
    account_name="sto8607",
    cors=azure_native.storage.CorsRulesResponseArgs(
        cors_rules=[
            azure_native.storage.CorsRuleArgs(
                allowed_headers=[
                    "x-ms-meta-abc",
                    "x-ms-meta-data*",
                    "x-ms-meta-target*",
                ],
                allowed_methods=[
                    "GET",
                    "HEAD",
                    "POST",
                    "OPTIONS",
                    "MERGE",
                    "PUT",
                ],
                allowed_origins=[
                    "http://www.contoso.com",
                    "http://www.fabrikam.com",
                ],
                exposed_headers=["x-ms-meta-*"],
                max_age_in_seconds=100,
            ),
            azure_native.storage.CorsRuleArgs(
                allowed_headers=["*"],
                allowed_methods=["GET"],
                allowed_origins=["*"],
                exposed_headers=["*"],
                max_age_in_seconds=2,
            ),
            azure_native.storage.CorsRuleArgs(
                allowed_headers=["x-ms-meta-12345675754564*"],
                allowed_methods=[
                    "GET",
                    "PUT",
                ],
                allowed_origins=[
                    "http://www.abc23.com",
                    "https://www.fabrikam.com/*",
                ],
                exposed_headers=[
                    "x-ms-meta-abc",
                    "x-ms-meta-data*",
                    "x-ms-meta-target*",
                ],
                max_age_in_seconds=2000,
            ),
        ],
    ),
    resource_group_name="res4410",
    table_service_name="default")

```

```yaml
resources:
  tableServiceProperties:
    type: azure-native:storage:TableServiceProperties
    properties:
      accountName: sto8607
      cors:
        corsRules:
          - allowedHeaders:
              - x-ms-meta-abc
              - x-ms-meta-data*
              - x-ms-meta-target*
            allowedMethods:
              - GET
              - HEAD
              - POST
              - OPTIONS
              - MERGE
              - PUT
            allowedOrigins:
              - http://www.contoso.com
              - http://www.fabrikam.com
            exposedHeaders:
              - x-ms-meta-*
            maxAgeInSeconds: 100
          - allowedHeaders:
              - '*'
            allowedMethods:
              - GET
            allowedOrigins:
              - '*'
            exposedHeaders:
              - '*'
            maxAgeInSeconds: 2
          - allowedHeaders:
              - x-ms-meta-12345675754564*
            allowedMethods:
              - GET
              - PUT
            allowedOrigins:
              - http://www.abc23.com
              - https://www.fabrikam.com/*
            exposedHeaders:
              - x-ms-meta-abc
              - x-ms-meta-data*
              - x-ms-meta-target*
            maxAgeInSeconds: 2000
      resourceGroupName: res4410
      tableServiceName: default

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storage:TableServiceProperties default /subscriptions/{subscription-id}/resourceGroups/res4410/providers/Microsoft.Storage/storageAccounts/sto8607/tableServices/default 
```
