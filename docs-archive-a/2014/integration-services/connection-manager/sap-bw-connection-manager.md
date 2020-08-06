---
title: SAP BW 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 06b166a1-a9df-48ea-a0e8-9b8d6979c0a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bc3bb32c4895c6ec8fbcf31d57e8685c74de32dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592813"
---
# <a name="sap-bw-connection-manager"></a><span data-ttu-id="1fcef-102">SAP BW 連接管理員</span><span class="sxs-lookup"><span data-stu-id="1fcef-102">SAP BW Connection Manager</span></span>
  <span data-ttu-id="1fcef-103">SAP BW 連接管理員是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的連接管理員元件。</span><span class="sxs-lookup"><span data-stu-id="1fcef-103">The SAP BW connection manager is the connection manager component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="1fcef-104">因此，SAP BW 連接管理員會提供 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 來源和目的地元件所需之 SAP Netweaver BW 版本 7 系統的連接</span><span class="sxs-lookup"><span data-stu-id="1fcef-104">Thus, the SAP BW connection manager provides the connectivity to an SAP Netweaver BW version 7 system that the source and destination components of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW need.</span></span> <span data-ttu-id="1fcef-105">(使用 SAP BW 連線管理員的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 元件只有屬於 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Connector 1.1 for SAP BW 封裝一部分的 SAP BW 來源和目的地)。</span><span class="sxs-lookup"><span data-stu-id="1fcef-105">(The SAP BW source and destination that are part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW package are the only [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components that use the SAP BW connection manager.)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1fcef-106">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="1fcef-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="1fcef-107">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="1fcef-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="1fcef-108">當您將 SAP BW 連接管理員加入至封裝時，連接管理員的 `ConnectionManagerType` 屬性就會設定為 `SAPBI`。</span><span class="sxs-lookup"><span data-stu-id="1fcef-108">When you add an SAP BW connection manager to a package, the `ConnectionManagerType` property of the connection manager is set to `SAPBI`.</span></span>  
  
## <a name="configuring-the-sap-bw-connection-manager"></a><span data-ttu-id="1fcef-109">設定 SAP BW 連接管理員</span><span class="sxs-lookup"><span data-stu-id="1fcef-109">Configuring the SAP BW Connection Manager</span></span>  
 <span data-ttu-id="1fcef-110">您可以利用下列方式設定 SAP BW 連接管理員：</span><span class="sxs-lookup"><span data-stu-id="1fcef-110">You can configure the SAP BW connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="1fcef-111">提供連接的用戶端、使用者名稱、密碼和語言。</span><span class="sxs-lookup"><span data-stu-id="1fcef-111">Provide the client, user name, password, and language for the connection.</span></span>  
  
-   <span data-ttu-id="1fcef-112">選擇要連接到單一應用程式伺服器，還是負載平衡的伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="1fcef-112">Choose whether to connect to a single application server or to a group of load-balanced servers.</span></span>  
  
-   <span data-ttu-id="1fcef-113">提供單一應用程式伺服器的主機和系統編號，或提供負載平衡伺服器群組的訊息伺服器、群組和 SID。</span><span class="sxs-lookup"><span data-stu-id="1fcef-113">Provide the host and system number for a single application server, or provide the message server, group, and SID for a group of load-balanced servers.</span></span>  
  
-   <span data-ttu-id="1fcef-114">針對 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的元件啟用 RFC 函數呼叫的自訂記錄</span><span class="sxs-lookup"><span data-stu-id="1fcef-114">Enable custom logging of RFC function calls for the components of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="1fcef-115">(這項記錄與您針對 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝啟用的選擇性記錄是分開的)。若要啟用 RFC 函數呼叫的記錄，您必須指定一個目錄，用以儲存每個 RFC 函數呼叫前後建立的記錄檔</span><span class="sxs-lookup"><span data-stu-id="1fcef-115">(This logging is separate from the optional logging that you can enable on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.) To enable logging of RFC function calls, you specify a directory in which to store the log files that are created before and after each RFC function call.</span></span> <span data-ttu-id="1fcef-116">(這項記錄功能會使用 XML 格式來建立許多記錄檔。</span><span class="sxs-lookup"><span data-stu-id="1fcef-116">(This logging feature creates many log files in XML format.</span></span> <span data-ttu-id="1fcef-117">因為這些記錄檔也包含所有傳輸的資料列，所以這些記錄檔可能會耗用大量磁碟空間)。如果您沒有選取記錄目錄，就不會啟用記錄功能。</span><span class="sxs-lookup"><span data-stu-id="1fcef-117">As these log files also contain all the rows of data that are transferred, these log files may consume a large amount of disk space.) If you do not select a log directory, logging is not enabled.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1fcef-118">如果傳輸的資料包含機密資訊，這些記錄檔也會包含該項機密資訊。</span><span class="sxs-lookup"><span data-stu-id="1fcef-118">If the data that is transferred contains sensitive information, the log files will also contain that sensitive information.</span></span>  
  
-   <span data-ttu-id="1fcef-119">使用您已輸入的值來測試連接。</span><span class="sxs-lookup"><span data-stu-id="1fcef-119">Use the values that you have entered to test the connection.</span></span>  
  
 <span data-ttu-id="1fcef-120">如果您不知道設定連接管理員的所有必要值，可能必須詢問 SAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="1fcef-120">If you do not know all the values that are required to configure the connection manager, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="1fcef-121">如需示範如何設定及使用 SAP BW 連接管理員、來源和目的地的逐步解說，請參閱＜ [搭配 SAP BI 7.0 使用 SQL Server 2008 Integration Services](https://go.microsoft.com/fwlink/?LinkID=137090)＞技術白皮書。</span><span class="sxs-lookup"><span data-stu-id="1fcef-121">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server 2008 Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkID=137090).</span></span> <span data-ttu-id="1fcef-122">這份技術白皮書也會示範如何設定 SAP BW 中的必要物件。</span><span class="sxs-lookup"><span data-stu-id="1fcef-122">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
### <a name="using-the-ssis-designer-to-configure-the-source"></a><span data-ttu-id="1fcef-123">使用 SSIS 設計師設定來源</span><span class="sxs-lookup"><span data-stu-id="1fcef-123">Using the SSIS Designer to Configure the Source</span></span>  
 <span data-ttu-id="1fcef-124">如需有關可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定之 SAP BW 連接管理員屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="1fcef-124">For more information about the properties of the SAP BW connection manager that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="1fcef-125">SAP BW 連線管理員編輯器</span><span class="sxs-lookup"><span data-stu-id="1fcef-125">SAP BW Connection Manager Editor</span></span>](../sap-bw-connection-manager-editor.md)  
  
## <a name="see-also"></a><span data-ttu-id="1fcef-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fcef-126">See Also</span></span>  
 [<span data-ttu-id="1fcef-127">Microsoft Connector 1.1 for SAP BW 元件</span><span class="sxs-lookup"><span data-stu-id="1fcef-127">Microsoft Connector 1.1 for SAP BW Components</span></span>](../microsoft-connector-for-sap-bw-components.md)  
  
  
