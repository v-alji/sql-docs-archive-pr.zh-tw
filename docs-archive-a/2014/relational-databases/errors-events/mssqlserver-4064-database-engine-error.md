---
title: MSSQLSERVER_4064 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 201098aadeb6bd091f0312532138f692ae8079b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599514"
---
# <a name="mssqlserver_4064"></a><span data-ttu-id="aff93-102">MSSQLSERVER_4064</span><span class="sxs-lookup"><span data-stu-id="aff93-102">MSSQLSERVER_4064</span></span>
    
## <a name="details"></a><span data-ttu-id="aff93-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aff93-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aff93-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="aff93-104">Product Name</span></span>|<span data-ttu-id="aff93-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="aff93-105">SQL Server</span></span>|  
|<span data-ttu-id="aff93-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="aff93-106">Event ID</span></span>|<span data-ttu-id="aff93-107">4064</span><span class="sxs-lookup"><span data-stu-id="aff93-107">4064</span></span>|  
|<span data-ttu-id="aff93-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="aff93-108">Event Source</span></span>|<span data-ttu-id="aff93-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="aff93-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="aff93-110">元件</span><span class="sxs-lookup"><span data-stu-id="aff93-110">Component</span></span>|<span data-ttu-id="aff93-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="aff93-111">SQLEngine</span></span>|  
|<span data-ttu-id="aff93-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="aff93-112">Symbolic Name</span></span>|<span data-ttu-id="aff93-113">DB_UFAIL_FATAL</span><span class="sxs-lookup"><span data-stu-id="aff93-113">DB_UFAIL_FATAL</span></span>|  
|<span data-ttu-id="aff93-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="aff93-114">Message Text</span></span>|<span data-ttu-id="aff93-115">無法開啟使用者預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="aff93-115">Cannot open user default database.</span></span> <span data-ttu-id="aff93-116">登入失敗。</span><span class="sxs-lookup"><span data-stu-id="aff93-116">Login failed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aff93-117">說明</span><span class="sxs-lookup"><span data-stu-id="aff93-117">Explanation</span></span>  
 <span data-ttu-id="aff93-118">由於預設資料庫發生問題，SQL Server 登入無法連接。</span><span class="sxs-lookup"><span data-stu-id="aff93-118">The SQL Server login was unable to connect because of a problem with its default database.</span></span> <span data-ttu-id="aff93-119">可能是資料庫本身無效，或是登入在資料庫上沒有 CONNECT 權限。</span><span class="sxs-lookup"><span data-stu-id="aff93-119">Either the database itself is invalid or the login lacks CONNECT permission on the database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aff93-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="aff93-120">User Action</span></span>  
 <span data-ttu-id="aff93-121">使用 ALTER LOGIN 變更登入的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="aff93-121">Use ALTER LOGIN to change the login's default database.</span></span> <span data-ttu-id="aff93-122">授與 CONNECT 權限給登入。</span><span class="sxs-lookup"><span data-stu-id="aff93-122">Grant CONNECT permission to the login.</span></span>  
  
  
