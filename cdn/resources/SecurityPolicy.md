SecurityPolicy association for AzureFrontDoor profile
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SecurityPolicies_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var securityPolicy = new AzureNative.Cdn.SecurityPolicy("securityPolicy", new()
    {
        Parameters = new AzureNative.Cdn.Inputs.SecurityPolicyWebApplicationFirewallParametersArgs
        {
            Associations = new[]
            {
                new AzureNative.Cdn.Inputs.SecurityPolicyWebApplicationFirewallAssociationArgs
                {
                    Domains = new[]
                    {
                        new AzureNative.Cdn.Inputs.ActivatedResourceReferenceArgs
                        {
                            Id = "/subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/customdomains/testdomain1",
                        },
                        new AzureNative.Cdn.Inputs.ActivatedResourceReferenceArgs
                        {
                            Id = "/subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/customdomains/testdomain2",
                        },
                    },
                    PatternsToMatch = new[]
                    {
                        "/*",
                    },
                },
            },
            Type = "WebApplicationFirewall",
            WafPolicy = new AzureNative.Cdn.Inputs.ResourceReferenceArgs
            {
                Id = "/subscriptions/subid/resourcegroups/RG/providers/Microsoft.Network/frontdoorwebapplicationfirewallpolicies/wafTest",
            },
        },
        ProfileName = "profile1",
        ResourceGroupName = "RG",
        SecurityPolicyName = "securityPolicy1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.cdn.SecurityPolicy;
import com.pulumi.azurenative.cdn.SecurityPolicyArgs;
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
        var securityPolicy = new SecurityPolicy("securityPolicy", SecurityPolicyArgs.builder()        
            .parameters(Map.ofEntries(
                Map.entry("associations", Map.ofEntries(
                    Map.entry("domains",                     
                        Map.of("id", "/subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/customdomains/testdomain1"),
                        Map.of("id", "/subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/customdomains/testdomain2")),
                    Map.entry("patternsToMatch", "/*")
                )),
                Map.entry("type", "WebApplicationFirewall"),
                Map.entry("wafPolicy", Map.of("id", "/subscriptions/subid/resourcegroups/RG/providers/Microsoft.Network/frontdoorwebapplicationfirewallpolicies/wafTest"))
            ))
            .profileName("profile1")
            .resourceGroupName("RG")
            .securityPolicyName("securityPolicy1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const securityPolicy = new azure_native.cdn.SecurityPolicy("securityPolicy", {
    parameters: {
        associations: [{
            domains: [
                {
                    id: "/subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/customdomains/testdomain1",
                },
                {
                    id: "/subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/customdomains/testdomain2",
                },
            ],
            patternsToMatch: ["/*"],
        }],
        type: "WebApplicationFirewall",
        wafPolicy: {
            id: "/subscriptions/subid/resourcegroups/RG/providers/Microsoft.Network/frontdoorwebapplicationfirewallpolicies/wafTest",
        },
    },
    profileName: "profile1",
    resourceGroupName: "RG",
    securityPolicyName: "securityPolicy1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

security_policy = azure_native.cdn.SecurityPolicy("securityPolicy",
    parameters=azure_native.cdn.SecurityPolicyWebApplicationFirewallParametersResponseArgs(
        associations=[{
            "domains": [
                azure_native.cdn.ActivatedResourceReferenceArgs(
                    id="/subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/customdomains/testdomain1",
                ),
                azure_native.cdn.ActivatedResourceReferenceArgs(
                    id="/subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/customdomains/testdomain2",
                ),
            ],
            "patternsToMatch": ["/*"],
        }],
        type="WebApplicationFirewall",
        waf_policy=azure_native.cdn.ResourceReferenceArgs(
            id="/subscriptions/subid/resourcegroups/RG/providers/Microsoft.Network/frontdoorwebapplicationfirewallpolicies/wafTest",
        ),
    ),
    profile_name="profile1",
    resource_group_name="RG",
    security_policy_name="securityPolicy1")

```

```yaml
resources:
  securityPolicy:
    type: azure-native:cdn:SecurityPolicy
    properties:
      parameters:
        associations:
          - domains:
              - id: /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/customdomains/testdomain1
              - id: /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/customdomains/testdomain2
            patternsToMatch:
              - /*
        type: WebApplicationFirewall
        wafPolicy:
          id: /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Network/frontdoorwebapplicationfirewallpolicies/wafTest
      profileName: profile1
      resourceGroupName: RG
      securityPolicyName: securityPolicy1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cdn:SecurityPolicy securityPolicy1 /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/securitypolicies/securityPolicy1 
```
