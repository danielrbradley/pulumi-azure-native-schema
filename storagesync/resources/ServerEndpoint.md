Server Endpoint object.
API Version: 2022-06-01.
Previous API Version: 2020-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ServerEndpoints_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serverEndpoint = new AzureNative.StorageSync.ServerEndpoint("serverEndpoint", new()
    {
        CloudTiering = "off",
        InitialDownloadPolicy = "NamespaceThenModifiedFiles",
        InitialUploadPolicy = "ServerAuthoritative",
        LocalCacheMode = "UpdateLocallyCachedFiles",
        OfflineDataTransfer = "on",
        OfflineDataTransferShareName = "myfileshare",
        ResourceGroupName = "SampleResourceGroup_1",
        ServerEndpointName = "SampleServerEndpoint_1",
        ServerLocalPath = "D:\\SampleServerEndpoint_1",
        ServerResourceId = "/subscriptions/52b8da2f-61e0-4a1f-8dde-336911f367fb/resourceGroups/SampleResourceGroup_1/providers/Microsoft.StorageSync/storageSyncServices/SampleStorageSyncService_1/registeredServers/080d4133-bdb5-40a0-96a0-71a6057bfe9a",
        StorageSyncServiceName = "SampleStorageSyncService_1",
        SyncGroupName = "SampleSyncGroup_1",
        TierFilesOlderThanDays = 0,
        VolumeFreeSpacePercent = 100,
    });

});


```

```go
package main

import (
	storagesync "github.com/pulumi/pulumi-azure-native-sdk/storagesync"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storagesync.NewServerEndpoint(ctx, "serverEndpoint", &storagesync.ServerEndpointArgs{
			CloudTiering:                 pulumi.String("off"),
			InitialDownloadPolicy:        pulumi.String("NamespaceThenModifiedFiles"),
			InitialUploadPolicy:          pulumi.String("ServerAuthoritative"),
			LocalCacheMode:               pulumi.String("UpdateLocallyCachedFiles"),
			OfflineDataTransfer:          pulumi.String("on"),
			OfflineDataTransferShareName: pulumi.String("myfileshare"),
			ResourceGroupName:            pulumi.String("SampleResourceGroup_1"),
			ServerEndpointName:           pulumi.String("SampleServerEndpoint_1"),
			ServerLocalPath:              pulumi.String("D:\\SampleServerEndpoint_1"),
			ServerResourceId:             pulumi.String("/subscriptions/52b8da2f-61e0-4a1f-8dde-336911f367fb/resourceGroups/SampleResourceGroup_1/providers/Microsoft.StorageSync/storageSyncServices/SampleStorageSyncService_1/registeredServers/080d4133-bdb5-40a0-96a0-71a6057bfe9a"),
			StorageSyncServiceName:       pulumi.String("SampleStorageSyncService_1"),
			SyncGroupName:                pulumi.String("SampleSyncGroup_1"),
			TierFilesOlderThanDays:       pulumi.Int(0),
			VolumeFreeSpacePercent:       pulumi.Int(100),
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
import com.pulumi.azurenative.storagesync.ServerEndpoint;
import com.pulumi.azurenative.storagesync.ServerEndpointArgs;
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
        var serverEndpoint = new ServerEndpoint("serverEndpoint", ServerEndpointArgs.builder()        
            .cloudTiering("off")
            .initialDownloadPolicy("NamespaceThenModifiedFiles")
            .initialUploadPolicy("ServerAuthoritative")
            .localCacheMode("UpdateLocallyCachedFiles")
            .offlineDataTransfer("on")
            .offlineDataTransferShareName("myfileshare")
            .resourceGroupName("SampleResourceGroup_1")
            .serverEndpointName("SampleServerEndpoint_1")
            .serverLocalPath("D:\\SampleServerEndpoint_1")
            .serverResourceId("/subscriptions/52b8da2f-61e0-4a1f-8dde-336911f367fb/resourceGroups/SampleResourceGroup_1/providers/Microsoft.StorageSync/storageSyncServices/SampleStorageSyncService_1/registeredServers/080d4133-bdb5-40a0-96a0-71a6057bfe9a")
            .storageSyncServiceName("SampleStorageSyncService_1")
            .syncGroupName("SampleSyncGroup_1")
            .tierFilesOlderThanDays(0)
            .volumeFreeSpacePercent(100)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverEndpoint = new azure_native.storagesync.ServerEndpoint("serverEndpoint", {
    cloudTiering: "off",
    initialDownloadPolicy: "NamespaceThenModifiedFiles",
    initialUploadPolicy: "ServerAuthoritative",
    localCacheMode: "UpdateLocallyCachedFiles",
    offlineDataTransfer: "on",
    offlineDataTransferShareName: "myfileshare",
    resourceGroupName: "SampleResourceGroup_1",
    serverEndpointName: "SampleServerEndpoint_1",
    serverLocalPath: "D:\\SampleServerEndpoint_1",
    serverResourceId: "/subscriptions/52b8da2f-61e0-4a1f-8dde-336911f367fb/resourceGroups/SampleResourceGroup_1/providers/Microsoft.StorageSync/storageSyncServices/SampleStorageSyncService_1/registeredServers/080d4133-bdb5-40a0-96a0-71a6057bfe9a",
    storageSyncServiceName: "SampleStorageSyncService_1",
    syncGroupName: "SampleSyncGroup_1",
    tierFilesOlderThanDays: 0,
    volumeFreeSpacePercent: 100,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_endpoint = azure_native.storagesync.ServerEndpoint("serverEndpoint",
    cloud_tiering="off",
    initial_download_policy="NamespaceThenModifiedFiles",
    initial_upload_policy="ServerAuthoritative",
    local_cache_mode="UpdateLocallyCachedFiles",
    offline_data_transfer="on",
    offline_data_transfer_share_name="myfileshare",
    resource_group_name="SampleResourceGroup_1",
    server_endpoint_name="SampleServerEndpoint_1",
    server_local_path="D:\\SampleServerEndpoint_1",
    server_resource_id="/subscriptions/52b8da2f-61e0-4a1f-8dde-336911f367fb/resourceGroups/SampleResourceGroup_1/providers/Microsoft.StorageSync/storageSyncServices/SampleStorageSyncService_1/registeredServers/080d4133-bdb5-40a0-96a0-71a6057bfe9a",
    storage_sync_service_name="SampleStorageSyncService_1",
    sync_group_name="SampleSyncGroup_1",
    tier_files_older_than_days=0,
    volume_free_space_percent=100)

```

```yaml
resources:
  serverEndpoint:
    type: azure-native:storagesync:ServerEndpoint
    properties:
      cloudTiering: off
      initialDownloadPolicy: NamespaceThenModifiedFiles
      initialUploadPolicy: ServerAuthoritative
      localCacheMode: UpdateLocallyCachedFiles
      offlineDataTransfer: on
      offlineDataTransferShareName: myfileshare
      resourceGroupName: SampleResourceGroup_1
      serverEndpointName: SampleServerEndpoint_1
      serverLocalPath: D:\SampleServerEndpoint_1
      serverResourceId: /subscriptions/52b8da2f-61e0-4a1f-8dde-336911f367fb/resourceGroups/SampleResourceGroup_1/providers/Microsoft.StorageSync/storageSyncServices/SampleStorageSyncService_1/registeredServers/080d4133-bdb5-40a0-96a0-71a6057bfe9a
      storageSyncServiceName: SampleStorageSyncService_1
      syncGroupName: SampleSyncGroup_1
      tierFilesOlderThanDays: 0
      volumeFreeSpacePercent: 100

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storagesync:ServerEndpoint SampleServerEndpoint_1 /subscriptions/52b8da2f-61e0-4a1f-8dde-336911f367fb/resourceGroups/SampleResourceGroup_1/providers/Microsoft.StorageSync/storageSyncServices/SampleStorageSyncService_1/syncGroups/SampleSyncGroup_1/serverEndpoints/SampleServerEndpoint_1 
```
