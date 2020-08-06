---
title: 維度處理目的地編輯器 (連線管理員頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.connection.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 44aab631-d62d-4895-8fc7-7f1f3b1b68ce
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 50ba42292c1f48c9b1cdf2ba00c709dacd2f9675
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606433"
---
# <a name="dimension-processing-destination-editor-connection-manager-page"></a><span data-ttu-id="0cede-102">維度處理目的地編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="0cede-102">Dimension Processing Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="0cede-103">使用 [維度處理目的地編輯器]\*\*\*\* 對話方塊的 [連線管理員]\*\*\*\* 頁面，以指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的連線。</span><span class="sxs-lookup"><span data-stu-id="0cede-103">Use the **Connection Manager** page of the **Dimension Processing Destination Editor** dialog box to specify a connection to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0cede-104">若要深入了解維度處理目的地，請參閱＜ [Dimension Processing Destination](data-flow/dimension-processing-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0cede-104">To learn more about the Dimension Processing destination, see [Dimension Processing Destination](data-flow/dimension-processing-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0cede-105">選項。</span><span class="sxs-lookup"><span data-stu-id="0cede-105">Options</span></span>  
 <span data-ttu-id="0cede-106">**[ODBC 目的地編輯器]**</span><span class="sxs-lookup"><span data-stu-id="0cede-106">**Connection manager**</span></span>  
 <span data-ttu-id="0cede-107">從清單中選取現有的連接管理員，或按一下 [新增]\*\*\*\* 來建立新的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="0cede-107">Select an existing connection manager from the list, or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="0cede-108">**新增**</span><span class="sxs-lookup"><span data-stu-id="0cede-108">**New**</span></span>  
 <span data-ttu-id="0cede-109">使用 [加入 Analysis Services 連接管理員]\*\*\*\* 對話方塊來建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="0cede-109">Create a new connection by using the **Add Analysis Services Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="0cede-110">**可用維度清單**</span><span class="sxs-lookup"><span data-stu-id="0cede-110">**List of available dimensions**</span></span>  
 <span data-ttu-id="0cede-111">選取要處理的維度。</span><span class="sxs-lookup"><span data-stu-id="0cede-111">Select the dimension to process.</span></span>  
  
 <span data-ttu-id="0cede-112">**處理方法**</span><span class="sxs-lookup"><span data-stu-id="0cede-112">**Processing method**</span></span>  
 <span data-ttu-id="0cede-113">選取要套用至清單中選取之維度的處理方法。</span><span class="sxs-lookup"><span data-stu-id="0cede-113">Select the processing method to apply to the dimension selected in the list.</span></span> <span data-ttu-id="0cede-114">此選項的預設值是 **[完整]**。</span><span class="sxs-lookup"><span data-stu-id="0cede-114">The default value of this option is **Full**.</span></span>  
  
|<span data-ttu-id="0cede-115">值</span><span class="sxs-lookup"><span data-stu-id="0cede-115">Value</span></span>|<span data-ttu-id="0cede-116">描述</span><span class="sxs-lookup"><span data-stu-id="0cede-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0cede-117">**加入 (累加)**</span><span class="sxs-lookup"><span data-stu-id="0cede-117">**Add (incremental)**</span></span>|<span data-ttu-id="0cede-118">執行維度的累加處理。</span><span class="sxs-lookup"><span data-stu-id="0cede-118">Perform an incremental processing of the dimension.</span></span>|  
|<span data-ttu-id="0cede-119">**完整**</span><span class="sxs-lookup"><span data-stu-id="0cede-119">**Full**</span></span>|<span data-ttu-id="0cede-120">執行維度的完整處理。</span><span class="sxs-lookup"><span data-stu-id="0cede-120">Perform full processing of the dimension.</span></span>|  
|<span data-ttu-id="0cede-121">**更新**</span><span class="sxs-lookup"><span data-stu-id="0cede-121">**Update**</span></span>|<span data-ttu-id="0cede-122">執行維度的更新處理。</span><span class="sxs-lookup"><span data-stu-id="0cede-122">Perform an update processing of the dimension.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0cede-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cede-123">See Also</span></span>  
 <span data-ttu-id="0cede-124">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0cede-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="0cede-125">[維度處理目的地編輯器 &#40;對應頁面&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="0cede-125">[Dimension Processing Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="0cede-126">維度處理目的地編輯器 &#40;進階頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="0cede-126">Dimension Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../../2014/integration-services/dimension-processing-destination-editor-advanced-page.md)  
  
  
