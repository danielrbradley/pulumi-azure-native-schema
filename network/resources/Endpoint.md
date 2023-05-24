Class representing a Traffic Manager endpoint.
API Version: 2018-08-01.
Previous API Version: 2018-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Endpoint-PUT-External-WithCustomHeaders
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var endpoint = new AzureNative.Network.Endpoint("endpoint", new()
    {
        CustomHeaders = new[]
        {
            new AzureNative.Network.Inputs.EndpointPropertiesCustomHeadersArgs
            {
                Name = "header-1",
                Value = "value-1",
            },
            new AzureNative.Network.Inputs.EndpointPropertiesCustomHeadersArgs
            {
                Name = "header-2",
                Value = "value-2",
            },
        },
        EndpointLocation = "North Europe",
        EndpointName = "azsmnet7187",
        EndpointStatus = "Enabled",
        EndpointType = "ExternalEndpoints",
        Name = "azsmnet7187",
        ProfileName = "azsmnet6386",
        ResourceGroupName = "azuresdkfornetautoresttrafficmanager1421",
        Target = "foobar.contoso.com",
        Type = "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
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
		_, err := network.NewEndpoint(ctx, "endpoint", &network.EndpointArgs{
			CustomHeaders: []network.EndpointPropertiesCustomHeadersArgs{
				{
					Name:  pulumi.String("header-1"),
					Value: pulumi.String("value-1"),
				},
				{
					Name:  pulumi.String("header-2"),
					Value: pulumi.String("value-2"),
				},
			},
			EndpointLocation:  pulumi.String("North Europe"),
			EndpointName:      pulumi.String("azsmnet7187"),
			EndpointStatus:    pulumi.String("Enabled"),
			EndpointType:      pulumi.String("ExternalEndpoints"),
			Name:              pulumi.String("azsmnet7187"),
			ProfileName:       pulumi.String("azsmnet6386"),
			ResourceGroupName: pulumi.String("azuresdkfornetautoresttrafficmanager1421"),
			Target:            pulumi.String("foobar.contoso.com"),
			Type:              pulumi.String("Microsoft.network/TrafficManagerProfiles/ExternalEndpoints"),
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
import com.pulumi.azurenative.network.Endpoint;
import com.pulumi.azurenative.network.EndpointArgs;
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
        var endpoint = new Endpoint("endpoint", EndpointArgs.builder()        
            .customHeaders(            
                Map.ofEntries(
                    Map.entry("name", "header-1"),
                    Map.entry("value", "value-1")
                ),
                Map.ofEntries(
                    Map.entry("name", "header-2"),
                    Map.entry("value", "value-2")
                ))
            .endpointLocation("North Europe")
            .endpointName("azsmnet7187")
            .endpointStatus("Enabled")
            .endpointType("ExternalEndpoints")
            .name("azsmnet7187")
            .profileName("azsmnet6386")
            .resourceGroupName("azuresdkfornetautoresttrafficmanager1421")
            .target("foobar.contoso.com")
            .type("Microsoft.network/TrafficManagerProfiles/ExternalEndpoints")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const endpoint = new azure_native.network.Endpoint("endpoint", {
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
    endpointLocation: "North Europe",
    endpointName: "azsmnet7187",
    endpointStatus: "Enabled",
    endpointType: "ExternalEndpoints",
    name: "azsmnet7187",
    profileName: "azsmnet6386",
    resourceGroupName: "azuresdkfornetautoresttrafficmanager1421",
    target: "foobar.contoso.com",
    type: "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

endpoint = azure_native.network.Endpoint("endpoint",
    custom_headers=[
        azure_native.network.EndpointPropertiesCustomHeadersArgs(
            name="header-1",
            value="value-1",
        ),
        azure_native.network.EndpointPropertiesCustomHeadersArgs(
            name="header-2",
            value="value-2",
        ),
    ],
    endpoint_location="North Europe",
    endpoint_name="azsmnet7187",
    endpoint_status="Enabled",
    endpoint_type="ExternalEndpoints",
    name="azsmnet7187",
    profile_name="azsmnet6386",
    resource_group_name="azuresdkfornetautoresttrafficmanager1421",
    target="foobar.contoso.com",
    type="Microsoft.network/TrafficManagerProfiles/ExternalEndpoints")

```

```yaml
resources:
  endpoint:
    type: azure-native:network:Endpoint
    properties:
      customHeaders:
        - name: header-1
          value: value-1
        - name: header-2
          value: value-2
      endpointLocation: North Europe
      endpointName: azsmnet7187
      endpointStatus: Enabled
      endpointType: ExternalEndpoints
      name: azsmnet7187
      profileName: azsmnet6386
      resourceGroupName: azuresdkfornetautoresttrafficmanager1421
      target: foobar.contoso.com
      type: Microsoft.network/TrafficManagerProfiles/ExternalEndpoints

```

{{% /example %}}
{{% example %}}
### Endpoint-PUT-External-WithGeoMapping
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var endpoint = new AzureNative.Network.Endpoint("endpoint", new()
    {
        EndpointName = "My%20external%20endpoint",
        EndpointStatus = "Enabled",
        EndpointType = "ExternalEndpoints",
        GeoMapping = new[]
        {
            "GEO-AS",
            "GEO-AF",
        },
        Name = "My external endpoint",
        ProfileName = "azuresdkfornetautoresttrafficmanager8224",
        ResourceGroupName = "azuresdkfornetautoresttrafficmanager2191",
        Target = "foobar.contoso.com",
        Type = "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
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
		_, err := network.NewEndpoint(ctx, "endpoint", &network.EndpointArgs{
			EndpointName:   pulumi.String("My%20external%20endpoint"),
			EndpointStatus: pulumi.String("Enabled"),
			EndpointType:   pulumi.String("ExternalEndpoints"),
			GeoMapping: pulumi.StringArray{
				pulumi.String("GEO-AS"),
				pulumi.String("GEO-AF"),
			},
			Name:              pulumi.String("My external endpoint"),
			ProfileName:       pulumi.String("azuresdkfornetautoresttrafficmanager8224"),
			ResourceGroupName: pulumi.String("azuresdkfornetautoresttrafficmanager2191"),
			Target:            pulumi.String("foobar.contoso.com"),
			Type:              pulumi.String("Microsoft.network/TrafficManagerProfiles/ExternalEndpoints"),
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
import com.pulumi.azurenative.network.Endpoint;
import com.pulumi.azurenative.network.EndpointArgs;
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
        var endpoint = new Endpoint("endpoint", EndpointArgs.builder()        
            .endpointName("My%20external%20endpoint")
            .endpointStatus("Enabled")
            .endpointType("ExternalEndpoints")
            .geoMapping(            
                "GEO-AS",
                "GEO-AF")
            .name("My external endpoint")
            .profileName("azuresdkfornetautoresttrafficmanager8224")
            .resourceGroupName("azuresdkfornetautoresttrafficmanager2191")
            .target("foobar.contoso.com")
            .type("Microsoft.network/TrafficManagerProfiles/ExternalEndpoints")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const endpoint = new azure_native.network.Endpoint("endpoint", {
    endpointName: "My%20external%20endpoint",
    endpointStatus: "Enabled",
    endpointType: "ExternalEndpoints",
    geoMapping: [
        "GEO-AS",
        "GEO-AF",
    ],
    name: "My external endpoint",
    profileName: "azuresdkfornetautoresttrafficmanager8224",
    resourceGroupName: "azuresdkfornetautoresttrafficmanager2191",
    target: "foobar.contoso.com",
    type: "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

endpoint = azure_native.network.Endpoint("endpoint",
    endpoint_name="My%20external%20endpoint",
    endpoint_status="Enabled",
    endpoint_type="ExternalEndpoints",
    geo_mapping=[
        "GEO-AS",
        "GEO-AF",
    ],
    name="My external endpoint",
    profile_name="azuresdkfornetautoresttrafficmanager8224",
    resource_group_name="azuresdkfornetautoresttrafficmanager2191",
    target="foobar.contoso.com",
    type="Microsoft.network/TrafficManagerProfiles/ExternalEndpoints")

```

```yaml
resources:
  endpoint:
    type: azure-native:network:Endpoint
    properties:
      endpointName: My%20external%20endpoint
      endpointStatus: Enabled
      endpointType: ExternalEndpoints
      geoMapping:
        - GEO-AS
        - GEO-AF
      name: My external endpoint
      profileName: azuresdkfornetautoresttrafficmanager8224
      resourceGroupName: azuresdkfornetautoresttrafficmanager2191
      target: foobar.contoso.com
      type: Microsoft.network/TrafficManagerProfiles/ExternalEndpoints

```

{{% /example %}}
{{% example %}}
### Endpoint-PUT-External-WithLocation
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var endpoint = new AzureNative.Network.Endpoint("endpoint", new()
    {
        EndpointLocation = "North Europe",
        EndpointName = "azsmnet7187",
        EndpointStatus = "Enabled",
        EndpointType = "ExternalEndpoints",
        Name = "azsmnet7187",
        ProfileName = "azsmnet6386",
        ResourceGroupName = "azuresdkfornetautoresttrafficmanager1421",
        Target = "foobar.contoso.com",
        Type = "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
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
		_, err := network.NewEndpoint(ctx, "endpoint", &network.EndpointArgs{
			EndpointLocation:  pulumi.String("North Europe"),
			EndpointName:      pulumi.String("azsmnet7187"),
			EndpointStatus:    pulumi.String("Enabled"),
			EndpointType:      pulumi.String("ExternalEndpoints"),
			Name:              pulumi.String("azsmnet7187"),
			ProfileName:       pulumi.String("azsmnet6386"),
			ResourceGroupName: pulumi.String("azuresdkfornetautoresttrafficmanager1421"),
			Target:            pulumi.String("foobar.contoso.com"),
			Type:              pulumi.String("Microsoft.network/TrafficManagerProfiles/ExternalEndpoints"),
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
import com.pulumi.azurenative.network.Endpoint;
import com.pulumi.azurenative.network.EndpointArgs;
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
        var endpoint = new Endpoint("endpoint", EndpointArgs.builder()        
            .endpointLocation("North Europe")
            .endpointName("azsmnet7187")
            .endpointStatus("Enabled")
            .endpointType("ExternalEndpoints")
            .name("azsmnet7187")
            .profileName("azsmnet6386")
            .resourceGroupName("azuresdkfornetautoresttrafficmanager1421")
            .target("foobar.contoso.com")
            .type("Microsoft.network/TrafficManagerProfiles/ExternalEndpoints")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const endpoint = new azure_native.network.Endpoint("endpoint", {
    endpointLocation: "North Europe",
    endpointName: "azsmnet7187",
    endpointStatus: "Enabled",
    endpointType: "ExternalEndpoints",
    name: "azsmnet7187",
    profileName: "azsmnet6386",
    resourceGroupName: "azuresdkfornetautoresttrafficmanager1421",
    target: "foobar.contoso.com",
    type: "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

endpoint = azure_native.network.Endpoint("endpoint",
    endpoint_location="North Europe",
    endpoint_name="azsmnet7187",
    endpoint_status="Enabled",
    endpoint_type="ExternalEndpoints",
    name="azsmnet7187",
    profile_name="azsmnet6386",
    resource_group_name="azuresdkfornetautoresttrafficmanager1421",
    target="foobar.contoso.com",
    type="Microsoft.network/TrafficManagerProfiles/ExternalEndpoints")

```

```yaml
resources:
  endpoint:
    type: azure-native:network:Endpoint
    properties:
      endpointLocation: North Europe
      endpointName: azsmnet7187
      endpointStatus: Enabled
      endpointType: ExternalEndpoints
      name: azsmnet7187
      profileName: azsmnet6386
      resourceGroupName: azuresdkfornetautoresttrafficmanager1421
      target: foobar.contoso.com
      type: Microsoft.network/TrafficManagerProfiles/ExternalEndpoints

```

{{% /example %}}
{{% example %}}
### Endpoint-PUT-External-WithSubnetMapping
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var endpoint = new AzureNative.Network.Endpoint("endpoint", new()
    {
        EndpointName = "My%20external%20endpoint",
        EndpointStatus = "Enabled",
        EndpointType = "ExternalEndpoints",
        Name = "My external endpoint",
        ProfileName = "azuresdkfornetautoresttrafficmanager8224",
        ResourceGroupName = "azuresdkfornetautoresttrafficmanager2191",
        Subnets = new[]
        {
            new AzureNative.Network.Inputs.EndpointPropertiesSubnetsArgs
            {
                First = "1.2.3.0",
                Scope = 24,
            },
            new AzureNative.Network.Inputs.EndpointPropertiesSubnetsArgs
            {
                First = "25.26.27.28",
                Last = "29.30.31.32",
            },
        },
        Target = "foobar.contoso.com",
        Type = "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
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
		_, err := network.NewEndpoint(ctx, "endpoint", &network.EndpointArgs{
			EndpointName:      pulumi.String("My%20external%20endpoint"),
			EndpointStatus:    pulumi.String("Enabled"),
			EndpointType:      pulumi.String("ExternalEndpoints"),
			Name:              pulumi.String("My external endpoint"),
			ProfileName:       pulumi.String("azuresdkfornetautoresttrafficmanager8224"),
			ResourceGroupName: pulumi.String("azuresdkfornetautoresttrafficmanager2191"),
			Subnets: []network.EndpointPropertiesSubnetsArgs{
				{
					First: pulumi.String("1.2.3.0"),
					Scope: pulumi.Int(24),
				},
				{
					First: pulumi.String("25.26.27.28"),
					Last:  pulumi.String("29.30.31.32"),
				},
			},
			Target: pulumi.String("foobar.contoso.com"),
			Type:   pulumi.String("Microsoft.network/TrafficManagerProfiles/ExternalEndpoints"),
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
import com.pulumi.azurenative.network.Endpoint;
import com.pulumi.azurenative.network.EndpointArgs;
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
        var endpoint = new Endpoint("endpoint", EndpointArgs.builder()        
            .endpointName("My%20external%20endpoint")
            .endpointStatus("Enabled")
            .endpointType("ExternalEndpoints")
            .name("My external endpoint")
            .profileName("azuresdkfornetautoresttrafficmanager8224")
            .resourceGroupName("azuresdkfornetautoresttrafficmanager2191")
            .subnets(            
                Map.ofEntries(
                    Map.entry("first", "1.2.3.0"),
                    Map.entry("scope", 24)
                ),
                Map.ofEntries(
                    Map.entry("first", "25.26.27.28"),
                    Map.entry("last", "29.30.31.32")
                ))
            .target("foobar.contoso.com")
            .type("Microsoft.network/TrafficManagerProfiles/ExternalEndpoints")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const endpoint = new azure_native.network.Endpoint("endpoint", {
    endpointName: "My%20external%20endpoint",
    endpointStatus: "Enabled",
    endpointType: "ExternalEndpoints",
    name: "My external endpoint",
    profileName: "azuresdkfornetautoresttrafficmanager8224",
    resourceGroupName: "azuresdkfornetautoresttrafficmanager2191",
    subnets: [
        {
            first: "1.2.3.0",
            scope: 24,
        },
        {
            first: "25.26.27.28",
            last: "29.30.31.32",
        },
    ],
    target: "foobar.contoso.com",
    type: "Microsoft.network/TrafficManagerProfiles/ExternalEndpoints",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

endpoint = azure_native.network.Endpoint("endpoint",
    endpoint_name="My%20external%20endpoint",
    endpoint_status="Enabled",
    endpoint_type="ExternalEndpoints",
    name="My external endpoint",
    profile_name="azuresdkfornetautoresttrafficmanager8224",
    resource_group_name="azuresdkfornetautoresttrafficmanager2191",
    subnets=[
        azure_native.network.EndpointPropertiesSubnetsArgs(
            first="1.2.3.0",
            scope=24,
        ),
        azure_native.network.EndpointPropertiesSubnetsArgs(
            first="25.26.27.28",
            last="29.30.31.32",
        ),
    ],
    target="foobar.contoso.com",
    type="Microsoft.network/TrafficManagerProfiles/ExternalEndpoints")

```

```yaml
resources:
  endpoint:
    type: azure-native:network:Endpoint
    properties:
      endpointName: My%20external%20endpoint
      endpointStatus: Enabled
      endpointType: ExternalEndpoints
      name: My external endpoint
      profileName: azuresdkfornetautoresttrafficmanager8224
      resourceGroupName: azuresdkfornetautoresttrafficmanager2191
      subnets:
        - first: 1.2.3.0
          scope: 24
        - first: 25.26.27.28
          last: 29.30.31.32
      target: foobar.contoso.com
      type: Microsoft.network/TrafficManagerProfiles/ExternalEndpoints

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:Endpoint My external endpoint /subscriptions/{subscription-id}/resourceGroups/azuresdkfornetautoresttrafficmanager2191/providers/Microsoft.Network/trafficManagerProfiles/azuresdkfornetautoresttrafficmanager8224/externalEndpoints/My external endpoint 
```
