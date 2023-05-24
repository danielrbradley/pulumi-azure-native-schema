Properties of the file share, including Id, resource name, resource type, Etag.
API Version: 2022-09-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create NFS Shares
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var fileShare = new AzureNative.Storage.FileShare("fileShare", new()
    {
        AccountName = "sto666",
        EnabledProtocols = "NFS",
        ResourceGroupName = "res346",
        ShareName = "share1235",
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
		_, err := storage.NewFileShare(ctx, "fileShare", &storage.FileShareArgs{
			AccountName:       pulumi.String("sto666"),
			EnabledProtocols:  pulumi.String("NFS"),
			ResourceGroupName: pulumi.String("res346"),
			ShareName:         pulumi.String("share1235"),
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
import com.pulumi.azurenative.storage.FileShare;
import com.pulumi.azurenative.storage.FileShareArgs;
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
        var fileShare = new FileShare("fileShare", FileShareArgs.builder()        
            .accountName("sto666")
            .enabledProtocols("NFS")
            .resourceGroupName("res346")
            .shareName("share1235")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const fileShare = new azure_native.storage.FileShare("fileShare", {
    accountName: "sto666",
    enabledProtocols: "NFS",
    resourceGroupName: "res346",
    shareName: "share1235",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

file_share = azure_native.storage.FileShare("fileShare",
    account_name="sto666",
    enabled_protocols="NFS",
    resource_group_name="res346",
    share_name="share1235")

```

```yaml
resources:
  fileShare:
    type: azure-native:storage:FileShare
    properties:
      accountName: sto666
      enabledProtocols: NFS
      resourceGroupName: res346
      shareName: share1235

```

{{% /example %}}
{{% example %}}
### PutShares
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var fileShare = new AzureNative.Storage.FileShare("fileShare", new()
    {
        AccountName = "sto328",
        ResourceGroupName = "res3376",
        ShareName = "share6185",
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
		_, err := storage.NewFileShare(ctx, "fileShare", &storage.FileShareArgs{
			AccountName:       pulumi.String("sto328"),
			ResourceGroupName: pulumi.String("res3376"),
			ShareName:         pulumi.String("share6185"),
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
import com.pulumi.azurenative.storage.FileShare;
import com.pulumi.azurenative.storage.FileShareArgs;
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
        var fileShare = new FileShare("fileShare", FileShareArgs.builder()        
            .accountName("sto328")
            .resourceGroupName("res3376")
            .shareName("share6185")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const fileShare = new azure_native.storage.FileShare("fileShare", {
    accountName: "sto328",
    resourceGroupName: "res3376",
    shareName: "share6185",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

file_share = azure_native.storage.FileShare("fileShare",
    account_name="sto328",
    resource_group_name="res3376",
    share_name="share6185")

```

```yaml
resources:
  fileShare:
    type: azure-native:storage:FileShare
    properties:
      accountName: sto328
      resourceGroupName: res3376
      shareName: share6185

```

{{% /example %}}
{{% example %}}
### PutShares with Access Tier
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var fileShare = new AzureNative.Storage.FileShare("fileShare", new()
    {
        AccessTier = "Hot",
        AccountName = "sto666",
        ResourceGroupName = "res346",
        ShareName = "share1235",
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
		_, err := storage.NewFileShare(ctx, "fileShare", &storage.FileShareArgs{
			AccessTier:        pulumi.String("Hot"),
			AccountName:       pulumi.String("sto666"),
			ResourceGroupName: pulumi.String("res346"),
			ShareName:         pulumi.String("share1235"),
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
import com.pulumi.azurenative.storage.FileShare;
import com.pulumi.azurenative.storage.FileShareArgs;
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
        var fileShare = new FileShare("fileShare", FileShareArgs.builder()        
            .accessTier("Hot")
            .accountName("sto666")
            .resourceGroupName("res346")
            .shareName("share1235")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const fileShare = new azure_native.storage.FileShare("fileShare", {
    accessTier: "Hot",
    accountName: "sto666",
    resourceGroupName: "res346",
    shareName: "share1235",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

file_share = azure_native.storage.FileShare("fileShare",
    access_tier="Hot",
    account_name="sto666",
    resource_group_name="res346",
    share_name="share1235")

```

```yaml
resources:
  fileShare:
    type: azure-native:storage:FileShare
    properties:
      accessTier: Hot
      accountName: sto666
      resourceGroupName: res346
      shareName: share1235

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storage:FileShare share1235 /subscriptions/{subscription-id}/resourceGroups/res346/providers/Microsoft.Storage/storageAccounts/sto666/fileServices/default/shares/share1235 
```
