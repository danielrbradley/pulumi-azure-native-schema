A Kusto cluster data set mapping
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
    var kustoClusterDataSetMapping = new AzureNative.DataShare.KustoClusterDataSetMapping("kustoClusterDataSetMapping", new()
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
		_, err := datashare.NewKustoClusterDataSetMapping(ctx, "kustoClusterDataSetMapping", &datashare.KustoClusterDataSetMappingArgs{
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
import com.pulumi.azurenative.datashare.KustoClusterDataSetMapping;
import com.pulumi.azurenative.datashare.KustoClusterDataSetMappingArgs;
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
        var kustoClusterDataSetMapping = new KustoClusterDataSetMapping("kustoClusterDataSetMapping", KustoClusterDataSetMappingArgs.builder()        
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

const kustoClusterDataSetMapping = new azure_native.datashare.KustoClusterDataSetMapping("kustoClusterDataSetMapping", {
    accountName: "Account1",
    dataSetMappingName: "DatasetMapping1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kusto_cluster_data_set_mapping = azure_native.datashare.KustoClusterDataSetMapping("kustoClusterDataSetMapping",
    account_name="Account1",
    data_set_mapping_name="DatasetMapping1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  kustoClusterDataSetMapping:
    type: azure-native:datashare:KustoClusterDataSetMapping
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
    var kustoClusterDataSetMapping = new AzureNative.DataShare.KustoClusterDataSetMapping("kustoClusterDataSetMapping", new()
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
		_, err := datashare.NewKustoClusterDataSetMapping(ctx, "kustoClusterDataSetMapping", &datashare.KustoClusterDataSetMappingArgs{
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
import com.pulumi.azurenative.datashare.KustoClusterDataSetMapping;
import com.pulumi.azurenative.datashare.KustoClusterDataSetMappingArgs;
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
        var kustoClusterDataSetMapping = new KustoClusterDataSetMapping("kustoClusterDataSetMapping", KustoClusterDataSetMappingArgs.builder()        
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

const kustoClusterDataSetMapping = new azure_native.datashare.KustoClusterDataSetMapping("kustoClusterDataSetMapping", {
    accountName: "Account1",
    dataSetMappingName: "DatasetMapping1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kusto_cluster_data_set_mapping = azure_native.datashare.KustoClusterDataSetMapping("kustoClusterDataSetMapping",
    account_name="Account1",
    data_set_mapping_name="DatasetMapping1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  kustoClusterDataSetMapping:
    type: azure-native:datashare:KustoClusterDataSetMapping
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
    var kustoClusterDataSetMapping = new AzureNative.DataShare.KustoClusterDataSetMapping("kustoClusterDataSetMapping", new()
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
		_, err := datashare.NewKustoClusterDataSetMapping(ctx, "kustoClusterDataSetMapping", &datashare.KustoClusterDataSetMappingArgs{
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
import com.pulumi.azurenative.datashare.KustoClusterDataSetMapping;
import com.pulumi.azurenative.datashare.KustoClusterDataSetMappingArgs;
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
        var kustoClusterDataSetMapping = new KustoClusterDataSetMapping("kustoClusterDataSetMapping", KustoClusterDataSetMappingArgs.builder()        
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

const kustoClusterDataSetMapping = new azure_native.datashare.KustoClusterDataSetMapping("kustoClusterDataSetMapping", {
    accountName: "Account1",
    dataSetMappingName: "DatasetMapping1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kusto_cluster_data_set_mapping = azure_native.datashare.KustoClusterDataSetMapping("kustoClusterDataSetMapping",
    account_name="Account1",
    data_set_mapping_name="DatasetMapping1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  kustoClusterDataSetMapping:
    type: azure-native:datashare:KustoClusterDataSetMapping
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
    var kustoClusterDataSetMapping = new AzureNative.DataShare.KustoClusterDataSetMapping("kustoClusterDataSetMapping", new()
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
		_, err := datashare.NewKustoClusterDataSetMapping(ctx, "kustoClusterDataSetMapping", &datashare.KustoClusterDataSetMappingArgs{
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
import com.pulumi.azurenative.datashare.KustoClusterDataSetMapping;
import com.pulumi.azurenative.datashare.KustoClusterDataSetMappingArgs;
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
        var kustoClusterDataSetMapping = new KustoClusterDataSetMapping("kustoClusterDataSetMapping", KustoClusterDataSetMappingArgs.builder()        
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

const kustoClusterDataSetMapping = new azure_native.datashare.KustoClusterDataSetMapping("kustoClusterDataSetMapping", {
    accountName: "Account1",
    dataSetMappingName: "DatasetMapping1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kusto_cluster_data_set_mapping = azure_native.datashare.KustoClusterDataSetMapping("kustoClusterDataSetMapping",
    account_name="Account1",
    data_set_mapping_name="DatasetMapping1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  kustoClusterDataSetMapping:
    type: azure-native:datashare:KustoClusterDataSetMapping
    properties:
      accountName: Account1
      dataSetMappingName: DatasetMapping1
      resourceGroupName: SampleResourceGroup
      shareSubscriptionName: ShareSubscription1

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
    var kustoClusterDataSetMapping = new AzureNative.DataShare.KustoClusterDataSetMapping("kustoClusterDataSetMapping", new()
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
		_, err := datashare.NewKustoClusterDataSetMapping(ctx, "kustoClusterDataSetMapping", &datashare.KustoClusterDataSetMappingArgs{
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
import com.pulumi.azurenative.datashare.KustoClusterDataSetMapping;
import com.pulumi.azurenative.datashare.KustoClusterDataSetMappingArgs;
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
        var kustoClusterDataSetMapping = new KustoClusterDataSetMapping("kustoClusterDataSetMapping", KustoClusterDataSetMappingArgs.builder()        
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

const kustoClusterDataSetMapping = new azure_native.datashare.KustoClusterDataSetMapping("kustoClusterDataSetMapping", {
    accountName: "consumerAccount",
    dataSetMappingName: "datasetMappingName1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kusto_cluster_data_set_mapping = azure_native.datashare.KustoClusterDataSetMapping("kustoClusterDataSetMapping",
    account_name="consumerAccount",
    data_set_mapping_name="datasetMappingName1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  kustoClusterDataSetMapping:
    type: azure-native:datashare:KustoClusterDataSetMapping
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
$ pulumi import azure-native:datashare:KustoClusterDataSetMapping datasetMappingName /subscriptions/4e745bb7-c420-479b-b0d6-a0f92d48a227/resourceGroups/SampleResourceGroup/providers/Microsoft.DataShare/accounts/consumerAccount/shareSubscriptions/ShareSubscription1/dataSetMappings/datasetMappingName1 
```
