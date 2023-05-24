A single API Management service resource in List or Get response.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateMultiRegionServiceWithCustomHostname
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiManagementService = new AzureNative.ApiManagement.ApiManagementService("apiManagementService", new()
    {
        AdditionalLocations = new[]
        {
            new AzureNative.ApiManagement.Inputs.AdditionalLocationArgs
            {
                DisableGateway = true,
                Location = "East US",
                Sku = new AzureNative.ApiManagement.Inputs.ApiManagementServiceSkuPropertiesArgs
                {
                    Capacity = 1,
                    Name = "Premium",
                },
            },
        },
        ApiVersionConstraint = new AzureNative.ApiManagement.Inputs.ApiVersionConstraintArgs
        {
            MinApiVersion = "2019-01-01",
        },
        HostnameConfigurations = new[]
        {
            new AzureNative.ApiManagement.Inputs.HostnameConfigurationArgs
            {
                CertificatePassword = "Password",
                DefaultSslBinding = true,
                EncodedCertificate = "****** Base 64 Encoded Certificate ************",
                HostName = "gateway1.msitesting.net",
                Type = "Proxy",
            },
            new AzureNative.ApiManagement.Inputs.HostnameConfigurationArgs
            {
                CertificatePassword = "Password",
                EncodedCertificate = "****** Base 64 Encoded Certificate ************",
                HostName = "mgmt.msitesting.net",
                Type = "Management",
            },
            new AzureNative.ApiManagement.Inputs.HostnameConfigurationArgs
            {
                CertificatePassword = "Password",
                EncodedCertificate = "****** Base 64 Encoded Certificate ************",
                HostName = "portal1.msitesting.net",
                Type = "Portal",
            },
        },
        Location = "West US",
        PublisherEmail = "apim@autorestsdk.com",
        PublisherName = "autorestsdk",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Sku = new AzureNative.ApiManagement.Inputs.ApiManagementServiceSkuPropertiesArgs
        {
            Capacity = 1,
            Name = "Premium",
        },
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
            { "tag3", "value3" },
        },
        VirtualNetworkType = "None",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewApiManagementService(ctx, "apiManagementService", &apimanagement.ApiManagementServiceArgs{
			AdditionalLocations: []apimanagement.AdditionalLocationArgs{
				{
					DisableGateway: pulumi.Bool(true),
					Location:       pulumi.String("East US"),
					Sku: {
						Capacity: pulumi.Int(1),
						Name:     pulumi.String("Premium"),
					},
				},
			},
			ApiVersionConstraint: &apimanagement.ApiVersionConstraintArgs{
				MinApiVersion: pulumi.String("2019-01-01"),
			},
			HostnameConfigurations: []apimanagement.HostnameConfigurationArgs{
				{
					CertificatePassword: pulumi.String("Password"),
					DefaultSslBinding:   pulumi.Bool(true),
					EncodedCertificate:  pulumi.String("****** Base 64 Encoded Certificate ************"),
					HostName:            pulumi.String("gateway1.msitesting.net"),
					Type:                pulumi.String("Proxy"),
				},
				{
					CertificatePassword: pulumi.String("Password"),
					EncodedCertificate:  pulumi.String("****** Base 64 Encoded Certificate ************"),
					HostName:            pulumi.String("mgmt.msitesting.net"),
					Type:                pulumi.String("Management"),
				},
				{
					CertificatePassword: pulumi.String("Password"),
					EncodedCertificate:  pulumi.String("****** Base 64 Encoded Certificate ************"),
					HostName:            pulumi.String("portal1.msitesting.net"),
					Type:                pulumi.String("Portal"),
				},
			},
			Location:          pulumi.String("West US"),
			PublisherEmail:    pulumi.String("apim@autorestsdk.com"),
			PublisherName:     pulumi.String("autorestsdk"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Sku: &apimanagement.ApiManagementServiceSkuPropertiesArgs{
				Capacity: pulumi.Int(1),
				Name:     pulumi.String("Premium"),
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
				"tag3": pulumi.String("value3"),
			},
			VirtualNetworkType: pulumi.String("None"),
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
import com.pulumi.azurenative.apimanagement.ApiManagementService;
import com.pulumi.azurenative.apimanagement.ApiManagementServiceArgs;
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
        var apiManagementService = new ApiManagementService("apiManagementService", ApiManagementServiceArgs.builder()        
            .additionalLocations(Map.ofEntries(
                Map.entry("disableGateway", true),
                Map.entry("location", "East US"),
                Map.entry("sku", Map.ofEntries(
                    Map.entry("capacity", 1),
                    Map.entry("name", "Premium")
                ))
            ))
            .apiVersionConstraint(Map.of("minApiVersion", "2019-01-01"))
            .hostnameConfigurations(            
                Map.ofEntries(
                    Map.entry("certificatePassword", "Password"),
                    Map.entry("defaultSslBinding", true),
                    Map.entry("encodedCertificate", "****** Base 64 Encoded Certificate ************"),
                    Map.entry("hostName", "gateway1.msitesting.net"),
                    Map.entry("type", "Proxy")
                ),
                Map.ofEntries(
                    Map.entry("certificatePassword", "Password"),
                    Map.entry("encodedCertificate", "****** Base 64 Encoded Certificate ************"),
                    Map.entry("hostName", "mgmt.msitesting.net"),
                    Map.entry("type", "Management")
                ),
                Map.ofEntries(
                    Map.entry("certificatePassword", "Password"),
                    Map.entry("encodedCertificate", "****** Base 64 Encoded Certificate ************"),
                    Map.entry("hostName", "portal1.msitesting.net"),
                    Map.entry("type", "Portal")
                ))
            .location("West US")
            .publisherEmail("apim@autorestsdk.com")
            .publisherName("autorestsdk")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("name", "Premium")
            ))
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2"),
                Map.entry("tag3", "value3")
            ))
            .virtualNetworkType("None")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiManagementService = new azure_native.apimanagement.ApiManagementService("apiManagementService", {
    additionalLocations: [{
        disableGateway: true,
        location: "East US",
        sku: {
            capacity: 1,
            name: "Premium",
        },
    }],
    apiVersionConstraint: {
        minApiVersion: "2019-01-01",
    },
    hostnameConfigurations: [
        {
            certificatePassword: "Password",
            defaultSslBinding: true,
            encodedCertificate: "****** Base 64 Encoded Certificate ************",
            hostName: "gateway1.msitesting.net",
            type: "Proxy",
        },
        {
            certificatePassword: "Password",
            encodedCertificate: "****** Base 64 Encoded Certificate ************",
            hostName: "mgmt.msitesting.net",
            type: "Management",
        },
        {
            certificatePassword: "Password",
            encodedCertificate: "****** Base 64 Encoded Certificate ************",
            hostName: "portal1.msitesting.net",
            type: "Portal",
        },
    ],
    location: "West US",
    publisherEmail: "apim@autorestsdk.com",
    publisherName: "autorestsdk",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    sku: {
        capacity: 1,
        name: "Premium",
    },
    tags: {
        tag1: "value1",
        tag2: "value2",
        tag3: "value3",
    },
    virtualNetworkType: "None",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_management_service = azure_native.apimanagement.ApiManagementService("apiManagementService",
    additional_locations=[{
        "disableGateway": True,
        "location": "East US",
        "sku": azure_native.apimanagement.ApiManagementServiceSkuPropertiesArgs(
            capacity=1,
            name="Premium",
        ),
    }],
    api_version_constraint=azure_native.apimanagement.ApiVersionConstraintArgs(
        min_api_version="2019-01-01",
    ),
    hostname_configurations=[
        azure_native.apimanagement.HostnameConfigurationArgs(
            certificate_password="Password",
            default_ssl_binding=True,
            encoded_certificate="****** Base 64 Encoded Certificate ************",
            host_name="gateway1.msitesting.net",
            type="Proxy",
        ),
        azure_native.apimanagement.HostnameConfigurationArgs(
            certificate_password="Password",
            encoded_certificate="****** Base 64 Encoded Certificate ************",
            host_name="mgmt.msitesting.net",
            type="Management",
        ),
        azure_native.apimanagement.HostnameConfigurationArgs(
            certificate_password="Password",
            encoded_certificate="****** Base 64 Encoded Certificate ************",
            host_name="portal1.msitesting.net",
            type="Portal",
        ),
    ],
    location="West US",
    publisher_email="apim@autorestsdk.com",
    publisher_name="autorestsdk",
    resource_group_name="rg1",
    service_name="apimService1",
    sku=azure_native.apimanagement.ApiManagementServiceSkuPropertiesArgs(
        capacity=1,
        name="Premium",
    ),
    tags={
        "tag1": "value1",
        "tag2": "value2",
        "tag3": "value3",
    },
    virtual_network_type="None")

```

```yaml
resources:
  apiManagementService:
    type: azure-native:apimanagement:ApiManagementService
    properties:
      additionalLocations:
        - disableGateway: true
          location: East US
          sku:
            capacity: 1
            name: Premium
      apiVersionConstraint:
        minApiVersion: 2019-01-01
      hostnameConfigurations:
        - certificatePassword: Password
          defaultSslBinding: true
          encodedCertificate: '****** Base 64 Encoded Certificate ************'
          hostName: gateway1.msitesting.net
          type: Proxy
        - certificatePassword: Password
          encodedCertificate: '****** Base 64 Encoded Certificate ************'
          hostName: mgmt.msitesting.net
          type: Management
        - certificatePassword: Password
          encodedCertificate: '****** Base 64 Encoded Certificate ************'
          hostName: portal1.msitesting.net
          type: Portal
      location: West US
      publisherEmail: apim@autorestsdk.com
      publisherName: autorestsdk
      resourceGroupName: rg1
      serviceName: apimService1
      sku:
        capacity: 1
        name: Premium
      tags:
        tag1: value1
        tag2: value2
        tag3: value3
      virtualNetworkType: None

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateService
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiManagementService = new AzureNative.ApiManagement.ApiManagementService("apiManagementService", new()
    {
        Location = "South Central US",
        PublisherEmail = "foo@contoso.com",
        PublisherName = "foo",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Sku = new AzureNative.ApiManagement.Inputs.ApiManagementServiceSkuPropertiesArgs
        {
            Capacity = 1,
            Name = "Developer",
        },
        Tags = 
        {
            { "Name", "Contoso" },
            { "Test", "User" },
        },
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewApiManagementService(ctx, "apiManagementService", &apimanagement.ApiManagementServiceArgs{
			Location:          pulumi.String("South Central US"),
			PublisherEmail:    pulumi.String("foo@contoso.com"),
			PublisherName:     pulumi.String("foo"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Sku: &apimanagement.ApiManagementServiceSkuPropertiesArgs{
				Capacity: pulumi.Int(1),
				Name:     pulumi.String("Developer"),
			},
			Tags: pulumi.StringMap{
				"Name": pulumi.String("Contoso"),
				"Test": pulumi.String("User"),
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
import com.pulumi.azurenative.apimanagement.ApiManagementService;
import com.pulumi.azurenative.apimanagement.ApiManagementServiceArgs;
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
        var apiManagementService = new ApiManagementService("apiManagementService", ApiManagementServiceArgs.builder()        
            .location("South Central US")
            .publisherEmail("foo@contoso.com")
            .publisherName("foo")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("name", "Developer")
            ))
            .tags(Map.ofEntries(
                Map.entry("Name", "Contoso"),
                Map.entry("Test", "User")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiManagementService = new azure_native.apimanagement.ApiManagementService("apiManagementService", {
    location: "South Central US",
    publisherEmail: "foo@contoso.com",
    publisherName: "foo",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    sku: {
        capacity: 1,
        name: "Developer",
    },
    tags: {
        Name: "Contoso",
        Test: "User",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_management_service = azure_native.apimanagement.ApiManagementService("apiManagementService",
    location="South Central US",
    publisher_email="foo@contoso.com",
    publisher_name="foo",
    resource_group_name="rg1",
    service_name="apimService1",
    sku=azure_native.apimanagement.ApiManagementServiceSkuPropertiesArgs(
        capacity=1,
        name="Developer",
    ),
    tags={
        "Name": "Contoso",
        "Test": "User",
    })

```

```yaml
resources:
  apiManagementService:
    type: azure-native:apimanagement:ApiManagementService
    properties:
      location: South Central US
      publisherEmail: foo@contoso.com
      publisherName: foo
      resourceGroupName: rg1
      serviceName: apimService1
      sku:
        capacity: 1
        name: Developer
      tags:
        Name: Contoso
        Test: User

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateServiceHavingMsi
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiManagementService = new AzureNative.ApiManagement.ApiManagementService("apiManagementService", new()
    {
        Identity = new AzureNative.ApiManagement.Inputs.ApiManagementServiceIdentityArgs
        {
            Type = "SystemAssigned",
        },
        Location = "West US",
        PublisherEmail = "apim@autorestsdk.com",
        PublisherName = "autorestsdk",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Sku = new AzureNative.ApiManagement.Inputs.ApiManagementServiceSkuPropertiesArgs
        {
            Capacity = 0,
            Name = "Consumption",
        },
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
            { "tag3", "value3" },
        },
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewApiManagementService(ctx, "apiManagementService", &apimanagement.ApiManagementServiceArgs{
			Identity: &apimanagement.ApiManagementServiceIdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			Location:          pulumi.String("West US"),
			PublisherEmail:    pulumi.String("apim@autorestsdk.com"),
			PublisherName:     pulumi.String("autorestsdk"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Sku: &apimanagement.ApiManagementServiceSkuPropertiesArgs{
				Capacity: pulumi.Int(0),
				Name:     pulumi.String("Consumption"),
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
				"tag3": pulumi.String("value3"),
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
import com.pulumi.azurenative.apimanagement.ApiManagementService;
import com.pulumi.azurenative.apimanagement.ApiManagementServiceArgs;
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
        var apiManagementService = new ApiManagementService("apiManagementService", ApiManagementServiceArgs.builder()        
            .identity(Map.of("type", "SystemAssigned"))
            .location("West US")
            .publisherEmail("apim@autorestsdk.com")
            .publisherName("autorestsdk")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .sku(Map.ofEntries(
                Map.entry("capacity", 0),
                Map.entry("name", "Consumption")
            ))
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2"),
                Map.entry("tag3", "value3")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiManagementService = new azure_native.apimanagement.ApiManagementService("apiManagementService", {
    identity: {
        type: "SystemAssigned",
    },
    location: "West US",
    publisherEmail: "apim@autorestsdk.com",
    publisherName: "autorestsdk",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    sku: {
        capacity: 0,
        name: "Consumption",
    },
    tags: {
        tag1: "value1",
        tag2: "value2",
        tag3: "value3",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_management_service = azure_native.apimanagement.ApiManagementService("apiManagementService",
    identity=azure_native.apimanagement.ApiManagementServiceIdentityArgs(
        type="SystemAssigned",
    ),
    location="West US",
    publisher_email="apim@autorestsdk.com",
    publisher_name="autorestsdk",
    resource_group_name="rg1",
    service_name="apimService1",
    sku=azure_native.apimanagement.ApiManagementServiceSkuPropertiesArgs(
        capacity=0,
        name="Consumption",
    ),
    tags={
        "tag1": "value1",
        "tag2": "value2",
        "tag3": "value3",
    })

```

```yaml
resources:
  apiManagementService:
    type: azure-native:apimanagement:ApiManagementService
    properties:
      identity:
        type: SystemAssigned
      location: West US
      publisherEmail: apim@autorestsdk.com
      publisherName: autorestsdk
      resourceGroupName: rg1
      serviceName: apimService1
      sku:
        capacity: 0
        name: Consumption
      tags:
        tag1: value1
        tag2: value2
        tag3: value3

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateServiceInVnetWithPublicIP
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiManagementService = new AzureNative.ApiManagement.ApiManagementService("apiManagementService", new()
    {
        Location = "East US 2 EUAP",
        PublicIpAddressId = "/subscriptions/subid/resourceGroups/rgName/providers/Microsoft.Network/publicIPAddresses/apimazvnet",
        PublisherEmail = "apim@autorestsdk.com",
        PublisherName = "autorestsdk",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Sku = new AzureNative.ApiManagement.Inputs.ApiManagementServiceSkuPropertiesArgs
        {
            Capacity = 2,
            Name = "Premium",
        },
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
            { "tag3", "value3" },
        },
        VirtualNetworkConfiguration = new AzureNative.ApiManagement.Inputs.VirtualNetworkConfigurationArgs
        {
            SubnetResourceId = "/subscriptions/subid/resourceGroups/rgName/providers/Microsoft.Network/virtualNetworks/apimcus/subnets/tenant",
        },
        VirtualNetworkType = "External",
        Zones = new[]
        {
            "1",
            "2",
        },
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewApiManagementService(ctx, "apiManagementService", &apimanagement.ApiManagementServiceArgs{
			Location:          pulumi.String("East US 2 EUAP"),
			PublicIpAddressId: pulumi.String("/subscriptions/subid/resourceGroups/rgName/providers/Microsoft.Network/publicIPAddresses/apimazvnet"),
			PublisherEmail:    pulumi.String("apim@autorestsdk.com"),
			PublisherName:     pulumi.String("autorestsdk"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Sku: &apimanagement.ApiManagementServiceSkuPropertiesArgs{
				Capacity: pulumi.Int(2),
				Name:     pulumi.String("Premium"),
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
				"tag3": pulumi.String("value3"),
			},
			VirtualNetworkConfiguration: &apimanagement.VirtualNetworkConfigurationArgs{
				SubnetResourceId: pulumi.String("/subscriptions/subid/resourceGroups/rgName/providers/Microsoft.Network/virtualNetworks/apimcus/subnets/tenant"),
			},
			VirtualNetworkType: pulumi.String("External"),
			Zones: pulumi.StringArray{
				pulumi.String("1"),
				pulumi.String("2"),
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
import com.pulumi.azurenative.apimanagement.ApiManagementService;
import com.pulumi.azurenative.apimanagement.ApiManagementServiceArgs;
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
        var apiManagementService = new ApiManagementService("apiManagementService", ApiManagementServiceArgs.builder()        
            .location("East US 2 EUAP")
            .publicIpAddressId("/subscriptions/subid/resourceGroups/rgName/providers/Microsoft.Network/publicIPAddresses/apimazvnet")
            .publisherEmail("apim@autorestsdk.com")
            .publisherName("autorestsdk")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("name", "Premium")
            ))
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2"),
                Map.entry("tag3", "value3")
            ))
            .virtualNetworkConfiguration(Map.of("subnetResourceId", "/subscriptions/subid/resourceGroups/rgName/providers/Microsoft.Network/virtualNetworks/apimcus/subnets/tenant"))
            .virtualNetworkType("External")
            .zones(            
                "1",
                "2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiManagementService = new azure_native.apimanagement.ApiManagementService("apiManagementService", {
    location: "East US 2 EUAP",
    publicIpAddressId: "/subscriptions/subid/resourceGroups/rgName/providers/Microsoft.Network/publicIPAddresses/apimazvnet",
    publisherEmail: "apim@autorestsdk.com",
    publisherName: "autorestsdk",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    sku: {
        capacity: 2,
        name: "Premium",
    },
    tags: {
        tag1: "value1",
        tag2: "value2",
        tag3: "value3",
    },
    virtualNetworkConfiguration: {
        subnetResourceId: "/subscriptions/subid/resourceGroups/rgName/providers/Microsoft.Network/virtualNetworks/apimcus/subnets/tenant",
    },
    virtualNetworkType: "External",
    zones: [
        "1",
        "2",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_management_service = azure_native.apimanagement.ApiManagementService("apiManagementService",
    location="East US 2 EUAP",
    public_ip_address_id="/subscriptions/subid/resourceGroups/rgName/providers/Microsoft.Network/publicIPAddresses/apimazvnet",
    publisher_email="apim@autorestsdk.com",
    publisher_name="autorestsdk",
    resource_group_name="rg1",
    service_name="apimService1",
    sku=azure_native.apimanagement.ApiManagementServiceSkuPropertiesArgs(
        capacity=2,
        name="Premium",
    ),
    tags={
        "tag1": "value1",
        "tag2": "value2",
        "tag3": "value3",
    },
    virtual_network_configuration=azure_native.apimanagement.VirtualNetworkConfigurationArgs(
        subnet_resource_id="/subscriptions/subid/resourceGroups/rgName/providers/Microsoft.Network/virtualNetworks/apimcus/subnets/tenant",
    ),
    virtual_network_type="External",
    zones=[
        "1",
        "2",
    ])

```

```yaml
resources:
  apiManagementService:
    type: azure-native:apimanagement:ApiManagementService
    properties:
      location: East US 2 EUAP
      publicIpAddressId: /subscriptions/subid/resourceGroups/rgName/providers/Microsoft.Network/publicIPAddresses/apimazvnet
      publisherEmail: apim@autorestsdk.com
      publisherName: autorestsdk
      resourceGroupName: rg1
      serviceName: apimService1
      sku:
        capacity: 2
        name: Premium
      tags:
        tag1: value1
        tag2: value2
        tag3: value3
      virtualNetworkConfiguration:
        subnetResourceId: /subscriptions/subid/resourceGroups/rgName/providers/Microsoft.Network/virtualNetworks/apimcus/subnets/tenant
      virtualNetworkType: External
      zones:
        - '1'
        - '2'

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateServiceInZones
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiManagementService = new AzureNative.ApiManagement.ApiManagementService("apiManagementService", new()
    {
        Location = "North europe",
        PublisherEmail = "apim@autorestsdk.com",
        PublisherName = "autorestsdk",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Sku = new AzureNative.ApiManagement.Inputs.ApiManagementServiceSkuPropertiesArgs
        {
            Capacity = 2,
            Name = "Premium",
        },
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
            { "tag3", "value3" },
        },
        Zones = new[]
        {
            "1",
            "2",
        },
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewApiManagementService(ctx, "apiManagementService", &apimanagement.ApiManagementServiceArgs{
			Location:          pulumi.String("North europe"),
			PublisherEmail:    pulumi.String("apim@autorestsdk.com"),
			PublisherName:     pulumi.String("autorestsdk"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Sku: &apimanagement.ApiManagementServiceSkuPropertiesArgs{
				Capacity: pulumi.Int(2),
				Name:     pulumi.String("Premium"),
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
				"tag3": pulumi.String("value3"),
			},
			Zones: pulumi.StringArray{
				pulumi.String("1"),
				pulumi.String("2"),
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
import com.pulumi.azurenative.apimanagement.ApiManagementService;
import com.pulumi.azurenative.apimanagement.ApiManagementServiceArgs;
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
        var apiManagementService = new ApiManagementService("apiManagementService", ApiManagementServiceArgs.builder()        
            .location("North europe")
            .publisherEmail("apim@autorestsdk.com")
            .publisherName("autorestsdk")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("name", "Premium")
            ))
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2"),
                Map.entry("tag3", "value3")
            ))
            .zones(            
                "1",
                "2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiManagementService = new azure_native.apimanagement.ApiManagementService("apiManagementService", {
    location: "North europe",
    publisherEmail: "apim@autorestsdk.com",
    publisherName: "autorestsdk",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    sku: {
        capacity: 2,
        name: "Premium",
    },
    tags: {
        tag1: "value1",
        tag2: "value2",
        tag3: "value3",
    },
    zones: [
        "1",
        "2",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_management_service = azure_native.apimanagement.ApiManagementService("apiManagementService",
    location="North europe",
    publisher_email="apim@autorestsdk.com",
    publisher_name="autorestsdk",
    resource_group_name="rg1",
    service_name="apimService1",
    sku=azure_native.apimanagement.ApiManagementServiceSkuPropertiesArgs(
        capacity=2,
        name="Premium",
    ),
    tags={
        "tag1": "value1",
        "tag2": "value2",
        "tag3": "value3",
    },
    zones=[
        "1",
        "2",
    ])

```

```yaml
resources:
  apiManagementService:
    type: azure-native:apimanagement:ApiManagementService
    properties:
      location: North europe
      publisherEmail: apim@autorestsdk.com
      publisherName: autorestsdk
      resourceGroupName: rg1
      serviceName: apimService1
      sku:
        capacity: 2
        name: Premium
      tags:
        tag1: value1
        tag2: value2
        tag3: value3
      zones:
        - '1'
        - '2'

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateServiceWithCustomHostnameKeyVault
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiManagementService = new AzureNative.ApiManagement.ApiManagementService("apiManagementService", new()
    {
        ApiVersionConstraint = new AzureNative.ApiManagement.Inputs.ApiVersionConstraintArgs
        {
            MinApiVersion = "2019-01-01",
        },
        HostnameConfigurations = new[]
        {
            new AzureNative.ApiManagement.Inputs.HostnameConfigurationArgs
            {
                DefaultSslBinding = true,
                HostName = "gateway1.msitesting.net",
                IdentityClientId = "329419bc-adec-4dce-9568-25a6d486e468",
                KeyVaultId = "https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert",
                Type = "Proxy",
            },
            new AzureNative.ApiManagement.Inputs.HostnameConfigurationArgs
            {
                HostName = "mgmt.msitesting.net",
                IdentityClientId = "329419bc-adec-4dce-9568-25a6d486e468",
                KeyVaultId = "https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert",
                Type = "Management",
            },
            new AzureNative.ApiManagement.Inputs.HostnameConfigurationArgs
            {
                HostName = "portal1.msitesting.net",
                IdentityClientId = "329419bc-adec-4dce-9568-25a6d486e468",
                KeyVaultId = "https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert",
                Type = "Portal",
            },
        },
        Identity = new AzureNative.ApiManagement.Inputs.ApiManagementServiceIdentityArgs
        {
            Type = "UserAssigned",
            UserAssignedIdentities = 
            {
                { "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/id1", null },
            },
        },
        Location = "North Europe",
        PublisherEmail = "apim@autorestsdk.com",
        PublisherName = "autorestsdk",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Sku = new AzureNative.ApiManagement.Inputs.ApiManagementServiceSkuPropertiesArgs
        {
            Capacity = 1,
            Name = "Premium",
        },
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
            { "tag3", "value3" },
        },
        VirtualNetworkType = "None",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewApiManagementService(ctx, "apiManagementService", &apimanagement.ApiManagementServiceArgs{
			ApiVersionConstraint: &apimanagement.ApiVersionConstraintArgs{
				MinApiVersion: pulumi.String("2019-01-01"),
			},
			HostnameConfigurations: []apimanagement.HostnameConfigurationArgs{
				{
					DefaultSslBinding: pulumi.Bool(true),
					HostName:          pulumi.String("gateway1.msitesting.net"),
					IdentityClientId:  pulumi.String("329419bc-adec-4dce-9568-25a6d486e468"),
					KeyVaultId:        pulumi.String("https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert"),
					Type:              pulumi.String("Proxy"),
				},
				{
					HostName:         pulumi.String("mgmt.msitesting.net"),
					IdentityClientId: pulumi.String("329419bc-adec-4dce-9568-25a6d486e468"),
					KeyVaultId:       pulumi.String("https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert"),
					Type:             pulumi.String("Management"),
				},
				{
					HostName:         pulumi.String("portal1.msitesting.net"),
					IdentityClientId: pulumi.String("329419bc-adec-4dce-9568-25a6d486e468"),
					KeyVaultId:       pulumi.String("https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert"),
					Type:             pulumi.String("Portal"),
				},
			},
			Identity: apimanagement.ApiManagementServiceIdentityResponse{
				Type: pulumi.String("UserAssigned"),
				UserAssignedIdentities: apimanagement.UserIdentityPropertiesMap{
					"/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/id1": nil,
				},
			},
			Location:          pulumi.String("North Europe"),
			PublisherEmail:    pulumi.String("apim@autorestsdk.com"),
			PublisherName:     pulumi.String("autorestsdk"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Sku: &apimanagement.ApiManagementServiceSkuPropertiesArgs{
				Capacity: pulumi.Int(1),
				Name:     pulumi.String("Premium"),
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
				"tag3": pulumi.String("value3"),
			},
			VirtualNetworkType: pulumi.String("None"),
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
import com.pulumi.azurenative.apimanagement.ApiManagementService;
import com.pulumi.azurenative.apimanagement.ApiManagementServiceArgs;
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
        var apiManagementService = new ApiManagementService("apiManagementService", ApiManagementServiceArgs.builder()        
            .apiVersionConstraint(Map.of("minApiVersion", "2019-01-01"))
            .hostnameConfigurations(            
                Map.ofEntries(
                    Map.entry("defaultSslBinding", true),
                    Map.entry("hostName", "gateway1.msitesting.net"),
                    Map.entry("identityClientId", "329419bc-adec-4dce-9568-25a6d486e468"),
                    Map.entry("keyVaultId", "https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert"),
                    Map.entry("type", "Proxy")
                ),
                Map.ofEntries(
                    Map.entry("hostName", "mgmt.msitesting.net"),
                    Map.entry("identityClientId", "329419bc-adec-4dce-9568-25a6d486e468"),
                    Map.entry("keyVaultId", "https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert"),
                    Map.entry("type", "Management")
                ),
                Map.ofEntries(
                    Map.entry("hostName", "portal1.msitesting.net"),
                    Map.entry("identityClientId", "329419bc-adec-4dce-9568-25a6d486e468"),
                    Map.entry("keyVaultId", "https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert"),
                    Map.entry("type", "Portal")
                ))
            .identity(Map.ofEntries(
                Map.entry("type", "UserAssigned"),
                Map.entry("userAssignedIdentities", Map.of("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/id1", ))
            ))
            .location("North Europe")
            .publisherEmail("apim@autorestsdk.com")
            .publisherName("autorestsdk")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("name", "Premium")
            ))
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2"),
                Map.entry("tag3", "value3")
            ))
            .virtualNetworkType("None")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiManagementService = new azure_native.apimanagement.ApiManagementService("apiManagementService", {
    apiVersionConstraint: {
        minApiVersion: "2019-01-01",
    },
    hostnameConfigurations: [
        {
            defaultSslBinding: true,
            hostName: "gateway1.msitesting.net",
            identityClientId: "329419bc-adec-4dce-9568-25a6d486e468",
            keyVaultId: "https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert",
            type: "Proxy",
        },
        {
            hostName: "mgmt.msitesting.net",
            identityClientId: "329419bc-adec-4dce-9568-25a6d486e468",
            keyVaultId: "https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert",
            type: "Management",
        },
        {
            hostName: "portal1.msitesting.net",
            identityClientId: "329419bc-adec-4dce-9568-25a6d486e468",
            keyVaultId: "https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert",
            type: "Portal",
        },
    ],
    identity: {
        type: "UserAssigned",
        userAssignedIdentities: {
            "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/id1": {},
        },
    },
    location: "North Europe",
    publisherEmail: "apim@autorestsdk.com",
    publisherName: "autorestsdk",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    sku: {
        capacity: 1,
        name: "Premium",
    },
    tags: {
        tag1: "value1",
        tag2: "value2",
        tag3: "value3",
    },
    virtualNetworkType: "None",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_management_service = azure_native.apimanagement.ApiManagementService("apiManagementService",
    api_version_constraint=azure_native.apimanagement.ApiVersionConstraintArgs(
        min_api_version="2019-01-01",
    ),
    hostname_configurations=[
        azure_native.apimanagement.HostnameConfigurationArgs(
            default_ssl_binding=True,
            host_name="gateway1.msitesting.net",
            identity_client_id="329419bc-adec-4dce-9568-25a6d486e468",
            key_vault_id="https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert",
            type="Proxy",
        ),
        azure_native.apimanagement.HostnameConfigurationArgs(
            host_name="mgmt.msitesting.net",
            identity_client_id="329419bc-adec-4dce-9568-25a6d486e468",
            key_vault_id="https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert",
            type="Management",
        ),
        azure_native.apimanagement.HostnameConfigurationArgs(
            host_name="portal1.msitesting.net",
            identity_client_id="329419bc-adec-4dce-9568-25a6d486e468",
            key_vault_id="https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert",
            type="Portal",
        ),
    ],
    identity=azure_native.apimanagement.ApiManagementServiceIdentityResponseArgs(
        type="UserAssigned",
        user_assigned_identities={
            "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/id1": azure_native.apimanagement.UserIdentityPropertiesArgs(),
        },
    ),
    location="North Europe",
    publisher_email="apim@autorestsdk.com",
    publisher_name="autorestsdk",
    resource_group_name="rg1",
    service_name="apimService1",
    sku=azure_native.apimanagement.ApiManagementServiceSkuPropertiesArgs(
        capacity=1,
        name="Premium",
    ),
    tags={
        "tag1": "value1",
        "tag2": "value2",
        "tag3": "value3",
    },
    virtual_network_type="None")

```

```yaml
resources:
  apiManagementService:
    type: azure-native:apimanagement:ApiManagementService
    properties:
      apiVersionConstraint:
        minApiVersion: 2019-01-01
      hostnameConfigurations:
        - defaultSslBinding: true
          hostName: gateway1.msitesting.net
          identityClientId: 329419bc-adec-4dce-9568-25a6d486e468
          keyVaultId: https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert
          type: Proxy
        - hostName: mgmt.msitesting.net
          identityClientId: 329419bc-adec-4dce-9568-25a6d486e468
          keyVaultId: https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert
          type: Management
        - hostName: portal1.msitesting.net
          identityClientId: 329419bc-adec-4dce-9568-25a6d486e468
          keyVaultId: https://rpbvtkeyvaultintegration.vault.azure.net/secrets/msitestingCert
          type: Portal
      identity:
        type: UserAssigned
        userAssignedIdentities:
          /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/id1: {}
      location: North Europe
      publisherEmail: apim@autorestsdk.com
      publisherName: autorestsdk
      resourceGroupName: rg1
      serviceName: apimService1
      sku:
        capacity: 1
        name: Premium
      tags:
        tag1: value1
        tag2: value2
        tag3: value3
      virtualNetworkType: None

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateServiceWithNatGatewayEnabled
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiManagementService = new AzureNative.ApiManagement.ApiManagementService("apiManagementService", new()
    {
        Location = "East US",
        NatGatewayState = "Enabled",
        PublisherEmail = "apim@autorestsdk.com",
        PublisherName = "autorestsdk",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Sku = new AzureNative.ApiManagement.Inputs.ApiManagementServiceSkuPropertiesArgs
        {
            Capacity = 1,
            Name = "Premium",
        },
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
            { "tag3", "value3" },
        },
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewApiManagementService(ctx, "apiManagementService", &apimanagement.ApiManagementServiceArgs{
			Location:          pulumi.String("East US"),
			NatGatewayState:   pulumi.String("Enabled"),
			PublisherEmail:    pulumi.String("apim@autorestsdk.com"),
			PublisherName:     pulumi.String("autorestsdk"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Sku: &apimanagement.ApiManagementServiceSkuPropertiesArgs{
				Capacity: pulumi.Int(1),
				Name:     pulumi.String("Premium"),
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
				"tag3": pulumi.String("value3"),
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
import com.pulumi.azurenative.apimanagement.ApiManagementService;
import com.pulumi.azurenative.apimanagement.ApiManagementServiceArgs;
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
        var apiManagementService = new ApiManagementService("apiManagementService", ApiManagementServiceArgs.builder()        
            .location("East US")
            .natGatewayState("Enabled")
            .publisherEmail("apim@autorestsdk.com")
            .publisherName("autorestsdk")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("name", "Premium")
            ))
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2"),
                Map.entry("tag3", "value3")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiManagementService = new azure_native.apimanagement.ApiManagementService("apiManagementService", {
    location: "East US",
    natGatewayState: "Enabled",
    publisherEmail: "apim@autorestsdk.com",
    publisherName: "autorestsdk",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    sku: {
        capacity: 1,
        name: "Premium",
    },
    tags: {
        tag1: "value1",
        tag2: "value2",
        tag3: "value3",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_management_service = azure_native.apimanagement.ApiManagementService("apiManagementService",
    location="East US",
    nat_gateway_state="Enabled",
    publisher_email="apim@autorestsdk.com",
    publisher_name="autorestsdk",
    resource_group_name="rg1",
    service_name="apimService1",
    sku=azure_native.apimanagement.ApiManagementServiceSkuPropertiesArgs(
        capacity=1,
        name="Premium",
    ),
    tags={
        "tag1": "value1",
        "tag2": "value2",
        "tag3": "value3",
    })

```

```yaml
resources:
  apiManagementService:
    type: azure-native:apimanagement:ApiManagementService
    properties:
      location: East US
      natGatewayState: Enabled
      publisherEmail: apim@autorestsdk.com
      publisherName: autorestsdk
      resourceGroupName: rg1
      serviceName: apimService1
      sku:
        capacity: 1
        name: Premium
      tags:
        tag1: value1
        tag2: value2
        tag3: value3

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateServiceWithSystemCertificates
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiManagementService = new AzureNative.ApiManagement.ApiManagementService("apiManagementService", new()
    {
        Certificates = new[]
        {
            new AzureNative.ApiManagement.Inputs.CertificateConfigurationArgs
            {
                CertificatePassword = "Password",
                EncodedCertificate = "*******Base64 encoded Certificate******************",
                StoreName = "CertificateAuthority",
            },
        },
        Location = "Central US",
        PublisherEmail = "apim@autorestsdk.com",
        PublisherName = "autorestsdk",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Sku = new AzureNative.ApiManagement.Inputs.ApiManagementServiceSkuPropertiesArgs
        {
            Capacity = 1,
            Name = "Basic",
        },
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
            { "tag3", "value3" },
        },
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewApiManagementService(ctx, "apiManagementService", &apimanagement.ApiManagementServiceArgs{
			Certificates: []apimanagement.CertificateConfigurationArgs{
				{
					CertificatePassword: pulumi.String("Password"),
					EncodedCertificate:  pulumi.String("*******Base64 encoded Certificate******************"),
					StoreName:           pulumi.String("CertificateAuthority"),
				},
			},
			Location:          pulumi.String("Central US"),
			PublisherEmail:    pulumi.String("apim@autorestsdk.com"),
			PublisherName:     pulumi.String("autorestsdk"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Sku: &apimanagement.ApiManagementServiceSkuPropertiesArgs{
				Capacity: pulumi.Int(1),
				Name:     pulumi.String("Basic"),
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
				"tag3": pulumi.String("value3"),
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
import com.pulumi.azurenative.apimanagement.ApiManagementService;
import com.pulumi.azurenative.apimanagement.ApiManagementServiceArgs;
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
        var apiManagementService = new ApiManagementService("apiManagementService", ApiManagementServiceArgs.builder()        
            .certificates(Map.ofEntries(
                Map.entry("certificatePassword", "Password"),
                Map.entry("encodedCertificate", "*******Base64 encoded Certificate******************"),
                Map.entry("storeName", "CertificateAuthority")
            ))
            .location("Central US")
            .publisherEmail("apim@autorestsdk.com")
            .publisherName("autorestsdk")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("name", "Basic")
            ))
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2"),
                Map.entry("tag3", "value3")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiManagementService = new azure_native.apimanagement.ApiManagementService("apiManagementService", {
    certificates: [{
        certificatePassword: "Password",
        encodedCertificate: "*******Base64 encoded Certificate******************",
        storeName: "CertificateAuthority",
    }],
    location: "Central US",
    publisherEmail: "apim@autorestsdk.com",
    publisherName: "autorestsdk",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    sku: {
        capacity: 1,
        name: "Basic",
    },
    tags: {
        tag1: "value1",
        tag2: "value2",
        tag3: "value3",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_management_service = azure_native.apimanagement.ApiManagementService("apiManagementService",
    certificates=[azure_native.apimanagement.CertificateConfigurationArgs(
        certificate_password="Password",
        encoded_certificate="*******Base64 encoded Certificate******************",
        store_name="CertificateAuthority",
    )],
    location="Central US",
    publisher_email="apim@autorestsdk.com",
    publisher_name="autorestsdk",
    resource_group_name="rg1",
    service_name="apimService1",
    sku=azure_native.apimanagement.ApiManagementServiceSkuPropertiesArgs(
        capacity=1,
        name="Basic",
    ),
    tags={
        "tag1": "value1",
        "tag2": "value2",
        "tag3": "value3",
    })

```

```yaml
resources:
  apiManagementService:
    type: azure-native:apimanagement:ApiManagementService
    properties:
      certificates:
        - certificatePassword: Password
          encodedCertificate: '*******Base64 encoded Certificate******************'
          storeName: CertificateAuthority
      location: Central US
      publisherEmail: apim@autorestsdk.com
      publisherName: autorestsdk
      resourceGroupName: rg1
      serviceName: apimService1
      sku:
        capacity: 1
        name: Basic
      tags:
        tag1: value1
        tag2: value2
        tag3: value3

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateServiceWithUserAssignedIdentity
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiManagementService = new AzureNative.ApiManagement.ApiManagementService("apiManagementService", new()
    {
        Identity = new AzureNative.ApiManagement.Inputs.ApiManagementServiceIdentityArgs
        {
            Type = "UserAssigned",
            UserAssignedIdentities = 
            {
                { "/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/apimService1", null },
            },
        },
        Location = "West US",
        PublisherEmail = "apim@autorestsdk.com",
        PublisherName = "autorestsdk",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Sku = new AzureNative.ApiManagement.Inputs.ApiManagementServiceSkuPropertiesArgs
        {
            Capacity = 0,
            Name = "Consumption",
        },
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
            { "tag3", "value3" },
        },
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewApiManagementService(ctx, "apiManagementService", &apimanagement.ApiManagementServiceArgs{
			Identity: apimanagement.ApiManagementServiceIdentityResponse{
				Type: pulumi.String("UserAssigned"),
				UserAssignedIdentities: apimanagement.UserIdentityPropertiesMap{
					"/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/apimService1": nil,
				},
			},
			Location:          pulumi.String("West US"),
			PublisherEmail:    pulumi.String("apim@autorestsdk.com"),
			PublisherName:     pulumi.String("autorestsdk"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Sku: &apimanagement.ApiManagementServiceSkuPropertiesArgs{
				Capacity: pulumi.Int(0),
				Name:     pulumi.String("Consumption"),
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
				"tag3": pulumi.String("value3"),
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
import com.pulumi.azurenative.apimanagement.ApiManagementService;
import com.pulumi.azurenative.apimanagement.ApiManagementServiceArgs;
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
        var apiManagementService = new ApiManagementService("apiManagementService", ApiManagementServiceArgs.builder()        
            .identity(Map.ofEntries(
                Map.entry("type", "UserAssigned"),
                Map.entry("userAssignedIdentities", Map.of("/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/apimService1", ))
            ))
            .location("West US")
            .publisherEmail("apim@autorestsdk.com")
            .publisherName("autorestsdk")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .sku(Map.ofEntries(
                Map.entry("capacity", 0),
                Map.entry("name", "Consumption")
            ))
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2"),
                Map.entry("tag3", "value3")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiManagementService = new azure_native.apimanagement.ApiManagementService("apiManagementService", {
    identity: {
        type: "UserAssigned",
        userAssignedIdentities: {
            "/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/apimService1": {},
        },
    },
    location: "West US",
    publisherEmail: "apim@autorestsdk.com",
    publisherName: "autorestsdk",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    sku: {
        capacity: 0,
        name: "Consumption",
    },
    tags: {
        tag1: "value1",
        tag2: "value2",
        tag3: "value3",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_management_service = azure_native.apimanagement.ApiManagementService("apiManagementService",
    identity=azure_native.apimanagement.ApiManagementServiceIdentityResponseArgs(
        type="UserAssigned",
        user_assigned_identities={
            "/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/apimService1": azure_native.apimanagement.UserIdentityPropertiesArgs(),
        },
    ),
    location="West US",
    publisher_email="apim@autorestsdk.com",
    publisher_name="autorestsdk",
    resource_group_name="rg1",
    service_name="apimService1",
    sku=azure_native.apimanagement.ApiManagementServiceSkuPropertiesArgs(
        capacity=0,
        name="Consumption",
    ),
    tags={
        "tag1": "value1",
        "tag2": "value2",
        "tag3": "value3",
    })

```

```yaml
resources:
  apiManagementService:
    type: azure-native:apimanagement:ApiManagementService
    properties:
      identity:
        type: UserAssigned
        userAssignedIdentities:
          /subscriptions/subid/resourcegroups/rg1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/apimService1: {}
      location: West US
      publisherEmail: apim@autorestsdk.com
      publisherName: autorestsdk
      resourceGroupName: rg1
      serviceName: apimService1
      sku:
        capacity: 0
        name: Consumption
      tags:
        tag1: value1
        tag2: value2
        tag3: value3

```

{{% /example %}}
{{% example %}}
### ApiManagementUndelete
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiManagementService = new AzureNative.ApiManagement.ApiManagementService("apiManagementService", new()
    {
        Location = "South Central US",
        PublisherEmail = "foo@contoso.com",
        PublisherName = "foo",
        ResourceGroupName = "rg1",
        Restore = true,
        ServiceName = "apimService1",
        Sku = new AzureNative.ApiManagement.Inputs.ApiManagementServiceSkuPropertiesArgs
        {
            Capacity = 1,
            Name = "Developer",
        },
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewApiManagementService(ctx, "apiManagementService", &apimanagement.ApiManagementServiceArgs{
			Location:          pulumi.String("South Central US"),
			PublisherEmail:    pulumi.String("foo@contoso.com"),
			PublisherName:     pulumi.String("foo"),
			ResourceGroupName: pulumi.String("rg1"),
			Restore:           pulumi.Bool(true),
			ServiceName:       pulumi.String("apimService1"),
			Sku: &apimanagement.ApiManagementServiceSkuPropertiesArgs{
				Capacity: pulumi.Int(1),
				Name:     pulumi.String("Developer"),
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
import com.pulumi.azurenative.apimanagement.ApiManagementService;
import com.pulumi.azurenative.apimanagement.ApiManagementServiceArgs;
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
        var apiManagementService = new ApiManagementService("apiManagementService", ApiManagementServiceArgs.builder()        
            .location("South Central US")
            .publisherEmail("foo@contoso.com")
            .publisherName("foo")
            .resourceGroupName("rg1")
            .restore(true)
            .serviceName("apimService1")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("name", "Developer")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiManagementService = new azure_native.apimanagement.ApiManagementService("apiManagementService", {
    location: "South Central US",
    publisherEmail: "foo@contoso.com",
    publisherName: "foo",
    resourceGroupName: "rg1",
    restore: true,
    serviceName: "apimService1",
    sku: {
        capacity: 1,
        name: "Developer",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_management_service = azure_native.apimanagement.ApiManagementService("apiManagementService",
    location="South Central US",
    publisher_email="foo@contoso.com",
    publisher_name="foo",
    resource_group_name="rg1",
    restore=True,
    service_name="apimService1",
    sku=azure_native.apimanagement.ApiManagementServiceSkuPropertiesArgs(
        capacity=1,
        name="Developer",
    ))

```

```yaml
resources:
  apiManagementService:
    type: azure-native:apimanagement:ApiManagementService
    properties:
      location: South Central US
      publisherEmail: foo@contoso.com
      publisherName: foo
      resourceGroupName: rg1
      restore: true
      serviceName: apimService1
      sku:
        capacity: 1
        name: Developer

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ApiManagementService apimService1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1 
```
