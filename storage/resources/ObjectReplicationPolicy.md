The replication policy between two storage accounts. Multiple rules can be defined in one policy.
API Version: 2022-09-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### StorageAccountCreateObjectReplicationPolicyOnDestination
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var objectReplicationPolicy = new AzureNative.Storage.ObjectReplicationPolicy("objectReplicationPolicy", new()
    {
        AccountName = "dst112",
        DestinationAccount = "dst112",
        ObjectReplicationPolicyId = "default",
        ResourceGroupName = "res7687",
        Rules = new[]
        {
            new AzureNative.Storage.Inputs.ObjectReplicationPolicyRuleArgs
            {
                DestinationContainer = "dcont139",
                Filters = new AzureNative.Storage.Inputs.ObjectReplicationPolicyFilterArgs
                {
                    PrefixMatch = new[]
                    {
                        "blobA",
                        "blobB",
                    },
                },
                SourceContainer = "scont139",
            },
        },
        SourceAccount = "src1122",
    });

});


```

```go
package main

import (
	storage "github.com/pulumi/pulumi-azure-native-sdk/storage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storage.NewObjectReplicationPolicy(ctx, "objectReplicationPolicy", &storage.ObjectReplicationPolicyArgs{
			AccountName:               pulumi.String("dst112"),
			DestinationAccount:        pulumi.String("dst112"),
			ObjectReplicationPolicyId: pulumi.String("default"),
			ResourceGroupName:         pulumi.String("res7687"),
			Rules: []storage.ObjectReplicationPolicyRuleArgs{
				{
					DestinationContainer: pulumi.String("dcont139"),
					Filters: {
						PrefixMatch: pulumi.StringArray{
							pulumi.String("blobA"),
							pulumi.String("blobB"),
						},
					},
					SourceContainer: pulumi.String("scont139"),
				},
			},
			SourceAccount: pulumi.String("src1122"),
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
import com.pulumi.azurenative.storage.ObjectReplicationPolicy;
import com.pulumi.azurenative.storage.ObjectReplicationPolicyArgs;
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
        var objectReplicationPolicy = new ObjectReplicationPolicy("objectReplicationPolicy", ObjectReplicationPolicyArgs.builder()        
            .accountName("dst112")
            .destinationAccount("dst112")
            .objectReplicationPolicyId("default")
            .resourceGroupName("res7687")
            .rules(Map.ofEntries(
                Map.entry("destinationContainer", "dcont139"),
                Map.entry("filters", Map.of("prefixMatch",                 
                    "blobA",
                    "blobB")),
                Map.entry("sourceContainer", "scont139")
            ))
            .sourceAccount("src1122")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const objectReplicationPolicy = new azure_native.storage.ObjectReplicationPolicy("objectReplicationPolicy", {
    accountName: "dst112",
    destinationAccount: "dst112",
    objectReplicationPolicyId: "default",
    resourceGroupName: "res7687",
    rules: [{
        destinationContainer: "dcont139",
        filters: {
            prefixMatch: [
                "blobA",
                "blobB",
            ],
        },
        sourceContainer: "scont139",
    }],
    sourceAccount: "src1122",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

object_replication_policy = azure_native.storage.ObjectReplicationPolicy("objectReplicationPolicy",
    account_name="dst112",
    destination_account="dst112",
    object_replication_policy_id="default",
    resource_group_name="res7687",
    rules=[{
        "destinationContainer": "dcont139",
        "filters": azure_native.storage.ObjectReplicationPolicyFilterArgs(
            prefix_match=[
                "blobA",
                "blobB",
            ],
        ),
        "sourceContainer": "scont139",
    }],
    source_account="src1122")

```

```yaml
resources:
  objectReplicationPolicy:
    type: azure-native:storage:ObjectReplicationPolicy
    properties:
      accountName: dst112
      destinationAccount: dst112
      objectReplicationPolicyId: default
      resourceGroupName: res7687
      rules:
        - destinationContainer: dcont139
          filters:
            prefixMatch:
              - blobA
              - blobB
          sourceContainer: scont139
      sourceAccount: src1122

```

{{% /example %}}
{{% example %}}
### StorageAccountCreateObjectReplicationPolicyOnSource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var objectReplicationPolicy = new AzureNative.Storage.ObjectReplicationPolicy("objectReplicationPolicy", new()
    {
        AccountName = "src1122",
        DestinationAccount = "dst112",
        ObjectReplicationPolicyId = "2a20bb73-5717-4635-985a-5d4cf777438f",
        ResourceGroupName = "res7687",
        Rules = new[]
        {
            new AzureNative.Storage.Inputs.ObjectReplicationPolicyRuleArgs
            {
                DestinationContainer = "dcont139",
                Filters = new AzureNative.Storage.Inputs.ObjectReplicationPolicyFilterArgs
                {
                    MinCreationTime = "2020-02-19T16:05:00Z",
                    PrefixMatch = new[]
                    {
                        "blobA",
                        "blobB",
                    },
                },
                RuleId = "d5d18a48-8801-4554-aeaa-74faf65f5ef9",
                SourceContainer = "scont139",
            },
        },
        SourceAccount = "src1122",
    });

});


```

```go
package main

import (
	storage "github.com/pulumi/pulumi-azure-native-sdk/storage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storage.NewObjectReplicationPolicy(ctx, "objectReplicationPolicy", &storage.ObjectReplicationPolicyArgs{
			AccountName:               pulumi.String("src1122"),
			DestinationAccount:        pulumi.String("dst112"),
			ObjectReplicationPolicyId: pulumi.String("2a20bb73-5717-4635-985a-5d4cf777438f"),
			ResourceGroupName:         pulumi.String("res7687"),
			Rules: []storage.ObjectReplicationPolicyRuleArgs{
				{
					DestinationContainer: pulumi.String("dcont139"),
					Filters: {
						MinCreationTime: pulumi.String("2020-02-19T16:05:00Z"),
						PrefixMatch: pulumi.StringArray{
							pulumi.String("blobA"),
							pulumi.String("blobB"),
						},
					},
					RuleId:          pulumi.String("d5d18a48-8801-4554-aeaa-74faf65f5ef9"),
					SourceContainer: pulumi.String("scont139"),
				},
			},
			SourceAccount: pulumi.String("src1122"),
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
import com.pulumi.azurenative.storage.ObjectReplicationPolicy;
import com.pulumi.azurenative.storage.ObjectReplicationPolicyArgs;
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
        var objectReplicationPolicy = new ObjectReplicationPolicy("objectReplicationPolicy", ObjectReplicationPolicyArgs.builder()        
            .accountName("src1122")
            .destinationAccount("dst112")
            .objectReplicationPolicyId("2a20bb73-5717-4635-985a-5d4cf777438f")
            .resourceGroupName("res7687")
            .rules(Map.ofEntries(
                Map.entry("destinationContainer", "dcont139"),
                Map.entry("filters", Map.ofEntries(
                    Map.entry("minCreationTime", "2020-02-19T16:05:00Z"),
                    Map.entry("prefixMatch",                     
                        "blobA",
                        "blobB")
                )),
                Map.entry("ruleId", "d5d18a48-8801-4554-aeaa-74faf65f5ef9"),
                Map.entry("sourceContainer", "scont139")
            ))
            .sourceAccount("src1122")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const objectReplicationPolicy = new azure_native.storage.ObjectReplicationPolicy("objectReplicationPolicy", {
    accountName: "src1122",
    destinationAccount: "dst112",
    objectReplicationPolicyId: "2a20bb73-5717-4635-985a-5d4cf777438f",
    resourceGroupName: "res7687",
    rules: [{
        destinationContainer: "dcont139",
        filters: {
            minCreationTime: "2020-02-19T16:05:00Z",
            prefixMatch: [
                "blobA",
                "blobB",
            ],
        },
        ruleId: "d5d18a48-8801-4554-aeaa-74faf65f5ef9",
        sourceContainer: "scont139",
    }],
    sourceAccount: "src1122",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

object_replication_policy = azure_native.storage.ObjectReplicationPolicy("objectReplicationPolicy",
    account_name="src1122",
    destination_account="dst112",
    object_replication_policy_id="2a20bb73-5717-4635-985a-5d4cf777438f",
    resource_group_name="res7687",
    rules=[{
        "destinationContainer": "dcont139",
        "filters": azure_native.storage.ObjectReplicationPolicyFilterArgs(
            min_creation_time="2020-02-19T16:05:00Z",
            prefix_match=[
                "blobA",
                "blobB",
            ],
        ),
        "ruleId": "d5d18a48-8801-4554-aeaa-74faf65f5ef9",
        "sourceContainer": "scont139",
    }],
    source_account="src1122")

```

```yaml
resources:
  objectReplicationPolicy:
    type: azure-native:storage:ObjectReplicationPolicy
    properties:
      accountName: src1122
      destinationAccount: dst112
      objectReplicationPolicyId: 2a20bb73-5717-4635-985a-5d4cf777438f
      resourceGroupName: res7687
      rules:
        - destinationContainer: dcont139
          filters:
            minCreationTime: 2020-02-19T16:05:00Z
            prefixMatch:
              - blobA
              - blobB
          ruleId: d5d18a48-8801-4554-aeaa-74faf65f5ef9
          sourceContainer: scont139
      sourceAccount: src1122

```

{{% /example %}}
{{% example %}}
### StorageAccountUpdateObjectReplicationPolicyOnDestination
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var objectReplicationPolicy = new AzureNative.Storage.ObjectReplicationPolicy("objectReplicationPolicy", new()
    {
        AccountName = "dst112",
        DestinationAccount = "dst112",
        ObjectReplicationPolicyId = "2a20bb73-5717-4635-985a-5d4cf777438f",
        ResourceGroupName = "res7687",
        Rules = new[]
        {
            new AzureNative.Storage.Inputs.ObjectReplicationPolicyRuleArgs
            {
                DestinationContainer = "dcont139",
                Filters = new AzureNative.Storage.Inputs.ObjectReplicationPolicyFilterArgs
                {
                    PrefixMatch = new[]
                    {
                        "blobA",
                        "blobB",
                    },
                },
                RuleId = "d5d18a48-8801-4554-aeaa-74faf65f5ef9",
                SourceContainer = "scont139",
            },
            new AzureNative.Storage.Inputs.ObjectReplicationPolicyRuleArgs
            {
                DestinationContainer = "dcont179",
                SourceContainer = "scont179",
            },
        },
        SourceAccount = "src1122",
    });

});


```

```go
package main

import (
	storage "github.com/pulumi/pulumi-azure-native-sdk/storage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storage.NewObjectReplicationPolicy(ctx, "objectReplicationPolicy", &storage.ObjectReplicationPolicyArgs{
			AccountName:               pulumi.String("dst112"),
			DestinationAccount:        pulumi.String("dst112"),
			ObjectReplicationPolicyId: pulumi.String("2a20bb73-5717-4635-985a-5d4cf777438f"),
			ResourceGroupName:         pulumi.String("res7687"),
			Rules: []storage.ObjectReplicationPolicyRuleArgs{
				{
					DestinationContainer: pulumi.String("dcont139"),
					Filters: {
						PrefixMatch: pulumi.StringArray{
							pulumi.String("blobA"),
							pulumi.String("blobB"),
						},
					},
					RuleId:          pulumi.String("d5d18a48-8801-4554-aeaa-74faf65f5ef9"),
					SourceContainer: pulumi.String("scont139"),
				},
				{
					DestinationContainer: pulumi.String("dcont179"),
					SourceContainer:      pulumi.String("scont179"),
				},
			},
			SourceAccount: pulumi.String("src1122"),
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
import com.pulumi.azurenative.storage.ObjectReplicationPolicy;
import com.pulumi.azurenative.storage.ObjectReplicationPolicyArgs;
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
        var objectReplicationPolicy = new ObjectReplicationPolicy("objectReplicationPolicy", ObjectReplicationPolicyArgs.builder()        
            .accountName("dst112")
            .destinationAccount("dst112")
            .objectReplicationPolicyId("2a20bb73-5717-4635-985a-5d4cf777438f")
            .resourceGroupName("res7687")
            .rules(            
                Map.ofEntries(
                    Map.entry("destinationContainer", "dcont139"),
                    Map.entry("filters", Map.of("prefixMatch",                     
                        "blobA",
                        "blobB")),
                    Map.entry("ruleId", "d5d18a48-8801-4554-aeaa-74faf65f5ef9"),
                    Map.entry("sourceContainer", "scont139")
                ),
                Map.ofEntries(
                    Map.entry("destinationContainer", "dcont179"),
                    Map.entry("sourceContainer", "scont179")
                ))
            .sourceAccount("src1122")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const objectReplicationPolicy = new azure_native.storage.ObjectReplicationPolicy("objectReplicationPolicy", {
    accountName: "dst112",
    destinationAccount: "dst112",
    objectReplicationPolicyId: "2a20bb73-5717-4635-985a-5d4cf777438f",
    resourceGroupName: "res7687",
    rules: [
        {
            destinationContainer: "dcont139",
            filters: {
                prefixMatch: [
                    "blobA",
                    "blobB",
                ],
            },
            ruleId: "d5d18a48-8801-4554-aeaa-74faf65f5ef9",
            sourceContainer: "scont139",
        },
        {
            destinationContainer: "dcont179",
            sourceContainer: "scont179",
        },
    ],
    sourceAccount: "src1122",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

object_replication_policy = azure_native.storage.ObjectReplicationPolicy("objectReplicationPolicy",
    account_name="dst112",
    destination_account="dst112",
    object_replication_policy_id="2a20bb73-5717-4635-985a-5d4cf777438f",
    resource_group_name="res7687",
    rules=[
        {
            "destinationContainer": "dcont139",
            "filters": azure_native.storage.ObjectReplicationPolicyFilterArgs(
                prefix_match=[
                    "blobA",
                    "blobB",
                ],
            ),
            "ruleId": "d5d18a48-8801-4554-aeaa-74faf65f5ef9",
            "sourceContainer": "scont139",
        },
        azure_native.storage.ObjectReplicationPolicyRuleArgs(
            destination_container="dcont179",
            source_container="scont179",
        ),
    ],
    source_account="src1122")

```

```yaml
resources:
  objectReplicationPolicy:
    type: azure-native:storage:ObjectReplicationPolicy
    properties:
      accountName: dst112
      destinationAccount: dst112
      objectReplicationPolicyId: 2a20bb73-5717-4635-985a-5d4cf777438f
      resourceGroupName: res7687
      rules:
        - destinationContainer: dcont139
          filters:
            prefixMatch:
              - blobA
              - blobB
          ruleId: d5d18a48-8801-4554-aeaa-74faf65f5ef9
          sourceContainer: scont139
        - destinationContainer: dcont179
          sourceContainer: scont179
      sourceAccount: src1122

```

{{% /example %}}
{{% example %}}
### StorageAccountUpdateObjectReplicationPolicyOnSource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var objectReplicationPolicy = new AzureNative.Storage.ObjectReplicationPolicy("objectReplicationPolicy", new()
    {
        AccountName = "src1122",
        DestinationAccount = "dst112",
        ObjectReplicationPolicyId = "2a20bb73-5717-4635-985a-5d4cf777438f",
        ResourceGroupName = "res7687",
        Rules = new[]
        {
            new AzureNative.Storage.Inputs.ObjectReplicationPolicyRuleArgs
            {
                DestinationContainer = "dcont139",
                Filters = new AzureNative.Storage.Inputs.ObjectReplicationPolicyFilterArgs
                {
                    PrefixMatch = new[]
                    {
                        "blobA",
                        "blobB",
                    },
                },
                RuleId = "d5d18a48-8801-4554-aeaa-74faf65f5ef9",
                SourceContainer = "scont139",
            },
            new AzureNative.Storage.Inputs.ObjectReplicationPolicyRuleArgs
            {
                DestinationContainer = "dcont179",
                RuleId = "cfbb4bc2-8b60-429f-b05a-d1e0942b33b2",
                SourceContainer = "scont179",
            },
        },
        SourceAccount = "src1122",
    });

});


```

```go
package main

import (
	storage "github.com/pulumi/pulumi-azure-native-sdk/storage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storage.NewObjectReplicationPolicy(ctx, "objectReplicationPolicy", &storage.ObjectReplicationPolicyArgs{
			AccountName:               pulumi.String("src1122"),
			DestinationAccount:        pulumi.String("dst112"),
			ObjectReplicationPolicyId: pulumi.String("2a20bb73-5717-4635-985a-5d4cf777438f"),
			ResourceGroupName:         pulumi.String("res7687"),
			Rules: []storage.ObjectReplicationPolicyRuleArgs{
				{
					DestinationContainer: pulumi.String("dcont139"),
					Filters: {
						PrefixMatch: pulumi.StringArray{
							pulumi.String("blobA"),
							pulumi.String("blobB"),
						},
					},
					RuleId:          pulumi.String("d5d18a48-8801-4554-aeaa-74faf65f5ef9"),
					SourceContainer: pulumi.String("scont139"),
				},
				{
					DestinationContainer: pulumi.String("dcont179"),
					RuleId:               pulumi.String("cfbb4bc2-8b60-429f-b05a-d1e0942b33b2"),
					SourceContainer:      pulumi.String("scont179"),
				},
			},
			SourceAccount: pulumi.String("src1122"),
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
import com.pulumi.azurenative.storage.ObjectReplicationPolicy;
import com.pulumi.azurenative.storage.ObjectReplicationPolicyArgs;
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
        var objectReplicationPolicy = new ObjectReplicationPolicy("objectReplicationPolicy", ObjectReplicationPolicyArgs.builder()        
            .accountName("src1122")
            .destinationAccount("dst112")
            .objectReplicationPolicyId("2a20bb73-5717-4635-985a-5d4cf777438f")
            .resourceGroupName("res7687")
            .rules(            
                Map.ofEntries(
                    Map.entry("destinationContainer", "dcont139"),
                    Map.entry("filters", Map.of("prefixMatch",                     
                        "blobA",
                        "blobB")),
                    Map.entry("ruleId", "d5d18a48-8801-4554-aeaa-74faf65f5ef9"),
                    Map.entry("sourceContainer", "scont139")
                ),
                Map.ofEntries(
                    Map.entry("destinationContainer", "dcont179"),
                    Map.entry("ruleId", "cfbb4bc2-8b60-429f-b05a-d1e0942b33b2"),
                    Map.entry("sourceContainer", "scont179")
                ))
            .sourceAccount("src1122")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const objectReplicationPolicy = new azure_native.storage.ObjectReplicationPolicy("objectReplicationPolicy", {
    accountName: "src1122",
    destinationAccount: "dst112",
    objectReplicationPolicyId: "2a20bb73-5717-4635-985a-5d4cf777438f",
    resourceGroupName: "res7687",
    rules: [
        {
            destinationContainer: "dcont139",
            filters: {
                prefixMatch: [
                    "blobA",
                    "blobB",
                ],
            },
            ruleId: "d5d18a48-8801-4554-aeaa-74faf65f5ef9",
            sourceContainer: "scont139",
        },
        {
            destinationContainer: "dcont179",
            ruleId: "cfbb4bc2-8b60-429f-b05a-d1e0942b33b2",
            sourceContainer: "scont179",
        },
    ],
    sourceAccount: "src1122",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

object_replication_policy = azure_native.storage.ObjectReplicationPolicy("objectReplicationPolicy",
    account_name="src1122",
    destination_account="dst112",
    object_replication_policy_id="2a20bb73-5717-4635-985a-5d4cf777438f",
    resource_group_name="res7687",
    rules=[
        {
            "destinationContainer": "dcont139",
            "filters": azure_native.storage.ObjectReplicationPolicyFilterArgs(
                prefix_match=[
                    "blobA",
                    "blobB",
                ],
            ),
            "ruleId": "d5d18a48-8801-4554-aeaa-74faf65f5ef9",
            "sourceContainer": "scont139",
        },
        azure_native.storage.ObjectReplicationPolicyRuleArgs(
            destination_container="dcont179",
            rule_id="cfbb4bc2-8b60-429f-b05a-d1e0942b33b2",
            source_container="scont179",
        ),
    ],
    source_account="src1122")

```

```yaml
resources:
  objectReplicationPolicy:
    type: azure-native:storage:ObjectReplicationPolicy
    properties:
      accountName: src1122
      destinationAccount: dst112
      objectReplicationPolicyId: 2a20bb73-5717-4635-985a-5d4cf777438f
      resourceGroupName: res7687
      rules:
        - destinationContainer: dcont139
          filters:
            prefixMatch:
              - blobA
              - blobB
          ruleId: d5d18a48-8801-4554-aeaa-74faf65f5ef9
          sourceContainer: scont139
        - destinationContainer: dcont179
          ruleId: cfbb4bc2-8b60-429f-b05a-d1e0942b33b2
          sourceContainer: scont179
      sourceAccount: src1122

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storage:ObjectReplicationPolicy 2a20bb73-5717-4635-985a-5d4cf777438f /subscriptions/{subscription-id}/resourceGroups/res7687/providers/Microsoft.Storage/storageAccounts/src1122/objectReplicationPolicies/2a20bb73-5717-4635-985a-5d4cf777438f 
```
