---
title: 產生及執行補充記錄指令碼 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- supLog
ms.assetid: 6e940d93-12c6-4cda-9333-5489b245f0e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1437a4b0f790376268095d8e52afa981af865b44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687120"
---
# <a name="generate-and-run-the-supplemental-logging-script"></a><span data-ttu-id="c42e2-102">產生及執行補充記錄指令碼</span><span class="sxs-lookup"><span data-stu-id="c42e2-102">Generate and Run the Supplemental Logging Script</span></span>
  <span data-ttu-id="c42e2-103">使用 [設定資料表來擷取變更] 頁面，於將設定補充記錄的 Oracle 來源資料庫上執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="c42e2-103">Use the Set up Tables for Capturing Changes page to run a script on the Oracle source database that will set up supplemental logging.</span></span>  
  
 <span data-ttu-id="c42e2-104">**若要執行補充記錄指令碼**</span><span class="sxs-lookup"><span data-stu-id="c42e2-104">**To run the supplemental logging scripts**</span></span>  
  
 <span data-ttu-id="c42e2-105">按一下 **[執行指令碼]** ，在針對 CDC 執行個體定義的資料表上執行補充記錄指令碼。</span><span class="sxs-lookup"><span data-stu-id="c42e2-105">Click **Run Script** to run the supplemental logging script on the tables defined for the CDC instance.</span></span> <span data-ttu-id="c42e2-106">此指令碼會指示 Oracle 資料庫在將 UPDATE 作業記錄到擷取的資料表時，將相關的所有資料行寫入其交易記錄中。</span><span class="sxs-lookup"><span data-stu-id="c42e2-106">This script instructs the Oracle database to write all columns of interest to its transaction logs when logging UPDATE operations to captured tables.</span></span> <span data-ttu-id="c42e2-107">通常是由 Oracle 系統管理員檢查和執行此指令碼。</span><span class="sxs-lookup"><span data-stu-id="c42e2-107">This script is normally examined and executed by an Oracle system administrator.</span></span>  
  
 <span data-ttu-id="c42e2-108">您也可以使用 SQL \* Plus 手動執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="c42e2-108">You can also run the scripts manually using SQL \* Plus.</span></span>  
  
 <span data-ttu-id="c42e2-109">**若要手動執行指令碼**</span><span class="sxs-lookup"><span data-stu-id="c42e2-109">**To run the scripts manually**</span></span>  
  
 <span data-ttu-id="c42e2-110">按一下 **[複製]** ，將指令碼貼到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="c42e2-110">Click **Copy** to paste the script to the clipboard.</span></span> <span data-ttu-id="c42e2-111">開啟 SQL\* Plus，然後移至包含 Oracle 來源資料庫的目錄。</span><span class="sxs-lookup"><span data-stu-id="c42e2-111">Open SQL\* Plus and go to the directory with your Oracle source database.</span></span> <span data-ttu-id="c42e2-112">將指令碼貼到 SQL\*Plus 中加以執行。</span><span class="sxs-lookup"><span data-stu-id="c42e2-112">Paste the script into SQL\*Plus to run it.</span></span>  
  
 <span data-ttu-id="c42e2-113">若要將補充記錄指令碼儲存在文字檔中，請按一下 **[另存新檔]** ，並瀏覽至您要儲存檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="c42e2-113">To save the supplemental logging script in a text file, click **Save as** and browse to the location where you want to save the file.</span></span> <span data-ttu-id="c42e2-114">提供檔案名稱，然後按一下 **[儲存]** 來儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="c42e2-114">Give the file a name and click **Save** to save the file.</span></span>  
  
 <span data-ttu-id="c42e2-115">按 **[下一步]** ， [Generate Mirror Tables and CDC Capture Instances](generate-mirror-tables-and-cdc-capture-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="c42e2-115">Click **Next** to [Generate Mirror Tables and CDC Capture Instances](generate-mirror-tables-and-cdc-capture-instances.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c42e2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c42e2-116">See Also</span></span>  
 <span data-ttu-id="c42e2-117">[如何建立 SQL Server 變更資料庫執行個體](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="c42e2-117">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="c42e2-118">檢閱及產生補充記錄指令碼</span><span class="sxs-lookup"><span data-stu-id="c42e2-118">Review and Generate Supplemental Logging Scripts</span></span>](review-and-generate-supplemental-logging-scripts.md)  
  
  
