---
title: 代理程式設定檔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.perfprofiles.f1
helpviewer_keywords:
- Agent Profiles dialog box
ms.assetid: 0422e99c-e688-419b-bb4c-c7bebeef1d8d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7584670088da1ac7a9c81f1f8f0cbdce8b040c7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593962"
---
# <a name="agent-profiles"></a><span data-ttu-id="4a742-102">代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="4a742-102">Agent Profiles</span></span>
  <span data-ttu-id="4a742-103">使用 **[代理程式設定檔]** 對話方塊，即可管理代理程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="4a742-103">Use the **Agent Profiles** dialog box to manage agent profiles.</span></span> <span data-ttu-id="4a742-104">代理程式設定檔提供便於管理每一個代理程式執行階段參數的方式。</span><span class="sxs-lookup"><span data-stu-id="4a742-104">Agent profiles provide a convenient way to manage the runtime parameters for each agent.</span></span> <span data-ttu-id="4a742-105">每一個代理程式都有預設的設定檔，有些代理程式還有其他預先定義的設定檔。</span><span class="sxs-lookup"><span data-stu-id="4a742-105">Each agent has a default profile, and some agents have additional predefined profiles.</span></span> <span data-ttu-id="4a742-106">例如，合併代理程式有專為低頻寬連接設計的「慢速連結」設定檔。</span><span class="sxs-lookup"><span data-stu-id="4a742-106">For example, the Merge Agent has a "slow link" profile designed for low bandwidth connections.</span></span> <span data-ttu-id="4a742-107">預先定義的設定檔對大部份應用程式而言已經足夠，但您也可以建立使用者自訂設定檔，來自訂代理程式的行為。</span><span class="sxs-lookup"><span data-stu-id="4a742-107">Predefined profiles are sufficient for most applications, but you can also create user-defined profiles, allowing you to customize agent behavior.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4a742-108">選項。</span><span class="sxs-lookup"><span data-stu-id="4a742-108">Options</span></span>  
 <span data-ttu-id="4a742-109">**選取頁面**</span><span class="sxs-lookup"><span data-stu-id="4a742-109">**Select a page**</span></span>  
 <span data-ttu-id="4a742-110">在左窗格中選取代理程式，右窗格就會顯示代理程式的設定檔。</span><span class="sxs-lookup"><span data-stu-id="4a742-110">Select an agent in the left pane, and the profiles for the agent are displayed in the right pane.</span></span>  
  
 <span data-ttu-id="4a742-111">**新項目的預設值**</span><span class="sxs-lookup"><span data-stu-id="4a742-111">**Default for New**</span></span>  
 <span data-ttu-id="4a742-112">選取為指定類型之代理程式建立作業時所使用的設定檔。</span><span class="sxs-lookup"><span data-stu-id="4a742-112">Select the profile that will be used when jobs are created for an agent of a given type.</span></span> <span data-ttu-id="4a742-113">例如，若您對合併式發行集建立一些訂閱，則每一個訂閱的合併代理程式作業就會使用所選取的設定檔。</span><span class="sxs-lookup"><span data-stu-id="4a742-113">For example, if you create a number of subscriptions to a merge publication, the Merge Agent job for each subscription will use the profile selected.</span></span> <span data-ttu-id="4a742-114">如果您要變更現有作業的設定檔，請選取設定檔，然後按一下 **[變更現有的代理程式]** 。</span><span class="sxs-lookup"><span data-stu-id="4a742-114">If you want to change the profile for existing jobs, select a profile, and then click **Change Existing Agents**.</span></span>  
  
 <span data-ttu-id="4a742-115">**名稱**</span><span class="sxs-lookup"><span data-stu-id="4a742-115">**Name**</span></span>  
 <span data-ttu-id="4a742-116">設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="4a742-116">The name of the profile.</span></span>  
  
 <span data-ttu-id="4a742-117">**型別**</span><span class="sxs-lookup"><span data-stu-id="4a742-117">**Type**</span></span>  
 <span data-ttu-id="4a742-118">設定檔的類型： **[使用者]** (使用者自訂) 或 **[系統]** (預先定義)。</span><span class="sxs-lookup"><span data-stu-id="4a742-118">The type of profile: **User** (user-defined) or **System** (predefined).</span></span>  
  
 <span data-ttu-id="4a742-119">**屬性 (...)**</span><span class="sxs-lookup"><span data-stu-id="4a742-119">**Properties (...)**</span></span>  
 <span data-ttu-id="4a742-120">按一下即可檢視代理程式設定檔中，每一個參數所使用的值。</span><span class="sxs-lookup"><span data-stu-id="4a742-120">Click to view the values used for each parameter in the agent profile.</span></span>  
  
 <span data-ttu-id="4a742-121">**新增**</span><span class="sxs-lookup"><span data-stu-id="4a742-121">**New**</span></span>  
 <span data-ttu-id="4a742-122">按一下即可建立新的設定檔。</span><span class="sxs-lookup"><span data-stu-id="4a742-122">Click to create a new profile.</span></span>  
  
 <span data-ttu-id="4a742-123">**刪除**</span><span class="sxs-lookup"><span data-stu-id="4a742-123">**Delete**</span></span>  
 <span data-ttu-id="4a742-124">選取使用者自訂設定檔，然後按一下 **[刪除]** 即可刪除該設定檔。</span><span class="sxs-lookup"><span data-stu-id="4a742-124">Select a user-defined profile, and then click **Delete** to delete that profile.</span></span> <span data-ttu-id="4a742-125">預先定義的設定檔無法刪除。</span><span class="sxs-lookup"><span data-stu-id="4a742-125">Predefined profiles cannot be deleted.</span></span>  
  
 <span data-ttu-id="4a742-126">**[變更現有的代理程式]**</span><span class="sxs-lookup"><span data-stu-id="4a742-126">**Change Existing Agents**</span></span>  
 <span data-ttu-id="4a742-127">選取設定檔，然後按一下 **[變更現有的代理程式]** ，即可指定特定代理程式類型的所有現有作業，都使用選取的設定檔。</span><span class="sxs-lookup"><span data-stu-id="4a742-127">Select a profile, and then click **Change Existing Agents** to specify that all existing jobs for an agent of a given type should use the selected profile.</span></span> <span data-ttu-id="4a742-128">例如，若您對合併式發行集建立了一些訂閱，但您要變更設定檔，以指定每個訂閱的合併代理程式作業都使用 **[慢速連結代理程式設定檔]** ，請選取該設定檔，然後按一下 **[變更現有的代理程式]** 。</span><span class="sxs-lookup"><span data-stu-id="4a742-128">For example, if you have created a number of subscriptions to a merge publication, and you want to change the profile to specify that the Merge Agent job for each of these subscriptions should use the **Slow link agent profile**, select that profile, and then click **Change Existing Agents**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a742-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a742-129">See Also</span></span>  
 <span data-ttu-id="4a742-130">[處理複寫代理程式設定檔](agents/work-with-replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="4a742-130">[Work with Replication Agent Profiles](agents/work-with-replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="4a742-131">[複寫代理程式概觀](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="4a742-131">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="4a742-132">複寫代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="4a742-132">Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
  
