---
title: 監視套件執行和其他作業 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cbbcd79f-ab9b-46ec-84cb-4821c1d16b99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 628b62d9c8e01d0dc0bf641551de67c3838a4504
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606978"
---
# <a name="monitoring-for-package-executions-and-other-operations"></a><span data-ttu-id="23b9f-102">監視封裝執行和其他作業</span><span class="sxs-lookup"><span data-stu-id="23b9f-102">Monitoring for Package Executions and Other Operations</span></span>
  <span data-ttu-id="23b9f-103">您可以使用下列其中一項或多項工具，監視 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 執行封裝、專案驗證及其他作業。</span><span class="sxs-lookup"><span data-stu-id="23b9f-103">You can monitor [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package executions, project validations, and other operations by using one of more of the following tools.</span></span> <span data-ttu-id="23b9f-104">某些工具 (例如資料點選) 僅適用於部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器的專案。</span><span class="sxs-lookup"><span data-stu-id="23b9f-104">Certain tools such as data taps are available only for projects that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
-   <span data-ttu-id="23b9f-105">記錄</span><span class="sxs-lookup"><span data-stu-id="23b9f-105">Logs</span></span>  
  
     <span data-ttu-id="23b9f-106">如需詳細資訊，請參閱 [集成服務 &#40;SSIS&#41; 記錄](integration-services-ssis-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="23b9f-106">For more information, see [Integration Services &#40;SSIS&#41; Logging](integration-services-ssis-logging.md).</span></span>  
  
-   <span data-ttu-id="23b9f-107">報表</span><span class="sxs-lookup"><span data-stu-id="23b9f-107">Reports</span></span>  
  
     <span data-ttu-id="23b9f-108">如需詳細資訊，請參閱 [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="23b9f-108">For more information, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
-   <span data-ttu-id="23b9f-109">檢視</span><span class="sxs-lookup"><span data-stu-id="23b9f-109">Views</span></span>  
  
     <span data-ttu-id="23b9f-110">如需詳細資訊，請參閱[檢視 &#40;Integration Services 目錄&#41;](/sql/integration-services/system-views/views-integration-services-catalog)。</span><span class="sxs-lookup"><span data-stu-id="23b9f-110">For more information, see [Views &#40;Integration Services Catalog&#41;](/sql/integration-services/system-views/views-integration-services-catalog).</span></span>  
  
-   <span data-ttu-id="23b9f-111">效能計數器</span><span class="sxs-lookup"><span data-stu-id="23b9f-111">Performance counters</span></span>  
  
     <span data-ttu-id="23b9f-112">如需相關資訊，請參閱 [Performance Counters](performance-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="23b9f-112">For more information, see [Performance Counters](performance-counters.md).</span></span>  
  
-   <span data-ttu-id="23b9f-113">資料點選</span><span class="sxs-lookup"><span data-stu-id="23b9f-113">Data taps</span></span>  
  
## <a name="operation-types"></a><span data-ttu-id="23b9f-114">作業類型</span><span class="sxs-lookup"><span data-stu-id="23b9f-114">Operation Types</span></span>  
 <span data-ttu-id="23b9f-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器上的 `SSISDB` 目錄中會監視數個不同類型的作業。</span><span class="sxs-lookup"><span data-stu-id="23b9f-115">Several different types of operations are monitored in the `SSISDB` catalog, on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="23b9f-116">每個作業都可以有多則與其相關聯的訊息。</span><span class="sxs-lookup"><span data-stu-id="23b9f-116">Each operation can have multiple messages associated with it.</span></span> <span data-ttu-id="23b9f-117">每則訊息可以分類在數種不同的類型之一。</span><span class="sxs-lookup"><span data-stu-id="23b9f-117">Each message can be classified into one of several different types.</span></span> <span data-ttu-id="23b9f-118">例如，訊息可以是資訊、警告或錯誤等類型。</span><span class="sxs-lookup"><span data-stu-id="23b9f-118">For example, a message can be of type Information, Warning, or Error.</span></span> <span data-ttu-id="23b9f-119">如需訊息類型的完整清單，請參閱 Transact-SQL [catalog.operation_messages &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database) 檢視的文件集。</span><span class="sxs-lookup"><span data-stu-id="23b9f-119">For the full list of message types, see the documentation for the Transact-SQL [catalog.operation_messages &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database) view.</span></span> <span data-ttu-id="23b9f-120">如需作業類型的完整清單，請參閱 [catalog.operations &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="23b9f-120">For a full list of the operations types, see [catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database).</span></span>  
  
 <span data-ttu-id="23b9f-121">有九種不同的狀態類型可用來指示作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="23b9f-121">Nine different status types are used to indicate the status of an operation.</span></span> <span data-ttu-id="23b9f-122">如需狀態類型的完整清單，請參閱 [catalog.operations &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database) 檢視。</span><span class="sxs-lookup"><span data-stu-id="23b9f-122">For a full list of the status types, see the [catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database) view.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="23b9f-123">相關內容</span><span class="sxs-lookup"><span data-stu-id="23b9f-123">Related Content</span></span>  
 <span data-ttu-id="23b9f-124">blogs.msdn.com 上的部落格文章： [SSIS T-SQL API Overview](https://go.microsoft.com/fwlink/?LinkId=249051)(SSIS T-SQL API 概觀)。</span><span class="sxs-lookup"><span data-stu-id="23b9f-124">Blog entry, [SSIS T-SQL API Overview](https://go.microsoft.com/fwlink/?LinkId=249051), on blogs.msdn.com.</span></span>  
  
  
