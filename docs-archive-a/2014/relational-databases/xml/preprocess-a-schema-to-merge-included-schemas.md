---
title: 前置處理結構描述以合併包含的結構描述 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- testing preprocessor tool
- xsd:include
- XML schema collections [SQL Server], preprocessor tool
- include element
- XML schemas [SQL Server], preprocessing
- schema collections [SQL Server], preprocessor tool
- preprocessor tool [XML schemas]
- XML schemas [SQL Server]
ms.assetid: cde1de5f-077a-4a6d-8a81-1ecb6e10d549
author: rothja
ms.author: jroth
ms.openlocfilehash: 1bd7ef3893a1e7fd51ca904caa0e76c64d2ae19c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706285"
---
# <a name="preprocess-a-schema-to-merge-included-schemas"></a><span data-ttu-id="4c9fe-102">前置處理結構描述以合併包含的結構描述</span><span class="sxs-lookup"><span data-stu-id="4c9fe-102">Preprocess a Schema to Merge Included Schemas</span></span>
  <span data-ttu-id="4c9fe-103">W3C XSD **include** 元素提供結構描述模組化的支援，在模組化中可以將 XML 結構描述分割成一個以上的實體檔案。</span><span class="sxs-lookup"><span data-stu-id="4c9fe-103">The W3C XSD **include** element provides support for schema modularity in which an XML schema can be partitioned into more than one physical file.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4c9fe-104">目前不支援這個元素。</span><span class="sxs-lookup"><span data-stu-id="4c9fe-104">currently does not support this element.</span></span> <span data-ttu-id="4c9fe-105">伺服器將會拒絕包含此元素的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="4c9fe-105">XML schemas that include this element will be rejected by the server.</span></span>  
  
 <span data-ttu-id="4c9fe-106">作為解決方案，可預先處理包含 \<xsd:include> 指示詞的 XML 結構描述，以便將任何所包含之結構描述的內容複製並合併成單一結構描述，以利上傳至伺服器。</span><span class="sxs-lookup"><span data-stu-id="4c9fe-106">As a solution, XML schemas that include the \<xsd:include> directive can be preprocessed to copy and merge the contents of any included schemas into a single schema for uploading to the server.</span></span> <span data-ttu-id="4c9fe-107">下列 C#  程式碼可用以預先處理。</span><span class="sxs-lookup"><span data-stu-id="4c9fe-107">The following C# code can be used for the preprocessing.</span></span> <span data-ttu-id="4c9fe-108">在程式碼開始部份的註解提供如何使用它的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c9fe-108">The comments in the early part of the code provide information about how to use it.</span></span>  
  
```  
// XSD Schema Include Normalizer  
// To compile:   
// csc filename.cs  
//  
// How to use:  
//  
// Arguments: [-q] input.xsd [output.xsd]  
//  
// input.xsd       - file to normalize  
// output.xsd      - file to output, default is console  
// -q              - quiet  
//   
// Example:  
//   
// filename.exe schema.xsd  
//   
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.IO;  
using System.Collections;  
public class XsdSchemaNormalizer  
{  
    private static bool NormalizeXmlSchema( String url, TextWriter writer )  
    {  
   try {  
       XmlTextReader txtRead = new XmlTextReader( url );  
       XmlSchema sch = XmlSchema.Read( txtRead, null );  
  
       // Compiling Schema  
       sch.Compile(null);  
  
       XmlSchema outSch =   
      XmlSchemaIncludeNormalizer.BuildIncludeFreeXmlSchema( sch);  
  
       outSch.Write( writer );  
   } catch ( Exception e ) {  
       Console.WriteLine(e.ToString());  
       return false;  
   }  
   return true;  
    }  
    public static void usage()  
    {  
   Console.WriteLine("Arguments: [-q] [-v] input.xsd [output.xsd]\n");  
   Console.WriteLine("input.xsd       - file to normalize");  
   Console.WriteLine("output.xsd      - file to output, default is console");  
   Console.WriteLine("-q              - quiet");  
    }  
    public static void Main(String []args)  
    {  
   if( args.GetLength(0) < 1 ) {  
       usage();  
       return;  
   }  
   int argi = 0;  
   bool quiet = false;  
   if( args[argi] == "-q" ) {  
       quiet = true;  
            argi++;  
   }  
  
   if( argi == args.GetLength(0) )  
   {  
       usage();  
       return;  
   }  
  
   String url = args[argi];  
  
   if( !quiet )  
       Console.WriteLine("Loading Schema: " + url);  
  
   if( argi < ( args.GetLength(0) - 1 ) )  
   {  
       if( !quiet )  
      Console.WriteLine("Outputing to file: " + args[argi+1]);  
  
       StreamWriter output =   
      new StreamWriter( new FileStream(args[argi+1], FileMode.Create ));  
  
       NormalizeXmlSchema( url, output);  
   }  
   else   
   {  
       NormalizeXmlSchema( url, Console.Out);  
   }  
  
    }  
}  
  
// A class to remove all <include> from a Xml Schema  
//  
public class XmlSchemaIncludeNormalizer  
{  
    // Takes as input a XmlSchema which has includes in it   
    // and the schema location uri of that XmlSchema  
    //   
    // Returns a "preprocessed" form of XmlSchema without any   
    // includes. It still retains imports though. Also, it does  
    // not propagate unhandled attributes  
    //  
    // It can throw any exception  
    public static XmlSchema BuildIncludeFreeXmlSchema( XmlSchema inSch )  
    {  
   XmlSchema outSch = new XmlSchema();  
  
   AddSchema( outSch, inSch );  
  
   return outSch;  
    }  
  
    // Adds everything in the second schema minus includes to   
    // the first schema  
    //  
    private static void AddSchema( XmlSchema outSch, XmlSchema add)  
    {  
   outSch.AttributeFormDefault = add.AttributeFormDefault;  
   outSch.BlockDefault = add.BlockDefault;  
   outSch.ElementFormDefault = add.ElementFormDefault;  
   outSch.FinalDefault = add.FinalDefault;  
   outSch.Id = add.Id;  
   outSch.TargetNamespace = add.TargetNamespace;  
   outSch.Version = add.Version;  
  
   AddTableToSchema( outSch, add.AttributeGroups );  
   AddTableToSchema( outSch, add.Attributes );  
   AddTableToSchema( outSch, add.Elements );  
   AddTableToSchema( outSch, add.Groups );  
   AddTableToSchema( outSch, add.Notations );  
   AddTableToSchema( outSch, add.SchemaTypes );  
  
   // Handle includes as a special case  
   for( int i = 0; i < add.Includes.Count; i++ )  
   {  
       if( ! ( add.Includes[i] is XmlSchemaInclude) )  
      outSch.Includes.Add( add.Includes[i] );  
   }  
    }  
  
    // Adds all items in the XmlSchemaObjectTable to the specified XmlSchema  
    //  
    private static void AddTableToSchema( XmlSchema outSch,   
                 XmlSchemaObjectTable table )  
    {  
   IDictionaryEnumerator e = table.GetEnumerator();  
  
   while( e.MoveNext() )  
   {  
       outSch.Items.Add( (XmlSchemaObject)e.Value );  
   }  
    }  
}  
```  
  
## <a name="testing-the-preprocessor-tool"></a><span data-ttu-id="4c9fe-109">測試前置處理器工具</span><span class="sxs-lookup"><span data-stu-id="4c9fe-109">Testing the Preprocessor Tool</span></span>  
 <span data-ttu-id="4c9fe-110">您可以使用下列 XSD 結構描述測試前置處理器工具：</span><span class="sxs-lookup"><span data-stu-id="4c9fe-110">You can use the following XSD schemas to test the preprocessor tool:</span></span>  
  
### <a name="books_commonxsd"></a><span data-ttu-id="4c9fe-111">books_common.xsd</span><span class="sxs-lookup"><span data-stu-id="4c9fe-111">books_common.xsd</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
     xmlns="bookstore-schema"  
     elementFormDefault="qualified" >  
  <xsd:element name="publisher" type="xsd:string"/>  
</xsd:schema>  
```  
  
### <a name="booksxsd"></a><span data-ttu-id="4c9fe-112">books.xsd</span><span class="sxs-lookup"><span data-stu-id="4c9fe-112">books.xsd</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
     xmlns="bookstore-schema"  
     elementFormDefault="qualified"  
     targetNamespace="bookstore-schema">  
  <xsd:include id="books_common" schemaLocation="books_common.xsd"/>  
  <xsd:element name="bookstore" type="xsd:string" />  
</xsd:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c9fe-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c9fe-113">See Also</span></span>  
 [<span data-ttu-id="4c9fe-114">XML 結構描述集合 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4c9fe-114">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
  
  
