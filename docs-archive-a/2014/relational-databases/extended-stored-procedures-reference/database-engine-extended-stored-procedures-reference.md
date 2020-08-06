---
title: 擴充預存程序程式設計人員參考 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- extended stored procedures [SQL Server], listed
ms.assetid: 4e9d0374-0927-4f17-bab9-2215b1b8fea8
author: rothja
ms.author: jroth
ms.openlocfilehash: f3b1beade751cd7a7407f3c33eb7f8ae58c9fd4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606316"
---
# <a name="extended-stored-procedures-programmer39s-reference"></a><span data-ttu-id="a299d-102">擴充預存程式程式設計人員&#39;s 參考</span><span class="sxs-lookup"><span data-stu-id="a299d-102">Extended Stored Procedures Programmer&#39;s Reference</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="a299d-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="a299d-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="a299d-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)]擴充預存程式 API （先前為 Open 資料服務的一部分）提供以伺服器為基礎的應用程式開發介面， (API) 來擴充 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="a299d-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Extended Stored Procedure API, previously part of Open Data Services, provides a server-based application programming interface (API) for extending [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] functionality.</span></span> <span data-ttu-id="a299d-105">API 包含用來建置應用程式的 C 和 C++ 函數和巨集。</span><span class="sxs-lookup"><span data-stu-id="a299d-105">The API consists of C and C++ functions and macros used to build applications.</span></span>  
  
 <span data-ttu-id="a299d-106">隨著 CLR 整合之類的更新和更強大技術的出現，擴充預存程序的需求也大致被取代。</span><span class="sxs-lookup"><span data-stu-id="a299d-106">With the emergence of newer and more powerful technologies such as CLR integration, the need for extended stored procedures has largely been replaced.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a299d-107">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="a299d-107">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="a299d-108">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="a299d-108">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a299d-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="a299d-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="a299d-110">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="a299d-110">Data Types</span></span>](srv-pfield-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-111">srv_alloc</span><span class="sxs-lookup"><span data-stu-id="a299d-111">srv_alloc</span></span>](srv-alloc-extended-stored-procedure-api.md)||  
|[<span data-ttu-id="a299d-112">srv_convert</span><span class="sxs-lookup"><span data-stu-id="a299d-112">srv_convert</span></span>](srv-pfieldex-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-113">srv_describe</span><span class="sxs-lookup"><span data-stu-id="a299d-113">srv_describe</span></span>](srv-rpcdb-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-114">srv_getbindtoken</span><span class="sxs-lookup"><span data-stu-id="a299d-114">srv_getbindtoken</span></span>](srv-rpcname-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-115">srv_got_attention</span><span class="sxs-lookup"><span data-stu-id="a299d-115">srv_got_attention</span></span>](srv-rpcnumber-extended-stored-procedure-api.md)|  
||[<span data-ttu-id="a299d-116">srv_rpcoptions</span><span class="sxs-lookup"><span data-stu-id="a299d-116">srv_rpcoptions</span></span>](srv-rpcoptions-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-117">srv_message_handler</span><span class="sxs-lookup"><span data-stu-id="a299d-117">srv_message_handler</span></span>](srv-rpcowner-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-118">srv_paramdata</span><span class="sxs-lookup"><span data-stu-id="a299d-118">srv_paramdata</span></span>](srv-rpcparams-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-119">srv_paraminfo</span><span class="sxs-lookup"><span data-stu-id="a299d-119">srv_paraminfo</span></span>](srv-senddone-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-120">srv_paramlen</span><span class="sxs-lookup"><span data-stu-id="a299d-120">srv_paramlen</span></span>](srv-sendmsg-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-121">srv_parammaxlen</span><span class="sxs-lookup"><span data-stu-id="a299d-121">srv_parammaxlen</span></span>](srv-sendrow-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-122">srv_paramname</span><span class="sxs-lookup"><span data-stu-id="a299d-122">srv_paramname</span></span>](srv-setcoldata-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-123">srv_paramnumber</span><span class="sxs-lookup"><span data-stu-id="a299d-123">srv_paramnumber</span></span>](srv-setcollen-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-124">srv_paramset</span><span class="sxs-lookup"><span data-stu-id="a299d-124">srv_paramset</span></span>](srv-setutype-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-125">srv_paramsetoutput</span><span class="sxs-lookup"><span data-stu-id="a299d-125">srv_paramsetoutput</span></span>](srv-willconvert-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-126">srv_paramstatus</span><span class="sxs-lookup"><span data-stu-id="a299d-126">srv_paramstatus</span></span>](srv-wsendmsg-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="a299d-127">srv_paramtype</span><span class="sxs-lookup"><span data-stu-id="a299d-127">srv_paramtype</span></span>](srv-paramtype-extended-stored-procedure-api.md)||  
  
  
