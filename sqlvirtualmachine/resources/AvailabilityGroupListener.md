A SQL Server availability group listener.
API Version: 2022-02-01.
Previous API Version: 2017-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates an availability group listener using load balancer. This is used for VMs present in single subnet.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var availabilityGroupListener = new AzureNative.SqlVirtualMachine.AvailabilityGroupListener("availabilityGroupListener", new()
    {
        AvailabilityGroupListenerName = "agl-test",
        AvailabilityGroupName = "ag-test",
        LoadBalancerConfigurations = new[]
        {
            new AzureNative.SqlVirtualMachine.Inputs.LoadBalancerConfigurationArgs
            {
                LoadBalancerResourceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/loadBalancers/lb-test",
                PrivateIpAddress = new AzureNative.SqlVirtualMachine.Inputs.PrivateIPAddressArgs
                {
                    IpAddress = "10.1.0.112",
                    SubnetResourceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default",
                },
                ProbePort = 59983,
                SqlVirtualMachineInstances = new[]
                {
                    "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm2",
                    "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm3",
                },
            },
        },
        Port = 1433,
        ResourceGroupName = "testrg",
        SqlVirtualMachineGroupName = "testvmgroup",
    });

});


```

```go
package main

import (
	sqlvirtualmachine "github.com/pulumi/pulumi-azure-native-sdk/sqlvirtualmachine"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sqlvirtualmachine.NewAvailabilityGroupListener(ctx, "availabilityGroupListener", &sqlvirtualmachine.AvailabilityGroupListenerArgs{
			AvailabilityGroupListenerName: pulumi.String("agl-test"),
			AvailabilityGroupName:         pulumi.String("ag-test"),
			LoadBalancerConfigurations: []sqlvirtualmachine.LoadBalancerConfigurationArgs{
				{
					LoadBalancerResourceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/loadBalancers/lb-test"),
					PrivateIpAddress: {
						IpAddress:        pulumi.String("10.1.0.112"),
						SubnetResourceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default"),
					},
					ProbePort: pulumi.Int(59983),
					SqlVirtualMachineInstances: pulumi.StringArray{
						pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm2"),
						pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm3"),
					},
				},
			},
			Port:                       pulumi.Int(1433),
			ResourceGroupName:          pulumi.String("testrg"),
			SqlVirtualMachineGroupName: pulumi.String("testvmgroup"),
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
import com.pulumi.azurenative.sqlvirtualmachine.AvailabilityGroupListener;
import com.pulumi.azurenative.sqlvirtualmachine.AvailabilityGroupListenerArgs;
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
        var availabilityGroupListener = new AvailabilityGroupListener("availabilityGroupListener", AvailabilityGroupListenerArgs.builder()        
            .availabilityGroupListenerName("agl-test")
            .availabilityGroupName("ag-test")
            .loadBalancerConfigurations(Map.ofEntries(
                Map.entry("loadBalancerResourceId", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/loadBalancers/lb-test"),
                Map.entry("privateIpAddress", Map.ofEntries(
                    Map.entry("ipAddress", "10.1.0.112"),
                    Map.entry("subnetResourceId", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default")
                )),
                Map.entry("probePort", 59983),
                Map.entry("sqlVirtualMachineInstances",                 
                    "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm2",
                    "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm3")
            ))
            .port(1433)
            .resourceGroupName("testrg")
            .sqlVirtualMachineGroupName("testvmgroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const availabilityGroupListener = new azure_native.sqlvirtualmachine.AvailabilityGroupListener("availabilityGroupListener", {
    availabilityGroupListenerName: "agl-test",
    availabilityGroupName: "ag-test",
    loadBalancerConfigurations: [{
        loadBalancerResourceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/loadBalancers/lb-test",
        privateIpAddress: {
            ipAddress: "10.1.0.112",
            subnetResourceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default",
        },
        probePort: 59983,
        sqlVirtualMachineInstances: [
            "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm2",
            "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm3",
        ],
    }],
    port: 1433,
    resourceGroupName: "testrg",
    sqlVirtualMachineGroupName: "testvmgroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

availability_group_listener = azure_native.sqlvirtualmachine.AvailabilityGroupListener("availabilityGroupListener",
    availability_group_listener_name="agl-test",
    availability_group_name="ag-test",
    load_balancer_configurations=[{
        "loadBalancerResourceId": "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/loadBalancers/lb-test",
        "privateIpAddress": azure_native.sqlvirtualmachine.PrivateIPAddressArgs(
            ip_address="10.1.0.112",
            subnet_resource_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default",
        ),
        "probePort": 59983,
        "sqlVirtualMachineInstances": [
            "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm2",
            "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm3",
        ],
    }],
    port=1433,
    resource_group_name="testrg",
    sql_virtual_machine_group_name="testvmgroup")

```

```yaml
resources:
  availabilityGroupListener:
    type: azure-native:sqlvirtualmachine:AvailabilityGroupListener
    properties:
      availabilityGroupListenerName: agl-test
      availabilityGroupName: ag-test
      loadBalancerConfigurations:
        - loadBalancerResourceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/loadBalancers/lb-test
          privateIpAddress:
            ipAddress: 10.1.0.112
            subnetResourceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default
          probePort: 59983
          sqlVirtualMachineInstances:
            - /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm2
            - /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm3
      port: 1433
      resourceGroupName: testrg
      sqlVirtualMachineGroupName: testvmgroup

```

{{% /example %}}
{{% example %}}
### Creates or updates an availability group listener. This is used for VMs present in multi subnet
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var availabilityGroupListener = new AzureNative.SqlVirtualMachine.AvailabilityGroupListener("availabilityGroupListener", new()
    {
        AvailabilityGroupListenerName = "agl-test",
        AvailabilityGroupName = "ag-test",
        MultiSubnetIpConfigurations = new[]
        {
            new AzureNative.SqlVirtualMachine.Inputs.MultiSubnetIpConfigurationArgs
            {
                PrivateIpAddress = new AzureNative.SqlVirtualMachine.Inputs.PrivateIPAddressArgs
                {
                    IpAddress = "10.0.0.112",
                    SubnetResourceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default",
                },
                SqlVirtualMachineInstance = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm2",
            },
            new AzureNative.SqlVirtualMachine.Inputs.MultiSubnetIpConfigurationArgs
            {
                PrivateIpAddress = new AzureNative.SqlVirtualMachine.Inputs.PrivateIPAddressArgs
                {
                    IpAddress = "10.0.1.112",
                    SubnetResourceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/alternate",
                },
                SqlVirtualMachineInstance = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm1",
            },
        },
        Port = 1433,
        ResourceGroupName = "testrg",
        SqlVirtualMachineGroupName = "testvmgroup",
    });

});


```

```go
package main

import (
	sqlvirtualmachine "github.com/pulumi/pulumi-azure-native-sdk/sqlvirtualmachine"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sqlvirtualmachine.NewAvailabilityGroupListener(ctx, "availabilityGroupListener", &sqlvirtualmachine.AvailabilityGroupListenerArgs{
			AvailabilityGroupListenerName: pulumi.String("agl-test"),
			AvailabilityGroupName:         pulumi.String("ag-test"),
			MultiSubnetIpConfigurations: []sqlvirtualmachine.MultiSubnetIpConfigurationArgs{
				{
					PrivateIpAddress: {
						IpAddress:        pulumi.String("10.0.0.112"),
						SubnetResourceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default"),
					},
					SqlVirtualMachineInstance: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm2"),
				},
				{
					PrivateIpAddress: {
						IpAddress:        pulumi.String("10.0.1.112"),
						SubnetResourceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/alternate"),
					},
					SqlVirtualMachineInstance: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm1"),
				},
			},
			Port:                       pulumi.Int(1433),
			ResourceGroupName:          pulumi.String("testrg"),
			SqlVirtualMachineGroupName: pulumi.String("testvmgroup"),
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
import com.pulumi.azurenative.sqlvirtualmachine.AvailabilityGroupListener;
import com.pulumi.azurenative.sqlvirtualmachine.AvailabilityGroupListenerArgs;
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
        var availabilityGroupListener = new AvailabilityGroupListener("availabilityGroupListener", AvailabilityGroupListenerArgs.builder()        
            .availabilityGroupListenerName("agl-test")
            .availabilityGroupName("ag-test")
            .multiSubnetIpConfigurations(            
                Map.ofEntries(
                    Map.entry("privateIpAddress", Map.ofEntries(
                        Map.entry("ipAddress", "10.0.0.112"),
                        Map.entry("subnetResourceId", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default")
                    )),
                    Map.entry("sqlVirtualMachineInstance", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm2")
                ),
                Map.ofEntries(
                    Map.entry("privateIpAddress", Map.ofEntries(
                        Map.entry("ipAddress", "10.0.1.112"),
                        Map.entry("subnetResourceId", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/alternate")
                    )),
                    Map.entry("sqlVirtualMachineInstance", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm1")
                ))
            .port(1433)
            .resourceGroupName("testrg")
            .sqlVirtualMachineGroupName("testvmgroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const availabilityGroupListener = new azure_native.sqlvirtualmachine.AvailabilityGroupListener("availabilityGroupListener", {
    availabilityGroupListenerName: "agl-test",
    availabilityGroupName: "ag-test",
    multiSubnetIpConfigurations: [
        {
            privateIpAddress: {
                ipAddress: "10.0.0.112",
                subnetResourceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default",
            },
            sqlVirtualMachineInstance: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm2",
        },
        {
            privateIpAddress: {
                ipAddress: "10.0.1.112",
                subnetResourceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/alternate",
            },
            sqlVirtualMachineInstance: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm1",
        },
    ],
    port: 1433,
    resourceGroupName: "testrg",
    sqlVirtualMachineGroupName: "testvmgroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

availability_group_listener = azure_native.sqlvirtualmachine.AvailabilityGroupListener("availabilityGroupListener",
    availability_group_listener_name="agl-test",
    availability_group_name="ag-test",
    multi_subnet_ip_configurations=[
        {
            "privateIpAddress": azure_native.sqlvirtualmachine.PrivateIPAddressArgs(
                ip_address="10.0.0.112",
                subnet_resource_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default",
            ),
            "sqlVirtualMachineInstance": "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm2",
        },
        {
            "privateIpAddress": azure_native.sqlvirtualmachine.PrivateIPAddressArgs(
                ip_address="10.0.1.112",
                subnet_resource_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/alternate",
            ),
            "sqlVirtualMachineInstance": "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm1",
        },
    ],
    port=1433,
    resource_group_name="testrg",
    sql_virtual_machine_group_name="testvmgroup")

```

```yaml
resources:
  availabilityGroupListener:
    type: azure-native:sqlvirtualmachine:AvailabilityGroupListener
    properties:
      availabilityGroupListenerName: agl-test
      availabilityGroupName: ag-test
      multiSubnetIpConfigurations:
        - privateIpAddress:
            ipAddress: 10.0.0.112
            subnetResourceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default
          sqlVirtualMachineInstance: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm2
        - privateIpAddress:
            ipAddress: 10.0.1.112
            subnetResourceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/alternate
          sqlVirtualMachineInstance: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachines/testvm1
      port: 1433
      resourceGroupName: testrg
      sqlVirtualMachineGroupName: testvmgroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sqlvirtualmachine:AvailabilityGroupListener agl-test /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.SqlVirtualMachine/sqlVirtualMachineGroups/testvmgroup/availabilityGroupListeners/agl-test 
```
