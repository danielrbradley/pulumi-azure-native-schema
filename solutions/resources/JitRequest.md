Information about JIT request definition.
API Version: 2021-07-01.
Previous API Version: 2019-07-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update jit request
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var jitRequest = new AzureNative.Solutions.JitRequest("jitRequest", new()
    {
        ApplicationResourceId = "/subscriptions/00c76877-e316-48a7-af60-4a09fec9d43f/resourceGroups/52F30DB2/providers/Microsoft.Solutions/applications/7E193158",
        JitAuthorizationPolicies = new[]
        {
            new AzureNative.Solutions.Inputs.JitAuthorizationPoliciesArgs
            {
                PrincipalId = "1db8e132e2934dbcb8e1178a61319491",
                RoleDefinitionId = "ecd05a23-931a-4c38-a52b-ac7c4c583334",
            },
        },
        JitRequestName = "myJitRequest",
        JitSchedulingPolicy = new AzureNative.Solutions.Inputs.JitSchedulingPolicyArgs
        {
            Duration = "PT8H",
            StartTime = "2021-04-22T05:48:30.6661804Z",
            Type = "Once",
        },
        ResourceGroupName = "rg",
    });

});


```

```go
package main

import (
	solutions "github.com/pulumi/pulumi-azure-native-sdk/solutions"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := solutions.NewJitRequest(ctx, "jitRequest", &solutions.JitRequestArgs{
			ApplicationResourceId: pulumi.String("/subscriptions/00c76877-e316-48a7-af60-4a09fec9d43f/resourceGroups/52F30DB2/providers/Microsoft.Solutions/applications/7E193158"),
			JitAuthorizationPolicies: []solutions.JitAuthorizationPoliciesArgs{
				{
					PrincipalId:      pulumi.String("1db8e132e2934dbcb8e1178a61319491"),
					RoleDefinitionId: pulumi.String("ecd05a23-931a-4c38-a52b-ac7c4c583334"),
				},
			},
			JitRequestName: pulumi.String("myJitRequest"),
			JitSchedulingPolicy: &solutions.JitSchedulingPolicyArgs{
				Duration:  pulumi.String("PT8H"),
				StartTime: pulumi.String("2021-04-22T05:48:30.6661804Z"),
				Type:      pulumi.String("Once"),
			},
			ResourceGroupName: pulumi.String("rg"),
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
import com.pulumi.azurenative.solutions.JitRequest;
import com.pulumi.azurenative.solutions.JitRequestArgs;
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
        var jitRequest = new JitRequest("jitRequest", JitRequestArgs.builder()        
            .applicationResourceId("/subscriptions/00c76877-e316-48a7-af60-4a09fec9d43f/resourceGroups/52F30DB2/providers/Microsoft.Solutions/applications/7E193158")
            .jitAuthorizationPolicies(Map.ofEntries(
                Map.entry("principalId", "1db8e132e2934dbcb8e1178a61319491"),
                Map.entry("roleDefinitionId", "ecd05a23-931a-4c38-a52b-ac7c4c583334")
            ))
            .jitRequestName("myJitRequest")
            .jitSchedulingPolicy(Map.ofEntries(
                Map.entry("duration", "PT8H"),
                Map.entry("startTime", "2021-04-22T05:48:30.6661804Z"),
                Map.entry("type", "Once")
            ))
            .resourceGroupName("rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const jitRequest = new azure_native.solutions.JitRequest("jitRequest", {
    applicationResourceId: "/subscriptions/00c76877-e316-48a7-af60-4a09fec9d43f/resourceGroups/52F30DB2/providers/Microsoft.Solutions/applications/7E193158",
    jitAuthorizationPolicies: [{
        principalId: "1db8e132e2934dbcb8e1178a61319491",
        roleDefinitionId: "ecd05a23-931a-4c38-a52b-ac7c4c583334",
    }],
    jitRequestName: "myJitRequest",
    jitSchedulingPolicy: {
        duration: "PT8H",
        startTime: "2021-04-22T05:48:30.6661804Z",
        type: "Once",
    },
    resourceGroupName: "rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

jit_request = azure_native.solutions.JitRequest("jitRequest",
    application_resource_id="/subscriptions/00c76877-e316-48a7-af60-4a09fec9d43f/resourceGroups/52F30DB2/providers/Microsoft.Solutions/applications/7E193158",
    jit_authorization_policies=[azure_native.solutions.JitAuthorizationPoliciesArgs(
        principal_id="1db8e132e2934dbcb8e1178a61319491",
        role_definition_id="ecd05a23-931a-4c38-a52b-ac7c4c583334",
    )],
    jit_request_name="myJitRequest",
    jit_scheduling_policy=azure_native.solutions.JitSchedulingPolicyArgs(
        duration="PT8H",
        start_time="2021-04-22T05:48:30.6661804Z",
        type="Once",
    ),
    resource_group_name="rg")

```

```yaml
resources:
  jitRequest:
    type: azure-native:solutions:JitRequest
    properties:
      applicationResourceId: /subscriptions/00c76877-e316-48a7-af60-4a09fec9d43f/resourceGroups/52F30DB2/providers/Microsoft.Solutions/applications/7E193158
      jitAuthorizationPolicies:
        - principalId: 1db8e132e2934dbcb8e1178a61319491
          roleDefinitionId: ecd05a23-931a-4c38-a52b-ac7c4c583334
      jitRequestName: myJitRequest
      jitSchedulingPolicy:
        duration: PT8H
        startTime: 2021-04-22T05:48:30.6661804Z
        type: Once
      resourceGroupName: rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:solutions:JitRequest myJitRequest /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Solutions/jitRequests/myJitRequest 
```
