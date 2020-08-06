---
title: 檢閱及產生補充記錄指令碼 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- scripts
ms.assetid: 5c858ae2-37d6-42e8-a252-7f6ed4e628a7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cb735c0ee318ac68d48c71c09fc76ec305eb2552
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594138"
---
# <a name="review-and-generate-supplemental-logging-scripts"></a><span data-ttu-id="1e136-102">檢閱及產生補充記錄指令碼</span><span class="sxs-lookup"><span data-stu-id="1e136-102">Review and Generate Supplemental Logging Scripts</span></span>
  <span data-ttu-id="1e136-103">使用 [指令碼]  索引標籤可在設定補充記錄的 Oracle 來源資料庫上執行或重新執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="1e136-103">Use the **Scripts** tab to run or re-run a script on the Oracle source database that sets up supplemental logging.</span></span>  
  
 <span data-ttu-id="1e136-104">在您執行指令碼之前，請選取下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="1e136-104">Before you run the scripts select one of the following:</span></span>  
  
 <span data-ttu-id="1e136-105">**在此工作階段中包含變更**</span><span class="sxs-lookup"><span data-stu-id="1e136-105">**Include changes in this session**</span></span>  
 <span data-ttu-id="1e136-106">選取這個選項，在已加入至 CDC 執行個體的任何新資料表上或是透過屬性編輯器以任何方式變更的資料表上執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="1e136-106">Select this to run the script on any new table that was added to the CDC instance or on tables that were changed in any way using the Properties editor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e136-107">如果未針對 CDC 執行個體中的資料表進行任何變更，則 Oracle 補充記錄指令碼區域會是空的。</span><span class="sxs-lookup"><span data-stu-id="1e136-107">If no changes were made to the tables in the CDC instance, the Oracle supplemental logging script area will be empty.</span></span>  
  
 <span data-ttu-id="1e136-108">**包含所有資料表/擷取執行個體**</span><span class="sxs-lookup"><span data-stu-id="1e136-108">**Include all tables/capture instances**</span></span>  
 <span data-ttu-id="1e136-109">選取這個選項，在 CDC 執行個體的所有資料表和擷取執行個體上執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="1e136-109">Select this to run the script on all of the tables and capture instances in the CDC instance.</span></span>  
  
 <span data-ttu-id="1e136-110">當您選取其中一個選項之後，請執行補充記錄指令碼。</span><span class="sxs-lookup"><span data-stu-id="1e136-110">After you select one of these options, run the supplemental logging script.</span></span>  
  
### <a name="to-run-the-supplemental-logging-scripts"></a><span data-ttu-id="1e136-111">若要執行補充記錄指令碼</span><span class="sxs-lookup"><span data-stu-id="1e136-111">To run the supplemental logging scripts</span></span>  
  
1.  <span data-ttu-id="1e136-112">按一下 **[執行指令碼]** ，在針對 CDC 執行個體定義的資料表上執行補充記錄指令碼。</span><span class="sxs-lookup"><span data-stu-id="1e136-112">Click **Run Script** to run the supplemental logging script on the tables defined for the CDC instance.</span></span> <span data-ttu-id="1e136-113">此指令碼會指示 Oracle 資料庫在將 UPDATE 作業記錄到擷取的資料表時，將相關的所有資料行寫入其交易記錄中。</span><span class="sxs-lookup"><span data-stu-id="1e136-113">This script instructs the Oracle database to write all columns of interest to its transaction logs when logging UPDATE operations to captured tables.</span></span> <span data-ttu-id="1e136-114">通常是由 Oracle 系統管理員檢查和執行此指令碼。</span><span class="sxs-lookup"><span data-stu-id="1e136-114">This script is normally examined and executed by an Oracle system administrator.</span></span>  
  
2.  <span data-ttu-id="1e136-115">當您執行補充記錄指令碼時，將會開啟 [執行指令碼的 Oracle 認證] 對話方塊，您可以在此提供有效的 Oracle 使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="1e136-115">When you run the supplemental logging scripts, the Oracle Credentials for Running Script dialog box opens where you provide a valid Oracle user name and password.</span></span> <span data-ttu-id="1e136-116">如需有關如何提供適當之 Oracle 認證的詳細資訊，請參閱＜ [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1e136-116">For information on how to provide the proper Oracle credentials, see [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).</span></span>  
  
 <span data-ttu-id="1e136-117">必要時，您也可以使用 SQL \* Plus 手動執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="1e136-117">You can also run the scripts manually using SQL \* Plus, if necessary.</span></span>  
  
### <a name="to-run-the-scripts-manually"></a><span data-ttu-id="1e136-118">若要手動執行指令碼</span><span class="sxs-lookup"><span data-stu-id="1e136-118">To run the scripts manually</span></span>  
  
1.  <span data-ttu-id="1e136-119">按一下 **[複製]** ，將指令碼貼到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="1e136-119">Click **Copy** to paste the script to the clipboard.</span></span> <span data-ttu-id="1e136-120">開啟 SQL\* Plus，然後移至包含 Oracle 來源資料庫的目錄。</span><span class="sxs-lookup"><span data-stu-id="1e136-120">Open SQL\* Plus and go to the directory with your Oracle source database.</span></span> <span data-ttu-id="1e136-121">將指令碼貼到 SQL\*Plus 中加以執行。</span><span class="sxs-lookup"><span data-stu-id="1e136-121">Paste the script into SQL\*Plus to run it.</span></span>  
  
### <a name="to-save-the-supplemental-logging-script-in-a-text-file"></a><span data-ttu-id="1e136-122">若要將補充記錄指令碼儲存到文字檔中</span><span class="sxs-lookup"><span data-stu-id="1e136-122">To save the supplemental logging script in a text file</span></span>  
  
1.  <span data-ttu-id="1e136-123">按一下 **[另存新檔]** ，並瀏覽至您想要儲存檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="1e136-123">Click **Save as** and browse to the location where you want to save the file.</span></span>  
  
2.  <span data-ttu-id="1e136-124">提供檔案名稱，然後按一下 **[儲存]** 來儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="1e136-124">Give the file a name and click **Save** to save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e136-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e136-125">See Also</span></span>  
 <span data-ttu-id="1e136-126">[如何編輯 CDC 執行個體屬性](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="1e136-126">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 [<span data-ttu-id="1e136-127">執行指令碼的 Oracle 認證</span><span class="sxs-lookup"><span data-stu-id="1e136-127">Oracle Credentials for Running Script</span></span>](oracle-credentials-for-running-script.md)  
  
  
