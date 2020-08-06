---
title: 只有系統管理員（sysadmin）使用者可以將作業步驟記錄檔寫入檔案系統 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9e2bf5095ac1e6b67f6c6f3f87444879913916e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596450"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a><span data-ttu-id="5b6bf-102">只有系統管理員 (sysadmin) 使用者可以將作業步驟記錄檔寫入檔案系統</span><span class="sxs-lookup"><span data-stu-id="5b6bf-102">Only sysadmin users can write job step log files to the file system</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="5b6bf-103">會選擇性地為每個作業步驟寫入記錄。</span><span class="sxs-lookup"><span data-stu-id="5b6bf-103">optionally writes a log for each job step.</span></span>  
  
## <a name="component"></a><span data-ttu-id="5b6bf-104">元件</span><span class="sxs-lookup"><span data-stu-id="5b6bf-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5b6bf-105">Agent</span><span class="sxs-lookup"><span data-stu-id="5b6bf-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="5b6bf-106">描述</span><span class="sxs-lookup"><span data-stu-id="5b6bf-106">Description</span></span>  
 <span data-ttu-id="5b6bf-107">在中 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 可以針對系統**管理員（sysadmin** ）固定伺服器角色的成員所擁有的作業，將記錄寫入檔案系統。</span><span class="sxs-lookup"><span data-stu-id="5b6bf-107">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write logs to the file system for jobs that are owned by members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="5b6bf-108">如果作業擁有者不是**系統管理員（sysadmin** ）角色的成員，而且 proxy 帳戶已啟用， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 就可以使用 proxy 帳戶的認證，將記錄寫入檔案系統。</span><span class="sxs-lookup"><span data-stu-id="5b6bf-108">If the job owner is not a member of the **sysadmin** role and if the proxy account is enabled, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write logs to the file system by using the credentials of the proxy account.</span></span>  
  
 <span data-ttu-id="5b6bf-109">升級之後，不是**系統管理員（sysadmin** ）固定伺服器角色成員之使用者所擁有的作業，就無法再將記錄寫入檔案系統。</span><span class="sxs-lookup"><span data-stu-id="5b6bf-109">After you upgrade, jobs that are owned by users who are not members of the **sysadmin** fixed server role can no longer write logs to the file system.</span></span> <span data-ttu-id="5b6bf-110">相反地，這些使用者可以選取選項，將其記錄寫入**msdb**資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="5b6bf-110">Instead, these users can select the option to write their logs to a table in the **msdb** database.</span></span> <span data-ttu-id="5b6bf-111">**系統管理員（sysadmin** ）角色的成員仍然可以將記錄檔寫入檔案系統。</span><span class="sxs-lookup"><span data-stu-id="5b6bf-111">Members of the **sysadmin** role can still write log files to the file system.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="5b6bf-112">更正動作</span><span class="sxs-lookup"><span data-stu-id="5b6bf-112">Corrective Action</span></span>  
 <span data-ttu-id="5b6bf-113">升級之後，不屬於**系統管理員（sysadmin** ）角色成員的使用者所擁有的工作將會繼續執行，但不會建立記錄。</span><span class="sxs-lookup"><span data-stu-id="5b6bf-113">After you upgrade, jobs that are owned by users who are not members of the **sysadmin** role will continue to run, but logs will not be created.</span></span> <span data-ttu-id="5b6bf-114">若要將作業步驟記錄到資料表，非**系統管理員（sysadmin** ）角色成員的使用者必須手動更新其作業。</span><span class="sxs-lookup"><span data-stu-id="5b6bf-114">To log job steps to a table, users who are not members of the **sysadmin** role must manually update their jobs.</span></span>  
  
 <span data-ttu-id="5b6bf-115">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜建立作業＞、＜建立作業步驟＞和＜處理多個作業步驟＞主題。</span><span class="sxs-lookup"><span data-stu-id="5b6bf-115">For more information, see the topics "Creating Jobs," "Creating Job Steps," and "Handling Multiple Job Steps" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b6bf-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b6bf-116">See Also</span></span>  
 [<span data-ttu-id="5b6bf-117">SQL Server Agent 升級問題</span><span class="sxs-lookup"><span data-stu-id="5b6bf-117">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
