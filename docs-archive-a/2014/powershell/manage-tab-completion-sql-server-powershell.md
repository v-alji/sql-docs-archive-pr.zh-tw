---
title: 管理 TAB 鍵自動完成 (SQL Server PowerShell) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 6296848a-890f-4ad3-8d9f-92ed6a79aa00
author: stevestein
ms.author: sstein
ms.openlocfilehash: 72bcf96245c536d6ea444bc1d7964b7579e793c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606940"
---
# <a name="manage-tab-completion-sql-server-powershell"></a><span data-ttu-id="ba576-102">管理完成索引標籤 (SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="ba576-102">Manage Tab Completion (SQL Server PowerShell)</span></span>
  <span data-ttu-id="ba576-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 嵌入式管理單元引進三個變數 (`$SqlServerMaximumTabCompletion`、`$SqlServerMaximumChildItems` 及 `$SqlServerIncludeSystemObjects`)，以控制 Windows PowerShell Tab-Completion。</span><span class="sxs-lookup"><span data-stu-id="ba576-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins introduce three variables (`$SqlServerMaximumTabCompletion`, `$SqlServerMaximumChildItems`, and `$SqlServerIncludeSystemObjects`) to control Windows PowerShell tab completion.</span></span> <span data-ttu-id="ba576-104">Tab-Completion 透過傳回其名稱開頭為所輸入字串的項目表，來減少必須輸入的資料量。</span><span class="sxs-lookup"><span data-stu-id="ba576-104">Tab completion reduces the amount of typing you must do by returning tables of items whose names start with the string you are typing.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="ba576-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="ba576-105">Before You Begin</span></span>  
 <span data-ttu-id="ba576-106">如果使用 Windows PowerShell Tab-Completion，當您已輸入一部分的路徑或 Cmdlet 名稱時，可以按 Tab 鍵來取得名稱符合您已輸入之項目的項目清單。</span><span class="sxs-lookup"><span data-stu-id="ba576-106">With Windows PowerShell tab-completion, when you have typed part of a path or cmdlet name, you can hit the Tab key to get a list of the items whose names match what you have already typed.</span></span> <span data-ttu-id="ba576-107">然後您可以從清單中選取想要的項目，而不必輸入名稱的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="ba576-107">You can then select the item you want from the list without having to type the rest of the name.</span></span>  
  
 <span data-ttu-id="ba576-108">如果您正在擁有許多物件的資料庫中工作，索引標籤完成的清單會變得很大。</span><span class="sxs-lookup"><span data-stu-id="ba576-108">If you are working in a database that has a lot of objects, the tab-completion lists can become very large.</span></span> <span data-ttu-id="ba576-109">某些 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件類型 (例如檢視表) 也會有大量的系統物件。</span><span class="sxs-lookup"><span data-stu-id="ba576-109">Some [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] object types, such as views, also have large numbers of system objects.</span></span>  
  
 <span data-ttu-id="ba576-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 嵌入式管理單元引進三個系統變數，可用來控制 TAB 鍵自動完成功能和 **Get-ChildItem**所呈現的資訊量。</span><span class="sxs-lookup"><span data-stu-id="ba576-110">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] snap-ins introduces three system variables that you can use to control the amount of information presented by tab-completion and **Get-ChildItem**.</span></span>  
  
 <span data-ttu-id="ba576-111">**$SqlServerMaximumTabCompletion =** *n*</span><span class="sxs-lookup"><span data-stu-id="ba576-111">**$SqlServerMaximumTabCompletion =** *n*</span></span>  
 <span data-ttu-id="ba576-112">指定 Tab-Completion 清單中要包含的最大物件數目。</span><span class="sxs-lookup"><span data-stu-id="ba576-112">Specifies the maximum number of objects to include in a tab-completion list.</span></span> <span data-ttu-id="ba576-113">如果您在有 *n* 個物件以上的路徑節點上選取 Tab 鍵，TAB 鍵自動完成清單就會在 *n*處截斷。</span><span class="sxs-lookup"><span data-stu-id="ba576-113">If you select Tab at a path node having more than *n* objects, the tab-completion list is truncated at *n*.</span></span> <span data-ttu-id="ba576-114">*n* 為整數。</span><span class="sxs-lookup"><span data-stu-id="ba576-114">*n* is an integer.</span></span> <span data-ttu-id="ba576-115">預設值為 0，表示列出的物件數沒有限制。</span><span class="sxs-lookup"><span data-stu-id="ba576-115">0 is the default setting, and means there is no limit to the number of objects listed.</span></span>  
  
 <span data-ttu-id="ba576-116">**$SqlServerMaximumChildItems =** *n*</span><span class="sxs-lookup"><span data-stu-id="ba576-116">**$SqlServerMaximumChildItems =** *n*</span></span>  
 <span data-ttu-id="ba576-117">指定 **Get-ChildItem**所顯示的最大物件數。</span><span class="sxs-lookup"><span data-stu-id="ba576-117">Specifies the maximum number of objects displayed by **Get-ChildItem**.</span></span> <span data-ttu-id="ba576-118">如果 **Get-ChildItem** 在具有 *n* 個物件以上的路徑節點上執行，此清單會在 *n*處截斷。</span><span class="sxs-lookup"><span data-stu-id="ba576-118">If **Get-ChildItem** is run at a path node having more than *n* objects, the list is truncated at *n*.</span></span> <span data-ttu-id="ba576-119">*n* 為整數。</span><span class="sxs-lookup"><span data-stu-id="ba576-119">*n* is an integer.</span></span> <span data-ttu-id="ba576-120">預設值為 0，表示列出的物件數沒有限制。</span><span class="sxs-lookup"><span data-stu-id="ba576-120">0 is the default setting, and means there is no limit to the number of objects listed.</span></span>  
  
 <span data-ttu-id="ba576-121">**$SqlServerIncludeSystemObjects =** { **$True** | **$False** }</span><span class="sxs-lookup"><span data-stu-id="ba576-121">**$SqlServerIncludeSystemObjects =** { **$True** | **$False** }</span></span>  
 <span data-ttu-id="ba576-122">如果設定為 **$True**，表示系統物件是透過 TAB 鍵自動完成功能和 **Get-ChildItem**所顯示。</span><span class="sxs-lookup"><span data-stu-id="ba576-122">If **$True**, system objects are displayed by tab-completion and **Get-ChildItem**.</span></span> <span data-ttu-id="ba576-123">如果設定為 **$False**，表示未顯示任何系統物件。</span><span class="sxs-lookup"><span data-stu-id="ba576-123">If **$False**, no system objects are displayed.</span></span> <span data-ttu-id="ba576-124">預設設定為 [ **$False**]。</span><span class="sxs-lookup"><span data-stu-id="ba576-124">The default setting is **$False**.</span></span>  
  
## <a name="set-the-sql-server-tab-completion-variables"></a><span data-ttu-id="ba576-125">設定 SQL Server Tab-Completion 變數</span><span class="sxs-lookup"><span data-stu-id="ba576-125">Set the SQL Server Tab Completion Variables</span></span>  
 <span data-ttu-id="ba576-126">針對任何想要變更其預設值的變數，將變數設定為新值。</span><span class="sxs-lookup"><span data-stu-id="ba576-126">For any of the variables you want to change from the default value, set the variable to the new value.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="ba576-127">範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="ba576-127">Example (PowerShell)</span></span>  
 <span data-ttu-id="ba576-128">下列範例會設定所有的三個變數，並列出其設定：</span><span class="sxs-lookup"><span data-stu-id="ba576-128">The following example sets all three variables and lists their settings:</span></span>  
  
```powershell
$SqlServerMaximumTabCompletion = 20  
$SqlServerMaximumChildItems = 10  
$SqlServerIncludeSystemObjects = $False  
dir variable:sqlserver*  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba576-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba576-129">See Also</span></span>  
 [<span data-ttu-id="ba576-130">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba576-130">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
