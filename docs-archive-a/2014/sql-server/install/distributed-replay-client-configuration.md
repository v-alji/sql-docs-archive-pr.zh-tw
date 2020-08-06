---
title: Distributed Replay 用戶端設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccf03e32-6bd9-43c0-b9b6-9fe0d9163339
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 53124029483c25ed7894b279283e1de02c647350
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606608"
---
# <a name="distributed-replay-client-configuration"></a><span data-ttu-id="f3a9d-102">Distributed Replay Client 組態</span><span class="sxs-lookup"><span data-stu-id="f3a9d-102">Distributed Replay Client Configuration</span></span>
  <span data-ttu-id="f3a9d-103">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈的 [Distributed Replay Client 組態]\*\*\*\* 頁面來指定您想要授與 Distributed Replay Client 服務之管理權限的使用者。</span><span class="sxs-lookup"><span data-stu-id="f3a9d-103">Use the **Distributed Replay Client Configuration** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to specify the users you want to grant administrative permissions to for the Distributed Replay client service.</span></span>  
  
 <span data-ttu-id="f3a9d-104">擁有管理權限的使用者將可不受限制地存取 Distributed Replay Client 服務。</span><span class="sxs-lookup"><span data-stu-id="f3a9d-104">Users that have administrative permissions will have unlimited access to the Distributed Replay client service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f3a9d-105">選項</span><span class="sxs-lookup"><span data-stu-id="f3a9d-105">Options</span></span>  
 <span data-ttu-id="f3a9d-106">**控制器名稱**</span><span class="sxs-lookup"><span data-stu-id="f3a9d-106">**Controller Name**</span></span>  
 <span data-ttu-id="f3a9d-107">這是選擇性參數，預設值是 \<*blank*> 。</span><span class="sxs-lookup"><span data-stu-id="f3a9d-107">This is an optional parameter, and the default value is \<*blank*>.</span></span>  
  
 <span data-ttu-id="f3a9d-108">針對 Distributed Replay Client 服務，輸入將與用戶端電腦進行通訊之控制器的名稱。</span><span class="sxs-lookup"><span data-stu-id="f3a9d-108">Enter the name of the controller that the client computer will communicate with for the Distributed Replay client service.</span></span> <span data-ttu-id="f3a9d-109">請注意：</span><span class="sxs-lookup"><span data-stu-id="f3a9d-109">Note the following:</span></span>  
  
-   <span data-ttu-id="f3a9d-110">名稱必須是完整網域名稱 (FQDN)。</span><span class="sxs-lookup"><span data-stu-id="f3a9d-110">The name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="f3a9d-111">例如，Microsoft 的產品階層中稱為 server1 的主機，其 FQDN 會是 server1.products.microsoft.com。</span><span class="sxs-lookup"><span data-stu-id="f3a9d-111">For example, a host called server1 in the products hierarchy at Microsoft may have an FQDN of server1.products.microsoft.com.</span></span>  
  
-   <span data-ttu-id="f3a9d-112">如果您已經設定了控制器，請在設定每個用戶端時輸入該控制器的名稱。</span><span class="sxs-lookup"><span data-stu-id="f3a9d-112">If you have already set up a controller, enter the name of the controller while configuring each client.</span></span>  
  
-   <span data-ttu-id="f3a9d-113">如果您尚未設定控制器，則可以將控制器名稱留空。</span><span class="sxs-lookup"><span data-stu-id="f3a9d-113">If you have net yet set up a controller, you can leave the controller name blank.</span></span> <span data-ttu-id="f3a9d-114">不過，您必須在 [用戶端組態]  檔中，手動輸入控制器名稱。</span><span class="sxs-lookup"><span data-stu-id="f3a9d-114">However, you must manually enter the controller name in the **client configuration** file.</span></span>  
  
 <span data-ttu-id="f3a9d-115">**工作目錄**</span><span class="sxs-lookup"><span data-stu-id="f3a9d-115">**Working Directory**</span></span>  
 <span data-ttu-id="f3a9d-116">指定 Distributed Replay Client 服務的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="f3a9d-116">Specify the working directory for the Distributed Replay client service.</span></span>  
  
 <span data-ttu-id="f3a9d-117">預設工作目錄為 \<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\。</span><span class="sxs-lookup"><span data-stu-id="f3a9d-117">The default working directory is \<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\.</span></span>  
  
 <span data-ttu-id="f3a9d-118">**結果目錄**</span><span class="sxs-lookup"><span data-stu-id="f3a9d-118">**Result Directory**</span></span>  
 <span data-ttu-id="f3a9d-119">指定 Distributed Replay Client 服務的結果目錄。</span><span class="sxs-lookup"><span data-stu-id="f3a9d-119">Specify the result directory for the Distributed Replay client service.</span></span>  
  
 <span data-ttu-id="f3a9d-120">預設結果目錄為 \<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\。</span><span class="sxs-lookup"><span data-stu-id="f3a9d-120">The default result directory is \<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\.</span></span>  
  
  
