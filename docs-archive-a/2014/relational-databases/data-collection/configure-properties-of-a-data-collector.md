---
title: 設定資料收集器的屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.datacollectionprop.advanced.f1
- sql12.swb.dc.datacollectionprop.general.f1
ms.assetid: cf98f57d-5a6d-4bc3-bf10-783e460fc63d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 05172c2c831ec649269512a625be069cdc67047a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702974"
---
# <a name="configure-properties-of-a-data-collector"></a><span data-ttu-id="f9277-102">設定資料收集器的屬性</span><span class="sxs-lookup"><span data-stu-id="f9277-102">Configure Properties of a Data Collector</span></span>
  <span data-ttu-id="f9277-103">本主題討論如何設定資料收集器的屬性。</span><span class="sxs-lookup"><span data-stu-id="f9277-103">This topic discusses how you can configure the properties of a data collector.</span></span>  
  
## <a name="data-collection-properties-general-tab"></a><span data-ttu-id="f9277-104">資料收集屬性 (一般索引標籤)</span><span class="sxs-lookup"><span data-stu-id="f9277-104">Data Collection Properties (General Tab)</span></span>  
 <span data-ttu-id="f9277-105">使用這個頁面可設定管理資料倉儲的設定，並指定在收集而來的資料上傳到資料倉儲之前，應該將這些資料儲存在哪裡。</span><span class="sxs-lookup"><span data-stu-id="f9277-105">Use this page to configure settings for the management data warehouse and specify where collected data should be stored before it is uploaded to the data warehouse.</span></span>  
  
 <span data-ttu-id="f9277-106">**啟用資料收集**</span><span class="sxs-lookup"><span data-stu-id="f9277-106">**Enable Data Collection**</span></span>  
 <span data-ttu-id="f9277-107">選取此選項可啟用資料收集。</span><span class="sxs-lookup"><span data-stu-id="f9277-107">Select to enable data collection.</span></span> <span data-ttu-id="f9277-108">這與執行 sp_syscollector_enable_collector 預存程序有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="f9277-108">This has the same effect as running the sp_syscollector_enable_collector stored procedure.</span></span> <span data-ttu-id="f9277-109">清除此核取方塊會停用資料收集，而且與執行 sp_syscollector_disable_collector 預存程序有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="f9277-109">Clearing this check box disables data collection and has the same effect as running the sp_syscollector_disable_collector stored procedure.</span></span>  
  
 <span data-ttu-id="f9277-110">**Server**</span><span class="sxs-lookup"><span data-stu-id="f9277-110">**Server**</span></span>  
 <span data-ttu-id="f9277-111">顯示將主控管理資料倉儲的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="f9277-111">Displays the name of the server that will host the management data warehouse</span></span>  
  
 <span data-ttu-id="f9277-112">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="f9277-112">**Database name**</span></span>  
 <span data-ttu-id="f9277-113">顯示用於管理資料倉儲的關聯式資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="f9277-113">Displays the name of the relational database that is used for the management data warehouse.</span></span>  
  
 <span data-ttu-id="f9277-114">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="f9277-114">**Test Connection**</span></span>  
 <span data-ttu-id="f9277-115">使用設定資料收集時所提供的資訊，測試與指定之 [伺服器]  的連接。</span><span class="sxs-lookup"><span data-stu-id="f9277-115">Test the connection to the specified **Server** using information provided when data collection is configured.</span></span>  
  
 <span data-ttu-id="f9277-116">**快取目錄**</span><span class="sxs-lookup"><span data-stu-id="f9277-116">**Cache directory**</span></span>  
 <span data-ttu-id="f9277-117">指定在收集而來的資料上傳到管理資料倉儲之前，應該將這些資料儲存在收集資料之系統上的哪一個目錄。</span><span class="sxs-lookup"><span data-stu-id="f9277-117">Specifies the directory where collected data is stored on the system collecting the data before it is uploaded to the management data warehouse.</span></span> <span data-ttu-id="f9277-118">如果未指定 [快取目錄]  ，資料收集器會嘗試尋找 %TEMP% 和 %TMP% 環境變數的位置，並使用其中一個位置當做暫存區的預設位置。</span><span class="sxs-lookup"><span data-stu-id="f9277-118">If **Cache directory** is not specified, the data collector attempts to locate the %TEMP% and %TMP% environment variables and use one these locations as the default location for temporary storage.</span></span> <span data-ttu-id="f9277-119">如果未設定這些環境變數，就會發生錯誤，而且系統會提示您建立快取目錄。</span><span class="sxs-lookup"><span data-stu-id="f9277-119">If these environment variables are not configured, an error occurs and you are prompted to create a cache directory.</span></span>  
  
## <a name="data-collection-properties-advanced-tab"></a><span data-ttu-id="f9277-120">資料收集屬性 (進階索引標籤)</span><span class="sxs-lookup"><span data-stu-id="f9277-120">Data Collection Properties (Advanced Tab)</span></span>  
 <span data-ttu-id="f9277-121">使用這個頁面可針對管理資料倉儲的連接來設定重試設定。</span><span class="sxs-lookup"><span data-stu-id="f9277-121">Use this page to configure the retry settings for the connection to the management data warehouse.</span></span>  
  
 <span data-ttu-id="f9277-122">**上傳失敗時的重試次數**</span><span class="sxs-lookup"><span data-stu-id="f9277-122">**Number of times to retry if upload fails**</span></span>  
 <span data-ttu-id="f9277-123">指定當上傳失敗時，重試上傳到管理資料倉儲的次數。</span><span class="sxs-lookup"><span data-stu-id="f9277-123">Specifies the number of times to retry an upload to the management data warehouse if an upload fails.</span></span> <span data-ttu-id="f9277-124">預設值是 1。</span><span class="sxs-lookup"><span data-stu-id="f9277-124">The default is 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9277-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9277-125">See Also</span></span>  
 <span data-ttu-id="f9277-126">[管理資料收集](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="f9277-126">[Manage Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="f9277-127">設定管理資料倉儲 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f9277-127">Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;</span></span>](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
