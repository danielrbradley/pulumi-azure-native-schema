Define the SAP Application Server Instance resource.
API Version: 2023-04-01.
Previous API Version: 2021-12-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create SAP Application Server Instances for HA System with Availability Set
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapApplicationServerInstance = new AzureNative.Workloads.SAPApplicationServerInstance("sapApplicationServerInstance", new()
    {
        ApplicationInstanceName = "app01",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPApplicationServerInstance(ctx, "sapApplicationServerInstance", &workloads.SAPApplicationServerInstanceArgs{
			ApplicationInstanceName: pulumi.String("app01"),
			Location:                pulumi.String("westcentralus"),
			ResourceGroupName:       pulumi.String("test-rg"),
			SapVirtualInstanceName:  pulumi.String("X00"),
			Tags:                    nil,
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
import com.pulumi.azurenative.workloads.SAPApplicationServerInstance;
import com.pulumi.azurenative.workloads.SAPApplicationServerInstanceArgs;
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
        var sapApplicationServerInstance = new SAPApplicationServerInstance("sapApplicationServerInstance", SAPApplicationServerInstanceArgs.builder()        
            .applicationInstanceName("app01")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapApplicationServerInstance = new azure_native.workloads.SAPApplicationServerInstance("sapApplicationServerInstance", {
    applicationInstanceName: "app01",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_application_server_instance = azure_native.workloads.SAPApplicationServerInstance("sapApplicationServerInstance",
    application_instance_name="app01",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapApplicationServerInstance:
    type: azure-native:workloads:SAPApplicationServerInstance
    properties:
      applicationInstanceName: app01
      location: westcentralus
      resourceGroupName: test-rg
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### SAPApplicationServerInstances_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapApplicationServerInstance = new AzureNative.Workloads.SAPApplicationServerInstance("sapApplicationServerInstance", new()
    {
        ApplicationInstanceName = "app01",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPApplicationServerInstance(ctx, "sapApplicationServerInstance", &workloads.SAPApplicationServerInstanceArgs{
			ApplicationInstanceName: pulumi.String("app01"),
			Location:                pulumi.String("westcentralus"),
			ResourceGroupName:       pulumi.String("test-rg"),
			SapVirtualInstanceName:  pulumi.String("X00"),
			Tags:                    nil,
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
import com.pulumi.azurenative.workloads.SAPApplicationServerInstance;
import com.pulumi.azurenative.workloads.SAPApplicationServerInstanceArgs;
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
        var sapApplicationServerInstance = new SAPApplicationServerInstance("sapApplicationServerInstance", SAPApplicationServerInstanceArgs.builder()        
            .applicationInstanceName("app01")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapApplicationServerInstance = new azure_native.workloads.SAPApplicationServerInstance("sapApplicationServerInstance", {
    applicationInstanceName: "app01",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_application_server_instance = azure_native.workloads.SAPApplicationServerInstance("sapApplicationServerInstance",
    application_instance_name="app01",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapApplicationServerInstance:
    type: azure-native:workloads:SAPApplicationServerInstance
    properties:
      applicationInstanceName: app01
      location: westcentralus
      resourceGroupName: test-rg
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:workloads:SAPApplicationServerInstance app01 /subscriptions/6d875e77-e412-4d7d-9af4-8895278b4443/resourceGroups/test-rg/providers/Microsoft.Workloads/sapVirtualInstances/X00/applicationInstances/app01 
```
