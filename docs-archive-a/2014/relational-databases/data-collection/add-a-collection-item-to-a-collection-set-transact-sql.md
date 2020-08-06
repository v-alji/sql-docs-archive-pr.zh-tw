---
title: 將收集項新增至收集組 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- collection items [SQL Server]
- collection sets [SQL Server], adding items
ms.assetid: 9fe6454e-8c0e-4b50-937b-d9871b20fd13
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0b21508761bdfbaf8918242b074f78203c1bcaed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606888"
---
# <a name="add-a-collection-item-to-a-collection-set-transact-sql"></a><span data-ttu-id="6aaba-102">將收集項加入收集組 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6aaba-102">Add a Collection Item to a Collection Set (Transact-SQL)</span></span>
  <span data-ttu-id="6aaba-103">您可以使用資料收集器所提供的預存程序，將收集項加入到現有的收集組中。</span><span class="sxs-lookup"><span data-stu-id="6aaba-103">You can add a collection item to an existing collection set using the stored procedures that are provided with the data collector.</span></span>  
  
 <span data-ttu-id="6aaba-104">請在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中使用查詢編輯器來完成以下步驟。</span><span class="sxs-lookup"><span data-stu-id="6aaba-104">Carry out the following steps using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="add-a-collection-item-to-a-collection-set"></a><span data-ttu-id="6aaba-105">將收集項加入收集組</span><span class="sxs-lookup"><span data-stu-id="6aaba-105">Add a collection item to a collection set</span></span>  
  
1.  <span data-ttu-id="6aaba-106">執行 **sp_syscollector_stop_collection_set** 預存程序，停止您想要加入此項目的收集組。</span><span class="sxs-lookup"><span data-stu-id="6aaba-106">Stop the collection set that you want to add the item to by running the **sp_syscollector_stop_collection_set** stored procedure.</span></span> <span data-ttu-id="6aaba-107">例如，若要停止名為 "Test Collection Set" 的收集組，請執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="6aaba-107">For example, to stop a collection set that is named "Test Collection Set", run the following statements:</span></span>  
  
    ```sql  
    USE msdb  
    DECLARE @csid int  
    SELECT @csid = collection_set_id  
    FROM syscollector_collection_sets  
    WHERE name = 'Test Collection Set'  
    SELECT @csid  
    EXEC dbo.sp_syscollector_stop_collection_set @collection_set_id = @csid  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="6aaba-108">您也可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的 [物件總管] 來停止收集組。</span><span class="sxs-lookup"><span data-stu-id="6aaba-108">You can also stop the collection set by using Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6aaba-109">如需詳細資訊，請參閱 [啟動或停止收集組](start-or-stop-a-collection-set.md)。</span><span class="sxs-lookup"><span data-stu-id="6aaba-109">For more information, see [Start or Stop a Collection Set](start-or-stop-a-collection-set.md).</span></span>  
  
2.  <span data-ttu-id="6aaba-110">宣告您想要加入收集項的收集組。</span><span class="sxs-lookup"><span data-stu-id="6aaba-110">Declare the collection set that you want to add the collection item to.</span></span> <span data-ttu-id="6aaba-111">下列程式碼會提供如何宣告收集組識別碼的範例。</span><span class="sxs-lookup"><span data-stu-id="6aaba-111">The following code provides an example of how to declare the collection set ID.</span></span>  
  
    ```sql  
    DECLARE @collection_set_id_1 int  
    SELECT @collection_set_id_1 = collection_set_id FROM [msdb].[dbo].[syscollector_collection_sets]  
    WHERE name = N'Test Collection Set'; -- name of collection set  
    ```  
  
3.  <span data-ttu-id="6aaba-112">宣告收集器型別。</span><span class="sxs-lookup"><span data-stu-id="6aaba-112">Declare the collector type.</span></span> <span data-ttu-id="6aaba-113">下列程式碼會提供如何宣告一般 T-SQL 查詢收集器型別的範例。</span><span class="sxs-lookup"><span data-stu-id="6aaba-113">The following code provides an example of how to declare the Generic T-SQL Query collector type.</span></span>  
  
    ```sql  
    DECLARE @collector_type_uid_1 uniqueidentifier  
    SELECT @collector_type_uid_1 = collector_type_uid FROM [msdb].[dbo].[syscollector_collector_types]   
       WHERE name = N'Generic T-SQL Query Collector Type';  
    ```  
  
     <span data-ttu-id="6aaba-114">您可以執行下列程式碼來取得已安裝的收集器型別清單：</span><span class="sxs-lookup"><span data-stu-id="6aaba-114">You can run the following code to obtain a list of the installed collector types:</span></span>  
  
    ```sql  
    USE msdb  
    SELECT * from syscollector_collector_types  
    GO  
    ```  
  
4.  <span data-ttu-id="6aaba-115">執行 **sp_syscollector_create_collection_item** 預存程序來建立收集項。</span><span class="sxs-lookup"><span data-stu-id="6aaba-115">Run the **sp_syscollector_create_collection_item** stored procedure to create the collection item.</span></span> <span data-ttu-id="6aaba-116">您必須宣告收集項的結構描述，好讓它對應到所需收集器型別的必要結構描述。</span><span class="sxs-lookup"><span data-stu-id="6aaba-116">You must declare the schema for the collection item so that it maps to the required schema for the desired collector type.</span></span> <span data-ttu-id="6aaba-117">下列範例會使用一般 T-SQL 查詢輸入結構描述。</span><span class="sxs-lookup"><span data-stu-id="6aaba-117">The following example uses the Generic T-SQL Query input schema.</span></span>  
  
    ```sql  
    DECLARE @collection_item_id int;  
    EXEC [msdb].[dbo].[sp_syscollector_create_collection_item]   
    @name=N'OS Wait Stats', --name of collection item  
    @parameters=N'  
    <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
     <Query>  
      <Value>select * from sys.dm_os_wait_stats</Value>  
      <OutputTable>os_wait_stats</OutputTable>  
    </Query>  
    </ns:TSQLQueryCollector>',  
    @collection_item_id = @collection_item_id OUTPUT,  
    @frequency = 60,  
    @collection_set_id = @collection_set_id_1, --- Provides the collection set ID number  
    @collector_type_uid = @collector_type_uid_1 -- Provides the collector type UID  
    SELECT @collection_item_id     
    ```  
  
5.  <span data-ttu-id="6aaba-118">在啟動更新的收集組之前，請執行下列查詢來確認新的收集項確實已經建立：</span><span class="sxs-lookup"><span data-stu-id="6aaba-118">Before starting the updated collection set, run the following query to verify that the new collection item has been created:</span></span>  
  
    ```xaml  
    USE msdb  
    SELECT * from syscollector_collection_sets  
    SELECT * from syscollector_collection_items  
    GO  
    ```  
  
     <span data-ttu-id="6aaba-119">收集組及其收集項都會顯示在 [結果]  索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="6aaba-119">The collection sets and their collection items are displayed in the **Results** tab.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aaba-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6aaba-120">See Also</span></span>  
 <span data-ttu-id="6aaba-121">[建立使用一般 T-SQL 查詢收集器型別的自訂收集組 &#40;Transact-SQL&#41;](create-custom-collection-set-generic-t-sql-query-collector-type.md) </span><span class="sxs-lookup"><span data-stu-id="6aaba-121">[Create a Custom Collection Set That Uses the Generic T-SQL Query Collector Type &#40;Transact-SQL&#41;](create-custom-collection-set-generic-t-sql-query-collector-type.md) </span></span>  
 [<span data-ttu-id="6aaba-122">資料收集器預存程序 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6aaba-122">Data Collector Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql)  
  
  
