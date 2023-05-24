An object that represents a webhook for a container registry.
API Version: 2022-12-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WebhookCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webhook = new AzureNative.ContainerRegistry.Webhook("webhook", new()
    {
        Actions = new[]
        {
            "push",
        },
        CustomHeaders = 
        {
            { "Authorization", "******" },
        },
        Location = "westus",
        RegistryName = "myRegistry",
        ResourceGroupName = "myResourceGroup",
        Scope = "myRepository",
        ServiceUri = "http://myservice.com",
        Status = "enabled",
        Tags = 
        {
            { "key", "value" },
        },
        WebhookName = "myWebhook",
    });

});


```

```go
package main

import (
	containerregistry "github.com/pulumi/pulumi-azure-native-sdk/containerregistry"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerregistry.NewWebhook(ctx, "webhook", &containerregistry.WebhookArgs{
			Actions: pulumi.StringArray{
				pulumi.String("push"),
			},
			CustomHeaders: pulumi.StringMap{
				"Authorization": pulumi.String("******"),
			},
			Location:          pulumi.String("westus"),
			RegistryName:      pulumi.String("myRegistry"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Scope:             pulumi.String("myRepository"),
			ServiceUri:        pulumi.String("http://myservice.com"),
			Status:            pulumi.String("enabled"),
			Tags: pulumi.StringMap{
				"key": pulumi.String("value"),
			},
			WebhookName: pulumi.String("myWebhook"),
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
import com.pulumi.azurenative.containerregistry.Webhook;
import com.pulumi.azurenative.containerregistry.WebhookArgs;
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
        var webhook = new Webhook("webhook", WebhookArgs.builder()        
            .actions("push")
            .customHeaders(Map.of("Authorization", "******"))
            .location("westus")
            .registryName("myRegistry")
            .resourceGroupName("myResourceGroup")
            .scope("myRepository")
            .serviceUri("http://myservice.com")
            .status("enabled")
            .tags(Map.of("key", "value"))
            .webhookName("myWebhook")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webhook = new azure_native.containerregistry.Webhook("webhook", {
    actions: ["push"],
    customHeaders: {
        Authorization: "******",
    },
    location: "westus",
    registryName: "myRegistry",
    resourceGroupName: "myResourceGroup",
    scope: "myRepository",
    serviceUri: "http://myservice.com",
    status: "enabled",
    tags: {
        key: "value",
    },
    webhookName: "myWebhook",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

webhook = azure_native.containerregistry.Webhook("webhook",
    actions=["push"],
    custom_headers={
        "Authorization": "******",
    },
    location="westus",
    registry_name="myRegistry",
    resource_group_name="myResourceGroup",
    scope="myRepository",
    service_uri="http://myservice.com",
    status="enabled",
    tags={
        "key": "value",
    },
    webhook_name="myWebhook")

```

```yaml
resources:
  webhook:
    type: azure-native:containerregistry:Webhook
    properties:
      actions:
        - push
      customHeaders:
        Authorization: '******'
      location: westus
      registryName: myRegistry
      resourceGroupName: myResourceGroup
      scope: myRepository
      serviceUri: http://myservice.com
      status: enabled
      tags:
        key: value
      webhookName: myWebhook

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerregistry:Webhook myWebhook /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.ContainerRegistry/registries/myRegistry/webhooks/myWebhook 
```
