---
title: 建置知識庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 51eff161-6ecd-4ee4-8187-1dd8ef4814bd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 03c9fc6c3a9168a66e8293c61db21a87fadc260f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592272"
---
# <a name="building-a-knowledge-base"></a><span data-ttu-id="91bdc-102">建立知識庫</span><span class="sxs-lookup"><span data-stu-id="91bdc-102">Building a Knowledge Base</span></span>
  <span data-ttu-id="91bdc-103">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中的知識庫是有關資料的知識儲存機制，可讓您了解資料及維護資料的完整性。</span><span class="sxs-lookup"><span data-stu-id="91bdc-103">A knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) is a repository of knowledge about your data that enables you to understand your data and maintain its integrity.</span></span> <span data-ttu-id="91bdc-104">知識庫是由定義域所組成，每一個定義域都代表資料欄位中的資料。</span><span class="sxs-lookup"><span data-stu-id="91bdc-104">A knowledge base consists of domains, each of which represents the data in a data field.</span></span> <span data-ttu-id="91bdc-105">DQS 會使用知識庫來執行資料庫的資料清理及刪除重複。</span><span class="sxs-lookup"><span data-stu-id="91bdc-105">The knowledge base is used by DQS to perform data cleansing and deduplication on a database.</span></span> <span data-ttu-id="91bdc-106">若要準備知識庫進行資料清理，您可以執行資料取樣的電腦輔助分析，並以互動方式管理定義域中的值。</span><span class="sxs-lookup"><span data-stu-id="91bdc-106">To prepare the knowledge base for data cleansing, you can run a computer-assisted analysis of a data sample, and interactively manage values in the domains.</span></span> <span data-ttu-id="91bdc-107">DQS 可讓您匯入知識、建立規則和關聯性、直接變更資料值，並充分利用預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="91bdc-107">DQS enables you to import knowledge, create rules and relationships, change data values directly, and leverage a default database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91bdc-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="91bdc-108">In This Section</span></span>  
 <span data-ttu-id="91bdc-109">您可以針對知識庫執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="91bdc-109">You can perform the following operations on a knowledge base:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="91bdc-110">從頭開始建立全新的知識庫，或是從現有的知識庫或 .dqs 資料檔案建立新的知識庫。</span><span class="sxs-lookup"><span data-stu-id="91bdc-110">Create a new knowledge base from scratch, from an existing knowledge base, or from a .dqs data file.</span></span>|[<span data-ttu-id="91bdc-111">建立知識庫</span><span class="sxs-lookup"><span data-stu-id="91bdc-111">Create a Knowledge Base</span></span>](../../2014/data-quality-services/create-a-knowledge-base.md)|  
|<span data-ttu-id="91bdc-112">開啟現有的知識庫來執行知識探索、定義域管理或加入比對原則。</span><span class="sxs-lookup"><span data-stu-id="91bdc-112">Open an existing knowledge base to perform knowledge discovery, domain management, or add a matching policy.</span></span>|[<span data-ttu-id="91bdc-113">開啟知識庫</span><span class="sxs-lookup"><span data-stu-id="91bdc-113">Open a Knowledge Base</span></span>](../../2014/data-quality-services/open-a-knowledge-base.md)|  
|<span data-ttu-id="91bdc-114">針對知識庫執行管理動作，包括開啟知識庫、解除鎖定知識庫、捨棄知識庫工作、重新命名知識庫、刪除知識庫，或是檢視知識庫的屬性。</span><span class="sxs-lookup"><span data-stu-id="91bdc-114">Perform management actions on a knowledge base, including opening it, unlocking it, discarding your work on it, renaming it, deleting it, or viewing its properties.</span></span>|[<span data-ttu-id="91bdc-115">管理知識庫</span><span class="sxs-lookup"><span data-stu-id="91bdc-115">Manage a Knowledge Base</span></span>](../../2014/data-quality-services/manage-a-knowledge-base.md)|  
|<span data-ttu-id="91bdc-116">透過知識探索將知識加入至知識庫；定義域值管理；加入比對原則；匯入知識、定義域或值；或是使用預設知識庫 (DQS 資料)。</span><span class="sxs-lookup"><span data-stu-id="91bdc-116">Add knowledge to a knowledge base through knowledge discovery; domain value management; adding a matching policy; importing a knowledge, domain, or values; or using the default knowledge base, DQS Data.</span></span>|[<span data-ttu-id="91bdc-117">將知識加入至知識庫</span><span class="sxs-lookup"><span data-stu-id="91bdc-117">Adding Knowledge to a Knowledge Base</span></span>](../../2014/data-quality-services/adding-knowledge-to-a-knowledge-base.md)|  
|<span data-ttu-id="91bdc-118">針對資料品質準則分析資料取樣。</span><span class="sxs-lookup"><span data-stu-id="91bdc-118">Analyze a data sample for data quality criteria.</span></span>|[<span data-ttu-id="91bdc-119">執行知識探索</span><span class="sxs-lookup"><span data-stu-id="91bdc-119">Perform Knowledge Discovery</span></span>](../../2014/data-quality-services/perform-knowledge-discovery.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="91bdc-120">相關工作</span><span class="sxs-lookup"><span data-stu-id="91bdc-120">Related Tasks</span></span>  
  
|<span data-ttu-id="91bdc-121">工作描述</span><span class="sxs-lookup"><span data-stu-id="91bdc-121">Task Description</span></span>|<span data-ttu-id="91bdc-122">主題</span><span class="sxs-lookup"><span data-stu-id="91bdc-122">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="91bdc-123">將知識匯入知識庫或是從知識庫匯出知識。</span><span class="sxs-lookup"><span data-stu-id="91bdc-123">Importing knowledge into, or exporting it from, a knowledge base.</span></span>|[<span data-ttu-id="91bdc-124">匯入和匯出知識</span><span class="sxs-lookup"><span data-stu-id="91bdc-124">Importing and Exporting Knowledge</span></span>](../../2014/data-quality-services/importing-and-exporting-knowledge.md)|  
|<span data-ttu-id="91bdc-125">建立單一定義域，並將知識加入至定義域。</span><span class="sxs-lookup"><span data-stu-id="91bdc-125">Creating a single domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="91bdc-126">管理定義域</span><span class="sxs-lookup"><span data-stu-id="91bdc-126">Managing a Domain</span></span>](../../2014/data-quality-services/managing-a-domain.md)|  
|<span data-ttu-id="91bdc-127">建立複合定義域，並將知識加入至定義域。</span><span class="sxs-lookup"><span data-stu-id="91bdc-127">Creating a composite domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="91bdc-128">管理複合定義域</span><span class="sxs-lookup"><span data-stu-id="91bdc-128">Managing a Composite Domain</span></span>](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  
