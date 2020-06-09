---
id: regular-expression-search
url: search/java/regular-expression-search
title: Regular expression search
weight: 17
description: ""
keywords: 
productName: GroupDocs.Search for Java
hideChildren: False
---
Regular expression (RegEx) search queries are universal and very flexible, but at the same time, in large indexes, their performance becomes extremely low. Another limitation of regular expressions is that search with a pattern is done for each word separately, and not the entire text of a document field.

Queries of this type always starts with the caret character, and if the regular expression itself also starts with the caret character, then there will be two caret characters at the beginning of the query.

A regex search query in text form cannot be combined with other types of queries. See the [Query language specification](Query%2Blanguage%2Bspecification.html) page. However, in object form, regular expressions can be combined with other queries. See the [Nesting search queries in object form]({{< ref "search/java/developer-guide/advanced-usage/searching/nesting-search-queries-in-object-form.md" >}}) page.

The following example demonstrates the regex search in text and object forms.

**Java**

```csharp
String indexFolder = "c:\\MyIndex\\";
String documentsFolder = "c:\\MyDocuments\\";
 
// Creating an index in the specified folder
Index index = new Index(indexFolder);
 
// Indexing documents from the specified folder
index.add(documentsFolder);
 
// Search for the phrase in text form
String query1 = "^^(.)\\1{1,}"; // The first caret character at the beginning indicates that this is a regular expression search query
SearchResult result1 = index.search(query1); // Search for two or more identical characters at the beginning of a word
 
// Search for the phrase in object form
SearchQuery query2 = SearchQuery.createRegexQuery("^(.)\\1{1,}"); // Search for two or more identical characters at the beginning of a word
SearchResult result2 = index.search(query2);
```

## More resources

### GitHub examples

You may easily run the code from documentation articles and see the features in action in our GitHub examples:

*   [GroupDocs.Search for .NET examples](https://github.com/groupdocs-search/GroupDocs.Search-for-.NET)
    
*   [GroupDocs.Search for Java examples](https://github.com/groupdocs-search/GroupDocs.Search-for-Java)
    

### Free online document search App

Along with full featured .NET library we provide simple, but powerful free Apps.

You are welcome to search over your PDF, DOC, DOCX, PPT, PPTX, XLS, XLSX and more with our free online [Free Online Document Search App](https://products.groupdocs.app/search).
