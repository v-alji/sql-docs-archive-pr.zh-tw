---
title: MSSQLSERVER_15661 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 966e23e8d970c36eba81253228cc18ed4af3ff77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584550"
---
# <a name="mssqlserver_15661"></a><span data-ttu-id="be09b-102">MSSQLSERVER_15661</span><span class="sxs-lookup"><span data-stu-id="be09b-102">MSSQLSERVER_15661</span></span>
    
## <a name="details"></a><span data-ttu-id="be09b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="be09b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="be09b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="be09b-104">Product Name</span></span>|<span data-ttu-id="be09b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="be09b-105">SQL Server</span></span>|  
|<span data-ttu-id="be09b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="be09b-106">Event ID</span></span>|<span data-ttu-id="be09b-107">15661</span><span class="sxs-lookup"><span data-stu-id="be09b-107">15661</span></span>|  
|<span data-ttu-id="be09b-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="be09b-108">Event Source</span></span>|<span data-ttu-id="be09b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="be09b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="be09b-110">元件</span><span class="sxs-lookup"><span data-stu-id="be09b-110">Component</span></span>|<span data-ttu-id="be09b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="be09b-111">SQLEngine</span></span>|  
|<span data-ttu-id="be09b-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="be09b-112">Symbolic Name</span></span>|<span data-ttu-id="be09b-113">SQLErrorNum15661</span><span class="sxs-lookup"><span data-stu-id="be09b-113">SQLErrorNum15661</span></span>|  
|<span data-ttu-id="be09b-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="be09b-114">Message Text</span></span>|<span data-ttu-id="be09b-115">sp_estimate_data_compression_savings 預存程序無法用於暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="be09b-115">The sp_estimate_data_compression_savings stored procedure cannot be used for temporary tables.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="be09b-116">說明</span><span class="sxs-lookup"><span data-stu-id="be09b-116">Explanation</span></span>  
 <span data-ttu-id="be09b-117">暫存資料表當做 sp_estimate_data_compression_savings 預存程序的引數使用。</span><span class="sxs-lookup"><span data-stu-id="be09b-117">A temporary table was used as an argument for the sp_estimate_data_compression_savings stored procedure.</span></span> <span data-ttu-id="be09b-118">雖然暫存資料表的壓縮有受到支援，但是您無法使用 sp_estimate_data_compression_savings 來預估所節省的壓縮。</span><span class="sxs-lookup"><span data-stu-id="be09b-118">Although the compression of temporary tables is supported, you cannot use sp_estimate_data_compression_savings to estimate the compression savings.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="be09b-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="be09b-119">User Action</span></span>  
 <span data-ttu-id="be09b-120">移除當做 sp_estimate_data_compression_savings 之引數的暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="be09b-120">Remove the temporary table as an argument for sp_estimate_data_compression_savings.</span></span>  
  
  
