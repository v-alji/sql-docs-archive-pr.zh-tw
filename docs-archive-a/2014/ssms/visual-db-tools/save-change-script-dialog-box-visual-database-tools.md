---
title: 儲存變更指令碼對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.generatechangescript
- vdtsql.chm:65544
ms.assetid: fc9d1639-5efa-44fe-a04f-4d4d0def2833
author: stevestein
ms.author: sstein
ms.openlocfilehash: 19a2bb2ce9a219c195421e2efa203fc115e1ae1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686668"
---
# <a name="save-change-script-dialog-box-visual-database-tools"></a><span data-ttu-id="06b7a-102">儲存變更指令碼對話方塊 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="06b7a-102">Save Change Script Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="06b7a-103">此對話方塊顯示從上次儲存資料表以來您所做變更的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="06b7a-103">This dialog box shows the [!INCLUDE[tsql](../../includes/tsql-md.md)] script for the changes you have made since you last saved the table.</span></span> <span data-ttu-id="06b7a-104">這也可以讓您在選擇的位置將指令碼儲存至文字檔。</span><span class="sxs-lookup"><span data-stu-id="06b7a-104">It also allows you to save the script to a text file at a location you choose.</span></span>  
  
 <span data-ttu-id="06b7a-105">您在 [資料表設計師] 中對資料表進行了尚未儲存的變更之後，即可存取這個對話方塊。</span><span class="sxs-lookup"><span data-stu-id="06b7a-105">You can access this dialog box after you have made unsaved changes to a table in Table Designer.</span></span> <span data-ttu-id="06b7a-106">在 [資料表設計工具]  功能表中，按一下 [產生變更指令碼]  。</span><span class="sxs-lookup"><span data-stu-id="06b7a-106">On the **Table Designer** menu, click **Generate Change Script**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06b7a-107">Visual Database Tools 提供的變更指令碼未包含錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="06b7a-107">Change scripts provided by Visual Database Tools contain no error handling.</span></span> <span data-ttu-id="06b7a-108">這些指令碼會假設資料庫物件在工具開啟之後並未變更，而且因此不會發生變更相關的問題。</span><span class="sxs-lookup"><span data-stu-id="06b7a-108">They assume that database objects have not changed since the tool was opened, and that change-related problems will therefore not occur.</span></span> <span data-ttu-id="06b7a-109">在執行變更指令碼之前，應先加入適當的錯誤處理陳述式。</span><span class="sxs-lookup"><span data-stu-id="06b7a-109">Before running a change script, you should include the appropriate error-handling statements.</span></span>  
  
## <a name="options"></a><span data-ttu-id="06b7a-110">選項。</span><span class="sxs-lookup"><span data-stu-id="06b7a-110">Options</span></span>  
 <span data-ttu-id="06b7a-111">**於每一次儲存時，自動產生變更指令碼**</span><span class="sxs-lookup"><span data-stu-id="06b7a-111">**Automatically generate change script on every save**</span></span>  
 <span data-ttu-id="06b7a-112">如果核取，[儲存變更指令碼]  對話方塊會在您將變更儲存至資料表時出現。</span><span class="sxs-lookup"><span data-stu-id="06b7a-112">If checked, the **Save Change Script** dialog box will appear any time you save changes to a table.</span></span>  
  
 <span data-ttu-id="06b7a-113">**是**</span><span class="sxs-lookup"><span data-stu-id="06b7a-113">**Yes**</span></span>  
 <span data-ttu-id="06b7a-114">顯示 [儲存]  對話方塊，以便您選擇文字檔的位置。</span><span class="sxs-lookup"><span data-stu-id="06b7a-114">Bring up the **Save** dialog box where you can choose the location for the text file.</span></span>  
  
 <span data-ttu-id="06b7a-115">**否**</span><span class="sxs-lookup"><span data-stu-id="06b7a-115">**No**</span></span>  
 <span data-ttu-id="06b7a-116">取消建立變更指令碼。</span><span class="sxs-lookup"><span data-stu-id="06b7a-116">Cancel the creation of the change script.</span></span>  
  
  
