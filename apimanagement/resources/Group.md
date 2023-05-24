Contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateGroup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var @group = new AzureNative.ApiManagement.Group("group", new()
    {
        DisplayName = "temp group",
        GroupId = "tempgroup",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewGroup(ctx, "group", &apimanagement.GroupArgs{
			DisplayName:       pulumi.String("temp group"),
			GroupId:           pulumi.String("tempgroup"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
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
import com.pulumi.azurenative.apimanagement.Group;
import com.pulumi.azurenative.apimanagement.GroupArgs;
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
            .displayName("temp group")
            .groupId("tempgroup")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const group = new azure_native.apimanagement.Group("group", {
    displayName: "temp group",
    groupId: "tempgroup",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

group = azure_native.apimanagement.Group("group",
    display_name="temp group",
    group_id="tempgroup",
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  group:
    type: azure-native:apimanagement:Group
    properties:
      displayName: temp group
      groupId: tempgroup
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateGroupExternal
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var @group = new AzureNative.ApiManagement.Group("group", new()
    {
        Description = "new group to test",
        DisplayName = "NewGroup (samiraad.onmicrosoft.com)",
        ExternalId = "aad://samiraad.onmicrosoft.com/groups/83cf2753-5831-4675-bc0e-2f8dc067c58d",
        GroupId = "aadGroup",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Type = AzureNative.ApiManagement.GroupType.External,
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewGroup(ctx, "group", &apimanagement.GroupArgs{
			Description:       pulumi.String("new group to test"),
			DisplayName:       pulumi.String("NewGroup (samiraad.onmicrosoft.com)"),
			ExternalId:        pulumi.String("aad://samiraad.onmicrosoft.com/groups/83cf2753-5831-4675-bc0e-2f8dc067c58d"),
			GroupId:           pulumi.String("aadGroup"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Type:              apimanagement.GroupTypeExternal,
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
import com.pulumi.azurenative.apimanagement.Group;
import com.pulumi.azurenative.apimanagement.GroupArgs;
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
            .description("new group to test")
            .displayName("NewGroup (samiraad.onmicrosoft.com)")
            .externalId("aad://samiraad.onmicrosoft.com/groups/83cf2753-5831-4675-bc0e-2f8dc067c58d")
            .groupId("aadGroup")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .type("external")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const group = new azure_native.apimanagement.Group("group", {
    description: "new group to test",
    displayName: "NewGroup (samiraad.onmicrosoft.com)",
    externalId: "aad://samiraad.onmicrosoft.com/groups/83cf2753-5831-4675-bc0e-2f8dc067c58d",
    groupId: "aadGroup",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    type: azure_native.apimanagement.GroupType.External,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

group = azure_native.apimanagement.Group("group",
    description="new group to test",
    display_name="NewGroup (samiraad.onmicrosoft.com)",
    external_id="aad://samiraad.onmicrosoft.com/groups/83cf2753-5831-4675-bc0e-2f8dc067c58d",
    group_id="aadGroup",
    resource_group_name="rg1",
    service_name="apimService1",
    type=azure_native.apimanagement.GroupType.EXTERNAL)

```

```yaml
resources:
  group:
    type: azure-native:apimanagement:Group
    properties:
      description: new group to test
      displayName: NewGroup (samiraad.onmicrosoft.com)
      externalId: aad://samiraad.onmicrosoft.com/groups/83cf2753-5831-4675-bc0e-2f8dc067c58d
      groupId: aadGroup
      resourceGroupName: rg1
      serviceName: apimService1
      type: external

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:Group aadGroup /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/groups/aadGroup 
```
