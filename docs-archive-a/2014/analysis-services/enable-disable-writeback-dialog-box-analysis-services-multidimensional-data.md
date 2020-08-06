---
title: 啟用-停用回寫對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitiondesigner.writebackenabledisable.f1
ms.assetid: 2d254393-3f0d-4b70-8b98-87159f9f3639
author: minewiskan
ms.author: owend
ms.openlocfilehash: 54ee4597ee78f45682730bd0e8d7119d204eaf2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607130"
---
# <a name="enable-disable-writeback-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="e6204-102">啟用-停用回寫對話方塊 (Analysis Services-多維度資料) </span><span class="sxs-lookup"><span data-stu-id="e6204-102">Enable-Disable Writeback Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="e6204-103">[啟用/停用回寫]\*\*\*\* 對話方塊會啟用或停用 Cube 中之量值群組的回寫。</span><span class="sxs-lookup"><span data-stu-id="e6204-103">The **Enable/Disable Writeback** dialog box enables or disables writeback for a measure group in a cube.</span></span> <span data-ttu-id="e6204-104">啟用量值群組的回寫會為該量值群組定義一個回寫資料分割，並建立一個回寫資料表。</span><span class="sxs-lookup"><span data-stu-id="e6204-104">Enabling writeback on a measure group defines a writeback partition and creates a writeback table for that measure group.</span></span> <span data-ttu-id="e6204-105">停用量值群組的回寫會移除回寫資料分割，但是不會刪除回寫資料表，以避免非預期的資料遺失。</span><span class="sxs-lookup"><span data-stu-id="e6204-105">Disabling writeback on a measure group removes the writeback partition but does not delete the writeback table, to avoid unanticipated data loss.</span></span> <span data-ttu-id="e6204-106">執行下列動作即可顯示 [啟用/停用回寫]\*\*\*\* 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="e6204-106">The **Enable/Disable Writeback** dialog box is displayed by:</span></span>  
  
-   <span data-ttu-id="e6204-107">在 Cube 設計師中，於[資料分割]\*\*\*\* 的 [量值群組]\*\*\*\* 窗格中按一下 [回寫設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6204-107">Clicking **Writeback Settings** in the **Measure Groups** pane on the **Partitions** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="e6204-108">在 Cube 設計師中，於 [資料分割]\*\*\*\* 索引標籤的 [量值群組]\*\*\*\* 窗格內，以滑鼠右鍵按一下 [資料分割]\*\*\*\* 方格中的資料分割，然後從內容功能表選取 [回寫設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6204-108">Right-clicking a partition in the **Partitions** grid in the **Measure Groups** pane on the **Partitions** tab in Cube Designer and selecting **Writeback Settings** from the context menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e6204-109">選項</span><span class="sxs-lookup"><span data-stu-id="e6204-109">Options</span></span>  
 <span data-ttu-id="e6204-110">**資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="e6204-110">**Table name**</span></span>  
 <span data-ttu-id="e6204-111">鍵入要為所選取資料分割建立之回寫資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="e6204-111">Type the name of the writeback table to create for the selected partition.</span></span> <span data-ttu-id="e6204-112">回寫資料表會儲存用戶端應用程式對量值群組所做的變更。</span><span class="sxs-lookup"><span data-stu-id="e6204-112">The writeback table stores the changes made to the measure group from a client application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6204-113">如果未啟用回寫，此選項會是停用的。</span><span class="sxs-lookup"><span data-stu-id="e6204-113">This option is disabled if writeback is not enabled.</span></span>  
  
 <span data-ttu-id="e6204-114">**資料來源**</span><span class="sxs-lookup"><span data-stu-id="e6204-114">**Data source**</span></span>  
 <span data-ttu-id="e6204-115">選取要包含回寫資料表的資料來源。</span><span class="sxs-lookup"><span data-stu-id="e6204-115">Select the data source to contain the writeback table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6204-116">如果未啟用回寫，此選項會是停用的。</span><span class="sxs-lookup"><span data-stu-id="e6204-116">This option is disabled if writeback is not enabled.</span></span>  
  
 <span data-ttu-id="e6204-117">**新增**</span><span class="sxs-lookup"><span data-stu-id="e6204-117">**New**</span></span>  
 <span data-ttu-id="e6204-118">按一下即可顯示 [連線管理員]\*\*\*\* 對話方塊，並定義要包含回寫資料表的新資料來源。</span><span class="sxs-lookup"><span data-stu-id="e6204-118">Click to display the **Connection Manager** dialog box and define a new data source to contain the writeback table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6204-119">如果未啟用回寫，此選項會是停用的。</span><span class="sxs-lookup"><span data-stu-id="e6204-119">This option is disabled if writeback is not enabled.</span></span>  
  
  
