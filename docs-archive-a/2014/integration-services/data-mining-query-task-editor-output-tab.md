---
title: 資料採礦查詢工作編輯器 (輸出] 索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dmquerytask.output.f1
helpviewer_keywords:
- Data Mining Query Task Editor
ms.assetid: 62f9e015-6fe0-4396-ad90-3ad51bf00025
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1508972b0487daa90f52af723d58185944a19a58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706593"
---
# <a name="data-mining-query-task-editor-output-tab"></a><span data-ttu-id="7961a-102">資料採礦查詢工作編輯器 (輸出索引標籤)</span><span class="sxs-lookup"><span data-stu-id="7961a-102">Data Mining Query Task Editor (Output Tab)</span></span>
  <span data-ttu-id="7961a-103">使用 **[資料採礦查詢工作編輯器]** 對話方塊的 **[輸出]** 索引標籤，即可指定預測查詢的目的地。</span><span class="sxs-lookup"><span data-stu-id="7961a-103">Use the **Output** tab of the **Data Mining Query Task Editor** dialog box to specify the destination of the prediction query.</span></span>  
  
 <span data-ttu-id="7961a-104">若要深入了解在封裝中實作資料採礦，請參閱 [Data Mining Query Task](control-flow/data-mining-query-task.md) (資料採礦查詢工作) 和 [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions)(資料採礦方案)。</span><span class="sxs-lookup"><span data-stu-id="7961a-104">To learn about implementing data mining in packages, see [Data Mining Query Task](control-flow/data-mining-query-task.md) and [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions).</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="7961a-105">一般選項</span><span class="sxs-lookup"><span data-stu-id="7961a-105">General Options</span></span>  
 <span data-ttu-id="7961a-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="7961a-106">**Name**</span></span>  
 <span data-ttu-id="7961a-107">為資料採礦查詢工作提供唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="7961a-107">Provide a unique name for the Data Mining Query task.</span></span> <span data-ttu-id="7961a-108">這個名稱是作為工作圖示中的標籤使用。</span><span class="sxs-lookup"><span data-stu-id="7961a-108">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7961a-109">工作名稱在封裝內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="7961a-109">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="7961a-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="7961a-110">**Description**</span></span>  
 <span data-ttu-id="7961a-111">輸入資料採礦查詢工作的描述。</span><span class="sxs-lookup"><span data-stu-id="7961a-111">Type a description of the Data Mining Query task.</span></span>  
  
## <a name="output-tab-options"></a><span data-ttu-id="7961a-112">輸出索引標籤選項</span><span class="sxs-lookup"><span data-stu-id="7961a-112">Output Tab Options</span></span>  
 <span data-ttu-id="7961a-113">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="7961a-113">**Connection**</span></span>  
 <span data-ttu-id="7961a-114">在清單中選取連線管理員，或按一下 [新增]\*\*\*\* 來建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="7961a-114">Select a connection manager in the list or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="7961a-115">**新增**</span><span class="sxs-lookup"><span data-stu-id="7961a-115">**New**</span></span>  
 <span data-ttu-id="7961a-116">建立新的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="7961a-116">Create a new connection manager.</span></span> <span data-ttu-id="7961a-117">只能使用 ADO.NET 和 OLE DB 連接管理員類型。</span><span class="sxs-lookup"><span data-stu-id="7961a-117">Only the ADO.NET and OLE DB connection manager types can be used.</span></span>  
  
 <span data-ttu-id="7961a-118">**輸出資料表**</span><span class="sxs-lookup"><span data-stu-id="7961a-118">**Output table**</span></span>  
 <span data-ttu-id="7961a-119">指定供預測查詢撰寫其結果的資料表。</span><span class="sxs-lookup"><span data-stu-id="7961a-119">Specify the table to which the prediction query writes its results.</span></span>  
  
 <span data-ttu-id="7961a-120">**卸除並重新建立輸出資料表**</span><span class="sxs-lookup"><span data-stu-id="7961a-120">**Drop and re-create the output table**</span></span>  
 <span data-ttu-id="7961a-121">指出預測查詢是否應藉由卸除然後重新建立資料表，來覆寫目的地資料表的內容。</span><span class="sxs-lookup"><span data-stu-id="7961a-121">Indicate whether the prediction query should overwrite content in the destination table by dropping and then re-creating the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7961a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7961a-122">See Also</span></span>  
 <span data-ttu-id="7961a-123">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="7961a-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="7961a-124">[資料採礦查詢工作編輯器 &#40;[模型] 索引標籤&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span><span class="sxs-lookup"><span data-stu-id="7961a-124">[Data Mining Query Task Editor &#40;Mining Model Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span></span>  
 <span data-ttu-id="7961a-125">[[資料採礦查詢工作編輯器] &#40;查詢] 索引標籤&#41;](../../2014/integration-services/data-mining-query-task-editor-query-tab.md) </span><span class="sxs-lookup"><span data-stu-id="7961a-125">[Data Mining Query Task Editor &#40;Query Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-query-tab.md) </span></span>  
 [<span data-ttu-id="7961a-126">資料採礦設計師</span><span class="sxs-lookup"><span data-stu-id="7961a-126">Data Mining Designer</span></span>](https://docs.microsoft.com/analysis-services/data-mining/data-mining-designer)  
  
  
