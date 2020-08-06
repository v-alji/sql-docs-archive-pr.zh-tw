---
title: MSSQLSERVER_33129 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33129 (Database Engine error)
ms.assetid: 83b5f368-f1a1-4a40-9bb6-c77e2dec690f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da7735889dce8bfc33e624115e8245f8a02f46b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595058"
---
# <a name="mssqlserver_33129"></a><span data-ttu-id="bbdce-102">MSSQLSERVER_33129</span><span class="sxs-lookup"><span data-stu-id="bbdce-102">MSSQLSERVER_33129</span></span>
    
## <a name="details"></a><span data-ttu-id="bbdce-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bbdce-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bbdce-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bbdce-104">Product Name</span></span>|<span data-ttu-id="bbdce-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="bbdce-105">SQL Server</span></span>|  
|<span data-ttu-id="bbdce-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bbdce-106">Event ID</span></span>|<span data-ttu-id="bbdce-107">33129</span><span class="sxs-lookup"><span data-stu-id="bbdce-107">33129</span></span>|  
|<span data-ttu-id="bbdce-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="bbdce-108">Event Source</span></span>|<span data-ttu-id="bbdce-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bbdce-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bbdce-110">元件</span><span class="sxs-lookup"><span data-stu-id="bbdce-110">Component</span></span>|<span data-ttu-id="bbdce-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bbdce-111">SQLEngine</span></span>|  
|<span data-ttu-id="bbdce-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bbdce-112">Symbolic Name</span></span>|<span data-ttu-id="bbdce-113">SEC_CANNOT_DISABLE_WIN_GROUP</span><span class="sxs-lookup"><span data-stu-id="bbdce-113">SEC_CANNOT_DISABLE_WIN_GROUP</span></span>|  
|<span data-ttu-id="bbdce-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bbdce-114">Message Text</span></span>|<span data-ttu-id="bbdce-115">無法使用含 DISABLE 引數的 ALTER_LOGIN 來拒絕存取 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="bbdce-115">Cannot use ALTER_LOGIN with the DISABLE argument to deny access to a Windows group.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bbdce-116">說明</span><span class="sxs-lookup"><span data-stu-id="bbdce-116">Explanation</span></span>  
 <span data-ttu-id="bbdce-117">嘗試停用 Windows 群組的登入時，會出現此訊息。</span><span class="sxs-lookup"><span data-stu-id="bbdce-117">This message occurs when attempting to disable the login of a Windows Group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bbdce-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bbdce-118">User Action</span></span>  
 <span data-ttu-id="bbdce-119">您無法停用 Windows 群組的登入。</span><span class="sxs-lookup"><span data-stu-id="bbdce-119">The login of a Windows Group cannot be disabled.</span></span> <span data-ttu-id="bbdce-120">若要暫時移除授予 Windows 群組的存取權限，則使用 REVOKE 撤銷對 Windows 群組之登入的 CONNECT 權限。</span><span class="sxs-lookup"><span data-stu-id="bbdce-120">To temporarily remove access permission granted to a Windows Group, REVOKE the CONNECT permission of the login for the Windows Group.</span></span> <span data-ttu-id="bbdce-121">Windows 使用者仍然可能透過其個別登入或透過另一個 Windows 群組具有存取權。</span><span class="sxs-lookup"><span data-stu-id="bbdce-121">Windows users might still have access through their individual login or through another Windows Group.</span></span> <span data-ttu-id="bbdce-122">以下的範例會撤銷 WESTCOAST 網域之 Accounting 群組的連接權限。</span><span class="sxs-lookup"><span data-stu-id="bbdce-122">The following example revokes the connect permission to the Accounting Group of the WESTCOAST domain.</span></span>  
  
```sql  
REVOKE CONNECT TO [WESTCOAST\Accounting];  
```  
  
  
