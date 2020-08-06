---
title: 資料庫屬性 (檔案頁面) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.files.f1
ms.assetid: 3c030e51-db82-4b43-b1e5-8547ddd3de87
author: stevestein
ms.author: sstein
ms.openlocfilehash: 955a17857ce0d847fb712473dddd581a072ab83d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686976"
---
# <a name="database-properties-files-page"></a><span data-ttu-id="a861c-102">資料庫屬性 (檔案頁面)</span><span class="sxs-lookup"><span data-stu-id="a861c-102">Database Properties (Files Page)</span></span>
  <span data-ttu-id="a861c-103">使用此頁面來建立新的資料庫，或者檢視或修改選取之資料庫的屬性。</span><span class="sxs-lookup"><span data-stu-id="a861c-103">Use this page to create a new database, or view or modify properties for the selected database.</span></span> <span data-ttu-id="a861c-104">此主題適用於現有資料庫的 [資料庫屬性 (檔案頁面)]，以及 [新增資料庫 (一般頁面)]。</span><span class="sxs-lookup"><span data-stu-id="a861c-104">This topic applies to the **Database Properties (Files Page)** for existing databases, and to the **New Database (General Page)**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="a861c-105">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="a861c-105">UI element list</span></span>  
 <span data-ttu-id="a861c-106">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="a861c-106">**Database name**</span></span>  
 <span data-ttu-id="a861c-107">加入或顯示資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="a861c-107">Add or display the name of the database.</span></span>  
  
 <span data-ttu-id="a861c-108">**擁有者**</span><span class="sxs-lookup"><span data-stu-id="a861c-108">**Owner**</span></span>  
 <span data-ttu-id="a861c-109">從清單中選取以指定資料庫的擁有者。</span><span class="sxs-lookup"><span data-stu-id="a861c-109">Specify the owner of the database by selecting from the list.</span></span>  
  
 <span data-ttu-id="a861c-110">**使用全文檢索索引**</span><span class="sxs-lookup"><span data-stu-id="a861c-110">**Use full-text indexing**</span></span>  
 <span data-ttu-id="a861c-111">這個核取方塊會被核取並停用，因為在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，全文檢索索引一定是啟用的。</span><span class="sxs-lookup"><span data-stu-id="a861c-111">This check box is checked and disabled because full-text indexing is always enabled in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="a861c-112">如需詳細資訊，請參閱 [全文檢索搜尋](../search/full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="a861c-112">For more information, see [Full-Text Search](../search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="a861c-113">**資料庫檔案**</span><span class="sxs-lookup"><span data-stu-id="a861c-113">**Database Files**</span></span>  
 <span data-ttu-id="a861c-114">加入、檢視、修改或移除相關聯資料庫的資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="a861c-114">Add, view, modify, or remove database files for the associated database.</span></span> <span data-ttu-id="a861c-115">資料庫檔案具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a861c-115">Database files have the following properties:</span></span>  
  
 <span data-ttu-id="a861c-116">**邏輯名稱**</span><span class="sxs-lookup"><span data-stu-id="a861c-116">**Logical Name**</span></span>  
 <span data-ttu-id="a861c-117">輸入或修改檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="a861c-117">Enter or modify the name of the file.</span></span>  
  
 <span data-ttu-id="a861c-118">**檔案類型**</span><span class="sxs-lookup"><span data-stu-id="a861c-118">**File Type**</span></span>  
 <span data-ttu-id="a861c-119">從清單中選取檔案類型。</span><span class="sxs-lookup"><span data-stu-id="a861c-119">Select the file type from the list.</span></span> <span data-ttu-id="a861c-120">檔案類型可以是 **[資料]** 、 **[記錄檔]** 或 **[FILESTREAM 資料]** 。</span><span class="sxs-lookup"><span data-stu-id="a861c-120">The file type can be **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="a861c-121">您無法修改現有檔案的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="a861c-121">You cannot modify the file type of an existing file.</span></span>  
  
 <span data-ttu-id="a861c-122">如果您要將檔案 (容器) 加入至記憶體最佳化檔案群組，請選取 [FILESTREAM 資料]。</span><span class="sxs-lookup"><span data-stu-id="a861c-122">Select **Filestream Data** if you are adding files (containers) to a memory-optimized filegroup.</span></span>  
  
 <span data-ttu-id="a861c-123">若要將檔案 (容器) 加入至 Filestream 資料檔案群組，就必須啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="a861c-123">To add files (containers) to a Filestream data filegroup, FILESTREAM must be enabled.</span></span> <span data-ttu-id="a861c-124">您可以使用 [[伺服器屬性 (進階頁面)]](../../database-engine/configure-windows/server-properties-advanced-page.md) 對話方塊來啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="a861c-124">You can enable FILESTREAM by using the [Server Properties (Advanced Page)](../../database-engine/configure-windows/server-properties-advanced-page.md) dialog box.</span></span>  
  
 <span data-ttu-id="a861c-125">**檔案群組**</span><span class="sxs-lookup"><span data-stu-id="a861c-125">**Filegroup**</span></span>  
 <span data-ttu-id="a861c-126">從清單中選取檔案的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="a861c-126">Select the filegroup for the file from the list.</span></span> <span data-ttu-id="a861c-127">依預設，此檔案群組為 PRIMARY。</span><span class="sxs-lookup"><span data-stu-id="a861c-127">By default, the filegroup is PRIMARY.</span></span> <span data-ttu-id="a861c-128">您可選取 [\<new filegroup>]，並在 [新增檔案群組] 對話方塊中輸入有關檔案群組的資訊，以建立新的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="a861c-128">You can create a new filegroup by selecting **\<new filegroup>** and entering information about the filegroup in the **New Filegroup** dialog box.</span></span> <span data-ttu-id="a861c-129">新的檔案群組亦可在 **[檔案群組]** 頁面上建立。</span><span class="sxs-lookup"><span data-stu-id="a861c-129">A new filegroup can also be created on the **Filegroup** page.</span></span> <span data-ttu-id="a861c-130">您無法修改現有檔案的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="a861c-130">You cannot modify the filegroup of an existing file.</span></span>  
  
 <span data-ttu-id="a861c-131">將檔案 (容器) 加入至記憶體最佳化檔案群組時，[檔案群組] 欄位會填入資料庫之記憶體最佳化檔案群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="a861c-131">When adding files (containers) to a memory-optimized filegroup, the **Filegroup** field will be populated with the name of the database's memory-optimized filegroup.</span></span>  
  
 <span data-ttu-id="a861c-132">**初始大小**</span><span class="sxs-lookup"><span data-stu-id="a861c-132">**Initial Size**</span></span>  
 <span data-ttu-id="a861c-133">輸入或修改檔案的初始大小 (以 MB 表示)。</span><span class="sxs-lookup"><span data-stu-id="a861c-133">Enter or modify the initial size for the file in megabytes.</span></span> <span data-ttu-id="a861c-134">依預設，這是 **[model]** 資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="a861c-134">By default, this is the value of the **model** database.</span></span>  
  
 <span data-ttu-id="a861c-135">這個欄位對於 FILESTREAM 檔案無效。</span><span class="sxs-lookup"><span data-stu-id="a861c-135">This field is not valid for FILESTREAM files.</span></span>  
  
 <span data-ttu-id="a861c-136">若為記憶體最佳化檔案群組中的檔案，就無法修改此欄位。</span><span class="sxs-lookup"><span data-stu-id="a861c-136">For files in memory-optimized filegroups, this field cannot be modified.</span></span>  
  
 <span data-ttu-id="a861c-137">**自動成長**</span><span class="sxs-lookup"><span data-stu-id="a861c-137">**Autogrowth**</span></span>  
 <span data-ttu-id="a861c-138">選取或顯示檔案的自動成長屬性。</span><span class="sxs-lookup"><span data-stu-id="a861c-138">Select or display the autogrowth properties for the file.</span></span> <span data-ttu-id="a861c-139">這些屬性會控制當達到檔案大小上限時檔案的展開方式。</span><span class="sxs-lookup"><span data-stu-id="a861c-139">These properties control how the file expands when its maximum file size is reached.</span></span> <span data-ttu-id="a861c-140">若要編輯自動成長值，請針對所要的檔案，按一下自動成長屬性旁的 [編輯] 按鈕，並變更 **[變更自動成長]** 對話方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="a861c-140">To edit autogrowth values, click the edit button next to the autogrowth properties for the file that you want, and change the values in the **Change Autogrowth** dialog box.</span></span> <span data-ttu-id="a861c-141">依預設，這些是 **[model]** 資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="a861c-141">By default, these are the values of the **model** database.</span></span>  
  
 <span data-ttu-id="a861c-142">這個欄位對於 FILESTREAM 檔案無效。</span><span class="sxs-lookup"><span data-stu-id="a861c-142">This field is not valid for FILESTREAM files.</span></span>  
  
 <span data-ttu-id="a861c-143">若為記憶體最佳化檔案群組中的檔案，此欄位應該是 [無限制]。</span><span class="sxs-lookup"><span data-stu-id="a861c-143">For files in memory-optimized filegroups, this field should be **Unlimited**.</span></span>  
  
 <span data-ttu-id="a861c-144">**路徑**</span><span class="sxs-lookup"><span data-stu-id="a861c-144">**Path**</span></span>  
 <span data-ttu-id="a861c-145">顯示選取之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a861c-145">Displays the path of the selected file.</span></span> <span data-ttu-id="a861c-146">若要指定新檔案的路徑，請按一下該檔案路徑旁的 [編輯] 按鈕，並導覽到目的資料夾。</span><span class="sxs-lookup"><span data-stu-id="a861c-146">To specify a path for a new file, click the edit button next to the path for the file, and navigate to the destination folder.</span></span> <span data-ttu-id="a861c-147">您無法修改現有檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a861c-147">You cannot modify the path of an existing file.</span></span>  
  
 <span data-ttu-id="a861c-148">如果是 FILESTREAM 檔案，路徑會是資料夾。</span><span class="sxs-lookup"><span data-stu-id="a861c-148">For FILESTREAM files, the path is a folder.</span></span> <span data-ttu-id="a861c-149">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 將會在此資料夾中建立基礎檔案。</span><span class="sxs-lookup"><span data-stu-id="a861c-149">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] will create the underlying files in this folder.</span></span>  
  
 <span data-ttu-id="a861c-150">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="a861c-150">**File Name**</span></span>  
 <span data-ttu-id="a861c-151">顯示檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="a861c-151">Displays the name of the file.</span></span>  
  
 <span data-ttu-id="a861c-152">這個欄位對於 FILESTREAM 檔案無效，包括記憶體最佳化檔案群組中的檔案。</span><span class="sxs-lookup"><span data-stu-id="a861c-152">This field is not valid for FILESTREAM files, including files in memory-optimized filegroups.</span></span>  
  
 <span data-ttu-id="a861c-153">**加入**</span><span class="sxs-lookup"><span data-stu-id="a861c-153">**Add**</span></span>  
 <span data-ttu-id="a861c-154">將新檔案加入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="a861c-154">Add a new file to the database.</span></span>  
  
 <span data-ttu-id="a861c-155">**移除**</span><span class="sxs-lookup"><span data-stu-id="a861c-155">**Remove**</span></span>  
 <span data-ttu-id="a861c-156">從資料庫中刪除選取的檔案。</span><span class="sxs-lookup"><span data-stu-id="a861c-156">Delete the selected file from the database.</span></span> <span data-ttu-id="a861c-157">除非檔案空白，否則就無法移除。</span><span class="sxs-lookup"><span data-stu-id="a861c-157">A file cannot be removed unless it is empty.</span></span> <span data-ttu-id="a861c-158">無法移除主要資料檔案和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a861c-158">The primary data file and log file cannot be removed.</span></span>  
  
 <span data-ttu-id="a861c-159">如需有關檔案的詳細資訊，請參閱＜ [Database Files and Filegroups](database-files-and-filegroups.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a861c-159">For information about files, see [Database Files and Filegroups](database-files-and-filegroups.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a861c-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a861c-160">See Also</span></span>  
 <span data-ttu-id="a861c-161">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a861c-161">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="a861c-162">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a861c-162">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
