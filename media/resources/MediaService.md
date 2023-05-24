A Media Services account.
API Version: 2023-01-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a Media Services account
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var mediaService = new AzureNative.Media.MediaService("mediaService", new()
    {
        AccountName = "contososports",
        Location = "South Central US",
        ResourceGroupName = "contosorg",
        StorageAccounts = new[]
        {
            new AzureNative.Media.Inputs.StorageAccountArgs
            {
                Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosorg/providers/Microsoft.Storage/storageAccounts/teststorageaccount",
                Type = "Primary",
            },
        },
        Tags = 
        {
            { "key1", "value1" },
            { "key2", "value2" },
        },
    });

});


```

```go
package main

import (
	media "github.com/pulumi/pulumi-azure-native-sdk/media"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := media.NewMediaService(ctx, "mediaService", &media.MediaServiceArgs{
			AccountName:       pulumi.String("contososports"),
			Location:          pulumi.String("South Central US"),
			ResourceGroupName: pulumi.String("contosorg"),
			StorageAccounts: []media.StorageAccountArgs{
				{
					Id:   pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosorg/providers/Microsoft.Storage/storageAccounts/teststorageaccount"),
					Type: pulumi.String("Primary"),
				},
			},
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
				"key2": pulumi.String("value2"),
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
import com.pulumi.azurenative.media.MediaService;
import com.pulumi.azurenative.media.MediaServiceArgs;
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
        var mediaService = new MediaService("mediaService", MediaServiceArgs.builder()        
            .accountName("contososports")
            .location("South Central US")
            .resourceGroupName("contosorg")
            .storageAccounts(Map.ofEntries(
                Map.entry("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosorg/providers/Microsoft.Storage/storageAccounts/teststorageaccount"),
                Map.entry("type", "Primary")
            ))
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const mediaService = new azure_native.media.MediaService("mediaService", {
    accountName: "contososports",
    location: "South Central US",
    resourceGroupName: "contosorg",
    storageAccounts: [{
        id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosorg/providers/Microsoft.Storage/storageAccounts/teststorageaccount",
        type: "Primary",
    }],
    tags: {
        key1: "value1",
        key2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

media_service = azure_native.media.MediaService("mediaService",
    account_name="contososports",
    location="South Central US",
    resource_group_name="contosorg",
    storage_accounts=[azure_native.media.StorageAccountArgs(
        id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosorg/providers/Microsoft.Storage/storageAccounts/teststorageaccount",
        type="Primary",
    )],
    tags={
        "key1": "value1",
        "key2": "value2",
    })

```

```yaml
resources:
  mediaService:
    type: azure-native:media:MediaService
    properties:
      accountName: contososports
      location: South Central US
      resourceGroupName: contosorg
      storageAccounts:
        - id: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosorg/providers/Microsoft.Storage/storageAccounts/teststorageaccount
          type: Primary
      tags:
        key1: value1
        key2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:media:MediaService contososports /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosorg/providers/Microsoft.Media/mediaservices/contososports 
```
