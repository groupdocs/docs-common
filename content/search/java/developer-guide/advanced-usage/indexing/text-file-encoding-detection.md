---
id: text-file-encoding-detection
url: search/java/text-file-encoding-detection
title: Text file encoding detection
weight: 18
description: ""
keywords: 
productName: GroupDocs.Search for Java
hideChildren: False
---
To automatically detect the encoding of a text file, the [setAutoDetectEncoding](https://apireference.groupdocs.com/search/java/com.groupdocs.search/IndexSettings#setAutoDetectEncoding(boolean)) method defined in the [IndexSettings](https://apireference.groupdocs.com/search/java/com.groupdocs.search/IndexSettings) class can be used. Passing the true value as an argument to this method allows to detect the following encodings:

*   UTF-32 LE,
*   UTF-32 BE,
*   UTF-16 LE,
*   UTF-16 BE,
*   UTF-8,
*   UTF-7,
*   ANSI.

By default, the encoding auto detection of text files is disabled. But in any case, the encoding of a text file can be set during indexing when the [FileIndexing](https://apireference.groupdocs.com/search/java/com.groupdocs.search.events/EventHub#FileIndexing) event is raised. If the encoding of a text file has not been detected or specified in the event arguments, then the default encoding, UTF-8, is used. Available encodings are presented in the [Encodings](https://apireference.groupdocs.com/search/java/com.groupdocs.search.common/Encodings) class. When the encoding of a text file is detected and used for indexing, it is saved in the index to use in such methods of [Index](https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index) class like [highlight](https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index#highlight(com.groupdocs.search.results.FoundDocument,%20com.groupdocs.search.highlighters.Highlighter)) and [getDocumentText](https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index#getDocumentText(com.groupdocs.search.results.DocumentInfo,%20com.groupdocs.search.common.OutputAdapter)).

The example below shows how to set encoding of a text during indexing.

**Java**

```csharp
String indexFolder = "c:\\MyIndex\\";
String documentsFolder = "c:\\MyDocuments\\";
 
// Creating an index
Index index = new Index(indexFolder);
 
// Subscribing to the event
index.getEvents().FileIndexing.add(new EventHandler<FileIndexingEventArgs>() {
    public void invoke(Object sender, FileIndexingEventArgs args) {
        if (args.getDocumentFullPath().endsWith(".txt")) {
            args.setEncoding(Encodings.Windows_1253); // Setting encoding for each text file
        }
    }
});
 
// Indexing documents from the specified folder
index.add(documentsFolder);
```

## More resources

### GitHub examples

You may easily run the code from documentation articles and see the features in action in our GitHub examples:

*   [GroupDocs.Search for .NET examples](https://github.com/groupdocs-search/GroupDocs.Search-for-.NET)
    
*   [GroupDocs.Search for Java examples](https://github.com/groupdocs-search/GroupDocs.Search-for-Java)
    

### Free online document search App

Along with full featured .NET library we provide simple, but powerful free Apps.

You are welcome to search over your PDF, DOC, DOCX, PPT, PPTX, XLS, XLSX and more with our free online [Free Online Document Search App](https://products.groupdocs.app/search).
