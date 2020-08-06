---
title: 功能審查 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 1e2b22b8-5811-4f50-875b-685f3ddbd1ee
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8e258ac763d8c5e057f8dcdb6f740aacb4fef1c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598182"
---
# <a name="feature-review"></a><span data-ttu-id="d69df-102">功能檢閱</span><span class="sxs-lookup"><span data-stu-id="d69df-102">Feature Review</span></span>
  <span data-ttu-id="d69df-103">[功能檢閱] 頁面是一份唯讀的功能清單，其中列出已經備妥而且將在完成映像步驟結束時設定並完成的功能。</span><span class="sxs-lookup"><span data-stu-id="d69df-103">The Feature Review page is a read-only list of features that have been prepared and will be configured and completed at the end of the complete image step.</span></span> <span data-ttu-id="d69df-104">此功能清單是在準備映像步驟期間選取，而且無法在完成映像步驟期間修改。</span><span class="sxs-lookup"><span data-stu-id="d69df-104">The feature list is selected during the prepare image step and cannot be modified during complete image step.</span></span> <span data-ttu-id="d69df-105">除了所顯示的功能以外，備妥的執行個體也會包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Writer 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="d69df-105">In addition to the features displayed, a prepared instance also includes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Writer, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="d69df-106">在您已經完成備妥 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的設定之後，就可以新增備妥 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中並未包含的其他功能。</span><span class="sxs-lookup"><span data-stu-id="d69df-106">You can add other features not included in the prepared instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance after you have completed the configuration of the prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="d69df-107">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="d69df-107">UI element list</span></span>  
  
|<span data-ttu-id="d69df-108">元件群組</span><span class="sxs-lookup"><span data-stu-id="d69df-108">Component Group</span></span>|<span data-ttu-id="d69df-109">元件和功能</span><span class="sxs-lookup"><span data-stu-id="d69df-109">Components and features</span></span>|  
|---------------------|-----------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="d69df-110">服務</span><span class="sxs-lookup"><span data-stu-id="d69df-110">Services</span></span>|<span data-ttu-id="d69df-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 是用來儲存、處理和保護資料安全的核心服務。</span><span class="sxs-lookup"><span data-stu-id="d69df-111">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] is the core service for storing, processing, and securing data.</span></span> <span data-ttu-id="d69df-112">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 包含以下元件：</span><span class="sxs-lookup"><span data-stu-id="d69df-112">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] includes the following components:</span></span><br /><br /> <span data-ttu-id="d69df-113">複寫：(選擇性) 複寫是一組技術，用於將資料和資料庫物件從某個資料庫複製和散發到另一個資料庫，然後在兩個資料庫之間進行同步處理以維護一致性。</span><span class="sxs-lookup"><span data-stu-id="d69df-113">Replication: (Optional) Replication is a set of technologies for copying and distributing data and database objects from one database to another and then synchronizing between databases to maintain consistency.</span></span><br /><br /> <span data-ttu-id="d69df-114">全文檢索搜尋：(選擇性) 全文檢索搜尋提供一種功能，可針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中一般以字元為主的資料發出全文檢索查詢。</span><span class="sxs-lookup"><span data-stu-id="d69df-114">Full-Text Search: (Optional) Full-Text Search provides functionality to issue full-text queries against plain character-based data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span><br /><br /> [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]<span data-ttu-id="d69df-115">：選擇性：[!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) 是一種資料清除方案，可讓您在資料來源中探索不一致和不正確的資料，並提供可清除資料的自動化和互動方式。</span><span class="sxs-lookup"><span data-stu-id="d69df-115">(Optional): [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) is a data-cleansing solution that enables you to discover inconsistent and incorrect data in your data source, and provides automated and interactive ways to cleanse the data.</span></span>|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="d69df-116">包括伺服器和用戶端元件，可用來建立、管理和部署表格式、矩陣、圖形化和自由形式報表。</span><span class="sxs-lookup"><span data-stu-id="d69df-116">includes server and client components for creating, managing, and deploying tabular, matrix, graphical, and free-form reports.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="d69df-117">也是一個可延伸的平台，可讓您用來開發報表應用程式。</span><span class="sxs-lookup"><span data-stu-id="d69df-117">is also an extensible platform that you can use to develop report applications.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d69df-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d69df-118">See Also</span></span>  
 [<span data-ttu-id="d69df-119">使用 SysPrep 安裝 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="d69df-119">Install SQL Server 2014 Using SysPrep</span></span>](../../database-engine/install-windows/install-sql-server-using-sysprep.md)  
  
  
