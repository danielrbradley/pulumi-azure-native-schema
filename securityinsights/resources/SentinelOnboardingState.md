Sentinel onboarding state
API Version: 2023-02-01.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Sentinel onboarding state
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sentinelOnboardingState = new AzureNative.SecurityInsights.SentinelOnboardingState("sentinelOnboardingState", new()
    {
        CustomerManagedKey = false,
        ResourceGroupName = "myRg",
        SentinelOnboardingStateName = "default",
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	securityinsights "github.com/pulumi/pulumi-azure-native-sdk/securityinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := securityinsights.NewSentinelOnboardingState(ctx, "sentinelOnboardingState", &securityinsights.SentinelOnboardingStateArgs{
			CustomerManagedKey:          pulumi.Bool(false),
			ResourceGroupName:           pulumi.String("myRg"),
			SentinelOnboardingStateName: pulumi.String("default"),
			WorkspaceName:               pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.SentinelOnboardingState;
import com.pulumi.azurenative.securityinsights.SentinelOnboardingStateArgs;
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
        var sentinelOnboardingState = new SentinelOnboardingState("sentinelOnboardingState", SentinelOnboardingStateArgs.builder()        
            .customerManagedKey(false)
            .resourceGroupName("myRg")
            .sentinelOnboardingStateName("default")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sentinelOnboardingState = new azure_native.securityinsights.SentinelOnboardingState("sentinelOnboardingState", {
    customerManagedKey: false,
    resourceGroupName: "myRg",
    sentinelOnboardingStateName: "default",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sentinel_onboarding_state = azure_native.securityinsights.SentinelOnboardingState("sentinelOnboardingState",
    customer_managed_key=False,
    resource_group_name="myRg",
    sentinel_onboarding_state_name="default",
    workspace_name="myWorkspace")

```

```yaml
resources:
  sentinelOnboardingState:
    type: azure-native:securityinsights:SentinelOnboardingState
    properties:
      customerManagedKey: false
      resourceGroupName: myRg
      sentinelOnboardingStateName: default
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:SentinelOnboardingState default /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/onboardingStates/default 
```
