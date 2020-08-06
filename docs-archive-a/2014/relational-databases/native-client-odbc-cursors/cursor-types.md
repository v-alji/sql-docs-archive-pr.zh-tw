---
title: 資料指標類型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- cursors [ODBC], types
- ODBC cursors, types
ms.assetid: 3a916cc7-f352-42cb-8b83-f78e06cef991
author: rothja
ms.author: jroth
ms.openlocfilehash: 6937dbb9ce42cd5631201e0c97be42b211742ada
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594078"
---
# <a name="cursor-types"></a><span data-ttu-id="7b3d2-102">資料指標類型</span><span class="sxs-lookup"><span data-stu-id="7b3d2-102">Cursor Types</span></span>
  <span data-ttu-id="7b3d2-103">ODBC 會定義 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驅動程式所支援的四種資料指標類型。</span><span class="sxs-lookup"><span data-stu-id="7b3d2-103">ODBC defines four cursor types supported by Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="7b3d2-104">這些資料指標在偵測結果集變更的能力和其所耗用的資源（例如**tempdb**中的記憶體和空間）方面有所不同。</span><span class="sxs-lookup"><span data-stu-id="7b3d2-104">These cursors vary in their ability to detect changes to the result set and in the resources they consume, such as memory and space in **tempdb**.</span></span> <span data-ttu-id="7b3d2-105">資料指標只有在嘗試重新提取變更過的資料列時，才能偵測到這些資料列的變更；沒有方法可讓資料來源通知資料指標目前所提取的資料列已變更。</span><span class="sxs-lookup"><span data-stu-id="7b3d2-105">A cursor can detect changes to rows only when it tries to refetch those rows; there is no way for the data source to notify the cursor of changes to the currently fetched rows.</span></span> <span data-ttu-id="7b3d2-106">交易隔離等級也會影響資料指標偵測到並非透過該資料指標所進行之變更的能力。</span><span class="sxs-lookup"><span data-stu-id="7b3d2-106">A cursor's ability to detect changes that were not made through the cursor is also influenced by the transaction isolation level.</span></span>  
  
 <span data-ttu-id="7b3d2-107">以下是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所支援的四種 ODBC 資料指標類型：</span><span class="sxs-lookup"><span data-stu-id="7b3d2-107">These are the four ODBC cursor types supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="7b3d2-108">順向資料指標：此種資料指標不支援捲動，而僅支援從資料指標開頭到結尾循序提取資料列。</span><span class="sxs-lookup"><span data-stu-id="7b3d2-108">Forward-only cursors do not support scrolling; they only support fetching rows serially from the start to the end of the cursor.</span></span>  
  
-   <span data-ttu-id="7b3d2-109">當資料指標開啟時，靜態資料指標會內建于**tempdb**中。</span><span class="sxs-lookup"><span data-stu-id="7b3d2-109">Static cursors are built in **tempdb** when the cursor is opened.</span></span> <span data-ttu-id="7b3d2-110">這種資料指標一定會顯示結果集在資料指標開啟時的原貌，</span><span class="sxs-lookup"><span data-stu-id="7b3d2-110">They always display the result set as it was when the cursor was opened.</span></span> <span data-ttu-id="7b3d2-111">而不會反映出資料的變更。</span><span class="sxs-lookup"><span data-stu-id="7b3d2-111">They never reflect changes to the data.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7b3d2-112">靜態資料指標永遠是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="7b3d2-112">static cursors are always read-only.</span></span> <span data-ttu-id="7b3d2-113">因為靜態伺服器資料指標是在**tempdb**中建立為工作資料表，所以資料指標結果集的大小不能超過所允許的資料列大小上限 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7b3d2-113">Because a static server cursor is built as a work table in **tempdb**, the size of the cursor result set cannot exceed the maximum row size allowed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="7b3d2-114">索引鍵集驅動的資料指標：這種資料指標開啟時，會將結果集中資料列的成員資格和順序設為固定。</span><span class="sxs-lookup"><span data-stu-id="7b3d2-114">Keyset-driven cursors have the membership and order of rows in the result set fixed when the cursor is opened.</span></span> <span data-ttu-id="7b3d2-115">您可透過此資料指標看到非索引鍵資料行的變更。</span><span class="sxs-lookup"><span data-stu-id="7b3d2-115">Changes to nonkey columns are visible through the cursor.</span></span>  
  
-   <span data-ttu-id="7b3d2-116">動態資料指標是靜態資料指標的相反。</span><span class="sxs-lookup"><span data-stu-id="7b3d2-116">Dynamic cursors are the opposite of static cursors.</span></span> <span data-ttu-id="7b3d2-117">動態資料指標會反映其結果集之中變更的資料列。</span><span class="sxs-lookup"><span data-stu-id="7b3d2-117">Dynamic cursors reflect all changes made to the rows in their result set.</span></span> <span data-ttu-id="7b3d2-118">每回擷取時結果集之中資料列的資料值、順序和成員均會變動。</span><span class="sxs-lookup"><span data-stu-id="7b3d2-118">The data values, order, and membership of the rows in the result set can change on each fetch.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b3d2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b3d2-119">See Also</span></span>  
 [<span data-ttu-id="7b3d2-120">&#40;ODBC&#41;使用資料指標</span><span class="sxs-lookup"><span data-stu-id="7b3d2-120">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
