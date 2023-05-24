Description of Rule Resource.
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RulesCreateCorrelationFilter
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var rule = new AzureNative.ServiceBus.Rule("rule", new()
    {
        CorrelationFilter = new AzureNative.ServiceBus.Inputs.CorrelationFilterArgs
        {
            Properties = 
            {
                { "topicHint", "Crop" },
            },
        },
        FilterType = AzureNative.ServiceBus.FilterType.CorrelationFilter,
        NamespaceName = "sdk-Namespace-1319",
        ResourceGroupName = "resourceGroupName",
        RuleName = "sdk-Rules-6571",
        SubscriptionName = "sdk-Subscriptions-8691",
        TopicName = "sdk-Topics-2081",
    });

});


```

```go
package main

import (
	servicebus "github.com/pulumi/pulumi-azure-native-sdk/servicebus"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicebus.NewRule(ctx, "rule", &servicebus.RuleArgs{
			CorrelationFilter: &servicebus.CorrelationFilterArgs{
				Properties: pulumi.StringMap{
					"topicHint": pulumi.String("Crop"),
				},
			},
			FilterType:        servicebus.FilterTypeCorrelationFilter,
			NamespaceName:     pulumi.String("sdk-Namespace-1319"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			RuleName:          pulumi.String("sdk-Rules-6571"),
			SubscriptionName:  pulumi.String("sdk-Subscriptions-8691"),
			TopicName:         pulumi.String("sdk-Topics-2081"),
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
import com.pulumi.azurenative.servicebus.Rule;
import com.pulumi.azurenative.servicebus.RuleArgs;
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
        var rule = new Rule("rule", RuleArgs.builder()        
            .correlationFilter(Map.of("properties", Map.of("topicHint", "Crop")))
            .filterType("CorrelationFilter")
            .namespaceName("sdk-Namespace-1319")
            .resourceGroupName("resourceGroupName")
            .ruleName("sdk-Rules-6571")
            .subscriptionName("sdk-Subscriptions-8691")
            .topicName("sdk-Topics-2081")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const rule = new azure_native.servicebus.Rule("rule", {
    correlationFilter: {
        properties: {
            topicHint: "Crop",
        },
    },
    filterType: azure_native.servicebus.FilterType.CorrelationFilter,
    namespaceName: "sdk-Namespace-1319",
    resourceGroupName: "resourceGroupName",
    ruleName: "sdk-Rules-6571",
    subscriptionName: "sdk-Subscriptions-8691",
    topicName: "sdk-Topics-2081",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

rule = azure_native.servicebus.Rule("rule",
    correlation_filter=azure_native.servicebus.CorrelationFilterArgs(
        properties={
            "topicHint": "Crop",
        },
    ),
    filter_type=azure_native.servicebus.FilterType.CORRELATION_FILTER,
    namespace_name="sdk-Namespace-1319",
    resource_group_name="resourceGroupName",
    rule_name="sdk-Rules-6571",
    subscription_name="sdk-Subscriptions-8691",
    topic_name="sdk-Topics-2081")

```

```yaml
resources:
  rule:
    type: azure-native:servicebus:Rule
    properties:
      correlationFilter:
        properties:
          topicHint: Crop
      filterType: CorrelationFilter
      namespaceName: sdk-Namespace-1319
      resourceGroupName: resourceGroupName
      ruleName: sdk-Rules-6571
      subscriptionName: sdk-Subscriptions-8691
      topicName: sdk-Topics-2081

```

{{% /example %}}
{{% example %}}
### RulesCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var rule = new AzureNative.ServiceBus.Rule("rule", new()
    {
        NamespaceName = "sdk-Namespace-1319",
        ResourceGroupName = "resourceGroupName",
        RuleName = "sdk-Rules-6571",
        SubscriptionName = "sdk-Subscriptions-8691",
        TopicName = "sdk-Topics-2081",
    });

});


```

```go
package main

import (
	servicebus "github.com/pulumi/pulumi-azure-native-sdk/servicebus"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicebus.NewRule(ctx, "rule", &servicebus.RuleArgs{
			NamespaceName:     pulumi.String("sdk-Namespace-1319"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			RuleName:          pulumi.String("sdk-Rules-6571"),
			SubscriptionName:  pulumi.String("sdk-Subscriptions-8691"),
			TopicName:         pulumi.String("sdk-Topics-2081"),
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
import com.pulumi.azurenative.servicebus.Rule;
import com.pulumi.azurenative.servicebus.RuleArgs;
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
        var rule = new Rule("rule", RuleArgs.builder()        
            .namespaceName("sdk-Namespace-1319")
            .resourceGroupName("resourceGroupName")
            .ruleName("sdk-Rules-6571")
            .subscriptionName("sdk-Subscriptions-8691")
            .topicName("sdk-Topics-2081")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const rule = new azure_native.servicebus.Rule("rule", {
    namespaceName: "sdk-Namespace-1319",
    resourceGroupName: "resourceGroupName",
    ruleName: "sdk-Rules-6571",
    subscriptionName: "sdk-Subscriptions-8691",
    topicName: "sdk-Topics-2081",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

rule = azure_native.servicebus.Rule("rule",
    namespace_name="sdk-Namespace-1319",
    resource_group_name="resourceGroupName",
    rule_name="sdk-Rules-6571",
    subscription_name="sdk-Subscriptions-8691",
    topic_name="sdk-Topics-2081")

```

```yaml
resources:
  rule:
    type: azure-native:servicebus:Rule
    properties:
      namespaceName: sdk-Namespace-1319
      resourceGroupName: resourceGroupName
      ruleName: sdk-Rules-6571
      subscriptionName: sdk-Subscriptions-8691
      topicName: sdk-Topics-2081

```

{{% /example %}}
{{% example %}}
### RulesCreateSqlFilter
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var rule = new AzureNative.ServiceBus.Rule("rule", new()
    {
        FilterType = AzureNative.ServiceBus.FilterType.SqlFilter,
        NamespaceName = "sdk-Namespace-1319",
        ResourceGroupName = "resourceGroupName",
        RuleName = "sdk-Rules-6571",
        SqlFilter = new AzureNative.ServiceBus.Inputs.SqlFilterArgs
        {
            SqlExpression = "myproperty=test",
        },
        SubscriptionName = "sdk-Subscriptions-8691",
        TopicName = "sdk-Topics-2081",
    });

});


```

```go
package main

import (
	servicebus "github.com/pulumi/pulumi-azure-native-sdk/servicebus"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicebus.NewRule(ctx, "rule", &servicebus.RuleArgs{
			FilterType:        servicebus.FilterTypeSqlFilter,
			NamespaceName:     pulumi.String("sdk-Namespace-1319"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			RuleName:          pulumi.String("sdk-Rules-6571"),
			SqlFilter: &servicebus.SqlFilterArgs{
				SqlExpression: pulumi.String("myproperty=test"),
			},
			SubscriptionName: pulumi.String("sdk-Subscriptions-8691"),
			TopicName:        pulumi.String("sdk-Topics-2081"),
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
import com.pulumi.azurenative.servicebus.Rule;
import com.pulumi.azurenative.servicebus.RuleArgs;
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
        var rule = new Rule("rule", RuleArgs.builder()        
            .filterType("SqlFilter")
            .namespaceName("sdk-Namespace-1319")
            .resourceGroupName("resourceGroupName")
            .ruleName("sdk-Rules-6571")
            .sqlFilter(Map.of("sqlExpression", "myproperty=test"))
            .subscriptionName("sdk-Subscriptions-8691")
            .topicName("sdk-Topics-2081")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const rule = new azure_native.servicebus.Rule("rule", {
    filterType: azure_native.servicebus.FilterType.SqlFilter,
    namespaceName: "sdk-Namespace-1319",
    resourceGroupName: "resourceGroupName",
    ruleName: "sdk-Rules-6571",
    sqlFilter: {
        sqlExpression: "myproperty=test",
    },
    subscriptionName: "sdk-Subscriptions-8691",
    topicName: "sdk-Topics-2081",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

rule = azure_native.servicebus.Rule("rule",
    filter_type=azure_native.servicebus.FilterType.SQL_FILTER,
    namespace_name="sdk-Namespace-1319",
    resource_group_name="resourceGroupName",
    rule_name="sdk-Rules-6571",
    sql_filter=azure_native.servicebus.SqlFilterArgs(
        sql_expression="myproperty=test",
    ),
    subscription_name="sdk-Subscriptions-8691",
    topic_name="sdk-Topics-2081")

```

```yaml
resources:
  rule:
    type: azure-native:servicebus:Rule
    properties:
      filterType: SqlFilter
      namespaceName: sdk-Namespace-1319
      resourceGroupName: resourceGroupName
      ruleName: sdk-Rules-6571
      sqlFilter:
        sqlExpression: myproperty=test
      subscriptionName: sdk-Subscriptions-8691
      topicName: sdk-Topics-2081

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicebus:Rule sdk-Rules-6571 /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-1319/topics/sdk-Topics-2081/subscriptions/sdk-Subscriptions-8691/rules/sdk-Rules-6571 
```
