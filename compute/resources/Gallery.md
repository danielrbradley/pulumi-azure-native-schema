Specifies information about the Shared Image Gallery that you want to create or update.
API Version: 2022-03-03.
Previous API Version: 2020-09-30. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a community gallery.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gallery = new AzureNative.Compute.Gallery("gallery", new()
    {
        Description = "This is the gallery description.",
        GalleryName = "myGalleryName",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        SharingProfile = new AzureNative.Compute.Inputs.SharingProfileArgs
        {
            CommunityGalleryInfo = new AzureNative.Compute.Inputs.CommunityGalleryInfoArgs
            {
                Eula = "eula",
                PublicNamePrefix = "PirPublic",
                PublisherContact = "pir@microsoft.com",
                PublisherUri = "uri",
            },
            Permissions = "Community",
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
		_, err := compute.NewGallery(ctx, "gallery", &compute.GalleryArgs{
			Description:       pulumi.String("This is the gallery description."),
			GalleryName:       pulumi.String("myGalleryName"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SharingProfile: compute.SharingProfileResponse{
				CommunityGalleryInfo: &compute.CommunityGalleryInfoArgs{
					Eula:             pulumi.String("eula"),
					PublicNamePrefix: pulumi.String("PirPublic"),
					PublisherContact: pulumi.String("pir@microsoft.com"),
					PublisherUri:     pulumi.String("uri"),
				},
				Permissions: pulumi.String("Community"),
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
import com.pulumi.azurenative.compute.Gallery;
import com.pulumi.azurenative.compute.GalleryArgs;
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
        var gallery = new Gallery("gallery", GalleryArgs.builder()        
            .description("This is the gallery description.")
            .galleryName("myGalleryName")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .sharingProfile(Map.ofEntries(
                Map.entry("communityGalleryInfo", Map.ofEntries(
                    Map.entry("eula", "eula"),
                    Map.entry("publicNamePrefix", "PirPublic"),
                    Map.entry("publisherContact", "pir@microsoft.com"),
                    Map.entry("publisherUri", "uri")
                )),
                Map.entry("permissions", "Community")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gallery = new azure_native.compute.Gallery("gallery", {
    description: "This is the gallery description.",
    galleryName: "myGalleryName",
    location: "West US",
    resourceGroupName: "myResourceGroup",
    sharingProfile: {
        communityGalleryInfo: {
            eula: "eula",
            publicNamePrefix: "PirPublic",
            publisherContact: "pir@microsoft.com",
            publisherUri: "uri",
        },
        permissions: "Community",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery = azure_native.compute.Gallery("gallery",
    description="This is the gallery description.",
    gallery_name="myGalleryName",
    location="West US",
    resource_group_name="myResourceGroup",
    sharing_profile=azure_native.compute.SharingProfileResponseArgs(
        community_gallery_info=azure_native.compute.CommunityGalleryInfoArgs(
            eula="eula",
            public_name_prefix="PirPublic",
            publisher_contact="pir@microsoft.com",
            publisher_uri="uri",
        ),
        permissions="Community",
    ))

```

```yaml
resources:
  gallery:
    type: azure-native:compute:Gallery
    properties:
      description: This is the gallery description.
      galleryName: myGalleryName
      location: West US
      resourceGroupName: myResourceGroup
      sharingProfile:
        communityGalleryInfo:
          eula: eula
          publicNamePrefix: PirPublic
          publisherContact: pir@microsoft.com
          publisherUri: uri
        permissions: Community

```

{{% /example %}}
{{% example %}}
### Create or update a simple gallery with sharing profile.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gallery = new AzureNative.Compute.Gallery("gallery", new()
    {
        Description = "This is the gallery description.",
        GalleryName = "myGalleryName",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        SharingProfile = new AzureNative.Compute.Inputs.SharingProfileArgs
        {
            Permissions = "Groups",
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
		_, err := compute.NewGallery(ctx, "gallery", &compute.GalleryArgs{
			Description:       pulumi.String("This is the gallery description."),
			GalleryName:       pulumi.String("myGalleryName"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SharingProfile: &compute.SharingProfileArgs{
				Permissions: pulumi.String("Groups"),
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
import com.pulumi.azurenative.compute.Gallery;
import com.pulumi.azurenative.compute.GalleryArgs;
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
        var gallery = new Gallery("gallery", GalleryArgs.builder()        
            .description("This is the gallery description.")
            .galleryName("myGalleryName")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .sharingProfile(Map.of("permissions", "Groups"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gallery = new azure_native.compute.Gallery("gallery", {
    description: "This is the gallery description.",
    galleryName: "myGalleryName",
    location: "West US",
    resourceGroupName: "myResourceGroup",
    sharingProfile: {
        permissions: "Groups",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery = azure_native.compute.Gallery("gallery",
    description="This is the gallery description.",
    gallery_name="myGalleryName",
    location="West US",
    resource_group_name="myResourceGroup",
    sharing_profile=azure_native.compute.SharingProfileArgs(
        permissions="Groups",
    ))

```

```yaml
resources:
  gallery:
    type: azure-native:compute:Gallery
    properties:
      description: This is the gallery description.
      galleryName: myGalleryName
      location: West US
      resourceGroupName: myResourceGroup
      sharingProfile:
        permissions: Groups

```

{{% /example %}}
{{% example %}}
### Create or update a simple gallery with soft deletion enabled.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gallery = new AzureNative.Compute.Gallery("gallery", new()
    {
        Description = "This is the gallery description.",
        GalleryName = "myGalleryName",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        SoftDeletePolicy = new AzureNative.Compute.Inputs.SoftDeletePolicyArgs
        {
            IsSoftDeleteEnabled = true,
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
		_, err := compute.NewGallery(ctx, "gallery", &compute.GalleryArgs{
			Description:       pulumi.String("This is the gallery description."),
			GalleryName:       pulumi.String("myGalleryName"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SoftDeletePolicy: &compute.SoftDeletePolicyArgs{
				IsSoftDeleteEnabled: pulumi.Bool(true),
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
import com.pulumi.azurenative.compute.Gallery;
import com.pulumi.azurenative.compute.GalleryArgs;
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
        var gallery = new Gallery("gallery", GalleryArgs.builder()        
            .description("This is the gallery description.")
            .galleryName("myGalleryName")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .softDeletePolicy(Map.of("isSoftDeleteEnabled", true))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gallery = new azure_native.compute.Gallery("gallery", {
    description: "This is the gallery description.",
    galleryName: "myGalleryName",
    location: "West US",
    resourceGroupName: "myResourceGroup",
    softDeletePolicy: {
        isSoftDeleteEnabled: true,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery = azure_native.compute.Gallery("gallery",
    description="This is the gallery description.",
    gallery_name="myGalleryName",
    location="West US",
    resource_group_name="myResourceGroup",
    soft_delete_policy=azure_native.compute.SoftDeletePolicyArgs(
        is_soft_delete_enabled=True,
    ))

```

```yaml
resources:
  gallery:
    type: azure-native:compute:Gallery
    properties:
      description: This is the gallery description.
      galleryName: myGalleryName
      location: West US
      resourceGroupName: myResourceGroup
      softDeletePolicy:
        isSoftDeleteEnabled: true

```

{{% /example %}}
{{% example %}}
### Create or update a simple gallery.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gallery = new AzureNative.Compute.Gallery("gallery", new()
    {
        Description = "This is the gallery description.",
        GalleryName = "myGalleryName",
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
		_, err := compute.NewGallery(ctx, "gallery", &compute.GalleryArgs{
			Description:       pulumi.String("This is the gallery description."),
			GalleryName:       pulumi.String("myGalleryName"),
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
import com.pulumi.azurenative.compute.Gallery;
import com.pulumi.azurenative.compute.GalleryArgs;
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
        var gallery = new Gallery("gallery", GalleryArgs.builder()        
            .description("This is the gallery description.")
            .galleryName("myGalleryName")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gallery = new azure_native.compute.Gallery("gallery", {
    description: "This is the gallery description.",
    galleryName: "myGalleryName",
    location: "West US",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery = azure_native.compute.Gallery("gallery",
    description="This is the gallery description.",
    gallery_name="myGalleryName",
    location="West US",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  gallery:
    type: azure-native:compute:Gallery
    properties:
      description: This is the gallery description.
      galleryName: myGalleryName
      location: West US
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:Gallery myGalleryName /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/galleries/{galleryName} 
```
