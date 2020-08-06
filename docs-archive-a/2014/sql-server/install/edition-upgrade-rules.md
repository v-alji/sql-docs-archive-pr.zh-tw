---
title: 版本升級規則 |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 77c4d751-4fea-4e69-a7c8-ab8fc0dbadb2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 453944ede41bfc5cf258c6f0946b15b716c6c22c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595479"
---
# <a name="edition-upgrade-rules"></a><span data-ttu-id="5fc54-102">版本升級規則</span><span class="sxs-lookup"><span data-stu-id="5fc54-102">Edition Upgrade Rules</span></span>
  <span data-ttu-id="5fc54-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式的作業完成之前，此安裝程式會驗證您的電腦組態。</span><span class="sxs-lookup"><span data-stu-id="5fc54-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup validates your computer configuration before the Setup operation completes.</span></span> <span data-ttu-id="5fc54-104">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝期間，System Configuration Checker (SCC) 會掃描將安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的電腦。</span><span class="sxs-lookup"><span data-stu-id="5fc54-104">During [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, the System Configuration Checker (SCC) scans the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be installed.</span></span> <span data-ttu-id="5fc54-105">SCC 會檢查是否有任何狀況阻止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝作業成功。</span><span class="sxs-lookup"><span data-stu-id="5fc54-105">The SCC checks for conditions that prevent a successful [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup operation.</span></span> <span data-ttu-id="5fc54-106">在安裝程式開始進行版本升級之前，SCC 會擷取每一個項目的狀態。</span><span class="sxs-lookup"><span data-stu-id="5fc54-106">Before Setup starts the edition upgrade, the SCC retrieves the status of each item.</span></span> <span data-ttu-id="5fc54-107">然後它會比較所需條件的結果，並提供解決封鎖問題的指引。</span><span class="sxs-lookup"><span data-stu-id="5fc54-107">It then compares the result with required conditions and provides guidance for removal of blocking issues.</span></span>  
  
 <span data-ttu-id="5fc54-108">系統組態檢查會產生報告，其中包含每個已執行規則以及執行狀態的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="5fc54-108">The system configuration check generates a report which contains a short description for each executed rule, and the execution status.</span></span> <span data-ttu-id="5fc54-109">系統組態檢查報告位於% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="5fc54-109">The system configuration check report is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
 <span data-ttu-id="5fc54-110">執行安裝作業之前，請檢閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="5fc54-110">Before you run the setup operation, review the following topics:</span></span>  
  
1.  [<span data-ttu-id="5fc54-111">安裝 SQL Server 2014 的硬體與軟體需求</span><span class="sxs-lookup"><span data-stu-id="5fc54-111">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [<span data-ttu-id="5fc54-112">SQL Server 2014 各版本所支援的功能</span><span class="sxs-lookup"><span data-stu-id="5fc54-112">Features Supported by the Editions of SQL Server 2014</span></span>](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [<span data-ttu-id="5fc54-113">SQL Server 安裝的安全性考量</span><span class="sxs-lookup"><span data-stu-id="5fc54-113">Security Considerations for a SQL Server Installation</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [<span data-ttu-id="5fc54-114">SQL Server 中的地區語言版本</span><span class="sxs-lookup"><span data-stu-id="5fc54-114">Local Language Versions in SQL Server</span></span>](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 <span data-ttu-id="5fc54-115">其他參考資料：</span><span class="sxs-lookup"><span data-stu-id="5fc54-115">Other references:</span></span>  
  
1.  [<span data-ttu-id="5fc54-116">支援的版本與版本升級</span><span class="sxs-lookup"><span data-stu-id="5fc54-116">Supported Version and Edition Upgrades</span></span>](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [<span data-ttu-id="5fc54-117">安裝容錯移轉叢集之前</span><span class="sxs-lookup"><span data-stu-id="5fc54-117">Before Installing Failover Clustering</span></span>](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="see-also"></a><span data-ttu-id="5fc54-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fc54-118">See Also</span></span>  
 [<span data-ttu-id="5fc54-119">安裝規則</span><span class="sxs-lookup"><span data-stu-id="5fc54-119">Install Rules</span></span>](../../../2014/sql-server/install/install-rules.md)  
  
  
