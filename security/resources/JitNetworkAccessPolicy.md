
API Version: 2020-01-01.
Previous API Version: 2020-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create JIT network access policy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var jitNetworkAccessPolicy = new AzureNative.Security.JitNetworkAccessPolicy("jitNetworkAccessPolicy", new()
    {
        AscLocation = "westeurope",
        JitNetworkAccessPolicyName = "default",
        Kind = "Basic",
        Requests = new[]
        {
            new AzureNative.Security.Inputs.JitNetworkAccessRequestArgs
            {
                Requestor = "barbara@contoso.com",
                StartTimeUtc = "2018-05-17T08:06:45.5691611Z",
                VirtualMachines = new[]
                {
                    new AzureNative.Security.Inputs.JitNetworkAccessRequestVirtualMachineArgs
                    {
                        Id = "/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg1/providers/Microsoft.Compute/virtualMachines/vm1",
                        Ports = new[]
                        {
                            new AzureNative.Security.Inputs.JitNetworkAccessRequestPortArgs
                            {
                                AllowedSourceAddressPrefix = "192.127.0.2",
                                EndTimeUtc = "2018-05-17T09:06:45.5691611Z",
                                Number = 3389,
                                Status = "Initiated",
                                StatusReason = "UserRequested",
                            },
                        },
                    },
                },
            },
        },
        ResourceGroupName = "myRg1",
        VirtualMachines = new[]
        {
            new AzureNative.Security.Inputs.JitNetworkAccessPolicyVirtualMachineArgs
            {
                Id = "/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg1/providers/Microsoft.Compute/virtualMachines/vm1",
                Ports = new[]
                {
                    new AzureNative.Security.Inputs.JitNetworkAccessPortRuleArgs
                    {
                        AllowedSourceAddressPrefix = "*",
                        MaxRequestAccessDuration = "PT3H",
                        Number = 22,
                        Protocol = "*",
                    },
                    new AzureNative.Security.Inputs.JitNetworkAccessPortRuleArgs
                    {
                        AllowedSourceAddressPrefix = "*",
                        MaxRequestAccessDuration = "PT3H",
                        Number = 3389,
                        Protocol = "*",
                    },
                },
            },
        },
    });

});


```

```go
package main

import (
	security "github.com/pulumi/pulumi-azure-native-sdk/security"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := security.NewJitNetworkAccessPolicy(ctx, "jitNetworkAccessPolicy", &security.JitNetworkAccessPolicyArgs{
			AscLocation:                pulumi.String("westeurope"),
			JitNetworkAccessPolicyName: pulumi.String("default"),
			Kind:                       pulumi.String("Basic"),
			Requests: []security.JitNetworkAccessRequestArgs{
				{
					Requestor:    pulumi.String("barbara@contoso.com"),
					StartTimeUtc: pulumi.String("2018-05-17T08:06:45.5691611Z"),
					VirtualMachines: security.JitNetworkAccessRequestVirtualMachineArray{
						{
							Id: pulumi.String("/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg1/providers/Microsoft.Compute/virtualMachines/vm1"),
							Ports: security.JitNetworkAccessRequestPortArray{
								{
									AllowedSourceAddressPrefix: pulumi.String("192.127.0.2"),
									EndTimeUtc:                 pulumi.String("2018-05-17T09:06:45.5691611Z"),
									Number:                     pulumi.Int(3389),
									Status:                     pulumi.String("Initiated"),
									StatusReason:               pulumi.String("UserRequested"),
								},
							},
						},
					},
				},
			},
			ResourceGroupName: pulumi.String("myRg1"),
			VirtualMachines: []security.JitNetworkAccessPolicyVirtualMachineArgs{
				{
					Id: pulumi.String("/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg1/providers/Microsoft.Compute/virtualMachines/vm1"),
					Ports: security.JitNetworkAccessPortRuleArray{
						{
							AllowedSourceAddressPrefix: pulumi.String("*"),
							MaxRequestAccessDuration:   pulumi.String("PT3H"),
							Number:                     pulumi.Int(22),
							Protocol:                   pulumi.String("*"),
						},
						{
							AllowedSourceAddressPrefix: pulumi.String("*"),
							MaxRequestAccessDuration:   pulumi.String("PT3H"),
							Number:                     pulumi.Int(3389),
							Protocol:                   pulumi.String("*"),
						},
					},
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
import com.pulumi.azurenative.security.JitNetworkAccessPolicy;
import com.pulumi.azurenative.security.JitNetworkAccessPolicyArgs;
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
        var jitNetworkAccessPolicy = new JitNetworkAccessPolicy("jitNetworkAccessPolicy", JitNetworkAccessPolicyArgs.builder()        
            .ascLocation("westeurope")
            .jitNetworkAccessPolicyName("default")
            .kind("Basic")
            .requests(Map.ofEntries(
                Map.entry("requestor", "barbara@contoso.com"),
                Map.entry("startTimeUtc", "2018-05-17T08:06:45.5691611Z"),
                Map.entry("virtualMachines", Map.ofEntries(
                    Map.entry("id", "/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg1/providers/Microsoft.Compute/virtualMachines/vm1"),
                    Map.entry("ports", Map.ofEntries(
                        Map.entry("allowedSourceAddressPrefix", "192.127.0.2"),
                        Map.entry("endTimeUtc", "2018-05-17T09:06:45.5691611Z"),
                        Map.entry("number", 3389),
                        Map.entry("status", "Initiated"),
                        Map.entry("statusReason", "UserRequested")
                    ))
                ))
            ))
            .resourceGroupName("myRg1")
            .virtualMachines(Map.ofEntries(
                Map.entry("id", "/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg1/providers/Microsoft.Compute/virtualMachines/vm1"),
                Map.entry("ports",                 
                    Map.ofEntries(
                        Map.entry("allowedSourceAddressPrefix", "*"),
                        Map.entry("maxRequestAccessDuration", "PT3H"),
                        Map.entry("number", 22),
                        Map.entry("protocol", "*")
                    ),
                    Map.ofEntries(
                        Map.entry("allowedSourceAddressPrefix", "*"),
                        Map.entry("maxRequestAccessDuration", "PT3H"),
                        Map.entry("number", 3389),
                        Map.entry("protocol", "*")
                    ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const jitNetworkAccessPolicy = new azure_native.security.JitNetworkAccessPolicy("jitNetworkAccessPolicy", {
    ascLocation: "westeurope",
    jitNetworkAccessPolicyName: "default",
    kind: "Basic",
    requests: [{
        requestor: "barbara@contoso.com",
        startTimeUtc: "2018-05-17T08:06:45.5691611Z",
        virtualMachines: [{
            id: "/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg1/providers/Microsoft.Compute/virtualMachines/vm1",
            ports: [{
                allowedSourceAddressPrefix: "192.127.0.2",
                endTimeUtc: "2018-05-17T09:06:45.5691611Z",
                number: 3389,
                status: "Initiated",
                statusReason: "UserRequested",
            }],
        }],
    }],
    resourceGroupName: "myRg1",
    virtualMachines: [{
        id: "/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg1/providers/Microsoft.Compute/virtualMachines/vm1",
        ports: [
            {
                allowedSourceAddressPrefix: "*",
                maxRequestAccessDuration: "PT3H",
                number: 22,
                protocol: "*",
            },
            {
                allowedSourceAddressPrefix: "*",
                maxRequestAccessDuration: "PT3H",
                number: 3389,
                protocol: "*",
            },
        ],
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

jit_network_access_policy = azure_native.security.JitNetworkAccessPolicy("jitNetworkAccessPolicy",
    asc_location="westeurope",
    jit_network_access_policy_name="default",
    kind="Basic",
    requests=[{
        "requestor": "barbara@contoso.com",
        "startTimeUtc": "2018-05-17T08:06:45.5691611Z",
        "virtualMachines": [{
            "id": "/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg1/providers/Microsoft.Compute/virtualMachines/vm1",
            "ports": [azure_native.security.JitNetworkAccessRequestPortArgs(
                allowed_source_address_prefix="192.127.0.2",
                end_time_utc="2018-05-17T09:06:45.5691611Z",
                number=3389,
                status="Initiated",
                status_reason="UserRequested",
            )],
        }],
    }],
    resource_group_name="myRg1",
    virtual_machines=[{
        "id": "/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg1/providers/Microsoft.Compute/virtualMachines/vm1",
        "ports": [
            azure_native.security.JitNetworkAccessPortRuleArgs(
                allowed_source_address_prefix="*",
                max_request_access_duration="PT3H",
                number=22,
                protocol="*",
            ),
            azure_native.security.JitNetworkAccessPortRuleArgs(
                allowed_source_address_prefix="*",
                max_request_access_duration="PT3H",
                number=3389,
                protocol="*",
            ),
        ],
    }])

```

```yaml
resources:
  jitNetworkAccessPolicy:
    type: azure-native:security:JitNetworkAccessPolicy
    properties:
      ascLocation: westeurope
      jitNetworkAccessPolicyName: default
      kind: Basic
      requests:
        - requestor: barbara@contoso.com
          startTimeUtc: 2018-05-17T08:06:45.5691611Z
          virtualMachines:
            - id: /subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg1/providers/Microsoft.Compute/virtualMachines/vm1
              ports:
                - allowedSourceAddressPrefix: 192.127.0.2
                  endTimeUtc: 2018-05-17T09:06:45.5691611Z
                  number: 3389
                  status: Initiated
                  statusReason: UserRequested
      resourceGroupName: myRg1
      virtualMachines:
        - id: /subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg1/providers/Microsoft.Compute/virtualMachines/vm1
          ports:
            - allowedSourceAddressPrefix: '*'
              maxRequestAccessDuration: PT3H
              number: 22
              protocol: '*'
            - allowedSourceAddressPrefix: '*'
              maxRequestAccessDuration: PT3H
              number: 3389
              protocol: '*'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:security:JitNetworkAccessPolicy default /subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg1/providers/Microsoft.Security/locations/westeurope/jitNetworkAccessPolicies/default 
```
