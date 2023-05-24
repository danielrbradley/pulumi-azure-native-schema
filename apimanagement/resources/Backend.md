Backend details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateBackendProxyBackend
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var backend = new AzureNative.ApiManagement.Backend("backend", new()
    {
        BackendId = "proxybackend",
        Credentials = new AzureNative.ApiManagement.Inputs.BackendCredentialsContractArgs
        {
            Authorization = new AzureNative.ApiManagement.Inputs.BackendAuthorizationHeaderCredentialsArgs
            {
                Parameter = "opensesma",
                Scheme = "Basic",
            },
            Header = 
            {
                { "x-my-1", new[]
                {
                    "val1",
                    "val2",
                } },
            },
            Query = 
            {
                { "sv", new[]
                {
                    "xx",
                    "bb",
                    "cc",
                } },
            },
        },
        Description = "description5308",
        Protocol = "http",
        Proxy = new AzureNative.ApiManagement.Inputs.BackendProxyContractArgs
        {
            Password = "<password>",
            Url = "http://192.168.1.1:8080",
            Username = "Contoso\\admin",
        },
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Tls = new AzureNative.ApiManagement.Inputs.BackendTlsPropertiesArgs
        {
            ValidateCertificateChain = true,
            ValidateCertificateName = true,
        },
        Url = "https://backendname2644/",
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
		_, err := apimanagement.NewBackend(ctx, "backend", &apimanagement.BackendArgs{
			BackendId: pulumi.String("proxybackend"),
			Credentials: apimanagement.BackendCredentialsContractResponse{
				Authorization: &apimanagement.BackendAuthorizationHeaderCredentialsArgs{
					Parameter: pulumi.String("opensesma"),
					Scheme:    pulumi.String("Basic"),
				},
				Header: pulumi.StringArrayMap{
					"x-my-1": pulumi.StringArray{
						pulumi.String("val1"),
						pulumi.String("val2"),
					},
				},
				Query: pulumi.StringArrayMap{
					"sv": pulumi.StringArray{
						pulumi.String("xx"),
						pulumi.String("bb"),
						pulumi.String("cc"),
					},
				},
			},
			Description: pulumi.String("description5308"),
			Protocol:    pulumi.String("http"),
			Proxy: &apimanagement.BackendProxyContractArgs{
				Password: pulumi.String("<password>"),
				Url:      pulumi.String("http://192.168.1.1:8080"),
				Username: pulumi.String("Contoso\\admin"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Tls: &apimanagement.BackendTlsPropertiesArgs{
				ValidateCertificateChain: pulumi.Bool(true),
				ValidateCertificateName:  pulumi.Bool(true),
			},
			Url: pulumi.String("https://backendname2644/"),
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
import com.pulumi.azurenative.apimanagement.Backend;
import com.pulumi.azurenative.apimanagement.BackendArgs;
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
        var backend = new Backend("backend", BackendArgs.builder()        
            .backendId("proxybackend")
            .credentials(Map.ofEntries(
                Map.entry("authorization", Map.ofEntries(
                    Map.entry("parameter", "opensesma"),
                    Map.entry("scheme", "Basic")
                )),
                Map.entry("header", Map.of("x-my-1",                 
                    "val1",
                    "val2")),
                Map.entry("query", Map.of("sv",                 
                    "xx",
                    "bb",
                    "cc"))
            ))
            .description("description5308")
            .protocol("http")
            .proxy(Map.ofEntries(
                Map.entry("password", "<password>"),
                Map.entry("url", "http://192.168.1.1:8080"),
                Map.entry("username", "Contoso\\admin")
            ))
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .tls(Map.ofEntries(
                Map.entry("validateCertificateChain", true),
                Map.entry("validateCertificateName", true)
            ))
            .url("https://backendname2644/")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const backend = new azure_native.apimanagement.Backend("backend", {
    backendId: "proxybackend",
    credentials: {
        authorization: {
            parameter: "opensesma",
            scheme: "Basic",
        },
        header: {
            "x-my-1": [
                "val1",
                "val2",
            ],
        },
        query: {
            sv: [
                "xx",
                "bb",
                "cc",
            ],
        },
    },
    description: "description5308",
    protocol: "http",
    proxy: {
        password: "<password>",
        url: "http://192.168.1.1:8080",
        username: "Contoso\\admin",
    },
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    tls: {
        validateCertificateChain: true,
        validateCertificateName: true,
    },
    url: "https://backendname2644/",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

backend = azure_native.apimanagement.Backend("backend",
    backend_id="proxybackend",
    credentials=azure_native.apimanagement.BackendCredentialsContractResponseArgs(
        authorization=azure_native.apimanagement.BackendAuthorizationHeaderCredentialsArgs(
            parameter="opensesma",
            scheme="Basic",
        ),
        header={
            "x-my-1": [
                "val1",
                "val2",
            ],
        },
        query={
            "sv": [
                "xx",
                "bb",
                "cc",
            ],
        },
    ),
    description="description5308",
    protocol="http",
    proxy=azure_native.apimanagement.BackendProxyContractArgs(
        password="<password>",
        url="http://192.168.1.1:8080",
        username="Contoso\\admin",
    ),
    resource_group_name="rg1",
    service_name="apimService1",
    tls=azure_native.apimanagement.BackendTlsPropertiesArgs(
        validate_certificate_chain=True,
        validate_certificate_name=True,
    ),
    url="https://backendname2644/")

```

```yaml
resources:
  backend:
    type: azure-native:apimanagement:Backend
    properties:
      backendId: proxybackend
      credentials:
        authorization:
          parameter: opensesma
          scheme: Basic
        header:
          x-my-1:
            - val1
            - val2
        query:
          sv:
            - xx
            - bb
            - cc
      description: description5308
      protocol: http
      proxy:
        password: <password>
        url: http://192.168.1.1:8080
        username: Contoso\admin
      resourceGroupName: rg1
      serviceName: apimService1
      tls:
        validateCertificateChain: true
        validateCertificateName: true
      url: https://backendname2644/

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateBackendServiceFabric
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var backend = new AzureNative.ApiManagement.Backend("backend", new()
    {
        BackendId = "sfbackend",
        Description = "Service Fabric Test App 1",
        Properties = new AzureNative.ApiManagement.Inputs.BackendPropertiesArgs
        {
            ServiceFabricCluster = new AzureNative.ApiManagement.Inputs.BackendServiceFabricClusterPropertiesArgs
            {
                ClientCertificateId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/certificates/cert1",
                ManagementEndpoints = new[]
                {
                    "https://somecluster.com",
                },
                MaxPartitionResolutionRetries = 5,
                ServerX509Names = new[]
                {
                    new AzureNative.ApiManagement.Inputs.X509CertificateNameArgs
                    {
                        IssuerCertificateThumbprint = "IssuerCertificateThumbprint1",
                        Name = "ServerCommonName1",
                    },
                },
            },
        },
        Protocol = "http",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Url = "fabric:/mytestapp/mytestservice",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.apimanagement.Backend;
import com.pulumi.azurenative.apimanagement.BackendArgs;
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
        var backend = new Backend("backend", BackendArgs.builder()        
            .backendId("sfbackend")
            .description("Service Fabric Test App 1")
            .properties(Map.of("serviceFabricCluster", Map.ofEntries(
                Map.entry("clientCertificateId", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/certificates/cert1"),
                Map.entry("managementEndpoints", "https://somecluster.com"),
                Map.entry("maxPartitionResolutionRetries", 5),
                Map.entry("serverX509Names", Map.ofEntries(
                    Map.entry("issuerCertificateThumbprint", "IssuerCertificateThumbprint1"),
                    Map.entry("name", "ServerCommonName1")
                ))
            )))
            .protocol("http")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .url("fabric:/mytestapp/mytestservice")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const backend = new azure_native.apimanagement.Backend("backend", {
    backendId: "sfbackend",
    description: "Service Fabric Test App 1",
    properties: {
        serviceFabricCluster: {
            clientCertificateId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/certificates/cert1",
            managementEndpoints: ["https://somecluster.com"],
            maxPartitionResolutionRetries: 5,
            serverX509Names: [{
                issuerCertificateThumbprint: "IssuerCertificateThumbprint1",
                name: "ServerCommonName1",
            }],
        },
    },
    protocol: "http",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    url: "fabric:/mytestapp/mytestservice",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

backend = azure_native.apimanagement.Backend("backend",
    backend_id="sfbackend",
    description="Service Fabric Test App 1",
    properties=azure_native.apimanagement.BackendPropertiesResponseArgs(
        service_fabric_cluster={
            "clientCertificateId": "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/certificates/cert1",
            "managementEndpoints": ["https://somecluster.com"],
            "maxPartitionResolutionRetries": 5,
            "serverX509Names": [azure_native.apimanagement.X509CertificateNameArgs(
                issuer_certificate_thumbprint="IssuerCertificateThumbprint1",
                name="ServerCommonName1",
            )],
        },
    ),
    protocol="http",
    resource_group_name="rg1",
    service_name="apimService1",
    url="fabric:/mytestapp/mytestservice")

```

```yaml
resources:
  backend:
    type: azure-native:apimanagement:Backend
    properties:
      backendId: sfbackend
      description: Service Fabric Test App 1
      properties:
        serviceFabricCluster:
          clientCertificateId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/certificates/cert1
          managementEndpoints:
            - https://somecluster.com
          maxPartitionResolutionRetries: 5
          serverX509Names:
            - issuerCertificateThumbprint: IssuerCertificateThumbprint1
              name: ServerCommonName1
      protocol: http
      resourceGroupName: rg1
      serviceName: apimService1
      url: fabric:/mytestapp/mytestservice

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:Backend sfbackend /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/backends/sfbackend 
```
