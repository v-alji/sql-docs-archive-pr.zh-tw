---
title: 使用中央管理伺服器管理多部伺服器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- central management server
- multiserver administration [SQL Server]
- master servers [SQL Server], central management servers
- target configuration [SQL Server]
- server configuration [SQL Server]
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3906165b595f6faa15812f70377a3bc0f550e52e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699838"
---
# <a name="administer-multiple-servers-using-central-management-servers"></a><span data-ttu-id="c7f8c-102">使用中央管理伺服器管理多部伺服器</span><span class="sxs-lookup"><span data-stu-id="c7f8c-102">Administer Multiple Servers Using Central Management Servers</span></span>
  <span data-ttu-id="c7f8c-103">您可以透過指定中央管理伺服器並建立伺服器群組來管理多部伺服器。</span><span class="sxs-lookup"><span data-stu-id="c7f8c-103">You can administer multiple servers by designating Central Management Servers and creating server groups.</span></span>  
  
## <a name="benefits-of-central-management-servers-and-server-groups"></a><span data-ttu-id="c7f8c-104">中央管理伺服器和伺服器群組的優點</span><span class="sxs-lookup"><span data-stu-id="c7f8c-104">Benefits of Central Management Servers and Server Groups</span></span>  
 <span data-ttu-id="c7f8c-105">指定為中央管理伺服器的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體，會針對一個或多個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體維護含有連接資訊的伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="c7f8c-105">An instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that is designated as a Central Management Server maintains server groups that contain the connection information for one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c7f8c-106">您可以針對伺服器群組同時執行 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式和以原則為基礎的管理原則。</span><span class="sxs-lookup"><span data-stu-id="c7f8c-106">[!INCLUDE[tsql](../includes/tsql-md.md)] statements and Policy-Based Management policies can be executed at the same time against server groups.</span></span> <span data-ttu-id="c7f8c-107">您也可以在透過中央管理伺服器所管理的執行個體上檢視 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c7f8c-107">You can also view the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] log files on instances that are managed through a Central Management Server.</span></span> <span data-ttu-id="c7f8c-108">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 版本無法指定為中央管理伺服器。</span><span class="sxs-lookup"><span data-stu-id="c7f8c-108">Versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] cannot be designated as a Central Management Server.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="c7f8c-109">陳述式。</span><span class="sxs-lookup"><span data-stu-id="c7f8c-109">statements can also be executed against local server groups in Registered Servers.</span></span>  
  
### <a name="related-tasks"></a><span data-ttu-id="c7f8c-110">相關工作</span><span class="sxs-lookup"><span data-stu-id="c7f8c-110">Related Tasks</span></span>  
 <span data-ttu-id="c7f8c-111">若要建立中央管理伺服器和伺服器群組，請使用 **中的** [已註冊的伺服器] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]視窗。</span><span class="sxs-lookup"><span data-stu-id="c7f8c-111">To create a Central Management Server and server groups, use the **Registered Servers** window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c7f8c-112">請注意，中央管理伺服器不可以是它所維護之群組的成員。</span><span class="sxs-lookup"><span data-stu-id="c7f8c-112">Note that the Central Management Server cannot be a member of a group that it maintains.</span></span> <span data-ttu-id="c7f8c-113">如需如何建立中央管理伺服器和伺服器群組的詳細資訊，請參閱[建立中央管理伺服器和伺服器群組 &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)。</span><span class="sxs-lookup"><span data-stu-id="c7f8c-113">For more information about how to create Central Management Servers and server groups, see [Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f8c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7f8c-114">See Also</span></span>  
 [<span data-ttu-id="c7f8c-115">使用原則式管理來管理伺服器</span><span class="sxs-lookup"><span data-stu-id="c7f8c-115">Administer Servers by Using Policy-Based Management</span></span>](policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
