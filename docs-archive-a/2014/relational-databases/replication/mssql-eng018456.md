---
title: MSSQL_ENG018456 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018456 error
ms.assetid: 3daa8144-d81f-445a-b6c3-4bb3e9fd1526
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b05ca549781215e0c4f247110fee87f6def56f04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702786"
---
# <a name="mssql_eng018456"></a><span data-ttu-id="379e1-102">MSSQL_ENG018456</span><span class="sxs-lookup"><span data-stu-id="379e1-102">MSSQL_ENG018456</span></span>
    
## <a name="message-details"></a><span data-ttu-id="379e1-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="379e1-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="379e1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="379e1-104">Product Name</span></span>|<span data-ttu-id="379e1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="379e1-105">SQL Server</span></span>|  
|<span data-ttu-id="379e1-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="379e1-106">Event ID</span></span>|<span data-ttu-id="379e1-107">18456</span><span class="sxs-lookup"><span data-stu-id="379e1-107">18456</span></span>|  
|<span data-ttu-id="379e1-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="379e1-108">Event Source</span></span>|<span data-ttu-id="379e1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="379e1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="379e1-110">元件</span><span class="sxs-lookup"><span data-stu-id="379e1-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="379e1-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="379e1-111">Symbolic Name</span></span>||  
|<span data-ttu-id="379e1-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="379e1-112">Message Text</span></span>|<span data-ttu-id="379e1-113">使用者 '%.\*ls'.%.\*ls 登入失敗</span><span class="sxs-lookup"><span data-stu-id="379e1-113">Login failed for user '%.\*ls'.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="379e1-114">說明</span><span class="sxs-lookup"><span data-stu-id="379e1-114">Explanation</span></span>  
 <span data-ttu-id="379e1-115">每當登入嘗試失敗時，都會產生 MSSQL_ENG018456 錯誤。</span><span class="sxs-lookup"><span data-stu-id="379e1-115">Error MSSQL_ENG018456 is raised whenever a login attempt fails.</span></span> <span data-ttu-id="379e1-116">如果錯誤訊息包含帳戶 **distributor_admin** (使用者 'distributor_admin' 登入失敗)，則為複寫所用帳戶的問題。</span><span class="sxs-lookup"><span data-stu-id="379e1-116">If the error message includes the account **distributor_admin** (Login failed for user 'distributor_admin'.), the issue is with an account used by replication.</span></span> <span data-ttu-id="379e1-117">複寫建立遠端伺服器， **repl_distributor**，可允許在散發者和發行者之間通訊。</span><span class="sxs-lookup"><span data-stu-id="379e1-117">Replication creates a remote server, **repl_distributor**, which allows communication between the Distributor and Publisher.</span></span> <span data-ttu-id="379e1-118">登入 **distributor_admin** 與此遠端伺服器相關聯，且必須具備有效的密碼。</span><span class="sxs-lookup"><span data-stu-id="379e1-118">The login **distributor_admin** is associated with this remote server and must have a valid password.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="379e1-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="379e1-119">User Action</span></span>  
 <span data-ttu-id="379e1-120">確定您已為此帳戶指定密碼。</span><span class="sxs-lookup"><span data-stu-id="379e1-120">Ensure that you have specified a password for this account.</span></span> <span data-ttu-id="379e1-121">如需詳細資訊，請參閱[保護散發者](security/secure-the-distributor.md)。</span><span class="sxs-lookup"><span data-stu-id="379e1-121">For more information, see [Secure the Distributor](security/secure-the-distributor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="379e1-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="379e1-122">See Also</span></span>  
 [<span data-ttu-id="379e1-123">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="379e1-123">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
