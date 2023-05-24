Data controller resource
API Version: 2023-03-15-preview.
Previous API Version: 2021-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a Data Controller.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataController = new AzureNative.AzureArcData.DataController("dataController", new()
    {
        DataControllerName = "testdataController",
        ExtendedLocation = new AzureNative.AzureArcData.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation",
            Type = "CustomLocation",
        },
        Location = "northeurope",
        Properties = new AzureNative.AzureArcData.Inputs.DataControllerPropertiesArgs
        {
            BasicLoginInformation = new AzureNative.AzureArcData.Inputs.BasicLoginInformationArgs
            {
                Password = "********",
                Username = "username",
            },
            ClusterId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s",
            ExtensionId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s/providers/Microsoft.KubernetesConfiguration/extensions/extension",
            Infrastructure = AzureNative.AzureArcData.Infrastructure.Onpremises,
            LogAnalyticsWorkspaceConfig = new AzureNative.AzureArcData.Inputs.LogAnalyticsWorkspaceConfigArgs
            {
                PrimaryKey = "********",
                WorkspaceId = "00000000-1111-2222-3333-444444444444",
            },
            LogsDashboardCredential = new AzureNative.AzureArcData.Inputs.BasicLoginInformationArgs
            {
                Password = "********",
                Username = "username",
            },
            MetricsDashboardCredential = new AzureNative.AzureArcData.Inputs.BasicLoginInformationArgs
            {
                Password = "********",
                Username = "username",
            },
            OnPremiseProperty = new AzureNative.AzureArcData.Inputs.OnPremisePropertyArgs
            {
                Id = "12345678-1234-1234-ab12-1a2b3c4d5e6f",
                PublicSigningKey = "publicOnPremSigningKey",
            },
            UploadServicePrincipal = new AzureNative.AzureArcData.Inputs.UploadServicePrincipalArgs
            {
                Authority = "https://login.microsoftonline.com/",
                ClientId = "00000000-1111-2222-3333-444444444444",
                ClientSecret = "********",
                TenantId = "00000000-1111-2222-3333-444444444444",
            },
            UploadWatermark = new AzureNative.AzureArcData.Inputs.UploadWatermarkArgs
            {
                Logs = "2020-01-01T17:18:19.1234567Z",
                Metrics = "2020-01-01T17:18:19.1234567Z",
                Usages = "2020-01-01T17:18:19.1234567Z",
            },
        },
        ResourceGroupName = "testrg",
        Tags = 
        {
            { "mytag", "myval" },
        },
    });

});


```

```go
package main

import (
	azurearcdata "github.com/pulumi/pulumi-azure-native-sdk/azurearcdata"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azurearcdata.NewDataController(ctx, "dataController", &azurearcdata.DataControllerArgs{
			DataControllerName: pulumi.String("testdataController"),
			ExtendedLocation: &azurearcdata.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation"),
				Type: pulumi.String("CustomLocation"),
			},
			Location: pulumi.String("northeurope"),
			Properties: azurearcdata.DataControllerPropertiesResponse{
				BasicLoginInformation: &azurearcdata.BasicLoginInformationArgs{
					Password: pulumi.String("********"),
					Username: pulumi.String("username"),
				},
				ClusterId:      pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s"),
				ExtensionId:    pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s/providers/Microsoft.KubernetesConfiguration/extensions/extension"),
				Infrastructure: azurearcdata.InfrastructureOnpremises,
				LogAnalyticsWorkspaceConfig: &azurearcdata.LogAnalyticsWorkspaceConfigArgs{
					PrimaryKey:  pulumi.String("********"),
					WorkspaceId: pulumi.String("00000000-1111-2222-3333-444444444444"),
				},
				LogsDashboardCredential: &azurearcdata.BasicLoginInformationArgs{
					Password: pulumi.String("********"),
					Username: pulumi.String("username"),
				},
				MetricsDashboardCredential: &azurearcdata.BasicLoginInformationArgs{
					Password: pulumi.String("********"),
					Username: pulumi.String("username"),
				},
				OnPremiseProperty: &azurearcdata.OnPremisePropertyArgs{
					Id:               pulumi.String("12345678-1234-1234-ab12-1a2b3c4d5e6f"),
					PublicSigningKey: pulumi.String("publicOnPremSigningKey"),
				},
				UploadServicePrincipal: &azurearcdata.UploadServicePrincipalArgs{
					Authority:    pulumi.String("https://login.microsoftonline.com/"),
					ClientId:     pulumi.String("00000000-1111-2222-3333-444444444444"),
					ClientSecret: pulumi.String("********"),
					TenantId:     pulumi.String("00000000-1111-2222-3333-444444444444"),
				},
				UploadWatermark: &azurearcdata.UploadWatermarkArgs{
					Logs:    pulumi.String("2020-01-01T17:18:19.1234567Z"),
					Metrics: pulumi.String("2020-01-01T17:18:19.1234567Z"),
					Usages:  pulumi.String("2020-01-01T17:18:19.1234567Z"),
				},
			},
			ResourceGroupName: pulumi.String("testrg"),
			Tags: pulumi.StringMap{
				"mytag": pulumi.String("myval"),
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
import com.pulumi.azurenative.azurearcdata.DataController;
import com.pulumi.azurenative.azurearcdata.DataControllerArgs;
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
        var dataController = new DataController("dataController", DataControllerArgs.builder()        
            .dataControllerName("testdataController")
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation"),
                Map.entry("type", "CustomLocation")
            ))
            .location("northeurope")
            .properties(Map.ofEntries(
                Map.entry("basicLoginInformation", Map.ofEntries(
                    Map.entry("password", "********"),
                    Map.entry("username", "username")
                )),
                Map.entry("clusterId", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s"),
                Map.entry("extensionId", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s/providers/Microsoft.KubernetesConfiguration/extensions/extension"),
                Map.entry("infrastructure", "onpremises"),
                Map.entry("logAnalyticsWorkspaceConfig", Map.ofEntries(
                    Map.entry("primaryKey", "********"),
                    Map.entry("workspaceId", "00000000-1111-2222-3333-444444444444")
                )),
                Map.entry("logsDashboardCredential", Map.ofEntries(
                    Map.entry("password", "********"),
                    Map.entry("username", "username")
                )),
                Map.entry("metricsDashboardCredential", Map.ofEntries(
                    Map.entry("password", "********"),
                    Map.entry("username", "username")
                )),
                Map.entry("onPremiseProperty", Map.ofEntries(
                    Map.entry("id", "12345678-1234-1234-ab12-1a2b3c4d5e6f"),
                    Map.entry("publicSigningKey", "publicOnPremSigningKey")
                )),
                Map.entry("uploadServicePrincipal", Map.ofEntries(
                    Map.entry("authority", "https://login.microsoftonline.com/"),
                    Map.entry("clientId", "00000000-1111-2222-3333-444444444444"),
                    Map.entry("clientSecret", "********"),
                    Map.entry("tenantId", "00000000-1111-2222-3333-444444444444")
                )),
                Map.entry("uploadWatermark", Map.ofEntries(
                    Map.entry("logs", "2020-01-01T17:18:19.1234567Z"),
                    Map.entry("metrics", "2020-01-01T17:18:19.1234567Z"),
                    Map.entry("usages", "2020-01-01T17:18:19.1234567Z")
                ))
            ))
            .resourceGroupName("testrg")
            .tags(Map.of("mytag", "myval"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataController = new azure_native.azurearcdata.DataController("dataController", {
    dataControllerName: "testdataController",
    extendedLocation: {
        name: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation",
        type: "CustomLocation",
    },
    location: "northeurope",
    properties: {
        basicLoginInformation: {
            password: "********",
            username: "username",
        },
        clusterId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s",
        extensionId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s/providers/Microsoft.KubernetesConfiguration/extensions/extension",
        infrastructure: azure_native.azurearcdata.Infrastructure.Onpremises,
        logAnalyticsWorkspaceConfig: {
            primaryKey: "********",
            workspaceId: "00000000-1111-2222-3333-444444444444",
        },
        logsDashboardCredential: {
            password: "********",
            username: "username",
        },
        metricsDashboardCredential: {
            password: "********",
            username: "username",
        },
        onPremiseProperty: {
            id: "12345678-1234-1234-ab12-1a2b3c4d5e6f",
            publicSigningKey: "publicOnPremSigningKey",
        },
        uploadServicePrincipal: {
            authority: "https://login.microsoftonline.com/",
            clientId: "00000000-1111-2222-3333-444444444444",
            clientSecret: "********",
            tenantId: "00000000-1111-2222-3333-444444444444",
        },
        uploadWatermark: {
            logs: "2020-01-01T17:18:19.1234567Z",
            metrics: "2020-01-01T17:18:19.1234567Z",
            usages: "2020-01-01T17:18:19.1234567Z",
        },
    },
    resourceGroupName: "testrg",
    tags: {
        mytag: "myval",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

data_controller = azure_native.azurearcdata.DataController("dataController",
    data_controller_name="testdataController",
    extended_location=azure_native.azurearcdata.ExtendedLocationArgs(
        name="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation",
        type="CustomLocation",
    ),
    location="northeurope",
    properties=azure_native.azurearcdata.DataControllerPropertiesResponseArgs(
        basic_login_information=azure_native.azurearcdata.BasicLoginInformationArgs(
            password="********",
            username="username",
        ),
        cluster_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s",
        extension_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s/providers/Microsoft.KubernetesConfiguration/extensions/extension",
        infrastructure=azure_native.azurearcdata.Infrastructure.ONPREMISES,
        log_analytics_workspace_config=azure_native.azurearcdata.LogAnalyticsWorkspaceConfigArgs(
            primary_key="********",
            workspace_id="00000000-1111-2222-3333-444444444444",
        ),
        logs_dashboard_credential=azure_native.azurearcdata.BasicLoginInformationArgs(
            password="********",
            username="username",
        ),
        metrics_dashboard_credential=azure_native.azurearcdata.BasicLoginInformationArgs(
            password="********",
            username="username",
        ),
        on_premise_property=azure_native.azurearcdata.OnPremisePropertyArgs(
            id="12345678-1234-1234-ab12-1a2b3c4d5e6f",
            public_signing_key="publicOnPremSigningKey",
        ),
        upload_service_principal=azure_native.azurearcdata.UploadServicePrincipalArgs(
            authority="https://login.microsoftonline.com/",
            client_id="00000000-1111-2222-3333-444444444444",
            client_secret="********",
            tenant_id="00000000-1111-2222-3333-444444444444",
        ),
        upload_watermark=azure_native.azurearcdata.UploadWatermarkArgs(
            logs="2020-01-01T17:18:19.1234567Z",
            metrics="2020-01-01T17:18:19.1234567Z",
            usages="2020-01-01T17:18:19.1234567Z",
        ),
    ),
    resource_group_name="testrg",
    tags={
        "mytag": "myval",
    })

```

```yaml
resources:
  dataController:
    type: azure-native:azurearcdata:DataController
    properties:
      dataControllerName: testdataController
      extendedLocation:
        name: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation
        type: CustomLocation
      location: northeurope
      properties:
        basicLoginInformation:
          password: '********'
          username: username
        clusterId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s
        extensionId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s/providers/Microsoft.KubernetesConfiguration/extensions/extension
        infrastructure: onpremises
        logAnalyticsWorkspaceConfig:
          primaryKey: '********'
          workspaceId: 00000000-1111-2222-3333-444444444444
        logsDashboardCredential:
          password: '********'
          username: username
        metricsDashboardCredential:
          password: '********'
          username: username
        onPremiseProperty:
          id: 12345678-1234-1234-ab12-1a2b3c4d5e6f
          publicSigningKey: publicOnPremSigningKey
        uploadServicePrincipal:
          authority: https://login.microsoftonline.com/
          clientId: 00000000-1111-2222-3333-444444444444
          clientSecret: '********'
          tenantId: 00000000-1111-2222-3333-444444444444
        uploadWatermark:
          logs: 2020-01-01T17:18:19.1234567Z
          metrics: 2020-01-01T17:18:19.1234567Z
          usages: 2020-01-01T17:18:19.1234567Z
      resourceGroupName: testrg
      tags:
        mytag: myval

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurearcdata:DataController testdataController /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/dataControllers/testdataController 
```
