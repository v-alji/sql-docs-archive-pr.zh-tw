---
title: 連接到報表或資料摘要 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connreportdatafeed.f1
ms.assetid: e0ccfb0b-e646-4de8-b7da-f88c986c96e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76dd51c32d13e64b0368267ba7ac66aa6d76a784
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593014"
---
# <a name="connect-to-a-report-or-data-feed-ssas"></a><span data-ttu-id="454a5-102">連接到報表或資料摘要 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="454a5-102">Connect to a Report or Data Feed (SSAS)</span></span>
  <span data-ttu-id="454a5-103">**[資料表匯入精靈]** 的這個頁面可讓您連接到資料摘要。</span><span class="sxs-lookup"><span data-stu-id="454a5-103">This page of the **Table Import Wizard** enables you to connect to a data feed.</span></span> <span data-ttu-id="454a5-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="454a5-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
## <a name="from-a-report"></a><span data-ttu-id="454a5-105">從報表</span><span class="sxs-lookup"><span data-stu-id="454a5-105">From a Report</span></span>  
 <span data-ttu-id="454a5-106">**易記連接名稱**</span><span class="sxs-lookup"><span data-stu-id="454a5-106">**Friendly Connection Name**</span></span>  
 <span data-ttu-id="454a5-107">輸入資料摘要連接的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="454a5-107">Type a friendly name for the data feed connection.</span></span>  
  
 <span data-ttu-id="454a5-108">**報表路徑**</span><span class="sxs-lookup"><span data-stu-id="454a5-108">**Report Path**</span></span>  
 <span data-ttu-id="454a5-109">列出產生資料摘要之 SQL Server Reporting Services 報表的 URL。</span><span class="sxs-lookup"><span data-stu-id="454a5-109">Lists the URL for a SQL Server Reporting Services report that generates data feeds.</span></span> <span data-ttu-id="454a5-110">按一下 **[瀏覽]** 可指定此報表的 URL。</span><span class="sxs-lookup"><span data-stu-id="454a5-110">Click **Browse** to specify the URL for the report.</span></span>  
  
 <span data-ttu-id="454a5-111">按一下 [檢視報告]\*\*\*\*，顯示報告。</span><span class="sxs-lookup"><span data-stu-id="454a5-111">Click **View Report** to display the report.</span></span>  
  
 <span data-ttu-id="454a5-112">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="454a5-112">**Browse**</span></span>  
 <span data-ttu-id="454a5-113">導覽至有報表可用的位置。</span><span class="sxs-lookup"><span data-stu-id="454a5-113">Navigate to a location where a report is available.</span></span>  
  
 <span data-ttu-id="454a5-114">**進階**</span><span class="sxs-lookup"><span data-stu-id="454a5-114">**Advanced**</span></span>  
 <span data-ttu-id="454a5-115">使用 [**設定高級屬性**] 對話方塊來設定其他連接屬性。</span><span class="sxs-lookup"><span data-stu-id="454a5-115">Set additional connection properties by using the **Set Advanced Properties** dialog box..</span></span>  
  
 <span data-ttu-id="454a5-116">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="454a5-116">**Test Connection**</span></span>  
 <span data-ttu-id="454a5-117">嘗試使用目前的設定建立與資料來源之間的連接。</span><span class="sxs-lookup"><span data-stu-id="454a5-117">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="454a5-118">顯示一則訊息，指出連接是否成功。</span><span class="sxs-lookup"><span data-stu-id="454a5-118">A message is displayed indicating whether the connection is successful.</span></span>  
  
## <a name="from-an-azure-datamarket-dataset"></a><span data-ttu-id="454a5-119">從 Azure DataMarket 資料集</span><span class="sxs-lookup"><span data-stu-id="454a5-119">From an Azure DataMarket Dataset</span></span>  
 <span data-ttu-id="454a5-120">**易記連接名稱**</span><span class="sxs-lookup"><span data-stu-id="454a5-120">**Friendly Connection Name**</span></span>  
 <span data-ttu-id="454a5-121">輸入資料摘要連接的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="454a5-121">Type a friendly name for the data feed connection.</span></span>  
  
 <span data-ttu-id="454a5-122">**資料摘要 URL**</span><span class="sxs-lookup"><span data-stu-id="454a5-122">**Data Feed URL**</span></span>  
 <span data-ttu-id="454a5-123">輸入 Atom 服務文件 (.atomsvc、.atom) 的完整路徑或是單一資料摘要的 URL，或是按一下 [瀏覽]\*\*\*\* 選取 Atom 服務文件。</span><span class="sxs-lookup"><span data-stu-id="454a5-123">Type the full path to an Atom service document (.atomsvc, .atom) or the URL for a single data feed, or click **Browse** to select an Atom service document.</span></span>  
  
 <span data-ttu-id="454a5-124">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="454a5-124">**Browse**</span></span>  
 <span data-ttu-id="454a5-125">導覽至有報表可用的位置。</span><span class="sxs-lookup"><span data-stu-id="454a5-125">Navigate to a location where a report is available.</span></span>  
  
 <span data-ttu-id="454a5-126">按一下 **[檢視可用的 Azure DataMarket 資料集]** 可顯示可用資料集。</span><span class="sxs-lookup"><span data-stu-id="454a5-126">Click **View available Azure DataMarket datasets** to display available datasets.</span></span>  
  
 <span data-ttu-id="454a5-127">**帳戶金鑰**</span><span class="sxs-lookup"><span data-stu-id="454a5-127">**Account key**</span></span>  
 <span data-ttu-id="454a5-128">指定用來存取 Azure Marketplace 資料集訂閱的帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="454a5-128">Specify the account key used to access your Azure Marketplace dataset subscriptions.</span></span>  
  
 <span data-ttu-id="454a5-129">**尋找**</span><span class="sxs-lookup"><span data-stu-id="454a5-129">**Find**</span></span>  
 <span data-ttu-id="454a5-130">找出與 Windows Live 帳戶關聯的帳號金鑰。</span><span class="sxs-lookup"><span data-stu-id="454a5-130">Locate an account key associated with a Windows Live account.</span></span>  
  
 <span data-ttu-id="454a5-131">**儲存我的帳號金鑰**</span><span class="sxs-lookup"><span data-stu-id="454a5-131">**Save my account key**</span></span>  
 <span data-ttu-id="454a5-132">將帳號金鑰 (已加密) 與資料連接一起儲存。</span><span class="sxs-lookup"><span data-stu-id="454a5-132">Saves the account key (encrypted) with the data connection.</span></span>  
  
 <span data-ttu-id="454a5-133">**進階**</span><span class="sxs-lookup"><span data-stu-id="454a5-133">**Advanced**</span></span>  
 <span data-ttu-id="454a5-134">使用 [**設定高級屬性**] 對話方塊來設定其他連接屬性。</span><span class="sxs-lookup"><span data-stu-id="454a5-134">Set additional connection properties by using the **Set Advanced Properties** dialog box..</span></span>  
  
 <span data-ttu-id="454a5-135">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="454a5-135">**Test Connection**</span></span>  
 <span data-ttu-id="454a5-136">嘗試使用目前的設定建立與資料來源之間的連接。</span><span class="sxs-lookup"><span data-stu-id="454a5-136">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="454a5-137">顯示一則訊息，指出連接是否成功。</span><span class="sxs-lookup"><span data-stu-id="454a5-137">A message is displayed indicating whether the connection is successful.</span></span>  
  
## <a name="from-other-feeds"></a><span data-ttu-id="454a5-138">從其他摘要</span><span class="sxs-lookup"><span data-stu-id="454a5-138">From Other Feeds</span></span>  
 <span data-ttu-id="454a5-139">**易記連接名稱**</span><span class="sxs-lookup"><span data-stu-id="454a5-139">**Friendly Connection Name**</span></span>  
 <span data-ttu-id="454a5-140">輸入資料摘要連接的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="454a5-140">Type a friendly name for the data feed connection.</span></span>  
  
 <span data-ttu-id="454a5-141">**資料摘要 URL**</span><span class="sxs-lookup"><span data-stu-id="454a5-141">**Data Feed URL**</span></span>  
 <span data-ttu-id="454a5-142">輸入 Atom 服務文件 (.atomsvc、.atom) 的完整路徑或是單一資料摘要的 URL，或是按一下 [瀏覽]\*\*\*\* 選取 Atom 服務文件。</span><span class="sxs-lookup"><span data-stu-id="454a5-142">Type the full path to an Atom service document (.atomsvc, .atom) or the URL for a single data feed, or click **Browse** to select an Atom service document.</span></span>  
  
 <span data-ttu-id="454a5-143">按一下 **[包含所有摘要資料行]** 可指定是否要匯入所有資料摘要資料行。</span><span class="sxs-lookup"><span data-stu-id="454a5-143">Click **Include all feed columns** to specify whether all the data feed columns are imported.</span></span>  
  
 <span data-ttu-id="454a5-144">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="454a5-144">**Browse**</span></span>  
 <span data-ttu-id="454a5-145">導覽至有資料摘要可用的位置。</span><span class="sxs-lookup"><span data-stu-id="454a5-145">Navigate to a location where a data feed is available.</span></span>  
  
 <span data-ttu-id="454a5-146">**進階**</span><span class="sxs-lookup"><span data-stu-id="454a5-146">**Advanced**</span></span>  
 <span data-ttu-id="454a5-147">使用 **[設定進階屬性]** 對話方塊設定其他連接屬性。</span><span class="sxs-lookup"><span data-stu-id="454a5-147">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span>  
  
 <span data-ttu-id="454a5-148">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="454a5-148">**Test Connection**</span></span>  
 <span data-ttu-id="454a5-149">嘗試使用目前的設定建立與資料來源之間的連接。</span><span class="sxs-lookup"><span data-stu-id="454a5-149">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="454a5-150">顯示一則訊息，指出連接是否成功。</span><span class="sxs-lookup"><span data-stu-id="454a5-150">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
