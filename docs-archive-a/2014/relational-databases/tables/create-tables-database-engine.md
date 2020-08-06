---
title: 建立資料表 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table creation [SQL Server], Visual Database Tools
ms.assetid: 6f7c6ac5-e6d3-4dca-831e-b28442ba535b
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8d84a4da6a10fbcbae311fe1bf738c03b85a4c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607333"
---
# <a name="create-tables-database-engine"></a><span data-ttu-id="2d4a8-102">建立資料表 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="2d4a8-102">Create Tables (Database Engine)</span></span>
  <span data-ttu-id="2d4a8-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立新資料表、為資料表命名，並將它加入至現有資料庫。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-103">You can create a new table, name it, and add it to an existing database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>

> [!NOTE]
>  <span data-ttu-id="2d4a8-104">如果您連接到 SQL Azure 資料庫，新的資料表選項將會啟動建立資料表範本指令碼。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-104">If you are connected to a SQL Azure database, the new table option launches a create table template script.</span></span> <span data-ttu-id="2d4a8-105">請編輯參數，然後執行指令碼來建立新的資料表。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-105">Edit the parameters, then run the script to create a new table.</span></span> <span data-ttu-id="2d4a8-106">如需詳細資訊，請參閱＜ [SQL Azure 概觀](https://microsoft.sharepoint.com/sites/infopedia_g01/pages/cards/azure-sql-database.aspx)＞。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-106">For more information, see [SQL Azure Overview](https://microsoft.sharepoint.com/sites/infopedia_g01/pages/cards/azure-sql-database.aspx).</span></span>

 <span data-ttu-id="2d4a8-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2d4a8-107">**In This Topic**</span></span>

-   <span data-ttu-id="2d4a8-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="2d4a8-108">**Before you begin:**</span></span>

     [<span data-ttu-id="2d4a8-109">安全性</span><span class="sxs-lookup"><span data-stu-id="2d4a8-109">Security</span></span>](#Security)

-   <span data-ttu-id="2d4a8-110">**若要使用下列項目來建立資料表：**</span><span class="sxs-lookup"><span data-stu-id="2d4a8-110">**To create a table, using:**</span></span>

     [<span data-ttu-id="2d4a8-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2d4a8-111">SQL Server Management Studio</span></span>](#SSMSProcedure)

     [<span data-ttu-id="2d4a8-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2d4a8-112">Transact-SQL</span></span>](#TsqlProcedure)

##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2d4a8-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="2d4a8-113">Before You Begin</span></span>

###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2d4a8-114">Security</span><span class="sxs-lookup"><span data-stu-id="2d4a8-114">Security</span></span>

####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2d4a8-115">權限</span><span class="sxs-lookup"><span data-stu-id="2d4a8-115">Permissions</span></span>
 <span data-ttu-id="2d4a8-116">需要資料庫的 CREATE TABLE 權限以及用以建立資料表之結構描述的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-116">Requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span>

 <span data-ttu-id="2d4a8-117">如果將 CREATE TABLE 陳述式中的任何資料行定義成 CLR 使用者定義型別，就需要類型的擁有權或它的 REFERENCES 權限。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-117">If any columns in the CREATE TABLE statement are defined as a CLR user-defined type, either ownership of the type or REFERENCES permission on it is required.</span></span>

 <span data-ttu-id="2d4a8-118">如果 CREATE TABLE 陳述式中的任何資料行有相關聯的 XML 結構描述集合，就需要 XML 結構描述集合的擁有權或它的 REFERENCES 權限。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-118">If any columns in the CREATE TABLE statement have an XML schema collection associated with them, either ownership of the XML schema collection or REFERENCES permission on it is required.</span></span>

##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2d4a8-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2d4a8-119">Using SQL Server Management Studio</span></span>

#### <a name="to-create-a-table-with-table-designer"></a><span data-ttu-id="2d4a8-120">若要使用資料表設計工具建立資料表</span><span class="sxs-lookup"><span data-stu-id="2d4a8-120">To create a table with Table Designer</span></span>

1.  <span data-ttu-id="2d4a8-121">在 **[物件總管]**，連接至包含要修改的資料庫的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-121">In **Object Explorer**, connect to the instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] that contains the database to be modified.</span></span>

2.  <span data-ttu-id="2d4a8-122">在 **[物件總管]** 中，展開 **[資料庫]** 節點，然後展開將包含新資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-122">In **Object Explorer**, expand the **Databases** node and then expand the database that will contain the new table.</span></span>

3.  <span data-ttu-id="2d4a8-123">在物件總管中，以滑鼠右鍵按一下資料庫的 [資料表]\*\*\*\* 節點，然後按一下 [新增資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-123">In Object Explorer, right-click the **Tables** node of your database and then click **New Table**.</span></span>

4.  <span data-ttu-id="2d4a8-124">輸入資料行名稱，選擇資料類型，然後選擇是否允許讓每個資料行都是 null，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-124">Type column names, choose data types, and choose whether to allow nulls for each column as shown in the following illustration.</span></span>

     <span data-ttu-id="2d4a8-125">![AddColumnsinTableDesigner](../../database-engine/media/addcolumnsintabledesigner.gif "AddColumnsinTableDesigner")</span><span class="sxs-lookup"><span data-stu-id="2d4a8-125">![AddColumnsinTableDesigner](../../database-engine/media/addcolumnsintabledesigner.gif "AddColumnsinTableDesigner")</span></span>

5.  <span data-ttu-id="2d4a8-126">若要指定資料行的其他屬性，例如識別或計算資料行值，請按一下資料行，然後在資料行屬性索引標籤中選擇適當的屬性。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-126">To specify more properties for a column, such as identity or computed column values, click the column and in the column properties tab, choose the appropriate properties.</span></span> <span data-ttu-id="2d4a8-127">如需資料行屬性的詳細資訊，請參閱[資料表資料行屬性 &#40;SQL Server Management Studio&#41;](table-column-properties-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-127">For more information about column properties, see [Table Column Properties &#40;SQL Server Management Studio&#41;](table-column-properties-sql-server-management-studio.md).</span></span>

6.  <span data-ttu-id="2d4a8-128">若要指定資料行做為主索引鍵，請以滑鼠右鍵按一下資料行並選取 [設定主索引鍵]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-128">To specify a column as a primary key, right-click the column and select **Set Primary Key**.</span></span> <span data-ttu-id="2d4a8-129">如需詳細資訊，請參閱 [Create Primary Keys](../tables/create-primary-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-129">For more information, see [Create Primary Keys](../tables/create-primary-keys.md).</span></span>

7.  <span data-ttu-id="2d4a8-130">若要建立外部索引鍵關聯性、檢查條件約束或索引，請在 [資料表設計工具] 窗格中按一下滑鼠右鍵並選取清單中的物件，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-130">To create foreign key relationships, check constraints, or indexes, right-click in the Table Designer pane and select an object from the list as shown in the following illustration.</span></span>

     <span data-ttu-id="2d4a8-131">![AddTableObjects](../../database-engine/media/addtableobjects.gif "AddTableObjects")</span><span class="sxs-lookup"><span data-stu-id="2d4a8-131">![AddTableObjects](../../database-engine/media/addtableobjects.gif "AddTableObjects")</span></span>

     <span data-ttu-id="2d4a8-132">如需有關這些物件的詳細資訊，請參閱＜ [Create Foreign Key Relationships](../tables/create-foreign-key-relationships.md)＞、＜ [Create Check Constraints](../tables/create-check-constraints.md) ＞和＜ [Indexes](../indexes/indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-132">For more information about these objects, see [Create Foreign Key Relationships](../tables/create-foreign-key-relationships.md), [Create Check Constraints](../tables/create-check-constraints.md) and [Indexes](../indexes/indexes.md).</span></span>

8.  <span data-ttu-id="2d4a8-133">依預設，此資料表包含在 **dbo** 結構描述中。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-133">By default, the table is contained in the **dbo** schema.</span></span> <span data-ttu-id="2d4a8-134">若要為資料表指定不同的結構描述，請在 [資料表設計工具] 窗格中按一下滑鼠右鍵並選取 [屬性]\*\*\*\*，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-134">To specify a different schema for the table, right-click in the Table Designer pane and select **Properties** as shown in the following illustration.</span></span> <span data-ttu-id="2d4a8-135">從 [結構描述]\*\*\*\* 下拉式清單中選取適當的結構描述。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-135">From the **Schema** drop-down list, select the appropriate schema.</span></span>

     <span data-ttu-id="2d4a8-136">![Specifyatableschema](../../database-engine/media/specifyatableschema.gif "Specifyatableschema")</span><span class="sxs-lookup"><span data-stu-id="2d4a8-136">![Specifyatableschema](../../database-engine/media/specifyatableschema.gif "Specifyatableschema")</span></span>

     <span data-ttu-id="2d4a8-137">如需有關結構描述的詳細資訊，請參閱＜ [Create a Database Schema](../security/authentication-access/create-a-database-schema.md)＞。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-137">For more information about schemas, see [Create a Database Schema](../security/authentication-access/create-a-database-schema.md).</span></span>

9. <span data-ttu-id="2d4a8-138">從 [檔案]\*\*\*\* 功能表中，選擇 [儲存 <資料表名稱>]\*\*\*\* \*\*。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-138">From the **File** menu, choose **Save** *table name*.</span></span>

10. <span data-ttu-id="2d4a8-139">在 **[選擇名稱]** 對話方塊中，輸入資料表的名稱，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-139">In the **Choose Name** dialog box, type a name for the table and click **OK**.</span></span>

11. <span data-ttu-id="2d4a8-140">若要檢視新的資料表，在 **[物件總管]**，展開 **[資料表]** 節點並按 **F5** 重新整理物件清單。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-140">To view the new table, in **Object Explorer**, expand the **Tables** node and press **F5** to refresh the list of objects.</span></span> <span data-ttu-id="2d4a8-141">新的資料表就會在資料表清單中顯示。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-141">The new table is displayed in the list of tables.</span></span>

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2d4a8-142">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2d4a8-142">Using Transact-SQL</span></span>

#### <a name="to-create-a-table-in-the-query-editor"></a><span data-ttu-id="2d4a8-143">若要在查詢編輯器中建立資料表</span><span class="sxs-lookup"><span data-stu-id="2d4a8-143">To create a table in the Query Editor</span></span>

1.  <span data-ttu-id="2d4a8-144">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-144">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>

2.  <span data-ttu-id="2d4a8-145">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-145">On the Standard bar, click **New Query**.</span></span>

3.  <span data-ttu-id="2d4a8-146">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-146">Copy and paste the following example into the query window and click **Execute**.</span></span>

    ```
    CREATE TABLE dbo.PurchaseOrderDetail
    (
        PurchaseOrderID int NOT NULL
        ,LineNumber smallint NOT NULL
        ,ProductID int NULL
        ,UnitPrice money NULL
        ,OrderQty smallint NULL
        ,ReceivedQty float NULL
        ,RejectedQty float NULL
        ,DueDate datetime NULL
    );
    ```

 <span data-ttu-id="2d4a8-147">如需更多範例，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2d4a8-147">For more examples, see [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span></span>


