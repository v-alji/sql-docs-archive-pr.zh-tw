---
title: 使用 ADO 搭配 SQL Server Native Client |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, ADO
- data access [SQL Server Native Client], ADO
- ADO [SQL Server Native Client]
- SQLNCLI, ADO
ms.assetid: 118a7cac-4c0d-44fd-b63e-3d542932d239
author: rothja
ms.author: jroth
ms.openlocfilehash: ccd14432aa3541572467a4c651c1f48b1ac957f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706385"
---
# <a name="using-ado-with-sql-server-native-client"></a><span data-ttu-id="8822b-102">使用 ADO 搭配 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="8822b-102">Using ADO with SQL Server Native Client</span></span>
  <span data-ttu-id="8822b-103">為了利用中引進的新功能 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] （例如，多個 active result sets (MARS) 、查詢通知、使用者定義型別 (udt) 或新的**xml**資料型別，使用 ActiveX Data Objects (ADO) 的現有應用程式應該使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者作為其資料存取提供者。</span><span class="sxs-lookup"><span data-stu-id="8822b-103">In order to take advantage of new features introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] such as multiple active result sets (MARS), query notifications, user-defined types (UDTs), or the new **xml** data type, existing applications that use ActiveX Data Objects (ADO) should use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider as their data access provider.</span></span>  
  
 <span data-ttu-id="8822b-104">如果您不需要使用 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 所導入的任何新功能，就不需要使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者。您可以繼續使用目前的資料存取提供者 (通常是 SQLOLEDB)。</span><span class="sxs-lookup"><span data-stu-id="8822b-104">If you do not need to use any of the new features introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], there is no need to use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider; you can continue using your current data access provider, which is typically SQLOLEDB.</span></span> <span data-ttu-id="8822b-105">如果您要強化現有的應用程式，而且需要使用 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 所導入的新功能，就應該使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="8822b-105">If you are enhancing an existing application and you need to use the new features introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], you should use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8822b-106">如果您正在開發新的應用程式，建議您考慮使用 ADO.NET 和 .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 來取代 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client，以便存取最新 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本的所有新功能。</span><span class="sxs-lookup"><span data-stu-id="8822b-106">If you are developing a new application, it is recommended that you consider using ADO.NET and the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instead of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to access all the new features of recent versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8822b-107">如需有關 .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的詳細資訊，請參閱 ADO.NET 的 .NET Framework SDK 文件集。</span><span class="sxs-lookup"><span data-stu-id="8822b-107">For more information about the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see the .NET Framework SDK documentation for ADO.NET.</span></span>  
  
 <span data-ttu-id="8822b-108">為了讓 ADO 使用最新 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本的新功能，我們已經對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者新增了一些增強功能，以便擴充 OLE DB 的核心功能。</span><span class="sxs-lookup"><span data-stu-id="8822b-108">To enable ADO to use new features of recent versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], some enhancements have been made to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider which extends the core features of OLE DB.</span></span> <span data-ttu-id="8822b-109">這些增強功能可讓 ADO 應用程式使用較新的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能，以及取用 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 所導入的兩種資料類型：**xml** 和 **udt**。</span><span class="sxs-lookup"><span data-stu-id="8822b-109">These enhancements allow ADO applications to use newer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features and to consume two data types introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]: **xml** and **udt**.</span></span> <span data-ttu-id="8822b-110">這些增強功能也會利用 **varchar**、**nvarchar** 和 **varbinary** 資料類型的增強功能。</span><span class="sxs-lookup"><span data-stu-id="8822b-110">These enhancements also exploit enhancements to the **varchar**, **nvarchar**, and **varbinary** data types.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="8822b-111">Native Client 會將 SSPROP_INIT_DATATYPECOMPATIBILITY 初始化屬性加入至 ADO 應用程式所使用的 DBPROPSET_SQLSERVERDBINIT 屬性集，以便以與 ADO 相容的方式來公開新的資料類型。</span><span class="sxs-lookup"><span data-stu-id="8822b-111">Native Client adds the SSPROP_INIT_DATATYPECOMPATIBILITY initialization property to the DBPROPSET_SQLSERVERDBINIT property set for use by ADO applications so that the new data types are exposed in a way compatible with ADO.</span></span> <span data-ttu-id="8822b-112">此外， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者也會定義名為的新連接字串關鍵字，此關鍵字 `DataTypeCompatibility` 會在連接字串中設定。</span><span class="sxs-lookup"><span data-stu-id="8822b-112">In addition, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider also defines a new connection string keyword named `DataTypeCompatibility` that is set in the connection string.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8822b-113">現有的 ADO 應用程式可以使用 SQLOLEDB 提供者來存取並更新 XML、UDT 和大數值文字與二進位欄位值。</span><span class="sxs-lookup"><span data-stu-id="8822b-113">Existing ADO applications can access and update XML, UDT, and large value text and binary field values using the SQLOLEDB provider.</span></span> <span data-ttu-id="8822b-114">新的較大 **varchar(max)** 、**nvarchar(max)** 和 **varbinary(max)** 資料類型會分別傳回成 ADO 類型 **adLongVarChar**、**adLongVarWChar** 和 **adLongVarBinary**。</span><span class="sxs-lookup"><span data-stu-id="8822b-114">The new larger **varchar(max)**, **nvarchar(max)**, and **varbinary(max)** data types are returned as the ADO types **adLongVarChar**, **adLongVarWChar** and **adLongVarBinary** respectively.</span></span> <span data-ttu-id="8822b-115">XML 資料行會傳回成 **adLongVarChar**，而且 UDT 資料行會傳回成 **adVarBinary**。</span><span class="sxs-lookup"><span data-stu-id="8822b-115">XML columns are returned as **adLongVarChar**, and UDT columns are returned as **adVarBinary**.</span></span> <span data-ttu-id="8822b-116">不過，如果您使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者 (SQLNCLI11) 來取代 SQLOLEDB，請務必將 `DataTypeCompatibility` 關鍵字設定為 "80"，以便新的資料類型會正確對應至 ADO 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8822b-116">However, if you use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider (SQLNCLI11) instead of SQLOLEDB, you need to make sure to set the `DataTypeCompatibility` keyword to "80" so that the new data types will map correctly to the ADO data types.</span></span>  
  
## <a name="enabling-sql-server-native-client-from-ado"></a><span data-ttu-id="8822b-117">從 ADO 啟用 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="8822b-117">Enabling SQL Server Native Client from ADO</span></span>  
 <span data-ttu-id="8822b-118">若要啟用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 的使用，ADO 應用程式必須在其連接字串中執行下列關鍵字：</span><span class="sxs-lookup"><span data-stu-id="8822b-118">To enable the usage of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, ADO applications will need to implement the following keywords in their connection strings:</span></span>  
  
-   `Provider=SQLNCLI11`  
  
-   `DataTypeCompatibility=80`  
  
 <span data-ttu-id="8822b-119">如需 Native Client 中支援的 ADO 連接字串關鍵字的詳細資訊 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，請參閱搭配[使用連接字串關鍵字與 SQL Server Native Client](using-connection-string-keywords-with-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="8822b-119">For more information about the ADO connections string keywords supported in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, see [Using Connection String Keywords with SQL Server Native Client](using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="8822b-120">以下範例會建立完全啟用以搭配 Native Client 使用的 ADO 連接字串 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，包括啟用 MARS 功能：</span><span class="sxs-lookup"><span data-stu-id="8822b-120">The following is an example of establishing an ADO connection string that is fully enabled to work with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, including the enabling of the MARS feature:</span></span>  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
```  
  
## <a name="examples"></a><span data-ttu-id="8822b-121">範例</span><span class="sxs-lookup"><span data-stu-id="8822b-121">Examples</span></span>  
 <span data-ttu-id="8822b-122">下列各節提供如何使用 ADO 搭配 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者的範例。</span><span class="sxs-lookup"><span data-stu-id="8822b-122">The following sections provide examples of how you can use ADO with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>  
  
### <a name="retrieving-xml-column-data"></a><span data-ttu-id="8822b-123">擷取 XML 資料行資料</span><span class="sxs-lookup"><span data-stu-id="8822b-123">Retrieving XML Column Data</span></span>  
 <span data-ttu-id="8822b-124">在這個範例中，使用了資料錄集來擷取並顯示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks** 範例資料庫中 XML 資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="8822b-124">In this example, a recordset is used to retrieve and display the data from an XML column in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks** sample database.</span></span>  
  
```  
Dim con As New ADODB.Connection  
Dim rst As New ADODB.Recordset  
Dim sXMLResult As String  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _   
         & "DataTypeCompatibility=80;"  
  
con.Open  
  
' Get the xml data as a recordset.  
Set rst.ActiveConnection = con  
rst.Source = "SELECT AdditionalContactInfo FROM Person.Contact " _  
   & "WHERE AdditionalContactInfo IS NOT NULL"  
rst.Open  
  
' Display the data in the recordset.  
While (Not rst.EOF)  
   sXMLResult = rst.Fields("AdditionalContactInfo").Value  
   Debug.Print (sXMLResult)  
   rst.MoveNext  
End While  
  
con.Close  
Set con = Nothing  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8822b-125">XML 資料行不支援資料錄集篩選。</span><span class="sxs-lookup"><span data-stu-id="8822b-125">Recordset filtering is not supported with XML columns.</span></span> <span data-ttu-id="8822b-126">如果已使用，就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="8822b-126">If used, an error will be returned.</span></span>  
  
### <a name="retrieving-udt-column-data"></a><span data-ttu-id="8822b-127">擷取 UDT 資料行資料</span><span class="sxs-lookup"><span data-stu-id="8822b-127">Retrieving UDT Column Data</span></span>  
 <span data-ttu-id="8822b-128">在這個範例中，使用了 **Command** 物件來執行可傳回 UDT 的 SQL 查詢、更新 UDT 資料，然後將新的資料插回資料庫中。</span><span class="sxs-lookup"><span data-stu-id="8822b-128">In this example, a **Command** object is used to execute a SQL query that returns a UDT, the UDT data is updated, and then the new data is inserted back into the database.</span></span> <span data-ttu-id="8822b-129">這個範例會假設已經在資料庫中註冊了 **Point** UDT。</span><span class="sxs-lookup"><span data-stu-id="8822b-129">This example assumes that the **Point** UDT has already been registered in the database.</span></span>  
  
```  
Dim con As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
Dim strOldUDT As String  
Dim strNewUDT As String  
Dim aryTempUDT() As String  
Dim strTempID As String  
Dim i As Integer  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;"  
  
con.Open  
  
' Get the UDT value.  
Set cmd.ActiveConnection = con  
cmd.CommandText = "SELECT ID, Pnt FROM dbo.Points.ToString()"  
Set rst = cmd.Execute  
strTempID = rst.Fields(0).Value  
strOldUDT = rst.Fields(1).Value  
  
' Do something with the UDT by adding i to each point.  
arytempUDT = Split(strOldUDT, ",")  
i = 3  
strNewUDT = LTrim(Str(Int(aryTempUDT(0)) + i)) + "," + _  
   LTrim(Str(Int(aryTempUDT(1)) + i))  
  
' Insert the new value back into the database.  
cmd.CommandText = "UPDATE dbo.Points SET Pnt = '" + strNewUDT + _  
   "' WHERE ID = '" + strTempID + "'"  
cmd.Execute  
  
con.Close  
Set con = Nothing  
```  
  
### <a name="enabling-and-using-mars"></a><span data-ttu-id="8822b-130">啟用並使用 MARS</span><span class="sxs-lookup"><span data-stu-id="8822b-130">Enabling and Using MARS</span></span>  
 <span data-ttu-id="8822b-131">在此範例中，連接字串的結構是為了透過 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者啟用 MARS，然後建立兩個記錄集物件，以便使用相同的連接來執行。</span><span class="sxs-lookup"><span data-stu-id="8822b-131">In this example, the connection string is constructed to enable MARS through the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, and then two recordset objects are created to execute using the same connection.</span></span>  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
  
Dim recordset1 As New ADODB.Recordset  
Dim recordset2 As New ADODB.Recordset  
  
Dim recordsaffected As Integer  
Set recordset1 =  con.Execute("SELECT * FROM Table1", recordsaffected, adCmdText)  
Set recordset2 =  con.Execute("SELECT * FROM Table2", recordsaffected, adCmdText)  
  
con.Close  
Set con = Nothing  
```  
  
 <span data-ttu-id="8822b-132">在舊版 OLE DB 提供者中，此程式碼會導致系統在第二次執行時建立隱含連接，因為每個單一連接只能開啟一個作用中結果集。</span><span class="sxs-lookup"><span data-stu-id="8822b-132">In prior versions of the OLE DB provider, this code would cause an implicit connection to be created on the second execution because only one active set of results could be opened per a single connection.</span></span> <span data-ttu-id="8822b-133">由於隱含連接不會在 OLE DB 連接集區中共用，所以這會產生額外的負擔。</span><span class="sxs-lookup"><span data-stu-id="8822b-133">Because the implicit connection was not pooled in the OLE DB connection pool this would cause additional overhead.</span></span> <span data-ttu-id="8822b-134">使用 Native Client OLE DB 提供者所公開的 MARS 功能時 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，您會在單一連接上收到多個作用中結果。</span><span class="sxs-lookup"><span data-stu-id="8822b-134">With the MARS feature exposed by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, you get multiple active results on the one connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8822b-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8822b-135">See Also</span></span>  
 [<span data-ttu-id="8822b-136">使用 SQL Server Native Client 建置應用程式</span><span class="sxs-lookup"><span data-stu-id="8822b-136">Building Applications with SQL Server Native Client</span></span>](building-applications-with-sql-server-native-client.md)  
  
  
