Defines web application firewall policy for Azure CDN.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var policy = new AzureNative.Cdn.Policy("policy", new()
    {
        CustomRules = new AzureNative.Cdn.Inputs.CustomRuleListArgs
        {
            Rules = new[]
            {
                new AzureNative.Cdn.Inputs.CustomRuleArgs
                {
                    Action = "Block",
                    EnabledState = "Enabled",
                    MatchConditions = new[]
                    {
                        new AzureNative.Cdn.Inputs.MatchConditionArgs
                        {
                            MatchValue = new[]
                            {
                                "CH",
                            },
                            MatchVariable = "RemoteAddr",
                            NegateCondition = false,
                            Operator = "GeoMatch",
                            Transforms = new[] {},
                        },
                        new AzureNative.Cdn.Inputs.MatchConditionArgs
                        {
                            MatchValue = new[]
                            {
                                "windows",
                            },
                            MatchVariable = "RequestHeader",
                            NegateCondition = false,
                            Operator = "Contains",
                            Selector = "UserAgent",
                            Transforms = new[] {},
                        },
                        new AzureNative.Cdn.Inputs.MatchConditionArgs
                        {
                            MatchValue = new[]
                            {
                                "<?php",
                                "?>",
                            },
                            MatchVariable = "QueryString",
                            NegateCondition = false,
                            Operator = "Contains",
                            Selector = "search",
                            Transforms = new[]
                            {
                                "UrlDecode",
                                "Lowercase",
                            },
                        },
                    },
                    Name = "CustomRule1",
                    Priority = 2,
                },
            },
        },
        Location = "WestUs",
        ManagedRules = new AzureNative.Cdn.Inputs.ManagedRuleSetListArgs
        {
            ManagedRuleSets = new[]
            {
                new AzureNative.Cdn.Inputs.ManagedRuleSetArgs
                {
                    RuleGroupOverrides = new[]
                    {
                        new AzureNative.Cdn.Inputs.ManagedRuleGroupOverrideArgs
                        {
                            RuleGroupName = "Group1",
                            Rules = new[]
                            {
                                new AzureNative.Cdn.Inputs.ManagedRuleOverrideArgs
                                {
                                    Action = "Redirect",
                                    EnabledState = "Enabled",
                                    RuleId = "GROUP1-0001",
                                },
                                new AzureNative.Cdn.Inputs.ManagedRuleOverrideArgs
                                {
                                    EnabledState = "Disabled",
                                    RuleId = "GROUP1-0002",
                                },
                            },
                        },
                    },
                    RuleSetType = "DefaultRuleSet",
                    RuleSetVersion = "preview-1.0",
                },
            },
        },
        PolicyName = "MicrosoftCdnWafPolicy",
        PolicySettings = new AzureNative.Cdn.Inputs.PolicySettingsArgs
        {
            DefaultCustomBlockResponseBody = "PGh0bWw+CjxoZWFkZXI+PHRpdGxlPkhlbGxvPC90aXRsZT48L2hlYWRlcj4KPGJvZHk+CkhlbGxvIHdvcmxkCjwvYm9keT4KPC9odG1sPg==",
            DefaultCustomBlockResponseStatusCode = 200,
            DefaultRedirectUrl = "http://www.bing.com",
        },
        RateLimitRules = new AzureNative.Cdn.Inputs.RateLimitRuleListArgs
        {
            Rules = new[]
            {
                new AzureNative.Cdn.Inputs.RateLimitRuleArgs
                {
                    Action = "Block",
                    EnabledState = "Enabled",
                    MatchConditions = new[]
                    {
                        new AzureNative.Cdn.Inputs.MatchConditionArgs
                        {
                            MatchValue = new[]
                            {
                                "192.168.1.0/24",
                                "10.0.0.0/24",
                            },
                            MatchVariable = "RemoteAddr",
                            NegateCondition = false,
                            Operator = "IPMatch",
                            Transforms = new[] {},
                        },
                    },
                    Name = "RateLimitRule1",
                    Priority = 1,
                    RateLimitDurationInMinutes = 0,
                    RateLimitThreshold = 1000,
                },
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Cdn.Inputs.SkuArgs
        {
            Name = "Standard_Microsoft",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.cdn.Policy;
import com.pulumi.azurenative.cdn.PolicyArgs;
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
            .customRules(Map.of("rules", Map.ofEntries(
                Map.entry("action", "Block"),
                Map.entry("enabledState", "Enabled"),
                Map.entry("matchConditions",                 
                    Map.ofEntries(
                        Map.entry("matchValue", "CH"),
                        Map.entry("matchVariable", "RemoteAddr"),
                        Map.entry("negateCondition", false),
                        Map.entry("operator", "GeoMatch"),
                        Map.entry("transforms", )
                    ),
                    Map.ofEntries(
                        Map.entry("matchValue", "windows"),
                        Map.entry("matchVariable", "RequestHeader"),
                        Map.entry("negateCondition", false),
                        Map.entry("operator", "Contains"),
                        Map.entry("selector", "UserAgent"),
                        Map.entry("transforms", )
                    ),
                    Map.ofEntries(
                        Map.entry("matchValue",                         
                            "<?php",
                            "?>"),
                        Map.entry("matchVariable", "QueryString"),
                        Map.entry("negateCondition", false),
                        Map.entry("operator", "Contains"),
                        Map.entry("selector", "search"),
                        Map.entry("transforms",                         
                            "UrlDecode",
                            "Lowercase")
                    )),
                Map.entry("name", "CustomRule1"),
                Map.entry("priority", 2)
            )))
            .location("WestUs")
            .managedRules(Map.of("managedRuleSets", Map.ofEntries(
                Map.entry("ruleGroupOverrides", Map.ofEntries(
                    Map.entry("ruleGroupName", "Group1"),
                    Map.entry("rules",                     
                        Map.ofEntries(
                            Map.entry("action", "Redirect"),
                            Map.entry("enabledState", "Enabled"),
                            Map.entry("ruleId", "GROUP1-0001")
                        ),
                        Map.ofEntries(
                            Map.entry("enabledState", "Disabled"),
                            Map.entry("ruleId", "GROUP1-0002")
                        ))
                )),
                Map.entry("ruleSetType", "DefaultRuleSet"),
                Map.entry("ruleSetVersion", "preview-1.0")
            )))
            .policyName("MicrosoftCdnWafPolicy")
            .policySettings(Map.ofEntries(
                Map.entry("defaultCustomBlockResponseBody", "PGh0bWw+CjxoZWFkZXI+PHRpdGxlPkhlbGxvPC90aXRsZT48L2hlYWRlcj4KPGJvZHk+CkhlbGxvIHdvcmxkCjwvYm9keT4KPC9odG1sPg=="),
                Map.entry("defaultCustomBlockResponseStatusCode", 200),
                Map.entry("defaultRedirectUrl", "http://www.bing.com")
            ))
            .rateLimitRules(Map.of("rules", Map.ofEntries(
                Map.entry("action", "Block"),
                Map.entry("enabledState", "Enabled"),
                Map.entry("matchConditions", Map.ofEntries(
                    Map.entry("matchValue",                     
                        "192.168.1.0/24",
                        "10.0.0.0/24"),
                    Map.entry("matchVariable", "RemoteAddr"),
                    Map.entry("negateCondition", false),
                    Map.entry("operator", "IPMatch"),
                    Map.entry("transforms", )
                )),
                Map.entry("name", "RateLimitRule1"),
                Map.entry("priority", 1),
                Map.entry("rateLimitDurationInMinutes", 0),
                Map.entry("rateLimitThreshold", 1000)
            )))
            .resourceGroupName("rg1")
            .sku(Map.of("name", "Standard_Microsoft"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policy = new azure_native.cdn.Policy("policy", {
    customRules: {
        rules: [{
            action: "Block",
            enabledState: "Enabled",
            matchConditions: [
                {
                    matchValue: ["CH"],
                    matchVariable: "RemoteAddr",
                    negateCondition: false,
                    operator: "GeoMatch",
                    transforms: [],
                },
                {
                    matchValue: ["windows"],
                    matchVariable: "RequestHeader",
                    negateCondition: false,
                    operator: "Contains",
                    selector: "UserAgent",
                    transforms: [],
                },
                {
                    matchValue: [
                        "<?php",
                        "?>",
                    ],
                    matchVariable: "QueryString",
                    negateCondition: false,
                    operator: "Contains",
                    selector: "search",
                    transforms: [
                        "UrlDecode",
                        "Lowercase",
                    ],
                },
            ],
            name: "CustomRule1",
            priority: 2,
        }],
    },
    location: "WestUs",
    managedRules: {
        managedRuleSets: [{
            ruleGroupOverrides: [{
                ruleGroupName: "Group1",
                rules: [
                    {
                        action: "Redirect",
                        enabledState: "Enabled",
                        ruleId: "GROUP1-0001",
                    },
                    {
                        enabledState: "Disabled",
                        ruleId: "GROUP1-0002",
                    },
                ],
            }],
            ruleSetType: "DefaultRuleSet",
            ruleSetVersion: "preview-1.0",
        }],
    },
    policyName: "MicrosoftCdnWafPolicy",
    policySettings: {
        defaultCustomBlockResponseBody: "PGh0bWw+CjxoZWFkZXI+PHRpdGxlPkhlbGxvPC90aXRsZT48L2hlYWRlcj4KPGJvZHk+CkhlbGxvIHdvcmxkCjwvYm9keT4KPC9odG1sPg==",
        defaultCustomBlockResponseStatusCode: 200,
        defaultRedirectUrl: "http://www.bing.com",
    },
    rateLimitRules: {
        rules: [{
            action: "Block",
            enabledState: "Enabled",
            matchConditions: [{
                matchValue: [
                    "192.168.1.0/24",
                    "10.0.0.0/24",
                ],
                matchVariable: "RemoteAddr",
                negateCondition: false,
                operator: "IPMatch",
                transforms: [],
            }],
            name: "RateLimitRule1",
            priority: 1,
            rateLimitDurationInMinutes: 0,
            rateLimitThreshold: 1000,
        }],
    },
    resourceGroupName: "rg1",
    sku: {
        name: "Standard_Microsoft",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy = azure_native.cdn.Policy("policy",
    custom_rules=azure_native.cdn.CustomRuleListResponseArgs(
        rules=[{
            "action": "Block",
            "enabledState": "Enabled",
            "matchConditions": [
                azure_native.cdn.MatchConditionArgs(
                    match_value=["CH"],
                    match_variable="RemoteAddr",
                    negate_condition=False,
                    operator="GeoMatch",
                    transforms=[],
                ),
                azure_native.cdn.MatchConditionArgs(
                    match_value=["windows"],
                    match_variable="RequestHeader",
                    negate_condition=False,
                    operator="Contains",
                    selector="UserAgent",
                    transforms=[],
                ),
                azure_native.cdn.MatchConditionArgs(
                    match_value=[
                        "<?php",
                        "?>",
                    ],
                    match_variable="QueryString",
                    negate_condition=False,
                    operator="Contains",
                    selector="search",
                    transforms=[
                        "UrlDecode",
                        "Lowercase",
                    ],
                ),
            ],
            "name": "CustomRule1",
            "priority": 2,
        }],
    ),
    location="WestUs",
    managed_rules=azure_native.cdn.ManagedRuleSetListResponseArgs(
        managed_rule_sets=[{
            "ruleGroupOverrides": [{
                "ruleGroupName": "Group1",
                "rules": [
                    azure_native.cdn.ManagedRuleOverrideArgs(
                        action="Redirect",
                        enabled_state="Enabled",
                        rule_id="GROUP1-0001",
                    ),
                    azure_native.cdn.ManagedRuleOverrideArgs(
                        enabled_state="Disabled",
                        rule_id="GROUP1-0002",
                    ),
                ],
            }],
            "ruleSetType": "DefaultRuleSet",
            "ruleSetVersion": "preview-1.0",
        }],
    ),
    policy_name="MicrosoftCdnWafPolicy",
    policy_settings=azure_native.cdn.PolicySettingsArgs(
        default_custom_block_response_body="PGh0bWw+CjxoZWFkZXI+PHRpdGxlPkhlbGxvPC90aXRsZT48L2hlYWRlcj4KPGJvZHk+CkhlbGxvIHdvcmxkCjwvYm9keT4KPC9odG1sPg==",
        default_custom_block_response_status_code=200,
        default_redirect_url="http://www.bing.com",
    ),
    rate_limit_rules=azure_native.cdn.RateLimitRuleListResponseArgs(
        rules=[{
            "action": "Block",
            "enabledState": "Enabled",
            "matchConditions": [azure_native.cdn.MatchConditionArgs(
                match_value=[
                    "192.168.1.0/24",
                    "10.0.0.0/24",
                ],
                match_variable="RemoteAddr",
                negate_condition=False,
                operator="IPMatch",
                transforms=[],
            )],
            "name": "RateLimitRule1",
            "priority": 1,
            "rateLimitDurationInMinutes": 0,
            "rateLimitThreshold": 1000,
        }],
    ),
    resource_group_name="rg1",
    sku=azure_native.cdn.SkuArgs(
        name="Standard_Microsoft",
    ))

```

```yaml
resources:
  policy:
    type: azure-native:cdn:Policy
    properties:
      customRules:
        rules:
          - action: Block
            enabledState: Enabled
            matchConditions:
              - matchValue:
                  - CH
                matchVariable: RemoteAddr
                negateCondition: false
                operator: GeoMatch
                transforms: []
              - matchValue:
                  - windows
                matchVariable: RequestHeader
                negateCondition: false
                operator: Contains
                selector: UserAgent
                transforms: []
              - matchValue:
                  - <?php
                  - ?>
                matchVariable: QueryString
                negateCondition: false
                operator: Contains
                selector: search
                transforms:
                  - UrlDecode
                  - Lowercase
            name: CustomRule1
            priority: 2
      location: WestUs
      managedRules:
        managedRuleSets:
          - ruleGroupOverrides:
              - ruleGroupName: Group1
                rules:
                  - action: Redirect
                    enabledState: Enabled
                    ruleId: GROUP1-0001
                  - enabledState: Disabled
                    ruleId: GROUP1-0002
            ruleSetType: DefaultRuleSet
            ruleSetVersion: preview-1.0
      policyName: MicrosoftCdnWafPolicy
      policySettings:
        defaultCustomBlockResponseBody: PGh0bWw+CjxoZWFkZXI+PHRpdGxlPkhlbGxvPC90aXRsZT48L2hlYWRlcj4KPGJvZHk+CkhlbGxvIHdvcmxkCjwvYm9keT4KPC9odG1sPg==
        defaultCustomBlockResponseStatusCode: 200
        defaultRedirectUrl: http://www.bing.com
      rateLimitRules:
        rules:
          - action: Block
            enabledState: Enabled
            matchConditions:
              - matchValue:
                  - 192.168.1.0/24
                  - 10.0.0.0/24
                matchVariable: RemoteAddr
                negateCondition: false
                operator: IPMatch
                transforms: []
            name: RateLimitRule1
            priority: 1
            rateLimitDurationInMinutes: 0
            rateLimitThreshold: 1000
      resourceGroupName: rg1
      sku:
        name: Standard_Microsoft

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cdn:Policy MicrosoftCdnWafPolicy /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cdn/CdnWebApplicationFirewallPolicies/MicrosoftCdnWafPolicy 
```
