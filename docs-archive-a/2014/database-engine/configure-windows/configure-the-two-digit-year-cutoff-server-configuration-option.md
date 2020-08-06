---
title: 設定 two digit year cutoff 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- two digit year cutoff option
- four-digit years [SQL Server]
ms.assetid: d94e81b6-f2e6-47ef-b497-ec3d827a1646
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c31c1d87c8b743132dd90d495f73ef711dc1f813
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594167"
---
# <a name="configure-the-two-digit-year-cutoff-server-configuration-option"></a><span data-ttu-id="56f40-102">設定 two digit year cutoff 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="56f40-102">Configure the two digit year cutoff Server Configuration Option</span></span>
  <span data-ttu-id="56f40-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] two digit year cutoff [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="56f40-103">This topic describes how to configure the **two digit year cutoff** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="56f40-104">**two digit year cutoff** 選項會指定從 1753 到 9999 之間的整數，以代表將兩位數年份解譯為四位數年份時的截止年份 (Cutoff Year)。</span><span class="sxs-lookup"><span data-stu-id="56f40-104">The **two digit year cutoff** option specifies an integer from 1753 to 9999 that represents the cutoff year for interpreting two-digit years as four-digit years.</span></span> <span data-ttu-id="56f40-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設時間範圍為 1950-2049，代表截止年份為 2049。</span><span class="sxs-lookup"><span data-stu-id="56f40-105">The default time span for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is 1950-2049, which represents a cutoff year of 2049.</span></span> <span data-ttu-id="56f40-106">這表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會自動把兩位數字年份 49 解譯為 2049，兩位數字年份 50 解譯為 1950，兩位數字年份 99 解譯為 1999。</span><span class="sxs-lookup"><span data-stu-id="56f40-106">This means that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprets a two-digit year of 49 as 2049, a two-digit year of 50 as 1950, and a two-digit year of 99 as 1999.</span></span> <span data-ttu-id="56f40-107">若要維持回溯相容性，請保留預設值。</span><span class="sxs-lookup"><span data-stu-id="56f40-107">To maintain backward compatibility, leave the setting at the default value.</span></span>  
  
 <span data-ttu-id="56f40-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="56f40-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="56f40-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="56f40-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="56f40-110">建議</span><span class="sxs-lookup"><span data-stu-id="56f40-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="56f40-111">安全性</span><span class="sxs-lookup"><span data-stu-id="56f40-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="56f40-112">**使用下列方法設定 two digit year cutoff 選項：**</span><span class="sxs-lookup"><span data-stu-id="56f40-112">**To configure the two digit year cutoff option, using:**</span></span>  
  
     [<span data-ttu-id="56f40-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="56f40-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="56f40-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="56f40-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="56f40-115">**後續操作：** [設定兩位數年份截止選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="56f40-115">**Follow Up:**  [After you configure the two digit year cutoff option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="56f40-116">開始之前</span><span class="sxs-lookup"><span data-stu-id="56f40-116">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="56f40-117">建議</span><span class="sxs-lookup"><span data-stu-id="56f40-117">Recommendations</span></span>  
  
-   <span data-ttu-id="56f40-118">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="56f40-118">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="56f40-119">OLE Automation 物件使用 2030 年做為兩位數截止年份。</span><span class="sxs-lookup"><span data-stu-id="56f40-119">OLE Automation objects use 2030 as the two-digit cutoff year.</span></span> <span data-ttu-id="56f40-120">您可以使用 **two digit year cutoff** 選項在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和用戶端應用程式之間提供一致的日期值。</span><span class="sxs-lookup"><span data-stu-id="56f40-120">You can use the **two digit year cutoff** option to provide consistency in date values between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and client applications.</span></span> <span data-ttu-id="56f40-121">但為避免模稜兩可的日期，資料中應使用四位數的年份。</span><span class="sxs-lookup"><span data-stu-id="56f40-121">However, to avoid ambiguity with dates, use four-digit years in your data.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="56f40-122">Security</span><span class="sxs-lookup"><span data-stu-id="56f40-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="56f40-123">權限</span><span class="sxs-lookup"><span data-stu-id="56f40-123">Permissions</span></span>  
 <span data-ttu-id="56f40-124">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="56f40-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="56f40-125">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="56f40-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="56f40-126">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="56f40-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="56f40-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="56f40-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-two-digit-year-cutoff-option"></a><span data-ttu-id="56f40-128">若要設定 two digit year cutoff 選項</span><span class="sxs-lookup"><span data-stu-id="56f40-128">To configure the two digit year cutoff option</span></span>  
  
1.  <span data-ttu-id="56f40-129">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="56f40-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="56f40-130">按一下 **[其他伺服器設定]** 節點。</span><span class="sxs-lookup"><span data-stu-id="56f40-130">Click the **Misc server settings** node.</span></span>  
  
3.  <span data-ttu-id="56f40-131">在 [Two digit year support (兩位數年份支援)] 下的 [當輸入兩位數年份時，解譯為下列之間的年份]  方塊中，輸入或選取一個值作為時間範圍的結束年份。</span><span class="sxs-lookup"><span data-stu-id="56f40-131">Under **Two digit year support**, in the **When a two digit year is entered**, **interpret it as a year between** box, type or select a value that is the ending year of the time span.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="56f40-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="56f40-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-two-digit-year-cutoff-option"></a><span data-ttu-id="56f40-133">若要設定 two digit year cutoff 選項</span><span class="sxs-lookup"><span data-stu-id="56f40-133">To configure the two digit year cutoff option</span></span>  
  
1.  <span data-ttu-id="56f40-134">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="56f40-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="56f40-135">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="56f40-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="56f40-136">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="56f40-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="56f40-137">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `two digit year cutoff` 選項的值設定為 `2030`。</span><span class="sxs-lookup"><span data-stu-id="56f40-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `two digit year cutoff` option to `2030`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'two digit year cutoff', 2030 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="56f40-138">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="56f40-138">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-two-digit-year-cutoff-option"></a><a name="FollowUp"></a> <span data-ttu-id="56f40-139">後續操作：設定兩位數年份截止選項之後</span><span class="sxs-lookup"><span data-stu-id="56f40-139">Follow Up: After you configure the two digit year cutoff option</span></span>  
 <span data-ttu-id="56f40-140">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="56f40-140">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f40-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56f40-141">See Also</span></span>  
 <span data-ttu-id="56f40-142">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="56f40-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="56f40-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="56f40-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="56f40-144">RECONFIGURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56f40-144">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
