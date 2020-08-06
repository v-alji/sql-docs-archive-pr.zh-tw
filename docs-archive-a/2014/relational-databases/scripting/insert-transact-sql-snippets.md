---
title: 插入 Transact-SQL 程式碼片段
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], snippets
- Transact-SQL snippets, code
- snippets [Transact-SQL], how to insert
ms.assetid: d66c96f4-2e84-4d79-9bfd-3635fdd98425
author: rothja
ms.author: jroth
ms.openlocfilehash: 26a7a224e700c726ee3d4437321843d45ddb6e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606219"
---
# <a name="insert-transact-sql-snippets"></a><span data-ttu-id="30ffc-102">插入 Transact-SQL 程式碼片段</span><span class="sxs-lookup"><span data-stu-id="30ffc-102">Insert Transact-SQL Snippets</span></span>
  <span data-ttu-id="30ffc-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼片段是範本，當您在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢編輯器中撰寫新的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 陳述式時可將它做為起點。</span><span class="sxs-lookup"><span data-stu-id="30ffc-103">A [!INCLUDE[tsql](../../includes/tsql-md.md)] code snippet is a template you can use as a starting point when writing new [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
## <a name="inserting-snippets"></a><span data-ttu-id="30ffc-104">插入程式碼片段</span><span class="sxs-lookup"><span data-stu-id="30ffc-104">Inserting Snippets</span></span>  
 <span data-ttu-id="30ffc-105">您可以使用 [插入程式碼片段]  功能表開啟分類的程式碼片段清單，從中選擇。</span><span class="sxs-lookup"><span data-stu-id="30ffc-105">You can use the **Insert Snippet** menu to open a categorized list of snippets to choose from.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="30ffc-106">程式碼片段包含取代點：建議與該點相關語法的文字。</span><span class="sxs-lookup"><span data-stu-id="30ffc-106">snippets contain replacement points: text that suggests the syntax relevant to that point.</span></span> <span data-ttu-id="30ffc-107">例如，CREATE TABLE 程式碼片段有資料表名稱、資料行名稱和資料行資料類型等元素的取代點。</span><span class="sxs-lookup"><span data-stu-id="30ffc-107">For example, the CREATE TABLE snippet has replacement points for elements such as the table name, column names, and column data types.</span></span> <span data-ttu-id="30ffc-108">在插入程式碼片段之後，您必須變更取代文字，以形成有效的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="30ffc-108">After inserting the snippet, you must change the replacement text to form a valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="30ffc-109">如需詳細資訊，請參閱 [完成 Transact-SQL 程式碼片段](complete-transact-sql-snippets.md)。</span><span class="sxs-lookup"><span data-stu-id="30ffc-109">For more information, see [Complete Transact-SQL Snippets](complete-transact-sql-snippets.md).</span></span>  
  
#### <a name="inserting-a-snippet-by-using-the-insert-snippet-menu"></a><span data-ttu-id="30ffc-110">藉由使用插入程式碼片段功能表，插入程式碼片段</span><span class="sxs-lookup"><span data-stu-id="30ffc-110">Inserting a Snippet by Using the Insert Snippet Menu</span></span>  
  
1.  <span data-ttu-id="30ffc-111">在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的 [查詢編輯器] 視窗中，將游標放在您想要插入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼片段的位置。</span><span class="sxs-lookup"><span data-stu-id="30ffc-111">In the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window, put the cursor where you want to insert the [!INCLUDE[tsql](../../includes/tsql-md.md)] snippet.</span></span>  
  
2.  <span data-ttu-id="30ffc-112">使用下列三種方法之一啟動程式碼片段選擇器工具提示：</span><span class="sxs-lookup"><span data-stu-id="30ffc-112">Launch the snippet picker tooltip in one of three ways:</span></span>  
  
    -   <span data-ttu-id="30ffc-113">按下 CTRL+K、CTRL+X。</span><span class="sxs-lookup"><span data-stu-id="30ffc-113">Press CTRL+K, CTRL+X.</span></span>  
  
    -   <span data-ttu-id="30ffc-114">在 [編輯]  功能表上，指向 [IntelliSense]  ，然後按一下 [插入程式碼片段]  。</span><span class="sxs-lookup"><span data-stu-id="30ffc-114">On the **Edit** menu, point to **IntelliSense**, then click **Insert Snippet**.</span></span>  
  
    -   <span data-ttu-id="30ffc-115">按一下滑鼠右鍵，然後從快速鍵功能表中選取 [插入程式碼片段]  命令。</span><span class="sxs-lookup"><span data-stu-id="30ffc-115">Right-click the mouse and then select the **Insert Snippet** command from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="30ffc-116">按兩下程式碼片段，或從程式碼片段選擇器中選取程式碼片段，然後按 TAB 或 ENTER。</span><span class="sxs-lookup"><span data-stu-id="30ffc-116">Double-click the snippet, or select the snippet from the snippet picker and then press TAB or ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30ffc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30ffc-117">See Also</span></span>  
 [<span data-ttu-id="30ffc-118">插入範圍陳述式 Transact-SQL 程式碼片段</span><span class="sxs-lookup"><span data-stu-id="30ffc-118">Insert Surround-with Transact-SQL snippets</span></span>](insert-surround-with-transact-sql-snippets.md)  
  
  
