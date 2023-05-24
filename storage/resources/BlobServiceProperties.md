The properties of a storage account’s Blob service.
API Version: 2022-09-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### BlobServicesPutAllowPermanentDelete
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blobServiceProperties = new AzureNative.Storage.BlobServiceProperties("blobServiceProperties", new()
    {
        AccountName = "sto8607",
        BlobServicesName = "default",
        DeleteRetentionPolicy = new AzureNative.Storage.Inputs.DeleteRetentionPolicyArgs
        {
            AllowPermanentDelete = true,
            Days = 300,
            Enabled = true,
        },
        IsVersioningEnabled = true,
        ResourceGroupName = "res4410",
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
		_, err := storage.NewBlobServiceProperties(ctx, "blobServiceProperties", &storage.BlobServicePropertiesArgs{
			AccountName:      pulumi.String("sto8607"),
			BlobServicesName: pulumi.String("default"),
			DeleteRetentionPolicy: &storage.DeleteRetentionPolicyArgs{
				AllowPermanentDelete: pulumi.Bool(true),
				Days:                 pulumi.Int(300),
				Enabled:              pulumi.Bool(true),
			},
			IsVersioningEnabled: pulumi.Bool(true),
			ResourceGroupName:   pulumi.String("res4410"),
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
import com.pulumi.azurenative.storage.BlobServiceProperties;
import com.pulumi.azurenative.storage.BlobServicePropertiesArgs;
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
        var blobServiceProperties = new BlobServiceProperties("blobServiceProperties", BlobServicePropertiesArgs.builder()        
            .accountName("sto8607")
            .blobServicesName("default")
            .deleteRetentionPolicy(Map.ofEntries(
                Map.entry("allowPermanentDelete", true),
                Map.entry("days", 300),
                Map.entry("enabled", true)
            ))
            .isVersioningEnabled(true)
            .resourceGroupName("res4410")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blobServiceProperties = new azure_native.storage.BlobServiceProperties("blobServiceProperties", {
    accountName: "sto8607",
    blobServicesName: "default",
    deleteRetentionPolicy: {
        allowPermanentDelete: true,
        days: 300,
        enabled: true,
    },
    isVersioningEnabled: true,
    resourceGroupName: "res4410",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blob_service_properties = azure_native.storage.BlobServiceProperties("blobServiceProperties",
    account_name="sto8607",
    blob_services_name="default",
    delete_retention_policy=azure_native.storage.DeleteRetentionPolicyArgs(
        allow_permanent_delete=True,
        days=300,
        enabled=True,
    ),
    is_versioning_enabled=True,
    resource_group_name="res4410")

```

```yaml
resources:
  blobServiceProperties:
    type: azure-native:storage:BlobServiceProperties
    properties:
      accountName: sto8607
      blobServicesName: default
      deleteRetentionPolicy:
        allowPermanentDelete: true
        days: 300
        enabled: true
      isVersioningEnabled: true
      resourceGroupName: res4410

```

{{% /example %}}
{{% example %}}
### BlobServicesPutLastAccessTimeBasedTracking
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blobServiceProperties = new AzureNative.Storage.BlobServiceProperties("blobServiceProperties", new()
    {
        AccountName = "sto8607",
        BlobServicesName = "default",
        LastAccessTimeTrackingPolicy = new AzureNative.Storage.Inputs.LastAccessTimeTrackingPolicyArgs
        {
            BlobType = new[]
            {
                "blockBlob",
            },
            Enable = true,
            Name = "AccessTimeTracking",
            TrackingGranularityInDays = 1,
        },
        ResourceGroupName = "res4410",
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
		_, err := storage.NewBlobServiceProperties(ctx, "blobServiceProperties", &storage.BlobServicePropertiesArgs{
			AccountName:      pulumi.String("sto8607"),
			BlobServicesName: pulumi.String("default"),
			LastAccessTimeTrackingPolicy: &storage.LastAccessTimeTrackingPolicyArgs{
				BlobType: pulumi.StringArray{
					pulumi.String("blockBlob"),
				},
				Enable:                    pulumi.Bool(true),
				Name:                      pulumi.String("AccessTimeTracking"),
				TrackingGranularityInDays: pulumi.Int(1),
			},
			ResourceGroupName: pulumi.String("res4410"),
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
import com.pulumi.azurenative.storage.BlobServiceProperties;
import com.pulumi.azurenative.storage.BlobServicePropertiesArgs;
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
        var blobServiceProperties = new BlobServiceProperties("blobServiceProperties", BlobServicePropertiesArgs.builder()        
            .accountName("sto8607")
            .blobServicesName("default")
            .lastAccessTimeTrackingPolicy(Map.ofEntries(
                Map.entry("blobType", "blockBlob"),
                Map.entry("enable", true),
                Map.entry("name", "AccessTimeTracking"),
                Map.entry("trackingGranularityInDays", 1)
            ))
            .resourceGroupName("res4410")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blobServiceProperties = new azure_native.storage.BlobServiceProperties("blobServiceProperties", {
    accountName: "sto8607",
    blobServicesName: "default",
    lastAccessTimeTrackingPolicy: {
        blobType: ["blockBlob"],
        enable: true,
        name: "AccessTimeTracking",
        trackingGranularityInDays: 1,
    },
    resourceGroupName: "res4410",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blob_service_properties = azure_native.storage.BlobServiceProperties("blobServiceProperties",
    account_name="sto8607",
    blob_services_name="default",
    last_access_time_tracking_policy=azure_native.storage.LastAccessTimeTrackingPolicyArgs(
        blob_type=["blockBlob"],
        enable=True,
        name="AccessTimeTracking",
        tracking_granularity_in_days=1,
    ),
    resource_group_name="res4410")

```

```yaml
resources:
  blobServiceProperties:
    type: azure-native:storage:BlobServiceProperties
    properties:
      accountName: sto8607
      blobServicesName: default
      lastAccessTimeTrackingPolicy:
        blobType:
          - blockBlob
        enable: true
        name: AccessTimeTracking
        trackingGranularityInDays: 1
      resourceGroupName: res4410

```

{{% /example %}}
{{% example %}}
### PutBlobServices
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blobServiceProperties = new AzureNative.Storage.BlobServiceProperties("blobServiceProperties", new()
    {
        AccountName = "sto8607",
        BlobServicesName = "default",
        ChangeFeed = new AzureNative.Storage.Inputs.ChangeFeedArgs
        {
            Enabled = true,
            RetentionInDays = 7,
        },
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
                        "x -ms-meta-target*",
                    },
                    MaxAgeInSeconds = 2000,
                },
            },
        },
        DefaultServiceVersion = "2017-07-29",
        DeleteRetentionPolicy = new AzureNative.Storage.Inputs.DeleteRetentionPolicyArgs
        {
            Days = 300,
            Enabled = true,
        },
        IsVersioningEnabled = true,
        ResourceGroupName = "res4410",
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
		_, err := storage.NewBlobServiceProperties(ctx, "blobServiceProperties", &storage.BlobServicePropertiesArgs{
			AccountName:      pulumi.String("sto8607"),
			BlobServicesName: pulumi.String("default"),
			ChangeFeed: &storage.ChangeFeedArgs{
				Enabled:         pulumi.Bool(true),
				RetentionInDays: pulumi.Int(7),
			},
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
							pulumi.String("x -ms-meta-target*"),
						},
						MaxAgeInSeconds: pulumi.Int(2000),
					},
				},
			},
			DefaultServiceVersion: pulumi.String("2017-07-29"),
			DeleteRetentionPolicy: &storage.DeleteRetentionPolicyArgs{
				Days:    pulumi.Int(300),
				Enabled: pulumi.Bool(true),
			},
			IsVersioningEnabled: pulumi.Bool(true),
			ResourceGroupName:   pulumi.String("res4410"),
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
import com.pulumi.azurenative.storage.BlobServiceProperties;
import com.pulumi.azurenative.storage.BlobServicePropertiesArgs;
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
        var blobServiceProperties = new BlobServiceProperties("blobServiceProperties", BlobServicePropertiesArgs.builder()        
            .accountName("sto8607")
            .blobServicesName("default")
            .changeFeed(Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("retentionInDays", 7)
            ))
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
                        "x -ms-meta-target*"),
                    Map.entry("maxAgeInSeconds", 2000)
                )))
            .defaultServiceVersion("2017-07-29")
            .deleteRetentionPolicy(Map.ofEntries(
                Map.entry("days", 300),
                Map.entry("enabled", true)
            ))
            .isVersioningEnabled(true)
            .resourceGroupName("res4410")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blobServiceProperties = new azure_native.storage.BlobServiceProperties("blobServiceProperties", {
    accountName: "sto8607",
    blobServicesName: "default",
    changeFeed: {
        enabled: true,
        retentionInDays: 7,
    },
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
                    "x -ms-meta-target*",
                ],
                maxAgeInSeconds: 2000,
            },
        ],
    },
    defaultServiceVersion: "2017-07-29",
    deleteRetentionPolicy: {
        days: 300,
        enabled: true,
    },
    isVersioningEnabled: true,
    resourceGroupName: "res4410",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blob_service_properties = azure_native.storage.BlobServiceProperties("blobServiceProperties",
    account_name="sto8607",
    blob_services_name="default",
    change_feed=azure_native.storage.ChangeFeedArgs(
        enabled=True,
        retention_in_days=7,
    ),
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
                    "x -ms-meta-target*",
                ],
                max_age_in_seconds=2000,
            ),
        ],
    ),
    default_service_version="2017-07-29",
    delete_retention_policy=azure_native.storage.DeleteRetentionPolicyArgs(
        days=300,
        enabled=True,
    ),
    is_versioning_enabled=True,
    resource_group_name="res4410")

```

```yaml
resources:
  blobServiceProperties:
    type: azure-native:storage:BlobServiceProperties
    properties:
      accountName: sto8607
      blobServicesName: default
      changeFeed:
        enabled: true
        retentionInDays: 7
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
              - x -ms-meta-target*
            maxAgeInSeconds: 2000
      defaultServiceVersion: 2017-07-29
      deleteRetentionPolicy:
        days: 300
        enabled: true
      isVersioningEnabled: true
      resourceGroupName: res4410

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storage:BlobServiceProperties default /subscriptions/{subscription-id}/resourceGroups/res4410/providers/Microsoft.Storage/storageAccounts/sto8607/blobServices/default 
```
