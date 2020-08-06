---
title: 解析資料行參考編輯器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.resolvereferences.mapper.F1
- sql12.dts.designer.resolvereferences.preview.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 600b6f4d5ec12290d654f0854cc548a5bbcf4335
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596819"
---
# <a name="resolve-column-reference-editor"></a><span data-ttu-id="97513-102">解析資料行參考編輯器</span><span class="sxs-lookup"><span data-stu-id="97513-102">Resolve Column Reference Editor</span></span>
  <span data-ttu-id="97513-103">當輸入路徑中斷連接，或是如果路徑中有任何未對應的資料行，對應的資料路徑旁邊就會顯示錯誤圖示。</span><span class="sxs-lookup"><span data-stu-id="97513-103">When an input path is disconnected or if there are any unmapped columns in the path, an error icon is displayed beside the corresponding data path.</span></span> <span data-ttu-id="97513-104">若要簡化資料行參考錯誤的解析，新的解析參考編輯器可讓您針對執行樹狀目錄中的所有路徑，將未對應的輸出資料行與未對應的輸入資料行連結。</span><span class="sxs-lookup"><span data-stu-id="97513-104">To simplify the resolution of column reference errors, the new Resolve References editor allows you to link unmapped output columns with unmapped input columns for all paths in the execution tree.</span></span> <span data-ttu-id="97513-105">解析參考編輯器也會反白顯示路徑，以指出正在解析哪些路徑。</span><span class="sxs-lookup"><span data-stu-id="97513-105">The Resolve References editor will also highlight the paths to indicate which paths are being resolved.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97513-106">現在即使是元件的輸入路徑中斷連接，都可以編輯元件。</span><span class="sxs-lookup"><span data-stu-id="97513-106">It is now possible to edit a component even when its input path is disconnected</span></span>  
  
 <span data-ttu-id="97513-107">解析所有資料行參考之後，如果沒有其他資料路徑錯誤，資料路徑旁邊就不會顯示錯誤圖示。</span><span class="sxs-lookup"><span data-stu-id="97513-107">After all column references have been resolved, if there are no other data path errors, no error icons will be displayed beside the data paths.</span></span>  
  
## <a name="options"></a><span data-ttu-id="97513-108">選項。</span><span class="sxs-lookup"><span data-stu-id="97513-108">Options</span></span>  
 <span data-ttu-id="97513-109">未對應的輸出資料行 (來源)：</span><span class="sxs-lookup"><span data-stu-id="97513-109">Unmapped Output Columns (Source):</span></span>  
 <span data-ttu-id="97513-110">上游路徑中目前未對應的資料行</span><span class="sxs-lookup"><span data-stu-id="97513-110">Columns from the upstream path that are not currently mapped</span></span>  
  
 <span data-ttu-id="97513-111">對應的資料行 (來源)：</span><span class="sxs-lookup"><span data-stu-id="97513-111">Mapped Columns (Source):</span></span>  
 <span data-ttu-id="97513-112">對應至下游路徑資料行的上游路徑資料行</span><span class="sxs-lookup"><span data-stu-id="97513-112">Columns from the upstream path that are mapped to columns from the downstream path</span></span>  
  
 <span data-ttu-id="97513-113">對應的資料行 (目的地)：</span><span class="sxs-lookup"><span data-stu-id="97513-113">Mapped Columns (Destination):</span></span>  
 <span data-ttu-id="97513-114">對應至下游路徑資料行的上游路徑資料行</span><span class="sxs-lookup"><span data-stu-id="97513-114">Columns from the upstream path that are mapped to columns from the downstream path</span></span>  
  
 <span data-ttu-id="97513-115">未對應的輸入資料行 (目的地)：</span><span class="sxs-lookup"><span data-stu-id="97513-115">Unmapped Input Columns (Destination):</span></span>  
 <span data-ttu-id="97513-116">下游路徑中目前未對應的資料行</span><span class="sxs-lookup"><span data-stu-id="97513-116">Columns from the downstream path that are not currently mapped</span></span>  
  
 <span data-ttu-id="97513-117">刪除未對應的輸入資料行</span><span class="sxs-lookup"><span data-stu-id="97513-117">Delete Unmapped Input Columns</span></span>  
 <span data-ttu-id="97513-118">核取「刪除未對應的輸入資料行」，以忽略資料路徑目的地的未對應資料行。</span><span class="sxs-lookup"><span data-stu-id="97513-118">Check Delete Unmapped Input Columns to ignore unmapped columns at the destination of the data path.</span></span> <span data-ttu-id="97513-119">[預覽變更] 按鈕會顯示當您按下 [確定] 按鈕時，將會出現的變更清單。</span><span class="sxs-lookup"><span data-stu-id="97513-119">The Preview Changes button displays a list of the changes that will occur when you press the OK button.</span></span>  
  
  
