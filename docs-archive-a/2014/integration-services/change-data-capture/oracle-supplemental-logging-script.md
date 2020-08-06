---
title: Oracle 補充記錄指令碼 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5e6ee618-b89b-46c7-92ad-4fc5ef7b777a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0aa55e71c17574eba9e25e098a3881b0eb4c9e11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687096"
---
# <a name="oracle-supplemental-logging-script"></a><span data-ttu-id="10114-102">Oracle 補充記錄指令碼</span><span class="sxs-lookup"><span data-stu-id="10114-102">Oracle Supplemental Logging Script</span></span>
  <span data-ttu-id="10114-103">此對話方塊會顯示 Oracle 補充記錄指令碼。</span><span class="sxs-lookup"><span data-stu-id="10114-103">This dialog box shows the script the Oracle supplemental logging script.</span></span>  
  
 <span data-ttu-id="10114-104">當您準備要使用的 CDC 執行個體時，CDC 設計工具會建立 Oracle SQL 指令碼，該指令碼會針對要擷取的資料表設定補充記錄。</span><span class="sxs-lookup"><span data-stu-id="10114-104">When you prepare a CDC Instance for use, the CDC Designer creates an Oracle SQL script that sets up supplemental logging for the tables to be captured.</span></span> <span data-ttu-id="10114-105">補充記錄指令碼會告知 Oracle 何時更新特定資料表，而且它寫入交易記錄中的變更記錄應該包含所有相關之資料行的資料，而不只是變更的資料行。</span><span class="sxs-lookup"><span data-stu-id="10114-105">The supplemental logging script tells Oracle that when a specific table is updated, the change records it writes to the transaction log should contain the data of all columns of interest, not just the columns that changed.</span></span>  
  
 <span data-ttu-id="10114-106">根據組織內的 Oracle DBA 政策而定，執行補充記錄指令碼可能需要 Oracle DBA 審查及核准。</span><span class="sxs-lookup"><span data-stu-id="10114-106">Depending on the Oracle DBA policies in your organization, running the supplemental logging script may require a review and approval by an Oracle DBA.</span></span>  
  
## <a name="options"></a><span data-ttu-id="10114-107">選項。</span><span class="sxs-lookup"><span data-stu-id="10114-107">Options</span></span>  
 <span data-ttu-id="10114-108">以下是如何執行指令碼的可用選項。</span><span class="sxs-lookup"><span data-stu-id="10114-108">The following are the available options for how to execute the script.</span></span>  
  
 <span data-ttu-id="10114-109">**執行指令碼**</span><span class="sxs-lookup"><span data-stu-id="10114-109">**Run Script**</span></span>  
 <span data-ttu-id="10114-110">在針對 CDC 執行個體定義的資料表上執行補充記錄指令碼。</span><span class="sxs-lookup"><span data-stu-id="10114-110">Runs the supplemental logging script on the tables defined for the CDC instance.</span></span> <span data-ttu-id="10114-111">若要執行此指令碼，Oracle 使用者必須擁有要擷取之所有資料表的 ALTER TABLE 權限以及 DBA_LOG_GROUPS 檢視表的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="10114-111">To run this script, the Oracle user must have ALTER TABLE permission for all the tables to be captured and SELECT permission on the DBA_LOG_GROUPS view.</span></span> <span data-ttu-id="10114-112">此外，Oracle 使用者必須擁有使用 Oracle 資料庫之必要權限的認證。</span><span class="sxs-lookup"><span data-stu-id="10114-112">In addition, the Oracle user must have the credentials for an Oracle database use with the required permissions.</span></span> <span data-ttu-id="10114-113">您可以讓程式提示您輸入 Oracle 認證，然後讓它執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="10114-113">You can let the program prompt you for the Oracle credentials and then have it run the script.</span></span>  
  
 <span data-ttu-id="10114-114">**另存新檔**</span><span class="sxs-lookup"><span data-stu-id="10114-114">**Save As**</span></span>  
 <span data-ttu-id="10114-115">將指令碼儲存至文字檔。</span><span class="sxs-lookup"><span data-stu-id="10114-115">Saves the script to a text file.</span></span> <span data-ttu-id="10114-116">如果 Oracle 資料庫管理員 (DBA) 需要檢查及執行補充記錄指令碼，就會使用這個方式。此程式可讓您將指令碼儲存成文字檔，之後可以將此文字檔透過電子郵件或其他方式傳送給 Oracle DBA 以供日後執行 (使用 SQL\*Plus Oracle 公用程式或其他工具，在 Oracle 資料庫上執行指令碼)。</span><span class="sxs-lookup"><span data-stu-id="10114-116">This is used if an Oracle database administrator (DBA) needs to examine and execute the supplemental logging script, the program lets you save the script to a text file that you can later send to the Oracle DBA by email or by other means to be execute later (by using the SQL\*Plus Oracle utility or other tool for running scripts on an Oracle database).</span></span>  
  
 <span data-ttu-id="10114-117">**複製**</span><span class="sxs-lookup"><span data-stu-id="10114-117">**Copy**</span></span>  
 <span data-ttu-id="10114-118">將指令碼複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="10114-118">Copies the script to the clipboard.</span></span> <span data-ttu-id="10114-119">備妥之後，您可以將指令碼貼到所需的任何位置，萬一 Oracle 資料庫管理員 (DBA) 需要檢查及執行補充記錄指令碼時，就可以派上用場。</span><span class="sxs-lookup"><span data-stu-id="10114-119">When ready you can paste the script in any location you need in case an Oracle database administrator (DBA) needs to examine and execute the supplemental logging script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10114-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10114-120">See Also</span></span>  
 <span data-ttu-id="10114-121">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="10114-121">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="10114-122">管理 CDC 執行個體</span><span class="sxs-lookup"><span data-stu-id="10114-122">Manage a CDC Instance</span></span>](manage-a-cdc-instance.md)  
  
  
