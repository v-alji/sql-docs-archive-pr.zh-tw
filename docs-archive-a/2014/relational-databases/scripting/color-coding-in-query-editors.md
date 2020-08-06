---
title: 查詢編輯器中的色彩編碼
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio], color coding
- color coding [Query Editor]
ms.assetid: 802882dc-c997-4e3f-8a01-994bb43169ae
author: rothja
ms.author: jroth
ms.openlocfilehash: f23b37cec051b52082cdb310a134a4603423b8c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594450"
---
# <a name="color-coding-in-query-editors"></a><span data-ttu-id="50b7f-102">查詢編輯器中的色彩編碼</span><span class="sxs-lookup"><span data-stu-id="50b7f-102">Color Coding in Query Editors</span></span>
  <span data-ttu-id="50b7f-103">在程式碼編輯器中輸入的文字會指派至類別目錄；每一個類別目錄都會以色彩識別。</span><span class="sxs-lookup"><span data-stu-id="50b7f-103">The text entered in the code editors is assigned a category; each category is identified by a color.</span></span> <span data-ttu-id="50b7f-104">這些色彩可協助您快速地找到程式碼中的文字。</span><span class="sxs-lookup"><span data-stu-id="50b7f-104">The colors help you quickly find text in your code.</span></span> <span data-ttu-id="50b7f-105">例如，註解會以深綠色突顯出來。</span><span class="sxs-lookup"><span data-stu-id="50b7f-105">For example, comments stand out in dark green.</span></span> <span data-ttu-id="50b7f-106">下表將列出最常見的色彩。</span><span class="sxs-lookup"><span data-stu-id="50b7f-106">The following table lists the most common colors.</span></span> <span data-ttu-id="50b7f-107">您可以檢視色彩及其類別目錄的完整清單，也可以使用 [工具]  和 [選項]  功能表來設定自訂的色彩配置。</span><span class="sxs-lookup"><span data-stu-id="50b7f-107">You can view the whole list of colors and their categories, and configure a custom color scheme by using the **Tools**, **Options** menu.</span></span> <span data-ttu-id="50b7f-108">如需如何變更預設色彩的詳細資訊，請參閱 [變更字型色彩、大小與樣式](change-font-color-size-and-style.md)。</span><span class="sxs-lookup"><span data-stu-id="50b7f-108">For more information about how to change the default colors, see [Change Font Color, Size, and Style](change-font-color-size-and-style.md).</span></span>  
  
## <a name="default-code-colors"></a><span data-ttu-id="50b7f-109">預設程式碼色彩</span><span class="sxs-lookup"><span data-stu-id="50b7f-109">Default Code Colors</span></span>  
  
|<span data-ttu-id="50b7f-110">Color</span><span class="sxs-lookup"><span data-stu-id="50b7f-110">Color</span></span>|<span data-ttu-id="50b7f-111">類別</span><span class="sxs-lookup"><span data-stu-id="50b7f-111">Category</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="50b7f-112">紅色</span><span class="sxs-lookup"><span data-stu-id="50b7f-112">Red</span></span>|<span data-ttu-id="50b7f-113">SQL 字串</span><span class="sxs-lookup"><span data-stu-id="50b7f-113">SQL string</span></span>|  
|<span data-ttu-id="50b7f-114">深綠色</span><span class="sxs-lookup"><span data-stu-id="50b7f-114">Dark green</span></span>|<span data-ttu-id="50b7f-115">註解</span><span class="sxs-lookup"><span data-stu-id="50b7f-115">Comment</span></span>|  
|<span data-ttu-id="50b7f-116">銀底黑色</span><span class="sxs-lookup"><span data-stu-id="50b7f-116">Black on silver background</span></span>|<span data-ttu-id="50b7f-117">SQLCMD 命令</span><span class="sxs-lookup"><span data-stu-id="50b7f-117">SQLCMD command</span></span>|  
|<span data-ttu-id="50b7f-118">桃紅色</span><span class="sxs-lookup"><span data-stu-id="50b7f-118">Magenta</span></span>|<span data-ttu-id="50b7f-119">系統函式</span><span class="sxs-lookup"><span data-stu-id="50b7f-119">System function</span></span>|  
|<span data-ttu-id="50b7f-120">綠色</span><span class="sxs-lookup"><span data-stu-id="50b7f-120">Green</span></span>|<span data-ttu-id="50b7f-121">系統資料表、檢視或資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="50b7f-121">System table, view, or table-valued function.</span></span> <span data-ttu-id="50b7f-122">此外，還包括系統結構描述 sys 與 INFORMATION_SCHEMA。</span><span class="sxs-lookup"><span data-stu-id="50b7f-122">Also, the system schemas sys and INFORMATION_SCHEMA.</span></span>|  
|<span data-ttu-id="50b7f-123">藍色</span><span class="sxs-lookup"><span data-stu-id="50b7f-123">Blue</span></span>|<span data-ttu-id="50b7f-124">關鍵字</span><span class="sxs-lookup"><span data-stu-id="50b7f-124">Keyword</span></span>|  
|<span data-ttu-id="50b7f-125">藍綠色</span><span class="sxs-lookup"><span data-stu-id="50b7f-125">Teal</span></span>|<span data-ttu-id="50b7f-126">行號或範本參數</span><span class="sxs-lookup"><span data-stu-id="50b7f-126">Line numbers or template parameter</span></span>|  
|<span data-ttu-id="50b7f-127">暗紅色</span><span class="sxs-lookup"><span data-stu-id="50b7f-127">Maroon</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="50b7f-128">預存程序</span><span class="sxs-lookup"><span data-stu-id="50b7f-128">stored procedure</span></span>|  
|<span data-ttu-id="50b7f-129">深灰色</span><span class="sxs-lookup"><span data-stu-id="50b7f-129">Dark gray</span></span>|<span data-ttu-id="50b7f-130">操作員</span><span class="sxs-lookup"><span data-stu-id="50b7f-130">Operators</span></span>|  
  
## <a name="status-bar"></a><span data-ttu-id="50b7f-131">狀態列</span><span class="sxs-lookup"><span data-stu-id="50b7f-131">Status Bar</span></span>  
 <span data-ttu-id="50b7f-132">您可以在 [物件總管] 中設定已註冊的伺服器或 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 伺服器，讓 [ [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器] 狀態列中顯示不同的色彩。</span><span class="sxs-lookup"><span data-stu-id="50b7f-132">You can configure registered servers or [!INCLUDE[ssDE](../../includes/ssde-md.md)] servers in Object Explorer to have different colors in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor status bar.</span></span> <span data-ttu-id="50b7f-133">這可協助您在同時開啟多個視窗時，識別每個編輯器視窗所連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="50b7f-133">This helps you identify which server each editor window is connected to when you have many windows open at the same time.</span></span> <span data-ttu-id="50b7f-134">如需設定狀態列色彩的詳細資訊，請參閱[狀態列 &#40;Database Engine 查詢編輯器&#41;](status-bar-database-engine-query-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="50b7f-134">For more information about setting status bar colors, see [Status Bar &#40;Database Engine Query Editor&#41;](status-bar-database-engine-query-editor.md).</span></span>  
  
 <span data-ttu-id="50b7f-135">某些類型的編輯器不會顯示狀態列，或不支援多種色彩。</span><span class="sxs-lookup"><span data-stu-id="50b7f-135">Some types of editors do not display the status bar, or do not support multiple colors.</span></span>  
  
  
