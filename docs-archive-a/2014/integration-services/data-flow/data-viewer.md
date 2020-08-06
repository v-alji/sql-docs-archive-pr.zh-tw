---
title: 資料檢視器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataviewer.f1
helpviewer_keywords:
- Data Viewer dialog box
ms.assetid: 6351309a-688f-4e82-9697-1712130f10a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dc576981e875eade84dd3576f4ed93b66784411f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596823"
---
# <a name="data-viewer"></a><span data-ttu-id="24f45-102">資料檢視器</span><span class="sxs-lookup"><span data-stu-id="24f45-102">Data Viewer</span></span>
  <span data-ttu-id="24f45-103">如果路徑設定為使用資料檢視器，當資料在資料流程元件之間移動時，資料檢視器會一一顯示緩衝區的資料。</span><span class="sxs-lookup"><span data-stu-id="24f45-103">If a path is configured to use a data viewer, the Data Viewer displays the data buffer by buffer as data moves between two data flow components.</span></span>  
  
## <a name="options"></a><span data-ttu-id="24f45-104">選項。</span><span class="sxs-lookup"><span data-stu-id="24f45-104">Options</span></span>  
 <span data-ttu-id="24f45-105">**綠色箭頭**</span><span class="sxs-lookup"><span data-stu-id="24f45-105">**Green arrow**</span></span>  
 <span data-ttu-id="24f45-106">按一下即可顯示下一個緩衝區中的資料。</span><span class="sxs-lookup"><span data-stu-id="24f45-106">Click to display the data in the next buffer.</span></span> <span data-ttu-id="24f45-107">如果在單一緩衝區中可以移動資料，則無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="24f45-107">If the data can be moved in a single buffer, this option is not available.</span></span>  
  
 <span data-ttu-id="24f45-108">**卸離**</span><span class="sxs-lookup"><span data-stu-id="24f45-108">**Detach**</span></span>  
 <span data-ttu-id="24f45-109">卸離資料檢視器。</span><span class="sxs-lookup"><span data-stu-id="24f45-109">Detach the data viewer.</span></span>  
  
 <span data-ttu-id="24f45-110">**請注意** 卸離資料檢視器不會刪除資料檢視器。</span><span class="sxs-lookup"><span data-stu-id="24f45-110">**Note** Detaching a data viewer does not delete the data viewer.</span></span> <span data-ttu-id="24f45-111">如果已卸離資料檢視器，則資料會繼續流經路徑，但不會更新檢視器中的資料以符合每個緩衝區中的資料。</span><span class="sxs-lookup"><span data-stu-id="24f45-111">If the data viewer has been detached, data continues to flow through the path, but the data in the viewer is not updated to match the data in each buffer.</span></span>  
  
 <span data-ttu-id="24f45-112">**附加**</span><span class="sxs-lookup"><span data-stu-id="24f45-112">**Attach**</span></span>  
 <span data-ttu-id="24f45-113">附加資料檢視器。</span><span class="sxs-lookup"><span data-stu-id="24f45-113">Attach a data viewer.</span></span>  
  
 <span data-ttu-id="24f45-114">**請注意** 當附加資料檢視器時，它會顯示資料流程中之每個緩衝區的資訊，然後暫停。</span><span class="sxs-lookup"><span data-stu-id="24f45-114">**Note** When the data viewer is attached, it displays information from each buffer in the data flow and then pauses.</span></span> <span data-ttu-id="24f45-115">您可以使用綠色箭頭來在緩衝區中向前推進。</span><span class="sxs-lookup"><span data-stu-id="24f45-115">You can advance through the buffers by using the green arrow.</span></span>  
  
 <span data-ttu-id="24f45-116">**複製資料**</span><span class="sxs-lookup"><span data-stu-id="24f45-116">**Copy Data**</span></span>  
 <span data-ttu-id="24f45-117">將目前緩衝區中的資料複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="24f45-117">Copy data in the current buffer to the Clipboard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f45-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24f45-118">See Also</span></span>  
 [<span data-ttu-id="24f45-119">偵錯資料流程</span><span class="sxs-lookup"><span data-stu-id="24f45-119">Debugging Data Flow</span></span>](../troubleshooting/debugging-data-flow.md)  
  
  
