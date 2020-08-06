---
title: WMI 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], WMI
- connection managers [Integration Services], WMI
- WMI connection manager [Integration Services]
ms.assetid: fbfa4ba7-3d0d-4d6b-94ad-50741a88d03d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f15aefb0ed112f1d5b7bb05421750b6689a11339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596864"
---
# <a name="wmi-connection-manager"></a><span data-ttu-id="9d817-102">WMI 連接管理員</span><span class="sxs-lookup"><span data-stu-id="9d817-102">WMI Connection Manager</span></span>
  <span data-ttu-id="9d817-103">WMI 連接管理員可讓封裝利用 Windows Management Instrumentation (WMI)，來管理企業環境中的資訊。</span><span class="sxs-lookup"><span data-stu-id="9d817-103">A WMI connection manager enables a package to use Windows Management Instrumentation (WMI) to manage information in an enterprise environment.</span></span> <span data-ttu-id="9d817-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含的「Web 服務」工作會使用 WMI 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="9d817-104">The Web Service task that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses a WMI connection manager.</span></span>  
  
 <span data-ttu-id="9d817-105">當您將 WMI 連線管理員加入封裝時， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立在執行時間解析為 WMI 連接的連線管理員、設定連線管理員屬性，並將連線管理員加入 `Connections` 封裝上的集合。</span><span class="sxs-lookup"><span data-stu-id="9d817-105">When you add a WMI connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a WMI connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="9d817-106">連接管理員的 `ConnectionManagerType` 屬性會設為 `WMI`。</span><span class="sxs-lookup"><span data-stu-id="9d817-106">The `ConnectionManagerType` property of the connection manager is set to `WMI`.</span></span>  
  
## <a name="configuration-of-the-wmi-connection-manager"></a><span data-ttu-id="9d817-107">設定 WMI 連接管理員</span><span class="sxs-lookup"><span data-stu-id="9d817-107">Configuration of the WMI Connection Manager</span></span>  
 <span data-ttu-id="9d817-108">您可以利用下列方式設定 WMI 連接管理員：</span><span class="sxs-lookup"><span data-stu-id="9d817-108">You can configure a WMI connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="9d817-109">指定伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="9d817-109">Specify the name of a server.</span></span>  
  
-   <span data-ttu-id="9d817-110">指定伺服器上的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9d817-110">Specify a namespace on the server.</span></span>  
  
-   <span data-ttu-id="9d817-111">選取驗證模式以連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="9d817-111">Select the authentication mode for connecting to the server.</span></span>  
  
 <span data-ttu-id="9d817-112">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="9d817-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="9d817-113">如需可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定之屬性的相關資訊，請參閱 [WMI 連線管理員編輯器](../wmi-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="9d817-113">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [WMI Connection Manager Editor](../wmi-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="9d817-114">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="9d817-114">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d817-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d817-115">See Also</span></span>  
 <span data-ttu-id="9d817-116">[Web 服務工作](../control-flow/web-service-task.md) </span><span class="sxs-lookup"><span data-stu-id="9d817-116">[Web Service Task](../control-flow/web-service-task.md) </span></span>  
 [<span data-ttu-id="9d817-117">Integration Services &#40;SSIS&#41; 連接</span><span class="sxs-lookup"><span data-stu-id="9d817-117">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
