---
title: 設定清理和比對的閾值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.general.f1
helpviewer_keywords:
- cleansing,threshold value
- cleansing threshold values
- matching,threshold value
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0faf64e96468a3a9aac0de12d3ec3acbb1e1ed85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687167"
---
# <a name="configure-threshold-values-for-cleansing-and-matching"></a><span data-ttu-id="c32cf-102">設定清理和比對的臨界值</span><span class="sxs-lookup"><span data-stu-id="c32cf-102">Configure Threshold Values for Cleansing and Matching</span></span>
  <span data-ttu-id="c32cf-103">此主題描述如何設定臨界值，該值將會在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中的電腦輔助的清理和比對活動期間使用。</span><span class="sxs-lookup"><span data-stu-id="c32cf-103">This topic describes how to configure threshold values that will be used during the computer-assisted cleansing and matching activities in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c32cf-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="c32cf-104">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c32cf-105">Security</span><span class="sxs-lookup"><span data-stu-id="c32cf-105">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c32cf-106">權限</span><span class="sxs-lookup"><span data-stu-id="c32cf-106">Permissions</span></span>  
 <span data-ttu-id="c32cf-107">您必須擁有 DQS_MAIN 資料庫的 dqs_administrator 角色，才能設定這些臨界值。</span><span class="sxs-lookup"><span data-stu-id="c32cf-107">You must have the dqs_administrator role on the DQS_MAIN database to configure these threshold values.</span></span>  
  
##  <a name="configuring-the-threshold-values"></a><a name="Configure"></a> <span data-ttu-id="c32cf-108">設定臨界值</span><span class="sxs-lookup"><span data-stu-id="c32cf-108">Configuring the Threshold Values</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="c32cf-109">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="c32cf-109">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="c32cf-110">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，按一下 **[組態]**。</span><span class="sxs-lookup"><span data-stu-id="c32cf-110">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="c32cf-111">接下來，按一下 [**一般設定**] 索引標籤。此索引標籤可讓您指定清理和比對活動的臨界值。</span><span class="sxs-lookup"><span data-stu-id="c32cf-111">Next, click the **General Settings** tab. This tab enables you to specify threshold values for cleansing as well as matching activities.</span></span>  
  
4.  <span data-ttu-id="c32cf-112">若要針對清理活動指定臨界值，請在 **[互動式清理]** 區域的以下方塊中指定適當的值：</span><span class="sxs-lookup"><span data-stu-id="c32cf-112">To specify threshold values for the cleansing activity, specify appropriate values in the following boxes under the **Interactive Cleansing** area:</span></span>  
  
    -   <span data-ttu-id="c32cf-113">**建議的最低分數**：DQS 在電腦輔助的清理程序期間將用來建議某個值之取代的最低分數或信賴等級。</span><span class="sxs-lookup"><span data-stu-id="c32cf-113">**Min score for suggestions**: The minimum score or the confidence level that will be used by DQS for suggesting replacements for a value during the computer-assisted cleansing process.</span></span> <span data-ttu-id="c32cf-114">請使用對應百分比值的十進位表示法來輸入值。</span><span class="sxs-lookup"><span data-stu-id="c32cf-114">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="c32cf-115">例如，輸入 0.75 代表 75%。</span><span class="sxs-lookup"><span data-stu-id="c32cf-115">For example, type 0.75 for 75%.</span></span> <span data-ttu-id="c32cf-116">這個值應該要小於或等於 **[自動更正的最低分數]** 方塊中指定的值。</span><span class="sxs-lookup"><span data-stu-id="c32cf-116">This value should be less than or equal to the value specified in the **Min score for auto corrections** box.</span></span> <span data-ttu-id="c32cf-117">預設值為 0.7。</span><span class="sxs-lookup"><span data-stu-id="c32cf-117">The default value is 0.7.</span></span>  
  
    -   <span data-ttu-id="c32cf-118">**自動更正的最低分數**：DQS 在電腦輔助的清理程序期間將用來自動更正某個值的最低分數或信賴等級。</span><span class="sxs-lookup"><span data-stu-id="c32cf-118">**Min score for auto corrections**: The minimum score or the confidence level that will be used by DQS for automatically correcting a value during the computer-assisted cleansing process.</span></span> <span data-ttu-id="c32cf-119">請使用對應百分比值的十進位表示法來輸入值。</span><span class="sxs-lookup"><span data-stu-id="c32cf-119">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="c32cf-120">例如，輸入 0.9 表示 90%。</span><span class="sxs-lookup"><span data-stu-id="c32cf-120">For example, enter 0.9 for 90%.</span></span> <span data-ttu-id="c32cf-121">預設值為 0.8。</span><span class="sxs-lookup"><span data-stu-id="c32cf-121">The default value is 0.8.</span></span>  
  
5.  <span data-ttu-id="c32cf-122">若要針對比對活動指定臨界值，請在 **[比對]** 區域底下的 **[最低記錄分數]** 方塊中指定值。</span><span class="sxs-lookup"><span data-stu-id="c32cf-122">To specify threshold value for the matching activity, specify a value in the **Min record score** box under the **Matching** area.</span></span> <span data-ttu-id="c32cf-123">這個值表示讓某筆記錄被視為符合另一筆記錄的最低分數。</span><span class="sxs-lookup"><span data-stu-id="c32cf-123">This value signifies the minimum score for a record to be considered as a match for another record.</span></span> <span data-ttu-id="c32cf-124">預設值是 80%。</span><span class="sxs-lookup"><span data-stu-id="c32cf-124">The default value is 80%.</span></span>  
  
6.  <span data-ttu-id="c32cf-125">按一下 **關閉**。</span><span class="sxs-lookup"><span data-stu-id="c32cf-125">Click **Close**.</span></span>  
  
  
