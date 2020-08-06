---
title: FTP 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- FTP connection manager
- connections [Integration Services], FTP
- connection managers [Integration Services], FTP
ms.assetid: c4f43455-29ca-44ba-ac7f-ea729b1daf93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a402f399ba4b7e69fc1d3cbca9dd64b32217ced1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688121"
---
# <a name="ftp-connection-manager"></a><span data-ttu-id="d5419-102">FTP 連接管理員</span><span class="sxs-lookup"><span data-stu-id="d5419-102">FTP Connection Manager</span></span>
  <span data-ttu-id="d5419-103">FTP 連接管理員可讓封裝連接到「檔案傳輸通訊協定 (FTP)」伺服器。</span><span class="sxs-lookup"><span data-stu-id="d5419-103">An FTP connection manager enables a package to connect to a File Transfer Protocol (FTP) server.</span></span> <span data-ttu-id="d5419-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含的 FTP 工作會使用此連線管理員。</span><span class="sxs-lookup"><span data-stu-id="d5419-104">The FTP task that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses this connection manager.</span></span>  
  
 <span data-ttu-id="d5419-105">當您將 FTP 連接管理員加入封裝時，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立在執行階段可解析為 FTP 連接的連接管理員、設定連接管理員屬性，並將連接管理員加入封裝上的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="d5419-105">When you add an FTP connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that can be resolved as an FTP connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="d5419-106">連接管理員的 `ConnectionManagerType` 屬性會設為 `FTP`。</span><span class="sxs-lookup"><span data-stu-id="d5419-106">The `ConnectionManagerType` property of the connection manager is set to `FTP`.</span></span>  
  
 <span data-ttu-id="d5419-107">您可以利用下列方式設定 FTP 連接管理員：</span><span class="sxs-lookup"><span data-stu-id="d5419-107">You can configure the FTP connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="d5419-108">指定伺服器名稱和伺服器通訊埠。</span><span class="sxs-lookup"><span data-stu-id="d5419-108">Specify a server name and server port.</span></span>  
  
-   <span data-ttu-id="d5419-109">指定匿名存取，或提供基本驗證的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="d5419-109">Specify anonymous access, or provide a user name and a password for basic authentication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d5419-110">FTP 連接管理員僅支援匿名驗證和基本驗證，</span><span class="sxs-lookup"><span data-stu-id="d5419-110">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="d5419-111">而不支援 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="d5419-111">It does not support Windows Authentication.</span></span>  
  
-   <span data-ttu-id="d5419-112">設定逾時、重試次數，以及一次複製的資料數量。</span><span class="sxs-lookup"><span data-stu-id="d5419-112">Set the time-out, number of retries, and the amount of data to copy at a time.</span></span>  
  
-   <span data-ttu-id="d5419-113">指示 FTP 連接管理員使用被動還是主動模式。</span><span class="sxs-lookup"><span data-stu-id="d5419-113">Indicate whether the FTP connection manager uses passive or active mode.</span></span>  
  
 <span data-ttu-id="d5419-114">依據 FTP 連接管理員連接之 FTP 站台的組態而定，您可能必須變更連接管理員的下列預設值：</span><span class="sxs-lookup"><span data-stu-id="d5419-114">Depending on the configuration of the FTP site to which the FTP connection manager connects, you may need to change the following default values of the connection manager:</span></span>  
  
-   <span data-ttu-id="d5419-115">伺服器通訊埠設定為 21。</span><span class="sxs-lookup"><span data-stu-id="d5419-115">The server port is set to 21.</span></span> <span data-ttu-id="d5419-116">您應該指定 FTP 站台接聽的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="d5419-116">You should specify the port that the FTP site listens to.</span></span>  
  
-   <span data-ttu-id="d5419-117">使用者名稱設定為 "anonymous"。</span><span class="sxs-lookup"><span data-stu-id="d5419-117">The user name is set to "anonymous".</span></span> <span data-ttu-id="d5419-118">您應該提供 FTP 站台需要的認證。</span><span class="sxs-lookup"><span data-stu-id="d5419-118">You should provide the credentials that the FTP site requires.</span></span>  
  
## <a name="activepassive-modes"></a><span data-ttu-id="d5419-119">主動/被動模式</span><span class="sxs-lookup"><span data-stu-id="d5419-119">Active/Passive Modes</span></span>  
 <span data-ttu-id="d5419-120">FTP 連接管理員可使用主動模式或使用被動模式來傳送和接收檔案。</span><span class="sxs-lookup"><span data-stu-id="d5419-120">An FTP connection manager can send and receive files using either active mode or passive mode.</span></span> <span data-ttu-id="d5419-121">在主動模式中，伺服器會起始資料連接，而在被動模式中，用戶端會起始資料連接。</span><span class="sxs-lookup"><span data-stu-id="d5419-121">In active mode, the server initiates the data connection, and in passive mode, the client initiates the data connection.</span></span>  
  
## <a name="configuration-of-the-ftp-connection-manager"></a><span data-ttu-id="d5419-122">設定 FTP 連接管理員</span><span class="sxs-lookup"><span data-stu-id="d5419-122">Configuration of the FTP Connection Manager</span></span>  
 <span data-ttu-id="d5419-123">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="d5419-123">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d5419-124">如需可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定之屬性的資訊，請參閱 [FTP 連線管理員編輯器](../ftp-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="d5419-124">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [FTP Connection Manager Editor](../ftp-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="d5419-125">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="d5419-125">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5419-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5419-126">See Also</span></span>  
 <span data-ttu-id="d5419-127">[FTP 工作](../control-flow/ftp-task.md) </span><span class="sxs-lookup"><span data-stu-id="d5419-127">[FTP Task](../control-flow/ftp-task.md) </span></span>  
 [<span data-ttu-id="d5419-128">Integration Services &#40;SSIS&#41; 連接</span><span class="sxs-lookup"><span data-stu-id="d5419-128">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
