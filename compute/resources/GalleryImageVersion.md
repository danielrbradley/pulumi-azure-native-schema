Specifies information about the gallery image version that you want to create or update.
API Version: 2022-03-03.
Previous API Version: 2020-09-30. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a simple Gallery Image Version using VM as source.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var galleryImageVersion = new AzureNative.Compute.GalleryImageVersion("galleryImageVersion", new()
    {
        GalleryImageName = "myGalleryImageName",
        GalleryImageVersionName = "1.0.0",
        GalleryName = "myGalleryName",
        Location = "West US",
        PublishingProfile = new AzureNative.Compute.Inputs.GalleryImageVersionPublishingProfileArgs
        {
            TargetRegions = new[]
            {
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    Encryption = new AzureNative.Compute.Inputs.EncryptionImagesArgs
                    {
                        DataDiskImages = new[]
                        {
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                                Lun = 0,
                            },
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                                Lun = 1,
                            },
                        },
                        OsDiskImage = new AzureNative.Compute.Inputs.OSDiskImageEncryptionArgs
                        {
                            DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                        },
                    },
                    ExcludeFromLatest = false,
                    Name = "West US",
                    RegionalReplicaCount = 2,
                },
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    Encryption = new AzureNative.Compute.Inputs.EncryptionImagesArgs
                    {
                        DataDiskImages = new[]
                        {
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                                Lun = 0,
                            },
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                                Lun = 1,
                            },
                        },
                        OsDiskImage = new AzureNative.Compute.Inputs.OSDiskImageEncryptionArgs
                        {
                            DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                        },
                    },
                    ExcludeFromLatest = false,
                    Name = "East US",
                    RegionalReplicaCount = 2,
                    StorageAccountType = "Standard_ZRS",
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        SafetyProfile = new AzureNative.Compute.Inputs.GalleryImageVersionSafetyProfileArgs
        {
            AllowDeletionOfReplicatedLocations = false,
        },
        StorageProfile = new AzureNative.Compute.Inputs.GalleryImageVersionStorageProfileArgs
        {
            Source = new AzureNative.Compute.Inputs.GalleryArtifactVersionFullSourceArgs
            {
                Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/virtualMachines/{vmName}",
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
import com.pulumi.azurenative.compute.GalleryImageVersion;
import com.pulumi.azurenative.compute.GalleryImageVersionArgs;
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
        var galleryImageVersion = new GalleryImageVersion("galleryImageVersion", GalleryImageVersionArgs.builder()        
            .galleryImageName("myGalleryImageName")
            .galleryImageVersionName("1.0.0")
            .galleryName("myGalleryName")
            .location("West US")
            .publishingProfile(Map.of("targetRegions",             
                Map.ofEntries(
                    Map.entry("encryption", Map.ofEntries(
                        Map.entry("dataDiskImages",                         
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet"),
                                Map.entry("lun", 0)
                            ),
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet"),
                                Map.entry("lun", 1)
                            )),
                        Map.entry("osDiskImage", Map.of("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet"))
                    )),
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "West US"),
                    Map.entry("regionalReplicaCount", 2)
                ),
                Map.ofEntries(
                    Map.entry("encryption", Map.ofEntries(
                        Map.entry("dataDiskImages",                         
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet"),
                                Map.entry("lun", 0)
                            ),
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet"),
                                Map.entry("lun", 1)
                            )),
                        Map.entry("osDiskImage", Map.of("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet"))
                    )),
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "East US"),
                    Map.entry("regionalReplicaCount", 2),
                    Map.entry("storageAccountType", "Standard_ZRS")
                )))
            .resourceGroupName("myResourceGroup")
            .safetyProfile(Map.of("allowDeletionOfReplicatedLocations", false))
            .storageProfile(Map.of("source", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/virtualMachines/{vmName}")))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const galleryImageVersion = new azure_native.compute.GalleryImageVersion("galleryImageVersion", {
    galleryImageName: "myGalleryImageName",
    galleryImageVersionName: "1.0.0",
    galleryName: "myGalleryName",
    location: "West US",
    publishingProfile: {
        targetRegions: [
            {
                encryption: {
                    dataDiskImages: [
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                            lun: 0,
                        },
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                            lun: 1,
                        },
                    ],
                    osDiskImage: {
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                    },
                },
                excludeFromLatest: false,
                name: "West US",
                regionalReplicaCount: 2,
            },
            {
                encryption: {
                    dataDiskImages: [
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                            lun: 0,
                        },
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                            lun: 1,
                        },
                    ],
                    osDiskImage: {
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                    },
                },
                excludeFromLatest: false,
                name: "East US",
                regionalReplicaCount: 2,
                storageAccountType: "Standard_ZRS",
            },
        ],
    },
    resourceGroupName: "myResourceGroup",
    safetyProfile: {
        allowDeletionOfReplicatedLocations: false,
    },
    storageProfile: {
        source: {
            id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/virtualMachines/{vmName}",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery_image_version = azure_native.compute.GalleryImageVersion("galleryImageVersion",
    gallery_image_name="myGalleryImageName",
    gallery_image_version_name="1.0.0",
    gallery_name="myGalleryName",
    location="West US",
    publishing_profile=azure_native.compute.GalleryImageVersionPublishingProfileResponseArgs(
        target_regions=[
            {
                "encryption": {
                    "dataDiskImages": [
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                            lun=0,
                        ),
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                            lun=1,
                        ),
                    ],
                    "osDiskImage": azure_native.compute.OSDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                    ),
                },
                "excludeFromLatest": False,
                "name": "West US",
                "regionalReplicaCount": 2,
            },
            {
                "encryption": {
                    "dataDiskImages": [
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                            lun=0,
                        ),
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                            lun=1,
                        ),
                    ],
                    "osDiskImage": azure_native.compute.OSDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                    ),
                },
                "excludeFromLatest": False,
                "name": "East US",
                "regionalReplicaCount": 2,
                "storageAccountType": "Standard_ZRS",
            },
        ],
    ),
    resource_group_name="myResourceGroup",
    safety_profile=azure_native.compute.GalleryImageVersionSafetyProfileArgs(
        allow_deletion_of_replicated_locations=False,
    ),
    storage_profile=azure_native.compute.GalleryImageVersionStorageProfileResponseArgs(
        source=azure_native.compute.GalleryArtifactVersionFullSourceArgs(
            id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/virtualMachines/{vmName}",
        ),
    ))

```

```yaml
resources:
  galleryImageVersion:
    type: azure-native:compute:GalleryImageVersion
    properties:
      galleryImageName: myGalleryImageName
      galleryImageVersionName: 1.0.0
      galleryName: myGalleryName
      location: West US
      publishingProfile:
        targetRegions:
          - encryption:
              dataDiskImages:
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet
                  lun: 0
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet
                  lun: 1
              osDiskImage:
                diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet
            excludeFromLatest: false
            name: West US
            regionalReplicaCount: 2
          - encryption:
              dataDiskImages:
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet
                  lun: 0
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet
                  lun: 1
              osDiskImage:
                diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet
            excludeFromLatest: false
            name: East US
            regionalReplicaCount: 2
            storageAccountType: Standard_ZRS
      resourceGroupName: myResourceGroup
      safetyProfile:
        allowDeletionOfReplicatedLocations: false
      storageProfile:
        source:
          id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/virtualMachines/{vmName}

```

{{% /example %}}
{{% example %}}
### Create or update a simple Gallery Image Version using community gallery image as source.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var galleryImageVersion = new AzureNative.Compute.GalleryImageVersion("galleryImageVersion", new()
    {
        GalleryImageName = "myGalleryImageName",
        GalleryImageVersionName = "1.0.0",
        GalleryName = "myGalleryName",
        Location = "West US",
        PublishingProfile = new AzureNative.Compute.Inputs.GalleryImageVersionPublishingProfileArgs
        {
            TargetRegions = new[]
            {
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    Encryption = new AzureNative.Compute.Inputs.EncryptionImagesArgs
                    {
                        DataDiskImages = new[]
                        {
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                                Lun = 0,
                            },
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                                Lun = 1,
                            },
                        },
                        OsDiskImage = new AzureNative.Compute.Inputs.OSDiskImageEncryptionArgs
                        {
                            DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                        },
                    },
                    ExcludeFromLatest = false,
                    Name = "West US",
                    RegionalReplicaCount = 1,
                },
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    Encryption = new AzureNative.Compute.Inputs.EncryptionImagesArgs
                    {
                        DataDiskImages = new[]
                        {
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                                Lun = 0,
                            },
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                                Lun = 1,
                            },
                        },
                        OsDiskImage = new AzureNative.Compute.Inputs.OSDiskImageEncryptionArgs
                        {
                            DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                        },
                    },
                    ExcludeFromLatest = false,
                    Name = "East US",
                    RegionalReplicaCount = 2,
                    StorageAccountType = "Standard_ZRS",
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        SafetyProfile = new AzureNative.Compute.Inputs.GalleryImageVersionSafetyProfileArgs
        {
            AllowDeletionOfReplicatedLocations = false,
        },
        StorageProfile = new AzureNative.Compute.Inputs.GalleryImageVersionStorageProfileArgs
        {
            Source = new AzureNative.Compute.Inputs.GalleryArtifactVersionFullSourceArgs
            {
                CommunityGalleryImageId = "/communityGalleries/{communityGalleryName}/images/{communityGalleryImageName}",
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
import com.pulumi.azurenative.compute.GalleryImageVersion;
import com.pulumi.azurenative.compute.GalleryImageVersionArgs;
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
        var galleryImageVersion = new GalleryImageVersion("galleryImageVersion", GalleryImageVersionArgs.builder()        
            .galleryImageName("myGalleryImageName")
            .galleryImageVersionName("1.0.0")
            .galleryName("myGalleryName")
            .location("West US")
            .publishingProfile(Map.of("targetRegions",             
                Map.ofEntries(
                    Map.entry("encryption", Map.ofEntries(
                        Map.entry("dataDiskImages",                         
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet"),
                                Map.entry("lun", 0)
                            ),
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet"),
                                Map.entry("lun", 1)
                            )),
                        Map.entry("osDiskImage", Map.of("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet"))
                    )),
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "West US"),
                    Map.entry("regionalReplicaCount", 1)
                ),
                Map.ofEntries(
                    Map.entry("encryption", Map.ofEntries(
                        Map.entry("dataDiskImages",                         
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet"),
                                Map.entry("lun", 0)
                            ),
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet"),
                                Map.entry("lun", 1)
                            )),
                        Map.entry("osDiskImage", Map.of("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet"))
                    )),
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "East US"),
                    Map.entry("regionalReplicaCount", 2),
                    Map.entry("storageAccountType", "Standard_ZRS")
                )))
            .resourceGroupName("myResourceGroup")
            .safetyProfile(Map.of("allowDeletionOfReplicatedLocations", false))
            .storageProfile(Map.of("source", Map.of("communityGalleryImageId", "/communityGalleries/{communityGalleryName}/images/{communityGalleryImageName}")))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const galleryImageVersion = new azure_native.compute.GalleryImageVersion("galleryImageVersion", {
    galleryImageName: "myGalleryImageName",
    galleryImageVersionName: "1.0.0",
    galleryName: "myGalleryName",
    location: "West US",
    publishingProfile: {
        targetRegions: [
            {
                encryption: {
                    dataDiskImages: [
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                            lun: 0,
                        },
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                            lun: 1,
                        },
                    ],
                    osDiskImage: {
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                    },
                },
                excludeFromLatest: false,
                name: "West US",
                regionalReplicaCount: 1,
            },
            {
                encryption: {
                    dataDiskImages: [
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                            lun: 0,
                        },
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                            lun: 1,
                        },
                    ],
                    osDiskImage: {
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                    },
                },
                excludeFromLatest: false,
                name: "East US",
                regionalReplicaCount: 2,
                storageAccountType: "Standard_ZRS",
            },
        ],
    },
    resourceGroupName: "myResourceGroup",
    safetyProfile: {
        allowDeletionOfReplicatedLocations: false,
    },
    storageProfile: {
        source: {
            communityGalleryImageId: "/communityGalleries/{communityGalleryName}/images/{communityGalleryImageName}",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery_image_version = azure_native.compute.GalleryImageVersion("galleryImageVersion",
    gallery_image_name="myGalleryImageName",
    gallery_image_version_name="1.0.0",
    gallery_name="myGalleryName",
    location="West US",
    publishing_profile=azure_native.compute.GalleryImageVersionPublishingProfileResponseArgs(
        target_regions=[
            {
                "encryption": {
                    "dataDiskImages": [
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                            lun=0,
                        ),
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                            lun=1,
                        ),
                    ],
                    "osDiskImage": azure_native.compute.OSDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                    ),
                },
                "excludeFromLatest": False,
                "name": "West US",
                "regionalReplicaCount": 1,
            },
            {
                "encryption": {
                    "dataDiskImages": [
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                            lun=0,
                        ),
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                            lun=1,
                        ),
                    ],
                    "osDiskImage": azure_native.compute.OSDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                    ),
                },
                "excludeFromLatest": False,
                "name": "East US",
                "regionalReplicaCount": 2,
                "storageAccountType": "Standard_ZRS",
            },
        ],
    ),
    resource_group_name="myResourceGroup",
    safety_profile=azure_native.compute.GalleryImageVersionSafetyProfileArgs(
        allow_deletion_of_replicated_locations=False,
    ),
    storage_profile=azure_native.compute.GalleryImageVersionStorageProfileResponseArgs(
        source=azure_native.compute.GalleryArtifactVersionFullSourceArgs(
            community_gallery_image_id="/communityGalleries/{communityGalleryName}/images/{communityGalleryImageName}",
        ),
    ))

```

```yaml
resources:
  galleryImageVersion:
    type: azure-native:compute:GalleryImageVersion
    properties:
      galleryImageName: myGalleryImageName
      galleryImageVersionName: 1.0.0
      galleryName: myGalleryName
      location: West US
      publishingProfile:
        targetRegions:
          - encryption:
              dataDiskImages:
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet
                  lun: 0
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet
                  lun: 1
              osDiskImage:
                diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet
            excludeFromLatest: false
            name: West US
            regionalReplicaCount: 1
          - encryption:
              dataDiskImages:
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet
                  lun: 0
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet
                  lun: 1
              osDiskImage:
                diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet
            excludeFromLatest: false
            name: East US
            regionalReplicaCount: 2
            storageAccountType: Standard_ZRS
      resourceGroupName: myResourceGroup
      safetyProfile:
        allowDeletionOfReplicatedLocations: false
      storageProfile:
        source:
          communityGalleryImageId: /communityGalleries/{communityGalleryName}/images/{communityGalleryImageName}

```

{{% /example %}}
{{% example %}}
### Create or update a simple Gallery Image Version using managed image as source.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var galleryImageVersion = new AzureNative.Compute.GalleryImageVersion("galleryImageVersion", new()
    {
        GalleryImageName = "myGalleryImageName",
        GalleryImageVersionName = "1.0.0",
        GalleryName = "myGalleryName",
        Location = "West US",
        PublishingProfile = new AzureNative.Compute.Inputs.GalleryImageVersionPublishingProfileArgs
        {
            TargetRegions = new[]
            {
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    Encryption = new AzureNative.Compute.Inputs.EncryptionImagesArgs
                    {
                        DataDiskImages = new[]
                        {
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                                Lun = 0,
                            },
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                                Lun = 1,
                            },
                        },
                        OsDiskImage = new AzureNative.Compute.Inputs.OSDiskImageEncryptionArgs
                        {
                            DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                        },
                    },
                    ExcludeFromLatest = false,
                    Name = "West US",
                    RegionalReplicaCount = 1,
                },
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    Encryption = new AzureNative.Compute.Inputs.EncryptionImagesArgs
                    {
                        DataDiskImages = new[]
                        {
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                                Lun = 0,
                            },
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                                Lun = 1,
                            },
                        },
                        OsDiskImage = new AzureNative.Compute.Inputs.OSDiskImageEncryptionArgs
                        {
                            DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                        },
                    },
                    ExcludeFromLatest = false,
                    Name = "East US",
                    RegionalReplicaCount = 2,
                    StorageAccountType = "Standard_ZRS",
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        SafetyProfile = new AzureNative.Compute.Inputs.GalleryImageVersionSafetyProfileArgs
        {
            AllowDeletionOfReplicatedLocations = false,
        },
        StorageProfile = new AzureNative.Compute.Inputs.GalleryImageVersionStorageProfileArgs
        {
            Source = new AzureNative.Compute.Inputs.GalleryArtifactVersionFullSourceArgs
            {
                Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}",
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
import com.pulumi.azurenative.compute.GalleryImageVersion;
import com.pulumi.azurenative.compute.GalleryImageVersionArgs;
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
        var galleryImageVersion = new GalleryImageVersion("galleryImageVersion", GalleryImageVersionArgs.builder()        
            .galleryImageName("myGalleryImageName")
            .galleryImageVersionName("1.0.0")
            .galleryName("myGalleryName")
            .location("West US")
            .publishingProfile(Map.of("targetRegions",             
                Map.ofEntries(
                    Map.entry("encryption", Map.ofEntries(
                        Map.entry("dataDiskImages",                         
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet"),
                                Map.entry("lun", 0)
                            ),
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet"),
                                Map.entry("lun", 1)
                            )),
                        Map.entry("osDiskImage", Map.of("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet"))
                    )),
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "West US"),
                    Map.entry("regionalReplicaCount", 1)
                ),
                Map.ofEntries(
                    Map.entry("encryption", Map.ofEntries(
                        Map.entry("dataDiskImages",                         
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet"),
                                Map.entry("lun", 0)
                            ),
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet"),
                                Map.entry("lun", 1)
                            )),
                        Map.entry("osDiskImage", Map.of("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet"))
                    )),
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "East US"),
                    Map.entry("regionalReplicaCount", 2),
                    Map.entry("storageAccountType", "Standard_ZRS")
                )))
            .resourceGroupName("myResourceGroup")
            .safetyProfile(Map.of("allowDeletionOfReplicatedLocations", false))
            .storageProfile(Map.of("source", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}")))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const galleryImageVersion = new azure_native.compute.GalleryImageVersion("galleryImageVersion", {
    galleryImageName: "myGalleryImageName",
    galleryImageVersionName: "1.0.0",
    galleryName: "myGalleryName",
    location: "West US",
    publishingProfile: {
        targetRegions: [
            {
                encryption: {
                    dataDiskImages: [
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                            lun: 0,
                        },
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                            lun: 1,
                        },
                    ],
                    osDiskImage: {
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                    },
                },
                excludeFromLatest: false,
                name: "West US",
                regionalReplicaCount: 1,
            },
            {
                encryption: {
                    dataDiskImages: [
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                            lun: 0,
                        },
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                            lun: 1,
                        },
                    ],
                    osDiskImage: {
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                    },
                },
                excludeFromLatest: false,
                name: "East US",
                regionalReplicaCount: 2,
                storageAccountType: "Standard_ZRS",
            },
        ],
    },
    resourceGroupName: "myResourceGroup",
    safetyProfile: {
        allowDeletionOfReplicatedLocations: false,
    },
    storageProfile: {
        source: {
            id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery_image_version = azure_native.compute.GalleryImageVersion("galleryImageVersion",
    gallery_image_name="myGalleryImageName",
    gallery_image_version_name="1.0.0",
    gallery_name="myGalleryName",
    location="West US",
    publishing_profile=azure_native.compute.GalleryImageVersionPublishingProfileResponseArgs(
        target_regions=[
            {
                "encryption": {
                    "dataDiskImages": [
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                            lun=0,
                        ),
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                            lun=1,
                        ),
                    ],
                    "osDiskImage": azure_native.compute.OSDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                    ),
                },
                "excludeFromLatest": False,
                "name": "West US",
                "regionalReplicaCount": 1,
            },
            {
                "encryption": {
                    "dataDiskImages": [
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                            lun=0,
                        ),
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                            lun=1,
                        ),
                    ],
                    "osDiskImage": azure_native.compute.OSDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                    ),
                },
                "excludeFromLatest": False,
                "name": "East US",
                "regionalReplicaCount": 2,
                "storageAccountType": "Standard_ZRS",
            },
        ],
    ),
    resource_group_name="myResourceGroup",
    safety_profile=azure_native.compute.GalleryImageVersionSafetyProfileArgs(
        allow_deletion_of_replicated_locations=False,
    ),
    storage_profile=azure_native.compute.GalleryImageVersionStorageProfileResponseArgs(
        source=azure_native.compute.GalleryArtifactVersionFullSourceArgs(
            id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}",
        ),
    ))

```

```yaml
resources:
  galleryImageVersion:
    type: azure-native:compute:GalleryImageVersion
    properties:
      galleryImageName: myGalleryImageName
      galleryImageVersionName: 1.0.0
      galleryName: myGalleryName
      location: West US
      publishingProfile:
        targetRegions:
          - encryption:
              dataDiskImages:
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet
                  lun: 0
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet
                  lun: 1
              osDiskImage:
                diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet
            excludeFromLatest: false
            name: West US
            regionalReplicaCount: 1
          - encryption:
              dataDiskImages:
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet
                  lun: 0
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet
                  lun: 1
              osDiskImage:
                diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet
            excludeFromLatest: false
            name: East US
            regionalReplicaCount: 2
            storageAccountType: Standard_ZRS
      resourceGroupName: myResourceGroup
      safetyProfile:
        allowDeletionOfReplicatedLocations: false
      storageProfile:
        source:
          id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}

```

{{% /example %}}
{{% example %}}
### Create or update a simple Gallery Image Version using mix of disks and snapshots as a source.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var galleryImageVersion = new AzureNative.Compute.GalleryImageVersion("galleryImageVersion", new()
    {
        GalleryImageName = "myGalleryImageName",
        GalleryImageVersionName = "1.0.0",
        GalleryName = "myGalleryName",
        Location = "West US",
        PublishingProfile = new AzureNative.Compute.Inputs.GalleryImageVersionPublishingProfileArgs
        {
            TargetRegions = new[]
            {
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    Encryption = new AzureNative.Compute.Inputs.EncryptionImagesArgs
                    {
                        DataDiskImages = new[]
                        {
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                                Lun = 1,
                            },
                        },
                        OsDiskImage = new AzureNative.Compute.Inputs.OSDiskImageEncryptionArgs
                        {
                            DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                        },
                    },
                    ExcludeFromLatest = false,
                    Name = "West US",
                    RegionalReplicaCount = 1,
                },
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    Encryption = new AzureNative.Compute.Inputs.EncryptionImagesArgs
                    {
                        DataDiskImages = new[]
                        {
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                                Lun = 1,
                            },
                        },
                        OsDiskImage = new AzureNative.Compute.Inputs.OSDiskImageEncryptionArgs
                        {
                            DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                        },
                    },
                    ExcludeFromLatest = false,
                    Name = "East US",
                    RegionalReplicaCount = 2,
                    StorageAccountType = "Standard_ZRS",
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        SafetyProfile = new AzureNative.Compute.Inputs.GalleryImageVersionSafetyProfileArgs
        {
            AllowDeletionOfReplicatedLocations = false,
        },
        StorageProfile = new AzureNative.Compute.Inputs.GalleryImageVersionStorageProfileArgs
        {
            DataDiskImages = new[]
            {
                new AzureNative.Compute.Inputs.GalleryDataDiskImageArgs
                {
                    HostCaching = AzureNative.Compute.HostCaching.None,
                    Lun = 1,
                    Source = new AzureNative.Compute.Inputs.GalleryDiskImageSourceArgs
                    {
                        Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/disks/{dataDiskName}",
                    },
                },
            },
            OsDiskImage = new AzureNative.Compute.Inputs.GalleryOSDiskImageArgs
            {
                HostCaching = AzureNative.Compute.HostCaching.ReadOnly,
                Source = new AzureNative.Compute.Inputs.GalleryDiskImageSourceArgs
                {
                    Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/snapshots/{osSnapshotName}",
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
import com.pulumi.azurenative.compute.GalleryImageVersion;
import com.pulumi.azurenative.compute.GalleryImageVersionArgs;
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
        var galleryImageVersion = new GalleryImageVersion("galleryImageVersion", GalleryImageVersionArgs.builder()        
            .galleryImageName("myGalleryImageName")
            .galleryImageVersionName("1.0.0")
            .galleryName("myGalleryName")
            .location("West US")
            .publishingProfile(Map.of("targetRegions",             
                Map.ofEntries(
                    Map.entry("encryption", Map.ofEntries(
                        Map.entry("dataDiskImages", Map.ofEntries(
                            Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet"),
                            Map.entry("lun", 1)
                        )),
                        Map.entry("osDiskImage", Map.of("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet"))
                    )),
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "West US"),
                    Map.entry("regionalReplicaCount", 1)
                ),
                Map.ofEntries(
                    Map.entry("encryption", Map.ofEntries(
                        Map.entry("dataDiskImages", Map.ofEntries(
                            Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet"),
                            Map.entry("lun", 1)
                        )),
                        Map.entry("osDiskImage", Map.of("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet"))
                    )),
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "East US"),
                    Map.entry("regionalReplicaCount", 2),
                    Map.entry("storageAccountType", "Standard_ZRS")
                )))
            .resourceGroupName("myResourceGroup")
            .safetyProfile(Map.of("allowDeletionOfReplicatedLocations", false))
            .storageProfile(Map.ofEntries(
                Map.entry("dataDiskImages", Map.ofEntries(
                    Map.entry("hostCaching", "None"),
                    Map.entry("lun", 1),
                    Map.entry("source", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/disks/{dataDiskName}"))
                )),
                Map.entry("osDiskImage", Map.ofEntries(
                    Map.entry("hostCaching", "ReadOnly"),
                    Map.entry("source", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/snapshots/{osSnapshotName}"))
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const galleryImageVersion = new azure_native.compute.GalleryImageVersion("galleryImageVersion", {
    galleryImageName: "myGalleryImageName",
    galleryImageVersionName: "1.0.0",
    galleryName: "myGalleryName",
    location: "West US",
    publishingProfile: {
        targetRegions: [
            {
                encryption: {
                    dataDiskImages: [{
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                        lun: 1,
                    }],
                    osDiskImage: {
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                    },
                },
                excludeFromLatest: false,
                name: "West US",
                regionalReplicaCount: 1,
            },
            {
                encryption: {
                    dataDiskImages: [{
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                        lun: 1,
                    }],
                    osDiskImage: {
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                    },
                },
                excludeFromLatest: false,
                name: "East US",
                regionalReplicaCount: 2,
                storageAccountType: "Standard_ZRS",
            },
        ],
    },
    resourceGroupName: "myResourceGroup",
    safetyProfile: {
        allowDeletionOfReplicatedLocations: false,
    },
    storageProfile: {
        dataDiskImages: [{
            hostCaching: azure_native.compute.HostCaching.None,
            lun: 1,
            source: {
                id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/disks/{dataDiskName}",
            },
        }],
        osDiskImage: {
            hostCaching: azure_native.compute.HostCaching.ReadOnly,
            source: {
                id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/snapshots/{osSnapshotName}",
            },
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery_image_version = azure_native.compute.GalleryImageVersion("galleryImageVersion",
    gallery_image_name="myGalleryImageName",
    gallery_image_version_name="1.0.0",
    gallery_name="myGalleryName",
    location="West US",
    publishing_profile=azure_native.compute.GalleryImageVersionPublishingProfileResponseArgs(
        target_regions=[
            {
                "encryption": {
                    "dataDiskImages": [azure_native.compute.DataDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                        lun=1,
                    )],
                    "osDiskImage": azure_native.compute.OSDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                    ),
                },
                "excludeFromLatest": False,
                "name": "West US",
                "regionalReplicaCount": 1,
            },
            {
                "encryption": {
                    "dataDiskImages": [azure_native.compute.DataDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                        lun=1,
                    )],
                    "osDiskImage": azure_native.compute.OSDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                    ),
                },
                "excludeFromLatest": False,
                "name": "East US",
                "regionalReplicaCount": 2,
                "storageAccountType": "Standard_ZRS",
            },
        ],
    ),
    resource_group_name="myResourceGroup",
    safety_profile=azure_native.compute.GalleryImageVersionSafetyProfileArgs(
        allow_deletion_of_replicated_locations=False,
    ),
    storage_profile=azure_native.compute.GalleryImageVersionStorageProfileResponseArgs(
        data_disk_images=[{
            "hostCaching": azure_native.compute.HostCaching.NONE,
            "lun": 1,
            "source": azure_native.compute.GalleryDiskImageSourceArgs(
                id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/disks/{dataDiskName}",
            ),
        }],
        os_disk_image={
            "hostCaching": azure_native.compute.HostCaching.READ_ONLY,
            "source": azure_native.compute.GalleryDiskImageSourceArgs(
                id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/snapshots/{osSnapshotName}",
            ),
        },
    ))

```

```yaml
resources:
  galleryImageVersion:
    type: azure-native:compute:GalleryImageVersion
    properties:
      galleryImageName: myGalleryImageName
      galleryImageVersionName: 1.0.0
      galleryName: myGalleryName
      location: West US
      publishingProfile:
        targetRegions:
          - encryption:
              dataDiskImages:
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet
                  lun: 1
              osDiskImage:
                diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet
            excludeFromLatest: false
            name: West US
            regionalReplicaCount: 1
          - encryption:
              dataDiskImages:
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet
                  lun: 1
              osDiskImage:
                diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet
            excludeFromLatest: false
            name: East US
            regionalReplicaCount: 2
            storageAccountType: Standard_ZRS
      resourceGroupName: myResourceGroup
      safetyProfile:
        allowDeletionOfReplicatedLocations: false
      storageProfile:
        dataDiskImages:
          - hostCaching: None
            lun: 1
            source:
              id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/disks/{dataDiskName}
        osDiskImage:
          hostCaching: ReadOnly
          source:
            id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/snapshots/{osSnapshotName}

```

{{% /example %}}
{{% example %}}
### Create or update a simple Gallery Image Version using shallow replication mode.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var galleryImageVersion = new AzureNative.Compute.GalleryImageVersion("galleryImageVersion", new()
    {
        GalleryImageName = "myGalleryImageName",
        GalleryImageVersionName = "1.0.0",
        GalleryName = "myGalleryName",
        Location = "West US",
        PublishingProfile = new AzureNative.Compute.Inputs.GalleryImageVersionPublishingProfileArgs
        {
            ReplicationMode = "Shallow",
            TargetRegions = new[]
            {
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    ExcludeFromLatest = false,
                    Name = "West US",
                    RegionalReplicaCount = 1,
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        SafetyProfile = new AzureNative.Compute.Inputs.GalleryImageVersionSafetyProfileArgs
        {
            AllowDeletionOfReplicatedLocations = false,
        },
        StorageProfile = new AzureNative.Compute.Inputs.GalleryImageVersionStorageProfileArgs
        {
            Source = new AzureNative.Compute.Inputs.GalleryArtifactVersionFullSourceArgs
            {
                Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}",
            },
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
		_, err := compute.NewGalleryImageVersion(ctx, "galleryImageVersion", &compute.GalleryImageVersionArgs{
			GalleryImageName:        pulumi.String("myGalleryImageName"),
			GalleryImageVersionName: pulumi.String("1.0.0"),
			GalleryName:             pulumi.String("myGalleryName"),
			Location:                pulumi.String("West US"),
			PublishingProfile: compute.GalleryImageVersionPublishingProfileResponse{
				ReplicationMode: pulumi.String("Shallow"),
				TargetRegions: compute.TargetRegionArray{
					&compute.TargetRegionArgs{
						ExcludeFromLatest:    pulumi.Bool(false),
						Name:                 pulumi.String("West US"),
						RegionalReplicaCount: pulumi.Int(1),
					},
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SafetyProfile: &compute.GalleryImageVersionSafetyProfileArgs{
				AllowDeletionOfReplicatedLocations: pulumi.Bool(false),
			},
			StorageProfile: compute.GalleryImageVersionStorageProfileResponse{
				Source: &compute.GalleryArtifactVersionFullSourceArgs{
					Id: pulumi.String("/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}"),
				},
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
import com.pulumi.azurenative.compute.GalleryImageVersion;
import com.pulumi.azurenative.compute.GalleryImageVersionArgs;
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
        var galleryImageVersion = new GalleryImageVersion("galleryImageVersion", GalleryImageVersionArgs.builder()        
            .galleryImageName("myGalleryImageName")
            .galleryImageVersionName("1.0.0")
            .galleryName("myGalleryName")
            .location("West US")
            .publishingProfile(Map.ofEntries(
                Map.entry("replicationMode", "Shallow"),
                Map.entry("targetRegions", Map.ofEntries(
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "West US"),
                    Map.entry("regionalReplicaCount", 1)
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .safetyProfile(Map.of("allowDeletionOfReplicatedLocations", false))
            .storageProfile(Map.of("source", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}")))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const galleryImageVersion = new azure_native.compute.GalleryImageVersion("galleryImageVersion", {
    galleryImageName: "myGalleryImageName",
    galleryImageVersionName: "1.0.0",
    galleryName: "myGalleryName",
    location: "West US",
    publishingProfile: {
        replicationMode: "Shallow",
        targetRegions: [{
            excludeFromLatest: false,
            name: "West US",
            regionalReplicaCount: 1,
        }],
    },
    resourceGroupName: "myResourceGroup",
    safetyProfile: {
        allowDeletionOfReplicatedLocations: false,
    },
    storageProfile: {
        source: {
            id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery_image_version = azure_native.compute.GalleryImageVersion("galleryImageVersion",
    gallery_image_name="myGalleryImageName",
    gallery_image_version_name="1.0.0",
    gallery_name="myGalleryName",
    location="West US",
    publishing_profile=azure_native.compute.GalleryImageVersionPublishingProfileResponseArgs(
        replication_mode="Shallow",
        target_regions=[azure_native.compute.TargetRegionArgs(
            exclude_from_latest=False,
            name="West US",
            regional_replica_count=1,
        )],
    ),
    resource_group_name="myResourceGroup",
    safety_profile=azure_native.compute.GalleryImageVersionSafetyProfileArgs(
        allow_deletion_of_replicated_locations=False,
    ),
    storage_profile=azure_native.compute.GalleryImageVersionStorageProfileResponseArgs(
        source=azure_native.compute.GalleryArtifactVersionFullSourceArgs(
            id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}",
        ),
    ))

```

```yaml
resources:
  galleryImageVersion:
    type: azure-native:compute:GalleryImageVersion
    properties:
      galleryImageName: myGalleryImageName
      galleryImageVersionName: 1.0.0
      galleryName: myGalleryName
      location: West US
      publishingProfile:
        replicationMode: Shallow
        targetRegions:
          - excludeFromLatest: false
            name: West US
            regionalReplicaCount: 1
      resourceGroupName: myResourceGroup
      safetyProfile:
        allowDeletionOfReplicatedLocations: false
      storageProfile:
        source:
          id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}

```

{{% /example %}}
{{% example %}}
### Create or update a simple Gallery Image Version using shared image as source.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var galleryImageVersion = new AzureNative.Compute.GalleryImageVersion("galleryImageVersion", new()
    {
        GalleryImageName = "myGalleryImageName",
        GalleryImageVersionName = "1.0.0",
        GalleryName = "myGalleryName",
        Location = "West US",
        PublishingProfile = new AzureNative.Compute.Inputs.GalleryImageVersionPublishingProfileArgs
        {
            TargetRegions = new[]
            {
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    Encryption = new AzureNative.Compute.Inputs.EncryptionImagesArgs
                    {
                        DataDiskImages = new[]
                        {
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                                Lun = 0,
                            },
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                                Lun = 1,
                            },
                        },
                        OsDiskImage = new AzureNative.Compute.Inputs.OSDiskImageEncryptionArgs
                        {
                            DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                        },
                    },
                    ExcludeFromLatest = false,
                    Name = "West US",
                    RegionalReplicaCount = 1,
                },
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    Encryption = new AzureNative.Compute.Inputs.EncryptionImagesArgs
                    {
                        DataDiskImages = new[]
                        {
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                                Lun = 0,
                            },
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                                Lun = 1,
                            },
                        },
                        OsDiskImage = new AzureNative.Compute.Inputs.OSDiskImageEncryptionArgs
                        {
                            DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                        },
                    },
                    ExcludeFromLatest = false,
                    Name = "East US",
                    RegionalReplicaCount = 2,
                    StorageAccountType = "Standard_ZRS",
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        SafetyProfile = new AzureNative.Compute.Inputs.GalleryImageVersionSafetyProfileArgs
        {
            AllowDeletionOfReplicatedLocations = false,
        },
        StorageProfile = new AzureNative.Compute.Inputs.GalleryImageVersionStorageProfileArgs
        {
            Source = new AzureNative.Compute.Inputs.GalleryArtifactVersionFullSourceArgs
            {
                Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/galleries/{galleryName}/images/{imageDefinitionName}/versions/{versionName}",
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
import com.pulumi.azurenative.compute.GalleryImageVersion;
import com.pulumi.azurenative.compute.GalleryImageVersionArgs;
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
        var galleryImageVersion = new GalleryImageVersion("galleryImageVersion", GalleryImageVersionArgs.builder()        
            .galleryImageName("myGalleryImageName")
            .galleryImageVersionName("1.0.0")
            .galleryName("myGalleryName")
            .location("West US")
            .publishingProfile(Map.of("targetRegions",             
                Map.ofEntries(
                    Map.entry("encryption", Map.ofEntries(
                        Map.entry("dataDiskImages",                         
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet"),
                                Map.entry("lun", 0)
                            ),
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet"),
                                Map.entry("lun", 1)
                            )),
                        Map.entry("osDiskImage", Map.of("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet"))
                    )),
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "West US"),
                    Map.entry("regionalReplicaCount", 1)
                ),
                Map.ofEntries(
                    Map.entry("encryption", Map.ofEntries(
                        Map.entry("dataDiskImages",                         
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet"),
                                Map.entry("lun", 0)
                            ),
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet"),
                                Map.entry("lun", 1)
                            )),
                        Map.entry("osDiskImage", Map.of("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet"))
                    )),
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "East US"),
                    Map.entry("regionalReplicaCount", 2),
                    Map.entry("storageAccountType", "Standard_ZRS")
                )))
            .resourceGroupName("myResourceGroup")
            .safetyProfile(Map.of("allowDeletionOfReplicatedLocations", false))
            .storageProfile(Map.of("source", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/galleries/{galleryName}/images/{imageDefinitionName}/versions/{versionName}")))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const galleryImageVersion = new azure_native.compute.GalleryImageVersion("galleryImageVersion", {
    galleryImageName: "myGalleryImageName",
    galleryImageVersionName: "1.0.0",
    galleryName: "myGalleryName",
    location: "West US",
    publishingProfile: {
        targetRegions: [
            {
                encryption: {
                    dataDiskImages: [
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                            lun: 0,
                        },
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                            lun: 1,
                        },
                    ],
                    osDiskImage: {
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                    },
                },
                excludeFromLatest: false,
                name: "West US",
                regionalReplicaCount: 1,
            },
            {
                encryption: {
                    dataDiskImages: [
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                            lun: 0,
                        },
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                            lun: 1,
                        },
                    ],
                    osDiskImage: {
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                    },
                },
                excludeFromLatest: false,
                name: "East US",
                regionalReplicaCount: 2,
                storageAccountType: "Standard_ZRS",
            },
        ],
    },
    resourceGroupName: "myResourceGroup",
    safetyProfile: {
        allowDeletionOfReplicatedLocations: false,
    },
    storageProfile: {
        source: {
            id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/galleries/{galleryName}/images/{imageDefinitionName}/versions/{versionName}",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery_image_version = azure_native.compute.GalleryImageVersion("galleryImageVersion",
    gallery_image_name="myGalleryImageName",
    gallery_image_version_name="1.0.0",
    gallery_name="myGalleryName",
    location="West US",
    publishing_profile=azure_native.compute.GalleryImageVersionPublishingProfileResponseArgs(
        target_regions=[
            {
                "encryption": {
                    "dataDiskImages": [
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                            lun=0,
                        ),
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                            lun=1,
                        ),
                    ],
                    "osDiskImage": azure_native.compute.OSDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                    ),
                },
                "excludeFromLatest": False,
                "name": "West US",
                "regionalReplicaCount": 1,
            },
            {
                "encryption": {
                    "dataDiskImages": [
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                            lun=0,
                        ),
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                            lun=1,
                        ),
                    ],
                    "osDiskImage": azure_native.compute.OSDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                    ),
                },
                "excludeFromLatest": False,
                "name": "East US",
                "regionalReplicaCount": 2,
                "storageAccountType": "Standard_ZRS",
            },
        ],
    ),
    resource_group_name="myResourceGroup",
    safety_profile=azure_native.compute.GalleryImageVersionSafetyProfileArgs(
        allow_deletion_of_replicated_locations=False,
    ),
    storage_profile=azure_native.compute.GalleryImageVersionStorageProfileResponseArgs(
        source=azure_native.compute.GalleryArtifactVersionFullSourceArgs(
            id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/galleries/{galleryName}/images/{imageDefinitionName}/versions/{versionName}",
        ),
    ))

```

```yaml
resources:
  galleryImageVersion:
    type: azure-native:compute:GalleryImageVersion
    properties:
      galleryImageName: myGalleryImageName
      galleryImageVersionName: 1.0.0
      galleryName: myGalleryName
      location: West US
      publishingProfile:
        targetRegions:
          - encryption:
              dataDiskImages:
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet
                  lun: 0
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet
                  lun: 1
              osDiskImage:
                diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet
            excludeFromLatest: false
            name: West US
            regionalReplicaCount: 1
          - encryption:
              dataDiskImages:
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet
                  lun: 0
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet
                  lun: 1
              osDiskImage:
                diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet
            excludeFromLatest: false
            name: East US
            regionalReplicaCount: 2
            storageAccountType: Standard_ZRS
      resourceGroupName: myResourceGroup
      safetyProfile:
        allowDeletionOfReplicatedLocations: false
      storageProfile:
        source:
          id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/galleries/{galleryName}/images/{imageDefinitionName}/versions/{versionName}

```

{{% /example %}}
{{% example %}}
### Create or update a simple Gallery Image Version using vhd as a source.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var galleryImageVersion = new AzureNative.Compute.GalleryImageVersion("galleryImageVersion", new()
    {
        GalleryImageName = "myGalleryImageName",
        GalleryImageVersionName = "1.0.0",
        GalleryName = "myGalleryName",
        Location = "West US",
        PublishingProfile = new AzureNative.Compute.Inputs.GalleryImageVersionPublishingProfileArgs
        {
            TargetRegions = new[]
            {
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    Encryption = new AzureNative.Compute.Inputs.EncryptionImagesArgs
                    {
                        DataDiskImages = new[]
                        {
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherDiskEncryptionSet",
                                Lun = 1,
                            },
                        },
                        OsDiskImage = new AzureNative.Compute.Inputs.OSDiskImageEncryptionArgs
                        {
                            DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myDiskEncryptionSet",
                        },
                    },
                    ExcludeFromLatest = false,
                    Name = "West US",
                    RegionalReplicaCount = 1,
                },
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    ExcludeFromLatest = false,
                    Name = "East US",
                    RegionalReplicaCount = 2,
                    StorageAccountType = "Standard_ZRS",
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        SafetyProfile = new AzureNative.Compute.Inputs.GalleryImageVersionSafetyProfileArgs
        {
            AllowDeletionOfReplicatedLocations = false,
        },
        StorageProfile = new AzureNative.Compute.Inputs.GalleryImageVersionStorageProfileArgs
        {
            DataDiskImages = new[]
            {
                new AzureNative.Compute.Inputs.GalleryDataDiskImageArgs
                {
                    HostCaching = AzureNative.Compute.HostCaching.None,
                    Lun = 1,
                    Source = new AzureNative.Compute.Inputs.GalleryDiskImageSourceArgs
                    {
                        Id = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/{storageAccount}",
                        Uri = "https://gallerysourcencus.blob.core.windows.net/myvhds/Windows-Server-2012-R2-20171216-en.us-128GB.vhd",
                    },
                },
            },
            OsDiskImage = new AzureNative.Compute.Inputs.GalleryOSDiskImageArgs
            {
                HostCaching = AzureNative.Compute.HostCaching.ReadOnly,
                Source = new AzureNative.Compute.Inputs.GalleryDiskImageSourceArgs
                {
                    Id = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/{storageAccount}",
                    Uri = "https://gallerysourcencus.blob.core.windows.net/myvhds/Windows-Server-2012-R2-20171216-en.us-128GB.vhd",
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
import com.pulumi.azurenative.compute.GalleryImageVersion;
import com.pulumi.azurenative.compute.GalleryImageVersionArgs;
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
        var galleryImageVersion = new GalleryImageVersion("galleryImageVersion", GalleryImageVersionArgs.builder()        
            .galleryImageName("myGalleryImageName")
            .galleryImageVersionName("1.0.0")
            .galleryName("myGalleryName")
            .location("West US")
            .publishingProfile(Map.of("targetRegions",             
                Map.ofEntries(
                    Map.entry("encryption", Map.ofEntries(
                        Map.entry("dataDiskImages", Map.ofEntries(
                            Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherDiskEncryptionSet"),
                            Map.entry("lun", 1)
                        )),
                        Map.entry("osDiskImage", Map.of("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myDiskEncryptionSet"))
                    )),
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "West US"),
                    Map.entry("regionalReplicaCount", 1)
                ),
                Map.ofEntries(
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "East US"),
                    Map.entry("regionalReplicaCount", 2),
                    Map.entry("storageAccountType", "Standard_ZRS")
                )))
            .resourceGroupName("myResourceGroup")
            .safetyProfile(Map.of("allowDeletionOfReplicatedLocations", false))
            .storageProfile(Map.ofEntries(
                Map.entry("dataDiskImages", Map.ofEntries(
                    Map.entry("hostCaching", "None"),
                    Map.entry("lun", 1),
                    Map.entry("source", Map.ofEntries(
                        Map.entry("id", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/{storageAccount}"),
                        Map.entry("uri", "https://gallerysourcencus.blob.core.windows.net/myvhds/Windows-Server-2012-R2-20171216-en.us-128GB.vhd")
                    ))
                )),
                Map.entry("osDiskImage", Map.ofEntries(
                    Map.entry("hostCaching", "ReadOnly"),
                    Map.entry("source", Map.ofEntries(
                        Map.entry("id", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/{storageAccount}"),
                        Map.entry("uri", "https://gallerysourcencus.blob.core.windows.net/myvhds/Windows-Server-2012-R2-20171216-en.us-128GB.vhd")
                    ))
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const galleryImageVersion = new azure_native.compute.GalleryImageVersion("galleryImageVersion", {
    galleryImageName: "myGalleryImageName",
    galleryImageVersionName: "1.0.0",
    galleryName: "myGalleryName",
    location: "West US",
    publishingProfile: {
        targetRegions: [
            {
                encryption: {
                    dataDiskImages: [{
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherDiskEncryptionSet",
                        lun: 1,
                    }],
                    osDiskImage: {
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myDiskEncryptionSet",
                    },
                },
                excludeFromLatest: false,
                name: "West US",
                regionalReplicaCount: 1,
            },
            {
                excludeFromLatest: false,
                name: "East US",
                regionalReplicaCount: 2,
                storageAccountType: "Standard_ZRS",
            },
        ],
    },
    resourceGroupName: "myResourceGroup",
    safetyProfile: {
        allowDeletionOfReplicatedLocations: false,
    },
    storageProfile: {
        dataDiskImages: [{
            hostCaching: azure_native.compute.HostCaching.None,
            lun: 1,
            source: {
                id: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/{storageAccount}",
                uri: "https://gallerysourcencus.blob.core.windows.net/myvhds/Windows-Server-2012-R2-20171216-en.us-128GB.vhd",
            },
        }],
        osDiskImage: {
            hostCaching: azure_native.compute.HostCaching.ReadOnly,
            source: {
                id: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/{storageAccount}",
                uri: "https://gallerysourcencus.blob.core.windows.net/myvhds/Windows-Server-2012-R2-20171216-en.us-128GB.vhd",
            },
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery_image_version = azure_native.compute.GalleryImageVersion("galleryImageVersion",
    gallery_image_name="myGalleryImageName",
    gallery_image_version_name="1.0.0",
    gallery_name="myGalleryName",
    location="West US",
    publishing_profile=azure_native.compute.GalleryImageVersionPublishingProfileResponseArgs(
        target_regions=[
            {
                "encryption": {
                    "dataDiskImages": [azure_native.compute.DataDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherDiskEncryptionSet",
                        lun=1,
                    )],
                    "osDiskImage": azure_native.compute.OSDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myDiskEncryptionSet",
                    ),
                },
                "excludeFromLatest": False,
                "name": "West US",
                "regionalReplicaCount": 1,
            },
            azure_native.compute.TargetRegionArgs(
                exclude_from_latest=False,
                name="East US",
                regional_replica_count=2,
                storage_account_type="Standard_ZRS",
            ),
        ],
    ),
    resource_group_name="myResourceGroup",
    safety_profile=azure_native.compute.GalleryImageVersionSafetyProfileArgs(
        allow_deletion_of_replicated_locations=False,
    ),
    storage_profile=azure_native.compute.GalleryImageVersionStorageProfileResponseArgs(
        data_disk_images=[{
            "hostCaching": azure_native.compute.HostCaching.NONE,
            "lun": 1,
            "source": azure_native.compute.GalleryDiskImageSourceArgs(
                id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/{storageAccount}",
                uri="https://gallerysourcencus.blob.core.windows.net/myvhds/Windows-Server-2012-R2-20171216-en.us-128GB.vhd",
            ),
        }],
        os_disk_image={
            "hostCaching": azure_native.compute.HostCaching.READ_ONLY,
            "source": azure_native.compute.GalleryDiskImageSourceArgs(
                id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/{storageAccount}",
                uri="https://gallerysourcencus.blob.core.windows.net/myvhds/Windows-Server-2012-R2-20171216-en.us-128GB.vhd",
            ),
        },
    ))

```

```yaml
resources:
  galleryImageVersion:
    type: azure-native:compute:GalleryImageVersion
    properties:
      galleryImageName: myGalleryImageName
      galleryImageVersionName: 1.0.0
      galleryName: myGalleryName
      location: West US
      publishingProfile:
        targetRegions:
          - encryption:
              dataDiskImages:
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherDiskEncryptionSet
                  lun: 1
              osDiskImage:
                diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myDiskEncryptionSet
            excludeFromLatest: false
            name: West US
            regionalReplicaCount: 1
          - excludeFromLatest: false
            name: East US
            regionalReplicaCount: 2
            storageAccountType: Standard_ZRS
      resourceGroupName: myResourceGroup
      safetyProfile:
        allowDeletionOfReplicatedLocations: false
      storageProfile:
        dataDiskImages:
          - hostCaching: None
            lun: 1
            source:
              id: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/{storageAccount}
              uri: https://gallerysourcencus.blob.core.windows.net/myvhds/Windows-Server-2012-R2-20171216-en.us-128GB.vhd
        osDiskImage:
          hostCaching: ReadOnly
          source:
            id: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/{storageAccount}
            uri: https://gallerysourcencus.blob.core.windows.net/myvhds/Windows-Server-2012-R2-20171216-en.us-128GB.vhd

```

{{% /example %}}
{{% example %}}
### Create or update a simple gallery image version with target extended locations specified.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var galleryImageVersion = new AzureNative.Compute.GalleryImageVersion("galleryImageVersion", new()
    {
        GalleryImageName = "myGalleryImageName",
        GalleryImageVersionName = "1.0.0",
        GalleryName = "myGalleryName",
        Location = "West US",
        PublishingProfile = new AzureNative.Compute.Inputs.GalleryImageVersionPublishingProfileArgs
        {
            TargetRegions = new[]
            {
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    Encryption = new AzureNative.Compute.Inputs.EncryptionImagesArgs
                    {
                        DataDiskImages = new[]
                        {
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                                Lun = 0,
                            },
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                                Lun = 1,
                            },
                        },
                        OsDiskImage = new AzureNative.Compute.Inputs.OSDiskImageEncryptionArgs
                        {
                            DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                        },
                    },
                    ExcludeFromLatest = false,
                    Name = "West US",
                    RegionalReplicaCount = 1,
                },
                new AzureNative.Compute.Inputs.TargetRegionArgs
                {
                    Encryption = new AzureNative.Compute.Inputs.EncryptionImagesArgs
                    {
                        DataDiskImages = new[]
                        {
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                                Lun = 0,
                            },
                            new AzureNative.Compute.Inputs.DataDiskImageEncryptionArgs
                            {
                                DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                                Lun = 1,
                            },
                        },
                        OsDiskImage = new AzureNative.Compute.Inputs.OSDiskImageEncryptionArgs
                        {
                            DiskEncryptionSetId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                        },
                    },
                    ExcludeFromLatest = false,
                    Name = "East US",
                    RegionalReplicaCount = 2,
                    StorageAccountType = "Standard_ZRS",
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        SafetyProfile = new AzureNative.Compute.Inputs.GalleryImageVersionSafetyProfileArgs
        {
            AllowDeletionOfReplicatedLocations = false,
        },
        StorageProfile = new AzureNative.Compute.Inputs.GalleryImageVersionStorageProfileArgs
        {
            Source = new AzureNative.Compute.Inputs.GalleryArtifactVersionFullSourceArgs
            {
                Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}",
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
import com.pulumi.azurenative.compute.GalleryImageVersion;
import com.pulumi.azurenative.compute.GalleryImageVersionArgs;
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
        var galleryImageVersion = new GalleryImageVersion("galleryImageVersion", GalleryImageVersionArgs.builder()        
            .galleryImageName("myGalleryImageName")
            .galleryImageVersionName("1.0.0")
            .galleryName("myGalleryName")
            .location("West US")
            .publishingProfile(Map.of("targetRegions",             
                Map.ofEntries(
                    Map.entry("encryption", Map.ofEntries(
                        Map.entry("dataDiskImages",                         
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet"),
                                Map.entry("lun", 0)
                            ),
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet"),
                                Map.entry("lun", 1)
                            )),
                        Map.entry("osDiskImage", Map.of("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet"))
                    )),
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "West US"),
                    Map.entry("regionalReplicaCount", 1)
                ),
                Map.ofEntries(
                    Map.entry("encryption", Map.ofEntries(
                        Map.entry("dataDiskImages",                         
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet"),
                                Map.entry("lun", 0)
                            ),
                            Map.ofEntries(
                                Map.entry("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet"),
                                Map.entry("lun", 1)
                            )),
                        Map.entry("osDiskImage", Map.of("diskEncryptionSetId", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet"))
                    )),
                    Map.entry("excludeFromLatest", false),
                    Map.entry("name", "East US"),
                    Map.entry("regionalReplicaCount", 2),
                    Map.entry("storageAccountType", "Standard_ZRS")
                )))
            .resourceGroupName("myResourceGroup")
            .safetyProfile(Map.of("allowDeletionOfReplicatedLocations", false))
            .storageProfile(Map.of("source", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}")))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const galleryImageVersion = new azure_native.compute.GalleryImageVersion("galleryImageVersion", {
    galleryImageName: "myGalleryImageName",
    galleryImageVersionName: "1.0.0",
    galleryName: "myGalleryName",
    location: "West US",
    publishingProfile: {
        targetRegions: [
            {
                encryption: {
                    dataDiskImages: [
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                            lun: 0,
                        },
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                            lun: 1,
                        },
                    ],
                    osDiskImage: {
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                    },
                },
                excludeFromLatest: false,
                name: "West US",
                regionalReplicaCount: 1,
            },
            {
                encryption: {
                    dataDiskImages: [
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                            lun: 0,
                        },
                        {
                            diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                            lun: 1,
                        },
                    ],
                    osDiskImage: {
                        diskEncryptionSetId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                    },
                },
                excludeFromLatest: false,
                name: "East US",
                regionalReplicaCount: 2,
                storageAccountType: "Standard_ZRS",
            },
        ],
    },
    resourceGroupName: "myResourceGroup",
    safetyProfile: {
        allowDeletionOfReplicatedLocations: false,
    },
    storageProfile: {
        source: {
            id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery_image_version = azure_native.compute.GalleryImageVersion("galleryImageVersion",
    gallery_image_name="myGalleryImageName",
    gallery_image_version_name="1.0.0",
    gallery_name="myGalleryName",
    location="West US",
    publishing_profile=azure_native.compute.GalleryImageVersionPublishingProfileResponseArgs(
        target_regions=[
            {
                "encryption": {
                    "dataDiskImages": [
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet",
                            lun=0,
                        ),
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                            lun=1,
                        ),
                    ],
                    "osDiskImage": azure_native.compute.OSDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet",
                    ),
                },
                "excludeFromLatest": False,
                "name": "West US",
                "regionalReplicaCount": 1,
            },
            {
                "encryption": {
                    "dataDiskImages": [
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet",
                            lun=0,
                        ),
                        azure_native.compute.DataDiskImageEncryptionArgs(
                            disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                            lun=1,
                        ),
                    ],
                    "osDiskImage": azure_native.compute.OSDiskImageEncryptionArgs(
                        disk_encryption_set_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet",
                    ),
                },
                "excludeFromLatest": False,
                "name": "East US",
                "regionalReplicaCount": 2,
                "storageAccountType": "Standard_ZRS",
            },
        ],
    ),
    resource_group_name="myResourceGroup",
    safety_profile=azure_native.compute.GalleryImageVersionSafetyProfileArgs(
        allow_deletion_of_replicated_locations=False,
    ),
    storage_profile=azure_native.compute.GalleryImageVersionStorageProfileResponseArgs(
        source=azure_native.compute.GalleryArtifactVersionFullSourceArgs(
            id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}",
        ),
    ))

```

```yaml
resources:
  galleryImageVersion:
    type: azure-native:compute:GalleryImageVersion
    properties:
      galleryImageName: myGalleryImageName
      galleryImageVersionName: 1.0.0
      galleryName: myGalleryName
      location: West US
      publishingProfile:
        targetRegions:
          - encryption:
              dataDiskImages:
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherWestUSDiskEncryptionSet
                  lun: 0
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet
                  lun: 1
              osDiskImage:
                diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myWestUSDiskEncryptionSet
            excludeFromLatest: false
            name: West US
            regionalReplicaCount: 1
          - encryption:
              dataDiskImages:
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myOtherEastUSDiskEncryptionSet
                  lun: 0
                - diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet
                  lun: 1
              osDiskImage:
                diskEncryptionSetId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSet/myEastUSDiskEncryptionSet
            excludeFromLatest: false
            name: East US
            regionalReplicaCount: 2
            storageAccountType: Standard_ZRS
      resourceGroupName: myResourceGroup
      safetyProfile:
        allowDeletionOfReplicatedLocations: false
      storageProfile:
        source:
          id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/images/{imageName}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:GalleryImageVersion 1.0.0 /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/galleries/{galleryName}/images/{galleryImageName}/versions/{galleryImageVersionName} 
```
