Access policies help define the authentication rules, and control access to specific video resources.
API Version: 2021-11-01-preview.
Previous API Version: 2021-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Register access policy entity.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var accessPolicy = new AzureNative.VideoAnalyzer.AccessPolicy("accessPolicy", new()
    {
        AccessPolicyName = "accessPolicyName1",
        AccountName = "testaccount2",
        Authentication = new AzureNative.VideoAnalyzer.Inputs.JwtAuthenticationArgs
        {
            Audiences = new[]
            {
                "audience1",
            },
            Claims = new[]
            {
                new AzureNative.VideoAnalyzer.Inputs.TokenClaimArgs
                {
                    Name = "claimname1",
                    Value = "claimvalue1",
                },
                new AzureNative.VideoAnalyzer.Inputs.TokenClaimArgs
                {
                    Name = "claimname2",
                    Value = "claimvalue2",
                },
            },
            Issuers = new[]
            {
                "issuer1",
                "issuer2",
            },
            Keys = 
            {
                new AzureNative.VideoAnalyzer.Inputs.RsaTokenKeyArgs
                {
                    Alg = "RS256",
                    E = "ZLFzZTY0IQ==",
                    Kid = "123",
                    N = "YmFzZTY0IQ==",
                    Type = "#Microsoft.VideoAnalyzer.RsaTokenKey",
                },
                new AzureNative.VideoAnalyzer.Inputs.EccTokenKeyArgs
                {
                    Alg = "ES256",
                    Kid = "124",
                    Type = "#Microsoft.VideoAnalyzer.EccTokenKey",
                    X = "XX==",
                    Y = "YY==",
                },
            },
            Type = "#Microsoft.VideoAnalyzer.JwtAuthentication",
        },
        ResourceGroupName = "testrg",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.videoanalyzer.AccessPolicy;
import com.pulumi.azurenative.videoanalyzer.AccessPolicyArgs;
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
        var accessPolicy = new AccessPolicy("accessPolicy", AccessPolicyArgs.builder()        
            .accessPolicyName("accessPolicyName1")
            .accountName("testaccount2")
            .authentication(Map.ofEntries(
                Map.entry("audiences", "audience1"),
                Map.entry("claims",                 
                    Map.ofEntries(
                        Map.entry("name", "claimname1"),
                        Map.entry("value", "claimvalue1")
                    ),
                    Map.ofEntries(
                        Map.entry("name", "claimname2"),
                        Map.entry("value", "claimvalue2")
                    )),
                Map.entry("issuers",                 
                    "issuer1",
                    "issuer2"),
                Map.entry("keys",                 
                    Map.ofEntries(
                        Map.entry("alg", "RS256"),
                        Map.entry("e", "ZLFzZTY0IQ=="),
                        Map.entry("kid", "123"),
                        Map.entry("n", "YmFzZTY0IQ=="),
                        Map.entry("type", "#Microsoft.VideoAnalyzer.RsaTokenKey")
                    ),
                    Map.ofEntries(
                        Map.entry("alg", "ES256"),
                        Map.entry("kid", "124"),
                        Map.entry("type", "#Microsoft.VideoAnalyzer.EccTokenKey"),
                        Map.entry("x", "XX=="),
                        Map.entry("y", "YY==")
                    )),
                Map.entry("type", "#Microsoft.VideoAnalyzer.JwtAuthentication")
            ))
            .resourceGroupName("testrg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const accessPolicy = new azure_native.videoanalyzer.AccessPolicy("accessPolicy", {
    accessPolicyName: "accessPolicyName1",
    accountName: "testaccount2",
    authentication: {
        audiences: ["audience1"],
        claims: [
            {
                name: "claimname1",
                value: "claimvalue1",
            },
            {
                name: "claimname2",
                value: "claimvalue2",
            },
        ],
        issuers: [
            "issuer1",
            "issuer2",
        ],
        keys: [
            {
                alg: "RS256",
                e: "ZLFzZTY0IQ==",
                kid: "123",
                n: "YmFzZTY0IQ==",
                type: "#Microsoft.VideoAnalyzer.RsaTokenKey",
            },
            {
                alg: "ES256",
                kid: "124",
                type: "#Microsoft.VideoAnalyzer.EccTokenKey",
                x: "XX==",
                y: "YY==",
            },
        ],
        type: "#Microsoft.VideoAnalyzer.JwtAuthentication",
    },
    resourceGroupName: "testrg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

access_policy = azure_native.videoanalyzer.AccessPolicy("accessPolicy",
    access_policy_name="accessPolicyName1",
    account_name="testaccount2",
    authentication=azure_native.videoanalyzer.JwtAuthenticationResponseArgs(
        audiences=["audience1"],
        claims=[
            azure_native.videoanalyzer.TokenClaimArgs(
                name="claimname1",
                value="claimvalue1",
            ),
            azure_native.videoanalyzer.TokenClaimArgs(
                name="claimname2",
                value="claimvalue2",
            ),
        ],
        issuers=[
            "issuer1",
            "issuer2",
        ],
        keys=[
            azure_native.videoanalyzer.RsaTokenKeyArgs(
                alg="RS256",
                e="ZLFzZTY0IQ==",
                kid="123",
                n="YmFzZTY0IQ==",
                type="#Microsoft.VideoAnalyzer.RsaTokenKey",
            ),
            azure_native.videoanalyzer.EccTokenKeyArgs(
                alg="ES256",
                kid="124",
                type="#Microsoft.VideoAnalyzer.EccTokenKey",
                x="XX==",
                y="YY==",
            ),
        ],
        type="#Microsoft.VideoAnalyzer.JwtAuthentication",
    ),
    resource_group_name="testrg")

```

```yaml
resources:
  accessPolicy:
    type: azure-native:videoanalyzer:AccessPolicy
    properties:
      accessPolicyName: accessPolicyName1
      accountName: testaccount2
      authentication:
        audiences:
          - audience1
        claims:
          - name: claimname1
            value: claimvalue1
          - name: claimname2
            value: claimvalue2
        issuers:
          - issuer1
          - issuer2
        keys:
          - alg: RS256
            e: ZLFzZTY0IQ==
            kid: '123'
            n: YmFzZTY0IQ==
            type: '#Microsoft.VideoAnalyzer.RsaTokenKey'
          - alg: ES256
            kid: '124'
            type: '#Microsoft.VideoAnalyzer.EccTokenKey'
            x: XX==
            y: YY==
        type: '#Microsoft.VideoAnalyzer.JwtAuthentication'
      resourceGroupName: testrg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:videoanalyzer:AccessPolicy accessPolicyName1 /subscriptions/591e76c3-3e97-44db-879c-3e2b12961b62/resourceGroups/testrg/providers/Microsoft.Media/videoAnalyzers/testaccount2/accesspolicies/accessPolicyName1 
```
