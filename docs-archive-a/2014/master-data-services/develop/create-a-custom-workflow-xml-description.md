---
title: 自訂工作流程 XML 描述 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: e267e5f4-38bb-466d-82e8-871eabeec07e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 77906426ddb901ec422367bf30aabef2e532ad06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607427"
---
# <a name="custom-workflow-xml-description-master-data-services"></a><span data-ttu-id="6dc85-102">自訂工作流程 XML 描述 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="6dc85-102">Custom Workflow XML Description (Master Data Services)</span></span>
  <span data-ttu-id="6dc85-103">在中 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] ，當工作流程啟動時，SQL SERVER MDS 工作流程整合服務會呼叫[MasterDataServices. WorkflowTypeExtender. IWorkflowTypeExtender. StartWorkflow \*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130))方法。</span><span class="sxs-lookup"><span data-stu-id="6dc85-103">In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], the [Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow\*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) method is called by SQL Server MDS Workflow Integration Service when a workflow starts.</span></span> <span data-ttu-id="6dc85-104">此方法會收到有關觸發工作流程商務規則之項目的中繼資料和資料，做為 XML 的區塊。</span><span class="sxs-lookup"><span data-stu-id="6dc85-104">This method receives metadata and data about the item that triggered the workflow business rule as a block of XML.</span></span> <span data-ttu-id="6dc85-105">如需實作工作流程處理常式的範例程式碼，請參閱[自訂工作流程範例 &#40;Master Data Services&#41;](create-a-custom-workflow-example.md)。</span><span class="sxs-lookup"><span data-stu-id="6dc85-105">For example code that implements a workflow handler, see [Custom Workflow Example &#40;Master Data Services&#41;](create-a-custom-workflow-example.md).</span></span>  
  
 <span data-ttu-id="6dc85-106">以下範例顯示傳送至工作流程處理常式之 XML 的可能外觀：</span><span class="sxs-lookup"><span data-stu-id="6dc85-106">The following example shows what the XML that is sent to the workflow handler might look like:</span></span>  
  
```scr  
<ExternalAction>  
  <Type>TEST</Type>  
  <SendData>1</SendData>  
  <Server_URL>This is my test!</Server_URL>  
  <Action_ID>Test Workflow</Action_ID>  
  <Model_ID>5</Model_ID>  
  <Model_Name>Customer</Model_Name>  
  <Entity_ID>34</Entity_ID>  
  <Entity_Name>Customer</Entity_Name>  
  <Version_ID>8</Version_ID>  
  <MemberType_ID>1</MemberType_ID>  
  <Member_ID>12</Member_ID>  
  <MemberData>  
    <ID>12</ID>  
    <Version_ID>8</Version_ID>  
    <ValidationStatus_ID>3</ValidationStatus_ID>  
    <ChangeTrackingMask>0</ChangeTrackingMask>  
    <EnterDTM>2011-02-25T20:16:36.650</EnterDTM>  
    <EnterUserID>2</EnterUserID>  
    <EnterUserName>MyUserName</EnterUserName>  
    <EnterUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</EnterUserMuid>  
    <EnterVersionId>8</EnterVersionId>  
    <EnterVersionName>VERSION_1</EnterVersionName>  
    <EnterVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</EnterVersionMuid>  
    <LastChgDTM>2011-02-25T20:16:36.650</LastChgDTM>  
    <LastChgUserID>2</LastChgUserID>  
    <LastChgUserName>MyUserName</LastChgUserName>  
    <LastChgUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</LastChgUserMuid>  
    <LastChgVersionId>8</LastChgVersionId>  
    <LastChgVersionName>VERSION_1</LastChgVersionName>  
    <LastChgVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</LastChgVersionMuid>  
    <Name>Test Customer</Name>  
    <Code>TC</Code>  
  </MemberData>  
</ExternalAction>  
```  
  
 <span data-ttu-id="6dc85-107">下表描述此 XML 中包含的某些標記：</span><span class="sxs-lookup"><span data-stu-id="6dc85-107">The following table describes some of the tags contained in this XML:</span></span>  
  
|<span data-ttu-id="6dc85-108">Tag</span><span class="sxs-lookup"><span data-stu-id="6dc85-108">Tag</span></span>|<span data-ttu-id="6dc85-109">描述</span><span class="sxs-lookup"><span data-stu-id="6dc85-109">Description</span></span>|  
|---------|-----------------|  
|\<Type>|<span data-ttu-id="6dc85-110">您在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 之 [工作流程類型]\*\*\*\* 文字方塊中輸入的文字，用以識別要載入的自訂工作流程組件。</span><span class="sxs-lookup"><span data-stu-id="6dc85-110">The text you entered in the **Workflow type** text box in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] to identify which custom workflow assembly to load.</span></span>|  
|\<SendData>|<span data-ttu-id="6dc85-111">在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 中，由 [訊息中包含成員資料]\*\*\*\* 核取方塊所控制的布林值。</span><span class="sxs-lookup"><span data-stu-id="6dc85-111">A Boolean value controlled by the **Include member data in the message** checkbox in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="6dc85-112">值為1表示 \<MemberData> 會傳送區段，否則 \<MemberData> 不會傳送區段。</span><span class="sxs-lookup"><span data-stu-id="6dc85-112">A value of 1 means that the \<MemberData> section is sent; otherwise the \<MemberData> section is not sent.</span></span>|  
|<span data-ttu-id="6dc85-113"><Server_URL></span><span class="sxs-lookup"><span data-stu-id="6dc85-113"><Server_URL></span></span>|<span data-ttu-id="6dc85-114">您在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 之 [工作流程網站]\*\*\*\* 文字方塊中輸入的文字。</span><span class="sxs-lookup"><span data-stu-id="6dc85-114">The text you entered in the **Workflow site** text box in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>|  
|<span data-ttu-id="6dc85-115"><Action_ID></span><span class="sxs-lookup"><span data-stu-id="6dc85-115"><Action_ID></span></span>|<span data-ttu-id="6dc85-116">您在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 之 [工作流程名稱]\*\*\*\* 文字方塊中輸入的文字。</span><span class="sxs-lookup"><span data-stu-id="6dc85-116">The text you entered in the **Workflow name** text box in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>|  
|\<MemberData>|<span data-ttu-id="6dc85-117">包含觸發工作流程動作之成員的資料。</span><span class="sxs-lookup"><span data-stu-id="6dc85-117">Contains the data of the member that triggered the workflow action.</span></span> <span data-ttu-id="6dc85-118">只有在的值為1時，才會包含此項 \<SendData> 。</span><span class="sxs-lookup"><span data-stu-id="6dc85-118">This is included only if the value of \<SendData> is 1.</span></span>|  
|\<Enter*xxx*>|<span data-ttu-id="6dc85-119">這組標記包含有關建立成員的中繼資料，例如建立成員的時間以及建立成員者。</span><span class="sxs-lookup"><span data-stu-id="6dc85-119">This set of tags contains metadata about the creation of the member, such as when it was created and who created it.</span></span>|  
|\<LastChg*xxx*>|<span data-ttu-id="6dc85-120">這組標記包含有關上次對成員所進行之變更的中繼資料，例如進行變更的時間以及進行變更者。</span><span class="sxs-lookup"><span data-stu-id="6dc85-120">This set of tags contains metadata about the last change made to the member, such as when the change was made and who made it.</span></span>|  
|\<Name>|<span data-ttu-id="6dc85-121">已變更之成員的第一個屬性。</span><span class="sxs-lookup"><span data-stu-id="6dc85-121">The first attribute of the member that was changed.</span></span> <span data-ttu-id="6dc85-122">此範例成員僅包含 Name 和 Code 屬性。</span><span class="sxs-lookup"><span data-stu-id="6dc85-122">This example member contains only Name and Code attributes.</span></span>|  
|\<Code>|<span data-ttu-id="6dc85-123">已變更之成員的下一個屬性。</span><span class="sxs-lookup"><span data-stu-id="6dc85-123">The next attribute of the member that was changed.</span></span> <span data-ttu-id="6dc85-124">如果此範例成員包含更多屬性，則會緊接著此屬性之後。</span><span class="sxs-lookup"><span data-stu-id="6dc85-124">If this example member contained more attributes, they would follow this one.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6dc85-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dc85-125">See Also</span></span>  
 <span data-ttu-id="6dc85-126">[建立自訂工作流程 &#40;Master Data Services&#41;](create-a-custom-workflow-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="6dc85-126">[Create a Custom Workflow &#40;Master Data Services&#41;](create-a-custom-workflow-master-data-services.md) </span></span>  
 [<span data-ttu-id="6dc85-127">自訂工作流程範例 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6dc85-127">Custom Workflow Example &#40;Master Data Services&#41;</span></span>](create-a-custom-workflow-example.md)  
  
  
