---
title: 資料分割處理目的地編輯器 (連線管理員頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.connection.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 7add6f82-eed1-47fc-a5d7-7b91f3f24d34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a0f79dfcc9c0d98d871a49618f4dabfb8a3bbac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595163"
---
# <a name="partition-processing-destination-editor-connection-manager-page"></a><span data-ttu-id="722fd-102">資料分割處理目的地編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="722fd-102">Partition Processing Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="722fd-103">使用 [資料分割處理目的地編輯器]\*\*\*\* 對話方塊的 [連線管理員]\*\*\*\* 頁面，以指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的連線。</span><span class="sxs-lookup"><span data-stu-id="722fd-103">Use the **Connection Manager** page of the **Partition Processing Destination Editor** dialog box to specify a connection to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="722fd-104">若要深入了解資料分割處理目的地，請參閱＜ [Partition Processing Destination](data-flow/partition-processing-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="722fd-104">To learn more abou the Partition Processing destination, see [Partition Processing Destination](data-flow/partition-processing-destination.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="722fd-105">此處描述的工作不適用於 Analysis Services 表格式模型。</span><span class="sxs-lookup"><span data-stu-id="722fd-105">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="722fd-106">您無法針對表格式模型，將輸入資料行對應至資料分割資料行。</span><span class="sxs-lookup"><span data-stu-id="722fd-106">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="722fd-107">您可以改用 Analysis Services 執行 DDL 工作 ( [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) ) 來處理資料分割。</span><span class="sxs-lookup"><span data-stu-id="722fd-107">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="722fd-108">選項。</span><span class="sxs-lookup"><span data-stu-id="722fd-108">Options</span></span>  
 <span data-ttu-id="722fd-109">**[ODBC 目的地編輯器]**</span><span class="sxs-lookup"><span data-stu-id="722fd-109">**Connection manager**</span></span>  
 <span data-ttu-id="722fd-110">從清單中選取現有的連線管理員，或按一下 [新增]  來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="722fd-110">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="722fd-111">**新增**</span><span class="sxs-lookup"><span data-stu-id="722fd-111">**New**</span></span>  
 <span data-ttu-id="722fd-112">使用 [加入 Analysis Services 連接管理員]\*\*\*\* 對話方塊來建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="722fd-112">Create a new connection by using the **Add Analysis Services Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="722fd-113">**可用的資料分割清單**</span><span class="sxs-lookup"><span data-stu-id="722fd-113">**List of available partitions**</span></span>  
 <span data-ttu-id="722fd-114">選取要處理的資料分割。</span><span class="sxs-lookup"><span data-stu-id="722fd-114">Select the partition to process.</span></span>  
  
 <span data-ttu-id="722fd-115">**處理方法**</span><span class="sxs-lookup"><span data-stu-id="722fd-115">**Processing method**</span></span>  
 <span data-ttu-id="722fd-116">選取處理方法。</span><span class="sxs-lookup"><span data-stu-id="722fd-116">Select the processing method.</span></span> <span data-ttu-id="722fd-117">此選項的預設值是 **[完整]**。</span><span class="sxs-lookup"><span data-stu-id="722fd-117">The default value of this option is **Full**.</span></span>  
  
|<span data-ttu-id="722fd-118">值</span><span class="sxs-lookup"><span data-stu-id="722fd-118">Value</span></span>|<span data-ttu-id="722fd-119">描述</span><span class="sxs-lookup"><span data-stu-id="722fd-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="722fd-120">加入 (累加)</span><span class="sxs-lookup"><span data-stu-id="722fd-120">Add (incremental)</span></span>|<span data-ttu-id="722fd-121">執行資料分割的累加處理。</span><span class="sxs-lookup"><span data-stu-id="722fd-121">Perform an incremental processing of the partition.</span></span>|  
|<span data-ttu-id="722fd-122">完整</span><span class="sxs-lookup"><span data-stu-id="722fd-122">Full</span></span>|<span data-ttu-id="722fd-123">執行資料分割的完整處理。</span><span class="sxs-lookup"><span data-stu-id="722fd-123">Perform full processing of the partition.</span></span>|  
|<span data-ttu-id="722fd-124">僅限資料</span><span class="sxs-lookup"><span data-stu-id="722fd-124">Data only</span></span>|<span data-ttu-id="722fd-125">執行資料分割的更新處理。</span><span class="sxs-lookup"><span data-stu-id="722fd-125">Perform an update processing of the partition.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="722fd-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="722fd-126">See Also</span></span>  
 <span data-ttu-id="722fd-127">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="722fd-127">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="722fd-128">[分割區處理目的地編輯器 &#40;對應頁面&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="722fd-128">[Partition Processing Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="722fd-129">資料分割處理目的地編輯器 &#40;進階頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="722fd-129">Partition Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)  
  
  
