---
title: 重新命名檢視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- renaming views
ms.assetid: 5eed0488-81d2-40e8-8fdf-b0a640a591d0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5cc76ced033a69788270c3fa9277bcca6972e080
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687722"
---
# <a name="rename-views"></a><span data-ttu-id="022ba-102">重新命名檢視</span><span class="sxs-lookup"><span data-stu-id="022ba-102">Rename Views</span></span>
  <span data-ttu-id="022ba-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中重新命名檢視。</span><span class="sxs-lookup"><span data-stu-id="022ba-103">You can rename a view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="022ba-104">如果您重新命名檢視，涉及該檢視的程式碼和應用程式都會失敗。</span><span class="sxs-lookup"><span data-stu-id="022ba-104">If you rename a view, code and applications that depend on the view may fail.</span></span> <span data-ttu-id="022ba-105">這些包含其他檢視、查詢、預存程序、使用者定義函數，以及用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="022ba-105">These include other views, queries, stored procedures, user-defined functions, and client applications.</span></span> <span data-ttu-id="022ba-106">注意，這些失敗會串聯。</span><span class="sxs-lookup"><span data-stu-id="022ba-106">Note that these failures will cascade.</span></span>  
  
 <span data-ttu-id="022ba-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="022ba-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="022ba-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="022ba-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="022ba-109">先決條件</span><span class="sxs-lookup"><span data-stu-id="022ba-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="022ba-110">安全性</span><span class="sxs-lookup"><span data-stu-id="022ba-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="022ba-111">**使用下列方法重新命名檢視：**</span><span class="sxs-lookup"><span data-stu-id="022ba-111">**To rename a view, using:**</span></span>  
  
     [<span data-ttu-id="022ba-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="022ba-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="022ba-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="022ba-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="022ba-114">**後續操作：** [重新命名檢視後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="022ba-114">**Follow Up:**  [After renaming a view](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="022ba-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="022ba-115">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="022ba-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="022ba-116">Prerequisites</span></span>  
 <span data-ttu-id="022ba-117">取得檢視的所有相依性的清單。</span><span class="sxs-lookup"><span data-stu-id="022ba-117">Obtain a list of all dependencies on the view.</span></span> <span data-ttu-id="022ba-118">參考檢視的任何物件、指令碼或應用程式都必須修改，以反映檢視的新名稱。</span><span class="sxs-lookup"><span data-stu-id="022ba-118">Any objects, scripts or applications that reference the view must be modified to reflect the new name of the view.</span></span> <span data-ttu-id="022ba-119">如需詳細資訊，請參閱 [Get Information About a View](get-information-about-a-view.md)。</span><span class="sxs-lookup"><span data-stu-id="022ba-119">For more information, see [Get Information About a View](get-information-about-a-view.md).</span></span> <span data-ttu-id="022ba-120">建議您卸除檢視，並使用新名稱重新建立檢視，而不要重新命名檢視。</span><span class="sxs-lookup"><span data-stu-id="022ba-120">We recommend that you drop the view and recreate it with a new name instead of renaming the view.</span></span> <span data-ttu-id="022ba-121">透過重新建立檢視，可更新檢視中所參考之物件的相依性資訊。</span><span class="sxs-lookup"><span data-stu-id="022ba-121">By recreating the view, you update the dependency information for the objects that are referenced in the view.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="022ba-122">Security</span><span class="sxs-lookup"><span data-stu-id="022ba-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="022ba-123">權限</span><span class="sxs-lookup"><span data-stu-id="022ba-123">Permissions</span></span>  
 <span data-ttu-id="022ba-124">需要 SCHEMA 的 ALTER 權限，或 OBJECT 的 CONTROL 權限，以及資料庫的 CREATE VIEW 權限。</span><span class="sxs-lookup"><span data-stu-id="022ba-124">Requires ALTER permission on SCHEMA or CONTROL permission on OBJECT is required, and CREATE VIEW permission in the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="022ba-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="022ba-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-view"></a><span data-ttu-id="022ba-126">若要重新命名檢視</span><span class="sxs-lookup"><span data-stu-id="022ba-126">To rename a view</span></span>  
  
1.  <span data-ttu-id="022ba-127">在 **[物件總管]** 中，展開資料庫，此資料庫包含您要重新命名的檢視，然後展開 **[檢視]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="022ba-127">In **Object Explorer**, expand the database that contains the view you wish to rename and then expand the **View** folder.</span></span>  
  
2.  <span data-ttu-id="022ba-128">以滑鼠右鍵按一下您要重新命名的檢視，然後選取 **[重新命名]** 。</span><span class="sxs-lookup"><span data-stu-id="022ba-128">Right-click the view you wish to rename and select **Rename**.</span></span>  
  
3.  <span data-ttu-id="022ba-129">輸入檢視的新名稱。</span><span class="sxs-lookup"><span data-stu-id="022ba-129">Enter the view's new name.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="022ba-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="022ba-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="022ba-131">**若要重新命名檢視**</span><span class="sxs-lookup"><span data-stu-id="022ba-131">**To rename a view**</span></span>  
  
 <span data-ttu-id="022ba-132">雖然您可以使用 **sp_rename** 變更檢視的名稱，但建議您刪除現有的檢視，然後使用新名稱重新建立檢視。</span><span class="sxs-lookup"><span data-stu-id="022ba-132">While you can use **sp_rename** to change the name of the view, we recommend that you delete the existing view and then re-create it with the new name.</span></span>  
  
 <span data-ttu-id="022ba-133">如需詳細資訊，請參閱 [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) 和 [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="022ba-133">For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) and [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql).</span></span>  
  
##  <a name="follow-up-after-renaming-a-view"></a><a name="FollowUp"></a> <span data-ttu-id="022ba-134">後續操作：重新命名檢視後</span><span class="sxs-lookup"><span data-stu-id="022ba-134">Follow Up: After Renaming a View</span></span>  
 <span data-ttu-id="022ba-135">確定參考檢視舊名稱的任何物件、指令碼和應用程式現在都使用新名稱。</span><span class="sxs-lookup"><span data-stu-id="022ba-135">Ensure that all objects, scripts, and applications that reference the view's old name now use the new name.</span></span>  
  
  
