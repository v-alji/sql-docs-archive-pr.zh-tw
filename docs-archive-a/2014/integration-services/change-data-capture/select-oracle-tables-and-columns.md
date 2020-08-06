---
title: 選取 Oracle 資料表和資料行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- selTabCol
ms.assetid: bf73f80e-a954-4c5f-874e-17fdd4082715
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d51e597f1210643b1543ed981045ade7b2fc2b62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594130"
---
# <a name="select-oracle-tables-and-columns"></a><span data-ttu-id="0dc16-102">選取 Oracle 資料表和資料行</span><span class="sxs-lookup"><span data-stu-id="0dc16-102">Select Oracle Tables and Columns</span></span>
  <span data-ttu-id="0dc16-103">使用 [選取 Oracle 資料表和資料行] 頁面，從擷取變更的 Oracle 來源資料庫選取資料表。</span><span class="sxs-lookup"><span data-stu-id="0dc16-103">Use the Select Oracle Tables and Columns page to select the tables from the Oracle source database where changes are captured.</span></span> <span data-ttu-id="0dc16-104">此頁面具有以下元素：</span><span class="sxs-lookup"><span data-stu-id="0dc16-104">This page has the following elements:</span></span>  
  
## <a name="options"></a><span data-ttu-id="0dc16-105">選項。</span><span class="sxs-lookup"><span data-stu-id="0dc16-105">Options</span></span>  
 <span data-ttu-id="0dc16-106">**資料表清單**</span><span class="sxs-lookup"><span data-stu-id="0dc16-106">**Table list**</span></span>  
 <span data-ttu-id="0dc16-107">此資料表清單具有三個資料行：</span><span class="sxs-lookup"><span data-stu-id="0dc16-107">The table list has three columns:</span></span>  
  
-   <span data-ttu-id="0dc16-108">**Oracle 資料表名稱**：資料表的名稱，包括資料表結構描述。</span><span class="sxs-lookup"><span data-stu-id="0dc16-108">**Oracle Table Name**: The name of the table, including the table schema.</span></span>  
  
-   <span data-ttu-id="0dc16-109">**擷取執行個體**：用來命名執行個體特有之異動資料擷取物件的擷取執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="0dc16-109">**Capture Instance**: The name of the capture instance used to name instance-specific change data capture objects.</span></span> <span data-ttu-id="0dc16-110">擷取執行個體不得為 NULL。</span><span class="sxs-lookup"><span data-stu-id="0dc16-110">The capture instance cannot be NULL.</span></span>  
  
     <span data-ttu-id="0dc16-111">如果沒有指定，就會採用 `<schema-name>_<table-name>`格式，從來源結構描述名稱加上來源資料表名稱衍生此名稱。</span><span class="sxs-lookup"><span data-stu-id="0dc16-111">If not specified, the name is derived from the source schema name plus the source table name in the format `<schema-name>_<table-name>`.</span></span> <span data-ttu-id="0dc16-112">擷取執行個體名稱不得超過 100 個字元，而且在資料庫中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="0dc16-112">The capture instance name cannot exceed 100 characters and must be unique within the database.</span></span>  
  
     <span data-ttu-id="0dc16-113">您可以在此資料行中按一下任何資料格，手動編輯 **capture_instance**。</span><span class="sxs-lookup"><span data-stu-id="0dc16-113">You can click in any cell in this column to manually edit the **capture_instance**.</span></span>  
  
-   <span data-ttu-id="0dc16-114">**安全性角色**：用來控制變更資料之存取權的資料庫控制角色名稱。</span><span class="sxs-lookup"><span data-stu-id="0dc16-114">**Security Role**: The name of the database gating role used to control access to change data.</span></span>  
  
     <span data-ttu-id="0dc16-115">您可以在此資料行中按一下任何資料格，手動編輯 **security_role**。</span><span class="sxs-lookup"><span data-stu-id="0dc16-115">You can click in any cell in this column to manually edit the **security_role**.</span></span>  
  
 <span data-ttu-id="0dc16-116">**加入資料表**</span><span class="sxs-lookup"><span data-stu-id="0dc16-116">**Add Tables**</span></span>  
 <span data-ttu-id="0dc16-117">按一下 [加入資料表]  開啟 [資料表選取範圍] 對話方塊，您可以在這裡[選取 Oracle 資料表來擷取變更](select-oracle-tables-for-capturing-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="0dc16-117">Click **Add Tables** to open the Table Selection dialog box where you can [Select Oracle Tables for Capturing Changes](select-oracle-tables-for-capturing-changes.md).</span></span>  
  
 <span data-ttu-id="0dc16-118">**編輯**</span><span class="sxs-lookup"><span data-stu-id="0dc16-118">**Edit**</span></span>  
 <span data-ttu-id="0dc16-119">從清單中選取資料表，並選取 [編輯]  ，開啟該資料表的 [屬性]  對話方塊，您可以在這裡[變更為了擷取變更所選取的資料表](make-changes-to-the-tables-selected-for-capturing-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="0dc16-119">Select a table from the list and select **Edit** to open the **Properties** dialog box for that table where you can [Make Changes to the Tables Selected for Capturing Changes](make-changes-to-the-tables-selected-for-capturing-changes.md).</span></span>  
  
 <span data-ttu-id="0dc16-120">**移除**</span><span class="sxs-lookup"><span data-stu-id="0dc16-120">**Remove**</span></span>  
 <span data-ttu-id="0dc16-121">從清單中選取資料表，並按一下 [移除]  ，從 CDC 執行個體中移除此資料表。</span><span class="sxs-lookup"><span data-stu-id="0dc16-121">Select a table from the list and click **Remove** to remove the table from the CDC instance.</span></span>  
  
 <span data-ttu-id="0dc16-122">在您使用正確的對話方塊[選取 Oracle 資料表來擷取變更](select-oracle-tables-for-capturing-changes.md)及/或[變更為了擷取變更所選取的資料表](make-changes-to-the-tables-selected-for-capturing-changes.md)之後，請按一下 [下一步]  [產生及執行補充記錄指令碼](generate-and-run-the-supplemental-logging-script.md)。</span><span class="sxs-lookup"><span data-stu-id="0dc16-122">After you [Select Oracle Tables for Capturing Changes](select-oracle-tables-for-capturing-changes.md) and/or [Make Changes to the Tables Selected for Capturing Changes](make-changes-to-the-tables-selected-for-capturing-changes.md) using the correct dialog boxes, click **Next** to [Generate and Run the Supplemental Logging Script](generate-and-run-the-supplemental-logging-script.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dc16-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0dc16-123">See Also</span></span>  
 <span data-ttu-id="0dc16-124">[如何建立 SQL Server 變更資料庫執行個體](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="0dc16-124">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 <span data-ttu-id="0dc16-125">[編輯資料表](edit-tables.md) </span><span class="sxs-lookup"><span data-stu-id="0dc16-125">[Edit Tables](edit-tables.md) </span></span>  
 <span data-ttu-id="0dc16-126">[將資料表新增至 CDC 執行個體](add-tables-to-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="0dc16-126">[Add Tables to a CDC Instance](add-tables-to-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="0dc16-127">編輯資料表屬性</span><span class="sxs-lookup"><span data-stu-id="0dc16-127">Edit the Table Properties</span></span>](edit-the-table-properties.md)  
  
  
