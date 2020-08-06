---
title: MSSQLSERVER_33027 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f6bb461b42b66368224fffd2c14f9b4da61abf5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595063"
---
# <a name="mssqlserver_33027"></a><span data-ttu-id="bf764-102">MSSQLSERVER_33027</span><span class="sxs-lookup"><span data-stu-id="bf764-102">MSSQLSERVER_33027</span></span>
    
## <a name="details"></a><span data-ttu-id="bf764-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bf764-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bf764-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bf764-104">Product Name</span></span>|<span data-ttu-id="bf764-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="bf764-105">SQL Server</span></span>|  
|<span data-ttu-id="bf764-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bf764-106">Event ID</span></span>|<span data-ttu-id="bf764-107">33027</span><span class="sxs-lookup"><span data-stu-id="bf764-107">33027</span></span>|  
|<span data-ttu-id="bf764-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="bf764-108">Event Source</span></span>|<span data-ttu-id="bf764-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bf764-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bf764-110">元件</span><span class="sxs-lookup"><span data-stu-id="bf764-110">Component</span></span>|<span data-ttu-id="bf764-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bf764-111">SQLEngine</span></span>|  
|<span data-ttu-id="bf764-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bf764-112">Symbolic Name</span></span>|<span data-ttu-id="bf764-113">SEC_CRYPTOPROV_CANTLOADDLL</span><span class="sxs-lookup"><span data-stu-id="bf764-113">SEC_CRYPTOPROV_CANTLOADDLL</span></span>|  
|<span data-ttu-id="bf764-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bf764-114">Message Text</span></span>|<span data-ttu-id="bf764-115">無法載入密碼編譯提供者 '%.\*ls'，因為 Authenticode 簽章或檔案路徑無效。</span><span class="sxs-lookup"><span data-stu-id="bf764-115">Failed to load cryptographic provider '%.\*ls' due to an invalid Authenticode signature or invalid file path.</span></span> <span data-ttu-id="bf764-116">請檢查先前其他失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="bf764-116">Check previous messages for other failures.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bf764-117">說明</span><span class="sxs-lookup"><span data-stu-id="bf764-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bf764-118">無法使用錯誤訊息中所列的密碼編譯提供者，因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法載入 DLL。</span><span class="sxs-lookup"><span data-stu-id="bf764-118">was unable to use the cryptographic provider listed in the error message, because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] could not load the DLL.</span></span> <span data-ttu-id="bf764-119">此名稱無效，或者 Authenticode 簽章無效。</span><span class="sxs-lookup"><span data-stu-id="bf764-119">Either the name is invalid or the Authenticode signature is invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bf764-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bf764-120">User Action</span></span>  
 <span data-ttu-id="bf764-121">檢查檔案是否存在，而且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是否擁有存取該位置的權限。</span><span class="sxs-lookup"><span data-stu-id="bf764-121">Check that the file is present and that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has permission to access that location.</span></span> <span data-ttu-id="bf764-122">檢查其他相關訊息的錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="bf764-122">Check the error log for additional related messages.</span></span> <span data-ttu-id="bf764-123">否則，如需詳細資訊，請連絡密碼編譯提供者。</span><span class="sxs-lookup"><span data-stu-id="bf764-123">Otherwise, contact the cryptographic provider for more information.</span></span>  
  
  
