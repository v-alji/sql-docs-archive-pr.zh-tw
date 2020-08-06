---
title: 新增縮排 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2d0b7ee8819f98df5e5658321a3d950ca31083b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597505"
---
# <a name="adding-indentation"></a><span data-ttu-id="e44a7-102">加入縮排</span><span class="sxs-lookup"><span data-stu-id="e44a7-102">Adding Indentation</span></span>
  <span data-ttu-id="e44a7-103">查詢編輯器可讓您利用單一步驟來縮排一大段的程式碼，而且您也可以變更縮排的量。</span><span class="sxs-lookup"><span data-stu-id="e44a7-103">Query Editor allows you to indent large sections of code with a single step, and you can change the amount of the indentation.</span></span>  
  
## <a name="indenting-code"></a><span data-ttu-id="e44a7-104">縮排程式碼</span><span class="sxs-lookup"><span data-stu-id="e44a7-104">Indenting Code</span></span>  
  
#### <a name="to-indent-multiple-lines-of-code"></a><span data-ttu-id="e44a7-105">若要縮排多行程式碼</span><span class="sxs-lookup"><span data-stu-id="e44a7-105">To indent multiple lines of code</span></span>  
  
1.  <span data-ttu-id="e44a7-106">在工具列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e44a7-106">On the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="e44a7-107">建立第二項查詢，從 [Person]\*\*\*\* 結構描述的 [Person]\*\*\*\* 資料表中，選取 [BusinessEntityID]\*\*\*\*、[FirstName]、[MiddleName]\*\*\*\* 與 [LastName]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="e44a7-107">Create a second query that selects the **BusinessEntityID**, FirstName, **MiddleName**, and **LastName** columns from the **Person** table of the **Person** schema.</span></span> <span data-ttu-id="e44a7-108">請將每個資料行個別放在一行中，使程式碼看起來如下：</span><span class="sxs-lookup"><span data-stu-id="e44a7-108">Place each column on a separate line so the code looks like this:</span></span>  
  
    ```  
    -- Search for a contact  
    SELECT   
    BusinessEntityID,  
    FirstName,   
    MiddleName,   
    LastName  
    FROM Person.Person  
    WHERE LastName = 'Sanchez';  
    GO  
    ```  
  
3.  <span data-ttu-id="e44a7-109">選取從 `BusinessEntityID` 到 `LastName` 的所有文字。</span><span class="sxs-lookup"><span data-stu-id="e44a7-109">Select all text from `BusinessEntityID` to `LastName`.</span></span>  
  
4.  <span data-ttu-id="e44a7-110">在 [SQL 編輯器]\*\*\*\* 工具列上，按一下 [增加縮排]\*\*\*\* 來同時縮排所有行。</span><span class="sxs-lookup"><span data-stu-id="e44a7-110">On the **SQL Editor** toolbar, click **Increase Indent** to indent all the lines at once.</span></span>  
  
#### <a name="to-change-the-default-indentation"></a><span data-ttu-id="e44a7-111">若要變更預設縮排</span><span class="sxs-lookup"><span data-stu-id="e44a7-111">To change the default indentation</span></span>  
  
1.  <span data-ttu-id="e44a7-112">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="e44a7-112">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="e44a7-113">依序展開 [文字編輯器]\*\*\*\* 和 [所有語言]\*\*\*\*，然後按一下 [索引標籤]\*\*\*\*，適當設定縮排的值。</span><span class="sxs-lookup"><span data-stu-id="e44a7-113">Expand **Text Editor**, expand **All Languages**, and click **Tabs** , and set indentation values as appropriate.</span></span> <span data-ttu-id="e44a7-114">請注意，您可以變更縮排大小，也可以變更 Tab 鍵距離，以及 Tab 鍵距離是否轉換成空格。</span><span class="sxs-lookup"><span data-stu-id="e44a7-114">Note that you can change the size of the indent as well as the size of tabs, and whether tabs are converted to spaces.</span></span>  
  
     <span data-ttu-id="e44a7-115">![索引標籤的外觀對話方塊](media/tabsdialog.gif "索引標籤的外觀對話方塊")</span><span class="sxs-lookup"><span data-stu-id="e44a7-115">![Appearance of the Tabs dialog box](media/tabsdialog.gif "Appearance of the Tabs dialog box")</span></span>  
  
3.  <span data-ttu-id="e44a7-116">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e44a7-116">Click **OK**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="e44a7-117">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="e44a7-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="e44a7-118">將查詢編輯器最大化</span><span class="sxs-lookup"><span data-stu-id="e44a7-118">Maximizing Query Editor</span></span>](lesson-2-3-maximizing-query-editor.md)  
  
  
