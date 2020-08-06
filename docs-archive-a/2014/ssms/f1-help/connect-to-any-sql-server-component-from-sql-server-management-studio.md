---
title: 從 SQL Server Management Studio 連接到任何 SQL Server 元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SQL Server Management Studio
- saving connections
- components [SQL Server], connections
- SQL Server Management Studio [SQL Server], connections
ms.assetid: 5eeb41bd-b25b-4d3b-a005-a7d9e4b5978e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9cd3e185ea6f289a2a6db46cdca2cb310fefbcf9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702310"
---
# <a name="connect-to-any-sql-server-component-from-sql-server-management-studio"></a><span data-ttu-id="bc42b-102">從 SQL Server Management Studio 連接到任何 SQL Server 元件</span><span class="sxs-lookup"><span data-stu-id="bc42b-102">Connect to Any SQL Server Component from SQL Server Management Studio</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="bc42b-103">提供管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之各項元件所需的功能。</span><span class="sxs-lookup"><span data-stu-id="bc42b-103">provides functionality for managing every component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bc42b-104">請利用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 來連接到：</span><span class="sxs-lookup"><span data-stu-id="bc42b-104">Use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to connect to:</span></span>  
  
-   <span data-ttu-id="bc42b-105">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc42b-105">An instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="bc42b-106">第 1 課：建立 Windows Azure 儲存體物件[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bc42b-106">.</span></span>  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]<span data-ttu-id="bc42b-107">第 1 課：建立 Windows Azure 儲存體物件[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bc42b-107">.</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="bc42b-108">第 1 課：建立 Windows Azure 儲存體物件[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bc42b-108">.</span></span>  
  
 <span data-ttu-id="bc42b-109">雖然 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 可讓您在沒有先建立資料來源連接的情況下，直接使用查詢，但大部分其他工作都需要連接。</span><span class="sxs-lookup"><span data-stu-id="bc42b-109">Although [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] allows you to work with queries without first establishing a connection to a data source, most other tasks require a connection.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="bc42b-110">提供 [連接到伺服器]  對話方塊，可讓您設定對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件的連線屬性。</span><span class="sxs-lookup"><span data-stu-id="bc42b-110">provides the **Connect to Server** dialog box to configure connection properties to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="bc42b-111">當 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 啟動時，便會開啟 [連接到伺服器]  對話方塊，提示您連線到伺服器。</span><span class="sxs-lookup"><span data-stu-id="bc42b-111">When [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] starts, it opens the **Connect to Server** dialog box and prompts you to connect to a server.</span></span> <span data-ttu-id="bc42b-112">[連接到伺服器]  對話方塊會保留上次使用的連線設定。</span><span class="sxs-lookup"><span data-stu-id="bc42b-112">The **Connect to Server** dialog box retains the connection settings from the last time it was used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc42b-113">您可以關閉這項功能，因此，不會自動起始任何連接。</span><span class="sxs-lookup"><span data-stu-id="bc42b-113">This feature can be turned off so no connection is automatically initiated.</span></span> <span data-ttu-id="bc42b-114">如需詳細資訊，請參閱 [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="bc42b-114">For more information, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md).</span></span>  
  
## <a name="saving-connections"></a><span data-ttu-id="bc42b-115">儲存連接</span><span class="sxs-lookup"><span data-stu-id="bc42b-115">Saving Connections</span></span>  
 <span data-ttu-id="bc42b-116">您可以儲存通往「已註冊的伺服器」中之特定伺服器的連接，也可以利用 [方案總管] 來儲存專案中的連接。</span><span class="sxs-lookup"><span data-stu-id="bc42b-116">You can save connections to specific servers in Registered Servers, or you can save connections in projects with Solution Explorer.</span></span>  
  
### <a name="saving-connections-in-registered-servers"></a><span data-ttu-id="bc42b-117">在已註冊的伺服器中儲存連接</span><span class="sxs-lookup"><span data-stu-id="bc42b-117">Saving Connections in Registered Servers</span></span>  
 <span data-ttu-id="bc42b-118">當您註冊伺服器時， [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 會在已註冊的伺服器中儲存連接資訊。</span><span class="sxs-lookup"><span data-stu-id="bc42b-118">When you register a server, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] saves the connection information in Registered Servers.</span></span> <span data-ttu-id="bc42b-119">若要連接到已註冊的伺服器，請在 [已註冊的伺服器] 中，按兩下這個伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="bc42b-119">To connect to a registered server, double-click the server name in Registered Servers.</span></span> <span data-ttu-id="bc42b-120">之後，[物件總管] 就會開啟通往伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="bc42b-120">Object Explorer then opens a connection to the server.</span></span>  
  
### <a name="saving-connections-in-solution-explorer"></a><span data-ttu-id="bc42b-121">在 [方案總管] 中儲存連接</span><span class="sxs-lookup"><span data-stu-id="bc42b-121">Saving Connections in Solution Explorer</span></span>  
 <span data-ttu-id="bc42b-122">[方案總管] 可讓您在專案中儲存相關的查詢、指令碼、連接和其他相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="bc42b-122">Solution Explorer allows you to store related queries, scripts, connections, and other associated information in a project.</span></span> <span data-ttu-id="bc42b-123">每個指令碼專案都包含名為 **連線**的節點，讓您可以從中儲存一或多個連線。</span><span class="sxs-lookup"><span data-stu-id="bc42b-123">Each script project contains a node called **Connections**, where you can save one or more connections.</span></span> <span data-ttu-id="bc42b-124">若要新增連接，請在 [連線]  滑鼠右鍵，然後按一下 [新增連線]  。</span><span class="sxs-lookup"><span data-stu-id="bc42b-124">To add a connection, right-click **Connections**, and then click **New Connection**.</span></span> <span data-ttu-id="bc42b-125">若要存取儲存的連線，請展開 [連線]  ，再按兩下該連線。</span><span class="sxs-lookup"><span data-stu-id="bc42b-125">To access a saved connection, expand **Connections** and double-click the connection.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="bc42b-126">會開啟該連線所關聯的查詢視窗。</span><span class="sxs-lookup"><span data-stu-id="bc42b-126">opens a query window associated with that connection.</span></span> <span data-ttu-id="bc42b-127">儲存好之後，指令碼會保留它們與特定連接的關聯。</span><span class="sxs-lookup"><span data-stu-id="bc42b-127">When saved, scripts retain their association to a specific connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc42b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc42b-128">See Also</span></span>  
 <span data-ttu-id="bc42b-129">[使用 SQL Server Management Studio](../sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="bc42b-129">[Use SQL Server Management Studio](../sql-server-management-studio-ssms.md) </span></span>  
 [<span data-ttu-id="bc42b-130">物件總管</span><span class="sxs-lookup"><span data-stu-id="bc42b-130">Object Explorer</span></span>](../object/object-explorer.md)  
  
  
