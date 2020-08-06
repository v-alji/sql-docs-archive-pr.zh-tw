---
title: 在 Management Studio 中使用屬性視窗
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- viewing properties
- Properties window [SQL Server Management Studio]
- complex properties [SQL Server Management Studio]
ms.assetid: 903d4aca-f57c-43d9-a893-702eceaa7004
author: rothja
ms.author: jroth
ms.openlocfilehash: 5030bf85fc87482b11e91967ff8fb1baf77a213e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606201"
---
# <a name="use-the-properties-window-in-management-studio"></a><span data-ttu-id="40c55-102">在 Management Studio 中使用屬性視窗</span><span class="sxs-lookup"><span data-stu-id="40c55-102">Use the Properties Window in Management Studio</span></span>
  <span data-ttu-id="40c55-103">[屬性] 視窗描述 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的項目狀態，如連接或執行程序表運算子，以及資料庫物件的詳細資訊，如資料表、檢視表及設計師。</span><span class="sxs-lookup"><span data-stu-id="40c55-103">The Properties window describes the state of an item in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], such as a connection or a Showplan operator, and information about database objects such as tables, views, and designers.</span></span>  
  
 <span data-ttu-id="40c55-104">您可以利用 [屬性] 視窗來檢視目前連接的屬性。</span><span class="sxs-lookup"><span data-stu-id="40c55-104">You can use the Properties window to view the properties of the current connection.</span></span> <span data-ttu-id="40c55-105">許多屬性在 [屬性] 視窗中都是唯讀的，但在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的其他位置是可改變的。</span><span class="sxs-lookup"><span data-stu-id="40c55-105">Many properties are read-only in the Properties window but can be changed elsewhere in the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="40c55-106">例如，查詢的 [資料庫] 屬性在 [屬性] 視窗是唯讀的，但在工具列中是可改變的。</span><span class="sxs-lookup"><span data-stu-id="40c55-106">For example, the Database property of a query is read-only in the Properties window, but can be changed on the tool bar.</span></span>  
  
### <a name="to-view-properties-using-the-properties-window"></a><span data-ttu-id="40c55-107">利用 [屬性] 視窗檢視屬性</span><span class="sxs-lookup"><span data-stu-id="40c55-107">To view properties using the Properties window</span></span>  
  
1.  <span data-ttu-id="40c55-108">如果看不到 [屬性] 視窗，請按一下 [檢視] 功能表中的 [屬性視窗]，或按 F4。</span><span class="sxs-lookup"><span data-stu-id="40c55-108">If the Properties window is not visible, click **Properties Window** on the **View** menu, or press F4.</span></span>  
  
2.  <span data-ttu-id="40c55-109">將焦點設在您要檢視的物件上。</span><span class="sxs-lookup"><span data-stu-id="40c55-109">Set the focus on the object that you want to view.</span></span>  
  
3.  <span data-ttu-id="40c55-110">在 [屬性] 視窗中，尋找特定屬性。</span><span class="sxs-lookup"><span data-stu-id="40c55-110">Look for a specific property in the Properties window.</span></span>  
  
### <a name="to-view-connection-properties-of-a-query-window"></a><span data-ttu-id="40c55-111">檢視查詢視窗的連接屬性</span><span class="sxs-lookup"><span data-stu-id="40c55-111">To view connection properties of a query window</span></span>  
  
1.  <span data-ttu-id="40c55-112">如果看不到 [屬性] 視窗，請按一下 [檢視] 功能表中的 [屬性視窗]，或按 F4。</span><span class="sxs-lookup"><span data-stu-id="40c55-112">If the Properties window is not visible, click **Properties Window** on the **View** menu, or press F4.</span></span>  
  
2.  <span data-ttu-id="40c55-113">在 [屬性] 視窗中，您可以見到所有連接屬性。</span><span class="sxs-lookup"><span data-stu-id="40c55-113">In the Properties window, you can see all the connection properties.</span></span>  
  
### <a name="to-view-the-properties-of-a-showplan-operator"></a><span data-ttu-id="40c55-114">檢視執行程序表運算子的屬性</span><span class="sxs-lookup"><span data-stu-id="40c55-114">To view the properties of a Showplan operator</span></span>  
  
1.  <span data-ttu-id="40c55-115">在 [查詢]  功能表上，按一下 [包括實際執行計畫]  。</span><span class="sxs-lookup"><span data-stu-id="40c55-115">On the **Query** menu, click **Include Actual Execution Plan**.</span></span>  
  
2.  <span data-ttu-id="40c55-116">在 [SQL 查詢編輯器] 中，輸入和執行查詢。</span><span class="sxs-lookup"><span data-stu-id="40c55-116">In the SQL Query Editor, type and execute a query.</span></span>  
  
3.  <span data-ttu-id="40c55-117">如果看不到 [屬性] 視窗，請按一下 [檢視] 功能表中的 [屬性視窗]，或按 F4。</span><span class="sxs-lookup"><span data-stu-id="40c55-117">If the Properties window is not visible, click **Properties Window** on the **View** menu, or press F4.</span></span>  
  
4.  <span data-ttu-id="40c55-118">在 [SQL 查詢編輯器] 的 [執行計畫]  索引標籤中，按一下運算子的圖示來檢視 [屬性] 視窗中之運算子的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="40c55-118">On the **Execution plan** tab of the SQL Query Editor click the icons of the operators to view information about the operators in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c55-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40c55-119">See Also</span></span>  
 [<span data-ttu-id="40c55-120">屬性視窗 &#40;Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="40c55-120">Properties Window &#40;Management Studio&#41;</span></span>](../../ssms/properties-window-management-studio.md)  
  
  
