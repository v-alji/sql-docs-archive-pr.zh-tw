---
title: 完成 Transact-SQL 程式碼片段
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], completing snippets
- snippets [Transact-SQL], completing
- Transact-SQL snippets, completing
ms.assetid: a8316a58-bb57-485e-845f-84c23360314c
author: rothja
ms.author: jroth
ms.openlocfilehash: d90c77f72ba8ce80d26503645d9b04d795f5e503
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594448"
---
# <a name="complete-transact-sql-snippets"></a><span data-ttu-id="fda6d-102">完成 Transact-SQL 程式碼片段</span><span class="sxs-lookup"><span data-stu-id="fda6d-102">Complete Transact-SQL Snippets</span></span>
  <span data-ttu-id="fda6d-103">一旦您已經將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼片段插入指令碼之後，就可以編輯片段的內容，以便建立完整的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="fda6d-103">Once a [!INCLUDE[tsql](../../includes/tsql-md.md)] code snippet has been inserted into a script, you edit the contents of the snippet to build a complete [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
## <a name="completing-snippets"></a><span data-ttu-id="fda6d-104">完成片段</span><span class="sxs-lookup"><span data-stu-id="fda6d-104">Completing Snippets</span></span>  
 <span data-ttu-id="fda6d-105">當您將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 片段加入至指令碼時，已插入的片段陳述式就會具有一個或多個反白顯示的取代點。</span><span class="sxs-lookup"><span data-stu-id="fda6d-105">When you add a [!INCLUDE[tsql](../../includes/tsql-md.md)] snippet to your script, the inserted snippet statement has one or more replacement points, which are highlighted.</span></span> <span data-ttu-id="fda6d-106">如果您將滑鼠指標停留在取代點上方，就會顯示工具提示，其中說明您可以指定的語法元素。</span><span class="sxs-lookup"><span data-stu-id="fda6d-106">If you rest your mouse pointer on a replacement point, a tooltip appears with a description of the syntax element you can specify.</span></span> <span data-ttu-id="fda6d-107">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器會將該片段視為不同於周圍的指令碼，直到您關閉來源檔案為止。</span><span class="sxs-lookup"><span data-stu-id="fda6d-107">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor recognizes the snippet as separate from the surrounding script until you close the source file.</span></span> <span data-ttu-id="fda6d-108">此外，取代點會維持作用中狀態，直到您關閉來源檔案為止。</span><span class="sxs-lookup"><span data-stu-id="fda6d-108">The replacement points remain active until you close the source file.</span></span>  
  
 <span data-ttu-id="fda6d-109">您也可以將其他語法元素加入至片段所插入的範本程式碼。</span><span class="sxs-lookup"><span data-stu-id="fda6d-109">You can also add additional syntax elements to the template code inserted by a snippet.</span></span> <span data-ttu-id="fda6d-110">例如，「建立資料表」片段範本會產生兩個資料行定義。您必須加入其他資料行定義，以便建立具有兩個以上資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="fda6d-110">For example, the Create Table snippet template generates two column definitions; you must add additional column definitions to create a table with more than two columns.</span></span>  
  
#### <a name="completing-the-snippet-statement"></a><span data-ttu-id="fda6d-111">完成片段陳述式</span><span class="sxs-lookup"><span data-stu-id="fda6d-111">Completing the Snippet Statement</span></span>  
  
1.  <span data-ttu-id="fda6d-112">您可以使用 TAB 鍵，從某個取代點移至下一個取代點。</span><span class="sxs-lookup"><span data-stu-id="fda6d-112">Use the TAB key to move from one replacement point to the next.</span></span> <span data-ttu-id="fda6d-113">您可以使用 SHIFT+TAB，移至上一個取代點。</span><span class="sxs-lookup"><span data-stu-id="fda6d-113">Use SHIFT+TAB to move to the previous replacement point.</span></span>  
  
2.  <span data-ttu-id="fda6d-114">按一下 CTRL+SPACE 叫用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="fda6d-114">Click CTRL+SPACE to invoke IntelliSense.</span></span>  
  
3.  <span data-ttu-id="fda6d-115">從清單中選取項目，或輸入您選擇的取代項目。</span><span class="sxs-lookup"><span data-stu-id="fda6d-115">Select an item from the list, or type a replacement of your choice.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fda6d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fda6d-116">See Also</span></span>  
 <span data-ttu-id="fda6d-117">[插入 Transact-SQL 程式碼片段](insert-transact-sql-snippets.md) </span><span class="sxs-lookup"><span data-stu-id="fda6d-117">[Insert Transact-SQL Snippets](insert-transact-sql-snippets.md) </span></span>  
 [<span data-ttu-id="fda6d-118">插入範圍陳述式 Transact-SQL 程式碼片段</span><span class="sxs-lookup"><span data-stu-id="fda6d-118">Insert Surround-with Transact-SQL snippets</span></span>](insert-surround-with-transact-sql-snippets.md)  
  
  
