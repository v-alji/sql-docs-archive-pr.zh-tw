---
title: 多個交易 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], multiple
- multiple transactions
ms.assetid: c3664a94-be89-40c0-a3a0-84b74a7fedbe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5ff909c92a23c965047edc0fcf278e17e4c76d94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596099"
---
# <a name="multiple-transactions"></a><span data-ttu-id="a0655-102">多個交易</span><span class="sxs-lookup"><span data-stu-id="a0655-102">Multiple Transactions</span></span>
  <span data-ttu-id="a0655-103">在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝中，封裝可以包含不相關的交易。</span><span class="sxs-lookup"><span data-stu-id="a0655-103">It is possible for a package to include unrelated transactions in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="a0655-104">任何時候如果巢狀容器階層中間的容器不支援交易，而階層中其上面或下面的容器設定為支援交易，則這些容器就會啟動分別的交易。</span><span class="sxs-lookup"><span data-stu-id="a0655-104">Any time a container in the middle of a nested container hierarchy does not support transactions, the containers above or below it in the hierarchy start separate transactions if they are configured to support transactions.</span></span> <span data-ttu-id="a0655-105">交易會從巢狀容器階層中最內層的工作到封裝依序進行認可或回復。</span><span class="sxs-lookup"><span data-stu-id="a0655-105">The transactions commit or roll back in order from the innermost task in the nested container hierarchy to the package.</span></span> <span data-ttu-id="a0655-106">不過，內部交易認可後，如果外部交易已中止，則不會回復該交易。</span><span class="sxs-lookup"><span data-stu-id="a0655-106">However, after the inner transaction commits, it does not roll back if an outer transaction is aborted.</span></span>

## <a name="illustration-of-multiple-transactions"></a><span data-ttu-id="a0655-107">多個交易的圖例</span><span class="sxs-lookup"><span data-stu-id="a0655-107">Illustration of Multiple Transactions</span></span>
 <span data-ttu-id="a0655-108">例如，封裝具有的「時序」容器包含兩個「Foreach 迴圈」容器，而每個容器包含兩個「執行 SQL」工作。</span><span class="sxs-lookup"><span data-stu-id="a0655-108">For example, a package has a Sequence container that holds two Foreach Loop containers, and each container include two Execute SQL tasks.</span></span> <span data-ttu-id="a0655-109">時序容器支援交易，Foreach 迴圈容器不支援，而執行 SQL 工作則支援。</span><span class="sxs-lookup"><span data-stu-id="a0655-109">The Sequence container supports transactions, the Foreach Loop containers do not, and the Execute SQL tasks do.</span></span> <span data-ttu-id="a0655-110">在此範例中，每一個執行 SQL 工作都會啟動自己的交易，而即使時序工作上的交易中止，也不會回復。</span><span class="sxs-lookup"><span data-stu-id="a0655-110">In this example, each Execute SQL task would start its own transaction and would not roll back if the transaction on the Sequence task was aborted.</span></span>

 <span data-ttu-id="a0655-111">「時序」容器、「Foreach 迴圈」容器和「執行 SQL」工作的 TransactionOption 屬性設定如下：</span><span class="sxs-lookup"><span data-stu-id="a0655-111">The TransactionOption properties of the Sequence container, Foreach Loop container and the Execute SQL tasks are set as follows:</span></span>

-   <span data-ttu-id="a0655-112">「時序」容器的 TransactionOption 屬性會設為 **Required**。</span><span class="sxs-lookup"><span data-stu-id="a0655-112">The TransactionOption property of the Sequence container is set to **Required**.</span></span>

-   <span data-ttu-id="a0655-113">「Foreach 迴圈」容器的 TransactionOption 屬性會設為 **NotSupported**。</span><span class="sxs-lookup"><span data-stu-id="a0655-113">The TransactionOption properties of the Foreach Loop containers are set to **NotSupported**.</span></span>

-   <span data-ttu-id="a0655-114">「執行 SQL」工作的 TransactionOption 屬性會設為 **Required**。</span><span class="sxs-lookup"><span data-stu-id="a0655-114">The TransactionOption properties of the Execute SQL tasks are set to **Required**.</span></span>

 <span data-ttu-id="a0655-115">下圖顯示封裝中五個不相關的交易。</span><span class="sxs-lookup"><span data-stu-id="a0655-115">The following diagram shows the five unrelated transactions in the package.</span></span> <span data-ttu-id="a0655-116">一個交易是由「時序」容器啟動的，四個交易是由「執行 SQL」工作啟動的。</span><span class="sxs-lookup"><span data-stu-id="a0655-116">One transaction is started by the Sequence container and four transactions are started by the Execute SQL tasks.</span></span>

 <span data-ttu-id="a0655-117">![多個交易的實作](media/mw-dts-trans2.gif "多個交易的實作")</span><span class="sxs-lookup"><span data-stu-id="a0655-117">![Implementation of multiple transactions](media/mw-dts-trans2.gif "Implementation of multiple transactions")</span></span>

## <a name="related-tasks"></a><span data-ttu-id="a0655-118">相關工作</span><span class="sxs-lookup"><span data-stu-id="a0655-118">Related Tasks</span></span>
 [<span data-ttu-id="a0655-119">設定封裝來使用交易</span><span class="sxs-lookup"><span data-stu-id="a0655-119">Configure a Package to Use Transactions</span></span>](../relational-databases/native-client-ole-db-transactions/transactions.md)


