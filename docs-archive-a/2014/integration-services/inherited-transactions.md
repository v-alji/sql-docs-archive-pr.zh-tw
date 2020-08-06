---
title: 繼承的交易 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], inherited
- child packages
- inherited transactions [Integration Services]
ms.assetid: 90db5564-d41e-4cfe-8c9e-4e68d41eff1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ecb480420fe9f2492c29fad37ee3cc6e6501e3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596194"
---
# <a name="inherited-transactions"></a><span data-ttu-id="04025-102">繼承的交易</span><span class="sxs-lookup"><span data-stu-id="04025-102">Inherited Transactions</span></span>
  <span data-ttu-id="04025-103">封裝可使用「執行封裝」工作執行另一個封裝。</span><span class="sxs-lookup"><span data-stu-id="04025-103">A package can run another package by using the Execute Package task.</span></span> <span data-ttu-id="04025-104">子封裝 (亦即「執行封裝」工作所執行的封裝) 可建立其自己的封裝交易，也可以繼承父封裝交易。</span><span class="sxs-lookup"><span data-stu-id="04025-104">The child package, which is the package run by the Execute Package task, may create its own package transaction, or it may inherit the parent package transaction.</span></span>  
  
 <span data-ttu-id="04025-105">如果下列兩個情況均成立，則子封裝將會繼承父封裝交易：</span><span class="sxs-lookup"><span data-stu-id="04025-105">A child package inherits the parent package transaction if both of the following are true:</span></span>  
  
-   <span data-ttu-id="04025-106">由一「執行封裝」工作叫用 (Invoke) 該封裝。</span><span class="sxs-lookup"><span data-stu-id="04025-106">The package is invoked by an Execute Package task.</span></span>  
  
-   <span data-ttu-id="04025-107">叫用該封裝的「執行封裝」工作亦聯結父封裝交易。</span><span class="sxs-lookup"><span data-stu-id="04025-107">The Execute Package task that invoked the package also joined the parent package transaction.</span></span>  
  
 <span data-ttu-id="04025-108">除非子封裝自行聯結交易，否則子封裝中的容器和工作無法聯結父封裝交易。</span><span class="sxs-lookup"><span data-stu-id="04025-108">Containers and tasks in the child package cannot join the parent package transaction unless the child package itself joins the transaction.</span></span>  
  
## <a name="illustration-of-package-transactions"></a><span data-ttu-id="04025-109">封裝交易的圖例說明</span><span class="sxs-lookup"><span data-stu-id="04025-109">Illustration of Package Transactions</span></span>  
 <span data-ttu-id="04025-110">在下圖中，有三個使用交易的封裝。</span><span class="sxs-lookup"><span data-stu-id="04025-110">In the following diagram, there are three packages that all use transactions.</span></span> <span data-ttu-id="04025-111">每一個封裝都包含多個工作。</span><span class="sxs-lookup"><span data-stu-id="04025-111">Each package contains multiple tasks.</span></span> <span data-ttu-id="04025-112">為強調交易的行為，只會顯示「執行封裝」工作。</span><span class="sxs-lookup"><span data-stu-id="04025-112">To emphasize the behavior of the transactions, only the Execute Package tasks are shown.</span></span> <span data-ttu-id="04025-113">封裝 A 執行封裝 B 和 C。而封裝 B 又執行封裝 D 和 E，封裝 C 執行封裝 F。</span><span class="sxs-lookup"><span data-stu-id="04025-113">Package A runs packages B and C. In turn, package B runs packages D and E, and package C runs package F.</span></span>  
  
 <span data-ttu-id="04025-114">封裝和工作具有下列交易屬性：</span><span class="sxs-lookup"><span data-stu-id="04025-114">Packages and tasks have the following transaction attributes:</span></span>  
  
-   <span data-ttu-id="04025-115">在封裝 A 和 C 上，**TransactionOption** 設為 **Required**</span><span class="sxs-lookup"><span data-stu-id="04025-115">**TransactionOption** is set to **Required** on packages A and C</span></span>  
  
-   <span data-ttu-id="04025-116">在封裝 B 和 D 上，以及在「執行封裝 B」、「執行封裝 D」和「執行封裝 F」工作上，**TransactionOption** 設為 **Supported** 。</span><span class="sxs-lookup"><span data-stu-id="04025-116">**TransactionOption** is set to **Supported** on packages B and D, and on the tasks Execute Package B, Execute Package D, and Execute Package F.</span></span>  
  
-   <span data-ttu-id="04025-117">在封裝 E 上，以及在「執行封裝 C」和「執行封裝 E」工作上，**TransactionOption** 設為 **NotSupported** 。</span><span class="sxs-lookup"><span data-stu-id="04025-117">**TransactionOption** is set to **NotSupported** on package E, and on the tasks Execute Package C and Execute Package E.</span></span>  
  
 <span data-ttu-id="04025-118">![繼承的交易流程](media/mw-dts-executepack.gif "繼承的交易流程")</span><span class="sxs-lookup"><span data-stu-id="04025-118">![Flow of inherited transactions](media/mw-dts-executepack.gif "Flow of inherited transactions")</span></span>  
  
 <span data-ttu-id="04025-119">只有封裝 B、D 和 F 可從其父封裝繼承交易。</span><span class="sxs-lookup"><span data-stu-id="04025-119">Only packages B, D, and F can inherit transactions from their parent packages.</span></span>  
  
 <span data-ttu-id="04025-120">封裝 B 和 D 會繼承由封裝 A 啟動的交易。</span><span class="sxs-lookup"><span data-stu-id="04025-120">Packages B and D inherit the transaction that was started by package A.</span></span>  
  
 <span data-ttu-id="04025-121">封裝 F 會繼承由封裝 C 啟動的交易。</span><span class="sxs-lookup"><span data-stu-id="04025-121">Package F inherits the transaction that was started by package C.</span></span>  
  
 <span data-ttu-id="04025-122">封裝 A 和 C 會控制其自己的交易。</span><span class="sxs-lookup"><span data-stu-id="04025-122">Packages A and C control their own transactions.</span></span>  
  
 <span data-ttu-id="04025-123">封裝 E 不使用交易。</span><span class="sxs-lookup"><span data-stu-id="04025-123">Package E does not use transactions.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="04025-124">相關工作</span><span class="sxs-lookup"><span data-stu-id="04025-124">Related Tasks</span></span>  
 [<span data-ttu-id="04025-125">設定封裝來使用交易</span><span class="sxs-lookup"><span data-stu-id="04025-125">Configure a Package to Use Transactions</span></span>](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
