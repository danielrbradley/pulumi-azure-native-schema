A group created in a Migration project.
API Version: 2019-10-01.
Previous API Version: 2019-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Groups_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var @group = new AzureNative.Migrate.Group("group", new()
    {
        ETag = "\"1e000c2c-0000-0d00-0000-5cdaa4190000\"",
        GroupName = "Group2",
        ProjectName = "abgoyalWEselfhostb72bproject",
        Properties = null,
        ResourceGroupName = "abgoyal-westEurope",
    });

});


```

```go
package main

import (
	migrate "github.com/pulumi/pulumi-azure-native-sdk/migrate"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := migrate.NewGroup(ctx, "group", &migrate.GroupArgs{
			ETag:              pulumi.String("\"1e000c2c-0000-0d00-0000-5cdaa4190000\""),
			GroupName:         pulumi.String("Group2"),
			ProjectName:       pulumi.String("abgoyalWEselfhostb72bproject"),
			Properties:        nil,
			ResourceGroupName: pulumi.String("abgoyal-westEurope"),
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
import com.pulumi.azurenative.migrate.Group;
import com.pulumi.azurenative.migrate.GroupArgs;
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
        var group = new Group("group", GroupArgs.builder()        
            .eTag("\"1e000c2c-0000-0d00-0000-5cdaa4190000\"")
            .groupName("Group2")
            .projectName("abgoyalWEselfhostb72bproject")
            .properties()
            .resourceGroupName("abgoyal-westEurope")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const group = new azure_native.migrate.Group("group", {
    eTag: "\"1e000c2c-0000-0d00-0000-5cdaa4190000\"",
    groupName: "Group2",
    projectName: "abgoyalWEselfhostb72bproject",
    properties: {},
    resourceGroupName: "abgoyal-westEurope",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

group = azure_native.migrate.Group("group",
    e_tag="\"1e000c2c-0000-0d00-0000-5cdaa4190000\"",
    group_name="Group2",
    project_name="abgoyalWEselfhostb72bproject",
    properties=azure_native.migrate.GroupPropertiesArgs(),
    resource_group_name="abgoyal-westEurope")

```

```yaml
resources:
  group:
    type: azure-native:migrate:Group
    properties:
      eTag: '"1e000c2c-0000-0d00-0000-5cdaa4190000"'
      groupName: Group2
      projectName: abgoyalWEselfhostb72bproject
      properties: {}
      resourceGroupName: abgoyal-westEurope

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:migrate:Group Group2 /subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourceGroups/abgoyal-westeurope/providers/Microsoft.Migrate/assessmentprojects/abgoyalWEselfhostb72bproject/groups/Group2 
```
