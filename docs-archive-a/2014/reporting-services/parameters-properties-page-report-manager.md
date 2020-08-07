---
title: 參數屬性頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ebb53598-2378-46ae-8935-d5192f8ea49a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ddaf6598225c36bd6490797e52aeb1a5fed1b60a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593855"
---
# <a name="parameters-properties-page-report-manager"></a><span data-ttu-id="5c99c-102">參數屬性頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="5c99c-102">Parameters Properties Page (Report Manager)</span></span>
  <span data-ttu-id="5c99c-103">使用 [參數] 屬性頁面，即可檢視或修改參數化報表的參數設定。</span><span class="sxs-lookup"><span data-stu-id="5c99c-103">Use the Parameters properties page to view or modify parameter settings for a parameterized report.</span></span>  
  
 <span data-ttu-id="5c99c-104">發行報表之前，在報表定義中指定參數。</span><span class="sxs-lookup"><span data-stu-id="5c99c-104">Parameters are specified in the report definition before the report is published.</span></span> <span data-ttu-id="5c99c-105">發行報表之後，您可以修改某些參數屬性值。</span><span class="sxs-lookup"><span data-stu-id="5c99c-105">After the report is published, you can modify some parameter property values.</span></span> <span data-ttu-id="5c99c-106">您可修改的值隨著報表中參數的定義方式而改變。</span><span class="sxs-lookup"><span data-stu-id="5c99c-106">The values that you can modify will vary based on how the parameters are defined in the report.</span></span> <span data-ttu-id="5c99c-107">例如，如果定義參數為統計值清單，您可以選擇不同的統計值作為預設值，但不可在清單新增或移除數值。</span><span class="sxs-lookup"><span data-stu-id="5c99c-107">For example, if a list of static values is defined for a parameter, you can choose a different static value to use as a default, but you cannot add or remove values from the list.</span></span> <span data-ttu-id="5c99c-108">同樣地，如果參數是以查詢為基礎，則在發行之前，會先在報表中定義該查詢的所有項目 (包括所使用的資料集、是否允許 Null 或空白的值，以及是否提供預設值)。</span><span class="sxs-lookup"><span data-stu-id="5c99c-108">Similarly, if the parameter is based on a query, all aspects of that query (including the dataset that is used, whether null or blank values are allowed, and whether a default value is provided) are defined in the report before publication.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="5c99c-109">導覽</span><span class="sxs-lookup"><span data-stu-id="5c99c-109">Navigation</span></span>  
 <span data-ttu-id="5c99c-110">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="5c99c-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-parameters-properties-page"></a><span data-ttu-id="5c99c-111">若要開啟參數屬性頁面</span><span class="sxs-lookup"><span data-stu-id="5c99c-111">To open the Parameters properties page</span></span>  
  
1.  <span data-ttu-id="5c99c-112">開啟報表管理員，然後找出您想要修改參數設定的報表。</span><span class="sxs-lookup"><span data-stu-id="5c99c-112">Open Report Manager, and locate the report for which you want to modify parameter settings.</span></span>  
  
2.  <span data-ttu-id="5c99c-113">將滑鼠停留在該報表上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="5c99c-113">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="5c99c-114">在下拉式功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="5c99c-114">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="5c99c-115">這樣就會開啟該報表的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="5c99c-115">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="5c99c-116">選取 [**參數**] 索引標籤。如果看不到 [**參數**] 索引標籤，報表就不會包含參數。</span><span class="sxs-lookup"><span data-stu-id="5c99c-116">Select the **Parameters** tab. If the **Parameters** tab is not visible, the report does not contain parameters.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5c99c-117">選項。</span><span class="sxs-lookup"><span data-stu-id="5c99c-117">Options</span></span>  
 <span data-ttu-id="5c99c-118">**參數名稱**</span><span class="sxs-lookup"><span data-stu-id="5c99c-118">**Parameter Name**</span></span>  
 <span data-ttu-id="5c99c-119">指定參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c99c-119">Specifies the name of the parameter.</span></span>  
  
 <span data-ttu-id="5c99c-120">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="5c99c-120">**Data Type**</span></span>  
 <span data-ttu-id="5c99c-121">指定參數的資料型別。</span><span class="sxs-lookup"><span data-stu-id="5c99c-121">Specifies the data type of the parameter.</span></span>  
  
 <span data-ttu-id="5c99c-122">**有預設值**</span><span class="sxs-lookup"><span data-stu-id="5c99c-122">**Has Default**</span></span>  
 <span data-ttu-id="5c99c-123">選取此核取方塊以指定參數是否具有預設值。</span><span class="sxs-lookup"><span data-stu-id="5c99c-123">Select this check box to specify whether the parameter has a default value.</span></span> <span data-ttu-id="5c99c-124">選取此核取方塊將啟用 **[預設值]**。</span><span class="sxs-lookup"><span data-stu-id="5c99c-124">Selecting this check box enables **Default Value**.</span></span> <span data-ttu-id="5c99c-125">如果報表參數接受 Null 值，它也會啟用 **[Null]** 。</span><span class="sxs-lookup"><span data-stu-id="5c99c-125">It also enables **Null** if the report parameter accepts null values.</span></span> <span data-ttu-id="5c99c-126">如果沒有選取 **[有預設值]** ，您就必須在報表執行時隱藏此值，或提示使用者提供值。</span><span class="sxs-lookup"><span data-stu-id="5c99c-126">If **Has Default** is not selected, you must either hide the value or prompt the user to provide a value when the report runs.</span></span>  
  
 <span data-ttu-id="5c99c-127">**預設值**</span><span class="sxs-lookup"><span data-stu-id="5c99c-127">**Default Value**</span></span>  
 <span data-ttu-id="5c99c-128">指定參數的值。</span><span class="sxs-lookup"><span data-stu-id="5c99c-128">Specify a value for the parameter.</span></span> <span data-ttu-id="5c99c-129">若要指定預設值，則必須選取 **[有預設值]** ，且不得選取 **[Null]** 。</span><span class="sxs-lookup"><span data-stu-id="5c99c-129">To specify a default value, **Has Default** must be selected, and **Null** must not be selected.</span></span> <span data-ttu-id="5c99c-130">可以透過報表定義來提供預設值。</span><span class="sxs-lookup"><span data-stu-id="5c99c-130">A default value may be provided through the report definition.</span></span> <span data-ttu-id="5c99c-131">如果 **[預設值]** 是用一或多個靜態值來擴展的，這些值就會由報表產生。</span><span class="sxs-lookup"><span data-stu-id="5c99c-131">If **Default Value** is populated with one or more static values, those values originate with the report.</span></span> <span data-ttu-id="5c99c-132">如果 **[預設值]** 是 **[以查詢為基礎]**，參數值就會由報表中所定義的查詢來決定。</span><span class="sxs-lookup"><span data-stu-id="5c99c-132">If **Default value** is **Query Based**, the parameter value is determined by a query that is defined in the report.</span></span>  
  
 <span data-ttu-id="5c99c-133">如果 **[預設值]** 能接受輸入的值，您就可以輸入用於報表之資料處理延伸模組的有效常數或語法。</span><span class="sxs-lookup"><span data-stu-id="5c99c-133">If **Default Value** accepts a value, you can type a constant or syntax that is valid for the data processing extension used with the report.</span></span> <span data-ttu-id="5c99c-134">例如，如果資料處理延伸模組的查詢語言支援萬用字元，就可以指定萬用字元作為預設值。</span><span class="sxs-lookup"><span data-stu-id="5c99c-134">For example, if the query language of the data processing extension supports wildcards, you can specify a wildcard character as a default value.</span></span>  
  
 <span data-ttu-id="5c99c-135">如果後續指定對使用者顯示提示，則預設值變成使用者可以使用或修改的初始值。</span><span class="sxs-lookup"><span data-stu-id="5c99c-135">If you subsequently specify that a prompt be displayed to the user, the default value becomes an initial value that users can either use or modify.</span></span> <span data-ttu-id="5c99c-136">若未提示參數值，則對執行該報表的全部使用者都使用此值。</span><span class="sxs-lookup"><span data-stu-id="5c99c-136">If you do not prompt for a parameter value, this value is used for all users who run the report.</span></span>  
  
 <span data-ttu-id="5c99c-137">**Null**</span><span class="sxs-lookup"><span data-stu-id="5c99c-137">**Null**</span></span>  
 <span data-ttu-id="5c99c-138">選取此核取方塊以指定 Null 作為預設值。</span><span class="sxs-lookup"><span data-stu-id="5c99c-138">Select this check box to specify null as the default value.</span></span> <span data-ttu-id="5c99c-139">Null 值表示即使使用者未提供參數值也可以執行報表。</span><span class="sxs-lookup"><span data-stu-id="5c99c-139">A null value means that the report runs even if the user does not provide a parameter value.</span></span> <span data-ttu-id="5c99c-140">如果資料行沒有這個核取方塊，則該參數不接受 Null 值。</span><span class="sxs-lookup"><span data-stu-id="5c99c-140">If there is no check box in this column, the parameter does not accept null values.</span></span>  
  
 <span data-ttu-id="5c99c-141">**隱藏**</span><span class="sxs-lookup"><span data-stu-id="5c99c-141">**Hide**</span></span>  
 <span data-ttu-id="5c99c-142">選取這個核取方塊可以隱藏報表上方參數區域中的參數。</span><span class="sxs-lookup"><span data-stu-id="5c99c-142">Select this check box to hide the parameter in the parameter area that appears at the top of the report.</span></span> <span data-ttu-id="5c99c-143">參數仍會出現在訂閱定義頁面，且仍可指定在報表 URL 上。</span><span class="sxs-lookup"><span data-stu-id="5c99c-143">The parameter will still appear in subscription definition pages and it can still be specified on a report URL.</span></span> <span data-ttu-id="5c99c-144">當想要一律以指定的預設值來執行報表時，隱藏參數相當有用。</span><span class="sxs-lookup"><span data-stu-id="5c99c-144">Hiding the parameter is useful when you want to always run the report with a default value that you specify.</span></span>  
  
 <span data-ttu-id="5c99c-145">如果想要讓參數顯示於報表中，請清除這個核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5c99c-145">Clear this check box if you want the parameter to be visible in the report.</span></span>  
  
 <span data-ttu-id="5c99c-146">**提示使用者**</span><span class="sxs-lookup"><span data-stu-id="5c99c-146">**Prompt User**</span></span>  
 <span data-ttu-id="5c99c-147">選取此核取方塊即可顯示提示使用者輸入參數值的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="5c99c-147">Select this check box to display a text box that prompts users for a parameter value.</span></span>  
  
 <span data-ttu-id="5c99c-148">若要以自主式模式執行報表 (例如產生報表記錄或報表執行快照集)、對全部使用者使用相同的參數值或不要求使用者輸入數值，請清除此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5c99c-148">Clear this check box if you want to run the report in unattended mode (for example, to generate report history or report execution snapshots), if you want to use the same parameter value for all users, or if you do not require user input for the value.</span></span>  
  
 <span data-ttu-id="5c99c-149">**顯示文字**</span><span class="sxs-lookup"><span data-stu-id="5c99c-149">**Display Text**</span></span>  
 <span data-ttu-id="5c99c-150">提供顯示在參數文字方塊旁邊的文字字串。</span><span class="sxs-lookup"><span data-stu-id="5c99c-150">Provide a text string that appears next to the parameter text box.</span></span> <span data-ttu-id="5c99c-151">這個字串提供標籤或描述性文字。</span><span class="sxs-lookup"><span data-stu-id="5c99c-151">This string provides a label or descriptive text.</span></span> <span data-ttu-id="5c99c-152">字串長度沒有限制。</span><span class="sxs-lookup"><span data-stu-id="5c99c-152">There is no limit on string length.</span></span> <span data-ttu-id="5c99c-153">較長的文字字串會在提供的空間中自動換行。</span><span class="sxs-lookup"><span data-stu-id="5c99c-153">Longer text strings wrap within the space provided.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c99c-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c99c-154">See Also</span></span>  
 <span data-ttu-id="5c99c-155">[一般屬性頁面、報表 &#40;報表管理員&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5c99c-155">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 [<span data-ttu-id="5c99c-156">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="5c99c-156">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
