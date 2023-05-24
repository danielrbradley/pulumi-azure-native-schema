A SQL DW Table data set mapping.
API Version: 2021-08-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DataSetMappings_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlDWTableDataSetMapping = new AzureNative.DataShare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", new()
    {
        AccountName = "Account1",
        DataSetMappingName = "DatasetMapping1",
        ResourceGroupName = "SampleResourceGroup",
        ShareSubscriptionName = "ShareSubscription1",
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
		_, err := datashare.NewSqlDWTableDataSetMapping(ctx, "sqlDWTableDataSetMapping", &datashare.SqlDWTableDataSetMappingArgs{
			AccountName:           pulumi.String("Account1"),
			DataSetMappingName:    pulumi.String("DatasetMapping1"),
			ResourceGroupName:     pulumi.String("SampleResourceGroup"),
			ShareSubscriptionName: pulumi.String("ShareSubscription1"),
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
import com.pulumi.azurenative.datashare.SqlDWTableDataSetMapping;
import com.pulumi.azurenative.datashare.SqlDWTableDataSetMappingArgs;
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
        var sqlDWTableDataSetMapping = new SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", SqlDWTableDataSetMappingArgs.builder()        
            .accountName("Account1")
            .dataSetMappingName("DatasetMapping1")
            .resourceGroupName("SampleResourceGroup")
            .shareSubscriptionName("ShareSubscription1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlDWTableDataSetMapping = new azure_native.datashare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", {
    accountName: "Account1",
    dataSetMappingName: "DatasetMapping1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_dw_table_data_set_mapping = azure_native.datashare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping",
    account_name="Account1",
    data_set_mapping_name="DatasetMapping1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  sqlDWTableDataSetMapping:
    type: azure-native:datashare:SqlDWTableDataSetMapping
    properties:
      accountName: Account1
      dataSetMappingName: DatasetMapping1
      resourceGroupName: SampleResourceGroup
      shareSubscriptionName: ShareSubscription1

```

{{% /example %}}
{{% example %}}
### DataSetMappings_SqlDB_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlDWTableDataSetMapping = new AzureNative.DataShare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", new()
    {
        AccountName = "Account1",
        DataSetMappingName = "DatasetMapping1",
        ResourceGroupName = "SampleResourceGroup",
        ShareSubscriptionName = "ShareSubscription1",
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
		_, err := datashare.NewSqlDWTableDataSetMapping(ctx, "sqlDWTableDataSetMapping", &datashare.SqlDWTableDataSetMappingArgs{
			AccountName:           pulumi.String("Account1"),
			DataSetMappingName:    pulumi.String("DatasetMapping1"),
			ResourceGroupName:     pulumi.String("SampleResourceGroup"),
			ShareSubscriptionName: pulumi.String("ShareSubscription1"),
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
import com.pulumi.azurenative.datashare.SqlDWTableDataSetMapping;
import com.pulumi.azurenative.datashare.SqlDWTableDataSetMappingArgs;
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
        var sqlDWTableDataSetMapping = new SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", SqlDWTableDataSetMappingArgs.builder()        
            .accountName("Account1")
            .dataSetMappingName("DatasetMapping1")
            .resourceGroupName("SampleResourceGroup")
            .shareSubscriptionName("ShareSubscription1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlDWTableDataSetMapping = new azure_native.datashare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", {
    accountName: "Account1",
    dataSetMappingName: "DatasetMapping1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_dw_table_data_set_mapping = azure_native.datashare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping",
    account_name="Account1",
    data_set_mapping_name="DatasetMapping1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  sqlDWTableDataSetMapping:
    type: azure-native:datashare:SqlDWTableDataSetMapping
    properties:
      accountName: Account1
      dataSetMappingName: DatasetMapping1
      resourceGroupName: SampleResourceGroup
      shareSubscriptionName: ShareSubscription1

```

{{% /example %}}
{{% example %}}
### DataSetMappings_SqlDWDataSetToAdlsGen2File_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlDWTableDataSetMapping = new AzureNative.DataShare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", new()
    {
        AccountName = "Account1",
        DataSetMappingName = "DatasetMapping1",
        ResourceGroupName = "SampleResourceGroup",
        ShareSubscriptionName = "ShareSubscription1",
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
		_, err := datashare.NewSqlDWTableDataSetMapping(ctx, "sqlDWTableDataSetMapping", &datashare.SqlDWTableDataSetMappingArgs{
			AccountName:           pulumi.String("Account1"),
			DataSetMappingName:    pulumi.String("DatasetMapping1"),
			ResourceGroupName:     pulumi.String("SampleResourceGroup"),
			ShareSubscriptionName: pulumi.String("ShareSubscription1"),
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
import com.pulumi.azurenative.datashare.SqlDWTableDataSetMapping;
import com.pulumi.azurenative.datashare.SqlDWTableDataSetMappingArgs;
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
        var sqlDWTableDataSetMapping = new SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", SqlDWTableDataSetMappingArgs.builder()        
            .accountName("Account1")
            .dataSetMappingName("DatasetMapping1")
            .resourceGroupName("SampleResourceGroup")
            .shareSubscriptionName("ShareSubscription1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlDWTableDataSetMapping = new azure_native.datashare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", {
    accountName: "Account1",
    dataSetMappingName: "DatasetMapping1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_dw_table_data_set_mapping = azure_native.datashare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping",
    account_name="Account1",
    data_set_mapping_name="DatasetMapping1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  sqlDWTableDataSetMapping:
    type: azure-native:datashare:SqlDWTableDataSetMapping
    properties:
      accountName: Account1
      dataSetMappingName: DatasetMapping1
      resourceGroupName: SampleResourceGroup
      shareSubscriptionName: ShareSubscription1

```

{{% /example %}}
{{% example %}}
### DataSetMappings_SqlDW_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlDWTableDataSetMapping = new AzureNative.DataShare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", new()
    {
        AccountName = "Account1",
        DataSetId = "a08f184b-0567-4b11-ba22-a1199336d226",
        DataSetMappingName = "DatasetMapping1",
        DataWarehouseName = "DataWarehouse1",
        Kind = "SqlDWTable",
        ResourceGroupName = "SampleResourceGroup",
        SchemaName = "dbo",
        ShareSubscriptionName = "ShareSubscription1",
        SqlServerResourceId = "/subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.Sql/servers/Server1",
        TableName = "Table1",
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
		_, err := datashare.NewSqlDWTableDataSetMapping(ctx, "sqlDWTableDataSetMapping", &datashare.SqlDWTableDataSetMappingArgs{
			AccountName:           pulumi.String("Account1"),
			DataSetId:             pulumi.String("a08f184b-0567-4b11-ba22-a1199336d226"),
			DataSetMappingName:    pulumi.String("DatasetMapping1"),
			DataWarehouseName:     pulumi.String("DataWarehouse1"),
			Kind:                  pulumi.String("SqlDWTable"),
			ResourceGroupName:     pulumi.String("SampleResourceGroup"),
			SchemaName:            pulumi.String("dbo"),
			ShareSubscriptionName: pulumi.String("ShareSubscription1"),
			SqlServerResourceId:   pulumi.String("/subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.Sql/servers/Server1"),
			TableName:             pulumi.String("Table1"),
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
import com.pulumi.azurenative.datashare.SqlDWTableDataSetMapping;
import com.pulumi.azurenative.datashare.SqlDWTableDataSetMappingArgs;
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
        var sqlDWTableDataSetMapping = new SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", SqlDWTableDataSetMappingArgs.builder()        
            .accountName("Account1")
            .dataSetId("a08f184b-0567-4b11-ba22-a1199336d226")
            .dataSetMappingName("DatasetMapping1")
            .dataWarehouseName("DataWarehouse1")
            .kind("SqlDWTable")
            .resourceGroupName("SampleResourceGroup")
            .schemaName("dbo")
            .shareSubscriptionName("ShareSubscription1")
            .sqlServerResourceId("/subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.Sql/servers/Server1")
            .tableName("Table1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlDWTableDataSetMapping = new azure_native.datashare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", {
    accountName: "Account1",
    dataSetId: "a08f184b-0567-4b11-ba22-a1199336d226",
    dataSetMappingName: "DatasetMapping1",
    dataWarehouseName: "DataWarehouse1",
    kind: "SqlDWTable",
    resourceGroupName: "SampleResourceGroup",
    schemaName: "dbo",
    shareSubscriptionName: "ShareSubscription1",
    sqlServerResourceId: "/subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.Sql/servers/Server1",
    tableName: "Table1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_dw_table_data_set_mapping = azure_native.datashare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping",
    account_name="Account1",
    data_set_id="a08f184b-0567-4b11-ba22-a1199336d226",
    data_set_mapping_name="DatasetMapping1",
    data_warehouse_name="DataWarehouse1",
    kind="SqlDWTable",
    resource_group_name="SampleResourceGroup",
    schema_name="dbo",
    share_subscription_name="ShareSubscription1",
    sql_server_resource_id="/subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.Sql/servers/Server1",
    table_name="Table1")

```

```yaml
resources:
  sqlDWTableDataSetMapping:
    type: azure-native:datashare:SqlDWTableDataSetMapping
    properties:
      accountName: Account1
      dataSetId: a08f184b-0567-4b11-ba22-a1199336d226
      dataSetMappingName: DatasetMapping1
      dataWarehouseName: DataWarehouse1
      kind: SqlDWTable
      resourceGroupName: SampleResourceGroup
      schemaName: dbo
      shareSubscriptionName: ShareSubscription1
      sqlServerResourceId: /subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.Sql/servers/Server1
      tableName: Table1

```

{{% /example %}}
{{% example %}}
### DataSetMappings_SynapseWorkspaceSqlPoolTable_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlDWTableDataSetMapping = new AzureNative.DataShare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", new()
    {
        AccountName = "consumerAccount",
        DataSetMappingName = "datasetMappingName1",
        ResourceGroupName = "SampleResourceGroup",
        ShareSubscriptionName = "ShareSubscription1",
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
		_, err := datashare.NewSqlDWTableDataSetMapping(ctx, "sqlDWTableDataSetMapping", &datashare.SqlDWTableDataSetMappingArgs{
			AccountName:           pulumi.String("consumerAccount"),
			DataSetMappingName:    pulumi.String("datasetMappingName1"),
			ResourceGroupName:     pulumi.String("SampleResourceGroup"),
			ShareSubscriptionName: pulumi.String("ShareSubscription1"),
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
import com.pulumi.azurenative.datashare.SqlDWTableDataSetMapping;
import com.pulumi.azurenative.datashare.SqlDWTableDataSetMappingArgs;
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
        var sqlDWTableDataSetMapping = new SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", SqlDWTableDataSetMappingArgs.builder()        
            .accountName("consumerAccount")
            .dataSetMappingName("datasetMappingName1")
            .resourceGroupName("SampleResourceGroup")
            .shareSubscriptionName("ShareSubscription1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlDWTableDataSetMapping = new azure_native.datashare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping", {
    accountName: "consumerAccount",
    dataSetMappingName: "datasetMappingName1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_dw_table_data_set_mapping = azure_native.datashare.SqlDWTableDataSetMapping("sqlDWTableDataSetMapping",
    account_name="consumerAccount",
    data_set_mapping_name="datasetMappingName1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  sqlDWTableDataSetMapping:
    type: azure-native:datashare:SqlDWTableDataSetMapping
    properties:
      accountName: consumerAccount
      dataSetMappingName: datasetMappingName1
      resourceGroupName: SampleResourceGroup
      shareSubscriptionName: ShareSubscription1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datashare:SqlDWTableDataSetMapping datasetMappingName /subscriptions/4e745bb7-c420-479b-b0d6-a0f92d48a227/resourceGroups/SampleResourceGroup/providers/Microsoft.DataShare/accounts/consumerAccount/shareSubscriptions/ShareSubscription1/dataSetMappings/datasetMappingName1 
```
