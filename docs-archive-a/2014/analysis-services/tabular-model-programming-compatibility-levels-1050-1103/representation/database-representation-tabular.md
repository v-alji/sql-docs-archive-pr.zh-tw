---
title: 表格式) 的資料庫表示 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 16a233fb-f83b-4ca1-acb5-6186eca0a62c
author: minewiskan
ms.author: owend
ms.openlocfilehash: c327e07685e98e6fa9f992025510e869d909e5ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594231"
---
# <a name="database-representationtabular"></a><span data-ttu-id="95a42-102">資料庫表示法 (表格式)</span><span class="sxs-lookup"><span data-stu-id="95a42-102">Database Representation(Tabular)</span></span>
  <span data-ttu-id="95a42-103">在表格式模式下，資料庫是表格式模型中所有物件的容器。</span><span class="sxs-lookup"><span data-stu-id="95a42-103">In Tabular Mode, the database is the container for all objects in the tabular model.</span></span>  
  
## <a name="database-representation"></a><span data-ttu-id="95a42-104">資料庫表示法</span><span class="sxs-lookup"><span data-stu-id="95a42-104">Database Representation</span></span>  
 <span data-ttu-id="95a42-105">資料庫是形成表格式模型之所有物件所在的地方。</span><span class="sxs-lookup"><span data-stu-id="95a42-105">The database is the place where all objects that form a tabular model reside.</span></span> <span data-ttu-id="95a42-106">開發人員會在資料庫這個容器內尋找物件，諸如連接、資料表、角色等。</span><span class="sxs-lookup"><span data-stu-id="95a42-106">Contained by the database, the developer finds objects like connections, tables, roles and many more.</span></span>  
  
### <a name="database-in-amo"></a><span data-ttu-id="95a42-107">AMO 中的資料庫</span><span class="sxs-lookup"><span data-stu-id="95a42-107">Database in AMO</span></span>  
 <span data-ttu-id="95a42-108">當您使用 AMO 管理表格式模型資料庫時，AMO 中的 <xref:Microsoft.AnalysisServices.Database> 物件與表格式模型中的資料庫邏輯物件會有一對一的相符關係。</span><span class="sxs-lookup"><span data-stu-id="95a42-108">When using AMO to manage a tabular model database, the <xref:Microsoft.AnalysisServices.Database> object in AMO matches one-to-one the database logical object in a tabular model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95a42-109">為了要能夠存取資料庫物件，使用者需要在 AMO 中擁有伺服器物件的存取權並加以連接。</span><span class="sxs-lookup"><span data-stu-id="95a42-109">In order to gain access to a database object, in AMO, the user needs to have access to a server object and connect to it.</span></span>  
  
### <a name="database-in-adomdnet"></a><span data-ttu-id="95a42-110">ADOMD.Net 中的資料庫</span><span class="sxs-lookup"><span data-stu-id="95a42-110">Database in ADOMD.Net</span></span>  
 <span data-ttu-id="95a42-111">當您使用 ADOMD 參照及查詢表格式模型資料庫時，將透過 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 物件取得對特定資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="95a42-111">When using ADOMD to consult and query a tabular model database, connection to a specific database is obtained through the <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> object.</span></span>  
  
 <span data-ttu-id="95a42-112">您可以使用以下程式碼片段直接連接至特定資料庫：</span><span class="sxs-lookup"><span data-stu-id="95a42-112">You can connect directly to a certain database using the following code snippet:</span></span>  
  
```csharp  
using ADOMD = Microsoft.AnalysisServices.AdomdClient;  
...  
   ADOMD.AdomdConnection currrentCnx = new ADOMD.AdomdConnection("Data Source=<<server\instance>>;Catalog=<<database>>");  
   currrentCnx.Open();  
...  
  
```  
  
 <span data-ttu-id="95a42-113">此外，您也可透過現有尚未關閉的連接物件，將目前的資料庫變更為另一個資料庫，如以下程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="95a42-113">Also, over an existing connection object (that hasn't been closed), you can change the current database to another as shown in the following code snippet:</span></span>  
  
```csharp  
currentCnx.ChangeDatabase("myOtherDatabase");  
  
```  
  
## <a name="database-in-amo"></a><span data-ttu-id="95a42-114">AMO 中的資料庫</span><span class="sxs-lookup"><span data-stu-id="95a42-114">Database in AMO</span></span>  
 <span data-ttu-id="95a42-115">當您要使用 AMO 管理資料庫物件時，請從 <xref:Microsoft.AnalysisServices.Server> 物件開始著手。</span><span class="sxs-lookup"><span data-stu-id="95a42-115">When using AMO to manage a database object, start with a <xref:Microsoft.AnalysisServices.Server> object.</span></span> <span data-ttu-id="95a42-116">接著在資料庫集合中搜尋您的資料庫，或透過加入資料庫至該集合的方式建立新的資料庫。</span><span class="sxs-lookup"><span data-stu-id="95a42-116">Then search for your database in the databases collection or create a new database by adding one to the collection.</span></span>  
  
 <span data-ttu-id="95a42-117">下列程式碼片段顯示在檢查資料庫不存在之後，連接到伺服器並建立空資料庫的步驟：</span><span class="sxs-lookup"><span data-stu-id="95a42-117">The following code snippet shows the steps to connect to a server and create an empty database, after checking the database doesn't exist:</span></span>  
  
```  
  
AMO.Server CurrentServer = new AMO.Server();  
try  
{  
    CurrentServer.Connect(currentServerName);  
}  
catch (Exception cnxException)  
{  
    MessageBox.Show(string.Format("Error while trying to connect to server: [{0}]\nError message: {1}", currentServerName, cnxException.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    return;  
}  
newDatabaseName = DatabaseName.Text;  
if (CurrentServer.Databases.Contains(newDatabaseName))  
{  
    return;  
}  
try  
{  
    AMO.Database newDatabase = CurrentServer.Databases.Add(newDatabaseName);  
  
    CurrentServer.Update();  
}  
catch (Exception createDBxc)  
{  
    MessageBox.Show(String.Format("Database [{0}] couldn't be created.\n{1}", newDatabaseName, createDBxc.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    newDatabaseAvailable = false;  
}  
  
```  
  
 <span data-ttu-id="95a42-118">若想實際了解如何使用 AMO 建立及操作資料庫表示法，請參閱「表格式 AMO 2012」範例的原始程式碼，特別要檢查以下的原始程式檔：Database.cs。</span><span class="sxs-lookup"><span data-stu-id="95a42-118">For a practical understanding on how to use AMO to create and manipulate database representations, see source code in the Tabular AMO 2012 sample; specifically check in the following source file: Database.cs.</span></span> <span data-ttu-id="95a42-119">提供此範例程式碼的用意只是為了支援這裡所說明的邏輯概念，您不應將其用於生產環境。</span><span class="sxs-lookup"><span data-stu-id="95a42-119">Sample code is provided only as a support to the logical concepts explained here, and should not be used in a production environment.</span></span>  
  
  
