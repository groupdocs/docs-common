---
id: using-aliases
url: search/java/using-aliases
title: Using aliases
weight: 28
description: ""
keywords: 
productName: GroupDocs.Search for Java
hideChildren: False
---
The use of aliases allows you to reduce the length of search queries in text form. To use an alias in a search query, you must enter the @ symbol with the name of the alias after it without spaces.

Aliases are stored in the alias dictionary. By default the alias dictionary is empty. Detailed information on managing the alias dictionary can be found on the [Alias dictionary](Alias%2Bdictionary.html) page of the [Managing dictionaries]({{< ref "search/java/developer-guide/advanced-usage/managing-dictionaries/_index.md" >}}) section.

An example of using aliases for searching is presented below.

**Java**

```csharp
String indexFolder = "c:\\MyIndex\\";
String documentsFolder = "c:\\MyDocuments\\";
 
// Creating an index in the specified folder
Index index = new Index(indexFolder);
 
// Indexing documents from the specified folder
index.add(documentsFolder);
 
// Adding aliases to the alias dictionary
index.getDictionaries().getAliasDictionary().add("t", "(theory OR relativity)");
index.getDictionaries().getAliasDictionary().add("e", "(Einstein OR Albert)");
 
// Search in the index
SearchResult result = index.search("@t OR @e");
```

## More resources

### GitHub examples

You may easily run the code from documentation articles and see the features in action in our GitHub examples:

*   [GroupDocs.Search for .NET examples](https://github.com/groupdocs-search/GroupDocs.Search-for-.NET)
    
*   [GroupDocs.Search for Java examples](https://github.com/groupdocs-search/GroupDocs.Search-for-Java)
    

### Free online document search App

Along with full featured .NET library we provide simple, but powerful free Apps.

You are welcome to search over your PDF, DOC, DOCX, PPT, PPTX, XLS, XLSX and more with our free online [Free Online Document Search App](https://products.groupdocs.app/search).
