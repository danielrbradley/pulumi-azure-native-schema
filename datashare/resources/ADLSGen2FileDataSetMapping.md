An ADLS Gen2 file data set mapping.
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
    var adlsGen2FileDataSetMapping = new AzureNative.DataShare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", new()
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
		_, err := datashare.NewADLSGen2FileDataSetMapping(ctx, "adlsGen2FileDataSetMapping", &datashare.ADLSGen2FileDataSetMappingArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FileDataSetMapping;
import com.pulumi.azurenative.datashare.ADLSGen2FileDataSetMappingArgs;
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
        var adlsGen2FileDataSetMapping = new ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", ADLSGen2FileDataSetMappingArgs.builder()        
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

const adlsGen2FileDataSetMapping = new azure_native.datashare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", {
    accountName: "Account1",
    dataSetMappingName: "DatasetMapping1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_file_data_set_mapping = azure_native.datashare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping",
    account_name="Account1",
    data_set_mapping_name="DatasetMapping1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  adlsGen2FileDataSetMapping:
    type: azure-native:datashare:ADLSGen2FileDataSetMapping
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
    var adlsGen2FileDataSetMapping = new AzureNative.DataShare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", new()
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
		_, err := datashare.NewADLSGen2FileDataSetMapping(ctx, "adlsGen2FileDataSetMapping", &datashare.ADLSGen2FileDataSetMappingArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FileDataSetMapping;
import com.pulumi.azurenative.datashare.ADLSGen2FileDataSetMappingArgs;
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
        var adlsGen2FileDataSetMapping = new ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", ADLSGen2FileDataSetMappingArgs.builder()        
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

const adlsGen2FileDataSetMapping = new azure_native.datashare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", {
    accountName: "Account1",
    dataSetMappingName: "DatasetMapping1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_file_data_set_mapping = azure_native.datashare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping",
    account_name="Account1",
    data_set_mapping_name="DatasetMapping1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  adlsGen2FileDataSetMapping:
    type: azure-native:datashare:ADLSGen2FileDataSetMapping
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
    var adlsGen2FileDataSetMapping = new AzureNative.DataShare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", new()
    {
        AccountName = "Account1",
        DataSetId = "a08f184b-0567-4b11-ba22-a1199336d226",
        DataSetMappingName = "DatasetMapping1",
        FilePath = "file21",
        FileSystem = "fileSystem",
        Kind = "AdlsGen2File",
        OutputType = "Csv",
        ResourceGroup = "SampleResourceGroup",
        ResourceGroupName = "SampleResourceGroup",
        ShareSubscriptionName = "ShareSubscription1",
        StorageAccountName = "storage2",
        SubscriptionId = "433a8dfd-e5d5-4e77-ad86-90acdc75eb1a",
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
		_, err := datashare.NewADLSGen2FileDataSetMapping(ctx, "adlsGen2FileDataSetMapping", &datashare.ADLSGen2FileDataSetMappingArgs{
			AccountName:           pulumi.String("Account1"),
			DataSetId:             pulumi.String("a08f184b-0567-4b11-ba22-a1199336d226"),
			DataSetMappingName:    pulumi.String("DatasetMapping1"),
			FilePath:              pulumi.String("file21"),
			FileSystem:            pulumi.String("fileSystem"),
			Kind:                  pulumi.String("AdlsGen2File"),
			OutputType:            pulumi.String("Csv"),
			ResourceGroup:         pulumi.String("SampleResourceGroup"),
			ResourceGroupName:     pulumi.String("SampleResourceGroup"),
			ShareSubscriptionName: pulumi.String("ShareSubscription1"),
			StorageAccountName:    pulumi.String("storage2"),
			SubscriptionId:        pulumi.String("433a8dfd-e5d5-4e77-ad86-90acdc75eb1a"),
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
import com.pulumi.azurenative.datashare.ADLSGen2FileDataSetMapping;
import com.pulumi.azurenative.datashare.ADLSGen2FileDataSetMappingArgs;
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
        var adlsGen2FileDataSetMapping = new ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", ADLSGen2FileDataSetMappingArgs.builder()        
            .accountName("Account1")
            .dataSetId("a08f184b-0567-4b11-ba22-a1199336d226")
            .dataSetMappingName("DatasetMapping1")
            .filePath("file21")
            .fileSystem("fileSystem")
            .kind("AdlsGen2File")
            .outputType("Csv")
            .resourceGroup("SampleResourceGroup")
            .resourceGroupName("SampleResourceGroup")
            .shareSubscriptionName("ShareSubscription1")
            .storageAccountName("storage2")
            .subscriptionId("433a8dfd-e5d5-4e77-ad86-90acdc75eb1a")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const adlsGen2FileDataSetMapping = new azure_native.datashare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", {
    accountName: "Account1",
    dataSetId: "a08f184b-0567-4b11-ba22-a1199336d226",
    dataSetMappingName: "DatasetMapping1",
    filePath: "file21",
    fileSystem: "fileSystem",
    kind: "AdlsGen2File",
    outputType: "Csv",
    resourceGroup: "SampleResourceGroup",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
    storageAccountName: "storage2",
    subscriptionId: "433a8dfd-e5d5-4e77-ad86-90acdc75eb1a",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_file_data_set_mapping = azure_native.datashare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping",
    account_name="Account1",
    data_set_id="a08f184b-0567-4b11-ba22-a1199336d226",
    data_set_mapping_name="DatasetMapping1",
    file_path="file21",
    file_system="fileSystem",
    kind="AdlsGen2File",
    output_type="Csv",
    resource_group="SampleResourceGroup",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1",
    storage_account_name="storage2",
    subscription_id="433a8dfd-e5d5-4e77-ad86-90acdc75eb1a")

```

```yaml
resources:
  adlsGen2FileDataSetMapping:
    type: azure-native:datashare:ADLSGen2FileDataSetMapping
    properties:
      accountName: Account1
      dataSetId: a08f184b-0567-4b11-ba22-a1199336d226
      dataSetMappingName: DatasetMapping1
      filePath: file21
      fileSystem: fileSystem
      kind: AdlsGen2File
      outputType: Csv
      resourceGroup: SampleResourceGroup
      resourceGroupName: SampleResourceGroup
      shareSubscriptionName: ShareSubscription1
      storageAccountName: storage2
      subscriptionId: 433a8dfd-e5d5-4e77-ad86-90acdc75eb1a

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
    var adlsGen2FileDataSetMapping = new AzureNative.DataShare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", new()
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
		_, err := datashare.NewADLSGen2FileDataSetMapping(ctx, "adlsGen2FileDataSetMapping", &datashare.ADLSGen2FileDataSetMappingArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FileDataSetMapping;
import com.pulumi.azurenative.datashare.ADLSGen2FileDataSetMappingArgs;
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
        var adlsGen2FileDataSetMapping = new ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", ADLSGen2FileDataSetMappingArgs.builder()        
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

const adlsGen2FileDataSetMapping = new azure_native.datashare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", {
    accountName: "Account1",
    dataSetMappingName: "DatasetMapping1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_file_data_set_mapping = azure_native.datashare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping",
    account_name="Account1",
    data_set_mapping_name="DatasetMapping1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  adlsGen2FileDataSetMapping:
    type: azure-native:datashare:ADLSGen2FileDataSetMapping
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
    var adlsGen2FileDataSetMapping = new AzureNative.DataShare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", new()
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
		_, err := datashare.NewADLSGen2FileDataSetMapping(ctx, "adlsGen2FileDataSetMapping", &datashare.ADLSGen2FileDataSetMappingArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FileDataSetMapping;
import com.pulumi.azurenative.datashare.ADLSGen2FileDataSetMappingArgs;
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
        var adlsGen2FileDataSetMapping = new ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", ADLSGen2FileDataSetMappingArgs.builder()        
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

const adlsGen2FileDataSetMapping = new azure_native.datashare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping", {
    accountName: "consumerAccount",
    dataSetMappingName: "datasetMappingName1",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_file_data_set_mapping = azure_native.datashare.ADLSGen2FileDataSetMapping("adlsGen2FileDataSetMapping",
    account_name="consumerAccount",
    data_set_mapping_name="datasetMappingName1",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1")

```

```yaml
resources:
  adlsGen2FileDataSetMapping:
    type: azure-native:datashare:ADLSGen2FileDataSetMapping
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
$ pulumi import azure-native:datashare:ADLSGen2FileDataSetMapping datasetMappingName /subscriptions/4e745bb7-c420-479b-b0d6-a0f92d48a227/resourceGroups/SampleResourceGroup/providers/Microsoft.DataShare/accounts/consumerAccount/shareSubscriptions/ShareSubscription1/dataSetMappings/datasetMappingName1 
```
