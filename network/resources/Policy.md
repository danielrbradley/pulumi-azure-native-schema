Defines web application firewall policy.
API Version: 2022-05-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates specific policy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policy = new AzureNative.Network.Policy("policy", new()
    {
        CustomRules = new AzureNative.Network.Inputs.CustomRuleListArgs
        {
            Rules = new[]
            {
                new AzureNative.Network.Inputs.CustomRuleArgs
                {
                    Action = "Block",
                    MatchConditions = new[]
                    {
                        new AzureNative.Network.Inputs.FrontDoorMatchConditionArgs
                        {
                            MatchValue = new[]
                            {
                                "192.168.1.0/24",
                                "10.0.0.0/24",
                            },
                            MatchVariable = "RemoteAddr",
                            Operator = "IPMatch",
                        },
                    },
                    Name = "Rule1",
                    Priority = 1,
                    RateLimitThreshold = 1000,
                    RuleType = "RateLimitRule",
                },
                new AzureNative.Network.Inputs.CustomRuleArgs
                {
                    Action = "Block",
                    MatchConditions = new[]
                    {
                        new AzureNative.Network.Inputs.FrontDoorMatchConditionArgs
                        {
                            MatchValue = new[]
                            {
                                "CH",
                            },
                            MatchVariable = "RemoteAddr",
                            Operator = "GeoMatch",
                        },
                        new AzureNative.Network.Inputs.FrontDoorMatchConditionArgs
                        {
                            MatchValue = new[]
                            {
                                "windows",
                            },
                            MatchVariable = "RequestHeader",
                            Operator = "Contains",
                            Selector = "UserAgent",
                            Transforms = new[]
                            {
                                "Lowercase",
                            },
                        },
                    },
                    Name = "Rule2",
                    Priority = 2,
                    RuleType = "MatchRule",
                },
            },
        },
        ManagedRules = new AzureNative.Network.Inputs.ManagedRuleSetListArgs
        {
            ManagedRuleSets = new[]
            {
                new AzureNative.Network.Inputs.FrontDoorManagedRuleSetArgs
                {
                    Exclusions = new[]
                    {
                        new AzureNative.Network.Inputs.ManagedRuleExclusionArgs
                        {
                            MatchVariable = "RequestHeaderNames",
                            Selector = "User-Agent",
                            SelectorMatchOperator = "Equals",
                        },
                    },
                    RuleGroupOverrides = new[]
                    {
                        new AzureNative.Network.Inputs.FrontDoorManagedRuleGroupOverrideArgs
                        {
                            Exclusions = new[]
                            {
                                new AzureNative.Network.Inputs.ManagedRuleExclusionArgs
                                {
                                    MatchVariable = "RequestCookieNames",
                                    Selector = "token",
                                    SelectorMatchOperator = "StartsWith",
                                },
                            },
                            RuleGroupName = "SQLI",
                            Rules = new[]
                            {
                                new AzureNative.Network.Inputs.FrontDoorManagedRuleOverrideArgs
                                {
                                    Action = "Redirect",
                                    EnabledState = "Enabled",
                                    Exclusions = new[]
                                    {
                                        new AzureNative.Network.Inputs.ManagedRuleExclusionArgs
                                        {
                                            MatchVariable = "QueryStringArgNames",
                                            Selector = "query",
                                            SelectorMatchOperator = "Equals",
                                        },
                                    },
                                    RuleId = "942100",
                                },
                                new AzureNative.Network.Inputs.FrontDoorManagedRuleOverrideArgs
                                {
                                    EnabledState = "Disabled",
                                    RuleId = "942110",
                                },
                            },
                        },
                    },
                    RuleSetAction = "Block",
                    RuleSetType = "DefaultRuleSet",
                    RuleSetVersion = "1.0",
                },
            },
        },
        PolicyName = "Policy1",
        PolicySettings = new AzureNative.Network.Inputs.FrontDoorPolicySettingsArgs
        {
            CustomBlockResponseBody = "PGh0bWw+CjxoZWFkZXI+PHRpdGxlPkhlbGxvPC90aXRsZT48L2hlYWRlcj4KPGJvZHk+CkhlbGxvIHdvcmxkCjwvYm9keT4KPC9odG1sPg==",
            CustomBlockResponseStatusCode = 499,
            EnabledState = "Enabled",
            Mode = "Prevention",
            RedirectUrl = "http://www.bing.com",
            RequestBodyCheck = "Disabled",
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.SkuArgs
        {
            Name = "Classic_AzureFrontDoor",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.network.Policy;
import com.pulumi.azurenative.network.PolicyArgs;
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
        var policy = new Policy("policy", PolicyArgs.builder()        
            .customRules(Map.of("rules",             
                Map.ofEntries(
                    Map.entry("action", "Block"),
                    Map.entry("matchConditions", Map.ofEntries(
                        Map.entry("matchValue",                         
                            "192.168.1.0/24",
                            "10.0.0.0/24"),
                        Map.entry("matchVariable", "RemoteAddr"),
                        Map.entry("operator", "IPMatch")
                    )),
                    Map.entry("name", "Rule1"),
                    Map.entry("priority", 1),
                    Map.entry("rateLimitThreshold", 1000),
                    Map.entry("ruleType", "RateLimitRule")
                ),
                Map.ofEntries(
                    Map.entry("action", "Block"),
                    Map.entry("matchConditions",                     
                        Map.ofEntries(
                            Map.entry("matchValue", "CH"),
                            Map.entry("matchVariable", "RemoteAddr"),
                            Map.entry("operator", "GeoMatch")
                        ),
                        Map.ofEntries(
                            Map.entry("matchValue", "windows"),
                            Map.entry("matchVariable", "RequestHeader"),
                            Map.entry("operator", "Contains"),
                            Map.entry("selector", "UserAgent"),
                            Map.entry("transforms", "Lowercase")
                        )),
                    Map.entry("name", "Rule2"),
                    Map.entry("priority", 2),
                    Map.entry("ruleType", "MatchRule")
                )))
            .managedRules(Map.of("managedRuleSets", Map.ofEntries(
                Map.entry("exclusions", Map.ofEntries(
                    Map.entry("matchVariable", "RequestHeaderNames"),
                    Map.entry("selector", "User-Agent"),
                    Map.entry("selectorMatchOperator", "Equals")
                )),
                Map.entry("ruleGroupOverrides", Map.ofEntries(
                    Map.entry("exclusions", Map.ofEntries(
                        Map.entry("matchVariable", "RequestCookieNames"),
                        Map.entry("selector", "token"),
                        Map.entry("selectorMatchOperator", "StartsWith")
                    )),
                    Map.entry("ruleGroupName", "SQLI"),
                    Map.entry("rules",                     
                        Map.ofEntries(
                            Map.entry("action", "Redirect"),
                            Map.entry("enabledState", "Enabled"),
                            Map.entry("exclusions", Map.ofEntries(
                                Map.entry("matchVariable", "QueryStringArgNames"),
                                Map.entry("selector", "query"),
                                Map.entry("selectorMatchOperator", "Equals")
                            )),
                            Map.entry("ruleId", "942100")
                        ),
                        Map.ofEntries(
                            Map.entry("enabledState", "Disabled"),
                            Map.entry("ruleId", "942110")
                        ))
                )),
                Map.entry("ruleSetAction", "Block"),
                Map.entry("ruleSetType", "DefaultRuleSet"),
                Map.entry("ruleSetVersion", "1.0")
            )))
            .policyName("Policy1")
            .policySettings(Map.ofEntries(
                Map.entry("customBlockResponseBody", "PGh0bWw+CjxoZWFkZXI+PHRpdGxlPkhlbGxvPC90aXRsZT48L2hlYWRlcj4KPGJvZHk+CkhlbGxvIHdvcmxkCjwvYm9keT4KPC9odG1sPg=="),
                Map.entry("customBlockResponseStatusCode", 499),
                Map.entry("enabledState", "Enabled"),
                Map.entry("mode", "Prevention"),
                Map.entry("redirectUrl", "http://www.bing.com"),
                Map.entry("requestBodyCheck", "Disabled")
            ))
            .resourceGroupName("rg1")
            .sku(Map.of("name", "Classic_AzureFrontDoor"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policy = new azure_native.network.Policy("policy", {
    customRules: {
        rules: [
            {
                action: "Block",
                matchConditions: [{
                    matchValue: [
                        "192.168.1.0/24",
                        "10.0.0.0/24",
                    ],
                    matchVariable: "RemoteAddr",
                    operator: "IPMatch",
                }],
                name: "Rule1",
                priority: 1,
                rateLimitThreshold: 1000,
                ruleType: "RateLimitRule",
            },
            {
                action: "Block",
                matchConditions: [
                    {
                        matchValue: ["CH"],
                        matchVariable: "RemoteAddr",
                        operator: "GeoMatch",
                    },
                    {
                        matchValue: ["windows"],
                        matchVariable: "RequestHeader",
                        operator: "Contains",
                        selector: "UserAgent",
                        transforms: ["Lowercase"],
                    },
                ],
                name: "Rule2",
                priority: 2,
                ruleType: "MatchRule",
            },
        ],
    },
    managedRules: {
        managedRuleSets: [{
            exclusions: [{
                matchVariable: "RequestHeaderNames",
                selector: "User-Agent",
                selectorMatchOperator: "Equals",
            }],
            ruleGroupOverrides: [{
                exclusions: [{
                    matchVariable: "RequestCookieNames",
                    selector: "token",
                    selectorMatchOperator: "StartsWith",
                }],
                ruleGroupName: "SQLI",
                rules: [
                    {
                        action: "Redirect",
                        enabledState: "Enabled",
                        exclusions: [{
                            matchVariable: "QueryStringArgNames",
                            selector: "query",
                            selectorMatchOperator: "Equals",
                        }],
                        ruleId: "942100",
                    },
                    {
                        enabledState: "Disabled",
                        ruleId: "942110",
                    },
                ],
            }],
            ruleSetAction: "Block",
            ruleSetType: "DefaultRuleSet",
            ruleSetVersion: "1.0",
        }],
    },
    policyName: "Policy1",
    policySettings: {
        customBlockResponseBody: "PGh0bWw+CjxoZWFkZXI+PHRpdGxlPkhlbGxvPC90aXRsZT48L2hlYWRlcj4KPGJvZHk+CkhlbGxvIHdvcmxkCjwvYm9keT4KPC9odG1sPg==",
        customBlockResponseStatusCode: 499,
        enabledState: "Enabled",
        mode: "Prevention",
        redirectUrl: "http://www.bing.com",
        requestBodyCheck: "Disabled",
    },
    resourceGroupName: "rg1",
    sku: {
        name: "Classic_AzureFrontDoor",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy = azure_native.network.Policy("policy",
    custom_rules=azure_native.network.CustomRuleListResponseArgs(
        rules=[
            {
                "action": "Block",
                "matchConditions": [azure_native.network.FrontDoorMatchConditionArgs(
                    match_value=[
                        "192.168.1.0/24",
                        "10.0.0.0/24",
                    ],
                    match_variable="RemoteAddr",
                    operator="IPMatch",
                )],
                "name": "Rule1",
                "priority": 1,
                "rateLimitThreshold": 1000,
                "ruleType": "RateLimitRule",
            },
            {
                "action": "Block",
                "matchConditions": [
                    azure_native.network.FrontDoorMatchConditionArgs(
                        match_value=["CH"],
                        match_variable="RemoteAddr",
                        operator="GeoMatch",
                    ),
                    azure_native.network.FrontDoorMatchConditionArgs(
                        match_value=["windows"],
                        match_variable="RequestHeader",
                        operator="Contains",
                        selector="UserAgent",
                        transforms=["Lowercase"],
                    ),
                ],
                "name": "Rule2",
                "priority": 2,
                "ruleType": "MatchRule",
            },
        ],
    ),
    managed_rules=azure_native.network.ManagedRuleSetListResponseArgs(
        managed_rule_sets=[{
            "exclusions": [azure_native.network.ManagedRuleExclusionArgs(
                match_variable="RequestHeaderNames",
                selector="User-Agent",
                selector_match_operator="Equals",
            )],
            "ruleGroupOverrides": [{
                "exclusions": [azure_native.network.ManagedRuleExclusionArgs(
                    match_variable="RequestCookieNames",
                    selector="token",
                    selector_match_operator="StartsWith",
                )],
                "ruleGroupName": "SQLI",
                "rules": [
                    {
                        "action": "Redirect",
                        "enabledState": "Enabled",
                        "exclusions": [azure_native.network.ManagedRuleExclusionArgs(
                            match_variable="QueryStringArgNames",
                            selector="query",
                            selector_match_operator="Equals",
                        )],
                        "ruleId": "942100",
                    },
                    azure_native.network.FrontDoorManagedRuleOverrideArgs(
                        enabled_state="Disabled",
                        rule_id="942110",
                    ),
                ],
            }],
            "ruleSetAction": "Block",
            "ruleSetType": "DefaultRuleSet",
            "ruleSetVersion": "1.0",
        }],
    ),
    policy_name="Policy1",
    policy_settings=azure_native.network.FrontDoorPolicySettingsArgs(
        custom_block_response_body="PGh0bWw+CjxoZWFkZXI+PHRpdGxlPkhlbGxvPC90aXRsZT48L2hlYWRlcj4KPGJvZHk+CkhlbGxvIHdvcmxkCjwvYm9keT4KPC9odG1sPg==",
        custom_block_response_status_code=499,
        enabled_state="Enabled",
        mode="Prevention",
        redirect_url="http://www.bing.com",
        request_body_check="Disabled",
    ),
    resource_group_name="rg1",
    sku=azure_native.network.SkuArgs(
        name="Classic_AzureFrontDoor",
    ))

```

```yaml
resources:
  policy:
    type: azure-native:network:Policy
    properties:
      customRules:
        rules:
          - action: Block
            matchConditions:
              - matchValue:
                  - 192.168.1.0/24
                  - 10.0.0.0/24
                matchVariable: RemoteAddr
                operator: IPMatch
            name: Rule1
            priority: 1
            rateLimitThreshold: 1000
            ruleType: RateLimitRule
          - action: Block
            matchConditions:
              - matchValue:
                  - CH
                matchVariable: RemoteAddr
                operator: GeoMatch
              - matchValue:
                  - windows
                matchVariable: RequestHeader
                operator: Contains
                selector: UserAgent
                transforms:
                  - Lowercase
            name: Rule2
            priority: 2
            ruleType: MatchRule
      managedRules:
        managedRuleSets:
          - exclusions:
              - matchVariable: RequestHeaderNames
                selector: User-Agent
                selectorMatchOperator: Equals
            ruleGroupOverrides:
              - exclusions:
                  - matchVariable: RequestCookieNames
                    selector: token
                    selectorMatchOperator: StartsWith
                ruleGroupName: SQLI
                rules:
                  - action: Redirect
                    enabledState: Enabled
                    exclusions:
                      - matchVariable: QueryStringArgNames
                        selector: query
                        selectorMatchOperator: Equals
                    ruleId: '942100'
                  - enabledState: Disabled
                    ruleId: '942110'
            ruleSetAction: Block
            ruleSetType: DefaultRuleSet
            ruleSetVersion: '1.0'
      policyName: Policy1
      policySettings:
        customBlockResponseBody: PGh0bWw+CjxoZWFkZXI+PHRpdGxlPkhlbGxvPC90aXRsZT48L2hlYWRlcj4KPGJvZHk+CkhlbGxvIHdvcmxkCjwvYm9keT4KPC9odG1sPg==
        customBlockResponseStatusCode: 499
        enabledState: Enabled
        mode: Prevention
        redirectUrl: http://www.bing.com
        requestBodyCheck: Disabled
      resourceGroupName: rg1
      sku:
        name: Classic_AzureFrontDoor

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:Policy Policy1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/FrontDoorWebApplicationFirewallPolicies/Policy1 
```
