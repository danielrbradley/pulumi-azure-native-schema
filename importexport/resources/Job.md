Contains the job information.
API Version: 2021-01-01.
Previous API Version: 2020-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create export job
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var job = new AzureNative.ImportExport.Job("job", new()
    {
        JobName = "myExportJob",
        Location = "West US",
        Properties = new AzureNative.ImportExport.Inputs.JobDetailsArgs
        {
            BackupDriveManifest = true,
            DiagnosticsPath = "waimportexport",
            Export = new AzureNative.ImportExport.Inputs.ExportArgs
            {
                BlobPathPrefix = new[]
                {
                    "/",
                },
            },
            JobType = "Export",
            LogLevel = "Verbose",
            ReturnAddress = new AzureNative.ImportExport.Inputs.ReturnAddressArgs
            {
                City = "Redmond",
                CountryOrRegion = "USA",
                Email = "Test@contoso.com",
                Phone = "4250000000",
                PostalCode = "98007",
                RecipientName = "Test",
                StateOrProvince = "wa",
                StreetAddress1 = "Street1",
                StreetAddress2 = "street2",
            },
            ReturnShipping = new AzureNative.ImportExport.Inputs.ReturnShippingArgs
            {
                CarrierAccountNumber = "989ffff",
                CarrierName = "FedEx",
            },
            StorageAccountId = "/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.ClassicStorage/storageAccounts/test",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	importexport "github.com/pulumi/pulumi-azure-native-sdk/importexport"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := importexport.NewJob(ctx, "job", &importexport.JobArgs{
			JobName:  pulumi.String("myExportJob"),
			Location: pulumi.String("West US"),
			Properties: importexport.JobDetailsResponse{
				BackupDriveManifest: pulumi.Bool(true),
				DiagnosticsPath:     pulumi.String("waimportexport"),
				Export: &importexport.ExportArgs{
					BlobPathPrefix: pulumi.StringArray{
						pulumi.String("/"),
					},
				},
				JobType:  pulumi.String("Export"),
				LogLevel: pulumi.String("Verbose"),
				ReturnAddress: &importexport.ReturnAddressArgs{
					City:            pulumi.String("Redmond"),
					CountryOrRegion: pulumi.String("USA"),
					Email:           pulumi.String("Test@contoso.com"),
					Phone:           pulumi.String("4250000000"),
					PostalCode:      pulumi.String("98007"),
					RecipientName:   pulumi.String("Test"),
					StateOrProvince: pulumi.String("wa"),
					StreetAddress1:  pulumi.String("Street1"),
					StreetAddress2:  pulumi.String("street2"),
				},
				ReturnShipping: &importexport.ReturnShippingArgs{
					CarrierAccountNumber: pulumi.String("989ffff"),
					CarrierName:          pulumi.String("FedEx"),
				},
				StorageAccountId: pulumi.String("/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.ClassicStorage/storageAccounts/test"),
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
import com.pulumi.azurenative.importexport.Job;
import com.pulumi.azurenative.importexport.JobArgs;
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
        var job = new Job("job", JobArgs.builder()        
            .jobName("myExportJob")
            .location("West US")
            .properties(Map.ofEntries(
                Map.entry("backupDriveManifest", true),
                Map.entry("diagnosticsPath", "waimportexport"),
                Map.entry("export", Map.of("blobPathPrefix", "/")),
                Map.entry("jobType", "Export"),
                Map.entry("logLevel", "Verbose"),
                Map.entry("returnAddress", Map.ofEntries(
                    Map.entry("city", "Redmond"),
                    Map.entry("countryOrRegion", "USA"),
                    Map.entry("email", "Test@contoso.com"),
                    Map.entry("phone", "4250000000"),
                    Map.entry("postalCode", "98007"),
                    Map.entry("recipientName", "Test"),
                    Map.entry("stateOrProvince", "wa"),
                    Map.entry("streetAddress1", "Street1"),
                    Map.entry("streetAddress2", "street2")
                )),
                Map.entry("returnShipping", Map.ofEntries(
                    Map.entry("carrierAccountNumber", "989ffff"),
                    Map.entry("carrierName", "FedEx")
                )),
                Map.entry("storageAccountId", "/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.ClassicStorage/storageAccounts/test")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const job = new azure_native.importexport.Job("job", {
    jobName: "myExportJob",
    location: "West US",
    properties: {
        backupDriveManifest: true,
        diagnosticsPath: "waimportexport",
        "export": {
            blobPathPrefix: ["/"],
        },
        jobType: "Export",
        logLevel: "Verbose",
        returnAddress: {
            city: "Redmond",
            countryOrRegion: "USA",
            email: "Test@contoso.com",
            phone: "4250000000",
            postalCode: "98007",
            recipientName: "Test",
            stateOrProvince: "wa",
            streetAddress1: "Street1",
            streetAddress2: "street2",
        },
        returnShipping: {
            carrierAccountNumber: "989ffff",
            carrierName: "FedEx",
        },
        storageAccountId: "/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.ClassicStorage/storageAccounts/test",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job = azure_native.importexport.Job("job",
    job_name="myExportJob",
    location="West US",
    properties=azure_native.importexport.JobDetailsResponseArgs(
        backup_drive_manifest=True,
        diagnostics_path="waimportexport",
        export=azure_native.importexport.ExportArgs(
            blob_path_prefix=["/"],
        ),
        job_type="Export",
        log_level="Verbose",
        return_address=azure_native.importexport.ReturnAddressArgs(
            city="Redmond",
            country_or_region="USA",
            email="Test@contoso.com",
            phone="4250000000",
            postal_code="98007",
            recipient_name="Test",
            state_or_province="wa",
            street_address1="Street1",
            street_address2="street2",
        ),
        return_shipping=azure_native.importexport.ReturnShippingArgs(
            carrier_account_number="989ffff",
            carrier_name="FedEx",
        ),
        storage_account_id="/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.ClassicStorage/storageAccounts/test",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  job:
    type: azure-native:importexport:Job
    properties:
      jobName: myExportJob
      location: West US
      properties:
        backupDriveManifest: true
        diagnosticsPath: waimportexport
        export:
          blobPathPrefix:
            - /
        jobType: Export
        logLevel: Verbose
        returnAddress:
          city: Redmond
          countryOrRegion: USA
          email: Test@contoso.com
          phone: '4250000000'
          postalCode: '98007'
          recipientName: Test
          stateOrProvince: wa
          streetAddress1: Street1
          streetAddress2: street2
        returnShipping:
          carrierAccountNumber: 989ffff
          carrierName: FedEx
        storageAccountId: /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.ClassicStorage/storageAccounts/test
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create import job
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var job = new AzureNative.ImportExport.Job("job", new()
    {
        JobName = "myJob",
        Location = "West US",
        Properties = new AzureNative.ImportExport.Inputs.JobDetailsArgs
        {
            BackupDriveManifest = true,
            DiagnosticsPath = "waimportexport",
            DriveList = new[]
            {
                new AzureNative.ImportExport.Inputs.DriveStatusArgs
                {
                    BitLockerKey = "238810-662376-448998-450120-652806-203390-606320-483076",
                    DriveHeaderHash = "0:1048576:FB6B6ED500D49DA6E0D723C98D42C657F2881CC13357C28DCECA6A524F1292501571A321238540E621AB5BD9C9A32637615919A75593E6CB5C1515DAE341CABF;135266304:143360:C957A189AFC38C4E80731252301EB91427CE55E61448FA3C73C6FDDE70ABBC197947EC8D0249A2C639BB10B95957D5820A4BE8DFBBF76FFFA688AE5CE0D42EC3",
                    DriveId = "9CA995BB",
                    ManifestFile = "\\8a0c23f7-14b7-470a-9633-fcd46590a1bc.manifest",
                    ManifestHash = "4228EC5D8E048CB9B515338C789314BE8D0B2FDBC7C7A0308E1C826242CDE74E",
                },
            },
            JobType = "Import",
            LogLevel = "Verbose",
            ReturnAddress = new AzureNative.ImportExport.Inputs.ReturnAddressArgs
            {
                City = "Redmond",
                CountryOrRegion = "USA",
                Email = "Test@contoso.com",
                Phone = "4250000000",
                PostalCode = "98007",
                RecipientName = "Test",
                StateOrProvince = "wa",
                StreetAddress1 = "Street1",
                StreetAddress2 = "street2",
            },
            ReturnShipping = new AzureNative.ImportExport.Inputs.ReturnShippingArgs
            {
                CarrierAccountNumber = "989ffff",
                CarrierName = "FedEx",
            },
            StorageAccountId = "/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.ClassicStorage/storageAccounts/test",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	importexport "github.com/pulumi/pulumi-azure-native-sdk/importexport"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := importexport.NewJob(ctx, "job", &importexport.JobArgs{
			JobName:  pulumi.String("myJob"),
			Location: pulumi.String("West US"),
			Properties: importexport.JobDetailsResponse{
				BackupDriveManifest: pulumi.Bool(true),
				DiagnosticsPath:     pulumi.String("waimportexport"),
				DriveList: importexport.DriveStatusArray{
					&importexport.DriveStatusArgs{
						BitLockerKey:    pulumi.String("238810-662376-448998-450120-652806-203390-606320-483076"),
						DriveHeaderHash: pulumi.String("0:1048576:FB6B6ED500D49DA6E0D723C98D42C657F2881CC13357C28DCECA6A524F1292501571A321238540E621AB5BD9C9A32637615919A75593E6CB5C1515DAE341CABF;135266304:143360:C957A189AFC38C4E80731252301EB91427CE55E61448FA3C73C6FDDE70ABBC197947EC8D0249A2C639BB10B95957D5820A4BE8DFBBF76FFFA688AE5CE0D42EC3"),
						DriveId:         pulumi.String("9CA995BB"),
						ManifestFile:    pulumi.String("\\8a0c23f7-14b7-470a-9633-fcd46590a1bc.manifest"),
						ManifestHash:    pulumi.String("4228EC5D8E048CB9B515338C789314BE8D0B2FDBC7C7A0308E1C826242CDE74E"),
					},
				},
				JobType:  pulumi.String("Import"),
				LogLevel: pulumi.String("Verbose"),
				ReturnAddress: &importexport.ReturnAddressArgs{
					City:            pulumi.String("Redmond"),
					CountryOrRegion: pulumi.String("USA"),
					Email:           pulumi.String("Test@contoso.com"),
					Phone:           pulumi.String("4250000000"),
					PostalCode:      pulumi.String("98007"),
					RecipientName:   pulumi.String("Test"),
					StateOrProvince: pulumi.String("wa"),
					StreetAddress1:  pulumi.String("Street1"),
					StreetAddress2:  pulumi.String("street2"),
				},
				ReturnShipping: &importexport.ReturnShippingArgs{
					CarrierAccountNumber: pulumi.String("989ffff"),
					CarrierName:          pulumi.String("FedEx"),
				},
				StorageAccountId: pulumi.String("/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.ClassicStorage/storageAccounts/test"),
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
import com.pulumi.azurenative.importexport.Job;
import com.pulumi.azurenative.importexport.JobArgs;
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
        var job = new Job("job", JobArgs.builder()        
            .jobName("myJob")
            .location("West US")
            .properties(Map.ofEntries(
                Map.entry("backupDriveManifest", true),
                Map.entry("diagnosticsPath", "waimportexport"),
                Map.entry("driveList", Map.ofEntries(
                    Map.entry("bitLockerKey", "238810-662376-448998-450120-652806-203390-606320-483076"),
                    Map.entry("driveHeaderHash", "0:1048576:FB6B6ED500D49DA6E0D723C98D42C657F2881CC13357C28DCECA6A524F1292501571A321238540E621AB5BD9C9A32637615919A75593E6CB5C1515DAE341CABF;135266304:143360:C957A189AFC38C4E80731252301EB91427CE55E61448FA3C73C6FDDE70ABBC197947EC8D0249A2C639BB10B95957D5820A4BE8DFBBF76FFFA688AE5CE0D42EC3"),
                    Map.entry("driveId", "9CA995BB"),
                    Map.entry("manifestFile", "\\8a0c23f7-14b7-470a-9633-fcd46590a1bc.manifest"),
                    Map.entry("manifestHash", "4228EC5D8E048CB9B515338C789314BE8D0B2FDBC7C7A0308E1C826242CDE74E")
                )),
                Map.entry("jobType", "Import"),
                Map.entry("logLevel", "Verbose"),
                Map.entry("returnAddress", Map.ofEntries(
                    Map.entry("city", "Redmond"),
                    Map.entry("countryOrRegion", "USA"),
                    Map.entry("email", "Test@contoso.com"),
                    Map.entry("phone", "4250000000"),
                    Map.entry("postalCode", "98007"),
                    Map.entry("recipientName", "Test"),
                    Map.entry("stateOrProvince", "wa"),
                    Map.entry("streetAddress1", "Street1"),
                    Map.entry("streetAddress2", "street2")
                )),
                Map.entry("returnShipping", Map.ofEntries(
                    Map.entry("carrierAccountNumber", "989ffff"),
                    Map.entry("carrierName", "FedEx")
                )),
                Map.entry("storageAccountId", "/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.ClassicStorage/storageAccounts/test")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const job = new azure_native.importexport.Job("job", {
    jobName: "myJob",
    location: "West US",
    properties: {
        backupDriveManifest: true,
        diagnosticsPath: "waimportexport",
        driveList: [{
            bitLockerKey: "238810-662376-448998-450120-652806-203390-606320-483076",
            driveHeaderHash: "0:1048576:FB6B6ED500D49DA6E0D723C98D42C657F2881CC13357C28DCECA6A524F1292501571A321238540E621AB5BD9C9A32637615919A75593E6CB5C1515DAE341CABF;135266304:143360:C957A189AFC38C4E80731252301EB91427CE55E61448FA3C73C6FDDE70ABBC197947EC8D0249A2C639BB10B95957D5820A4BE8DFBBF76FFFA688AE5CE0D42EC3",
            driveId: "9CA995BB",
            manifestFile: "\\8a0c23f7-14b7-470a-9633-fcd46590a1bc.manifest",
            manifestHash: "4228EC5D8E048CB9B515338C789314BE8D0B2FDBC7C7A0308E1C826242CDE74E",
        }],
        jobType: "Import",
        logLevel: "Verbose",
        returnAddress: {
            city: "Redmond",
            countryOrRegion: "USA",
            email: "Test@contoso.com",
            phone: "4250000000",
            postalCode: "98007",
            recipientName: "Test",
            stateOrProvince: "wa",
            streetAddress1: "Street1",
            streetAddress2: "street2",
        },
        returnShipping: {
            carrierAccountNumber: "989ffff",
            carrierName: "FedEx",
        },
        storageAccountId: "/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.ClassicStorage/storageAccounts/test",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job = azure_native.importexport.Job("job",
    job_name="myJob",
    location="West US",
    properties=azure_native.importexport.JobDetailsResponseArgs(
        backup_drive_manifest=True,
        diagnostics_path="waimportexport",
        drive_list=[azure_native.importexport.DriveStatusArgs(
            bit_locker_key="238810-662376-448998-450120-652806-203390-606320-483076",
            drive_header_hash="0:1048576:FB6B6ED500D49DA6E0D723C98D42C657F2881CC13357C28DCECA6A524F1292501571A321238540E621AB5BD9C9A32637615919A75593E6CB5C1515DAE341CABF;135266304:143360:C957A189AFC38C4E80731252301EB91427CE55E61448FA3C73C6FDDE70ABBC197947EC8D0249A2C639BB10B95957D5820A4BE8DFBBF76FFFA688AE5CE0D42EC3",
            drive_id="9CA995BB",
            manifest_file="\\8a0c23f7-14b7-470a-9633-fcd46590a1bc.manifest",
            manifest_hash="4228EC5D8E048CB9B515338C789314BE8D0B2FDBC7C7A0308E1C826242CDE74E",
        )],
        job_type="Import",
        log_level="Verbose",
        return_address=azure_native.importexport.ReturnAddressArgs(
            city="Redmond",
            country_or_region="USA",
            email="Test@contoso.com",
            phone="4250000000",
            postal_code="98007",
            recipient_name="Test",
            state_or_province="wa",
            street_address1="Street1",
            street_address2="street2",
        ),
        return_shipping=azure_native.importexport.ReturnShippingArgs(
            carrier_account_number="989ffff",
            carrier_name="FedEx",
        ),
        storage_account_id="/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.ClassicStorage/storageAccounts/test",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  job:
    type: azure-native:importexport:Job
    properties:
      jobName: myJob
      location: West US
      properties:
        backupDriveManifest: true
        diagnosticsPath: waimportexport
        driveList:
          - bitLockerKey: 238810-662376-448998-450120-652806-203390-606320-483076
            driveHeaderHash: 0:1048576:FB6B6ED500D49DA6E0D723C98D42C657F2881CC13357C28DCECA6A524F1292501571A321238540E621AB5BD9C9A32637615919A75593E6CB5C1515DAE341CABF;135266304:143360:C957A189AFC38C4E80731252301EB91427CE55E61448FA3C73C6FDDE70ABBC197947EC8D0249A2C639BB10B95957D5820A4BE8DFBBF76FFFA688AE5CE0D42EC3
            driveId: 9CA995BB
            manifestFile: \8a0c23f7-14b7-470a-9633-fcd46590a1bc.manifest
            manifestHash: 4228EC5D8E048CB9B515338C789314BE8D0B2FDBC7C7A0308E1C826242CDE74E
        jobType: Import
        logLevel: Verbose
        returnAddress:
          city: Redmond
          countryOrRegion: USA
          email: Test@contoso.com
          phone: '4250000000'
          postalCode: '98007'
          recipientName: Test
          stateOrProvince: wa
          streetAddress1: Street1
          streetAddress2: street2
        returnShipping:
          carrierAccountNumber: 989ffff
          carrierName: FedEx
        storageAccountId: /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.ClassicStorage/storageAccounts/test
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:importexport:Job myJob /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.ImportExport/jobs/myJob 
```
