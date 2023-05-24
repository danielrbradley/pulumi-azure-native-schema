Friendly domain name mapping to the endpoint hostname that the customer provides for branding purposes, e.g. www.contoso.com.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CustomDomains_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var customDomain = new AzureNative.Cdn.CustomDomain("customDomain", new()
    {
        CustomDomainName = "www-someDomain-net",
        EndpointName = "endpoint1",
        HostName = "www.someDomain.net",
        ProfileName = "profile1",
        ResourceGroupName = "RG",
    });

});


```

```go
package main

import (
	cdn "github.com/pulumi/pulumi-azure-native-sdk/cdn"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := cdn.NewCustomDomain(ctx, "customDomain", &cdn.CustomDomainArgs{
			CustomDomainName:  pulumi.String("www-someDomain-net"),
			EndpointName:      pulumi.String("endpoint1"),
			HostName:          pulumi.String("www.someDomain.net"),
			ProfileName:       pulumi.String("profile1"),
			ResourceGroupName: pulumi.String("RG"),
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
import com.pulumi.azurenative.cdn.CustomDomain;
import com.pulumi.azurenative.cdn.CustomDomainArgs;
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
        var customDomain = new CustomDomain("customDomain", CustomDomainArgs.builder()        
            .customDomainName("www-someDomain-net")
            .endpointName("endpoint1")
            .hostName("www.someDomain.net")
            .profileName("profile1")
            .resourceGroupName("RG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const customDomain = new azure_native.cdn.CustomDomain("customDomain", {
    customDomainName: "www-someDomain-net",
    endpointName: "endpoint1",
    hostName: "www.someDomain.net",
    profileName: "profile1",
    resourceGroupName: "RG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

custom_domain = azure_native.cdn.CustomDomain("customDomain",
    custom_domain_name="www-someDomain-net",
    endpoint_name="endpoint1",
    host_name="www.someDomain.net",
    profile_name="profile1",
    resource_group_name="RG")

```

```yaml
resources:
  customDomain:
    type: azure-native:cdn:CustomDomain
    properties:
      customDomainName: www-someDomain-net
      endpointName: endpoint1
      hostName: www.someDomain.net
      profileName: profile1
      resourceGroupName: RG

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cdn:CustomDomain www-someDomain-net /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/customdomains/www-someDomain-net 
```
