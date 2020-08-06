---
title: 快速資訊 (IntelliSense)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Quick Info option [IntelliSense]
- declarations [IntelliSense]
- IntelliSense [SQL Server], Quick Info
- identifier declarations [IntelliSense]
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
author: rothja
ms.author: jroth
ms.openlocfilehash: 4f173c57438301702a8e51acf4531c655fde0cc8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710557"
---
# <a name="quick-info-intellisense"></a><span data-ttu-id="276e3-102">快速資訊 (IntelliSense)</span><span class="sxs-lookup"><span data-stu-id="276e3-102">Quick Info (IntelliSense)</span></span>
  <span data-ttu-id="276e3-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense 的 **[快速資訊]** 選項會顯示程式碼中之任何識別碼的完整宣告。</span><span class="sxs-lookup"><span data-stu-id="276e3-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense **Quick Info** option displays the complete declaration for any identifier in your code.</span></span> <span data-ttu-id="276e3-104">當您將滑鼠指標移到識別碼上方時，系統就會在黃色的快顯視窗中顯示它的宣告。</span><span class="sxs-lookup"><span data-stu-id="276e3-104">When you move the mouse pointer over an identifier, its declaration is displayed in a yellow pop-up window.</span></span> <span data-ttu-id="276e3-105">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，資料庫引擎和 XML 查詢編輯器中會提供 **[快速諮詢]** 。</span><span class="sxs-lookup"><span data-stu-id="276e3-105">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **Quick Info** is available in the Database Engine and XML Query Editors.</span></span>  
  
## <a name="transact-sql-quick-info"></a><span data-ttu-id="276e3-106">Transact-SQL 快速諮詢</span><span class="sxs-lookup"><span data-stu-id="276e3-106">Transact-SQL Quick Info</span></span>  
 <span data-ttu-id="276e3-107">**[快速諮詢]** 會在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器中顯示兩種資訊。</span><span class="sxs-lookup"><span data-stu-id="276e3-107">**Quick Info** displays two types of information in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="276e3-108">不是處於偵錯模式時， **[快速諮詢]** 會顯示運算式宣告。</span><span class="sxs-lookup"><span data-stu-id="276e3-108">When not in debug mode, **Quick Info** displays the expression declaration.</span></span> <span data-ttu-id="276e3-109">處於偵錯模式時， **[快速諮詢]** 會改為顯示運算式的名稱及其目前值。</span><span class="sxs-lookup"><span data-stu-id="276e3-109">When in debug mode, **Quick Info** instead displays the name of the expression and its current value.</span></span>  
  
 <span data-ttu-id="276e3-110">在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器中， **[快速資訊]** 僅適用於 IntelliSense 支援的這些 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語法部分。</span><span class="sxs-lookup"><span data-stu-id="276e3-110">In the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor, **Quick Info** is available only for those parts of the [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax that IntelliSense supports.</span></span> <span data-ttu-id="276e3-111">例如，如果您將滑鼠指標移到某個物件的識別碼上方，但是該物件具有 IntelliSense 不支援的資料類型，[快速資訊]  快顯視窗就會包含表示不支援此資料類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="276e3-111">For example, if you move the mouse pointer over the identifier for an object that has a data type that IntelliSense does not support, the **Quick Info** pop-up window contains a message that states that the data type is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="276e3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="276e3-112">See Also</span></span>  
 [<span data-ttu-id="276e3-113">IntelliSense 所支援的 Transact-SQL 語法</span><span class="sxs-lookup"><span data-stu-id="276e3-113">Transact-SQL Syntax Supported by IntelliSense</span></span>](transact-sql-syntax-supported-by-intellisense.md)  
  
  
