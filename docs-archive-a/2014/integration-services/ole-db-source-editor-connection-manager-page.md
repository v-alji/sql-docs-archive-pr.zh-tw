---
title: OLE DB 來源編輯器 (連線管理員頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsourceadapter.connection.f1
helpviewer_keywords:
- OLE DB Source Editor
ms.assetid: 53699902-8699-4547-b56b-a5b2079e98b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e6b9d841ff902107847a9d85779af41f476315db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599594"
---
# <a name="ole-db-source-editor-connection-manager-page"></a><span data-ttu-id="4f2e1-102">OLE DB 來源編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="4f2e1-102">OLE DB Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="4f2e1-103">使用 [OLE DB 來源編輯器]  對話方塊的 [連接管理員]  頁面，來選取來源的 OLE DB 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-103">Use the **Connection Manager** page of the **OLE DB Source Editor** dialog box to select the OLE DB connection manager for the source.</span></span> <span data-ttu-id="4f2e1-104">這個頁面也可以讓您從資料庫中選取資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-104">This page also lets you select a table or view from the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f2e1-105">若要從使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2007 的資料來源載入資料，請使用 OLE DB 來源。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-105">To load data from a data source that uses [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2007, use an OLE DB source.</span></span> <span data-ttu-id="4f2e1-106">您無法使用 Excel 來源，從 Excel 2007 資料來源載入資料。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-106">You cannot use an Excel source to load data from an Excel 2007 data source.</span></span> <span data-ttu-id="4f2e1-107">如需詳細資訊，請參閱 [設定 OLE DB 連接管理員](configure-ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-107">For more information, see [Configure OLE DB Connection Manager](configure-ole-db-connection-manager.md).</span></span>  
>   
>  <span data-ttu-id="4f2e1-108">若要從使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2003 或更早版本的資料來源載入資料，請使用 Excel 來源。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-108">To load data from a data source that uses [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2003 or earlier, use an Excel source.</span></span> <span data-ttu-id="4f2e1-109">如需詳細資訊，請參閱 [Excel 來源編輯器 &#40;連接管理員頁面&#41;](../../2014/integration-services/excel-source-editor-connection-manager-page.md)。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-109">For more information, see [Excel Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/excel-source-editor-connection-manager-page.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f2e1-110">[ `CommandTimeout` **OLE DB 來源編輯器**] 中無法使用 OLE DB 來源的屬性，但是可以使用**進階編輯器**來設定。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-110">The `CommandTimeout` property of the OLE DB source is not available in the **OLE DB Source Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="4f2e1-111">如需這個屬性的詳細資訊，請參閱 [OLE DB 自訂屬性](data-flow/ole-db-custom-properties.md)的＜Excel 來源＞一節。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-111">For more information on this property, see the Excel Source section of [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md).</span></span>  
  
 <span data-ttu-id="4f2e1-112">若要深入了解 OLE DB 來源，請參閱＜ [OLE DB Source](data-flow/ole-db-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-112">To learn more about the OLE DB source, see [OLE DB Source](data-flow/ole-db-source.md).</span></span>  
  
## <a name="open-the-ole-db-source-editor-connection-manager-page"></a><span data-ttu-id="4f2e1-113">開啟 OLE DB 來源編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="4f2e1-113">Open the OLE DB Source Editor (Connection Manager Page</span></span>  
  
1.  <span data-ttu-id="4f2e1-114">將 OLE DB 來源加入 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝 (於 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中)。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-114">Add the OLE DB source to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="4f2e1-115">以滑鼠右鍵按一下來源元件，然後按一下 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-115">Right-click the source component and when click **Edit**.</span></span>  
  
3.  <span data-ttu-id="4f2e1-116">按一下 [連接管理員]  。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-116">Click **Connection Manager**.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="4f2e1-117">靜態選項</span><span class="sxs-lookup"><span data-stu-id="4f2e1-117">Static Options</span></span>  
 <span data-ttu-id="4f2e1-118">**[無快取]**</span><span class="sxs-lookup"><span data-stu-id="4f2e1-118">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="4f2e1-119">從清單中選取現有的連線管理員，或按一下 [新增]  來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-119">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="4f2e1-120">**新增**</span><span class="sxs-lookup"><span data-stu-id="4f2e1-120">**New**</span></span>  
 <span data-ttu-id="4f2e1-121">使用 [設定 OLE DB 連線管理員]  對話方塊建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-121">Create a new connection manager by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="4f2e1-122">**資料存取模式**</span><span class="sxs-lookup"><span data-stu-id="4f2e1-122">**Data access mode**</span></span>  
 <span data-ttu-id="4f2e1-123">從來源中指定選取資料的方法。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-123">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="4f2e1-124">選項</span><span class="sxs-lookup"><span data-stu-id="4f2e1-124">Option</span></span>|<span data-ttu-id="4f2e1-125">描述</span><span class="sxs-lookup"><span data-stu-id="4f2e1-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4f2e1-126">資料表或檢視</span><span class="sxs-lookup"><span data-stu-id="4f2e1-126">Table or view</span></span>|<span data-ttu-id="4f2e1-127">從 OLE DB 資料來源中的資料表或檢視擷取資料。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-127">Retrieve data from a table or view in the OLE DB data source.</span></span>|  
|<span data-ttu-id="4f2e1-128">資料表名稱或檢視名稱變數</span><span class="sxs-lookup"><span data-stu-id="4f2e1-128">Table name or view name variable</span></span>|<span data-ttu-id="4f2e1-129">請在變數中指定資料表或檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-129">Specify the table or view name in a variable.</span></span><br /><br /> <span data-ttu-id="4f2e1-130">**相關資訊：** [在套件中使用變數](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="4f2e1-130">**Related information:** [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="4f2e1-131">SQL (命令)</span><span class="sxs-lookup"><span data-stu-id="4f2e1-131">SQL command</span></span>|<span data-ttu-id="4f2e1-132">使用 SQL 查詢從 OLE DB 資料來源中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-132">Retrieve data from the OLE DB data source by using a SQL query.</span></span>|  
|<span data-ttu-id="4f2e1-133">來自變數的 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="4f2e1-133">SQL command from variable</span></span>|<span data-ttu-id="4f2e1-134">在變數中指定 SQL 查詢文字。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-134">Specify the SQL query text in a variable.</span></span>|  
  
 <span data-ttu-id="4f2e1-135">**預覽**</span><span class="sxs-lookup"><span data-stu-id="4f2e1-135">**Preview**</span></span>  
 <span data-ttu-id="4f2e1-136">使用 [資料檢視]  對話方塊來預覽結果。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-136">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="4f2e1-137">[預覽]  最多可顯示 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-137">**Preview** can display up to 200 rows.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f2e1-138">在預覽資料時，具有 CLR 使用者定義型別的資料行不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-138">When you preview data, columns with a CLR user-defined type do not contain data.</span></span> <span data-ttu-id="4f2e1-139">而會顯示值 \<value too big to display> 或 System.Byte[]。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-139">Instead the values \<value too big to display> or System.Byte[] display.</span></span> <span data-ttu-id="4f2e1-140">使用 SQL OLE DB 提供者存取資料來源時會顯示前者，而使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client 提供者時會顯示後者。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-140">The former displays when the data source is accessed using the SQL OLE DB provider, the latter when using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client provider.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="4f2e1-141">資料存取模式動態選項</span><span class="sxs-lookup"><span data-stu-id="4f2e1-141">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="4f2e1-142">資料存取模式 = 資料表或檢視</span><span class="sxs-lookup"><span data-stu-id="4f2e1-142">Data access mode = Table or view</span></span>  
 <span data-ttu-id="4f2e1-143">**資料表或檢視的名稱**</span><span class="sxs-lookup"><span data-stu-id="4f2e1-143">**Name of the table or the view**</span></span>  
 <span data-ttu-id="4f2e1-144">從資料來源中可用的清單中選取資料表或檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-144">Select the name of the table or view from a list of those available in the data source.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="4f2e1-145">資料存取模式 = 資料表名稱或檢視名稱變數</span><span class="sxs-lookup"><span data-stu-id="4f2e1-145">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="4f2e1-146">**變數名稱**</span><span class="sxs-lookup"><span data-stu-id="4f2e1-146">**Variable name**</span></span>  
 <span data-ttu-id="4f2e1-147">請選取包含資料表或檢視名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-147">Select the variable that contains the name of the table or view.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="4f2e1-148">資料存取模式 = SQL 命令</span><span class="sxs-lookup"><span data-stu-id="4f2e1-148">Data access mode = SQL command</span></span>  
 <span data-ttu-id="4f2e1-149">**SQL 命令文字**</span><span class="sxs-lookup"><span data-stu-id="4f2e1-149">**SQL command text**</span></span>  
 <span data-ttu-id="4f2e1-150">輸入 SQL 查詢文字，按一下 [建立查詢]  建立查詢，或按一下 [瀏覽]  找到包含查詢文字的檔案。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-150">Enter the text of a SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="4f2e1-151">**參數**</span><span class="sxs-lookup"><span data-stu-id="4f2e1-151">**Parameters**</span></span>  
 <span data-ttu-id="4f2e1-152">如果您所輸入的參數化查詢使用 ?</span><span class="sxs-lookup"><span data-stu-id="4f2e1-152">If you have entered a parameterized query by using ?</span></span> <span data-ttu-id="4f2e1-153">做為查詢文字中的參數預留位置，請使用 **[設定查詢參數]** 對話方塊，將查詢輸入參數對應到封裝變數。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-153">as a parameter placeholder in the query text, use the **Set Query Parameters** dialog box to map query input parameters to package variables.</span></span>  
  
 <span data-ttu-id="4f2e1-154">**建立查詢**</span><span class="sxs-lookup"><span data-stu-id="4f2e1-154">**Build query**</span></span>  
 <span data-ttu-id="4f2e1-155">使用 [查詢產生器]  對話方塊，以視覺化的方式來建構 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-155">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="4f2e1-156">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="4f2e1-156">**Browse**</span></span>  
 <span data-ttu-id="4f2e1-157">使用 [開啟]  對話方塊來找出包含 SQL 查詢文字的檔案。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-157">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="4f2e1-158">**剖析查詢**</span><span class="sxs-lookup"><span data-stu-id="4f2e1-158">**Parse query**</span></span>  
 <span data-ttu-id="4f2e1-159">請確認查詢文字的語法。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-159">Verify the syntax of the query text.</span></span>  
  
### <a name="data-access-mode--sql-command-from-variable"></a><span data-ttu-id="4f2e1-160">資料存取模式 = 來自變數的 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="4f2e1-160">Data access mode = SQL command from variable</span></span>  
 <span data-ttu-id="4f2e1-161">**變數名稱**</span><span class="sxs-lookup"><span data-stu-id="4f2e1-161">**Variable name**</span></span>  
 <span data-ttu-id="4f2e1-162">選取包含 SQL 查詢文字的變數。</span><span class="sxs-lookup"><span data-stu-id="4f2e1-162">Select the variable that contains the text of the SQL query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f2e1-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f2e1-163">See Also</span></span>  
 <span data-ttu-id="4f2e1-164">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4f2e1-164">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="4f2e1-165">[OLE DB 來源編輯器 &#40;資料行] 頁面&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="4f2e1-165">[OLE DB Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="4f2e1-166">[OLE DB 來源編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="4f2e1-166">[OLE DB Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="4f2e1-167">[使用 OLE DB 來源來解壓縮資料](data-flow/extract-data-by-using-the-ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="4f2e1-167">[Extract Data by Using the OLE DB Source](data-flow/extract-data-by-using-the-ole-db-source.md) </span></span>  
 [<span data-ttu-id="4f2e1-168">OLE DB 連線管理員</span><span class="sxs-lookup"><span data-stu-id="4f2e1-168">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  
