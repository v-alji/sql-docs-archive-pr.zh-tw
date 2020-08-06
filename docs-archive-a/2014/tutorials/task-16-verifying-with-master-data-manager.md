---
title: 工作16：使用主資料管理員進行驗證 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d1649582f97e9e08691726745e4ba14b2f8226bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700510"
---
# <a name="task-16-verifying-with-master-data-manager"></a><span data-ttu-id="2837b-102">工作 16：使用主資料管理員驗證</span><span class="sxs-lookup"><span data-stu-id="2837b-102">Task 16: Verifying with Master Data Manager</span></span>
  <span data-ttu-id="2837b-103">在這項工作中，您會檢查 SSIS 封裝提交的批次作業狀態，並確認資料已使用主資料管理員上傳至 MDS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2837b-103">In this task, you check the status of the batch job submitted by the SSIS package and verify that the data was uploaded to MDS server by using Master Data Manager.</span></span>  
  
1.  <span data-ttu-id="2837b-104">啟動**主資料管理員** (`http://localhost/MDS`) 。</span><span class="sxs-lookup"><span data-stu-id="2837b-104">Launch **Master Data Manager** (`http://localhost/MDS`).</span></span> <span data-ttu-id="2837b-105">如果已開啟，請按一下頂端的 [ **Microsoft SQL Server Master Data Services** ，切換到**首頁**。</span><span class="sxs-lookup"><span data-stu-id="2837b-105">If it is already open, click **Microsoft SQL Server Master Data Services** at the top to switch to the **home page**.</span></span>  
  
2.  <span data-ttu-id="2837b-106">按一下 [**整合管理**]。</span><span class="sxs-lookup"><span data-stu-id="2837b-106">Click **Integration Management**.</span></span>  
  
3.  <span data-ttu-id="2837b-107">請注意，您已在清單中提交名為**EIMBatch**的批次。</span><span class="sxs-lookup"><span data-stu-id="2837b-107">Notice that there is a batch with named **EIMBatch** that you submitted in the list.</span></span> <span data-ttu-id="2837b-108">如果看不到下列畫面，請按一下功能表列上的 [匯**入資料**]。</span><span class="sxs-lookup"><span data-stu-id="2837b-108">Click **Import Data** on the menu bar if you do not see the following screen.</span></span>  
  
     <span data-ttu-id="2837b-109">![EIM 批次](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM 批次")</span><span class="sxs-lookup"><span data-stu-id="2837b-109">![EIM Batch](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM Batch")</span></span>  
  
4.  <span data-ttu-id="2837b-110">按一下頂端的 [ **SQL Server 2012 Master Data Services** ，切換回首頁。</span><span class="sxs-lookup"><span data-stu-id="2837b-110">Switch back to the home page by click **SQL Server 2012 Master Data Services** at the top.</span></span>  
  
5.  <span data-ttu-id="2837b-111">請確定已針對 [**模型**] 選取 [**供應商**型號]，並選取 [**版本**] **VERSION_1** ，然後按一下 [ **Explorer**]。</span><span class="sxs-lookup"><span data-stu-id="2837b-111">Make sure that **Suppliers** model is selected for **Model** and **VERSION_1** is selected for **Version**, and click **Explorer**.</span></span>  
  
6.  <span data-ttu-id="2837b-112">您可以看到資料的 SSIS 封裝已匯入至 MDS。</span><span class="sxs-lookup"><span data-stu-id="2837b-112">You can see the data SSIS package imported into MDS.</span></span> <span data-ttu-id="2837b-113">資料應該是清理的，而且沒有重複的程式**代碼**值 (注意： Excel 中的 [已供貨**商**] 欄對應到 MDS) 的 [供應商] 實體的 [ **Code** ] 屬性。</span><span class="sxs-lookup"><span data-stu-id="2837b-113">The data should be cleansed and have no duplicates **Code** values (Note: **SupplierID** column in Excel corresponds to **Code** attribute of Supplier entity in MDS).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="2837b-114">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2837b-114">Next Step</span></span>  
 [<span data-ttu-id="2837b-115">工作 17：檢閱 SSIS 封裝所建立的 DQS 清理專案</span><span class="sxs-lookup"><span data-stu-id="2837b-115">Task 17: Reviewing DQS Cleansing Project Created by the SSIS package</span></span>](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
