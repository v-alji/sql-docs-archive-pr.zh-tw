---
title: 設定公用程式控制點資料倉儲 (SQL Server 公用程式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 60b9623b468f2763cf619c325412373e3603f3a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592692"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a><span data-ttu-id="1e6d9-102">設定公用程式控制點資料倉儲 (SQL Server 公用程式)</span><span class="sxs-lookup"><span data-stu-id="1e6d9-102">Configure Your Utility Control Point Data Warehouse (SQL Server Utility)</span></span>
  <span data-ttu-id="1e6d9-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 Managed 執行個體所收集的資料會儲存在公用程式管理資料倉儲 (UMDW) 中；UMDW 檔案名稱為 sysutility_mdw。</span><span class="sxs-lookup"><span data-stu-id="1e6d9-103">Data collected by managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are stored in the utility management data warehouse (UMDW); the UMDW file name is sysutility_mdw.</span></span>  
  
 <span data-ttu-id="1e6d9-104">您可以設定 UMDW 資料保留週期。</span><span class="sxs-lookup"><span data-stu-id="1e6d9-104">You can configure the UMDW data retention period.</span></span> <span data-ttu-id="1e6d9-105">如需詳細資訊，請參閱[公用程式管理 &#40;SQL Server 公用程式&#41;](../../database-engine/utility-administration-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="1e6d9-105">For more information, see [Utility Administration &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="1e6d9-106">這一版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]無法設定下列組態設定：</span><span class="sxs-lookup"><span data-stu-id="1e6d9-106">The following configuration settings are not configurable in this release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="1e6d9-107">UMDW 名稱：Sysutility_mdw。</span><span class="sxs-lookup"><span data-stu-id="1e6d9-107">UMDW name: Sysutility_mdw.</span></span>  
  
-   <span data-ttu-id="1e6d9-108">收集組上傳頻率：每隔 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="1e6d9-108">Collection set upload frequency: Every 15 minutes.</span></span>  
  
 <span data-ttu-id="1e6d9-109">UMDW 目錄是可設定的：\<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP 名稱>\MSSQL\Data\\，其中 \<System drive> 通常是 C:\ 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="1e6d9-109">The UMDW directory is configurable: \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, where \<System drive> is normally the C:\ drive.</span></span> <span data-ttu-id="1e6d9-110">記錄檔 Sysutility_mdw_\<GUID>_LOG 位於相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="1e6d9-110">The log file, Sysutility_mdw_\<GUID>_LOG, is located in the same directory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e6d9-111">可以使用卸離/附加或 ALTER DATABASE 來變更 UMDW (sysutility_mdw) 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="1e6d9-111">The UMDW (sysutility_mdw) file location can be changed using detach/attach or ALTER DATABASE.</span></span> <span data-ttu-id="1e6d9-112">我們建議使用 ALTER DATABASE。</span><span class="sxs-lookup"><span data-stu-id="1e6d9-112">We recommend the use of ALTER DATABASE.</span></span> <span data-ttu-id="1e6d9-113">如需詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1e6d9-113">For more information see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e6d9-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e6d9-114">See Also</span></span>  
 [<span data-ttu-id="1e6d9-115">SQL Server 公用程式的功能與工作</span><span class="sxs-lookup"><span data-stu-id="1e6d9-115">SQL Server Utility Features and Tasks</span></span>](sql-server-utility-features-and-tasks.md)  
  
  
