---
title: 確認升級程式期間，壓縮的磁片磁碟機上沒有任何資料庫檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- compressed drives [SQL Server]
ms.assetid: 63be6853-c54a-42b2-ae1a-db2175f1d28e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9c04f7890ba8d8efe64afaf11b922af156c5de46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585763"
---
# <a name="verify-that-no-database-files-are-on-compressed-drives-during-the-upgrade-process"></a><span data-ttu-id="bd585-102">確認在升級過程中，壓縮磁碟機上沒有資料庫檔案</span><span class="sxs-lookup"><span data-stu-id="bd585-102">Verify that no database files are on compressed drives during the upgrade process</span></span>
  <span data-ttu-id="bd585-103">Upgrade Advisor 在壓縮磁碟機上偵測到資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="bd585-103">Upgrade Advisor detected database files on a compressed drive.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bd585-104">不能在壓縮磁碟機上建立或升級資料庫。</span><span class="sxs-lookup"><span data-stu-id="bd585-104">cannot create or upgrade databases on compressed drives.</span></span>  
  
## <a name="component"></a><span data-ttu-id="bd585-105">元件</span><span class="sxs-lookup"><span data-stu-id="bd585-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="bd585-106">更正動作</span><span class="sxs-lookup"><span data-stu-id="bd585-106">Corrective Action</span></span>  
 <span data-ttu-id="bd585-107">當您安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，請為系統資料庫選取未壓縮磁碟機，並確認要升級的資料庫不在壓縮磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="bd585-107">When you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], select an uncompressed drive for system databases and verify that databases to be upgraded are not on compressed drives.</span></span> <span data-ttu-id="bd585-108">不過請注意，在資料庫升級之後，您可以在 NTFS 壓縮檔案系統上放置唯讀資料庫和唯讀次要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="bd585-108">However, note that after the database has been upgraded, you can put read-only databases and read-only secondary filegroups on an NTFS compressed file system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd585-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd585-109">See Also</span></span>  
 <span data-ttu-id="bd585-110">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="bd585-110">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="bd585-111">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="bd585-111">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
