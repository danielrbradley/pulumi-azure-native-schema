Define the Database resource.
API Version: 2023-04-01.
Previous API Version: 2021-12-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create SAP Database Instances for HA System with Availability Set
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapDatabaseInstance = new AzureNative.Workloads.SAPDatabaseInstance("sapDatabaseInstance", new()
    {
        DatabaseInstanceName = "databaseServer",
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
		_, err := workloads.NewSAPDatabaseInstance(ctx, "sapDatabaseInstance", &workloads.SAPDatabaseInstanceArgs{
			DatabaseInstanceName:   pulumi.String("databaseServer"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPDatabaseInstance;
import com.pulumi.azurenative.workloads.SAPDatabaseInstanceArgs;
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
        var sapDatabaseInstance = new SAPDatabaseInstance("sapDatabaseInstance", SAPDatabaseInstanceArgs.builder()        
            .databaseInstanceName("databaseServer")
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

const sapDatabaseInstance = new azure_native.workloads.SAPDatabaseInstance("sapDatabaseInstance", {
    databaseInstanceName: "databaseServer",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_database_instance = azure_native.workloads.SAPDatabaseInstance("sapDatabaseInstance",
    database_instance_name="databaseServer",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapDatabaseInstance:
    type: azure-native:workloads:SAPDatabaseInstance
    properties:
      databaseInstanceName: databaseServer
      location: westcentralus
      resourceGroupName: test-rg
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### SAPDatabaseInstances_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapDatabaseInstance = new AzureNative.Workloads.SAPDatabaseInstance("sapDatabaseInstance", new()
    {
        DatabaseInstanceName = "databaseServer",
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
		_, err := workloads.NewSAPDatabaseInstance(ctx, "sapDatabaseInstance", &workloads.SAPDatabaseInstanceArgs{
			DatabaseInstanceName:   pulumi.String("databaseServer"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPDatabaseInstance;
import com.pulumi.azurenative.workloads.SAPDatabaseInstanceArgs;
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
        var sapDatabaseInstance = new SAPDatabaseInstance("sapDatabaseInstance", SAPDatabaseInstanceArgs.builder()        
            .databaseInstanceName("databaseServer")
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

const sapDatabaseInstance = new azure_native.workloads.SAPDatabaseInstance("sapDatabaseInstance", {
    databaseInstanceName: "databaseServer",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_database_instance = azure_native.workloads.SAPDatabaseInstance("sapDatabaseInstance",
    database_instance_name="databaseServer",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapDatabaseInstance:
    type: azure-native:workloads:SAPDatabaseInstance
    properties:
      databaseInstanceName: databaseServer
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
$ pulumi import azure-native:workloads:SAPDatabaseInstance databaseServer /subscriptions/6d875e77-e412-4d7d-9af4-8895278b4443/resourceGroups/test-rg/providers/Microsoft.Workloads/sapVirtualInstances/X00/databaseInstances/databaseServer 
```
