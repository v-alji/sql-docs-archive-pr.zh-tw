---
title: 指定 Oracle 發行者的資料類型對應 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], data type mapping
- data types [SQL Server replication], Oracle publishing
- mapping data types [SQL Server replication]
ms.assetid: f172d631-3b8c-4912-bd0f-568366cd9870
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26331e3864940b9c7f2a2588e3d3cbfa9944c900
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705001"
---
# <a name="specify-data-type-mappings-for-an-oracle-publisher"></a><span data-ttu-id="1bb26-102">指定 Oracle 發行者的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="1bb26-102">Specify Data Type Mappings for an Oracle Publisher</span></span>
  <span data-ttu-id="1bb26-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中指定 Oracle 發行者的資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="1bb26-103">This topic describes how to specify data type mappings for an Oracle Publisher in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1bb26-104">雖然有針對 Oracle 發行者提供一組預設的資料類型對應，但是可能需要針對給定的發行集指定不同的對應。</span><span class="sxs-lookup"><span data-stu-id="1bb26-104">Although a set of default data type mappings are provided for Oracle Publishers, it might be necessary to specify different mappings for a given publication.</span></span>  
  
 <span data-ttu-id="1bb26-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="1bb26-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1bb26-106">**若要指定 Oracle 發行者的資料類型對應，請使用：**</span><span class="sxs-lookup"><span data-stu-id="1bb26-106">**To specify data type mappings for an Oracle Publisher, using:**</span></span>  
  
     [<span data-ttu-id="1bb26-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1bb26-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1bb26-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1bb26-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1bb26-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1bb26-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="1bb26-110">您可以在 [發行項屬性 - \<Article>] 對話方塊的 [資料對應] 索引標籤上，指定資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="1bb26-110">Specify data type mappings on the **Data Mapping** tab of the **Article Properties - \<Article>** dialog box.</span></span> <span data-ttu-id="1bb26-111">您可以從 [新增發行集] 精靈的 [發行項] 頁面，以及 [發行集屬性 - \<Publication>] 對話方塊存取這個對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1bb26-111">This is available from the **Articles** page of the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="1bb26-112">如需使用精靈和存取對話方塊的詳細資訊，請參閱[從 Oracle 資料庫建立發行集](create-a-publication-from-an-oracle-database.md)和[檢視及修改發行集屬性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1bb26-112">For more information about using the wizard and accessing the dialog box, see [Create a Publication from an Oracle Database](create-a-publication-from-an-oracle-database.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-specify-a-data-type-mapping"></a><span data-ttu-id="1bb26-113">若要指定資料類型對應</span><span class="sxs-lookup"><span data-stu-id="1bb26-113">To specify a data type mapping</span></span>  
  
1.  <span data-ttu-id="1bb26-114">在 [新增發行集] 精靈的 [發行項] 頁面上，或是在 [發行集屬性 - \<Publication>] 對話方塊中，選取一個資料表，然後按一下 [發行項屬性]。</span><span class="sxs-lookup"><span data-stu-id="1bb26-114">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="1bb26-115">按一下 **[設定反白顯示資料表發行項的屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="1bb26-115">Click **Set Properties of Highlighted Table Article**.</span></span>  
  
3.  <span data-ttu-id="1bb26-116">在 [發行項屬性 - \<Article>] 對話方塊的 [資料對應] 索引標籤上，從 [訂閱者資料類型] 資料行選取對應：</span><span class="sxs-lookup"><span data-stu-id="1bb26-116">On the **Data Mapping** tab of the **Article Properties - \<Article>** dialog box, select mappings from the **Subscriber Data Type** column:</span></span>  
  
    -   <span data-ttu-id="1bb26-117">針對某些資料類型，只有一個可能的對應，在此情況下，屬性方格中的資料行為唯讀。</span><span class="sxs-lookup"><span data-stu-id="1bb26-117">For some data types there is only one possible mapping, in which case the column in the property grid is read-only.</span></span>  
  
    -   <span data-ttu-id="1bb26-118">對於某些資料類型，有多種類型可供您選擇。</span><span class="sxs-lookup"><span data-stu-id="1bb26-118">For some types, there is more than one type that you can select.</span></span> <span data-ttu-id="1bb26-119">除非您的應用程式需要不同的對應，否則[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 建議您使用預設對應。</span><span class="sxs-lookup"><span data-stu-id="1bb26-119">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] recommends that you use the default mapping unless your application requires a different mapping.</span></span> <span data-ttu-id="1bb26-120">如需詳細資訊，請參閱 [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md)。</span><span class="sxs-lookup"><span data-stu-id="1bb26-120">For more information, see [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1bb26-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1bb26-121">Using Transact-SQL</span></span>  
 <span data-ttu-id="1bb26-122">您可以使用複寫預存程序以程式設計的方式指定自訂資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="1bb26-122">You can specify custom data type mappings programmatically using replication stored procedures.</span></span> <span data-ttu-id="1bb26-123">您也可以設定在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 與非資料庫管理系統之間對應資料類型 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (DBMS) 時所使用的預設對應。</span><span class="sxs-lookup"><span data-stu-id="1bb26-123">You can also set the default mappings that are used when mapping data types between [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database management system (DBMS).</span></span> <span data-ttu-id="1bb26-124">如需詳細資訊，請參閱 [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md)。</span><span class="sxs-lookup"><span data-stu-id="1bb26-124">For more information, see [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).</span></span>  
  
#### <a name="to-define-custom-data-type-mappings-when-creating-an-article-belonging-to-an-oracle-publication"></a><span data-ttu-id="1bb26-125">在建立屬於 Oracle 發行集的發行項時定義自訂資料類型對應</span><span class="sxs-lookup"><span data-stu-id="1bb26-125">To define custom data type mappings when creating an article belonging to an Oracle publication</span></span>  
  
1.  <span data-ttu-id="1bb26-126">如果沒有 Oracle 發行集存在，請建立一個。</span><span class="sxs-lookup"><span data-stu-id="1bb26-126">If one does not already exist, create an Oracle publication.</span></span>  
  
2.  <span data-ttu-id="1bb26-127">在散發者上執行 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1bb26-127">At the Distributor, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="1bb26-128">針對 **\@use_default_datatypes** 指定 **0** 值。</span><span class="sxs-lookup"><span data-stu-id="1bb26-128">Specify a value of **0** for **\@use_default_datatypes**.</span></span> <span data-ttu-id="1bb26-129">如需詳細資訊，請參閱 [定義發行項](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="1bb26-129">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
3.  <span data-ttu-id="1bb26-130">在散發者上，執行 [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) ，以檢視已發行之發行項中資料行的現有對應。</span><span class="sxs-lookup"><span data-stu-id="1bb26-130">At the Distributor, execute [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) to view the existing mapping for a column in a published article.</span></span>  
  
4.  <span data-ttu-id="1bb26-131">在散發者上，執行 [sp_changearticlecolumndatatype](/sql/relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1bb26-131">At the Distributor, execute [sp_changearticlecolumndatatype](/sql/relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql).</span></span> <span data-ttu-id="1bb26-132">針對 **\@publisher** 指定 Oracle 發行者的名稱，並指定 **\@publication**、 **\@article** 和 **\@column** 來定義已發佈的資料行。</span><span class="sxs-lookup"><span data-stu-id="1bb26-132">Specify the name of the Oracle Publisher for **\@publisher**, as well as **\@publication**, **\@article**, and **\@column** to define the published column.</span></span> <span data-ttu-id="1bb26-133">針對 **\@type** 指定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 要對應的資料類型名稱，並指定適用的 **\@length**、 **\@precision** 和 **\@scale**。</span><span class="sxs-lookup"><span data-stu-id="1bb26-133">Specify the name of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type to map to for **\@type**, as well as **\@length**, **\@precision**, and **\@scale**, where applicable.</span></span>  
  
5.  <span data-ttu-id="1bb26-134">在散發者上執行 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1bb26-134">At the Distributor, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="1bb26-135">這樣會建立用來從 Oracle 發行集產生快照集的檢視。</span><span class="sxs-lookup"><span data-stu-id="1bb26-135">This creates the view used to generate the snapshot from the Oracle publication.</span></span>  
  
#### <a name="to-specify-a-mapping-as-the-default-mapping-for-a-data-type"></a><span data-ttu-id="1bb26-136">將對應指定為資料類型的預設對應</span><span class="sxs-lookup"><span data-stu-id="1bb26-136">To specify a mapping as the default mapping for a data type</span></span>  
  
1.  <span data-ttu-id="1bb26-137">(選擇性) 在任何資料庫的散發者上，執行 [sp_getdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1bb26-137">(Optional) At the Distributor on any database, execute [sp_getdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql).</span></span> <span data-ttu-id="1bb26-138">指定 **\@source_dbms**、 **\@source_type**、 **\@destination_dbms**、 **\@destination_version** 及識別來源 DBMS 所需的任何其他參數。</span><span class="sxs-lookup"><span data-stu-id="1bb26-138">Specify **\@source_dbms**, **\@source_type**, **\@destination_dbms**, **\@destination_version**, and any other parameters needed to identify the source DBMS.</span></span> <span data-ttu-id="1bb26-139">目的地 DBMS 中有關目前對應之資料類型的資訊會使用輸出參數傳回。</span><span class="sxs-lookup"><span data-stu-id="1bb26-139">Information on the currently mapped data type in the destination DBMS is returned using the output parameters.</span></span>  
  
2.  <span data-ttu-id="1bb26-140">(選擇性) 在任何資料庫的散發者上，執行 [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1bb26-140">(Optional) At the Distributor on any database, execute [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql).</span></span> <span data-ttu-id="1bb26-141">指定 **\@source_dbms** 及篩選結果集所需的任何其他參數。</span><span class="sxs-lookup"><span data-stu-id="1bb26-141">Specify **\@source_dbms** and any other parameters needed to filter the result set.</span></span> <span data-ttu-id="1bb26-142">請記下結果集中所需之對應的 **mapping_id** 值。</span><span class="sxs-lookup"><span data-stu-id="1bb26-142">Note the value of **mapping_id** for the desired mapping in the result set.</span></span>  
  
3.  <span data-ttu-id="1bb26-143">在任何資料庫的散發者上，執行 [sp_setdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1bb26-143">At the Distributor on any database, execute [sp_setdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql).</span></span>  
  
    -   <span data-ttu-id="1bb26-144">如果您知道步驟 2 中所取得 **mapping_id** 的所需值，請針對 **\@mapping_id** 來指定它。</span><span class="sxs-lookup"><span data-stu-id="1bb26-144">If you know the desired value of **mapping_id** obtained in step 2, specify it for **\@mapping_id**.</span></span>  
  
    -   <span data-ttu-id="1bb26-145">如果您不知道 **mapping_id**，請指定 **\@source_dbms**、 **\@source_type**、 **\@destination_dbms**、 **\@destination_type** 等參數，以及識別現有對應所需的任何其他參數。</span><span class="sxs-lookup"><span data-stu-id="1bb26-145">If you do not know the **mapping_id**, specify the parameters **\@source_dbms**, **\@source_type**, **\@destination_dbms**, **\@destination_type**, and any other parameters required to identify an existing mapping.</span></span>  
  
#### <a name="to-find-valid-data-types-for-a-given-oracle-data-type"></a><span data-ttu-id="1bb26-146">在有效的資料類型中找出給定的 Oracle 資料類型</span><span class="sxs-lookup"><span data-stu-id="1bb26-146">To find valid data types for a given Oracle data type</span></span>  
  
1.  <span data-ttu-id="1bb26-147">在任何資料庫的散發者上，執行 [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1bb26-147">At the Distributor on any database, execute [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql).</span></span> <span data-ttu-id="1bb26-148">針對 **\@source_dbms** 指定 **ORACLE** 值，並指定篩選結果集所需的任何其他參數。</span><span class="sxs-lookup"><span data-stu-id="1bb26-148">Specify a value of **ORACLE** for **\@source_dbms** and any other parameters needed to filter the result set.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="1bb26-149">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1bb26-149">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="1bb26-150">這個範例會變更具有 NUMBER 之 Oracle 資料類型的資料行，好讓它對應到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型 `numeric`(38,38)，而不是預設的資料類型 `float`。</span><span class="sxs-lookup"><span data-stu-id="1bb26-150">This example changes a column with an Oracle data type of NUMBER so it is mapped to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type `numeric`(38,38), instead of the default data type `float`.</span></span>  
  
 [!code-sql[HowTo#sp_changecolumndatatype](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_changecolumndatatype)]  
  
 <span data-ttu-id="1bb26-151">這個範例查詢會針對 Oracle 9 資料類型 `CHAR` 傳回預設及替代對應。</span><span class="sxs-lookup"><span data-stu-id="1bb26-151">This example query returns the default and alternative mappings for the Oracle 9 data type `CHAR`.</span></span>  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_char](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_char)]  
  
 <span data-ttu-id="1bb26-152">這個範例查詢會針對 Oracle 9 資料類型 `NUMBER` 傳回預設對應 (如果指定此資料類型，則不含小數位數或有效位數)。</span><span class="sxs-lookup"><span data-stu-id="1bb26-152">This example query returns the default mappings for the Oracle 9 data type `NUMBER` when it is specified without a scale or precision.</span></span>  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_number](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_number)]  
  
## <a name="see-also"></a><span data-ttu-id="1bb26-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bb26-153">See Also</span></span>  
 <span data-ttu-id="1bb26-154">[Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="1bb26-154">[Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md) </span></span>  
 <span data-ttu-id="1bb26-155">[異質資料庫複寫](../non-sql/heterogeneous-database-replication.md) </span><span class="sxs-lookup"><span data-stu-id="1bb26-155">[Heterogeneous Database Replication](../non-sql/heterogeneous-database-replication.md) </span></span>  
 <span data-ttu-id="1bb26-156">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="1bb26-156">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="1bb26-157">設定 Oracle 發行者</span><span class="sxs-lookup"><span data-stu-id="1bb26-157">Configure an Oracle Publisher</span></span>](../non-sql/configure-an-oracle-publisher.md)  
  
  
