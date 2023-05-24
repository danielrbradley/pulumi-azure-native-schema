The configuration store along with all resource properties. The Configuration Store will have all information to begin utilizing it.
API Version: 2022-05-01.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ConfigurationStores_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var configurationStore = new AzureNative.AppConfiguration.ConfigurationStore("configurationStore", new()
    {
        ConfigStoreName = "contoso",
        Location = "westus",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.AppConfiguration.Inputs.SkuArgs
        {
            Name = "Standard",
        },
        Tags = 
        {
            { "myTag", "myTagValue" },
        },
    });

});


```

```go
package main

import (
	appconfiguration "github.com/pulumi/pulumi-azure-native-sdk/appconfiguration"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appconfiguration.NewConfigurationStore(ctx, "configurationStore", &appconfiguration.ConfigurationStoreArgs{
			ConfigStoreName:   pulumi.String("contoso"),
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &appconfiguration.SkuArgs{
				Name: pulumi.String("Standard"),
			},
			Tags: pulumi.StringMap{
				"myTag": pulumi.String("myTagValue"),
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
import com.pulumi.azurenative.appconfiguration.ConfigurationStore;
import com.pulumi.azurenative.appconfiguration.ConfigurationStoreArgs;
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
        var configurationStore = new ConfigurationStore("configurationStore", ConfigurationStoreArgs.builder()        
            .configStoreName("contoso")
            .location("westus")
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "Standard"))
            .tags(Map.of("myTag", "myTagValue"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const configurationStore = new azure_native.appconfiguration.ConfigurationStore("configurationStore", {
    configStoreName: "contoso",
    location: "westus",
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "Standard",
    },
    tags: {
        myTag: "myTagValue",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

configuration_store = azure_native.appconfiguration.ConfigurationStore("configurationStore",
    config_store_name="contoso",
    location="westus",
    resource_group_name="myResourceGroup",
    sku=azure_native.appconfiguration.SkuArgs(
        name="Standard",
    ),
    tags={
        "myTag": "myTagValue",
    })

```

```yaml
resources:
  configurationStore:
    type: azure-native:appconfiguration:ConfigurationStore
    properties:
      configStoreName: contoso
      location: westus
      resourceGroupName: myResourceGroup
      sku:
        name: Standard
      tags:
        myTag: myTagValue

```

{{% /example %}}
{{% example %}}
### ConfigurationStores_Create_With_Local_Auth_Disabled
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var configurationStore = new AzureNative.AppConfiguration.ConfigurationStore("configurationStore", new()
    {
        ConfigStoreName = "contoso",
        DisableLocalAuth = true,
        Location = "westus",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.AppConfiguration.Inputs.SkuArgs
        {
            Name = "Standard",
        },
    });

});


```

```go
package main

import (
	appconfiguration "github.com/pulumi/pulumi-azure-native-sdk/appconfiguration"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appconfiguration.NewConfigurationStore(ctx, "configurationStore", &appconfiguration.ConfigurationStoreArgs{
			ConfigStoreName:   pulumi.String("contoso"),
			DisableLocalAuth:  pulumi.Bool(true),
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &appconfiguration.SkuArgs{
				Name: pulumi.String("Standard"),
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
import com.pulumi.azurenative.appconfiguration.ConfigurationStore;
import com.pulumi.azurenative.appconfiguration.ConfigurationStoreArgs;
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
        var configurationStore = new ConfigurationStore("configurationStore", ConfigurationStoreArgs.builder()        
            .configStoreName("contoso")
            .disableLocalAuth(true)
            .location("westus")
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "Standard"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const configurationStore = new azure_native.appconfiguration.ConfigurationStore("configurationStore", {
    configStoreName: "contoso",
    disableLocalAuth: true,
    location: "westus",
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "Standard",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

configuration_store = azure_native.appconfiguration.ConfigurationStore("configurationStore",
    config_store_name="contoso",
    disable_local_auth=True,
    location="westus",
    resource_group_name="myResourceGroup",
    sku=azure_native.appconfiguration.SkuArgs(
        name="Standard",
    ))

```

```yaml
resources:
  configurationStore:
    type: azure-native:appconfiguration:ConfigurationStore
    properties:
      configStoreName: contoso
      disableLocalAuth: true
      location: westus
      resourceGroupName: myResourceGroup
      sku:
        name: Standard

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appconfiguration:ConfigurationStore contoso /subscriptions/c80fb759-c965-4c6a-9110-9b2b2d038882/resourceGroups/myResourceGroup/providers/Microsoft.AppConfiguration/configurationStores/contoso 
```
