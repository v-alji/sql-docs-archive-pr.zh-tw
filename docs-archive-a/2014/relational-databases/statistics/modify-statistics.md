---
title: 修改統計資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- statistics [SQL Server], modifying
- modifying statistics
ms.assetid: b06299ca-ed52-411a-b245-45eac4628c99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6dd44da6d1a80050f37f08e49773f95af0e5a339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599415"
---
# <a name="modify-statistics"></a><span data-ttu-id="ef9a5-102">修改統計資料</span><span class="sxs-lookup"><span data-stu-id="ef9a5-102">Modify Statistics</span></span>
  <span data-ttu-id="ef9a5-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改現有統計資料。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-103">You can modify existing statistics in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ef9a5-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="ef9a5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ef9a5-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="ef9a5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ef9a5-106">安全性</span><span class="sxs-lookup"><span data-stu-id="ef9a5-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ef9a5-107">**若要使用下列項目修改統計資料：**</span><span class="sxs-lookup"><span data-stu-id="ef9a5-107">**To modify statistics, using:**</span></span>  
  
     [<span data-ttu-id="ef9a5-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ef9a5-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ef9a5-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ef9a5-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ef9a5-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="ef9a5-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ef9a5-111">Security</span><span class="sxs-lookup"><span data-stu-id="ef9a5-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ef9a5-112">權限</span><span class="sxs-lookup"><span data-stu-id="ef9a5-112">Permissions</span></span>  
 <span data-ttu-id="ef9a5-113">需要：</span><span class="sxs-lookup"><span data-stu-id="ef9a5-113">Requires that:</span></span>  
  
-   <span data-ttu-id="ef9a5-114">使用者有資料表或檢視的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-114">The user has ALTER permission on the table or view.</span></span>  
  
-   <span data-ttu-id="ef9a5-115">使用者必須是資料表或索引檢視表擁有者，或是下列其中一個角色的成員： **sysadmin** 固定伺服器角色、 **db_owner** 固定資料庫角色或 **db_ddladmin** 固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-115">The user be the table or indexed view owner, or a member of one of the following roles: **sysadmin** fixed server role, **db_owner** fixed database role, or the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ef9a5-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ef9a5-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-statistics"></a><span data-ttu-id="ef9a5-117">若要修改統計資料</span><span class="sxs-lookup"><span data-stu-id="ef9a5-117">To modify statistics</span></span>  
  
1.  <span data-ttu-id="ef9a5-118">在 **[物件總管]** 中，按一下加號展開要在其中修改統計資料的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-118">In **Object Explorer**, click the plus sign to expand the database in which you want to modify a statistic.</span></span>  
  
2.  <span data-ttu-id="ef9a5-119">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-119">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="ef9a5-120">按一下加號展開要在其中修改統計資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-120">Click the plus sign to expand the table in which you want to modify a statistic.</span></span>  
  
4.  <span data-ttu-id="ef9a5-121">按一下加號展開 **[統計資料]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-121">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="ef9a5-122">以滑鼠右鍵按一下要修改的統計資料物件，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-122">Right-click the statistics object that you wish to modify and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="ef9a5-123">在 [統計資料屬性 - *statistics_name*] 對話方塊的 [一般] 頁面上，按一下 [新增]、[移除]、[上移]、[下移] 或任何組合，以改變統計資料的屬性。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-123">In the **Statistics Properties -** *statistics_name* dialog box, on the **General** page, click **Add**, **Remove**, **Move Up**, or **Move Down**, or any combination, to alter the properties of the statistics.</span></span> <span data-ttu-id="ef9a5-124">請記住，資料行在 [統計資料行] 方格中位置會大幅影響統計資料的效益。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-124">Remember that a column's location within the **Statistics Columns** grid can substantially impact the usefulness of the statistics.</span></span>  
  
7.  <span data-ttu-id="ef9a5-125">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-125">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ef9a5-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ef9a5-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="ef9a5-127">**若要修改統計資料**</span><span class="sxs-lookup"><span data-stu-id="ef9a5-127">**To modify statistics**</span></span>  
  
 <span data-ttu-id="ef9a5-128">您無法使用 Transact-SQL 陳述式來執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-128">This task cannot be performed using Transact-SQL statements.</span></span> <span data-ttu-id="ef9a5-129">若要使用 Transact-SQL 來修改統計資料，您必須先刪除現有的統計資料，然後以新的屬性重新建立統計資料。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-129">To modify statistics using Transact-SQL, you must first delete the existing statistic and then re-create it with new attributes.</span></span>  
  
 <span data-ttu-id="ef9a5-130">如需詳細資訊，請參閱 [DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql) 和 [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-130">For more information, see [DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql) and [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).</span></span>  
  
  
