---
title: 資料來源物件 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], data source objects
- SQL Server Native Client, data source objects
- SQLNCLI, data source objects
- SQL Server Native Client OLE DB provider, data source objects
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- CLSID
ms.assetid: c1d4ed20-ad3b-4e33-a26b-38d7517237b7
author: rothja
ms.author: jroth
ms.openlocfilehash: 9cf3f0b0308d655b50149c174547c19966f550ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686920"
---
# <a name="data-source-objects-ole-db"></a><span data-ttu-id="6312d-102">資料來源物件 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="6312d-102">Data Source Objects (OLE DB)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="6312d-103">Native Client 會針對用於建立資料存放區連結的一組 OLE DB 介面（例如），使用「資料來源」一詞 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6312d-103">Native Client uses the term data source for the set of OLE DB interfaces used to establish a link to a data store, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6312d-104">建立提供者之資料來源物件的實例是 Native Client 取用者的第一個工作 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6312d-104">Creating an instance of the data source object of the provider is the first task of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client consumer.</span></span>  
  
 <span data-ttu-id="6312d-105">每個 OLE DB 提供者都會為自己宣告一個類別識別碼 (CLSID)。</span><span class="sxs-lookup"><span data-stu-id="6312d-105">Every OLE DB provider declares a class identifier (CLSID) for itself.</span></span> <span data-ttu-id="6312d-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者的 CLSID 是 C/c + + GUID CLSID_SQLNCLI10 (符號 SQLNCLI_CLSID 會解析成您所參考之 SQLNCLI 檔中的正確 progid) 。</span><span class="sxs-lookup"><span data-stu-id="6312d-106">The CLSID for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider is the C/C++ GUID CLSID_SQLNCLI10 (the symbol SQLNCLI_CLSID will resolve to the correct progid in the sqlncli.h file that you reference).</span></span> <span data-ttu-id="6312d-107">透過 CLSID，取用者會使用 OLE **CoCreateInstance** 函式來製造資料來源物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6312d-107">With the CLSID, the consumer uses the OLE **CoCreateInstance** function to manufacture an instance of the data source object.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="6312d-108">Native Client 是同進程伺服器。</span><span class="sxs-lookup"><span data-stu-id="6312d-108">Native Client is an in-process server.</span></span> <span data-ttu-id="6312d-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者物件的實例是使用 CLSCTX_INPROC_SERVER 宏所建立，以指出可執行檔內容。</span><span class="sxs-lookup"><span data-stu-id="6312d-109">Instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider objects are created using the CLSCTX_INPROC_SERVER macro to indicate the executable context.</span></span>  
  
 <span data-ttu-id="6312d-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者資料來源物件會公開允許取用者連接到現有資料庫的 OLE DB 初始化介面 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6312d-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source object exposes the OLE DB initialization interfaces that allow the consumer to connect to existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="6312d-111">透過 Native Client OLE DB 提供者所建立的每個連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 都會自動設定這些選項：</span><span class="sxs-lookup"><span data-stu-id="6312d-111">Every connection made through the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider sets these options automatically:</span></span>  
  
-   <span data-ttu-id="6312d-112">SET ANSI_WARNINGS ON</span><span class="sxs-lookup"><span data-stu-id="6312d-112">SET ANSI_WARNINGS ON</span></span>  
  
-   <span data-ttu-id="6312d-113">SET ANSI_NULLS ON</span><span class="sxs-lookup"><span data-stu-id="6312d-113">SET ANSI_NULLS ON</span></span>  
  
-   <span data-ttu-id="6312d-114">SET ANSI_PADDING ON</span><span class="sxs-lookup"><span data-stu-id="6312d-114">SET ANSI_PADDING ON</span></span>  
  
-   <span data-ttu-id="6312d-115">SET ANSI_NULL_DFLT_ON ON</span><span class="sxs-lookup"><span data-stu-id="6312d-115">SET ANSI_NULL_DFLT_ON ON</span></span>  
  
-   <span data-ttu-id="6312d-116">SET QUOTED_IDENTIFIER ON</span><span class="sxs-lookup"><span data-stu-id="6312d-116">SET QUOTED_IDENTIFIER ON</span></span>  
  
-   <span data-ttu-id="6312d-117">SET CONCAT_OF_NULL_YIELDS_NULL ON</span><span class="sxs-lookup"><span data-stu-id="6312d-117">SET CONCAT_OF_NULL_YIELDS_NULL ON</span></span>  
  
 <span data-ttu-id="6312d-118">這個範例會使用類別識別碼宏來建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 原生用戶端 OLE DB 提供者資料來源物件，並取得其**IDBInitialize**介面的參考。</span><span class="sxs-lookup"><span data-stu-id="6312d-118">This example uses the class identifier macro to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source object and get a reference to its **IDBInitialize** interface.</span></span>  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 <span data-ttu-id="6312d-119">成功建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者資料來源物件的實例之後，取用者應用程式就可以透過初始化資料來源並建立會話來繼續。</span><span class="sxs-lookup"><span data-stu-id="6312d-119">With successful creation of an instance of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source object, the consumer application can continue by initializing the data source and creating sessions.</span></span> <span data-ttu-id="6312d-120">OLE DB 工作階段會顯示允許資料存取與操作的介面。</span><span class="sxs-lookup"><span data-stu-id="6312d-120">OLE DB sessions present the interfaces that allow data access and manipulation.</span></span>  
  
 <span data-ttu-id="6312d-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 成功初始化資料來源時，使其第一次連接到指定的實例。</span><span class="sxs-lookup"><span data-stu-id="6312d-121">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider makes its first connection to a specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as part of a successful data source initialization.</span></span> <span data-ttu-id="6312d-122">只要在任何資料來源初始化介面上維持參考，或是在呼叫 **IDBInitialize::Uninitialize** 方法前，都會維持連線。</span><span class="sxs-lookup"><span data-stu-id="6312d-122">The connection is maintained as long as a reference is maintained on any data source initialization interface, or until the **IDBInitialize::Uninitialize** method is called.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6312d-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="6312d-123">In This Section</span></span>  
  
-   [<span data-ttu-id="6312d-124">資料來源屬性 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="6312d-124">Data Source Properties &#40;OLE DB&#41;</span></span>](data-source-properties-ole-db.md)  
  
-   [<span data-ttu-id="6312d-125">資料來源資訊屬性</span><span class="sxs-lookup"><span data-stu-id="6312d-125">Data Source Information Properties</span></span>](data-source-information-properties.md)  
  
-   [<span data-ttu-id="6312d-126">初始化和授權屬性</span><span class="sxs-lookup"><span data-stu-id="6312d-126">Initialization and Authorization Properties</span></span>](initialization-and-authorization-properties.md)  
  
-   [<span data-ttu-id="6312d-127">工作階段</span><span class="sxs-lookup"><span data-stu-id="6312d-127">Sessions</span></span>](sessions.md)  
  
-   [<span data-ttu-id="6312d-128">工作階段屬性</span><span class="sxs-lookup"><span data-stu-id="6312d-128">Session Properties</span></span>](session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [<span data-ttu-id="6312d-129">保存的資料來源物件</span><span class="sxs-lookup"><span data-stu-id="6312d-129">Persisted Data Source Objects</span></span>](persisted-data-source-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="6312d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6312d-130">See Also</span></span>  
 [<span data-ttu-id="6312d-131">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="6312d-131">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
