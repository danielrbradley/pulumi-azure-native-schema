A provider instance associated with SAP monitor.
API Version: 2023-04-01.
Previous API Version: 2021-12-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a Db2 provider
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var providerInstance = new AzureNative.Workloads.ProviderInstance("providerInstance", new()
    {
        MonitorName = "mySapMonitor",
        ProviderInstanceName = "myProviderInstance",
        ProviderSettings = new AzureNative.Workloads.Inputs.DB2ProviderInstancePropertiesArgs
        {
            DbName = "dbName",
            DbPassword = "password",
            DbPasswordUri = "",
            DbPort = "dbPort",
            DbUsername = "username",
            Hostname = "hostname",
            ProviderType = "Db2",
            SapSid = "SID",
            SslCertificateUri = "https://storageaccount.blob.core.windows.net/containername/filename",
            SslPreference = "ServerCertificate",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewProviderInstance(ctx, "providerInstance", &workloads.ProviderInstanceArgs{
			MonitorName:          pulumi.String("mySapMonitor"),
			ProviderInstanceName: pulumi.String("myProviderInstance"),
			ProviderSettings: workloads.DB2ProviderInstanceProperties{
				DbName:            "dbName",
				DbPassword:        "password",
				DbPasswordUri:     "",
				DbPort:            "dbPort",
				DbUsername:        "username",
				Hostname:          "hostname",
				ProviderType:      "Db2",
				SapSid:            "SID",
				SslCertificateUri: "https://storageaccount.blob.core.windows.net/containername/filename",
				SslPreference:     "ServerCertificate",
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.workloads.ProviderInstance;
import com.pulumi.azurenative.workloads.ProviderInstanceArgs;
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
        var providerInstance = new ProviderInstance("providerInstance", ProviderInstanceArgs.builder()        
            .monitorName("mySapMonitor")
            .providerInstanceName("myProviderInstance")
            .providerSettings(Map.ofEntries(
                Map.entry("dbName", "dbName"),
                Map.entry("dbPassword", "password"),
                Map.entry("dbPasswordUri", ""),
                Map.entry("dbPort", "dbPort"),
                Map.entry("dbUsername", "username"),
                Map.entry("hostname", "hostname"),
                Map.entry("providerType", "Db2"),
                Map.entry("sapSid", "SID"),
                Map.entry("sslCertificateUri", "https://storageaccount.blob.core.windows.net/containername/filename"),
                Map.entry("sslPreference", "ServerCertificate")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const providerInstance = new azure_native.workloads.ProviderInstance("providerInstance", {
    monitorName: "mySapMonitor",
    providerInstanceName: "myProviderInstance",
    providerSettings: {
        dbName: "dbName",
        dbPassword: "password",
        dbPasswordUri: "",
        dbPort: "dbPort",
        dbUsername: "username",
        hostname: "hostname",
        providerType: "Db2",
        sapSid: "SID",
        sslCertificateUri: "https://storageaccount.blob.core.windows.net/containername/filename",
        sslPreference: "ServerCertificate",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provider_instance = azure_native.workloads.ProviderInstance("providerInstance",
    monitor_name="mySapMonitor",
    provider_instance_name="myProviderInstance",
    provider_settings=azure_native.workloads.DB2ProviderInstancePropertiesArgs(
        db_name="dbName",
        db_password="password",
        db_password_uri="",
        db_port="dbPort",
        db_username="username",
        hostname="hostname",
        provider_type="Db2",
        sap_sid="SID",
        ssl_certificate_uri="https://storageaccount.blob.core.windows.net/containername/filename",
        ssl_preference="ServerCertificate",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  providerInstance:
    type: azure-native:workloads:ProviderInstance
    properties:
      monitorName: mySapMonitor
      providerInstanceName: myProviderInstance
      providerSettings:
        dbName: dbName
        dbPassword: password
        dbPasswordUri:
        dbPort: dbPort
        dbUsername: username
        hostname: hostname
        providerType: Db2
        sapSid: SID
        sslCertificateUri: https://storageaccount.blob.core.windows.net/containername/filename
        sslPreference: ServerCertificate
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a Db2 provider with Root Certificate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var providerInstance = new AzureNative.Workloads.ProviderInstance("providerInstance", new()
    {
        MonitorName = "mySapMonitor",
        ProviderInstanceName = "myProviderInstance",
        ProviderSettings = new AzureNative.Workloads.Inputs.DB2ProviderInstancePropertiesArgs
        {
            DbName = "dbName",
            DbPassword = "password",
            DbPasswordUri = "",
            DbPort = "dbPort",
            DbUsername = "username",
            Hostname = "hostname",
            ProviderType = "Db2",
            SapSid = "SID",
            SslPreference = "RootCertificate",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewProviderInstance(ctx, "providerInstance", &workloads.ProviderInstanceArgs{
			MonitorName:          pulumi.String("mySapMonitor"),
			ProviderInstanceName: pulumi.String("myProviderInstance"),
			ProviderSettings: workloads.DB2ProviderInstanceProperties{
				DbName:        "dbName",
				DbPassword:    "password",
				DbPasswordUri: "",
				DbPort:        "dbPort",
				DbUsername:    "username",
				Hostname:      "hostname",
				ProviderType:  "Db2",
				SapSid:        "SID",
				SslPreference: "RootCertificate",
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.workloads.ProviderInstance;
import com.pulumi.azurenative.workloads.ProviderInstanceArgs;
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
        var providerInstance = new ProviderInstance("providerInstance", ProviderInstanceArgs.builder()        
            .monitorName("mySapMonitor")
            .providerInstanceName("myProviderInstance")
            .providerSettings(Map.ofEntries(
                Map.entry("dbName", "dbName"),
                Map.entry("dbPassword", "password"),
                Map.entry("dbPasswordUri", ""),
                Map.entry("dbPort", "dbPort"),
                Map.entry("dbUsername", "username"),
                Map.entry("hostname", "hostname"),
                Map.entry("providerType", "Db2"),
                Map.entry("sapSid", "SID"),
                Map.entry("sslPreference", "RootCertificate")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const providerInstance = new azure_native.workloads.ProviderInstance("providerInstance", {
    monitorName: "mySapMonitor",
    providerInstanceName: "myProviderInstance",
    providerSettings: {
        dbName: "dbName",
        dbPassword: "password",
        dbPasswordUri: "",
        dbPort: "dbPort",
        dbUsername: "username",
        hostname: "hostname",
        providerType: "Db2",
        sapSid: "SID",
        sslPreference: "RootCertificate",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provider_instance = azure_native.workloads.ProviderInstance("providerInstance",
    monitor_name="mySapMonitor",
    provider_instance_name="myProviderInstance",
    provider_settings=azure_native.workloads.DB2ProviderInstancePropertiesArgs(
        db_name="dbName",
        db_password="password",
        db_password_uri="",
        db_port="dbPort",
        db_username="username",
        hostname="hostname",
        provider_type="Db2",
        sap_sid="SID",
        ssl_preference="RootCertificate",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  providerInstance:
    type: azure-native:workloads:ProviderInstance
    properties:
      monitorName: mySapMonitor
      providerInstanceName: myProviderInstance
      providerSettings:
        dbName: dbName
        dbPassword: password
        dbPasswordUri:
        dbPort: dbPort
        dbUsername: username
        hostname: hostname
        providerType: Db2
        sapSid: SID
        sslPreference: RootCertificate
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a MsSqlServer provider
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var providerInstance = new AzureNative.Workloads.ProviderInstance("providerInstance", new()
    {
        MonitorName = "mySapMonitor",
        ProviderInstanceName = "myProviderInstance",
        ProviderSettings = new AzureNative.Workloads.Inputs.MsSqlServerProviderInstancePropertiesArgs
        {
            DbPassword = "****",
            DbPasswordUri = "",
            DbPort = "5912",
            DbUsername = "user",
            Hostname = "hostname",
            ProviderType = "MsSqlServer",
            SapSid = "sid",
            SslCertificateUri = "https://storageaccount.blob.core.windows.net/containername/filename",
            SslPreference = "ServerCertificate",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewProviderInstance(ctx, "providerInstance", &workloads.ProviderInstanceArgs{
			MonitorName:          pulumi.String("mySapMonitor"),
			ProviderInstanceName: pulumi.String("myProviderInstance"),
			ProviderSettings: workloads.MsSqlServerProviderInstanceProperties{
				DbPassword:        "****",
				DbPasswordUri:     "",
				DbPort:            "5912",
				DbUsername:        "user",
				Hostname:          "hostname",
				ProviderType:      "MsSqlServer",
				SapSid:            "sid",
				SslCertificateUri: "https://storageaccount.blob.core.windows.net/containername/filename",
				SslPreference:     "ServerCertificate",
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.workloads.ProviderInstance;
import com.pulumi.azurenative.workloads.ProviderInstanceArgs;
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
        var providerInstance = new ProviderInstance("providerInstance", ProviderInstanceArgs.builder()        
            .monitorName("mySapMonitor")
            .providerInstanceName("myProviderInstance")
            .providerSettings(Map.ofEntries(
                Map.entry("dbPassword", "****"),
                Map.entry("dbPasswordUri", ""),
                Map.entry("dbPort", "5912"),
                Map.entry("dbUsername", "user"),
                Map.entry("hostname", "hostname"),
                Map.entry("providerType", "MsSqlServer"),
                Map.entry("sapSid", "sid"),
                Map.entry("sslCertificateUri", "https://storageaccount.blob.core.windows.net/containername/filename"),
                Map.entry("sslPreference", "ServerCertificate")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const providerInstance = new azure_native.workloads.ProviderInstance("providerInstance", {
    monitorName: "mySapMonitor",
    providerInstanceName: "myProviderInstance",
    providerSettings: {
        dbPassword: "****",
        dbPasswordUri: "",
        dbPort: "5912",
        dbUsername: "user",
        hostname: "hostname",
        providerType: "MsSqlServer",
        sapSid: "sid",
        sslCertificateUri: "https://storageaccount.blob.core.windows.net/containername/filename",
        sslPreference: "ServerCertificate",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provider_instance = azure_native.workloads.ProviderInstance("providerInstance",
    monitor_name="mySapMonitor",
    provider_instance_name="myProviderInstance",
    provider_settings=azure_native.workloads.MsSqlServerProviderInstancePropertiesArgs(
        db_password="****",
        db_password_uri="",
        db_port="5912",
        db_username="user",
        hostname="hostname",
        provider_type="MsSqlServer",
        sap_sid="sid",
        ssl_certificate_uri="https://storageaccount.blob.core.windows.net/containername/filename",
        ssl_preference="ServerCertificate",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  providerInstance:
    type: azure-native:workloads:ProviderInstance
    properties:
      monitorName: mySapMonitor
      providerInstanceName: myProviderInstance
      providerSettings:
        dbPassword: '****'
        dbPasswordUri:
        dbPort: '5912'
        dbUsername: user
        hostname: hostname
        providerType: MsSqlServer
        sapSid: sid
        sslCertificateUri: https://storageaccount.blob.core.windows.net/containername/filename
        sslPreference: ServerCertificate
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a MsSqlServer provider with Root Certificate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var providerInstance = new AzureNative.Workloads.ProviderInstance("providerInstance", new()
    {
        MonitorName = "mySapMonitor",
        ProviderInstanceName = "myProviderInstance",
        ProviderSettings = new AzureNative.Workloads.Inputs.MsSqlServerProviderInstancePropertiesArgs
        {
            DbPassword = "****",
            DbPasswordUri = "",
            DbPort = "5912",
            DbUsername = "user",
            Hostname = "hostname",
            ProviderType = "MsSqlServer",
            SapSid = "sid",
            SslPreference = "RootCertificate",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewProviderInstance(ctx, "providerInstance", &workloads.ProviderInstanceArgs{
			MonitorName:          pulumi.String("mySapMonitor"),
			ProviderInstanceName: pulumi.String("myProviderInstance"),
			ProviderSettings: workloads.MsSqlServerProviderInstanceProperties{
				DbPassword:    "****",
				DbPasswordUri: "",
				DbPort:        "5912",
				DbUsername:    "user",
				Hostname:      "hostname",
				ProviderType:  "MsSqlServer",
				SapSid:        "sid",
				SslPreference: "RootCertificate",
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.workloads.ProviderInstance;
import com.pulumi.azurenative.workloads.ProviderInstanceArgs;
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
        var providerInstance = new ProviderInstance("providerInstance", ProviderInstanceArgs.builder()        
            .monitorName("mySapMonitor")
            .providerInstanceName("myProviderInstance")
            .providerSettings(Map.ofEntries(
                Map.entry("dbPassword", "****"),
                Map.entry("dbPasswordUri", ""),
                Map.entry("dbPort", "5912"),
                Map.entry("dbUsername", "user"),
                Map.entry("hostname", "hostname"),
                Map.entry("providerType", "MsSqlServer"),
                Map.entry("sapSid", "sid"),
                Map.entry("sslPreference", "RootCertificate")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const providerInstance = new azure_native.workloads.ProviderInstance("providerInstance", {
    monitorName: "mySapMonitor",
    providerInstanceName: "myProviderInstance",
    providerSettings: {
        dbPassword: "****",
        dbPasswordUri: "",
        dbPort: "5912",
        dbUsername: "user",
        hostname: "hostname",
        providerType: "MsSqlServer",
        sapSid: "sid",
        sslPreference: "RootCertificate",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provider_instance = azure_native.workloads.ProviderInstance("providerInstance",
    monitor_name="mySapMonitor",
    provider_instance_name="myProviderInstance",
    provider_settings=azure_native.workloads.MsSqlServerProviderInstancePropertiesArgs(
        db_password="****",
        db_password_uri="",
        db_port="5912",
        db_username="user",
        hostname="hostname",
        provider_type="MsSqlServer",
        sap_sid="sid",
        ssl_preference="RootCertificate",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  providerInstance:
    type: azure-native:workloads:ProviderInstance
    properties:
      monitorName: mySapMonitor
      providerInstanceName: myProviderInstance
      providerSettings:
        dbPassword: '****'
        dbPasswordUri:
        dbPort: '5912'
        dbUsername: user
        hostname: hostname
        providerType: MsSqlServer
        sapSid: sid
        sslPreference: RootCertificate
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a OS provider
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var providerInstance = new AzureNative.Workloads.ProviderInstance("providerInstance", new()
    {
        MonitorName = "mySapMonitor",
        ProviderInstanceName = "myProviderInstance",
        ProviderSettings = new AzureNative.Workloads.Inputs.PrometheusOSProviderInstancePropertiesArgs
        {
            PrometheusUrl = "http://192.168.0.0:9090/metrics",
            ProviderType = "PrometheusOS",
            SapSid = "SID",
            SslCertificateUri = "https://storageaccount.blob.core.windows.net/containername/filename",
            SslPreference = "ServerCertificate",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewProviderInstance(ctx, "providerInstance", &workloads.ProviderInstanceArgs{
			MonitorName:          pulumi.String("mySapMonitor"),
			ProviderInstanceName: pulumi.String("myProviderInstance"),
			ProviderSettings: workloads.PrometheusOSProviderInstanceProperties{
				PrometheusUrl:     "http://192.168.0.0:9090/metrics",
				ProviderType:      "PrometheusOS",
				SapSid:            "SID",
				SslCertificateUri: "https://storageaccount.blob.core.windows.net/containername/filename",
				SslPreference:     "ServerCertificate",
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.workloads.ProviderInstance;
import com.pulumi.azurenative.workloads.ProviderInstanceArgs;
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
        var providerInstance = new ProviderInstance("providerInstance", ProviderInstanceArgs.builder()        
            .monitorName("mySapMonitor")
            .providerInstanceName("myProviderInstance")
            .providerSettings(Map.ofEntries(
                Map.entry("prometheusUrl", "http://192.168.0.0:9090/metrics"),
                Map.entry("providerType", "PrometheusOS"),
                Map.entry("sapSid", "SID"),
                Map.entry("sslCertificateUri", "https://storageaccount.blob.core.windows.net/containername/filename"),
                Map.entry("sslPreference", "ServerCertificate")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const providerInstance = new azure_native.workloads.ProviderInstance("providerInstance", {
    monitorName: "mySapMonitor",
    providerInstanceName: "myProviderInstance",
    providerSettings: {
        prometheusUrl: "http://192.168.0.0:9090/metrics",
        providerType: "PrometheusOS",
        sapSid: "SID",
        sslCertificateUri: "https://storageaccount.blob.core.windows.net/containername/filename",
        sslPreference: "ServerCertificate",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provider_instance = azure_native.workloads.ProviderInstance("providerInstance",
    monitor_name="mySapMonitor",
    provider_instance_name="myProviderInstance",
    provider_settings=azure_native.workloads.PrometheusOSProviderInstancePropertiesArgs(
        prometheus_url="http://192.168.0.0:9090/metrics",
        provider_type="PrometheusOS",
        sap_sid="SID",
        ssl_certificate_uri="https://storageaccount.blob.core.windows.net/containername/filename",
        ssl_preference="ServerCertificate",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  providerInstance:
    type: azure-native:workloads:ProviderInstance
    properties:
      monitorName: mySapMonitor
      providerInstanceName: myProviderInstance
      providerSettings:
        prometheusUrl: http://192.168.0.0:9090/metrics
        providerType: PrometheusOS
        sapSid: SID
        sslCertificateUri: https://storageaccount.blob.core.windows.net/containername/filename
        sslPreference: ServerCertificate
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a OS provider with Root Certificate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var providerInstance = new AzureNative.Workloads.ProviderInstance("providerInstance", new()
    {
        MonitorName = "mySapMonitor",
        ProviderInstanceName = "myProviderInstance",
        ProviderSettings = new AzureNative.Workloads.Inputs.PrometheusOSProviderInstancePropertiesArgs
        {
            PrometheusUrl = "http://192.168.0.0:9090/metrics",
            ProviderType = "PrometheusOS",
            SapSid = "SID",
            SslPreference = "RootCertificate",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewProviderInstance(ctx, "providerInstance", &workloads.ProviderInstanceArgs{
			MonitorName:          pulumi.String("mySapMonitor"),
			ProviderInstanceName: pulumi.String("myProviderInstance"),
			ProviderSettings: workloads.PrometheusOSProviderInstanceProperties{
				PrometheusUrl: "http://192.168.0.0:9090/metrics",
				ProviderType:  "PrometheusOS",
				SapSid:        "SID",
				SslPreference: "RootCertificate",
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.workloads.ProviderInstance;
import com.pulumi.azurenative.workloads.ProviderInstanceArgs;
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
        var providerInstance = new ProviderInstance("providerInstance", ProviderInstanceArgs.builder()        
            .monitorName("mySapMonitor")
            .providerInstanceName("myProviderInstance")
            .providerSettings(Map.ofEntries(
                Map.entry("prometheusUrl", "http://192.168.0.0:9090/metrics"),
                Map.entry("providerType", "PrometheusOS"),
                Map.entry("sapSid", "SID"),
                Map.entry("sslPreference", "RootCertificate")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const providerInstance = new azure_native.workloads.ProviderInstance("providerInstance", {
    monitorName: "mySapMonitor",
    providerInstanceName: "myProviderInstance",
    providerSettings: {
        prometheusUrl: "http://192.168.0.0:9090/metrics",
        providerType: "PrometheusOS",
        sapSid: "SID",
        sslPreference: "RootCertificate",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provider_instance = azure_native.workloads.ProviderInstance("providerInstance",
    monitor_name="mySapMonitor",
    provider_instance_name="myProviderInstance",
    provider_settings=azure_native.workloads.PrometheusOSProviderInstancePropertiesArgs(
        prometheus_url="http://192.168.0.0:9090/metrics",
        provider_type="PrometheusOS",
        sap_sid="SID",
        ssl_preference="RootCertificate",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  providerInstance:
    type: azure-native:workloads:ProviderInstance
    properties:
      monitorName: mySapMonitor
      providerInstanceName: myProviderInstance
      providerSettings:
        prometheusUrl: http://192.168.0.0:9090/metrics
        providerType: PrometheusOS
        sapSid: SID
        sslPreference: RootCertificate
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a PrometheusHaCluster provider
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var providerInstance = new AzureNative.Workloads.ProviderInstance("providerInstance", new()
    {
        MonitorName = "mySapMonitor",
        ProviderInstanceName = "myProviderInstance",
        ProviderSettings = new AzureNative.Workloads.Inputs.PrometheusHaClusterProviderInstancePropertiesArgs
        {
            ClusterName = "clusterName",
            Hostname = "hostname",
            PrometheusUrl = "http://192.168.0.0:9090/metrics",
            ProviderType = "PrometheusHaCluster",
            Sid = "sid",
            SslCertificateUri = "https://storageaccount.blob.core.windows.net/containername/filename",
            SslPreference = "ServerCertificate",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewProviderInstance(ctx, "providerInstance", &workloads.ProviderInstanceArgs{
			MonitorName:          pulumi.String("mySapMonitor"),
			ProviderInstanceName: pulumi.String("myProviderInstance"),
			ProviderSettings: workloads.PrometheusHaClusterProviderInstanceProperties{
				ClusterName:       "clusterName",
				Hostname:          "hostname",
				PrometheusUrl:     "http://192.168.0.0:9090/metrics",
				ProviderType:      "PrometheusHaCluster",
				Sid:               "sid",
				SslCertificateUri: "https://storageaccount.blob.core.windows.net/containername/filename",
				SslPreference:     "ServerCertificate",
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.workloads.ProviderInstance;
import com.pulumi.azurenative.workloads.ProviderInstanceArgs;
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
        var providerInstance = new ProviderInstance("providerInstance", ProviderInstanceArgs.builder()        
            .monitorName("mySapMonitor")
            .providerInstanceName("myProviderInstance")
            .providerSettings(Map.ofEntries(
                Map.entry("clusterName", "clusterName"),
                Map.entry("hostname", "hostname"),
                Map.entry("prometheusUrl", "http://192.168.0.0:9090/metrics"),
                Map.entry("providerType", "PrometheusHaCluster"),
                Map.entry("sid", "sid"),
                Map.entry("sslCertificateUri", "https://storageaccount.blob.core.windows.net/containername/filename"),
                Map.entry("sslPreference", "ServerCertificate")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const providerInstance = new azure_native.workloads.ProviderInstance("providerInstance", {
    monitorName: "mySapMonitor",
    providerInstanceName: "myProviderInstance",
    providerSettings: {
        clusterName: "clusterName",
        hostname: "hostname",
        prometheusUrl: "http://192.168.0.0:9090/metrics",
        providerType: "PrometheusHaCluster",
        sid: "sid",
        sslCertificateUri: "https://storageaccount.blob.core.windows.net/containername/filename",
        sslPreference: "ServerCertificate",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provider_instance = azure_native.workloads.ProviderInstance("providerInstance",
    monitor_name="mySapMonitor",
    provider_instance_name="myProviderInstance",
    provider_settings=azure_native.workloads.PrometheusHaClusterProviderInstancePropertiesArgs(
        cluster_name="clusterName",
        hostname="hostname",
        prometheus_url="http://192.168.0.0:9090/metrics",
        provider_type="PrometheusHaCluster",
        sid="sid",
        ssl_certificate_uri="https://storageaccount.blob.core.windows.net/containername/filename",
        ssl_preference="ServerCertificate",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  providerInstance:
    type: azure-native:workloads:ProviderInstance
    properties:
      monitorName: mySapMonitor
      providerInstanceName: myProviderInstance
      providerSettings:
        clusterName: clusterName
        hostname: hostname
        prometheusUrl: http://192.168.0.0:9090/metrics
        providerType: PrometheusHaCluster
        sid: sid
        sslCertificateUri: https://storageaccount.blob.core.windows.net/containername/filename
        sslPreference: ServerCertificate
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a PrometheusHaCluster provider with Root Certificate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var providerInstance = new AzureNative.Workloads.ProviderInstance("providerInstance", new()
    {
        MonitorName = "mySapMonitor",
        ProviderInstanceName = "myProviderInstance",
        ProviderSettings = new AzureNative.Workloads.Inputs.PrometheusHaClusterProviderInstancePropertiesArgs
        {
            ClusterName = "clusterName",
            Hostname = "hostname",
            PrometheusUrl = "http://192.168.0.0:9090/metrics",
            ProviderType = "PrometheusHaCluster",
            Sid = "sid",
            SslPreference = "RootCertificate",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewProviderInstance(ctx, "providerInstance", &workloads.ProviderInstanceArgs{
			MonitorName:          pulumi.String("mySapMonitor"),
			ProviderInstanceName: pulumi.String("myProviderInstance"),
			ProviderSettings: workloads.PrometheusHaClusterProviderInstanceProperties{
				ClusterName:   "clusterName",
				Hostname:      "hostname",
				PrometheusUrl: "http://192.168.0.0:9090/metrics",
				ProviderType:  "PrometheusHaCluster",
				Sid:           "sid",
				SslPreference: "RootCertificate",
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.workloads.ProviderInstance;
import com.pulumi.azurenative.workloads.ProviderInstanceArgs;
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
        var providerInstance = new ProviderInstance("providerInstance", ProviderInstanceArgs.builder()        
            .monitorName("mySapMonitor")
            .providerInstanceName("myProviderInstance")
            .providerSettings(Map.ofEntries(
                Map.entry("clusterName", "clusterName"),
                Map.entry("hostname", "hostname"),
                Map.entry("prometheusUrl", "http://192.168.0.0:9090/metrics"),
                Map.entry("providerType", "PrometheusHaCluster"),
                Map.entry("sid", "sid"),
                Map.entry("sslPreference", "RootCertificate")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const providerInstance = new azure_native.workloads.ProviderInstance("providerInstance", {
    monitorName: "mySapMonitor",
    providerInstanceName: "myProviderInstance",
    providerSettings: {
        clusterName: "clusterName",
        hostname: "hostname",
        prometheusUrl: "http://192.168.0.0:9090/metrics",
        providerType: "PrometheusHaCluster",
        sid: "sid",
        sslPreference: "RootCertificate",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provider_instance = azure_native.workloads.ProviderInstance("providerInstance",
    monitor_name="mySapMonitor",
    provider_instance_name="myProviderInstance",
    provider_settings=azure_native.workloads.PrometheusHaClusterProviderInstancePropertiesArgs(
        cluster_name="clusterName",
        hostname="hostname",
        prometheus_url="http://192.168.0.0:9090/metrics",
        provider_type="PrometheusHaCluster",
        sid="sid",
        ssl_preference="RootCertificate",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  providerInstance:
    type: azure-native:workloads:ProviderInstance
    properties:
      monitorName: mySapMonitor
      providerInstanceName: myProviderInstance
      providerSettings:
        clusterName: clusterName
        hostname: hostname
        prometheusUrl: http://192.168.0.0:9090/metrics
        providerType: PrometheusHaCluster
        sid: sid
        sslPreference: RootCertificate
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a SAP monitor Hana provider
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var providerInstance = new AzureNative.Workloads.ProviderInstance("providerInstance", new()
    {
        MonitorName = "mySapMonitor",
        ProviderInstanceName = "myProviderInstance",
        ProviderSettings = new AzureNative.Workloads.Inputs.HanaDbProviderInstancePropertiesArgs
        {
            DbName = "db",
            DbPassword = "****",
            DbPasswordUri = "",
            DbUsername = "user",
            Hostname = "name",
            InstanceNumber = "00",
            ProviderType = "SapHana",
            SapSid = "SID",
            SqlPort = "0000",
            SslCertificateUri = "https://storageaccount.blob.core.windows.net/containername/filename",
            SslHostNameInCertificate = "xyz.domain.com",
            SslPreference = "ServerCertificate",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewProviderInstance(ctx, "providerInstance", &workloads.ProviderInstanceArgs{
			MonitorName:          pulumi.String("mySapMonitor"),
			ProviderInstanceName: pulumi.String("myProviderInstance"),
			ProviderSettings: workloads.HanaDbProviderInstanceProperties{
				DbName:                   "db",
				DbPassword:               "****",
				DbPasswordUri:            "",
				DbUsername:               "user",
				Hostname:                 "name",
				InstanceNumber:           "00",
				ProviderType:             "SapHana",
				SapSid:                   "SID",
				SqlPort:                  "0000",
				SslCertificateUri:        "https://storageaccount.blob.core.windows.net/containername/filename",
				SslHostNameInCertificate: "xyz.domain.com",
				SslPreference:            "ServerCertificate",
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.workloads.ProviderInstance;
import com.pulumi.azurenative.workloads.ProviderInstanceArgs;
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
        var providerInstance = new ProviderInstance("providerInstance", ProviderInstanceArgs.builder()        
            .monitorName("mySapMonitor")
            .providerInstanceName("myProviderInstance")
            .providerSettings(Map.ofEntries(
                Map.entry("dbName", "db"),
                Map.entry("dbPassword", "****"),
                Map.entry("dbPasswordUri", ""),
                Map.entry("dbUsername", "user"),
                Map.entry("hostname", "name"),
                Map.entry("instanceNumber", "00"),
                Map.entry("providerType", "SapHana"),
                Map.entry("sapSid", "SID"),
                Map.entry("sqlPort", "0000"),
                Map.entry("sslCertificateUri", "https://storageaccount.blob.core.windows.net/containername/filename"),
                Map.entry("sslHostNameInCertificate", "xyz.domain.com"),
                Map.entry("sslPreference", "ServerCertificate")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const providerInstance = new azure_native.workloads.ProviderInstance("providerInstance", {
    monitorName: "mySapMonitor",
    providerInstanceName: "myProviderInstance",
    providerSettings: {
        dbName: "db",
        dbPassword: "****",
        dbPasswordUri: "",
        dbUsername: "user",
        hostname: "name",
        instanceNumber: "00",
        providerType: "SapHana",
        sapSid: "SID",
        sqlPort: "0000",
        sslCertificateUri: "https://storageaccount.blob.core.windows.net/containername/filename",
        sslHostNameInCertificate: "xyz.domain.com",
        sslPreference: "ServerCertificate",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provider_instance = azure_native.workloads.ProviderInstance("providerInstance",
    monitor_name="mySapMonitor",
    provider_instance_name="myProviderInstance",
    provider_settings=azure_native.workloads.HanaDbProviderInstancePropertiesArgs(
        db_name="db",
        db_password="****",
        db_password_uri="",
        db_username="user",
        hostname="name",
        instance_number="00",
        provider_type="SapHana",
        sap_sid="SID",
        sql_port="0000",
        ssl_certificate_uri="https://storageaccount.blob.core.windows.net/containername/filename",
        ssl_host_name_in_certificate="xyz.domain.com",
        ssl_preference="ServerCertificate",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  providerInstance:
    type: azure-native:workloads:ProviderInstance
    properties:
      monitorName: mySapMonitor
      providerInstanceName: myProviderInstance
      providerSettings:
        dbName: db
        dbPassword: '****'
        dbPasswordUri:
        dbUsername: user
        hostname: name
        instanceNumber: '00'
        providerType: SapHana
        sapSid: SID
        sqlPort: '0000'
        sslCertificateUri: https://storageaccount.blob.core.windows.net/containername/filename
        sslHostNameInCertificate: xyz.domain.com
        sslPreference: ServerCertificate
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a SAP monitor Hana provider with Root Certificate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var providerInstance = new AzureNative.Workloads.ProviderInstance("providerInstance", new()
    {
        MonitorName = "mySapMonitor",
        ProviderInstanceName = "myProviderInstance",
        ProviderSettings = new AzureNative.Workloads.Inputs.HanaDbProviderInstancePropertiesArgs
        {
            DbName = "db",
            DbPassword = "****",
            DbPasswordUri = "",
            DbUsername = "user",
            Hostname = "name",
            InstanceNumber = "00",
            ProviderType = "SapHana",
            SapSid = "SID",
            SqlPort = "0000",
            SslHostNameInCertificate = "xyz.domain.com",
            SslPreference = "RootCertificate",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewProviderInstance(ctx, "providerInstance", &workloads.ProviderInstanceArgs{
			MonitorName:          pulumi.String("mySapMonitor"),
			ProviderInstanceName: pulumi.String("myProviderInstance"),
			ProviderSettings: workloads.HanaDbProviderInstanceProperties{
				DbName:                   "db",
				DbPassword:               "****",
				DbPasswordUri:            "",
				DbUsername:               "user",
				Hostname:                 "name",
				InstanceNumber:           "00",
				ProviderType:             "SapHana",
				SapSid:                   "SID",
				SqlPort:                  "0000",
				SslHostNameInCertificate: "xyz.domain.com",
				SslPreference:            "RootCertificate",
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.workloads.ProviderInstance;
import com.pulumi.azurenative.workloads.ProviderInstanceArgs;
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
        var providerInstance = new ProviderInstance("providerInstance", ProviderInstanceArgs.builder()        
            .monitorName("mySapMonitor")
            .providerInstanceName("myProviderInstance")
            .providerSettings(Map.ofEntries(
                Map.entry("dbName", "db"),
                Map.entry("dbPassword", "****"),
                Map.entry("dbPasswordUri", ""),
                Map.entry("dbUsername", "user"),
                Map.entry("hostname", "name"),
                Map.entry("instanceNumber", "00"),
                Map.entry("providerType", "SapHana"),
                Map.entry("sapSid", "SID"),
                Map.entry("sqlPort", "0000"),
                Map.entry("sslHostNameInCertificate", "xyz.domain.com"),
                Map.entry("sslPreference", "RootCertificate")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const providerInstance = new azure_native.workloads.ProviderInstance("providerInstance", {
    monitorName: "mySapMonitor",
    providerInstanceName: "myProviderInstance",
    providerSettings: {
        dbName: "db",
        dbPassword: "****",
        dbPasswordUri: "",
        dbUsername: "user",
        hostname: "name",
        instanceNumber: "00",
        providerType: "SapHana",
        sapSid: "SID",
        sqlPort: "0000",
        sslHostNameInCertificate: "xyz.domain.com",
        sslPreference: "RootCertificate",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provider_instance = azure_native.workloads.ProviderInstance("providerInstance",
    monitor_name="mySapMonitor",
    provider_instance_name="myProviderInstance",
    provider_settings=azure_native.workloads.HanaDbProviderInstancePropertiesArgs(
        db_name="db",
        db_password="****",
        db_password_uri="",
        db_username="user",
        hostname="name",
        instance_number="00",
        provider_type="SapHana",
        sap_sid="SID",
        sql_port="0000",
        ssl_host_name_in_certificate="xyz.domain.com",
        ssl_preference="RootCertificate",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  providerInstance:
    type: azure-native:workloads:ProviderInstance
    properties:
      monitorName: mySapMonitor
      providerInstanceName: myProviderInstance
      providerSettings:
        dbName: db
        dbPassword: '****'
        dbPasswordUri:
        dbUsername: user
        hostname: name
        instanceNumber: '00'
        providerType: SapHana
        sapSid: SID
        sqlPort: '0000'
        sslHostNameInCertificate: xyz.domain.com
        sslPreference: RootCertificate
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a SAP monitor NetWeaver provider
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var providerInstance = new AzureNative.Workloads.ProviderInstance("providerInstance", new()
    {
        MonitorName = "mySapMonitor",
        ProviderInstanceName = "myProviderInstance",
        ProviderSettings = new AzureNative.Workloads.Inputs.SapNetWeaverProviderInstancePropertiesArgs
        {
            ProviderType = "SapNetWeaver",
            SapClientId = "111",
            SapHostFileEntries = new[]
            {
                "127.0.0.1 name fqdn",
            },
            SapHostname = "name",
            SapInstanceNr = "00",
            SapPassword = "****",
            SapPasswordUri = "",
            SapPortNumber = "1234",
            SapSid = "SID",
            SapUsername = "username",
            SslCertificateUri = "https://storageaccount.blob.core.windows.net/containername/filename",
            SslPreference = "ServerCertificate",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewProviderInstance(ctx, "providerInstance", &workloads.ProviderInstanceArgs{
			MonitorName:          pulumi.String("mySapMonitor"),
			ProviderInstanceName: pulumi.String("myProviderInstance"),
			ProviderSettings: workloads.SapNetWeaverProviderInstanceProperties{
				ProviderType: "SapNetWeaver",
				SapClientId:  "111",
				SapHostFileEntries: []string{
					"127.0.0.1 name fqdn",
				},
				SapHostname:       "name",
				SapInstanceNr:     "00",
				SapPassword:       "****",
				SapPasswordUri:    "",
				SapPortNumber:     "1234",
				SapSid:            "SID",
				SapUsername:       "username",
				SslCertificateUri: "https://storageaccount.blob.core.windows.net/containername/filename",
				SslPreference:     "ServerCertificate",
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.workloads.ProviderInstance;
import com.pulumi.azurenative.workloads.ProviderInstanceArgs;
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
        var providerInstance = new ProviderInstance("providerInstance", ProviderInstanceArgs.builder()        
            .monitorName("mySapMonitor")
            .providerInstanceName("myProviderInstance")
            .providerSettings(Map.ofEntries(
                Map.entry("providerType", "SapNetWeaver"),
                Map.entry("sapClientId", "111"),
                Map.entry("sapHostFileEntries", "127.0.0.1 name fqdn"),
                Map.entry("sapHostname", "name"),
                Map.entry("sapInstanceNr", "00"),
                Map.entry("sapPassword", "****"),
                Map.entry("sapPasswordUri", ""),
                Map.entry("sapPortNumber", "1234"),
                Map.entry("sapSid", "SID"),
                Map.entry("sapUsername", "username"),
                Map.entry("sslCertificateUri", "https://storageaccount.blob.core.windows.net/containername/filename"),
                Map.entry("sslPreference", "ServerCertificate")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const providerInstance = new azure_native.workloads.ProviderInstance("providerInstance", {
    monitorName: "mySapMonitor",
    providerInstanceName: "myProviderInstance",
    providerSettings: {
        providerType: "SapNetWeaver",
        sapClientId: "111",
        sapHostFileEntries: ["127.0.0.1 name fqdn"],
        sapHostname: "name",
        sapInstanceNr: "00",
        sapPassword: "****",
        sapPasswordUri: "",
        sapPortNumber: "1234",
        sapSid: "SID",
        sapUsername: "username",
        sslCertificateUri: "https://storageaccount.blob.core.windows.net/containername/filename",
        sslPreference: "ServerCertificate",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provider_instance = azure_native.workloads.ProviderInstance("providerInstance",
    monitor_name="mySapMonitor",
    provider_instance_name="myProviderInstance",
    provider_settings=azure_native.workloads.SapNetWeaverProviderInstancePropertiesArgs(
        provider_type="SapNetWeaver",
        sap_client_id="111",
        sap_host_file_entries=["127.0.0.1 name fqdn"],
        sap_hostname="name",
        sap_instance_nr="00",
        sap_password="****",
        sap_password_uri="",
        sap_port_number="1234",
        sap_sid="SID",
        sap_username="username",
        ssl_certificate_uri="https://storageaccount.blob.core.windows.net/containername/filename",
        ssl_preference="ServerCertificate",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  providerInstance:
    type: azure-native:workloads:ProviderInstance
    properties:
      monitorName: mySapMonitor
      providerInstanceName: myProviderInstance
      providerSettings:
        providerType: SapNetWeaver
        sapClientId: '111'
        sapHostFileEntries:
          - 127.0.0.1 name fqdn
        sapHostname: name
        sapInstanceNr: '00'
        sapPassword: '****'
        sapPasswordUri:
        sapPortNumber: '1234'
        sapSid: SID
        sapUsername: username
        sslCertificateUri: https://storageaccount.blob.core.windows.net/containername/filename
        sslPreference: ServerCertificate
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a SAP monitor NetWeaver provider with Root Certificate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var providerInstance = new AzureNative.Workloads.ProviderInstance("providerInstance", new()
    {
        MonitorName = "mySapMonitor",
        ProviderInstanceName = "myProviderInstance",
        ProviderSettings = new AzureNative.Workloads.Inputs.SapNetWeaverProviderInstancePropertiesArgs
        {
            ProviderType = "SapNetWeaver",
            SapClientId = "111",
            SapHostFileEntries = new[]
            {
                "127.0.0.1 name fqdn",
            },
            SapHostname = "name",
            SapInstanceNr = "00",
            SapPassword = "****",
            SapPasswordUri = "",
            SapPortNumber = "1234",
            SapSid = "SID",
            SapUsername = "username",
            SslPreference = "RootCertificate",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewProviderInstance(ctx, "providerInstance", &workloads.ProviderInstanceArgs{
			MonitorName:          pulumi.String("mySapMonitor"),
			ProviderInstanceName: pulumi.String("myProviderInstance"),
			ProviderSettings: workloads.SapNetWeaverProviderInstanceProperties{
				ProviderType: "SapNetWeaver",
				SapClientId:  "111",
				SapHostFileEntries: []string{
					"127.0.0.1 name fqdn",
				},
				SapHostname:    "name",
				SapInstanceNr:  "00",
				SapPassword:    "****",
				SapPasswordUri: "",
				SapPortNumber:  "1234",
				SapSid:         "SID",
				SapUsername:    "username",
				SslPreference:  "RootCertificate",
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.workloads.ProviderInstance;
import com.pulumi.azurenative.workloads.ProviderInstanceArgs;
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
        var providerInstance = new ProviderInstance("providerInstance", ProviderInstanceArgs.builder()        
            .monitorName("mySapMonitor")
            .providerInstanceName("myProviderInstance")
            .providerSettings(Map.ofEntries(
                Map.entry("providerType", "SapNetWeaver"),
                Map.entry("sapClientId", "111"),
                Map.entry("sapHostFileEntries", "127.0.0.1 name fqdn"),
                Map.entry("sapHostname", "name"),
                Map.entry("sapInstanceNr", "00"),
                Map.entry("sapPassword", "****"),
                Map.entry("sapPasswordUri", ""),
                Map.entry("sapPortNumber", "1234"),
                Map.entry("sapSid", "SID"),
                Map.entry("sapUsername", "username"),
                Map.entry("sslPreference", "RootCertificate")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const providerInstance = new azure_native.workloads.ProviderInstance("providerInstance", {
    monitorName: "mySapMonitor",
    providerInstanceName: "myProviderInstance",
    providerSettings: {
        providerType: "SapNetWeaver",
        sapClientId: "111",
        sapHostFileEntries: ["127.0.0.1 name fqdn"],
        sapHostname: "name",
        sapInstanceNr: "00",
        sapPassword: "****",
        sapPasswordUri: "",
        sapPortNumber: "1234",
        sapSid: "SID",
        sapUsername: "username",
        sslPreference: "RootCertificate",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provider_instance = azure_native.workloads.ProviderInstance("providerInstance",
    monitor_name="mySapMonitor",
    provider_instance_name="myProviderInstance",
    provider_settings=azure_native.workloads.SapNetWeaverProviderInstancePropertiesArgs(
        provider_type="SapNetWeaver",
        sap_client_id="111",
        sap_host_file_entries=["127.0.0.1 name fqdn"],
        sap_hostname="name",
        sap_instance_nr="00",
        sap_password="****",
        sap_password_uri="",
        sap_port_number="1234",
        sap_sid="SID",
        sap_username="username",
        ssl_preference="RootCertificate",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  providerInstance:
    type: azure-native:workloads:ProviderInstance
    properties:
      monitorName: mySapMonitor
      providerInstanceName: myProviderInstance
      providerSettings:
        providerType: SapNetWeaver
        sapClientId: '111'
        sapHostFileEntries:
          - 127.0.0.1 name fqdn
        sapHostname: name
        sapInstanceNr: '00'
        sapPassword: '****'
        sapPasswordUri:
        sapPortNumber: '1234'
        sapSid: SID
        sapUsername: username
        sslPreference: RootCertificate
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:workloads:ProviderInstance myProviderInstance /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Workloads/monitors/mySapMonitor/providerInstances/myProviderInstance 
```
