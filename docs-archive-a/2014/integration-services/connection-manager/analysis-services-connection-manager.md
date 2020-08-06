---
title: Analysis Services 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], Analysis Services
- connection managers [Integration Services], Analysis Services
- Analysis Services connection manager
ms.assetid: 9f9cadad-a1d0-4db5-98f5-df5dbbec1be4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b5da84acd131b75ef9ea174986836265934fb44b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596231"
---
# <a name="analysis-services-connection-manager"></a><span data-ttu-id="a57a0-102">Analysis Services 連接管理員</span><span class="sxs-lookup"><span data-stu-id="a57a0-102">Analysis Services Connection Manager</span></span>
  <span data-ttu-id="a57a0-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連線管理員能使套件連線到執行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫的伺服器，或連線到提供 Cube 和維度資料存取權的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="a57a0-103">An [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager enables a package to connect to a server that runs an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project that provides access to cube and dimension data.</span></span> <span data-ttu-id="a57a0-104">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中開發封裝時，您只能連接到 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="a57a0-104">You can only connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project while developing packages in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="a57a0-105">在執行階段，封裝會連接到您部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案的伺服器和資料庫。</span><span class="sxs-lookup"><span data-stu-id="a57a0-105">At run time, packages connect to the server and the database to which you deployed the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span>  
  
 <span data-ttu-id="a57a0-106">工作 (例如「 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行 DDL」工作和「 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 處理」工作) 及目的地 (例如「資料採礦模型定型」目的地) 都使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="a57a0-106">Both tasks, such as the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task and the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task, and destinations, such as the Data Mining Model Training destination, use an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager.</span></span>  
  
 <span data-ttu-id="a57a0-107">如需 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫的詳細資訊，請參閱[多維度模型資料庫 &#40;SSAS&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/multidimensional-model-databases-ssas)。</span><span class="sxs-lookup"><span data-stu-id="a57a0-107">For more information about [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases, see [Multidimensional Model Databases &#40;SSAS&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/multidimensional-model-databases-ssas).</span></span>  
  
## <a name="configuration-of-the-analysis-services-connection-manager"></a><span data-ttu-id="a57a0-108">Analysis Services 連接管理員的組態</span><span class="sxs-lookup"><span data-stu-id="a57a0-108">Configuration of the Analysis Services Connection Manager</span></span>  
 <span data-ttu-id="a57a0-109">當您將 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連線管理員加入封裝時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立在執行時間解析為連接的連線管理員 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、設定連線管理員屬性，並將連線管理員加入 `Connections` 封裝上的集合。</span><span class="sxs-lookup"><span data-stu-id="a57a0-109">When you add an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that is resolved as an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="a57a0-110">連接管理員的 `ConnectionManagerType` 屬性會設為 `MSOLAP100`。</span><span class="sxs-lookup"><span data-stu-id="a57a0-110">The `ConnectionManagerType` property of the connection manager is set to `MSOLAP100`.</span></span>  
  
 <span data-ttu-id="a57a0-111">您可以利用下列方式設定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連線管理員：</span><span class="sxs-lookup"><span data-stu-id="a57a0-111">You can configure the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="a57a0-112">提供一個設定為符合 Microsoft OLE Provider for Analysis Services 提供者需求的連接字串。</span><span class="sxs-lookup"><span data-stu-id="a57a0-112">Provide a connection string configured to meet the requirements of the Microsoft OLE Provider for Analysis Services provider.</span></span>  
  
-   <span data-ttu-id="a57a0-113">指定要連接的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="a57a0-113">Specify the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project to connect to.</span></span>  
  
-   <span data-ttu-id="a57a0-114">如果您要連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]執行個體，請指定驗證模式。</span><span class="sxs-lookup"><span data-stu-id="a57a0-114">If you are connecting to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], specify the authentication mode.</span></span>  
  
-   <span data-ttu-id="a57a0-115">指示是否在執行階段保留從連接管理員建立的連接。</span><span class="sxs-lookup"><span data-stu-id="a57a0-115">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="a57a0-116">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="a57a0-116">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="a57a0-117">如需可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="a57a0-117">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topic:</span></span>  
  
-   [<span data-ttu-id="a57a0-118">加入 Analysis Services 連線管理員對話方塊 UI 參考</span><span class="sxs-lookup"><span data-stu-id="a57a0-118">Add Analysis Services Connection Manager Dialog Box UI Reference</span></span>](add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 <span data-ttu-id="a57a0-119">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="a57a0-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
