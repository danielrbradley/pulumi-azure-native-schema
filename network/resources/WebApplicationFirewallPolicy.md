Defines web application firewall policy.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates a WAF policy within a resource group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webApplicationFirewallPolicy = new AzureNative.Network.WebApplicationFirewallPolicy("webApplicationFirewallPolicy", new()
    {
        CustomRules = new[]
        {
            new AzureNative.Network.Inputs.WebApplicationFirewallCustomRuleArgs
            {
                Action = "Block",
                MatchConditions = new[]
                {
                    new AzureNative.Network.Inputs.MatchConditionArgs
                    {
                        MatchValues = new[]
                        {
                            "192.168.1.0/24",
                            "10.0.0.0/24",
                        },
                        MatchVariables = new[]
                        {
                            new AzureNative.Network.Inputs.MatchVariableArgs
                            {
                                VariableName = "RemoteAddr",
                            },
                        },
                        Operator = "IPMatch",
                    },
                },
                Name = "Rule1",
                Priority = 1,
                RuleType = "MatchRule",
            },
            new AzureNative.Network.Inputs.WebApplicationFirewallCustomRuleArgs
            {
                Action = "Block",
                MatchConditions = new[]
                {
                    new AzureNative.Network.Inputs.MatchConditionArgs
                    {
                        MatchValues = new[]
                        {
                            "192.168.1.0/24",
                        },
                        MatchVariables = new[]
                        {
                            new AzureNative.Network.Inputs.MatchVariableArgs
                            {
                                VariableName = "RemoteAddr",
                            },
                        },
                        Operator = "IPMatch",
                    },
                    new AzureNative.Network.Inputs.MatchConditionArgs
                    {
                        MatchValues = new[]
                        {
                            "Windows",
                        },
                        MatchVariables = new[]
                        {
                            new AzureNative.Network.Inputs.MatchVariableArgs
                            {
                                Selector = "UserAgent",
                                VariableName = "RequestHeaders",
                            },
                        },
                        Operator = "Contains",
                    },
                },
                Name = "Rule2",
                Priority = 2,
                RuleType = "MatchRule",
            },
        },
        Location = "WestUs",
        ManagedRules = new AzureNative.Network.Inputs.ManagedRulesDefinitionArgs
        {
            Exclusions = new[]
            {
                new AzureNative.Network.Inputs.OwaspCrsExclusionEntryArgs
                {
                    ExclusionManagedRuleSets = new[]
                    {
                        new AzureNative.Network.Inputs.ExclusionManagedRuleSetArgs
                        {
                            RuleGroups = new[]
                            {
                                new AzureNative.Network.Inputs.ExclusionManagedRuleGroupArgs
                                {
                                    RuleGroupName = "REQUEST-930-APPLICATION-ATTACK-LFI",
                                    Rules = new[]
                                    {
                                        new AzureNative.Network.Inputs.ExclusionManagedRuleArgs
                                        {
                                            RuleId = "930120",
                                        },
                                    },
                                },
                                new AzureNative.Network.Inputs.ExclusionManagedRuleGroupArgs
                                {
                                    RuleGroupName = "REQUEST-932-APPLICATION-ATTACK-RCE",
                                },
                            },
                            RuleSetType = "OWASP",
                            RuleSetVersion = "3.2",
                        },
                    },
                    MatchVariable = "RequestArgNames",
                    Selector = "hello",
                    SelectorMatchOperator = "StartsWith",
                },
                new AzureNative.Network.Inputs.OwaspCrsExclusionEntryArgs
                {
                    ExclusionManagedRuleSets = new[]
                    {
                        new AzureNative.Network.Inputs.ExclusionManagedRuleSetArgs
                        {
                            RuleGroups = new[] {},
                            RuleSetType = "OWASP",
                            RuleSetVersion = "3.1",
                        },
                    },
                    MatchVariable = "RequestArgNames",
                    Selector = "hello",
                    SelectorMatchOperator = "EndsWith",
                },
                new AzureNative.Network.Inputs.OwaspCrsExclusionEntryArgs
                {
                    MatchVariable = "RequestArgNames",
                    Selector = "test",
                    SelectorMatchOperator = "StartsWith",
                },
                new AzureNative.Network.Inputs.OwaspCrsExclusionEntryArgs
                {
                    MatchVariable = "RequestArgValues",
                    Selector = "test",
                    SelectorMatchOperator = "StartsWith",
                },
            },
            ManagedRuleSets = new[]
            {
                new AzureNative.Network.Inputs.ManagedRuleSetArgs
                {
                    RuleGroupOverrides = new[]
                    {
                        new AzureNative.Network.Inputs.ManagedRuleGroupOverrideArgs
                        {
                            RuleGroupName = "REQUEST-931-APPLICATION-ATTACK-RFI",
                            Rules = new[]
                            {
                                new AzureNative.Network.Inputs.ManagedRuleOverrideArgs
                                {
                                    Action = "Log",
                                    RuleId = "931120",
                                    State = "Enabled",
                                },
                                new AzureNative.Network.Inputs.ManagedRuleOverrideArgs
                                {
                                    Action = "AnomalyScoring",
                                    RuleId = "931130",
                                    State = "Disabled",
                                },
                            },
                        },
                    },
                    RuleSetType = "OWASP",
                    RuleSetVersion = "3.2",
                },
            },
        },
        PolicyName = "Policy1",
        ResourceGroupName = "rg1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.network.WebApplicationFirewallPolicy;
import com.pulumi.azurenative.network.WebApplicationFirewallPolicyArgs;
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
        var webApplicationFirewallPolicy = new WebApplicationFirewallPolicy("webApplicationFirewallPolicy", WebApplicationFirewallPolicyArgs.builder()        
            .customRules(            
                Map.ofEntries(
                    Map.entry("action", "Block"),
                    Map.entry("matchConditions", Map.ofEntries(
                        Map.entry("matchValues",                         
                            "192.168.1.0/24",
                            "10.0.0.0/24"),
                        Map.entry("matchVariables", Map.of("variableName", "RemoteAddr")),
                        Map.entry("operator", "IPMatch")
                    )),
                    Map.entry("name", "Rule1"),
                    Map.entry("priority", 1),
                    Map.entry("ruleType", "MatchRule")
                ),
                Map.ofEntries(
                    Map.entry("action", "Block"),
                    Map.entry("matchConditions",                     
                        Map.ofEntries(
                            Map.entry("matchValues", "192.168.1.0/24"),
                            Map.entry("matchVariables", Map.of("variableName", "RemoteAddr")),
                            Map.entry("operator", "IPMatch")
                        ),
                        Map.ofEntries(
                            Map.entry("matchValues", "Windows"),
                            Map.entry("matchVariables", Map.ofEntries(
                                Map.entry("selector", "UserAgent"),
                                Map.entry("variableName", "RequestHeaders")
                            )),
                            Map.entry("operator", "Contains")
                        )),
                    Map.entry("name", "Rule2"),
                    Map.entry("priority", 2),
                    Map.entry("ruleType", "MatchRule")
                ))
            .location("WestUs")
            .managedRules(Map.ofEntries(
                Map.entry("exclusions",                 
                    Map.ofEntries(
                        Map.entry("exclusionManagedRuleSets", Map.ofEntries(
                            Map.entry("ruleGroups",                             
                                Map.ofEntries(
                                    Map.entry("ruleGroupName", "REQUEST-930-APPLICATION-ATTACK-LFI"),
                                    Map.entry("rules", Map.of("ruleId", "930120"))
                                ),
                                Map.of("ruleGroupName", "REQUEST-932-APPLICATION-ATTACK-RCE")),
                            Map.entry("ruleSetType", "OWASP"),
                            Map.entry("ruleSetVersion", "3.2")
                        )),
                        Map.entry("matchVariable", "RequestArgNames"),
                        Map.entry("selector", "hello"),
                        Map.entry("selectorMatchOperator", "StartsWith")
                    ),
                    Map.ofEntries(
                        Map.entry("exclusionManagedRuleSets", Map.ofEntries(
                            Map.entry("ruleGroups", ),
                            Map.entry("ruleSetType", "OWASP"),
                            Map.entry("ruleSetVersion", "3.1")
                        )),
                        Map.entry("matchVariable", "RequestArgNames"),
                        Map.entry("selector", "hello"),
                        Map.entry("selectorMatchOperator", "EndsWith")
                    ),
                    Map.ofEntries(
                        Map.entry("matchVariable", "RequestArgNames"),
                        Map.entry("selector", "test"),
                        Map.entry("selectorMatchOperator", "StartsWith")
                    ),
                    Map.ofEntries(
                        Map.entry("matchVariable", "RequestArgValues"),
                        Map.entry("selector", "test"),
                        Map.entry("selectorMatchOperator", "StartsWith")
                    )),
                Map.entry("managedRuleSets", Map.ofEntries(
                    Map.entry("ruleGroupOverrides", Map.ofEntries(
                        Map.entry("ruleGroupName", "REQUEST-931-APPLICATION-ATTACK-RFI"),
                        Map.entry("rules",                         
                            Map.ofEntries(
                                Map.entry("action", "Log"),
                                Map.entry("ruleId", "931120"),
                                Map.entry("state", "Enabled")
                            ),
                            Map.ofEntries(
                                Map.entry("action", "AnomalyScoring"),
                                Map.entry("ruleId", "931130"),
                                Map.entry("state", "Disabled")
                            ))
                    )),
                    Map.entry("ruleSetType", "OWASP"),
                    Map.entry("ruleSetVersion", "3.2")
                ))
            ))
            .policyName("Policy1")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webApplicationFirewallPolicy = new azure_native.network.WebApplicationFirewallPolicy("webApplicationFirewallPolicy", {
    customRules: [
        {
            action: "Block",
            matchConditions: [{
                matchValues: [
                    "192.168.1.0/24",
                    "10.0.0.0/24",
                ],
                matchVariables: [{
                    variableName: "RemoteAddr",
                }],
                operator: "IPMatch",
            }],
            name: "Rule1",
            priority: 1,
            ruleType: "MatchRule",
        },
        {
            action: "Block",
            matchConditions: [
                {
                    matchValues: ["192.168.1.0/24"],
                    matchVariables: [{
                        variableName: "RemoteAddr",
                    }],
                    operator: "IPMatch",
                },
                {
                    matchValues: ["Windows"],
                    matchVariables: [{
                        selector: "UserAgent",
                        variableName: "RequestHeaders",
                    }],
                    operator: "Contains",
                },
            ],
            name: "Rule2",
            priority: 2,
            ruleType: "MatchRule",
        },
    ],
    location: "WestUs",
    managedRules: {
        exclusions: [
            {
                exclusionManagedRuleSets: [{
                    ruleGroups: [
                        {
                            ruleGroupName: "REQUEST-930-APPLICATION-ATTACK-LFI",
                            rules: [{
                                ruleId: "930120",
                            }],
                        },
                        {
                            ruleGroupName: "REQUEST-932-APPLICATION-ATTACK-RCE",
                        },
                    ],
                    ruleSetType: "OWASP",
                    ruleSetVersion: "3.2",
                }],
                matchVariable: "RequestArgNames",
                selector: "hello",
                selectorMatchOperator: "StartsWith",
            },
            {
                exclusionManagedRuleSets: [{
                    ruleGroups: [],
                    ruleSetType: "OWASP",
                    ruleSetVersion: "3.1",
                }],
                matchVariable: "RequestArgNames",
                selector: "hello",
                selectorMatchOperator: "EndsWith",
            },
            {
                matchVariable: "RequestArgNames",
                selector: "test",
                selectorMatchOperator: "StartsWith",
            },
            {
                matchVariable: "RequestArgValues",
                selector: "test",
                selectorMatchOperator: "StartsWith",
            },
        ],
        managedRuleSets: [{
            ruleGroupOverrides: [{
                ruleGroupName: "REQUEST-931-APPLICATION-ATTACK-RFI",
                rules: [
                    {
                        action: "Log",
                        ruleId: "931120",
                        state: "Enabled",
                    },
                    {
                        action: "AnomalyScoring",
                        ruleId: "931130",
                        state: "Disabled",
                    },
                ],
            }],
            ruleSetType: "OWASP",
            ruleSetVersion: "3.2",
        }],
    },
    policyName: "Policy1",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_application_firewall_policy = azure_native.network.WebApplicationFirewallPolicy("webApplicationFirewallPolicy",
    custom_rules=[
        {
            "action": "Block",
            "matchConditions": [{
                "matchValues": [
                    "192.168.1.0/24",
                    "10.0.0.0/24",
                ],
                "matchVariables": [azure_native.network.MatchVariableArgs(
                    variable_name="RemoteAddr",
                )],
                "operator": "IPMatch",
            }],
            "name": "Rule1",
            "priority": 1,
            "ruleType": "MatchRule",
        },
        {
            "action": "Block",
            "matchConditions": [
                {
                    "matchValues": ["192.168.1.0/24"],
                    "matchVariables": [azure_native.network.MatchVariableArgs(
                        variable_name="RemoteAddr",
                    )],
                    "operator": "IPMatch",
                },
                {
                    "matchValues": ["Windows"],
                    "matchVariables": [azure_native.network.MatchVariableArgs(
                        selector="UserAgent",
                        variable_name="RequestHeaders",
                    )],
                    "operator": "Contains",
                },
            ],
            "name": "Rule2",
            "priority": 2,
            "ruleType": "MatchRule",
        },
    ],
    location="WestUs",
    managed_rules=azure_native.network.ManagedRulesDefinitionResponseArgs(
        exclusions=[
            {
                "exclusionManagedRuleSets": [{
                    "ruleGroups": [
                        {
                            "ruleGroupName": "REQUEST-930-APPLICATION-ATTACK-LFI",
                            "rules": [azure_native.network.ExclusionManagedRuleArgs(
                                rule_id="930120",
                            )],
                        },
                        azure_native.network.ExclusionManagedRuleGroupArgs(
                            rule_group_name="REQUEST-932-APPLICATION-ATTACK-RCE",
                        ),
                    ],
                    "ruleSetType": "OWASP",
                    "ruleSetVersion": "3.2",
                }],
                "matchVariable": "RequestArgNames",
                "selector": "hello",
                "selectorMatchOperator": "StartsWith",
            },
            {
                "exclusionManagedRuleSets": [{
                    "ruleGroups": [],
                    "ruleSetType": "OWASP",
                    "ruleSetVersion": "3.1",
                }],
                "matchVariable": "RequestArgNames",
                "selector": "hello",
                "selectorMatchOperator": "EndsWith",
            },
            azure_native.network.OwaspCrsExclusionEntryArgs(
                match_variable="RequestArgNames",
                selector="test",
                selector_match_operator="StartsWith",
            ),
            azure_native.network.OwaspCrsExclusionEntryArgs(
                match_variable="RequestArgValues",
                selector="test",
                selector_match_operator="StartsWith",
            ),
        ],
        managed_rule_sets=[{
            "ruleGroupOverrides": [{
                "ruleGroupName": "REQUEST-931-APPLICATION-ATTACK-RFI",
                "rules": [
                    azure_native.network.ManagedRuleOverrideArgs(
                        action="Log",
                        rule_id="931120",
                        state="Enabled",
                    ),
                    azure_native.network.ManagedRuleOverrideArgs(
                        action="AnomalyScoring",
                        rule_id="931130",
                        state="Disabled",
                    ),
                ],
            }],
            "ruleSetType": "OWASP",
            "ruleSetVersion": "3.2",
        }],
    ),
    policy_name="Policy1",
    resource_group_name="rg1")

```

```yaml
resources:
  webApplicationFirewallPolicy:
    type: azure-native:network:WebApplicationFirewallPolicy
    properties:
      customRules:
        - action: Block
          matchConditions:
            - matchValues:
                - 192.168.1.0/24
                - 10.0.0.0/24
              matchVariables:
                - variableName: RemoteAddr
              operator: IPMatch
          name: Rule1
          priority: 1
          ruleType: MatchRule
        - action: Block
          matchConditions:
            - matchValues:
                - 192.168.1.0/24
              matchVariables:
                - variableName: RemoteAddr
              operator: IPMatch
            - matchValues:
                - Windows
              matchVariables:
                - selector: UserAgent
                  variableName: RequestHeaders
              operator: Contains
          name: Rule2
          priority: 2
          ruleType: MatchRule
      location: WestUs
      managedRules:
        exclusions:
          - exclusionManagedRuleSets:
              - ruleGroups:
                  - ruleGroupName: REQUEST-930-APPLICATION-ATTACK-LFI
                    rules:
                      - ruleId: '930120'
                  - ruleGroupName: REQUEST-932-APPLICATION-ATTACK-RCE
                ruleSetType: OWASP
                ruleSetVersion: '3.2'
            matchVariable: RequestArgNames
            selector: hello
            selectorMatchOperator: StartsWith
          - exclusionManagedRuleSets:
              - ruleGroups: []
                ruleSetType: OWASP
                ruleSetVersion: '3.1'
            matchVariable: RequestArgNames
            selector: hello
            selectorMatchOperator: EndsWith
          - matchVariable: RequestArgNames
            selector: test
            selectorMatchOperator: StartsWith
          - matchVariable: RequestArgValues
            selector: test
            selectorMatchOperator: StartsWith
        managedRuleSets:
          - ruleGroupOverrides:
              - ruleGroupName: REQUEST-931-APPLICATION-ATTACK-RFI
                rules:
                  - action: Log
                    ruleId: '931120'
                    state: Enabled
                  - action: AnomalyScoring
                    ruleId: '931130'
                    state: Disabled
            ruleSetType: OWASP
            ruleSetVersion: '3.2'
      policyName: Policy1
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:WebApplicationFirewallPolicy Policy1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/ApplicationGatewayWebApplicationFirewallPolicies/Policy1 
```
