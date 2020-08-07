---
title: 資料行對應 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.columnmapandtransform.f1
ms.assetid: eadc54a6-f936-4ffc-91d7-fbfd2bdcab93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7994de1292677421447d441c1ac5aeb2b6fbc618
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597941"
---
# <a name="column-mappings-sql-server-import-and-export-wizard"></a><span data-ttu-id="3385d-102">資料行對應 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="3385d-102">Column Mappings (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="3385d-103">使用 [資料**行**對應] 對話方塊，即可編輯轉換參數。</span><span class="sxs-lookup"><span data-stu-id="3385d-103">Use the **Column Mappings** dialog box to edit transformation parameters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3385d-104">當您選取 [資料表複製] 選項時，並不必複製資料表中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="3385d-104">You do not have to copy all the columns in a table when you select the Table Copy option.</span></span> <span data-ttu-id="3385d-105">**\<ignore>** 針對您要略過的資料行，在此對話方塊的 [**目的地**] 資料行中選取。</span><span class="sxs-lookup"><span data-stu-id="3385d-105">Select **\<ignore>** in the **Destination** column of this dialog box for columns that you want to skip.</span></span>  
  
 <span data-ttu-id="3385d-106">若要深入瞭解此嚮導，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="3385d-106">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="3385d-107">若要瞭解用來啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="3385d-107">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="3385d-108">「SQL Server 匯入和匯出精靈」的用途在於將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="3385d-108">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="3385d-109">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="3385d-109">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="3385d-110">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="3385d-110">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="3385d-111">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="3385d-111">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3385d-112">選項。</span><span class="sxs-lookup"><span data-stu-id="3385d-112">Options</span></span>  
 <span data-ttu-id="3385d-113">**Source**</span><span class="sxs-lookup"><span data-stu-id="3385d-113">**Source**</span></span>  
 <span data-ttu-id="3385d-114">識別選取的來源資料表、檢視，或查詢。</span><span class="sxs-lookup"><span data-stu-id="3385d-114">Identifies the selected source table, view, or query.</span></span>  
  
 <span data-ttu-id="3385d-115">**目的地**</span><span class="sxs-lookup"><span data-stu-id="3385d-115">**Destination**</span></span>  
 <span data-ttu-id="3385d-116">識別選取的目的地資料表、檢視，或查詢。</span><span class="sxs-lookup"><span data-stu-id="3385d-116">Identifies the selected destination table, view, or query.</span></span>  
  
 <span data-ttu-id="3385d-117">**建立目的地資料表/檔案**</span><span class="sxs-lookup"><span data-stu-id="3385d-117">**Create destination table/file**</span></span>  
 <span data-ttu-id="3385d-118">如果目的地資料表不存在，請指定是否要建立目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="3385d-118">Specify whether to create the destination table if it does not already exist.</span></span>  
  
 <span data-ttu-id="3385d-119">**刪除目的地資料表/檔案中的資料列**</span><span class="sxs-lookup"><span data-stu-id="3385d-119">**Delete rows in destination table/file**</span></span>  
 <span data-ttu-id="3385d-120">指定在載入新資料之前，是否要清除現有資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="3385d-120">Specify whether to clear the data from an existing table before loading new data.</span></span>  
  
 <span data-ttu-id="3385d-121">**將資料列附加至目的地資料表/檔案**</span><span class="sxs-lookup"><span data-stu-id="3385d-121">**Append rows to destination table/file**</span></span>  
 <span data-ttu-id="3385d-122">指定是否要將新資料附加到現有資料表中已存在的資料後面。</span><span class="sxs-lookup"><span data-stu-id="3385d-122">Specify whether to append the new data to the data already present in an existing table.</span></span>  
  
 <span data-ttu-id="3385d-123">**編輯 SQL**</span><span class="sxs-lookup"><span data-stu-id="3385d-123">**Edit SQL**</span></span>  
 <span data-ttu-id="3385d-124">使用 [**建立資料表的 SQL 語句**] 對話方塊中的 [預設] 語句，或針對您的用途加以修改。</span><span class="sxs-lookup"><span data-stu-id="3385d-124">Use the default statement in the **Create Table SQL Statement** dialog box, or modify it for your purposes.</span></span> <span data-ttu-id="3385d-125">如果修改此陳述式，您還必須對資料表對應進行相關的變更。</span><span class="sxs-lookup"><span data-stu-id="3385d-125">If you modify this statement, you must also make associated changes to table mapping.</span></span>  
  
 <span data-ttu-id="3385d-126">**卸除並重新建立目的地資料表**</span><span class="sxs-lookup"><span data-stu-id="3385d-126">**Drop and re-create destination table**</span></span>  
 <span data-ttu-id="3385d-127">選擇此選項即可覆寫目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="3385d-127">Choose this option to overwrite the destination table.</span></span> <span data-ttu-id="3385d-128">只有在您使用精靈來建立目的地資料表時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="3385d-128">This option is only available when you use the wizard to create the destination table.</span></span> <span data-ttu-id="3385d-129">目的地資料表只有在您儲存精靈所建立的封裝，然後再次執行封裝時才會卸除並重建。</span><span class="sxs-lookup"><span data-stu-id="3385d-129">The destination table is only dropped and re-created if you save the package that the wizard creates, and then run the package again.</span></span>  
  
 <span data-ttu-id="3385d-130">**啟用識別插入**</span><span class="sxs-lookup"><span data-stu-id="3385d-130">**Enable identity insert**</span></span>  
 <span data-ttu-id="3385d-131">選擇此選項即可允許將來源資料中的現有識別值，插入目的地資料表裡的識別欄位中。</span><span class="sxs-lookup"><span data-stu-id="3385d-131">Choose this option to allow existing identity values in the source data to be inserted into an identity column in the destination table.</span></span> <span data-ttu-id="3385d-132">依預設，目的地識別欄位並不允許此動作。</span><span class="sxs-lookup"><span data-stu-id="3385d-132">By default, the destination identity column does not allow this.</span></span>  
  
 <span data-ttu-id="3385d-133">**對應**</span><span class="sxs-lookup"><span data-stu-id="3385d-133">**Mappings**</span></span>  
 <span data-ttu-id="3385d-134">顯示資料來源中的每個資料行如何對應至目的地中的資料行。</span><span class="sxs-lookup"><span data-stu-id="3385d-134">Displays how each column in the data source maps to a column in the destination.</span></span>  
  
 <span data-ttu-id="3385d-135">這份清單具有下列資料行：</span><span class="sxs-lookup"><span data-stu-id="3385d-135">This list has the following columns:</span></span>  
  
 <span data-ttu-id="3385d-136">**Source**</span><span class="sxs-lookup"><span data-stu-id="3385d-136">**Source**</span></span>  
 <span data-ttu-id="3385d-137">檢視您可以為其設定轉換參數的每個來源資料行。</span><span class="sxs-lookup"><span data-stu-id="3385d-137">View each source column for which you can set transformation parameters.</span></span>  
  
 <span data-ttu-id="3385d-138">**目的地**</span><span class="sxs-lookup"><span data-stu-id="3385d-138">**Destination**</span></span>  
 <span data-ttu-id="3385d-139">指定在進行複製作業的期間，您是否想要忽略某資料行。</span><span class="sxs-lookup"><span data-stu-id="3385d-139">Specify whether you want to ignore a column during the copy operation.</span></span> <span data-ttu-id="3385d-140">您可以 **\<ignore>** 針對想要略過的資料行，在此資料行中選取，只複製資料行的子集。</span><span class="sxs-lookup"><span data-stu-id="3385d-140">You can copy only a subset of columns by selecting **\<ignore>** in this column for columns that you want to skip.</span></span> <span data-ttu-id="3385d-141">在對應資料行之前，您必須忽略不會加以對應的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="3385d-141">Before you map columns, you must ignore all columns that will not be mapped.</span></span>  
  
 <span data-ttu-id="3385d-142">**型別**</span><span class="sxs-lookup"><span data-stu-id="3385d-142">**Type**</span></span>  
 <span data-ttu-id="3385d-143">選取資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3385d-143">Select a data type for the column.</span></span>  
  
 <span data-ttu-id="3385d-144">**可為 Null**</span><span class="sxs-lookup"><span data-stu-id="3385d-144">**Nullable**</span></span>  
 <span data-ttu-id="3385d-145">指定資料行是否允許有 Null 值。</span><span class="sxs-lookup"><span data-stu-id="3385d-145">Specify whether a column will allow a null value.</span></span>  
  
 <span data-ttu-id="3385d-146">**大小**</span><span class="sxs-lookup"><span data-stu-id="3385d-146">**Size**</span></span>  
 <span data-ttu-id="3385d-147">指定資料行中的字元數目。</span><span class="sxs-lookup"><span data-stu-id="3385d-147">Specify the number of characters in the column.</span></span>  
  
 <span data-ttu-id="3385d-148">**有效位數**</span><span class="sxs-lookup"><span data-stu-id="3385d-148">**Precision**</span></span>  
 <span data-ttu-id="3385d-149">參考數字的位數，來指定所顯示資料的有效位數。</span><span class="sxs-lookup"><span data-stu-id="3385d-149">Specify the precision of displayed data, referring to the number of digits.</span></span>  
  
 <span data-ttu-id="3385d-150">**縮放比例**</span><span class="sxs-lookup"><span data-stu-id="3385d-150">**Scale**</span></span>  
 <span data-ttu-id="3385d-151">參考小數的位數，來指定所顯示資料的小數位數。</span><span class="sxs-lookup"><span data-stu-id="3385d-151">Specify the scale of displayed data, referring to the number of decimal places.</span></span>  
  
  
