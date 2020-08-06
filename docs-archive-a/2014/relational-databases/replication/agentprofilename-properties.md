---
title: '&lt;代理程式設定檔名稱&gt; 屬性 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.perfprofileprops.f1
helpviewer_keywords:
- Agent Profile Properties dialog box
ms.assetid: 01a992d2-e4ff-417c-93f0-dc43ab2d1624
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 561f55353b7e40d168266cf5ba531519c8225053
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606803"
---
# <a name="ltagentprofilenamegt-properties"></a><span data-ttu-id="ead5c-102">&lt;代理程式設定檔名稱&gt; 屬性</span><span class="sxs-lookup"><span data-stu-id="ead5c-102">&lt;AgentProfileName&gt; Properties</span></span>
  <span data-ttu-id="ead5c-103">請使用 **[代理程式設定檔屬性]** 對話方塊，即可檢視設定檔中、每一個代理程式參數所指定的值，以及修改使用者自訂設定檔的值。</span><span class="sxs-lookup"><span data-stu-id="ead5c-103">Use the **Agent Profiles Properties** dialog box to view the values specified for each agent parameter in a profile and to modify the values for user-defined profiles.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ead5c-104">選項。</span><span class="sxs-lookup"><span data-stu-id="ead5c-104">Options</span></span>  
 <span data-ttu-id="ead5c-105">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ead5c-105">**Name**</span></span>  
 <span data-ttu-id="ead5c-106">設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="ead5c-106">The name of the profile.</span></span>  
  
 <span data-ttu-id="ead5c-107">**說明**</span><span class="sxs-lookup"><span data-stu-id="ead5c-107">**Description**</span></span>  
 <span data-ttu-id="ead5c-108">設定檔的描述。</span><span class="sxs-lookup"><span data-stu-id="ead5c-108">A description of the profile.</span></span>  
  
 <span data-ttu-id="ead5c-109">**參數**</span><span class="sxs-lookup"><span data-stu-id="ead5c-109">**Parameter**</span></span>  
 <span data-ttu-id="ead5c-110">設定檔中包括的代理程式參數。</span><span class="sxs-lookup"><span data-stu-id="ead5c-110">The agent parameters included in the profile.</span></span> <span data-ttu-id="ead5c-111">設定檔不一定要指定每一個參數的值。</span><span class="sxs-lookup"><span data-stu-id="ead5c-111">Profiles do not necessarily specify a value for each parameter.</span></span> <span data-ttu-id="ead5c-112">若要檢視給定代理程式的所有有效參數，請清除 **[只顯示這個設定檔中使用的參數]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ead5c-112">To see all parameters that are valid for a given agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="ead5c-113">如需每一個參數的描述，請參閱：</span><span class="sxs-lookup"><span data-stu-id="ead5c-113">For descriptions of each parameter, see:</span></span>  
  
-   [<span data-ttu-id="ead5c-114">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="ead5c-114">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
-   [<span data-ttu-id="ead5c-115">複寫記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="ead5c-115">Replication Log Reader Agent</span></span>](agents/replication-log-reader-agent.md)  
  
-   [<span data-ttu-id="ead5c-116">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="ead5c-116">Replication Distribution Agent</span></span>](agents/replication-distribution-agent.md)  
  
-   [<span data-ttu-id="ead5c-117">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="ead5c-117">Replication Merge Agent</span></span>](agents/replication-merge-agent.md)  
  
-   [<span data-ttu-id="ead5c-118">複寫佇列讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="ead5c-118">Replication Queue Reader Agent</span></span>](agents/replication-queue-reader-agent.md)  
  
 <span data-ttu-id="ead5c-119">**預設值**</span><span class="sxs-lookup"><span data-stu-id="ead5c-119">**Default Value**</span></span>  
 <span data-ttu-id="ead5c-120">每一個代理程式參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="ead5c-120">The default value for each agent parameter.</span></span>  
  
 <span data-ttu-id="ead5c-121">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="ead5c-121">**Value**</span></span>  
 <span data-ttu-id="ead5c-122">設定檔中指定的參數值。</span><span class="sxs-lookup"><span data-stu-id="ead5c-122">The value specified for the parameter in the profile.</span></span> <span data-ttu-id="ead5c-123">此欄位為使用者自訂設定檔中可編輯的欄位。</span><span class="sxs-lookup"><span data-stu-id="ead5c-123">This field is editable for user-defined profiles.</span></span>  
  
 <span data-ttu-id="ead5c-124">**[只顯示這個設定檔中使用的參數]**</span><span class="sxs-lookup"><span data-stu-id="ead5c-124">**Show only parameters used in this profile**</span></span>  
 <span data-ttu-id="ead5c-125">清除即可顯示給定代理程式的所有有效參數。</span><span class="sxs-lookup"><span data-stu-id="ead5c-125">Clear to show all valid parameters for a given agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ead5c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ead5c-126">See Also</span></span>  
 <span data-ttu-id="ead5c-127">[處理複寫代理程式設定檔](agents/work-with-replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="ead5c-127">[Work with Replication Agent Profiles](agents/work-with-replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="ead5c-128">[複寫代理程式概觀](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="ead5c-128">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="ead5c-129">複寫代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="ead5c-129">Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
  
