Snapshot resource.
API Version: 2022-07-02.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a snapshot by importing an unmanaged blob from a different subscription.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var snapshot = new AzureNative.Compute.Snapshot("snapshot", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Import",
            SourceUri = "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
            StorageAccountId = "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount",
        },
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        SnapshotName = "mySnapshot1",
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewSnapshot(ctx, "snapshot", &compute.SnapshotArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption:     pulumi.String("Import"),
				SourceUri:        pulumi.String("https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd"),
				StorageAccountId: pulumi.String("subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount"),
			},
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SnapshotName:      pulumi.String("mySnapshot1"),
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
import com.pulumi.azurenative.compute.Snapshot;
import com.pulumi.azurenative.compute.SnapshotArgs;
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
        var snapshot = new Snapshot("snapshot", SnapshotArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "Import"),
                Map.entry("sourceUri", "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd"),
                Map.entry("storageAccountId", "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount")
            ))
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .snapshotName("mySnapshot1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const snapshot = new azure_native.compute.Snapshot("snapshot", {
    creationData: {
        createOption: "Import",
        sourceUri: "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
        storageAccountId: "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount",
    },
    location: "West US",
    resourceGroupName: "myResourceGroup",
    snapshotName: "mySnapshot1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

snapshot = azure_native.compute.Snapshot("snapshot",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Import",
        source_uri="https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
        storage_account_id="subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount",
    ),
    location="West US",
    resource_group_name="myResourceGroup",
    snapshot_name="mySnapshot1")

```

```yaml
resources:
  snapshot:
    type: azure-native:compute:Snapshot
    properties:
      creationData:
        createOption: Import
        sourceUri: https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd
        storageAccountId: subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount
      location: West US
      resourceGroupName: myResourceGroup
      snapshotName: mySnapshot1

```

{{% /example %}}
{{% example %}}
### Create a snapshot by importing an unmanaged blob from the same subscription.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var snapshot = new AzureNative.Compute.Snapshot("snapshot", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Import",
            SourceUri = "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
        },
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        SnapshotName = "mySnapshot1",
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewSnapshot(ctx, "snapshot", &compute.SnapshotArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption: pulumi.String("Import"),
				SourceUri:    pulumi.String("https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd"),
			},
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SnapshotName:      pulumi.String("mySnapshot1"),
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
import com.pulumi.azurenative.compute.Snapshot;
import com.pulumi.azurenative.compute.SnapshotArgs;
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
        var snapshot = new Snapshot("snapshot", SnapshotArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "Import"),
                Map.entry("sourceUri", "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd")
            ))
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .snapshotName("mySnapshot1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const snapshot = new azure_native.compute.Snapshot("snapshot", {
    creationData: {
        createOption: "Import",
        sourceUri: "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
    },
    location: "West US",
    resourceGroupName: "myResourceGroup",
    snapshotName: "mySnapshot1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

snapshot = azure_native.compute.Snapshot("snapshot",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Import",
        source_uri="https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
    ),
    location="West US",
    resource_group_name="myResourceGroup",
    snapshot_name="mySnapshot1")

```

```yaml
resources:
  snapshot:
    type: azure-native:compute:Snapshot
    properties:
      creationData:
        createOption: Import
        sourceUri: https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd
      location: West US
      resourceGroupName: myResourceGroup
      snapshotName: mySnapshot1

```

{{% /example %}}
{{% example %}}
### Create a snapshot from an existing snapshot in the same or a different subscription in a different region.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var snapshot = new AzureNative.Compute.Snapshot("snapshot", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "CopyStart",
            SourceResourceId = "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot1",
        },
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        SnapshotName = "mySnapshot2",
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewSnapshot(ctx, "snapshot", &compute.SnapshotArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption:     pulumi.String("CopyStart"),
				SourceResourceId: pulumi.String("subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot1"),
			},
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SnapshotName:      pulumi.String("mySnapshot2"),
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
import com.pulumi.azurenative.compute.Snapshot;
import com.pulumi.azurenative.compute.SnapshotArgs;
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
        var snapshot = new Snapshot("snapshot", SnapshotArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "CopyStart"),
                Map.entry("sourceResourceId", "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot1")
            ))
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .snapshotName("mySnapshot2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const snapshot = new azure_native.compute.Snapshot("snapshot", {
    creationData: {
        createOption: "CopyStart",
        sourceResourceId: "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot1",
    },
    location: "West US",
    resourceGroupName: "myResourceGroup",
    snapshotName: "mySnapshot2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

snapshot = azure_native.compute.Snapshot("snapshot",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="CopyStart",
        source_resource_id="subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot1",
    ),
    location="West US",
    resource_group_name="myResourceGroup",
    snapshot_name="mySnapshot2")

```

```yaml
resources:
  snapshot:
    type: azure-native:compute:Snapshot
    properties:
      creationData:
        createOption: CopyStart
        sourceResourceId: subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot1
      location: West US
      resourceGroupName: myResourceGroup
      snapshotName: mySnapshot2

```

{{% /example %}}
{{% example %}}
### Create a snapshot from an existing snapshot in the same or a different subscription.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var snapshot = new AzureNative.Compute.Snapshot("snapshot", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Copy",
            SourceResourceId = "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot1",
        },
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        SnapshotName = "mySnapshot2",
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewSnapshot(ctx, "snapshot", &compute.SnapshotArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption:     pulumi.String("Copy"),
				SourceResourceId: pulumi.String("subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot1"),
			},
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SnapshotName:      pulumi.String("mySnapshot2"),
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
import com.pulumi.azurenative.compute.Snapshot;
import com.pulumi.azurenative.compute.SnapshotArgs;
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
        var snapshot = new Snapshot("snapshot", SnapshotArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "Copy"),
                Map.entry("sourceResourceId", "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot1")
            ))
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .snapshotName("mySnapshot2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const snapshot = new azure_native.compute.Snapshot("snapshot", {
    creationData: {
        createOption: "Copy",
        sourceResourceId: "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot1",
    },
    location: "West US",
    resourceGroupName: "myResourceGroup",
    snapshotName: "mySnapshot2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

snapshot = azure_native.compute.Snapshot("snapshot",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Copy",
        source_resource_id="subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot1",
    ),
    location="West US",
    resource_group_name="myResourceGroup",
    snapshot_name="mySnapshot2")

```

```yaml
resources:
  snapshot:
    type: azure-native:compute:Snapshot
    properties:
      creationData:
        createOption: Copy
        sourceResourceId: subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot1
      location: West US
      resourceGroupName: myResourceGroup
      snapshotName: mySnapshot2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:Snapshot mySnapshot2 /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/snapshots/{snapshotName} 
```
