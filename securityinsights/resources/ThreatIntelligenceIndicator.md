Threat intelligence information object.
API Version: 2023-02-01.
Previous API Version: 2019-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update a threat Intelligence indicator
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var threatIntelligenceIndicator = new AzureNative.SecurityInsights.ThreatIntelligenceIndicator("threatIntelligenceIndicator", new()
    {
        Confidence = 78,
        CreatedByRef = "contoso@contoso.com",
        Description = "debugging indicators",
        DisplayName = "new schema",
        ExternalReferences = new[] {},
        GranularMarkings = new[] {},
        KillChainPhases = new[] {},
        Kind = "indicator",
        Labels = new[] {},
        Modified = "",
        Name = "d9cd6f0b-96b9-3984-17cd-a779d1e15a93",
        Pattern = "[url:value = 'https://www.contoso.com']",
        PatternType = "url",
        ResourceGroupName = "myRg",
        Revoked = false,
        Source = "Azure Sentinel",
        ThreatIntelligenceTags = new[]
        {
            "new schema",
        },
        ThreatTypes = new[]
        {
            "compromised",
        },
        ValidFrom = "2020-04-15T17:44:00.114052Z",
        ValidUntil = "",
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
		_, err := securityinsights.NewThreatIntelligenceIndicator(ctx, "threatIntelligenceIndicator", &securityinsights.ThreatIntelligenceIndicatorArgs{
			Confidence:         pulumi.Int(78),
			CreatedByRef:       pulumi.String("contoso@contoso.com"),
			Description:        pulumi.String("debugging indicators"),
			DisplayName:        pulumi.String("new schema"),
			ExternalReferences: securityinsights.ThreatIntelligenceExternalReferenceArray{},
			GranularMarkings:   securityinsights.ThreatIntelligenceGranularMarkingModelArray{},
			KillChainPhases:    securityinsights.ThreatIntelligenceKillChainPhaseArray{},
			Kind:               pulumi.String("indicator"),
			Labels:             pulumi.StringArray{},
			Modified:           pulumi.String(""),
			Name:               pulumi.String("d9cd6f0b-96b9-3984-17cd-a779d1e15a93"),
			Pattern:            pulumi.String("[url:value = 'https://www.contoso.com']"),
			PatternType:        pulumi.String("url"),
			ResourceGroupName:  pulumi.String("myRg"),
			Revoked:            pulumi.Bool(false),
			Source:             pulumi.String("Azure Sentinel"),
			ThreatIntelligenceTags: pulumi.StringArray{
				pulumi.String("new schema"),
			},
			ThreatTypes: pulumi.StringArray{
				pulumi.String("compromised"),
			},
			ValidFrom:     pulumi.String("2020-04-15T17:44:00.114052Z"),
			ValidUntil:    pulumi.String(""),
			WorkspaceName: pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.ThreatIntelligenceIndicator;
import com.pulumi.azurenative.securityinsights.ThreatIntelligenceIndicatorArgs;
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
        var threatIntelligenceIndicator = new ThreatIntelligenceIndicator("threatIntelligenceIndicator", ThreatIntelligenceIndicatorArgs.builder()        
            .confidence(78)
            .createdByRef("contoso@contoso.com")
            .description("debugging indicators")
            .displayName("new schema")
            .externalReferences()
            .granularMarkings()
            .killChainPhases()
            .kind("indicator")
            .labels()
            .modified("")
            .name("d9cd6f0b-96b9-3984-17cd-a779d1e15a93")
            .pattern("[url:value = 'https://www.contoso.com']")
            .patternType("url")
            .resourceGroupName("myRg")
            .revoked(false)
            .source("Azure Sentinel")
            .threatIntelligenceTags("new schema")
            .threatTypes("compromised")
            .validFrom("2020-04-15T17:44:00.114052Z")
            .validUntil("")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const threatIntelligenceIndicator = new azure_native.securityinsights.ThreatIntelligenceIndicator("threatIntelligenceIndicator", {
    confidence: 78,
    createdByRef: "contoso@contoso.com",
    description: "debugging indicators",
    displayName: "new schema",
    externalReferences: [],
    granularMarkings: [],
    killChainPhases: [],
    kind: "indicator",
    labels: [],
    modified: "",
    name: "d9cd6f0b-96b9-3984-17cd-a779d1e15a93",
    pattern: "[url:value = 'https://www.contoso.com']",
    patternType: "url",
    resourceGroupName: "myRg",
    revoked: false,
    source: "Azure Sentinel",
    threatIntelligenceTags: ["new schema"],
    threatTypes: ["compromised"],
    validFrom: "2020-04-15T17:44:00.114052Z",
    validUntil: "",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

threat_intelligence_indicator = azure_native.securityinsights.ThreatIntelligenceIndicator("threatIntelligenceIndicator",
    confidence=78,
    created_by_ref="contoso@contoso.com",
    description="debugging indicators",
    display_name="new schema",
    external_references=[],
    granular_markings=[],
    kill_chain_phases=[],
    kind="indicator",
    labels=[],
    modified="",
    name="d9cd6f0b-96b9-3984-17cd-a779d1e15a93",
    pattern="[url:value = 'https://www.contoso.com']",
    pattern_type="url",
    resource_group_name="myRg",
    revoked=False,
    source="Azure Sentinel",
    threat_intelligence_tags=["new schema"],
    threat_types=["compromised"],
    valid_from="2020-04-15T17:44:00.114052Z",
    valid_until="",
    workspace_name="myWorkspace")

```

```yaml
resources:
  threatIntelligenceIndicator:
    type: azure-native:securityinsights:ThreatIntelligenceIndicator
    properties:
      confidence: 78
      createdByRef: contoso@contoso.com
      description: debugging indicators
      displayName: new schema
      externalReferences: []
      granularMarkings: []
      killChainPhases: []
      kind: indicator
      labels: []
      modified:
      name: d9cd6f0b-96b9-3984-17cd-a779d1e15a93
      pattern: '[url:value = ''https://www.contoso.com'']'
      patternType: url
      resourceGroupName: myRg
      revoked: false
      source: Azure Sentinel
      threatIntelligenceTags:
        - new schema
      threatTypes:
        - compromised
      validFrom: 2020-04-15T17:44:00.114052Z
      validUntil:
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:ThreatIntelligenceIndicator 180105c7-a28d-b1a2-4a78-234f6ec80fd6 /subscriptions/bd794837-4d29-4647-9105-6339bfdb4e6a/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/ThreatIntelligence/180105c7-a28d-b1a2-4a78-234f6ec80fd6 
```
