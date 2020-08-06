---
title: 在 [記錄事件] 視窗中查看記錄專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], viewing
- Integration Services packages, logs
- packages [Integration Services], logs
ms.assetid: c02123c3-67fc-4370-ad14-91ed259f1873
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16b6f11758d7de2c833731cd007426000a01d8ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687023"
---
# <a name="view-log-entries-in-the-log-events-window"></a><span data-ttu-id="888f9-102">檢視記錄事件視窗中的記錄項目</span><span class="sxs-lookup"><span data-stu-id="888f9-102">View Log Entries in the Log Events Window</span></span>
  <span data-ttu-id="888f9-103">此程序描述如何執行封裝並檢視封裝寫入的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="888f9-103">This procedure describes how to run a package and view the log entries it writes.</span></span> <span data-ttu-id="888f9-104">您可以即時檢視記錄項目，</span><span class="sxs-lookup"><span data-stu-id="888f9-104">You can view the log entries in real time.</span></span> <span data-ttu-id="888f9-105">也可以複製及儲存寫入 [記錄事件]\*\*\*\* 視窗中的記錄項目，以執行進一步的分析。</span><span class="sxs-lookup"><span data-stu-id="888f9-105">The log entries that are written to the **Log Events** window can also be copied and saved for further analysis.</span></span>  
  
 <span data-ttu-id="888f9-106">您不需要將記錄項目寫入記錄檔，以便將項目寫入 [記錄事件]\*\*\*\* 視窗中。</span><span class="sxs-lookup"><span data-stu-id="888f9-106">It is not necessary to write the log entries to a log to write the entries to the **Log Events** window.</span></span>  
  
### <a name="to-view-log-entries"></a><span data-ttu-id="888f9-107">檢視記錄項目</span><span class="sxs-lookup"><span data-stu-id="888f9-107">To view log entries</span></span>  
  
1.  <span data-ttu-id="888f9-108">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="888f9-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="888f9-109">在 **[SSIS]** 功能表上，按一下 **記錄事件**。</span><span class="sxs-lookup"><span data-stu-id="888f9-109">On the **SSIS** menu, click **Log Events**.</span></span> <span data-ttu-id="888f9-110">您可以將 View.LogEvents 命令對應到您在 [選項]\*\*\*\* 對話方塊的 [鍵盤]\*\*\*\* 頁面中所選擇的組合鍵，以選擇性地顯示 [記錄事件]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="888f9-110">You can optionally display the **Log Events** window by mapping the View.LogEvents command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
3.  <span data-ttu-id="888f9-111">在 [偵錯] 功能表上，按一下 [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="888f9-111">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="888f9-112">當執行階段遇到為了記錄而啟用的事件與自訂訊息時，每個事件或訊息的記錄項目都會寫入 [記錄事件]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="888f9-112">As the runtime encounters the events and custom messages that are enabled for logging, log entries for each event or message are written to the **Log Events** window.</span></span>  
  
4.  <span data-ttu-id="888f9-113">在 [偵錯] 功能表上，按一下 [停止偵錯]。</span><span class="sxs-lookup"><span data-stu-id="888f9-113">On the **Debug** menu, click **Stop Debugging**.</span></span>  
  
     <span data-ttu-id="888f9-114">記錄項目將繼續保留在 [記錄事件]\*\*\*\* 視窗中，直到您重新執行封裝、執行不同的封裝或關閉 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 為止。</span><span class="sxs-lookup"><span data-stu-id="888f9-114">The log entries remain available in the **Log Events** window until you rerun the package, run a different package, or close [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
5.  <span data-ttu-id="888f9-115">檢視 [記錄事件]\*\*\*\* 視窗中的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="888f9-115">View the log entries in the **Log Events** window.</span></span>  
  
6.  <span data-ttu-id="888f9-116">(選擇性) 按一下要複製的記錄項目，按一下滑鼠右鍵，然後按一下 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="888f9-116">Optionally, click the log entries to copy, right-click, and then click **Copy**.</span></span>  
  
7.  <span data-ttu-id="888f9-117">(選擇性) 按兩下記錄項目，然後在 [記錄項目]\*\*\*\* 對話方塊中檢視單一記錄項目的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="888f9-117">Optionally, double-click a log entry, and in the **Log Entry** dialog box, view the details for a single log entry.</span></span>  
  
8.  <span data-ttu-id="888f9-118">在 [記錄項目]\*\*\*\* 對話方塊中，按一下上下箭頭以顯示上一個或下一個記錄項目，然後按一下複製圖示來複製記錄項目。</span><span class="sxs-lookup"><span data-stu-id="888f9-118">In the **Log Entry** dialog box, click the up and down arrows to display the previous or next log entry, and click the copy icon to copy the log entry.</span></span>  
  
9. <span data-ttu-id="888f9-119">開啟文字編輯器、貼上，然後將記錄項目儲存為文字檔。</span><span class="sxs-lookup"><span data-stu-id="888f9-119">Open a text editor, paste, and then save the log entry to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="888f9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="888f9-120">See Also</span></span>  
 [<span data-ttu-id="888f9-121">Integration Services &#40;SSIS&#41; 記錄</span><span class="sxs-lookup"><span data-stu-id="888f9-121">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
