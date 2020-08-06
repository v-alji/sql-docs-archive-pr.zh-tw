---
title: 名稱比對 (資料來源 View Wizard)  (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourceviewwizard.namematchingcriteria.f1
ms.assetid: 7f811e02-0fe6-45c9-a7b7-29c61032d96b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 50cc46db7f582e0aea1570dadc956336ef8be074
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596345"
---
# <a name="name-matching-data-source-view-wizard-analysis-services"></a><span data-ttu-id="27f40-102">名稱比對 (資料來源檢視精靈) (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="27f40-102">Name Matching (Data Source View Wizard) (Analysis Services)</span></span>
  <span data-ttu-id="27f40-103">使用 **[名稱比對]** 頁面並選取要使用的準則，即可偵測您為資料來源檢視所選取的資料表，與結構描述中的其他資料表是否有關聯性。</span><span class="sxs-lookup"><span data-stu-id="27f40-103">Use the **Name Matching** page to select the criterion to use for detecting possible relationships between the tables that you select for the data source view and the other tables in the schema.</span></span> <span data-ttu-id="27f40-104">如果兩個資料表之間不存在實體外部索引鍵的關聯性，此準則可以幫助您識別相關的資料表，並將資料表加入資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="27f40-104">If no physical foreign key relationships exist between the tables, this criterion helps you identify and add related tables to the data source view.</span></span> <span data-ttu-id="27f40-105">由名稱比對識別的邏輯關聯性，也會加入到資料來源檢視中。</span><span class="sxs-lookup"><span data-stu-id="27f40-105">The logical relationships that are identified by name matching are also added to the data source view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27f40-106">只有當您選取的資料來源有多個資料表，但各個資料表間沒有任何外部索引鍵關聯性時，才會顯示這個頁面。</span><span class="sxs-lookup"><span data-stu-id="27f40-106">This page appears only if you select a data source that has multiple tables but no foreign key relationships between any one of the tables.</span></span>  
  
## <a name="options"></a><span data-ttu-id="27f40-107">選項</span><span class="sxs-lookup"><span data-stu-id="27f40-107">Options</span></span>  
 <span data-ttu-id="27f40-108">**以比對資料行的方式來建立邏輯關聯性**</span><span class="sxs-lookup"><span data-stu-id="27f40-108">**Create logical relationships by matching columns**</span></span>  
 <span data-ttu-id="27f40-109">選取即可使用名稱比對準則，來偵測您選取要包含在資料來源檢視中的資料表，與結構描述中的其他資料表是否有邏輯相依性和關聯性。</span><span class="sxs-lookup"><span data-stu-id="27f40-109">Select to use a name-matching criterion to detect possible logical dependencies and relationships between the tables that you select to include in the data source view and the other tables in the schema.</span></span> <span data-ttu-id="27f40-110">如果您清除此核取方塊，就不會在資料來源中使用名稱比對準則來識別資料表之間的邏輯關聯性。</span><span class="sxs-lookup"><span data-stu-id="27f40-110">If you clear this check box, no name-matching criterion is used to identify logical relationships between tables in the data source.</span></span>  
  
 <span data-ttu-id="27f40-111">**符合的外部索引鍵**</span><span class="sxs-lookup"><span data-stu-id="27f40-111">**Foreign key matches**</span></span>  
 <span data-ttu-id="27f40-112">選取建立資料表之間的邏輯關聯性和資料來源中的檢視所使用的準則。</span><span class="sxs-lookup"><span data-stu-id="27f40-112">Select the criterion to use for creating logical relationships between tables and views in the data source.</span></span> <span data-ttu-id="27f40-113">比對字串中的非英數字元會被忽略。</span><span class="sxs-lookup"><span data-stu-id="27f40-113">Non-alphanumeric characters are ignored in matching strings.</span></span> <span data-ttu-id="27f40-114">例如，「Customer ID」、「Customer_ID」和「CustomerID」全部都會相符。</span><span class="sxs-lookup"><span data-stu-id="27f40-114">For example, "Customer ID", "Customer_ID", "CustomerID" all match.</span></span> <span data-ttu-id="27f40-115">選取下表的選項之一，即可以指定的條件建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="27f40-115">Select one of the options in the following table to create relationships under the specified conditions.</span></span>  
  
|<span data-ttu-id="27f40-116">選取</span><span class="sxs-lookup"><span data-stu-id="27f40-116">Select</span></span>|<span data-ttu-id="27f40-117">即可建立</span><span class="sxs-lookup"><span data-stu-id="27f40-117">To create</span></span>|  
|------------|---------------|  
|<span data-ttu-id="27f40-118">**與主索引鍵的名稱相同**</span><span class="sxs-lookup"><span data-stu-id="27f40-118">**Same name as primary key**</span></span>|<span data-ttu-id="27f40-119">資料行名稱符合所選資料表之主索引鍵資料行名稱的任何資料表之邏輯關聯性。</span><span class="sxs-lookup"><span data-stu-id="27f40-119">A logical relationship to any table with a column name that matches the name of the primary key column in a selected table.</span></span>|  
|<span data-ttu-id="27f40-120">**與目的地資料表的名稱相同**</span><span class="sxs-lookup"><span data-stu-id="27f40-120">**Same name as destination table name**</span></span>|<span data-ttu-id="27f40-121">資料行名稱符合所選資料表名稱的任何資料表之邏輯關聯性。</span><span class="sxs-lookup"><span data-stu-id="27f40-121">A logical relationship to any table with a column name that matches the name of a selected table.</span></span>|  
|<span data-ttu-id="27f40-122">**目的地資料表名稱 + 主索引鍵名稱**</span><span class="sxs-lookup"><span data-stu-id="27f40-122">**Destination table name + primary key name**</span></span>|<span data-ttu-id="27f40-123">資料行名稱符合所選資料表名稱串連所選資料表之主索引鍵資料行名稱的邏輯關聯性。</span><span class="sxs-lookup"><span data-stu-id="27f40-123">A logical relationship to any table in which a column name matches the selected table name concatenated with the name of the primary key column for the selected table, in that order.</span></span> <span data-ttu-id="27f40-124">串連字串中的非英數字元會被忽略 (例如，「Product ID」、「Product_ID」和「ProductID」全部都會相符)。</span><span class="sxs-lookup"><span data-stu-id="27f40-124">Non-alphanumeric characters within the concatenation are ignored (for example, "Product ID", "Product_ID" and "ProductID" all match).</span></span>|  
  
 <span data-ttu-id="27f40-125">**描述及範例**</span><span class="sxs-lookup"><span data-stu-id="27f40-125">**Description and sample**</span></span>  
 <span data-ttu-id="27f40-126">檢視所選準則的描述及範例。</span><span class="sxs-lookup"><span data-stu-id="27f40-126">View a description and a sample of the selected criterion.</span></span>  
  
  
