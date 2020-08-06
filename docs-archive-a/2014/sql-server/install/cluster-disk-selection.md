---
title: 叢集磁片選取 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0f53d6d3f623254d2b17996be7fd5b8235dca223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595507"
---
# <a name="cluster-disk-selection"></a><span data-ttu-id="5d5de-102">叢集磁碟選取</span><span class="sxs-lookup"><span data-stu-id="5d5de-102">Cluster Disk Selection</span></span>
  <span data-ttu-id="5d5de-103">您可以使用 **安裝精靈的** [叢集磁碟選取] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 頁面來選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集的共用叢集磁碟資源。</span><span class="sxs-lookup"><span data-stu-id="5d5de-103">Use the **Cluster Disk Selection** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to select the shared cluster disk resource for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span> <span data-ttu-id="5d5de-104">叢集磁碟就是即將放置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料的位置。</span><span class="sxs-lookup"><span data-stu-id="5d5de-104">The cluster disk is where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data will be placed.</span></span>  
  
 <span data-ttu-id="5d5de-105">共用叢集磁片不是叢集安裝的必要條件 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5d5de-105">A shared cluster disk is not a requirement for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] cluster installations.</span></span> <span data-ttu-id="5d5de-106">SMB 檔案伺服器是容錯移轉叢集安裝的支援儲存體 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，而且可以在完成安裝之前，使用 [**資料庫引擎-資料目錄**] 頁面來指定。</span><span class="sxs-lookup"><span data-stu-id="5d5de-106">An SMB file server is a supported storage for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] failover cluster installations, and can be specified by using the **Database Engine - Data Directories** page before completing the installation.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="5d5de-107">如果您已經選取了要安裝 Analysis Services，就必須指定共用叢集磁碟。</span><span class="sxs-lookup"><span data-stu-id="5d5de-107">If you have selected Analysis Services to be installed, you must specify a shared cluster disk.</span></span>  
>   
>  <span data-ttu-id="5d5de-108">如果您計畫在這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體上啟用 FILESTREAM，就必須指定共用叢集磁碟。</span><span class="sxs-lookup"><span data-stu-id="5d5de-108">If you plan to enable FILESTREAM on this [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance, you must specify a shared cluster disk.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5d5de-109">選項</span><span class="sxs-lookup"><span data-stu-id="5d5de-109">Options</span></span>  
 <span data-ttu-id="5d5de-110">**共用磁片**</span><span class="sxs-lookup"><span data-stu-id="5d5de-110">**Shared Disks**</span></span>  
 <span data-ttu-id="5d5de-111">從清單中選取單一磁碟。</span><span class="sxs-lookup"><span data-stu-id="5d5de-111">Select a single disk from the list.</span></span> <span data-ttu-id="5d5de-112">叢集磁碟就是即將放置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料的位置。</span><span class="sxs-lookup"><span data-stu-id="5d5de-112">The cluster disk is where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data will be placed.</span></span>  
  
 <span data-ttu-id="5d5de-113">您只能指定一個磁碟。</span><span class="sxs-lookup"><span data-stu-id="5d5de-113">Only one disk can be specified.</span></span> <span data-ttu-id="5d5de-114">如果您選取包含叢集仲裁資源的群組，則會出現警告。</span><span class="sxs-lookup"><span data-stu-id="5d5de-114">If you select the group containing the cluster quorum resource, a warning will be displayed.</span></span> <span data-ttu-id="5d5de-115">我們建議您不要安裝到叢集仲裁資源。</span><span class="sxs-lookup"><span data-stu-id="5d5de-115">We recommend that you do not install to the cluster quorum resource.</span></span>  
  
 <span data-ttu-id="5d5de-116">**可用共用磁碟**</span><span class="sxs-lookup"><span data-stu-id="5d5de-116">**Available Shared Disks**</span></span>  
 <span data-ttu-id="5d5de-117">顯示可用磁碟的清單、每個磁碟是否具有成為共用磁碟的資格，以及每個磁碟資源的描述。</span><span class="sxs-lookup"><span data-stu-id="5d5de-117">Displays a list of available disks, whether each is qualified as a shared disk, and a description of each disk resource.</span></span>  
  
  
