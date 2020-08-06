---
title: " (文字編輯器的選項-Transact-sql-IntelliSense) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Advanced
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Advanced
dev_langs:
- TSQL
ms.assetid: 1855d916-5bf9-4d94-b0fb-9f9bb05ff950
author: rothja
ms.author: jroth
ms.openlocfilehash: 2d8f9c865516dc5e4c0ddadbdc908a9b4c8ec366
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597994"
---
# <a name="options-text-editor-transact-sql-intellisense"></a><span data-ttu-id="dbc0b-102"> (文字編輯器的選項-Transact-sql-IntelliSense) </span><span class="sxs-lookup"><span data-stu-id="dbc0b-102">Options (Text Editor-Transact-SQL-IntelliSense)</span></span>
  <span data-ttu-id="dbc0b-103">**[選項]** 對話方塊可讓您變更 [!INCLUDE[ssDE](../includes/ssde-md.md)] 查詢編輯器的 IntelliSense 設定。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-103">The **Options** dialog box lets you change the IntelliSense settings for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="dbc0b-104">在 [工具]\*\*\*\* 功能表上，按一下 [選項]\*\*\*\*，依序展開 [文字編輯器]\*\*\*\* 資料夾和 [Transact-SQL]\*\*\*\* 資料夾，然後按一下 [進階]\*\*\*\*，即可使用這些設定。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-104">These settings are available when, on the **Tools** menu, you click **Options**, expand the **Text Editor** folder, expand the **Transact-SQL** folder, and then click **Advanced**.</span></span>  
  
## <a name="transact-sql-intellisense-settings"></a><span data-ttu-id="dbc0b-105">Transact-SQL IntelliSense 設定</span><span class="sxs-lookup"><span data-stu-id="dbc0b-105">Transact-SQL IntelliSense Settings</span></span>  
 <span data-ttu-id="dbc0b-106">為 [!INCLUDE[ssDE](../includes/ssde-md.md)] 查詢編輯器指定 IntelliSense 選項。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-106">Specifies the IntelliSense options for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor.</span></span>  
  
### <a name="enable-intellisense"></a><span data-ttu-id="dbc0b-107">啟用 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="dbc0b-107">Enable IntelliSense</span></span>  
 <span data-ttu-id="dbc0b-108">啟用 IntelliSense 功能。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-108">Enables the IntelliSense features.</span></span> <span data-ttu-id="dbc0b-109">當此方塊未選取時，就無法使用特定的 IntelliSense 選項。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-109">When this box is not selected, the specific IntelliSense options are unavailable.</span></span> <span data-ttu-id="dbc0b-110">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-110">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="dbc0b-111">**底線錯誤**</span><span class="sxs-lookup"><span data-stu-id="dbc0b-111">**Underline errors**</span></span>  
 <span data-ttu-id="dbc0b-112">在查詢視窗中識別 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式內的語法和語意錯誤。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-112">Identifies syntax and semantic errors in [!INCLUDE[tsql](../includes/tsql-md.md)] statements in the query window.</span></span> <span data-ttu-id="dbc0b-113">所有的錯誤和警告都會以紅色出現。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-113">All errors and warnings appear in red.</span></span> <span data-ttu-id="dbc0b-114">只有在已經實作 IntelliSense 的 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式中，才會支援警告和錯誤。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-114">Errors and warnings are supported only for the [!INCLUDE[tsql](../includes/tsql-md.md)] statements for which IntelliSense has been implemented.</span></span> <span data-ttu-id="dbc0b-115">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-115">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="dbc0b-116">**大綱陳述式**</span><span class="sxs-lookup"><span data-stu-id="dbc0b-116">**Outline statements**</span></span>  
 <span data-ttu-id="dbc0b-117">在檔案開啟時，啟用大綱功能。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-117">Enables the outlining feature when a file is opened.</span></span> <span data-ttu-id="dbc0b-118">這會建立可摺疊的 [!INCLUDE[tsql](../includes/tsql-md.md)] 程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-118">This creates collapsible blocks of [!INCLUDE[tsql](../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="dbc0b-119">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-119">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="dbc0b-120">**最大指令碼大小**</span><span class="sxs-lookup"><span data-stu-id="dbc0b-120">**Maximum script size**</span></span>  
 <span data-ttu-id="dbc0b-121">指定停用 IntelliSense 功能時的大小。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-121">Specifies the size at which IntelliSense functionality is disabled.</span></span> <span data-ttu-id="dbc0b-122">如果指令碼超出指定的大小，就會發出警告訊息。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-122">If a script exceeds the specified size, a warning message is issued.</span></span> <span data-ttu-id="dbc0b-123">所有的 IntelliSense 功能 (色彩編碼除外) 都會針對該編輯器視窗而停用。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-123">All IntelliSense features, except color coding, are disabled for that editor window.</span></span> <span data-ttu-id="dbc0b-124">當刪除足夠的文字將指令碼大小縮減為這個限制以下時，IntelliSense 將會重新啟用。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-124">IntelliSense is reenabled when enough text is deleted to reduce the script size to under the limit.</span></span> <span data-ttu-id="dbc0b-125">針對大型指令碼啟用 IntelliSense 可能會讓執行速度很慢的電腦降低效能。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-125">Enabling IntelliSense for large script sizes can decrease performance on slow computers.</span></span> <span data-ttu-id="dbc0b-126">允許的大小為 100 KB、500 KB、1 MB、2 MB 和無限制。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-126">The allowed sizes are 100 KB, 500 KB, 1 MB, 2 MB, and Unlimited.</span></span> <span data-ttu-id="dbc0b-127">預設值是 1 MB。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-127">The default is 1 MB.</span></span>  
  
 <span data-ttu-id="dbc0b-128">**內建函數名稱的大小寫**</span><span class="sxs-lookup"><span data-stu-id="dbc0b-128">**Casing for built-in function names**</span></span>  
 <span data-ttu-id="dbc0b-129">指定完成清單內所包含的內建 [!INCLUDE[tsql](../includes/tsql-md.md)] 函數名稱是使用大寫字母 (如 DATEADD) 還是小寫字母 (如 dateadd)。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-129">Specifies whether the names of built-in [!INCLUDE[tsql](../includes/tsql-md.md)] functions that are included in completion lists use uppercase letters, such as DATEADD; or lowercase letters, such as dateadd.</span></span> <span data-ttu-id="dbc0b-130">選取最符合您使用之 [!INCLUDE[tsql](../includes/tsql-md.md)] 編碼慣例的選項。</span><span class="sxs-lookup"><span data-stu-id="dbc0b-130">Select the option that best matches the [!INCLUDE[tsql](../includes/tsql-md.md)] coding conventions that you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc0b-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbc0b-131">See Also</span></span>  
 [<span data-ttu-id="dbc0b-132">疑難排解 IntelliSense &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="dbc0b-132">Troubleshooting IntelliSense &#40;SQL Server Management Studio&#41;</span></span>](../relational-databases/scripting/troubleshooting-intellisense.md)  
  
  
