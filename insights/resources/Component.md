An Application Insights component definition.
API Version: 2020-02-02.
Previous API Version: 2015-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ComponentCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var component = new AzureNative.Insights.Component("component", new()
    {
        ApplicationType = "web",
        FlowType = "Bluefield",
        Kind = "web",
        Location = "South Central US",
        RequestSource = "rest",
        ResourceGroupName = "my-resource-group",
        ResourceName = "my-component",
        WorkspaceResourceId = "/subscriptions/subid/resourcegroups/my-resource-group/providers/microsoft.operationalinsights/workspaces/my-workspace",
    });

});


```

```go
package main

import (
	insights "github.com/pulumi/pulumi-azure-native-sdk/insights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := insights.NewComponent(ctx, "component", &insights.ComponentArgs{
			ApplicationType:     pulumi.String("web"),
			FlowType:            pulumi.String("Bluefield"),
			Kind:                pulumi.String("web"),
			Location:            pulumi.String("South Central US"),
			RequestSource:       pulumi.String("rest"),
			ResourceGroupName:   pulumi.String("my-resource-group"),
			ResourceName:        pulumi.String("my-component"),
			WorkspaceResourceId: pulumi.String("/subscriptions/subid/resourcegroups/my-resource-group/providers/microsoft.operationalinsights/workspaces/my-workspace"),
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
import com.pulumi.azurenative.insights.Component;
import com.pulumi.azurenative.insights.ComponentArgs;
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
        var component = new Component("component", ComponentArgs.builder()        
            .applicationType("web")
            .flowType("Bluefield")
            .kind("web")
            .location("South Central US")
            .requestSource("rest")
            .resourceGroupName("my-resource-group")
            .resourceName("my-component")
            .workspaceResourceId("/subscriptions/subid/resourcegroups/my-resource-group/providers/microsoft.operationalinsights/workspaces/my-workspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const component = new azure_native.insights.Component("component", {
    applicationType: "web",
    flowType: "Bluefield",
    kind: "web",
    location: "South Central US",
    requestSource: "rest",
    resourceGroupName: "my-resource-group",
    resourceName: "my-component",
    workspaceResourceId: "/subscriptions/subid/resourcegroups/my-resource-group/providers/microsoft.operationalinsights/workspaces/my-workspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

component = azure_native.insights.Component("component",
    application_type="web",
    flow_type="Bluefield",
    kind="web",
    location="South Central US",
    request_source="rest",
    resource_group_name="my-resource-group",
    resource_name_="my-component",
    workspace_resource_id="/subscriptions/subid/resourcegroups/my-resource-group/providers/microsoft.operationalinsights/workspaces/my-workspace")

```

```yaml
resources:
  component:
    type: azure-native:insights:Component
    properties:
      applicationType: web
      flowType: Bluefield
      kind: web
      location: South Central US
      requestSource: rest
      resourceGroupName: my-resource-group
      resourceName: my-component
      workspaceResourceId: /subscriptions/subid/resourcegroups/my-resource-group/providers/microsoft.operationalinsights/workspaces/my-workspace

```

{{% /example %}}
{{% example %}}
### ComponentUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var component = new AzureNative.Insights.Component("component", new()
    {
        Kind = "web",
        Location = "South Central US",
        ResourceGroupName = "my-resource-group",
        ResourceName = "my-component",
        Tags = 
        {
            { "ApplicationGatewayType", "Internal-Only" },
            { "BillingEntity", "Self" },
        },
    });

});


```

```go
package main

import (
	insights "github.com/pulumi/pulumi-azure-native-sdk/insights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := insights.NewComponent(ctx, "component", &insights.ComponentArgs{
			Kind:              pulumi.String("web"),
			Location:          pulumi.String("South Central US"),
			ResourceGroupName: pulumi.String("my-resource-group"),
			ResourceName:      pulumi.String("my-component"),
			Tags: pulumi.StringMap{
				"ApplicationGatewayType": pulumi.String("Internal-Only"),
				"BillingEntity":          pulumi.String("Self"),
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
import com.pulumi.azurenative.insights.Component;
import com.pulumi.azurenative.insights.ComponentArgs;
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
        var component = new Component("component", ComponentArgs.builder()        
            .kind("web")
            .location("South Central US")
            .resourceGroupName("my-resource-group")
            .resourceName("my-component")
            .tags(Map.ofEntries(
                Map.entry("ApplicationGatewayType", "Internal-Only"),
                Map.entry("BillingEntity", "Self")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const component = new azure_native.insights.Component("component", {
    kind: "web",
    location: "South Central US",
    resourceGroupName: "my-resource-group",
    resourceName: "my-component",
    tags: {
        ApplicationGatewayType: "Internal-Only",
        BillingEntity: "Self",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

component = azure_native.insights.Component("component",
    kind="web",
    location="South Central US",
    resource_group_name="my-resource-group",
    resource_name_="my-component",
    tags={
        "ApplicationGatewayType": "Internal-Only",
        "BillingEntity": "Self",
    })

```

```yaml
resources:
  component:
    type: azure-native:insights:Component
    properties:
      kind: web
      location: South Central US
      resourceGroupName: my-resource-group
      resourceName: my-component
      tags:
        ApplicationGatewayType: Internal-Only
        BillingEntity: Self

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:Component my-component /subscriptions/subid/resourceGroups/my-resource-group/providers/Microsoft.Insights/components/my-component 
```
