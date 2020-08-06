---
title: 快取連線管理員編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cacheconnection.f1
ms.assetid: 0d8f9324-0c35-4eea-b06d-da3cc2426d2c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 38a858217925496d8dd937d684368bdb2e061b14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599634"
---
# <a name="cache-connection-manager-editor"></a><span data-ttu-id="e301c-102">快取連接管理員編輯器</span><span class="sxs-lookup"><span data-stu-id="e301c-102">Cache Connection Manager Editor</span></span>
  <span data-ttu-id="e301c-103">快取連接管理員會從快取轉換或快取檔案 (.caw) 中讀取參考資料集，而且可以將資料儲存至快取檔案。</span><span class="sxs-lookup"><span data-stu-id="e301c-103">The Cache connection manager reads a reference dataset from the Cache transform or from a cache file (.caw), and can save the data to a cache file.</span></span> <span data-ttu-id="e301c-104">資料永遠會儲存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="e301c-104">The data is always stored in memory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e301c-105">快取連接管理員不支援二進位大型物件 (BLOB) 資料類型 DT_TEXT、DT_NTEXT 和 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="e301c-105">The Cache connection manager does not support the Binary Large Object (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE.</span></span> <span data-ttu-id="e301c-106">如果參考資料集包含 BLOB 資料類型，則在您執行封裝時元件會失敗。</span><span class="sxs-lookup"><span data-stu-id="e301c-106">If the reference dataset contains a BLOB data type, the component will fail when you run the package.</span></span> <span data-ttu-id="e301c-107">您可以使用 **[快取連接管理員編輯器]** 修改資料行資料類型。</span><span class="sxs-lookup"><span data-stu-id="e301c-107">You can use the **Cache Connection Manager Editor** to modify column data types.</span></span>  
  
 <span data-ttu-id="e301c-108">查閱轉換會針對參考資料集執行查閱。</span><span class="sxs-lookup"><span data-stu-id="e301c-108">The Lookup transformation performs lookups on the reference dataset.</span></span>  
  
 <span data-ttu-id="e301c-109">[快取連線管理員編輯器]\*\*\*\* 對話方塊包含下列索引標籤：</span><span class="sxs-lookup"><span data-stu-id="e301c-109">The **Cache Connection ManagerEditor** dialog box includes the following tabs:</span></span>  
  
-   <span data-ttu-id="e301c-110">[[一般] 索引標籤](#generaltab)</span><span class="sxs-lookup"><span data-stu-id="e301c-110">[General tab](#generaltab)</span></span>  
  
-   [<span data-ttu-id="e301c-111">資料行索引標籤</span><span class="sxs-lookup"><span data-stu-id="e301c-111">Columns tab</span></span>](#columnstab)  
  
 <span data-ttu-id="e301c-112">若要深入瞭解快取連線管理員，請參閱快取[連線管理員](connection-manager/cache-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="e301c-112">To learn more about the Cache Connection Manager, see [Cache Connection Manager](connection-manager/cache-connection-manager.md).</span></span>  
  
##  <a name="general-tab"></a><a name="generaltab"></a><span data-ttu-id="e301c-113">[一般] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="e301c-113">General Tab</span></span>  
 <span data-ttu-id="e301c-114">使用 [快取連線管理員編輯器]\*\*\*\* 對話方塊的 [一般]\*\*\*\* 索引標籤即可指出要從檔案中讀取快取，還是要將快取儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="e301c-114">Use the **General** tab of the **Cache Connection ManagerEditor** dialog box to indicate whether to read the cache from a file or save the cache to a file.</span></span>  
  
### <a name="options"></a><span data-ttu-id="e301c-115">選項。</span><span class="sxs-lookup"><span data-stu-id="e301c-115">Options</span></span>  
 <span data-ttu-id="e301c-116">**連線管理員名稱**</span><span class="sxs-lookup"><span data-stu-id="e301c-116">**Connection manager name**</span></span>  
 <span data-ttu-id="e301c-117">提供唯一的名稱給工作流程中的快取連接。</span><span class="sxs-lookup"><span data-stu-id="e301c-117">Provide a unique name for the cache connection in the workflow.</span></span> <span data-ttu-id="e301c-118">提供的名稱將顯示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師內。</span><span class="sxs-lookup"><span data-stu-id="e301c-118">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="e301c-119">**說明**</span><span class="sxs-lookup"><span data-stu-id="e301c-119">**Description**</span></span>  
 <span data-ttu-id="e301c-120">描述連接。</span><span class="sxs-lookup"><span data-stu-id="e301c-120">Describe the connection.</span></span> <span data-ttu-id="e301c-121">最佳作法是根據其用途描述連接，使封裝可以自我記錄並易於維護。</span><span class="sxs-lookup"><span data-stu-id="e301c-121">As a best practice, describe the connection according to its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="e301c-122">**使用檔案快取**</span><span class="sxs-lookup"><span data-stu-id="e301c-122">**Use file cache**</span></span>  
 <span data-ttu-id="e301c-123">指出是否要使用快取檔案。</span><span class="sxs-lookup"><span data-stu-id="e301c-123">Indicate whether to use a cache file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e301c-124">封裝保護等級不會套用至快取檔案。</span><span class="sxs-lookup"><span data-stu-id="e301c-124">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="e301c-125">如果快取檔案包含機密資訊，請使用存取控制清單 (ACL) 限制對其中儲存檔案的位置或資料夾的存取權。</span><span class="sxs-lookup"><span data-stu-id="e301c-125">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="e301c-126">您應該只啟用特定帳戶的存取權。</span><span class="sxs-lookup"><span data-stu-id="e301c-126">You should enable access only to certain accounts.</span></span> <span data-ttu-id="e301c-127">如需詳細資訊，請參閱 [對封裝使用之檔案的存取權](../../2014/integration-services/access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="e301c-127">For more information, see [Access to Files Used by Packages](../../2014/integration-services/access-to-files-used-by-packages.md).</span></span>  
  
 <span data-ttu-id="e301c-128">如果您將快取連接管理員設定為使用快取檔案，連接管理員將進行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="e301c-128">If you configure the cache connection manager to use a cache file, the connection manager will do one of the following actions:</span></span>  
  
-   <span data-ttu-id="e301c-129">當「快取轉換」轉換設定為將資料流程中資料來源的資料寫入快取連接管理員時，將資料儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="e301c-129">Save data to the file when a Cache Transform transformation is configured to write data from a data source in the data flow to the Cache connection manager.</span></span> <span data-ttu-id="e301c-130">如需詳細資訊，請參閱 [Cache Transform](data-flow/transformations/cache-transform.md)。</span><span class="sxs-lookup"><span data-stu-id="e301c-130">For more information, see [Cache Transform](data-flow/transformations/cache-transform.md).</span></span>  
  
-   <span data-ttu-id="e301c-131">從快取檔案中讀取資料。</span><span class="sxs-lookup"><span data-stu-id="e301c-131">Read data from the cache file.</span></span>  
  
 <span data-ttu-id="e301c-132">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="e301c-132">**File name**</span></span>  
 <span data-ttu-id="e301c-133">輸入快取檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e301c-133">Type the path and file name of the cache file.</span></span>  
  
 <span data-ttu-id="e301c-134">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="e301c-134">**Browse**</span></span>  
 <span data-ttu-id="e301c-135">找出快取檔案。</span><span class="sxs-lookup"><span data-stu-id="e301c-135">Locate the cache file.</span></span>  
  
 <span data-ttu-id="e301c-136">**重新整理中繼資料**</span><span class="sxs-lookup"><span data-stu-id="e301c-136">**Refresh Metadata**</span></span>  
 <span data-ttu-id="e301c-137">在快取連接管理員中，刪除資料行中繼資料，然後將選取快取檔案的資料行中繼資料重新填入快取連接管理員。</span><span class="sxs-lookup"><span data-stu-id="e301c-137">Delete the column metadata in the Cache connection manager and repopulate the Cache connection manager with column metadata from a selected cache file.</span></span>  
  
##  <a name="columns-tab"></a><a name="columnstab"></a><span data-ttu-id="e301c-138">資料行索引標籤</span><span class="sxs-lookup"><span data-stu-id="e301c-138">Columns Tab</span></span>  
 <span data-ttu-id="e301c-139">使用 **[快取連接管理員編輯器]** 對話方塊的 **[資料行]** 索引標籤即可設定快取中每個資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="e301c-139">Use the **Columns** tab of the **Cache Connection Manager Editor** dialog box to configure the properties of each column in the cache.</span></span>  
  
### <a name="options"></a><span data-ttu-id="e301c-140">選項。</span><span class="sxs-lookup"><span data-stu-id="e301c-140">Options</span></span>  
 <span data-ttu-id="e301c-141">**資料行**</span><span class="sxs-lookup"><span data-stu-id="e301c-141">**Column**</span></span>  
 <span data-ttu-id="e301c-142">指定資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="e301c-142">Specify the column name.</span></span>  
  
 <span data-ttu-id="e301c-143">**索引位置**</span><span class="sxs-lookup"><span data-stu-id="e301c-143">**Index Position**</span></span>  
 <span data-ttu-id="e301c-144">指定每個資料行的索引位置，藉以指定哪些資料行是索引資料行。</span><span class="sxs-lookup"><span data-stu-id="e301c-144">Specify which columns are index columns by specifying the index position of each column.</span></span> <span data-ttu-id="e301c-145">此索引是一或多個資料行的集合。</span><span class="sxs-lookup"><span data-stu-id="e301c-145">The index is a collection of one or more columns.</span></span>  
  
 <span data-ttu-id="e301c-146">如果是非索引資料行，索引位置為 0。</span><span class="sxs-lookup"><span data-stu-id="e301c-146">For non-index columns, the index position is 0.</span></span>  
  
 <span data-ttu-id="e301c-147">如果是索引資料行，則索引位置是循序的正數。</span><span class="sxs-lookup"><span data-stu-id="e301c-147">For index columns, the index position is a sequential, positive number.</span></span> <span data-ttu-id="e301c-148">這個數目表示查閱轉換比較參考資料集中的資料列與輸入資料來源中的資料列所依據的順序。</span><span class="sxs-lookup"><span data-stu-id="e301c-148">This number indicates the order in which the Lookup transformation compares rows in the reference dataset to rows in the input data source.</span></span> <span data-ttu-id="e301c-149">擁有最多唯一值的資料行應該有最低的索引位置。</span><span class="sxs-lookup"><span data-stu-id="e301c-149">The column with the most unique values should have the lowest index position.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e301c-150">當查閱轉換是設定為使用快取連接管理員，則只有參考資料集中的索引資料行可以對應到輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="e301c-150">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="e301c-151">而且，所有的索引資料行都必須進行對應。</span><span class="sxs-lookup"><span data-stu-id="e301c-151">Also, all index columns must be mapped.</span></span>  
  
 <span data-ttu-id="e301c-152">**型別**</span><span class="sxs-lookup"><span data-stu-id="e301c-152">**Type**</span></span>  
 <span data-ttu-id="e301c-153">指定資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e301c-153">Specify the data type of the column.</span></span>  
  
 `Length`  
 <span data-ttu-id="e301c-154">指定資料行資料類型。</span><span class="sxs-lookup"><span data-stu-id="e301c-154">Specifies the column data type.</span></span> <span data-ttu-id="e301c-155">如果適用於資料類型，您可以更新 `Length`。</span><span class="sxs-lookup"><span data-stu-id="e301c-155">If applicable to the data type, you can update `Length`.</span></span>  
  
 `Precision`  
 <span data-ttu-id="e301c-156">針對特定資料行資料類型指定有效位數。</span><span class="sxs-lookup"><span data-stu-id="e301c-156">Specifies the precision for certain column data types.</span></span> <span data-ttu-id="e301c-157">位數 (Precision) 是指數字中總共的位數。</span><span class="sxs-lookup"><span data-stu-id="e301c-157">Precision is the number of digits in a number.</span></span> <span data-ttu-id="e301c-158">如果適用於資料類型，您可以更新 `Precision`。</span><span class="sxs-lookup"><span data-stu-id="e301c-158">If applicable to the data type, you can update `Precision`.</span></span>  
  
 `Scale`  
 <span data-ttu-id="e301c-159">針對特定資料行資料類型指定小數位數。</span><span class="sxs-lookup"><span data-stu-id="e301c-159">Specifies the scale for certain column data types.</span></span> <span data-ttu-id="e301c-160">小數位數 (Scale) 則是指數字中小數點右方的位數。</span><span class="sxs-lookup"><span data-stu-id="e301c-160">Scale is the number of digits to the right of the decimal point in a number.</span></span> <span data-ttu-id="e301c-161">如果適用於資料類型，您可以更新 `Scale`。</span><span class="sxs-lookup"><span data-stu-id="e301c-161">If applicable to the data type, you can update `Scale`.</span></span>  
  
 `Code Page`  
 <span data-ttu-id="e301c-162">指定資料行類型的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="e301c-162">Specifies the code page for the column type.</span></span> <span data-ttu-id="e301c-163">如果適用於資料類型，您可以更新 `Code Page`。</span><span class="sxs-lookup"><span data-stu-id="e301c-163">If applicable to the data type, you can update `Code Page`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e301c-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e301c-164">See Also</span></span>  
 [<span data-ttu-id="e301c-165">查閱轉換</span><span class="sxs-lookup"><span data-stu-id="e301c-165">Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
