---
title: MSSQLSERVER_26014 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 26014 (Database Engine error)
ms.assetid: e2b0dfc7-0681-4e5d-8875-1d5f63534086
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8114183b212767d01013eee9387d8b2efa2e0d7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596039"
---
# <a name="mssqlserver_26014"></a><span data-ttu-id="1ec53-102">MSSQLSERVER_26014</span><span class="sxs-lookup"><span data-stu-id="1ec53-102">MSSQLSERVER_26014</span></span>
    
## <a name="details"></a><span data-ttu-id="1ec53-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1ec53-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1ec53-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1ec53-104">Product Name</span></span>|<span data-ttu-id="1ec53-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ec53-105">SQL Server</span></span>|  
|<span data-ttu-id="1ec53-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1ec53-106">Event ID</span></span>|<span data-ttu-id="1ec53-107">26014</span><span class="sxs-lookup"><span data-stu-id="1ec53-107">26014</span></span>|  
|<span data-ttu-id="1ec53-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="1ec53-108">Event Source</span></span>|<span data-ttu-id="1ec53-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1ec53-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1ec53-110">元件</span><span class="sxs-lookup"><span data-stu-id="1ec53-110">Component</span></span>|<span data-ttu-id="1ec53-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1ec53-111">SQLEngine</span></span>|  
|<span data-ttu-id="1ec53-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1ec53-112">Symbolic Name</span></span>|<span data-ttu-id="1ec53-113">SNI_SSL_USER_CERT_FAILURE</span><span class="sxs-lookup"><span data-stu-id="1ec53-113">SNI_SSL_USER_CERT_FAILURE</span></span>|  
|<span data-ttu-id="1ec53-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1ec53-114">Message Text</span></span>|<span data-ttu-id="1ec53-115">無法載入使用者指定的憑證 [Cert Hash(sha1) "%hs"]。</span><span class="sxs-lookup"><span data-stu-id="1ec53-115">Unable to load user-specified certificate [Cert Hash(sha1) "%hs"].</span></span> <span data-ttu-id="1ec53-116">伺服器將不會接受連接。</span><span class="sxs-lookup"><span data-stu-id="1ec53-116">The server will not accept a connection.</span></span> <span data-ttu-id="1ec53-117">您應該確認已正確安裝憑證。</span><span class="sxs-lookup"><span data-stu-id="1ec53-117">You should verify that the certificate is correctly installed.</span></span> <span data-ttu-id="1ec53-118">請參閱線上叢書中的＜設定憑證給 SSL 使用＞(Configuring Certificate for Use by SSL)。</span><span class="sxs-lookup"><span data-stu-id="1ec53-118">See "Configuring Certificate for Use by SSL" in Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1ec53-119">說明</span><span class="sxs-lookup"><span data-stu-id="1ec53-119">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1ec53-120">已嘗試載入在訊息中指定的憑證，但是作業失敗。</span><span class="sxs-lookup"><span data-stu-id="1ec53-120">attempted to load the certificate named in the message but the operation failed.</span></span> <span data-ttu-id="1ec53-121">您必須先解決此問題，然後 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 才能使用這個憑證。</span><span class="sxs-lookup"><span data-stu-id="1ec53-121">This problem must be resolved before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can use this certificate.</span></span>  
  
 <span data-ttu-id="1ec53-122">造成此錯誤的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="1ec53-122">Possible causes of the error include:</span></span>  
  
-   <span data-ttu-id="1ec53-123">憑證可能已經移動或刪除。</span><span class="sxs-lookup"><span data-stu-id="1ec53-123">The certificate could have been moved or deleted.</span></span>  
  
-   <span data-ttu-id="1ec53-124">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所使用的登入已經變更，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能就沒有存取此憑證的權限。</span><span class="sxs-lookup"><span data-stu-id="1ec53-124">If the login used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has changed, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may not have permission to access the certificate.</span></span>  
  
-   <span data-ttu-id="1ec53-125">憑證可能已經過期。</span><span class="sxs-lookup"><span data-stu-id="1ec53-125">The certificate may have expired.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1ec53-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1ec53-126">User Action</span></span>  
 <span data-ttu-id="1ec53-127">請確定在訊息中指定的憑證存在系統上、可以存取，而且可供使用。</span><span class="sxs-lookup"><span data-stu-id="1ec53-127">Make sure the certificate named in the message exists on the system, is accessible, and it is valid for use.</span></span>  
  
  
