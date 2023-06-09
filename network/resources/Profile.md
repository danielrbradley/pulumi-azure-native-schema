Class representing a Traffic Manager profile.
API Version: 2018-08-01.
Previous API Version: 2018-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Profile-PUT-MultiValue
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var profile = new AzureNative.Network.Profile("profile", new()
    {
        DnsConfig = new AzureNative.Network.Inputs.DnsConfigArgs
        {
            RelativeName = "azsmnet6386",
            Ttl = 35,
        },
        Location = "global",
        MaxReturn = 2,
        MonitorConfig = new AzureNative.Network.Inputs.MonitorConfigArgs
        {
            Path = "/testpath.aspx",
            Port = 80,
            Protocol = "HTTP",
        },
        ProfileName = "azsmnet6386",
        ProfileStatus = "Enabled",
        ResourceGroupName = "azuresdkfornetautoresttrafficmanager1421",
        TrafficRoutingMethod = "MultiValue",
        TrafficViewEnrollmentStatus = "Disabled",
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
		_, err := network.NewProfile(ctx, "profile", &network.ProfileArgs{
			DnsConfig: &network.DnsConfigArgs{
				RelativeName: pulumi.String("azsmnet6386"),
				Ttl:          pulumi.Float64(35),
			},
			Location:  pulumi.String("global"),
			MaxReturn: pulumi.Float64(2),
			MonitorConfig: &network.MonitorConfigArgs{
				Path:     pulumi.String("/testpath.aspx"),
				Port:     pulumi.Float64(80),
				Protocol: pulumi.String("HTTP"),
			},
			ProfileName:                 pulumi.String("azsmnet6386"),
			ProfileStatus:               pulumi.String("Enabled"),
			ResourceGroupName:           pulumi.String("azuresdkfornetautoresttrafficmanager1421"),
			TrafficRoutingMethod:        pulumi.String("MultiValue"),
			TrafficViewEnrollmentStatus: pulumi.String("Disabled"),
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
import com.pulumi.azurenative.network.Profile;
import com.pulumi.azurenative.network.ProfileArgs;
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
        var profile = new Profile("profile", ProfileArgs.builder()        
            .dnsConfig(Map.ofEntries(
                Map.entry("relativeName", "azsmnet6386"),
                Map.entry("ttl", 35)
            ))
            .location("global")
            .maxReturn(2)
            .monitorConfig(Map.ofEntries(
                Map.entry("path", "/testpath.aspx"),
                Map.entry("port", 80),
                Map.entry("protocol", "HTTP")
            ))
            .profileName("azsmnet6386")
            .profileStatus("Enabled")
            .resourceGroupName("azuresdkfornetautoresttrafficmanager1421")
            .trafficRoutingMethod("MultiValue")
            .trafficViewEnrollmentStatus("Disabled")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const profile = new azure_native.network.Profile("profile", {
    dnsConfig: {
        relativeName: "azsmnet6386",
        ttl: 35,
    },
    location: "global",
    maxReturn: 2,
    monitorConfig: {
        path: "/testpath.aspx",
        port: 80,
        protocol: "HTTP",
    },
    profileName: "azsmnet6386",
    profileStatus: "Enabled",
    resourceGroupName: "azuresdkfornetautoresttrafficmanager1421",
    trafficRoutingMethod: "MultiValue",
    trafficViewEnrollmentStatus: "Disabled",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

profile = azure_native.network.Profile("profile",
    dns_config=azure_native.network.DnsConfigArgs(
        relative_name="azsmnet6386",
        ttl=35,
    ),
    location="global",
    max_return=2,
    monitor_config=azure_native.network.MonitorConfigArgs(
        path="/testpath.aspx",
        port=80,
        protocol="HTTP",
    ),
    profile_name="azsmnet6386",
    profile_status="Enabled",
    resource_group_name="azuresdkfornetautoresttrafficmanager1421",
    traffic_routing_method="MultiValue",
    traffic_view_enrollment_status="Disabled")

```

```yaml
resources:
  profile:
    type: azure-native:network:Profile
    properties:
      dnsConfig:
        relativeName: azsmnet6386
        ttl: 35
      location: global
      maxReturn: 2
      monitorConfig:
        path: /testpath.aspx
        port: 80
        protocol: HTTP
      profileName: azsmnet6386
      profileStatus: Enabled
      resourceGroupName: azuresdkfornetautoresttrafficmanager1421
      trafficRoutingMethod: MultiValue
      trafficViewEnrollmentStatus: Disabled

```

{{% /example %}}
{{% example %}}
### Profile-PUT-NoEndpoints
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var profile = new AzureNative.Network.Profile("profile", new()
    {
        DnsConfig = new AzureNative.Network.Inputs.DnsConfigArgs
        {
            RelativeName = "azsmnet6386",
            Ttl = 35,
        },
        Location = "global",
        MonitorConfig = new AzureNative.Network.Inputs.MonitorConfigArgs
        {
            Path = "/testpath.aspx",
            Port = 80,
            Protocol = "HTTP",
        },
        ProfileName = "azsmnet6386",
        ProfileStatus = "Enabled",
        ResourceGroupName = "azuresdkfornetautoresttrafficmanager1421",
        TrafficRoutingMethod = "Performance",
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
		_, err := network.NewProfile(ctx, "profile", &network.ProfileArgs{
			DnsConfig: &network.DnsConfigArgs{
				RelativeName: pulumi.String("azsmnet6386"),
				Ttl:          pulumi.Float64(35),
			},
			Location: pulumi.String("global"),
			MonitorConfig: &network.MonitorConfigArgs{
				Path:     pulumi.String("/testpath.aspx"),
				Port:     pulumi.Float64(80),
				Protocol: pulumi.String("HTTP"),
			},
			ProfileName:          pulumi.String("azsmnet6386"),
			ProfileStatus:        pulumi.String("Enabled"),
			ResourceGroupName:    pulumi.String("azuresdkfornetautoresttrafficmanager1421"),
			TrafficRoutingMethod: pulumi.String("Performance"),
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
import com.pulumi.azurenative.network.Profile;
import com.pulumi.azurenative.network.ProfileArgs;
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
        var profile = new Profile("profile", ProfileArgs.builder()        
            .dnsConfig(Map.ofEntries(
                Map.entry("relativeName", "azsmnet6386"),
                Map.entry("ttl", 35)
            ))
            .location("global")
            .monitorConfig(Map.ofEntries(
                Map.entry("path", "/testpath.aspx"),
                Map.entry("port", 80),
                Map.entry("protocol", "HTTP")
            ))
            .profileName("azsmnet6386")
            .profileStatus("Enabled")
            .resourceGroupName("azuresdkfornetautoresttrafficmanager1421")
            .trafficRoutingMethod("Performance")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const profile = new azure_native.network.Profile("profile", {
    dnsConfig: {
        relativeName: "azsmnet6386",
        ttl: 35,
    },
    location: "global",
    monitorConfig: {
        path: "/testpath.aspx",
        port: 80,
        protocol: "HTTP",
    },
    profileName: "azsmnet6386",
    profileStatus: "Enabled",
    resourceGroupName: "azuresdkfornetautoresttrafficmanager1421",
    trafficRoutingMethod: "Performance",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

profile = azure_native.network.Profile("profile",
    dns_config=azure_native.network.DnsConfigArgs(
        relative_name="azsmnet6386",
        ttl=35,
    ),
    location="global",
    monitor_config=azure_native.network.MonitorConfigArgs(
        path="/testpath.aspx",
        port=80,
        protocol="HTTP",
    ),
    profile_name="azsmnet6386",
    profile_status="Enabled",
    resource_group_name="azuresdkfornetautoresttrafficmanager1421",
    traffic_routing_method="Performance")

```

```yaml
resources:
  profile:
    type: azure-native:network:Profile
    properties:
      dnsConfig:
        relativeName: azsmnet6386
        ttl: 35
      location: global
      monitorConfig:
        path: /testpath.aspx
        port: 80
        protocol: HTTP
      profileName: azsmnet6386
      profileStatus: Enabled
      resourceGroupName: azuresdkfornetautoresttrafficmanager1421
      trafficRoutingMethod: Performance

```

{{% /example %}}
{{% example %}}
### Profile-PUT-WithAliasing
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var profile = new AzureNative.Network.Profile("profile", new()
    {
        AllowedEndpointRecordTypes = new[]
        {
            "DomainName",
        },
        DnsConfig = new AzureNative.Network.Inputs.DnsConfigArgs
        {
            RelativeName = "azuresdkfornetautoresttrafficmanager6192",
            Ttl = 35,
        },
        Endpoints = new[]
        {
            new AzureNative.Network.Inputs.EndpointArgs
            {
                EndpointLocation = "North Europe",
                EndpointStatus = "Enabled",
                Name = "My external endpoint",
                Target = "foobar.contoso.com",
                Type = "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
            },
        },
        Location = "global",
        MonitorConfig = new AzureNative.Network.Inputs.MonitorConfigArgs
        {
            IntervalInSeconds = 10,
            Path = "/testpath.aspx",
            Port = 80,
            Protocol = "HTTP",
            TimeoutInSeconds = 5,
            ToleratedNumberOfFailures = 2,
        },
        ProfileName = "azuresdkfornetautoresttrafficmanager6192",
        ProfileStatus = "Enabled",
        ResourceGroupName = "azuresdkfornetautoresttrafficmanager2583",
        TrafficRoutingMethod = "Performance",
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
		_, err := network.NewProfile(ctx, "profile", &network.ProfileArgs{
			AllowedEndpointRecordTypes: pulumi.StringArray{
				pulumi.String("DomainName"),
			},
			DnsConfig: &network.DnsConfigArgs{
				RelativeName: pulumi.String("azuresdkfornetautoresttrafficmanager6192"),
				Ttl:          pulumi.Float64(35),
			},
			Endpoints: []network.EndpointTypeArgs{
				{
					EndpointLocation: pulumi.String("North Europe"),
					EndpointStatus:   pulumi.String("Enabled"),
					Name:             pulumi.String("My external endpoint"),
					Target:           pulumi.String("foobar.contoso.com"),
					Type:             pulumi.String("Microsoft.network/TrafficManagerProfiles/ExternalEndpoints"),
				},
			},
			Location: pulumi.String("global"),
			MonitorConfig: &network.MonitorConfigArgs{
				IntervalInSeconds:         pulumi.Float64(10),
				Path:                      pulumi.String("/testpath.aspx"),
				Port:                      pulumi.Float64(80),
				Protocol:                  pulumi.String("HTTP"),
				TimeoutInSeconds:          pulumi.Float64(5),
				ToleratedNumberOfFailures: pulumi.Float64(2),
			},
			ProfileName:          pulumi.String("azuresdkfornetautoresttrafficmanager6192"),
			ProfileStatus:        pulumi.String("Enabled"),
			ResourceGroupName:    pulumi.String("azuresdkfornetautoresttrafficmanager2583"),
			TrafficRoutingMethod: pulumi.String("Performance"),
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
import com.pulumi.azurenative.network.Profile;
import com.pulumi.azurenative.network.ProfileArgs;
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
        var profile = new Profile("profile", ProfileArgs.builder()        
            .allowedEndpointRecordTypes("DomainName")
            .dnsConfig(Map.ofEntries(
                Map.entry("relativeName", "azuresdkfornetautoresttrafficmanager6192"),
                Map.entry("ttl", 35)
            ))
            .endpoints(Map.ofEntries(
                Map.entry("endpointLocation", "North Europe"),
                Map.entry("endpointStatus", "Enabled"),
                Map.entry("name", "My external endpoint"),
                Map.entry("target", "foobar.contoso.com"),
                Map.entry("type", "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints")
            ))
            .location("global")
            .monitorConfig(Map.ofEntries(
                Map.entry("intervalInSeconds", 10),
                Map.entry("path", "/testpath.aspx"),
                Map.entry("port", 80),
                Map.entry("protocol", "HTTP"),
                Map.entry("timeoutInSeconds", 5),
                Map.entry("toleratedNumberOfFailures", 2)
            ))
            .profileName("azuresdkfornetautoresttrafficmanager6192")
            .profileStatus("Enabled")
            .resourceGroupName("azuresdkfornetautoresttrafficmanager2583")
            .trafficRoutingMethod("Performance")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const profile = new azure_native.network.Profile("profile", {
    allowedEndpointRecordTypes: ["DomainName"],
    dnsConfig: {
        relativeName: "azuresdkfornetautoresttrafficmanager6192",
        ttl: 35,
    },
    endpoints: [{
        endpointLocation: "North Europe",
        endpointStatus: "Enabled",
        name: "My external endpoint",
        target: "foobar.contoso.com",
        type: "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
    }],
    location: "global",
    monitorConfig: {
        intervalInSeconds: 10,
        path: "/testpath.aspx",
        port: 80,
        protocol: "HTTP",
        timeoutInSeconds: 5,
        toleratedNumberOfFailures: 2,
    },
    profileName: "azuresdkfornetautoresttrafficmanager6192",
    profileStatus: "Enabled",
    resourceGroupName: "azuresdkfornetautoresttrafficmanager2583",
    trafficRoutingMethod: "Performance",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

profile = azure_native.network.Profile("profile",
    allowed_endpoint_record_types=["DomainName"],
    dns_config=azure_native.network.DnsConfigArgs(
        relative_name="azuresdkfornetautoresttrafficmanager6192",
        ttl=35,
    ),
    endpoints=[azure_native.network.EndpointArgs(
        endpoint_location="North Europe",
        endpoint_status="Enabled",
        name="My external endpoint",
        target="foobar.contoso.com",
        type="Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
    )],
    location="global",
    monitor_config=azure_native.network.MonitorConfigArgs(
        interval_in_seconds=10,
        path="/testpath.aspx",
        port=80,
        protocol="HTTP",
        timeout_in_seconds=5,
        tolerated_number_of_failures=2,
    ),
    profile_name="azuresdkfornetautoresttrafficmanager6192",
    profile_status="Enabled",
    resource_group_name="azuresdkfornetautoresttrafficmanager2583",
    traffic_routing_method="Performance")

```

```yaml
resources:
  profile:
    type: azure-native:network:Profile
    properties:
      allowedEndpointRecordTypes:
        - DomainName
      dnsConfig:
        relativeName: azuresdkfornetautoresttrafficmanager6192
        ttl: 35
      endpoints:
        - endpointLocation: North Europe
          endpointStatus: Enabled
          name: My external endpoint
          target: foobar.contoso.com
          type: Microsoft.network/TrafficManagerProfiles/ExternalEndpoints
      location: global
      monitorConfig:
        intervalInSeconds: 10
        path: /testpath.aspx
        port: 80
        protocol: HTTP
        timeoutInSeconds: 5
        toleratedNumberOfFailures: 2
      profileName: azuresdkfornetautoresttrafficmanager6192
      profileStatus: Enabled
      resourceGroupName: azuresdkfornetautoresttrafficmanager2583
      trafficRoutingMethod: Performance

```

{{% /example %}}
{{% example %}}
### Profile-PUT-WithCustomHeaders
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var profile = new AzureNative.Network.Profile("profile", new()
    {
        DnsConfig = new AzureNative.Network.Inputs.DnsConfigArgs
        {
            RelativeName = "azuresdkfornetautoresttrafficmanager6192",
            Ttl = 35,
        },
        Endpoints = new[]
        {
            new AzureNative.Network.Inputs.EndpointArgs
            {
                CustomHeaders = new[]
                {
                    new AzureNative.Network.Inputs.EndpointPropertiesCustomHeadersArgs
                    {
                        Name = "header-2",
                        Value = "value-2-overridden",
                    },
                },
                EndpointLocation = "North Europe",
                EndpointStatus = "Enabled",
                Name = "My external endpoint",
                Target = "foobar.contoso.com",
                Type = "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
            },
        },
        Location = "global",
        MonitorConfig = new AzureNative.Network.Inputs.MonitorConfigArgs
        {
            CustomHeaders = new[]
            {
                new AzureNative.Network.Inputs.MonitorConfigCustomHeadersArgs
                {
                    Name = "header-1",
                    Value = "value-1",
                },
                new AzureNative.Network.Inputs.MonitorConfigCustomHeadersArgs
                {
                    Name = "header-2",
                    Value = "value-2",
                },
            },
            ExpectedStatusCodeRanges = new[]
            {
                new AzureNative.Network.Inputs.MonitorConfigExpectedStatusCodeRangesArgs
                {
                    Max = 205,
                    Min = 200,
                },
                new AzureNative.Network.Inputs.MonitorConfigExpectedStatusCodeRangesArgs
                {
                    Max = 410,
                    Min = 400,
                },
            },
            IntervalInSeconds = 10,
            Path = "/testpath.aspx",
            Port = 80,
            Protocol = "HTTP",
            TimeoutInSeconds = 5,
            ToleratedNumberOfFailures = 2,
        },
        ProfileName = "azuresdkfornetautoresttrafficmanager6192",
        ProfileStatus = "Enabled",
        ResourceGroupName = "azuresdkfornetautoresttrafficmanager2583",
        TrafficRoutingMethod = "Performance",
        TrafficViewEnrollmentStatus = "Disabled",
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
		_, err := network.NewProfile(ctx, "profile", &network.ProfileArgs{
			DnsConfig: &network.DnsConfigArgs{
				RelativeName: pulumi.String("azuresdkfornetautoresttrafficmanager6192"),
				Ttl:          pulumi.Float64(35),
			},
			Endpoints: []network.EndpointTypeArgs{
				{
					CustomHeaders: network.EndpointPropertiesCustomHeadersArray{
						{
							Name:  pulumi.String("header-2"),
							Value: pulumi.String("value-2-overridden"),
						},
					},
					EndpointLocation: pulumi.String("North Europe"),
					EndpointStatus:   pulumi.String("Enabled"),
					Name:             pulumi.String("My external endpoint"),
					Target:           pulumi.String("foobar.contoso.com"),
					Type:             pulumi.String("Microsoft.network/TrafficManagerProfiles/ExternalEndpoints"),
				},
			},
			Location: pulumi.String("global"),
			MonitorConfig: network.MonitorConfigResponse{
				CustomHeaders: network.MonitorConfigCustomHeadersArray{
					&network.MonitorConfigCustomHeadersArgs{
						Name:  pulumi.String("header-1"),
						Value: pulumi.String("value-1"),
					},
					&network.MonitorConfigCustomHeadersArgs{
						Name:  pulumi.String("header-2"),
						Value: pulumi.String("value-2"),
					},
				},
				ExpectedStatusCodeRanges: network.MonitorConfigExpectedStatusCodeRangesArray{
					&network.MonitorConfigExpectedStatusCodeRangesArgs{
						Max: pulumi.Int(205),
						Min: pulumi.Int(200),
					},
					&network.MonitorConfigExpectedStatusCodeRangesArgs{
						Max: pulumi.Int(410),
						Min: pulumi.Int(400),
					},
				},
				IntervalInSeconds:         pulumi.Float64(10),
				Path:                      pulumi.String("/testpath.aspx"),
				Port:                      pulumi.Float64(80),
				Protocol:                  pulumi.String("HTTP"),
				TimeoutInSeconds:          pulumi.Float64(5),
				ToleratedNumberOfFailures: pulumi.Float64(2),
			},
			ProfileName:                 pulumi.String("azuresdkfornetautoresttrafficmanager6192"),
			ProfileStatus:               pulumi.String("Enabled"),
			ResourceGroupName:           pulumi.String("azuresdkfornetautoresttrafficmanager2583"),
			TrafficRoutingMethod:        pulumi.String("Performance"),
			TrafficViewEnrollmentStatus: pulumi.String("Disabled"),
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
import com.pulumi.azurenative.network.Profile;
import com.pulumi.azurenative.network.ProfileArgs;
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
        var profile = new Profile("profile", ProfileArgs.builder()        
            .dnsConfig(Map.ofEntries(
                Map.entry("relativeName", "azuresdkfornetautoresttrafficmanager6192"),
                Map.entry("ttl", 35)
            ))
            .endpoints(Map.ofEntries(
                Map.entry("customHeaders", Map.ofEntries(
                    Map.entry("name", "header-2"),
                    Map.entry("value", "value-2-overridden")
                )),
                Map.entry("endpointLocation", "North Europe"),
                Map.entry("endpointStatus", "Enabled"),
                Map.entry("name", "My external endpoint"),
                Map.entry("target", "foobar.contoso.com"),
                Map.entry("type", "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints")
            ))
            .location("global")
            .monitorConfig(Map.ofEntries(
                Map.entry("customHeaders",                 
                    Map.ofEntries(
                        Map.entry("name", "header-1"),
                        Map.entry("value", "value-1")
                    ),
                    Map.ofEntries(
                        Map.entry("name", "header-2"),
                        Map.entry("value", "value-2")
                    )),
                Map.entry("expectedStatusCodeRanges",                 
                    Map.ofEntries(
                        Map.entry("max", 205),
                        Map.entry("min", 200)
                    ),
                    Map.ofEntries(
                        Map.entry("max", 410),
                        Map.entry("min", 400)
                    )),
                Map.entry("intervalInSeconds", 10),
                Map.entry("path", "/testpath.aspx"),
                Map.entry("port", 80),
                Map.entry("protocol", "HTTP"),
                Map.entry("timeoutInSeconds", 5),
                Map.entry("toleratedNumberOfFailures", 2)
            ))
            .profileName("azuresdkfornetautoresttrafficmanager6192")
            .profileStatus("Enabled")
            .resourceGroupName("azuresdkfornetautoresttrafficmanager2583")
            .trafficRoutingMethod("Performance")
            .trafficViewEnrollmentStatus("Disabled")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const profile = new azure_native.network.Profile("profile", {
    dnsConfig: {
        relativeName: "azuresdkfornetautoresttrafficmanager6192",
        ttl: 35,
    },
    endpoints: [{
        customHeaders: [{
            name: "header-2",
            value: "value-2-overridden",
        }],
        endpointLocation: "North Europe",
        endpointStatus: "Enabled",
        name: "My external endpoint",
        target: "foobar.contoso.com",
        type: "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
    }],
    location: "global",
    monitorConfig: {
        customHeaders: [
            {
                name: "header-1",
                value: "value-1",
            },
            {
                name: "header-2",
                value: "value-2",
            },
        ],
        expectedStatusCodeRanges: [
            {
                max: 205,
                min: 200,
            },
            {
                max: 410,
                min: 400,
            },
        ],
        intervalInSeconds: 10,
        path: "/testpath.aspx",
        port: 80,
        protocol: "HTTP",
        timeoutInSeconds: 5,
        toleratedNumberOfFailures: 2,
    },
    profileName: "azuresdkfornetautoresttrafficmanager6192",
    profileStatus: "Enabled",
    resourceGroupName: "azuresdkfornetautoresttrafficmanager2583",
    trafficRoutingMethod: "Performance",
    trafficViewEnrollmentStatus: "Disabled",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

profile = azure_native.network.Profile("profile",
    dns_config=azure_native.network.DnsConfigArgs(
        relative_name="azuresdkfornetautoresttrafficmanager6192",
        ttl=35,
    ),
    endpoints=[{
        "customHeaders": [azure_native.network.EndpointPropertiesCustomHeadersArgs(
            name="header-2",
            value="value-2-overridden",
        )],
        "endpointLocation": "North Europe",
        "endpointStatus": "Enabled",
        "name": "My external endpoint",
        "target": "foobar.contoso.com",
        "type": "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
    }],
    location="global",
    monitor_config=azure_native.network.MonitorConfigResponseArgs(
        custom_headers=[
            azure_native.network.MonitorConfigCustomHeadersArgs(
                name="header-1",
                value="value-1",
            ),
            azure_native.network.MonitorConfigCustomHeadersArgs(
                name="header-2",
                value="value-2",
            ),
        ],
        expected_status_code_ranges=[
            azure_native.network.MonitorConfigExpectedStatusCodeRangesArgs(
                max=205,
                min=200,
            ),
            azure_native.network.MonitorConfigExpectedStatusCodeRangesArgs(
                max=410,
                min=400,
            ),
        ],
        interval_in_seconds=10,
        path="/testpath.aspx",
        port=80,
        protocol="HTTP",
        timeout_in_seconds=5,
        tolerated_number_of_failures=2,
    ),
    profile_name="azuresdkfornetautoresttrafficmanager6192",
    profile_status="Enabled",
    resource_group_name="azuresdkfornetautoresttrafficmanager2583",
    traffic_routing_method="Performance",
    traffic_view_enrollment_status="Disabled")

```

```yaml
resources:
  profile:
    type: azure-native:network:Profile
    properties:
      dnsConfig:
        relativeName: azuresdkfornetautoresttrafficmanager6192
        ttl: 35
      endpoints:
        - customHeaders:
            - name: header-2
              value: value-2-overridden
          endpointLocation: North Europe
          endpointStatus: Enabled
          name: My external endpoint
          target: foobar.contoso.com
          type: Microsoft.network/TrafficManagerProfiles/ExternalEndpoints
      location: global
      monitorConfig:
        customHeaders:
          - name: header-1
            value: value-1
          - name: header-2
            value: value-2
        expectedStatusCodeRanges:
          - max: 205
            min: 200
          - max: 410
            min: 400
        intervalInSeconds: 10
        path: /testpath.aspx
        port: 80
        protocol: HTTP
        timeoutInSeconds: 5
        toleratedNumberOfFailures: 2
      profileName: azuresdkfornetautoresttrafficmanager6192
      profileStatus: Enabled
      resourceGroupName: azuresdkfornetautoresttrafficmanager2583
      trafficRoutingMethod: Performance
      trafficViewEnrollmentStatus: Disabled

```

{{% /example %}}
{{% example %}}
### Profile-PUT-WithEndpoints
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var profile = new AzureNative.Network.Profile("profile", new()
    {
        DnsConfig = new AzureNative.Network.Inputs.DnsConfigArgs
        {
            RelativeName = "azuresdkfornetautoresttrafficmanager6192",
            Ttl = 35,
        },
        Endpoints = new[]
        {
            new AzureNative.Network.Inputs.EndpointArgs
            {
                EndpointLocation = "North Europe",
                EndpointStatus = "Enabled",
                Name = "My external endpoint",
                Target = "foobar.contoso.com",
                Type = "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
            },
        },
        Location = "global",
        MonitorConfig = new AzureNative.Network.Inputs.MonitorConfigArgs
        {
            IntervalInSeconds = 10,
            Path = "/testpath.aspx",
            Port = 80,
            Protocol = "HTTP",
            TimeoutInSeconds = 5,
            ToleratedNumberOfFailures = 2,
        },
        ProfileName = "azuresdkfornetautoresttrafficmanager6192",
        ProfileStatus = "Enabled",
        ResourceGroupName = "azuresdkfornetautoresttrafficmanager2583",
        TrafficRoutingMethod = "Performance",
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
		_, err := network.NewProfile(ctx, "profile", &network.ProfileArgs{
			DnsConfig: &network.DnsConfigArgs{
				RelativeName: pulumi.String("azuresdkfornetautoresttrafficmanager6192"),
				Ttl:          pulumi.Float64(35),
			},
			Endpoints: []network.EndpointTypeArgs{
				{
					EndpointLocation: pulumi.String("North Europe"),
					EndpointStatus:   pulumi.String("Enabled"),
					Name:             pulumi.String("My external endpoint"),
					Target:           pulumi.String("foobar.contoso.com"),
					Type:             pulumi.String("Microsoft.network/TrafficManagerProfiles/ExternalEndpoints"),
				},
			},
			Location: pulumi.String("global"),
			MonitorConfig: &network.MonitorConfigArgs{
				IntervalInSeconds:         pulumi.Float64(10),
				Path:                      pulumi.String("/testpath.aspx"),
				Port:                      pulumi.Float64(80),
				Protocol:                  pulumi.String("HTTP"),
				TimeoutInSeconds:          pulumi.Float64(5),
				ToleratedNumberOfFailures: pulumi.Float64(2),
			},
			ProfileName:          pulumi.String("azuresdkfornetautoresttrafficmanager6192"),
			ProfileStatus:        pulumi.String("Enabled"),
			ResourceGroupName:    pulumi.String("azuresdkfornetautoresttrafficmanager2583"),
			TrafficRoutingMethod: pulumi.String("Performance"),
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
import com.pulumi.azurenative.network.Profile;
import com.pulumi.azurenative.network.ProfileArgs;
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
        var profile = new Profile("profile", ProfileArgs.builder()        
            .dnsConfig(Map.ofEntries(
                Map.entry("relativeName", "azuresdkfornetautoresttrafficmanager6192"),
                Map.entry("ttl", 35)
            ))
            .endpoints(Map.ofEntries(
                Map.entry("endpointLocation", "North Europe"),
                Map.entry("endpointStatus", "Enabled"),
                Map.entry("name", "My external endpoint"),
                Map.entry("target", "foobar.contoso.com"),
                Map.entry("type", "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints")
            ))
            .location("global")
            .monitorConfig(Map.ofEntries(
                Map.entry("intervalInSeconds", 10),
                Map.entry("path", "/testpath.aspx"),
                Map.entry("port", 80),
                Map.entry("protocol", "HTTP"),
                Map.entry("timeoutInSeconds", 5),
                Map.entry("toleratedNumberOfFailures", 2)
            ))
            .profileName("azuresdkfornetautoresttrafficmanager6192")
            .profileStatus("Enabled")
            .resourceGroupName("azuresdkfornetautoresttrafficmanager2583")
            .trafficRoutingMethod("Performance")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const profile = new azure_native.network.Profile("profile", {
    dnsConfig: {
        relativeName: "azuresdkfornetautoresttrafficmanager6192",
        ttl: 35,
    },
    endpoints: [{
        endpointLocation: "North Europe",
        endpointStatus: "Enabled",
        name: "My external endpoint",
        target: "foobar.contoso.com",
        type: "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
    }],
    location: "global",
    monitorConfig: {
        intervalInSeconds: 10,
        path: "/testpath.aspx",
        port: 80,
        protocol: "HTTP",
        timeoutInSeconds: 5,
        toleratedNumberOfFailures: 2,
    },
    profileName: "azuresdkfornetautoresttrafficmanager6192",
    profileStatus: "Enabled",
    resourceGroupName: "azuresdkfornetautoresttrafficmanager2583",
    trafficRoutingMethod: "Performance",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

profile = azure_native.network.Profile("profile",
    dns_config=azure_native.network.DnsConfigArgs(
        relative_name="azuresdkfornetautoresttrafficmanager6192",
        ttl=35,
    ),
    endpoints=[azure_native.network.EndpointArgs(
        endpoint_location="North Europe",
        endpoint_status="Enabled",
        name="My external endpoint",
        target="foobar.contoso.com",
        type="Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
    )],
    location="global",
    monitor_config=azure_native.network.MonitorConfigArgs(
        interval_in_seconds=10,
        path="/testpath.aspx",
        port=80,
        protocol="HTTP",
        timeout_in_seconds=5,
        tolerated_number_of_failures=2,
    ),
    profile_name="azuresdkfornetautoresttrafficmanager6192",
    profile_status="Enabled",
    resource_group_name="azuresdkfornetautoresttrafficmanager2583",
    traffic_routing_method="Performance")

```

```yaml
resources:
  profile:
    type: azure-native:network:Profile
    properties:
      dnsConfig:
        relativeName: azuresdkfornetautoresttrafficmanager6192
        ttl: 35
      endpoints:
        - endpointLocation: North Europe
          endpointStatus: Enabled
          name: My external endpoint
          target: foobar.contoso.com
          type: Microsoft.network/TrafficManagerProfiles/ExternalEndpoints
      location: global
      monitorConfig:
        intervalInSeconds: 10
        path: /testpath.aspx
        port: 80
        protocol: HTTP
        timeoutInSeconds: 5
        toleratedNumberOfFailures: 2
      profileName: azuresdkfornetautoresttrafficmanager6192
      profileStatus: Enabled
      resourceGroupName: azuresdkfornetautoresttrafficmanager2583
      trafficRoutingMethod: Performance

```

{{% /example %}}
{{% example %}}
### Profile-PUT-WithNestedEndpoints
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var profile = new AzureNative.Network.Profile("profile", new()
    {
        DnsConfig = new AzureNative.Network.Inputs.DnsConfigArgs
        {
            RelativeName = "parentprofile",
            Ttl = 35,
        },
        Endpoints = new[]
        {
            new AzureNative.Network.Inputs.EndpointArgs
            {
                EndpointStatus = "Enabled",
                MinChildEndpoints = 2,
                MinChildEndpointsIPv4 = 1,
                MinChildEndpointsIPv6 = 2,
                Name = "MyFirstNestedEndpoint",
                Priority = 1,
                Target = "firstnestedprofile.tmpreview.watmtest.azure-test.net",
                Type = "Microsoft.Network/trafficManagerProfiles/nestedEndpoints",
                Weight = 1,
            },
            new AzureNative.Network.Inputs.EndpointArgs
            {
                EndpointStatus = "Enabled",
                MinChildEndpoints = 2,
                MinChildEndpointsIPv4 = 2,
                MinChildEndpointsIPv6 = 1,
                Name = "MySecondNestedEndpoint",
                Priority = 2,
                Target = "secondnestedprofile.tmpreview.watmtest.azure-test.net",
                Type = "Microsoft.Network/trafficManagerProfiles/nestedEndpoints",
                Weight = 1,
            },
        },
        Location = "global",
        MonitorConfig = new AzureNative.Network.Inputs.MonitorConfigArgs
        {
            IntervalInSeconds = 10,
            Path = "/testpath.aspx",
            Port = 80,
            Protocol = "HTTP",
            TimeoutInSeconds = 5,
            ToleratedNumberOfFailures = 2,
        },
        ProfileName = "parentprofile",
        ProfileStatus = "Enabled",
        ResourceGroupName = "myresourcegroup",
        TrafficRoutingMethod = "Priority",
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
		_, err := network.NewProfile(ctx, "profile", &network.ProfileArgs{
			DnsConfig: &network.DnsConfigArgs{
				RelativeName: pulumi.String("parentprofile"),
				Ttl:          pulumi.Float64(35),
			},
			Endpoints: []network.EndpointTypeArgs{
				{
					EndpointStatus:        pulumi.String("Enabled"),
					MinChildEndpoints:     pulumi.Float64(2),
					MinChildEndpointsIPv4: pulumi.Float64(1),
					MinChildEndpointsIPv6: pulumi.Float64(2),
					Name:                  pulumi.String("MyFirstNestedEndpoint"),
					Priority:              pulumi.Float64(1),
					Target:                pulumi.String("firstnestedprofile.tmpreview.watmtest.azure-test.net"),
					Type:                  pulumi.String("Microsoft.Network/trafficManagerProfiles/nestedEndpoints"),
					Weight:                pulumi.Float64(1),
				},
				{
					EndpointStatus:        pulumi.String("Enabled"),
					MinChildEndpoints:     pulumi.Float64(2),
					MinChildEndpointsIPv4: pulumi.Float64(2),
					MinChildEndpointsIPv6: pulumi.Float64(1),
					Name:                  pulumi.String("MySecondNestedEndpoint"),
					Priority:              pulumi.Float64(2),
					Target:                pulumi.String("secondnestedprofile.tmpreview.watmtest.azure-test.net"),
					Type:                  pulumi.String("Microsoft.Network/trafficManagerProfiles/nestedEndpoints"),
					Weight:                pulumi.Float64(1),
				},
			},
			Location: pulumi.String("global"),
			MonitorConfig: &network.MonitorConfigArgs{
				IntervalInSeconds:         pulumi.Float64(10),
				Path:                      pulumi.String("/testpath.aspx"),
				Port:                      pulumi.Float64(80),
				Protocol:                  pulumi.String("HTTP"),
				TimeoutInSeconds:          pulumi.Float64(5),
				ToleratedNumberOfFailures: pulumi.Float64(2),
			},
			ProfileName:          pulumi.String("parentprofile"),
			ProfileStatus:        pulumi.String("Enabled"),
			ResourceGroupName:    pulumi.String("myresourcegroup"),
			TrafficRoutingMethod: pulumi.String("Priority"),
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
import com.pulumi.azurenative.network.Profile;
import com.pulumi.azurenative.network.ProfileArgs;
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
        var profile = new Profile("profile", ProfileArgs.builder()        
            .dnsConfig(Map.ofEntries(
                Map.entry("relativeName", "parentprofile"),
                Map.entry("ttl", 35)
            ))
            .endpoints(            
                Map.ofEntries(
                    Map.entry("endpointStatus", "Enabled"),
                    Map.entry("minChildEndpoints", 2),
                    Map.entry("minChildEndpointsIPv4", 1),
                    Map.entry("minChildEndpointsIPv6", 2),
                    Map.entry("name", "MyFirstNestedEndpoint"),
                    Map.entry("priority", 1),
                    Map.entry("target", "firstnestedprofile.tmpreview.watmtest.azure-test.net"),
                    Map.entry("type", "Microsoft.Network/trafficManagerProfiles/nestedEndpoints"),
                    Map.entry("weight", 1)
                ),
                Map.ofEntries(
                    Map.entry("endpointStatus", "Enabled"),
                    Map.entry("minChildEndpoints", 2),
                    Map.entry("minChildEndpointsIPv4", 2),
                    Map.entry("minChildEndpointsIPv6", 1),
                    Map.entry("name", "MySecondNestedEndpoint"),
                    Map.entry("priority", 2),
                    Map.entry("target", "secondnestedprofile.tmpreview.watmtest.azure-test.net"),
                    Map.entry("type", "Microsoft.Network/trafficManagerProfiles/nestedEndpoints"),
                    Map.entry("weight", 1)
                ))
            .location("global")
            .monitorConfig(Map.ofEntries(
                Map.entry("intervalInSeconds", 10),
                Map.entry("path", "/testpath.aspx"),
                Map.entry("port", 80),
                Map.entry("protocol", "HTTP"),
                Map.entry("timeoutInSeconds", 5),
                Map.entry("toleratedNumberOfFailures", 2)
            ))
            .profileName("parentprofile")
            .profileStatus("Enabled")
            .resourceGroupName("myresourcegroup")
            .trafficRoutingMethod("Priority")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const profile = new azure_native.network.Profile("profile", {
    dnsConfig: {
        relativeName: "parentprofile",
        ttl: 35,
    },
    endpoints: [
        {
            endpointStatus: "Enabled",
            minChildEndpoints: 2,
            minChildEndpointsIPv4: 1,
            minChildEndpointsIPv6: 2,
            name: "MyFirstNestedEndpoint",
            priority: 1,
            target: "firstnestedprofile.tmpreview.watmtest.azure-test.net",
            type: "Microsoft.Network/trafficManagerProfiles/nestedEndpoints",
            weight: 1,
        },
        {
            endpointStatus: "Enabled",
            minChildEndpoints: 2,
            minChildEndpointsIPv4: 2,
            minChildEndpointsIPv6: 1,
            name: "MySecondNestedEndpoint",
            priority: 2,
            target: "secondnestedprofile.tmpreview.watmtest.azure-test.net",
            type: "Microsoft.Network/trafficManagerProfiles/nestedEndpoints",
            weight: 1,
        },
    ],
    location: "global",
    monitorConfig: {
        intervalInSeconds: 10,
        path: "/testpath.aspx",
        port: 80,
        protocol: "HTTP",
        timeoutInSeconds: 5,
        toleratedNumberOfFailures: 2,
    },
    profileName: "parentprofile",
    profileStatus: "Enabled",
    resourceGroupName: "myresourcegroup",
    trafficRoutingMethod: "Priority",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

profile = azure_native.network.Profile("profile",
    dns_config=azure_native.network.DnsConfigArgs(
        relative_name="parentprofile",
        ttl=35,
    ),
    endpoints=[
        azure_native.network.EndpointArgs(
            endpoint_status="Enabled",
            min_child_endpoints=2,
            min_child_endpoints_i_pv4=1,
            min_child_endpoints_i_pv6=2,
            name="MyFirstNestedEndpoint",
            priority=1,
            target="firstnestedprofile.tmpreview.watmtest.azure-test.net",
            type="Microsoft.Network/trafficManagerProfiles/nestedEndpoints",
            weight=1,
        ),
        azure_native.network.EndpointArgs(
            endpoint_status="Enabled",
            min_child_endpoints=2,
            min_child_endpoints_i_pv4=2,
            min_child_endpoints_i_pv6=1,
            name="MySecondNestedEndpoint",
            priority=2,
            target="secondnestedprofile.tmpreview.watmtest.azure-test.net",
            type="Microsoft.Network/trafficManagerProfiles/nestedEndpoints",
            weight=1,
        ),
    ],
    location="global",
    monitor_config=azure_native.network.MonitorConfigArgs(
        interval_in_seconds=10,
        path="/testpath.aspx",
        port=80,
        protocol="HTTP",
        timeout_in_seconds=5,
        tolerated_number_of_failures=2,
    ),
    profile_name="parentprofile",
    profile_status="Enabled",
    resource_group_name="myresourcegroup",
    traffic_routing_method="Priority")

```

```yaml
resources:
  profile:
    type: azure-native:network:Profile
    properties:
      dnsConfig:
        relativeName: parentprofile
        ttl: 35
      endpoints:
        - endpointStatus: Enabled
          minChildEndpoints: 2
          minChildEndpointsIPv4: 1
          minChildEndpointsIPv6: 2
          name: MyFirstNestedEndpoint
          priority: 1
          target: firstnestedprofile.tmpreview.watmtest.azure-test.net
          type: Microsoft.Network/trafficManagerProfiles/nestedEndpoints
          weight: 1
        - endpointStatus: Enabled
          minChildEndpoints: 2
          minChildEndpointsIPv4: 2
          minChildEndpointsIPv6: 1
          name: MySecondNestedEndpoint
          priority: 2
          target: secondnestedprofile.tmpreview.watmtest.azure-test.net
          type: Microsoft.Network/trafficManagerProfiles/nestedEndpoints
          weight: 1
      location: global
      monitorConfig:
        intervalInSeconds: 10
        path: /testpath.aspx
        port: 80
        protocol: HTTP
        timeoutInSeconds: 5
        toleratedNumberOfFailures: 2
      profileName: parentprofile
      profileStatus: Enabled
      resourceGroupName: myresourcegroup
      trafficRoutingMethod: Priority

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:Profile parentprofile /subscriptions/{subscription-id}/resourceGroups/myresourcegroup/providers/Microsoft.Network/trafficManagerProfiles/parentprofile 
```
