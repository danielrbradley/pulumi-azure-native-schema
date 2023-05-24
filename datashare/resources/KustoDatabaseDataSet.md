A kusto database data set.
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
    var kustoDatabaseDataSet = new AzureNative.DataShare.KustoDatabaseDataSet("kustoDatabaseDataSet", new()
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
		_, err := datashare.NewKustoDatabaseDataSet(ctx, "kustoDatabaseDataSet", &datashare.KustoDatabaseDataSetArgs{
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
import com.pulumi.azurenative.datashare.KustoDatabaseDataSet;
import com.pulumi.azurenative.datashare.KustoDatabaseDataSetArgs;
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
        var kustoDatabaseDataSet = new KustoDatabaseDataSet("kustoDatabaseDataSet", KustoDatabaseDataSetArgs.builder()        
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

const kustoDatabaseDataSet = new azure_native.datashare.KustoDatabaseDataSet("kustoDatabaseDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kusto_database_data_set = azure_native.datashare.KustoDatabaseDataSet("kustoDatabaseDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  kustoDatabaseDataSet:
    type: azure-native:datashare:KustoDatabaseDataSet
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
    var kustoDatabaseDataSet = new AzureNative.DataShare.KustoDatabaseDataSet("kustoDatabaseDataSet", new()
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
		_, err := datashare.NewKustoDatabaseDataSet(ctx, "kustoDatabaseDataSet", &datashare.KustoDatabaseDataSetArgs{
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
import com.pulumi.azurenative.datashare.KustoDatabaseDataSet;
import com.pulumi.azurenative.datashare.KustoDatabaseDataSetArgs;
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
        var kustoDatabaseDataSet = new KustoDatabaseDataSet("kustoDatabaseDataSet", KustoDatabaseDataSetArgs.builder()        
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

const kustoDatabaseDataSet = new azure_native.datashare.KustoDatabaseDataSet("kustoDatabaseDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kusto_database_data_set = azure_native.datashare.KustoDatabaseDataSet("kustoDatabaseDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  kustoDatabaseDataSet:
    type: azure-native:datashare:KustoDatabaseDataSet
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
    var kustoDatabaseDataSet = new AzureNative.DataShare.KustoDatabaseDataSet("kustoDatabaseDataSet", new()
    {
        AccountName = "Account1",
        DataSetName = "Dataset1",
        Kind = "KustoDatabase",
        KustoDatabaseResourceId = "/subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.Kusto/clusters/Cluster1/databases/Database1",
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
		_, err := datashare.NewKustoDatabaseDataSet(ctx, "kustoDatabaseDataSet", &datashare.KustoDatabaseDataSetArgs{
			AccountName:             pulumi.String("Account1"),
			DataSetName:             pulumi.String("Dataset1"),
			Kind:                    pulumi.String("KustoDatabase"),
			KustoDatabaseResourceId: pulumi.String("/subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.Kusto/clusters/Cluster1/databases/Database1"),
			ResourceGroupName:       pulumi.String("SampleResourceGroup"),
			ShareName:               pulumi.String("Share1"),
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
import com.pulumi.azurenative.datashare.KustoDatabaseDataSet;
import com.pulumi.azurenative.datashare.KustoDatabaseDataSetArgs;
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
        var kustoDatabaseDataSet = new KustoDatabaseDataSet("kustoDatabaseDataSet", KustoDatabaseDataSetArgs.builder()        
            .accountName("Account1")
            .dataSetName("Dataset1")
            .kind("KustoDatabase")
            .kustoDatabaseResourceId("/subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.Kusto/clusters/Cluster1/databases/Database1")
            .resourceGroupName("SampleResourceGroup")
            .shareName("Share1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const kustoDatabaseDataSet = new azure_native.datashare.KustoDatabaseDataSet("kustoDatabaseDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    kind: "KustoDatabase",
    kustoDatabaseResourceId: "/subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.Kusto/clusters/Cluster1/databases/Database1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kusto_database_data_set = azure_native.datashare.KustoDatabaseDataSet("kustoDatabaseDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    kind="KustoDatabase",
    kusto_database_resource_id="/subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.Kusto/clusters/Cluster1/databases/Database1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  kustoDatabaseDataSet:
    type: azure-native:datashare:KustoDatabaseDataSet
    properties:
      accountName: Account1
      dataSetName: Dataset1
      kind: KustoDatabase
      kustoDatabaseResourceId: /subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.Kusto/clusters/Cluster1/databases/Database1
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
    var kustoDatabaseDataSet = new AzureNative.DataShare.KustoDatabaseDataSet("kustoDatabaseDataSet", new()
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
		_, err := datashare.NewKustoDatabaseDataSet(ctx, "kustoDatabaseDataSet", &datashare.KustoDatabaseDataSetArgs{
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
import com.pulumi.azurenative.datashare.KustoDatabaseDataSet;
import com.pulumi.azurenative.datashare.KustoDatabaseDataSetArgs;
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
        var kustoDatabaseDataSet = new KustoDatabaseDataSet("kustoDatabaseDataSet", KustoDatabaseDataSetArgs.builder()        
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

const kustoDatabaseDataSet = new azure_native.datashare.KustoDatabaseDataSet("kustoDatabaseDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kusto_database_data_set = azure_native.datashare.KustoDatabaseDataSet("kustoDatabaseDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  kustoDatabaseDataSet:
    type: azure-native:datashare:KustoDatabaseDataSet
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
    var kustoDatabaseDataSet = new AzureNative.DataShare.KustoDatabaseDataSet("kustoDatabaseDataSet", new()
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
		_, err := datashare.NewKustoDatabaseDataSet(ctx, "kustoDatabaseDataSet", &datashare.KustoDatabaseDataSetArgs{
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
import com.pulumi.azurenative.datashare.KustoDatabaseDataSet;
import com.pulumi.azurenative.datashare.KustoDatabaseDataSetArgs;
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
        var kustoDatabaseDataSet = new KustoDatabaseDataSet("kustoDatabaseDataSet", KustoDatabaseDataSetArgs.builder()        
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

const kustoDatabaseDataSet = new azure_native.datashare.KustoDatabaseDataSet("kustoDatabaseDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kusto_database_data_set = azure_native.datashare.KustoDatabaseDataSet("kustoDatabaseDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  kustoDatabaseDataSet:
    type: azure-native:datashare:KustoDatabaseDataSet
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
    var kustoDatabaseDataSet = new AzureNative.DataShare.KustoDatabaseDataSet("kustoDatabaseDataSet", new()
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
		_, err := datashare.NewKustoDatabaseDataSet(ctx, "kustoDatabaseDataSet", &datashare.KustoDatabaseDataSetArgs{
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
import com.pulumi.azurenative.datashare.KustoDatabaseDataSet;
import com.pulumi.azurenative.datashare.KustoDatabaseDataSetArgs;
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
        var kustoDatabaseDataSet = new KustoDatabaseDataSet("kustoDatabaseDataSet", KustoDatabaseDataSetArgs.builder()        
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

const kustoDatabaseDataSet = new azure_native.datashare.KustoDatabaseDataSet("kustoDatabaseDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kusto_database_data_set = azure_native.datashare.KustoDatabaseDataSet("kustoDatabaseDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  kustoDatabaseDataSet:
    type: azure-native:datashare:KustoDatabaseDataSet
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
    var kustoDatabaseDataSet = new AzureNative.DataShare.KustoDatabaseDataSet("kustoDatabaseDataSet", new()
    {
        AccountName = "sourceAccount",
        DataSetName = "dataset1",
        ResourceGroupName = "SampleResourceGroup",
        ShareName = "share1",
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
		_, err := datashare.NewKustoDatabaseDataSet(ctx, "kustoDatabaseDataSet", &datashare.KustoDatabaseDataSetArgs{
			AccountName:       pulumi.String("sourceAccount"),
			DataSetName:       pulumi.String("dataset1"),
			ResourceGroupName: pulumi.String("SampleResourceGroup"),
			ShareName:         pulumi.String("share1"),
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
import com.pulumi.azurenative.datashare.KustoDatabaseDataSet;
import com.pulumi.azurenative.datashare.KustoDatabaseDataSetArgs;
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
        var kustoDatabaseDataSet = new KustoDatabaseDataSet("kustoDatabaseDataSet", KustoDatabaseDataSetArgs.builder()        
            .accountName("sourceAccount")
            .dataSetName("dataset1")
            .resourceGroupName("SampleResourceGroup")
            .shareName("share1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const kustoDatabaseDataSet = new azure_native.datashare.KustoDatabaseDataSet("kustoDatabaseDataSet", {
    accountName: "sourceAccount",
    dataSetName: "dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kusto_database_data_set = azure_native.datashare.KustoDatabaseDataSet("kustoDatabaseDataSet",
    account_name="sourceAccount",
    data_set_name="dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="share1")

```

```yaml
resources:
  kustoDatabaseDataSet:
    type: azure-native:datashare:KustoDatabaseDataSet
    properties:
      accountName: sourceAccount
      dataSetName: dataset1
      resourceGroupName: SampleResourceGroup
      shareName: share1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datashare:KustoDatabaseDataSet dataset1 /subscriptions/0f3dcfc3-18f8-4099-b381-8353e19d43a7/resourceGroups/SampleResourceGroup/providers/Microsoft.DataShare/accounts/sourceAccount/shares/share1/dataSets/dataset1 
```
