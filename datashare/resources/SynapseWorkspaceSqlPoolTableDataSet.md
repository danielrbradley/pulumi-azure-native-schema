A Synapse Workspace Sql Pool Table data set.
API Version: 2021-08-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DataSets_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var synapseWorkspaceSqlPoolTableDataSet = new AzureNative.DataShare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", new()
    {
        AccountName = "Account1",
        DataSetName = "Dataset1",
        ResourceGroupName = "SampleResourceGroup",
        ShareName = "Share1",
    });

});


```

```go
package main

import (
	datashare "github.com/pulumi/pulumi-azure-native-sdk/datashare"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datashare.NewSynapseWorkspaceSqlPoolTableDataSet(ctx, "synapseWorkspaceSqlPoolTableDataSet", &datashare.SynapseWorkspaceSqlPoolTableDataSetArgs{
			AccountName:       pulumi.String("Account1"),
			DataSetName:       pulumi.String("Dataset1"),
			ResourceGroupName: pulumi.String("SampleResourceGroup"),
			ShareName:         pulumi.String("Share1"),
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
import com.pulumi.azurenative.datashare.SynapseWorkspaceSqlPoolTableDataSet;
import com.pulumi.azurenative.datashare.SynapseWorkspaceSqlPoolTableDataSetArgs;
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
        var synapseWorkspaceSqlPoolTableDataSet = new SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", SynapseWorkspaceSqlPoolTableDataSetArgs.builder()        
            .accountName("Account1")
            .dataSetName("Dataset1")
            .resourceGroupName("SampleResourceGroup")
            .shareName("Share1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const synapseWorkspaceSqlPoolTableDataSet = new azure_native.datashare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

synapse_workspace_sql_pool_table_data_set = azure_native.datashare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  synapseWorkspaceSqlPoolTableDataSet:
    type: azure-native:datashare:SynapseWorkspaceSqlPoolTableDataSet
    properties:
      accountName: Account1
      dataSetName: Dataset1
      resourceGroupName: SampleResourceGroup
      shareName: Share1

```

{{% /example %}}
{{% example %}}
### DataSets_KustoCluster_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var synapseWorkspaceSqlPoolTableDataSet = new AzureNative.DataShare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", new()
    {
        AccountName = "Account1",
        DataSetName = "Dataset1",
        ResourceGroupName = "SampleResourceGroup",
        ShareName = "Share1",
    });

});


```

```go
package main

import (
	datashare "github.com/pulumi/pulumi-azure-native-sdk/datashare"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datashare.NewSynapseWorkspaceSqlPoolTableDataSet(ctx, "synapseWorkspaceSqlPoolTableDataSet", &datashare.SynapseWorkspaceSqlPoolTableDataSetArgs{
			AccountName:       pulumi.String("Account1"),
			DataSetName:       pulumi.String("Dataset1"),
			ResourceGroupName: pulumi.String("SampleResourceGroup"),
			ShareName:         pulumi.String("Share1"),
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
import com.pulumi.azurenative.datashare.SynapseWorkspaceSqlPoolTableDataSet;
import com.pulumi.azurenative.datashare.SynapseWorkspaceSqlPoolTableDataSetArgs;
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
        var synapseWorkspaceSqlPoolTableDataSet = new SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", SynapseWorkspaceSqlPoolTableDataSetArgs.builder()        
            .accountName("Account1")
            .dataSetName("Dataset1")
            .resourceGroupName("SampleResourceGroup")
            .shareName("Share1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const synapseWorkspaceSqlPoolTableDataSet = new azure_native.datashare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

synapse_workspace_sql_pool_table_data_set = azure_native.datashare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  synapseWorkspaceSqlPoolTableDataSet:
    type: azure-native:datashare:SynapseWorkspaceSqlPoolTableDataSet
    properties:
      accountName: Account1
      dataSetName: Dataset1
      resourceGroupName: SampleResourceGroup
      shareName: Share1

```

{{% /example %}}
{{% example %}}
### DataSets_KustoDatabase_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var synapseWorkspaceSqlPoolTableDataSet = new AzureNative.DataShare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", new()
    {
        AccountName = "Account1",
        DataSetName = "Dataset1",
        ResourceGroupName = "SampleResourceGroup",
        ShareName = "Share1",
    });

});


```

```go
package main

import (
	datashare "github.com/pulumi/pulumi-azure-native-sdk/datashare"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datashare.NewSynapseWorkspaceSqlPoolTableDataSet(ctx, "synapseWorkspaceSqlPoolTableDataSet", &datashare.SynapseWorkspaceSqlPoolTableDataSetArgs{
			AccountName:       pulumi.String("Account1"),
			DataSetName:       pulumi.String("Dataset1"),
			ResourceGroupName: pulumi.String("SampleResourceGroup"),
			ShareName:         pulumi.String("Share1"),
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
import com.pulumi.azurenative.datashare.SynapseWorkspaceSqlPoolTableDataSet;
import com.pulumi.azurenative.datashare.SynapseWorkspaceSqlPoolTableDataSetArgs;
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
        var synapseWorkspaceSqlPoolTableDataSet = new SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", SynapseWorkspaceSqlPoolTableDataSetArgs.builder()        
            .accountName("Account1")
            .dataSetName("Dataset1")
            .resourceGroupName("SampleResourceGroup")
            .shareName("Share1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const synapseWorkspaceSqlPoolTableDataSet = new azure_native.datashare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

synapse_workspace_sql_pool_table_data_set = azure_native.datashare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  synapseWorkspaceSqlPoolTableDataSet:
    type: azure-native:datashare:SynapseWorkspaceSqlPoolTableDataSet
    properties:
      accountName: Account1
      dataSetName: Dataset1
      resourceGroupName: SampleResourceGroup
      shareName: Share1

```

{{% /example %}}
{{% example %}}
### DataSets_KustoTable_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var synapseWorkspaceSqlPoolTableDataSet = new AzureNative.DataShare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", new()
    {
        AccountName = "Account1",
        DataSetName = "Dataset1",
        ResourceGroupName = "SampleResourceGroup",
        ShareName = "Share1",
    });

});


```

```go
package main

import (
	datashare "github.com/pulumi/pulumi-azure-native-sdk/datashare"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datashare.NewSynapseWorkspaceSqlPoolTableDataSet(ctx, "synapseWorkspaceSqlPoolTableDataSet", &datashare.SynapseWorkspaceSqlPoolTableDataSetArgs{
			AccountName:       pulumi.String("Account1"),
			DataSetName:       pulumi.String("Dataset1"),
			ResourceGroupName: pulumi.String("SampleResourceGroup"),
			ShareName:         pulumi.String("Share1"),
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
import com.pulumi.azurenative.datashare.SynapseWorkspaceSqlPoolTableDataSet;
import com.pulumi.azurenative.datashare.SynapseWorkspaceSqlPoolTableDataSetArgs;
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
        var synapseWorkspaceSqlPoolTableDataSet = new SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", SynapseWorkspaceSqlPoolTableDataSetArgs.builder()        
            .accountName("Account1")
            .dataSetName("Dataset1")
            .resourceGroupName("SampleResourceGroup")
            .shareName("Share1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const synapseWorkspaceSqlPoolTableDataSet = new azure_native.datashare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

synapse_workspace_sql_pool_table_data_set = azure_native.datashare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  synapseWorkspaceSqlPoolTableDataSet:
    type: azure-native:datashare:SynapseWorkspaceSqlPoolTableDataSet
    properties:
      accountName: Account1
      dataSetName: Dataset1
      resourceGroupName: SampleResourceGroup
      shareName: Share1

```

{{% /example %}}
{{% example %}}
### DataSets_SqlDBTable_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var synapseWorkspaceSqlPoolTableDataSet = new AzureNative.DataShare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", new()
    {
        AccountName = "Account1",
        DataSetName = "Dataset1",
        ResourceGroupName = "SampleResourceGroup",
        ShareName = "Share1",
    });

});


```

```go
package main

import (
	datashare "github.com/pulumi/pulumi-azure-native-sdk/datashare"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datashare.NewSynapseWorkspaceSqlPoolTableDataSet(ctx, "synapseWorkspaceSqlPoolTableDataSet", &datashare.SynapseWorkspaceSqlPoolTableDataSetArgs{
			AccountName:       pulumi.String("Account1"),
			DataSetName:       pulumi.String("Dataset1"),
			ResourceGroupName: pulumi.String("SampleResourceGroup"),
			ShareName:         pulumi.String("Share1"),
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
import com.pulumi.azurenative.datashare.SynapseWorkspaceSqlPoolTableDataSet;
import com.pulumi.azurenative.datashare.SynapseWorkspaceSqlPoolTableDataSetArgs;
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
        var synapseWorkspaceSqlPoolTableDataSet = new SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", SynapseWorkspaceSqlPoolTableDataSetArgs.builder()        
            .accountName("Account1")
            .dataSetName("Dataset1")
            .resourceGroupName("SampleResourceGroup")
            .shareName("Share1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const synapseWorkspaceSqlPoolTableDataSet = new azure_native.datashare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

synapse_workspace_sql_pool_table_data_set = azure_native.datashare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  synapseWorkspaceSqlPoolTableDataSet:
    type: azure-native:datashare:SynapseWorkspaceSqlPoolTableDataSet
    properties:
      accountName: Account1
      dataSetName: Dataset1
      resourceGroupName: SampleResourceGroup
      shareName: Share1

```

{{% /example %}}
{{% example %}}
### DataSets_SqlDWTable_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var synapseWorkspaceSqlPoolTableDataSet = new AzureNative.DataShare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", new()
    {
        AccountName = "Account1",
        DataSetName = "Dataset1",
        ResourceGroupName = "SampleResourceGroup",
        ShareName = "Share1",
    });

});


```

```go
package main

import (
	datashare "github.com/pulumi/pulumi-azure-native-sdk/datashare"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datashare.NewSynapseWorkspaceSqlPoolTableDataSet(ctx, "synapseWorkspaceSqlPoolTableDataSet", &datashare.SynapseWorkspaceSqlPoolTableDataSetArgs{
			AccountName:       pulumi.String("Account1"),
			DataSetName:       pulumi.String("Dataset1"),
			ResourceGroupName: pulumi.String("SampleResourceGroup"),
			ShareName:         pulumi.String("Share1"),
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
import com.pulumi.azurenative.datashare.SynapseWorkspaceSqlPoolTableDataSet;
import com.pulumi.azurenative.datashare.SynapseWorkspaceSqlPoolTableDataSetArgs;
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
        var synapseWorkspaceSqlPoolTableDataSet = new SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", SynapseWorkspaceSqlPoolTableDataSetArgs.builder()        
            .accountName("Account1")
            .dataSetName("Dataset1")
            .resourceGroupName("SampleResourceGroup")
            .shareName("Share1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const synapseWorkspaceSqlPoolTableDataSet = new azure_native.datashare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

synapse_workspace_sql_pool_table_data_set = azure_native.datashare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  synapseWorkspaceSqlPoolTableDataSet:
    type: azure-native:datashare:SynapseWorkspaceSqlPoolTableDataSet
    properties:
      accountName: Account1
      dataSetName: Dataset1
      resourceGroupName: SampleResourceGroup
      shareName: Share1

```

{{% /example %}}
{{% example %}}
### DataSets_SynapseWorkspaceSqlPoolTable_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var synapseWorkspaceSqlPoolTableDataSet = new AzureNative.DataShare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", new()
    {
        AccountName = "sourceAccount",
        DataSetName = "dataset1",
        Kind = "SynapseWorkspaceSqlPoolTable",
        ResourceGroupName = "SampleResourceGroup",
        ShareName = "share1",
        SynapseWorkspaceSqlPoolTableResourceId = "/subscriptions/0f3dcfc3-18f8-4099-b381-8353e19d43a7/resourceGroups/SampleResourceGroup/providers/Microsoft.Synapse/workspaces/ExampleWorkspace/sqlPools/ExampleSqlPool/schemas/dbo/tables/table1",
    });

});


```

```go
package main

import (
	datashare "github.com/pulumi/pulumi-azure-native-sdk/datashare"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datashare.NewSynapseWorkspaceSqlPoolTableDataSet(ctx, "synapseWorkspaceSqlPoolTableDataSet", &datashare.SynapseWorkspaceSqlPoolTableDataSetArgs{
			AccountName:                            pulumi.String("sourceAccount"),
			DataSetName:                            pulumi.String("dataset1"),
			Kind:                                   pulumi.String("SynapseWorkspaceSqlPoolTable"),
			ResourceGroupName:                      pulumi.String("SampleResourceGroup"),
			ShareName:                              pulumi.String("share1"),
			SynapseWorkspaceSqlPoolTableResourceId: pulumi.String("/subscriptions/0f3dcfc3-18f8-4099-b381-8353e19d43a7/resourceGroups/SampleResourceGroup/providers/Microsoft.Synapse/workspaces/ExampleWorkspace/sqlPools/ExampleSqlPool/schemas/dbo/tables/table1"),
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
import com.pulumi.azurenative.datashare.SynapseWorkspaceSqlPoolTableDataSet;
import com.pulumi.azurenative.datashare.SynapseWorkspaceSqlPoolTableDataSetArgs;
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
        var synapseWorkspaceSqlPoolTableDataSet = new SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", SynapseWorkspaceSqlPoolTableDataSetArgs.builder()        
            .accountName("sourceAccount")
            .dataSetName("dataset1")
            .kind("SynapseWorkspaceSqlPoolTable")
            .resourceGroupName("SampleResourceGroup")
            .shareName("share1")
            .synapseWorkspaceSqlPoolTableResourceId("/subscriptions/0f3dcfc3-18f8-4099-b381-8353e19d43a7/resourceGroups/SampleResourceGroup/providers/Microsoft.Synapse/workspaces/ExampleWorkspace/sqlPools/ExampleSqlPool/schemas/dbo/tables/table1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const synapseWorkspaceSqlPoolTableDataSet = new azure_native.datashare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet", {
    accountName: "sourceAccount",
    dataSetName: "dataset1",
    kind: "SynapseWorkspaceSqlPoolTable",
    resourceGroupName: "SampleResourceGroup",
    shareName: "share1",
    synapseWorkspaceSqlPoolTableResourceId: "/subscriptions/0f3dcfc3-18f8-4099-b381-8353e19d43a7/resourceGroups/SampleResourceGroup/providers/Microsoft.Synapse/workspaces/ExampleWorkspace/sqlPools/ExampleSqlPool/schemas/dbo/tables/table1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

synapse_workspace_sql_pool_table_data_set = azure_native.datashare.SynapseWorkspaceSqlPoolTableDataSet("synapseWorkspaceSqlPoolTableDataSet",
    account_name="sourceAccount",
    data_set_name="dataset1",
    kind="SynapseWorkspaceSqlPoolTable",
    resource_group_name="SampleResourceGroup",
    share_name="share1",
    synapse_workspace_sql_pool_table_resource_id="/subscriptions/0f3dcfc3-18f8-4099-b381-8353e19d43a7/resourceGroups/SampleResourceGroup/providers/Microsoft.Synapse/workspaces/ExampleWorkspace/sqlPools/ExampleSqlPool/schemas/dbo/tables/table1")

```

```yaml
resources:
  synapseWorkspaceSqlPoolTableDataSet:
    type: azure-native:datashare:SynapseWorkspaceSqlPoolTableDataSet
    properties:
      accountName: sourceAccount
      dataSetName: dataset1
      kind: SynapseWorkspaceSqlPoolTable
      resourceGroupName: SampleResourceGroup
      shareName: share1
      synapseWorkspaceSqlPoolTableResourceId: /subscriptions/0f3dcfc3-18f8-4099-b381-8353e19d43a7/resourceGroups/SampleResourceGroup/providers/Microsoft.Synapse/workspaces/ExampleWorkspace/sqlPools/ExampleSqlPool/schemas/dbo/tables/table1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datashare:SynapseWorkspaceSqlPoolTableDataSet dataset1 /subscriptions/0f3dcfc3-18f8-4099-b381-8353e19d43a7/resourceGroups/SampleResourceGroup/providers/Microsoft.DataShare/accounts/sourceAccount/shares/share1/dataSets/dataset1 
```
