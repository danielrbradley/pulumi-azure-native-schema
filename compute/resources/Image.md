The source user image virtual hard disk. The virtual hard disk will be copied before being attached to the virtual machine. If SourceImage is provided, the destination virtual hard drive must not exist.
API Version: 2022-11-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a virtual machine image from a blob with DiskEncryptionSet resource.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var image = new AzureNative.Compute.Image("image", new()
    {
        ImageName = "myImage",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.ImageStorageProfileArgs
        {
            OsDisk = new AzureNative.Compute.Inputs.ImageOSDiskArgs
            {
                BlobUri = "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
                DiskEncryptionSet = new AzureNative.Compute.Inputs.DiskEncryptionSetParametersArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                },
                OsState = AzureNative.Compute.OperatingSystemStateTypes.Generalized,
                OsType = AzureNative.Compute.OperatingSystemTypes.Linux,
            },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.Image;
import com.pulumi.azurenative.compute.ImageArgs;
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
        var image = new Image("image", ImageArgs.builder()        
            .imageName("myImage")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.of("osDisk", Map.ofEntries(
                Map.entry("blobUri", "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd"),
                Map.entry("diskEncryptionSet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}")),
                Map.entry("osState", "Generalized"),
                Map.entry("osType", "Linux")
            )))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const image = new azure_native.compute.Image("image", {
    imageName: "myImage",
    location: "West US",
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        osDisk: {
            blobUri: "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
            diskEncryptionSet: {
                id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
            },
            osState: azure_native.compute.OperatingSystemStateTypes.Generalized,
            osType: azure_native.compute.OperatingSystemTypes.Linux,
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

image = azure_native.compute.Image("image",
    image_name="myImage",
    location="West US",
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.ImageStorageProfileResponseArgs(
        os_disk={
            "blobUri": "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
            "diskEncryptionSet": azure_native.compute.DiskEncryptionSetParametersArgs(
                id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
            ),
            "osState": azure_native.compute.OperatingSystemStateTypes.GENERALIZED,
            "osType": azure_native.compute.OperatingSystemTypes.LINUX,
        },
    ))

```

```yaml
resources:
  image:
    type: azure-native:compute:Image
    properties:
      imageName: myImage
      location: West US
      resourceGroupName: myResourceGroup
      storageProfile:
        osDisk:
          blobUri: https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd
          diskEncryptionSet:
            id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}
          osState: Generalized
          osType: Linux

```

{{% /example %}}
{{% example %}}
### Create a virtual machine image from a blob.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var image = new AzureNative.Compute.Image("image", new()
    {
        ImageName = "myImage",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.ImageStorageProfileArgs
        {
            OsDisk = new AzureNative.Compute.Inputs.ImageOSDiskArgs
            {
                BlobUri = "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
                OsState = AzureNative.Compute.OperatingSystemStateTypes.Generalized,
                OsType = AzureNative.Compute.OperatingSystemTypes.Linux,
            },
            ZoneResilient = true,
        },
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
		_, err := compute.NewImage(ctx, "image", &compute.ImageArgs{
			ImageName:         pulumi.String("myImage"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			StorageProfile: compute.ImageStorageProfileResponse{
				OsDisk: &compute.ImageOSDiskArgs{
					BlobUri: pulumi.String("https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd"),
					OsState: compute.OperatingSystemStateTypesGeneralized,
					OsType:  compute.OperatingSystemTypesLinux,
				},
				ZoneResilient: pulumi.Bool(true),
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
import com.pulumi.azurenative.compute.Image;
import com.pulumi.azurenative.compute.ImageArgs;
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
        var image = new Image("image", ImageArgs.builder()        
            .imageName("myImage")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("blobUri", "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd"),
                    Map.entry("osState", "Generalized"),
                    Map.entry("osType", "Linux")
                )),
                Map.entry("zoneResilient", true)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const image = new azure_native.compute.Image("image", {
    imageName: "myImage",
    location: "West US",
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        osDisk: {
            blobUri: "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
            osState: azure_native.compute.OperatingSystemStateTypes.Generalized,
            osType: azure_native.compute.OperatingSystemTypes.Linux,
        },
        zoneResilient: true,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

image = azure_native.compute.Image("image",
    image_name="myImage",
    location="West US",
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.ImageStorageProfileResponseArgs(
        os_disk=azure_native.compute.ImageOSDiskArgs(
            blob_uri="https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
            os_state=azure_native.compute.OperatingSystemStateTypes.GENERALIZED,
            os_type=azure_native.compute.OperatingSystemTypes.LINUX,
        ),
        zone_resilient=True,
    ))

```

```yaml
resources:
  image:
    type: azure-native:compute:Image
    properties:
      imageName: myImage
      location: West US
      resourceGroupName: myResourceGroup
      storageProfile:
        osDisk:
          blobUri: https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd
          osState: Generalized
          osType: Linux
        zoneResilient: true

```

{{% /example %}}
{{% example %}}
### Create a virtual machine image from a managed disk with DiskEncryptionSet resource.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var image = new AzureNative.Compute.Image("image", new()
    {
        ImageName = "myImage",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.ImageStorageProfileArgs
        {
            OsDisk = new AzureNative.Compute.Inputs.ImageOSDiskArgs
            {
                DiskEncryptionSet = new AzureNative.Compute.Inputs.DiskEncryptionSetParametersArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                },
                OsState = AzureNative.Compute.OperatingSystemStateTypes.Generalized,
                OsType = AzureNative.Compute.OperatingSystemTypes.Linux,
                Snapshot = new AzureNative.Compute.Inputs.SubResourceArgs
                {
                    Id = "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot",
                },
            },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.Image;
import com.pulumi.azurenative.compute.ImageArgs;
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
        var image = new Image("image", ImageArgs.builder()        
            .imageName("myImage")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.of("osDisk", Map.ofEntries(
                Map.entry("diskEncryptionSet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}")),
                Map.entry("osState", "Generalized"),
                Map.entry("osType", "Linux"),
                Map.entry("snapshot", Map.of("id", "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot"))
            )))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const image = new azure_native.compute.Image("image", {
    imageName: "myImage",
    location: "West US",
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        osDisk: {
            diskEncryptionSet: {
                id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
            },
            osState: azure_native.compute.OperatingSystemStateTypes.Generalized,
            osType: azure_native.compute.OperatingSystemTypes.Linux,
            snapshot: {
                id: "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot",
            },
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

image = azure_native.compute.Image("image",
    image_name="myImage",
    location="West US",
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.ImageStorageProfileResponseArgs(
        os_disk={
            "diskEncryptionSet": azure_native.compute.DiskEncryptionSetParametersArgs(
                id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
            ),
            "osState": azure_native.compute.OperatingSystemStateTypes.GENERALIZED,
            "osType": azure_native.compute.OperatingSystemTypes.LINUX,
            "snapshot": azure_native.compute.SubResourceArgs(
                id="subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot",
            ),
        },
    ))

```

```yaml
resources:
  image:
    type: azure-native:compute:Image
    properties:
      imageName: myImage
      location: West US
      resourceGroupName: myResourceGroup
      storageProfile:
        osDisk:
          diskEncryptionSet:
            id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}
          osState: Generalized
          osType: Linux
          snapshot:
            id: subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot

```

{{% /example %}}
{{% example %}}
### Create a virtual machine image from a managed disk.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var image = new AzureNative.Compute.Image("image", new()
    {
        ImageName = "myImage",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.ImageStorageProfileArgs
        {
            OsDisk = new AzureNative.Compute.Inputs.ImageOSDiskArgs
            {
                ManagedDisk = new AzureNative.Compute.Inputs.SubResourceArgs
                {
                    Id = "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk",
                },
                OsState = AzureNative.Compute.OperatingSystemStateTypes.Generalized,
                OsType = AzureNative.Compute.OperatingSystemTypes.Linux,
            },
            ZoneResilient = true,
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.Image;
import com.pulumi.azurenative.compute.ImageArgs;
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
        var image = new Image("image", ImageArgs.builder()        
            .imageName("myImage")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("managedDisk", Map.of("id", "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk")),
                    Map.entry("osState", "Generalized"),
                    Map.entry("osType", "Linux")
                )),
                Map.entry("zoneResilient", true)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const image = new azure_native.compute.Image("image", {
    imageName: "myImage",
    location: "West US",
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        osDisk: {
            managedDisk: {
                id: "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk",
            },
            osState: azure_native.compute.OperatingSystemStateTypes.Generalized,
            osType: azure_native.compute.OperatingSystemTypes.Linux,
        },
        zoneResilient: true,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

image = azure_native.compute.Image("image",
    image_name="myImage",
    location="West US",
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.ImageStorageProfileResponseArgs(
        os_disk={
            "managedDisk": azure_native.compute.SubResourceArgs(
                id="subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk",
            ),
            "osState": azure_native.compute.OperatingSystemStateTypes.GENERALIZED,
            "osType": azure_native.compute.OperatingSystemTypes.LINUX,
        },
        zone_resilient=True,
    ))

```

```yaml
resources:
  image:
    type: azure-native:compute:Image
    properties:
      imageName: myImage
      location: West US
      resourceGroupName: myResourceGroup
      storageProfile:
        osDisk:
          managedDisk:
            id: subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk
          osState: Generalized
          osType: Linux
        zoneResilient: true

```

{{% /example %}}
{{% example %}}
### Create a virtual machine image from a snapshot with DiskEncryptionSet resource.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var image = new AzureNative.Compute.Image("image", new()
    {
        ImageName = "myImage",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.ImageStorageProfileArgs
        {
            OsDisk = new AzureNative.Compute.Inputs.ImageOSDiskArgs
            {
                DiskEncryptionSet = new AzureNative.Compute.Inputs.DiskEncryptionSetParametersArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                },
                ManagedDisk = new AzureNative.Compute.Inputs.SubResourceArgs
                {
                    Id = "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk",
                },
                OsState = AzureNative.Compute.OperatingSystemStateTypes.Generalized,
                OsType = AzureNative.Compute.OperatingSystemTypes.Linux,
            },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.Image;
import com.pulumi.azurenative.compute.ImageArgs;
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
        var image = new Image("image", ImageArgs.builder()        
            .imageName("myImage")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.of("osDisk", Map.ofEntries(
                Map.entry("diskEncryptionSet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}")),
                Map.entry("managedDisk", Map.of("id", "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk")),
                Map.entry("osState", "Generalized"),
                Map.entry("osType", "Linux")
            )))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const image = new azure_native.compute.Image("image", {
    imageName: "myImage",
    location: "West US",
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        osDisk: {
            diskEncryptionSet: {
                id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
            },
            managedDisk: {
                id: "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk",
            },
            osState: azure_native.compute.OperatingSystemStateTypes.Generalized,
            osType: azure_native.compute.OperatingSystemTypes.Linux,
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

image = azure_native.compute.Image("image",
    image_name="myImage",
    location="West US",
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.ImageStorageProfileResponseArgs(
        os_disk={
            "diskEncryptionSet": azure_native.compute.DiskEncryptionSetParametersArgs(
                id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
            ),
            "managedDisk": azure_native.compute.SubResourceArgs(
                id="subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk",
            ),
            "osState": azure_native.compute.OperatingSystemStateTypes.GENERALIZED,
            "osType": azure_native.compute.OperatingSystemTypes.LINUX,
        },
    ))

```

```yaml
resources:
  image:
    type: azure-native:compute:Image
    properties:
      imageName: myImage
      location: West US
      resourceGroupName: myResourceGroup
      storageProfile:
        osDisk:
          diskEncryptionSet:
            id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}
          managedDisk:
            id: subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk
          osState: Generalized
          osType: Linux

```

{{% /example %}}
{{% example %}}
### Create a virtual machine image from a snapshot.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var image = new AzureNative.Compute.Image("image", new()
    {
        ImageName = "myImage",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.ImageStorageProfileArgs
        {
            OsDisk = new AzureNative.Compute.Inputs.ImageOSDiskArgs
            {
                OsState = AzureNative.Compute.OperatingSystemStateTypes.Generalized,
                OsType = AzureNative.Compute.OperatingSystemTypes.Linux,
                Snapshot = new AzureNative.Compute.Inputs.SubResourceArgs
                {
                    Id = "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot",
                },
            },
            ZoneResilient = false,
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.Image;
import com.pulumi.azurenative.compute.ImageArgs;
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
        var image = new Image("image", ImageArgs.builder()        
            .imageName("myImage")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("osState", "Generalized"),
                    Map.entry("osType", "Linux"),
                    Map.entry("snapshot", Map.of("id", "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot"))
                )),
                Map.entry("zoneResilient", false)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const image = new azure_native.compute.Image("image", {
    imageName: "myImage",
    location: "West US",
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        osDisk: {
            osState: azure_native.compute.OperatingSystemStateTypes.Generalized,
            osType: azure_native.compute.OperatingSystemTypes.Linux,
            snapshot: {
                id: "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot",
            },
        },
        zoneResilient: false,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

image = azure_native.compute.Image("image",
    image_name="myImage",
    location="West US",
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.ImageStorageProfileResponseArgs(
        os_disk={
            "osState": azure_native.compute.OperatingSystemStateTypes.GENERALIZED,
            "osType": azure_native.compute.OperatingSystemTypes.LINUX,
            "snapshot": azure_native.compute.SubResourceArgs(
                id="subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot",
            ),
        },
        zone_resilient=False,
    ))

```

```yaml
resources:
  image:
    type: azure-native:compute:Image
    properties:
      imageName: myImage
      location: West US
      resourceGroupName: myResourceGroup
      storageProfile:
        osDisk:
          osState: Generalized
          osType: Linux
          snapshot:
            id: subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot
        zoneResilient: false

```

{{% /example %}}
{{% example %}}
### Create a virtual machine image from an existing virtual machine.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var image = new AzureNative.Compute.Image("image", new()
    {
        ImageName = "myImage",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        SourceVirtualMachine = new AzureNative.Compute.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM",
        },
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
		_, err := compute.NewImage(ctx, "image", &compute.ImageArgs{
			ImageName:         pulumi.String("myImage"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SourceVirtualMachine: &compute.SubResourceArgs{
				Id: pulumi.String("/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM"),
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
import com.pulumi.azurenative.compute.Image;
import com.pulumi.azurenative.compute.ImageArgs;
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
        var image = new Image("image", ImageArgs.builder()        
            .imageName("myImage")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .sourceVirtualMachine(Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const image = new azure_native.compute.Image("image", {
    imageName: "myImage",
    location: "West US",
    resourceGroupName: "myResourceGroup",
    sourceVirtualMachine: {
        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

image = azure_native.compute.Image("image",
    image_name="myImage",
    location="West US",
    resource_group_name="myResourceGroup",
    source_virtual_machine=azure_native.compute.SubResourceArgs(
        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM",
    ))

```

```yaml
resources:
  image:
    type: azure-native:compute:Image
    properties:
      imageName: myImage
      location: West US
      resourceGroupName: myResourceGroup
      sourceVirtualMachine:
        id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM

```

{{% /example %}}
{{% example %}}
### Create a virtual machine image that includes a data disk from a blob.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var image = new AzureNative.Compute.Image("image", new()
    {
        ImageName = "myImage",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.ImageStorageProfileArgs
        {
            DataDisks = new[]
            {
                new AzureNative.Compute.Inputs.ImageDataDiskArgs
                {
                    BlobUri = "https://mystorageaccount.blob.core.windows.net/dataimages/dataimage.vhd",
                    Lun = 1,
                },
            },
            OsDisk = new AzureNative.Compute.Inputs.ImageOSDiskArgs
            {
                BlobUri = "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
                OsState = AzureNative.Compute.OperatingSystemStateTypes.Generalized,
                OsType = AzureNative.Compute.OperatingSystemTypes.Linux,
            },
            ZoneResilient = false,
        },
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
		_, err := compute.NewImage(ctx, "image", &compute.ImageArgs{
			ImageName:         pulumi.String("myImage"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			StorageProfile: compute.ImageStorageProfileResponse{
				DataDisks: compute.ImageDataDiskArray{
					&compute.ImageDataDiskArgs{
						BlobUri: pulumi.String("https://mystorageaccount.blob.core.windows.net/dataimages/dataimage.vhd"),
						Lun:     pulumi.Int(1),
					},
				},
				OsDisk: &compute.ImageOSDiskArgs{
					BlobUri: pulumi.String("https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd"),
					OsState: compute.OperatingSystemStateTypesGeneralized,
					OsType:  compute.OperatingSystemTypesLinux,
				},
				ZoneResilient: pulumi.Bool(false),
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
import com.pulumi.azurenative.compute.Image;
import com.pulumi.azurenative.compute.ImageArgs;
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
        var image = new Image("image", ImageArgs.builder()        
            .imageName("myImage")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("dataDisks", Map.ofEntries(
                    Map.entry("blobUri", "https://mystorageaccount.blob.core.windows.net/dataimages/dataimage.vhd"),
                    Map.entry("lun", 1)
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("blobUri", "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd"),
                    Map.entry("osState", "Generalized"),
                    Map.entry("osType", "Linux")
                )),
                Map.entry("zoneResilient", false)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const image = new azure_native.compute.Image("image", {
    imageName: "myImage",
    location: "West US",
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        dataDisks: [{
            blobUri: "https://mystorageaccount.blob.core.windows.net/dataimages/dataimage.vhd",
            lun: 1,
        }],
        osDisk: {
            blobUri: "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
            osState: azure_native.compute.OperatingSystemStateTypes.Generalized,
            osType: azure_native.compute.OperatingSystemTypes.Linux,
        },
        zoneResilient: false,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

image = azure_native.compute.Image("image",
    image_name="myImage",
    location="West US",
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.ImageStorageProfileResponseArgs(
        data_disks=[azure_native.compute.ImageDataDiskArgs(
            blob_uri="https://mystorageaccount.blob.core.windows.net/dataimages/dataimage.vhd",
            lun=1,
        )],
        os_disk=azure_native.compute.ImageOSDiskArgs(
            blob_uri="https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
            os_state=azure_native.compute.OperatingSystemStateTypes.GENERALIZED,
            os_type=azure_native.compute.OperatingSystemTypes.LINUX,
        ),
        zone_resilient=False,
    ))

```

```yaml
resources:
  image:
    type: azure-native:compute:Image
    properties:
      imageName: myImage
      location: West US
      resourceGroupName: myResourceGroup
      storageProfile:
        dataDisks:
          - blobUri: https://mystorageaccount.blob.core.windows.net/dataimages/dataimage.vhd
            lun: 1
        osDisk:
          blobUri: https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd
          osState: Generalized
          osType: Linux
        zoneResilient: false

```

{{% /example %}}
{{% example %}}
### Create a virtual machine image that includes a data disk from a managed disk.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var image = new AzureNative.Compute.Image("image", new()
    {
        ImageName = "myImage",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.ImageStorageProfileArgs
        {
            DataDisks = new[]
            {
                new AzureNative.Compute.Inputs.ImageDataDiskArgs
                {
                    Lun = 1,
                    ManagedDisk = new AzureNative.Compute.Inputs.SubResourceArgs
                    {
                        Id = "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk2",
                    },
                },
            },
            OsDisk = new AzureNative.Compute.Inputs.ImageOSDiskArgs
            {
                ManagedDisk = new AzureNative.Compute.Inputs.SubResourceArgs
                {
                    Id = "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk",
                },
                OsState = AzureNative.Compute.OperatingSystemStateTypes.Generalized,
                OsType = AzureNative.Compute.OperatingSystemTypes.Linux,
            },
            ZoneResilient = false,
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.Image;
import com.pulumi.azurenative.compute.ImageArgs;
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
        var image = new Image("image", ImageArgs.builder()        
            .imageName("myImage")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("dataDisks", Map.ofEntries(
                    Map.entry("lun", 1),
                    Map.entry("managedDisk", Map.of("id", "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk2"))
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("managedDisk", Map.of("id", "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk")),
                    Map.entry("osState", "Generalized"),
                    Map.entry("osType", "Linux")
                )),
                Map.entry("zoneResilient", false)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const image = new azure_native.compute.Image("image", {
    imageName: "myImage",
    location: "West US",
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        dataDisks: [{
            lun: 1,
            managedDisk: {
                id: "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk2",
            },
        }],
        osDisk: {
            managedDisk: {
                id: "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk",
            },
            osState: azure_native.compute.OperatingSystemStateTypes.Generalized,
            osType: azure_native.compute.OperatingSystemTypes.Linux,
        },
        zoneResilient: false,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

image = azure_native.compute.Image("image",
    image_name="myImage",
    location="West US",
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.ImageStorageProfileResponseArgs(
        data_disks=[{
            "lun": 1,
            "managedDisk": azure_native.compute.SubResourceArgs(
                id="subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk2",
            ),
        }],
        os_disk={
            "managedDisk": azure_native.compute.SubResourceArgs(
                id="subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk",
            ),
            "osState": azure_native.compute.OperatingSystemStateTypes.GENERALIZED,
            "osType": azure_native.compute.OperatingSystemTypes.LINUX,
        },
        zone_resilient=False,
    ))

```

```yaml
resources:
  image:
    type: azure-native:compute:Image
    properties:
      imageName: myImage
      location: West US
      resourceGroupName: myResourceGroup
      storageProfile:
        dataDisks:
          - lun: 1
            managedDisk:
              id: subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk2
        osDisk:
          managedDisk:
            id: subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myManagedDisk
          osState: Generalized
          osType: Linux
        zoneResilient: false

```

{{% /example %}}
{{% example %}}
### Create a virtual machine image that includes a data disk from a snapshot.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var image = new AzureNative.Compute.Image("image", new()
    {
        ImageName = "myImage",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.ImageStorageProfileArgs
        {
            DataDisks = new[]
            {
                new AzureNative.Compute.Inputs.ImageDataDiskArgs
                {
                    Lun = 1,
                    Snapshot = new AzureNative.Compute.Inputs.SubResourceArgs
                    {
                        Id = "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot2",
                    },
                },
            },
            OsDisk = new AzureNative.Compute.Inputs.ImageOSDiskArgs
            {
                OsState = AzureNative.Compute.OperatingSystemStateTypes.Generalized,
                OsType = AzureNative.Compute.OperatingSystemTypes.Linux,
                Snapshot = new AzureNative.Compute.Inputs.SubResourceArgs
                {
                    Id = "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot",
                },
            },
            ZoneResilient = true,
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.Image;
import com.pulumi.azurenative.compute.ImageArgs;
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
        var image = new Image("image", ImageArgs.builder()        
            .imageName("myImage")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("dataDisks", Map.ofEntries(
                    Map.entry("lun", 1),
                    Map.entry("snapshot", Map.of("id", "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot2"))
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("osState", "Generalized"),
                    Map.entry("osType", "Linux"),
                    Map.entry("snapshot", Map.of("id", "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot"))
                )),
                Map.entry("zoneResilient", true)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const image = new azure_native.compute.Image("image", {
    imageName: "myImage",
    location: "West US",
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        dataDisks: [{
            lun: 1,
            snapshot: {
                id: "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot2",
            },
        }],
        osDisk: {
            osState: azure_native.compute.OperatingSystemStateTypes.Generalized,
            osType: azure_native.compute.OperatingSystemTypes.Linux,
            snapshot: {
                id: "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot",
            },
        },
        zoneResilient: true,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

image = azure_native.compute.Image("image",
    image_name="myImage",
    location="West US",
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.ImageStorageProfileResponseArgs(
        data_disks=[{
            "lun": 1,
            "snapshot": azure_native.compute.SubResourceArgs(
                id="subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot2",
            ),
        }],
        os_disk={
            "osState": azure_native.compute.OperatingSystemStateTypes.GENERALIZED,
            "osType": azure_native.compute.OperatingSystemTypes.LINUX,
            "snapshot": azure_native.compute.SubResourceArgs(
                id="subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot",
            ),
        },
        zone_resilient=True,
    ))

```

```yaml
resources:
  image:
    type: azure-native:compute:Image
    properties:
      imageName: myImage
      location: West US
      resourceGroupName: myResourceGroup
      storageProfile:
        dataDisks:
          - lun: 1
            snapshot:
              id: subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot2
        osDisk:
          osState: Generalized
          osType: Linux
          snapshot:
            id: subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot
        zoneResilient: true

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:Image myImage /subscriptions/{subscription-id}/resourceGroups/disk/providers/Microsoft.Compute/images/myImage 
```
