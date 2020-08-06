---
title: MSSQLSERVER_12329 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 12329 (Database Engine error)
ms.assetid: 43f90287-36d5-46c2-ac91-a37202dcf6d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7576e32946ce0a453637273c449bbff20e5b6fac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596046"
---
# <a name="mssqlserver_12329"></a><span data-ttu-id="b4609-102">MSSQLSERVER_12329</span><span class="sxs-lookup"><span data-stu-id="b4609-102">MSSQLSERVER_12329</span></span>
    
## <a name="details"></a><span data-ttu-id="b4609-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b4609-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b4609-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b4609-104">Product Name</span></span>|<span data-ttu-id="b4609-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b4609-105">SQL Server</span></span>|  
|<span data-ttu-id="b4609-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b4609-106">Event ID</span></span>|<span data-ttu-id="b4609-107">12329</span><span class="sxs-lookup"><span data-stu-id="b4609-107">12329</span></span>|  
|<span data-ttu-id="b4609-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="b4609-108">Event Source</span></span>|<span data-ttu-id="b4609-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b4609-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b4609-110">元件</span><span class="sxs-lookup"><span data-stu-id="b4609-110">Component</span></span>|<span data-ttu-id="b4609-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b4609-111">SQLEngine</span></span>|  
|<span data-ttu-id="b4609-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b4609-112">Symbolic Name</span></span>|<span data-ttu-id="b4609-113">HK_UNSUPPORTED_NON_LATIN_CODEPAGE</span><span class="sxs-lookup"><span data-stu-id="b4609-113">HK_UNSUPPORTED_NON_LATIN_CODEPAGE</span></span>|  
|<span data-ttu-id="b4609-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b4609-114">Message Text</span></span>|<span data-ttu-id="b4609-115">*construct* 不支援資料類型 char(n) 和 varchar(n) 使用包含非 1252 之字碼頁的定序。</span><span class="sxs-lookup"><span data-stu-id="b4609-115">The data types char(n) and varchar(n) using a collation that has a code page other than 1252 are not supported with  *construct*.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b4609-116">說明</span><span class="sxs-lookup"><span data-stu-id="b4609-116">Explanation</span></span>  
 <span data-ttu-id="b4609-117">如有資料類型 char(n) 和 varchar(n) 使用包含非 1252 之字碼頁的定序，請勿使用這些資料類型。</span><span class="sxs-lookup"><span data-stu-id="b4609-117">Do not use the data types char(n) and varchar(n) using a collation that has a code page other than 1252.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b4609-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b4609-118">User Action</span></span>  
 <span data-ttu-id="b4609-119">其中一個會產生此錯誤的非預期的狀況為：</span><span class="sxs-lookup"><span data-stu-id="b4609-119">One unexpected situation that can generate this error is:</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = 'us_english')  
```  
  
 <span data-ttu-id="b4609-120">請改用：</span><span class="sxs-lookup"><span data-stu-id="b4609-120">Use this instead:</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
```  
  
  
