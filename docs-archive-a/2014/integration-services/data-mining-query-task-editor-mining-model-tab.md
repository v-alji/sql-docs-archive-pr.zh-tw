---
title: 資料採礦查詢工作編輯器 ([採礦模型] 索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dmquerytask.miningmodel.f1
helpviewer_keywords:
- Data Mining Query Task Editor
ms.assetid: 0ede9b86-be27-471e-b012-22a65adce579
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 794365c8d15ff9725fc385bb43d51e70ffa529b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703225"
---
# <a name="data-mining-query-task-editor-mining-model-tab"></a><span data-ttu-id="d95e6-102">資料採礦查詢工作編輯器 (採礦模型索引標籤)</span><span class="sxs-lookup"><span data-stu-id="d95e6-102">Data Mining Query Task Editor (Mining Model Tab)</span></span>
  <span data-ttu-id="d95e6-103">使用 **[資料採礦查詢工作]** 對話方塊的 **[採礦模型]** 索引標籤，即可指定要使用的採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="d95e6-103">Use the **Mining Model** tab of the **Data Mining Query Task** dialog box to specify the mining structure and mining model to use.</span></span>  
  
 <span data-ttu-id="d95e6-104">若要深入了解在封裝中實作資料採礦，請參閱 [Data Mining Query Task](control-flow/data-mining-query-task.md) (資料採礦查詢工作) 和 [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions)(資料採礦方案)。</span><span class="sxs-lookup"><span data-stu-id="d95e6-104">To learn about implementing data mining in packages, see [Data Mining Query Task](control-flow/data-mining-query-task.md) and [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions).</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="d95e6-105">一般選項</span><span class="sxs-lookup"><span data-stu-id="d95e6-105">General Options</span></span>  
 <span data-ttu-id="d95e6-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d95e6-106">**Name**</span></span>  
 <span data-ttu-id="d95e6-107">為資料採礦查詢工作提供唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="d95e6-107">Provide a unique name for the Data Mining Query task.</span></span> <span data-ttu-id="d95e6-108">這個名稱是作為工作圖示中的標籤使用。</span><span class="sxs-lookup"><span data-stu-id="d95e6-108">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d95e6-109">工作名稱在封裝內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="d95e6-109">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="d95e6-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="d95e6-110">**Description**</span></span>  
 <span data-ttu-id="d95e6-111">輸入資料採礦查詢工作的描述。</span><span class="sxs-lookup"><span data-stu-id="d95e6-111">Type a description of the Data Mining Query task.</span></span>  
  
## <a name="mining-model-tab-options"></a><span data-ttu-id="d95e6-112">採礦模型索引標籤選項</span><span class="sxs-lookup"><span data-stu-id="d95e6-112">Mining Model Tab Options</span></span>  
 <span data-ttu-id="d95e6-113">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="d95e6-113">**Connection**</span></span>  
 <span data-ttu-id="d95e6-114">在清單中選取 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 連線管理員，或按一下 [新增]\*\*\*\* 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="d95e6-114">Select an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] connection manager in the list or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d95e6-115">**相關主題：**  [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md) (Analysis Services 連線管理員)</span><span class="sxs-lookup"><span data-stu-id="d95e6-115">**Related Topics:**  [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md)</span></span>  
  
 <span data-ttu-id="d95e6-116">**新增**</span><span class="sxs-lookup"><span data-stu-id="d95e6-116">**New**</span></span>  
 <span data-ttu-id="d95e6-117">建立新的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="d95e6-117">Create a new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] connection manager.</span></span>  
  
 <span data-ttu-id="d95e6-118">**相關主題：** [加入 Analysis Services 連線管理員對話方塊 UI 參考](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)</span><span class="sxs-lookup"><span data-stu-id="d95e6-118">**Related Topics:** [Add Analysis Services Connection Manager Dialog Box UI Reference](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)</span></span>  
  
 <span data-ttu-id="d95e6-119">**採礦結構**</span><span class="sxs-lookup"><span data-stu-id="d95e6-119">**Mining structure**</span></span>  
 <span data-ttu-id="d95e6-120">從清單中選取採礦結構。</span><span class="sxs-lookup"><span data-stu-id="d95e6-120">Select a mining structure in the list.</span></span>  
  
 <span data-ttu-id="d95e6-121">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="d95e6-121">**Mining models**</span></span>  
 <span data-ttu-id="d95e6-122">選取在所選取採礦結構上建立的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="d95e6-122">Select a mining model built on the selected mining structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d95e6-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d95e6-123">See Also</span></span>  
 <span data-ttu-id="d95e6-124">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d95e6-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="d95e6-125">[[資料採礦查詢工作編輯器] &#40;查詢] 索引標籤&#41;](../../2014/integration-services/data-mining-query-task-editor-query-tab.md) </span><span class="sxs-lookup"><span data-stu-id="d95e6-125">[Data Mining Query Task Editor &#40;Query Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-query-tab.md) </span></span>  
 <span data-ttu-id="d95e6-126">[資料採礦查詢工作編輯器 &#40;輸出] 索引標籤&#41;](../../2014/integration-services/data-mining-query-task-editor-output-tab.md) </span><span class="sxs-lookup"><span data-stu-id="d95e6-126">[Data Mining Query Task Editor &#40;Output Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-output-tab.md) </span></span>  
 [<span data-ttu-id="d95e6-127">資料採礦設計師</span><span class="sxs-lookup"><span data-stu-id="d95e6-127">Data Mining Designer</span></span>](https://docs.microsoft.com/analysis-services/data-mining/data-mining-designer)  
  
  
