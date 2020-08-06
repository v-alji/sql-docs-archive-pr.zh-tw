---
title: 啟用和停用 RDL 沙箱 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d5619e9f-ec5b-4376-9b34-1f74de6fade7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7af1477751093862c99d00978278315e600511e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703886"
---
# <a name="enable-and-disable-rdl-sandboxing"></a><span data-ttu-id="3bd71-102">啟用或停用 RDL 沙箱</span><span class="sxs-lookup"><span data-stu-id="3bd71-102">Enable and Disable RDL Sandboxing</span></span>
  <span data-ttu-id="3bd71-103">RDL (報表定義語言) 沙箱功能可在多個租用戶使用報表伺服器之單一 Web 伺服陣列的環境中，讓您偵測及限制個別租用戶使用特定資源類型的情形。</span><span class="sxs-lookup"><span data-stu-id="3bd71-103">The RDL (Report Definition Language) Sandboxing feature lets you detect and restrict the usage of specific types of resources, by individual tenants, in an environment of multiple tenants that use a single web farm of report servers.</span></span> <span data-ttu-id="3bd71-104">這種情形的一個範例是裝載服務案例，在此案例中，您可能要為由多個可能分屬不同公司的租用戶所使用的報表伺服器，維護單一 Web 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="3bd71-104">An example of this is a hosting services scenario where you might maintain a single web farm of report servers that are used by multiple tenants, and perhaps different companies.</span></span> <span data-ttu-id="3bd71-105">您身為報表伺服器管理員，可以啟用此功能來幫助您達成下列目標：</span><span class="sxs-lookup"><span data-stu-id="3bd71-105">As a report server administrator, you can enable this feature to help achieve the following objectives:</span></span>  
  
-   <span data-ttu-id="3bd71-106">限制外部資源的大小。</span><span class="sxs-lookup"><span data-stu-id="3bd71-106">Restrict external resource sizes.</span></span> <span data-ttu-id="3bd71-107">外部資源包括影像、.xslt 檔案和對應資料。</span><span class="sxs-lookup"><span data-stu-id="3bd71-107">External resources include images, .xslt files, and map data.</span></span>  
  
-   <span data-ttu-id="3bd71-108">在報表發行時間，限制用於運算式文字的型別和成員。</span><span class="sxs-lookup"><span data-stu-id="3bd71-108">At report publish time, limit types and members that are used in expression text.</span></span>  
  
-   <span data-ttu-id="3bd71-109">在報表處理時間，限制運算式的文字長度和傳回值大小。</span><span class="sxs-lookup"><span data-stu-id="3bd71-109">At report processing time, limit the length of the text and the size of the return value for expressions.</span></span>  
  
 <span data-ttu-id="3bd71-110">當啟用 RDL 沙箱功能時，將會停用下列功能：</span><span class="sxs-lookup"><span data-stu-id="3bd71-110">When RDL Sandboxing is enabled, the following features are disabled:</span></span>  
  
-   <span data-ttu-id="3bd71-111">報表定義之元素中的自訂程式碼 **\<Code>** 。</span><span class="sxs-lookup"><span data-stu-id="3bd71-111">Custom code in the **\<Code>** element of a report definition.</span></span>  
  
-   <span data-ttu-id="3bd71-112">RDL 對於 [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] 自訂報表項目的回溯相容性模式。</span><span class="sxs-lookup"><span data-stu-id="3bd71-112">RDL backward compatibility mode for [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] custom report items.</span></span>  
  
-   <span data-ttu-id="3bd71-113">運算式中的指名參數。</span><span class="sxs-lookup"><span data-stu-id="3bd71-113">Named parameters in expressions.</span></span>  
  
 <span data-ttu-id="3bd71-114">本主題描述 RSReportServer.Config 檔案中 <> 元素中的每個元素 `RDLSandboxing` 。</span><span class="sxs-lookup"><span data-stu-id="3bd71-114">This topic describes each element in the <`RDLSandboxing`> element in the RSReportServer.Config file.</span></span> <span data-ttu-id="3bd71-115">如需如何編輯此檔案的詳細資訊，請參閱[Modify a Reporting Services Configuration File (RSreportserver.config)](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) (修改 Reporting Services 組態檔 (RSreportserver.config))。</span><span class="sxs-lookup"><span data-stu-id="3bd71-115">For more information about how to modify this file, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).</span></span> <span data-ttu-id="3bd71-116">伺服器追蹤記錄會記錄與 RDL 沙箱功能有關的活動。</span><span class="sxs-lookup"><span data-stu-id="3bd71-116">A server trace log records activity related to the RDL Sandboxing feature.</span></span> <span data-ttu-id="3bd71-117">如需追蹤紀錄的詳細資訊，請參閱 [報表伺服器服務追蹤記錄](report-server/report-server-service-trace-log.md)。</span><span class="sxs-lookup"><span data-stu-id="3bd71-117">For more information about trace logs, see [Report Server Service Trace Log](report-server/report-server-service-trace-log.md).</span></span>  
  
## <a name="example-configuration"></a><span data-ttu-id="3bd71-118">設定範例</span><span class="sxs-lookup"><span data-stu-id="3bd71-118">Example Configuration</span></span>  
 <span data-ttu-id="3bd71-119">下列範例會顯示 RSReportServer.Config 檔案中 <> 元素的設定和範例值 `RDLSandboxing` 。</span><span class="sxs-lookup"><span data-stu-id="3bd71-119">The following example shows the settings and example values for the <`RDLSandboxing`> element in the RSReportServer.Config file.</span></span>  
  
```  
<RDLSandboxing>  
   <MaxExpressionLength>5000</MaxExpressionLength>  
   <MaxResourceSize>5000</MaxResourceSize>  
   <MaxStringResultLength>3000</MaxStringResultLength>  
   <MaxArrayResultLength>250</MaxArrayResultLength>  
   <Types>  
      <Allow Namespace="System.Drawing" AllowNew="True">Bitmap</Allow>  
      <Allow Namespace="TypeConverters.Custom" AllowNew="True">*</Allow>  
   </Types>  
   <Members>  
      <Deny>Format</Deny>  
      <Deny>StrDup</Deny>  
   </Members>  
</RDLSandboxing>  
```  
  
## <a name="configuration-settings"></a><span data-ttu-id="3bd71-120">組態設定</span><span class="sxs-lookup"><span data-stu-id="3bd71-120">Configuration Settings</span></span>  
 <span data-ttu-id="3bd71-121">下表提供有關組態設定的資訊。</span><span class="sxs-lookup"><span data-stu-id="3bd71-121">The following table provides information about configuration settings.</span></span> <span data-ttu-id="3bd71-122">設定會依其出現在組態檔的順序顯示。</span><span class="sxs-lookup"><span data-stu-id="3bd71-122">Settings are presented in the order in which they appear in the configuration file.</span></span>  
  
|<span data-ttu-id="3bd71-123">設定</span><span class="sxs-lookup"><span data-stu-id="3bd71-123">Setting</span></span>|<span data-ttu-id="3bd71-124">描述</span><span class="sxs-lookup"><span data-stu-id="3bd71-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3bd71-125">**MaxExpressionLength**</span><span class="sxs-lookup"><span data-stu-id="3bd71-125">**MaxExpressionLength**</span></span>|<span data-ttu-id="3bd71-126">RDL 運算式中允許的最大字元數。</span><span class="sxs-lookup"><span data-stu-id="3bd71-126">Maximum number of characters allowed in RDL expressions.</span></span><br /><br /> <span data-ttu-id="3bd71-127">預設值：1000</span><span class="sxs-lookup"><span data-stu-id="3bd71-127">Default: 1000</span></span>|  
|<span data-ttu-id="3bd71-128">**MaxResourceSize**</span><span class="sxs-lookup"><span data-stu-id="3bd71-128">**MaxResourceSize**</span></span>|<span data-ttu-id="3bd71-129">外部資源允許的最大 KB 數。</span><span class="sxs-lookup"><span data-stu-id="3bd71-129">Maximum number of KB allowed for an external resource.</span></span><br /><br /> <span data-ttu-id="3bd71-130">預設值：100</span><span class="sxs-lookup"><span data-stu-id="3bd71-130">Default: 100</span></span>|  
|<span data-ttu-id="3bd71-131">**MaxStringResultLength**</span><span class="sxs-lookup"><span data-stu-id="3bd71-131">**MaxStringResultLength**</span></span>|<span data-ttu-id="3bd71-132">RDL 運算式的傳回值中允許的最大字元數。</span><span class="sxs-lookup"><span data-stu-id="3bd71-132">Maximum number of characters allowed in a return value for an RDL expression.</span></span><br /><br /> <span data-ttu-id="3bd71-133">預設值：1000</span><span class="sxs-lookup"><span data-stu-id="3bd71-133">Default: 1000</span></span>|  
|<span data-ttu-id="3bd71-134">**MaxArrayResultLength**</span><span class="sxs-lookup"><span data-stu-id="3bd71-134">**MaxArrayResultLength**</span></span>|<span data-ttu-id="3bd71-135">RDL 運算式的陣列傳回值中允許的最大項目數。</span><span class="sxs-lookup"><span data-stu-id="3bd71-135">Maximum number of items allowed in an array return value for an RDL expression.</span></span><br /><br /> <span data-ttu-id="3bd71-136">預設值：100</span><span class="sxs-lookup"><span data-stu-id="3bd71-136">Default: 100</span></span>|  
|<span data-ttu-id="3bd71-137">**類型**</span><span class="sxs-lookup"><span data-stu-id="3bd71-137">**Types**</span></span>|<span data-ttu-id="3bd71-138">RDL 運算式中允許的成員清單。</span><span class="sxs-lookup"><span data-stu-id="3bd71-138">The list of members to allow within RDL expressions.</span></span>|  
|<span data-ttu-id="3bd71-139">**允許**</span><span class="sxs-lookup"><span data-stu-id="3bd71-139">**Allow**</span></span>|<span data-ttu-id="3bd71-140">RDL 運算式中允許的類型或類型集合。</span><span class="sxs-lookup"><span data-stu-id="3bd71-140">A type or set of types to allow in RDL expressions.</span></span>|  
|<span data-ttu-id="3bd71-141">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="3bd71-141">**Namespace**</span></span>|<span data-ttu-id="3bd71-142">**Allow** 的屬性，這是包含一或多個套用至 Value 之類型的命名空間。</span><span class="sxs-lookup"><span data-stu-id="3bd71-142">Attribute for **Allow** that is the namespace that contains one or more types that apply to Value.</span></span> <span data-ttu-id="3bd71-143">這個屬性不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3bd71-143">This property is case-insensitive.</span></span>|  
|`AllowNew`|<span data-ttu-id="3bd71-144">**允許**的布林值屬性，控制是否允許在 rdl 運算式或 rdl 元素中建立類型的新實例 **\<Class>** 。</span><span class="sxs-lookup"><span data-stu-id="3bd71-144">Boolean attribute for **Allow** that controls whether new instances of the type are allowed to be created in RDL expressions or in an RDL **\<Class>** element.</span></span><br /><br /> <span data-ttu-id="3bd71-145">注意：啟用時，不論的設定為何，都 `RDLSandboxing` 無法在 RDL 運算式中建立新的陣列 `AllowNew` 。</span><span class="sxs-lookup"><span data-stu-id="3bd71-145">Note: When `RDLSandboxing` is enabled, new arrays cannot be created in RDL expressions, regardless of the setting of `AllowNew`.</span></span>|  
|<span data-ttu-id="3bd71-146">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="3bd71-146">**Value**</span></span>|<span data-ttu-id="3bd71-147">**Allow** 的值，這是 RDL 運算式中允許之類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="3bd71-147">Value for **Allow** that is the name of the type to allow in RDL expressions.</span></span> <span data-ttu-id="3bd71-148">值 **\*** 表示允許命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="3bd71-148">The value **\*** indicates that all types in the namespace are allowed.</span></span> <span data-ttu-id="3bd71-149">這個屬性不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3bd71-149">This property is case-insensitive.</span></span>|  
|<span data-ttu-id="3bd71-150">**成員**</span><span class="sxs-lookup"><span data-stu-id="3bd71-150">**Members**</span></span>|<span data-ttu-id="3bd71-151">如需包含在元素中的類型清單 **\<Types>** ，則為 RDL 運算式中不允許的成員名稱清單。</span><span class="sxs-lookup"><span data-stu-id="3bd71-151">For the list of types that are include in the **\<Types>** element, the list of member names that are not allowed in RDL expressions.</span></span>|  
|<span data-ttu-id="3bd71-152">**Deny**</span><span class="sxs-lookup"><span data-stu-id="3bd71-152">**Deny**</span></span>|<span data-ttu-id="3bd71-153">RDL 運算式中不允許的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="3bd71-153">The name of a member that is not allowed in RDL expressions.</span></span> <span data-ttu-id="3bd71-154">這個屬性不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3bd71-154">This property is case-insensitive.</span></span><br /><br /> <span data-ttu-id="3bd71-155">注意：為成員指定**Deny**時，不允許所有類型的所有成員使用此名稱。</span><span class="sxs-lookup"><span data-stu-id="3bd71-155">Note: When **Deny** is specified for a member, all members with this name for all types are not allowed.</span></span>|  
  
## <a name="working-with-expressions-when-rdl-sandboxing-is-enabled"></a><span data-ttu-id="3bd71-156">在啟用 RDL 沙箱功能時使用運算式</span><span class="sxs-lookup"><span data-stu-id="3bd71-156">Working with Expressions when RDL Sandboxing is Enabled</span></span>  
 <span data-ttu-id="3bd71-157">您可以修改 RDL 沙箱功能，透過下列方式幫助管理運算式所使用的資源：</span><span class="sxs-lookup"><span data-stu-id="3bd71-157">You can modify the RDL Sandboxing feature to help manage the resources that are used by an expression in the following ways:</span></span>  
  
-   <span data-ttu-id="3bd71-158">限制用於運算式的字元數。</span><span class="sxs-lookup"><span data-stu-id="3bd71-158">Restrict the number of characters that are used for an expression.</span></span>  
  
-   <span data-ttu-id="3bd71-159">限制運算式傳回之結果的大小。</span><span class="sxs-lookup"><span data-stu-id="3bd71-159">Restrict the size of the result returned by an expression.</span></span>  
  
-   <span data-ttu-id="3bd71-160">允許可用於運算式的特定類型清單。</span><span class="sxs-lookup"><span data-stu-id="3bd71-160">Allow a specific list of types that can be used in an expression.</span></span>  
  
-   <span data-ttu-id="3bd71-161">針對可用於運算式的允許類型清單，依名稱限制成員的清單。</span><span class="sxs-lookup"><span data-stu-id="3bd71-161">Restrict the list of members by name for the list of allowed types that can be used in an expression.</span></span>  
  
-   <span data-ttu-id="3bd71-162">RDL 沙箱功能可讓您建立核准的類型清單以及遭到拒絕的成員清單。</span><span class="sxs-lookup"><span data-stu-id="3bd71-162">The RDL Sandboxing feature enables you to create a list of approved types and a list of denied members.</span></span> <span data-ttu-id="3bd71-163">核准的類型清單稱為允許清單，</span><span class="sxs-lookup"><span data-stu-id="3bd71-163">The list of approved types is called an allow list.</span></span> <span data-ttu-id="3bd71-164">遭到拒絕的成員清單則稱為封鎖清單。</span><span class="sxs-lookup"><span data-stu-id="3bd71-164">The list of denied members is called a block list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3bd71-165">在報告定義中，電腦無法得知運算式參考的每個執行個體的類型。</span><span class="sxs-lookup"><span data-stu-id="3bd71-165">In the report definition, a computer cannot know the type of each instances of an expression reference.</span></span> <span data-ttu-id="3bd71-166">當您將成員加入至封鎖清單時，您會在允許清單的所有類型中拒絕該名稱的所有成員。</span><span class="sxs-lookup"><span data-stu-id="3bd71-166">When you add a member to the block list, you are denying all members of that name across all types in the allow list.</span></span>  
  
 <span data-ttu-id="3bd71-167">RDL 運算式的結果會在執行階段驗證。</span><span class="sxs-lookup"><span data-stu-id="3bd71-167">RDL expression results are verified at run time.</span></span> <span data-ttu-id="3bd71-168">當發行報表時，便會在報表定義中驗證 RDL 運算式。</span><span class="sxs-lookup"><span data-stu-id="3bd71-168">RDL expressions are verified in the report definition when the report is published.</span></span> <span data-ttu-id="3bd71-169">監視報表伺服器追蹤記錄，查看是否有違規情形。</span><span class="sxs-lookup"><span data-stu-id="3bd71-169">Monitor the report server trace log for violations.</span></span> <span data-ttu-id="3bd71-170">如需詳細資訊，請參閱 [Report Server Service Trace Log](report-server/report-server-service-trace-log.md)。</span><span class="sxs-lookup"><span data-stu-id="3bd71-170">For more information, see [Report Server Service Trace Log](report-server/report-server-service-trace-log.md).</span></span>  
  
### <a name="working-with-types"></a><span data-ttu-id="3bd71-171">處理類型</span><span class="sxs-lookup"><span data-stu-id="3bd71-171">Working with Types</span></span>  
 <span data-ttu-id="3bd71-172">當您將某個類型加入至允許清單時，您會控制存取 RDL 運算式的下列進入點：</span><span class="sxs-lookup"><span data-stu-id="3bd71-172">When you add a type to the allow list, you are controlling the following entry points to access RDL expressions:</span></span>  
  
-   <span data-ttu-id="3bd71-173">某個類型的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="3bd71-173">Static members of a type.</span></span>  
  
-   <span data-ttu-id="3bd71-174">[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `New` 方法。</span><span class="sxs-lookup"><span data-stu-id="3bd71-174">The [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `New` method.</span></span>  
  
-   <span data-ttu-id="3bd71-175">**\<Classes>** 報表定義中的元素。</span><span class="sxs-lookup"><span data-stu-id="3bd71-175">The **\<Classes>** element in the report definition.</span></span>  
  
-   <span data-ttu-id="3bd71-176">您已經針對允許清單內的某個類型加入至封鎖清單中的成員。</span><span class="sxs-lookup"><span data-stu-id="3bd71-176">Members that you have added to the block list for a type in the allow list.</span></span>  
  
 <span data-ttu-id="3bd71-177">允許清單不能控制下列進入點：</span><span class="sxs-lookup"><span data-stu-id="3bd71-177">The allow list does not control the following entry points:</span></span>  
  
-   <span data-ttu-id="3bd71-178">報表資料集。</span><span class="sxs-lookup"><span data-stu-id="3bd71-178">Report datasets.</span></span> <span data-ttu-id="3bd71-179">報表資料集中從查詢傳回的欄位可能會包含任何有效的 RDL 類型。</span><span class="sxs-lookup"><span data-stu-id="3bd71-179">Fields in report datasets that are returned from queries might contain any valid RDL type.</span></span>  
  
-   <span data-ttu-id="3bd71-180">報表參數。</span><span class="sxs-lookup"><span data-stu-id="3bd71-180">Report parameters.</span></span> <span data-ttu-id="3bd71-181">使用者提供的參數值可能會包含任何有效的 RDL 類型。</span><span class="sxs-lookup"><span data-stu-id="3bd71-181">User-supplied parameter values might contain any valid RDL type.</span></span>  
  
-   <span data-ttu-id="3bd71-182">具備已啟用的類型而不在封鎖清單內的成員。</span><span class="sxs-lookup"><span data-stu-id="3bd71-182">Members of an enabled type that are not in the block list.</span></span> <span data-ttu-id="3bd71-183">根據預設，將會啟用允許清單中所有類型的所有成員。</span><span class="sxs-lookup"><span data-stu-id="3bd71-183">By default, all members of all types in the allow list are enabled.</span></span> <span data-ttu-id="3bd71-184">當您將成員名稱加入至封鎖清單時，您會在允許清單的所有類型中拒絕該名稱的所有成員。</span><span class="sxs-lookup"><span data-stu-id="3bd71-184">When you add a member name to the block list, you are denying all members with that name across all types that are in the allow list.</span></span>  
  
 <span data-ttu-id="3bd71-185">若要啟用一個類型的成員，但是拒絕另一個類型的同名成員，您必須執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="3bd71-185">To enable a member of one type but deny a member with the same name for a different type, you must do the following:</span></span>  
  
-   <span data-ttu-id="3bd71-186">新增 **\<Deny>** 成員名稱的元素。</span><span class="sxs-lookup"><span data-stu-id="3bd71-186">Add a **\<Deny>** element for the member name.</span></span>  
  
-   <span data-ttu-id="3bd71-187">針對您想要啟用的成員，在自訂組件的某個類別上建立另一個名稱的 Proxy 成員。</span><span class="sxs-lookup"><span data-stu-id="3bd71-187">Create a proxy member with a different name on a class in a custom assembly for the member that you want to enable.</span></span>  
  
-   <span data-ttu-id="3bd71-188">將這個新類別加入至允許清單。</span><span class="sxs-lookup"><span data-stu-id="3bd71-188">Add that new class to the allow list.</span></span>  
  
 <span data-ttu-id="3bd71-189">若要將 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 函數加入允許清單，請將 Microsoft.VisualBasic 命名空間中的對應類型加入允許清單。</span><span class="sxs-lookup"><span data-stu-id="3bd71-189">To add [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework functions to the allow list, add the corresponding types from the Microsoft.VisualBasic namespace to the allow list.</span></span>  
  
 <span data-ttu-id="3bd71-190">若要將 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 類型關鍵字加入至允許清單，請將對應的 CLR 類型加入至允許清單。</span><span class="sxs-lookup"><span data-stu-id="3bd71-190">To add [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework type keywords to the allow list, add the corresponding CLR type to the allow list.</span></span> <span data-ttu-id="3bd71-191">例如，若要使用 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 關鍵字 `Integer` ，請將下列 XML 片段加入至 **\<RDLSandboxing>** 元素：</span><span class="sxs-lookup"><span data-stu-id="3bd71-191">For example, to use the [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework keyword `Integer`, add the following XML fragment to the **\<RDLSandboxing>** element:</span></span>  
  
```  
<Allow Namespace="System">Int32</Allow>  
```  
  
 <span data-ttu-id="3bd71-192">若要將一般或 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 可為 Null 的類型加入至允許清單，您必須執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="3bd71-192">To add a generic or a [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework nullable type to the allow list, you must do the following:</span></span>  
  
-   <span data-ttu-id="3bd71-193">針對一般或 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 可為 Null 的類型建立 Proxy 類型。</span><span class="sxs-lookup"><span data-stu-id="3bd71-193">Create a proxy type for the generic or [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework nullable type.</span></span>  
  
-   <span data-ttu-id="3bd71-194">將 Proxy 類型加入至允許清單。</span><span class="sxs-lookup"><span data-stu-id="3bd71-194">Add the proxy type to the allow list.</span></span>  
  
 <span data-ttu-id="3bd71-195">將自訂組件中的類型加入至允許清單並不會以隱含方式授與此組件的執行權限。</span><span class="sxs-lookup"><span data-stu-id="3bd71-195">Adding a type from a custom assembly to the allow list does not implicitly grant execute permission on the assembly.</span></span> <span data-ttu-id="3bd71-196">您必須特別修改程式碼存取安全性檔案，並提供組件的執行權限。</span><span class="sxs-lookup"><span data-stu-id="3bd71-196">You must specifically modify the code access security file and provide execute permission to your assembly.</span></span> <span data-ttu-id="3bd71-197">如需詳細資訊，請參閱 [Code Access Security in Reporting Services](extensions/secure-development/code-access-security-in-reporting-services.md)(Reporting Services 中的程式碼存取安全性)。</span><span class="sxs-lookup"><span data-stu-id="3bd71-197">For more information, see [Code Access Security in Reporting Services](extensions/secure-development/code-access-security-in-reporting-services.md).</span></span>  
  
#### <a name="maintaining-the-deny-list-of-members"></a><span data-ttu-id="3bd71-198">維護 \<Deny> 成員清單</span><span class="sxs-lookup"><span data-stu-id="3bd71-198">Maintaining the \<Deny> List of Members</span></span>  
 <span data-ttu-id="3bd71-199">當您將新的類型加入至允許清單時，請使用下列清單來判斷何時可能需要更新成員的封鎖清單：</span><span class="sxs-lookup"><span data-stu-id="3bd71-199">When you add a new type to the allow list, use the following list to determine when you might have to update the block list of members:</span></span>  
  
-   <span data-ttu-id="3bd71-200">當您使用導入新類型的版本來更新自訂組件時。</span><span class="sxs-lookup"><span data-stu-id="3bd71-200">When you update a custom assembly with a version that introduces new types.</span></span>  
  
-   <span data-ttu-id="3bd71-201">當您將成員加入至允許清單中的類型時。</span><span class="sxs-lookup"><span data-stu-id="3bd71-201">When you add members to the types in the allow list.</span></span>  
  
-   <span data-ttu-id="3bd71-202">當您在報表伺服器上更新 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 時。</span><span class="sxs-lookup"><span data-stu-id="3bd71-202">When you update the [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] on the report server.</span></span>  
  
-   <span data-ttu-id="3bd71-203">當您將報表伺服器升級到更新版本的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]時。</span><span class="sxs-lookup"><span data-stu-id="3bd71-203">When you upgrade the report server to a later version of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="3bd71-204">當您因為新的成員可能已加入至 RDL 類型，而更新報表伺服器來處理較新的 RDL 結構描述時。</span><span class="sxs-lookup"><span data-stu-id="3bd71-204">When you update a report server to handle a later RDL schema, because new members might have been added to RDL types.</span></span>  
  
### <a name="working-with-operators-and-new"></a><span data-ttu-id="3bd71-205">使用運算子及 New</span><span class="sxs-lookup"><span data-stu-id="3bd71-205">Working with Operators and New</span></span>  
 <span data-ttu-id="3bd71-206">根據預設，一定會允許 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 語言運算子，但是 `New` 除外。</span><span class="sxs-lookup"><span data-stu-id="3bd71-206">By default, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework language operators, except for `New`, are always allowed.</span></span> <span data-ttu-id="3bd71-207">`New`運算子是由 `AllowNew` 元素上的屬性所控制 **\<Allow>** 。</span><span class="sxs-lookup"><span data-stu-id="3bd71-207">The `New` operator is controlled by the `AllowNew` attribute on the **\<Allow>** element.</span></span> <span data-ttu-id="3bd71-208">系統一律允許其他語言運算子，例如預設集合存取子運算子 `!` 和 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 轉換宏（例如 `CInt` ）。</span><span class="sxs-lookup"><span data-stu-id="3bd71-208">Other language operators, such as the default collection accessor operator `!` and [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework cast macros such as `CInt`, are always allowed.</span></span>  
  
 <span data-ttu-id="3bd71-209">不支援將運算子加入至封鎖清單中，包括自訂運算子。</span><span class="sxs-lookup"><span data-stu-id="3bd71-209">Adding operators to a block list, including custom operators, is not supported.</span></span> <span data-ttu-id="3bd71-210">若要排除某個類型的運算子，您必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3bd71-210">To exclude operators for a type, you must do the following:</span></span>  
  
-   <span data-ttu-id="3bd71-211">建立 Proxy 類型，此類型不會實作您想要排除的運算子。</span><span class="sxs-lookup"><span data-stu-id="3bd71-211">Create a proxy type that does not implement the operators that you want to exclude.</span></span>  
  
-   <span data-ttu-id="3bd71-212">將 Proxy 類型加入至允許清單。</span><span class="sxs-lookup"><span data-stu-id="3bd71-212">Add the proxy type to the allow list.</span></span>  
  
 <span data-ttu-id="3bd71-213">若要在 RDL 運算式中建立新的陣列，請在您定義之類別上的方法中建立此陣列，並將該類別加入至允許清單。</span><span class="sxs-lookup"><span data-stu-id="3bd71-213">To create a new array in an RDL expression, create the array in a method on a class that you define, and add that class to the allow list.</span></span>  
  
 <span data-ttu-id="3bd71-214">若要在 RDL 運算式中建立新的陣列，您必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3bd71-214">To create a new array in an RDL expression, you must do the following:</span></span>  
  
-   <span data-ttu-id="3bd71-215">定義新的類別，並在該類別上的方法中建立此陣列。</span><span class="sxs-lookup"><span data-stu-id="3bd71-215">Define a new class and create the array in a method on that class.</span></span>  
  
-   <span data-ttu-id="3bd71-216">將此類別加入至允許清單。</span><span class="sxs-lookup"><span data-stu-id="3bd71-216">Add the class to the allow list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bd71-217">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bd71-217">See Also</span></span>  
 <span data-ttu-id="3bd71-218">[Rsreportserver.config 設定檔](report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="3bd71-218">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) </span></span>  
 [<span data-ttu-id="3bd71-219">報表伺服器服務追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="3bd71-219">Report Server Service Trace Log</span></span>](report-server/report-server-service-trace-log.md)  
  
  
