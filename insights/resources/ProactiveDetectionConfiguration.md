Properties that define a ProactiveDetection configuration.
API Version: 2015-05-01.
Previous API Version: 2015-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ProactiveDetectionConfigurationUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var proactiveDetectionConfiguration = new AzureNative.Insights.ProactiveDetectionConfiguration("proactiveDetectionConfiguration", new()
    {
        ConfigurationId = "slowpageloadtime",
        CustomEmails = new[]
        {
            "foo@microsoft.com",
            "foo2@microsoft.com",
        },
        Enabled = true,
        Name = "slowpageloadtime",
        ResourceGroupName = "my-resource-group",
        ResourceName = "my-component",
        RuleDefinitions = new AzureNative.Insights.Inputs.ApplicationInsightsComponentProactiveDetectionConfigurationRuleDefinitionsArgs
        {
            Description = "Smart Detection rules notify you of performance anomaly issues.",
            DisplayName = "Slow page load time",
            HelpUrl = "https://docs.microsoft.com/en-us/azure/application-insights/app-insights-proactive-performance-diagnostics",
            IsEnabledByDefault = true,
            IsHidden = false,
            IsInPreview = false,
            Name = "slowpageloadtime",
            SupportsEmailNotifications = true,
        },
        SendEmailsToSubscriptionOwners = true,
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
		_, err := insights.NewProactiveDetectionConfiguration(ctx, "proactiveDetectionConfiguration", &insights.ProactiveDetectionConfigurationArgs{
			ConfigurationId: pulumi.String("slowpageloadtime"),
			CustomEmails: pulumi.StringArray{
				pulumi.String("foo@microsoft.com"),
				pulumi.String("foo2@microsoft.com"),
			},
			Enabled:           pulumi.Bool(true),
			Name:              pulumi.String("slowpageloadtime"),
			ResourceGroupName: pulumi.String("my-resource-group"),
			ResourceName:      pulumi.String("my-component"),
			RuleDefinitions: &insights.ApplicationInsightsComponentProactiveDetectionConfigurationRuleDefinitionsArgs{
				Description:                pulumi.String("Smart Detection rules notify you of performance anomaly issues."),
				DisplayName:                pulumi.String("Slow page load time"),
				HelpUrl:                    pulumi.String("https://docs.microsoft.com/en-us/azure/application-insights/app-insights-proactive-performance-diagnostics"),
				IsEnabledByDefault:         pulumi.Bool(true),
				IsHidden:                   pulumi.Bool(false),
				IsInPreview:                pulumi.Bool(false),
				Name:                       pulumi.String("slowpageloadtime"),
				SupportsEmailNotifications: pulumi.Bool(true),
			},
			SendEmailsToSubscriptionOwners: pulumi.Bool(true),
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
import com.pulumi.azurenative.insights.ProactiveDetectionConfiguration;
import com.pulumi.azurenative.insights.ProactiveDetectionConfigurationArgs;
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
        var proactiveDetectionConfiguration = new ProactiveDetectionConfiguration("proactiveDetectionConfiguration", ProactiveDetectionConfigurationArgs.builder()        
            .configurationId("slowpageloadtime")
            .customEmails(            
                "foo@microsoft.com",
                "foo2@microsoft.com")
            .enabled(true)
            .name("slowpageloadtime")
            .resourceGroupName("my-resource-group")
            .resourceName("my-component")
            .ruleDefinitions(Map.ofEntries(
                Map.entry("description", "Smart Detection rules notify you of performance anomaly issues."),
                Map.entry("displayName", "Slow page load time"),
                Map.entry("helpUrl", "https://docs.microsoft.com/en-us/azure/application-insights/app-insights-proactive-performance-diagnostics"),
                Map.entry("isEnabledByDefault", true),
                Map.entry("isHidden", false),
                Map.entry("isInPreview", false),
                Map.entry("name", "slowpageloadtime"),
                Map.entry("supportsEmailNotifications", true)
            ))
            .sendEmailsToSubscriptionOwners(true)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const proactiveDetectionConfiguration = new azure_native.insights.ProactiveDetectionConfiguration("proactiveDetectionConfiguration", {
    configurationId: "slowpageloadtime",
    customEmails: [
        "foo@microsoft.com",
        "foo2@microsoft.com",
    ],
    enabled: true,
    name: "slowpageloadtime",
    resourceGroupName: "my-resource-group",
    resourceName: "my-component",
    ruleDefinitions: {
        description: "Smart Detection rules notify you of performance anomaly issues.",
        displayName: "Slow page load time",
        helpUrl: "https://docs.microsoft.com/en-us/azure/application-insights/app-insights-proactive-performance-diagnostics",
        isEnabledByDefault: true,
        isHidden: false,
        isInPreview: false,
        name: "slowpageloadtime",
        supportsEmailNotifications: true,
    },
    sendEmailsToSubscriptionOwners: true,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

proactive_detection_configuration = azure_native.insights.ProactiveDetectionConfiguration("proactiveDetectionConfiguration",
    configuration_id="slowpageloadtime",
    custom_emails=[
        "foo@microsoft.com",
        "foo2@microsoft.com",
    ],
    enabled=True,
    name="slowpageloadtime",
    resource_group_name="my-resource-group",
    resource_name_="my-component",
    rule_definitions=azure_native.insights.ApplicationInsightsComponentProactiveDetectionConfigurationRuleDefinitionsArgs(
        description="Smart Detection rules notify you of performance anomaly issues.",
        display_name="Slow page load time",
        help_url="https://docs.microsoft.com/en-us/azure/application-insights/app-insights-proactive-performance-diagnostics",
        is_enabled_by_default=True,
        is_hidden=False,
        is_in_preview=False,
        name="slowpageloadtime",
        supports_email_notifications=True,
    ),
    send_emails_to_subscription_owners=True)

```

```yaml
resources:
  proactiveDetectionConfiguration:
    type: azure-native:insights:ProactiveDetectionConfiguration
    properties:
      configurationId: slowpageloadtime
      customEmails:
        - foo@microsoft.com
        - foo2@microsoft.com
      enabled: true
      name: slowpageloadtime
      resourceGroupName: my-resource-group
      resourceName: my-component
      ruleDefinitions:
        description: Smart Detection rules notify you of performance anomaly issues.
        displayName: Slow page load time
        helpUrl: https://docs.microsoft.com/en-us/azure/application-insights/app-insights-proactive-performance-diagnostics
        isEnabledByDefault: true
        isHidden: false
        isInPreview: false
        name: slowpageloadtime
        supportsEmailNotifications: true
      sendEmailsToSubscriptionOwners: true

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:ProactiveDetectionConfiguration myresource1 /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Insights/components/{resourceName}/ProactiveDetectionConfigs/{ConfigurationId} 
```
