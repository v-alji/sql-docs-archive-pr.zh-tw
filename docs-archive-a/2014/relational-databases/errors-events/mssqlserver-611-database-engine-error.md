---
title: MSSQLSERVER_611 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f0caa1c218e8b80059c0c97aac652da7db870af3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606354"
---
# <a name="mssqlserver_611"></a><span data-ttu-id="0b5e0-102">MSSQLSERVER_611</span><span class="sxs-lookup"><span data-stu-id="0b5e0-102">MSSQLSERVER_611</span></span>
    
## <a name="details"></a><span data-ttu-id="0b5e0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0b5e0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0b5e0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0b5e0-104">Product Name</span></span>|<span data-ttu-id="0b5e0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0b5e0-105">SQL Server</span></span>|  
|<span data-ttu-id="0b5e0-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0b5e0-106">Event ID</span></span>|<span data-ttu-id="0b5e0-107">611</span><span class="sxs-lookup"><span data-stu-id="0b5e0-107">611</span></span>|  
|<span data-ttu-id="0b5e0-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="0b5e0-108">Event Source</span></span>|<span data-ttu-id="0b5e0-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0b5e0-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0b5e0-110">元件</span><span class="sxs-lookup"><span data-stu-id="0b5e0-110">Component</span></span>|<span data-ttu-id="0b5e0-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0b5e0-111">SQLEngine</span></span>|  
|<span data-ttu-id="0b5e0-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0b5e0-112">Symbolic Name</span></span>|<span data-ttu-id="0b5e0-113">VAR_SIZE_TOO_BIG</span><span class="sxs-lookup"><span data-stu-id="0b5e0-113">VAR_SIZE_TOO_BIG</span></span>|  
|<span data-ttu-id="0b5e0-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0b5e0-114">Message Text</span></span>|<span data-ttu-id="0b5e0-115">無法插入或更新資料列，因為變數資料行的總大小 (包括負擔) 要比限制多出 %d 個位元組。</span><span class="sxs-lookup"><span data-stu-id="0b5e0-115">Cannot insert or update a row because total variable column size, including overhead, is %d bytes more than the limit.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0b5e0-116">說明</span><span class="sxs-lookup"><span data-stu-id="0b5e0-116">Explanation</span></span>  
 <span data-ttu-id="0b5e0-117">變數資料行大小上限多於結構描述允許的值。</span><span class="sxs-lookup"><span data-stu-id="0b5e0-117">The maximum variable column size is more than that allowed by the schema.</span></span> <span data-ttu-id="0b5e0-118">當變數資料行大小超出啟用 Vardecimal 資料格式時固定案例中的限制，或是變數資料行大小超出 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 壓縮資料記錄所允許的限制時，就會傳回錯誤 611。</span><span class="sxs-lookup"><span data-stu-id="0b5e0-118">Error 611 is returned when the variable column is over the limit in the fixed case when vardecimal storage format is enabled, or when the variable column size is over the limit allowed in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] for a compressed data record.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0b5e0-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0b5e0-119">User Action</span></span>  
 <span data-ttu-id="0b5e0-120">縮減此記錄的大小。</span><span class="sxs-lookup"><span data-stu-id="0b5e0-120">Reduce the size of the record.</span></span>  
  
  
