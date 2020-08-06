---
title: Excel Services 不支援下列功能，而且可能不會顯示或只顯示部分：批註、圖形或其他物件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
author: minewiskan
ms.author: owend
ms.openlocfilehash: 67c2989ab89f242fdce2ca64f3c2f361e17d49ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700315"
---
# <a name="the-following-features-are-not-supported-by-excel-services-and-may-not-display-or-may-display-only-partially-comments-shapes-or-other-objects"></a><span data-ttu-id="ed68f-102">下列功能不受 Excel Services 的支援，而且可能不會顯示或是只顯示一部分：註解、形狀或其他物件</span><span class="sxs-lookup"><span data-stu-id="ed68f-102">The following features are not supported by Excel Services and may not display or may display only partially: Comments, Shapes, or other objects</span></span>
  <span data-ttu-id="ed68f-103">當您從 PowerPivot 欄位清單將交叉分析篩選器加入到 PowerPivot 活頁簿時，將會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="ed68f-103">This error occurs when you add Slicers to a PowerPivot workbook from a PowerPivot Field List.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ed68f-104">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ed68f-104">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ed68f-105">適用於</span><span class="sxs-lookup"><span data-stu-id="ed68f-105">Applies to</span></span>|<span data-ttu-id="ed68f-106">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="ed68f-106">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="ed68f-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="ed68f-107">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="ed68f-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed68f-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="ed68f-109">原因</span><span class="sxs-lookup"><span data-stu-id="ed68f-109">Cause</span></span>|<span data-ttu-id="ed68f-110">Excel Web Access 無法轉譯形狀物件，該物件用來控制從 PowerPivot 欄位清單加入至活頁簿之交叉分析篩選器的位置和格式。</span><span class="sxs-lookup"><span data-stu-id="ed68f-110">Excel Web Access cannot render the Shape object used to control positioning and formatting of Slicers added to a workbook from the PowerPivot Field List.</span></span>|  
|<span data-ttu-id="ed68f-111">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ed68f-111">Message Text</span></span>|<span data-ttu-id="ed68f-112">下列功能不受 Excel Services 的支援，而且可能不會顯示或是只顯示一部分：</span><span class="sxs-lookup"><span data-stu-id="ed68f-112">The following features are not supported by Excel Services and may not display or may display only partially:</span></span><br /><br /> <span data-ttu-id="ed68f-113">註解、形狀或其他物件</span><span class="sxs-lookup"><span data-stu-id="ed68f-113">Comments, Shapes, or other objects</span></span><br /><br /> <span data-ttu-id="ed68f-114">某些功能 (例如外部資料查詢) 會顯示只能在 Microsoft Excel 中重新整理的快取資料。</span><span class="sxs-lookup"><span data-stu-id="ed68f-114">Some features, such as external data queries, display cached data which can only be refreshed in Microsoft Excel.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ed68f-115">說明</span><span class="sxs-lookup"><span data-stu-id="ed68f-115">Explanation</span></span>  
 <span data-ttu-id="ed68f-116">當您在瀏覽器中開啟 PowerPivot 活頁簿，並按一下該訊息的 [**詳細資料**] 按鈕時，Excel Web 存取會顯示這個錯誤，不**支援的功能此活頁簿可能不會如預期顯示**。</span><span class="sxs-lookup"><span data-stu-id="ed68f-116">Excel Web Access shows this error when you open a PowerPivot workbook in a browser and you click the **Details** button for the message, **Unsupported Features This workbook may not display as intended**.</span></span>  
  
 <span data-ttu-id="ed68f-117">發生這個錯誤是因為 PowerPivot 活頁簿包含交叉分析篩選器，此交叉分析篩選器的配置是由 Excel 中的隱藏形狀物件所控制。</span><span class="sxs-lookup"><span data-stu-id="ed68f-117">This error occurs because the PowerPivot workbook contains Slicers whose layout is controlled by a hidden Shape object in Excel.</span></span> <span data-ttu-id="ed68f-118">形狀物件會控制交叉分析篩選器在水平和垂直位置的格式與定位。</span><span class="sxs-lookup"><span data-stu-id="ed68f-118">The Shape object controls the formatting and positioning of the Slicers in horizontal and vertical placements.</span></span>  
  
 <span data-ttu-id="ed68f-119">Excel Services 無法轉譯形狀物件，但是因為此物件是隱藏的，所以它無法轉譯的事實並不會造成問題。</span><span class="sxs-lookup"><span data-stu-id="ed68f-119">Excel Services cannot render a Shape object, but because the object is hidden, the fact that it does not render is not an issue.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ed68f-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ed68f-120">User Action</span></span>  
 <span data-ttu-id="ed68f-121">可以忽略這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="ed68f-121">This error can be ignored.</span></span> <span data-ttu-id="ed68f-122">按一下 [確定]\*\*\*\*，關閉錯誤訊息，並繼續使用活頁簿和交叉分析篩選器，而不會發生任何問題。</span><span class="sxs-lookup"><span data-stu-id="ed68f-122">Click **OK** to close the error message and proceed to use the workbook and Slicers with no problem.</span></span>  
  
  
