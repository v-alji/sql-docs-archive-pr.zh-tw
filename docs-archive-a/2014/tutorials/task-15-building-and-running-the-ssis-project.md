---
title: 工作15：建立和執行 SSIS 專案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 13adf4e0-216a-4992-b13d-b7b1e1629e77
ms.author: lle
author: lrtoyou1223
ms.openlocfilehash: 2a008cd848c95b48e6e22798b6ef903942b4d656
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703490"
---
# <a name="task-15-building-and-running-the-ssis-project"></a><span data-ttu-id="d44b4-102">工作 15：建置及執行 SSIS 專案</span><span class="sxs-lookup"><span data-stu-id="d44b4-102">Task 15: Building and Running the SSIS Project</span></span>

  <span data-ttu-id="d44b4-103">在這項工作中，您會建立及執行 SSIS 專案。</span><span class="sxs-lookup"><span data-stu-id="d44b4-103">In this task, you build and run the SSIS project.</span></span> <span data-ttu-id="d44b4-104">如果您的電腦上已安裝64位版本的 Excel 2010，則您應該將**Run64BitRuntime**的值設定為**False** ，excel 來源才能正常執行。</span><span class="sxs-lookup"><span data-stu-id="d44b4-104">If you have the 64-bit version of Excel 2010 installed on your computer, you should set the value of **Run64BitRuntime** to **False** for the Excel source to work.</span></span>  
  
1.  <span data-ttu-id="d44b4-105">在 [**方案總管**] 視窗中，按一下功能表上的 [**專案**]，然後按一下 [ **CleanseAndCurateSuppliers 屬性**]。</span><span class="sxs-lookup"><span data-stu-id="d44b4-105">In the **Solution Explorer** window, click **Project** on the menu, and click **CleanseAndCurateSuppliers Properties**.</span></span>  
  
2.  <span data-ttu-id="d44b4-106">在 [**屬性**] 對話方塊中，展開左側的 [設定**屬性**]，然後按一下 [**調試**]。</span><span class="sxs-lookup"><span data-stu-id="d44b4-106">In the **Properties** dialog box, expand **Configuration Properties** on left, and click **Debugging**.</span></span>  
  
3.  <span data-ttu-id="d44b4-107">將**Run64BitRuntime**設定為**False**。</span><span class="sxs-lookup"><span data-stu-id="d44b4-107">Set **Run64BitRuntime** to **False**.</span></span>  
  
     <span data-ttu-id="d44b4-108">![CleanseAndCurateSuppliers 專案屬性](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "CleanseAndCurateSuppliers 專案屬性")</span><span class="sxs-lookup"><span data-stu-id="d44b4-108">![CleanseAndCurateSuppliers Project Properties](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "CleanseAndCurateSuppliers Project Properties")</span></span>  
  
4.  <span data-ttu-id="d44b4-109">按一下 [確定]\*\*\*\* 以關閉 [內容]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d44b4-109">Click **OK** to close the **Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="d44b4-110">按一下功能表列上的 [**建立**]，然後按一下 [**建立 CleanseAndCurateSuppliers**]。</span><span class="sxs-lookup"><span data-stu-id="d44b4-110">Click **Build** on menu bar and click **Build CleanseAndCurateSuppliers**.</span></span> <span data-ttu-id="d44b4-111">確定沒有任何建立錯誤。</span><span class="sxs-lookup"><span data-stu-id="d44b4-111">Make sure that there are no build errors.</span></span>  
  
6.  <span data-ttu-id="d44b4-112">按一下功能表列上的 [ **Debug** ]，然後按一下 [**開始調試**]。</span><span class="sxs-lookup"><span data-stu-id="d44b4-112">Click **Debug** on the menu bar and click **Start Debugging**.</span></span>  
  
7.  <span data-ttu-id="d44b4-113">查看 [**進度**] 視窗中的訊息，並確認已成功執行和結束封裝。</span><span class="sxs-lookup"><span data-stu-id="d44b4-113">Review messages in the **Progress** window and verify that package executed and ended successfully.</span></span>  
  
     <span data-ttu-id="d44b4-114">![進度視窗中的 [結果]](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "進度視窗中的 [結果]")</span><span class="sxs-lookup"><span data-stu-id="d44b4-114">![Results from Progress Window](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "Results from Progress Window")</span></span>  
  
     <span data-ttu-id="d44b4-115">![進度視窗中的 [最後狀態]](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "進度視窗中的 [最後狀態]")</span><span class="sxs-lookup"><span data-stu-id="d44b4-115">![Final Status from Progress Window](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "Final Status from Progress Window")</span></span>  
  
8.  <span data-ttu-id="d44b4-116">按一下功能表列上的 [ **Debug** ]，然後按一下 [**停止調試**] 以停止調試進程。</span><span class="sxs-lookup"><span data-stu-id="d44b4-116">Click **Debug** on menu bar and click **Stop Debugging** to stop the debugging session.</span></span> <span data-ttu-id="d44b4-117">如果封裝失敗，您應該啟用資料檢視器，並查看資料如何在元件之間流動。</span><span class="sxs-lookup"><span data-stu-id="d44b4-117">If the package fails, you should enable data viewers and see how the data flows between components.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="d44b4-118">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d44b4-118">Next Step</span></span>  
 [<span data-ttu-id="d44b4-119">工作 16：使用主資料管理員驗證</span><span class="sxs-lookup"><span data-stu-id="d44b4-119">Task 16: Verifying with Master Data Manager</span></span>](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  
