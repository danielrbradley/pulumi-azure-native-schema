An Azure resource which represents access to a suite of Maps REST APIs.
API Version: 2021-02-01.
Previous API Version: 2018-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Gen1 Account
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.Maps.Account("account", new()
    {
        AccountName = "myMapsAccount",
        Kind = "Gen1",
        Location = "global",
        Properties = new AzureNative.Maps.Inputs.MapsAccountPropertiesArgs
        {
            DisableLocalAuth = false,
        },
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Maps.Inputs.SkuArgs
        {
            Name = "S0",
        },
        Tags = 
        {
            { "test", "true" },
        },
    });

});


```

```go
package main

import (
	maps "github.com/pulumi/pulumi-azure-native-sdk/maps"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := maps.NewAccount(ctx, "account", &maps.AccountArgs{
			AccountName: pulumi.String("myMapsAccount"),
			Kind:        pulumi.String("Gen1"),
			Location:    pulumi.String("global"),
			Properties: &maps.MapsAccountPropertiesArgs{
				DisableLocalAuth: pulumi.Bool(false),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &maps.SkuArgs{
				Name: pulumi.String("S0"),
			},
			Tags: pulumi.StringMap{
				"test": pulumi.String("true"),
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
import com.pulumi.azurenative.maps.Account;
import com.pulumi.azurenative.maps.AccountArgs;
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
        var account = new Account("account", AccountArgs.builder()        
            .accountName("myMapsAccount")
            .kind("Gen1")
            .location("global")
            .properties(Map.of("disableLocalAuth", false))
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "S0"))
            .tags(Map.of("test", "true"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.maps.Account("account", {
    accountName: "myMapsAccount",
    kind: "Gen1",
    location: "global",
    properties: {
        disableLocalAuth: false,
    },
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "S0",
    },
    tags: {
        test: "true",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.maps.Account("account",
    account_name="myMapsAccount",
    kind="Gen1",
    location="global",
    properties=azure_native.maps.MapsAccountPropertiesArgs(
        disable_local_auth=False,
    ),
    resource_group_name="myResourceGroup",
    sku=azure_native.maps.SkuArgs(
        name="S0",
    ),
    tags={
        "test": "true",
    })

```

```yaml
resources:
  account:
    type: azure-native:maps:Account
    properties:
      accountName: myMapsAccount
      kind: Gen1
      location: global
      properties:
        disableLocalAuth: false
      resourceGroupName: myResourceGroup
      sku:
        name: S0
      tags:
        test: 'true'

```

{{% /example %}}
{{% example %}}
### Create Gen2 Account
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.Maps.Account("account", new()
    {
        AccountName = "myMapsAccount",
        Kind = "Gen2",
        Location = "global",
        Properties = new AzureNative.Maps.Inputs.MapsAccountPropertiesArgs
        {
            DisableLocalAuth = true,
        },
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Maps.Inputs.SkuArgs
        {
            Name = "G2",
        },
        Tags = 
        {
            { "test", "true" },
        },
    });

});


```

```go
package main

import (
	maps "github.com/pulumi/pulumi-azure-native-sdk/maps"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := maps.NewAccount(ctx, "account", &maps.AccountArgs{
			AccountName: pulumi.String("myMapsAccount"),
			Kind:        pulumi.String("Gen2"),
			Location:    pulumi.String("global"),
			Properties: &maps.MapsAccountPropertiesArgs{
				DisableLocalAuth: pulumi.Bool(true),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &maps.SkuArgs{
				Name: pulumi.String("G2"),
			},
			Tags: pulumi.StringMap{
				"test": pulumi.String("true"),
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
import com.pulumi.azurenative.maps.Account;
import com.pulumi.azurenative.maps.AccountArgs;
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
        var account = new Account("account", AccountArgs.builder()        
            .accountName("myMapsAccount")
            .kind("Gen2")
            .location("global")
            .properties(Map.of("disableLocalAuth", true))
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "G2"))
            .tags(Map.of("test", "true"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.maps.Account("account", {
    accountName: "myMapsAccount",
    kind: "Gen2",
    location: "global",
    properties: {
        disableLocalAuth: true,
    },
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "G2",
    },
    tags: {
        test: "true",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.maps.Account("account",
    account_name="myMapsAccount",
    kind="Gen2",
    location="global",
    properties=azure_native.maps.MapsAccountPropertiesArgs(
        disable_local_auth=True,
    ),
    resource_group_name="myResourceGroup",
    sku=azure_native.maps.SkuArgs(
        name="G2",
    ),
    tags={
        "test": "true",
    })

```

```yaml
resources:
  account:
    type: azure-native:maps:Account
    properties:
      accountName: myMapsAccount
      kind: Gen2
      location: global
      properties:
        disableLocalAuth: true
      resourceGroupName: myResourceGroup
      sku:
        name: G2
      tags:
        test: 'true'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:maps:Account myMapsAccount /subscriptions/21a9967a-e8a9-4656-a70b-96ff1c4d05a0/resourceGroups/myResourceGroup/providers/Microsoft.Maps/accounts/myMapsAccount 
```
