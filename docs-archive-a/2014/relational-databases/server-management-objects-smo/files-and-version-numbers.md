---
title: 檔案和版本號碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
author: stevestein
ms.author: sstein
ms.openlocfilehash: f1a7286f15af28f97e488b8b40fd745a0d320108
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595912"
---
# <a name="files-and-version-numbers"></a><span data-ttu-id="352d8-102">檔案和版本號碼</span><span class="sxs-lookup"><span data-stu-id="352d8-102">Files and Version Numbers</span></span>
  <span data-ttu-id="352d8-103">所有必要的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理物件 (SMO) 元件會安裝為 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端或伺服器實例的一部分。</span><span class="sxs-lookup"><span data-stu-id="352d8-103">All required [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) components are installed as part of an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client or server.</span></span> <span data-ttu-id="352d8-104">SMO 是實作於數個 Managed 組件中。</span><span class="sxs-lookup"><span data-stu-id="352d8-104">SMO is implemented in several managed assemblies.</span></span> <span data-ttu-id="352d8-105">您可以在用戶端或伺服器上開發 SMO 應用程式。</span><span class="sxs-lookup"><span data-stu-id="352d8-105">You can develop SMO applications on either a client or a server.</span></span>  
  
|<span data-ttu-id="352d8-106">目錄</span><span class="sxs-lookup"><span data-stu-id="352d8-106">Directory</span></span>|<span data-ttu-id="352d8-107">檔案</span><span class="sxs-lookup"><span data-stu-id="352d8-107">File</span></span>|<span data-ttu-id="352d8-108">描述</span><span class="sxs-lookup"><span data-stu-id="352d8-108">Description</span></span>|  
|---------------|----------|-----------------|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="352d8-109">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="352d8-109">Microsoft.SqlServer.ConnectionInfo.dll</span></span>|<span data-ttu-id="352d8-110">包含與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體進行連接的支援。</span><span class="sxs-lookup"><span data-stu-id="352d8-110">Contains support for connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="352d8-111">Microsoft.SqlServer.ServiceBrokerEnum.dll</span><span class="sxs-lookup"><span data-stu-id="352d8-111">Microsoft.SqlServer.ServiceBrokerEnum.dll</span></span>|<span data-ttu-id="352d8-112">包含 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker 程式設計的支援。</span><span class="sxs-lookup"><span data-stu-id="352d8-112">Contains support for programming the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker.</span></span> <span data-ttu-id="352d8-113">只有在存取 Service Broker 的程式中才需要此檔案。</span><span class="sxs-lookup"><span data-stu-id="352d8-113">This is required only in programs that access the Service Broker.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="352d8-114">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="352d8-114">Microsoft.SqlServer.Smo.dll</span></span>|<span data-ttu-id="352d8-115">包含大部分的 SMO 類別。</span><span class="sxs-lookup"><span data-stu-id="352d8-115">Contains the most of the SMO classes.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="352d8-116">Microsoft.SqlServer.SmoExtended.dll</span><span class="sxs-lookup"><span data-stu-id="352d8-116">Microsoft.SqlServer.SmoExtended.dll</span></span><br /><br /> <span data-ttu-id="352d8-117">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span><span class="sxs-lookup"><span data-stu-id="352d8-117">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span></span><br /><br /> <span data-ttu-id="352d8-118">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="352d8-118">Microsoft.SqlServer.SqlEnum.dll</span></span>|<span data-ttu-id="352d8-119">包含 SMO 類別的支援。</span><span class="sxs-lookup"><span data-stu-id="352d8-119">Contains support for the SMO classes.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="352d8-120">Microsoft.SqlServer.WmiEnum.dll</span><span class="sxs-lookup"><span data-stu-id="352d8-120">Microsoft.SqlServer.WmiEnum.dll</span></span>|<span data-ttu-id="352d8-121">包含 Windows Management Instrumentation (WMI) 提供者類別。</span><span class="sxs-lookup"><span data-stu-id="352d8-121">Contains the Windows Management Instrumentation (WMI) Provider classes.</span></span> <span data-ttu-id="352d8-122">這只有在使用 WMI 提供者類別的程式中才需要此檔案。</span><span class="sxs-lookup"><span data-stu-id="352d8-122">This is required only for programs that use the WMI Provider classes.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="352d8-123">Microsoft.SqlServer.RegSvrEnum.dll</span><span class="sxs-lookup"><span data-stu-id="352d8-123">Microsoft.SqlServer.RegSvrEnum.dll</span></span>|<span data-ttu-id="352d8-124">包含已註冊的伺服器的類別。</span><span class="sxs-lookup"><span data-stu-id="352d8-124">Contains the Registered Server classes.</span></span> <span data-ttu-id="352d8-125">這只有在使用已註冊伺服器類別的程式中才需要此檔案。</span><span class="sxs-lookup"><span data-stu-id="352d8-125">This is required only for programs that use the Registered Server classes.</span></span>|  
  
  
