Domain Topic.
API Version: 2022-06-15.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DomainTopics_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var domainTopic = new AzureNative.EventGrid.DomainTopic("domainTopic", new()
    {
        DomainName = "exampledomain1",
        DomainTopicName = "exampledomaintopic1",
        ResourceGroupName = "examplerg",
    });

});


```

```go
package main

import (
	eventgrid "github.com/pulumi/pulumi-azure-native-sdk/eventgrid"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := eventgrid.NewDomainTopic(ctx, "domainTopic", &eventgrid.DomainTopicArgs{
			DomainName:        pulumi.String("exampledomain1"),
			DomainTopicName:   pulumi.String("exampledomaintopic1"),
			ResourceGroupName: pulumi.String("examplerg"),
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
import com.pulumi.azurenative.eventgrid.DomainTopic;
import com.pulumi.azurenative.eventgrid.DomainTopicArgs;
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
        var domainTopic = new DomainTopic("domainTopic", DomainTopicArgs.builder()        
            .domainName("exampledomain1")
            .domainTopicName("exampledomaintopic1")
            .resourceGroupName("examplerg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const domainTopic = new azure_native.eventgrid.DomainTopic("domainTopic", {
    domainName: "exampledomain1",
    domainTopicName: "exampledomaintopic1",
    resourceGroupName: "examplerg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

domain_topic = azure_native.eventgrid.DomainTopic("domainTopic",
    domain_name="exampledomain1",
    domain_topic_name="exampledomaintopic1",
    resource_group_name="examplerg")

```

```yaml
resources:
  domainTopic:
    type: azure-native:eventgrid:DomainTopic
    properties:
      domainName: exampledomain1
      domainTopicName: exampledomaintopic1
      resourceGroupName: examplerg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventgrid:DomainTopic exampledomaintopic1 /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/domains/exampledomain1/topics/exampledomaintopic1 
```
