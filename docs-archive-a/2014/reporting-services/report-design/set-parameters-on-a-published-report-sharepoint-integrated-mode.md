---
title: 在已發行的報表上設定參數 (SharePoint 整合模式中的 Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], content management
- report parameters [Reporting Services]
ms.assetid: dec5d985-a6c1-4dd8-8a66-a848e89a2e18
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4d0a2b1a23f382adb9e0cdddbebcded0050d34bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585029"
---
# <a name="set-parameters-on-a-published-report-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="13ba0-102">在已發行的報表上設定參數 (SharePoint 整合模式中的 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="13ba0-102">Set Parameters on a Published Report (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="13ba0-103">參數化報表是指可接受輸入值的報表，而這些輸入值會在您執行報表時用來篩選資料。</span><span class="sxs-lookup"><span data-stu-id="13ba0-103">A parameterized report is a report that accepts input values that are used to filter data when you run the report.</span></span> <span data-ttu-id="13ba0-104">參數是在報表建立時定義的。</span><span class="sxs-lookup"><span data-stu-id="13ba0-104">Parameters are defined when the report is created.</span></span> <span data-ttu-id="13ba0-105">根據報表參數在報表定義中的定義方式，它可能會接受單一值、多個值或動態值，而這些值會變更以便回應之前的選取項目 (例如，當您選取產品類別目錄時，下一個選取項目可能是來自該類別目錄的特定產品)。</span><span class="sxs-lookup"><span data-stu-id="13ba0-105">Depending on how a report parameter is defined in the report definition, it can accept a single value, multiple values, or dynamic values, which change in response to a previous selection (for example, when you select product category, your next selection might be a specific product from that category).</span></span> <span data-ttu-id="13ba0-106">參數可能會有預設值，而且此值可用來自動執行已篩選的報表版本或可能由不同的值取代。</span><span class="sxs-lookup"><span data-stu-id="13ba0-106">A parameter can have a default value, which can be used to run a filtered version of the report automatically or possibly be replaced with a different value.</span></span>  
  
 <span data-ttu-id="13ba0-107">這些屬性可以在報表定義中設定，或是在已經發行報表後設定。</span><span class="sxs-lookup"><span data-stu-id="13ba0-107">These properties can be set in the report definition, or after the report is published.</span></span> <span data-ttu-id="13ba0-108">雖然您可以在已發行的報表中修改某些參數屬性來變更值並顯示屬性，但是您無法變更參數名稱或資料類型。</span><span class="sxs-lookup"><span data-stu-id="13ba0-108">Although you can modify some parameter properties in a published to change the value and display properties, you cannot change a parameter name or the data type.</span></span> <span data-ttu-id="13ba0-109">參數名稱與資料類型僅能透過報表定義中的報表作者變更。</span><span class="sxs-lookup"><span data-stu-id="13ba0-109">The parameter name and data type can only be changed by the report author in the report definition.</span></span>  
  
 <span data-ttu-id="13ba0-110">若要執行參數化的報表，雖然報表可能包含要從中選擇之有效值的下拉式清單，但是您通常必須知道要輸入哪些值。</span><span class="sxs-lookup"><span data-stu-id="13ba0-110">To run a parameterized report, you typically must know which values to type, although a report might include drop-down lists of valid values from which to choose.</span></span>  
  
 <span data-ttu-id="13ba0-111">若要在已發行的報表上設定參數屬性，您必須擁有該報表的「編輯項目」權限。</span><span class="sxs-lookup"><span data-stu-id="13ba0-111">To set parameter properties on a published report, you must have Edit Items permission for the report.</span></span> <span data-ttu-id="13ba0-112">您可以在從 SharePoint 網站執行的報表上，修改部分或所有參數屬性。</span><span class="sxs-lookup"><span data-stu-id="13ba0-112">You can modify some or all of the parameter properties on a report that you run from a SharePoint site.</span></span> <span data-ttu-id="13ba0-113">但是，您無法透過儲存想要重複使用之參數值的組合，個人化報表。</span><span class="sxs-lookup"><span data-stu-id="13ba0-113">You cannot personalize a report by saving a combination of parameter values that you want to use repeatedly.</span></span> <span data-ttu-id="13ba0-114">您所指定的任何預設值都會由開啟報表的所有使用者使用。</span><span class="sxs-lookup"><span data-stu-id="13ba0-114">Any default values that you specify are used by all users who open the report.</span></span>  
  
 <span data-ttu-id="13ba0-115">如果報表內嵌在設定為永遠顯示該報表的報表檢視器 Web 組件中，在報表檢視器 Web 組件上設定屬性。</span><span class="sxs-lookup"><span data-stu-id="13ba0-115">If the report is embedded in a Report Viewer Web part that is configured to always show that report, set the properties on the Report Viewer Web Part.</span></span> <span data-ttu-id="13ba0-116">如需詳細資訊，請參閱[將報表檢視器網頁組件新增至網頁 &#40;SharePoint 整合模式的 Reporting Services&#41;](../report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)。</span><span class="sxs-lookup"><span data-stu-id="13ba0-116">For more information, see [Add the Report Viewer Web Part to a Web Page &#40;Reporting Services in SharePoint Integrated Mode&#41;](../report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
### <a name="to-run-a-parameterized-report"></a><span data-ttu-id="13ba0-117">執行參數化的報表</span><span class="sxs-lookup"><span data-stu-id="13ba0-117">To run a parameterized report</span></span>  
  
1.  <span data-ttu-id="13ba0-118">開啟包含報表的文件庫。</span><span class="sxs-lookup"><span data-stu-id="13ba0-118">Open the library that contains the report.</span></span>  
  
2.  <span data-ttu-id="13ba0-119">按一下報表名稱。</span><span class="sxs-lookup"><span data-stu-id="13ba0-119">Click the report name.</span></span> <span data-ttu-id="13ba0-120">您必須事先知道哪些報表具有參數。</span><span class="sxs-lookup"><span data-stu-id="13ba0-120">You must know in advance which reports have parameters.</span></span> <span data-ttu-id="13ba0-121">報表上沒有視覺上的識別碼可以表示該報表已被參數化。</span><span class="sxs-lookup"><span data-stu-id="13ba0-121">There is no visual identifier on the report to indicate that it is parameterized.</span></span>  
  
3.  <span data-ttu-id="13ba0-122">當報表開啟時，指定您要使用的參數。</span><span class="sxs-lookup"><span data-stu-id="13ba0-122">When the report opens, specify the parameters you want to use.</span></span> <span data-ttu-id="13ba0-123">根據屬性在報表檢視器 Web 組件上的設定，可能可以顯示、折疊或隱藏 [參數] 區域。</span><span class="sxs-lookup"><span data-stu-id="13ba0-123">The Parameters area might be visible, collapsed, or hidden depending on how properties are set on the Report Viewer Web Part.</span></span>  
  
    1.  <span data-ttu-id="13ba0-124">如果有顯示 [參數] 區域，為每個參數選擇一個值。</span><span class="sxs-lookup"><span data-stu-id="13ba0-124">If the Parameters area is visible, choose a value for each parameter.</span></span>  
  
    2.  <span data-ttu-id="13ba0-125">如果有一條細色帶沿著中央有個箭號的報表長度向下，表示 [參數] 區域是折疊的。</span><span class="sxs-lookup"><span data-stu-id="13ba0-125">If there is a thin strip of color that runs down the length of the report that has an arrow in the middle of it, the Parameters area is collapsed.</span></span> <span data-ttu-id="13ba0-126">您可以按一下箭號，來展開它。</span><span class="sxs-lookup"><span data-stu-id="13ba0-126">You can click the arrow to expand it.</span></span>  
  
    3.  <span data-ttu-id="13ba0-127">如果 [參數] 區域已隱藏，您就無法指定值。</span><span class="sxs-lookup"><span data-stu-id="13ba0-127">If the Parameters area is hidden, you cannot specify a value.</span></span>  
  
4.  <span data-ttu-id="13ba0-128">在 [參數] 區域底部按一下 [套用]  以執行報表。</span><span class="sxs-lookup"><span data-stu-id="13ba0-128">Click **Apply** at the bottom of the Parameters area to run the report.</span></span>  
  
     <span data-ttu-id="13ba0-129">有時候，指定了值的組合可能也無法提供您所預期的結果。</span><span class="sxs-lookup"><span data-stu-id="13ba0-129">It is possible to specify a combination of values that do not give you the results you expect.</span></span> <span data-ttu-id="13ba0-130">如果您沒有取得所需的資訊，可能就需要由報表作者修改報表。</span><span class="sxs-lookup"><span data-stu-id="13ba0-130">The report might need to be modified by the report author if you are not getting the information you require.</span></span>  
  
5.  <span data-ttu-id="13ba0-131">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="13ba0-131">Click **OK**.</span></span>  
  
### <a name="to-set-parameter-properties"></a><span data-ttu-id="13ba0-132">設定參數屬性</span><span class="sxs-lookup"><span data-stu-id="13ba0-132">To set parameter properties</span></span>  
  
1.  <span data-ttu-id="13ba0-133">開啟包含報表的文件庫或資料夾。</span><span class="sxs-lookup"><span data-stu-id="13ba0-133">Open the library or folder that contains the report.</span></span>  
  
2.  <span data-ttu-id="13ba0-134">指向報表，然後按一下向下箭號。</span><span class="sxs-lookup"><span data-stu-id="13ba0-134">Point to the report and click the down arrow.</span></span>  
  
3.  <span data-ttu-id="13ba0-135">按一下 [管理參數]  。</span><span class="sxs-lookup"><span data-stu-id="13ba0-135">Click **Manage Parameters**.</span></span> <span data-ttu-id="13ba0-136">如果報表包含參數，每個參數都會列在頁面上。</span><span class="sxs-lookup"><span data-stu-id="13ba0-136">If the report contains parameters, each parameter will be listed on the page.</span></span> <span data-ttu-id="13ba0-137">此清單會顯示參數名稱、資料類型、預設使用的資料值，以及開啟報表時它是否會顯示在參數區域中。</span><span class="sxs-lookup"><span data-stu-id="13ba0-137">The list shows the parameter name, data type, data value that is used by default, and whether it is visible in the parameter area when you open the report.</span></span>  
  
4.  <span data-ttu-id="13ba0-138">按一下清單中的參數，即可修改其設定。</span><span class="sxs-lookup"><span data-stu-id="13ba0-138">Click a parameter in the list to modify its settings.</span></span>  
  
5.  <span data-ttu-id="13ba0-139">在 [預設值] 中，輸入參數的值。</span><span class="sxs-lookup"><span data-stu-id="13ba0-139">In Default Value, enter a value for the parameter.</span></span> <span data-ttu-id="13ba0-140">由於此值將不會進行驗證，因此請確定您提供了適用於報表的值。</span><span class="sxs-lookup"><span data-stu-id="13ba0-140">The value will not be validated, so be sure that you are providing a value that works for the report.</span></span>  
  
    1.  <span data-ttu-id="13ba0-141">如果您要使用建立報表時所定義的預設值，請選擇 [使用報表定義中指定的值運算式]  。</span><span class="sxs-lookup"><span data-stu-id="13ba0-141">Choose **Use value expression specified in report definition** if you want to use the default value that was defined when the report was created.</span></span> <span data-ttu-id="13ba0-142">如果報表定義不提供預設值，將無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="13ba0-142">If the report definition does not provide a default value, this option will be unavailable.</span></span>  
  
    2.  <span data-ttu-id="13ba0-143">如果您要為報表定義預設值指定一個取代值，請選擇 [覆寫報表預設值]  。</span><span class="sxs-lookup"><span data-stu-id="13ba0-143">Choose **Override the report default value** if you want to specify a replacement for the report definition default value.</span></span> <span data-ttu-id="13ba0-144">對於接受 Null 值的報表參數，您可以根據該參數，選擇性地選取 [Null]  核取方塊以防止篩選。</span><span class="sxs-lookup"><span data-stu-id="13ba0-144">Optionally, for report parameters that accept null values, you can select the **Null** check box to prevent filtering based on that parameter.</span></span>  
  
    3.  <span data-ttu-id="13ba0-145">如果您想讓每位使用者指定值，然後再處理報表，請選擇 [參數沒有預設值]  。</span><span class="sxs-lookup"><span data-stu-id="13ba0-145">Choose **Parameter does not have a default value** if you want each user to specify a value before the report is processed.</span></span> <span data-ttu-id="13ba0-146">如果您選取這個選項，就應該設定提示使用者指定值的顯示設定。</span><span class="sxs-lookup"><span data-stu-id="13ba0-146">If you select this option, you should set display settings that prompt the user to specify a value.</span></span>  
  
     <span data-ttu-id="13ba0-147">請注意，如果所有參數值都具有預設值，當使用者開啟報表時，報表將會使用這些值自動執行。</span><span class="sxs-lookup"><span data-stu-id="13ba0-147">Note that if all parameter values have a default value, the report will automatically run with those values when the user opens the report.</span></span> <span data-ttu-id="13ba0-148">不過，如果有顯示參數區域，使用者可以覆寫預設值，然後重新執行報表。</span><span class="sxs-lookup"><span data-stu-id="13ba0-148">However, if the parameter area is displayed, users can override the default value and re-run the report.</span></span>  
  
6.  <span data-ttu-id="13ba0-149">您可以設定顯示選項，以便決定參數是否會顯示。</span><span class="sxs-lookup"><span data-stu-id="13ba0-149">Set display options to determine whether the parameter is visible.</span></span>  
  
    1.  <span data-ttu-id="13ba0-150">選擇 [提示使用者]  ，即可在頁面上顯示參數。</span><span class="sxs-lookup"><span data-stu-id="13ba0-150">Choose **Prompt User** to show the parameter on the page.</span></span> <span data-ttu-id="13ba0-151">您可以指定出現在欄位中的提示文字，以提供關於使用者必須提供之資料格式或類型的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="13ba0-151">You can specify prompt text that appears within a field to provide a brief statement about the format or type of data that the user must provide.</span></span>  
  
    2.  <span data-ttu-id="13ba0-152">如果您要使用預設值，而且不想讓此參數顯示在 [參數] 區域中，請選擇 [隱藏]  。</span><span class="sxs-lookup"><span data-stu-id="13ba0-152">Choose **Hidden** if you are using a default value and you do not want the parameter to be visible in the Parameters area.</span></span>  
  
    3.  <span data-ttu-id="13ba0-153">如果您要使用預設值，而且不想讓此參數顯示在 [參數] 區域或訂閱頁面上，請選擇 [內部]  。</span><span class="sxs-lookup"><span data-stu-id="13ba0-153">Choose **Internal** if you are using a default value and you do not want the parameter to be visible in the Parameters area or on subscription pages.</span></span>  
  
7.  <span data-ttu-id="13ba0-154">按一下 [套用]  。</span><span class="sxs-lookup"><span data-stu-id="13ba0-154">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13ba0-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13ba0-155">See Also</span></span>  
 [<span data-ttu-id="13ba0-156">報表伺服器項目的 SharePoint 網站和清單權限參考</span><span class="sxs-lookup"><span data-stu-id="13ba0-156">SharePoint Site and List Permission Reference for Report Server Items</span></span>](../security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)  
  
  
