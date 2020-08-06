---
title: SQL Server 設定管理員說明 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, help
ms.assetid: 6e909911-39a6-469b-b22a-3afdfd08a30b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 10a6d6052fe109892f975774a1ed65b818ef0581
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705777"
---
# <a name="sql-server-configuration-manager-help"></a><span data-ttu-id="1f8a9-102">SQL Server 組態管理員說明</span><span class="sxs-lookup"><span data-stu-id="1f8a9-102">SQL Server Configuration Manager Help</span></span>
  <span data-ttu-id="1f8a9-103">您可以使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」來設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務以及設定網路連接性。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-103">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and configure network connectivity.</span></span> <span data-ttu-id="1f8a9-104">若要建立或管理資料庫物件、設定安全性以及撰寫 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢，請使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-104">To create or manage database objects, configure security, and write [!INCLUDE[tsql](../../includes/tsql-md.md)] queries, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="1f8a9-105">如需有關 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的詳細資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-105">For more information about [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="1f8a9-106">本節包含關於「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」中對話方塊的 F1 說明主題。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-106">This section contains the F1 Help topics for the dialogs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1f8a9-107">Configuration Manager 無法設定早於 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-107">Configuration Manager cannot configure versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="services"></a><span data-ttu-id="1f8a9-108">服務</span><span class="sxs-lookup"><span data-stu-id="1f8a9-108">Services</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1f8a9-109">組態管理員」可用來管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-109">Configuration Manager manages services that are related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1f8a9-110">雖然大部分的工作可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 的 [Windows 服務] 對話方塊來完成，但請特別注意，「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」可對其所管理的服務執行其他作業，如在服務帳戶變更時套用正確的權限。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-110">Although many of these tasks can be accomplished using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Services dialog, is important to note that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager performs additional operations on the services it manages, such as applying the correct permissions when the service account is changed.</span></span> <span data-ttu-id="1f8a9-111">使用一般的 [Windows 服務] 對話方塊來設定任一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務可能會導致服務異常。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-111">Using the normal Windows Services dialog to configure any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services might cause the service to malfunction.</span></span>  
  
 <span data-ttu-id="1f8a9-112">您可以使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」來執行下列服務工作：</span><span class="sxs-lookup"><span data-stu-id="1f8a9-112">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for the following tasks for services:</span></span>  
  
-   <span data-ttu-id="1f8a9-113">啟動、停止與暫停服務</span><span class="sxs-lookup"><span data-stu-id="1f8a9-113">Start, stop, and pause services</span></span>  
  
-   <span data-ttu-id="1f8a9-114">將服務設定為自動或手動啟動、停用服務，或變更其他服務設定</span><span class="sxs-lookup"><span data-stu-id="1f8a9-114">Configure services to start automatically or manually, disable the services, or change other service settings</span></span>  
  
-   <span data-ttu-id="1f8a9-115">變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務使用的帳戶密碼</span><span class="sxs-lookup"><span data-stu-id="1f8a9-115">Change the passwords for the accounts used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services</span></span>  
  
-   <span data-ttu-id="1f8a9-116">使用追蹤旗標 (命令列參數) 啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f8a9-116">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using trace flags (command line parameters)</span></span>  
  
-   <span data-ttu-id="1f8a9-117">檢視服務屬性</span><span class="sxs-lookup"><span data-stu-id="1f8a9-117">View the properties of services</span></span>  
  
## <a name="sql-server-network-configuration"></a><span data-ttu-id="1f8a9-118">SQL Server 網路組態</span><span class="sxs-lookup"><span data-stu-id="1f8a9-118">SQL Server Network Configuration</span></span>  
 <span data-ttu-id="1f8a9-119">您可以使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」來執行此電腦上與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務相關的下列工作：</span><span class="sxs-lookup"><span data-stu-id="1f8a9-119">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for the following tasks related to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services on this computer:</span></span>  
  
-   <span data-ttu-id="1f8a9-120">啟用或停用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="1f8a9-120">Enable or disable a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] network protocol</span></span>  
  
-   <span data-ttu-id="1f8a9-121">設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="1f8a9-121">Configure a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] network protocol</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f8a9-122">如需如何設定通訊協定並連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的簡要教學課程，請參閱 [教學課程：Database Engine 使用者入門](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-122">For a short tutorial about how to configure protocols and connect to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], see [Tutorial: Getting Started with the Database Engine](../../relational-databases/tutorial-getting-started-with-the-database-engine.md).</span></span>  
  
## <a name="sql-server-native-client-configuration"></a><span data-ttu-id="1f8a9-123">SQL Server Native Client 組態</span><span class="sxs-lookup"><span data-stu-id="1f8a9-123">SQL Server Native Client Configuration</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1f8a9-124">用戶端使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 網路程式庫連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-124">clients connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client network library.</span></span> <span data-ttu-id="1f8a9-125">您可以使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」執行與此電腦用戶端應用程式相關的下列工作：</span><span class="sxs-lookup"><span data-stu-id="1f8a9-125">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for the following tasks related to client applications on this computer:</span></span>  
  
-   <span data-ttu-id="1f8a9-126">針對此電腦上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端應用程式，指定連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體時要使用的通訊協定順序。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-126">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client applications on this computer, specify the protocol order, when connecting to instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="1f8a9-127">設定用戶端連接通訊協定。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-127">Configure client connection protocols.</span></span>  
  
-   <span data-ttu-id="1f8a9-128">針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端應用程式，建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的別名，使用戶端可以用自訂的連接字串來連接。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-128">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client applications, create aliases for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], so that clients can connect using a custom connection string.</span></span>  
  
 <span data-ttu-id="1f8a9-129">如需有關這些工作的詳細資訊，請參閱各項工作的 F1 說明。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-129">For more information about each of these tasks, see F1 help for each task.</span></span>  
  
#### <a name="to-open-sql-server-configuration-manager"></a><span data-ttu-id="1f8a9-130">若要開啟 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="1f8a9-130">To open SQL Server Configuration Manager</span></span>  
  
-   <span data-ttu-id="1f8a9-131">在 [開始]\*\*\*\* 功能表上，依序指向 [所有程式]\*\*\*\*、[Microsoft SQL Server]\*\*\*\* \(版本) 和 [組態工具]\*\*\*\*，然後按一下 [SQL Server 組態管理員]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1f8a9-131">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server** (version), point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f8a9-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f8a9-132">See Also</span></span>  
 <span data-ttu-id="1f8a9-133">[SQL Server 服務](../../../2014/tools/configuration-manager/sql-server-services.md) </span><span class="sxs-lookup"><span data-stu-id="1f8a9-133">[SQL Server Services](../../../2014/tools/configuration-manager/sql-server-services.md) </span></span>  
 <span data-ttu-id="1f8a9-134">[SQL Server 網路設定](sql-server-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="1f8a9-134">[SQL Server Network Configuration](sql-server-network-configuration.md) </span></span>  
 <span data-ttu-id="1f8a9-135">[SQL Native Client 11.0 設定](../../../2014/tools/configuration-manager/sql-native-client-11-0-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="1f8a9-135">[SQL Native Client 11.0 Configuration](../../../2014/tools/configuration-manager/sql-native-client-11-0-configuration.md) </span></span>  
 [<span data-ttu-id="1f8a9-136">選擇網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="1f8a9-136">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
