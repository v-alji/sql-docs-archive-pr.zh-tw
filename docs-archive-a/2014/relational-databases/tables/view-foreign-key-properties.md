---
title: 檢視外部索引鍵屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- foreign keys [SQL Server], attributes
- displaying foreign keys attributes
- viewing foreign keys attributes
ms.assetid: b0e57cb7-9b26-4b96-b76a-1f59f5f498c5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5860a0cf26b983d75bab86862ee1e5fdd7737712
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585782"
---
# <a name="view-foreign-key-properties"></a><span data-ttu-id="e5cab-102">檢視外部索引鍵屬性</span><span class="sxs-lookup"><span data-stu-id="e5cab-102">View Foreign Key Properties</span></span>
  <span data-ttu-id="e5cab-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視關聯性的外部索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="e5cab-103">You can view the foreign key attributes of a relationship in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e5cab-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="e5cab-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e5cab-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="e5cab-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e5cab-106">安全性</span><span class="sxs-lookup"><span data-stu-id="e5cab-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e5cab-107">**使用下列方法，檢視特定資料表的外部索引鍵屬性：**</span><span class="sxs-lookup"><span data-stu-id="e5cab-107">**To view the foreign key attributes of a specific table, using:**</span></span>  
  
     [<span data-ttu-id="e5cab-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e5cab-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e5cab-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e5cab-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e5cab-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="e5cab-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e5cab-111">Security</span><span class="sxs-lookup"><span data-stu-id="e5cab-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e5cab-112">權限</span><span class="sxs-lookup"><span data-stu-id="e5cab-112">Permissions</span></span>  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] <span data-ttu-id="e5cab-113">如需相關資訊，請參閱 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="e5cab-113">For more information, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e5cab-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e5cab-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a><span data-ttu-id="e5cab-115">檢視特定資料表中之關聯性的外部索引鍵屬性</span><span class="sxs-lookup"><span data-stu-id="e5cab-115">To view the foreign key attributes of a relationship in a specific table</span></span>  
  
1.  <span data-ttu-id="e5cab-116">針對包含您要檢視外部索引鍵的資料表開啟 [資料表設計工具]，以滑鼠右鍵按一下 [資料表設計工具]，然後從快速鍵功能表選擇 [關聯性]  。</span><span class="sxs-lookup"><span data-stu-id="e5cab-116">Open the Table Designer for the table containing the foreign key you want to view, right-click in the Table Designer, and choose **Relationships** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="e5cab-117">從 [ **外部索引鍵關聯性** ] 對話方塊中，選取具備您想要檢視之屬性的關聯性。</span><span class="sxs-lookup"><span data-stu-id="e5cab-117">In the **Foreign Key Relationships** dialog box, select the relationship with properties you want to view.</span></span>  
  
 <span data-ttu-id="e5cab-118">如果外部索引鍵資料行與主索引鍵相關聯，主索引鍵資料行會在 **[資料表設計工具]** 內由資料列選取器中的主索引鍵符號識別。</span><span class="sxs-lookup"><span data-stu-id="e5cab-118">If the foreign key columns are related to a primary key, the primary key columns are identified in **Table Designer** by a primary key symbol in the row selector.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e5cab-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e5cab-119">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a><span data-ttu-id="e5cab-120">檢視特定資料表中之關聯性的外部索引鍵屬性</span><span class="sxs-lookup"><span data-stu-id="e5cab-120">To view the foreign key attributes of a relationship in a specific table</span></span>  
  
1.  <span data-ttu-id="e5cab-121">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e5cab-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e5cab-122">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e5cab-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e5cab-123">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e5cab-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e5cab-124">此範例會針對範例資料庫中的 `HumanResources.Employee` 資料表傳回所有外部索引鍵及其屬性。</span><span class="sxs-lookup"><span data-stu-id="e5cab-124">The example returns all foreign keys and their properties for the table `HumanResources.Employee` in the sample database.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT   
        f.name AS foreign_key_name  
       ,OBJECT_NAME(f.parent_object_id) AS table_name  
       ,COL_NAME(fc.parent_object_id, fc.parent_column_id) AS constraint_column_name  
       ,OBJECT_NAME (f.referenced_object_id) AS referenced_object  
       ,COL_NAME(fc.referenced_object_id, fc.referenced_column_id) AS referenced_column_name  
       ,is_disabled  
       ,delete_referential_action_desc  
       ,update_referential_action_desc  
    FROM sys.foreign_keys AS f  
    INNER JOIN sys.foreign_key_columns AS fc   
       ON f.object_id = fc.constraint_object_id   
    WHERE f.parent_object_id = OBJECT_ID('HumanResources.Employee');  
    ```  
  
 <span data-ttu-id="e5cab-125">如需詳細資訊，請參閱 [sys.foreign_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-keys-transact-sql) 和 [sys.foreign_key_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-key-columns-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e5cab-125">For more information, see [sys.foreign_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-keys-transact-sql) and [sys.foreign_key_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-key-columns-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
