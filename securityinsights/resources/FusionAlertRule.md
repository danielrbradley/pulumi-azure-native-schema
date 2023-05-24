Represents Fusion alert rule.
API Version: 2023-02-01.
Previous API Version: 2020-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates a Fusion alert rule.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var fusionAlertRule = new AzureNative.SecurityInsights.FusionAlertRule("fusionAlertRule", new()
    {
        AlertRuleTemplateName = "f71aba3d-28fb-450b-b192-4e76a83015c8",
        Enabled = true,
        Kind = "Fusion",
        ResourceGroupName = "myRg",
        RuleId = "myFirstFusionRule",
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
		_, err := securityinsights.NewFusionAlertRule(ctx, "fusionAlertRule", &securityinsights.FusionAlertRuleArgs{
			AlertRuleTemplateName: pulumi.String("f71aba3d-28fb-450b-b192-4e76a83015c8"),
			Enabled:               pulumi.Bool(true),
			Kind:                  pulumi.String("Fusion"),
			ResourceGroupName:     pulumi.String("myRg"),
			RuleId:                pulumi.String("myFirstFusionRule"),
			WorkspaceName:         pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.FusionAlertRule;
import com.pulumi.azurenative.securityinsights.FusionAlertRuleArgs;
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
        var fusionAlertRule = new FusionAlertRule("fusionAlertRule", FusionAlertRuleArgs.builder()        
            .alertRuleTemplateName("f71aba3d-28fb-450b-b192-4e76a83015c8")
            .enabled(true)
            .kind("Fusion")
            .resourceGroupName("myRg")
            .ruleId("myFirstFusionRule")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const fusionAlertRule = new azure_native.securityinsights.FusionAlertRule("fusionAlertRule", {
    alertRuleTemplateName: "f71aba3d-28fb-450b-b192-4e76a83015c8",
    enabled: true,
    kind: "Fusion",
    resourceGroupName: "myRg",
    ruleId: "myFirstFusionRule",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

fusion_alert_rule = azure_native.securityinsights.FusionAlertRule("fusionAlertRule",
    alert_rule_template_name="f71aba3d-28fb-450b-b192-4e76a83015c8",
    enabled=True,
    kind="Fusion",
    resource_group_name="myRg",
    rule_id="myFirstFusionRule",
    workspace_name="myWorkspace")

```

```yaml
resources:
  fusionAlertRule:
    type: azure-native:securityinsights:FusionAlertRule
    properties:
      alertRuleTemplateName: f71aba3d-28fb-450b-b192-4e76a83015c8
      enabled: true
      kind: Fusion
      resourceGroupName: myRg
      ruleId: myFirstFusionRule
      workspaceName: myWorkspace

```

{{% /example %}}
{{% example %}}
### Creates or updates a MicrosoftSecurityIncidentCreation rule.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var fusionAlertRule = new AzureNative.SecurityInsights.FusionAlertRule("fusionAlertRule", new()
    {
        ResourceGroupName = "myRg",
        RuleId = "microsoftSecurityIncidentCreationRuleExample",
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
		_, err := securityinsights.NewFusionAlertRule(ctx, "fusionAlertRule", &securityinsights.FusionAlertRuleArgs{
			ResourceGroupName: pulumi.String("myRg"),
			RuleId:            pulumi.String("microsoftSecurityIncidentCreationRuleExample"),
			WorkspaceName:     pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.FusionAlertRule;
import com.pulumi.azurenative.securityinsights.FusionAlertRuleArgs;
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
        var fusionAlertRule = new FusionAlertRule("fusionAlertRule", FusionAlertRuleArgs.builder()        
            .resourceGroupName("myRg")
            .ruleId("microsoftSecurityIncidentCreationRuleExample")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const fusionAlertRule = new azure_native.securityinsights.FusionAlertRule("fusionAlertRule", {
    resourceGroupName: "myRg",
    ruleId: "microsoftSecurityIncidentCreationRuleExample",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

fusion_alert_rule = azure_native.securityinsights.FusionAlertRule("fusionAlertRule",
    resource_group_name="myRg",
    rule_id="microsoftSecurityIncidentCreationRuleExample",
    workspace_name="myWorkspace")

```

```yaml
resources:
  fusionAlertRule:
    type: azure-native:securityinsights:FusionAlertRule
    properties:
      resourceGroupName: myRg
      ruleId: microsoftSecurityIncidentCreationRuleExample
      workspaceName: myWorkspace

```

{{% /example %}}
{{% example %}}
### Creates or updates a Scheduled alert rule.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var fusionAlertRule = new AzureNative.SecurityInsights.FusionAlertRule("fusionAlertRule", new()
    {
        ResourceGroupName = "myRg",
        RuleId = "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
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
		_, err := securityinsights.NewFusionAlertRule(ctx, "fusionAlertRule", &securityinsights.FusionAlertRuleArgs{
			ResourceGroupName: pulumi.String("myRg"),
			RuleId:            pulumi.String("73e01a99-5cd7-4139-a149-9f2736ff2ab5"),
			WorkspaceName:     pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.FusionAlertRule;
import com.pulumi.azurenative.securityinsights.FusionAlertRuleArgs;
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
        var fusionAlertRule = new FusionAlertRule("fusionAlertRule", FusionAlertRuleArgs.builder()        
            .resourceGroupName("myRg")
            .ruleId("73e01a99-5cd7-4139-a149-9f2736ff2ab5")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const fusionAlertRule = new azure_native.securityinsights.FusionAlertRule("fusionAlertRule", {
    resourceGroupName: "myRg",
    ruleId: "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

fusion_alert_rule = azure_native.securityinsights.FusionAlertRule("fusionAlertRule",
    resource_group_name="myRg",
    rule_id="73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    workspace_name="myWorkspace")

```

```yaml
resources:
  fusionAlertRule:
    type: azure-native:securityinsights:FusionAlertRule
    properties:
      resourceGroupName: myRg
      ruleId: 73e01a99-5cd7-4139-a149-9f2736ff2ab5
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:FusionAlertRule 73e01a99-5cd7-4139-a149-9f2736ff2ab5 /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/alertRules/73e01a99-5cd7-4139-a149-9f2736ff2ab5 
```
