---
title: 設定一般檔案目的地 (SQL Server 的匯入及匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.configureflatfiledest.f1
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2af8a1653d9a1aef0828aa112a25825ed23b8bf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597942"
---
# <a name="configure-flat-file-destination-sql-server-import-and-export-wizard"></a><span data-ttu-id="f8f78-102">設定一般檔案目的地 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="f8f78-102">Configure Flat File Destination (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="f8f78-103">使用 [**設定**一般檔案目的地] 頁面，即可指定目的地一般檔案的格式化選項，並在繼續之前預覽結果。</span><span class="sxs-lookup"><span data-stu-id="f8f78-103">Use the **Configure Flat File Destination** page to specify formatting options for the destination flat file, and to preview results before continuing.</span></span>  
  
 <span data-ttu-id="f8f78-104">若要深入瞭解此嚮導，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="f8f78-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="f8f78-105">若要瞭解用來啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="f8f78-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="f8f78-106">「SQL Server 匯入和匯出精靈」的用途在於將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="f8f78-106">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="f8f78-107">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="f8f78-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="f8f78-108">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="f8f78-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="f8f78-109">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="f8f78-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f8f78-110">選項</span><span class="sxs-lookup"><span data-stu-id="f8f78-110">Options</span></span>  
 <span data-ttu-id="f8f78-111">**來源一般檔案**</span><span class="sxs-lookup"><span data-stu-id="f8f78-111">**Source flat file**</span></span>  
 <span data-ttu-id="f8f78-112">目的地檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="f8f78-112">The name of the destination file.</span></span>  
  
 <span data-ttu-id="f8f78-113">**資料列分隔符號**</span><span class="sxs-lookup"><span data-stu-id="f8f78-113">**Row delimiter**</span></span>  
 <span data-ttu-id="f8f78-114">從資料列分隔符號的清單中選取。</span><span class="sxs-lookup"><span data-stu-id="f8f78-114">Select from the list of delimiters for rows.</span></span>  
  
|<span data-ttu-id="f8f78-115">值</span><span class="sxs-lookup"><span data-stu-id="f8f78-115">Value</span></span>|<span data-ttu-id="f8f78-116">描述</span><span class="sxs-lookup"><span data-stu-id="f8f78-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f8f78-117">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-117">**{CR}{LF}**</span></span>|<span data-ttu-id="f8f78-118">資料列是以歸位字元和換行字元的組合分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-118">The row is delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="f8f78-119">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-119">**{CR}**</span></span>|<span data-ttu-id="f8f78-120">資料列是以歸位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-120">The row is delimited by a carriage return.</span></span>|  
|<span data-ttu-id="f8f78-121">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-121">**{LF}**</span></span>|<span data-ttu-id="f8f78-122">資料列是以換行字元分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-122">The row is delimited by a line feed.</span></span>|  
|<span data-ttu-id="f8f78-123">**分號 {;}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-123">**Semicolon {;}**</span></span>|<span data-ttu-id="f8f78-124">資料列是以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-124">The row is delimited by a semicolon.</span></span>|  
|<span data-ttu-id="f8f78-125">**冒號 {:}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-125">**Colon {:}**</span></span>|<span data-ttu-id="f8f78-126">資料列是以冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-126">The row is delimited by a colon.</span></span>|  
|<span data-ttu-id="f8f78-127">**逗號 {,}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-127">**Comma {,}**</span></span>|<span data-ttu-id="f8f78-128">資料列是以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-128">The row is delimited by a comma.</span></span>|  
|<span data-ttu-id="f8f78-129">**定位字元 {t}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-129">**Tab {t}**</span></span>|<span data-ttu-id="f8f78-130">資料列是以定位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-130">The row is delimited by a tab.</span></span>|  
|<span data-ttu-id="f8f78-131">**分隔號 {&#124;}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-131">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="f8f78-132">資料列是以分隔號分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-132">The row is delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="f8f78-133">**資料行分隔符號**</span><span class="sxs-lookup"><span data-stu-id="f8f78-133">**Column delimiter**</span></span>  
 <span data-ttu-id="f8f78-134">從資料行分隔符號的清單中選取。</span><span class="sxs-lookup"><span data-stu-id="f8f78-134">Select from the list of delimiters for columns.</span></span>  
  
|<span data-ttu-id="f8f78-135">值</span><span class="sxs-lookup"><span data-stu-id="f8f78-135">Value</span></span>|<span data-ttu-id="f8f78-136">描述</span><span class="sxs-lookup"><span data-stu-id="f8f78-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f8f78-137">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-137">**{CR}{LF}**</span></span>|<span data-ttu-id="f8f78-138">資料行是以歸位字元和換行字元的組合分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-138">The columns are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="f8f78-139">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-139">**{CR}**</span></span>|<span data-ttu-id="f8f78-140">資料行是以歸位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-140">The columns are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="f8f78-141">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-141">**{LF}**</span></span>|<span data-ttu-id="f8f78-142">資料行是以換行字元分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-142">The columns are delimited by a line feed.</span></span>|  
|<span data-ttu-id="f8f78-143">**分號 {;}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-143">**Semicolon {;}**</span></span>|<span data-ttu-id="f8f78-144">資料行是以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-144">The columns are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="f8f78-145">**冒號 {:}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-145">**Colon {:}**</span></span>|<span data-ttu-id="f8f78-146">資料行是以冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-146">The columns are delimited by a colon.</span></span>|  
|<span data-ttu-id="f8f78-147">**逗號 {,}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-147">**Comma {,}**</span></span>|<span data-ttu-id="f8f78-148">資料行是以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-148">The columns are delimited by a comma.</span></span>|  
|<span data-ttu-id="f8f78-149">**定位字元 {t}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-149">**Tab {t}**</span></span>|<span data-ttu-id="f8f78-150">資料行是以定位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-150">The columns are delimited by a tab.</span></span>|  
|<span data-ttu-id="f8f78-151">**分隔號 {&#124;}**</span><span class="sxs-lookup"><span data-stu-id="f8f78-151">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="f8f78-152">資料行是以分隔號分隔。</span><span class="sxs-lookup"><span data-stu-id="f8f78-152">The columns are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="f8f78-153">**預覽**</span><span class="sxs-lookup"><span data-stu-id="f8f78-153">**Preview**</span></span>  
 <span data-ttu-id="f8f78-154">在 [**預覽資料**] 對話方塊中，針對目的地一般檔案選取的格式化選項結果。</span><span class="sxs-lookup"><span data-stu-id="f8f78-154">View in the **Preview Data** dialog box the results of the selected formatting options for the destination flat file.</span></span>  
  
 <span data-ttu-id="f8f78-155">**編輯轉換**</span><span class="sxs-lookup"><span data-stu-id="f8f78-155">**Edit transform**</span></span>  
 <span data-ttu-id="f8f78-156">使用 [資料行對應] 對話方塊，刪除資料列、附加資料列，以及設定目的地檔案**中的資料**行。</span><span class="sxs-lookup"><span data-stu-id="f8f78-156">Delete rows, append rows, and configure columns in the destination file by using the **Column Mappings** dialog box.</span></span>  
  
  
