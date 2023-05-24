Type of the Storage Target.
API Version: 2023-01-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### StorageTargets_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageTarget = new AzureNative.StorageCache.StorageTarget("storageTarget", new()
    {
        CacheName = "sc1",
        Junctions = new[]
        {
            new AzureNative.StorageCache.Inputs.NamespaceJunctionArgs
            {
                NamespacePath = "/path/on/cache",
                NfsAccessPolicy = "default",
                NfsExport = "exp1",
                TargetPath = "/path/on/exp1",
            },
            new AzureNative.StorageCache.Inputs.NamespaceJunctionArgs
            {
                NamespacePath = "/path2/on/cache",
                NfsAccessPolicy = "rootSquash",
                NfsExport = "exp2",
                TargetPath = "/path2/on/exp2",
            },
        },
        Nfs3 = new AzureNative.StorageCache.Inputs.Nfs3TargetArgs
        {
            Target = "10.0.44.44",
            UsageModel = "READ_ONLY",
            VerificationTimer = 30,
        },
        ResourceGroupName = "scgroup",
        StorageTargetName = "st1",
        TargetType = "nfs3",
    });

});


```

```go
package main

import (
	storagecache "github.com/pulumi/pulumi-azure-native-sdk/storagecache"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storagecache.NewStorageTarget(ctx, "storageTarget", &storagecache.StorageTargetArgs{
			CacheName: pulumi.String("sc1"),
			Junctions: []storagecache.NamespaceJunctionArgs{
				{
					NamespacePath:   pulumi.String("/path/on/cache"),
					NfsAccessPolicy: pulumi.String("default"),
					NfsExport:       pulumi.String("exp1"),
					TargetPath:      pulumi.String("/path/on/exp1"),
				},
				{
					NamespacePath:   pulumi.String("/path2/on/cache"),
					NfsAccessPolicy: pulumi.String("rootSquash"),
					NfsExport:       pulumi.String("exp2"),
					TargetPath:      pulumi.String("/path2/on/exp2"),
				},
			},
			Nfs3: &storagecache.Nfs3TargetArgs{
				Target:            pulumi.String("10.0.44.44"),
				UsageModel:        pulumi.String("READ_ONLY"),
				VerificationTimer: pulumi.Int(30),
			},
			ResourceGroupName: pulumi.String("scgroup"),
			StorageTargetName: pulumi.String("st1"),
			TargetType:        pulumi.String("nfs3"),
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
import com.pulumi.azurenative.storagecache.StorageTarget;
import com.pulumi.azurenative.storagecache.StorageTargetArgs;
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
        var storageTarget = new StorageTarget("storageTarget", StorageTargetArgs.builder()        
            .cacheName("sc1")
            .junctions(            
                Map.ofEntries(
                    Map.entry("namespacePath", "/path/on/cache"),
                    Map.entry("nfsAccessPolicy", "default"),
                    Map.entry("nfsExport", "exp1"),
                    Map.entry("targetPath", "/path/on/exp1")
                ),
                Map.ofEntries(
                    Map.entry("namespacePath", "/path2/on/cache"),
                    Map.entry("nfsAccessPolicy", "rootSquash"),
                    Map.entry("nfsExport", "exp2"),
                    Map.entry("targetPath", "/path2/on/exp2")
                ))
            .nfs3(Map.ofEntries(
                Map.entry("target", "10.0.44.44"),
                Map.entry("usageModel", "READ_ONLY"),
                Map.entry("verificationTimer", 30)
            ))
            .resourceGroupName("scgroup")
            .storageTargetName("st1")
            .targetType("nfs3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageTarget = new azure_native.storagecache.StorageTarget("storageTarget", {
    cacheName: "sc1",
    junctions: [
        {
            namespacePath: "/path/on/cache",
            nfsAccessPolicy: "default",
            nfsExport: "exp1",
            targetPath: "/path/on/exp1",
        },
        {
            namespacePath: "/path2/on/cache",
            nfsAccessPolicy: "rootSquash",
            nfsExport: "exp2",
            targetPath: "/path2/on/exp2",
        },
    ],
    nfs3: {
        target: "10.0.44.44",
        usageModel: "READ_ONLY",
        verificationTimer: 30,
    },
    resourceGroupName: "scgroup",
    storageTargetName: "st1",
    targetType: "nfs3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_target = azure_native.storagecache.StorageTarget("storageTarget",
    cache_name="sc1",
    junctions=[
        azure_native.storagecache.NamespaceJunctionArgs(
            namespace_path="/path/on/cache",
            nfs_access_policy="default",
            nfs_export="exp1",
            target_path="/path/on/exp1",
        ),
        azure_native.storagecache.NamespaceJunctionArgs(
            namespace_path="/path2/on/cache",
            nfs_access_policy="rootSquash",
            nfs_export="exp2",
            target_path="/path2/on/exp2",
        ),
    ],
    nfs3=azure_native.storagecache.Nfs3TargetArgs(
        target="10.0.44.44",
        usage_model="READ_ONLY",
        verification_timer=30,
    ),
    resource_group_name="scgroup",
    storage_target_name="st1",
    target_type="nfs3")

```

```yaml
resources:
  storageTarget:
    type: azure-native:storagecache:StorageTarget
    properties:
      cacheName: sc1
      junctions:
        - namespacePath: /path/on/cache
          nfsAccessPolicy: default
          nfsExport: exp1
          targetPath: /path/on/exp1
        - namespacePath: /path2/on/cache
          nfsAccessPolicy: rootSquash
          nfsExport: exp2
          targetPath: /path2/on/exp2
      nfs3:
        target: 10.0.44.44
        usageModel: READ_ONLY
        verificationTimer: 30
      resourceGroupName: scgroup
      storageTargetName: st1
      targetType: nfs3

```

{{% /example %}}
{{% example %}}
### StorageTargets_CreateOrUpdate_BlobNfs
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageTarget = new AzureNative.StorageCache.StorageTarget("storageTarget", new()
    {
        BlobNfs = new AzureNative.StorageCache.Inputs.BlobNfsTargetArgs
        {
            Target = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.Storage/storageAccounts/blofnfs/blobServices/default/containers/blobnfs",
            UsageModel = "READ_WRITE",
            VerificationTimer = 28800,
            WriteBackTimer = 3600,
        },
        CacheName = "sc1",
        Junctions = new[]
        {
            new AzureNative.StorageCache.Inputs.NamespaceJunctionArgs
            {
                NamespacePath = "/blobnfs",
            },
        },
        ResourceGroupName = "scgroup",
        StorageTargetName = "st1",
        TargetType = "blobNfs",
    });

});


```

```go
package main

import (
	storagecache "github.com/pulumi/pulumi-azure-native-sdk/storagecache"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storagecache.NewStorageTarget(ctx, "storageTarget", &storagecache.StorageTargetArgs{
			BlobNfs: &storagecache.BlobNfsTargetArgs{
				Target:            pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.Storage/storageAccounts/blofnfs/blobServices/default/containers/blobnfs"),
				UsageModel:        pulumi.String("READ_WRITE"),
				VerificationTimer: pulumi.Int(28800),
				WriteBackTimer:    pulumi.Int(3600),
			},
			CacheName: pulumi.String("sc1"),
			Junctions: []storagecache.NamespaceJunctionArgs{
				{
					NamespacePath: pulumi.String("/blobnfs"),
				},
			},
			ResourceGroupName: pulumi.String("scgroup"),
			StorageTargetName: pulumi.String("st1"),
			TargetType:        pulumi.String("blobNfs"),
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
import com.pulumi.azurenative.storagecache.StorageTarget;
import com.pulumi.azurenative.storagecache.StorageTargetArgs;
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
        var storageTarget = new StorageTarget("storageTarget", StorageTargetArgs.builder()        
            .blobNfs(Map.ofEntries(
                Map.entry("target", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.Storage/storageAccounts/blofnfs/blobServices/default/containers/blobnfs"),
                Map.entry("usageModel", "READ_WRITE"),
                Map.entry("verificationTimer", 28800),
                Map.entry("writeBackTimer", 3600)
            ))
            .cacheName("sc1")
            .junctions(Map.of("namespacePath", "/blobnfs"))
            .resourceGroupName("scgroup")
            .storageTargetName("st1")
            .targetType("blobNfs")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageTarget = new azure_native.storagecache.StorageTarget("storageTarget", {
    blobNfs: {
        target: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.Storage/storageAccounts/blofnfs/blobServices/default/containers/blobnfs",
        usageModel: "READ_WRITE",
        verificationTimer: 28800,
        writeBackTimer: 3600,
    },
    cacheName: "sc1",
    junctions: [{
        namespacePath: "/blobnfs",
    }],
    resourceGroupName: "scgroup",
    storageTargetName: "st1",
    targetType: "blobNfs",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_target = azure_native.storagecache.StorageTarget("storageTarget",
    blob_nfs=azure_native.storagecache.BlobNfsTargetArgs(
        target="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.Storage/storageAccounts/blofnfs/blobServices/default/containers/blobnfs",
        usage_model="READ_WRITE",
        verification_timer=28800,
        write_back_timer=3600,
    ),
    cache_name="sc1",
    junctions=[azure_native.storagecache.NamespaceJunctionArgs(
        namespace_path="/blobnfs",
    )],
    resource_group_name="scgroup",
    storage_target_name="st1",
    target_type="blobNfs")

```

```yaml
resources:
  storageTarget:
    type: azure-native:storagecache:StorageTarget
    properties:
      blobNfs:
        target: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.Storage/storageAccounts/blofnfs/blobServices/default/containers/blobnfs
        usageModel: READ_WRITE
        verificationTimer: 28800
        writeBackTimer: 3600
      cacheName: sc1
      junctions:
        - namespacePath: /blobnfs
      resourceGroupName: scgroup
      storageTargetName: st1
      targetType: blobNfs

```

{{% /example %}}
{{% example %}}
### StorageTargets_CreateOrUpdate_NoJunctions
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageTarget = new AzureNative.StorageCache.StorageTarget("storageTarget", new()
    {
        CacheName = "sc1",
        Nfs3 = new AzureNative.StorageCache.Inputs.Nfs3TargetArgs
        {
            Target = "10.0.44.44",
            UsageModel = "READ_ONLY",
            VerificationTimer = 30,
        },
        ResourceGroupName = "scgroup",
        StorageTargetName = "st1",
        TargetType = "nfs3",
    });

});


```

```go
package main

import (
	storagecache "github.com/pulumi/pulumi-azure-native-sdk/storagecache"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storagecache.NewStorageTarget(ctx, "storageTarget", &storagecache.StorageTargetArgs{
			CacheName: pulumi.String("sc1"),
			Nfs3: &storagecache.Nfs3TargetArgs{
				Target:            pulumi.String("10.0.44.44"),
				UsageModel:        pulumi.String("READ_ONLY"),
				VerificationTimer: pulumi.Int(30),
			},
			ResourceGroupName: pulumi.String("scgroup"),
			StorageTargetName: pulumi.String("st1"),
			TargetType:        pulumi.String("nfs3"),
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
import com.pulumi.azurenative.storagecache.StorageTarget;
import com.pulumi.azurenative.storagecache.StorageTargetArgs;
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
        var storageTarget = new StorageTarget("storageTarget", StorageTargetArgs.builder()        
            .cacheName("sc1")
            .nfs3(Map.ofEntries(
                Map.entry("target", "10.0.44.44"),
                Map.entry("usageModel", "READ_ONLY"),
                Map.entry("verificationTimer", 30)
            ))
            .resourceGroupName("scgroup")
            .storageTargetName("st1")
            .targetType("nfs3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageTarget = new azure_native.storagecache.StorageTarget("storageTarget", {
    cacheName: "sc1",
    nfs3: {
        target: "10.0.44.44",
        usageModel: "READ_ONLY",
        verificationTimer: 30,
    },
    resourceGroupName: "scgroup",
    storageTargetName: "st1",
    targetType: "nfs3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_target = azure_native.storagecache.StorageTarget("storageTarget",
    cache_name="sc1",
    nfs3=azure_native.storagecache.Nfs3TargetArgs(
        target="10.0.44.44",
        usage_model="READ_ONLY",
        verification_timer=30,
    ),
    resource_group_name="scgroup",
    storage_target_name="st1",
    target_type="nfs3")

```

```yaml
resources:
  storageTarget:
    type: azure-native:storagecache:StorageTarget
    properties:
      cacheName: sc1
      nfs3:
        target: 10.0.44.44
        usageModel: READ_ONLY
        verificationTimer: 30
      resourceGroupName: scgroup
      storageTargetName: st1
      targetType: nfs3

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storagecache:StorageTarget st1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.StorageCache/caches/sc1/storagetargets/st1 
```
