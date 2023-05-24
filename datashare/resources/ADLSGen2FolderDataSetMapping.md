An ADLS Gen2 folder data set mapping.
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
    var adlsGen2FolderDataSetMapping = new AzureNative.DataShare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", new()
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
		_, err := datashare.NewADLSGen2FolderDataSetMapping(ctx, "adlsGen2FolderDataSetMapping", &datashare.ADLSGen2FolderDataSetMappingArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetMapping;
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetMappingArgs;
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
        var adlsGen2FolderDataSetMapping = new ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", ADLSGen2FolderDataSetMappingArgs.builder()        
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

const adlsGen2FolderDataSetMapping = new azure_native.datashare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", {
    accountName: "Account1",
    dataSetMappingName: "DatasetMapping1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_folder_data_set_mapping = azure_native.datashare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping",
    account_name="Account1",
    data_set_mapping_name="DatasetMapping1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  adlsGen2FolderDataSetMapping:
    type: azure-native:datashare:ADLSGen2FolderDataSetMapping
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
    var adlsGen2FolderDataSetMapping = new AzureNative.DataShare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", new()
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
		_, err := datashare.NewADLSGen2FolderDataSetMapping(ctx, "adlsGen2FolderDataSetMapping", &datashare.ADLSGen2FolderDataSetMappingArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetMapping;
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetMappingArgs;
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
        var adlsGen2FolderDataSetMapping = new ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", ADLSGen2FolderDataSetMappingArgs.builder()        
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

const adlsGen2FolderDataSetMapping = new azure_native.datashare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", {
    accountName: "Account1",
    dataSetMappingName: "DatasetMapping1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_folder_data_set_mapping = azure_native.datashare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping",
    account_name="Account1",
    data_set_mapping_name="DatasetMapping1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  adlsGen2FolderDataSetMapping:
    type: azure-native:datashare:ADLSGen2FolderDataSetMapping
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
    var adlsGen2FolderDataSetMapping = new AzureNative.DataShare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", new()
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
		_, err := datashare.NewADLSGen2FolderDataSetMapping(ctx, "adlsGen2FolderDataSetMapping", &datashare.ADLSGen2FolderDataSetMappingArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetMapping;
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetMappingArgs;
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
        var adlsGen2FolderDataSetMapping = new ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", ADLSGen2FolderDataSetMappingArgs.builder()        
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

const adlsGen2FolderDataSetMapping = new azure_native.datashare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", {
    accountName: "Account1",
    dataSetMappingName: "DatasetMapping1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_folder_data_set_mapping = azure_native.datashare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping",
    account_name="Account1",
    data_set_mapping_name="DatasetMapping1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  adlsGen2FolderDataSetMapping:
    type: azure-native:datashare:ADLSGen2FolderDataSetMapping
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
    var adlsGen2FolderDataSetMapping = new AzureNative.DataShare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", new()
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
		_, err := datashare.NewADLSGen2FolderDataSetMapping(ctx, "adlsGen2FolderDataSetMapping", &datashare.ADLSGen2FolderDataSetMappingArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetMapping;
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetMappingArgs;
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
        var adlsGen2FolderDataSetMapping = new ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", ADLSGen2FolderDataSetMappingArgs.builder()        
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

const adlsGen2FolderDataSetMapping = new azure_native.datashare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", {
    accountName: "Account1",
    dataSetMappingName: "DatasetMapping1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_folder_data_set_mapping = azure_native.datashare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping",
    account_name="Account1",
    data_set_mapping_name="DatasetMapping1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  adlsGen2FolderDataSetMapping:
    type: azure-native:datashare:ADLSGen2FolderDataSetMapping
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
    var adlsGen2FolderDataSetMapping = new AzureNative.DataShare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", new()
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
		_, err := datashare.NewADLSGen2FolderDataSetMapping(ctx, "adlsGen2FolderDataSetMapping", &datashare.ADLSGen2FolderDataSetMappingArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetMapping;
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetMappingArgs;
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
        var adlsGen2FolderDataSetMapping = new ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", ADLSGen2FolderDataSetMappingArgs.builder()        
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

const adlsGen2FolderDataSetMapping = new azure_native.datashare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping", {
    accountName: "consumerAccount",
    dataSetMappingName: "datasetMappingName1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_folder_data_set_mapping = azure_native.datashare.ADLSGen2FolderDataSetMapping("adlsGen2FolderDataSetMapping",
    account_name="consumerAccount",
    data_set_mapping_name="datasetMappingName1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  adlsGen2FolderDataSetMapping:
    type: azure-native:datashare:ADLSGen2FolderDataSetMapping
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
$ pulumi import azure-native:datashare:ADLSGen2FolderDataSetMapping datasetMappingName /subscriptions/4e745bb7-c420-479b-b0d6-a0f92d48a227/resourceGroups/SampleResourceGroup/providers/Microsoft.DataShare/accounts/consumerAccount/shareSubscriptions/ShareSubscription1/dataSetMappings/datasetMappingName1 
```
