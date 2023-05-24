DigitalTwinsInstance endpoint resource.
API Version: 2023-01-31.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put a DigitalTwinsEndpoint resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var digitalTwinsEndpoint = new AzureNative.DigitalTwins.DigitalTwinsEndpoint("digitalTwinsEndpoint", new()
    {
        EndpointName = "myServiceBus",
        Properties = new AzureNative.DigitalTwins.Inputs.ServiceBusArgs
        {
            AuthenticationType = "KeyBased",
            EndpointType = "ServiceBus",
            PrimaryConnectionString = "Endpoint=sb://mysb.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=xyzxyzoX4=;EntityPath=abcabc",
            SecondaryConnectionString = "Endpoint=sb://mysb.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=xyzxyzoX4=;EntityPath=abcabc",
        },
        ResourceGroupName = "resRg",
        ResourceName = "myDigitalTwinsService",
    });

});


```

```go
package main

import (
	digitaltwins "github.com/pulumi/pulumi-azure-native-sdk/digitaltwins"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := digitaltwins.NewDigitalTwinsEndpoint(ctx, "digitalTwinsEndpoint", &digitaltwins.DigitalTwinsEndpointArgs{
			EndpointName: pulumi.String("myServiceBus"),
			Properties: digitaltwins.ServiceBus{
				AuthenticationType:        "KeyBased",
				EndpointType:              "ServiceBus",
				PrimaryConnectionString:   "Endpoint=sb://mysb.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=xyzxyzoX4=;EntityPath=abcabc",
				SecondaryConnectionString: "Endpoint=sb://mysb.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=xyzxyzoX4=;EntityPath=abcabc",
			},
			ResourceGroupName: pulumi.String("resRg"),
			ResourceName:      pulumi.String("myDigitalTwinsService"),
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
import com.pulumi.azurenative.digitaltwins.DigitalTwinsEndpoint;
import com.pulumi.azurenative.digitaltwins.DigitalTwinsEndpointArgs;
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
        var digitalTwinsEndpoint = new DigitalTwinsEndpoint("digitalTwinsEndpoint", DigitalTwinsEndpointArgs.builder()        
            .endpointName("myServiceBus")
            .properties(Map.ofEntries(
                Map.entry("authenticationType", "KeyBased"),
                Map.entry("endpointType", "ServiceBus"),
                Map.entry("primaryConnectionString", "Endpoint=sb://mysb.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=xyzxyzoX4=;EntityPath=abcabc"),
                Map.entry("secondaryConnectionString", "Endpoint=sb://mysb.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=xyzxyzoX4=;EntityPath=abcabc")
            ))
            .resourceGroupName("resRg")
            .resourceName("myDigitalTwinsService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const digitalTwinsEndpoint = new azure_native.digitaltwins.DigitalTwinsEndpoint("digitalTwinsEndpoint", {
    endpointName: "myServiceBus",
    properties: {
        authenticationType: "KeyBased",
        endpointType: "ServiceBus",
        primaryConnectionString: "Endpoint=sb://mysb.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=xyzxyzoX4=;EntityPath=abcabc",
        secondaryConnectionString: "Endpoint=sb://mysb.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=xyzxyzoX4=;EntityPath=abcabc",
    },
    resourceGroupName: "resRg",
    resourceName: "myDigitalTwinsService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

digital_twins_endpoint = azure_native.digitaltwins.DigitalTwinsEndpoint("digitalTwinsEndpoint",
    endpoint_name="myServiceBus",
    properties=azure_native.digitaltwins.ServiceBusArgs(
        authentication_type="KeyBased",
        endpoint_type="ServiceBus",
        primary_connection_string="Endpoint=sb://mysb.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=xyzxyzoX4=;EntityPath=abcabc",
        secondary_connection_string="Endpoint=sb://mysb.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=xyzxyzoX4=;EntityPath=abcabc",
    ),
    resource_group_name="resRg",
    resource_name_="myDigitalTwinsService")

```

```yaml
resources:
  digitalTwinsEndpoint:
    type: azure-native:digitaltwins:DigitalTwinsEndpoint
    properties:
      endpointName: myServiceBus
      properties:
        authenticationType: KeyBased
        endpointType: ServiceBus
        primaryConnectionString: Endpoint=sb://mysb.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=xyzxyzoX4=;EntityPath=abcabc
        secondaryConnectionString: Endpoint=sb://mysb.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=xyzxyzoX4=;EntityPath=abcabc
      resourceGroupName: resRg
      resourceName: myDigitalTwinsService

```

{{% /example %}}
{{% example %}}
### Put a DigitalTwinsEndpoint resource with identity
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var digitalTwinsEndpoint = new AzureNative.DigitalTwins.DigitalTwinsEndpoint("digitalTwinsEndpoint", new()
    {
        EndpointName = "myServiceBus",
        Properties = new AzureNative.DigitalTwins.Inputs.ServiceBusArgs
        {
            AuthenticationType = "IdentityBased",
            EndpointType = "ServiceBus",
            EndpointUri = "sb://mysb.servicebus.windows.net/",
            EntityPath = "mysbtopic",
        },
        ResourceGroupName = "resRg",
        ResourceName = "myDigitalTwinsService",
    });

});


```

```go
package main

import (
	digitaltwins "github.com/pulumi/pulumi-azure-native-sdk/digitaltwins"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := digitaltwins.NewDigitalTwinsEndpoint(ctx, "digitalTwinsEndpoint", &digitaltwins.DigitalTwinsEndpointArgs{
			EndpointName: pulumi.String("myServiceBus"),
			Properties: digitaltwins.ServiceBus{
				AuthenticationType: "IdentityBased",
				EndpointType:       "ServiceBus",
				EndpointUri:        "sb://mysb.servicebus.windows.net/",
				EntityPath:         "mysbtopic",
			},
			ResourceGroupName: pulumi.String("resRg"),
			ResourceName:      pulumi.String("myDigitalTwinsService"),
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
import com.pulumi.azurenative.digitaltwins.DigitalTwinsEndpoint;
import com.pulumi.azurenative.digitaltwins.DigitalTwinsEndpointArgs;
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
        var digitalTwinsEndpoint = new DigitalTwinsEndpoint("digitalTwinsEndpoint", DigitalTwinsEndpointArgs.builder()        
            .endpointName("myServiceBus")
            .properties(Map.ofEntries(
                Map.entry("authenticationType", "IdentityBased"),
                Map.entry("endpointType", "ServiceBus"),
                Map.entry("endpointUri", "sb://mysb.servicebus.windows.net/"),
                Map.entry("entityPath", "mysbtopic")
            ))
            .resourceGroupName("resRg")
            .resourceName("myDigitalTwinsService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const digitalTwinsEndpoint = new azure_native.digitaltwins.DigitalTwinsEndpoint("digitalTwinsEndpoint", {
    endpointName: "myServiceBus",
    properties: {
        authenticationType: "IdentityBased",
        endpointType: "ServiceBus",
        endpointUri: "sb://mysb.servicebus.windows.net/",
        entityPath: "mysbtopic",
    },
    resourceGroupName: "resRg",
    resourceName: "myDigitalTwinsService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

digital_twins_endpoint = azure_native.digitaltwins.DigitalTwinsEndpoint("digitalTwinsEndpoint",
    endpoint_name="myServiceBus",
    properties=azure_native.digitaltwins.ServiceBusArgs(
        authentication_type="IdentityBased",
        endpoint_type="ServiceBus",
        endpoint_uri="sb://mysb.servicebus.windows.net/",
        entity_path="mysbtopic",
    ),
    resource_group_name="resRg",
    resource_name_="myDigitalTwinsService")

```

```yaml
resources:
  digitalTwinsEndpoint:
    type: azure-native:digitaltwins:DigitalTwinsEndpoint
    properties:
      endpointName: myServiceBus
      properties:
        authenticationType: IdentityBased
        endpointType: ServiceBus
        endpointUri: sb://mysb.servicebus.windows.net/
        entityPath: mysbtopic
      resourceGroupName: resRg
      resourceName: myDigitalTwinsService

```

{{% /example %}}
{{% example %}}
### Put a DigitalTwinsEndpoint resource with user assigned identity
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var digitalTwinsEndpoint = new AzureNative.DigitalTwins.DigitalTwinsEndpoint("digitalTwinsEndpoint", new()
    {
        EndpointName = "myServiceBus",
        Properties = new AzureNative.DigitalTwins.Inputs.ServiceBusArgs
        {
            AuthenticationType = "IdentityBased",
            EndpointType = "ServiceBus",
            EndpointUri = "sb://mysb.servicebus.windows.net/",
            EntityPath = "mysbtopic",
            Identity = new AzureNative.DigitalTwins.Inputs.ManagedIdentityReferenceArgs
            {
                Type = "UserAssigned",
                UserAssignedIdentity = "/subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourceGroups/testrg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/testidentity",
            },
        },
        ResourceGroupName = "resRg",
        ResourceName = "myDigitalTwinsService",
    });

});


```

```go
package main

import (
	digitaltwins "github.com/pulumi/pulumi-azure-native-sdk/digitaltwins"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := digitaltwins.NewDigitalTwinsEndpoint(ctx, "digitalTwinsEndpoint", &digitaltwins.DigitalTwinsEndpointArgs{
			EndpointName: pulumi.String("myServiceBus"),
			Properties: digitaltwins.ServiceBus{
				AuthenticationType: "IdentityBased",
				EndpointType:       "ServiceBus",
				EndpointUri:        "sb://mysb.servicebus.windows.net/",
				EntityPath:         "mysbtopic",
				Identity: digitaltwins.ManagedIdentityReference{
					Type:                 "UserAssigned",
					UserAssignedIdentity: "/subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourceGroups/testrg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/testidentity",
				},
			},
			ResourceGroupName: pulumi.String("resRg"),
			ResourceName:      pulumi.String("myDigitalTwinsService"),
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
import com.pulumi.azurenative.digitaltwins.DigitalTwinsEndpoint;
import com.pulumi.azurenative.digitaltwins.DigitalTwinsEndpointArgs;
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
        var digitalTwinsEndpoint = new DigitalTwinsEndpoint("digitalTwinsEndpoint", DigitalTwinsEndpointArgs.builder()        
            .endpointName("myServiceBus")
            .properties(Map.ofEntries(
                Map.entry("authenticationType", "IdentityBased"),
                Map.entry("endpointType", "ServiceBus"),
                Map.entry("endpointUri", "sb://mysb.servicebus.windows.net/"),
                Map.entry("entityPath", "mysbtopic"),
                Map.entry("identity", Map.ofEntries(
                    Map.entry("type", "UserAssigned"),
                    Map.entry("userAssignedIdentity", "/subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourceGroups/testrg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/testidentity")
                ))
            ))
            .resourceGroupName("resRg")
            .resourceName("myDigitalTwinsService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const digitalTwinsEndpoint = new azure_native.digitaltwins.DigitalTwinsEndpoint("digitalTwinsEndpoint", {
    endpointName: "myServiceBus",
    properties: {
        authenticationType: "IdentityBased",
        endpointType: "ServiceBus",
        endpointUri: "sb://mysb.servicebus.windows.net/",
        entityPath: "mysbtopic",
        identity: {
            type: "UserAssigned",
            userAssignedIdentity: "/subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourceGroups/testrg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/testidentity",
        },
    },
    resourceGroupName: "resRg",
    resourceName: "myDigitalTwinsService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

digital_twins_endpoint = azure_native.digitaltwins.DigitalTwinsEndpoint("digitalTwinsEndpoint",
    endpoint_name="myServiceBus",
    properties=azure_native.digitaltwins.ServiceBusArgs(
        authentication_type="IdentityBased",
        endpoint_type="ServiceBus",
        endpoint_uri="sb://mysb.servicebus.windows.net/",
        entity_path="mysbtopic",
        identity=azure_native.digitaltwins.ManagedIdentityReferenceArgs(
            type="UserAssigned",
            user_assigned_identity="/subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourceGroups/testrg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/testidentity",
        ),
    ),
    resource_group_name="resRg",
    resource_name_="myDigitalTwinsService")

```

```yaml
resources:
  digitalTwinsEndpoint:
    type: azure-native:digitaltwins:DigitalTwinsEndpoint
    properties:
      endpointName: myServiceBus
      properties:
        authenticationType: IdentityBased
        endpointType: ServiceBus
        endpointUri: sb://mysb.servicebus.windows.net/
        entityPath: mysbtopic
        identity:
          type: UserAssigned
          userAssignedIdentity: /subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourceGroups/testrg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/testidentity
      resourceGroupName: resRg
      resourceName: myDigitalTwinsService

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:digitaltwins:DigitalTwinsEndpoint myServiceBus /subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourcegroups/resRg/providers/Microsoft.DigitalTwins/digitalTwinsInstances/myDigitalTwinsService/endpoints/myServiceBus 
```
