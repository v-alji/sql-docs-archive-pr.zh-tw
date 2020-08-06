---
title: 了解本機和遠端執行之間的差異 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- packages [Integration Services], troubleshooting
ms.assetid: 610ee7d9-4fea-4aba-9395-57add826923b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 399584c790f4c5a5dd136121c58a5ff7743f4969
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698443"
---
# <a name="understanding-the-differences-between-local-and-remote-execution"></a><span data-ttu-id="ad0ec-102">了解本機和遠端執行之間的差異</span><span class="sxs-lookup"><span data-stu-id="ad0ec-102">Understanding the Differences between Local and Remote Execution</span></span>
  <span data-ttu-id="ad0ec-103">封裝開發人員與系統管理員應了解 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的執行位置有其限制。</span><span class="sxs-lookup"><span data-stu-id="ad0ec-103">Package developers and administrators should be aware that there are restrictions related to where an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package runs.</span></span>  
  
-   <span data-ttu-id="ad0ec-104">**封裝會在其啟動程式的相同電腦上執行**。</span><span class="sxs-lookup"><span data-stu-id="ad0ec-104">**A package runs on the same computer as the program that launches it**.</span></span> <span data-ttu-id="ad0ec-105">即使當程式載入的封裝是儲存在遠端的另一台伺服器上，封裝仍然會在本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="ad0ec-105">Even when a program loads a package that is stored remotely on another server, the package runs on the local computer.</span></span>  
  
-   <span data-ttu-id="ad0ec-106">**您只能在已安裝 Integration Services 的電腦之開發環境外部執行封裝**。</span><span class="sxs-lookup"><span data-stu-id="ad0ec-106">**You can only run a package outside the development environment on a computer that has Integration Services installed**.</span></span> <span data-ttu-id="ad0ec-107">在未安裝 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的用戶端電腦上，無法在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的外部執行封裝，除此之外，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 授權的條款也可能不允許您在其他電腦上安裝 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ad0ec-107">You cannot run packages outside of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] on a client computer that does not have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed, and the terms of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] licensing may not permit you to install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] on additional computers.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ad0ec-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 是伺服器元件，不可轉散發至用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="ad0ec-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is a server component and is not redistributable to client computers.</span></span> <span data-ttu-id="ad0ec-109">如果要從用戶端電腦執行封裝，必須以封裝能夠在伺服器上執行的方式啟動。</span><span class="sxs-lookup"><span data-stu-id="ad0ec-109">To run packages from a client computer, you need to launch them in a manner that ensures that the packages run on the server.</span></span>  
  
 <span data-ttu-id="ad0ec-110">如需有關載入和執行儲存之封裝的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="ad0ec-110">For more information about loading and running a saved package, see:</span></span>  
  
-   [<span data-ttu-id="ad0ec-111">以程式設計方式載入和執行本機套件</span><span class="sxs-lookup"><span data-stu-id="ad0ec-111">Loading and Running a Local Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
  
-   [<span data-ttu-id="ad0ec-112">以程式設計方式載入和執行遠端套件</span><span class="sxs-lookup"><span data-stu-id="ad0ec-112">Loading and Running a Remote Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
 <span data-ttu-id="ad0ec-113">如需有關執行封裝以及將其輸出載入自訂程式的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="ad0ec-113">For more information about running a package and loading its output into a custom program, see:</span></span>  
  
-   [<span data-ttu-id="ad0ec-114">載入本機套件的輸出</span><span class="sxs-lookup"><span data-stu-id="ad0ec-114">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
<span data-ttu-id="ad0ec-115">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="ad0ec-115">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ad0ec-116">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="ad0ec-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ad0ec-117">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="ad0ec-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ad0ec-118">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="ad0ec-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad0ec-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad0ec-119">See Also</span></span>  
 <span data-ttu-id="ad0ec-120">[以程式設計方式載入和執行本機封裝](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="ad0ec-120">[Loading and Running a Local Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) </span></span>  
 <span data-ttu-id="ad0ec-121">[以程式設計方式載入和執行遠端封裝](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="ad0ec-121">[Loading and Running a Remote Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span></span>  
 [<span data-ttu-id="ad0ec-122">載入本機套件的輸出</span><span class="sxs-lookup"><span data-stu-id="ad0ec-122">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
