Describes a DNS record set (a collection of DNS records with the same name and type) in a Private DNS zone.
API Version: 2020-06-01.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PUT Private DNS Zone A Record Set
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateRecordSet = new AzureNative.Network.PrivateRecordSet("privateRecordSet", new()
    {
        ARecords = new[]
        {
            new AzureNative.Network.Inputs.ARecordArgs
            {
                Ipv4Address = "1.2.3.4",
            },
        },
        Metadata = 
        {
            { "key1", "value1" },
        },
        PrivateZoneName = "privatezone1.com",
        RecordType = "A",
        RelativeRecordSetName = "recordA",
        ResourceGroupName = "resourceGroup1",
        Ttl = 3600,
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
		_, err := network.NewPrivateRecordSet(ctx, "privateRecordSet", &network.PrivateRecordSetArgs{
			ARecords: []network.ARecordArgs{
				{
					Ipv4Address: pulumi.String("1.2.3.4"),
				},
			},
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			PrivateZoneName:       pulumi.String("privatezone1.com"),
			RecordType:            pulumi.String("A"),
			RelativeRecordSetName: pulumi.String("recordA"),
			ResourceGroupName:     pulumi.String("resourceGroup1"),
			Ttl:                   pulumi.Float64(3600),
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
import com.pulumi.azurenative.network.PrivateRecordSet;
import com.pulumi.azurenative.network.PrivateRecordSetArgs;
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
        var privateRecordSet = new PrivateRecordSet("privateRecordSet", PrivateRecordSetArgs.builder()        
            .aRecords(Map.of("ipv4Address", "1.2.3.4"))
            .metadata(Map.of("key1", "value1"))
            .privateZoneName("privatezone1.com")
            .recordType("A")
            .relativeRecordSetName("recordA")
            .resourceGroupName("resourceGroup1")
            .ttl(3600)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateRecordSet = new azure_native.network.PrivateRecordSet("privateRecordSet", {
    aRecords: [{
        ipv4Address: "1.2.3.4",
    }],
    metadata: {
        key1: "value1",
    },
    privateZoneName: "privatezone1.com",
    recordType: "A",
    relativeRecordSetName: "recordA",
    resourceGroupName: "resourceGroup1",
    ttl: 3600,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_record_set = azure_native.network.PrivateRecordSet("privateRecordSet",
    a_records=[azure_native.network.ARecordArgs(
        ipv4_address="1.2.3.4",
    )],
    metadata={
        "key1": "value1",
    },
    private_zone_name="privatezone1.com",
    record_type="A",
    relative_record_set_name="recordA",
    resource_group_name="resourceGroup1",
    ttl=3600)

```

```yaml
resources:
  privateRecordSet:
    type: azure-native:network:PrivateRecordSet
    properties:
      aRecords:
        - ipv4Address: 1.2.3.4
      metadata:
        key1: value1
      privateZoneName: privatezone1.com
      recordType: A
      relativeRecordSetName: recordA
      resourceGroupName: resourceGroup1
      ttl: 3600

```

{{% /example %}}
{{% example %}}
### PUT Private DNS Zone AAAA Record Set
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateRecordSet = new AzureNative.Network.PrivateRecordSet("privateRecordSet", new()
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
        PrivateZoneName = "privatezone1.com",
        RecordType = "AAAA",
        RelativeRecordSetName = "recordAAAA",
        ResourceGroupName = "resourceGroup1",
        Ttl = 3600,
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
		_, err := network.NewPrivateRecordSet(ctx, "privateRecordSet", &network.PrivateRecordSetArgs{
			AaaaRecords: []network.AaaaRecordArgs{
				{
					Ipv6Address: pulumi.String("::1"),
				},
			},
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			PrivateZoneName:       pulumi.String("privatezone1.com"),
			RecordType:            pulumi.String("AAAA"),
			RelativeRecordSetName: pulumi.String("recordAAAA"),
			ResourceGroupName:     pulumi.String("resourceGroup1"),
			Ttl:                   pulumi.Float64(3600),
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
import com.pulumi.azurenative.network.PrivateRecordSet;
import com.pulumi.azurenative.network.PrivateRecordSetArgs;
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
        var privateRecordSet = new PrivateRecordSet("privateRecordSet", PrivateRecordSetArgs.builder()        
            .aaaaRecords(Map.of("ipv6Address", "::1"))
            .metadata(Map.of("key1", "value1"))
            .privateZoneName("privatezone1.com")
            .recordType("AAAA")
            .relativeRecordSetName("recordAAAA")
            .resourceGroupName("resourceGroup1")
            .ttl(3600)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateRecordSet = new azure_native.network.PrivateRecordSet("privateRecordSet", {
    aaaaRecords: [{
        ipv6Address: "::1",
    }],
    metadata: {
        key1: "value1",
    },
    privateZoneName: "privatezone1.com",
    recordType: "AAAA",
    relativeRecordSetName: "recordAAAA",
    resourceGroupName: "resourceGroup1",
    ttl: 3600,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_record_set = azure_native.network.PrivateRecordSet("privateRecordSet",
    aaaa_records=[azure_native.network.AaaaRecordArgs(
        ipv6_address="::1",
    )],
    metadata={
        "key1": "value1",
    },
    private_zone_name="privatezone1.com",
    record_type="AAAA",
    relative_record_set_name="recordAAAA",
    resource_group_name="resourceGroup1",
    ttl=3600)

```

```yaml
resources:
  privateRecordSet:
    type: azure-native:network:PrivateRecordSet
    properties:
      aaaaRecords:
        - ipv6Address: ::1
      metadata:
        key1: value1
      privateZoneName: privatezone1.com
      recordType: AAAA
      relativeRecordSetName: recordAAAA
      resourceGroupName: resourceGroup1
      ttl: 3600

```

{{% /example %}}
{{% example %}}
### PUT Private DNS Zone CNAME Record Set
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateRecordSet = new AzureNative.Network.PrivateRecordSet("privateRecordSet", new()
    {
        CnameRecord = new AzureNative.Network.Inputs.CnameRecordArgs
        {
            Cname = "contoso.com",
        },
        Metadata = 
        {
            { "key1", "value1" },
        },
        PrivateZoneName = "privatezone1.com",
        RecordType = "CNAME",
        RelativeRecordSetName = "recordCNAME",
        ResourceGroupName = "resourceGroup1",
        Ttl = 3600,
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
		_, err := network.NewPrivateRecordSet(ctx, "privateRecordSet", &network.PrivateRecordSetArgs{
			CnameRecord: &network.CnameRecordArgs{
				Cname: pulumi.String("contoso.com"),
			},
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			PrivateZoneName:       pulumi.String("privatezone1.com"),
			RecordType:            pulumi.String("CNAME"),
			RelativeRecordSetName: pulumi.String("recordCNAME"),
			ResourceGroupName:     pulumi.String("resourceGroup1"),
			Ttl:                   pulumi.Float64(3600),
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
import com.pulumi.azurenative.network.PrivateRecordSet;
import com.pulumi.azurenative.network.PrivateRecordSetArgs;
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
        var privateRecordSet = new PrivateRecordSet("privateRecordSet", PrivateRecordSetArgs.builder()        
            .cnameRecord(Map.of("cname", "contoso.com"))
            .metadata(Map.of("key1", "value1"))
            .privateZoneName("privatezone1.com")
            .recordType("CNAME")
            .relativeRecordSetName("recordCNAME")
            .resourceGroupName("resourceGroup1")
            .ttl(3600)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateRecordSet = new azure_native.network.PrivateRecordSet("privateRecordSet", {
    cnameRecord: {
        cname: "contoso.com",
    },
    metadata: {
        key1: "value1",
    },
    privateZoneName: "privatezone1.com",
    recordType: "CNAME",
    relativeRecordSetName: "recordCNAME",
    resourceGroupName: "resourceGroup1",
    ttl: 3600,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_record_set = azure_native.network.PrivateRecordSet("privateRecordSet",
    cname_record=azure_native.network.CnameRecordArgs(
        cname="contoso.com",
    ),
    metadata={
        "key1": "value1",
    },
    private_zone_name="privatezone1.com",
    record_type="CNAME",
    relative_record_set_name="recordCNAME",
    resource_group_name="resourceGroup1",
    ttl=3600)

```

```yaml
resources:
  privateRecordSet:
    type: azure-native:network:PrivateRecordSet
    properties:
      cnameRecord:
        cname: contoso.com
      metadata:
        key1: value1
      privateZoneName: privatezone1.com
      recordType: CNAME
      relativeRecordSetName: recordCNAME
      resourceGroupName: resourceGroup1
      ttl: 3600

```

{{% /example %}}
{{% example %}}
### PUT Private DNS Zone MX Record Set
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateRecordSet = new AzureNative.Network.PrivateRecordSet("privateRecordSet", new()
    {
        Metadata = 
        {
            { "key1", "value1" },
        },
        MxRecords = new[]
        {
            new AzureNative.Network.Inputs.MxRecordArgs
            {
                Exchange = "mail.privatezone1.com",
                Preference = 0,
            },
        },
        PrivateZoneName = "privatezone1.com",
        RecordType = "MX",
        RelativeRecordSetName = "recordMX",
        ResourceGroupName = "resourceGroup1",
        Ttl = 3600,
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
		_, err := network.NewPrivateRecordSet(ctx, "privateRecordSet", &network.PrivateRecordSetArgs{
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			MxRecords: []network.MxRecordArgs{
				{
					Exchange:   pulumi.String("mail.privatezone1.com"),
					Preference: pulumi.Int(0),
				},
			},
			PrivateZoneName:       pulumi.String("privatezone1.com"),
			RecordType:            pulumi.String("MX"),
			RelativeRecordSetName: pulumi.String("recordMX"),
			ResourceGroupName:     pulumi.String("resourceGroup1"),
			Ttl:                   pulumi.Float64(3600),
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
import com.pulumi.azurenative.network.PrivateRecordSet;
import com.pulumi.azurenative.network.PrivateRecordSetArgs;
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
        var privateRecordSet = new PrivateRecordSet("privateRecordSet", PrivateRecordSetArgs.builder()        
            .metadata(Map.of("key1", "value1"))
            .mxRecords(Map.ofEntries(
                Map.entry("exchange", "mail.privatezone1.com"),
                Map.entry("preference", 0)
            ))
            .privateZoneName("privatezone1.com")
            .recordType("MX")
            .relativeRecordSetName("recordMX")
            .resourceGroupName("resourceGroup1")
            .ttl(3600)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateRecordSet = new azure_native.network.PrivateRecordSet("privateRecordSet", {
    metadata: {
        key1: "value1",
    },
    mxRecords: [{
        exchange: "mail.privatezone1.com",
        preference: 0,
    }],
    privateZoneName: "privatezone1.com",
    recordType: "MX",
    relativeRecordSetName: "recordMX",
    resourceGroupName: "resourceGroup1",
    ttl: 3600,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_record_set = azure_native.network.PrivateRecordSet("privateRecordSet",
    metadata={
        "key1": "value1",
    },
    mx_records=[azure_native.network.MxRecordArgs(
        exchange="mail.privatezone1.com",
        preference=0,
    )],
    private_zone_name="privatezone1.com",
    record_type="MX",
    relative_record_set_name="recordMX",
    resource_group_name="resourceGroup1",
    ttl=3600)

```

```yaml
resources:
  privateRecordSet:
    type: azure-native:network:PrivateRecordSet
    properties:
      metadata:
        key1: value1
      mxRecords:
        - exchange: mail.privatezone1.com
          preference: 0
      privateZoneName: privatezone1.com
      recordType: MX
      relativeRecordSetName: recordMX
      resourceGroupName: resourceGroup1
      ttl: 3600

```

{{% /example %}}
{{% example %}}
### PUT Private DNS Zone PTR Record Set
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateRecordSet = new AzureNative.Network.PrivateRecordSet("privateRecordSet", new()
    {
        Metadata = 
        {
            { "key1", "value1" },
        },
        PrivateZoneName = "0.0.127.in-addr.arpa",
        PtrRecords = new[]
        {
            new AzureNative.Network.Inputs.PtrRecordArgs
            {
                Ptrdname = "localhost",
            },
        },
        RecordType = "PTR",
        RelativeRecordSetName = "1",
        ResourceGroupName = "resourceGroup1",
        Ttl = 3600,
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
		_, err := network.NewPrivateRecordSet(ctx, "privateRecordSet", &network.PrivateRecordSetArgs{
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			PrivateZoneName: pulumi.String("0.0.127.in-addr.arpa"),
			PtrRecords: []network.PtrRecordArgs{
				{
					Ptrdname: pulumi.String("localhost"),
				},
			},
			RecordType:            pulumi.String("PTR"),
			RelativeRecordSetName: pulumi.String("1"),
			ResourceGroupName:     pulumi.String("resourceGroup1"),
			Ttl:                   pulumi.Float64(3600),
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
import com.pulumi.azurenative.network.PrivateRecordSet;
import com.pulumi.azurenative.network.PrivateRecordSetArgs;
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
        var privateRecordSet = new PrivateRecordSet("privateRecordSet", PrivateRecordSetArgs.builder()        
            .metadata(Map.of("key1", "value1"))
            .privateZoneName("0.0.127.in-addr.arpa")
            .ptrRecords(Map.of("ptrdname", "localhost"))
            .recordType("PTR")
            .relativeRecordSetName("1")
            .resourceGroupName("resourceGroup1")
            .ttl(3600)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateRecordSet = new azure_native.network.PrivateRecordSet("privateRecordSet", {
    metadata: {
        key1: "value1",
    },
    privateZoneName: "0.0.127.in-addr.arpa",
    ptrRecords: [{
        ptrdname: "localhost",
    }],
    recordType: "PTR",
    relativeRecordSetName: "1",
    resourceGroupName: "resourceGroup1",
    ttl: 3600,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_record_set = azure_native.network.PrivateRecordSet("privateRecordSet",
    metadata={
        "key1": "value1",
    },
    private_zone_name="0.0.127.in-addr.arpa",
    ptr_records=[azure_native.network.PtrRecordArgs(
        ptrdname="localhost",
    )],
    record_type="PTR",
    relative_record_set_name="1",
    resource_group_name="resourceGroup1",
    ttl=3600)

```

```yaml
resources:
  privateRecordSet:
    type: azure-native:network:PrivateRecordSet
    properties:
      metadata:
        key1: value1
      privateZoneName: 0.0.127.in-addr.arpa
      ptrRecords:
        - ptrdname: localhost
      recordType: PTR
      relativeRecordSetName: '1'
      resourceGroupName: resourceGroup1
      ttl: 3600

```

{{% /example %}}
{{% example %}}
### PUT Private DNS Zone SOA Record Set
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateRecordSet = new AzureNative.Network.PrivateRecordSet("privateRecordSet", new()
    {
        Metadata = 
        {
            { "key1", "value1" },
        },
        PrivateZoneName = "privatezone1.com",
        RecordType = "SOA",
        RelativeRecordSetName = "@",
        ResourceGroupName = "resourceGroup1",
        SoaRecord = new AzureNative.Network.Inputs.SoaRecordArgs
        {
            Email = "azureprivatedns-hostmaster.microsoft.com",
            ExpireTime = 2419200,
            Host = "azureprivatedns.net",
            MinimumTtl = 300,
            RefreshTime = 3600,
            RetryTime = 300,
            SerialNumber = 1,
        },
        Ttl = 3600,
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
		_, err := network.NewPrivateRecordSet(ctx, "privateRecordSet", &network.PrivateRecordSetArgs{
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			PrivateZoneName:       pulumi.String("privatezone1.com"),
			RecordType:            pulumi.String("SOA"),
			RelativeRecordSetName: pulumi.String("@"),
			ResourceGroupName:     pulumi.String("resourceGroup1"),
			SoaRecord: &network.SoaRecordArgs{
				Email:        pulumi.String("azureprivatedns-hostmaster.microsoft.com"),
				ExpireTime:   pulumi.Float64(2419200),
				Host:         pulumi.String("azureprivatedns.net"),
				MinimumTtl:   pulumi.Float64(300),
				RefreshTime:  pulumi.Float64(3600),
				RetryTime:    pulumi.Float64(300),
				SerialNumber: pulumi.Float64(1),
			},
			Ttl: pulumi.Float64(3600),
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
import com.pulumi.azurenative.network.PrivateRecordSet;
import com.pulumi.azurenative.network.PrivateRecordSetArgs;
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
        var privateRecordSet = new PrivateRecordSet("privateRecordSet", PrivateRecordSetArgs.builder()        
            .metadata(Map.of("key1", "value1"))
            .privateZoneName("privatezone1.com")
            .recordType("SOA")
            .relativeRecordSetName("@")
            .resourceGroupName("resourceGroup1")
            .soaRecord(Map.ofEntries(
                Map.entry("email", "azureprivatedns-hostmaster.microsoft.com"),
                Map.entry("expireTime", 2419200),
                Map.entry("host", "azureprivatedns.net"),
                Map.entry("minimumTtl", 300),
                Map.entry("refreshTime", 3600),
                Map.entry("retryTime", 300),
                Map.entry("serialNumber", 1)
            ))
            .ttl(3600)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateRecordSet = new azure_native.network.PrivateRecordSet("privateRecordSet", {
    metadata: {
        key1: "value1",
    },
    privateZoneName: "privatezone1.com",
    recordType: "SOA",
    relativeRecordSetName: "@",
    resourceGroupName: "resourceGroup1",
    soaRecord: {
        email: "azureprivatedns-hostmaster.microsoft.com",
        expireTime: 2419200,
        host: "azureprivatedns.net",
        minimumTtl: 300,
        refreshTime: 3600,
        retryTime: 300,
        serialNumber: 1,
    },
    ttl: 3600,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_record_set = azure_native.network.PrivateRecordSet("privateRecordSet",
    metadata={
        "key1": "value1",
    },
    private_zone_name="privatezone1.com",
    record_type="SOA",
    relative_record_set_name="@",
    resource_group_name="resourceGroup1",
    soa_record=azure_native.network.SoaRecordArgs(
        email="azureprivatedns-hostmaster.microsoft.com",
        expire_time=2419200,
        host="azureprivatedns.net",
        minimum_ttl=300,
        refresh_time=3600,
        retry_time=300,
        serial_number=1,
    ),
    ttl=3600)

```

```yaml
resources:
  privateRecordSet:
    type: azure-native:network:PrivateRecordSet
    properties:
      metadata:
        key1: value1
      privateZoneName: privatezone1.com
      recordType: SOA
      relativeRecordSetName: '@'
      resourceGroupName: resourceGroup1
      soaRecord:
        email: azureprivatedns-hostmaster.microsoft.com
        expireTime: 2.4192e+06
        host: azureprivatedns.net
        minimumTtl: 300
        refreshTime: 3600
        retryTime: 300
        serialNumber: 1
      ttl: 3600

```

{{% /example %}}
{{% example %}}
### PUT Private DNS Zone SRV Record Set
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateRecordSet = new AzureNative.Network.PrivateRecordSet("privateRecordSet", new()
    {
        Metadata = 
        {
            { "key1", "value1" },
        },
        PrivateZoneName = "privatezone1.com",
        RecordType = "SRV",
        RelativeRecordSetName = "recordSRV",
        ResourceGroupName = "resourceGroup1",
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
		_, err := network.NewPrivateRecordSet(ctx, "privateRecordSet", &network.PrivateRecordSetArgs{
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			PrivateZoneName:       pulumi.String("privatezone1.com"),
			RecordType:            pulumi.String("SRV"),
			RelativeRecordSetName: pulumi.String("recordSRV"),
			ResourceGroupName:     pulumi.String("resourceGroup1"),
			SrvRecords: []network.SrvRecordArgs{
				{
					Port:     pulumi.Int(80),
					Priority: pulumi.Int(0),
					Target:   pulumi.String("contoso.com"),
					Weight:   pulumi.Int(10),
				},
			},
			Ttl: pulumi.Float64(3600),
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
import com.pulumi.azurenative.network.PrivateRecordSet;
import com.pulumi.azurenative.network.PrivateRecordSetArgs;
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
        var privateRecordSet = new PrivateRecordSet("privateRecordSet", PrivateRecordSetArgs.builder()        
            .metadata(Map.of("key1", "value1"))
            .privateZoneName("privatezone1.com")
            .recordType("SRV")
            .relativeRecordSetName("recordSRV")
            .resourceGroupName("resourceGroup1")
            .srvRecords(Map.ofEntries(
                Map.entry("port", 80),
                Map.entry("priority", 0),
                Map.entry("target", "contoso.com"),
                Map.entry("weight", 10)
            ))
            .ttl(3600)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateRecordSet = new azure_native.network.PrivateRecordSet("privateRecordSet", {
    metadata: {
        key1: "value1",
    },
    privateZoneName: "privatezone1.com",
    recordType: "SRV",
    relativeRecordSetName: "recordSRV",
    resourceGroupName: "resourceGroup1",
    srvRecords: [{
        port: 80,
        priority: 0,
        target: "contoso.com",
        weight: 10,
    }],
    ttl: 3600,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_record_set = azure_native.network.PrivateRecordSet("privateRecordSet",
    metadata={
        "key1": "value1",
    },
    private_zone_name="privatezone1.com",
    record_type="SRV",
    relative_record_set_name="recordSRV",
    resource_group_name="resourceGroup1",
    srv_records=[azure_native.network.SrvRecordArgs(
        port=80,
        priority=0,
        target="contoso.com",
        weight=10,
    )],
    ttl=3600)

```

```yaml
resources:
  privateRecordSet:
    type: azure-native:network:PrivateRecordSet
    properties:
      metadata:
        key1: value1
      privateZoneName: privatezone1.com
      recordType: SRV
      relativeRecordSetName: recordSRV
      resourceGroupName: resourceGroup1
      srvRecords:
        - port: 80
          priority: 0
          target: contoso.com
          weight: 10
      ttl: 3600

```

{{% /example %}}
{{% example %}}
### PUT Private DNS Zone TXT Record Set
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateRecordSet = new AzureNative.Network.PrivateRecordSet("privateRecordSet", new()
    {
        Metadata = 
        {
            { "key1", "value1" },
        },
        PrivateZoneName = "privatezone1.com",
        RecordType = "TXT",
        RelativeRecordSetName = "recordTXT",
        ResourceGroupName = "resourceGroup1",
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
		_, err := network.NewPrivateRecordSet(ctx, "privateRecordSet", &network.PrivateRecordSetArgs{
			Metadata: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			PrivateZoneName:       pulumi.String("privatezone1.com"),
			RecordType:            pulumi.String("TXT"),
			RelativeRecordSetName: pulumi.String("recordTXT"),
			ResourceGroupName:     pulumi.String("resourceGroup1"),
			Ttl:                   pulumi.Float64(3600),
			TxtRecords: []network.TxtRecordArgs{
				{
					Value: pulumi.StringArray{
						pulumi.String("string1"),
						pulumi.String("string2"),
					},
				},
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
import com.pulumi.azurenative.network.PrivateRecordSet;
import com.pulumi.azurenative.network.PrivateRecordSetArgs;
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
        var privateRecordSet = new PrivateRecordSet("privateRecordSet", PrivateRecordSetArgs.builder()        
            .metadata(Map.of("key1", "value1"))
            .privateZoneName("privatezone1.com")
            .recordType("TXT")
            .relativeRecordSetName("recordTXT")
            .resourceGroupName("resourceGroup1")
            .ttl(3600)
            .txtRecords(Map.of("value",             
                "string1",
                "string2"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateRecordSet = new azure_native.network.PrivateRecordSet("privateRecordSet", {
    metadata: {
        key1: "value1",
    },
    privateZoneName: "privatezone1.com",
    recordType: "TXT",
    relativeRecordSetName: "recordTXT",
    resourceGroupName: "resourceGroup1",
    ttl: 3600,
    txtRecords: [{
        value: [
            "string1",
            "string2",
        ],
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_record_set = azure_native.network.PrivateRecordSet("privateRecordSet",
    metadata={
        "key1": "value1",
    },
    private_zone_name="privatezone1.com",
    record_type="TXT",
    relative_record_set_name="recordTXT",
    resource_group_name="resourceGroup1",
    ttl=3600,
    txt_records=[azure_native.network.TxtRecordArgs(
        value=[
            "string1",
            "string2",
        ],
    )])

```

```yaml
resources:
  privateRecordSet:
    type: azure-native:network:PrivateRecordSet
    properties:
      metadata:
        key1: value1
      privateZoneName: privatezone1.com
      recordType: TXT
      relativeRecordSetName: recordTXT
      resourceGroupName: resourceGroup1
      ttl: 3600
      txtRecords:
        - value:
            - string1
            - string2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:PrivateRecordSet recordtxt /subscriptions/subscriptionId/resourceGroups/resourceGroup1/providers/Microsoft.Network/privateDnsZones/privatezone1.com/TXT/recordtxt 
```
