---
title: 檢視資料表定義 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- showing table properties
- displaying table properties
- tables [SQL Server], properties
- viewing table properties
ms.assetid: 1865fb7c-f480-4100-9007-df5364cd002a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 53170a78a104bfce4b4e4177015461f2eb9093e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607325"
---
# <a name="view-the-table-definition"></a><span data-ttu-id="ece7d-102">檢視資料表定義</span><span class="sxs-lookup"><span data-stu-id="ece7d-102">View the Table Definition</span></span>
  <span data-ttu-id="ece7d-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中顯示資料表的屬性。</span><span class="sxs-lookup"><span data-stu-id="ece7d-103">You can display properties for a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ece7d-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="ece7d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ece7d-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="ece7d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ece7d-106">安全性</span><span class="sxs-lookup"><span data-stu-id="ece7d-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ece7d-107">**若要使用下列項目來顯示資料表屬性：**</span><span class="sxs-lookup"><span data-stu-id="ece7d-107">**To display table properties, using:**</span></span>  
  
     [<span data-ttu-id="ece7d-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ece7d-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ece7d-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ece7d-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ece7d-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="ece7d-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ece7d-111">Security</span><span class="sxs-lookup"><span data-stu-id="ece7d-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ece7d-112">權限</span><span class="sxs-lookup"><span data-stu-id="ece7d-112">Permissions</span></span>  
 <span data-ttu-id="ece7d-113">只有當您擁有資料表或者已經被授與該資料表的權限時，才能查看資料表的屬性。</span><span class="sxs-lookup"><span data-stu-id="ece7d-113">You can only see properties in a table if you either own the table or have been granted permissions to that table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ece7d-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ece7d-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-show-table-properties-in-the-properties-window"></a><span data-ttu-id="ece7d-115">若要在屬性視窗中顯示資料表屬性</span><span class="sxs-lookup"><span data-stu-id="ece7d-115">To show table properties in the Properties window</span></span>  
  
1.  <span data-ttu-id="ece7d-116">在 [物件總管] 中，選取您想要顯示屬性的資料表。</span><span class="sxs-lookup"><span data-stu-id="ece7d-116">In Object Explorer, select the table for which you want to show properties.</span></span>  
  
2.  <span data-ttu-id="ece7d-117">以滑鼠右鍵按一下資料表，然後從捷徑功能表中選擇 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="ece7d-117">Right-click the table and choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="ece7d-118">如需詳細資訊，請參閱 [Table Properties](table-properties-ssms.md)。</span><span class="sxs-lookup"><span data-stu-id="ece7d-118">For more information, see [Table Properties](table-properties-ssms.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ece7d-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ece7d-119">Using Transact-SQL</span></span>  
  
#### <a name="to-show-table-properties"></a><span data-ttu-id="ece7d-120">若要顯示資料表屬性</span><span class="sxs-lookup"><span data-stu-id="ece7d-120">To show table properties</span></span>  
  
1.  <span data-ttu-id="ece7d-121">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ece7d-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ece7d-122">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ece7d-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ece7d-123">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ece7d-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ece7d-124">此範例會從指定之物件的 `sys.tables` 目錄檢視傳回所有資料行。</span><span class="sxs-lookup"><span data-stu-id="ece7d-124">The example returns all columns from the `sys.tables` catalog view for the specified object.</span></span>  
  
    ```  
    SELECT * FROM sys.tables  
    WHERE object_id = 1973582069;  
  
    ```  
  
 <span data-ttu-id="ece7d-125">如需詳細資訊，請參閱 [sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ece7d-125">For more information, see [sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
