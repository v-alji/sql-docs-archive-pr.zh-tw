---
title: 建立使用範本的指令碼 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ed48014c-3fc9-48ff-8c0f-8d1822195f14
author: stevestein
ms.author: sstein
ms.openlocfilehash: b404ecc505e93c302e4c737f9c0b0161d9015519
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702241"
---
# <a name="create-scripts-using-templates"></a><span data-ttu-id="b86b8-102">利用範本建立指令碼</span><span class="sxs-lookup"><span data-stu-id="b86b8-102">Create Scripts Using Templates</span></span>
  <span data-ttu-id="b86b8-103">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 提供大量包含許多一般工作的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式之指令碼範本。</span><span class="sxs-lookup"><span data-stu-id="b86b8-103">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] provides a large number of script templates containing the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for many common tasks.</span></span> <span data-ttu-id="b86b8-104">這些範本包含使用者提供值的參數，如資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="b86b8-104">These templates contain parameters for the user-provided values such as a table name.</span></span> <span data-ttu-id="b86b8-105">您可以利用這些參數，只輸入名稱一次，之後，便自動將名稱複製到指令碼內所有必要的位置。</span><span class="sxs-lookup"><span data-stu-id="b86b8-105">Using the parameters, you can type the name once and then automatically copy the name to all the necessary locations within the script.</span></span> <span data-ttu-id="b86b8-106">您可以撰寫您自己的自訂範本來支援您最常撰寫的指令碼。</span><span class="sxs-lookup"><span data-stu-id="b86b8-106">You can write your own custom templates to support the scripts that you write most often.</span></span> <span data-ttu-id="b86b8-107">您也可以重新組織範本樹狀結構、移動範本，或建立新資料夾來存放範本。</span><span class="sxs-lookup"><span data-stu-id="b86b8-107">You can also reorganize the template tree, moving templates or creating new folders to hold the templates.</span></span> <span data-ttu-id="b86b8-108">在下列練習中，您將利用範本，指定定序範本來建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="b86b8-108">In the following practice, you will use a template to create a database, specifying collation template.</span></span>  
  
## <a name="using-templates"></a><span data-ttu-id="b86b8-109">使用範本</span><span class="sxs-lookup"><span data-stu-id="b86b8-109">Using Templates</span></span>  
  
#### <a name="to-create-a-script-using-a-template"></a><span data-ttu-id="b86b8-110">若要利用範本建立指令碼</span><span class="sxs-lookup"><span data-stu-id="b86b8-110">To create a script using a template</span></span>  
  
1.  <span data-ttu-id="b86b8-111">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]的 [檢視]  功能表上，按一下 [範本總管] 。</span><span class="sxs-lookup"><span data-stu-id="b86b8-111">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="b86b8-112">[範本總管] 中的範本會組織成不同的群組。</span><span class="sxs-lookup"><span data-stu-id="b86b8-112">The templates in Template Explorer are organized into groups.</span></span> <span data-ttu-id="b86b8-113">展開 [資料庫]\*\*\*\*，然後按兩下 [建立資料庫]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b86b8-113">Expand **Database**, and then double-click **Create Database**.</span></span>  
  
3.  <span data-ttu-id="b86b8-114">在 [連接到 Database Engine]\*\*\*\* 對話方塊中，填妥連接資訊，然後按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b86b8-114">In the **Connect to Database Engine** dialog box, complete the connection information and then click **Connect**.</span></span> <span data-ttu-id="b86b8-115">此時會開啟一個新的 [查詢編輯器] 視窗，其中含有 [建立資料庫]\*\*\*\* 範本的內容。</span><span class="sxs-lookup"><span data-stu-id="b86b8-115">A new Query Editor window opens, containing the contents of the **Create Database** template.</span></span>  
  
4.  <span data-ttu-id="b86b8-116">在 **[查詢]** 功能表上，按一下 **[指定範本參數的值]** 。</span><span class="sxs-lookup"><span data-stu-id="b86b8-116">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
5.  <span data-ttu-id="b86b8-117">在 [指定範本參數的值]\*\*\*\* 對話方塊中，[值]\*\*\*\* 資料行包含 **Database_Name** 參數的建議值。</span><span class="sxs-lookup"><span data-stu-id="b86b8-117">In the **Specify Values for Template Parameters** dialog box, the **Value** column contains a suggested value for the **Database_Name** parameter.</span></span> <span data-ttu-id="b86b8-118">在 [資料庫名稱]\*\*\*\* 參數方塊中，輸入 [行銷]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b86b8-118">In the **Database Name** parameter box, type **Marketing**, and then click **OK**.</span></span> <span data-ttu-id="b86b8-119">請注意在不同位置將 [行銷] 插入指令碼的方式。</span><span class="sxs-lookup"><span data-stu-id="b86b8-119">Note how "Marketing" is inserted into the script in several locations.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="b86b8-120">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="b86b8-120">Next Task in Lesson</span></span>  
 [<span data-ttu-id="b86b8-121">建立自訂範本</span><span class="sxs-lookup"><span data-stu-id="b86b8-121">Create Custom Templates</span></span>](lesson-3-2-create-custom-templates.md)  
  
  
