---
title: 編輯資料表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- tabProps
ms.assetid: fed8fada-2abc-45e2-8228-0656f9c599cb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8e8058a0c3e8b81814283f055e4c4ac2b08dd2fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585533"
---
# <a name="edit-tables"></a><span data-ttu-id="89655-102">編輯資料表</span><span class="sxs-lookup"><span data-stu-id="89655-102">Edit Tables</span></span>
  <span data-ttu-id="89655-103">使用 **[資料表]** 索引標籤，以變更您從 Oracle 來源資料庫選取的資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="89655-103">Use the **Tables** tab to make changes to the tables and columns that you selected from the Oracle source database.</span></span> <span data-ttu-id="89655-104">此索引標籤具有以下元素：</span><span class="sxs-lookup"><span data-stu-id="89655-104">This tab has the following elements:</span></span>  
  
 <span data-ttu-id="89655-105">**資料表清單**</span><span class="sxs-lookup"><span data-stu-id="89655-105">**Table list**</span></span>  
 <span data-ttu-id="89655-106">此資料表清單具有三個資料行：</span><span class="sxs-lookup"><span data-stu-id="89655-106">The table list has three columns:</span></span>  
  
-   <span data-ttu-id="89655-107">**Oracle 資料表名稱**：資料表的名稱，包括資料表結構描述。</span><span class="sxs-lookup"><span data-stu-id="89655-107">**Oracle Table Name**: The name of the table, including the table schema.</span></span>  
  
-   <span data-ttu-id="89655-108">**擷取執行個體**：用來命名執行個體特有之異動資料擷取物件的擷取執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="89655-108">**Capture Instance**: The name of the capture instance used to name instance-specific change data capture objects.</span></span> <span data-ttu-id="89655-109">擷取執行個體不得為 NULL。</span><span class="sxs-lookup"><span data-stu-id="89655-109">The capture instance cannot be NULL.</span></span> <span data-ttu-id="89655-110">如果未指定，名稱會衍生自來源結構描述名稱，加上 `<schema-name>_<table-name>.` 格式的來源資料表名稱。擷取執行個體名稱不能超過 100 個字元，而且在資料庫內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="89655-110">If not specified, the name is derived from the source schema name plus the source table name in the format `<schema-name>_<table-name>.` The capture instance name cannot exceed 100 characters and must be unique within the database.</span></span> <span data-ttu-id="89655-111">您可以在此資料行中按一下任何資料格，手動編輯 **capture_instance**。</span><span class="sxs-lookup"><span data-stu-id="89655-111">You can click in any cell in this column to manually edit the **capture_instance**.</span></span>  
  
-   <span data-ttu-id="89655-112">**安全性角色**：用來取得變更資料之存取權的資料庫角色名稱。</span><span class="sxs-lookup"><span data-stu-id="89655-112">**Security Role**: The name of the database role used to gain access to change data.</span></span> <span data-ttu-id="89655-113">您可以在此資料行中按一下任何資料格，手動編輯 **security_role**。</span><span class="sxs-lookup"><span data-stu-id="89655-113">You can click in any cell in this column to manually edit the **security_role**.</span></span>  
  
 <span data-ttu-id="89655-114">**加入資料表**</span><span class="sxs-lookup"><span data-stu-id="89655-114">**Add Tables**</span></span>  
 <span data-ttu-id="89655-115">按一下 [加入資料表]  開啟 [資料表選取範圍] 對話方塊，即可[將資料表加入至 CDC 執行個體](add-tables-to-a-cdc-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="89655-115">Click **Add Tables** to open the Table Selection dialog box where you can [Add Tables to a CDC Instance](add-tables-to-a-cdc-instance.md).</span></span> <span data-ttu-id="89655-116">當您初次在此工作階段存取 Oracle 資料庫時，您必須 [Connect to Oracle](connect-to-oracle.md)。</span><span class="sxs-lookup"><span data-stu-id="89655-116">The first time this session that you access the Oracle database, you must [Connect to Oracle](connect-to-oracle.md).</span></span>  
  
 <span data-ttu-id="89655-117">**編輯**</span><span class="sxs-lookup"><span data-stu-id="89655-117">**Edit**</span></span>  
 <span data-ttu-id="89655-118">從清單中選取資料表，然後選取 [編輯]  開啟該資料表的 [屬性]  對話方塊，即可[編輯資料表屬性](edit-the-table-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="89655-118">Select a table from the list and select **Edit** to open the **Properties** dialog box for that table where you can [Edit the Table Properties](edit-the-table-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="89655-119">您不能針對已經有鏡像資料表的資料表編輯類型對應。</span><span class="sxs-lookup"><span data-stu-id="89655-119">You cannot edit type mapping for tables that already have mirror tables.</span></span> <span data-ttu-id="89655-120">您只能針對新的資料表編輯類型對應。</span><span class="sxs-lookup"><span data-stu-id="89655-120">You can do this for new tables only.</span></span>  
  
 <span data-ttu-id="89655-121">**移除**</span><span class="sxs-lookup"><span data-stu-id="89655-121">**Remove**</span></span>  
 <span data-ttu-id="89655-122">從清單中選取資料表，並按一下 [移除]  ，從 CDC 執行個體中移除此資料表。</span><span class="sxs-lookup"><span data-stu-id="89655-122">Select a table from the list and click **Remove** to remove the table from the CDC instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89655-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89655-123">See Also</span></span>  
 <span data-ttu-id="89655-124">[如何編輯 CDC 執行個體屬性](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="89655-124">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 [<span data-ttu-id="89655-125">選取 Oracle 資料表和資料行</span><span class="sxs-lookup"><span data-stu-id="89655-125">Select Oracle Tables and Columns</span></span>](select-oracle-tables-and-columns.md)  
  
  
