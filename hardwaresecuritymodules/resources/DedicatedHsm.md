Resource information with extended details.
API Version: 2021-11-30.
Previous API Version: 2018-10-31-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a new or update an existing dedicated HSM
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dedicatedHsm = new AzureNative.HardwareSecurityModules.DedicatedHsm("dedicatedHsm", new()
    {
        Location = "westus",
        Name = "hsm1",
        NetworkProfile = new AzureNative.HardwareSecurityModules.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.HardwareSecurityModules.Inputs.NetworkInterfaceArgs
                {
                    PrivateIpAddress = "1.0.0.1",
                },
            },
            Subnet = new AzureNative.HardwareSecurityModules.Inputs.ApiEntityReferenceArgs
            {
                Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01",
            },
        },
        ResourceGroupName = "hsm-group",
        Sku = new AzureNative.HardwareSecurityModules.Inputs.SkuArgs
        {
            Name = "SafeNet Luna Network HSM A790",
        },
        StampId = "stamp01",
        Tags = 
        {
            { "Dept", "hsm" },
            { "Environment", "dogfood" },
        },
    });

});


```

```go
package main

import (
	hardwaresecuritymodules "github.com/pulumi/pulumi-azure-native-sdk/hardwaresecuritymodules"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hardwaresecuritymodules.NewDedicatedHsm(ctx, "dedicatedHsm", &hardwaresecuritymodules.DedicatedHsmArgs{
			Location: pulumi.String("westus"),
			Name:     pulumi.String("hsm1"),
			NetworkProfile: hardwaresecuritymodules.NetworkProfileResponse{
				NetworkInterfaces: hardwaresecuritymodules.NetworkInterfaceArray{
					&hardwaresecuritymodules.NetworkInterfaceArgs{
						PrivateIpAddress: pulumi.String("1.0.0.1"),
					},
				},
				Subnet: &hardwaresecuritymodules.ApiEntityReferenceArgs{
					Id: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01"),
				},
			},
			ResourceGroupName: pulumi.String("hsm-group"),
			Sku: &hardwaresecuritymodules.SkuArgs{
				Name: pulumi.String("SafeNet Luna Network HSM A790"),
			},
			StampId: pulumi.String("stamp01"),
			Tags: pulumi.StringMap{
				"Dept":        pulumi.String("hsm"),
				"Environment": pulumi.String("dogfood"),
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
import com.pulumi.azurenative.hardwaresecuritymodules.DedicatedHsm;
import com.pulumi.azurenative.hardwaresecuritymodules.DedicatedHsmArgs;
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
        var dedicatedHsm = new DedicatedHsm("dedicatedHsm", DedicatedHsmArgs.builder()        
            .location("westus")
            .name("hsm1")
            .networkProfile(Map.ofEntries(
                Map.entry("networkInterfaces", Map.of("privateIpAddress", "1.0.0.1")),
                Map.entry("subnet", Map.of("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01"))
            ))
            .resourceGroupName("hsm-group")
            .sku(Map.of("name", "SafeNet Luna Network HSM A790"))
            .stampId("stamp01")
            .tags(Map.ofEntries(
                Map.entry("Dept", "hsm"),
                Map.entry("Environment", "dogfood")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dedicatedHsm = new azure_native.hardwaresecuritymodules.DedicatedHsm("dedicatedHsm", {
    location: "westus",
    name: "hsm1",
    networkProfile: {
        networkInterfaces: [{
            privateIpAddress: "1.0.0.1",
        }],
        subnet: {
            id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01",
        },
    },
    resourceGroupName: "hsm-group",
    sku: {
        name: "SafeNet Luna Network HSM A790",
    },
    stampId: "stamp01",
    tags: {
        Dept: "hsm",
        Environment: "dogfood",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dedicated_hsm = azure_native.hardwaresecuritymodules.DedicatedHsm("dedicatedHsm",
    location="westus",
    name="hsm1",
    network_profile=azure_native.hardwaresecuritymodules.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.hardwaresecuritymodules.NetworkInterfaceArgs(
            private_ip_address="1.0.0.1",
        )],
        subnet=azure_native.hardwaresecuritymodules.ApiEntityReferenceArgs(
            id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01",
        ),
    ),
    resource_group_name="hsm-group",
    sku=azure_native.hardwaresecuritymodules.SkuArgs(
        name="SafeNet Luna Network HSM A790",
    ),
    stamp_id="stamp01",
    tags={
        "Dept": "hsm",
        "Environment": "dogfood",
    })

```

```yaml
resources:
  dedicatedHsm:
    type: azure-native:hardwaresecuritymodules:DedicatedHsm
    properties:
      location: westus
      name: hsm1
      networkProfile:
        networkInterfaces:
          - privateIpAddress: 1.0.0.1
        subnet:
          id: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01
      resourceGroupName: hsm-group
      sku:
        name: SafeNet Luna Network HSM A790
      stampId: stamp01
      tags:
        Dept: hsm
        Environment: dogfood

```

{{% /example %}}
{{% example %}}
### Create a new or update an existing payment HSM
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dedicatedHsm = new AzureNative.HardwareSecurityModules.DedicatedHsm("dedicatedHsm", new()
    {
        Location = "westus",
        Name = "hsm1",
        NetworkProfile = new AzureNative.HardwareSecurityModules.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.HardwareSecurityModules.Inputs.NetworkInterfaceArgs
                {
                    PrivateIpAddress = "1.0.0.1",
                },
            },
            Subnet = new AzureNative.HardwareSecurityModules.Inputs.ApiEntityReferenceArgs
            {
                Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01",
            },
        },
        ResourceGroupName = "hsm-group",
        Sku = new AzureNative.HardwareSecurityModules.Inputs.SkuArgs
        {
            Name = "payShield10K_LMK1_CPS60",
        },
        StampId = "stamp01",
        Tags = 
        {
            { "Dept", "hsm" },
            { "Environment", "dogfood" },
        },
    });

});


```

```go
package main

import (
	hardwaresecuritymodules "github.com/pulumi/pulumi-azure-native-sdk/hardwaresecuritymodules"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hardwaresecuritymodules.NewDedicatedHsm(ctx, "dedicatedHsm", &hardwaresecuritymodules.DedicatedHsmArgs{
			Location: pulumi.String("westus"),
			Name:     pulumi.String("hsm1"),
			NetworkProfile: hardwaresecuritymodules.NetworkProfileResponse{
				NetworkInterfaces: hardwaresecuritymodules.NetworkInterfaceArray{
					&hardwaresecuritymodules.NetworkInterfaceArgs{
						PrivateIpAddress: pulumi.String("1.0.0.1"),
					},
				},
				Subnet: &hardwaresecuritymodules.ApiEntityReferenceArgs{
					Id: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01"),
				},
			},
			ResourceGroupName: pulumi.String("hsm-group"),
			Sku: &hardwaresecuritymodules.SkuArgs{
				Name: pulumi.String("payShield10K_LMK1_CPS60"),
			},
			StampId: pulumi.String("stamp01"),
			Tags: pulumi.StringMap{
				"Dept":        pulumi.String("hsm"),
				"Environment": pulumi.String("dogfood"),
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
import com.pulumi.azurenative.hardwaresecuritymodules.DedicatedHsm;
import com.pulumi.azurenative.hardwaresecuritymodules.DedicatedHsmArgs;
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
        var dedicatedHsm = new DedicatedHsm("dedicatedHsm", DedicatedHsmArgs.builder()        
            .location("westus")
            .name("hsm1")
            .networkProfile(Map.ofEntries(
                Map.entry("networkInterfaces", Map.of("privateIpAddress", "1.0.0.1")),
                Map.entry("subnet", Map.of("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01"))
            ))
            .resourceGroupName("hsm-group")
            .sku(Map.of("name", "payShield10K_LMK1_CPS60"))
            .stampId("stamp01")
            .tags(Map.ofEntries(
                Map.entry("Dept", "hsm"),
                Map.entry("Environment", "dogfood")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dedicatedHsm = new azure_native.hardwaresecuritymodules.DedicatedHsm("dedicatedHsm", {
    location: "westus",
    name: "hsm1",
    networkProfile: {
        networkInterfaces: [{
            privateIpAddress: "1.0.0.1",
        }],
        subnet: {
            id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01",
        },
    },
    resourceGroupName: "hsm-group",
    sku: {
        name: "payShield10K_LMK1_CPS60",
    },
    stampId: "stamp01",
    tags: {
        Dept: "hsm",
        Environment: "dogfood",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dedicated_hsm = azure_native.hardwaresecuritymodules.DedicatedHsm("dedicatedHsm",
    location="westus",
    name="hsm1",
    network_profile=azure_native.hardwaresecuritymodules.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.hardwaresecuritymodules.NetworkInterfaceArgs(
            private_ip_address="1.0.0.1",
        )],
        subnet=azure_native.hardwaresecuritymodules.ApiEntityReferenceArgs(
            id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01",
        ),
    ),
    resource_group_name="hsm-group",
    sku=azure_native.hardwaresecuritymodules.SkuArgs(
        name="payShield10K_LMK1_CPS60",
    ),
    stamp_id="stamp01",
    tags={
        "Dept": "hsm",
        "Environment": "dogfood",
    })

```

```yaml
resources:
  dedicatedHsm:
    type: azure-native:hardwaresecuritymodules:DedicatedHsm
    properties:
      location: westus
      name: hsm1
      networkProfile:
        networkInterfaces:
          - privateIpAddress: 1.0.0.1
        subnet:
          id: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01
      resourceGroupName: hsm-group
      sku:
        name: payShield10K_LMK1_CPS60
      stampId: stamp01
      tags:
        Dept: hsm
        Environment: dogfood

```

{{% /example %}}
{{% example %}}
### Create a new or update an existing payment HSM with management profile
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dedicatedHsm = new AzureNative.HardwareSecurityModules.DedicatedHsm("dedicatedHsm", new()
    {
        Location = "westus",
        ManagementNetworkProfile = new AzureNative.HardwareSecurityModules.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.HardwareSecurityModules.Inputs.NetworkInterfaceArgs
                {
                    PrivateIpAddress = "1.0.0.2",
                },
            },
            Subnet = new AzureNative.HardwareSecurityModules.Inputs.ApiEntityReferenceArgs
            {
                Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01",
            },
        },
        Name = "hsm1",
        NetworkProfile = new AzureNative.HardwareSecurityModules.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.HardwareSecurityModules.Inputs.NetworkInterfaceArgs
                {
                    PrivateIpAddress = "1.0.0.1",
                },
            },
            Subnet = new AzureNative.HardwareSecurityModules.Inputs.ApiEntityReferenceArgs
            {
                Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01",
            },
        },
        ResourceGroupName = "hsm-group",
        Sku = new AzureNative.HardwareSecurityModules.Inputs.SkuArgs
        {
            Name = "payShield10K_LMK1_CPS60",
        },
        StampId = "stamp01",
        Tags = 
        {
            { "Dept", "hsm" },
            { "Environment", "dogfood" },
        },
    });

});


```

```go
package main

import (
	hardwaresecuritymodules "github.com/pulumi/pulumi-azure-native-sdk/hardwaresecuritymodules"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hardwaresecuritymodules.NewDedicatedHsm(ctx, "dedicatedHsm", &hardwaresecuritymodules.DedicatedHsmArgs{
			Location: pulumi.String("westus"),
			ManagementNetworkProfile: hardwaresecuritymodules.NetworkProfileResponse{
				NetworkInterfaces: hardwaresecuritymodules.NetworkInterfaceArray{
					&hardwaresecuritymodules.NetworkInterfaceArgs{
						PrivateIpAddress: pulumi.String("1.0.0.2"),
					},
				},
				Subnet: &hardwaresecuritymodules.ApiEntityReferenceArgs{
					Id: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01"),
				},
			},
			Name: pulumi.String("hsm1"),
			NetworkProfile: hardwaresecuritymodules.NetworkProfileResponse{
				NetworkInterfaces: hardwaresecuritymodules.NetworkInterfaceArray{
					&hardwaresecuritymodules.NetworkInterfaceArgs{
						PrivateIpAddress: pulumi.String("1.0.0.1"),
					},
				},
				Subnet: &hardwaresecuritymodules.ApiEntityReferenceArgs{
					Id: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01"),
				},
			},
			ResourceGroupName: pulumi.String("hsm-group"),
			Sku: &hardwaresecuritymodules.SkuArgs{
				Name: pulumi.String("payShield10K_LMK1_CPS60"),
			},
			StampId: pulumi.String("stamp01"),
			Tags: pulumi.StringMap{
				"Dept":        pulumi.String("hsm"),
				"Environment": pulumi.String("dogfood"),
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
import com.pulumi.azurenative.hardwaresecuritymodules.DedicatedHsm;
import com.pulumi.azurenative.hardwaresecuritymodules.DedicatedHsmArgs;
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
        var dedicatedHsm = new DedicatedHsm("dedicatedHsm", DedicatedHsmArgs.builder()        
            .location("westus")
            .managementNetworkProfile(Map.ofEntries(
                Map.entry("networkInterfaces", Map.of("privateIpAddress", "1.0.0.2")),
                Map.entry("subnet", Map.of("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01"))
            ))
            .name("hsm1")
            .networkProfile(Map.ofEntries(
                Map.entry("networkInterfaces", Map.of("privateIpAddress", "1.0.0.1")),
                Map.entry("subnet", Map.of("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01"))
            ))
            .resourceGroupName("hsm-group")
            .sku(Map.of("name", "payShield10K_LMK1_CPS60"))
            .stampId("stamp01")
            .tags(Map.ofEntries(
                Map.entry("Dept", "hsm"),
                Map.entry("Environment", "dogfood")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dedicatedHsm = new azure_native.hardwaresecuritymodules.DedicatedHsm("dedicatedHsm", {
    location: "westus",
    managementNetworkProfile: {
        networkInterfaces: [{
            privateIpAddress: "1.0.0.2",
        }],
        subnet: {
            id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01",
        },
    },
    name: "hsm1",
    networkProfile: {
        networkInterfaces: [{
            privateIpAddress: "1.0.0.1",
        }],
        subnet: {
            id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01",
        },
    },
    resourceGroupName: "hsm-group",
    sku: {
        name: "payShield10K_LMK1_CPS60",
    },
    stampId: "stamp01",
    tags: {
        Dept: "hsm",
        Environment: "dogfood",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dedicated_hsm = azure_native.hardwaresecuritymodules.DedicatedHsm("dedicatedHsm",
    location="westus",
    management_network_profile=azure_native.hardwaresecuritymodules.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.hardwaresecuritymodules.NetworkInterfaceArgs(
            private_ip_address="1.0.0.2",
        )],
        subnet=azure_native.hardwaresecuritymodules.ApiEntityReferenceArgs(
            id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01",
        ),
    ),
    name="hsm1",
    network_profile=azure_native.hardwaresecuritymodules.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.hardwaresecuritymodules.NetworkInterfaceArgs(
            private_ip_address="1.0.0.1",
        )],
        subnet=azure_native.hardwaresecuritymodules.ApiEntityReferenceArgs(
            id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01",
        ),
    ),
    resource_group_name="hsm-group",
    sku=azure_native.hardwaresecuritymodules.SkuArgs(
        name="payShield10K_LMK1_CPS60",
    ),
    stamp_id="stamp01",
    tags={
        "Dept": "hsm",
        "Environment": "dogfood",
    })

```

```yaml
resources:
  dedicatedHsm:
    type: azure-native:hardwaresecuritymodules:DedicatedHsm
    properties:
      location: westus
      managementNetworkProfile:
        networkInterfaces:
          - privateIpAddress: 1.0.0.2
        subnet:
          id: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01
      name: hsm1
      networkProfile:
        networkInterfaces:
          - privateIpAddress: 1.0.0.1
        subnet:
          id: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.Network/virtualNetworks/stamp01/subnets/stamp01
      resourceGroupName: hsm-group
      sku:
        name: payShield10K_LMK1_CPS60
      stampId: stamp01
      tags:
        Dept: hsm
        Environment: dogfood

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hardwaresecuritymodules:DedicatedHsm hsm1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/hsm-group/providers/Microsoft.HardwareSecurityModules/dedicatedHSMs/hsm1 
```
