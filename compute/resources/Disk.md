Disk resource.
API Version: 2022-07-02.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a confidential VM supported disk encrypted with customer managed key
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "FromImage",
            ImageReference = new AzureNative.Compute.Inputs.ImageDiskReferenceArgs
            {
                Id = "/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/westus/Publishers/{publisher}/ArtifactTypes/VMImage/Offers/{offer}/Skus/{sku}/Versions/1.0.0",
            },
        },
        DiskName = "myDisk",
        Location = "West US",
        OsType = AzureNative.Compute.OperatingSystemTypes.Windows,
        ResourceGroupName = "myResourceGroup",
        SecurityProfile = new AzureNative.Compute.Inputs.DiskSecurityProfileArgs
        {
            SecureVMDiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{diskEncryptionSetName}",
            SecurityType = "ConfidentialVM_DiskEncryptedWithCustomerKey",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: compute.CreationDataResponse{
				CreateOption: pulumi.String("FromImage"),
				ImageReference: &compute.ImageDiskReferenceArgs{
					Id: pulumi.String("/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/westus/Publishers/{publisher}/ArtifactTypes/VMImage/Offers/{offer}/Skus/{sku}/Versions/1.0.0"),
				},
			},
			DiskName:          pulumi.String("myDisk"),
			Location:          pulumi.String("West US"),
			OsType:            compute.OperatingSystemTypesWindows,
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SecurityProfile: &compute.DiskSecurityProfileArgs{
				SecureVMDiskEncryptionSetId: pulumi.String("/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{diskEncryptionSetName}"),
				SecurityType:                pulumi.String("ConfidentialVM_DiskEncryptedWithCustomerKey"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "FromImage"),
                Map.entry("imageReference", Map.of("id", "/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/westus/Publishers/{publisher}/ArtifactTypes/VMImage/Offers/{offer}/Skus/{sku}/Versions/1.0.0"))
            ))
            .diskName("myDisk")
            .location("West US")
            .osType("Windows")
            .resourceGroupName("myResourceGroup")
            .securityProfile(Map.ofEntries(
                Map.entry("secureVMDiskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{diskEncryptionSetName}"),
                Map.entry("securityType", "ConfidentialVM_DiskEncryptedWithCustomerKey")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "FromImage",
        imageReference: {
            id: "/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/westus/Publishers/{publisher}/ArtifactTypes/VMImage/Offers/{offer}/Skus/{sku}/Versions/1.0.0",
        },
    },
    diskName: "myDisk",
    location: "West US",
    osType: azure_native.compute.OperatingSystemTypes.Windows,
    resourceGroupName: "myResourceGroup",
    securityProfile: {
        secureVMDiskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{diskEncryptionSetName}",
        securityType: "ConfidentialVM_DiskEncryptedWithCustomerKey",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataResponseArgs(
        create_option="FromImage",
        image_reference=azure_native.compute.ImageDiskReferenceArgs(
            id="/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/westus/Publishers/{publisher}/ArtifactTypes/VMImage/Offers/{offer}/Skus/{sku}/Versions/1.0.0",
        ),
    ),
    disk_name="myDisk",
    location="West US",
    os_type=azure_native.compute.OperatingSystemTypes.WINDOWS,
    resource_group_name="myResourceGroup",
    security_profile=azure_native.compute.DiskSecurityProfileArgs(
        secure_vm_disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{diskEncryptionSetName}",
        security_type="ConfidentialVM_DiskEncryptedWithCustomerKey",
    ))

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: FromImage
        imageReference:
          id: /Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/westus/Publishers/{publisher}/ArtifactTypes/VMImage/Offers/{offer}/Skus/{sku}/Versions/1.0.0
      diskName: myDisk
      location: West US
      osType: Windows
      resourceGroupName: myResourceGroup
      securityProfile:
        secureVMDiskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{diskEncryptionSetName}
        securityType: ConfidentialVM_DiskEncryptedWithCustomerKey

```

{{% /example %}}
{{% example %}}
### Create a managed disk and associate with disk access resource.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Empty",
        },
        DiskAccessId = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskAccesses/{existing-diskAccess-name}",
        DiskName = "myDisk",
        DiskSizeGB = 200,
        Location = "West US",
        NetworkAccessPolicy = "AllowPrivate",
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption: pulumi.String("Empty"),
			},
			DiskAccessId:        pulumi.String("/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskAccesses/{existing-diskAccess-name}"),
			DiskName:            pulumi.String("myDisk"),
			DiskSizeGB:          pulumi.Int(200),
			Location:            pulumi.String("West US"),
			NetworkAccessPolicy: pulumi.String("AllowPrivate"),
			ResourceGroupName:   pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.of("createOption", "Empty"))
            .diskAccessId("/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskAccesses/{existing-diskAccess-name}")
            .diskName("myDisk")
            .diskSizeGB(200)
            .location("West US")
            .networkAccessPolicy("AllowPrivate")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Empty",
    },
    diskAccessId: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskAccesses/{existing-diskAccess-name}",
    diskName: "myDisk",
    diskSizeGB: 200,
    location: "West US",
    networkAccessPolicy: "AllowPrivate",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Empty",
    ),
    disk_access_id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskAccesses/{existing-diskAccess-name}",
    disk_name="myDisk",
    disk_size_gb=200,
    location="West US",
    network_access_policy="AllowPrivate",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Empty
      diskAccessId: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskAccesses/{existing-diskAccess-name}
      diskName: myDisk
      diskSizeGB: 200
      location: West US
      networkAccessPolicy: AllowPrivate
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a managed disk and associate with disk encryption set.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Empty",
        },
        DiskName = "myDisk",
        DiskSizeGB = 200,
        Encryption = new AzureNative.Compute.Inputs.EncryptionArgs
        {
            DiskEncryptionSetId = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
        },
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption: pulumi.String("Empty"),
			},
			DiskName:   pulumi.String("myDisk"),
			DiskSizeGB: pulumi.Int(200),
			Encryption: &compute.EncryptionArgs{
				DiskEncryptionSetId: pulumi.String("/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}"),
			},
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.of("createOption", "Empty"))
            .diskName("myDisk")
            .diskSizeGB(200)
            .encryption(Map.of("diskEncryptionSetId", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}"))
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Empty",
    },
    diskName: "myDisk",
    diskSizeGB: 200,
    encryption: {
        diskEncryptionSetId: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
    },
    location: "West US",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Empty",
    ),
    disk_name="myDisk",
    disk_size_gb=200,
    encryption=azure_native.compute.EncryptionArgs(
        disk_encryption_set_id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
    ),
    location="West US",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Empty
      diskName: myDisk
      diskSizeGB: 200
      encryption:
        diskEncryptionSetId: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}
      location: West US
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a managed disk by copying a snapshot.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Copy",
            SourceResourceId = "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot",
        },
        DiskName = "myDisk",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption:     pulumi.String("Copy"),
				SourceResourceId: pulumi.String("subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot"),
			},
			DiskName:          pulumi.String("myDisk"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "Copy"),
                Map.entry("sourceResourceId", "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot")
            ))
            .diskName("myDisk")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Copy",
        sourceResourceId: "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot",
    },
    diskName: "myDisk",
    location: "West US",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Copy",
        source_resource_id="subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot",
    ),
    disk_name="myDisk",
    location="West US",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Copy
        sourceResourceId: subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/snapshots/mySnapshot
      diskName: myDisk
      location: West US
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a managed disk by importing an unmanaged blob from a different subscription.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Import",
            SourceUri = "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
            StorageAccountId = "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount",
        },
        DiskName = "myDisk",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption:     pulumi.String("Import"),
				SourceUri:        pulumi.String("https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd"),
				StorageAccountId: pulumi.String("subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount"),
			},
			DiskName:          pulumi.String("myDisk"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "Import"),
                Map.entry("sourceUri", "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd"),
                Map.entry("storageAccountId", "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount")
            ))
            .diskName("myDisk")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Import",
        sourceUri: "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
        storageAccountId: "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount",
    },
    diskName: "myDisk",
    location: "West US",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Import",
        source_uri="https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
        storage_account_id="subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount",
    ),
    disk_name="myDisk",
    location="West US",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Import
        sourceUri: https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd
        storageAccountId: subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount
      diskName: myDisk
      location: West US
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a managed disk by importing an unmanaged blob from the same subscription.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Import",
            SourceUri = "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
        },
        DiskName = "myDisk",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption: pulumi.String("Import"),
				SourceUri:    pulumi.String("https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd"),
			},
			DiskName:          pulumi.String("myDisk"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "Import"),
                Map.entry("sourceUri", "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd")
            ))
            .diskName("myDisk")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Import",
        sourceUri: "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
    },
    diskName: "myDisk",
    location: "West US",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Import",
        source_uri="https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
    ),
    disk_name="myDisk",
    location="West US",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Import
        sourceUri: https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd
      diskName: myDisk
      location: West US
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a managed disk from ImportSecure create option
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "ImportSecure",
            SecurityDataUri = "https://mystorageaccount.blob.core.windows.net/osimages/vmgs.vhd",
            SourceUri = "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
            StorageAccountId = "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount",
        },
        DiskName = "myDisk",
        Location = "West US",
        OsType = AzureNative.Compute.OperatingSystemTypes.Windows,
        ResourceGroupName = "myResourceGroup",
        SecurityProfile = new AzureNative.Compute.Inputs.DiskSecurityProfileArgs
        {
            SecurityType = "ConfidentialVM_VMGuestStateOnlyEncryptedWithPlatformKey",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption:     pulumi.String("ImportSecure"),
				SecurityDataUri:  pulumi.String("https://mystorageaccount.blob.core.windows.net/osimages/vmgs.vhd"),
				SourceUri:        pulumi.String("https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd"),
				StorageAccountId: pulumi.String("subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount"),
			},
			DiskName:          pulumi.String("myDisk"),
			Location:          pulumi.String("West US"),
			OsType:            compute.OperatingSystemTypesWindows,
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SecurityProfile: &compute.DiskSecurityProfileArgs{
				SecurityType: pulumi.String("ConfidentialVM_VMGuestStateOnlyEncryptedWithPlatformKey"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "ImportSecure"),
                Map.entry("securityDataUri", "https://mystorageaccount.blob.core.windows.net/osimages/vmgs.vhd"),
                Map.entry("sourceUri", "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd"),
                Map.entry("storageAccountId", "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount")
            ))
            .diskName("myDisk")
            .location("West US")
            .osType("Windows")
            .resourceGroupName("myResourceGroup")
            .securityProfile(Map.of("securityType", "ConfidentialVM_VMGuestStateOnlyEncryptedWithPlatformKey"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "ImportSecure",
        securityDataUri: "https://mystorageaccount.blob.core.windows.net/osimages/vmgs.vhd",
        sourceUri: "https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
        storageAccountId: "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount",
    },
    diskName: "myDisk",
    location: "West US",
    osType: azure_native.compute.OperatingSystemTypes.Windows,
    resourceGroupName: "myResourceGroup",
    securityProfile: {
        securityType: "ConfidentialVM_VMGuestStateOnlyEncryptedWithPlatformKey",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="ImportSecure",
        security_data_uri="https://mystorageaccount.blob.core.windows.net/osimages/vmgs.vhd",
        source_uri="https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd",
        storage_account_id="subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount",
    ),
    disk_name="myDisk",
    location="West US",
    os_type=azure_native.compute.OperatingSystemTypes.WINDOWS,
    resource_group_name="myResourceGroup",
    security_profile=azure_native.compute.DiskSecurityProfileArgs(
        security_type="ConfidentialVM_VMGuestStateOnlyEncryptedWithPlatformKey",
    ))

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: ImportSecure
        securityDataUri: https://mystorageaccount.blob.core.windows.net/osimages/vmgs.vhd
        sourceUri: https://mystorageaccount.blob.core.windows.net/osimages/osimage.vhd
        storageAccountId: subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount
      diskName: myDisk
      location: West US
      osType: Windows
      resourceGroupName: myResourceGroup
      securityProfile:
        securityType: ConfidentialVM_VMGuestStateOnlyEncryptedWithPlatformKey

```

{{% /example %}}
{{% example %}}
### Create a managed disk from UploadPreparedSecure create option
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "UploadPreparedSecure",
            UploadSizeBytes = 10737418752,
        },
        DiskName = "myDisk",
        Location = "West US",
        OsType = AzureNative.Compute.OperatingSystemTypes.Windows,
        ResourceGroupName = "myResourceGroup",
        SecurityProfile = new AzureNative.Compute.Inputs.DiskSecurityProfileArgs
        {
            SecurityType = "TrustedLaunch",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption:    pulumi.String("UploadPreparedSecure"),
				UploadSizeBytes: pulumi.Float64(10737418752),
			},
			DiskName:          pulumi.String("myDisk"),
			Location:          pulumi.String("West US"),
			OsType:            compute.OperatingSystemTypesWindows,
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SecurityProfile: &compute.DiskSecurityProfileArgs{
				SecurityType: pulumi.String("TrustedLaunch"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "UploadPreparedSecure"),
                Map.entry("uploadSizeBytes", 10737418752)
            ))
            .diskName("myDisk")
            .location("West US")
            .osType("Windows")
            .resourceGroupName("myResourceGroup")
            .securityProfile(Map.of("securityType", "TrustedLaunch"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "UploadPreparedSecure",
        uploadSizeBytes: 10737418752,
    },
    diskName: "myDisk",
    location: "West US",
    osType: azure_native.compute.OperatingSystemTypes.Windows,
    resourceGroupName: "myResourceGroup",
    securityProfile: {
        securityType: "TrustedLaunch",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="UploadPreparedSecure",
        upload_size_bytes=10737418752,
    ),
    disk_name="myDisk",
    location="West US",
    os_type=azure_native.compute.OperatingSystemTypes.WINDOWS,
    resource_group_name="myResourceGroup",
    security_profile=azure_native.compute.DiskSecurityProfileArgs(
        security_type="TrustedLaunch",
    ))

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: UploadPreparedSecure
        uploadSizeBytes: 1.0737418752e+10
      diskName: myDisk
      location: West US
      osType: Windows
      resourceGroupName: myResourceGroup
      securityProfile:
        securityType: TrustedLaunch

```

{{% /example %}}
{{% example %}}
### Create a managed disk from a platform image.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "FromImage",
            ImageReference = new AzureNative.Compute.Inputs.ImageDiskReferenceArgs
            {
                Id = "/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/westus/Publishers/{publisher}/ArtifactTypes/VMImage/Offers/{offer}/Skus/{sku}/Versions/1.0.0",
            },
        },
        DiskName = "myDisk",
        Location = "West US",
        OsType = AzureNative.Compute.OperatingSystemTypes.Windows,
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: compute.CreationDataResponse{
				CreateOption: pulumi.String("FromImage"),
				ImageReference: &compute.ImageDiskReferenceArgs{
					Id: pulumi.String("/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/westus/Publishers/{publisher}/ArtifactTypes/VMImage/Offers/{offer}/Skus/{sku}/Versions/1.0.0"),
				},
			},
			DiskName:          pulumi.String("myDisk"),
			Location:          pulumi.String("West US"),
			OsType:            compute.OperatingSystemTypesWindows,
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "FromImage"),
                Map.entry("imageReference", Map.of("id", "/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/westus/Publishers/{publisher}/ArtifactTypes/VMImage/Offers/{offer}/Skus/{sku}/Versions/1.0.0"))
            ))
            .diskName("myDisk")
            .location("West US")
            .osType("Windows")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "FromImage",
        imageReference: {
            id: "/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/westus/Publishers/{publisher}/ArtifactTypes/VMImage/Offers/{offer}/Skus/{sku}/Versions/1.0.0",
        },
    },
    diskName: "myDisk",
    location: "West US",
    osType: azure_native.compute.OperatingSystemTypes.Windows,
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataResponseArgs(
        create_option="FromImage",
        image_reference=azure_native.compute.ImageDiskReferenceArgs(
            id="/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/westus/Publishers/{publisher}/ArtifactTypes/VMImage/Offers/{offer}/Skus/{sku}/Versions/1.0.0",
        ),
    ),
    disk_name="myDisk",
    location="West US",
    os_type=azure_native.compute.OperatingSystemTypes.WINDOWS,
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: FromImage
        imageReference:
          id: /Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/westus/Publishers/{publisher}/ArtifactTypes/VMImage/Offers/{offer}/Skus/{sku}/Versions/1.0.0
      diskName: myDisk
      location: West US
      osType: Windows
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a managed disk from an Azure Compute Gallery community image.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "FromImage",
            GalleryImageReference = new AzureNative.Compute.Inputs.ImageDiskReferenceArgs
            {
                CommunityGalleryImageId = "/CommunityGalleries/{communityGalleryPublicGalleryName}/Images/{imageName}/Versions/1.0.0",
            },
        },
        DiskName = "myDisk",
        Location = "West US",
        OsType = AzureNative.Compute.OperatingSystemTypes.Windows,
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: compute.CreationDataResponse{
				CreateOption: pulumi.String("FromImage"),
				GalleryImageReference: &compute.ImageDiskReferenceArgs{
					CommunityGalleryImageId: pulumi.String("/CommunityGalleries/{communityGalleryPublicGalleryName}/Images/{imageName}/Versions/1.0.0"),
				},
			},
			DiskName:          pulumi.String("myDisk"),
			Location:          pulumi.String("West US"),
			OsType:            compute.OperatingSystemTypesWindows,
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "FromImage"),
                Map.entry("galleryImageReference", Map.of("communityGalleryImageId", "/CommunityGalleries/{communityGalleryPublicGalleryName}/Images/{imageName}/Versions/1.0.0"))
            ))
            .diskName("myDisk")
            .location("West US")
            .osType("Windows")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "FromImage",
        galleryImageReference: {
            communityGalleryImageId: "/CommunityGalleries/{communityGalleryPublicGalleryName}/Images/{imageName}/Versions/1.0.0",
        },
    },
    diskName: "myDisk",
    location: "West US",
    osType: azure_native.compute.OperatingSystemTypes.Windows,
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataResponseArgs(
        create_option="FromImage",
        gallery_image_reference=azure_native.compute.ImageDiskReferenceArgs(
            community_gallery_image_id="/CommunityGalleries/{communityGalleryPublicGalleryName}/Images/{imageName}/Versions/1.0.0",
        ),
    ),
    disk_name="myDisk",
    location="West US",
    os_type=azure_native.compute.OperatingSystemTypes.WINDOWS,
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: FromImage
        galleryImageReference:
          communityGalleryImageId: /CommunityGalleries/{communityGalleryPublicGalleryName}/Images/{imageName}/Versions/1.0.0
      diskName: myDisk
      location: West US
      osType: Windows
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a managed disk from an Azure Compute Gallery direct shared image.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "FromImage",
            GalleryImageReference = new AzureNative.Compute.Inputs.ImageDiskReferenceArgs
            {
                SharedGalleryImageId = "/SharedGalleries/{sharedGalleryUniqueName}/Images/{imageName}/Versions/1.0.0",
            },
        },
        DiskName = "myDisk",
        Location = "West US",
        OsType = AzureNative.Compute.OperatingSystemTypes.Windows,
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: compute.CreationDataResponse{
				CreateOption: pulumi.String("FromImage"),
				GalleryImageReference: &compute.ImageDiskReferenceArgs{
					SharedGalleryImageId: pulumi.String("/SharedGalleries/{sharedGalleryUniqueName}/Images/{imageName}/Versions/1.0.0"),
				},
			},
			DiskName:          pulumi.String("myDisk"),
			Location:          pulumi.String("West US"),
			OsType:            compute.OperatingSystemTypesWindows,
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "FromImage"),
                Map.entry("galleryImageReference", Map.of("sharedGalleryImageId", "/SharedGalleries/{sharedGalleryUniqueName}/Images/{imageName}/Versions/1.0.0"))
            ))
            .diskName("myDisk")
            .location("West US")
            .osType("Windows")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "FromImage",
        galleryImageReference: {
            sharedGalleryImageId: "/SharedGalleries/{sharedGalleryUniqueName}/Images/{imageName}/Versions/1.0.0",
        },
    },
    diskName: "myDisk",
    location: "West US",
    osType: azure_native.compute.OperatingSystemTypes.Windows,
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataResponseArgs(
        create_option="FromImage",
        gallery_image_reference=azure_native.compute.ImageDiskReferenceArgs(
            shared_gallery_image_id="/SharedGalleries/{sharedGalleryUniqueName}/Images/{imageName}/Versions/1.0.0",
        ),
    ),
    disk_name="myDisk",
    location="West US",
    os_type=azure_native.compute.OperatingSystemTypes.WINDOWS,
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: FromImage
        galleryImageReference:
          sharedGalleryImageId: /SharedGalleries/{sharedGalleryUniqueName}/Images/{imageName}/Versions/1.0.0
      diskName: myDisk
      location: West US
      osType: Windows
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a managed disk from an Azure Compute Gallery image.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "FromImage",
            GalleryImageReference = new AzureNative.Compute.Inputs.ImageDiskReferenceArgs
            {
                Id = "/Subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/Providers/Microsoft.Compute/Galleries/{galleryName}/Images/{imageName}/Versions/1.0.0",
            },
        },
        DiskName = "myDisk",
        Location = "West US",
        OsType = AzureNative.Compute.OperatingSystemTypes.Windows,
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: compute.CreationDataResponse{
				CreateOption: pulumi.String("FromImage"),
				GalleryImageReference: &compute.ImageDiskReferenceArgs{
					Id: pulumi.String("/Subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/Providers/Microsoft.Compute/Galleries/{galleryName}/Images/{imageName}/Versions/1.0.0"),
				},
			},
			DiskName:          pulumi.String("myDisk"),
			Location:          pulumi.String("West US"),
			OsType:            compute.OperatingSystemTypesWindows,
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "FromImage"),
                Map.entry("galleryImageReference", Map.of("id", "/Subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/Providers/Microsoft.Compute/Galleries/{galleryName}/Images/{imageName}/Versions/1.0.0"))
            ))
            .diskName("myDisk")
            .location("West US")
            .osType("Windows")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "FromImage",
        galleryImageReference: {
            id: "/Subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/Providers/Microsoft.Compute/Galleries/{galleryName}/Images/{imageName}/Versions/1.0.0",
        },
    },
    diskName: "myDisk",
    location: "West US",
    osType: azure_native.compute.OperatingSystemTypes.Windows,
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataResponseArgs(
        create_option="FromImage",
        gallery_image_reference=azure_native.compute.ImageDiskReferenceArgs(
            id="/Subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/Providers/Microsoft.Compute/Galleries/{galleryName}/Images/{imageName}/Versions/1.0.0",
        ),
    ),
    disk_name="myDisk",
    location="West US",
    os_type=azure_native.compute.OperatingSystemTypes.WINDOWS,
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: FromImage
        galleryImageReference:
          id: /Subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/Providers/Microsoft.Compute/Galleries/{galleryName}/Images/{imageName}/Versions/1.0.0
      diskName: myDisk
      location: West US
      osType: Windows
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a managed disk from an existing managed disk in the same or different subscription.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Copy",
            SourceResourceId = "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myDisk1",
        },
        DiskName = "myDisk2",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption:     pulumi.String("Copy"),
				SourceResourceId: pulumi.String("subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myDisk1"),
			},
			DiskName:          pulumi.String("myDisk2"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "Copy"),
                Map.entry("sourceResourceId", "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myDisk1")
            ))
            .diskName("myDisk2")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Copy",
        sourceResourceId: "subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myDisk1",
    },
    diskName: "myDisk2",
    location: "West US",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Copy",
        source_resource_id="subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myDisk1",
    ),
    disk_name="myDisk2",
    location="West US",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Copy
        sourceResourceId: subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/myDisk1
      diskName: myDisk2
      location: West US
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a managed disk with dataAccessAuthMode
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Empty",
        },
        DataAccessAuthMode = "AzureActiveDirectory",
        DiskName = "myDisk",
        DiskSizeGB = 200,
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption: pulumi.String("Empty"),
			},
			DataAccessAuthMode: pulumi.String("AzureActiveDirectory"),
			DiskName:           pulumi.String("myDisk"),
			DiskSizeGB:         pulumi.Int(200),
			Location:           pulumi.String("West US"),
			ResourceGroupName:  pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.of("createOption", "Empty"))
            .dataAccessAuthMode("AzureActiveDirectory")
            .diskName("myDisk")
            .diskSizeGB(200)
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Empty",
    },
    dataAccessAuthMode: "AzureActiveDirectory",
    diskName: "myDisk",
    diskSizeGB: 200,
    location: "West US",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Empty",
    ),
    data_access_auth_mode="AzureActiveDirectory",
    disk_name="myDisk",
    disk_size_gb=200,
    location="West US",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Empty
      dataAccessAuthMode: AzureActiveDirectory
      diskName: myDisk
      diskSizeGB: 200
      location: West US
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a managed disk with optimizedForFrequentAttach.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Empty",
        },
        DiskName = "myDisk",
        DiskSizeGB = 200,
        Location = "West US",
        OptimizedForFrequentAttach = true,
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption: pulumi.String("Empty"),
			},
			DiskName:                   pulumi.String("myDisk"),
			DiskSizeGB:                 pulumi.Int(200),
			Location:                   pulumi.String("West US"),
			OptimizedForFrequentAttach: pulumi.Bool(true),
			ResourceGroupName:          pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.of("createOption", "Empty"))
            .diskName("myDisk")
            .diskSizeGB(200)
            .location("West US")
            .optimizedForFrequentAttach(true)
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Empty",
    },
    diskName: "myDisk",
    diskSizeGB: 200,
    location: "West US",
    optimizedForFrequentAttach: true,
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Empty",
    ),
    disk_name="myDisk",
    disk_size_gb=200,
    location="West US",
    optimized_for_frequent_attach=True,
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Empty
      diskName: myDisk
      diskSizeGB: 200
      location: West US
      optimizedForFrequentAttach: true
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a managed disk with performancePlus.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Upload",
            PerformancePlus = true,
        },
        DiskName = "myDisk",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption:    pulumi.String("Upload"),
				PerformancePlus: pulumi.Bool(true),
			},
			DiskName:          pulumi.String("myDisk"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "Upload"),
                Map.entry("performancePlus", true)
            ))
            .diskName("myDisk")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Upload",
        performancePlus: true,
    },
    diskName: "myDisk",
    location: "West US",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Upload",
        performance_plus=True,
    ),
    disk_name="myDisk",
    location="West US",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Upload
        performancePlus: true
      diskName: myDisk
      location: West US
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a managed disk with premium v2 account type.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Empty",
        },
        DiskIOPSReadWrite = 125,
        DiskMBpsReadWrite = 3000,
        DiskName = "myPremiumV2Disk",
        DiskSizeGB = 200,
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.DiskSkuArgs
        {
            Name = "PremiumV2_LRS",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption: pulumi.String("Empty"),
			},
			DiskIOPSReadWrite: pulumi.Float64(125),
			DiskMBpsReadWrite: pulumi.Float64(3000),
			DiskName:          pulumi.String("myPremiumV2Disk"),
			DiskSizeGB:        pulumi.Int(200),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &compute.DiskSkuArgs{
				Name: pulumi.String("PremiumV2_LRS"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.of("createOption", "Empty"))
            .diskIOPSReadWrite(125)
            .diskMBpsReadWrite(3000)
            .diskName("myPremiumV2Disk")
            .diskSizeGB(200)
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "PremiumV2_LRS"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Empty",
    },
    diskIOPSReadWrite: 125,
    diskMBpsReadWrite: 3000,
    diskName: "myPremiumV2Disk",
    diskSizeGB: 200,
    location: "West US",
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "PremiumV2_LRS",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Empty",
    ),
    disk_iops_read_write=125,
    disk_m_bps_read_write=3000,
    disk_name="myPremiumV2Disk",
    disk_size_gb=200,
    location="West US",
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.DiskSkuArgs(
        name="PremiumV2_LRS",
    ))

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Empty
      diskIOPSReadWrite: 125
      diskMBpsReadWrite: 3000
      diskName: myPremiumV2Disk
      diskSizeGB: 200
      location: West US
      resourceGroupName: myResourceGroup
      sku:
        name: PremiumV2_LRS

```

{{% /example %}}
{{% example %}}
### Create a managed disk with security profile
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "FromImage",
            ImageReference = new AzureNative.Compute.Inputs.ImageDiskReferenceArgs
            {
                Id = "/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/uswest/Publishers/Microsoft/ArtifactTypes/VMImage/Offers/{offer}",
            },
        },
        DiskName = "myDisk",
        Location = "North Central US",
        OsType = AzureNative.Compute.OperatingSystemTypes.Windows,
        ResourceGroupName = "myResourceGroup",
        SecurityProfile = new AzureNative.Compute.Inputs.DiskSecurityProfileArgs
        {
            SecurityType = "TrustedLaunch",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: compute.CreationDataResponse{
				CreateOption: pulumi.String("FromImage"),
				ImageReference: &compute.ImageDiskReferenceArgs{
					Id: pulumi.String("/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/uswest/Publishers/Microsoft/ArtifactTypes/VMImage/Offers/{offer}"),
				},
			},
			DiskName:          pulumi.String("myDisk"),
			Location:          pulumi.String("North Central US"),
			OsType:            compute.OperatingSystemTypesWindows,
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SecurityProfile: &compute.DiskSecurityProfileArgs{
				SecurityType: pulumi.String("TrustedLaunch"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "FromImage"),
                Map.entry("imageReference", Map.of("id", "/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/uswest/Publishers/Microsoft/ArtifactTypes/VMImage/Offers/{offer}"))
            ))
            .diskName("myDisk")
            .location("North Central US")
            .osType("Windows")
            .resourceGroupName("myResourceGroup")
            .securityProfile(Map.of("securityType", "TrustedLaunch"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "FromImage",
        imageReference: {
            id: "/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/uswest/Publishers/Microsoft/ArtifactTypes/VMImage/Offers/{offer}",
        },
    },
    diskName: "myDisk",
    location: "North Central US",
    osType: azure_native.compute.OperatingSystemTypes.Windows,
    resourceGroupName: "myResourceGroup",
    securityProfile: {
        securityType: "TrustedLaunch",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataResponseArgs(
        create_option="FromImage",
        image_reference=azure_native.compute.ImageDiskReferenceArgs(
            id="/Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/uswest/Publishers/Microsoft/ArtifactTypes/VMImage/Offers/{offer}",
        ),
    ),
    disk_name="myDisk",
    location="North Central US",
    os_type=azure_native.compute.OperatingSystemTypes.WINDOWS,
    resource_group_name="myResourceGroup",
    security_profile=azure_native.compute.DiskSecurityProfileArgs(
        security_type="TrustedLaunch",
    ))

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: FromImage
        imageReference:
          id: /Subscriptions/{subscriptionId}/Providers/Microsoft.Compute/Locations/uswest/Publishers/Microsoft/ArtifactTypes/VMImage/Offers/{offer}
      diskName: myDisk
      location: North Central US
      osType: Windows
      resourceGroupName: myResourceGroup
      securityProfile:
        securityType: TrustedLaunch

```

{{% /example %}}
{{% example %}}
### Create a managed disk with ssd zrs account type.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Empty",
        },
        DiskName = "myDisk",
        DiskSizeGB = 200,
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.DiskSkuArgs
        {
            Name = "Premium_ZRS",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption: pulumi.String("Empty"),
			},
			DiskName:          pulumi.String("myDisk"),
			DiskSizeGB:        pulumi.Int(200),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &compute.DiskSkuArgs{
				Name: pulumi.String("Premium_ZRS"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.of("createOption", "Empty"))
            .diskName("myDisk")
            .diskSizeGB(200)
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "Premium_ZRS"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Empty",
    },
    diskName: "myDisk",
    diskSizeGB: 200,
    location: "West US",
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "Premium_ZRS",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Empty",
    ),
    disk_name="myDisk",
    disk_size_gb=200,
    location="West US",
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.DiskSkuArgs(
        name="Premium_ZRS",
    ))

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Empty
      diskName: myDisk
      diskSizeGB: 200
      location: West US
      resourceGroupName: myResourceGroup
      sku:
        name: Premium_ZRS

```

{{% /example %}}
{{% example %}}
### Create a managed disk with ultra account type with readOnly property set.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Empty",
            LogicalSectorSize = 4096,
        },
        DiskIOPSReadWrite = 125,
        DiskMBpsReadWrite = 3000,
        DiskName = "myUltraReadOnlyDisk",
        DiskSizeGB = 200,
        Encryption = new AzureNative.Compute.Inputs.EncryptionArgs
        {
            Type = "EncryptionAtRestWithPlatformKey",
        },
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.DiskSkuArgs
        {
            Name = "UltraSSD_LRS",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption:      pulumi.String("Empty"),
				LogicalSectorSize: pulumi.Int(4096),
			},
			DiskIOPSReadWrite: pulumi.Float64(125),
			DiskMBpsReadWrite: pulumi.Float64(3000),
			DiskName:          pulumi.String("myUltraReadOnlyDisk"),
			DiskSizeGB:        pulumi.Int(200),
			Encryption: &compute.EncryptionArgs{
				Type: pulumi.String("EncryptionAtRestWithPlatformKey"),
			},
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &compute.DiskSkuArgs{
				Name: pulumi.String("UltraSSD_LRS"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "Empty"),
                Map.entry("logicalSectorSize", 4096)
            ))
            .diskIOPSReadWrite(125)
            .diskMBpsReadWrite(3000)
            .diskName("myUltraReadOnlyDisk")
            .diskSizeGB(200)
            .encryption(Map.of("type", "EncryptionAtRestWithPlatformKey"))
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "UltraSSD_LRS"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Empty",
        logicalSectorSize: 4096,
    },
    diskIOPSReadWrite: 125,
    diskMBpsReadWrite: 3000,
    diskName: "myUltraReadOnlyDisk",
    diskSizeGB: 200,
    encryption: {
        type: "EncryptionAtRestWithPlatformKey",
    },
    location: "West US",
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "UltraSSD_LRS",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Empty",
        logical_sector_size=4096,
    ),
    disk_iops_read_write=125,
    disk_m_bps_read_write=3000,
    disk_name="myUltraReadOnlyDisk",
    disk_size_gb=200,
    encryption=azure_native.compute.EncryptionArgs(
        type="EncryptionAtRestWithPlatformKey",
    ),
    location="West US",
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.DiskSkuArgs(
        name="UltraSSD_LRS",
    ))

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Empty
        logicalSectorSize: 4096
      diskIOPSReadWrite: 125
      diskMBpsReadWrite: 3000
      diskName: myUltraReadOnlyDisk
      diskSizeGB: 200
      encryption:
        type: EncryptionAtRestWithPlatformKey
      location: West US
      resourceGroupName: myResourceGroup
      sku:
        name: UltraSSD_LRS

```

{{% /example %}}
{{% example %}}
### Create a managed upload disk.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Upload",
            UploadSizeBytes = 10737418752,
        },
        DiskName = "myDisk",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption:    pulumi.String("Upload"),
				UploadSizeBytes: pulumi.Float64(10737418752),
			},
			DiskName:          pulumi.String("myDisk"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "Upload"),
                Map.entry("uploadSizeBytes", 10737418752)
            ))
            .diskName("myDisk")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Upload",
        uploadSizeBytes: 10737418752,
    },
    diskName: "myDisk",
    location: "West US",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Upload",
        upload_size_bytes=10737418752,
    ),
    disk_name="myDisk",
    location="West US",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Upload
        uploadSizeBytes: 1.0737418752e+10
      diskName: myDisk
      location: West US
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create an empty managed disk in extended location.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Empty",
        },
        DiskName = "myDisk",
        DiskSizeGB = 200,
        ExtendedLocation = new AzureNative.Compute.Inputs.ExtendedLocationArgs
        {
            Name = "{edge-zone-id}",
            Type = "EdgeZone",
        },
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption: pulumi.String("Empty"),
			},
			DiskName:   pulumi.String("myDisk"),
			DiskSizeGB: pulumi.Int(200),
			ExtendedLocation: &compute.ExtendedLocationArgs{
				Name: pulumi.String("{edge-zone-id}"),
				Type: pulumi.String("EdgeZone"),
			},
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.of("createOption", "Empty"))
            .diskName("myDisk")
            .diskSizeGB(200)
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "{edge-zone-id}"),
                Map.entry("type", "EdgeZone")
            ))
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Empty",
    },
    diskName: "myDisk",
    diskSizeGB: 200,
    extendedLocation: {
        name: "{edge-zone-id}",
        type: "EdgeZone",
    },
    location: "West US",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Empty",
    ),
    disk_name="myDisk",
    disk_size_gb=200,
    extended_location=azure_native.compute.ExtendedLocationArgs(
        name="{edge-zone-id}",
        type="EdgeZone",
    ),
    location="West US",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Empty
      diskName: myDisk
      diskSizeGB: 200
      extendedLocation:
        name: '{edge-zone-id}'
        type: EdgeZone
      location: West US
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create an empty managed disk.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Empty",
        },
        DiskName = "myDisk",
        DiskSizeGB = 200,
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption: pulumi.String("Empty"),
			},
			DiskName:          pulumi.String("myDisk"),
			DiskSizeGB:        pulumi.Int(200),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.of("createOption", "Empty"))
            .diskName("myDisk")
            .diskSizeGB(200)
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Empty",
    },
    diskName: "myDisk",
    diskSizeGB: 200,
    location: "West US",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Empty",
    ),
    disk_name="myDisk",
    disk_size_gb=200,
    location="West US",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Empty
      diskName: myDisk
      diskSizeGB: 200
      location: West US
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create an ultra managed disk with logicalSectorSize 512E
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.Compute.Disk("disk", new()
    {
        CreationData = new AzureNative.Compute.Inputs.CreationDataArgs
        {
            CreateOption = "Empty",
            LogicalSectorSize = 512,
        },
        DiskName = "myDisk",
        DiskSizeGB = 200,
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.DiskSkuArgs
        {
            Name = "UltraSSD_LRS",
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
		_, err := compute.NewDisk(ctx, "disk", &compute.DiskArgs{
			CreationData: &compute.CreationDataArgs{
				CreateOption:      pulumi.String("Empty"),
				LogicalSectorSize: pulumi.Int(512),
			},
			DiskName:          pulumi.String("myDisk"),
			DiskSizeGB:        pulumi.Int(200),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &compute.DiskSkuArgs{
				Name: pulumi.String("UltraSSD_LRS"),
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
import com.pulumi.azurenative.compute.Disk;
import com.pulumi.azurenative.compute.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .creationData(Map.ofEntries(
                Map.entry("createOption", "Empty"),
                Map.entry("logicalSectorSize", 512)
            ))
            .diskName("myDisk")
            .diskSizeGB(200)
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "UltraSSD_LRS"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.compute.Disk("disk", {
    creationData: {
        createOption: "Empty",
        logicalSectorSize: 512,
    },
    diskName: "myDisk",
    diskSizeGB: 200,
    location: "West US",
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "UltraSSD_LRS",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.compute.Disk("disk",
    creation_data=azure_native.compute.CreationDataArgs(
        create_option="Empty",
        logical_sector_size=512,
    ),
    disk_name="myDisk",
    disk_size_gb=200,
    location="West US",
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.DiskSkuArgs(
        name="UltraSSD_LRS",
    ))

```

```yaml
resources:
  disk:
    type: azure-native:compute:Disk
    properties:
      creationData:
        createOption: Empty
        logicalSectorSize: 512
      diskName: myDisk
      diskSizeGB: 200
      location: West US
      resourceGroupName: myResourceGroup
      sku:
        name: UltraSSD_LRS

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:Disk myDisk /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/disks/{diskName} 
```
