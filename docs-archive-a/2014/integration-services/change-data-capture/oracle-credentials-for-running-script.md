---
title: 執行指令碼的 Oracle 認證 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 683b313e5b1065c3709c4637ddf968641612cc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687097"
---
# <a name="oracle-credentials-for-running-script"></a><span data-ttu-id="56726-102">Oracle Credentials for Running Script</span><span class="sxs-lookup"><span data-stu-id="56726-102">Oracle Credentials for Running Script</span></span>
  <span data-ttu-id="56726-103">若要從 Oracle CDC 設計工具主控台執行 Oracle 補充記錄指令碼，此程式會提示您輸入執行此指令碼之 Oracle 使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="56726-103">To run the Oracle supplemental logging script from the Oracle CDC Designer console, the program prompts you for the credentials of the Oracle user who is running the script.</span></span> <span data-ttu-id="56726-104">若要執行此指令碼，Oracle 使用者必須擁有要擷取之所有資料表的 ALTER TABLE 權限以及 DBA_LOG_GROUPS 檢視表的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="56726-104">To run this script, the Oracle user must have ALTER TABLE permission for all the tables to be captured and SELECT permission on the DBA_LOG_GROUPS view.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="56726-105">工作清單</span><span class="sxs-lookup"><span data-stu-id="56726-105">Task List</span></span>  
 <span data-ttu-id="56726-106">請在此對話方塊中輸入以下資訊：</span><span class="sxs-lookup"><span data-stu-id="56726-106">Enter the following in this dialog box:</span></span>  
  
 <span data-ttu-id="56726-107">**驗證**</span><span class="sxs-lookup"><span data-stu-id="56726-107">**Authentication**</span></span>  
  
 <span data-ttu-id="56726-108">選取下列其中一個：</span><span class="sxs-lookup"><span data-stu-id="56726-108">Select one of the following:</span></span>  
  
-   <span data-ttu-id="56726-109">**Windows 驗證**：選取此選項可使用目前的 Windows 網域認證。</span><span class="sxs-lookup"><span data-stu-id="56726-109">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="56726-110">只有當設定 Oracle 資料庫使用 Windows 驗證時，才可使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="56726-110">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="56726-111">**Oracle 驗證**：如果您選取這個選項，您必須在您所連接的來源 Oracle 資料庫中輸入使用者的 **[使用者名稱]** 和 **[密碼]** 。</span><span class="sxs-lookup"><span data-stu-id="56726-111">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Source Oracle database you are connecting to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56726-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56726-112">See Also</span></span>  
 <span data-ttu-id="56726-113">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="56726-113">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="56726-114">檢閱及產生補充記錄指令碼</span><span class="sxs-lookup"><span data-stu-id="56726-114">Review and Generate Supplemental Logging Scripts</span></span>](review-and-generate-supplemental-logging-scripts.md)  
  
  
