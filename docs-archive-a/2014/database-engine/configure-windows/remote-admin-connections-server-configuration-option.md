---
title: 遠端管理員連接伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- administrator connections [SQL Server]
- DAC
- connections [SQL Server], dedicated administrator
- remote admin connections option
- dedicated administrator connections [SQL Server]
ms.assetid: bf32b60a-7a48-401f-b6be-b5e2e46c413f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c17cf278d18444c5b93d4f4b7e0a3da8dbfb671e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599176"
---
# <a name="remote-admin-connections-server-configuration-option"></a><span data-ttu-id="01f8b-102">遠端管理員連接伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="01f8b-102">remote admin connections Server Configuration Option</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="01f8b-103">會提供專用管理員連接 (DAC)。</span><span class="sxs-lookup"><span data-stu-id="01f8b-103">provides a dedicated administrator connection (DAC).</span></span> <span data-ttu-id="01f8b-104">DAC 可讓系統管理員存取執行中的伺服器，如此一來，即使伺服器遭到鎖定或在異常狀態下執行，而且未回應 [!INCLUDE[tsql](../../includes/tsql-md.md)] 連接時，也能執行診斷功能或 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 陳述式，或針對伺服器上的問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="01f8b-104">The DAC lets an administrator access a running server to execute diagnostic functions or [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, or to troubleshoot problems on the server, even when the server is locked or running in an abnormal state and not responding to a [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] connection.</span></span> <span data-ttu-id="01f8b-105">依預設，只能從伺服器上的用戶端使用 DAC。</span><span class="sxs-lookup"><span data-stu-id="01f8b-105">By default, the DAC is only available from a client on the server.</span></span> <span data-ttu-id="01f8b-106">若要讓遠端電腦上的用戶端應用程式使用 DAC，請使用 sp_configure 的 remote admin connections 選項。</span><span class="sxs-lookup"><span data-stu-id="01f8b-106">To enable client applications on remote computers to use the DAC, use the remote admin connections option of sp_configure.</span></span>  
  
 <span data-ttu-id="01f8b-107">根據預設，DAC 只會接聽回送 IP 位址 (127.0.0.1)、通訊埠 1434。</span><span class="sxs-lookup"><span data-stu-id="01f8b-107">By default, the DAC only listens on the loop-back IP address (127.0.0.1), port 1434.</span></span> <span data-ttu-id="01f8b-108">如果無法使用 TCP 通訊埠 1434，當 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 啟動時，會自動指派 TCP 通訊埠。</span><span class="sxs-lookup"><span data-stu-id="01f8b-108">If TCP port 1434 is not available, a TCP port is dynamically assigned when the [!INCLUDE[ssDE](../../includes/ssde-md.md)] starts up.</span></span> <span data-ttu-id="01f8b-109">在電腦上安裝多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，請檢查錯誤記錄檔以取得 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="01f8b-109">When more than one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a computer, check the error log for the TCP port number.</span></span>  
  
 <span data-ttu-id="01f8b-110">下表列出 remote admin connections 選項的可能值。</span><span class="sxs-lookup"><span data-stu-id="01f8b-110">The following table lists the possible values for the remote admin connections option.</span></span>  
  
|<span data-ttu-id="01f8b-111">值</span><span class="sxs-lookup"><span data-stu-id="01f8b-111">Value</span></span>|<span data-ttu-id="01f8b-112">描述</span><span class="sxs-lookup"><span data-stu-id="01f8b-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="01f8b-113">0</span><span class="sxs-lookup"><span data-stu-id="01f8b-113">0</span></span>|<span data-ttu-id="01f8b-114">表示只允許使用 DAC 的本機連接。</span><span class="sxs-lookup"><span data-stu-id="01f8b-114">Indicates only local connections are allowed by using the DAC.</span></span>|  
|<span data-ttu-id="01f8b-115">1</span><span class="sxs-lookup"><span data-stu-id="01f8b-115">1</span></span>|<span data-ttu-id="01f8b-116">表示允許使用 DAC 的遠端連接。</span><span class="sxs-lookup"><span data-stu-id="01f8b-116">Indicates remote connections are allowed by using the DAC.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="01f8b-117">範例</span><span class="sxs-lookup"><span data-stu-id="01f8b-117">Example</span></span>  
 <span data-ttu-id="01f8b-118">下列範例會從遠端電腦啟用 DAC。</span><span class="sxs-lookup"><span data-stu-id="01f8b-118">The following example enables the DAC from a remote computer.</span></span>  
  
```  
sp_configure 'remote admin connections', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="01f8b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01f8b-119">See Also</span></span>  
 [<span data-ttu-id="01f8b-120">資料庫管理員的診斷連接</span><span class="sxs-lookup"><span data-stu-id="01f8b-120">Diagnostic Connection for Database Administrators</span></span>](diagnostic-connection-for-database-administrators.md)  
  
  
