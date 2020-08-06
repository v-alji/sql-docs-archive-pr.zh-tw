---
title: 針對 IntelliSense 進行疑難排解
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- unavailable options [IntelliSense]
- IntelliSense [SQL Server], troubleshooting
- IntelliSense [SQL Server], unavailable options
- troubleshooting [IntelliSense]
ms.assetid: 4b72ffc6-aea2-4e11-ab36-fa2de4d7bcc5
author: rothja
ms.author: jroth
ms.openlocfilehash: 087baf616fc215c480ae78621623cbe1ed512b57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702642"
---
# <a name="troubleshooting-intellisense-sql-server-management-studio"></a><span data-ttu-id="e966b-102">疑難排解 IntelliSense (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e966b-102">Troubleshooting IntelliSense (SQL Server Management Studio)</span></span>
  <span data-ttu-id="e966b-103">在某些情況下，IntelliSense 選項的運作可能會不符合您的預期。</span><span class="sxs-lookup"><span data-stu-id="e966b-103">There are certain cases when the IntelliSense options might not work as you expect.</span></span>  
  
## <a name="conditions-that-affect-intellisense"></a><span data-ttu-id="e966b-104">影響 IntelliSense 的條件</span><span class="sxs-lookup"><span data-stu-id="e966b-104">Conditions That Affect IntelliSense</span></span>  
 <span data-ttu-id="e966b-105">下列條件可能會影響 IntelliSense 的行為：</span><span class="sxs-lookup"><span data-stu-id="e966b-105">The following conditions might affect the behavior of IntelliSense:</span></span>  
  
-   <span data-ttu-id="e966b-106">游標上面有程式碼發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e966b-106">There is a code error above the cursor.</span></span>  
  
     <span data-ttu-id="e966b-107">如果在插入點位置之上，有不完整的陳述式或其他編碼錯誤，IntelliSense 可能無法剖析程式碼元素，因此，將無法運作。</span><span class="sxs-lookup"><span data-stu-id="e966b-107">If there is an incomplete statement or other coding error above the location of the insertion point, IntelliSense may be unable to parse the code elements, and therefore will not work.</span></span> <span data-ttu-id="e966b-108">您可以將適當的程式碼註解化來重新啟用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="e966b-108">You can comment out the applicable code to enable IntelliSense again.</span></span>  
  
-   <span data-ttu-id="e966b-109">插入點位於程式碼註解內。</span><span class="sxs-lookup"><span data-stu-id="e966b-109">The insertion point is inside a code comment.</span></span>  
  
     <span data-ttu-id="e966b-110">如果插入點在來源檔案內的註解中，便無法使用 IntelliSense 選項。</span><span class="sxs-lookup"><span data-stu-id="e966b-110">IntelliSense options are not available when the insertion point is within a comment in your source file.</span></span>  
  
-   <span data-ttu-id="e966b-111">插入點位於字串常值內。</span><span class="sxs-lookup"><span data-stu-id="e966b-111">The insertion point is inside a string literal.</span></span>  
  
     <span data-ttu-id="e966b-112">如果插入點在括住字串常值的引號內，便無法使用 IntelliSense 選項，例如：</span><span class="sxs-lookup"><span data-stu-id="e966b-112">IntelliSense options are not available when the insertion point is inside the quotation marks around a string literal, for example:</span></span>  
  
     `WHERE FirstName LIKE 'Patri%|'`  
  
-   <span data-ttu-id="e966b-113">已關閉自動選項。</span><span class="sxs-lookup"><span data-stu-id="e966b-113">The automatic options are turned off.</span></span>  
  
     <span data-ttu-id="e966b-114">依預設，許多 IntelliSense 功能都會自動運作，但您可以停用任何功能。</span><span class="sxs-lookup"><span data-stu-id="e966b-114">Many IntelliSense features work automatically by default, but you can disable any feature.</span></span>  
  
     <span data-ttu-id="e966b-115">即使已停用自動完成陳述式的功能，您也可以使用 IntelliSense 功能。</span><span class="sxs-lookup"><span data-stu-id="e966b-115">Even when automatic statement completion is disabled, you can use an IntelliSense feature.</span></span> <span data-ttu-id="e966b-116">如需詳細資訊，請參閱[設定 IntelliSense &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="e966b-116">For more information, see [Configure IntelliSense &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md).</span></span>  
  
## <a name="database-engine-query-intellisense"></a><span data-ttu-id="e966b-117">Database Engine 查詢 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="e966b-117">Database Engine Query IntelliSense</span></span>  
 <span data-ttu-id="e966b-118">下列問題適用於 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 查詢編輯器：</span><span class="sxs-lookup"><span data-stu-id="e966b-118">The following issues apply to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Query Editor:</span></span>  
  
-   <span data-ttu-id="e966b-119">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器中的 IntelliSense 功能不支援所有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語法元素。</span><span class="sxs-lookup"><span data-stu-id="e966b-119">The IntelliSense functionality of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor does not support all [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax elements.</span></span> <span data-ttu-id="e966b-120">參數說明不支援某些物件中的參數，例如擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="e966b-120">Parameter help does not support the parameters in some objects, such as extended stored procedures.</span></span> <span data-ttu-id="e966b-121">如需詳細資訊，請參閱 [IntelliSense 所支援的 Transact-SQL 語法](transact-sql-syntax-supported-by-intellisense.md)。</span><span class="sxs-lookup"><span data-stu-id="e966b-121">For more information, see [Transact-SQL Syntax Supported by IntelliSense](transact-sql-syntax-supported-by-intellisense.md).</span></span>  
  
-   <span data-ttu-id="e966b-122">只有當 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器連接至 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 或更新版本的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 執行個體時，才能使用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="e966b-122">IntelliSense is only available when the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor is connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span> <span data-ttu-id="e966b-123">當查詢編輯器連接至舊版 [!INCLUDE[ssDE](../../includes/ssde-md.md)]時，則無法使用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="e966b-123">IntelliSense is not available when the Query Editor is connected to earlier versions of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="e966b-124">當 SQLCMD 模式開啟時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器中的 IntelliSense 卻關閉。</span><span class="sxs-lookup"><span data-stu-id="e966b-124">IntelliSense is turned off in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor when the SQLCMD mode is set on.</span></span>  
  
-   <span data-ttu-id="e966b-125">IntelliSense 功能不包含您的編輯器視窗連接到資料庫後，由另一個連接所建立的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="e966b-125">IntelliSense functionality does not cover database objects created by another connection after your editor window connected to the database.</span></span> <span data-ttu-id="e966b-126">如果 IntelliSense 功能中遺漏物件，例如完成清單，您可以選擇三個機制的其中一個，以重新整理編輯器視窗的快取物件：</span><span class="sxs-lookup"><span data-stu-id="e966b-126">If objects are missing from IntelliSense features such as completion lists, you can choose one of these three mechanisms to refresh the cache of objects for your editor window:</span></span>  
  
    -   <span data-ttu-id="e966b-127">選取 **[編輯]** 功能表，選取 **[IntelliSense]**，再選取 **[重新整理本機快取]**。</span><span class="sxs-lookup"><span data-stu-id="e966b-127">Select the **Edit** menu, select **IntelliSense**, then select **Refresh Local Cache**.</span></span>  
  
    -   <span data-ttu-id="e966b-128">使用 CTRL+Shift+R 鍵盤快速鍵。</span><span class="sxs-lookup"><span data-stu-id="e966b-128">Use the CTRL+Shift+R keyboard shortcut.</span></span>  
  
    -   <span data-ttu-id="e966b-129">中斷您的編輯視器窗與 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體的連接，然後再重新連接。</span><span class="sxs-lookup"><span data-stu-id="e966b-129">Disconnect your editor window from the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and reconnect.</span></span>  
  
-   <span data-ttu-id="e966b-130">完成清單不包含您沒有權限的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="e966b-130">Completion lists do not include database objects for which you do not have permissions.</span></span> <span data-ttu-id="e966b-131">IntelliSense 旗標會參考您沒有權限的物件。</span><span class="sxs-lookup"><span data-stu-id="e966b-131">IntelliSense flags references to objects for which you do have permissions.</span></span> <span data-ttu-id="e966b-132">例如，如果您開啟其他使用者撰寫的指令碼，對於該使用者擁有權限而您沒有權限之物件的任何參考，都會標示為不正確。</span><span class="sxs-lookup"><span data-stu-id="e966b-132">For example, if you open a script that is written by someone else, any references to objects for which that person has permissions and you do not are flagged as incorrect.</span></span>  
  
-   <span data-ttu-id="e966b-133">如果您喪失與 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體的連接，完成清單可能會停止運作。</span><span class="sxs-lookup"><span data-stu-id="e966b-133">Completion lists might stop working if you lose the connection to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="e966b-134">請重新連接到該執行個體。</span><span class="sxs-lookup"><span data-stu-id="e966b-134">Reconnect to the instance.</span></span>  
  
  
