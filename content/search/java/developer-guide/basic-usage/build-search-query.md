---
id: build-search-query
url: search/java/build-search-query
title: Build search query
weight: 2
description: ""
keywords: 
productName: GroupDocs.Search for Java
hideChildren: False
---
This page contains information about building text search queries of various types. More examples on building search queries are provided on the page [Search operation table](Search%2Boperation%2Btable.html). A detailed specification of search query language is presented on the page [Query language specification]({{< ref "search/java/developer-guide/advanced-usage/searching/query-language-specification.md" >}}).

In addition to text search queries, there is also the ability to create queries in an object form. Search query forms are described on the page [Queries in text and object form]({{< ref "search/java/developer-guide/advanced-usage/searching/queries-in-text-and-object-form.md" >}}).

You can also use search options to customize your search queries. Detailed information on search options is provided on the page [Search options]({{< ref "search/java/developer-guide/advanced-usage/searching/search-options.md" >}}).

## Simple search query

The first type of search query is a simple search query. Queries of this type are used to search for a single word in the text of a document. The example is presented below.

**Java**

```csharp
String query = "Einstein";
SearchResult result = index.search(query); // Search in the index
```

## Wildcard search query

A more complex type of query is a wildcard search query. There are 2 types of wildcard characters in a word: a one character wildcard and a character group wildcard. Detailed information about wildcards in a word is provided on the page [Wildcard search]({{< ref "search/java/developer-guide/advanced-usage/searching/wildcard-search.md" >}}). The example below demonstrates use of the one character wildcard.

**Java**

```csharp
String query = "?ffect";
SearchResult result = index.search(query); // Search for words 'affect', 'effect', ets.
```

The character group wildcard allows you to specify a range of unknown characters in the form ?(N~M), where N and M are in the range from 0 to 255. The next example demonstrates use of the character group wildcard.

**Java**

```csharp
String query = "princip?(2~4)";
SearchResult result = index.search(query); // Search for words 'principal', 'principle', 'principles', 'principally', ets.
```

## Faceted search query

The next type of query - faceted search query - allows you to specify the document field for the search. Detailed information about faceted search is presented on the page [Faceted search]({{< ref "search/java/developer-guide/advanced-usage/searching/faceted-search.md" >}}). The following example shows how to search only in 'Content' field.

**Java**

```csharp
String query = "Content: Einstein";
SearchResult result = index.search(query); // Search for word 'Einstein' only in 'Content' field
```

## Numeric range search query

The following type of query allows you to specify a range of numbers to search - numeric range search query. Detailed information about numeric range search is presented on the page [Numeric range search]({{< ref "search/java/developer-guide/advanced-usage/searching/numeric-range-search.md" >}}). The example below demonstrates how to search for numbers in the range from 2000 to 3000.

**Java**

```csharp
String query = "2000 ~~ 3000";
SearchResult result = index.search(query); // Search for numbers from 2000 to 3000
```

## Date range search query

Search for dates from a particular range is performed using a date range search query. Details on the date range search are presented on the page [Date range search]({{< ref "search/java/developer-guide/advanced-usage/searching/date-range-search.md" >}}). The example demonstrates how to search for dates in the format 'MM/dd/yyyy' in the range from 01/01/2000 to 06/15/2001.

**Java**

```csharp
SearchOptions options = new SearchOptions(); // Creating a search options object
options.getDateFormats().clear(); // Removing default date formats
 
// Creating a date format pattern 'MM/dd/yyyy'
DateFormatElement[] elements = new DateFormatElement[]
{
    DateFormatElement.getMonthTwoDigits(),
    DateFormatElement.getDateSeparator(),
    DateFormatElement.getDayOfMonthTwoDigits(),
    DateFormatElement.getDateSeparator(),
    DateFormatElement.getYearFourDigits(),
};
DateFormat dateFormat = new DateFormat(elements, "/");
 
options.getDateFormats().addItem(dateFormat); // Adding the date format pattern to the date format collection
String query = "daterange(2000-01-01 ~~ 2001-06-15)"; // Dates in the search query are always specified in the format 'yyyy-MM-dd'
 
SearchResult result = index.search(query, options); // Search in index
```

## Regular expression search query

The next type of query is a regular expression search query. Detailed information about queries of this type is presented on the page [Regular expression search]({{< ref "search/java/developer-guide/advanced-usage/searching/regular-expression-search.md" >}}). The following example demonstrates the use of regular expressions to search in an index.

**Java**

```csharp
String query = "^(.)\\1{2,}"; // The caret character at the beginning indicates that this is a regular expression search query
SearchResult result = index.search(query); // Search for three or more identical characters in a row
```

## Boolean search query

The next type of search query is a boolean search query. Queries of this type allow you to use the logical conditions for the presence or absence of particular words in documents. The boolean operators AND, OR, NOT can be used in queries of this type. Detailed information about this type of search is presented on the page [Boolean search]({{< ref "search/java/developer-guide/advanced-usage/searching/boolean-search.md" >}}). The following example demonstrates how to search for documents containing the word 'Einstein' but not containing the word 'relativity'.

**Java**

```csharp
String query = "Einstein AND NOT relativity";
SearchResult result = index.search(query);
```

Boolean search queries can be combined using parentheses and other types of queries. For example, the following query searches for all documents containing words that start with 'relativ' in the document path or that contain the word 'Einstein' in the document content.

**Java**

```csharp
String query = "FileName: relativ?(1~3) OR Content: (Einstein AND Albert)";
SearchResult result = index.search(query); // Search for documents whose paths contain 'relative', 'relativity', ets., or documents containing both 'Einstein' and 'Albert' in the content
```

## Phrase search query

Another type of query - a phrase search query - allows you to search entire phrases in documents. Detailed information on the phase search is on the page [Phrase search]({{< ref "search/java/developer-guide/advanced-usage/searching/phrase-search.md" >}}). An example of the phrase search is presented below.

**Java**

```csharp
String query = "\"theory of special relativity\"";
SearchResult result = index.search(query); // Search for the phrase 'theory of special relativity'
```

## More resources

### Advanced usage topics

To learn more about search features and get familiar how to enhance your search solution, please refer to the [advanced usage section]({{< ref "search/java/developer-guide/advanced-usage/_index.md" >}}).

### GitHub examples

You may easily run the code from documentation articles and see the features in action in our GitHub examples:

*   [GroupDocs.Search for .NET examples](https://github.com/groupdocs-search/GroupDocs.Search-for-.NET)
    
*   [GroupDocs.Search for Java examples](https://github.com/groupdocs-search/GroupDocs.Search-for-Java)
    

### Free online document search App

Along with full featured .NET library we provide simple, but powerful free Apps.

You are welcome to search over your PDF, DOC, DOCX, PPT, PPTX, XLS, XLSX and more with our free online [Free Online Document Search App](https://products.groupdocs.app/search).
