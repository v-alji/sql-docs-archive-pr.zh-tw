---
title: 參數資訊 (IntelliSense)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Parameter Info option [IntelliSense]
- stored function parameter completion [Intellisense]
- language references [SQL Server]
- IntelliSense [SQL Server], Parameter Info option
ms.assetid: 56c2aac9-c65c-4679-b62c-d9f689876dde
author: rothja
ms.author: jroth
ms.openlocfilehash: b7e5e7496753006808f75378182db0d3cb606d4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599460"
---
# <a name="parameter-info-intellisense"></a><span data-ttu-id="e72aa-102">參數資訊 (IntelliSense)</span><span class="sxs-lookup"><span data-stu-id="e72aa-102">Parameter Info (IntelliSense)</span></span>
  <span data-ttu-id="e72aa-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense 的 [參數資訊]  選項會開啟一個參數清單，為您提供函數或預存程序所需之參數數目、名稱和類型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e72aa-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense **Parameter Info** option opens a parameters list that provides information about the number, names, and types of the parameters that are required by a function or stored procedure.</span></span> <span data-ttu-id="e72aa-104">粗體的參數表示當您輸入函數或預存程序時所需的下一個參數。</span><span class="sxs-lookup"><span data-stu-id="e72aa-104">The parameter in bold indicates the next parameter that is required as you type a function or stored procedure.</span></span>  
  
 <span data-ttu-id="e72aa-105">巢狀函數也有參數清單。</span><span class="sxs-lookup"><span data-stu-id="e72aa-105">The parameter list is also displayed for nested functions.</span></span> <span data-ttu-id="e72aa-106">如果您將函數當作參數輸入到另一個函數中，參數清單會顯示內部函數的參數。</span><span class="sxs-lookup"><span data-stu-id="e72aa-106">If you type a function as a parameter to another function, the parameter list displays the parameters for the inner function.</span></span> <span data-ttu-id="e72aa-107">之後，當內部函數參數清單完成時，參數清單會回復成顯示外部函數參數。</span><span class="sxs-lookup"><span data-stu-id="e72aa-107">Then, when the inner function parameter list is complete, the parameter list reverts to displaying the outer function parameters.</span></span>  
  
#### <a name="to-view-parameter-info-for-functions-or-stored-procedures"></a><span data-ttu-id="e72aa-108">檢視函數或預存程序的參數資訊</span><span class="sxs-lookup"><span data-stu-id="e72aa-108">To view Parameter Info for functions or stored procedures</span></span>  
  
1.  <span data-ttu-id="e72aa-109">在函數名稱之後，依照通常開啟參數清單時的相同輸入方式，輸入一個左括號。</span><span class="sxs-lookup"><span data-stu-id="e72aa-109">After the name of a function, type an open parenthesis as you usually type to open the parameters list.</span></span> <span data-ttu-id="e72aa-110">輸入預存程序的名稱之後，以您通常輸入的方式輸入一個空格，即可取得有關程序參數的資訊。</span><span class="sxs-lookup"><span data-stu-id="e72aa-110">After you type the name of a stored procedure, type a space as you usually type to obtain information about the procedure parameters.</span></span>  
  
     <span data-ttu-id="e72aa-111">此時 IntelliSense 會在插入點之下，在快顯視窗中，顯示函數的完整宣告或預存程序的參數。</span><span class="sxs-lookup"><span data-stu-id="e72aa-111">IntelliSense displays the complete declaration for the function or the parameters for a stored procedure in a pop-up window just under the insertion point.</span></span> <span data-ttu-id="e72aa-112">清單中的第一個參數會以粗體字顯示。</span><span class="sxs-lookup"><span data-stu-id="e72aa-112">The first parameter in the list appears in bold.</span></span>  
  
2.  <span data-ttu-id="e72aa-113">當您輸入參數時，會變更粗體字型來反映您必須輸入的下一個參數。</span><span class="sxs-lookup"><span data-stu-id="e72aa-113">As you type the parameters, the bold font changes to reflect the next parameter that you need to enter.</span></span>  
  
3.  <span data-ttu-id="e72aa-114">您隨時可以按 ESC 來關閉這份清單，或繼續輸入直到函數完成。</span><span class="sxs-lookup"><span data-stu-id="e72aa-114">Press ESC at any time to close the list, or continue typing until you have completed the function.</span></span>  
  
     <span data-ttu-id="e72aa-115">如果是函數，當您輸入右括號時，也會關閉參數清單。</span><span class="sxs-lookup"><span data-stu-id="e72aa-115">For a function, if you type the closing parenthesis you also close the parameter list.</span></span>  
  
#### <a name="to-manually-start-parameter-info"></a><span data-ttu-id="e72aa-116">手動啟動參數資訊</span><span class="sxs-lookup"><span data-stu-id="e72aa-116">To manually start Parameter Info</span></span>  
  
1.  <span data-ttu-id="e72aa-117">按一下 [編輯]  功能表，選取 [IntelliSense]  ，然後選取 [參數資訊]  。</span><span class="sxs-lookup"><span data-stu-id="e72aa-117">On the **Edit** menu, select **IntelliSense** and then select **Parameter Info**.</span></span>  
  
2.  <span data-ttu-id="e72aa-118">按下 CTRL+SHIFT+SPACE 鍵盤快速鍵。</span><span class="sxs-lookup"><span data-stu-id="e72aa-118">Press the CTRL+SHIFT+SPACE keyboard shortcut.</span></span>  
  
 <span data-ttu-id="e72aa-119">如需詳細資訊，請參閱[設定 IntelliSense &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="e72aa-119">For more information, see [Configure IntelliSense &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e72aa-120">[參數資訊]  選項僅適用於 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器和 XML 查詢編輯器。</span><span class="sxs-lookup"><span data-stu-id="e72aa-120">The **Parameter Info** option is available only for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor and the XML Query Editor.</span></span>  
  
  
