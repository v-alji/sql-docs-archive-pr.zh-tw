---
title: 執行 Reporting Services 指令碼檔案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], running
ms.assetid: 0de4995c-85ec-4d4c-aaef-fbd30edfb20f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c787d860838a57a2bd0f51aac1e9159833f038d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704809"
---
# <a name="run-a-reporting-services-script-file"></a><span data-ttu-id="39b22-102">執行 Reporting Services 指令碼檔案</span><span class="sxs-lookup"><span data-stu-id="39b22-102">Run a Reporting Services Script File</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="39b22-103">指令碼檔案是使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 指令碼環境 (RS.exe)，從命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="39b22-103">script files are run from the command prompt using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] script environment (RS.exe).</span></span> <span data-ttu-id="39b22-104">RS.exe 包含多個命令提示字元引數供您使用。</span><span class="sxs-lookup"><span data-stu-id="39b22-104">RS.exe has many command prompt arguments available for you to use.</span></span> <span data-ttu-id="39b22-105">如需命令提示字元選項的詳細資訊，請參閱 [RS.exe 公用程式 &#40;SSRS&#41;](rs-exe-utility-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="39b22-105">For more information about the command prompt options, see [RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md).</span></span> <span data-ttu-id="39b22-106">如需其他指令碼範例，請參閱 [SQL Server Reporting Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=177889)。</span><span class="sxs-lookup"><span data-stu-id="39b22-106">For more script samples, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="sample-command-lines"></a><span data-ttu-id="39b22-107">範例命令列</span><span class="sxs-lookup"><span data-stu-id="39b22-107">Sample Command Lines</span></span>  
  
-   <span data-ttu-id="39b22-108">在指令碼環境中執行 Script.rss 以指定目標報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="39b22-108">Run Script.rss in the script environment designating the target report server.</span></span> <span data-ttu-id="39b22-109">預設會套用 Windows 驗證：</span><span class="sxs-lookup"><span data-stu-id="39b22-109">Windows Authentication is applied by default:</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver  
    ```  
  
-   <span data-ttu-id="39b22-110">在指令碼環境中執行 Script.rss 以指定驗證 Web 服務呼叫的使用者名稱和密碼：</span><span class="sxs-lookup"><span data-stu-id="39b22-110">Run Script.rss in the script environment specifying a user name and password for authenticating the Web service calls:</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -u myusername -p mypassword  
    ```  
  
-   <span data-ttu-id="39b22-111">在指令碼環境中執行 Script.rss 以指定 30 秒的伺服器逾時：</span><span class="sxs-lookup"><span data-stu-id="39b22-111">Run Script.rss in the script environment specifying a server time-out of 30 seconds:</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -l 30  
    ```  
  
-   <span data-ttu-id="39b22-112">在指令碼環境中執行 Script.rss 以指定稱為 *report*的全域指令碼 (Global Script) 變數。</span><span class="sxs-lookup"><span data-stu-id="39b22-112">Run Script.rss in the script environment specifying a global script variable called *report*.</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -v report="Company Sales"  
    ```  
  
-   <span data-ttu-id="39b22-113">在指令碼環境中執行 Script.rss 以指定指令碼檔案中的 Web 服務作業以批次方式執行。</span><span class="sxs-lookup"><span data-stu-id="39b22-113">Run Script.rss in the script environment specifying that the Web service operations in the script file are run as a batch.</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -b  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="39b22-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39b22-114">See Also</span></span>  
 [<span data-ttu-id="39b22-115">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="39b22-115">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
