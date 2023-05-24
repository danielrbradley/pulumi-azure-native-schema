The details of the snoozed or dismissed rule; for example, the duration, name, and GUID associated with the rule.
API Version: 2022-10-01.
Previous API Version: 2020-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateSuppression
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var suppression = new AzureNative.Advisor.Suppression("suppression", new()
    {
        Name = "suppressionName1",
        RecommendationId = "recommendationId",
        ResourceUri = "resourceUri",
        Ttl = "07:00:00:00",
    });

});


```

```go
package main

import (
	advisor "github.com/pulumi/pulumi-azure-native-sdk/advisor"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := advisor.NewSuppression(ctx, "suppression", &advisor.SuppressionArgs{
			Name:             pulumi.String("suppressionName1"),
			RecommendationId: pulumi.String("recommendationId"),
			ResourceUri:      pulumi.String("resourceUri"),
			Ttl:              pulumi.String("07:00:00:00"),
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
import com.pulumi.azurenative.advisor.Suppression;
import com.pulumi.azurenative.advisor.SuppressionArgs;
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
        var suppression = new Suppression("suppression", SuppressionArgs.builder()        
            .name("suppressionName1")
            .recommendationId("recommendationId")
            .resourceUri("resourceUri")
            .ttl("07:00:00:00")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const suppression = new azure_native.advisor.Suppression("suppression", {
    name: "suppressionName1",
    recommendationId: "recommendationId",
    resourceUri: "resourceUri",
    ttl: "07:00:00:00",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

suppression = azure_native.advisor.Suppression("suppression",
    name="suppressionName1",
    recommendation_id="recommendationId",
    resource_uri="resourceUri",
    ttl="07:00:00:00")

```

```yaml
resources:
  suppression:
    type: azure-native:advisor:Suppression
    properties:
      name: suppressionName1
      recommendationId: recommendationId
      resourceUri: resourceUri
      ttl: 07:00:00:00

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:advisor:Suppression suppressionName1 /resourceUri/providers/Microsoft.Advisor/recommendations/recommendationId/suppressions/suppressionName1 
```
