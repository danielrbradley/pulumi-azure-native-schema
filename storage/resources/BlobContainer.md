Properties of the blob container, including Id, resource name, resource type, Etag.
API Version: 2022-09-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutContainerWithDefaultEncryptionScope
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blobContainer = new AzureNative.Storage.BlobContainer("blobContainer", new()
    {
        AccountName = "sto328",
        ContainerName = "container6185",
        DefaultEncryptionScope = "encryptionscope185",
        DenyEncryptionScopeOverride = true,
        ResourceGroupName = "res3376",
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
		_, err := storage.NewBlobContainer(ctx, "blobContainer", &storage.BlobContainerArgs{
			AccountName:                 pulumi.String("sto328"),
			ContainerName:               pulumi.String("container6185"),
			DefaultEncryptionScope:      pulumi.String("encryptionscope185"),
			DenyEncryptionScopeOverride: pulumi.Bool(true),
			ResourceGroupName:           pulumi.String("res3376"),
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
import com.pulumi.azurenative.storage.BlobContainer;
import com.pulumi.azurenative.storage.BlobContainerArgs;
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
        var blobContainer = new BlobContainer("blobContainer", BlobContainerArgs.builder()        
            .accountName("sto328")
            .containerName("container6185")
            .defaultEncryptionScope("encryptionscope185")
            .denyEncryptionScopeOverride(true)
            .resourceGroupName("res3376")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blobContainer = new azure_native.storage.BlobContainer("blobContainer", {
    accountName: "sto328",
    containerName: "container6185",
    defaultEncryptionScope: "encryptionscope185",
    denyEncryptionScopeOverride: true,
    resourceGroupName: "res3376",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blob_container = azure_native.storage.BlobContainer("blobContainer",
    account_name="sto328",
    container_name="container6185",
    default_encryption_scope="encryptionscope185",
    deny_encryption_scope_override=True,
    resource_group_name="res3376")

```

```yaml
resources:
  blobContainer:
    type: azure-native:storage:BlobContainer
    properties:
      accountName: sto328
      containerName: container6185
      defaultEncryptionScope: encryptionscope185
      denyEncryptionScopeOverride: true
      resourceGroupName: res3376

```

{{% /example %}}
{{% example %}}
### PutContainerWithObjectLevelWorm
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blobContainer = new AzureNative.Storage.BlobContainer("blobContainer", new()
    {
        AccountName = "sto328",
        ContainerName = "container6185",
        ImmutableStorageWithVersioning = new AzureNative.Storage.Inputs.ImmutableStorageWithVersioningArgs
        {
            Enabled = true,
        },
        ResourceGroupName = "res3376",
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
		_, err := storage.NewBlobContainer(ctx, "blobContainer", &storage.BlobContainerArgs{
			AccountName:   pulumi.String("sto328"),
			ContainerName: pulumi.String("container6185"),
			ImmutableStorageWithVersioning: &storage.ImmutableStorageWithVersioningArgs{
				Enabled: pulumi.Bool(true),
			},
			ResourceGroupName: pulumi.String("res3376"),
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
import com.pulumi.azurenative.storage.BlobContainer;
import com.pulumi.azurenative.storage.BlobContainerArgs;
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
        var blobContainer = new BlobContainer("blobContainer", BlobContainerArgs.builder()        
            .accountName("sto328")
            .containerName("container6185")
            .immutableStorageWithVersioning(Map.of("enabled", true))
            .resourceGroupName("res3376")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blobContainer = new azure_native.storage.BlobContainer("blobContainer", {
    accountName: "sto328",
    containerName: "container6185",
    immutableStorageWithVersioning: {
        enabled: true,
    },
    resourceGroupName: "res3376",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blob_container = azure_native.storage.BlobContainer("blobContainer",
    account_name="sto328",
    container_name="container6185",
    immutable_storage_with_versioning=azure_native.storage.ImmutableStorageWithVersioningArgs(
        enabled=True,
    ),
    resource_group_name="res3376")

```

```yaml
resources:
  blobContainer:
    type: azure-native:storage:BlobContainer
    properties:
      accountName: sto328
      containerName: container6185
      immutableStorageWithVersioning:
        enabled: true
      resourceGroupName: res3376

```

{{% /example %}}
{{% example %}}
### PutContainers
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blobContainer = new AzureNative.Storage.BlobContainer("blobContainer", new()
    {
        AccountName = "sto328",
        ContainerName = "container6185",
        ResourceGroupName = "res3376",
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
		_, err := storage.NewBlobContainer(ctx, "blobContainer", &storage.BlobContainerArgs{
			AccountName:       pulumi.String("sto328"),
			ContainerName:     pulumi.String("container6185"),
			ResourceGroupName: pulumi.String("res3376"),
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
import com.pulumi.azurenative.storage.BlobContainer;
import com.pulumi.azurenative.storage.BlobContainerArgs;
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
        var blobContainer = new BlobContainer("blobContainer", BlobContainerArgs.builder()        
            .accountName("sto328")
            .containerName("container6185")
            .resourceGroupName("res3376")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blobContainer = new azure_native.storage.BlobContainer("blobContainer", {
    accountName: "sto328",
    containerName: "container6185",
    resourceGroupName: "res3376",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blob_container = azure_native.storage.BlobContainer("blobContainer",
    account_name="sto328",
    container_name="container6185",
    resource_group_name="res3376")

```

```yaml
resources:
  blobContainer:
    type: azure-native:storage:BlobContainer
    properties:
      accountName: sto328
      containerName: container6185
      resourceGroupName: res3376

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storage:BlobContainer container6185 /subscriptions/{subscription-id}/resourceGroups/res3376/providers/Microsoft.Storage/storageAccounts/sto328/blobServices/default/containers/container6185 
```
