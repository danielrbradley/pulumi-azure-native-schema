Describes an Azure Cognitive Search service and its current state.
API Version: 2022-09-01.
Previous API Version: 2020-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SearchCreateOrUpdateService
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.Search.Service("service", new()
    {
        HostingMode = AzureNative.Search.HostingMode.Default,
        Location = "westus",
        PartitionCount = 1,
        ReplicaCount = 3,
        ResourceGroupName = "rg1",
        SearchServiceName = "mysearchservice",
        Sku = new AzureNative.Search.Inputs.SkuArgs
        {
            Name = AzureNative.Search.SkuName.Standard,
        },
        Tags = 
        {
            { "app-name", "My e-commerce app" },
        },
    });

});


```

```go
package main

import (
	search "github.com/pulumi/pulumi-azure-native-sdk/search"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := search.NewService(ctx, "service", &search.ServiceArgs{
			HostingMode:       search.HostingModeDefault,
			Location:          pulumi.String("westus"),
			PartitionCount:    pulumi.Int(1),
			ReplicaCount:      pulumi.Int(3),
			ResourceGroupName: pulumi.String("rg1"),
			SearchServiceName: pulumi.String("mysearchservice"),
			Sku: &search.SkuArgs{
				Name: search.SkuNameStandard,
			},
			Tags: pulumi.StringMap{
				"app-name": pulumi.String("My e-commerce app"),
			},
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
import com.pulumi.azurenative.search.Service;
import com.pulumi.azurenative.search.ServiceArgs;
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
            .hostingMode("default")
            .location("westus")
            .partitionCount(1)
            .replicaCount(3)
            .resourceGroupName("rg1")
            .searchServiceName("mysearchservice")
            .sku(Map.of("name", "standard"))
            .tags(Map.of("app-name", "My e-commerce app"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.search.Service("service", {
    hostingMode: azure_native.search.HostingMode.Default,
    location: "westus",
    partitionCount: 1,
    replicaCount: 3,
    resourceGroupName: "rg1",
    searchServiceName: "mysearchservice",
    sku: {
        name: azure_native.search.SkuName.Standard,
    },
    tags: {
        "app-name": "My e-commerce app",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.search.Service("service",
    hosting_mode=azure_native.search.HostingMode.DEFAULT,
    location="westus",
    partition_count=1,
    replica_count=3,
    resource_group_name="rg1",
    search_service_name="mysearchservice",
    sku=azure_native.search.SkuArgs(
        name=azure_native.search.SkuName.STANDARD,
    ),
    tags={
        "app-name": "My e-commerce app",
    })

```

```yaml
resources:
  service:
    type: azure-native:search:Service
    properties:
      hostingMode: default
      location: westus
      partitionCount: 1
      replicaCount: 3
      resourceGroupName: rg1
      searchServiceName: mysearchservice
      sku:
        name: standard
      tags:
        app-name: My e-commerce app

```

{{% /example %}}
{{% example %}}
### SearchCreateOrUpdateServiceAuthOptions
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.Search.Service("service", new()
    {
        AuthOptions = new AzureNative.Search.Inputs.DataPlaneAuthOptionsArgs
        {
            AadOrApiKey = new AzureNative.Search.Inputs.DataPlaneAadOrApiKeyAuthOptionArgs
            {
                AadAuthFailureMode = AzureNative.Search.AadAuthFailureMode.Http401WithBearerChallenge,
            },
        },
        HostingMode = AzureNative.Search.HostingMode.Default,
        Location = "westus",
        PartitionCount = 1,
        ReplicaCount = 3,
        ResourceGroupName = "rg1",
        SearchServiceName = "mysearchservice",
        Sku = new AzureNative.Search.Inputs.SkuArgs
        {
            Name = AzureNative.Search.SkuName.Standard,
        },
        Tags = 
        {
            { "app-name", "My e-commerce app" },
        },
    });

});


```

```go
package main

import (
	search "github.com/pulumi/pulumi-azure-native-sdk/search"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := search.NewService(ctx, "service", &search.ServiceArgs{
			AuthOptions: search.DataPlaneAuthOptionsResponse{
				AadOrApiKey: &search.DataPlaneAadOrApiKeyAuthOptionArgs{
					AadAuthFailureMode: search.AadAuthFailureModeHttp401WithBearerChallenge,
				},
			},
			HostingMode:       search.HostingModeDefault,
			Location:          pulumi.String("westus"),
			PartitionCount:    pulumi.Int(1),
			ReplicaCount:      pulumi.Int(3),
			ResourceGroupName: pulumi.String("rg1"),
			SearchServiceName: pulumi.String("mysearchservice"),
			Sku: &search.SkuArgs{
				Name: search.SkuNameStandard,
			},
			Tags: pulumi.StringMap{
				"app-name": pulumi.String("My e-commerce app"),
			},
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
import com.pulumi.azurenative.search.Service;
import com.pulumi.azurenative.search.ServiceArgs;
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
            .authOptions(Map.of("aadOrApiKey", Map.of("aadAuthFailureMode", "http401WithBearerChallenge")))
            .hostingMode("default")
            .location("westus")
            .partitionCount(1)
            .replicaCount(3)
            .resourceGroupName("rg1")
            .searchServiceName("mysearchservice")
            .sku(Map.of("name", "standard"))
            .tags(Map.of("app-name", "My e-commerce app"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.search.Service("service", {
    authOptions: {
        aadOrApiKey: {
            aadAuthFailureMode: azure_native.search.AadAuthFailureMode.Http401WithBearerChallenge,
        },
    },
    hostingMode: azure_native.search.HostingMode.Default,
    location: "westus",
    partitionCount: 1,
    replicaCount: 3,
    resourceGroupName: "rg1",
    searchServiceName: "mysearchservice",
    sku: {
        name: azure_native.search.SkuName.Standard,
    },
    tags: {
        "app-name": "My e-commerce app",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.search.Service("service",
    auth_options=azure_native.search.DataPlaneAuthOptionsResponseArgs(
        aad_or_api_key=azure_native.search.DataPlaneAadOrApiKeyAuthOptionArgs(
            aad_auth_failure_mode=azure_native.search.AadAuthFailureMode.HTTP401_WITH_BEARER_CHALLENGE,
        ),
    ),
    hosting_mode=azure_native.search.HostingMode.DEFAULT,
    location="westus",
    partition_count=1,
    replica_count=3,
    resource_group_name="rg1",
    search_service_name="mysearchservice",
    sku=azure_native.search.SkuArgs(
        name=azure_native.search.SkuName.STANDARD,
    ),
    tags={
        "app-name": "My e-commerce app",
    })

```

```yaml
resources:
  service:
    type: azure-native:search:Service
    properties:
      authOptions:
        aadOrApiKey:
          aadAuthFailureMode: http401WithBearerChallenge
      hostingMode: default
      location: westus
      partitionCount: 1
      replicaCount: 3
      resourceGroupName: rg1
      searchServiceName: mysearchservice
      sku:
        name: standard
      tags:
        app-name: My e-commerce app

```

{{% /example %}}
{{% example %}}
### SearchCreateOrUpdateServiceDisableLocalAuth
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.Search.Service("service", new()
    {
        DisableLocalAuth = true,
        HostingMode = AzureNative.Search.HostingMode.Default,
        Location = "westus",
        PartitionCount = 1,
        ReplicaCount = 3,
        ResourceGroupName = "rg1",
        SearchServiceName = "mysearchservice",
        Sku = new AzureNative.Search.Inputs.SkuArgs
        {
            Name = AzureNative.Search.SkuName.Standard,
        },
        Tags = 
        {
            { "app-name", "My e-commerce app" },
        },
    });

});


```

```go
package main

import (
	search "github.com/pulumi/pulumi-azure-native-sdk/search"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := search.NewService(ctx, "service", &search.ServiceArgs{
			DisableLocalAuth:  pulumi.Bool(true),
			HostingMode:       search.HostingModeDefault,
			Location:          pulumi.String("westus"),
			PartitionCount:    pulumi.Int(1),
			ReplicaCount:      pulumi.Int(3),
			ResourceGroupName: pulumi.String("rg1"),
			SearchServiceName: pulumi.String("mysearchservice"),
			Sku: &search.SkuArgs{
				Name: search.SkuNameStandard,
			},
			Tags: pulumi.StringMap{
				"app-name": pulumi.String("My e-commerce app"),
			},
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
import com.pulumi.azurenative.search.Service;
import com.pulumi.azurenative.search.ServiceArgs;
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
            .disableLocalAuth(true)
            .hostingMode("default")
            .location("westus")
            .partitionCount(1)
            .replicaCount(3)
            .resourceGroupName("rg1")
            .searchServiceName("mysearchservice")
            .sku(Map.of("name", "standard"))
            .tags(Map.of("app-name", "My e-commerce app"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.search.Service("service", {
    disableLocalAuth: true,
    hostingMode: azure_native.search.HostingMode.Default,
    location: "westus",
    partitionCount: 1,
    replicaCount: 3,
    resourceGroupName: "rg1",
    searchServiceName: "mysearchservice",
    sku: {
        name: azure_native.search.SkuName.Standard,
    },
    tags: {
        "app-name": "My e-commerce app",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.search.Service("service",
    disable_local_auth=True,
    hosting_mode=azure_native.search.HostingMode.DEFAULT,
    location="westus",
    partition_count=1,
    replica_count=3,
    resource_group_name="rg1",
    search_service_name="mysearchservice",
    sku=azure_native.search.SkuArgs(
        name=azure_native.search.SkuName.STANDARD,
    ),
    tags={
        "app-name": "My e-commerce app",
    })

```

```yaml
resources:
  service:
    type: azure-native:search:Service
    properties:
      disableLocalAuth: true
      hostingMode: default
      location: westus
      partitionCount: 1
      replicaCount: 3
      resourceGroupName: rg1
      searchServiceName: mysearchservice
      sku:
        name: standard
      tags:
        app-name: My e-commerce app

```

{{% /example %}}
{{% example %}}
### SearchCreateOrUpdateServiceToAllowAccessFromPrivateEndpoints
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.Search.Service("service", new()
    {
        HostingMode = AzureNative.Search.HostingMode.Default,
        Location = "westus",
        PartitionCount = 1,
        PublicNetworkAccess = AzureNative.Search.PublicNetworkAccess.Disabled,
        ReplicaCount = 3,
        ResourceGroupName = "rg1",
        SearchServiceName = "mysearchservice",
        Sku = new AzureNative.Search.Inputs.SkuArgs
        {
            Name = AzureNative.Search.SkuName.Standard,
        },
        Tags = 
        {
            { "app-name", "My e-commerce app" },
        },
    });

});


```

```go
package main

import (
	search "github.com/pulumi/pulumi-azure-native-sdk/search"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := search.NewService(ctx, "service", &search.ServiceArgs{
			HostingMode:         search.HostingModeDefault,
			Location:            pulumi.String("westus"),
			PartitionCount:      pulumi.Int(1),
			PublicNetworkAccess: search.PublicNetworkAccessDisabled,
			ReplicaCount:        pulumi.Int(3),
			ResourceGroupName:   pulumi.String("rg1"),
			SearchServiceName:   pulumi.String("mysearchservice"),
			Sku: &search.SkuArgs{
				Name: search.SkuNameStandard,
			},
			Tags: pulumi.StringMap{
				"app-name": pulumi.String("My e-commerce app"),
			},
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
import com.pulumi.azurenative.search.Service;
import com.pulumi.azurenative.search.ServiceArgs;
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
            .hostingMode("default")
            .location("westus")
            .partitionCount(1)
            .publicNetworkAccess("disabled")
            .replicaCount(3)
            .resourceGroupName("rg1")
            .searchServiceName("mysearchservice")
            .sku(Map.of("name", "standard"))
            .tags(Map.of("app-name", "My e-commerce app"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.search.Service("service", {
    hostingMode: azure_native.search.HostingMode.Default,
    location: "westus",
    partitionCount: 1,
    publicNetworkAccess: azure_native.search.PublicNetworkAccess.Disabled,
    replicaCount: 3,
    resourceGroupName: "rg1",
    searchServiceName: "mysearchservice",
    sku: {
        name: azure_native.search.SkuName.Standard,
    },
    tags: {
        "app-name": "My e-commerce app",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.search.Service("service",
    hosting_mode=azure_native.search.HostingMode.DEFAULT,
    location="westus",
    partition_count=1,
    public_network_access=azure_native.search.PublicNetworkAccess.DISABLED,
    replica_count=3,
    resource_group_name="rg1",
    search_service_name="mysearchservice",
    sku=azure_native.search.SkuArgs(
        name=azure_native.search.SkuName.STANDARD,
    ),
    tags={
        "app-name": "My e-commerce app",
    })

```

```yaml
resources:
  service:
    type: azure-native:search:Service
    properties:
      hostingMode: default
      location: westus
      partitionCount: 1
      publicNetworkAccess: disabled
      replicaCount: 3
      resourceGroupName: rg1
      searchServiceName: mysearchservice
      sku:
        name: standard
      tags:
        app-name: My e-commerce app

```

{{% /example %}}
{{% example %}}
### SearchCreateOrUpdateServiceToAllowAccessFromPublicCustomIPs
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.Search.Service("service", new()
    {
        HostingMode = AzureNative.Search.HostingMode.Default,
        Location = "westus",
        NetworkRuleSet = new AzureNative.Search.Inputs.NetworkRuleSetArgs
        {
            IpRules = new[]
            {
                new AzureNative.Search.Inputs.IpRuleArgs
                {
                    Value = "123.4.5.6",
                },
                new AzureNative.Search.Inputs.IpRuleArgs
                {
                    Value = "123.4.6.0/18",
                },
            },
        },
        PartitionCount = 1,
        ReplicaCount = 1,
        ResourceGroupName = "rg1",
        SearchServiceName = "mysearchservice",
        Sku = new AzureNative.Search.Inputs.SkuArgs
        {
            Name = AzureNative.Search.SkuName.Standard,
        },
        Tags = 
        {
            { "app-name", "My e-commerce app" },
        },
    });

});


```

```go
package main

import (
	search "github.com/pulumi/pulumi-azure-native-sdk/search"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := search.NewService(ctx, "service", &search.ServiceArgs{
			HostingMode: search.HostingModeDefault,
			Location:    pulumi.String("westus"),
			NetworkRuleSet: search.NetworkRuleSetResponse{
				IpRules: search.IpRuleArray{
					&search.IpRuleArgs{
						Value: pulumi.String("123.4.5.6"),
					},
					&search.IpRuleArgs{
						Value: pulumi.String("123.4.6.0/18"),
					},
				},
			},
			PartitionCount:    pulumi.Int(1),
			ReplicaCount:      pulumi.Int(1),
			ResourceGroupName: pulumi.String("rg1"),
			SearchServiceName: pulumi.String("mysearchservice"),
			Sku: &search.SkuArgs{
				Name: search.SkuNameStandard,
			},
			Tags: pulumi.StringMap{
				"app-name": pulumi.String("My e-commerce app"),
			},
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
import com.pulumi.azurenative.search.Service;
import com.pulumi.azurenative.search.ServiceArgs;
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
            .hostingMode("default")
            .location("westus")
            .networkRuleSet(Map.of("ipRules",             
                Map.of("value", "123.4.5.6"),
                Map.of("value", "123.4.6.0/18")))
            .partitionCount(1)
            .replicaCount(1)
            .resourceGroupName("rg1")
            .searchServiceName("mysearchservice")
            .sku(Map.of("name", "standard"))
            .tags(Map.of("app-name", "My e-commerce app"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.search.Service("service", {
    hostingMode: azure_native.search.HostingMode.Default,
    location: "westus",
    networkRuleSet: {
        ipRules: [
            {
                value: "123.4.5.6",
            },
            {
                value: "123.4.6.0/18",
            },
        ],
    },
    partitionCount: 1,
    replicaCount: 1,
    resourceGroupName: "rg1",
    searchServiceName: "mysearchservice",
    sku: {
        name: azure_native.search.SkuName.Standard,
    },
    tags: {
        "app-name": "My e-commerce app",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.search.Service("service",
    hosting_mode=azure_native.search.HostingMode.DEFAULT,
    location="westus",
    network_rule_set=azure_native.search.NetworkRuleSetResponseArgs(
        ip_rules=[
            azure_native.search.IpRuleArgs(
                value="123.4.5.6",
            ),
            azure_native.search.IpRuleArgs(
                value="123.4.6.0/18",
            ),
        ],
    ),
    partition_count=1,
    replica_count=1,
    resource_group_name="rg1",
    search_service_name="mysearchservice",
    sku=azure_native.search.SkuArgs(
        name=azure_native.search.SkuName.STANDARD,
    ),
    tags={
        "app-name": "My e-commerce app",
    })

```

```yaml
resources:
  service:
    type: azure-native:search:Service
    properties:
      hostingMode: default
      location: westus
      networkRuleSet:
        ipRules:
          - value: 123.4.5.6
          - value: 123.4.6.0/18
      partitionCount: 1
      replicaCount: 1
      resourceGroupName: rg1
      searchServiceName: mysearchservice
      sku:
        name: standard
      tags:
        app-name: My e-commerce app

```

{{% /example %}}
{{% example %}}
### SearchCreateOrUpdateServiceWithCmkEnforcement
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.Search.Service("service", new()
    {
        EncryptionWithCmk = new AzureNative.Search.Inputs.EncryptionWithCmkArgs
        {
            Enforcement = AzureNative.Search.SearchEncryptionWithCmk.Enabled,
        },
        HostingMode = AzureNative.Search.HostingMode.Default,
        Location = "westus",
        PartitionCount = 1,
        ReplicaCount = 3,
        ResourceGroupName = "rg1",
        SearchServiceName = "mysearchservice",
        Sku = new AzureNative.Search.Inputs.SkuArgs
        {
            Name = AzureNative.Search.SkuName.Standard,
        },
        Tags = 
        {
            { "app-name", "My e-commerce app" },
        },
    });

});


```

```go
package main

import (
	search "github.com/pulumi/pulumi-azure-native-sdk/search"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := search.NewService(ctx, "service", &search.ServiceArgs{
			EncryptionWithCmk: &search.EncryptionWithCmkArgs{
				Enforcement: search.SearchEncryptionWithCmkEnabled,
			},
			HostingMode:       search.HostingModeDefault,
			Location:          pulumi.String("westus"),
			PartitionCount:    pulumi.Int(1),
			ReplicaCount:      pulumi.Int(3),
			ResourceGroupName: pulumi.String("rg1"),
			SearchServiceName: pulumi.String("mysearchservice"),
			Sku: &search.SkuArgs{
				Name: search.SkuNameStandard,
			},
			Tags: pulumi.StringMap{
				"app-name": pulumi.String("My e-commerce app"),
			},
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
import com.pulumi.azurenative.search.Service;
import com.pulumi.azurenative.search.ServiceArgs;
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
            .encryptionWithCmk(Map.of("enforcement", "Enabled"))
            .hostingMode("default")
            .location("westus")
            .partitionCount(1)
            .replicaCount(3)
            .resourceGroupName("rg1")
            .searchServiceName("mysearchservice")
            .sku(Map.of("name", "standard"))
            .tags(Map.of("app-name", "My e-commerce app"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.search.Service("service", {
    encryptionWithCmk: {
        enforcement: azure_native.search.SearchEncryptionWithCmk.Enabled,
    },
    hostingMode: azure_native.search.HostingMode.Default,
    location: "westus",
    partitionCount: 1,
    replicaCount: 3,
    resourceGroupName: "rg1",
    searchServiceName: "mysearchservice",
    sku: {
        name: azure_native.search.SkuName.Standard,
    },
    tags: {
        "app-name": "My e-commerce app",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.search.Service("service",
    encryption_with_cmk=azure_native.search.EncryptionWithCmkArgs(
        enforcement=azure_native.search.SearchEncryptionWithCmk.ENABLED,
    ),
    hosting_mode=azure_native.search.HostingMode.DEFAULT,
    location="westus",
    partition_count=1,
    replica_count=3,
    resource_group_name="rg1",
    search_service_name="mysearchservice",
    sku=azure_native.search.SkuArgs(
        name=azure_native.search.SkuName.STANDARD,
    ),
    tags={
        "app-name": "My e-commerce app",
    })

```

```yaml
resources:
  service:
    type: azure-native:search:Service
    properties:
      encryptionWithCmk:
        enforcement: Enabled
      hostingMode: default
      location: westus
      partitionCount: 1
      replicaCount: 3
      resourceGroupName: rg1
      searchServiceName: mysearchservice
      sku:
        name: standard
      tags:
        app-name: My e-commerce app

```

{{% /example %}}
{{% example %}}
### SearchCreateOrUpdateServiceWithIdentity
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.Search.Service("service", new()
    {
        HostingMode = AzureNative.Search.HostingMode.Default,
        Identity = new AzureNative.Search.Inputs.IdentityArgs
        {
            Type = AzureNative.Search.IdentityType.SystemAssigned,
        },
        Location = "westus",
        PartitionCount = 1,
        ReplicaCount = 3,
        ResourceGroupName = "rg1",
        SearchServiceName = "mysearchservice",
        Sku = new AzureNative.Search.Inputs.SkuArgs
        {
            Name = AzureNative.Search.SkuName.Standard,
        },
        Tags = 
        {
            { "app-name", "My e-commerce app" },
        },
    });

});


```

```go
package main

import (
	search "github.com/pulumi/pulumi-azure-native-sdk/search"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := search.NewService(ctx, "service", &search.ServiceArgs{
			HostingMode: search.HostingModeDefault,
			Identity: &search.IdentityArgs{
				Type: search.IdentityTypeSystemAssigned,
			},
			Location:          pulumi.String("westus"),
			PartitionCount:    pulumi.Int(1),
			ReplicaCount:      pulumi.Int(3),
			ResourceGroupName: pulumi.String("rg1"),
			SearchServiceName: pulumi.String("mysearchservice"),
			Sku: &search.SkuArgs{
				Name: search.SkuNameStandard,
			},
			Tags: pulumi.StringMap{
				"app-name": pulumi.String("My e-commerce app"),
			},
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
import com.pulumi.azurenative.search.Service;
import com.pulumi.azurenative.search.ServiceArgs;
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
            .hostingMode("default")
            .identity(Map.of("type", "SystemAssigned"))
            .location("westus")
            .partitionCount(1)
            .replicaCount(3)
            .resourceGroupName("rg1")
            .searchServiceName("mysearchservice")
            .sku(Map.of("name", "standard"))
            .tags(Map.of("app-name", "My e-commerce app"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.search.Service("service", {
    hostingMode: azure_native.search.HostingMode.Default,
    identity: {
        type: azure_native.search.IdentityType.SystemAssigned,
    },
    location: "westus",
    partitionCount: 1,
    replicaCount: 3,
    resourceGroupName: "rg1",
    searchServiceName: "mysearchservice",
    sku: {
        name: azure_native.search.SkuName.Standard,
    },
    tags: {
        "app-name": "My e-commerce app",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.search.Service("service",
    hosting_mode=azure_native.search.HostingMode.DEFAULT,
    identity=azure_native.search.IdentityArgs(
        type=azure_native.search.IdentityType.SYSTEM_ASSIGNED,
    ),
    location="westus",
    partition_count=1,
    replica_count=3,
    resource_group_name="rg1",
    search_service_name="mysearchservice",
    sku=azure_native.search.SkuArgs(
        name=azure_native.search.SkuName.STANDARD,
    ),
    tags={
        "app-name": "My e-commerce app",
    })

```

```yaml
resources:
  service:
    type: azure-native:search:Service
    properties:
      hostingMode: default
      identity:
        type: SystemAssigned
      location: westus
      partitionCount: 1
      replicaCount: 3
      resourceGroupName: rg1
      searchServiceName: mysearchservice
      sku:
        name: standard
      tags:
        app-name: My e-commerce app

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:search:Service mysearchservice /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Search/searchServices/mysearchservice 
```
