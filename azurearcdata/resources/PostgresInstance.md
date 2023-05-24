A Postgres Instance.
API Version: 2023-03-15-preview.
Previous API Version: 2021-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a Postgres Instance.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var postgresInstance = new AzureNative.AzureArcData.PostgresInstance("postgresInstance", new()
    {
        ExtendedLocation = new AzureNative.AzureArcData.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation",
            Type = "CustomLocation",
        },
        Location = "eastus",
        PostgresInstanceName = "testpostgresInstance",
        Properties = new AzureNative.AzureArcData.Inputs.PostgresInstancePropertiesArgs
        {
            Admin = "admin",
            BasicLoginInformation = new AzureNative.AzureArcData.Inputs.BasicLoginInformationArgs
            {
                Password = "********",
                Username = "username",
            },
            DataControllerId = "dataControllerId",
            K8sRaw = 
            {
                { "apiVersion", "apiVersion" },
                { "kind", "postgresql-12" },
                { "metadata", 
                {
                    { "creationTimestamp", "2020-08-25T14:55:10Z" },
                    { "generation", 1 },
                    { "name", "pg1" },
                    { "namespace", "test" },
                    { "resourceVersion", "527780" },
                    { "selfLink", "/apis/arcdata.microsoft.com/v1alpha1/namespaces/test/postgresql-12s/pg1" },
                    { "uid", "1111aaaa-ffff-ffff-ffff-99999aaaaaaa" },
                } },
                { "spec", 
                {
                    { "backups", 
                    {
                        { "deltaMinutes", 3 },
                        { "fullMinutes", 10 },
                        { "tiers", new[]
                        {
                            
                            {
                                { "retention", 
                                {
                                    { "maximums", new[]
                                    {
                                        "6",
                                        "512MB",
                                    } },
                                    { "minimums", new[]
                                    {
                                        "3",
                                    } },
                                } },
                                { "storage", 
                                {
                                    { "volumeSize", "1Gi" },
                                } },
                            },
                        } },
                    } },
                    { "engine", 
                    {
                        { "extensions", new[]
                        {
                            
                            {
                                { "name", "citus" },
                            },
                        } },
                    } },
                    { "scale", 
                    {
                        { "shards", 3 },
                    } },
                    { "scheduling", 
                    {
                        { "default", 
                        {
                            { "resources", 
                            {
                                { "requests", 
                                {
                                    { "memory", "256Mi" },
                                } },
                            } },
                        } },
                    } },
                    { "service", 
                    {
                        { "type", "NodePort" },
                    } },
                    { "storage", 
                    {
                        { "data", 
                        {
                            { "className", "local-storage" },
                            { "size", "5Gi" },
                        } },
                        { "logs", 
                        {
                            { "className", "local-storage" },
                            { "size", "5Gi" },
                        } },
                    } },
                } },
                { "status", 
                {
                    { "externalEndpoint", null },
                    { "readyPods", "4/4" },
                    { "state", "Ready" },
                } },
            },
        },
        ResourceGroupName = "testrg",
        Sku = new AzureNative.AzureArcData.Inputs.PostgresInstanceSkuArgs
        {
            Dev = true,
            Name = "default",
            Tier = AzureNative.AzureArcData.PostgresInstanceSkuTier.Hyperscale,
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
		_, err := azurearcdata.NewPostgresInstance(ctx, "postgresInstance", &azurearcdata.PostgresInstanceArgs{
			ExtendedLocation: &azurearcdata.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation"),
				Type: pulumi.String("CustomLocation"),
			},
			Location:             pulumi.String("eastus"),
			PostgresInstanceName: pulumi.String("testpostgresInstance"),
			Properties: azurearcdata.PostgresInstancePropertiesResponse{
				Admin: pulumi.String("admin"),
				BasicLoginInformation: &azurearcdata.BasicLoginInformationArgs{
					Password: pulumi.String("********"),
					Username: pulumi.String("username"),
				},
				DataControllerId: pulumi.String("dataControllerId"),
				K8sRaw: pulumi.Any{
					ApiVersion: "apiVersion",
					Kind:       "postgresql-12",
					Metadata: map[string]interface{}{
						"creationTimestamp": "2020-08-25T14:55:10Z",
						"generation":        1,
						"name":              "pg1",
						"namespace":         "test",
						"resourceVersion":   "527780",
						"selfLink":          "/apis/arcdata.microsoft.com/v1alpha1/namespaces/test/postgresql-12s/pg1",
						"uid":               "1111aaaa-ffff-ffff-ffff-99999aaaaaaa",
					},
					Spec: map[string]interface{}{
						"backups": map[string]interface{}{
							"deltaMinutes": 3,
							"fullMinutes":  10,
							"tiers": []map[string]interface{}{
								map[string]interface{}{
									"retention": map[string]interface{}{
										"maximums": []string{
											"6",
											"512MB",
										},
										"minimums": []string{
											"3",
										},
									},
									"storage": map[string]interface{}{
										"volumeSize": "1Gi",
									},
								},
							},
						},
						"engine": map[string]interface{}{
							"extensions": []map[string]interface{}{
								map[string]interface{}{
									"name": "citus",
								},
							},
						},
						"scale": map[string]interface{}{
							"shards": 3,
						},
						"scheduling": map[string]interface{}{
							"default": map[string]interface{}{
								"resources": map[string]interface{}{
									"requests": map[string]interface{}{
										"memory": "256Mi",
									},
								},
							},
						},
						"service": map[string]interface{}{
							"type": "NodePort",
						},
						"storage": map[string]interface{}{
							"data": map[string]interface{}{
								"className": "local-storage",
								"size":      "5Gi",
							},
							"logs": map[string]interface{}{
								"className": "local-storage",
								"size":      "5Gi",
							},
						},
					},
					Status: map[string]interface{}{
						"externalEndpoint": nil,
						"readyPods":        "4/4",
						"state":            "Ready",
					},
				},
			},
			ResourceGroupName: pulumi.String("testrg"),
			Sku: &azurearcdata.PostgresInstanceSkuArgs{
				Dev:  pulumi.Bool(true),
				Name: pulumi.String("default"),
				Tier: azurearcdata.PostgresInstanceSkuTierHyperscale,
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
import com.pulumi.azurenative.azurearcdata.PostgresInstance;
import com.pulumi.azurenative.azurearcdata.PostgresInstanceArgs;
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
        var postgresInstance = new PostgresInstance("postgresInstance", PostgresInstanceArgs.builder()        
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation"),
                Map.entry("type", "CustomLocation")
            ))
            .location("eastus")
            .postgresInstanceName("testpostgresInstance")
            .properties(Map.ofEntries(
                Map.entry("admin", "admin"),
                Map.entry("basicLoginInformation", Map.ofEntries(
                    Map.entry("password", "********"),
                    Map.entry("username", "username")
                )),
                Map.entry("dataControllerId", "dataControllerId"),
                Map.entry("k8sRaw", Map.ofEntries(
                    Map.entry("apiVersion", "apiVersion"),
                    Map.entry("kind", "postgresql-12"),
                    Map.entry("metadata", PostgresInstancePropertiesArgs.builder()
                        .creationTimestamp("2020-08-25T14:55:10Z")
                        .generation(1)
                        .name("pg1")
                        .namespace("test")
                        .resourceVersion("527780")
                        .selfLink("/apis/arcdata.microsoft.com/v1alpha1/namespaces/test/postgresql-12s/pg1")
                        .uid("1111aaaa-ffff-ffff-ffff-99999aaaaaaa")
                        .build()),
                    Map.entry("spec", PostgresInstancePropertiesArgs.builder()
                        .backups(%!v(PANIC=Format method: runtime error: invalid memory address or nil pointer dereference))
                        .engine(%!v(PANIC=Format method: runtime error: invalid memory address or nil pointer dereference))
                        .scale(%!v(PANIC=Format method: runtime error: invalid memory address or nil pointer dereference))
                        .scheduling(%!v(PANIC=Format method: runtime error: invalid memory address or nil pointer dereference))
                        .service(%!v(PANIC=Format method: runtime error: invalid memory address or nil pointer dereference))
                        .storage(%!v(PANIC=Format method: runtime error: invalid memory address or nil pointer dereference))
                        .build()),
                    Map.entry("status", PostgresInstancePropertiesArgs.builder()
                        .externalEndpoint(null)
                        .readyPods("4/4")
                        .state("Ready")
                        .build())
                ))
            ))
            .resourceGroupName("testrg")
            .sku(Map.ofEntries(
                Map.entry("dev", true),
                Map.entry("name", "default"),
                Map.entry("tier", "Hyperscale")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const postgresInstance = new azure_native.azurearcdata.PostgresInstance("postgresInstance", {
    extendedLocation: {
        name: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation",
        type: "CustomLocation",
    },
    location: "eastus",
    postgresInstanceName: "testpostgresInstance",
    properties: {
        admin: "admin",
        basicLoginInformation: {
            password: "********",
            username: "username",
        },
        dataControllerId: "dataControllerId",
        k8sRaw: {
            apiVersion: "apiVersion",
            kind: "postgresql-12",
            metadata: {
                creationTimestamp: "2020-08-25T14:55:10Z",
                generation: 1,
                name: "pg1",
                namespace: "test",
                resourceVersion: "527780",
                selfLink: "/apis/arcdata.microsoft.com/v1alpha1/namespaces/test/postgresql-12s/pg1",
                uid: "1111aaaa-ffff-ffff-ffff-99999aaaaaaa",
            },
            spec: {
                backups: {
                    deltaMinutes: 3,
                    fullMinutes: 10,
                    tiers: [{
                        retention: {
                            maximums: [
                                "6",
                                "512MB",
                            ],
                            minimums: ["3"],
                        },
                        storage: {
                            volumeSize: "1Gi",
                        },
                    }],
                },
                engine: {
                    extensions: [{
                        name: "citus",
                    }],
                },
                scale: {
                    shards: 3,
                },
                scheduling: {
                    "default": {
                        resources: {
                            requests: {
                                memory: "256Mi",
                            },
                        },
                    },
                },
                service: {
                    type: "NodePort",
                },
                storage: {
                    data: {
                        className: "local-storage",
                        size: "5Gi",
                    },
                    logs: {
                        className: "local-storage",
                        size: "5Gi",
                    },
                },
            },
            status: {
                externalEndpoint: undefined,
                readyPods: "4/4",
                state: "Ready",
            },
        },
    },
    resourceGroupName: "testrg",
    sku: {
        dev: true,
        name: "default",
        tier: azure_native.azurearcdata.PostgresInstanceSkuTier.Hyperscale,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

postgres_instance = azure_native.azurearcdata.PostgresInstance("postgresInstance",
    extended_location=azure_native.azurearcdata.ExtendedLocationArgs(
        name="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation",
        type="CustomLocation",
    ),
    location="eastus",
    postgres_instance_name="testpostgresInstance",
    properties=azure_native.azurearcdata.PostgresInstancePropertiesResponseArgs(
        admin="admin",
        basic_login_information=azure_native.azurearcdata.BasicLoginInformationArgs(
            password="********",
            username="username",
        ),
        data_controller_id="dataControllerId",
        k8s_raw={
            "apiVersion": "apiVersion",
            "kind": "postgresql-12",
            "metadata": {
                "creationTimestamp": "2020-08-25T14:55:10Z",
                "generation": 1,
                "name": "pg1",
                "namespace": "test",
                "resourceVersion": "527780",
                "selfLink": "/apis/arcdata.microsoft.com/v1alpha1/namespaces/test/postgresql-12s/pg1",
                "uid": "1111aaaa-ffff-ffff-ffff-99999aaaaaaa",
            },
            "spec": {
                "backups": {
                    "deltaMinutes": 3,
                    "fullMinutes": 10,
                    "tiers": [{
                        "retention": {
                            "maximums": [
                                "6",
                                "512MB",
                            ],
                            "minimums": ["3"],
                        },
                        "storage": {
                            "volumeSize": "1Gi",
                        },
                    }],
                },
                "engine": {
                    "extensions": [{
                        "name": "citus",
                    }],
                },
                "scale": {
                    "shards": 3,
                },
                "scheduling": {
                    "default": {
                        "resources": {
                            "requests": {
                                "memory": "256Mi",
                            },
                        },
                    },
                },
                "service": {
                    "type": "NodePort",
                },
                "storage": {
                    "data": {
                        "className": "local-storage",
                        "size": "5Gi",
                    },
                    "logs": {
                        "className": "local-storage",
                        "size": "5Gi",
                    },
                },
            },
            "status": {
                "externalEndpoint": None,
                "readyPods": "4/4",
                "state": "Ready",
            },
        },
    ),
    resource_group_name="testrg",
    sku=azure_native.azurearcdata.PostgresInstanceSkuArgs(
        dev=True,
        name="default",
        tier=azure_native.azurearcdata.PostgresInstanceSkuTier.HYPERSCALE,
    ))

```

```yaml
resources:
  postgresInstance:
    type: azure-native:azurearcdata:PostgresInstance
    properties:
      extendedLocation:
        name: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation
        type: CustomLocation
      location: eastus
      postgresInstanceName: testpostgresInstance
      properties:
        admin: admin
        basicLoginInformation:
          password: '********'
          username: username
        dataControllerId: dataControllerId
        k8sRaw:
          apiVersion: apiVersion
          kind: postgresql-12
          metadata:
            creationTimestamp: 2020-08-25T14:55:10Z
            generation: 1
            name: pg1
            namespace: test
            resourceVersion: '527780'
            selfLink: /apis/arcdata.microsoft.com/v1alpha1/namespaces/test/postgresql-12s/pg1
            uid: 1111aaaa-ffff-ffff-ffff-99999aaaaaaa
          spec:
            backups:
              deltaMinutes: 3
              fullMinutes: 10
              tiers:
                - retention:
                    maximums:
                      - '6'
                      - 512MB
                    minimums:
                      - '3'
                  storage:
                    volumeSize: 1Gi
            engine:
              extensions:
                - name: citus
            scale:
              shards: 3
            scheduling:
              default:
                resources:
                  requests:
                    memory: 256Mi
            service:
              type: NodePort
            storage:
              data:
                className: local-storage
                size: 5Gi
              logs:
                className: local-storage
                size: 5Gi
          status:
            externalEndpoint: null
            readyPods: 4/4
            state: Ready
      resourceGroupName: testrg
      sku:
        dev: true
        name: default
        tier: Hyperscale

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurearcdata:PostgresInstance testpostgresInstance /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/PostgresInstance/testpostgresInstance 
```
