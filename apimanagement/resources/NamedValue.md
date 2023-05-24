NamedValue details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateNamedValue
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var namedValue = new AzureNative.ApiManagement.NamedValue("namedValue", new()
    {
        DisplayName = "prop3name",
        NamedValueId = "testprop2",
        ResourceGroupName = "rg1",
        Secret = false,
        ServiceName = "apimService1",
        Tags = new[]
        {
            "foo",
            "bar",
        },
        Value = "propValue",
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
		_, err := apimanagement.NewNamedValue(ctx, "namedValue", &apimanagement.NamedValueArgs{
			DisplayName:       pulumi.String("prop3name"),
			NamedValueId:      pulumi.String("testprop2"),
			ResourceGroupName: pulumi.String("rg1"),
			Secret:            pulumi.Bool(false),
			ServiceName:       pulumi.String("apimService1"),
			Tags: pulumi.StringArray{
				pulumi.String("foo"),
				pulumi.String("bar"),
			},
			Value: pulumi.String("propValue"),
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
import com.pulumi.azurenative.apimanagement.NamedValue;
import com.pulumi.azurenative.apimanagement.NamedValueArgs;
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
        var namedValue = new NamedValue("namedValue", NamedValueArgs.builder()        
            .displayName("prop3name")
            .namedValueId("testprop2")
            .resourceGroupName("rg1")
            .secret(false)
            .serviceName("apimService1")
            .tags(            
                "foo",
                "bar")
            .value("propValue")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const namedValue = new azure_native.apimanagement.NamedValue("namedValue", {
    displayName: "prop3name",
    namedValueId: "testprop2",
    resourceGroupName: "rg1",
    secret: false,
    serviceName: "apimService1",
    tags: [
        "foo",
        "bar",
    ],
    value: "propValue",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

named_value = azure_native.apimanagement.NamedValue("namedValue",
    display_name="prop3name",
    named_value_id="testprop2",
    resource_group_name="rg1",
    secret=False,
    service_name="apimService1",
    tags=[
        "foo",
        "bar",
    ],
    value="propValue")

```

```yaml
resources:
  namedValue:
    type: azure-native:apimanagement:NamedValue
    properties:
      displayName: prop3name
      namedValueId: testprop2
      resourceGroupName: rg1
      secret: false
      serviceName: apimService1
      tags:
        - foo
        - bar
      value: propValue

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateNamedValueWithKeyVault
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var namedValue = new AzureNative.ApiManagement.NamedValue("namedValue", new()
    {
        DisplayName = "prop6namekv",
        KeyVault = new AzureNative.ApiManagement.Inputs.KeyVaultContractCreatePropertiesArgs
        {
            IdentityClientId = "ceaa6b06-c00f-43ef-99ac-f53d1fe876a0",
            SecretIdentifier = "https://contoso.vault.azure.net/secrets/aadSecret",
        },
        NamedValueId = "testprop6",
        ResourceGroupName = "rg1",
        Secret = true,
        ServiceName = "apimService1",
        Tags = new[]
        {
            "foo",
            "bar",
        },
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
		_, err := apimanagement.NewNamedValue(ctx, "namedValue", &apimanagement.NamedValueArgs{
			DisplayName: pulumi.String("prop6namekv"),
			KeyVault: &apimanagement.KeyVaultContractCreatePropertiesArgs{
				IdentityClientId: pulumi.String("ceaa6b06-c00f-43ef-99ac-f53d1fe876a0"),
				SecretIdentifier: pulumi.String("https://contoso.vault.azure.net/secrets/aadSecret"),
			},
			NamedValueId:      pulumi.String("testprop6"),
			ResourceGroupName: pulumi.String("rg1"),
			Secret:            pulumi.Bool(true),
			ServiceName:       pulumi.String("apimService1"),
			Tags: pulumi.StringArray{
				pulumi.String("foo"),
				pulumi.String("bar"),
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
import com.pulumi.azurenative.apimanagement.NamedValue;
import com.pulumi.azurenative.apimanagement.NamedValueArgs;
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
        var namedValue = new NamedValue("namedValue", NamedValueArgs.builder()        
            .displayName("prop6namekv")
            .keyVault(Map.ofEntries(
                Map.entry("identityClientId", "ceaa6b06-c00f-43ef-99ac-f53d1fe876a0"),
                Map.entry("secretIdentifier", "https://contoso.vault.azure.net/secrets/aadSecret")
            ))
            .namedValueId("testprop6")
            .resourceGroupName("rg1")
            .secret(true)
            .serviceName("apimService1")
            .tags(            
                "foo",
                "bar")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const namedValue = new azure_native.apimanagement.NamedValue("namedValue", {
    displayName: "prop6namekv",
    keyVault: {
        identityClientId: "ceaa6b06-c00f-43ef-99ac-f53d1fe876a0",
        secretIdentifier: "https://contoso.vault.azure.net/secrets/aadSecret",
    },
    namedValueId: "testprop6",
    resourceGroupName: "rg1",
    secret: true,
    serviceName: "apimService1",
    tags: [
        "foo",
        "bar",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

named_value = azure_native.apimanagement.NamedValue("namedValue",
    display_name="prop6namekv",
    key_vault=azure_native.apimanagement.KeyVaultContractCreatePropertiesArgs(
        identity_client_id="ceaa6b06-c00f-43ef-99ac-f53d1fe876a0",
        secret_identifier="https://contoso.vault.azure.net/secrets/aadSecret",
    ),
    named_value_id="testprop6",
    resource_group_name="rg1",
    secret=True,
    service_name="apimService1",
    tags=[
        "foo",
        "bar",
    ])

```

```yaml
resources:
  namedValue:
    type: azure-native:apimanagement:NamedValue
    properties:
      displayName: prop6namekv
      keyVault:
        identityClientId: ceaa6b06-c00f-43ef-99ac-f53d1fe876a0
        secretIdentifier: https://contoso.vault.azure.net/secrets/aadSecret
      namedValueId: testprop6
      resourceGroupName: rg1
      secret: true
      serviceName: apimService1
      tags:
        - foo
        - bar

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:NamedValue testprop6 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/namedValues/testprop6 
```
