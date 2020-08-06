---
title: 原始檔案目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledest.f1
helpviewer_keywords:
- append options [Integration Services]
- destinations [Integration Services], Raw File
- raw data [Integration Services]
- writing raw data
- Raw File destination
ms.assetid: d311b458-aefc-4b4d-b1a1-4c0ebbb34214
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fc5ce99be6e467ba323137ef885cbb13bfb328ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593465"
---
# <a name="raw-file-destination"></a><span data-ttu-id="c6d4f-102">Raw File Destination</span><span class="sxs-lookup"><span data-stu-id="c6d4f-102">Raw File Destination</span></span>
  <span data-ttu-id="c6d4f-103">「原始檔案」目的地會將原始資料寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-103">The Raw File destination writes raw data to a file.</span></span> <span data-ttu-id="c6d4f-104">由於資料的格式對於目的地而言是原生的，因此資料不需翻譯，也幾乎不需要剖析。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-104">Because the format of the data is native to the destination, the data requires no translation and little parsing.</span></span> <span data-ttu-id="c6d4f-105">這表示，「原始檔案」目的地可比其他目的地更快地寫入資料，例如「一般檔案」和 OLE DB 目的地。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-105">This means that the Raw File destination can write data more quickly than other destinations such as the Flat File and the OLE DB destinations.</span></span>  
  
 <span data-ttu-id="c6d4f-106">除了將原始資料寫入檔案之外，您也可以使用原始檔案目的地產生僅包含資料行 (僅中繼資料的檔案) 的空白原始檔案，而不必執行封裝。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-106">In addition to writing raw data to a file, you can also use the Raw File destination to generate an empty raw file that contains only the columns (metadata-only file), without having to run the package.</span></span> <span data-ttu-id="c6d4f-107">您可以使用原始檔案來源擷取之前由目的地撰寫的原始資料。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-107">You use the Raw File source to retrieve raw data that was previously written by the destination.</span></span> <span data-ttu-id="c6d4f-108">您也可以將原始檔案來源指向僅中繼資料的檔案。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-108">You can also point the Raw File source to the metadata-only file.</span></span>  
  
 <span data-ttu-id="c6d4f-109">原始檔案格式包含排序資訊。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-109">The raw file format contains sort information.</span></span> <span data-ttu-id="c6d4f-110">原始檔案目的地會儲存所有排序資訊，包括字串資料行的比較旗標。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-110">The Raw File Destination saves all the sort information including the comparison flags for string columns.</span></span> <span data-ttu-id="c6d4f-111">原始檔案來源會讀取並接受排序資訊。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-111">The Raw File source reads and honors the sort information.</span></span> <span data-ttu-id="c6d4f-112">您可以使用進階編輯器，選擇將原始檔案來源設定為忽略檔案中的排序旗標。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-112">You do have the option of configuring the Raw File Source to ignore the sort flags in the file, using the Advanced Editor.</span></span> <span data-ttu-id="c6d4f-113">如需比較旗標的詳細資訊，請參閱 [比較字串資料](comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-113">For more information about comparison flags, see [Comparing String Data](comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="c6d4f-114">您可以利用下列方式設定「原始檔案」目的地：</span><span class="sxs-lookup"><span data-stu-id="c6d4f-114">You can configure the Raw File destination in the following ways:</span></span>  
  
-   <span data-ttu-id="c6d4f-115">指定存取模式，可以是在其中寫入「原始檔案」目的地的檔案名稱或包含該檔案名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-115">Specify an access mode which is either the name of the file or a variable that contains the name of the file to which the Raw File destination writes.</span></span>  
  
-   <span data-ttu-id="c6d4f-116">指示「原始檔案」目的地是將資料附加至具有相同名稱的現有檔案還是建立新檔案。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-116">Indicate whether the Raw File destination appends data to an existing file that has the same name or creates a new file.</span></span>  
  
 <span data-ttu-id="c6d4f-117">「原始檔案」目的地通常用於寫入在各個封裝執行之間已部份處理之資料的中介結果。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-117">The Raw File destination is frequently used to write intermediary results of partly processed data between package executions.</span></span> <span data-ttu-id="c6d4f-118">儲存原始資料表示「原始檔案」來源可快速讀取資料，然後在將這些資料載入到其最終目的地前作進一步的轉換。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-118">Storing raw data means that the data can be read quickly by a Raw File source and then further transformed before it is loaded into its final destination.</span></span> <span data-ttu-id="c6d4f-119">例如，封裝可執行多次，每次均將原始資料寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-119">For example, a package might run several times, and each time write raw data to files.</span></span> <span data-ttu-id="c6d4f-120">稍後，另一個封裝可使用「原始檔案」來源從每份檔案讀取，並使用「聯集全部」轉換將資料合併到一個資料集中，然後在將這些資料載入到其最終目的地 (例如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表) 之前，套用可摘要資料的其他轉換。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-120">Later, a different package can use the Raw File source to read from each file, use a Union All transformation to merge the data into one data set, and then apply additional transformations that summarize the data before loading the data into its final destination such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c6d4f-121">「原始檔案」目的地支援 Null 資料但不支援二進位大型物件 (BLOB) 資料。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-121">The Raw File destination supports null data but not binary large object (BLOB) data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c6d4f-122">「原始檔案」目的地不使用連接管理員。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-122">The Raw File destination does not use a connection manager.</span></span>  
  
 <span data-ttu-id="c6d4f-123">此來源具有一個規則輸入。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-123">This source has one regular input.</span></span> <span data-ttu-id="c6d4f-124">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-124">It does not support an error output.</span></span>  
  
## <a name="append-and-new-file-options"></a><span data-ttu-id="c6d4f-125">附加和新增檔案選項</span><span class="sxs-lookup"><span data-stu-id="c6d4f-125">Append and New File Options</span></span>  
 <span data-ttu-id="c6d4f-126">WriteOption 屬性包含將資料附加至現有檔案或建立新檔案的選項。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-126">The WriteOption property includes options to append data to an existing file or create a new file.</span></span>  
  
 <span data-ttu-id="c6d4f-127">下表描述 WriteOption 屬性的可用選項。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-127">The following table describes the available options for the WriteOption property.</span></span>  
  
|<span data-ttu-id="c6d4f-128">選項</span><span class="sxs-lookup"><span data-stu-id="c6d4f-128">Option</span></span>|<span data-ttu-id="c6d4f-129">描述</span><span class="sxs-lookup"><span data-stu-id="c6d4f-129">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c6d4f-130">附加</span><span class="sxs-lookup"><span data-stu-id="c6d4f-130">Append</span></span>|<span data-ttu-id="c6d4f-131">將資料附加至現有檔案。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-131">Appends data to an existing file.</span></span> <span data-ttu-id="c6d4f-132">附加資料的中繼資料必須符合檔案格式。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-132">The metadata of the appended data must match the file format.</span></span>|  
|<span data-ttu-id="c6d4f-133">永遠建立</span><span class="sxs-lookup"><span data-stu-id="c6d4f-133">Create always</span></span>|<span data-ttu-id="c6d4f-134">永遠建立新檔案。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-134">Always creates a new file.</span></span>|  
|<span data-ttu-id="c6d4f-135">建立一次</span><span class="sxs-lookup"><span data-stu-id="c6d4f-135">Create once</span></span>|<span data-ttu-id="c6d4f-136">建立新檔案。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-136">Creates a new file.</span></span> <span data-ttu-id="c6d4f-137">如果該檔案存在，元件就會失敗。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-137">If the file exists, the component fails.</span></span>|  
|<span data-ttu-id="c6d4f-138">截斷與附加</span><span class="sxs-lookup"><span data-stu-id="c6d4f-138">Truncate and append</span></span>|<span data-ttu-id="c6d4f-139">截斷一個現有檔案，然後將資料寫入該檔案。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-139">Truncates an existing file and then writes the data to the file.</span></span> <span data-ttu-id="c6d4f-140">附加資料的中繼資料必須符合檔案格式。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-140">The metadata of the appended data must match the file format.</span></span>|  
  
 <span data-ttu-id="c6d4f-141">以下是關於附加資料的重要項目：</span><span class="sxs-lookup"><span data-stu-id="c6d4f-141">The following are important items about appending data:</span></span>  
  
-   <span data-ttu-id="c6d4f-142">將資料附加到現有的原始檔案時，不會重新排序資料。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-142">Appending data to an existing raw file does not re-sort the data.</span></span>  
  
     <span data-ttu-id="c6d4f-143">您需要確定已排序的索引鍵維持正確的順序。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-143">You need to make certain that the sorted keys remain in the correct order.</span></span>  
  
-   <span data-ttu-id="c6d4f-144">將資料附加到現有的原始檔案時，不會變更檔案中繼資料 (排序資訊)。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-144">Appending data to an existing raw file does not change the file metadata (sort information).</span></span>  
  
 <span data-ttu-id="c6d4f-145">例如，封裝會讀取以 ProductKey (PK) 排序的資料。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-145">For example, a package reads data sorted on the ProductKey (PK).</span></span> <span data-ttu-id="c6d4f-146">封裝資料流程會將資料附加到現有的原始資料。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-146">The package data flow appends the data to an existing raw file.</span></span> <span data-ttu-id="c6d4f-147">封裝第一次執行時，會收到三個資料列 (PK 1000、1100、1200)。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-147">The first time the package runs, three rows are received (PK 1000, 1100, 1200).</span></span> <span data-ttu-id="c6d4f-148">原始檔案現在包含下列資料。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-148">The raw file now contains the following data.</span></span>  
  
-   <span data-ttu-id="c6d4f-149">1000, productA</span><span class="sxs-lookup"><span data-stu-id="c6d4f-149">1000, productA</span></span>  
  
-   <span data-ttu-id="c6d4f-150">1100, productB</span><span class="sxs-lookup"><span data-stu-id="c6d4f-150">1100, productB</span></span>  
  
-   <span data-ttu-id="c6d4f-151">1200, productC</span><span class="sxs-lookup"><span data-stu-id="c6d4f-151">1200, productC</span></span>  
  
 <span data-ttu-id="c6d4f-152">封裝第二次執行時，會收到兩個資料列 (PK 1001、1300)。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-152">The second time the package runs, two new rows are received (PK 1001, 1300).</span></span> <span data-ttu-id="c6d4f-153">原始檔案現在包含下列資料。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-153">The raw file now contains the following data.</span></span>  
  
-   <span data-ttu-id="c6d4f-154">1000, productA</span><span class="sxs-lookup"><span data-stu-id="c6d4f-154">1000, productA</span></span>  
  
-   <span data-ttu-id="c6d4f-155">1100, productB</span><span class="sxs-lookup"><span data-stu-id="c6d4f-155">1100, productB</span></span>  
  
-   <span data-ttu-id="c6d4f-156">1200, productC</span><span class="sxs-lookup"><span data-stu-id="c6d4f-156">1200, productC</span></span>  
  
-   <span data-ttu-id="c6d4f-157">1001, productD</span><span class="sxs-lookup"><span data-stu-id="c6d4f-157">1001, productD</span></span>  
  
-   <span data-ttu-id="c6d4f-158">1300, productE</span><span class="sxs-lookup"><span data-stu-id="c6d4f-158">1300, productE</span></span>  
  
 <span data-ttu-id="c6d4f-159">新的資料會附加到原始檔案結尾，而且已排序的索引鍵 (PK) 會失序。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-159">The new data is appended to the end of the raw file, and the sorted keys (PK) are out of order.</span></span> <span data-ttu-id="c6d4f-160">此外，附加作業不會變更檔案中繼資料 (排序資訊)。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-160">In addition, the append operation didn't change the file metadata (sort information).</span></span> <span data-ttu-id="c6d4f-161">如果您使用原始檔案來源讀取檔案，此元件會指出，即使檔案中的資料不再處於正確的順序，檔案仍以 PK 排序。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-161">If you read the file by using the Raw File source, the component indicates that the file is still sorted on PK even though the data in the file is no longer in the correct order.</span></span>  
  
 <span data-ttu-id="c6d4f-162">若要在附加資料時保持已排序的索引鍵處於正確的順序，您可以設計封裝資料流程，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c6d4f-162">To keep the sorted keys in the correct order while appending data, you can design the package data flow as follows:</span></span>  
  
1.  <span data-ttu-id="c6d4f-163">使用來源 A 擷取新的資料列。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-163">Retrieve new rows by using Source A.</span></span>  
  
2.  <span data-ttu-id="c6d4f-164">使用來源 B，從 RawFile1 擷取現有的資料列。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-164">Retrieve existing rows from RawFile1 using Source B.</span></span>  
  
3.  <span data-ttu-id="c6d4f-165">使用聯集全部 (Union All) 轉換結合來源 A 與來源 B 的輸入。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-165">Combine the inputs from Source A and Source B by using the Union All transformation.</span></span>  
  
4.  <span data-ttu-id="c6d4f-166">以 PK 排序。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-166">Sort on PK.</span></span>  
  
5.  <span data-ttu-id="c6d4f-167">使用原始檔案目的地寫入 RawFile2。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-167">Write to RawFile2 by using the Raw File destination.</span></span>  
  
     <span data-ttu-id="c6d4f-168">在資料流程中，由於 RawFile1 是讀取來源，因此遭到鎖定。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-168">RawFile1 is locked because it's being read from, in the data flow.</span></span>  
  
6.  <span data-ttu-id="c6d4f-169">將 RawFile1 取代成 RawFile2。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-169">Replace RawFile1 with RawFile2.</span></span>  
  
### <a name="using-the-raw-file-destination-in-a-loop"></a><span data-ttu-id="c6d4f-170">在迴圈中使用原始檔案目的地</span><span class="sxs-lookup"><span data-stu-id="c6d4f-170">Using the Raw File Destination in a Loop</span></span>  
 <span data-ttu-id="c6d4f-171">如果使用「原始檔案」目的地的資料流程位於迴圈中，您可以建立一次該檔案，然後在迴圈重複時將資料附加至檔案。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-171">If the data flow that uses the Raw File destination is in a loop, you may want to create the file once and then append data to the file when the loop repeats.</span></span> <span data-ttu-id="c6d4f-172">若要將資料附加至檔案，附加的資料必須符合現有檔案的格式。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-172">To append data to the file, the data that is appended must match the format of the existing file.</span></span>  
  
 <span data-ttu-id="c6d4f-173">若要在迴圈的第一次反覆運算中建立檔案，然後在迴圈的後續反覆運算中附加資料列，您需要在設計階段執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c6d4f-173">To create the file in the first iteration of the loop, and then append rows in the subsequent iterations of the loop, you need to do the following at design time:</span></span>  
  
1.  <span data-ttu-id="c6d4f-174">將 WriteOption 屬性設為 [CreateOnce]  或 [CreateAlways]  ，然後執行一次迴圈的反覆運算。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-174">Set the WriteOption property to **CreateOnce** or **CreateAlways**and run one iteration of the loop.</span></span> <span data-ttu-id="c6d4f-175">檔案就會建立，</span><span class="sxs-lookup"><span data-stu-id="c6d4f-175">The file is created.</span></span> <span data-ttu-id="c6d4f-176">這可確保附加資料的中繼資料與該檔案相符。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-176">This ensures that the metadata of appended data and the file matches.</span></span>  
  
2.  <span data-ttu-id="c6d4f-177">將 [WriteOption] 屬性重設為 [**附加**]，並將 ValidateExternalMetadata 屬性設定為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-177">Reset the WriteOption property to **Append** and set the ValidateExternalMetadata property to `False`.</span></span>  
  
 <span data-ttu-id="c6d4f-178">如果您使用 [TruncateAppend]  選項，而不是 [Append]  選項，它就會截斷在任何先前反覆運算中新增的資料列，然後附加新的資料列。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-178">If you use the **TruncateAppend** option instead of the **Append** option, it will truncate rows that were added in any previous iteration, and then append new rows.</span></span> <span data-ttu-id="c6d4f-179">使用 [TruncateAppend]  選項也會要求資料符合檔案格式。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-179">Using the **TruncateAppend** option also requires that the data matches the file format.</span></span>  
  
## <a name="configuration-of-the-raw-file-destination"></a><span data-ttu-id="c6d4f-180">原始檔案目的地的組態</span><span class="sxs-lookup"><span data-stu-id="c6d4f-180">Configuration of the Raw File Destination</span></span>  
 <span data-ttu-id="c6d4f-181">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-181">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="c6d4f-182">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-182">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="c6d4f-183">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="c6d4f-183">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c6d4f-184">Common Properties</span><span class="sxs-lookup"><span data-stu-id="c6d4f-184">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="c6d4f-185">原始檔案自訂屬性</span><span class="sxs-lookup"><span data-stu-id="c6d4f-185">Raw File Custom Properties</span></span>](raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="c6d4f-186">相關工作</span><span class="sxs-lookup"><span data-stu-id="c6d4f-186">Related Tasks</span></span>  
 <span data-ttu-id="c6d4f-187">如需如何設定此元件屬性的資訊，請參閱 [設定資料流程元件的屬性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-187">For information about how to set properties of the component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="c6d4f-188">相關內容</span><span class="sxs-lookup"><span data-stu-id="c6d4f-188">Related Content</span></span>  
 <span data-ttu-id="c6d4f-189">Sqlservercentral.com 上的部落格文章： [Raw Files Are Awesome](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131)(原始檔案令人敬畏)。</span><span class="sxs-lookup"><span data-stu-id="c6d4f-189">Blog entry, [Raw Files Are Awesome](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131), on sqlservercentral.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d4f-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6d4f-190">See Also</span></span>  
 <span data-ttu-id="c6d4f-191">[原始檔案來源](raw-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="c6d4f-191">[Raw File Source](raw-file-source.md) </span></span>  
 [<span data-ttu-id="c6d4f-192">資料流程</span><span class="sxs-lookup"><span data-stu-id="c6d4f-192">Data Flow</span></span>](data-flow.md)  
  
  
