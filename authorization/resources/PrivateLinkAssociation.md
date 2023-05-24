
API Version: 2020-05-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a private link association, associate scope to rmpl.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateLinkAssociation = new AzureNative.Authorization.PrivateLinkAssociation("privateLinkAssociation", new()
    {
        GroupId = "my-management-group",
        PlaId = "00000000-0000-0000-0000-000000000000",
        Properties = new AzureNative.Authorization.Inputs.PrivateLinkAssociationPropertiesArgs
        {
            PrivateLink = "00000000-0000-0000-0000-000000000000",
            PublicNetworkAccess = "Enabled",
        },
    });

});


```

```go
package main

import (
	authorization "github.com/pulumi/pulumi-azure-native-sdk/authorization"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := authorization.NewPrivateLinkAssociation(ctx, "privateLinkAssociation", &authorization.PrivateLinkAssociationArgs{
			GroupId: pulumi.String("my-management-group"),
			PlaId:   pulumi.String("00000000-0000-0000-0000-000000000000"),
			Properties: &authorization.PrivateLinkAssociationPropertiesArgs{
				PrivateLink:         pulumi.String("00000000-0000-0000-0000-000000000000"),
				PublicNetworkAccess: pulumi.String("Enabled"),
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
import com.pulumi.azurenative.authorization.PrivateLinkAssociation;
import com.pulumi.azurenative.authorization.PrivateLinkAssociationArgs;
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
        var privateLinkAssociation = new PrivateLinkAssociation("privateLinkAssociation", PrivateLinkAssociationArgs.builder()        
            .groupId("my-management-group")
            .plaId("00000000-0000-0000-0000-000000000000")
            .properties(Map.ofEntries(
                Map.entry("privateLink", "00000000-0000-0000-0000-000000000000"),
                Map.entry("publicNetworkAccess", "Enabled")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateLinkAssociation = new azure_native.authorization.PrivateLinkAssociation("privateLinkAssociation", {
    groupId: "my-management-group",
    plaId: "00000000-0000-0000-0000-000000000000",
    properties: {
        privateLink: "00000000-0000-0000-0000-000000000000",
        publicNetworkAccess: "Enabled",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_link_association = azure_native.authorization.PrivateLinkAssociation("privateLinkAssociation",
    group_id="my-management-group",
    pla_id="00000000-0000-0000-0000-000000000000",
    properties=azure_native.authorization.PrivateLinkAssociationPropertiesArgs(
        private_link="00000000-0000-0000-0000-000000000000",
        public_network_access="Enabled",
    ))

```

```yaml
resources:
  privateLinkAssociation:
    type: azure-native:authorization:PrivateLinkAssociation
    properties:
      groupId: my-management-group
      plaId: 00000000-0000-0000-0000-000000000000
      properties:
        privateLink: 00000000-0000-0000-0000-000000000000
        publicNetworkAccess: Enabled

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:authorization:PrivateLinkAssociation my-pla 00000000-0000-0000-0000-000000000000 
```
