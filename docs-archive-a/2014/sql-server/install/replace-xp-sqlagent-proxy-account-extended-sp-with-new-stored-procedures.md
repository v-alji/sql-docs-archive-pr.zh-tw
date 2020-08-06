---
title: 以新的預存程式取代 xp_sqlagent_proxy_account 擴充預存程式的用法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- xp_sqlagent_proxy_account
ms.assetid: 0e3cc931-6237-41dd-bf0d-0c03f4d8fff2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d124ab73f4b4315550134f28ffad232b4a1c0ec2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598139"
---
# <a name="replace-usage-of-the-xp_sqlagent_proxy_account-extended-stored-procedure-with-new-stored-procedures"></a><span data-ttu-id="b8da2-102">使用新的預存程序取代 xp_sqlagent_proxy_account 擴充預存程序的使用方式</span><span class="sxs-lookup"><span data-stu-id="b8da2-102">Replace usage of the xp_sqlagent_proxy_account extended stored procedure with new stored procedures</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b8da2-103">Agent 支援多個 Proxy。</span><span class="sxs-lookup"><span data-stu-id="b8da2-103">Agent supports multiple proxies.</span></span> <span data-ttu-id="b8da2-104">您可以使用一組新的預存程序定義這些 Proxy。</span><span class="sxs-lookup"><span data-stu-id="b8da2-104">You define these proxies by using a new set of stored procedures.</span></span> <span data-ttu-id="b8da2-105">如需有關新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 預存程序的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的下列主題：</span><span class="sxs-lookup"><span data-stu-id="b8da2-105">For more information about the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stored procedures, see the following topics in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online:</span></span>  
  
-   <span data-ttu-id="b8da2-106">＜sp_add_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞</span><span class="sxs-lookup"><span data-stu-id="b8da2-106">"sp_add_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="b8da2-107">＜sp_delete_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞</span><span class="sxs-lookup"><span data-stu-id="b8da2-107">"sp_delete_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="b8da2-108">＜sp_enum_login_for_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞</span><span class="sxs-lookup"><span data-stu-id="b8da2-108">"sp_enum_login_for_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="b8da2-109">＜sp_enum_proxy_for_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞</span><span class="sxs-lookup"><span data-stu-id="b8da2-109">"sp_enum_proxy_for_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="b8da2-110">＜sp_enum_sqlagent_subsystems ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞</span><span class="sxs-lookup"><span data-stu-id="b8da2-110">"sp_enum_sqlagent_subsystems ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="b8da2-111">＜sp_grant_proxy_to_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞</span><span class="sxs-lookup"><span data-stu-id="b8da2-111">"sp_grant_proxy_to_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="b8da2-112">＜sp_grant_login_to_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞</span><span class="sxs-lookup"><span data-stu-id="b8da2-112">"sp_grant_login_to_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="b8da2-113">＜sp_help_proxy" ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞</span><span class="sxs-lookup"><span data-stu-id="b8da2-113">"sp_help_proxy" ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="b8da2-114">＜sp_revoke_login_from_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞</span><span class="sxs-lookup"><span data-stu-id="b8da2-114">"sp_revoke_login_from_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="b8da2-115">＜sp_revoke_proxy_from_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞</span><span class="sxs-lookup"><span data-stu-id="b8da2-115">"sp_revoke_proxy_from_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="b8da2-116">＜sp_update_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞</span><span class="sxs-lookup"><span data-stu-id="b8da2-116">"sp_update_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8da2-117">升級至之後 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ，任何使用**xp_sqlagent_proxy_account**擴充預存程式的語句都將無法使用。</span><span class="sxs-lookup"><span data-stu-id="b8da2-117">After you upgrade to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], any statements that use the **xp_sqlagent_proxy_account** extended stored procedure will not work.</span></span> <span data-ttu-id="b8da2-118">使用**sp_xp_cmdshell_proxy_account**而不是**xp_sqlagent_proxy_account**來設定**xp_cmdshell**的 proxy。</span><span class="sxs-lookup"><span data-stu-id="b8da2-118">Use **sp_xp_cmdshell_proxy_account** instead of **xp_sqlagent_proxy_account** to set the proxy for **xp_cmdshell**.</span></span>  
  
## <a name="component"></a><span data-ttu-id="b8da2-119">元件</span><span class="sxs-lookup"><span data-stu-id="b8da2-119">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b8da2-120">Agent</span><span class="sxs-lookup"><span data-stu-id="b8da2-120">Agent</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8da2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8da2-121">See Also</span></span>  
 [<span data-ttu-id="b8da2-122">SQL Server Agent 升級問題</span><span class="sxs-lookup"><span data-stu-id="b8da2-122">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
