---
title: 針對使用 Proxy 的多伺服器作業進行疑難排解 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
author: stevestein
ms.author: sstein
ms.openlocfilehash: 19de975ef5e1f22c93cec72a5014a01da5b03dd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699148"
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a><span data-ttu-id="262e0-102">針對使用 Proxy 的多伺服器作業進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="262e0-102">Troubleshoot Multiserver Jobs That Use Proxies</span></span>
  <span data-ttu-id="262e0-103">這是在目標伺服器上，於 Proxy 帳戶的環境下執行 Proxy 之相關聯步驟的散發式作業。</span><span class="sxs-lookup"><span data-stu-id="262e0-103">Distributed jobs whose steps are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="262e0-104">如果使用 Proxy 帳戶從主要伺服器下載的作業步驟失敗，請在 **msdb** 資料庫的 **sysdownloadlist** 資料表中，檢查 **error_message** 資料行，以了解下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="262e0-104">If job steps that use proxy accounts fail when downloaded from the master server, check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="262e0-105">「作業步驟需要 Proxy 帳戶，不過目標伺服器上已停用 Proxy 比對。」</span><span class="sxs-lookup"><span data-stu-id="262e0-105">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span>  
  
     <span data-ttu-id="262e0-106">若要解決此錯誤，請設定**\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT\MICROSOFT SQL Server\MSSQL.**_ \SQLServerAgent\AllowDownloadedJobsToMatchProxyName 登錄子機碼 \<n_> **\SQLServerAgent\AllowDownloadedJobsToMatchProxyName**為\*\*1 (true) \*\*。</span><span class="sxs-lookup"><span data-stu-id="262e0-106">To resolve this error, set the **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.**_\<n_>**\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** registry subkey to **1 (true)**.</span></span> <span data-ttu-id="262e0-107">根據預設，此子機碼設定為**0** (`false`) 。</span><span class="sxs-lookup"><span data-stu-id="262e0-107">By default, this subkey is set to **0** (`false`).</span></span> <span data-ttu-id="262e0-108">MSSQL 的值 **。**\<*n*></span><span class="sxs-lookup"><span data-stu-id="262e0-108">The value of **MSSQL.**\<*n*></span></span> <span data-ttu-id="262e0-109">這是實例名稱;例如， **mssql. 1**或**mssql. 3**。</span><span class="sxs-lookup"><span data-stu-id="262e0-109">is the instance name; for example, **MSSQL.1** or **MSSQL.3**.</span></span>  
  
-   <span data-ttu-id="262e0-110">「找不到 Proxy。」</span><span class="sxs-lookup"><span data-stu-id="262e0-110">"Proxy not found."</span></span>  
  
     <span data-ttu-id="262e0-111">若要解決此錯誤，請確定目標伺服器上有 Proxy 帳戶，且帳戶名稱與執行該作業步驟的主要伺服器 Proxy 帳戶相同。</span><span class="sxs-lookup"><span data-stu-id="262e0-111">To resolve this error, make sure a proxy account exists on the target server with the same name as the master server proxy account under which the job step runs.</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="262e0-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="262e0-112">See Also</span></span>  
 [<span data-ttu-id="262e0-113">建立多伺服器環境</span><span class="sxs-lookup"><span data-stu-id="262e0-113">Create a Multiserver Environment</span></span>](create-a-multiserver-environment.md)  
  
  
