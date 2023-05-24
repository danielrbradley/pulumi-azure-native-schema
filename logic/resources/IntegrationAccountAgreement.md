The integration account agreement.
API Version: 2019-05-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an agreement
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var integrationAccountAgreement = new AzureNative.Logic.IntegrationAccountAgreement("integrationAccountAgreement", new()
    {
        AgreementName = "testAgreement",
        AgreementType = AzureNative.Logic.AgreementType.AS2,
        Content = new AzureNative.Logic.Inputs.AgreementContentArgs
        {
            AS2 = new AzureNative.Logic.Inputs.AS2AgreementContentArgs
            {
                ReceiveAgreement = new AzureNative.Logic.Inputs.AS2OneWayAgreementArgs
                {
                    ProtocolSettings = new AzureNative.Logic.Inputs.AS2ProtocolSettingsArgs
                    {
                        AcknowledgementConnectionSettings = new AzureNative.Logic.Inputs.AS2AcknowledgementConnectionSettingsArgs
                        {
                            IgnoreCertificateNameMismatch = true,
                            KeepHttpConnectionAlive = true,
                            SupportHttpStatusCodeContinue = true,
                            UnfoldHttpHeaders = true,
                        },
                        EnvelopeSettings = new AzureNative.Logic.Inputs.AS2EnvelopeSettingsArgs
                        {
                            AutogenerateFileName = true,
                            FileNameTemplate = "Test",
                            MessageContentType = "text/plain",
                            SuspendMessageOnFileNameGenerationError = true,
                            TransmitFileNameInMimeHeader = true,
                        },
                        ErrorSettings = new AzureNative.Logic.Inputs.AS2ErrorSettingsArgs
                        {
                            ResendIfMDNNotReceived = true,
                            SuspendDuplicateMessage = true,
                        },
                        MdnSettings = new AzureNative.Logic.Inputs.AS2MdnSettingsArgs
                        {
                            DispositionNotificationTo = "http://tempuri.org",
                            MdnText = "Sample",
                            MicHashingAlgorithm = "SHA1",
                            NeedMDN = true,
                            ReceiptDeliveryUrl = "http://tempuri.org",
                            SendInboundMDNToMessageBox = true,
                            SendMDNAsynchronously = true,
                            SignMDN = true,
                            SignOutboundMDNIfOptional = true,
                        },
                        MessageConnectionSettings = new AzureNative.Logic.Inputs.AS2MessageConnectionSettingsArgs
                        {
                            IgnoreCertificateNameMismatch = true,
                            KeepHttpConnectionAlive = true,
                            SupportHttpStatusCodeContinue = true,
                            UnfoldHttpHeaders = true,
                        },
                        SecuritySettings = new AzureNative.Logic.Inputs.AS2SecuritySettingsArgs
                        {
                            EnableNRRForInboundDecodedMessages = true,
                            EnableNRRForInboundEncodedMessages = true,
                            EnableNRRForInboundMDN = true,
                            EnableNRRForOutboundDecodedMessages = true,
                            EnableNRRForOutboundEncodedMessages = true,
                            EnableNRRForOutboundMDN = true,
                            OverrideGroupSigningCertificate = false,
                        },
                        ValidationSettings = new AzureNative.Logic.Inputs.AS2ValidationSettingsArgs
                        {
                            CheckCertificateRevocationListOnReceive = true,
                            CheckCertificateRevocationListOnSend = true,
                            CheckDuplicateMessage = true,
                            CompressMessage = true,
                            EncryptMessage = false,
                            EncryptionAlgorithm = "AES128",
                            InterchangeDuplicatesValidityDays = 100,
                            OverrideMessageProperties = true,
                            SignMessage = false,
                        },
                    },
                    ReceiverBusinessIdentity = new AzureNative.Logic.Inputs.BusinessIdentityArgs
                    {
                        Qualifier = "ZZ",
                        Value = "ZZ",
                    },
                    SenderBusinessIdentity = new AzureNative.Logic.Inputs.BusinessIdentityArgs
                    {
                        Qualifier = "AA",
                        Value = "AA",
                    },
                },
                SendAgreement = new AzureNative.Logic.Inputs.AS2OneWayAgreementArgs
                {
                    ProtocolSettings = new AzureNative.Logic.Inputs.AS2ProtocolSettingsArgs
                    {
                        AcknowledgementConnectionSettings = new AzureNative.Logic.Inputs.AS2AcknowledgementConnectionSettingsArgs
                        {
                            IgnoreCertificateNameMismatch = true,
                            KeepHttpConnectionAlive = true,
                            SupportHttpStatusCodeContinue = true,
                            UnfoldHttpHeaders = true,
                        },
                        EnvelopeSettings = new AzureNative.Logic.Inputs.AS2EnvelopeSettingsArgs
                        {
                            AutogenerateFileName = true,
                            FileNameTemplate = "Test",
                            MessageContentType = "text/plain",
                            SuspendMessageOnFileNameGenerationError = true,
                            TransmitFileNameInMimeHeader = true,
                        },
                        ErrorSettings = new AzureNative.Logic.Inputs.AS2ErrorSettingsArgs
                        {
                            ResendIfMDNNotReceived = true,
                            SuspendDuplicateMessage = true,
                        },
                        MdnSettings = new AzureNative.Logic.Inputs.AS2MdnSettingsArgs
                        {
                            DispositionNotificationTo = "http://tempuri.org",
                            MdnText = "Sample",
                            MicHashingAlgorithm = "SHA1",
                            NeedMDN = true,
                            ReceiptDeliveryUrl = "http://tempuri.org",
                            SendInboundMDNToMessageBox = true,
                            SendMDNAsynchronously = true,
                            SignMDN = true,
                            SignOutboundMDNIfOptional = true,
                        },
                        MessageConnectionSettings = new AzureNative.Logic.Inputs.AS2MessageConnectionSettingsArgs
                        {
                            IgnoreCertificateNameMismatch = true,
                            KeepHttpConnectionAlive = true,
                            SupportHttpStatusCodeContinue = true,
                            UnfoldHttpHeaders = true,
                        },
                        SecuritySettings = new AzureNative.Logic.Inputs.AS2SecuritySettingsArgs
                        {
                            EnableNRRForInboundDecodedMessages = true,
                            EnableNRRForInboundEncodedMessages = true,
                            EnableNRRForInboundMDN = true,
                            EnableNRRForOutboundDecodedMessages = true,
                            EnableNRRForOutboundEncodedMessages = true,
                            EnableNRRForOutboundMDN = true,
                            OverrideGroupSigningCertificate = false,
                        },
                        ValidationSettings = new AzureNative.Logic.Inputs.AS2ValidationSettingsArgs
                        {
                            CheckCertificateRevocationListOnReceive = true,
                            CheckCertificateRevocationListOnSend = true,
                            CheckDuplicateMessage = true,
                            CompressMessage = true,
                            EncryptMessage = false,
                            EncryptionAlgorithm = "AES128",
                            InterchangeDuplicatesValidityDays = 100,
                            OverrideMessageProperties = true,
                            SignMessage = false,
                        },
                    },
                    ReceiverBusinessIdentity = new AzureNative.Logic.Inputs.BusinessIdentityArgs
                    {
                        Qualifier = "AA",
                        Value = "AA",
                    },
                    SenderBusinessIdentity = new AzureNative.Logic.Inputs.BusinessIdentityArgs
                    {
                        Qualifier = "ZZ",
                        Value = "ZZ",
                    },
                },
            },
        },
        GuestIdentity = new AzureNative.Logic.Inputs.BusinessIdentityArgs
        {
            Qualifier = "AA",
            Value = "AA",
        },
        GuestPartner = "GuestPartner",
        HostIdentity = new AzureNative.Logic.Inputs.BusinessIdentityArgs
        {
            Qualifier = "ZZ",
            Value = "ZZ",
        },
        HostPartner = "HostPartner",
        IntegrationAccountName = "testIntegrationAccount",
        Location = "westus",
        Metadata = null,
        ResourceGroupName = "testResourceGroup",
        Tags = 
        {
            { "IntegrationAccountAgreement", "<IntegrationAccountAgreementName>" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.logic.IntegrationAccountAgreement;
import com.pulumi.azurenative.logic.IntegrationAccountAgreementArgs;
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
        var integrationAccountAgreement = new IntegrationAccountAgreement("integrationAccountAgreement", IntegrationAccountAgreementArgs.builder()        
            .agreementName("testAgreement")
            .agreementType("AS2")
            .content(Map.of("aS2", Map.ofEntries(
                Map.entry("receiveAgreement", Map.ofEntries(
                    Map.entry("protocolSettings", Map.ofEntries(
                        Map.entry("acknowledgementConnectionSettings", Map.ofEntries(
                            Map.entry("ignoreCertificateNameMismatch", true),
                            Map.entry("keepHttpConnectionAlive", true),
                            Map.entry("supportHttpStatusCodeContinue", true),
                            Map.entry("unfoldHttpHeaders", true)
                        )),
                        Map.entry("envelopeSettings", Map.ofEntries(
                            Map.entry("autogenerateFileName", true),
                            Map.entry("fileNameTemplate", "Test"),
                            Map.entry("messageContentType", "text/plain"),
                            Map.entry("suspendMessageOnFileNameGenerationError", true),
                            Map.entry("transmitFileNameInMimeHeader", true)
                        )),
                        Map.entry("errorSettings", Map.ofEntries(
                            Map.entry("resendIfMDNNotReceived", true),
                            Map.entry("suspendDuplicateMessage", true)
                        )),
                        Map.entry("mdnSettings", Map.ofEntries(
                            Map.entry("dispositionNotificationTo", "http://tempuri.org"),
                            Map.entry("mdnText", "Sample"),
                            Map.entry("micHashingAlgorithm", "SHA1"),
                            Map.entry("needMDN", true),
                            Map.entry("receiptDeliveryUrl", "http://tempuri.org"),
                            Map.entry("sendInboundMDNToMessageBox", true),
                            Map.entry("sendMDNAsynchronously", true),
                            Map.entry("signMDN", true),
                            Map.entry("signOutboundMDNIfOptional", true)
                        )),
                        Map.entry("messageConnectionSettings", Map.ofEntries(
                            Map.entry("ignoreCertificateNameMismatch", true),
                            Map.entry("keepHttpConnectionAlive", true),
                            Map.entry("supportHttpStatusCodeContinue", true),
                            Map.entry("unfoldHttpHeaders", true)
                        )),
                        Map.entry("securitySettings", Map.ofEntries(
                            Map.entry("enableNRRForInboundDecodedMessages", true),
                            Map.entry("enableNRRForInboundEncodedMessages", true),
                            Map.entry("enableNRRForInboundMDN", true),
                            Map.entry("enableNRRForOutboundDecodedMessages", true),
                            Map.entry("enableNRRForOutboundEncodedMessages", true),
                            Map.entry("enableNRRForOutboundMDN", true),
                            Map.entry("overrideGroupSigningCertificate", false)
                        )),
                        Map.entry("validationSettings", Map.ofEntries(
                            Map.entry("checkCertificateRevocationListOnReceive", true),
                            Map.entry("checkCertificateRevocationListOnSend", true),
                            Map.entry("checkDuplicateMessage", true),
                            Map.entry("compressMessage", true),
                            Map.entry("encryptMessage", false),
                            Map.entry("encryptionAlgorithm", "AES128"),
                            Map.entry("interchangeDuplicatesValidityDays", 100),
                            Map.entry("overrideMessageProperties", true),
                            Map.entry("signMessage", false)
                        ))
                    )),
                    Map.entry("receiverBusinessIdentity", Map.ofEntries(
                        Map.entry("qualifier", "ZZ"),
                        Map.entry("value", "ZZ")
                    )),
                    Map.entry("senderBusinessIdentity", Map.ofEntries(
                        Map.entry("qualifier", "AA"),
                        Map.entry("value", "AA")
                    ))
                )),
                Map.entry("sendAgreement", Map.ofEntries(
                    Map.entry("protocolSettings", Map.ofEntries(
                        Map.entry("acknowledgementConnectionSettings", Map.ofEntries(
                            Map.entry("ignoreCertificateNameMismatch", true),
                            Map.entry("keepHttpConnectionAlive", true),
                            Map.entry("supportHttpStatusCodeContinue", true),
                            Map.entry("unfoldHttpHeaders", true)
                        )),
                        Map.entry("envelopeSettings", Map.ofEntries(
                            Map.entry("autogenerateFileName", true),
                            Map.entry("fileNameTemplate", "Test"),
                            Map.entry("messageContentType", "text/plain"),
                            Map.entry("suspendMessageOnFileNameGenerationError", true),
                            Map.entry("transmitFileNameInMimeHeader", true)
                        )),
                        Map.entry("errorSettings", Map.ofEntries(
                            Map.entry("resendIfMDNNotReceived", true),
                            Map.entry("suspendDuplicateMessage", true)
                        )),
                        Map.entry("mdnSettings", Map.ofEntries(
                            Map.entry("dispositionNotificationTo", "http://tempuri.org"),
                            Map.entry("mdnText", "Sample"),
                            Map.entry("micHashingAlgorithm", "SHA1"),
                            Map.entry("needMDN", true),
                            Map.entry("receiptDeliveryUrl", "http://tempuri.org"),
                            Map.entry("sendInboundMDNToMessageBox", true),
                            Map.entry("sendMDNAsynchronously", true),
                            Map.entry("signMDN", true),
                            Map.entry("signOutboundMDNIfOptional", true)
                        )),
                        Map.entry("messageConnectionSettings", Map.ofEntries(
                            Map.entry("ignoreCertificateNameMismatch", true),
                            Map.entry("keepHttpConnectionAlive", true),
                            Map.entry("supportHttpStatusCodeContinue", true),
                            Map.entry("unfoldHttpHeaders", true)
                        )),
                        Map.entry("securitySettings", Map.ofEntries(
                            Map.entry("enableNRRForInboundDecodedMessages", true),
                            Map.entry("enableNRRForInboundEncodedMessages", true),
                            Map.entry("enableNRRForInboundMDN", true),
                            Map.entry("enableNRRForOutboundDecodedMessages", true),
                            Map.entry("enableNRRForOutboundEncodedMessages", true),
                            Map.entry("enableNRRForOutboundMDN", true),
                            Map.entry("overrideGroupSigningCertificate", false)
                        )),
                        Map.entry("validationSettings", Map.ofEntries(
                            Map.entry("checkCertificateRevocationListOnReceive", true),
                            Map.entry("checkCertificateRevocationListOnSend", true),
                            Map.entry("checkDuplicateMessage", true),
                            Map.entry("compressMessage", true),
                            Map.entry("encryptMessage", false),
                            Map.entry("encryptionAlgorithm", "AES128"),
                            Map.entry("interchangeDuplicatesValidityDays", 100),
                            Map.entry("overrideMessageProperties", true),
                            Map.entry("signMessage", false)
                        ))
                    )),
                    Map.entry("receiverBusinessIdentity", Map.ofEntries(
                        Map.entry("qualifier", "AA"),
                        Map.entry("value", "AA")
                    )),
                    Map.entry("senderBusinessIdentity", Map.ofEntries(
                        Map.entry("qualifier", "ZZ"),
                        Map.entry("value", "ZZ")
                    ))
                ))
            )))
            .guestIdentity(Map.ofEntries(
                Map.entry("qualifier", "AA"),
                Map.entry("value", "AA")
            ))
            .guestPartner("GuestPartner")
            .hostIdentity(Map.ofEntries(
                Map.entry("qualifier", "ZZ"),
                Map.entry("value", "ZZ")
            ))
            .hostPartner("HostPartner")
            .integrationAccountName("testIntegrationAccount")
            .location("westus")
            .metadata()
            .resourceGroupName("testResourceGroup")
            .tags(Map.of("IntegrationAccountAgreement", "<IntegrationAccountAgreementName>"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const integrationAccountAgreement = new azure_native.logic.IntegrationAccountAgreement("integrationAccountAgreement", {
    agreementName: "testAgreement",
    agreementType: azure_native.logic.AgreementType.AS2,
    content: {
        aS2: {
            receiveAgreement: {
                protocolSettings: {
                    acknowledgementConnectionSettings: {
                        ignoreCertificateNameMismatch: true,
                        keepHttpConnectionAlive: true,
                        supportHttpStatusCodeContinue: true,
                        unfoldHttpHeaders: true,
                    },
                    envelopeSettings: {
                        autogenerateFileName: true,
                        fileNameTemplate: "Test",
                        messageContentType: "text/plain",
                        suspendMessageOnFileNameGenerationError: true,
                        transmitFileNameInMimeHeader: true,
                    },
                    errorSettings: {
                        resendIfMDNNotReceived: true,
                        suspendDuplicateMessage: true,
                    },
                    mdnSettings: {
                        dispositionNotificationTo: "http://tempuri.org",
                        mdnText: "Sample",
                        micHashingAlgorithm: "SHA1",
                        needMDN: true,
                        receiptDeliveryUrl: "http://tempuri.org",
                        sendInboundMDNToMessageBox: true,
                        sendMDNAsynchronously: true,
                        signMDN: true,
                        signOutboundMDNIfOptional: true,
                    },
                    messageConnectionSettings: {
                        ignoreCertificateNameMismatch: true,
                        keepHttpConnectionAlive: true,
                        supportHttpStatusCodeContinue: true,
                        unfoldHttpHeaders: true,
                    },
                    securitySettings: {
                        enableNRRForInboundDecodedMessages: true,
                        enableNRRForInboundEncodedMessages: true,
                        enableNRRForInboundMDN: true,
                        enableNRRForOutboundDecodedMessages: true,
                        enableNRRForOutboundEncodedMessages: true,
                        enableNRRForOutboundMDN: true,
                        overrideGroupSigningCertificate: false,
                    },
                    validationSettings: {
                        checkCertificateRevocationListOnReceive: true,
                        checkCertificateRevocationListOnSend: true,
                        checkDuplicateMessage: true,
                        compressMessage: true,
                        encryptMessage: false,
                        encryptionAlgorithm: "AES128",
                        interchangeDuplicatesValidityDays: 100,
                        overrideMessageProperties: true,
                        signMessage: false,
                    },
                },
                receiverBusinessIdentity: {
                    qualifier: "ZZ",
                    value: "ZZ",
                },
                senderBusinessIdentity: {
                    qualifier: "AA",
                    value: "AA",
                },
            },
            sendAgreement: {
                protocolSettings: {
                    acknowledgementConnectionSettings: {
                        ignoreCertificateNameMismatch: true,
                        keepHttpConnectionAlive: true,
                        supportHttpStatusCodeContinue: true,
                        unfoldHttpHeaders: true,
                    },
                    envelopeSettings: {
                        autogenerateFileName: true,
                        fileNameTemplate: "Test",
                        messageContentType: "text/plain",
                        suspendMessageOnFileNameGenerationError: true,
                        transmitFileNameInMimeHeader: true,
                    },
                    errorSettings: {
                        resendIfMDNNotReceived: true,
                        suspendDuplicateMessage: true,
                    },
                    mdnSettings: {
                        dispositionNotificationTo: "http://tempuri.org",
                        mdnText: "Sample",
                        micHashingAlgorithm: "SHA1",
                        needMDN: true,
                        receiptDeliveryUrl: "http://tempuri.org",
                        sendInboundMDNToMessageBox: true,
                        sendMDNAsynchronously: true,
                        signMDN: true,
                        signOutboundMDNIfOptional: true,
                    },
                    messageConnectionSettings: {
                        ignoreCertificateNameMismatch: true,
                        keepHttpConnectionAlive: true,
                        supportHttpStatusCodeContinue: true,
                        unfoldHttpHeaders: true,
                    },
                    securitySettings: {
                        enableNRRForInboundDecodedMessages: true,
                        enableNRRForInboundEncodedMessages: true,
                        enableNRRForInboundMDN: true,
                        enableNRRForOutboundDecodedMessages: true,
                        enableNRRForOutboundEncodedMessages: true,
                        enableNRRForOutboundMDN: true,
                        overrideGroupSigningCertificate: false,
                    },
                    validationSettings: {
                        checkCertificateRevocationListOnReceive: true,
                        checkCertificateRevocationListOnSend: true,
                        checkDuplicateMessage: true,
                        compressMessage: true,
                        encryptMessage: false,
                        encryptionAlgorithm: "AES128",
                        interchangeDuplicatesValidityDays: 100,
                        overrideMessageProperties: true,
                        signMessage: false,
                    },
                },
                receiverBusinessIdentity: {
                    qualifier: "AA",
                    value: "AA",
                },
                senderBusinessIdentity: {
                    qualifier: "ZZ",
                    value: "ZZ",
                },
            },
        },
    },
    guestIdentity: {
        qualifier: "AA",
        value: "AA",
    },
    guestPartner: "GuestPartner",
    hostIdentity: {
        qualifier: "ZZ",
        value: "ZZ",
    },
    hostPartner: "HostPartner",
    integrationAccountName: "testIntegrationAccount",
    location: "westus",
    metadata: {},
    resourceGroupName: "testResourceGroup",
    tags: {
        IntegrationAccountAgreement: "<IntegrationAccountAgreementName>",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

integration_account_agreement = azure_native.logic.IntegrationAccountAgreement("integrationAccountAgreement",
    agreement_name="testAgreement",
    agreement_type=azure_native.logic.AgreementType.AS2,
    content=azure_native.logic.AgreementContentResponseArgs(
        a_s2={
            "receiveAgreement": {
                "protocolSettings": {
                    "acknowledgementConnectionSettings": azure_native.logic.AS2AcknowledgementConnectionSettingsArgs(
                        ignore_certificate_name_mismatch=True,
                        keep_http_connection_alive=True,
                        support_http_status_code_continue=True,
                        unfold_http_headers=True,
                    ),
                    "envelopeSettings": azure_native.logic.AS2EnvelopeSettingsArgs(
                        autogenerate_file_name=True,
                        file_name_template="Test",
                        message_content_type="text/plain",
                        suspend_message_on_file_name_generation_error=True,
                        transmit_file_name_in_mime_header=True,
                    ),
                    "errorSettings": azure_native.logic.AS2ErrorSettingsArgs(
                        resend_if_mdn_not_received=True,
                        suspend_duplicate_message=True,
                    ),
                    "mdnSettings": azure_native.logic.AS2MdnSettingsArgs(
                        disposition_notification_to="http://tempuri.org",
                        mdn_text="Sample",
                        mic_hashing_algorithm="SHA1",
                        need_mdn=True,
                        receipt_delivery_url="http://tempuri.org",
                        send_inbound_mdn_to_message_box=True,
                        send_mdnasynchronously=True,
                        sign_mdn=True,
                        sign_outbound_mdn_if_optional=True,
                    ),
                    "messageConnectionSettings": azure_native.logic.AS2MessageConnectionSettingsArgs(
                        ignore_certificate_name_mismatch=True,
                        keep_http_connection_alive=True,
                        support_http_status_code_continue=True,
                        unfold_http_headers=True,
                    ),
                    "securitySettings": azure_native.logic.AS2SecuritySettingsArgs(
                        enable_nrr_for_inbound_decoded_messages=True,
                        enable_nrr_for_inbound_encoded_messages=True,
                        enable_nrr_for_inbound_mdn=True,
                        enable_nrr_for_outbound_decoded_messages=True,
                        enable_nrr_for_outbound_encoded_messages=True,
                        enable_nrr_for_outbound_mdn=True,
                        override_group_signing_certificate=False,
                    ),
                    "validationSettings": azure_native.logic.AS2ValidationSettingsArgs(
                        check_certificate_revocation_list_on_receive=True,
                        check_certificate_revocation_list_on_send=True,
                        check_duplicate_message=True,
                        compress_message=True,
                        encrypt_message=False,
                        encryption_algorithm="AES128",
                        interchange_duplicates_validity_days=100,
                        override_message_properties=True,
                        sign_message=False,
                    ),
                },
                "receiverBusinessIdentity": azure_native.logic.BusinessIdentityArgs(
                    qualifier="ZZ",
                    value="ZZ",
                ),
                "senderBusinessIdentity": azure_native.logic.BusinessIdentityArgs(
                    qualifier="AA",
                    value="AA",
                ),
            },
            "sendAgreement": {
                "protocolSettings": {
                    "acknowledgementConnectionSettings": azure_native.logic.AS2AcknowledgementConnectionSettingsArgs(
                        ignore_certificate_name_mismatch=True,
                        keep_http_connection_alive=True,
                        support_http_status_code_continue=True,
                        unfold_http_headers=True,
                    ),
                    "envelopeSettings": azure_native.logic.AS2EnvelopeSettingsArgs(
                        autogenerate_file_name=True,
                        file_name_template="Test",
                        message_content_type="text/plain",
                        suspend_message_on_file_name_generation_error=True,
                        transmit_file_name_in_mime_header=True,
                    ),
                    "errorSettings": azure_native.logic.AS2ErrorSettingsArgs(
                        resend_if_mdn_not_received=True,
                        suspend_duplicate_message=True,
                    ),
                    "mdnSettings": azure_native.logic.AS2MdnSettingsArgs(
                        disposition_notification_to="http://tempuri.org",
                        mdn_text="Sample",
                        mic_hashing_algorithm="SHA1",
                        need_mdn=True,
                        receipt_delivery_url="http://tempuri.org",
                        send_inbound_mdn_to_message_box=True,
                        send_mdnasynchronously=True,
                        sign_mdn=True,
                        sign_outbound_mdn_if_optional=True,
                    ),
                    "messageConnectionSettings": azure_native.logic.AS2MessageConnectionSettingsArgs(
                        ignore_certificate_name_mismatch=True,
                        keep_http_connection_alive=True,
                        support_http_status_code_continue=True,
                        unfold_http_headers=True,
                    ),
                    "securitySettings": azure_native.logic.AS2SecuritySettingsArgs(
                        enable_nrr_for_inbound_decoded_messages=True,
                        enable_nrr_for_inbound_encoded_messages=True,
                        enable_nrr_for_inbound_mdn=True,
                        enable_nrr_for_outbound_decoded_messages=True,
                        enable_nrr_for_outbound_encoded_messages=True,
                        enable_nrr_for_outbound_mdn=True,
                        override_group_signing_certificate=False,
                    ),
                    "validationSettings": azure_native.logic.AS2ValidationSettingsArgs(
                        check_certificate_revocation_list_on_receive=True,
                        check_certificate_revocation_list_on_send=True,
                        check_duplicate_message=True,
                        compress_message=True,
                        encrypt_message=False,
                        encryption_algorithm="AES128",
                        interchange_duplicates_validity_days=100,
                        override_message_properties=True,
                        sign_message=False,
                    ),
                },
                "receiverBusinessIdentity": azure_native.logic.BusinessIdentityArgs(
                    qualifier="AA",
                    value="AA",
                ),
                "senderBusinessIdentity": azure_native.logic.BusinessIdentityArgs(
                    qualifier="ZZ",
                    value="ZZ",
                ),
            },
        },
    ),
    guest_identity=azure_native.logic.BusinessIdentityArgs(
        qualifier="AA",
        value="AA",
    ),
    guest_partner="GuestPartner",
    host_identity=azure_native.logic.BusinessIdentityArgs(
        qualifier="ZZ",
        value="ZZ",
    ),
    host_partner="HostPartner",
    integration_account_name="testIntegrationAccount",
    location="westus",
    metadata={},
    resource_group_name="testResourceGroup",
    tags={
        "IntegrationAccountAgreement": "<IntegrationAccountAgreementName>",
    })

```

```yaml
resources:
  integrationAccountAgreement:
    type: azure-native:logic:IntegrationAccountAgreement
    properties:
      agreementName: testAgreement
      agreementType: AS2
      content:
        aS2:
          receiveAgreement:
            protocolSettings:
              acknowledgementConnectionSettings:
                ignoreCertificateNameMismatch: true
                keepHttpConnectionAlive: true
                supportHttpStatusCodeContinue: true
                unfoldHttpHeaders: true
              envelopeSettings:
                autogenerateFileName: true
                fileNameTemplate: Test
                messageContentType: text/plain
                suspendMessageOnFileNameGenerationError: true
                transmitFileNameInMimeHeader: true
              errorSettings:
                resendIfMDNNotReceived: true
                suspendDuplicateMessage: true
              mdnSettings:
                dispositionNotificationTo: http://tempuri.org
                mdnText: Sample
                micHashingAlgorithm: SHA1
                needMDN: true
                receiptDeliveryUrl: http://tempuri.org
                sendInboundMDNToMessageBox: true
                sendMDNAsynchronously: true
                signMDN: true
                signOutboundMDNIfOptional: true
              messageConnectionSettings:
                ignoreCertificateNameMismatch: true
                keepHttpConnectionAlive: true
                supportHttpStatusCodeContinue: true
                unfoldHttpHeaders: true
              securitySettings:
                enableNRRForInboundDecodedMessages: true
                enableNRRForInboundEncodedMessages: true
                enableNRRForInboundMDN: true
                enableNRRForOutboundDecodedMessages: true
                enableNRRForOutboundEncodedMessages: true
                enableNRRForOutboundMDN: true
                overrideGroupSigningCertificate: false
              validationSettings:
                checkCertificateRevocationListOnReceive: true
                checkCertificateRevocationListOnSend: true
                checkDuplicateMessage: true
                compressMessage: true
                encryptMessage: false
                encryptionAlgorithm: AES128
                interchangeDuplicatesValidityDays: 100
                overrideMessageProperties: true
                signMessage: false
            receiverBusinessIdentity:
              qualifier: ZZ
              value: ZZ
            senderBusinessIdentity:
              qualifier: AA
              value: AA
          sendAgreement:
            protocolSettings:
              acknowledgementConnectionSettings:
                ignoreCertificateNameMismatch: true
                keepHttpConnectionAlive: true
                supportHttpStatusCodeContinue: true
                unfoldHttpHeaders: true
              envelopeSettings:
                autogenerateFileName: true
                fileNameTemplate: Test
                messageContentType: text/plain
                suspendMessageOnFileNameGenerationError: true
                transmitFileNameInMimeHeader: true
              errorSettings:
                resendIfMDNNotReceived: true
                suspendDuplicateMessage: true
              mdnSettings:
                dispositionNotificationTo: http://tempuri.org
                mdnText: Sample
                micHashingAlgorithm: SHA1
                needMDN: true
                receiptDeliveryUrl: http://tempuri.org
                sendInboundMDNToMessageBox: true
                sendMDNAsynchronously: true
                signMDN: true
                signOutboundMDNIfOptional: true
              messageConnectionSettings:
                ignoreCertificateNameMismatch: true
                keepHttpConnectionAlive: true
                supportHttpStatusCodeContinue: true
                unfoldHttpHeaders: true
              securitySettings:
                enableNRRForInboundDecodedMessages: true
                enableNRRForInboundEncodedMessages: true
                enableNRRForInboundMDN: true
                enableNRRForOutboundDecodedMessages: true
                enableNRRForOutboundEncodedMessages: true
                enableNRRForOutboundMDN: true
                overrideGroupSigningCertificate: false
              validationSettings:
                checkCertificateRevocationListOnReceive: true
                checkCertificateRevocationListOnSend: true
                checkDuplicateMessage: true
                compressMessage: true
                encryptMessage: false
                encryptionAlgorithm: AES128
                interchangeDuplicatesValidityDays: 100
                overrideMessageProperties: true
                signMessage: false
            receiverBusinessIdentity:
              qualifier: AA
              value: AA
            senderBusinessIdentity:
              qualifier: ZZ
              value: ZZ
      guestIdentity:
        qualifier: AA
        value: AA
      guestPartner: GuestPartner
      hostIdentity:
        qualifier: ZZ
        value: ZZ
      hostPartner: HostPartner
      integrationAccountName: testIntegrationAccount
      location: westus
      metadata: {}
      resourceGroupName: testResourceGroup
      tags:
        IntegrationAccountAgreement: <IntegrationAccountAgreementName>

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logic:IntegrationAccountAgreement <IntegrationAccountAgreementName> /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testResourceGroup/providers/Microsoft.Logic/integrationAccounts/IntegrationAccount4533/agreements/<IntegrationAccountAgreementName> 
```
