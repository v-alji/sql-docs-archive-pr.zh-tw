---
title: '[連接到現有次要複本] 頁面 (新增複本嚮導] 和 [新增資料庫] Wizard) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.connecttoreplicas.f1
- sql12.swb.adddatabasewizard.connecttoreplicas.f1
ms.assetid: 850f1bc8-d7d0-425c-bd7b-03f0e9d3348e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 80af8dfebd6e23a923ddf67438edabf9ab0e2f65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688230"
---
# <a name="connect-to-existing-secondary-replicas-page-add-replica-wizard-and-add-databases-wizard"></a><span data-ttu-id="b9aa8-102">連線到現有次要複本頁面 (新增複本精靈及新增資料庫精靈)</span><span class="sxs-lookup"><span data-stu-id="b9aa8-102">Connect to Existing Secondary Replicas Page (Add Replica Wizard and Add Databases Wizard)</span></span>
  <span data-ttu-id="b9aa8-103"> 本描述主題描述 [連線到現有次要複本\]\*\*\** 頁面的選項。</span><span class="sxs-lookup"><span data-stu-id="b9aa8-103">This help topic describes the options of the **Connect to Existing Secondary Replicas** page.</span></span> <span data-ttu-id="b9aa8-104">本主題同時適用於 [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] 的 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 和 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b9aa8-104">This topic is used by the [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] and [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="b9aa8-105">**方格資料行：**</span><span class="sxs-lookup"><span data-stu-id="b9aa8-105">**Grid columns:**</span></span>  
 <span data-ttu-id="b9aa8-106">**伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="b9aa8-106">**Server Instance**</span></span>  
 <span data-ttu-id="b9aa8-107">顯示將裝載可用性複本的伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="b9aa8-107">Displays the name of the server instance that will host the availability replica.</span></span>  
  
 <span data-ttu-id="b9aa8-108">**連線方式**</span><span class="sxs-lookup"><span data-stu-id="b9aa8-108">**Connected As**</span></span>  
 <span data-ttu-id="b9aa8-109">顯示在建立連接後連接到伺服器執行個體的帳戶。</span><span class="sxs-lookup"><span data-stu-id="b9aa8-109">Displays the account that is connected to the server instance, once the connection has been established.</span></span> <span data-ttu-id="b9aa8-110">如果此資料行對於給定的伺服器執行個體顯示 [未連接]\*\*\*\*，您需要按一下 [連接]\*\*\*\* 或 [全部連接]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b9aa8-110">If this column displays "**Not Connected**" for a given server instance, you will need to click either the **Connect** or **Connect All** button.</span></span>  
  
 <span data-ttu-id="b9aa8-111">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="b9aa8-111">**Connect**</span></span>  
 <span data-ttu-id="b9aa8-112">如果這個伺服器執行個體是在與其他需要連接的伺服器執行個體不同的帳戶下執行，請按一下此按鈕。</span><span class="sxs-lookup"><span data-stu-id="b9aa8-112">Click if this server instance is running under a different account than other server instances to which you need to connect.</span></span>  
  
 <span data-ttu-id="b9aa8-113">**全部連接**</span><span class="sxs-lookup"><span data-stu-id="b9aa8-113">**Connect All**</span></span>  
 <span data-ttu-id="b9aa8-114">只有在每個需要連接的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體都是在相同使用者帳戶下以服務方式執行時，才按一下此按鈕。</span><span class="sxs-lookup"><span data-stu-id="b9aa8-114">Click only if every instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to which you need to connect is running as a service in the same user account.</span></span>  
  
 <span data-ttu-id="b9aa8-115">**取消**</span><span class="sxs-lookup"><span data-stu-id="b9aa8-115">**Cancel**</span></span>  
 <span data-ttu-id="b9aa8-116">按一下可取消精靈。</span><span class="sxs-lookup"><span data-stu-id="b9aa8-116">Click to cancel the wizard.</span></span> <span data-ttu-id="b9aa8-117">在 [連接到現有次要複本]\*\*\*\* 頁面上，取消精靈會導致精靈結束，而不執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="b9aa8-117">On the **Connect to Existing Secondary Replica** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b9aa8-118">相關工作</span><span class="sxs-lookup"><span data-stu-id="b9aa8-118">Related Tasks</span></span>  
  
-   <span data-ttu-id="b9aa8-119">[使用 [將複本加入可用性群組中精靈] &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="b9aa8-119">[Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="b9aa8-120">使用將資料庫加入至可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b9aa8-120">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="b9aa8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9aa8-121">See Also</span></span>  
 [<span data-ttu-id="b9aa8-122">AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;</span><span class="sxs-lookup"><span data-stu-id="b9aa8-122">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
