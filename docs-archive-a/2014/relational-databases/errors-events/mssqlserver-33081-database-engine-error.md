---
title: MSSQLSERVER_33081 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33081 (Database Engine error)
ms.assetid: 839705e7-fa37-4c0d-9f3f-95a9eab98bcf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0752220cc20641d9b51a3a66fecc86f9efd63433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595061"
---
# <a name="mssqlserver_33081"></a><span data-ttu-id="890c5-102">MSSQLSERVER_33081</span><span class="sxs-lookup"><span data-stu-id="890c5-102">MSSQLSERVER_33081</span></span>
    
## <a name="details"></a><span data-ttu-id="890c5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="890c5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="890c5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="890c5-104">Product Name</span></span>|<span data-ttu-id="890c5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="890c5-105">SQL Server</span></span>|  
|<span data-ttu-id="890c5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="890c5-106">Event ID</span></span>|<span data-ttu-id="890c5-107">33081</span><span class="sxs-lookup"><span data-stu-id="890c5-107">33081</span></span>|  
|<span data-ttu-id="890c5-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="890c5-108">Event Source</span></span>|<span data-ttu-id="890c5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="890c5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="890c5-110">元件</span><span class="sxs-lookup"><span data-stu-id="890c5-110">Component</span></span>|<span data-ttu-id="890c5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="890c5-111">SQLEngine</span></span>|  
|<span data-ttu-id="890c5-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="890c5-112">Symbolic Name</span></span>|<span data-ttu-id="890c5-113">SEC_DLL_TRUST_VERIFICATION_FAILED</span><span class="sxs-lookup"><span data-stu-id="890c5-113">SEC_DLL_TRUST_VERIFICATION_FAILED</span></span>|  
|<span data-ttu-id="890c5-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="890c5-114">Message Text</span></span>|<span data-ttu-id="890c5-115">無法載入密碼編譯提供者 '%.\*ls'，因為 Authenticode 簽章或檔案路徑無效。</span><span class="sxs-lookup"><span data-stu-id="890c5-115">Failed to load cryptographic provider '%.\*ls' due to an invalid Authenticode signature or invalid file path.</span></span>  <span data-ttu-id="890c5-116">請檢查先前其他失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="890c5-116">Check previous messages for other failures.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="890c5-117">說明</span><span class="sxs-lookup"><span data-stu-id="890c5-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="890c5-118">無法載入錯誤訊息中所列的密碼編譯提供者。</span><span class="sxs-lookup"><span data-stu-id="890c5-118">was unable to load the cryptographic provider listed in the error message.</span></span> <span data-ttu-id="890c5-119">有幾項 Win API 失敗可能導致此錯誤。</span><span class="sxs-lookup"><span data-stu-id="890c5-119">There are several Win API failures which might cause this error.</span></span> <span data-ttu-id="890c5-120">信號緩衝區中包含 API 所傳回已失敗的 API 名稱及 Windows 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="890c5-120">The ring buffer contains the name of the failed API and the Windows error code returned by the API.</span></span> <span data-ttu-id="890c5-121">如需詳細資訊，請使用下列查詢針對 sys.dm_os_ring_buffers 檢視進行查詢。</span><span class="sxs-lookup"><span data-stu-id="890c5-121">To get more information, query the sys.dm_os_ring_buffers view using the following query.</span></span>  
  
```  
SELECT * FROM sys.dm_os_ring_buffers   
WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
```  
  
## <a name="user-action"></a><span data-ttu-id="890c5-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="890c5-122">User Action</span></span>  
 <span data-ttu-id="890c5-123">若要調查問題，請搜尋 MSDN (https://msdn.microsoft.com/) 中的 Windows 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="890c5-123">To investigate the problem, search for the Windows error code in MSDN (https://msdn.microsoft.com/).</span></span> <span data-ttu-id="890c5-124">解決此錯誤或連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS 以了解詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="890c5-124">Resolve the error, or contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS for more information.</span></span> <span data-ttu-id="890c5-125">如果您需要連絡 CSS，請收集下列資訊以供支援人員參考。</span><span class="sxs-lookup"><span data-stu-id="890c5-125">If you need to contact CSS, collect the following information for our support staff.</span></span>  
  
-   <span data-ttu-id="890c5-126">顯示無法載入密碼編譯提供者錯誤的錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="890c5-126">The error log showing the failed to load cryptographic provider error.</span></span>  
  
-   <span data-ttu-id="890c5-127">下列陳述式的輸出：</span><span class="sxs-lookup"><span data-stu-id="890c5-127">The output from the following statement:</span></span>  
  
    ```  
    SELECT * FROM sys.dm_os_ring_buffers   
    WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="890c5-128">請立即收集信號緩衝區資訊，以免於重新開啟時失去這些資訊。</span><span class="sxs-lookup"><span data-stu-id="890c5-128">Try to collect the ring buffer information promptly as ring buffer information can be lost during a restart.</span></span>  
  
  
