Job Resource.
API Version: 2022-12-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### JobsCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var job = new AzureNative.DataBox.Job("job", new()
    {
        Details = new AzureNative.DataBox.Inputs.DataBoxJobDetailsArgs
        {
            ContactDetails = new AzureNative.DataBox.Inputs.ContactDetailsArgs
            {
                ContactName = "XXXX XXXX",
                EmailList = new[]
                {
                    "xxxx@xxxx.xxx",
                },
                Phone = "0000000000",
                PhoneExtension = "",
            },
            DataImportDetails = new[]
            {
                new AzureNative.DataBox.Inputs.DataImportDetailsArgs
                {
                    AccountDetails = new AzureNative.DataBox.Inputs.StorageAccountDetailsArgs
                    {
                        DataAccountType = "StorageAccount",
                        StorageAccountId = "/subscriptions/YourSubscriptionId/resourcegroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
                    },
                },
            },
            JobDetailsType = "DataBox",
            ShippingAddress = new AzureNative.DataBox.Inputs.ShippingAddressArgs
            {
                AddressType = "Commercial",
                City = "XXXX XXXX",
                CompanyName = "XXXX XXXX",
                Country = "XX",
                PostalCode = "00000",
                StateOrProvince = "XX",
                StreetAddress1 = "XXXX XXXX",
                StreetAddress2 = "XXXX XXXX",
            },
        },
        JobName = "TestJobName1",
        Location = "westus",
        ResourceGroupName = "YourResourceGroupName",
        Sku = new AzureNative.DataBox.Inputs.SkuArgs
        {
            Name = "DataBox",
        },
        TransferType = "ImportToAzure",
    });

});


```

```go
package main

import (
	databox "github.com/pulumi/pulumi-azure-native-sdk/databox"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := databox.NewJob(ctx, "job", &databox.JobArgs{
			Details: databox.DataBoxJobDetails{
				ContactDetails: databox.ContactDetails{
					ContactName: "XXXX XXXX",
					EmailList: []string{
						"xxxx@xxxx.xxx",
					},
					Phone:          "0000000000",
					PhoneExtension: "",
				},
				DataImportDetails: []databox.DataImportDetails{
					{
						AccountDetails: {
							DataAccountType:  "StorageAccount",
							StorageAccountId: "/subscriptions/YourSubscriptionId/resourcegroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
						},
					},
				},
				JobDetailsType: "DataBox",
				ShippingAddress: databox.ShippingAddress{
					AddressType:     "Commercial",
					City:            "XXXX XXXX",
					CompanyName:     "XXXX XXXX",
					Country:         "XX",
					PostalCode:      "00000",
					StateOrProvince: "XX",
					StreetAddress1:  "XXXX XXXX",
					StreetAddress2:  "XXXX XXXX",
				},
			},
			JobName:           pulumi.String("TestJobName1"),
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("YourResourceGroupName"),
			Sku: &databox.SkuArgs{
				Name: pulumi.String("DataBox"),
			},
			TransferType: pulumi.String("ImportToAzure"),
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
import com.pulumi.azurenative.databox.Job;
import com.pulumi.azurenative.databox.JobArgs;
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
            .details(Map.ofEntries(
                Map.entry("contactDetails", Map.ofEntries(
                    Map.entry("contactName", "XXXX XXXX"),
                    Map.entry("emailList", "xxxx@xxxx.xxx"),
                    Map.entry("phone", "0000000000"),
                    Map.entry("phoneExtension", "")
                )),
                Map.entry("dataImportDetails", Map.of("accountDetails", Map.ofEntries(
                    Map.entry("dataAccountType", "StorageAccount"),
                    Map.entry("storageAccountId", "/subscriptions/YourSubscriptionId/resourcegroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName")
                ))),
                Map.entry("jobDetailsType", "DataBox"),
                Map.entry("shippingAddress", Map.ofEntries(
                    Map.entry("addressType", "Commercial"),
                    Map.entry("city", "XXXX XXXX"),
                    Map.entry("companyName", "XXXX XXXX"),
                    Map.entry("country", "XX"),
                    Map.entry("postalCode", "00000"),
                    Map.entry("stateOrProvince", "XX"),
                    Map.entry("streetAddress1", "XXXX XXXX"),
                    Map.entry("streetAddress2", "XXXX XXXX")
                ))
            ))
            .jobName("TestJobName1")
            .location("westus")
            .resourceGroupName("YourResourceGroupName")
            .sku(Map.of("name", "DataBox"))
            .transferType("ImportToAzure")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const job = new azure_native.databox.Job("job", {
    details: {
        contactDetails: {
            contactName: "XXXX XXXX",
            emailList: ["xxxx@xxxx.xxx"],
            phone: "0000000000",
            phoneExtension: "",
        },
        dataImportDetails: [{
            accountDetails: {
                dataAccountType: "StorageAccount",
                storageAccountId: "/subscriptions/YourSubscriptionId/resourcegroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
            },
        }],
        jobDetailsType: "DataBox",
        shippingAddress: {
            addressType: "Commercial",
            city: "XXXX XXXX",
            companyName: "XXXX XXXX",
            country: "XX",
            postalCode: "00000",
            stateOrProvince: "XX",
            streetAddress1: "XXXX XXXX",
            streetAddress2: "XXXX XXXX",
        },
    },
    jobName: "TestJobName1",
    location: "westus",
    resourceGroupName: "YourResourceGroupName",
    sku: {
        name: "DataBox",
    },
    transferType: "ImportToAzure",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job = azure_native.databox.Job("job",
    details=azure_native.databox.DataBoxJobDetailsArgs(
        contact_details=azure_native.databox.ContactDetailsArgs(
            contact_name="XXXX XXXX",
            email_list=["xxxx@xxxx.xxx"],
            phone="0000000000",
            phone_extension="",
        ),
        data_import_details=[azure_native.databox.DataImportDetailsArgs(
            account_details=azure_native.databox.StorageAccountDetailsArgs(
                data_account_type="StorageAccount",
                storage_account_id="/subscriptions/YourSubscriptionId/resourcegroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
            ),
        )],
        job_details_type="DataBox",
        shipping_address=azure_native.databox.ShippingAddressArgs(
            address_type="Commercial",
            city="XXXX XXXX",
            company_name="XXXX XXXX",
            country="XX",
            postal_code="00000",
            state_or_province="XX",
            street_address1="XXXX XXXX",
            street_address2="XXXX XXXX",
        ),
    ),
    job_name="TestJobName1",
    location="westus",
    resource_group_name="YourResourceGroupName",
    sku=azure_native.databox.SkuArgs(
        name="DataBox",
    ),
    transfer_type="ImportToAzure")

```

```yaml
resources:
  job:
    type: azure-native:databox:Job
    properties:
      details:
        contactDetails:
          contactName: XXXX XXXX
          emailList:
            - xxxx@xxxx.xxx
          phone: '0000000000'
          phoneExtension:
        dataImportDetails:
          - accountDetails:
              dataAccountType: StorageAccount
              storageAccountId: /subscriptions/YourSubscriptionId/resourcegroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName
        jobDetailsType: DataBox
        shippingAddress:
          addressType: Commercial
          city: XXXX XXXX
          companyName: XXXX XXXX
          country: XX
          postalCode: '00000'
          stateOrProvince: XX
          streetAddress1: XXXX XXXX
          streetAddress2: XXXX XXXX
      jobName: TestJobName1
      location: westus
      resourceGroupName: YourResourceGroupName
      sku:
        name: DataBox
      transferType: ImportToAzure

```

{{% /example %}}
{{% example %}}
### JobsCreateDevicePassword
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var job = new AzureNative.DataBox.Job("job", new()
    {
        Details = new AzureNative.DataBox.Inputs.DataBoxJobDetailsArgs
        {
            ContactDetails = new AzureNative.DataBox.Inputs.ContactDetailsArgs
            {
                ContactName = "XXXX XXXX",
                EmailList = new[]
                {
                    "xxxx@xxxx.xxx",
                },
                Phone = "0000000000",
                PhoneExtension = "",
            },
            DataImportDetails = new[]
            {
                new AzureNative.DataBox.Inputs.DataImportDetailsArgs
                {
                    AccountDetails = new AzureNative.DataBox.Inputs.StorageAccountDetailsArgs
                    {
                        DataAccountType = "StorageAccount",
                        SharePassword = "<sharePassword>",
                        StorageAccountId = "/subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
                    },
                },
            },
            DevicePassword = "<devicePassword>",
            JobDetailsType = "DataBox",
            ShippingAddress = new AzureNative.DataBox.Inputs.ShippingAddressArgs
            {
                AddressType = "Commercial",
                City = "XXXX XXXX",
                CompanyName = "XXXX XXXX",
                Country = "XX",
                PostalCode = "00000",
                StateOrProvince = "XX",
                StreetAddress1 = "XXXX XXXX",
                StreetAddress2 = "XXXX XXXX",
            },
        },
        JobName = "TestJobName1",
        Location = "westus",
        ResourceGroupName = "YourResourceGroupName",
        Sku = new AzureNative.DataBox.Inputs.SkuArgs
        {
            Name = "DataBox",
        },
        TransferType = "ImportToAzure",
    });

});


```

```go
package main

import (
	databox "github.com/pulumi/pulumi-azure-native-sdk/databox"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := databox.NewJob(ctx, "job", &databox.JobArgs{
			Details: databox.DataBoxJobDetails{
				ContactDetails: databox.ContactDetails{
					ContactName: "XXXX XXXX",
					EmailList: []string{
						"xxxx@xxxx.xxx",
					},
					Phone:          "0000000000",
					PhoneExtension: "",
				},
				DataImportDetails: []databox.DataImportDetails{
					{
						AccountDetails: {
							DataAccountType:  "StorageAccount",
							SharePassword:    "<sharePassword>",
							StorageAccountId: "/subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
						},
					},
				},
				DevicePassword: "<devicePassword>",
				JobDetailsType: "DataBox",
				ShippingAddress: databox.ShippingAddress{
					AddressType:     "Commercial",
					City:            "XXXX XXXX",
					CompanyName:     "XXXX XXXX",
					Country:         "XX",
					PostalCode:      "00000",
					StateOrProvince: "XX",
					StreetAddress1:  "XXXX XXXX",
					StreetAddress2:  "XXXX XXXX",
				},
			},
			JobName:           pulumi.String("TestJobName1"),
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("YourResourceGroupName"),
			Sku: &databox.SkuArgs{
				Name: pulumi.String("DataBox"),
			},
			TransferType: pulumi.String("ImportToAzure"),
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
import com.pulumi.azurenative.databox.Job;
import com.pulumi.azurenative.databox.JobArgs;
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
            .details(Map.ofEntries(
                Map.entry("contactDetails", Map.ofEntries(
                    Map.entry("contactName", "XXXX XXXX"),
                    Map.entry("emailList", "xxxx@xxxx.xxx"),
                    Map.entry("phone", "0000000000"),
                    Map.entry("phoneExtension", "")
                )),
                Map.entry("dataImportDetails", Map.of("accountDetails", Map.ofEntries(
                    Map.entry("dataAccountType", "StorageAccount"),
                    Map.entry("sharePassword", "<sharePassword>"),
                    Map.entry("storageAccountId", "/subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName")
                ))),
                Map.entry("devicePassword", "<devicePassword>"),
                Map.entry("jobDetailsType", "DataBox"),
                Map.entry("shippingAddress", Map.ofEntries(
                    Map.entry("addressType", "Commercial"),
                    Map.entry("city", "XXXX XXXX"),
                    Map.entry("companyName", "XXXX XXXX"),
                    Map.entry("country", "XX"),
                    Map.entry("postalCode", "00000"),
                    Map.entry("stateOrProvince", "XX"),
                    Map.entry("streetAddress1", "XXXX XXXX"),
                    Map.entry("streetAddress2", "XXXX XXXX")
                ))
            ))
            .jobName("TestJobName1")
            .location("westus")
            .resourceGroupName("YourResourceGroupName")
            .sku(Map.of("name", "DataBox"))
            .transferType("ImportToAzure")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const job = new azure_native.databox.Job("job", {
    details: {
        contactDetails: {
            contactName: "XXXX XXXX",
            emailList: ["xxxx@xxxx.xxx"],
            phone: "0000000000",
            phoneExtension: "",
        },
        dataImportDetails: [{
            accountDetails: {
                dataAccountType: "StorageAccount",
                sharePassword: "<sharePassword>",
                storageAccountId: "/subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
            },
        }],
        devicePassword: "<devicePassword>",
        jobDetailsType: "DataBox",
        shippingAddress: {
            addressType: "Commercial",
            city: "XXXX XXXX",
            companyName: "XXXX XXXX",
            country: "XX",
            postalCode: "00000",
            stateOrProvince: "XX",
            streetAddress1: "XXXX XXXX",
            streetAddress2: "XXXX XXXX",
        },
    },
    jobName: "TestJobName1",
    location: "westus",
    resourceGroupName: "YourResourceGroupName",
    sku: {
        name: "DataBox",
    },
    transferType: "ImportToAzure",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job = azure_native.databox.Job("job",
    details=azure_native.databox.DataBoxJobDetailsArgs(
        contact_details=azure_native.databox.ContactDetailsArgs(
            contact_name="XXXX XXXX",
            email_list=["xxxx@xxxx.xxx"],
            phone="0000000000",
            phone_extension="",
        ),
        data_import_details=[azure_native.databox.DataImportDetailsArgs(
            account_details=azure_native.databox.StorageAccountDetailsArgs(
                data_account_type="StorageAccount",
                share_password="<sharePassword>",
                storage_account_id="/subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
            ),
        )],
        device_password="<devicePassword>",
        job_details_type="DataBox",
        shipping_address=azure_native.databox.ShippingAddressArgs(
            address_type="Commercial",
            city="XXXX XXXX",
            company_name="XXXX XXXX",
            country="XX",
            postal_code="00000",
            state_or_province="XX",
            street_address1="XXXX XXXX",
            street_address2="XXXX XXXX",
        ),
    ),
    job_name="TestJobName1",
    location="westus",
    resource_group_name="YourResourceGroupName",
    sku=azure_native.databox.SkuArgs(
        name="DataBox",
    ),
    transfer_type="ImportToAzure")

```

```yaml
resources:
  job:
    type: azure-native:databox:Job
    properties:
      details:
        contactDetails:
          contactName: XXXX XXXX
          emailList:
            - xxxx@xxxx.xxx
          phone: '0000000000'
          phoneExtension:
        dataImportDetails:
          - accountDetails:
              dataAccountType: StorageAccount
              sharePassword: <sharePassword>
              storageAccountId: /subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName
        devicePassword: <devicePassword>
        jobDetailsType: DataBox
        shippingAddress:
          addressType: Commercial
          city: XXXX XXXX
          companyName: XXXX XXXX
          country: XX
          postalCode: '00000'
          stateOrProvince: XX
          streetAddress1: XXXX XXXX
          streetAddress2: XXXX XXXX
      jobName: TestJobName1
      location: westus
      resourceGroupName: YourResourceGroupName
      sku:
        name: DataBox
      transferType: ImportToAzure

```

{{% /example %}}
{{% example %}}
### JobsCreateDoubleEncryption
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var job = new AzureNative.DataBox.Job("job", new()
    {
        Details = new AzureNative.DataBox.Inputs.DataBoxJobDetailsArgs
        {
            ContactDetails = new AzureNative.DataBox.Inputs.ContactDetailsArgs
            {
                ContactName = "XXXX XXXX",
                EmailList = new[]
                {
                    "xxxx@xxxx.xxx",
                },
                Phone = "0000000000",
                PhoneExtension = "",
            },
            DataImportDetails = new[]
            {
                new AzureNative.DataBox.Inputs.DataImportDetailsArgs
                {
                    AccountDetails = new AzureNative.DataBox.Inputs.StorageAccountDetailsArgs
                    {
                        DataAccountType = "StorageAccount",
                        StorageAccountId = "/subscriptions/YourSubscriptionId/resourcegroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
                    },
                },
            },
            JobDetailsType = "DataBox",
            Preferences = new AzureNative.DataBox.Inputs.PreferencesArgs
            {
                EncryptionPreferences = new AzureNative.DataBox.Inputs.EncryptionPreferencesArgs
                {
                    DoubleEncryption = "Enabled",
                },
            },
            ShippingAddress = new AzureNative.DataBox.Inputs.ShippingAddressArgs
            {
                AddressType = "Commercial",
                City = "XXXX XXXX",
                CompanyName = "XXXX XXXX",
                Country = "XX",
                PostalCode = "00000",
                StateOrProvince = "XX",
                StreetAddress1 = "XXXX XXXX",
                StreetAddress2 = "XXXX XXXX",
            },
        },
        JobName = "TestJobName1",
        Location = "westus",
        ResourceGroupName = "YourResourceGroupName",
        Sku = new AzureNative.DataBox.Inputs.SkuArgs
        {
            Name = "DataBox",
        },
        TransferType = "ImportToAzure",
    });

});


```

```go
package main

import (
	databox "github.com/pulumi/pulumi-azure-native-sdk/databox"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := databox.NewJob(ctx, "job", &databox.JobArgs{
			Details: databox.DataBoxJobDetails{
				ContactDetails: databox.ContactDetails{
					ContactName: "XXXX XXXX",
					EmailList: []string{
						"xxxx@xxxx.xxx",
					},
					Phone:          "0000000000",
					PhoneExtension: "",
				},
				DataImportDetails: []databox.DataImportDetails{
					{
						AccountDetails: {
							DataAccountType:  "StorageAccount",
							StorageAccountId: "/subscriptions/YourSubscriptionId/resourcegroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
						},
					},
				},
				JobDetailsType: "DataBox",
				Preferences: databox.Preferences{
					EncryptionPreferences: databox.EncryptionPreferences{
						DoubleEncryption: "Enabled",
					},
				},
				ShippingAddress: databox.ShippingAddress{
					AddressType:     "Commercial",
					City:            "XXXX XXXX",
					CompanyName:     "XXXX XXXX",
					Country:         "XX",
					PostalCode:      "00000",
					StateOrProvince: "XX",
					StreetAddress1:  "XXXX XXXX",
					StreetAddress2:  "XXXX XXXX",
				},
			},
			JobName:           pulumi.String("TestJobName1"),
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("YourResourceGroupName"),
			Sku: &databox.SkuArgs{
				Name: pulumi.String("DataBox"),
			},
			TransferType: pulumi.String("ImportToAzure"),
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
import com.pulumi.azurenative.databox.Job;
import com.pulumi.azurenative.databox.JobArgs;
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
            .details(Map.ofEntries(
                Map.entry("contactDetails", Map.ofEntries(
                    Map.entry("contactName", "XXXX XXXX"),
                    Map.entry("emailList", "xxxx@xxxx.xxx"),
                    Map.entry("phone", "0000000000"),
                    Map.entry("phoneExtension", "")
                )),
                Map.entry("dataImportDetails", Map.of("accountDetails", Map.ofEntries(
                    Map.entry("dataAccountType", "StorageAccount"),
                    Map.entry("storageAccountId", "/subscriptions/YourSubscriptionId/resourcegroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName")
                ))),
                Map.entry("jobDetailsType", "DataBox"),
                Map.entry("preferences", Map.of("encryptionPreferences", Map.of("doubleEncryption", "Enabled"))),
                Map.entry("shippingAddress", Map.ofEntries(
                    Map.entry("addressType", "Commercial"),
                    Map.entry("city", "XXXX XXXX"),
                    Map.entry("companyName", "XXXX XXXX"),
                    Map.entry("country", "XX"),
                    Map.entry("postalCode", "00000"),
                    Map.entry("stateOrProvince", "XX"),
                    Map.entry("streetAddress1", "XXXX XXXX"),
                    Map.entry("streetAddress2", "XXXX XXXX")
                ))
            ))
            .jobName("TestJobName1")
            .location("westus")
            .resourceGroupName("YourResourceGroupName")
            .sku(Map.of("name", "DataBox"))
            .transferType("ImportToAzure")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const job = new azure_native.databox.Job("job", {
    details: {
        contactDetails: {
            contactName: "XXXX XXXX",
            emailList: ["xxxx@xxxx.xxx"],
            phone: "0000000000",
            phoneExtension: "",
        },
        dataImportDetails: [{
            accountDetails: {
                dataAccountType: "StorageAccount",
                storageAccountId: "/subscriptions/YourSubscriptionId/resourcegroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
            },
        }],
        jobDetailsType: "DataBox",
        preferences: {
            encryptionPreferences: {
                doubleEncryption: "Enabled",
            },
        },
        shippingAddress: {
            addressType: "Commercial",
            city: "XXXX XXXX",
            companyName: "XXXX XXXX",
            country: "XX",
            postalCode: "00000",
            stateOrProvince: "XX",
            streetAddress1: "XXXX XXXX",
            streetAddress2: "XXXX XXXX",
        },
    },
    jobName: "TestJobName1",
    location: "westus",
    resourceGroupName: "YourResourceGroupName",
    sku: {
        name: "DataBox",
    },
    transferType: "ImportToAzure",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job = azure_native.databox.Job("job",
    details=azure_native.databox.DataBoxJobDetailsArgs(
        contact_details=azure_native.databox.ContactDetailsArgs(
            contact_name="XXXX XXXX",
            email_list=["xxxx@xxxx.xxx"],
            phone="0000000000",
            phone_extension="",
        ),
        data_import_details=[azure_native.databox.DataImportDetailsArgs(
            account_details=azure_native.databox.StorageAccountDetailsArgs(
                data_account_type="StorageAccount",
                storage_account_id="/subscriptions/YourSubscriptionId/resourcegroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
            ),
        )],
        job_details_type="DataBox",
        preferences=azure_native.databox.PreferencesArgs(
            encryption_preferences=azure_native.databox.EncryptionPreferencesArgs(
                double_encryption="Enabled",
            ),
        ),
        shipping_address=azure_native.databox.ShippingAddressArgs(
            address_type="Commercial",
            city="XXXX XXXX",
            company_name="XXXX XXXX",
            country="XX",
            postal_code="00000",
            state_or_province="XX",
            street_address1="XXXX XXXX",
            street_address2="XXXX XXXX",
        ),
    ),
    job_name="TestJobName1",
    location="westus",
    resource_group_name="YourResourceGroupName",
    sku=azure_native.databox.SkuArgs(
        name="DataBox",
    ),
    transfer_type="ImportToAzure")

```

```yaml
resources:
  job:
    type: azure-native:databox:Job
    properties:
      details:
        contactDetails:
          contactName: XXXX XXXX
          emailList:
            - xxxx@xxxx.xxx
          phone: '0000000000'
          phoneExtension:
        dataImportDetails:
          - accountDetails:
              dataAccountType: StorageAccount
              storageAccountId: /subscriptions/YourSubscriptionId/resourcegroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName
        jobDetailsType: DataBox
        preferences:
          encryptionPreferences:
            doubleEncryption: Enabled
        shippingAddress:
          addressType: Commercial
          city: XXXX XXXX
          companyName: XXXX XXXX
          country: XX
          postalCode: '00000'
          stateOrProvince: XX
          streetAddress1: XXXX XXXX
          streetAddress2: XXXX XXXX
      jobName: TestJobName1
      location: westus
      resourceGroupName: YourResourceGroupName
      sku:
        name: DataBox
      transferType: ImportToAzure

```

{{% /example %}}
{{% example %}}
### JobsCreateExport
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var job = new AzureNative.DataBox.Job("job", new()
    {
        Details = new AzureNative.DataBox.Inputs.DataBoxJobDetailsArgs
        {
            ContactDetails = new AzureNative.DataBox.Inputs.ContactDetailsArgs
            {
                ContactName = "XXXX XXXX",
                EmailList = new[]
                {
                    "xxxx@xxxx.xxx",
                },
                Phone = "0000000000",
                PhoneExtension = "",
            },
            DataExportDetails = new[]
            {
                new AzureNative.DataBox.Inputs.DataExportDetailsArgs
                {
                    AccountDetails = new AzureNative.DataBox.Inputs.StorageAccountDetailsArgs
                    {
                        DataAccountType = "StorageAccount",
                        StorageAccountId = "/subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
                    },
                    TransferConfiguration = new AzureNative.DataBox.Inputs.TransferConfigurationArgs
                    {
                        TransferAllDetails = new AzureNative.DataBox.Inputs.TransferConfigurationTransferAllDetailsArgs
                        {
                            Include = new AzureNative.DataBox.Inputs.TransferAllDetailsArgs
                            {
                                DataAccountType = "StorageAccount",
                                TransferAllBlobs = true,
                                TransferAllFiles = true,
                            },
                        },
                        TransferConfigurationType = "TransferAll",
                    },
                },
            },
            JobDetailsType = "DataBox",
            ShippingAddress = new AzureNative.DataBox.Inputs.ShippingAddressArgs
            {
                AddressType = "Commercial",
                City = "XXXX XXXX",
                CompanyName = "XXXX XXXX",
                Country = "XX",
                PostalCode = "00000",
                StateOrProvince = "XX",
                StreetAddress1 = "XXXX XXXX",
                StreetAddress2 = "XXXX XXXX",
            },
        },
        JobName = "TestJobName1",
        Location = "westus",
        ResourceGroupName = "YourResourceGroupName",
        Sku = new AzureNative.DataBox.Inputs.SkuArgs
        {
            Name = "DataBox",
        },
        TransferType = "ExportFromAzure",
    });

});


```

```go
package main

import (
	databox "github.com/pulumi/pulumi-azure-native-sdk/databox"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := databox.NewJob(ctx, "job", &databox.JobArgs{
			Details: databox.DataBoxJobDetails{
				ContactDetails: databox.ContactDetails{
					ContactName: "XXXX XXXX",
					EmailList: []string{
						"xxxx@xxxx.xxx",
					},
					Phone:          "0000000000",
					PhoneExtension: "",
				},
				DataExportDetails: []databox.DataExportDetails{
					{
						AccountDetails: {
							DataAccountType:  "StorageAccount",
							StorageAccountId: "/subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
						},
						TransferConfiguration: {
							TransferAllDetails: {
								Include: {
									DataAccountType:  "StorageAccount",
									TransferAllBlobs: true,
									TransferAllFiles: true,
								},
							},
							TransferConfigurationType: "TransferAll",
						},
					},
				},
				JobDetailsType: "DataBox",
				ShippingAddress: databox.ShippingAddress{
					AddressType:     "Commercial",
					City:            "XXXX XXXX",
					CompanyName:     "XXXX XXXX",
					Country:         "XX",
					PostalCode:      "00000",
					StateOrProvince: "XX",
					StreetAddress1:  "XXXX XXXX",
					StreetAddress2:  "XXXX XXXX",
				},
			},
			JobName:           pulumi.String("TestJobName1"),
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("YourResourceGroupName"),
			Sku: &databox.SkuArgs{
				Name: pulumi.String("DataBox"),
			},
			TransferType: pulumi.String("ExportFromAzure"),
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
import com.pulumi.azurenative.databox.Job;
import com.pulumi.azurenative.databox.JobArgs;
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
            .details(Map.ofEntries(
                Map.entry("contactDetails", Map.ofEntries(
                    Map.entry("contactName", "XXXX XXXX"),
                    Map.entry("emailList", "xxxx@xxxx.xxx"),
                    Map.entry("phone", "0000000000"),
                    Map.entry("phoneExtension", "")
                )),
                Map.entry("dataExportDetails", Map.ofEntries(
                    Map.entry("accountDetails", Map.ofEntries(
                        Map.entry("dataAccountType", "StorageAccount"),
                        Map.entry("storageAccountId", "/subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName")
                    )),
                    Map.entry("transferConfiguration", Map.ofEntries(
                        Map.entry("transferAllDetails", Map.of("include", Map.ofEntries(
                            Map.entry("dataAccountType", "StorageAccount"),
                            Map.entry("transferAllBlobs", true),
                            Map.entry("transferAllFiles", true)
                        ))),
                        Map.entry("transferConfigurationType", "TransferAll")
                    ))
                )),
                Map.entry("jobDetailsType", "DataBox"),
                Map.entry("shippingAddress", Map.ofEntries(
                    Map.entry("addressType", "Commercial"),
                    Map.entry("city", "XXXX XXXX"),
                    Map.entry("companyName", "XXXX XXXX"),
                    Map.entry("country", "XX"),
                    Map.entry("postalCode", "00000"),
                    Map.entry("stateOrProvince", "XX"),
                    Map.entry("streetAddress1", "XXXX XXXX"),
                    Map.entry("streetAddress2", "XXXX XXXX")
                ))
            ))
            .jobName("TestJobName1")
            .location("westus")
            .resourceGroupName("YourResourceGroupName")
            .sku(Map.of("name", "DataBox"))
            .transferType("ExportFromAzure")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const job = new azure_native.databox.Job("job", {
    details: {
        contactDetails: {
            contactName: "XXXX XXXX",
            emailList: ["xxxx@xxxx.xxx"],
            phone: "0000000000",
            phoneExtension: "",
        },
        dataExportDetails: [{
            accountDetails: {
                dataAccountType: "StorageAccount",
                storageAccountId: "/subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
            },
            transferConfiguration: {
                transferAllDetails: {
                    include: {
                        dataAccountType: "StorageAccount",
                        transferAllBlobs: true,
                        transferAllFiles: true,
                    },
                },
                transferConfigurationType: "TransferAll",
            },
        }],
        jobDetailsType: "DataBox",
        shippingAddress: {
            addressType: "Commercial",
            city: "XXXX XXXX",
            companyName: "XXXX XXXX",
            country: "XX",
            postalCode: "00000",
            stateOrProvince: "XX",
            streetAddress1: "XXXX XXXX",
            streetAddress2: "XXXX XXXX",
        },
    },
    jobName: "TestJobName1",
    location: "westus",
    resourceGroupName: "YourResourceGroupName",
    sku: {
        name: "DataBox",
    },
    transferType: "ExportFromAzure",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job = azure_native.databox.Job("job",
    details=azure_native.databox.DataBoxJobDetailsArgs(
        contact_details=azure_native.databox.ContactDetailsArgs(
            contact_name="XXXX XXXX",
            email_list=["xxxx@xxxx.xxx"],
            phone="0000000000",
            phone_extension="",
        ),
        data_export_details=[azure_native.databox.DataExportDetailsArgs(
            account_details=azure_native.databox.StorageAccountDetailsArgs(
                data_account_type="StorageAccount",
                storage_account_id="/subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName",
            ),
            transfer_configuration=azure_native.databox.TransferConfigurationArgs(
                transfer_all_details=azure_native.databox.TransferConfigurationTransferAllDetailsArgs(
                    include=azure_native.databox.TransferAllDetailsArgs(
                        data_account_type="StorageAccount",
                        transfer_all_blobs=True,
                        transfer_all_files=True,
                    ),
                ),
                transfer_configuration_type="TransferAll",
            ),
        )],
        job_details_type="DataBox",
        shipping_address=azure_native.databox.ShippingAddressArgs(
            address_type="Commercial",
            city="XXXX XXXX",
            company_name="XXXX XXXX",
            country="XX",
            postal_code="00000",
            state_or_province="XX",
            street_address1="XXXX XXXX",
            street_address2="XXXX XXXX",
        ),
    ),
    job_name="TestJobName1",
    location="westus",
    resource_group_name="YourResourceGroupName",
    sku=azure_native.databox.SkuArgs(
        name="DataBox",
    ),
    transfer_type="ExportFromAzure")

```

```yaml
resources:
  job:
    type: azure-native:databox:Job
    properties:
      details:
        contactDetails:
          contactName: XXXX XXXX
          emailList:
            - xxxx@xxxx.xxx
          phone: '0000000000'
          phoneExtension:
        dataExportDetails:
          - accountDetails:
              dataAccountType: StorageAccount
              storageAccountId: /subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.Storage/storageAccounts/YourStorageAccountName
            transferConfiguration:
              transferAllDetails:
                include:
                  dataAccountType: StorageAccount
                  transferAllBlobs: true
                  transferAllFiles: true
              transferConfigurationType: TransferAll
        jobDetailsType: DataBox
        shippingAddress:
          addressType: Commercial
          city: XXXX XXXX
          companyName: XXXX XXXX
          country: XX
          postalCode: '00000'
          stateOrProvince: XX
          streetAddress1: XXXX XXXX
          streetAddress2: XXXX XXXX
      jobName: TestJobName1
      location: westus
      resourceGroupName: YourResourceGroupName
      sku:
        name: DataBox
      transferType: ExportFromAzure

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databox:Job TestJobName1 /subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.DataBox/jobs/TestJobName1 
```
