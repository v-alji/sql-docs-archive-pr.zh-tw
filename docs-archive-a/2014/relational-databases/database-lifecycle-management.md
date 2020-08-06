---
title: 資料庫生命週期管理 (DLM) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Data sync
- SQL Database
- Azure Training Kit
- Database development
- Database backup
- Database connection management
- Database community
- Backup and restore
- Database import and export
- SQL Data Sync
- Azure Service Dashboard
- SQL Server Management Studio
- Database management
- Database export
- SQL Server Data Tools
- SSMS
- SSDT
- Database migration
- Database connectivity
ms.assetid: 91da13a4-0eea-4e88-b608-dada881ff5f2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0a2c469b23e1ce4134767920547297b23ec030cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598988"
---
# <a name="database-lifecycle-management"></a><span data-ttu-id="5f72f-102">資料庫生命週期管理</span><span class="sxs-lookup"><span data-stu-id="5f72f-102">Database Lifecycle Management</span></span>
  <span data-ttu-id="5f72f-103">資料庫生命週期管理 (DLM) 是一種管理資料庫和資料資產的原則式方法。</span><span class="sxs-lookup"><span data-stu-id="5f72f-103">Database lifecycle management (DLM) is a policy-based approach to managing databases and data assets.</span></span> <span data-ttu-id="5f72f-104">DLM 不是產品而是一套針對資料庫應用程式管理資料庫結構描述、資料和中繼資料的完整方法。</span><span class="sxs-lookup"><span data-stu-id="5f72f-104">DLM is not a product but a comprehensive approach to managing the database schema, data, and metadata for a database application.</span></span> <span data-ttu-id="5f72f-105">周全且主動的 DLM 方法可讓組織根據適當的效能、保護、可用性和成本層級管理資料資源。</span><span class="sxs-lookup"><span data-stu-id="5f72f-105">A thoughtful and proactive approach to DLM enables an organization to manage data resources according to appropriate levels of performance, protection, availability, and cost.</span></span>  
  
 <span data-ttu-id="5f72f-106">DLM 一開始會探討專案設計與意圖，接著探討資料庫開發、測試、建置、部署、維護、監視和備份活動，最後再探討資料封存。</span><span class="sxs-lookup"><span data-stu-id="5f72f-106">DLM begins with discussion of project design and intent, continues with database develop, test, build, deploy, maintain, monitor, and backup activities, and ends with data archive.</span></span> <span data-ttu-id="5f72f-107">本主題將提供 DLM 各階段的概觀：從資料庫開發開始，然後依序進行建置、部署和監視動作 (圖 1)。</span><span class="sxs-lookup"><span data-stu-id="5f72f-107">This topic provides an overview of the stages of DLM that begin with database development and progress through build, deploy, and monitor actions (Figure 1).</span></span> <span data-ttu-id="5f72f-108">同時也包含資料管理活動，以及資料可攜性作業，例如匯入/匯出、備份、移轉和同步。</span><span class="sxs-lookup"><span data-stu-id="5f72f-108">Also included are data management activities, and data portability operations like import/export, backup, migrate, and sync.</span></span>  
  
 <span data-ttu-id="5f72f-109">若要閱讀完整主題，請參閱 [Database Lifecycle Management (DLM)](https://go.microsoft.com/fwlink/?LinkId=276949)(資料庫生命週期管理 (DLM))。</span><span class="sxs-lookup"><span data-stu-id="5f72f-109">To read the complete topic, see [Database Lifecycle Management (DLM)](https://go.microsoft.com/fwlink/?LinkId=276949).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f72f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f72f-110">See Also</span></span>  
 <span data-ttu-id="5f72f-111">[Azure 首頁](https://www.windowsazure.com/) </span><span class="sxs-lookup"><span data-stu-id="5f72f-111">[Azure Home Page](https://www.windowsazure.com/) </span></span>  
 <span data-ttu-id="5f72f-112">[Azure 開發人員中心](https://www.windowsazure.com/develop/overview/) </span><span class="sxs-lookup"><span data-stu-id="5f72f-112">[Azure Developer Center](https://www.windowsazure.com/develop/overview/) </span></span>  
 <span data-ttu-id="5f72f-113">[Azure 管理中心](https://www.windowsazure.com/manage/overview/) </span><span class="sxs-lookup"><span data-stu-id="5f72f-113">[Azure Manage Center](https://www.windowsazure.com/manage/overview/) </span></span>  
 <span data-ttu-id="5f72f-114">[Azure 團隊部落格](https://www.windowsazure.com/community/blog/) </span><span class="sxs-lookup"><span data-stu-id="5f72f-114">[Azure Team Blog](https://www.windowsazure.com/community/blog/) </span></span>  
 [<span data-ttu-id="5f72f-115">Azure 支援選項</span><span class="sxs-lookup"><span data-stu-id="5f72f-115">Azure Support Options</span></span>](https://www.windowsazure.com/support/contact/)  
  
