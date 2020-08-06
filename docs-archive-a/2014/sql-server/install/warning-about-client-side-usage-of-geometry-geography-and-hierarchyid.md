---
title: 有關用戶端使用 GEOMETRY、GEOGRAPHY 和 HIERARCHYID 的警告 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 500ee6b3-2154-45d2-a3cf-8760166d9413
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 66898aa056800c0a7573b5afa73762785706ff7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595409"
---
# <a name="warning-about-client-side-usage-of-geometry-geography-and-hierarchyid"></a><span data-ttu-id="5cea5-102">有關用戶端使用 GEOMETRY、GEOGRAPHY 和 HIERARCHYID 的警告</span><span class="sxs-lookup"><span data-stu-id="5cea5-102">Warning about client side usage of GEOMETRY, GEOGRAPHY and HIERARCHYID</span></span>
  <span data-ttu-id="5cea5-103">元件**Microsoft.SqlServer.Types.dll**（其中包含空間資料類型）已從版本10.0 升級為11.0 版。</span><span class="sxs-lookup"><span data-stu-id="5cea5-103">The assembly **Microsoft.SqlServer.Types.dll**, which contains the spatial data types, has been upgraded from version 10.0 to version 11.0.</span></span> <span data-ttu-id="5cea5-104">當某些條件成立時，參考這個組件的自訂應用程式可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="5cea5-104">Custom applications that reference this assembly may fail when certain conditions are true.</span></span>  
  
## <a name="component"></a><span data-ttu-id="5cea5-105">元件</span><span class="sxs-lookup"><span data-stu-id="5cea5-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="5cea5-106">描述</span><span class="sxs-lookup"><span data-stu-id="5cea5-106">Description</span></span>  
 <span data-ttu-id="5cea5-107">元件**Microsoft.SqlServer.Types.dll**（其中包含空間資料類型）已從版本10.0 升級為11.0 版。</span><span class="sxs-lookup"><span data-stu-id="5cea5-107">The assembly **Microsoft.SqlServer.Types.dll**, which contains the spatial data types, has been upgraded from version 10.0 to version 11.0.</span></span> <span data-ttu-id="5cea5-108">當下列條件成立時，參考這個組件的自訂應用程式可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="5cea5-108">Custom applications that reference this assembly may fail when the following conditions are true.</span></span>  
  
-   <span data-ttu-id="5cea5-109">當您將自訂應用程式從安裝的電腦移 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 至只安裝了的電腦時 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，應用程式將會失敗，因為參考的10.0 版**SqlTypes**元件不存在。</span><span class="sxs-lookup"><span data-stu-id="5cea5-109">When you move a custom application from a computer on which [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] was installed to a computer on which only [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is installed, the application will fail because the referenced version 10.0 of the **SqlTypes** assembly is not present.</span></span> <span data-ttu-id="5cea5-110">您可能會收到下列錯誤訊息：`"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`</span><span class="sxs-lookup"><span data-stu-id="5cea5-110">You may see this error message: `"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`</span></span>  
  
-   <span data-ttu-id="5cea5-111">當您參考**SqlTypes**元件版本11.0，而且也安裝了10.0 版時，您可能會看到此錯誤訊息：`"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`</span><span class="sxs-lookup"><span data-stu-id="5cea5-111">When you reference the **SqlTypes** assembly version 11.0, and version 10.0 is also installed, you may see this error message: `"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`</span></span>  
  
-   <span data-ttu-id="5cea5-112">當您從以 .NET 3.5、4或4.5 為目標的自訂應用程式參考**SqlTypes**元件版本11.0 時，應用程式將會失敗，因為 SqlClient 的設計會載入版本10.0 的元件。</span><span class="sxs-lookup"><span data-stu-id="5cea5-112">When you reference the **SqlTypes** assembly version 11.0 from a custom application that targets .NET 3.5, 4, or 4.5, the application will fail because SqlClient by design loads version 10.0 of the assembly.</span></span> <span data-ttu-id="5cea5-113">當應用程式呼叫下列其中一個方法時，就會發生這項失敗：</span><span class="sxs-lookup"><span data-stu-id="5cea5-113">This failure occurs when the application calls one of the following methods:</span></span>  
  
    -   <span data-ttu-id="5cea5-114">`GetValue` 類別的 `SqlDataReader` 方法</span><span class="sxs-lookup"><span data-stu-id="5cea5-114">`GetValue` method of the `SqlDataReader` class</span></span>  
  
    -   <span data-ttu-id="5cea5-115">`GetValues` 類別的 `SqlDataReader` 方法</span><span class="sxs-lookup"><span data-stu-id="5cea5-115">`GetValues` method of the `SqlDataReader` class</span></span>  
  
    -   <span data-ttu-id="5cea5-116">`SqlDataReader` 類別的括號索引運算子 []</span><span class="sxs-lookup"><span data-stu-id="5cea5-116">bracket index operator [] of the `SqlDataReader` class</span></span>  
  
    -   <span data-ttu-id="5cea5-117">`ExecuteScalar` 類別的 `SqlCommand` 方法</span><span class="sxs-lookup"><span data-stu-id="5cea5-117">`ExecuteScalar` method of the `SqlCommand` class</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="5cea5-118">更正動作</span><span class="sxs-lookup"><span data-stu-id="5cea5-118">Corrective Action</span></span>  
 <span data-ttu-id="5cea5-119">您可以使用下列其中一個方法來解決這個問題：</span><span class="sxs-lookup"><span data-stu-id="5cea5-119">You can work around this issue by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="5cea5-120">您可以在程式碼中呼叫 `GetSqlBytes` 方法 (而非上列 Get 方法) 來擷取 CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統類型，藉以解決此問題，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5cea5-120">You can work around this issue in your code by calling the `GetSqlBytes` method, instead of the Get methods listed above, to retrieve CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system types, as shown in the following example:</span></span>  
  
    ```csharp  
    string query = "SELECT [SpatialColumn] FROM [SpatialTable]";  
          using (SqlConnection conn = new SqlConnection("..."))  
          {  
                SqlCommand cmd = new SqlCommand(query, conn);  
  
                conn.Open();  
                SqlDataReader reader = cmd.ExecuteReader();  
  
                while (reader.Read())  
                {  
                      // In version 11.0 only  
                      SqlGeometry g =   
    SqlGeometry.Deserialize(reader.GetSqlBytes(0));  
  
                      // In version 10.0 or 11.0  
                      SqlGeometry g2 = new SqlGeometry();  
                      g.Read(new BinaryReader(reader.GetSqlBytes(0).Stream));  
                }  
          }  
    ```  
  
-   <span data-ttu-id="5cea5-121">您可以在應用程式組態檔中使用組件重新導向，藉以解決此問題，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5cea5-121">You can work around this issue by using assembly redirection in the application configuration file, as shown in the following example:</span></span>  
  
    ```xml  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
        ...  
        <dependentAssembly>  
            <assemblyIdentity name="Microsoft.SqlServer.Types" publicKeyToken="89845dcd8080cc91" culture="neutral" />  
            <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />  
        </dependentAssembly>  
        ...  
    </assemblyBinding>  
    ```  
  
-   <span data-ttu-id="5cea5-122">您可以在連接字串中針對 "Type System Version" 屬性指定 "SQL Server 2012" 值，強制 SqlClient 載入組件 11.0 版，藉以解決此問題。</span><span class="sxs-lookup"><span data-stu-id="5cea5-122">You can work around this issue in your connection string by specifying a value of "SQL Server 2012" for the "Type System Version" attribute to force SqlClient to load version 11.0 of the assembly.</span></span> <span data-ttu-id="5cea5-123">此連接字串屬性僅適用於 .NET 4.5 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="5cea5-123">This connection string attribute is available only in .NET 4.5 and above.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cea5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cea5-124">See Also</span></span>  
 <span data-ttu-id="5cea5-125">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="5cea5-125">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="5cea5-126">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="5cea5-126">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md
)  
  
  
