PrivateLink Policy configuration object.
API Version: 2020-03-01.
Previous API Version: 2020-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### privateLinkPolicyCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateLinkForAzureAd = new AzureNative.AadIam.PrivateLinkForAzureAd("privateLinkForAzureAd", new()
    {
        AllTenants = false,
        Name = "myOrgPrivateLinkPolicy",
        OwnerTenantId = "950f8bca-bf4d-4a41-ad10-034e792a243d",
        PolicyName = "ddb1",
        ResourceGroup = "myOrgVnetRG",
        ResourceGroupName = "rg1",
        ResourceName = "myOrgVnetPrivateLink",
        SubscriptionId = "57849194-ea1f-470b-abda-d195b25634c1",
        Tenants = new[]
        {
            "3616657d-1c80-41ae-9d83-2a2776f2c9be",
            "727b6ef1-18ab-4627-ac95-3f9cd945ed87",
        },
    });

});


```

```go
package main

import (
	aadiam "github.com/pulumi/pulumi-azure-native-sdk/aadiam"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := aadiam.NewPrivateLinkForAzureAd(ctx, "privateLinkForAzureAd", &aadiam.PrivateLinkForAzureAdArgs{
			AllTenants:        pulumi.Bool(false),
			Name:              pulumi.String("myOrgPrivateLinkPolicy"),
			OwnerTenantId:     pulumi.String("950f8bca-bf4d-4a41-ad10-034e792a243d"),
			PolicyName:        pulumi.String("ddb1"),
			ResourceGroup:     pulumi.String("myOrgVnetRG"),
			ResourceGroupName: pulumi.String("rg1"),
			ResourceName:      pulumi.String("myOrgVnetPrivateLink"),
			SubscriptionId:    pulumi.String("57849194-ea1f-470b-abda-d195b25634c1"),
			Tenants: pulumi.StringArray{
				pulumi.String("3616657d-1c80-41ae-9d83-2a2776f2c9be"),
				pulumi.String("727b6ef1-18ab-4627-ac95-3f9cd945ed87"),
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
import com.pulumi.azurenative.aadiam.PrivateLinkForAzureAd;
import com.pulumi.azurenative.aadiam.PrivateLinkForAzureAdArgs;
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
        var privateLinkForAzureAd = new PrivateLinkForAzureAd("privateLinkForAzureAd", PrivateLinkForAzureAdArgs.builder()        
            .allTenants(false)
            .name("myOrgPrivateLinkPolicy")
            .ownerTenantId("950f8bca-bf4d-4a41-ad10-034e792a243d")
            .policyName("ddb1")
            .resourceGroup("myOrgVnetRG")
            .resourceGroupName("rg1")
            .resourceName("myOrgVnetPrivateLink")
            .subscriptionId("57849194-ea1f-470b-abda-d195b25634c1")
            .tenants(            
                "3616657d-1c80-41ae-9d83-2a2776f2c9be",
                "727b6ef1-18ab-4627-ac95-3f9cd945ed87")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateLinkForAzureAd = new azure_native.aadiam.PrivateLinkForAzureAd("privateLinkForAzureAd", {
    allTenants: false,
    name: "myOrgPrivateLinkPolicy",
    ownerTenantId: "950f8bca-bf4d-4a41-ad10-034e792a243d",
    policyName: "ddb1",
    resourceGroup: "myOrgVnetRG",
    resourceGroupName: "rg1",
    resourceName: "myOrgVnetPrivateLink",
    subscriptionId: "57849194-ea1f-470b-abda-d195b25634c1",
    tenants: [
        "3616657d-1c80-41ae-9d83-2a2776f2c9be",
        "727b6ef1-18ab-4627-ac95-3f9cd945ed87",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_link_for_azure_ad = azure_native.aadiam.PrivateLinkForAzureAd("privateLinkForAzureAd",
    all_tenants=False,
    name="myOrgPrivateLinkPolicy",
    owner_tenant_id="950f8bca-bf4d-4a41-ad10-034e792a243d",
    policy_name="ddb1",
    resource_group="myOrgVnetRG",
    resource_group_name="rg1",
    resource_name_="myOrgVnetPrivateLink",
    subscription_id="57849194-ea1f-470b-abda-d195b25634c1",
    tenants=[
        "3616657d-1c80-41ae-9d83-2a2776f2c9be",
        "727b6ef1-18ab-4627-ac95-3f9cd945ed87",
    ])

```

```yaml
resources:
  privateLinkForAzureAd:
    type: azure-native:aadiam:PrivateLinkForAzureAd
    properties:
      allTenants: false
      name: myOrgPrivateLinkPolicy
      ownerTenantId: 950f8bca-bf4d-4a41-ad10-034e792a243d
      policyName: ddb1
      resourceGroup: myOrgVnetRG
      resourceGroupName: rg1
      resourceName: myOrgVnetPrivateLink
      subscriptionId: 57849194-ea1f-470b-abda-d195b25634c1
      tenants:
        - 3616657d-1c80-41ae-9d83-2a2776f2c9be
        - 727b6ef1-18ab-4627-ac95-3f9cd945ed87

```

{{% /example %}}
{{% example %}}
### privateLinkPolicyMinCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateLinkForAzureAd = new AzureNative.AadIam.PrivateLinkForAzureAd("privateLinkForAzureAd", new()
    {
        AllTenants = false,
        Name = "myOrgPrivateLinkPolicy",
        OwnerTenantId = "950f8bca-bf4d-4a41-ad10-034e792a243d",
        PolicyName = "ddb1",
        ResourceGroup = "myOrgVnetRG",
        ResourceGroupName = "rg1",
        ResourceName = "myOrgVnetPrivateLink",
        SubscriptionId = "57849194-ea1f-470b-abda-d195b25634c1",
        Tenants = new[]
        {
            "3616657d-1c80-41ae-9d83-2a2776f2c9be",
            "727b6ef1-18ab-4627-ac95-3f9cd945ed87",
        },
    });

});


```

```go
package main

import (
	aadiam "github.com/pulumi/pulumi-azure-native-sdk/aadiam"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := aadiam.NewPrivateLinkForAzureAd(ctx, "privateLinkForAzureAd", &aadiam.PrivateLinkForAzureAdArgs{
			AllTenants:        pulumi.Bool(false),
			Name:              pulumi.String("myOrgPrivateLinkPolicy"),
			OwnerTenantId:     pulumi.String("950f8bca-bf4d-4a41-ad10-034e792a243d"),
			PolicyName:        pulumi.String("ddb1"),
			ResourceGroup:     pulumi.String("myOrgVnetRG"),
			ResourceGroupName: pulumi.String("rg1"),
			ResourceName:      pulumi.String("myOrgVnetPrivateLink"),
			SubscriptionId:    pulumi.String("57849194-ea1f-470b-abda-d195b25634c1"),
			Tenants: pulumi.StringArray{
				pulumi.String("3616657d-1c80-41ae-9d83-2a2776f2c9be"),
				pulumi.String("727b6ef1-18ab-4627-ac95-3f9cd945ed87"),
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
import com.pulumi.azurenative.aadiam.PrivateLinkForAzureAd;
import com.pulumi.azurenative.aadiam.PrivateLinkForAzureAdArgs;
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
        var privateLinkForAzureAd = new PrivateLinkForAzureAd("privateLinkForAzureAd", PrivateLinkForAzureAdArgs.builder()        
            .allTenants(false)
            .name("myOrgPrivateLinkPolicy")
            .ownerTenantId("950f8bca-bf4d-4a41-ad10-034e792a243d")
            .policyName("ddb1")
            .resourceGroup("myOrgVnetRG")
            .resourceGroupName("rg1")
            .resourceName("myOrgVnetPrivateLink")
            .subscriptionId("57849194-ea1f-470b-abda-d195b25634c1")
            .tenants(            
                "3616657d-1c80-41ae-9d83-2a2776f2c9be",
                "727b6ef1-18ab-4627-ac95-3f9cd945ed87")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateLinkForAzureAd = new azure_native.aadiam.PrivateLinkForAzureAd("privateLinkForAzureAd", {
    allTenants: false,
    name: "myOrgPrivateLinkPolicy",
    ownerTenantId: "950f8bca-bf4d-4a41-ad10-034e792a243d",
    policyName: "ddb1",
    resourceGroup: "myOrgVnetRG",
    resourceGroupName: "rg1",
    resourceName: "myOrgVnetPrivateLink",
    subscriptionId: "57849194-ea1f-470b-abda-d195b25634c1",
    tenants: [
        "3616657d-1c80-41ae-9d83-2a2776f2c9be",
        "727b6ef1-18ab-4627-ac95-3f9cd945ed87",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_link_for_azure_ad = azure_native.aadiam.PrivateLinkForAzureAd("privateLinkForAzureAd",
    all_tenants=False,
    name="myOrgPrivateLinkPolicy",
    owner_tenant_id="950f8bca-bf4d-4a41-ad10-034e792a243d",
    policy_name="ddb1",
    resource_group="myOrgVnetRG",
    resource_group_name="rg1",
    resource_name_="myOrgVnetPrivateLink",
    subscription_id="57849194-ea1f-470b-abda-d195b25634c1",
    tenants=[
        "3616657d-1c80-41ae-9d83-2a2776f2c9be",
        "727b6ef1-18ab-4627-ac95-3f9cd945ed87",
    ])

```

```yaml
resources:
  privateLinkForAzureAd:
    type: azure-native:aadiam:PrivateLinkForAzureAd
    properties:
      allTenants: false
      name: myOrgPrivateLinkPolicy
      ownerTenantId: 950f8bca-bf4d-4a41-ad10-034e792a243d
      policyName: ddb1
      resourceGroup: myOrgVnetRG
      resourceGroupName: rg1
      resourceName: myOrgVnetPrivateLink
      subscriptionId: 57849194-ea1f-470b-abda-d195b25634c1
      tenants:
        - 3616657d-1c80-41ae-9d83-2a2776f2c9be
        - 727b6ef1-18ab-4627-ac95-3f9cd945ed87

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:aadiam:PrivateLinkForAzureAd myOrgPrivateLinkPolicy /subscriptions/{subscriptionId}/resourcegroups/{resourceGroupName}/providers/microsoft.aadiam/privateLinkForAzureAd/{policyName} 
```
