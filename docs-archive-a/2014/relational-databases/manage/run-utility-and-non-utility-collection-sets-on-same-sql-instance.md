---
title: SQL Server 的相同實例上執行公用程式和非公用程式收集組的考慮 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ca7ee9b3-ef9a-4ba4-83d0-9ee9f80dab27
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67df2d65cc9da4026377e77c152c0d78f3749932
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597113"
---
# <a name="considerations-for-running-utility-and-non-utility-collection-sets-on-the-same-instance-of-sql-server"></a><span data-ttu-id="ee63a-102">在相同 SQL Server 執行個體上執行公用程式和非公用程式收集組的考量事項</span><span class="sxs-lookup"><span data-stu-id="ee63a-102">Considerations for Running Utility and non-Utility Collection Sets on the Same Instance of SQL Server</span></span>
  <span data-ttu-id="ee63a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式收集組與非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式收集組會一起受到支援。</span><span class="sxs-lookup"><span data-stu-id="ee63a-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection set is supported side-by-side with non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection sets.</span></span> <span data-ttu-id="ee63a-104">也就是說，當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 Managed 執行個體為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式的成員時，可以受到其他收集組的監視。</span><span class="sxs-lookup"><span data-stu-id="ee63a-104">That is, a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be monitored by other collection sets while it is a member of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="ee63a-105">但是，當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體註冊到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式時，您必須停用非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式資料收集功能。</span><span class="sxs-lookup"><span data-stu-id="ee63a-105">However, you must disable non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility data collection functionality while the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is being enrolled into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
 <span data-ttu-id="ee63a-106">當使用 UCP 註冊此執行個體之後，您必須重新啟動非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式收集組。</span><span class="sxs-lookup"><span data-stu-id="ee63a-106">After the instance is enrolled with the UCP, you can restart non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection sets.</span></span> <span data-ttu-id="ee63a-107">但是請注意，Managed 執行個體上的所有收集組都會將其資料上傳到公用程式管理資料倉儲 (UMDW)；UMDW 檔案名稱為 sysutility_mdw。</span><span class="sxs-lookup"><span data-stu-id="ee63a-107">Note, however, that all collection sets on the managed instance will upload their data to the utility management data warehouse (UMDW); the UMDW file name is sysutility_mdw.</span></span>  
  
 <span data-ttu-id="ee63a-108">若要將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式收集組與非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式收集組並存執行，請考量以下幾點：</span><span class="sxs-lookup"><span data-stu-id="ee63a-108">To run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection sets side-by-side with non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection sets, consider the following points:</span></span>  
  
-   <span data-ttu-id="ee63a-109">並存的收集組有受到支援。</span><span class="sxs-lookup"><span data-stu-id="ee63a-109">Side-by-side collection sets are supported.</span></span>  
  
-   <span data-ttu-id="ee63a-110">將執行個體註冊到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式時，您必須停用現有的資料收集器。</span><span class="sxs-lookup"><span data-stu-id="ee63a-110">You must disable existing data collectors while enrolling instances into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
-   <span data-ttu-id="ee63a-111">若要通過驗證需求，當您建立 UCP 之前，您必須在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上執行下列預存程序，而將它註冊到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式之前，必須在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上：</span><span class="sxs-lookup"><span data-stu-id="ee63a-111">To pass validation requirements, you must run the following stored procedures on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you create a UCP, and on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you enroll it into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility:</span></span>  
  
    ```  
    exec msdb.dbo.sp_syscollector_set_warehouse_database_name NULL  
    exec msdb.dbo.sp_syscollector_set_warehouse_instance_name NULL  
    ```  
  
     <span data-ttu-id="ee63a-112">如果在您啟動建立 UCP 精靈或新增 Managed 執行個體精靈之前並未執行這些預存程序，此作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="ee63a-112">If you do not run these stored procedures before you launch the Create UCP Wizard or Add Managed Instance Wizard, the operation will fail.</span></span>  
  
-   <span data-ttu-id="ee63a-113">您必須針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Managed 執行個體上的所有收集組使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]公用程式 UMDW (sysutility_mdw)。</span><span class="sxs-lookup"><span data-stu-id="ee63a-113">You must use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility UMDW (sysutility_mdw) for all collection sets on a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee63a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee63a-114">See Also</span></span>  
 <span data-ttu-id="ee63a-115">[SQL Server 公用程式的功能與工作](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="ee63a-115">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="ee63a-116">設定公用程式控制點資料倉儲 &#40;SQL Server 公用程式&#41;</span><span class="sxs-lookup"><span data-stu-id="ee63a-116">Configure Your Utility Control Point Data Warehouse &#40;SQL Server Utility&#41;</span></span>](configure-your-utility-control-point-data-warehouse-sql-server-utility.md)  
  
  
