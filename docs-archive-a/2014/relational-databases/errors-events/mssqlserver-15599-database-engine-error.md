---
title: MSSQLSERVER_15599 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 15f1b3eb6d97837f1c1c4a9944535cade5b31300
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598946"
---
# <a name="mssqlserver_15599"></a><span data-ttu-id="505be-102">MSSQLSERVER_15599</span><span class="sxs-lookup"><span data-stu-id="505be-102">MSSQLSERVER_15599</span></span>
    
## <a name="details"></a><span data-ttu-id="505be-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="505be-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="505be-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="505be-104">Product Name</span></span>|<span data-ttu-id="505be-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="505be-105">SQL Server</span></span>|  
|<span data-ttu-id="505be-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="505be-106">Event ID</span></span>|<span data-ttu-id="505be-107">15599</span><span class="sxs-lookup"><span data-stu-id="505be-107">15599</span></span>|  
|<span data-ttu-id="505be-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="505be-108">Event Source</span></span>|<span data-ttu-id="505be-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="505be-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="505be-110">元件</span><span class="sxs-lookup"><span data-stu-id="505be-110">Component</span></span>|<span data-ttu-id="505be-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="505be-111">SQLEngine</span></span>|  
|<span data-ttu-id="505be-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="505be-112">Symbolic Name</span></span>|<span data-ttu-id="505be-113">SEC_LOCAL_TEMP_AUDIT_PERMISSIONS</span><span class="sxs-lookup"><span data-stu-id="505be-113">SEC_LOCAL_TEMP_AUDIT_PERMISSIONS</span></span>|  
|<span data-ttu-id="505be-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="505be-114">Message Text</span></span>|<span data-ttu-id="505be-115">本機暫存物件上不能設定稽核與權限。</span><span class="sxs-lookup"><span data-stu-id="505be-115">Auditing and permissions can't be set on local temporary objects.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="505be-116">說明</span><span class="sxs-lookup"><span data-stu-id="505be-116">Explanation</span></span>  
 <span data-ttu-id="505be-117">為本機或全域暫存物件設定稽核與權限不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="505be-117">Auditing and permissions do not have any effect when set for local or global temp objects.</span></span> <span data-ttu-id="505be-118">陳述式不會產生錯誤 (作業將回報成功)，但不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="505be-118">The statements do not result in an error (the operations will return success), but have no effect.</span></span>  
  
 <span data-ttu-id="505be-119">此行為尚未改變，但從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 起，使用者將會看到此訊息文字警示。</span><span class="sxs-lookup"><span data-stu-id="505be-119">This behavior has not changed, however beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], this informational message alerts the user.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="505be-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="505be-120">User Action</span></span>  
 <span data-ttu-id="505be-121">無須採取任何動作，但可考慮移除所有嘗試為本機或全域暫存物件設定稽核或權限的陳述式。</span><span class="sxs-lookup"><span data-stu-id="505be-121">No action is necessary, but consider removing statements that attempt to set auditing or permissions on local or global temp objects.</span></span>  
  
  
