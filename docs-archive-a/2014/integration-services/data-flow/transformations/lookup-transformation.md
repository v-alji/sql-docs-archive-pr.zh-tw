---
title: 查閱轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptrans.f1
helpviewer_keywords:
- Lookup transformation
- joining columns [Integration Services]
- cache [Integration Services]
- match exactly [Integration Services]
- lookups [Integration Services]
- exact matches [Integration Services]
ms.assetid: de1cc8de-e7af-4727-b5a5-a1f0a739aa09
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 567c5d95c2ee7c15ea5c541f7fe2010d46ba36f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599096"
---
# <a name="lookup-transformation"></a><span data-ttu-id="63826-102">查閱轉換</span><span class="sxs-lookup"><span data-stu-id="63826-102">Lookup Transformation</span></span>
  <span data-ttu-id="63826-103">「查閱」轉換會藉由聯結輸入資料行中的資料與參考資料集中的資料行來執行查閱。</span><span class="sxs-lookup"><span data-stu-id="63826-103">The Lookup transformation performs lookups by joining data in input columns with columns in a reference dataset.</span></span> <span data-ttu-id="63826-104">您可以使用查閱在相關資料表中存取以通用資料行中的值為基礎的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="63826-104">You use the lookup to access additional information in a related table that is based on values in common columns.</span></span>  
  
 <span data-ttu-id="63826-105">參考資料集可以是快取檔案、現有的資料表或檢視、新資料表或 SQL 查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="63826-105">The reference dataset can be a cache file, an existing table or view, a new table, or the result of an SQL query.</span></span> <span data-ttu-id="63826-106">「查閱」轉換會使用 OLE DB 連接管理員或快取連接管理員來連接到參考資料集。</span><span class="sxs-lookup"><span data-stu-id="63826-106">The Lookup transformation uses either an OLE DB connection manager or a Cache connection manager to connect to the reference dataset.</span></span> <span data-ttu-id="63826-107">如需詳細資訊，請參閱 [OLE DB 連線管理員](../../connection-manager/ole-db-connection-manager.md) 和 [快取連線管理員](../../connection-manager/cache-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="63826-107">For more information, see [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md) and [Cache Connection Manager](../../connection-manager/cache-connection-manager.md)</span></span>  
  
 <span data-ttu-id="63826-108">您可以利用下列方式設定「查閱」轉換：</span><span class="sxs-lookup"><span data-stu-id="63826-108">You can configure the Lookup transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="63826-109">選取您要使用的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="63826-109">Select the connection manager that you want to use.</span></span> <span data-ttu-id="63826-110">如果想要連接到資料庫，請選取 OLE DB 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="63826-110">If you want to connect to a database, select an OLE DB connection manager.</span></span> <span data-ttu-id="63826-111">如果想要連接到快取檔案，請選取快取連接管理員。</span><span class="sxs-lookup"><span data-stu-id="63826-111">If you want to connect to a cache file, select a Cache connection manager.</span></span>  
  
-   <span data-ttu-id="63826-112">指定包含參考資料集的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="63826-112">Specify the table or view that contains the reference dataset.</span></span>  
  
-   <span data-ttu-id="63826-113">藉由指定 SQL 陳述式產生參考資料集。</span><span class="sxs-lookup"><span data-stu-id="63826-113">Generate a reference dataset by specifying an SQL statement.</span></span>  
  
-   <span data-ttu-id="63826-114">指定輸入與參考資料集之間的聯結。</span><span class="sxs-lookup"><span data-stu-id="63826-114">Specify joins between the input and the reference dataset.</span></span>  
  
-   <span data-ttu-id="63826-115">從參考資料集將資料行加入至「查閱」轉換輸出。</span><span class="sxs-lookup"><span data-stu-id="63826-115">Add columns from the reference dataset to the Lookup transformation output.</span></span>  
  
-   <span data-ttu-id="63826-116">設定快取選項。</span><span class="sxs-lookup"><span data-stu-id="63826-116">Configure the caching options.</span></span>  
  
 <span data-ttu-id="63826-117">「查閱」轉換支援下列 OLE DB 連接管理員的資料提供者：</span><span class="sxs-lookup"><span data-stu-id="63826-117">The Lookup transformation supports the following database providers for the OLE DB connection manager:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
-   <span data-ttu-id="63826-118">Oracle</span><span class="sxs-lookup"><span data-stu-id="63826-118">Oracle</span></span>  
  
-   <span data-ttu-id="63826-119">DB2</span><span class="sxs-lookup"><span data-stu-id="63826-119">DB2</span></span>  
  
 <span data-ttu-id="63826-120">「查閱」轉換會嘗試在轉換輸入的值與參考資料集的值之間執行等聯結 (Equi-Join)</span><span class="sxs-lookup"><span data-stu-id="63826-120">The Lookup transformation tries to perform an equi-join between values in the transformation input and values in the reference dataset.</span></span> <span data-ttu-id="63826-121">(等聯結表示轉換輸入中的各資料列，必須至少符合參考資料集中的某個資料列)。如果無法執行等聯結，則「查閱」轉換會執行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="63826-121">(An equi-join means that each row in the transformation input must match at least one row from the reference dataset.) If an equi-join is not possible, the Lookup transformation takes one of the following actions:</span></span>  
  
-   <span data-ttu-id="63826-122">如果參考資料集中沒有相符的項目，則不會發生聯結。</span><span class="sxs-lookup"><span data-stu-id="63826-122">If there is no matching entry in the reference dataset, no join occurs.</span></span> <span data-ttu-id="63826-123">根據預設，「查閱」轉換會將沒有相符項目的資料列視為錯誤；</span><span class="sxs-lookup"><span data-stu-id="63826-123">By default, the Lookup transformation treats rows without matching entries as errors.</span></span> <span data-ttu-id="63826-124">不過，您可以設定「查閱」轉換，以將這些資料列重新導向至無相符結果輸出。</span><span class="sxs-lookup"><span data-stu-id="63826-124">However, you can configure the Lookup transformation to redirect such rows to a no match output.</span></span> <span data-ttu-id="63826-125">如需詳細資訊，請參閱[查閱轉換編輯器 &#40;一般頁面&#41;](../../lookup-transformation-editor-general-page.md) 和[查閱轉換編輯器 &#40;錯誤輸出頁面&#41;](../../lookup-transformation-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="63826-125">For more information, see [Lookup Transformation Editor &#40;General Page&#41;](../../lookup-transformation-editor-general-page.md) and [Lookup Transformation Editor &#40;Error Output Page&#41;](../../lookup-transformation-editor-error-output-page.md).</span></span>  
  
-   <span data-ttu-id="63826-126">如果參考資料表中有多個相符項目，「查閱」轉換將只傳回查閱查詢所傳回的第一個相符項目。</span><span class="sxs-lookup"><span data-stu-id="63826-126">If there are multiple matches in the reference table, the Lookup transformation returns only the first match returned by the lookup query.</span></span> <span data-ttu-id="63826-127">如果找到多個相符項目，則「查閱」轉換只會在已設定為將所有參考資料集載入至快取時才產生錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="63826-127">If multiple matches are found, the Lookup transformation generates an error or warning only when the transformation has been configured to load all the reference dataset into the cache.</span></span> <span data-ttu-id="63826-128">在這種情況下，「查閱」轉換會在轉換填滿快取時偵測到多個相符項目時產生警告。</span><span class="sxs-lookup"><span data-stu-id="63826-128">In this case, the Lookup transformation generates a warning when the transformation detects multiple matches as the transformation fills the cache.</span></span>  
  
 <span data-ttu-id="63826-129">聯結可以是複合聯結，表示您可以將轉換輸入中的多個資料行聯結至參考資料集中的資料行。</span><span class="sxs-lookup"><span data-stu-id="63826-129">The join can be a composite join, which means that you can join multiple columns in the transformation input to columns in the reference dataset.</span></span> <span data-ttu-id="63826-130">轉換支援聯結任何資料類型的資料行，但 DT_R4、DT_R8、DT_TEXT、DT_NTEXT 或 DT_IMAG 除外。</span><span class="sxs-lookup"><span data-stu-id="63826-130">The transformation supports join columns with any data type, except for DT_R4, DT_R8, DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span> <span data-ttu-id="63826-131">如需詳細資訊，請參閱 [Integration Services 資料類型](../integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="63826-131">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="63826-132">通常參考資料集的值會加入至轉換輸出。</span><span class="sxs-lookup"><span data-stu-id="63826-132">Typically, values from the reference dataset are added to the transformation output.</span></span> <span data-ttu-id="63826-133">例如，「查閱」轉換可從使用輸出資料行之值的資料表擷取產品名稱，然後將產品名稱加入至轉換輸出。</span><span class="sxs-lookup"><span data-stu-id="63826-133">For example, the Lookup transformation can extract a product name from a table using a value from an input column, and then add the product name to the transformation output.</span></span> <span data-ttu-id="63826-134">參考資料表的值可取代資料行的值，或者可加入至新的資料行。</span><span class="sxs-lookup"><span data-stu-id="63826-134">The values from the reference table can replace column values or can be added to new columns.</span></span>  
  
 <span data-ttu-id="63826-135">「查閱」轉換執行的查閱區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="63826-135">The lookups performed by the Lookup transformation are case sensitive.</span></span> <span data-ttu-id="63826-136">若要避免由於資料中的大小寫不同而造成查閱失敗，請先使用「字元對應」轉換將資料轉換成大寫或小寫，</span><span class="sxs-lookup"><span data-stu-id="63826-136">To avoid lookup failures that are caused by case differences in data, first use the Character Map transformation to convert the data to uppercase or lowercase.</span></span> <span data-ttu-id="63826-137">然後在產生參考資料表的 SQL 陳述式中包含 UPPER 或 LOWER 函數。</span><span class="sxs-lookup"><span data-stu-id="63826-137">Then, include the UPPER or LOWER functions in the SQL statement that generates the reference table.</span></span> <span data-ttu-id="63826-138">如需詳細資訊，請參閱[字元對應轉換](character-map-transformation.md)、[UPPER &#40;Transact-SQL&#41;](/sql/t-sql/functions/upper-transact-sql) 和 [LOWER &#40;Transact-SQL&#41;](/sql/t-sql/functions/lower-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="63826-138">For more information, see [Character Map Transformation](character-map-transformation.md), [UPPER &#40;Transact-SQL&#41;](/sql/t-sql/functions/upper-transact-sql), and [LOWER &#40;Transact-SQL&#41;](/sql/t-sql/functions/lower-transact-sql).</span></span>  
  
 <span data-ttu-id="63826-139">「查閱」轉換具有下列的輸入和輸出：</span><span class="sxs-lookup"><span data-stu-id="63826-139">The Lookup transformation has the following inputs and outputs:</span></span>  
  
-   <span data-ttu-id="63826-140">輸入。</span><span class="sxs-lookup"><span data-stu-id="63826-140">Input.</span></span>  
  
-   <span data-ttu-id="63826-141">相符結果輸出。</span><span class="sxs-lookup"><span data-stu-id="63826-141">Match output.</span></span> <span data-ttu-id="63826-142">相符結果輸出會處理轉換輸入中，至少符合參考資料集中一個項目的資料列。</span><span class="sxs-lookup"><span data-stu-id="63826-142">The match output handles the rows in the transformation input that match at least one entry in the reference dataset.</span></span>  
  
-   <span data-ttu-id="63826-143">無相符結果輸出。</span><span class="sxs-lookup"><span data-stu-id="63826-143">No Match output.</span></span> <span data-ttu-id="63826-144">無相符結果輸出會處理輸入中沒有至少符合參考資料集中一個項目的資料列。</span><span class="sxs-lookup"><span data-stu-id="63826-144">The no match output handles rows in the input that do not match at least one entry in the reference dataset.</span></span> <span data-ttu-id="63826-145">如果將「查閱」轉換設定為把沒有相符項目的資料列視為錯誤，則這些資料列會重新導向至錯誤輸出；</span><span class="sxs-lookup"><span data-stu-id="63826-145">If you configure the Lookup transformation to treat the rows without matching entries as errors, the rows are redirected to the error output.</span></span> <span data-ttu-id="63826-146">否則，轉換會將這些資料列重新導向至無相符結果輸出。</span><span class="sxs-lookup"><span data-stu-id="63826-146">Otherwise, the transformation would redirect those rows to the no match output.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63826-147">在 [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)] 中，「查閱」轉換僅具有一個輸出：</span><span class="sxs-lookup"><span data-stu-id="63826-147">In [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)], the Lookup transformation had only one output.</span></span> <span data-ttu-id="63826-148">如需如何執行在中建立之查閱轉換的詳細資訊 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ，請參閱[升級查閱轉換](../../../sql-server/install/upgrade-lookup-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="63826-148">For more information about how to run a Lookup transformation that was created in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], see [Upgrade Lookup Transformations](../../../sql-server/install/upgrade-lookup-transformations.md).</span></span>  
  
-   <span data-ttu-id="63826-149">錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="63826-149">Error output.</span></span>  
  
## <a name="caching-the-reference-dataset"></a><span data-ttu-id="63826-150">快取參考資料集</span><span class="sxs-lookup"><span data-stu-id="63826-150">Caching the Reference Dataset</span></span>  
 <span data-ttu-id="63826-151">記憶體中的快取會儲存參考資料集，並儲存編列資料索引的雜湊資料表。</span><span class="sxs-lookup"><span data-stu-id="63826-151">An in-memory cache stores the reference dataset and stores a hash table that indexes the data.</span></span> <span data-ttu-id="63826-152">在完成封裝的執行之前，快取都會保留在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="63826-152">The cache remains in memory until the execution of the package is completed.</span></span> <span data-ttu-id="63826-153">您可以將快取保存至快取檔案 (.caw)。</span><span class="sxs-lookup"><span data-stu-id="63826-153">You can persist the cache to a cache file (.caw).</span></span>  
  
 <span data-ttu-id="63826-154">將快取保存至檔案後，系統就可以更快地載入快取。</span><span class="sxs-lookup"><span data-stu-id="63826-154">When you persist the cache to a file, the system loads the cache faster.</span></span> <span data-ttu-id="63826-155">如此可改善「查閱」轉換和封裝的效能。</span><span class="sxs-lookup"><span data-stu-id="63826-155">This improves the performance of the Lookup transformation and the package.</span></span> <span data-ttu-id="63826-156">請記住，當您使用快取檔案時，所使用的資料並不如資料庫中的資料新。</span><span class="sxs-lookup"><span data-stu-id="63826-156">Remember, that when you use a cache file, you are working with data that is not as current as the data in the database.</span></span>  
  
 <span data-ttu-id="63826-157">下列是將快取保存至檔案的其他優點：</span><span class="sxs-lookup"><span data-stu-id="63826-157">The following are additional benefits of persisting the cache to a file:</span></span>  
  
-   <span data-ttu-id="63826-158">***在多個封裝間共用快取檔案。如需詳細資訊，請參閱***  [使用快取連線管理員以完整快取模式實作查閱轉換](../../connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)  ***。***</span><span class="sxs-lookup"><span data-stu-id="63826-158">***Share the cache file between multiple packages. For more information, see***  [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)  ***.***</span></span>  
  
-   <span data-ttu-id="63826-159">使用封裝部署快取檔案，</span><span class="sxs-lookup"><span data-stu-id="63826-159">Deploy the cache file with a package.</span></span> <span data-ttu-id="63826-160">***接著就可以在多部電腦上使用資料。***</span><span class="sxs-lookup"><span data-stu-id="63826-160">***You can then use the data on multiple computers.***</span></span> <span data-ttu-id="63826-161">如需詳細資訊，請參閱 [針對查閱轉換來建立及部署快取](create-and-deploy-a-cache-for-the-lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="63826-161">For more information, see [Create and Deploy a Cache for the Lookup Transformation](create-and-deploy-a-cache-for-the-lookup-transformation.md).</span></span>  
  
-   <span data-ttu-id="63826-162">使用「原始檔案」來源從快取檔案讀取資料，</span><span class="sxs-lookup"><span data-stu-id="63826-162">Use the Raw File source to read data from the cache file.</span></span> <span data-ttu-id="63826-163">接著就可以使用其他的資料流程元件來轉換或移動資料。</span><span class="sxs-lookup"><span data-stu-id="63826-163">You can then use other data flow components to transform or move the data.</span></span> <span data-ttu-id="63826-164">如需相關資訊，請參閱 [Raw File Source](../raw-file-source.md)。</span><span class="sxs-lookup"><span data-stu-id="63826-164">For more information, see [Raw File Source](../raw-file-source.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63826-165">快取連接管理員不支援使用「原始檔案」目的地所建立或修改的快取檔案。</span><span class="sxs-lookup"><span data-stu-id="63826-165">The Cache connection manager does not support cache files that are created or modified by using the Raw File destination.</span></span>  
  
-   <span data-ttu-id="63826-166">使用「檔案系統」工作在快取檔案上執行作業和設定屬性。</span><span class="sxs-lookup"><span data-stu-id="63826-166">Perform operations and set attributes on the cache file by using the File System task.</span></span> <span data-ttu-id="63826-167">如需詳細資訊，請參閱 [檔案系統工作](../../control-flow/file-system-task.md)。</span><span class="sxs-lookup"><span data-stu-id="63826-167">For more information, see and [File System Task](../../control-flow/file-system-task.md).</span></span>  
  
 <span data-ttu-id="63826-168">下列是快取選項：</span><span class="sxs-lookup"><span data-stu-id="63826-168">The following are the caching options:</span></span>  
  
-   <span data-ttu-id="63826-169">參考資料集是藉由執行「查閱」轉換之前使用資料表、檢視或 SQL 查詢而產生並載入快取。</span><span class="sxs-lookup"><span data-stu-id="63826-169">The reference dataset is generated by using a table, view, or SQL query and loaded into cache, before the Lookup transformation runs.</span></span> <span data-ttu-id="63826-170">您可以使用 OLE DB 連接管理員來存取資料集。</span><span class="sxs-lookup"><span data-stu-id="63826-170">You use the OLE DB connection manager to access the dataset.</span></span>  
  
     <span data-ttu-id="63826-171">此快取選項與 [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]中用於「查閱」轉換的完整快取選項相容。</span><span class="sxs-lookup"><span data-stu-id="63826-171">This caching option is compatible with the full caching option that is available for the Lookup transformation in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="63826-172">參考資料集是從資料流程中已連接的資料來源或從快取檔案產生，然後在「查閱」轉換執行之前載入至快取。</span><span class="sxs-lookup"><span data-stu-id="63826-172">The reference dataset is generated from a connected data source in the data flow or from a cache file, and is loaded into cache before the Lookup transformation runs.</span></span> <span data-ttu-id="63826-173">您可以使用快取連接管理員或是快取轉換來存取資料集。</span><span class="sxs-lookup"><span data-stu-id="63826-173">You use the Cache connection manager, and, optionally, the Cache transformation, to access the dataset.</span></span> <span data-ttu-id="63826-174">如需詳細資訊，請參閱 [快取連線管理員](../../connection-manager/cache-connection-manager.md) 和 [快取轉換](cache-transform.md)。</span><span class="sxs-lookup"><span data-stu-id="63826-174">For more information, see [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) and [Cache Transform](cache-transform.md).</span></span>  
  
-   <span data-ttu-id="63826-175">參考資料集是藉由在執行「查閱」轉換期間使用資料表、檢視或 SQL 查詢而產生。</span><span class="sxs-lookup"><span data-stu-id="63826-175">The reference dataset is generated by using a table, view, or SQL query during the execution of the Lookup transformation.</span></span> <span data-ttu-id="63826-176">在參考資料集中具有相符項目的資料列，以及在資料集中沒有相符項目的資料列，都可以載入至快取。</span><span class="sxs-lookup"><span data-stu-id="63826-176">The rows with matching entries in the reference dataset and the rows without matching entries in the dataset are loaded into cache.</span></span>  
  
     <span data-ttu-id="63826-177">超過快取的記憶體大小時，查閱轉換會自動從快取中移除最不常用的資料列。</span><span class="sxs-lookup"><span data-stu-id="63826-177">When the memory size of the cache is exceeded, the Lookup transformation automatically removes the least frequently used rows from the cache.</span></span>  
  
     <span data-ttu-id="63826-178">此快取選項與 [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]中用於「查閱」轉換的部分快取選項相容。</span><span class="sxs-lookup"><span data-stu-id="63826-178">This caching option is compatible with the partial caching option that is available for the Lookup transformation in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="63826-179">參考資料集是藉由在執行「查閱」轉換期間使用資料表、檢視或 SQL 查詢而產生。</span><span class="sxs-lookup"><span data-stu-id="63826-179">The reference dataset is generated by using a table, view, or SQL query during the execution of the Lookup transformation.</span></span> <span data-ttu-id="63826-180">不會將任何資料存入快取。</span><span class="sxs-lookup"><span data-stu-id="63826-180">No data is cached.</span></span>  
  
     <span data-ttu-id="63826-181">此快取選項與 [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]中用於「查閱」轉換的無快取選項相容。</span><span class="sxs-lookup"><span data-stu-id="63826-181">This caching option is compatible with the no caching option that is available for the Lookup transformation in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)].</span></span>  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="63826-182">和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的差異在於比較字串的方式。</span><span class="sxs-lookup"><span data-stu-id="63826-182">and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] differ in the way they compare strings.</span></span> <span data-ttu-id="63826-183">如果「查閱」轉換是設定為在執行之前將參考資料集載入至快取，則 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 會在快取中進行查閱比較。</span><span class="sxs-lookup"><span data-stu-id="63826-183">If the Lookup transformation is configured to load the reference dataset into cache before the Lookup transformation runs, [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] does the lookup comparison in the cache.</span></span> <span data-ttu-id="63826-184">否則，查閱作業會使用參數化的 SQL 陳述式而由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 進行查閱比較。</span><span class="sxs-lookup"><span data-stu-id="63826-184">Otherwise, the lookup operation uses a parameterized SQL statement and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does the lookup comparison.</span></span> <span data-ttu-id="63826-185">這表示「查閱」轉換可能會根據快取類型，從相同的查閱資料表傳回不同數目的相符項目。</span><span class="sxs-lookup"><span data-stu-id="63826-185">This means that the Lookup transformation might return a different number of matches from the same lookup table depending on the cache type.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="63826-186">相關工作</span><span class="sxs-lookup"><span data-stu-id="63826-186">Related Tasks</span></span>  
 <span data-ttu-id="63826-187">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="63826-187">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span> <span data-ttu-id="63826-188">如需進一步詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="63826-188">For more details, see the following topics.</span></span>  
  
-   [<span data-ttu-id="63826-189">以沒有快取或部分快取模式實作查閱</span><span class="sxs-lookup"><span data-stu-id="63826-189">Implement a Lookup in No Cache or Partial Cache Mode</span></span>](implement-a-lookup-in-no-cache-or-partial-cache-mode.md)  
  
-   [<span data-ttu-id="63826-190">使用快取連線管理員以完整快取模式實作查閱轉換</span><span class="sxs-lookup"><span data-stu-id="63826-190">Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager</span></span>](../../connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)  
  
-   [<span data-ttu-id="63826-191">使用 OLE DB 連接管理員，以完整快取模式來實作查閱轉換</span><span class="sxs-lookup"><span data-stu-id="63826-191">Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager</span></span>](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md)  
  
-   [<span data-ttu-id="63826-192">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="63826-192">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="63826-193">相關內容</span><span class="sxs-lookup"><span data-stu-id="63826-193">Related Content</span></span>  
  
-   <span data-ttu-id="63826-194">位於 msdn.microsoft.com 的影片： [如何：在完整快取模式中實作查閱轉換 (SQL Server 影片)](https://go.microsoft.com/fwlink/?LinkId=131031)</span><span class="sxs-lookup"><span data-stu-id="63826-194">Video, [How to: Implement a Lookup Transformation in Full Cache Mode](https://go.microsoft.com/fwlink/?LinkId=131031), on msdn.microsoft.com</span></span>  
  
-   <span data-ttu-id="63826-195">位於 blogs.msdn.com 的部落格項目： [Best Practices for Using the Lookup Transformation Cache Modes](https://go.microsoft.com/fwlink/?LinkId=146623)(使用查閱轉換快取模式的最佳做法)</span><span class="sxs-lookup"><span data-stu-id="63826-195">Blog entry, [Best Practices for Using the Lookup Transformation Cache Modes](https://go.microsoft.com/fwlink/?LinkId=146623), on blogs.msdn.com</span></span>  
  
-   <span data-ttu-id="63826-196">位於 blogs.msdn.com 的部落格項目： [Lookup Pattern: Case Insensitive](https://go.microsoft.com/fwlink/?LinkId=157782)(查閱模式：不區分案例)</span><span class="sxs-lookup"><span data-stu-id="63826-196">Blog entry, [Lookup Pattern: Case Insensitive](https://go.microsoft.com/fwlink/?LinkId=157782), on blogs.msdn.com</span></span>  
  
-   <span data-ttu-id="63826-197">位於 msftisprodsamples.codeplex.com 上的範例： [Lookup Transformation](https://go.microsoft.com/fwlink/?LinkId=267528)(查閱轉換)。</span><span class="sxs-lookup"><span data-stu-id="63826-197">Sample, [Lookup Transformation](https://go.microsoft.com/fwlink/?LinkId=267528), on msftisprodsamples.codeplex.com.</span></span>  
  
     <span data-ttu-id="63826-198">如需安裝 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 產品範例和範例資料庫的資訊，請參閱 [SQL Server Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=267527)(SQL Server Integration Services 產品範例)。</span><span class="sxs-lookup"><span data-stu-id="63826-198">For information on installing [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] product samples and sample databases, see [SQL Server Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=267527).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63826-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63826-199">See Also</span></span>  
 <span data-ttu-id="63826-200">[模糊查閱轉換](fuzzy-lookup-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="63826-200">[Fuzzy Lookup Transformation](fuzzy-lookup-transformation.md) </span></span>  
 <span data-ttu-id="63826-201">[詞彙查閱轉換](term-lookup-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="63826-201">[Term Lookup Transformation](term-lookup-transformation.md) </span></span>  
 <span data-ttu-id="63826-202">[資料流程](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="63826-202">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="63826-203">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="63826-203">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
