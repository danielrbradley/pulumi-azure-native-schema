An ADLS Gen 2 folder data set.
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
    var adlsGen2FolderDataSet = new AzureNative.DataShare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet", new()
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
		_, err := datashare.NewADLSGen2FolderDataSet(ctx, "adlsGen2FolderDataSet", &datashare.ADLSGen2FolderDataSetArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSet;
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetArgs;
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
        var adlsGen2FolderDataSet = new ADLSGen2FolderDataSet("adlsGen2FolderDataSet", ADLSGen2FolderDataSetArgs.builder()        
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

const adlsGen2FolderDataSet = new azure_native.datashare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_folder_data_set = azure_native.datashare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  adlsGen2FolderDataSet:
    type: azure-native:datashare:ADLSGen2FolderDataSet
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
    var adlsGen2FolderDataSet = new AzureNative.DataShare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet", new()
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
		_, err := datashare.NewADLSGen2FolderDataSet(ctx, "adlsGen2FolderDataSet", &datashare.ADLSGen2FolderDataSetArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSet;
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetArgs;
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
        var adlsGen2FolderDataSet = new ADLSGen2FolderDataSet("adlsGen2FolderDataSet", ADLSGen2FolderDataSetArgs.builder()        
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

const adlsGen2FolderDataSet = new azure_native.datashare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_folder_data_set = azure_native.datashare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  adlsGen2FolderDataSet:
    type: azure-native:datashare:ADLSGen2FolderDataSet
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
    var adlsGen2FolderDataSet = new AzureNative.DataShare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet", new()
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
		_, err := datashare.NewADLSGen2FolderDataSet(ctx, "adlsGen2FolderDataSet", &datashare.ADLSGen2FolderDataSetArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSet;
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetArgs;
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
        var adlsGen2FolderDataSet = new ADLSGen2FolderDataSet("adlsGen2FolderDataSet", ADLSGen2FolderDataSetArgs.builder()        
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

const adlsGen2FolderDataSet = new azure_native.datashare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_folder_data_set = azure_native.datashare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  adlsGen2FolderDataSet:
    type: azure-native:datashare:ADLSGen2FolderDataSet
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
    var adlsGen2FolderDataSet = new AzureNative.DataShare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet", new()
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
		_, err := datashare.NewADLSGen2FolderDataSet(ctx, "adlsGen2FolderDataSet", &datashare.ADLSGen2FolderDataSetArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSet;
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetArgs;
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
        var adlsGen2FolderDataSet = new ADLSGen2FolderDataSet("adlsGen2FolderDataSet", ADLSGen2FolderDataSetArgs.builder()        
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

const adlsGen2FolderDataSet = new azure_native.datashare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_folder_data_set = azure_native.datashare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  adlsGen2FolderDataSet:
    type: azure-native:datashare:ADLSGen2FolderDataSet
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
    var adlsGen2FolderDataSet = new AzureNative.DataShare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet", new()
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
		_, err := datashare.NewADLSGen2FolderDataSet(ctx, "adlsGen2FolderDataSet", &datashare.ADLSGen2FolderDataSetArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSet;
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetArgs;
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
        var adlsGen2FolderDataSet = new ADLSGen2FolderDataSet("adlsGen2FolderDataSet", ADLSGen2FolderDataSetArgs.builder()        
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

const adlsGen2FolderDataSet = new azure_native.datashare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_folder_data_set = azure_native.datashare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  adlsGen2FolderDataSet:
    type: azure-native:datashare:ADLSGen2FolderDataSet
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
    var adlsGen2FolderDataSet = new AzureNative.DataShare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet", new()
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
		_, err := datashare.NewADLSGen2FolderDataSet(ctx, "adlsGen2FolderDataSet", &datashare.ADLSGen2FolderDataSetArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSet;
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetArgs;
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
        var adlsGen2FolderDataSet = new ADLSGen2FolderDataSet("adlsGen2FolderDataSet", ADLSGen2FolderDataSetArgs.builder()        
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

const adlsGen2FolderDataSet = new azure_native.datashare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet", {
    accountName: "Account1",
    dataSetName: "Dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_folder_data_set = azure_native.datashare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet",
    account_name="Account1",
    data_set_name="Dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1")

```

```yaml
resources:
  adlsGen2FolderDataSet:
    type: azure-native:datashare:ADLSGen2FolderDataSet
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
    var adlsGen2FolderDataSet = new AzureNative.DataShare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet", new()
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
		_, err := datashare.NewADLSGen2FolderDataSet(ctx, "adlsGen2FolderDataSet", &datashare.ADLSGen2FolderDataSetArgs{
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
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSet;
import com.pulumi.azurenative.datashare.ADLSGen2FolderDataSetArgs;
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
        var adlsGen2FolderDataSet = new ADLSGen2FolderDataSet("adlsGen2FolderDataSet", ADLSGen2FolderDataSetArgs.builder()        
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

const adlsGen2FolderDataSet = new azure_native.datashare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet", {
    accountName: "sourceAccount",
    dataSetName: "dataset1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "share1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adls_gen2_folder_data_set = azure_native.datashare.ADLSGen2FolderDataSet("adlsGen2FolderDataSet",
    account_name="sourceAccount",
    data_set_name="dataset1",
    resource_group_name="SampleResourceGroup",
    share_name="share1")

```

```yaml
resources:
  adlsGen2FolderDataSet:
    type: azure-native:datashare:ADLSGen2FolderDataSet
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
$ pulumi import azure-native:datashare:ADLSGen2FolderDataSet dataset1 /subscriptions/0f3dcfc3-18f8-4099-b381-8353e19d43a7/resourceGroups/SampleResourceGroup/providers/Microsoft.DataShare/accounts/sourceAccount/shares/share1/dataSets/dataset1 
```
