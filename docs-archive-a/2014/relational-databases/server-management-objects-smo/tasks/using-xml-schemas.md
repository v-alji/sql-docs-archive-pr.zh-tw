---
title: 使用 XML 架構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- XML [SMO]
ms.assetid: 9d04de01-efeb-4b2d-8c28-3234bc7ff2f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: a0e5c58bb05da7025651a4e55e29541d694ba1ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709037"
---
# <a name="using-xml-schemas"></a><span data-ttu-id="8f60a-102">使用 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="8f60a-102">Using XML Schemas</span></span>
  <span data-ttu-id="8f60a-103">SMO 中的 XML 程式設計僅限於提供 XML 資料類型、XML 命名空間，以及 XML 資料類型資料行上的簡單索引。</span><span class="sxs-lookup"><span data-stu-id="8f60a-103">XML programming in SMO is limited to providing XML data types, XML namespaces, and simple indexing on XML data type columns.</span></span>  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="8f60a-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]提供 XML 檔實例的原生儲存區。</span><span class="sxs-lookup"><span data-stu-id="8f60a-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provides native storage for XML document instances.</span></span> <span data-ttu-id="8f60a-105">XML 結構描述可讓您定義複雜的 XML 資料類型，後者則可用於驗證 XML 文件以確保資料完整性。</span><span class="sxs-lookup"><span data-stu-id="8f60a-105">XML schemas let you define complex XML data types, which can be used to validate XML documents to ensure data integrity.</span></span> <span data-ttu-id="8f60a-106">XML 結構描述是定義在 <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> 物件中。</span><span class="sxs-lookup"><span data-stu-id="8f60a-106">The XML schema is defined in the <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f60a-107">範例</span><span class="sxs-lookup"><span data-stu-id="8f60a-107">Example</span></span>  
 <span data-ttu-id="8f60a-108">如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="8f60a-108">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="8f60a-109">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="8f60a-109">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-an-xml-schema-in-visual-basic"></a><span data-ttu-id="8f60a-110">在 Visual Basic 中建立 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="8f60a-110">Creating an XML Schema in Visual Basic</span></span>  
 <span data-ttu-id="8f60a-111">此程式碼範例示範如何使用 <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> 物件來建立 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="8f60a-111">This code example shows how to create an XML schema by using the <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> object.</span></span> <span data-ttu-id="8f60a-112">定義 XML 結構描述集合的 <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> 屬性包含數個雙引號。</span><span class="sxs-lookup"><span data-stu-id="8f60a-112">The <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> property, which defines the XML schema collection, contains several double quotation marks.</span></span> <span data-ttu-id="8f60a-113">這些會由 `chr(34)` 字串取代。</span><span class="sxs-lookup"><span data-stu-id="8f60a-113">These are replaced by the `chr(34)` string.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBXMLSchema1](SMO How to#SMO_VBXMLSchema1)]  -->  
  
## <a name="creating-an-xml-schema-in-visual-c"></a><span data-ttu-id="8f60a-114">在 Visual C# 中建立 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="8f60a-114">Creating an XML Schema in Visual C#</span></span>  
 <span data-ttu-id="8f60a-115">此程式碼範例示範如何使用 <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> 物件來建立 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="8f60a-115">This code example shows how to create an XML schema by using the <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> object.</span></span> <span data-ttu-id="8f60a-116">定義 XML 結構描述集合的 <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> 屬性包含數個雙引號。</span><span class="sxs-lookup"><span data-stu-id="8f60a-116">The <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> property, which defines the XML schema collection, contains several double quotation marks.</span></span> <span data-ttu-id="8f60a-117">這些會由 `chr(34)` 字串取代。</span><span class="sxs-lookup"><span data-stu-id="8f60a-117">These are replaced by the `chr(34)` string.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = default(Server);  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Define an XmlSchemaCollection object by supplying the parent  
            // database and name arguments in the constructor.   
            XmlSchemaCollection xsc = default(XmlSchemaCollection);  
            xsc = new XmlSchemaCollection(db, "MySampleCollection");  
            xsc.Text = "<schema xmlns=" + Strings.Chr(34) + "http://www.w3.org/2001/XMLSchema" + Strings.Chr(34) + " xmlns:ns=" + Strings.Chr(34) + "http://ns" + Strings.Chr(34) + "><element name=" + Strings.Chr(34) + "e" + Strings.Chr(34) + " type=" + Strings.Chr(34) + "dateTime" + Strings.Chr(34) + "/></schema>";  
            //Create the XML schema collection on the instance of SQL Server.   
            xsc.Create();  
        }  
```  
  
## <a name="creating-an-xml-schema-in-powershell"></a><span data-ttu-id="8f60a-118">在 PowerShell 中建立 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="8f60a-118">Creating an XML Schema in PowerShell</span></span>  
 <span data-ttu-id="8f60a-119">此程式碼範例示範如何使用 <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> 物件來建立 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="8f60a-119">This code example shows how to create an XML schema by using the <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> object.</span></span> <span data-ttu-id="8f60a-120">定義 XML 結構描述集合的 <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> 屬性包含數個雙引號。</span><span class="sxs-lookup"><span data-stu-id="8f60a-120">The <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> property, which defines the XML schema collection, contains several double quotation marks.</span></span> <span data-ttu-id="8f60a-121">這些會由 `chr(34)` 字串取代。</span><span class="sxs-lookup"><span data-stu-id="8f60a-121">These are replaced by the `chr(34)` string.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalHost  
$srv = Get-Item default  
  
#Reference the AdventureWorks database.  
$db = $srv.Databases["AdventureWorks2012"]  
  
#Create a new schema collection  
$xsc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.XmlSchemaCollection `  
-argumentlist $db,"MySampleCollection"  
  
#Add the xml  
$dq = '"' # the double quote character  
$xsc.Text = "<schema xmlns=" + $dq + "http://www.w3.org/2001/XMLSchema" + $dq + `  
"  xmlns:ns=" + $dq + "http://ns" + $dq + "><element name=" + $dq + "e" + $dq +`  
 " type=" + $dq + "dateTime" + $dq + "/></schema>"  
  
#Create the XML schema collection on the instance of SQL Server.  
$xsc.Create()  
```  
