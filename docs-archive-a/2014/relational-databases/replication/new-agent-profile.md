---
title: 新增代理程式設定檔 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.newperfprofile.f1
helpviewer_keywords:
- New Agent Profile dialog box
ms.assetid: ebf59330-a421-45a5-9020-0484a96852bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1d7848e44585fd35a5b5a33cf431e15de96c9375
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705037"
---
# <a name="new-agent-profile"></a><span data-ttu-id="7c351-102">新增代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="7c351-102">New Agent Profile</span></span>
  <span data-ttu-id="7c351-103">使用 **[新增代理程式設定檔]** 對話方塊，即可建立新的設定檔。</span><span class="sxs-lookup"><span data-stu-id="7c351-103">Use the **New Agent Profile** dialog box to create a new profile.</span></span> <span data-ttu-id="7c351-104">新的設定檔一律會以現有設定檔為基礎，但是還可以進行修改來滿足應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="7c351-104">New profiles are always based on existing profiles, but they can be modified to meet application requirements.</span></span> <span data-ttu-id="7c351-105">建立了設定檔之後，即可套用到 **[代理程式設定檔]** 對話方塊中之現有及未來的代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="7c351-105">After a profile has been created, it can be applied to existing and future agent jobs in the **Agent Profiles** dialog box.</span></span> <span data-ttu-id="7c351-106">代理程式參數值可在 \<**AgentProfileName> 屬性\*\*對話方塊中編輯。</span><span class="sxs-lookup"><span data-stu-id="7c351-106">Agent parameter values can be edited in the \<**AgentProfileName> Properties\*\* dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7c351-107">選項。</span><span class="sxs-lookup"><span data-stu-id="7c351-107">Options</span></span>  
 <span data-ttu-id="7c351-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="7c351-108">**Name**</span></span>  
 <span data-ttu-id="7c351-109">輸入設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="7c351-109">Enter a name for the profile.</span></span>  
  
 <span data-ttu-id="7c351-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="7c351-110">**Description**</span></span>  
 <span data-ttu-id="7c351-111">輸入設定檔的描述。</span><span class="sxs-lookup"><span data-stu-id="7c351-111">Enter a description for the profile.</span></span>  
  
 <span data-ttu-id="7c351-112">**參數**</span><span class="sxs-lookup"><span data-stu-id="7c351-112">**Parameter**</span></span>  
 <span data-ttu-id="7c351-113">設定檔中包括的代理程式參數。</span><span class="sxs-lookup"><span data-stu-id="7c351-113">The agent parameters included in the profile.</span></span> <span data-ttu-id="7c351-114">作為新設定檔之基礎的設定檔，並不一定會為每一個參數都指定值。</span><span class="sxs-lookup"><span data-stu-id="7c351-114">The profile on which the new profile is based does not necessarily specify a value for each parameter.</span></span> <span data-ttu-id="7c351-115">若要檢視給定代理程式的所有有效參數，請清除 **[只顯示這個設定檔中使用的參數]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7c351-115">To see all parameters that are valid for a given agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="7c351-116">如需每一個參數的描述，請參閱：</span><span class="sxs-lookup"><span data-stu-id="7c351-116">For descriptions of each parameter, see:</span></span>  
  
-   [<span data-ttu-id="7c351-117">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="7c351-117">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
-   [<span data-ttu-id="7c351-118">複寫記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="7c351-118">Replication Log Reader Agent</span></span>](agents/replication-log-reader-agent.md)  
  
-   [<span data-ttu-id="7c351-119">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="7c351-119">Replication Distribution Agent</span></span>](agents/replication-distribution-agent.md)  
  
-   [<span data-ttu-id="7c351-120">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="7c351-120">Replication Merge Agent</span></span>](agents/replication-merge-agent.md)  
  
-   [<span data-ttu-id="7c351-121">複寫佇列讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="7c351-121">Replication Queue Reader Agent</span></span>](agents/replication-queue-reader-agent.md)  
  
 <span data-ttu-id="7c351-122">**預設值**</span><span class="sxs-lookup"><span data-stu-id="7c351-122">**Default Value**</span></span>  
 <span data-ttu-id="7c351-123">每一個代理程式參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="7c351-123">The default value for each agent parameter.</span></span>  
  
 <span data-ttu-id="7c351-124">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="7c351-124">**Value**</span></span>  
 <span data-ttu-id="7c351-125">針對作為新設定檔之基礎的設定檔中，所指定的參數值。</span><span class="sxs-lookup"><span data-stu-id="7c351-125">The value specified for the parameter in the profile on which the new profile is based.</span></span> <span data-ttu-id="7c351-126">編輯此欄位，即可變更參數的值。</span><span class="sxs-lookup"><span data-stu-id="7c351-126">Edit this field for any parameter values you want to change.</span></span>  
  
 <span data-ttu-id="7c351-127">**[只顯示這個設定檔中使用的參數]**</span><span class="sxs-lookup"><span data-stu-id="7c351-127">**Show only parameters used in this profile**</span></span>  
 <span data-ttu-id="7c351-128">清除即可顯示給定代理程式的所有有效參數。</span><span class="sxs-lookup"><span data-stu-id="7c351-128">Clear to show all valid parameters for a given agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c351-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c351-129">See Also</span></span>  
 <span data-ttu-id="7c351-130">[處理複寫代理程式設定檔](agents/work-with-replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="7c351-130">[Work with Replication Agent Profiles](agents/work-with-replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="7c351-131">[複寫代理程式概觀](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="7c351-131">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="7c351-132">複寫代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="7c351-132">Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
  
