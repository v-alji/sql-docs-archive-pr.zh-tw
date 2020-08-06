---
title: Master Data Services 資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], about the database
- database [Master Data Services]
ms.assetid: 5f590cc1-6ec2-4b8c-a598-03de0f6051a0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7e4bae180dfb7c9051d5445a689c44978ef73bfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597175"
---
# <a name="master-data-services-database"></a><span data-ttu-id="86b6b-102">Master Data Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="86b6b-102">Master Data Services Database</span></span>
  <span data-ttu-id="86b6b-103">此資料庫包含 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 系統的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="86b6b-103">The database contains all of the information for the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system.</span></span> <span data-ttu-id="86b6b-104">它是 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 部署的核心。</span><span class="sxs-lookup"><span data-stu-id="86b6b-104">It is central to a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] deployment.</span></span> <span data-ttu-id="86b6b-105">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫：</span><span class="sxs-lookup"><span data-stu-id="86b6b-105">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database:</span></span>  
  
-   <span data-ttu-id="86b6b-106">儲存 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 系統所需的設定、資料庫物件和資料。</span><span class="sxs-lookup"><span data-stu-id="86b6b-106">Stores the settings, database objects, and data required by the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system.</span></span>  
  
-   <span data-ttu-id="86b6b-107">包含用來處理來源系統中資料的臨時資料表。</span><span class="sxs-lookup"><span data-stu-id="86b6b-107">Contains staging tables that are used to process data from source systems.</span></span>  
  
-   <span data-ttu-id="86b6b-108">提供用來儲存來源系統中主資料的結構描述和資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="86b6b-108">Provides a schema and database objects to store master data from source systems.</span></span>  
  
-   <span data-ttu-id="86b6b-109">支援版本控制功能，包括商務規則驗證和電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="86b6b-109">Supports versioning functionality, including business rule validation and e-mail notifications.</span></span>  
  
-   <span data-ttu-id="86b6b-110">為需要從資料庫擷取資料的訂閱系統，提供檢視表。</span><span class="sxs-lookup"><span data-stu-id="86b6b-110">Provides views for subscribing systems that need to retrieve data from the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86b6b-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="86b6b-111">In This Section</span></span>  
  
-   [<span data-ttu-id="86b6b-112">分葉成員暫存資料表 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="86b6b-112">Leaf Member Staging Table &#40;Master Data Services&#41;</span></span>](leaf-member-staging-table-master-data-services.md)  
  
-   [<span data-ttu-id="86b6b-113">合併成員暫存資料表 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="86b6b-113">Consolidated Member Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md)  
  
-   [<span data-ttu-id="86b6b-114">關聯性暫存資料表 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="86b6b-114">Relationship Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/relationship-staging-table-master-data-services.md)  
  
-   [<span data-ttu-id="86b6b-115">暫存處理序錯誤 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="86b6b-115">Staging Process Errors &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/staging-process-errors-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="86b6b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86b6b-116">See Also</span></span>  
 <span data-ttu-id="86b6b-117">[建立 Master Data Services 資料庫](install-windows/create-a-master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="86b6b-117">[Create a Master Data Services Database](install-windows/create-a-master-data-services-database.md) </span></span>  
 <span data-ttu-id="86b6b-118">[資料庫物件安全性 &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="86b6b-118">[Database Object Security &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md) </span></span>  
 [<span data-ttu-id="86b6b-119">資料庫登入、使用者和角色 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="86b6b-119">Database Logins, Users, and Roles &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/database-logins-users-and-roles-master-data-services.md)  
  
  
