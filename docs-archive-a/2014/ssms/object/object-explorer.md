---
title: 物件總管 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.objectexplorer.commandsoptions
- SQL12.SWB.SQLSERVEROBJECTEXPLORER.DHELP
- sql12.swb.objectexplorer.scriptingoptions
- sql12.swb.oe.f1
helpviewer_keywords:
- multi-select [SQL Server Management Studio]
- Registered Servers [SQL Server], Object Explorer
- Query Editor [SQL Server Management Studio], Object Explorer
- connections [SQL Server], SQL Server Management Studio
- servers [SQL Server], Registered Servers
- Object Explorer
- SQL Server Management Studio [SQL Server], connections
- viewing objects
- filtering objects [SQL Server]
- Object Explorer, about Object Explorer
ms.assetid: 469ea8e2-79b9-44c8-bb6f-f0e1c5dbf0f2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3acefcd03af1b39d467625800d8837553ff5253b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596442"
---
# <a name="object-explorer"></a><span data-ttu-id="52f22-102">物件總管</span><span class="sxs-lookup"><span data-stu-id="52f22-102">Object Explorer</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="52f22-103">提供的功能，可用於管理 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]及 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]執行個體中的物件。</span><span class="sxs-lookup"><span data-stu-id="52f22-103">provides features for managing objects in instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="benefits-of-object-explorer"></a><span data-ttu-id="52f22-104">物件總管的優點</span><span class="sxs-lookup"><span data-stu-id="52f22-104">Benefits of Object Explorer</span></span>  
 <span data-ttu-id="52f22-105">[物件總管] 提供階層式使用者介面以檢視及管理每個 SQL Server 執行個體中的物件。</span><span class="sxs-lookup"><span data-stu-id="52f22-105">Object Explorer provides a hierarchical user interface to view and manage the objects in each instance of SQL Server.</span></span> <span data-ttu-id="52f22-106">[物件總管詳細資料] 窗格會以表格式檢視來呈現執行個體物件，而且可以搜尋特定物件。</span><span class="sxs-lookup"><span data-stu-id="52f22-106">The Object Explorer Details pane presents a tabular view of instance objects, and the capability to search for specific objects.</span></span> <span data-ttu-id="52f22-107">物件總管的功能會隨著伺服器的類型而有些不同，不過，它通常會包括資料庫的開發功能，以及所有伺服器類型的管理功能。</span><span class="sxs-lookup"><span data-stu-id="52f22-107">The capabilities of Object Explorer vary slightly depending on the type of server, but generally include the development features for databases, and management features for all server types.</span></span>  
  
## <a name="object-explorer-tasks"></a><span data-ttu-id="52f22-108">物件總管工作</span><span class="sxs-lookup"><span data-stu-id="52f22-108">Object Explorer Tasks</span></span>  
  
|<span data-ttu-id="52f22-109">描述</span><span class="sxs-lookup"><span data-stu-id="52f22-109">Description</span></span>|<span data-ttu-id="52f22-110">主題</span><span class="sxs-lookup"><span data-stu-id="52f22-110">Topic</span></span>|  
|-----------------|-----------|  
|<span data-ttu-id="52f22-111">描述如何開啟 [物件總管]，以及設定可定義總管行為的選項。</span><span class="sxs-lookup"><span data-stu-id="52f22-111">Describes how to open the Object Explorer and configure the options that define the behavior of the explorer.</span></span>|[<span data-ttu-id="52f22-112">開啟和設定物件總管</span><span class="sxs-lookup"><span data-stu-id="52f22-112">Open and Configure Object Explorer</span></span>](open-and-configure-object-explorer.md)|  
|<span data-ttu-id="52f22-113">描述如何將 [物件總管] 連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]及 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="52f22-113">Describes how to connect Object Explorer to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>|[<span data-ttu-id="52f22-114">從物件總管連接到執行個體</span><span class="sxs-lookup"><span data-stu-id="52f22-114">Connect to an Instance From Object Explorer</span></span>](connect-to-an-instance-from-object-explorer.md)|  
|<span data-ttu-id="52f22-115">描述如何管理 [物件總管] 階層中以節點形式呈現的物件。</span><span class="sxs-lookup"><span data-stu-id="52f22-115">Describes how to manage objects represented as nodes in the Object Explorer hierarchy.</span></span>|[<span data-ttu-id="52f22-116">使用物件總管管理物件</span><span class="sxs-lookup"><span data-stu-id="52f22-116">Manage Objects by Using Object Explorer</span></span>](manage-objects-by-using-object-explorer.md)|  
|<span data-ttu-id="52f22-117">描述 [物件總管詳細資料] 窗格，此窗格是以表格式檢視呈現伺服器中的所有物件，而伺服器具有可管理這些物件的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="52f22-117">Describes the Object Explorer Details Pane, a tabular view of all of the objects in the server with a user interface to manage them.</span></span>|[<span data-ttu-id="52f22-118">物件總管詳細資料窗格</span><span class="sxs-lookup"><span data-stu-id="52f22-118">Object Explorer Details Pane</span></span>](object-explorer-details-pane.md)|  
|<span data-ttu-id="52f22-119">描述在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中執行自訂報表的方式。</span><span class="sxs-lookup"><span data-stu-id="52f22-119">Describes ways to run custom reports in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>|[<span data-ttu-id="52f22-120">Management Studio 中的自訂報表</span><span class="sxs-lookup"><span data-stu-id="52f22-120">Custom Reports in Management Studio</span></span>](custom-reports-in-management-studio.md)|  
  
  
