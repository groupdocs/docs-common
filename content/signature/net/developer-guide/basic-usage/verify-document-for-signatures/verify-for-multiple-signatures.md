---
id: verify-for-multiple-signatures
url: signature/net/verify-for-multiple-signatures
title: Verify for multiple signatures
weight: 5
description: "This topic explains how to verify electronic signatures of various types with GroupDocs.Signature API."
keywords: 
productName: GroupDocs.Signature for .NET
hideChildren: False
---
[**GroupDocs.Signature**](https://products.groupdocs.com/signature/net) supports verification of documents for different signature types. This approach requires to add all required verification options to list.

Here are the steps to verify document for multiple signatures with GroupDocs.Signature:

*   Create new instance of [Signature](https://apireference.groupdocs.com/net/signature/groupdocs.signature/signature) class and pass source document path or stream as a constructor parameter.
    
*   Instantiate required several [VerifyOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/verifyoptions) objects ([BarcodeVerifyOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/barcodeverifyoptions)[, ](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/barcodesearchoptions)[QrCodeVerifyOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/qrcodeverifyoptions)[, ](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/qrcodesearchoptions)[DigitalVerifyOptions,](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/digitalverifyoptions)[ ](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/qrcodesearchoptions)[TextVerifyOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/textverifyoptions)[) and add instances to List<](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/qrcodesearchoptions)[VerifyOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/verifyoptions)[\> collection.  
    ](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/qrcodesearchoptions)
    
*   Call [Verify](https://apireference.groupdocs.com/net/signature/groupdocs.signature/signature/methods/verify) method of [Signature](https://apireference.groupdocs.com/net/signature/groupdocs.signature/signature) class instance and pass filled list o List<[VerifyOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/verifyoptions)\> to it.   
      
    

This example shows how to search for different signature types in the document.

```csharp
using (Signature signature = new Signature("sampleSigned.pdf"))
{
    TextVerifyOptions textVerifyOptions = new TextVerifyOptions()
    {
        AllPages = true, // this value is set by default
        SignatureImplementation = TextSignatureImplementation.Stamp,
        Text = "John",
        MatchType = TextMatchType.Contains
    };
    BarcodeVerifyOptions barcVerifyOptions = new BarcodeVerifyOptions()
    {
        AllPages = true, // this value is set by default
        Text = "John",
        MatchType = TextMatchType.Contains
    };
    QrCodeVerifyOptions qrcdVerifyOptions = new QrCodeVerifyOptions()
    {
        AllPages = true, // this value is set by default
        Text = "John",
        MatchType = TextMatchType.Contains
    };
    DigitalVerifyOptions digtVerifyOptions = new DigitalVerifyOptions("certificate.pdf")
    {
        Comments = "Test comment"
    };
    // verify document signatures
    List<VerifyOptions> listOptions = new List<VerifyOptions>();
    listOptions.Add(textVerifyOptions);
    listOptions.Add(barcVerifyOptions);
    listOptions.Add(qrcdVerifyOptions);
    listOptions.Add(digtVerifyOptions);
    VerificationResult result = signature.Verify(listOptions);
    if (result.IsValid)
    {
        Console.WriteLine("\nDocument was verified successfully!");
    }
    else
    {
        Console.WriteLine("\nDocument failed verification process.");
    }
}
```

## More resources

### Advanced Usage Topics

To learn more about document eSign features, please refer to the [advanced usage section]({{< ref "signature/net/developer-guide/advanced-usage/_index.md" >}}).

### GitHub Examples 

You may easily run the code above and see the feature in action in our GitHub examples:

*   [GroupDocs.Signature for .NET examples, plugins, and showcase](https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET)
    
*   [GroupDocs.Signature for Java examples, plugins, and showcase](https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java)
    
*   [Document Signature for .NET MVC UI Example](https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET-MVC) 
    
*   [Document Signature for .NET App WebForms UI Example](https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET-WebForms)
    
*   [Document Signature for Java App Dropwizard UI Example](https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java-Dropwizard)
    
*   [Document Signature for Java Spring UI Example](https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java-Spring)
    

### Free Online App 

Along with full-featured .NET library we provide simple, but powerful free Apps.

You are welcome to eSign PDF, Word, Excel, PowerPoint documents with free to use online **[GroupDocs Signature App](https://products.groupdocs.app/signature)**.
