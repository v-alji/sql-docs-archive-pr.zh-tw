---
title: 適用于 SAP BW 的 Microsoft Connector 1.1 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5281f080-53d5-4679-aa26-f4cd4ac7a2df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ec5cfe83b201976be0512c54b77bc79f8aa824b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705270"
---
# <a name="microsoft-connector-11-for-sap-bw"></a><span data-ttu-id="033e3-102">Microsoft Connector 1.1 for SAP BW</span><span class="sxs-lookup"><span data-stu-id="033e3-102">Microsoft Connector 1.1 for SAP BW</span></span>
  <span data-ttu-id="033e3-103">[!INCLUDE[msCoName](../includes/msconame-md.md)]適用于 SAP BW 的連接器1.1 是由三個元件所組成，可讓您將資料從 SAP NETWEAVER BW 版本7系統中提取或載入資料。</span><span class="sxs-lookup"><span data-stu-id="033e3-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW consists of a set of three components that let you extract data from, or load data into, an SAP Netweaver BW version 7 system.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="033e3-104">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="033e3-104">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="033e3-105">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="033e3-105">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="033e3-106">擷取 SAP Netweaver BW 中的資料需要額外的 SAP 授權。</span><span class="sxs-lookup"><span data-stu-id="033e3-106">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="033e3-107">請洽詢 SAP 以確認這些需求。</span><span class="sxs-lookup"><span data-stu-id="033e3-107">Check with SAP to verify these requirements.</span></span>  
  
## <a name="components"></a><span data-ttu-id="033e3-108">元件</span><span class="sxs-lookup"><span data-stu-id="033e3-108">Components</span></span>  
 <span data-ttu-id="033e3-109">[!INCLUDE[msCoName](../includes/msconame-md.md)]適用于 SAP BW 的連接器1.1 具有下列元件：</span><span class="sxs-lookup"><span data-stu-id="033e3-109">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW has the following components:</span></span>  
  
-   <span data-ttu-id="033e3-110">**SAP BW 來源** - SAP BW 來源是一個資料流程來源元件，可讓您擷取 SAP Netweaver BW 版本 7 系統中的資料。</span><span class="sxs-lookup"><span data-stu-id="033e3-110">**SAP BW Source**-The SAP BW source is a data flow source component that lets you extract data from an SAP Netweaver BW version 7 system.</span></span>  
  
-   <span data-ttu-id="033e3-111">**SAP BW 目的地** - SAP BW 目的地是一個資料流程目的地元件，可讓您將資料載入至 SAP Netweaver BW 版本 7 系統中。</span><span class="sxs-lookup"><span data-stu-id="033e3-111">**SAP BW Destination**-The SAP BW destination is a data flow destination component that lets you load data into an SAP Netweaver BW version 7 system.</span></span>  
  
-   <span data-ttu-id="033e3-112">**SAP BW 連線管理員** - SAP BW 連線管理員可將 SAP BW 來源或 SAP BW 目的地連接至 SAP Netweaver BW 版本 7 系統。</span><span class="sxs-lookup"><span data-stu-id="033e3-112">**SAP BW Connection Manager**-The SAP BW connection manager connects either an SAP BW source or SAP BW destination to an SAP Netweaver BW version 7 system.</span></span>  
  
 <span data-ttu-id="033e3-113">如需示範如何設定及使用 SAP BW 連線管理員、來源和目的地的逐步解說，請參閱技術白皮書： [Using SQL Server Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkId=301897)(搭配 SAP BI 7.0 使用 SQL Server Integration Services)。</span><span class="sxs-lookup"><span data-stu-id="033e3-113">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkId=301897).</span></span> <span data-ttu-id="033e3-114">這份技術白皮書也會示範如何設定 SAP BW 中的必要物件。</span><span class="sxs-lookup"><span data-stu-id="033e3-114">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
## <a name="documentation"></a><span data-ttu-id="033e3-115">文件</span><span class="sxs-lookup"><span data-stu-id="033e3-115">Documentation</span></span>  
 <span data-ttu-id="033e3-116">適用于 SAP BW 的連接器1.1 的這個說明檔 [!INCLUDE[msCoName](../includes/msconame-md.md)] 包含下列主題和章節：</span><span class="sxs-lookup"><span data-stu-id="033e3-116">This Help file for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW contains the following topics and sections:</span></span>  
  
 [<span data-ttu-id="033e3-117">安裝 Microsoft Connector for 1.1 SAP BW</span><span class="sxs-lookup"><span data-stu-id="033e3-117">Installing the Microsoft Connector for 1.1 SAP BW</span></span>](installing-the-microsoft-connector-for-sap-bw.md)  
 <span data-ttu-id="033e3-118">說明 [!INCLUDE[msCoName](../includes/msconame-md.md)] SAP BW 的連接器1.1 安裝需求。</span><span class="sxs-lookup"><span data-stu-id="033e3-118">Describes the installation requirements for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
 [<span data-ttu-id="033e3-119">Microsoft Connector 1.1 for SAP BW 元件</span><span class="sxs-lookup"><span data-stu-id="033e3-119">Microsoft Connector 1.1 for SAP BW Components</span></span>](microsoft-connector-for-sap-bw-components.md)  
 <span data-ttu-id="033e3-120">描述 SAP BW 的連接器1.1 的每個元件 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="033e3-120">Describes each component of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
 [<span data-ttu-id="033e3-121">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="033e3-121">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](microsoft-connector-for-sap-bw-f1-help.md)  
 <span data-ttu-id="033e3-122">描述 SAP BW 的連接器1.1 每個元件的使用者介面 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="033e3-122">Describes the user interface of each component of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
  
