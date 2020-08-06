---
title: 在應用程式中使用 XML 資料 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- parameters [XML in SQL Server]
- XML [SQL Server], ADO
- columns [XML in SQL Server], ADO.NET
- ADO [XML in SQL Server]
- columns [XML in SQL Server], SQL Server Native Client
- xml data type [SQL Server], ADO
- SQLNCLI, XML
- xml data type [SQL Server], SQL Server Native Client
- SQL Server Native Client, XML
- ADO.NET [XML in SQL Server]
- XML [SQL Server], ADO.NET
- columns [XML in SQL Server], ADO
- xml data type [SQL Server], ADO.NET
- XML [SQL Server], SQL Server Native Client
ms.assetid: 5dabf7e0-c6df-451d-a070-4661f84607fd
author: rothja
ms.author: jroth
ms.openlocfilehash: 79dd4f4d2ff3cd61bc33c632f499bfb8e8817f0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686850"
---
# <a name="use-xml-data-in-applications"></a><span data-ttu-id="7bca2-102">在應用程式中使用 XML 資料</span><span class="sxs-lookup"><span data-stu-id="7bca2-102">Use XML Data in Applications</span></span>
  <span data-ttu-id="7bca2-103">此主描述在您的應用程式中使用 `xml` 資料類型時，可用的選項有哪些。</span><span class="sxs-lookup"><span data-stu-id="7bca2-103">This topic describes the options that are available to you for working with the `xml` data type in your application.</span></span> <span data-ttu-id="7bca2-104">此主題包括有關下列項目的資訊：</span><span class="sxs-lookup"><span data-stu-id="7bca2-104">The topic includes information about the following:</span></span>  
  
-   <span data-ttu-id="7bca2-105">使用 ADO 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 處理 `xml` 類型資料行中的 XML</span><span class="sxs-lookup"><span data-stu-id="7bca2-105">Handling XML from an `xml` type column by using ADO and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   <span data-ttu-id="7bca2-106">使用 ADO.NET 處理 `xml` 類型資料行的 XML</span><span class="sxs-lookup"><span data-stu-id="7bca2-106">Handling XML from an `xml` type column by using ADO.NET</span></span>  
  
-   <span data-ttu-id="7bca2-107">使用 ADO.NET 處理參數中的 `xml` 類型</span><span class="sxs-lookup"><span data-stu-id="7bca2-107">Handling `xml` type in parameters by using ADO.NET</span></span>  
  
## <a name="handling-xml-from-an-xml-type-column-by-using-ado-and-sql-server-native-client"></a><span data-ttu-id="7bca2-108">使用 ADO 和 SQL Server Native Client 處理 xml 類型資料行中的 XML</span><span class="sxs-lookup"><span data-stu-id="7bca2-108">Handling XML from an xml Type Column by Using ADO and SQL Server Native Client</span></span>  
 <span data-ttu-id="7bca2-109">若要使用 MDAC 元件來存取 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]中所引進的類型和功能，您必須在 ADO 連接字串中設定 DataTypeCompatibility 初始化屬性。</span><span class="sxs-lookup"><span data-stu-id="7bca2-109">To use MDAC components to access the types and features that were introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you must set the DataTypeCompatibility initialization property in the ADO connection string.</span></span>  
  
 <span data-ttu-id="7bca2-110">例如，以下 Visual Basic Scripting Edition (VBScript) 範例顯示查詢 `Demographics` 範例資料庫 `Sales.Store` 資料表的 `xml` 資料類型資料行 `AdventureWorks2012` 的結果。</span><span class="sxs-lookup"><span data-stu-id="7bca2-110">For example, the following Visual Basic Scripting Edition (VBScript) sample shows the results of querying an `xml` data type column, `Demographics`, in the `Sales.Store` table of the `AdventureWorks2012` sample database.</span></span> <span data-ttu-id="7bca2-111">此查詢特別會尋找此資料行，其資料列的 `CustomerID` 等於 `3`的例項值。</span><span class="sxs-lookup"><span data-stu-id="7bca2-111">Specifically, the query looks for the instance value of this column for the row where the `CustomerID` is equal to `3`.</span></span>  
  
```  
Const DS = "MyServer"  
Const DB = "AdventureWorks2012"  
  
Set objConn = CreateObject("ADODB.Connection")  
Set objRs = CreateObject("ADODB.Recordset")  
  
CommandText = "SELECT Demographics" & _  
              " FROM Sales.Store" & _  
              " INNER JOIN Sales.Customer" & _  
              " ON Sales.Store.BusinessEntityID = sales.customer.StoreID" & _  
              " WHERE Sales.Customer.CustomerID = 3" & _  
              " OR Sales.Customer.CustomerID = 4"  
  
ConnectionString = "Provider=SQLNCLI11" & _  
                   ";Data Source=" & DS & _  
                   ";Initial Catalog=" & DB & _  
                   ";Integrated Security=SSPI;" & _  
                   "DataTypeCompatibility=80"  
  
'Connect to the data source.  
objConn.Open ConnectionString  
  
'Execute command through the connection and display  
Set objRs = objConn.Execute(CommandText)  
  
Dim rowcount  
rowcount = 0  
Do While Not objRs.EOF  
   rowcount = rowcount + 1  
   MsgBox "Row " & rowcount & _  
           vbCrLf & vbCrLf & objRs(0)  
   objRs.MoveNext  
Loop  
  
'Clean up.  
objRs.Close  
objConn.Close  
Set objRs = Nothing  
Set objConn = Nothing  
```  
  
 <span data-ttu-id="7bca2-112">此範例顯示如何設定資料類型相容性屬性。</span><span class="sxs-lookup"><span data-stu-id="7bca2-112">This example shows how to set the data type compatibility property.</span></span> <span data-ttu-id="7bca2-113">當您使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 時，預設會設定為 0。</span><span class="sxs-lookup"><span data-stu-id="7bca2-113">By default, this is set to 0 when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="7bca2-114">如果您將此值設定為 80，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 提供者會讓 `xml` 和使用者定義類型的資料行顯示為 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="7bca2-114">If you set the value to 80, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client provider will make `xml` and user-defined type columns appear as [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] data types.</span></span> <span data-ttu-id="7bca2-115">分別是 DBTYPE_WSTR 和 DBTYPE_BYTES。</span><span class="sxs-lookup"><span data-stu-id="7bca2-115">This would be DBTYPE_WSTR and DBTYPE_BYTES, respectively.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7bca2-116">您也必須在用戶端電腦上安裝 Native Client，而且連接字串必須以 "`Provider=SQLNCLI11;...`" 指定它當作資料提供者。</span><span class="sxs-lookup"><span data-stu-id="7bca2-116">Native Client must also be installed on the client computer and the connection string must specify it for use as the data provider with "`Provider=SQLNCLI11;...`".</span></span>  
  
#### <a name="to-test-this-example"></a><span data-ttu-id="7bca2-117">若要測試此範例</span><span class="sxs-lookup"><span data-stu-id="7bca2-117">To test this example</span></span>  
  
1.  <span data-ttu-id="7bca2-118">確認已安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client，而且用戶端電腦上可以使用 MDAC 2.6.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7bca2-118">Verify that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is installed and that MDAC 2.6.0or later is available on the client computer.</span></span>  
  
     <span data-ttu-id="7bca2-119">如需詳細資訊，請參閱 [SQL Server Native Client 程式設計](../native-client/sql-server-native-client-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="7bca2-119">For more information, see [SQL Server Native Client Programming](../native-client/sql-server-native-client-programming.md).</span></span>  
  
2.  <span data-ttu-id="7bca2-120">確認已在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 中安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="7bca2-120">Verify that the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
     <span data-ttu-id="7bca2-121">此範例需要 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="7bca2-121">This example requires the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
3.  <span data-ttu-id="7bca2-122">複製此主題先前顯示的程式碼，並將程式碼貼到文字編輯器或程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="7bca2-122">Copy the code shown previously in this topic and paste the code into your text or code editor.</span></span> <span data-ttu-id="7bca2-123">將檔案儲存為 HandlingXmlDataType.vbs。</span><span class="sxs-lookup"><span data-stu-id="7bca2-123">Save the file as HandlingXmlDataType.vbs.</span></span>  
  
4.  <span data-ttu-id="7bca2-124">依您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝所需修改指令碼，並儲存變更。</span><span class="sxs-lookup"><span data-stu-id="7bca2-124">Modify the script as required for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation and save your changes.</span></span>  
  
     <span data-ttu-id="7bca2-125">例如，您應該將 `MyServer` 更改為 `(local)` 或安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之伺服器的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="7bca2-125">For example, where `MyServer` is specified, you should replace it with either `(local)` or the actual name of the server on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
5.  <span data-ttu-id="7bca2-126">執行 HandlingXmlDataType.vbs，並執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="7bca2-126">Run HandlingXmlDataType.vbs and execute the script.</span></span>  
  
 <span data-ttu-id="7bca2-127">結果應該類似以下範例輸出：</span><span class="sxs-lookup"><span data-stu-id="7bca2-127">The results should be similar to the following sample output:</span></span>  
  
```  
Row 1  
  
<StoreSurvey xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>1500000</AnnualSales>  
  <AnnualRevenue>150000</AnnualRevenue>  
  <BankName>Primary International</BankName>  
  <BusinessType>OS</BusinessType>  
  <YearOpened>1974</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>38000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>DSL</Internet>  
  <NumberEmployees>40</NumberEmployees>  
</StoreSurvey>  
  
Row 2  
  
<StoreSurvey xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>United Security</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1976</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>6000</SquareFeet>  
  <Brands>2</Brands>  
  <Internet>DSL</Internet>  
  <NumberEmployees>5</NumberEmployees>  
</StoreSurvey>  
```  
  
## <a name="handling-xml-from-an-xml-type-column-by-using-adonet"></a><span data-ttu-id="7bca2-128">使用 ADO.NET 處理 xml 類型資料行的 XML</span><span class="sxs-lookup"><span data-stu-id="7bca2-128">Handling XML from an xml Type Column by Using ADO.NET</span></span>  
 <span data-ttu-id="7bca2-129">若要 `xml` 使用 ADO.NET 和來處理資料類型資料行中的 XML， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 您可以使用類別的標準行為 `SqlCommand` 。</span><span class="sxs-lookup"><span data-stu-id="7bca2-129">To handle XML from an `xml` data type column by using ADO.NET and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] you can use the standard behavior of the `SqlCommand` class.</span></span> <span data-ttu-id="7bca2-130">例如，使用 `xml` 擷取 `SqlDataReader` 資料類型資料行及其值，就跟擷取 SQL 資料行的方式一樣。不過，如果您想要將 `xml` 資料類型的內容處理為 XML，您就必須先將內容指定為 `XmlReader` 類型。</span><span class="sxs-lookup"><span data-stu-id="7bca2-130">For example, an `xml` data type column and its values can be retrieved in the same way any SQL column is retrieved by using a `SqlDataReader`.However, if you want to work with the contents of an `xml` data type column as XML, you will first have to assign the contents to an `XmlReader` type.</span></span>  
  
 <span data-ttu-id="7bca2-131">如需詳細資訊及範例程式碼，請參閱 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK 文件中的＜資料讀取器中的 XML 資料行值＞。</span><span class="sxs-lookup"><span data-stu-id="7bca2-131">For more information and example code, see "XML Column Values in a Data Reader" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK documentation.</span></span>  
  
## <a name="handling-an-xml-type-column-in-parameters-by-using-adonet"></a><span data-ttu-id="7bca2-132">使用 ADO.NET 處理參數中的 xml 類型資料行</span><span class="sxs-lookup"><span data-stu-id="7bca2-132">Handling an xml Type Column in Parameters by Using ADO.NET</span></span>  
 <span data-ttu-id="7bca2-133">若要以 ADO.NET 和 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 處理傳遞為參數的 xml 資料類型，您可以提供值作為 `SqlXml` 資料類型的例項。</span><span class="sxs-lookup"><span data-stu-id="7bca2-133">To handle an xml data type passed as a parameter in ADO.NET and the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can supply the value as an instance of the `SqlXml` data type.</span></span> <span data-ttu-id="7bca2-134">這裡不牽涉特殊的處理，因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 `xml` 資料類型資料行可以接受與其他資料行及資料類型 (如 `string` 或 `integer`) 相同方式的參數值。</span><span class="sxs-lookup"><span data-stu-id="7bca2-134">No special handling is involved, because `xml` data type columns in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can accept parameter values in the same way as other columns and data types, such as `string` or `integer`.</span></span>  
  
 <span data-ttu-id="7bca2-135">如需詳細資訊及範例程式碼，請參閱 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK 文件中的＜作為命令列參數的 XML 值＞。</span><span class="sxs-lookup"><span data-stu-id="7bca2-135">For more information and example code, see "XML Values as Command Parameters" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bca2-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bca2-136">See Also</span></span>  
 [<span data-ttu-id="7bca2-137">XML 資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7bca2-137">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
