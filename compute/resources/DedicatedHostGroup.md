Specifies information about the dedicated host group that the dedicated hosts should be assigned to. <br><br> Currently, a dedicated host can only be added to a dedicated host group at creation time. An existing dedicated host cannot be added to another dedicated host group.
API Version: 2022-11-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a dedicated host group with Ultra SSD support.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dedicatedHostGroup = new AzureNative.Compute.DedicatedHostGroup("dedicatedHostGroup", new()
    {
        AdditionalCapabilities = new AzureNative.Compute.Inputs.DedicatedHostGroupPropertiesAdditionalCapabilitiesArgs
        {
            UltraSSDEnabled = true,
        },
        HostGroupName = "myDedicatedHostGroup",
        Location = "westus",
        PlatformFaultDomainCount = 3,
        ResourceGroupName = "myResourceGroup",
        SupportAutomaticPlacement = true,
        Tags = 
        {
            { "department", "finance" },
        },
        Zones = new[]
        {
            "1",
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
		_, err := compute.NewDedicatedHostGroup(ctx, "dedicatedHostGroup", &compute.DedicatedHostGroupArgs{
			AdditionalCapabilities: &compute.DedicatedHostGroupPropertiesAdditionalCapabilitiesArgs{
				UltraSSDEnabled: pulumi.Bool(true),
			},
			HostGroupName:             pulumi.String("myDedicatedHostGroup"),
			Location:                  pulumi.String("westus"),
			PlatformFaultDomainCount:  pulumi.Int(3),
			ResourceGroupName:         pulumi.String("myResourceGroup"),
			SupportAutomaticPlacement: pulumi.Bool(true),
			Tags: pulumi.StringMap{
				"department": pulumi.String("finance"),
			},
			Zones: pulumi.StringArray{
				pulumi.String("1"),
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
import com.pulumi.azurenative.compute.DedicatedHostGroup;
import com.pulumi.azurenative.compute.DedicatedHostGroupArgs;
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
        var dedicatedHostGroup = new DedicatedHostGroup("dedicatedHostGroup", DedicatedHostGroupArgs.builder()        
            .additionalCapabilities(Map.of("ultraSSDEnabled", true))
            .hostGroupName("myDedicatedHostGroup")
            .location("westus")
            .platformFaultDomainCount(3)
            .resourceGroupName("myResourceGroup")
            .supportAutomaticPlacement(true)
            .tags(Map.of("department", "finance"))
            .zones("1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dedicatedHostGroup = new azure_native.compute.DedicatedHostGroup("dedicatedHostGroup", {
    additionalCapabilities: {
        ultraSSDEnabled: true,
    },
    hostGroupName: "myDedicatedHostGroup",
    location: "westus",
    platformFaultDomainCount: 3,
    resourceGroupName: "myResourceGroup",
    supportAutomaticPlacement: true,
    tags: {
        department: "finance",
    },
    zones: ["1"],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dedicated_host_group = azure_native.compute.DedicatedHostGroup("dedicatedHostGroup",
    additional_capabilities=azure_native.compute.DedicatedHostGroupPropertiesAdditionalCapabilitiesArgs(
        ultra_ssd_enabled=True,
    ),
    host_group_name="myDedicatedHostGroup",
    location="westus",
    platform_fault_domain_count=3,
    resource_group_name="myResourceGroup",
    support_automatic_placement=True,
    tags={
        "department": "finance",
    },
    zones=["1"])

```

```yaml
resources:
  dedicatedHostGroup:
    type: azure-native:compute:DedicatedHostGroup
    properties:
      additionalCapabilities:
        ultraSSDEnabled: true
      hostGroupName: myDedicatedHostGroup
      location: westus
      platformFaultDomainCount: 3
      resourceGroupName: myResourceGroup
      supportAutomaticPlacement: true
      tags:
        department: finance
      zones:
        - '1'

```

{{% /example %}}
{{% example %}}
### Create or update a dedicated host group.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dedicatedHostGroup = new AzureNative.Compute.DedicatedHostGroup("dedicatedHostGroup", new()
    {
        HostGroupName = "myDedicatedHostGroup",
        Location = "westus",
        PlatformFaultDomainCount = 3,
        ResourceGroupName = "myResourceGroup",
        SupportAutomaticPlacement = true,
        Tags = 
        {
            { "department", "finance" },
        },
        Zones = new[]
        {
            "1",
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
		_, err := compute.NewDedicatedHostGroup(ctx, "dedicatedHostGroup", &compute.DedicatedHostGroupArgs{
			HostGroupName:             pulumi.String("myDedicatedHostGroup"),
			Location:                  pulumi.String("westus"),
			PlatformFaultDomainCount:  pulumi.Int(3),
			ResourceGroupName:         pulumi.String("myResourceGroup"),
			SupportAutomaticPlacement: pulumi.Bool(true),
			Tags: pulumi.StringMap{
				"department": pulumi.String("finance"),
			},
			Zones: pulumi.StringArray{
				pulumi.String("1"),
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
import com.pulumi.azurenative.compute.DedicatedHostGroup;
import com.pulumi.azurenative.compute.DedicatedHostGroupArgs;
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
        var dedicatedHostGroup = new DedicatedHostGroup("dedicatedHostGroup", DedicatedHostGroupArgs.builder()        
            .hostGroupName("myDedicatedHostGroup")
            .location("westus")
            .platformFaultDomainCount(3)
            .resourceGroupName("myResourceGroup")
            .supportAutomaticPlacement(true)
            .tags(Map.of("department", "finance"))
            .zones("1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dedicatedHostGroup = new azure_native.compute.DedicatedHostGroup("dedicatedHostGroup", {
    hostGroupName: "myDedicatedHostGroup",
    location: "westus",
    platformFaultDomainCount: 3,
    resourceGroupName: "myResourceGroup",
    supportAutomaticPlacement: true,
    tags: {
        department: "finance",
    },
    zones: ["1"],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dedicated_host_group = azure_native.compute.DedicatedHostGroup("dedicatedHostGroup",
    host_group_name="myDedicatedHostGroup",
    location="westus",
    platform_fault_domain_count=3,
    resource_group_name="myResourceGroup",
    support_automatic_placement=True,
    tags={
        "department": "finance",
    },
    zones=["1"])

```

```yaml
resources:
  dedicatedHostGroup:
    type: azure-native:compute:DedicatedHostGroup
    properties:
      hostGroupName: myDedicatedHostGroup
      location: westus
      platformFaultDomainCount: 3
      resourceGroupName: myResourceGroup
      supportAutomaticPlacement: true
      tags:
        department: finance
      zones:
        - '1'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:DedicatedHostGroup myDedicatedHostGroup /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/HostGroups/myDedicatedHostGroup 
```
