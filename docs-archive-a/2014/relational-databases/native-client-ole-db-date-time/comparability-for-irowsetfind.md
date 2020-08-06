---
title: IRowsetFind 的相容性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability [ODBC]
ms.assetid: 7d148b56-9bbe-4e55-b31f-43f115705402
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ad359ca4957b434c3798d1a441eb0fd57644a59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592675"
---
# <a name="comparability-for-irowsetfind"></a><span data-ttu-id="992d0-102">IRowsetFind 的相容性</span><span class="sxs-lookup"><span data-stu-id="992d0-102">Comparability for IRowsetFind</span></span>
  <span data-ttu-id="992d0-103">IRowsetFind 僅針對日期/時間類型，支援下列比較：</span><span class="sxs-lookup"><span data-stu-id="992d0-103">For date/time types only, IRowsetFind supports the following comparisons:</span></span>  
  
-   <span data-ttu-id="992d0-104">LT</span><span class="sxs-lookup"><span data-stu-id="992d0-104">LT</span></span>  
  
-   <span data-ttu-id="992d0-105">LE</span><span class="sxs-lookup"><span data-stu-id="992d0-105">LE</span></span>  
  
-   <span data-ttu-id="992d0-106">EQ</span><span class="sxs-lookup"><span data-stu-id="992d0-106">EQ</span></span>  
  
-   <span data-ttu-id="992d0-107">GE</span><span class="sxs-lookup"><span data-stu-id="992d0-107">GE</span></span>  
  
-   <span data-ttu-id="992d0-108">GT</span><span class="sxs-lookup"><span data-stu-id="992d0-108">GT</span></span>  
  
-   <span data-ttu-id="992d0-109">NE</span><span class="sxs-lookup"><span data-stu-id="992d0-109">NE</span></span>  
  
-   <span data-ttu-id="992d0-110">IGNORE</span><span class="sxs-lookup"><span data-stu-id="992d0-110">IGNORE</span></span>  
  
 <span data-ttu-id="992d0-111">如果嘗試任何其他比較，就會傳回 DB_E_BADCOMPAREOP。</span><span class="sxs-lookup"><span data-stu-id="992d0-111">If any other comparison is attempted, DB_E_BADCOMPAREOP is returned.</span></span> <span data-ttu-id="992d0-112">這與 OLE DB 規格一致。</span><span class="sxs-lookup"><span data-stu-id="992d0-112">This is consistent with the OLE DB specification.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="992d0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="992d0-113">See Also</span></span>  
 [<span data-ttu-id="992d0-114">日期和時間改善 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="992d0-114">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
