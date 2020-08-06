---
title: 維護計畫 (報告與記錄頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reportinglogging.f1
ms.assetid: 3a30b17a-3deb-446f-900a-62f88934a90f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c7a95a7092ce2cdac4aa0540a5cb57d86b48497
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594529"
---
# <a name="maintenance-plan-reporting-and-logging-page"></a><span data-ttu-id="9a698-102">維護計畫 (報告與記錄頁面)</span><span class="sxs-lookup"><span data-stu-id="9a698-102">Maintenance Plan (Reporting and Logging Page)</span></span>
  <span data-ttu-id="9a698-103">使用 **[報表與記錄]** 對話方塊設定執行維護計畫時產生的報表和記錄。</span><span class="sxs-lookup"><span data-stu-id="9a698-103">Use the **Reporting and Logging** dialog box to configure the reports and logs that are generated when maintenance plans are executed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9a698-104">選項。</span><span class="sxs-lookup"><span data-stu-id="9a698-104">Options</span></span>  
 <span data-ttu-id="9a698-105">**產生文字檔報表**</span><span class="sxs-lookup"><span data-stu-id="9a698-105">**Generate a text file report**</span></span>  
 <span data-ttu-id="9a698-106">指定是否要 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 撰寫文字檔報表。</span><span class="sxs-lookup"><span data-stu-id="9a698-106">Specify if you want [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to write a text file report.</span></span>  
  
 <span data-ttu-id="9a698-107">**建立新檔案**</span><span class="sxs-lookup"><span data-stu-id="9a698-107">**Create a new file**</span></span>  
 <span data-ttu-id="9a698-108">每次執行維護計畫都建立新的報表檔案。</span><span class="sxs-lookup"><span data-stu-id="9a698-108">Create a new report file for each execution of the maintenance plan.</span></span> <span data-ttu-id="9a698-109">依預設，寫入報表檔案的電腦，是主控包含此維護計畫之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的電腦，而寫入位置是安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，所建立的預設記錄檔資料夾。</span><span class="sxs-lookup"><span data-stu-id="9a698-109">By default, the report files are written to the computer hosting the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contains this maintenance plan, in the folder established as the default log folder during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup.</span></span> <span data-ttu-id="9a698-110">若要指定其他資料夾，請在 [資料夾]  文字方塊中輸入資料夾的完整路徑，或者按一下瀏覽按鈕 ( **...** ) 並瀏覽至您要的資料夾。</span><span class="sxs-lookup"><span data-stu-id="9a698-110">To specify a different folder, enter the full path of the folder in the **Folder** text box, or click the browse button (**...**) and navigate to the desired folder.</span></span>  
  
 <span data-ttu-id="9a698-111">**附加至檔案**</span><span class="sxs-lookup"><span data-stu-id="9a698-111">**Append to file**</span></span>  
 <span data-ttu-id="9a698-112">將來自每個計畫執行的報表附加至 [檔案名稱]  文字方塊中所指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="9a698-112">Append the report from each plan execution to the file specified in the **File name** text box.</span></span> <span data-ttu-id="9a698-113">您也可以按一下瀏覽按鈕並從對話方塊中選取檔案，以指定檔案。</span><span class="sxs-lookup"><span data-stu-id="9a698-113">You may also specify a file by clicking the browse button and selecting a file from the dialog box.</span></span>  
  
 <span data-ttu-id="9a698-114">**傳送報表至電子郵件收件者**</span><span class="sxs-lookup"><span data-stu-id="9a698-114">**Send report to an e-mail recipient**</span></span>  
 <span data-ttu-id="9a698-115">透過電子郵件傳送維護計畫執行的結果。</span><span class="sxs-lookup"><span data-stu-id="9a698-115">Transmit the outcome of a maintenance plan execution via e-mail.</span></span> <span data-ttu-id="9a698-116">此選項只有在已啟用 Database Mail 並已正確設定之後才能使用。</span><span class="sxs-lookup"><span data-stu-id="9a698-116">This option is only available if Database Mail is enabled and properly configured.</span></span>  
  
 <span data-ttu-id="9a698-117">**代理程式操作員**</span><span class="sxs-lookup"><span data-stu-id="9a698-117">**Agent operator**</span></span>  
 <span data-ttu-id="9a698-118">從清單中選取代理程式操作員，以作為電子郵件的收件者。</span><span class="sxs-lookup"><span data-stu-id="9a698-118">Select an agent operator from the list who will be the recipient of the e-mail.</span></span> <span data-ttu-id="9a698-119">此選項只有在郵件已啟用並已正確設定之後才能使用。</span><span class="sxs-lookup"><span data-stu-id="9a698-119">This option is only available if mail is enabled and properly</span></span>  
  
 <span data-ttu-id="9a698-120">**記錄擴充資訊**</span><span class="sxs-lookup"><span data-stu-id="9a698-120">**Log extended information**</span></span>  
 <span data-ttu-id="9a698-121">在記錄檔中包含更多資訊。</span><span class="sxs-lookup"><span data-stu-id="9a698-121">Include more information in the log.</span></span> <span data-ttu-id="9a698-122">包含此選項會增加預存維護計畫記錄的大小。</span><span class="sxs-lookup"><span data-stu-id="9a698-122">Including this option will increase the size of the stored maintenance plan history.</span></span>  
  
 <span data-ttu-id="9a698-123">**記錄到遠端伺服器**</span><span class="sxs-lookup"><span data-stu-id="9a698-123">**Log to remote server**</span></span>  
 <span data-ttu-id="9a698-124">將維護計畫記錄記錄到遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="9a698-124">Logs maintenance plan history to a remote server.</span></span>  
  
 <span data-ttu-id="9a698-125">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="9a698-125">**Connection**</span></span>  
 <span data-ttu-id="9a698-126">指定記錄到遠端伺服器使用的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="9a698-126">Specifies the connection information to use when logging to a remote server.</span></span>  
  
 <span data-ttu-id="9a698-127">**新增**</span><span class="sxs-lookup"><span data-stu-id="9a698-127">**New**</span></span>  
 <span data-ttu-id="9a698-128">顯示 [連接屬性]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9a698-128">Displays the **Connection Properties** dialog box.</span></span> <span data-ttu-id="9a698-129">用來設定記錄到遠端伺服器的新連接資訊。</span><span class="sxs-lookup"><span data-stu-id="9a698-129">Used to configure new connection information for logging to a remote server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a698-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a698-130">See Also</span></span>  
 <span data-ttu-id="9a698-131">[維護計畫](maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="9a698-131">[Maintenance Plans](maintenance-plans.md) </span></span>  
 [<span data-ttu-id="9a698-132">Database Mail</span><span class="sxs-lookup"><span data-stu-id="9a698-132">Database Mail</span></span>](../database-mail/database-mail.md)  
  
  
