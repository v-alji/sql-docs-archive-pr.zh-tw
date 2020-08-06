---
title: 設定封裝使用交易 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], configuring packages to use
ms.assetid: 8bf14957-27b4-456b-81d9-e1a0e0ca94b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f469c2439deb2d16ac9046a1628e82c34e39b31d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688122"
---
# <a name="configure-a-package-to-use-transactions"></a><span data-ttu-id="2bd46-102">設定封裝來使用交易</span><span class="sxs-lookup"><span data-stu-id="2bd46-102">Configure a Package to Use Transactions</span></span>
  <span data-ttu-id="2bd46-103">將封裝設定成使用交易時，您有兩個選項：</span><span class="sxs-lookup"><span data-stu-id="2bd46-103">When you configure a package to use transactions, you have two options:</span></span>  
  
-   <span data-ttu-id="2bd46-104">擁有封裝的單一交易。</span><span class="sxs-lookup"><span data-stu-id="2bd46-104">Have a single transaction for the package.</span></span> <span data-ttu-id="2bd46-105">在此情況下，封裝本身會 *「起始」* (Initiate) 這筆交易，而封裝中的個別工作和容器會參與這個單一交易。</span><span class="sxs-lookup"><span data-stu-id="2bd46-105">In this case, it is the package itself that *initiates* this transaction, whereas individual tasks and containers in the package participate in this single transaction.</span></span>  
  
-   <span data-ttu-id="2bd46-106">在封裝中擁有多個交易。</span><span class="sxs-lookup"><span data-stu-id="2bd46-106">Have multiple transactions in the package.</span></span> <span data-ttu-id="2bd46-107">在此情況下，雖然封裝支援交易，但是封裝中的個別工作和容器實際上會起始交易。</span><span class="sxs-lookup"><span data-stu-id="2bd46-107">In this case, the package supports transactions, but individual tasks and containers in the package actually initiate the transactions.</span></span>  
  
 <span data-ttu-id="2bd46-108">下列程序將描述如何設定這兩個選項。</span><span class="sxs-lookup"><span data-stu-id="2bd46-108">The following procedures describe how to configure both options.</span></span>  
  
## <a name="configuring-a-single-transaction"></a><span data-ttu-id="2bd46-109">設定單一交易</span><span class="sxs-lookup"><span data-stu-id="2bd46-109">Configuring a Single Transaction</span></span>  
 <span data-ttu-id="2bd46-110">在這個選項中，封裝本身會起始單一交易。</span><span class="sxs-lookup"><span data-stu-id="2bd46-110">In this option, the package itself initiates a single transaction.</span></span> <span data-ttu-id="2bd46-111">您可以藉由將封裝的 TransactionOption 屬性設定為，來設定封裝來起始此交易 `Required` 。</span><span class="sxs-lookup"><span data-stu-id="2bd46-111">You configure the package to initiate this transaction by setting the TransactionOption property of the package to `Required`.</span></span>  
  
 <span data-ttu-id="2bd46-112">接著，您可以在這個單一交易中編列特定工作和容器。</span><span class="sxs-lookup"><span data-stu-id="2bd46-112">Next, you enlist specific tasks and containers in this single transaction.</span></span> <span data-ttu-id="2bd46-113">若要將工作或容器登記到交易中，您可以將該工作或容器的 TransactionOption 屬性設定為 `Supported` 。</span><span class="sxs-lookup"><span data-stu-id="2bd46-113">To enlist a task or container in a transaction, you set the TransactionOption property of that task or container to `Supported`.</span></span>  
  
#### <a name="to-configure-a-package-to-use-a-single-transaction"></a><span data-ttu-id="2bd46-114">將封裝設定成使用單一交易</span><span class="sxs-lookup"><span data-stu-id="2bd46-114">To configure a package to use a single transaction</span></span>  
  
1.  <span data-ttu-id="2bd46-115">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含您要設定以使用交易之封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="2bd46-115">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to configure to use a transaction.</span></span>  
  
2.  <span data-ttu-id="2bd46-116">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="2bd46-116">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="2bd46-117">按一下 **[控制流程]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2bd46-117">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="2bd46-118">以滑鼠右鍵按一下控制流程設計介面背景的任何位置，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="2bd46-118">Right-click anywhere in the background of the control flow design surface, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="2bd46-119">在 [**屬性**] 視窗中，將 [TransactionOption] 屬性設定為 `Required` 。</span><span class="sxs-lookup"><span data-stu-id="2bd46-119">In the **Properties** window, set the TransactionOption property to `Required`.</span></span>  
  
6.  <span data-ttu-id="2bd46-120">在 [控制流程]\*\*\*\* 索引標籤的設計介面上，以滑鼠右鍵按一下您要在交易中註冊的工作或容器，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2bd46-120">On the design surface of the **ControlFlow** tab, right-click the task or the container that you want to enroll in the transaction, and then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="2bd46-121">在 [**屬性**] 視窗中，將 [TransactionOption] 屬性設定為 `Supported` 。</span><span class="sxs-lookup"><span data-stu-id="2bd46-121">In the **Properties** window, set the TransactionOption property to `Supported`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2bd46-122">若要在交易中編列連接，請註冊在交易中使用連接的工作。</span><span class="sxs-lookup"><span data-stu-id="2bd46-122">To enlist a connection in a transaction, enroll the tasks that use the connection in the transaction.</span></span> <span data-ttu-id="2bd46-123">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 連接](connection-manager/integration-services-ssis-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="2bd46-123">For more information, see [Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md).</span></span>  
  
8.  <span data-ttu-id="2bd46-124">針對您想要在此交易中註冊的每個工作和容器，重複步驟 6 和 7。</span><span class="sxs-lookup"><span data-stu-id="2bd46-124">Repeat steps 6 and 7 for each task and container that you want to enroll in the transaction.</span></span>  
  
## <a name="configuring-multiple-transactions"></a><span data-ttu-id="2bd46-125">設定多個交易</span><span class="sxs-lookup"><span data-stu-id="2bd46-125">Configuring Multiple Transactions</span></span>  
 <span data-ttu-id="2bd46-126">在這個選項中，雖然封裝本身支援交易，但是不會啟動交易。</span><span class="sxs-lookup"><span data-stu-id="2bd46-126">In this option, the package itself supports transactions but does not start a transaction.</span></span> <span data-ttu-id="2bd46-127">您可以藉由將封裝的 TransactionOption 屬性設定為，來設定封裝以支援交易 `Supported` 。</span><span class="sxs-lookup"><span data-stu-id="2bd46-127">You configure the package to support transactions by setting the TransactionOption property of the package to `Supported`.</span></span>  
  
 <span data-ttu-id="2bd46-128">接著，您可以將封裝內部的所需工作和容器設定成起始或參與交易。</span><span class="sxs-lookup"><span data-stu-id="2bd46-128">Next, you configure the desired tasks and containers inside the package to initiate or participate in transactions.</span></span> <span data-ttu-id="2bd46-129">若要將工作或容器設定成起始交易，您可以將該工作或容器的 TransactionOption 屬性設為 `Required` 。</span><span class="sxs-lookup"><span data-stu-id="2bd46-129">To configure a task or container to initiate a transaction, you set the TransactionOption property of that task or container to `Required`.</span></span>  
  
#### <a name="to-configure-a-package-to-use-multiple-transactions"></a><span data-ttu-id="2bd46-130">將封裝設定成使用多個交易</span><span class="sxs-lookup"><span data-stu-id="2bd46-130">To configure a package to use multiple transactions</span></span>  
  
1.  <span data-ttu-id="2bd46-131">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含您要設定成使用交易之封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="2bd46-131">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to configure to use transaction.s</span></span>  
  
2.  <span data-ttu-id="2bd46-132">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="2bd46-132">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="2bd46-133">按一下 **[控制流程]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2bd46-133">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="2bd46-134">以滑鼠右鍵按一下控制流程設計介面背景的任何位置，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="2bd46-134">Right-click anywhere in the background of the control flow design surface, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="2bd46-135">在 [**屬性**] 視窗中，將 [TransactionOption] 屬性設定為 `Supported` 。</span><span class="sxs-lookup"><span data-stu-id="2bd46-135">In the **Properties** window, set the TransactionOption property to `Supported`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2bd46-136">封裝支援交易，但交易是由封裝中的工作或容器所啟動。</span><span class="sxs-lookup"><span data-stu-id="2bd46-136">The package supports transactions, but the transactions are started by task or containers in the package.</span></span>  
  
6.  <span data-ttu-id="2bd46-137">在 [控制流程]\*\*\*\* 索引標籤的設計介面上，以滑鼠右鍵按一下要啟動其交易之封裝內的工作或容器，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2bd46-137">On the design surface of the **ControlFlow** tab, right-click the task or the container in the package for which you want to start a transaction, and then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="2bd46-138">在 [**屬性**] 視窗中，將 [TransactionOption] 屬性設定為 `Required` 。</span><span class="sxs-lookup"><span data-stu-id="2bd46-138">In the **Properties** window, set the TransactionOption property to `Required`.</span></span>  
  
8.  <span data-ttu-id="2bd46-139">如果交易由容器啟動，請以滑鼠右鍵按一下您要在交易中註冊的工作或容器，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2bd46-139">If a transaction is started by a container, right-click the task or the container that you want to enroll in the transaction, and then click **Properties**.</span></span>  
  
9. <span data-ttu-id="2bd46-140">在 [**屬性**] 視窗中，將 [TransactionOption] 屬性設定為 `Supported` 。</span><span class="sxs-lookup"><span data-stu-id="2bd46-140">In the **Properties** window, set the TransactionOption property to `Supported`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2bd46-141">若要在交易中編列連接，請註冊在交易中使用連接的工作。</span><span class="sxs-lookup"><span data-stu-id="2bd46-141">To enlist a connection in a transaction, enroll the tasks that use the connection in the transaction.</span></span> <span data-ttu-id="2bd46-142">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 連接](connection-manager/integration-services-ssis-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="2bd46-142">For more information, see [Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md).</span></span>  
  
10. <span data-ttu-id="2bd46-143">針對啟動交易的每個工作和容器，重複步驟 6 至 9。</span><span class="sxs-lookup"><span data-stu-id="2bd46-143">Repeat steps 6 through 9 for each task and container that starts a transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bd46-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bd46-144">See Also</span></span>  
 [<span data-ttu-id="2bd46-145">Integration Services 交易</span><span class="sxs-lookup"><span data-stu-id="2bd46-145">Integration Services Transactions</span></span>](integration-services-transactions.md)  
  
  
