Properties for the database account.
API Version: 2022-11-15.
Previous API Version: 2021-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DataTransferServiceCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.DocumentDB.Service("service", new()
    {
        AccountName = "ddb1",
        InstanceCount = 1,
        InstanceSize = "Cosmos.D4s",
        ResourceGroupName = "rg1",
        ServiceName = "DataTransfer",
        ServiceType = "DataTransfer",
    });

});


```

```go
package main

import (
	documentdb "github.com/pulumi/pulumi-azure-native-sdk/documentdb"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := documentdb.NewService(ctx, "service", &documentdb.ServiceArgs{
			AccountName:       pulumi.String("ddb1"),
			InstanceCount:     pulumi.Int(1),
			InstanceSize:      pulumi.String("Cosmos.D4s"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("DataTransfer"),
			ServiceType:       pulumi.String("DataTransfer"),
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
import com.pulumi.azurenative.documentdb.Service;
import com.pulumi.azurenative.documentdb.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .accountName("ddb1")
            .instanceCount(1)
            .instanceSize("Cosmos.D4s")
            .resourceGroupName("rg1")
            .serviceName("DataTransfer")
            .serviceType("DataTransfer")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.documentdb.Service("service", {
    accountName: "ddb1",
    instanceCount: 1,
    instanceSize: "Cosmos.D4s",
    resourceGroupName: "rg1",
    serviceName: "DataTransfer",
    serviceType: "DataTransfer",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.documentdb.Service("service",
    account_name="ddb1",
    instance_count=1,
    instance_size="Cosmos.D4s",
    resource_group_name="rg1",
    service_name="DataTransfer",
    service_type="DataTransfer")

```

```yaml
resources:
  service:
    type: azure-native:documentdb:Service
    properties:
      accountName: ddb1
      instanceCount: 1
      instanceSize: Cosmos.D4s
      resourceGroupName: rg1
      serviceName: DataTransfer
      serviceType: DataTransfer

```

{{% /example %}}
{{% example %}}
### GraphAPIComputeServiceCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.DocumentDB.Service("service", new()
    {
        AccountName = "ddb1",
        InstanceCount = 1,
        InstanceSize = "Cosmos.D4s",
        ResourceGroupName = "rg1",
        ServiceName = "GraphAPICompute",
        ServiceType = "GraphAPICompute",
    });

});


```

```go
package main

import (
	documentdb "github.com/pulumi/pulumi-azure-native-sdk/documentdb"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := documentdb.NewService(ctx, "service", &documentdb.ServiceArgs{
			AccountName:       pulumi.String("ddb1"),
			InstanceCount:     pulumi.Int(1),
			InstanceSize:      pulumi.String("Cosmos.D4s"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("GraphAPICompute"),
			ServiceType:       pulumi.String("GraphAPICompute"),
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
import com.pulumi.azurenative.documentdb.Service;
import com.pulumi.azurenative.documentdb.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .accountName("ddb1")
            .instanceCount(1)
            .instanceSize("Cosmos.D4s")
            .resourceGroupName("rg1")
            .serviceName("GraphAPICompute")
            .serviceType("GraphAPICompute")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.documentdb.Service("service", {
    accountName: "ddb1",
    instanceCount: 1,
    instanceSize: "Cosmos.D4s",
    resourceGroupName: "rg1",
    serviceName: "GraphAPICompute",
    serviceType: "GraphAPICompute",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.documentdb.Service("service",
    account_name="ddb1",
    instance_count=1,
    instance_size="Cosmos.D4s",
    resource_group_name="rg1",
    service_name="GraphAPICompute",
    service_type="GraphAPICompute")

```

```yaml
resources:
  service:
    type: azure-native:documentdb:Service
    properties:
      accountName: ddb1
      instanceCount: 1
      instanceSize: Cosmos.D4s
      resourceGroupName: rg1
      serviceName: GraphAPICompute
      serviceType: GraphAPICompute

```

{{% /example %}}
{{% example %}}
### MaterializedViewsBuilderServiceCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.DocumentDB.Service("service", new()
    {
        AccountName = "ddb1",
        InstanceCount = 1,
        InstanceSize = "Cosmos.D4s",
        ResourceGroupName = "rg1",
        ServiceName = "MaterializedViewsBuilder",
        ServiceType = "MaterializedViewsBuilder",
    });

});


```

```go
package main

import (
	documentdb "github.com/pulumi/pulumi-azure-native-sdk/documentdb"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := documentdb.NewService(ctx, "service", &documentdb.ServiceArgs{
			AccountName:       pulumi.String("ddb1"),
			InstanceCount:     pulumi.Int(1),
			InstanceSize:      pulumi.String("Cosmos.D4s"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("MaterializedViewsBuilder"),
			ServiceType:       pulumi.String("MaterializedViewsBuilder"),
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
import com.pulumi.azurenative.documentdb.Service;
import com.pulumi.azurenative.documentdb.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .accountName("ddb1")
            .instanceCount(1)
            .instanceSize("Cosmos.D4s")
            .resourceGroupName("rg1")
            .serviceName("MaterializedViewsBuilder")
            .serviceType("MaterializedViewsBuilder")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.documentdb.Service("service", {
    accountName: "ddb1",
    instanceCount: 1,
    instanceSize: "Cosmos.D4s",
    resourceGroupName: "rg1",
    serviceName: "MaterializedViewsBuilder",
    serviceType: "MaterializedViewsBuilder",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.documentdb.Service("service",
    account_name="ddb1",
    instance_count=1,
    instance_size="Cosmos.D4s",
    resource_group_name="rg1",
    service_name="MaterializedViewsBuilder",
    service_type="MaterializedViewsBuilder")

```

```yaml
resources:
  service:
    type: azure-native:documentdb:Service
    properties:
      accountName: ddb1
      instanceCount: 1
      instanceSize: Cosmos.D4s
      resourceGroupName: rg1
      serviceName: MaterializedViewsBuilder
      serviceType: MaterializedViewsBuilder

```

{{% /example %}}
{{% example %}}
### SqlDedicatedGatewayServiceCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.DocumentDB.Service("service", new()
    {
        AccountName = "ddb1",
        InstanceCount = 1,
        InstanceSize = "Cosmos.D4s",
        ResourceGroupName = "rg1",
        ServiceName = "SqlDedicatedGateway",
        ServiceType = "SqlDedicatedGateway",
    });

});


```

```go
package main

import (
	documentdb "github.com/pulumi/pulumi-azure-native-sdk/documentdb"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := documentdb.NewService(ctx, "service", &documentdb.ServiceArgs{
			AccountName:       pulumi.String("ddb1"),
			InstanceCount:     pulumi.Int(1),
			InstanceSize:      pulumi.String("Cosmos.D4s"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("SqlDedicatedGateway"),
			ServiceType:       pulumi.String("SqlDedicatedGateway"),
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
import com.pulumi.azurenative.documentdb.Service;
import com.pulumi.azurenative.documentdb.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .accountName("ddb1")
            .instanceCount(1)
            .instanceSize("Cosmos.D4s")
            .resourceGroupName("rg1")
            .serviceName("SqlDedicatedGateway")
            .serviceType("SqlDedicatedGateway")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.documentdb.Service("service", {
    accountName: "ddb1",
    instanceCount: 1,
    instanceSize: "Cosmos.D4s",
    resourceGroupName: "rg1",
    serviceName: "SqlDedicatedGateway",
    serviceType: "SqlDedicatedGateway",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.documentdb.Service("service",
    account_name="ddb1",
    instance_count=1,
    instance_size="Cosmos.D4s",
    resource_group_name="rg1",
    service_name="SqlDedicatedGateway",
    service_type="SqlDedicatedGateway")

```

```yaml
resources:
  service:
    type: azure-native:documentdb:Service
    properties:
      accountName: ddb1
      instanceCount: 1
      instanceSize: Cosmos.D4s
      resourceGroupName: rg1
      serviceName: SqlDedicatedGateway
      serviceType: SqlDedicatedGateway

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:Service SqlDedicatedGateway /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DocumentDB/databaseAccounts/ddb1/services/SqlDedicatedGateway 
```
