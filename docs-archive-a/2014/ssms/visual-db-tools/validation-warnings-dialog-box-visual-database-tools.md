---
title: 驗證警告對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65556
- vdt.dlgbox.validationwarnings
ms.assetid: fc76e234-ec9c-4a19-a65b-cb558ec8268e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4f94c3ae91e077af853db949847bc8448f6a4753
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596965"
---
# <a name="validation-warnings-dialog-box-visual-database-tools"></a><span data-ttu-id="6b86d-102">驗證警告對話方塊 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6b86d-102">Validation Warnings Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="6b86d-103">如果您嘗試儲存可能具有損壞性副作用 (Side Effect) 的修改，或是資料庫認可操作可能失敗時，便會出現此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6b86d-103">This dialog box appears if you attempt to save modifications with potentially damaging side effects, or if the database commit operation is likely to fail.</span></span> <span data-ttu-id="6b86d-104">此會對話方塊指出有哪些可能的副作用，或是認可操作可能失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="6b86d-104">This dialog box indicates what those side effects might be or why the commit operation might fail.</span></span> <span data-ttu-id="6b86d-105">它可讓您選擇繼續執行修改或取消操作。</span><span class="sxs-lookup"><span data-stu-id="6b86d-105">It gives you the chance to continue with the modification or cancel the operation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b86d-106">當您嘗試將所做的修改傳輸至資料庫時，或當您儲存變更指令碼時，便會出現此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6b86d-106">This dialog box appears when you attempt to transmit your modifications to the database or when you save a change script.</span></span>  
  
 <span data-ttu-id="6b86d-107">下列任何一個原因都會使這個對話方塊出現：</span><span class="sxs-lookup"><span data-stu-id="6b86d-107">The dialog box can appear for any of these reasons:</span></span>  
  
-   <span data-ttu-id="6b86d-108">您可能沒有可以認可所有修改的資料庫權限。</span><span class="sxs-lookup"><span data-stu-id="6b86d-108">You might not have database permissions to commit all the modifications.</span></span>  
  
-   <span data-ttu-id="6b86d-109">您的修改會導致不適當形成的衍生資料行、預設條件約束或檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="6b86d-109">Your modifications would result in improperly formed derived columns, default constraints, or check constraints.</span></span>  
  
-   <span data-ttu-id="6b86d-110">對資料行的資料類型所做的修改可能造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="6b86d-110">A modification to a column's data type might cause data loss.</span></span>  
  
-   <span data-ttu-id="6b86d-111">某項修改會導致索引大於 900 個位元組。</span><span class="sxs-lookup"><span data-stu-id="6b86d-111">A modification would result in an index greater than 900 bytes.</span></span>  
  
-   <span data-ttu-id="6b86d-112">某項修改會變更提供結構描述繫結檢視或使用者定義函數的資料表或資料行。</span><span class="sxs-lookup"><span data-stu-id="6b86d-112">A modification would change a table or column contributing to a schema-bound view or user-defined function.</span></span>  
  
-   <span data-ttu-id="6b86d-113">某項修改會導致重新建立資料表，該資料表具有一或多個加密的觸發程序；觸發程序將被卸除。</span><span class="sxs-lookup"><span data-stu-id="6b86d-113">A modification would result in the re-creation of a table that has one or more encrypted triggers; the triggers will be dropped.</span></span>  
  
-   <span data-ttu-id="6b86d-114">您的修改會使一個資料表中的資料行，產生需要特別注意的 ANSI_NULLS、ANSI_PADDING 或兩者的設定。</span><span class="sxs-lookup"><span data-stu-id="6b86d-114">Your modifications will yield noteworthy settings of ANSI_NULLS or ANSI_PADDING or both for the columns within one table.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6b86d-115">選項。</span><span class="sxs-lookup"><span data-stu-id="6b86d-115">Options</span></span>  
 <span data-ttu-id="6b86d-116">**是**</span><span class="sxs-lookup"><span data-stu-id="6b86d-116">**Yes**</span></span>  
 <span data-ttu-id="6b86d-117">繼續執行作業並產生變更指令碼，或將修改內容傳輸至資料庫。</span><span class="sxs-lookup"><span data-stu-id="6b86d-117">Proceed with the operation and generate the change script or transmit the modifications to the database.</span></span> <span data-ttu-id="6b86d-118">如果您沒有修改資料庫的權限、如果您的修改將導致索引大於 900 個位元組，或者如果您的修改將導致不適當形成的計算資料行、預設條件約束或檢查條件約束，則認可操作仍然可能失敗。</span><span class="sxs-lookup"><span data-stu-id="6b86d-118">The commit operation can still fail if you do not have privileges to modify the database, if your modifications will result in an index greater than 900 bytes, or if your modifications will result in an improperly formed computed column, default constraint, or check constraint.</span></span>  
  
 <span data-ttu-id="6b86d-119">**否**</span><span class="sxs-lookup"><span data-stu-id="6b86d-119">**No**</span></span>  
 <span data-ttu-id="6b86d-120">取消儲存動作。</span><span class="sxs-lookup"><span data-stu-id="6b86d-120">Cancel the save action.</span></span>  
  
 <span data-ttu-id="6b86d-121">**儲存為文字檔**</span><span class="sxs-lookup"><span data-stu-id="6b86d-121">**Save Text File**</span></span>  
 <span data-ttu-id="6b86d-122">顯示 [另存新檔]  對話方塊，您可在此為包含警告清單的文字檔指定一個位置。</span><span class="sxs-lookup"><span data-stu-id="6b86d-122">Display the **Save As** dialog box, where you can specify a location for a text file containing a list of the warnings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b86d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b86d-123">See Also</span></span>  
 <span data-ttu-id="6b86d-124">[設計資料表 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6b86d-124">[Design Tables &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="6b86d-125">設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="6b86d-125">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
