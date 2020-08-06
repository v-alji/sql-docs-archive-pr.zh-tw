---
title: 分割區處理目的地編輯器 (對應頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.mapping.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: e75b766c-85ba-453e-9576-4a1a34f91ecc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3855b15c7ebf1f6fa95c941931869064d552680e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599577"
---
# <a name="partition-processing-destination-editor-mappings-page"></a><span data-ttu-id="98eb6-102">資料分割處理目的地編輯器 (對應頁面)</span><span class="sxs-lookup"><span data-stu-id="98eb6-102">Partition Processing Destination Editor (Mappings Page)</span></span>
  <span data-ttu-id="98eb6-103">使用 **[資料分割處理目的地編輯器]** 對話方塊的 **[對應]** 頁面，來將輸入資料行對應至資料分割資料行。</span><span class="sxs-lookup"><span data-stu-id="98eb6-103">Use the **Mappings** page of the **Partition Processing Destination Editor** dialog box to map input columns to partition columns.</span></span>  
  
 <span data-ttu-id="98eb6-104">若要深入了解資料分割處理目的地，請參閱＜ [Partition Processing Destination](data-flow/partition-processing-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="98eb6-104">To learn more abou the Partition Processing destination, see [Partition Processing Destination](data-flow/partition-processing-destination.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98eb6-105">此處描述的工作不適用於 Analysis Services 表格式模型。</span><span class="sxs-lookup"><span data-stu-id="98eb6-105">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="98eb6-106">您無法針對表格式模型，將輸入資料行對應至資料分割資料行。</span><span class="sxs-lookup"><span data-stu-id="98eb6-106">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="98eb6-107">您可以改用 Analysis Services 執行 DDL 工作 ( [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) ) 來處理資料分割。</span><span class="sxs-lookup"><span data-stu-id="98eb6-107">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="98eb6-108">選項。</span><span class="sxs-lookup"><span data-stu-id="98eb6-108">Options</span></span>  
 <span data-ttu-id="98eb6-109">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="98eb6-109">**Available Input Columns**</span></span>  
 <span data-ttu-id="98eb6-110">檢視可用的輸入資料行清單。</span><span class="sxs-lookup"><span data-stu-id="98eb6-110">View the list of available input columns.</span></span> <span data-ttu-id="98eb6-111">使用拖放作業，即可將資料表中的可用輸入資料行對應到目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="98eb6-111">Use a drag-and-drop operation to map available input columns in the table to destination columns.</span></span>  
  
 <span data-ttu-id="98eb6-112">**可用的目的地資料行**</span><span class="sxs-lookup"><span data-stu-id="98eb6-112">**Available Destination Columns**</span></span>  
 <span data-ttu-id="98eb6-113">檢視可用的目的地資料行清單。</span><span class="sxs-lookup"><span data-stu-id="98eb6-113">View the list of available destination columns.</span></span> <span data-ttu-id="98eb6-114">使用拖放作業，即可將資料表中的可用目的地資料行對應到輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="98eb6-114">Use a drag-and-drop operation to map available destination columns in the table to input columns.</span></span>  
  
 <span data-ttu-id="98eb6-115">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="98eb6-115">**Input Column**</span></span>  
 <span data-ttu-id="98eb6-116">從上述資料表檢視選取的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="98eb6-116">View input columns selected from the table above.</span></span> <span data-ttu-id="98eb6-117">您可以使用 **[可用的輸入資料行]** 清單來變更對應。</span><span class="sxs-lookup"><span data-stu-id="98eb6-117">You can change the mappings by using the list of **Available Input Columns**.</span></span>  
  
 <span data-ttu-id="98eb6-118">**目的地資料行**</span><span class="sxs-lookup"><span data-stu-id="98eb6-118">**Destination Column**</span></span>  
 <span data-ttu-id="98eb6-119">檢視每個可用的目的地資料行，不論是否已經對應。</span><span class="sxs-lookup"><span data-stu-id="98eb6-119">View each available destination column, whether it is mapped or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98eb6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98eb6-120">See Also</span></span>  
 <span data-ttu-id="98eb6-121">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="98eb6-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="98eb6-122">[資料分割處理目的地編輯器 &#40;連線管理員頁面&#41;](../../2014/integration-services/partition-processing-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="98eb6-122">[Partition Processing Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/partition-processing-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="98eb6-123">資料分割處理目的地編輯器 &#40;進階頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="98eb6-123">Partition Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)  
  
  
