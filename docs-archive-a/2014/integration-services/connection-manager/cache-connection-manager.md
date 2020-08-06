---
title: 快取連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Cache connection manager
ms.assetid: bdc92038-3720-4795-8a5c-79b963f2c952
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b8a7cc8bbe9e93c385fca6257e0be2e79bd3148a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596217"
---
# <a name="cache-connection-manager"></a><span data-ttu-id="a9477-102">快取連接管理員</span><span class="sxs-lookup"><span data-stu-id="a9477-102">Cache Connection Manager</span></span>
  <span data-ttu-id="a9477-103">快取連接管理員會從快取轉換或快取檔案 (.caw) 中讀取資料，而且可以將資料儲存至快取檔案。</span><span class="sxs-lookup"><span data-stu-id="a9477-103">The Cache connection manager reads data from the Cache transform or from a cache file (.caw), and can save the data to a cache file.</span></span> <span data-ttu-id="a9477-104">不論您是否將快取連接管理員設定為使用快取檔案，資料一定會儲存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="a9477-104">Whether you configure the Cache connection manager to use a cache file, the data is always stored in memory.</span></span>  
  
 <span data-ttu-id="a9477-105">「快取轉換」轉換會將資料流程中已連接之資料來源的資料寫入快取連接管理員。</span><span class="sxs-lookup"><span data-stu-id="a9477-105">The Cache Transform transformation writes data from a connected data source in the data flow to a Cache connection manager.</span></span> <span data-ttu-id="a9477-106">封裝中的「查閱」轉換會在資料上執行查閱。</span><span class="sxs-lookup"><span data-stu-id="a9477-106">The Lookup transformation in a package performs lookups on the data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9477-107">快取連接管理員不支援二進位大型物件 (BLOB) 資料類型 DT_TEXT、DT_NTEXT 和 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="a9477-107">The Cache connection manager does not support the Binary Large Object (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE.</span></span> <span data-ttu-id="a9477-108">如果參考資料集包含 BLOB 資料類型，則在您執行封裝時元件會失敗。</span><span class="sxs-lookup"><span data-stu-id="a9477-108">If the reference dataset contains a BLOB data type, the component will fail when you run the package.</span></span> <span data-ttu-id="a9477-109">您可以使用 **[快取連接管理員編輯器]** 修改資料行資料類型。</span><span class="sxs-lookup"><span data-stu-id="a9477-109">You can use the **Cache Connection Manager Editor** to modify column data types.</span></span> <span data-ttu-id="a9477-110">如需詳細資訊，請參閱 [快取連線管理員編輯器](../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="a9477-110">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9477-111">封裝保護等級不會套用至快取檔案。</span><span class="sxs-lookup"><span data-stu-id="a9477-111">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="a9477-112">如果快取檔案包含機密資訊，請使用存取控制清單 (ACL) 限制對其中儲存檔案的位置或資料夾的存取權。</span><span class="sxs-lookup"><span data-stu-id="a9477-112">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="a9477-113">您應該只啟用特定帳戶的存取權。</span><span class="sxs-lookup"><span data-stu-id="a9477-113">You should enable access only to certain accounts.</span></span> <span data-ttu-id="a9477-114">如需詳細資訊，請參閱 [對封裝使用之檔案的存取權](../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="a9477-114">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
## <a name="configuration-of-the-cache-connection-manager"></a><span data-ttu-id="a9477-115">快取連接管理員的組態</span><span class="sxs-lookup"><span data-stu-id="a9477-115">Configuration of the Cache Connection Manager</span></span>  
 <span data-ttu-id="a9477-116">您可以利用下列方式設定快取連接管理員：</span><span class="sxs-lookup"><span data-stu-id="a9477-116">You can configure the Cache connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="a9477-117">指出是否要使用快取檔案。</span><span class="sxs-lookup"><span data-stu-id="a9477-117">Indicate whether to use a cache file.</span></span>  
  
     <span data-ttu-id="a9477-118">如果您將快取連接管理員設定為使用快取檔案，連接管理員將進行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="a9477-118">If you configure the cache connection manager to use a cache file, the connection manager will do one of the following actions:</span></span>  
  
    -   <span data-ttu-id="a9477-119">當「快取轉換」轉換設定為將資料流程中資料來源的資料寫入快取連接管理員時，將資料儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="a9477-119">Save data to the file when a Cache Transform transformation is configured to write data from a data source in the data flow to the Cache connection manager.</span></span>  
  
    -   <span data-ttu-id="a9477-120">從快取檔案中讀取資料。</span><span class="sxs-lookup"><span data-stu-id="a9477-120">Read data from the cache file.</span></span>  
  
     <span data-ttu-id="a9477-121">如需詳細資訊，請參閱 [Cache Transform](../data-flow/transformations/cache-transform.md)。</span><span class="sxs-lookup"><span data-stu-id="a9477-121">For more information, see [Cache Transform](../data-flow/transformations/cache-transform.md).</span></span>  
  
-   <span data-ttu-id="a9477-122">變更儲存在快取中的資料行的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a9477-122">Change metadata for the columns stored in the cache.</span></span>  
  
-   <span data-ttu-id="a9477-123">在執行階段更新快取檔案名稱，其方法是使用運算式來設定 ConnectionString 屬性。</span><span class="sxs-lookup"><span data-stu-id="a9477-123">Update the cache file name at runtime by using an expression to set the ConnectionString property.</span></span> <span data-ttu-id="a9477-124">如需詳細資訊，請參閱 [在封裝中使用屬性運算式](../expressions/use-property-expressions-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="a9477-124">For more information, see [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md).</span></span>  
  
 <span data-ttu-id="a9477-125">您可以透過 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="a9477-125">You can set properties through [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="a9477-126">如需可在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 設計師中設定之屬性的詳細資訊，請參閱 [快取連線管理員編輯器](../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="a9477-126">For more information about the properties that you can set in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="a9477-127">如需如何以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和[以程式設計方式新增連線](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="a9477-127">For information about how to configure a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="a9477-128">相關工作</span><span class="sxs-lookup"><span data-stu-id="a9477-128">Related Tasks</span></span>  
 [<span data-ttu-id="a9477-129">使用快取連線管理員以完整快取模式實作查閱轉換</span><span class="sxs-lookup"><span data-stu-id="a9477-129">Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager</span></span>](lookup-transformation-full-cache-mode-ole-db-connection-manager.md)  
  
  
