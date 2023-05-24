Describes a forwarding rule within a DNS forwarding ruleset.
API Version: 2022-07-01.
Previous API Version: 2020-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Upsert forwarding rule in a DNS forwarding ruleset
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var forwardingRule = new AzureNative.Network.ForwardingRule("forwardingRule", new()
    {
        DnsForwardingRulesetName = "sampleDnsForwardingRuleset",
        DomainName = "contoso.com.",
        ForwardingRuleName = "sampleForwardingRule",
        ForwardingRuleState = "Enabled",
        Metadata = 
        {
            { "additionalProp1", "value1" },
        },
        ResourceGroupName = "sampleResourceGroup",
        TargetDnsServers = new[]
        {
            new AzureNative.Network.Inputs.TargetDnsServerArgs
            {
                IpAddress = "10.0.0.1",
                Port = 53,
            },
            new AzureNative.Network.Inputs.TargetDnsServerArgs
            {
                IpAddress = "10.0.0.2",
                Port = 53,
            },
        },
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewForwardingRule(ctx, "forwardingRule", &network.ForwardingRuleArgs{
			DnsForwardingRulesetName: pulumi.String("sampleDnsForwardingRuleset"),
			DomainName:               pulumi.String("contoso.com."),
			ForwardingRuleName:       pulumi.String("sampleForwardingRule"),
			ForwardingRuleState:      pulumi.String("Enabled"),
			Metadata: pulumi.StringMap{
				"additionalProp1": pulumi.String("value1"),
			},
			ResourceGroupName: pulumi.String("sampleResourceGroup"),
			TargetDnsServers: []network.TargetDnsServerArgs{
				{
					IpAddress: pulumi.String("10.0.0.1"),
					Port:      pulumi.Int(53),
				},
				{
					IpAddress: pulumi.String("10.0.0.2"),
					Port:      pulumi.Int(53),
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
import com.pulumi.azurenative.network.ForwardingRule;
import com.pulumi.azurenative.network.ForwardingRuleArgs;
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
        var forwardingRule = new ForwardingRule("forwardingRule", ForwardingRuleArgs.builder()        
            .dnsForwardingRulesetName("sampleDnsForwardingRuleset")
            .domainName("contoso.com.")
            .forwardingRuleName("sampleForwardingRule")
            .forwardingRuleState("Enabled")
            .metadata(Map.of("additionalProp1", "value1"))
            .resourceGroupName("sampleResourceGroup")
            .targetDnsServers(            
                Map.ofEntries(
                    Map.entry("ipAddress", "10.0.0.1"),
                    Map.entry("port", 53)
                ),
                Map.ofEntries(
                    Map.entry("ipAddress", "10.0.0.2"),
                    Map.entry("port", 53)
                ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const forwardingRule = new azure_native.network.ForwardingRule("forwardingRule", {
    dnsForwardingRulesetName: "sampleDnsForwardingRuleset",
    domainName: "contoso.com.",
    forwardingRuleName: "sampleForwardingRule",
    forwardingRuleState: "Enabled",
    metadata: {
        additionalProp1: "value1",
    },
    resourceGroupName: "sampleResourceGroup",
    targetDnsServers: [
        {
            ipAddress: "10.0.0.1",
            port: 53,
        },
        {
            ipAddress: "10.0.0.2",
            port: 53,
        },
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

forwarding_rule = azure_native.network.ForwardingRule("forwardingRule",
    dns_forwarding_ruleset_name="sampleDnsForwardingRuleset",
    domain_name="contoso.com.",
    forwarding_rule_name="sampleForwardingRule",
    forwarding_rule_state="Enabled",
    metadata={
        "additionalProp1": "value1",
    },
    resource_group_name="sampleResourceGroup",
    target_dns_servers=[
        azure_native.network.TargetDnsServerArgs(
            ip_address="10.0.0.1",
            port=53,
        ),
        azure_native.network.TargetDnsServerArgs(
            ip_address="10.0.0.2",
            port=53,
        ),
    ])

```

```yaml
resources:
  forwardingRule:
    type: azure-native:network:ForwardingRule
    properties:
      dnsForwardingRulesetName: sampleDnsForwardingRuleset
      domainName: contoso.com.
      forwardingRuleName: sampleForwardingRule
      forwardingRuleState: Enabled
      metadata:
        additionalProp1: value1
      resourceGroupName: sampleResourceGroup
      targetDnsServers:
        - ipAddress: 10.0.0.1
          port: 53
        - ipAddress: 10.0.0.2
          port: 53

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ForwardingRule sampleForwardingRule /subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsForwardingRulesets/sampleDnsForwardingRuleset/forwardingRules/sampleForwardingRule 
```
