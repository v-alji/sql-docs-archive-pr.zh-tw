---
title: 查看或變更資料和記錄檔的預設位置 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: def6be137aecbab7f2730fa4c2bf210b374a3a7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688190"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files-sql-server-management-studio"></a><span data-ttu-id="2e1f9-102">檢視或變更資料及記錄檔的預設位置 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="2e1f9-102">View or Change the Default Locations for Data and Log Files (SQL Server Management Studio)</span></span>
  <span data-ttu-id="2e1f9-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中檢視及變更新資料和記錄檔的預設位置。</span><span class="sxs-lookup"><span data-stu-id="2e1f9-103">This topic describes how to view and change the default locations of new data and log files in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="2e1f9-104">預設路徑是從登錄取得。</span><span class="sxs-lookup"><span data-stu-id="2e1f9-104">The default path is obtained from the registry.</span></span> <span data-ttu-id="2e1f9-105">在變更位置之後，如果未指定不同的位置， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中建立的所有新資料庫都會使用該位置。</span><span class="sxs-lookup"><span data-stu-id="2e1f9-105">After you change the location all new databases created in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will use that location if a different location is not specified.</span></span>  
  
 <span data-ttu-id="2e1f9-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2e1f9-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2e1f9-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="2e1f9-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2e1f9-108">建議</span><span class="sxs-lookup"><span data-stu-id="2e1f9-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="2e1f9-109">**使用下列方法檢視或變更資料和記錄檔的預設位置：**</span><span class="sxs-lookup"><span data-stu-id="2e1f9-109">**To view or change the data and log file default locations, using:**</span></span>  
  
     [<span data-ttu-id="2e1f9-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2e1f9-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   <span data-ttu-id="2e1f9-111">**待處理**  [變更預設位置之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="2e1f9-111">**Follow Up:**  [Changing the Default Locations](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2e1f9-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="2e1f9-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2e1f9-113">建議</span><span class="sxs-lookup"><span data-stu-id="2e1f9-113">Recommendations</span></span>  
 <span data-ttu-id="2e1f9-114">保護資料檔和記錄檔的最佳作法是確定它們受到存取控制清單 (ACL) 所保護。</span><span class="sxs-lookup"><span data-stu-id="2e1f9-114">The best practice for protecting your data files and log files is to ensure that they are protected by access control lists (ACLs).</span></span> <span data-ttu-id="2e1f9-115">ACL 應該設在建立這些檔案所在的根目錄下。</span><span class="sxs-lookup"><span data-stu-id="2e1f9-115">The ACLs should be set on the directory root under which the files are created.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2e1f9-116">Security</span><span class="sxs-lookup"><span data-stu-id="2e1f9-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2e1f9-117">權限</span><span class="sxs-lookup"><span data-stu-id="2e1f9-117">Permissions</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2e1f9-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2e1f9-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-default-locations-for-database-files"></a><span data-ttu-id="2e1f9-119">若要檢視或變更資料庫檔案的預設位置</span><span class="sxs-lookup"><span data-stu-id="2e1f9-119">To view or change the default locations for database files</span></span>  
  
1.  <span data-ttu-id="2e1f9-120">在 [物件總管] 中，以滑鼠右鍵按一下伺服器，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="2e1f9-120">In Object Explorer, right-click a server and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="2e1f9-121">在左面板中，按一下 **[資料庫設定]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="2e1f9-121">In the left panel, click the **Database settings** page.</span></span>  
  
3.  <span data-ttu-id="2e1f9-122">在 **[資料庫預設位置]** 中，您可以檢視新資料檔和新記錄檔的目前預設位置。</span><span class="sxs-lookup"><span data-stu-id="2e1f9-122">In **Database default locations**, view the current default locations for new data files and new log files.</span></span> <span data-ttu-id="2e1f9-123">若要變更預設位置，在 **[資料]** 或 **[記錄]** 欄位中輸入新的預設路徑名稱，或按一下 [瀏覽] 按鈕來尋找並選取路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="2e1f9-123">To change a default location, enter a new default pathname in the **Data** or **Log** field, or click the browse button to find and select a pathname.</span></span>  
  
##  <a name="follow-up-after-changing-the-default-locations"></a><a name="FollowUp"></a><span data-ttu-id="2e1f9-124">後續操作：變更預設位置之後</span><span class="sxs-lookup"><span data-stu-id="2e1f9-124">Follow Up: After Changing the Default Locations</span></span>  
 <span data-ttu-id="2e1f9-125">您必須停止然後啟動 SQL Server 服務以完成變更。</span><span class="sxs-lookup"><span data-stu-id="2e1f9-125">You must stop and start the SQL Server service to complete the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e1f9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e1f9-126">See Also</span></span>  
 <span data-ttu-id="2e1f9-127">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e1f9-127">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="2e1f9-128">建立資料庫</span><span class="sxs-lookup"><span data-stu-id="2e1f9-128">Create a Database</span></span>](../../relational-databases/databases/create-a-database.md)  
  
  
