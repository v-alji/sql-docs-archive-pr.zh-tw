---
title: 產生篩選 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.generatefilters.f1
ms.assetid: be28515c-5d6d-467b-b933-d7c8d97a45b4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0e484c89c97d3f32f3e41197800202f796a25d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585835"
---
# <a name="generate-filters"></a><span data-ttu-id="8c1a4-102">產生篩選</span><span class="sxs-lookup"><span data-stu-id="8c1a4-102">Generate Filters</span></span>
  <span data-ttu-id="8c1a4-103">**[產生篩選]** 對話方塊可讓您在合併式發行集內定義一個資料表的資料列篩選；然後複寫會自動將篩選擴充至透過外部索引鍵關聯性相關的其他資料表。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-103">The **Generate Filters** dialog box allows you to define a row filter on one table in a merge publication; replication then automatically extends the filter to other tables that are related through foreign key relationships.</span></span> <span data-ttu-id="8c1a4-104">例如，若您定義客戶資料表的篩選，使其只包含 French 客戶的資料，則複寫會擴充該篩選，使相關的訂單與訂單的詳細資料只包含與 French 客戶相關的資料。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-104">For example, if you define a filter on a customer table so that it only contains data on French customers, replication extends that filter so that related orders and order details tables contain only information related to French customers.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8c1a4-105">選項。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-105">Options</span></span>  
 <span data-ttu-id="8c1a4-106">此對話方塊包含三個步驟的處理序，可在資料表上建立資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-106">This dialog box involves a three-step process to create a row filter on a table.</span></span> <span data-ttu-id="8c1a4-107">接著，篩選會透過主索引鍵和外部索引鍵關聯性擴充到與已篩選資料表相關的資料表。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-107">The filter is then extended to the tables related to the filtered table through primary key and foreign key relationships.</span></span> <span data-ttu-id="8c1a4-108">例如，指定三個資料表 **Customer**、 **SalesOrderHeader**以及 **SalesOrderDetail**， **Customer** 和 **SalesOrderHeader**之間具有關聯性，而 **SalesOrderHeader** 和 **SalesOrderDetail**之間具有關聯性，將資料列篩選套用至 **Customer**，複寫會將篩選擴充至 **SalesOrderHeader** 和 **SalesOrderDetail**。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-108">For example, given the three tables **Customer**, **SalesOrderHeader**, and **SalesOrderDetail**, with a relationship between **Customer** and **SalesOrderHeader**, and a relationship between **SalesOrderHeader** and **SalesOrderDetail**, apply a row filter to **Customer**, and replication extends that filter to **SalesOrderHeader** and **SalesOrderDetail**.</span></span>  
  
1.  <span data-ttu-id="8c1a4-109">**選取要篩選的資料表。**</span><span class="sxs-lookup"><span data-stu-id="8c1a4-109">**Select the table to filter.**</span></span>  
  
     <span data-ttu-id="8c1a4-110">從下拉式清單方塊中選取資料表。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-110">Select a table from the drop-down list box.</span></span> <span data-ttu-id="8c1a4-111">只有在 **[發行項]** 頁面上選取資料表時，資料表才會出現在清單方塊中。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-111">Tables appear in the list box only if they were selected on the **Articles** page.</span></span>  
  
2.  <span data-ttu-id="8c1a4-112">**完成篩選陳述式來識別訂閱者將接收哪些資料表資料列。**</span><span class="sxs-lookup"><span data-stu-id="8c1a4-112">**Complete the filter statement to identify which table rows Subscribers will receive.**</span></span>  
  
     <span data-ttu-id="8c1a4-113">定義新的篩選陳述式。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-113">Define a new filter statement.</span></span> <span data-ttu-id="8c1a4-114">**[資料行]** 清單方塊會列出您要從 **[請選取要篩選的資料表]** 中選取之資料表發行的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-114">The **Columns** list box lists all the columns that you are publishing from the table you selected in **Select the table to filter**.</span></span> <span data-ttu-id="8c1a4-115">**[篩選陳述式]** 文字區域包括預設文字，其格式為：</span><span class="sxs-lookup"><span data-stu-id="8c1a4-115">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
     `SELECT <published_columns> FROM [tableowner].[tablename] WHERE`  
  
     <span data-ttu-id="8c1a4-116">無法變更此文字；請使用標準 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語法在 WHERE 關鍵字之後鍵入篩選子句。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-116">This text cannot be changed; type the filter clause after the WHERE keyword using standard [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="8c1a4-117">基於效能的考量，建議您不要在參數化資料列篩選器子句中的資料行名稱套用函數，例如 `LEFT([MyColumn]) = SUSER_SNAME()`。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-117">For performance reasons, we recommended that you not apply functions to column names in parameterized row filter clauses, such as `LEFT([MyColumn]) = SUSER_SNAME()`.</span></span> <span data-ttu-id="8c1a4-118">如果在篩選子句中使用 HOST_NAME，並且覆寫 HOST_NAME 值，則可能需要使用 CONVERT 來轉換資料類型。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-118">If you use HOST_NAME in a filter clause and override the HOST_NAME value, it might be necessary to convert data types using CONVERT.</span></span> <span data-ttu-id="8c1a4-119">如需有關此案例之最佳做法的詳細資訊，請參閱主題＜ [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)＞中的「覆寫 HOST_NAME() 值」一節。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-119">For more information about best practices for this case, see the section "Overriding the HOST_NAME() Value" in the topic [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
3.  <span data-ttu-id="8c1a4-120">**指定多少訂閱會從這個資料表接收資料。**</span><span class="sxs-lookup"><span data-stu-id="8c1a4-120">**Specify how many subscriptions will receive data from this table.**</span></span>  
  
     <span data-ttu-id="8c1a4-121">僅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-121">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="8c1a4-122">合併式複寫可以讓您指定最適合您的資料與應用程式的資料分割類型。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-122">Merge replication allows you to specify the type of partitions that are best suited to your data and application.</span></span> <span data-ttu-id="8c1a4-123">如果您選取 **[這個資料表中的一個資料列只會提供給一個訂閱]** ，合併式複寫會設定非重疊資料分割選項。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-123">If you select **A row from this table will go to only one subscription**, merge replication sets the nonoverlapping partitions option.</span></span> <span data-ttu-id="8c1a4-124">非重疊資料分割配合預先計算的資料分割使用可以提升效能，其中非重疊資料分割會最小化與預先計算之資料分割相關聯的上傳成本。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-124">Nonoverlapping partitions work in conjunction with precomputed partitions to improve performance, with nonoverlapping partitions minimizing the upload cost associated with precomputed partitions.</span></span> <span data-ttu-id="8c1a4-125">當使用的參數化篩選和聯結篩選越複雜時，非重疊資料分割在效能上的益處更為醒目。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-125">The performance benefit of nonoverlapping partitions is more noticeable when the parameterized filters and join filters used are more complex.</span></span> <span data-ttu-id="8c1a4-126">如果您選取此選項，必須確定分割資料的方式不會讓一個資料列複寫到一個以上的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-126">If you select this option, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="8c1a4-127">如需進一步資訊，請參閱主題＜ [參數化資料列篩選器](merge/parameterized-filters-parameterized-row-filters.md)＞中的「設定資料分割選項」。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-127">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="8c1a4-128">您加入篩選之後，按一下 **[確定]** 即可結束並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-128">After you have added a filter, click **OK** to exit and close the dialog box.</span></span> <span data-ttu-id="8c1a4-129">您指定的篩選會被剖析，並會針對 SELECT 子句中的資料表執行。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-129">The filter you specified is parsed and run against the table in the SELECT clause.</span></span> <span data-ttu-id="8c1a4-130">如果篩選陳述式包含語法錯誤或其他問題，則系統會通知您，然後您可以編輯該篩選陳述式。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-130">If the filter statement contains syntax errors or other problems, you will be notified and will be able to edit the filter statement.</span></span>  
  
 <span data-ttu-id="8c1a4-131">剖析陳述式之後，複寫會建立必要的聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-131">After the statement is parsed, replication creates the necessary join filters.</span></span> <span data-ttu-id="8c1a4-132">如果尚未針對此精靈執行的發行者設定散發者，就會提示您進行設定。</span><span class="sxs-lookup"><span data-stu-id="8c1a4-132">If you have not yet configured the Distributor for the Publisher against which this wizard is running, you are prompted to configure it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c1a4-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c1a4-133">See Also</span></span>  
 <span data-ttu-id="8c1a4-134">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="8c1a4-134">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="8c1a4-135">[檢視及修改發行集屬性](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="8c1a4-135">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="8c1a4-136">[篩選發行的資料](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="8c1a4-136">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="8c1a4-137">[Join Filters](merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="8c1a4-137">[Join Filters](merge/join-filters.md) </span></span>  
 <span data-ttu-id="8c1a4-138">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="8c1a4-138">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="8c1a4-139">發行資料和資料庫物件</span><span class="sxs-lookup"><span data-stu-id="8c1a4-139">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  
