---
title: 產生鏡像資料表和 CDC 擷取執行個體 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- mirTab
ms.assetid: 260c1617-eecc-4007-a84d-3c5778ce46b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78daea310112cf7e9e78e489097fe9a76e69996b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687117"
---
# <a name="generate-mirror-tables-and-cdc-capture-instances"></a><span data-ttu-id="a9320-102">產生鏡像資料表和 CDC 擷取執行個體</span><span class="sxs-lookup"><span data-stu-id="a9320-102">Generate Mirror Tables and CDC Capture Instances</span></span>
  <span data-ttu-id="a9320-103">使用 [產生鏡像資料表] 頁面，針對 CDC 執行個體中包含的資料表產生鏡像資料表。</span><span class="sxs-lookup"><span data-stu-id="a9320-103">Use the Generate Mirror Tables page to generate the mirror tables for the tables you included in the CDC instance</span></span>  
  
 <span data-ttu-id="a9320-104">按一下 **[執行]** ，建立鏡像資料表。</span><span class="sxs-lookup"><span data-stu-id="a9320-104">Click **Run** to create the mirror tables.</span></span> <span data-ttu-id="a9320-105">隨即顯示每一個資料表的建立進度，而且會顯示一則訊息，讓您知道每一個鏡像資料表是否已順利完成還是發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="a9320-105">The progress for the creation of each table is displayed and a message is displayed to let you know whether each mirror table is completed successfully or with errors.</span></span> <span data-ttu-id="a9320-106">如果出現任何錯誤，請按一下 **[詳細資料]** ，查看包含錯誤說明的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a9320-106">If any errors occur, click **Details** to see a dialog box with an explanation of the error.</span></span>  
  
 <span data-ttu-id="a9320-107">如果有任何資料表建立失敗，您可以選擇繼續或刪除任何失敗的資料表，然後再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="a9320-107">If any of the tables fail to be created, you can choose to continue or delete any tables that failed before continuing.</span></span> <span data-ttu-id="a9320-108">當精靈執行完之後，您可以決定是否要在 Oracle 來源資料庫中修正資料表，或者不要在 CDC 執行個體中使用此資料表。</span><span class="sxs-lookup"><span data-stu-id="a9320-108">After you finish running the wizard, you can decide whether to fix the table in the Oracle source database or not use it in the CDC instance.</span></span> <span data-ttu-id="a9320-109">如果您修正此資料表，當您 [Edit Tables](edit-tables.md)時可以將它加入。</span><span class="sxs-lookup"><span data-stu-id="a9320-109">If you fix the table, you can add it when you [Edit Tables](edit-tables.md).</span></span>  
  
 <span data-ttu-id="a9320-110">按 **[下一步]** ，開啟 [Finish](finish.md) 頁面。</span><span class="sxs-lookup"><span data-stu-id="a9320-110">Click **Next** to open the [Finish](finish.md) page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9320-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9320-111">See Also</span></span>  
 [<span data-ttu-id="a9320-112">如何建立 SQL Server 變更資料庫執行個體</span><span class="sxs-lookup"><span data-stu-id="a9320-112">How to Create the SQL Server Change Database Instance</span></span>](how-to-create-the-sql-server-change-database-instance.md)  
  
  
