---
title: 代理程式設定檔 (單一代理程式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.perfprofileagentname.f1
helpviewer_keywords:
- Agent Profile dialog box
ms.assetid: 22713555-c496-4ce1-8ec7-4ae75cfadca8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7def9a6fef4e7e66076ee18552705c6071dab134
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593963"
---
# <a name="agent-profiles-single-agent"></a><span data-ttu-id="84dea-102">代理程式設定檔 (單一代理程式)</span><span class="sxs-lookup"><span data-stu-id="84dea-102">Agent Profiles (single agent)</span></span>
  <span data-ttu-id="84dea-103">使用 **[代理程式設定檔]** 對話方塊，即可管理代理程式的設定檔。</span><span class="sxs-lookup"><span data-stu-id="84dea-103">Use the **Agent Profiles** dialog box to manage profiles for an agent.</span></span> <span data-ttu-id="84dea-104">代理程式設定檔提供便於管理每一個代理程式執行階段參數的方式。</span><span class="sxs-lookup"><span data-stu-id="84dea-104">Agent profiles provide a convenient way to manage the runtime parameters for each agent.</span></span> <span data-ttu-id="84dea-105">每一個代理程式都有預設的設定檔，有些代理程式還有其他預先定義的設定檔。</span><span class="sxs-lookup"><span data-stu-id="84dea-105">Each agent has a default profile, and some agents have additional predefined profiles.</span></span> <span data-ttu-id="84dea-106">例如，合併代理程式有專為低頻寬連接設計的「慢速連結」設定檔。</span><span class="sxs-lookup"><span data-stu-id="84dea-106">For example, the Merge Agent has a "slow link" profile designed for low bandwidth connections.</span></span> <span data-ttu-id="84dea-107">預先定義的設定檔對大部份應用程式而言已經足夠，但您也可以建立使用者自訂設定檔，來自訂代理程式的行為。</span><span class="sxs-lookup"><span data-stu-id="84dea-107">Predefined profiles are sufficient for most applications, but you can also create user-defined profiles, allowing you to customize agent behavior.</span></span>  
  
## <a name="options"></a><span data-ttu-id="84dea-108">選項。</span><span class="sxs-lookup"><span data-stu-id="84dea-108">Options</span></span>  
 <span data-ttu-id="84dea-109">**新項目的預設值**</span><span class="sxs-lookup"><span data-stu-id="84dea-109">**Default for New**</span></span>  
 <span data-ttu-id="84dea-110">選取為指定類型之代理程式建立作業時所使用的設定檔。</span><span class="sxs-lookup"><span data-stu-id="84dea-110">Select the profile that will be used when jobs are created for an agent of a given type.</span></span> <span data-ttu-id="84dea-111">例如，若您對合併式發行集建立一些訂閱，則每一個訂閱的合併代理程式作業就會使用所選取的設定檔。</span><span class="sxs-lookup"><span data-stu-id="84dea-111">For example, if you create a number of subscriptions to a merge publication, the Merge Agent job for each subscription will use the profile selected.</span></span> <span data-ttu-id="84dea-112">如果您要變更現有作業的設定檔，請選取設定檔，然後按一下 **[變更現有的代理程式]** 。</span><span class="sxs-lookup"><span data-stu-id="84dea-112">If you want to change the profile for existing jobs, select a profile, and then click **Change Existing Agents**.</span></span>  
  
 <span data-ttu-id="84dea-113">**名稱**</span><span class="sxs-lookup"><span data-stu-id="84dea-113">**Name**</span></span>  
 <span data-ttu-id="84dea-114">設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="84dea-114">The name of the profile.</span></span>  
  
 <span data-ttu-id="84dea-115">**型別**</span><span class="sxs-lookup"><span data-stu-id="84dea-115">**Type**</span></span>  
 <span data-ttu-id="84dea-116">設定檔的類型： **[使用者]** (使用者自訂) 或 **[系統]** (預先定義)。</span><span class="sxs-lookup"><span data-stu-id="84dea-116">The type of profile: **User** (user-defined) or **System** (predefined).</span></span>  
  
 <span data-ttu-id="84dea-117">**屬性 (...)**</span><span class="sxs-lookup"><span data-stu-id="84dea-117">**Properties (...)**</span></span>  
 <span data-ttu-id="84dea-118">按一下即可檢視代理程式設定檔中，每一個參數所使用的值。</span><span class="sxs-lookup"><span data-stu-id="84dea-118">Click to view the values used for each parameter in the agent profile.</span></span>  
  
 <span data-ttu-id="84dea-119">**新增**</span><span class="sxs-lookup"><span data-stu-id="84dea-119">**New**</span></span>  
 <span data-ttu-id="84dea-120">按一下即可建立新的設定檔。</span><span class="sxs-lookup"><span data-stu-id="84dea-120">Click to create a new profile.</span></span>  
  
 <span data-ttu-id="84dea-121">**刪除**</span><span class="sxs-lookup"><span data-stu-id="84dea-121">**Delete**</span></span>  
 <span data-ttu-id="84dea-122">選取使用者自訂設定檔，然後按一下 **[刪除]** 即可刪除該設定檔。</span><span class="sxs-lookup"><span data-stu-id="84dea-122">Select a user-defined profile, and then click **Delete** to delete that profile.</span></span> <span data-ttu-id="84dea-123">預先定義的設定檔無法刪除。</span><span class="sxs-lookup"><span data-stu-id="84dea-123">Predefined profiles cannot be deleted.</span></span>  
  
 <span data-ttu-id="84dea-124">**[變更現有的代理程式]**</span><span class="sxs-lookup"><span data-stu-id="84dea-124">**Change Existing Agents**</span></span>  
 <span data-ttu-id="84dea-125">選取設定檔，然後按一下 **[變更現有的代理程式]** ，即可指定特定代理程式類型的所有現有作業，都使用選取的設定檔。</span><span class="sxs-lookup"><span data-stu-id="84dea-125">Select a profile, and then click **Change Existing Agents** to specify that all existing jobs for an agent of a given type should use the selected profile.</span></span> <span data-ttu-id="84dea-126">例如，若您對合併式發行集建立了一些訂閱，但您要變更設定檔，以指定每個訂閱的合併代理程式作業都使用 **[慢速連結代理程式設定檔]** ，請選取該設定檔，然後按一下 **[變更現有的代理程式]** 。</span><span class="sxs-lookup"><span data-stu-id="84dea-126">For example, if you have created a number of subscriptions to a merge publication, and you want to change the profile to specify that the Merge Agent job for each of these subscriptions should use the **Slow link agent profile**, select that profile, and then click **Change Existing Agents**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84dea-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84dea-127">See Also</span></span>  
 <span data-ttu-id="84dea-128">[處理複寫代理程式設定檔](agents/work-with-replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="84dea-128">[Work with Replication Agent Profiles](agents/work-with-replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="84dea-129">[複寫代理程式概觀](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="84dea-129">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="84dea-130">複寫代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="84dea-130">Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
  
