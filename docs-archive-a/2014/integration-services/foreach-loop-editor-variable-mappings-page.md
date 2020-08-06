---
title: Foreach 迴圈編輯器 (變數對應頁面) |Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.mapping.f1
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd37c8c6c00f18d8b5493a058239cc880ecc1f5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710738"
---
# <a name="foreach-loop-editor-variable-mappings-page"></a><span data-ttu-id="6ad8c-102">Foreach 迴圈編輯器 (變數對應頁面)</span><span class="sxs-lookup"><span data-stu-id="6ad8c-102">Foreach Loop Editor (Variable Mappings Page)</span></span>
  <span data-ttu-id="6ad8c-103">使用 [Foreach 迴圈編輯器]  對話方塊的 [變數對應]  頁面，即可將變數對應至集合值。</span><span class="sxs-lookup"><span data-stu-id="6ad8c-103">Use the **Variables Mappings** page of the **Foreach Loop Editor** dialog box to map variables to the collection value.</span></span> <span data-ttu-id="6ad8c-104">會用迴圈之每個反覆運算上的集合值來更新變數的值。</span><span class="sxs-lookup"><span data-stu-id="6ad8c-104">The value of the variable is updated with the collection values on each iteration of the loop.</span></span>  
  
 <span data-ttu-id="6ad8c-105">若要了解如何在 Integration Services 封裝中使用「Foreach 迴圈」容器，請參閱 [Foreach 迴圈容器](control-flow/foreach-loop-container.md) 。</span><span class="sxs-lookup"><span data-stu-id="6ad8c-105">To learn about how to use the Foreach Loop container in an Integration Services package,  see [Foreach Loop Container](control-flow/foreach-loop-container.md) .</span></span> <span data-ttu-id="6ad8c-106">若要了解如何設定此容器，請參閱 [設定 Foreach 迴圈容器](../../2014/integration-services/configure-a-foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="6ad8c-106">To learn about how to configure it, see [Configure a Foreach Loop Container](../../2014/integration-services/configure-a-foreach-loop-container.md).</span></span>  
  
 <span data-ttu-id="6ad8c-107">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 教學課程中的＜建立簡易 ETL 套件教學課程＞包含一門如何新增和設定 Foreach 迴圈的課程。</span><span class="sxs-lookup"><span data-stu-id="6ad8c-107">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tutorial, Creating a Simple ETL Package Tutorial, includes a lesson that teaches you to add and configure a Foreach Loop.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6ad8c-108">選項。</span><span class="sxs-lookup"><span data-stu-id="6ad8c-108">Options</span></span>  
 <span data-ttu-id="6ad8c-109">**變數**</span><span class="sxs-lookup"><span data-stu-id="6ad8c-109">**Variable**</span></span>  
 <span data-ttu-id="6ad8c-110">選取現有的變數，或按一下 \<**New variable...**> 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="6ad8c-110">Select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6ad8c-111">對應變數之後，新資料列會自動加入 [變數]  清單。</span><span class="sxs-lookup"><span data-stu-id="6ad8c-111">After you map a variable, a new row is automatically added to the **Variable** list.</span></span>  
  
 <span data-ttu-id="6ad8c-112">**相關主題**：[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="6ad8c-112">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="6ad8c-113">**Index**</span><span class="sxs-lookup"><span data-stu-id="6ad8c-113">**Index**</span></span>  
 <span data-ttu-id="6ad8c-114">如果使用 Foreach 項目列舉值，請指定集合值中要對應至變數的資料行索引。</span><span class="sxs-lookup"><span data-stu-id="6ad8c-114">If using the Foreach Item enumerator, specify the index of the column in the collection value to map to the variable.</span></span> <span data-ttu-id="6ad8c-115">針對其他列舉值類型，此索引是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="6ad8c-115">For other enumerator types, the index is read-only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6ad8c-116">索引是以 0 為基底。</span><span class="sxs-lookup"><span data-stu-id="6ad8c-116">The index is 0-based.</span></span>  
  
 <span data-ttu-id="6ad8c-117">**相關主題**： [使用 Foreach 迴圈容器來循環使用 Excel 檔案和資料表](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)</span><span class="sxs-lookup"><span data-stu-id="6ad8c-117">**Related Topics**: [Loop through Excel Files and Tables by Using a Foreach Loop Container](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)</span></span>  
  
 <span data-ttu-id="6ad8c-118">**刪除**</span><span class="sxs-lookup"><span data-stu-id="6ad8c-118">**Delete**</span></span>  
 <span data-ttu-id="6ad8c-119">選取變數，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="6ad8c-119">Select a variable, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad8c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ad8c-120">See Also</span></span>  
 <span data-ttu-id="6ad8c-121">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="6ad8c-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="6ad8c-122">[[Foreach 迴圈編輯器] &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="6ad8c-122">[Foreach Loop Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="6ad8c-123">[[Foreach 迴圈編輯器] &#40;集合] 頁面&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md) </span><span class="sxs-lookup"><span data-stu-id="6ad8c-123">[Foreach Loop Editor &#40;Collection Page&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md) </span></span>  
 <span data-ttu-id="6ad8c-124">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="6ad8c-124">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="6ad8c-125">For 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="6ad8c-125">For Loop Container</span></span>](control-flow/for-loop-container.md)  
  
  
