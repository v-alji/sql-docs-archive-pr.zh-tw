---
title: 訂閱者類型 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.subscribertypes.f1
ms.assetid: a70656cb-21c9-4489-be77-ccd396747e3b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d356377dec1f5307fa136c94ea682c0824479a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606238"
---
# <a name="subscriber-types"></a><span data-ttu-id="9e42d-102">訂閱者類型</span><span class="sxs-lookup"><span data-stu-id="9e42d-102">Subscriber Types</span></span>
  <span data-ttu-id="9e42d-103">合併式複寫可讓您指定發行集必須支援的訂閱者類型。</span><span class="sxs-lookup"><span data-stu-id="9e42d-103">Merge replication allows you to specify the types of Subscribers that a publication must support.</span></span> <span data-ttu-id="9e42d-104">選取訂閱者類型會設定 *發行集相容性層級*，以決定發行集可以使用哪些功能。</span><span class="sxs-lookup"><span data-stu-id="9e42d-104">Selecting Subscriber types sets the *publication compatibility level*, which determines which features can be used by a publication.</span></span>  
  
 <span data-ttu-id="9e42d-105">建立發行集快照集之後，可以在 **[發行集屬性]** 對話方塊的 **[一般]** 頁面上增加發行集相容性層級 (設定更多限制)；不可以減少相容性層級。</span><span class="sxs-lookup"><span data-stu-id="9e42d-105">After a publication snapshot is created, the publication compatibility level can be increased (made more restrictive) on the **General** page of the **Publication Properties** dialog box; the compatibility level cannot be decreased.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9e42d-106">選項。</span><span class="sxs-lookup"><span data-stu-id="9e42d-106">Options</span></span>  
 <span data-ttu-id="9e42d-107">選取此發行集必須支援的每個訂閱者類型。</span><span class="sxs-lookup"><span data-stu-id="9e42d-107">Select each Subscriber type that this publication must support.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 <span data-ttu-id="9e42d-108">發行集可以使用所有的功能。</span><span class="sxs-lookup"><span data-stu-id="9e42d-108">The publication can use all features.</span></span>  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]  
 <span data-ttu-id="9e42d-109">發行集需要快照集檔案為字元格式 (這可由快照集代理程式自動處理)。</span><span class="sxs-lookup"><span data-stu-id="9e42d-109">The publication requires snapshot files to be in character format (this is handled automatically by the Snapshot Agent).</span></span> [!INCLUDE[ssEW](../../includes/ssew-md.md)] <span data-ttu-id="9e42d-110">也有許多與相容性層級無關的限制。</span><span class="sxs-lookup"><span data-stu-id="9e42d-110">also has a number of restrictions not related to compatibility level.</span></span>  
  
 <span data-ttu-id="9e42d-111">如果選取此選項，就會啟用發行集的 Web 同步處理選項。</span><span class="sxs-lookup"><span data-stu-id="9e42d-111">If this option is selected, the Web synchronization option is enabled for the publication.</span></span> <span data-ttu-id="9e42d-112">如需有關 Web 同步處理的詳細資訊，請參閱＜ [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9e42d-112">For more information about Web synchronization, see [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e42d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e42d-113">See Also</span></span>  
 <span data-ttu-id="9e42d-114">[發行資料和資料庫物件](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="9e42d-114">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="9e42d-115">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="9e42d-115">[Create a Publication](publish/create-a-publication.md) </span></span>  
 [<span data-ttu-id="9e42d-116">檢視及修改散發者和發行者屬性</span><span class="sxs-lookup"><span data-stu-id="9e42d-116">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

  
