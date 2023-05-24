Describes a DNS record set (a collection of DNS records with the same name and type).
API Version: 2018-05-01.
Previous API Version: 2018-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create A recordset
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var recordSet = new AzureNative.Network.RecordSet("recordSet", new()
    {
        ARecords = new[]
        {
            new AzureNative.Network.Inputs.ARecordArgs
            {
                Ipv4Address = "127.0.0.1",
            },
        },
        Metadata = 
        {
            { "key1", "value1" },
        },
        RecordType = "A",
        RelativeRecordSetName = "record1",
        ResourceGroupName = "rg1",
        Ttl = 3600,
        ZoneName = "zone1",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewRecordSet(ctx, "recordSet", &network.RecordSetArgs{
			ARecords: []network.ARecordArgs{
				{
					Ipv4Address: pulumi.String("127.0.0.1"),
				},
			},
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			RecordType:            pulumi.String("A"),
			RelativeRecordSetName: pulumi.String("record1"),
			ResourceGroupName:     pulumi.String("rg1"),
			Ttl:                   pulumi.Float64(3600),
			ZoneName:              pulumi.String("zone1"),
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
import com.pulumi.azurenative.network.RecordSet;
import com.pulumi.azurenative.network.RecordSetArgs;
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
        var recordSet = new RecordSet("recordSet", RecordSetArgs.builder()        
            .aRecords(Map.of("ipv4Address", "127.0.0.1"))
            .metadata(Map.of("key1", "value1"))
            .recordType("A")
            .relativeRecordSetName("record1")
            .resourceGroupName("rg1")
            .ttl(3600)
            .zoneName("zone1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const recordSet = new azure_native.network.RecordSet("recordSet", {
    aRecords: [{
        ipv4Address: "127.0.0.1",
    }],
    metadata: {
        key1: "value1",
    },
    recordType: "A",
    relativeRecordSetName: "record1",
    resourceGroupName: "rg1",
    ttl: 3600,
    zoneName: "zone1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

record_set = azure_native.network.RecordSet("recordSet",
    a_records=[azure_native.network.ARecordArgs(
        ipv4_address="127.0.0.1",
    )],
    metadata={
        "key1": "value1",
    },
    record_type="A",
    relative_record_set_name="record1",
    resource_group_name="rg1",
    ttl=3600,
    zone_name="zone1")

```

```yaml
resources:
  recordSet:
    type: azure-native:network:RecordSet
    properties:
      aRecords:
        - ipv4Address: 127.0.0.1
      metadata:
        key1: value1
      recordType: A
      relativeRecordSetName: record1
      resourceGroupName: rg1
      ttl: 3600
      zoneName: zone1

```

{{% /example %}}
{{% example %}}
### Create A recordset with alias target resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var recordSet = new AzureNative.Network.RecordSet("recordSet", new()
    {
        Metadata = 
        {
            { "key1", "value1" },
        },
        RecordType = "A",
        RelativeRecordSetName = "record1",
        ResourceGroupName = "rg1",
        TargetResource = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/726f8cd6-6459-4db4-8e6d-2cd2716904e2/resourceGroups/test/providers/Microsoft.Network/trafficManagerProfiles/testpp2",
        },
        Ttl = 3600,
        ZoneName = "zone1",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewRecordSet(ctx, "recordSet", &network.RecordSetArgs{
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			RecordType:            pulumi.String("A"),
			RelativeRecordSetName: pulumi.String("record1"),
			ResourceGroupName:     pulumi.String("rg1"),
			TargetResource: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/726f8cd6-6459-4db4-8e6d-2cd2716904e2/resourceGroups/test/providers/Microsoft.Network/trafficManagerProfiles/testpp2"),
			},
			Ttl:      pulumi.Float64(3600),
			ZoneName: pulumi.String("zone1"),
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
import com.pulumi.azurenative.network.RecordSet;
import com.pulumi.azurenative.network.RecordSetArgs;
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
        var recordSet = new RecordSet("recordSet", RecordSetArgs.builder()        
            .metadata(Map.of("key1", "value1"))
            .recordType("A")
            .relativeRecordSetName("record1")
            .resourceGroupName("rg1")
            .targetResource(Map.of("id", "/subscriptions/726f8cd6-6459-4db4-8e6d-2cd2716904e2/resourceGroups/test/providers/Microsoft.Network/trafficManagerProfiles/testpp2"))
            .ttl(3600)
            .zoneName("zone1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const recordSet = new azure_native.network.RecordSet("recordSet", {
    metadata: {
        key1: "value1",
    },
    recordType: "A",
    relativeRecordSetName: "record1",
    resourceGroupName: "rg1",
    targetResource: {
        id: "/subscriptions/726f8cd6-6459-4db4-8e6d-2cd2716904e2/resourceGroups/test/providers/Microsoft.Network/trafficManagerProfiles/testpp2",
    },
    ttl: 3600,
    zoneName: "zone1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

record_set = azure_native.network.RecordSet("recordSet",
    metadata={
        "key1": "value1",
    },
    record_type="A",
    relative_record_set_name="record1",
    resource_group_name="rg1",
    target_resource=azure_native.network.SubResourceArgs(
        id="/subscriptions/726f8cd6-6459-4db4-8e6d-2cd2716904e2/resourceGroups/test/providers/Microsoft.Network/trafficManagerProfiles/testpp2",
    ),
    ttl=3600,
    zone_name="zone1")

```

```yaml
resources:
  recordSet:
    type: azure-native:network:RecordSet
    properties:
      metadata:
        key1: value1
      recordType: A
      relativeRecordSetName: record1
      resourceGroupName: rg1
      targetResource:
        id: /subscriptions/726f8cd6-6459-4db4-8e6d-2cd2716904e2/resourceGroups/test/providers/Microsoft.Network/trafficManagerProfiles/testpp2
      ttl: 3600
      zoneName: zone1

```

{{% /example %}}
{{% example %}}
### Create AAAA recordset
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var recordSet = new AzureNative.Network.RecordSet("recordSet", new()
    {
        AaaaRecords = new[]
        {
            new AzureNative.Network.Inputs.AaaaRecordArgs
            {
                Ipv6Address = "::1",
            },
        },
        Metadata = 
        {
            { "key1", "value1" },
        },
        RecordType = "AAAA",
        RelativeRecordSetName = "record1",
        ResourceGroupName = "rg1",
        Ttl = 3600,
        ZoneName = "zone1",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewRecordSet(ctx, "recordSet", &network.RecordSetArgs{
			AaaaRecords: []network.AaaaRecordArgs{
				{
					Ipv6Address: pulumi.String("::1"),
				},
			},
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			RecordType:            pulumi.String("AAAA"),
			RelativeRecordSetName: pulumi.String("record1"),
			ResourceGroupName:     pulumi.String("rg1"),
			Ttl:                   pulumi.Float64(3600),
			ZoneName:              pulumi.String("zone1"),
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
import com.pulumi.azurenative.network.RecordSet;
import com.pulumi.azurenative.network.RecordSetArgs;
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
        var recordSet = new RecordSet("recordSet", RecordSetArgs.builder()        
            .aaaaRecords(Map.of("ipv6Address", "::1"))
            .metadata(Map.of("key1", "value1"))
            .recordType("AAAA")
            .relativeRecordSetName("record1")
            .resourceGroupName("rg1")
            .ttl(3600)
            .zoneName("zone1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const recordSet = new azure_native.network.RecordSet("recordSet", {
    aaaaRecords: [{
        ipv6Address: "::1",
    }],
    metadata: {
        key1: "value1",
    },
    recordType: "AAAA",
    relativeRecordSetName: "record1",
    resourceGroupName: "rg1",
    ttl: 3600,
    zoneName: "zone1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

record_set = azure_native.network.RecordSet("recordSet",
    aaaa_records=[azure_native.network.AaaaRecordArgs(
        ipv6_address="::1",
    )],
    metadata={
        "key1": "value1",
    },
    record_type="AAAA",
    relative_record_set_name="record1",
    resource_group_name="rg1",
    ttl=3600,
    zone_name="zone1")

```

```yaml
resources:
  recordSet:
    type: azure-native:network:RecordSet
    properties:
      aaaaRecords:
        - ipv6Address: ::1
      metadata:
        key1: value1
      recordType: AAAA
      relativeRecordSetName: record1
      resourceGroupName: rg1
      ttl: 3600
      zoneName: zone1

```

{{% /example %}}
{{% example %}}
### Create CAA recordset
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var recordSet = new AzureNative.Network.RecordSet("recordSet", new()
    {
        CaaRecords = new[]
        {
            new AzureNative.Network.Inputs.CaaRecordArgs
            {
                Flags = 0,
                Tag = "issue",
                Value = "ca.contoso.com",
            },
        },
        Metadata = 
        {
            { "key1", "value1" },
        },
        RecordType = "CAA",
        RelativeRecordSetName = "record1",
        ResourceGroupName = "rg1",
        Ttl = 3600,
        ZoneName = "zone1",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewRecordSet(ctx, "recordSet", &network.RecordSetArgs{
			CaaRecords: []network.CaaRecordArgs{
				{
					Flags: pulumi.Int(0),
					Tag:   pulumi.String("issue"),
					Value: pulumi.String("ca.contoso.com"),
				},
			},
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			RecordType:            pulumi.String("CAA"),
			RelativeRecordSetName: pulumi.String("record1"),
			ResourceGroupName:     pulumi.String("rg1"),
			Ttl:                   pulumi.Float64(3600),
			ZoneName:              pulumi.String("zone1"),
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
import com.pulumi.azurenative.network.RecordSet;
import com.pulumi.azurenative.network.RecordSetArgs;
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
        var recordSet = new RecordSet("recordSet", RecordSetArgs.builder()        
            .caaRecords(Map.ofEntries(
                Map.entry("flags", 0),
                Map.entry("tag", "issue"),
                Map.entry("value", "ca.contoso.com")
            ))
            .metadata(Map.of("key1", "value1"))
            .recordType("CAA")
            .relativeRecordSetName("record1")
            .resourceGroupName("rg1")
            .ttl(3600)
            .zoneName("zone1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const recordSet = new azure_native.network.RecordSet("recordSet", {
    caaRecords: [{
        flags: 0,
        tag: "issue",
        value: "ca.contoso.com",
    }],
    metadata: {
        key1: "value1",
    },
    recordType: "CAA",
    relativeRecordSetName: "record1",
    resourceGroupName: "rg1",
    ttl: 3600,
    zoneName: "zone1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

record_set = azure_native.network.RecordSet("recordSet",
    caa_records=[azure_native.network.CaaRecordArgs(
        flags=0,
        tag="issue",
        value="ca.contoso.com",
    )],
    metadata={
        "key1": "value1",
    },
    record_type="CAA",
    relative_record_set_name="record1",
    resource_group_name="rg1",
    ttl=3600,
    zone_name="zone1")

```

```yaml
resources:
  recordSet:
    type: azure-native:network:RecordSet
    properties:
      caaRecords:
        - flags: 0
          tag: issue
          value: ca.contoso.com
      metadata:
        key1: value1
      recordType: CAA
      relativeRecordSetName: record1
      resourceGroupName: rg1
      ttl: 3600
      zoneName: zone1

```

{{% /example %}}
{{% example %}}
### Create CNAME recordset
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var recordSet = new AzureNative.Network.RecordSet("recordSet", new()
    {
        CnameRecord = new AzureNative.Network.Inputs.CnameRecordArgs
        {
            Cname = "contoso.com",
        },
        Metadata = 
        {
            { "key1", "value1" },
        },
        RecordType = "CNAME",
        RelativeRecordSetName = "record1",
        ResourceGroupName = "rg1",
        Ttl = 3600,
        ZoneName = "zone1",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewRecordSet(ctx, "recordSet", &network.RecordSetArgs{
			CnameRecord: &network.CnameRecordArgs{
				Cname: pulumi.String("contoso.com"),
			},
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			RecordType:            pulumi.String("CNAME"),
			RelativeRecordSetName: pulumi.String("record1"),
			ResourceGroupName:     pulumi.String("rg1"),
			Ttl:                   pulumi.Float64(3600),
			ZoneName:              pulumi.String("zone1"),
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
import com.pulumi.azurenative.network.RecordSet;
import com.pulumi.azurenative.network.RecordSetArgs;
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
        var recordSet = new RecordSet("recordSet", RecordSetArgs.builder()        
            .cnameRecord(Map.of("cname", "contoso.com"))
            .metadata(Map.of("key1", "value1"))
            .recordType("CNAME")
            .relativeRecordSetName("record1")
            .resourceGroupName("rg1")
            .ttl(3600)
            .zoneName("zone1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const recordSet = new azure_native.network.RecordSet("recordSet", {
    cnameRecord: {
        cname: "contoso.com",
    },
    metadata: {
        key1: "value1",
    },
    recordType: "CNAME",
    relativeRecordSetName: "record1",
    resourceGroupName: "rg1",
    ttl: 3600,
    zoneName: "zone1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

record_set = azure_native.network.RecordSet("recordSet",
    cname_record=azure_native.network.CnameRecordArgs(
        cname="contoso.com",
    ),
    metadata={
        "key1": "value1",
    },
    record_type="CNAME",
    relative_record_set_name="record1",
    resource_group_name="rg1",
    ttl=3600,
    zone_name="zone1")

```

```yaml
resources:
  recordSet:
    type: azure-native:network:RecordSet
    properties:
      cnameRecord:
        cname: contoso.com
      metadata:
        key1: value1
      recordType: CNAME
      relativeRecordSetName: record1
      resourceGroupName: rg1
      ttl: 3600
      zoneName: zone1

```

{{% /example %}}
{{% example %}}
### Create MX recordset
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var recordSet = new AzureNative.Network.RecordSet("recordSet", new()
    {
        Metadata = 
        {
            { "key1", "value1" },
        },
        MxRecords = new[]
        {
            new AzureNative.Network.Inputs.MxRecordArgs
            {
                Exchange = "mail.contoso.com",
                Preference = 0,
            },
        },
        RecordType = "MX",
        RelativeRecordSetName = "record1",
        ResourceGroupName = "rg1",
        Ttl = 3600,
        ZoneName = "zone1",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewRecordSet(ctx, "recordSet", &network.RecordSetArgs{
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			MxRecords: []network.MxRecordArgs{
				{
					Exchange:   pulumi.String("mail.contoso.com"),
					Preference: pulumi.Int(0),
				},
			},
			RecordType:            pulumi.String("MX"),
			RelativeRecordSetName: pulumi.String("record1"),
			ResourceGroupName:     pulumi.String("rg1"),
			Ttl:                   pulumi.Float64(3600),
			ZoneName:              pulumi.String("zone1"),
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
import com.pulumi.azurenative.network.RecordSet;
import com.pulumi.azurenative.network.RecordSetArgs;
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
        var recordSet = new RecordSet("recordSet", RecordSetArgs.builder()        
            .metadata(Map.of("key1", "value1"))
            .mxRecords(Map.ofEntries(
                Map.entry("exchange", "mail.contoso.com"),
                Map.entry("preference", 0)
            ))
            .recordType("MX")
            .relativeRecordSetName("record1")
            .resourceGroupName("rg1")
            .ttl(3600)
            .zoneName("zone1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const recordSet = new azure_native.network.RecordSet("recordSet", {
    metadata: {
        key1: "value1",
    },
    mxRecords: [{
        exchange: "mail.contoso.com",
        preference: 0,
    }],
    recordType: "MX",
    relativeRecordSetName: "record1",
    resourceGroupName: "rg1",
    ttl: 3600,
    zoneName: "zone1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

record_set = azure_native.network.RecordSet("recordSet",
    metadata={
        "key1": "value1",
    },
    mx_records=[azure_native.network.MxRecordArgs(
        exchange="mail.contoso.com",
        preference=0,
    )],
    record_type="MX",
    relative_record_set_name="record1",
    resource_group_name="rg1",
    ttl=3600,
    zone_name="zone1")

```

```yaml
resources:
  recordSet:
    type: azure-native:network:RecordSet
    properties:
      metadata:
        key1: value1
      mxRecords:
        - exchange: mail.contoso.com
          preference: 0
      recordType: MX
      relativeRecordSetName: record1
      resourceGroupName: rg1
      ttl: 3600
      zoneName: zone1

```

{{% /example %}}
{{% example %}}
### Create NS recordset
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var recordSet = new AzureNative.Network.RecordSet("recordSet", new()
    {
        Metadata = 
        {
            { "key1", "value1" },
        },
        NsRecords = new[]
        {
            new AzureNative.Network.Inputs.NsRecordArgs
            {
                Nsdname = "ns1.contoso.com",
            },
        },
        RecordType = "NS",
        RelativeRecordSetName = "record1",
        ResourceGroupName = "rg1",
        Ttl = 3600,
        ZoneName = "zone1",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewRecordSet(ctx, "recordSet", &network.RecordSetArgs{
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			NsRecords: []network.NsRecordArgs{
				{
					Nsdname: pulumi.String("ns1.contoso.com"),
				},
			},
			RecordType:            pulumi.String("NS"),
			RelativeRecordSetName: pulumi.String("record1"),
			ResourceGroupName:     pulumi.String("rg1"),
			Ttl:                   pulumi.Float64(3600),
			ZoneName:              pulumi.String("zone1"),
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
import com.pulumi.azurenative.network.RecordSet;
import com.pulumi.azurenative.network.RecordSetArgs;
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
        var recordSet = new RecordSet("recordSet", RecordSetArgs.builder()        
            .metadata(Map.of("key1", "value1"))
            .nsRecords(Map.of("nsdname", "ns1.contoso.com"))
            .recordType("NS")
            .relativeRecordSetName("record1")
            .resourceGroupName("rg1")
            .ttl(3600)
            .zoneName("zone1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const recordSet = new azure_native.network.RecordSet("recordSet", {
    metadata: {
        key1: "value1",
    },
    nsRecords: [{
        nsdname: "ns1.contoso.com",
    }],
    recordType: "NS",
    relativeRecordSetName: "record1",
    resourceGroupName: "rg1",
    ttl: 3600,
    zoneName: "zone1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

record_set = azure_native.network.RecordSet("recordSet",
    metadata={
        "key1": "value1",
    },
    ns_records=[azure_native.network.NsRecordArgs(
        nsdname="ns1.contoso.com",
    )],
    record_type="NS",
    relative_record_set_name="record1",
    resource_group_name="rg1",
    ttl=3600,
    zone_name="zone1")

```

```yaml
resources:
  recordSet:
    type: azure-native:network:RecordSet
    properties:
      metadata:
        key1: value1
      nsRecords:
        - nsdname: ns1.contoso.com
      recordType: NS
      relativeRecordSetName: record1
      resourceGroupName: rg1
      ttl: 3600
      zoneName: zone1

```

{{% /example %}}
{{% example %}}
### Create PTR recordset
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var recordSet = new AzureNative.Network.RecordSet("recordSet", new()
    {
        Metadata = 
        {
            { "key1", "value1" },
        },
        PtrRecords = new[]
        {
            new AzureNative.Network.Inputs.PtrRecordArgs
            {
                Ptrdname = "localhost",
            },
        },
        RecordType = "PTR",
        RelativeRecordSetName = "1",
        ResourceGroupName = "rg1",
        Ttl = 3600,
        ZoneName = "0.0.127.in-addr.arpa",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewRecordSet(ctx, "recordSet", &network.RecordSetArgs{
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			PtrRecords: []network.PtrRecordArgs{
				{
					Ptrdname: pulumi.String("localhost"),
				},
			},
			RecordType:            pulumi.String("PTR"),
			RelativeRecordSetName: pulumi.String("1"),
			ResourceGroupName:     pulumi.String("rg1"),
			Ttl:                   pulumi.Float64(3600),
			ZoneName:              pulumi.String("0.0.127.in-addr.arpa"),
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
import com.pulumi.azurenative.network.RecordSet;
import com.pulumi.azurenative.network.RecordSetArgs;
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
        var recordSet = new RecordSet("recordSet", RecordSetArgs.builder()        
            .metadata(Map.of("key1", "value1"))
            .ptrRecords(Map.of("ptrdname", "localhost"))
            .recordType("PTR")
            .relativeRecordSetName("1")
            .resourceGroupName("rg1")
            .ttl(3600)
            .zoneName("0.0.127.in-addr.arpa")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const recordSet = new azure_native.network.RecordSet("recordSet", {
    metadata: {
        key1: "value1",
    },
    ptrRecords: [{
        ptrdname: "localhost",
    }],
    recordType: "PTR",
    relativeRecordSetName: "1",
    resourceGroupName: "rg1",
    ttl: 3600,
    zoneName: "0.0.127.in-addr.arpa",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

record_set = azure_native.network.RecordSet("recordSet",
    metadata={
        "key1": "value1",
    },
    ptr_records=[azure_native.network.PtrRecordArgs(
        ptrdname="localhost",
    )],
    record_type="PTR",
    relative_record_set_name="1",
    resource_group_name="rg1",
    ttl=3600,
    zone_name="0.0.127.in-addr.arpa")

```

```yaml
resources:
  recordSet:
    type: azure-native:network:RecordSet
    properties:
      metadata:
        key1: value1
      ptrRecords:
        - ptrdname: localhost
      recordType: PTR
      relativeRecordSetName: '1'
      resourceGroupName: rg1
      ttl: 3600
      zoneName: 0.0.127.in-addr.arpa

```

{{% /example %}}
{{% example %}}
### Create SOA recordset
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var recordSet = new AzureNative.Network.RecordSet("recordSet", new()
    {
        Metadata = 
        {
            { "key1", "value1" },
        },
        RecordType = "SOA",
        RelativeRecordSetName = "@",
        ResourceGroupName = "rg1",
        SoaRecord = new AzureNative.Network.Inputs.SoaRecordArgs
        {
            Email = "hostmaster.contoso.com",
            ExpireTime = 2419200,
            Host = "ns1.contoso.com",
            MinimumTtl = 300,
            RefreshTime = 3600,
            RetryTime = 300,
            SerialNumber = 1,
        },
        Ttl = 3600,
        ZoneName = "zone1",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewRecordSet(ctx, "recordSet", &network.RecordSetArgs{
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			RecordType:            pulumi.String("SOA"),
			RelativeRecordSetName: pulumi.String("@"),
			ResourceGroupName:     pulumi.String("rg1"),
			SoaRecord: &network.SoaRecordArgs{
				Email:        pulumi.String("hostmaster.contoso.com"),
				ExpireTime:   pulumi.Float64(2419200),
				Host:         pulumi.String("ns1.contoso.com"),
				MinimumTtl:   pulumi.Float64(300),
				RefreshTime:  pulumi.Float64(3600),
				RetryTime:    pulumi.Float64(300),
				SerialNumber: pulumi.Float64(1),
			},
			Ttl:      pulumi.Float64(3600),
			ZoneName: pulumi.String("zone1"),
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
import com.pulumi.azurenative.network.RecordSet;
import com.pulumi.azurenative.network.RecordSetArgs;
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
        var recordSet = new RecordSet("recordSet", RecordSetArgs.builder()        
            .metadata(Map.of("key1", "value1"))
            .recordType("SOA")
            .relativeRecordSetName("@")
            .resourceGroupName("rg1")
            .soaRecord(Map.ofEntries(
                Map.entry("email", "hostmaster.contoso.com"),
                Map.entry("expireTime", 2419200),
                Map.entry("host", "ns1.contoso.com"),
                Map.entry("minimumTtl", 300),
                Map.entry("refreshTime", 3600),
                Map.entry("retryTime", 300),
                Map.entry("serialNumber", 1)
            ))
            .ttl(3600)
            .zoneName("zone1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const recordSet = new azure_native.network.RecordSet("recordSet", {
    metadata: {
        key1: "value1",
    },
    recordType: "SOA",
    relativeRecordSetName: "@",
    resourceGroupName: "rg1",
    soaRecord: {
        email: "hostmaster.contoso.com",
        expireTime: 2419200,
        host: "ns1.contoso.com",
        minimumTtl: 300,
        refreshTime: 3600,
        retryTime: 300,
        serialNumber: 1,
    },
    ttl: 3600,
    zoneName: "zone1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

record_set = azure_native.network.RecordSet("recordSet",
    metadata={
        "key1": "value1",
    },
    record_type="SOA",
    relative_record_set_name="@",
    resource_group_name="rg1",
    soa_record=azure_native.network.SoaRecordArgs(
        email="hostmaster.contoso.com",
        expire_time=2419200,
        host="ns1.contoso.com",
        minimum_ttl=300,
        refresh_time=3600,
        retry_time=300,
        serial_number=1,
    ),
    ttl=3600,
    zone_name="zone1")

```

```yaml
resources:
  recordSet:
    type: azure-native:network:RecordSet
    properties:
      metadata:
        key1: value1
      recordType: SOA
      relativeRecordSetName: '@'
      resourceGroupName: rg1
      soaRecord:
        email: hostmaster.contoso.com
        expireTime: 2.4192e+06
        host: ns1.contoso.com
        minimumTtl: 300
        refreshTime: 3600
        retryTime: 300
        serialNumber: 1
      ttl: 3600
      zoneName: zone1

```

{{% /example %}}
{{% example %}}
### Create SRV recordset
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var recordSet = new AzureNative.Network.RecordSet("recordSet", new()
    {
        Metadata = 
        {
            { "key1", "value1" },
        },
        RecordType = "SRV",
        RelativeRecordSetName = "record1",
        ResourceGroupName = "rg1",
        SrvRecords = new[]
        {
            new AzureNative.Network.Inputs.SrvRecordArgs
            {
                Port = 80,
                Priority = 0,
                Target = "contoso.com",
                Weight = 10,
            },
        },
        Ttl = 3600,
        ZoneName = "zone1",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewRecordSet(ctx, "recordSet", &network.RecordSetArgs{
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			RecordType:            pulumi.String("SRV"),
			RelativeRecordSetName: pulumi.String("record1"),
			ResourceGroupName:     pulumi.String("rg1"),
			SrvRecords: []network.SrvRecordArgs{
				{
					Port:     pulumi.Int(80),
					Priority: pulumi.Int(0),
					Target:   pulumi.String("contoso.com"),
					Weight:   pulumi.Int(10),
				},
			},
			Ttl:      pulumi.Float64(3600),
			ZoneName: pulumi.String("zone1"),
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
import com.pulumi.azurenative.network.RecordSet;
import com.pulumi.azurenative.network.RecordSetArgs;
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
        var recordSet = new RecordSet("recordSet", RecordSetArgs.builder()        
            .metadata(Map.of("key1", "value1"))
            .recordType("SRV")
            .relativeRecordSetName("record1")
            .resourceGroupName("rg1")
            .srvRecords(Map.ofEntries(
                Map.entry("port", 80),
                Map.entry("priority", 0),
                Map.entry("target", "contoso.com"),
                Map.entry("weight", 10)
            ))
            .ttl(3600)
            .zoneName("zone1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const recordSet = new azure_native.network.RecordSet("recordSet", {
    metadata: {
        key1: "value1",
    },
    recordType: "SRV",
    relativeRecordSetName: "record1",
    resourceGroupName: "rg1",
    srvRecords: [{
        port: 80,
        priority: 0,
        target: "contoso.com",
        weight: 10,
    }],
    ttl: 3600,
    zoneName: "zone1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

record_set = azure_native.network.RecordSet("recordSet",
    metadata={
        "key1": "value1",
    },
    record_type="SRV",
    relative_record_set_name="record1",
    resource_group_name="rg1",
    srv_records=[azure_native.network.SrvRecordArgs(
        port=80,
        priority=0,
        target="contoso.com",
        weight=10,
    )],
    ttl=3600,
    zone_name="zone1")

```

```yaml
resources:
  recordSet:
    type: azure-native:network:RecordSet
    properties:
      metadata:
        key1: value1
      recordType: SRV
      relativeRecordSetName: record1
      resourceGroupName: rg1
      srvRecords:
        - port: 80
          priority: 0
          target: contoso.com
          weight: 10
      ttl: 3600
      zoneName: zone1

```

{{% /example %}}
{{% example %}}
### Create TXT recordset
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var recordSet = new AzureNative.Network.RecordSet("recordSet", new()
    {
        Metadata = 
        {
            { "key1", "value1" },
        },
        RecordType = "TXT",
        RelativeRecordSetName = "record1",
        ResourceGroupName = "rg1",
        Ttl = 3600,
        TxtRecords = new[]
        {
            new AzureNative.Network.Inputs.TxtRecordArgs
            {
                Value = new[]
                {
                    "string1",
                    "string2",
                },
            },
        },
        ZoneName = "zone1",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewRecordSet(ctx, "recordSet", &network.RecordSetArgs{
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			RecordType:            pulumi.String("TXT"),
			RelativeRecordSetName: pulumi.String("record1"),
			ResourceGroupName:     pulumi.String("rg1"),
			Ttl:                   pulumi.Float64(3600),
			TxtRecords: []network.TxtRecordArgs{
				{
					Value: pulumi.StringArray{
						pulumi.String("string1"),
						pulumi.String("string2"),
					},
				},
			},
			ZoneName: pulumi.String("zone1"),
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
import com.pulumi.azurenative.network.RecordSet;
import com.pulumi.azurenative.network.RecordSetArgs;
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
        var recordSet = new RecordSet("recordSet", RecordSetArgs.builder()        
            .metadata(Map.of("key1", "value1"))
            .recordType("TXT")
            .relativeRecordSetName("record1")
            .resourceGroupName("rg1")
            .ttl(3600)
            .txtRecords(Map.of("value",             
                "string1",
                "string2"))
            .zoneName("zone1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const recordSet = new azure_native.network.RecordSet("recordSet", {
    metadata: {
        key1: "value1",
    },
    recordType: "TXT",
    relativeRecordSetName: "record1",
    resourceGroupName: "rg1",
    ttl: 3600,
    txtRecords: [{
        value: [
            "string1",
            "string2",
        ],
    }],
    zoneName: "zone1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

record_set = azure_native.network.RecordSet("recordSet",
    metadata={
        "key1": "value1",
    },
    record_type="TXT",
    relative_record_set_name="record1",
    resource_group_name="rg1",
    ttl=3600,
    txt_records=[azure_native.network.TxtRecordArgs(
        value=[
            "string1",
            "string2",
        ],
    )],
    zone_name="zone1")

```

```yaml
resources:
  recordSet:
    type: azure-native:network:RecordSet
    properties:
      metadata:
        key1: value1
      recordType: TXT
      relativeRecordSetName: record1
      resourceGroupName: rg1
      ttl: 3600
      txtRecords:
        - value:
            - string1
            - string2
      zoneName: zone1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:RecordSet record1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/dnsZones/zone1/TXT/record1 
```
