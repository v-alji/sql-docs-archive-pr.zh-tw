---
title: 啟用或停用 DQS 中的分析通知 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- enable notifications
- notifications,enable
- notifications,disable
ms.assetid: e439bb29-60cc-4afd-a79a-f629b8d843c1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b3b5e8cec1cac3eb1ce4357480c0f994a33d4c40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700264"
---
# <a name="enable-or-disable-profiling-notifications-in-dqs"></a><span data-ttu-id="34d2c-102">在 DQS 中啟用或停用分析通知</span><span class="sxs-lookup"><span data-stu-id="34d2c-102">Enable or Disable Profiling Notifications in DQS</span></span>
  <span data-ttu-id="34d2c-103">此主題描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中啟用或停用分析通知。</span><span class="sxs-lookup"><span data-stu-id="34d2c-103">This topic describes how to enable or disable profiling notifications in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="34d2c-104">根據預設，DQS 中會啟用分析通知。</span><span class="sxs-lookup"><span data-stu-id="34d2c-104">By default, profiling notifications are enabled in DQS.</span></span> <span data-ttu-id="34d2c-105">分析通知告訴您有關資料來源的重要事實，以及針對資料執行之目前活動的效用。</span><span class="sxs-lookup"><span data-stu-id="34d2c-105">Profiling notifications tell you important facts about the data source and the effectiveness of the current activity performed on the data.</span></span> <span data-ttu-id="34d2c-106">如需詳細資訊，請參閱 [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md)。</span><span class="sxs-lookup"><span data-stu-id="34d2c-106">For more information, see [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="34d2c-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="34d2c-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="34d2c-108">Security</span><span class="sxs-lookup"><span data-stu-id="34d2c-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="34d2c-109">權限</span><span class="sxs-lookup"><span data-stu-id="34d2c-109">Permissions</span></span>  
 <span data-ttu-id="34d2c-110">您必須擁有 DQS_MAIN 資料庫的 dqs_administrator 角色，才能啟用通知。</span><span class="sxs-lookup"><span data-stu-id="34d2c-110">You must have the dqs_administrator role on the DQS_MAIN database to enable notifications.</span></span>  
  
##  <a name="enable-or-disable-profiling-notifications"></a><a name="Enable"></a><span data-ttu-id="34d2c-111">啟用或停用分析通知</span><span class="sxs-lookup"><span data-stu-id="34d2c-111">Enable or Disable Profiling Notifications</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="34d2c-112">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="34d2c-112">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="34d2c-113">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，按一下 **[組態]**。</span><span class="sxs-lookup"><span data-stu-id="34d2c-113">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="34d2c-114">接下來，按一下 **[一般設定]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="34d2c-114">Next, click the **General Settings** tab.</span></span>  
  
4.  <span data-ttu-id="34d2c-115">清除或選取 **[啟用通知]** 核取方塊，針對 DQS 中的各種活動啟用分析通知。</span><span class="sxs-lookup"><span data-stu-id="34d2c-115">Clear or select the **Enable Notifications** check box to disable or enable profiling notifications for various activities in DQS.</span></span>  
  
5.  <span data-ttu-id="34d2c-116">按一下 **關閉**。</span><span class="sxs-lookup"><span data-stu-id="34d2c-116">Click **Close**.</span></span>  
  
  
