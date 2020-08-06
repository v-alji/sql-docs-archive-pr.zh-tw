---
title: Integration Services 交易 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], transactions
- transactions [Integration Services], about transactions in packages
- tasks [Integration Services], transactions
- transactions [Integration Services]
ms.assetid: 3c78bb26-ddce-4831-a5f8-09d4f4fd53cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c0ee195bbcb7b9779111add4c1f2349816d5441
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596155"
---
# <a name="integration-services-transactions"></a><span data-ttu-id="2e50b-102">Integration Services 交易</span><span class="sxs-lookup"><span data-stu-id="2e50b-102">Integration Services Transactions</span></span>
  <span data-ttu-id="2e50b-103">封裝使用交易將工作執行的資料庫動作繫結至原子單位，這樣可以保持資料的完整性。</span><span class="sxs-lookup"><span data-stu-id="2e50b-103">Packages use transactions to bind the database actions that tasks perform into atomic units, and by doing this maintain data integrity.</span></span> <span data-ttu-id="2e50b-104">所有 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 容器類型 (套件、For 迴圈、Foreach 迴圈和時序容器，以及套件每個工作的工作主機) 皆可設定成使用交易。</span><span class="sxs-lookup"><span data-stu-id="2e50b-104">All [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] container types-packages, the For Loop, Foreach Loop, and Sequence containers, and the task hosts that encapsulate each task-can be configured to use transactions.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="2e50b-105">提供三個設定交易的選項，分別是 **NotSupported**、 **Supported**及 **Required**。</span><span class="sxs-lookup"><span data-stu-id="2e50b-105">provides three options for configuring transactions: **NotSupported**, **Supported**, and **Required**.</span></span>  
  
-   <span data-ttu-id="2e50b-106">**Required** 指出容器會啟動交易，除非其父容器已經將其啟動。</span><span class="sxs-lookup"><span data-stu-id="2e50b-106">**Required** indicates that the container starts a transaction, unless one is already started by its parent container.</span></span> <span data-ttu-id="2e50b-107">如果交易已經存在，則容器會聯結交易。</span><span class="sxs-lookup"><span data-stu-id="2e50b-107">If a transaction already exists, the container joins the transaction.</span></span> <span data-ttu-id="2e50b-108">例如，如果未設定為支援交易的封裝包括使用 **Required** 選項的「時序」容器，則「時序」容器會啟動其自己的交易。</span><span class="sxs-lookup"><span data-stu-id="2e50b-108">For example, if a package that is not configured to support transactions includes a Sequence container that uses the **Required** option, the Sequence container would start its own transaction.</span></span> <span data-ttu-id="2e50b-109">如果封裝設定為使用 **Required** 選項，則「時序」容器會聯結封裝交易。</span><span class="sxs-lookup"><span data-stu-id="2e50b-109">If the package were configured to use the **Required** option, the Sequence container would join the package transaction.</span></span>  
  
-   <span data-ttu-id="2e50b-110">**Supported** 指出容器不啟動交易，但會聯結其父容器啟動的任何交易。</span><span class="sxs-lookup"><span data-stu-id="2e50b-110">**Supported** indicates that the container does not start a transaction, but joins any transaction started by its parent container.</span></span> <span data-ttu-id="2e50b-111">例如，如果具有四個「執行 SQL」工作的封裝啟動交易，且全部四個工作都使用 **Supported** 選項，則任何工作失敗時，都會回復「執行 SQL」工作執行的資料庫更新。</span><span class="sxs-lookup"><span data-stu-id="2e50b-111">For example, if a package with four Execute SQL tasks starts a transaction and all four tasks use the **Supported** option, the database updates performed by the Execute SQL tasks are rolled back if any task fails.</span></span> <span data-ttu-id="2e50b-112">如果封裝未啟動交易，則四個「執行 SQL」工作不會由交易繫結，且只會回復由失敗之工作執行的資料庫更新。</span><span class="sxs-lookup"><span data-stu-id="2e50b-112">If the package does not start a transaction, the four Execute SQL tasks are not bound by a transaction, and no database updates except the ones performed by the failed task are rolled back.</span></span>  
  
-   <span data-ttu-id="2e50b-113">**NotSupported** 指出容器不啟動交易或聯結現有的交易。</span><span class="sxs-lookup"><span data-stu-id="2e50b-113">**NotSupported** indicates that the container does not start a transaction or join an existing transaction.</span></span> <span data-ttu-id="2e50b-114">父容器啟動的交易不會影響已設定為不支援交易的子容器。</span><span class="sxs-lookup"><span data-stu-id="2e50b-114">A transaction started by a parent container does not affect child containers that have been configured to not support transactions.</span></span> <span data-ttu-id="2e50b-115">例如，如果封裝設定為啟動交易，且封裝中的「For 迴圈」容器使用 **NotSupported** 選項，則「For 迴圈」中的工作一旦失敗將無法回復。</span><span class="sxs-lookup"><span data-stu-id="2e50b-115">For example, if a package is configured to start a transaction and a For Loop container in the package uses the **NotSupported** option, none of the tasks in the For Loop can roll back if they fail.</span></span>  
  
 <span data-ttu-id="2e50b-116">您可以設定容器上的 TransactionOption 屬性來設定交易。</span><span class="sxs-lookup"><span data-stu-id="2e50b-116">You configure transactions by setting the TransactionOption property on the container.</span></span> <span data-ttu-id="2e50b-117">使用 **中的** [屬性] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]視窗，可以設定此屬性，也可以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="2e50b-117">You can set this property by using the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], or you can set the property programmatically.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2e50b-118">`TransactionOption` 屬性會影響是否會套用容器所要求的 `IsolationLevel` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="2e50b-118">The `TransactionOption` property influences whether or not the value of the `IsolationLevel` property requested by a container is applied.</span></span> <span data-ttu-id="2e50b-119">如需詳細資訊，請參閱 `IsolationLevel` [設定封裝屬性](set-package-properties.md)主題中的屬性說明。</span><span class="sxs-lookup"><span data-stu-id="2e50b-119">For more information, see the description of the `IsolationLevel` property in the topic, [Setting Package Properties](set-package-properties.md).</span></span>  
  
### <a name="to-configure-a-package-to-use-transactions"></a><span data-ttu-id="2e50b-120">若要設定封裝使用交易</span><span class="sxs-lookup"><span data-stu-id="2e50b-120">To configure a package to use transactions</span></span>  
  
-   [<span data-ttu-id="2e50b-121">設定封裝來使用交易</span><span class="sxs-lookup"><span data-stu-id="2e50b-121">Configure a Package to Use Transactions</span></span>](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
## <a name="external-resources"></a><span data-ttu-id="2e50b-122">外部資源</span><span class="sxs-lookup"><span data-stu-id="2e50b-122">External Resources</span></span>  
  
-   <span data-ttu-id="2e50b-123">位於 www.mssqltips.com 的部落格項目： [如何在 SQL Server Integration Services SSIS 中使用交易](https://go.microsoft.com/fwlink/?LinkId=157783)</span><span class="sxs-lookup"><span data-stu-id="2e50b-123">Blog entry, [How to Use Transactions in SQL Server Integration Services SSIS](https://go.microsoft.com/fwlink/?LinkId=157783), on www.mssqltips.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e50b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e50b-124">See Also</span></span>  
 <span data-ttu-id="2e50b-125">[繼承的交易](../../2014/integration-services/inherited-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="2e50b-125">[Inherited Transactions](../../2014/integration-services/inherited-transactions.md) </span></span>  
 [<span data-ttu-id="2e50b-126">多個交易</span><span class="sxs-lookup"><span data-stu-id="2e50b-126">Multiple Transactions</span></span>](../../2014/integration-services/multiple-transactions.md)  
  
  
