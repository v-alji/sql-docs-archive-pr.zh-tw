---
title: 大型 CLR 使用者定義型別 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
ms.assetid: b65eb61d-ccf6-49c0-98e7-9a4ef4b2f790
author: rothja
ms.author: jroth
ms.openlocfilehash: 27f0c13caea8c4aca63d78238509c6d05f1bf7bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698080"
---
# <a name="large-clr-user-defined-types"></a><span data-ttu-id="7bd6b-102">大型 CLR 使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="7bd6b-102">Large CLR User-Defined Types</span></span>
  <span data-ttu-id="7bd6b-103">在 SQL Server 2005，Common Language Runtime (CLR) 中的使用者定義型別 (UDT) 在大小上限制為 8,000 個位元組。</span><span class="sxs-lookup"><span data-stu-id="7bd6b-103">In SQL Server 2005, user-defined types (UDTs) in the common language runtime (CLR) were restricted to 8,000 bytes in size.</span></span> <span data-ttu-id="7bd6b-104">在 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 和更新版本中已提高此限制。</span><span class="sxs-lookup"><span data-stu-id="7bd6b-104">This restriction has been lifted in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] and later versions.</span></span> <span data-ttu-id="7bd6b-105">CLR UDT 現在會以大型物件 (LOB) 類型類似的方式處理。</span><span class="sxs-lookup"><span data-stu-id="7bd6b-105">CLR UDTs are now treated in a similar way to large object (LOB) types.</span></span> <span data-ttu-id="7bd6b-106">也就是說，小於或等於 8,000 個位元組的 UDT 行為與 SQL Server 2005 相同，但是支援較大的 UDT，而且會將其大小報告為「無限制」。</span><span class="sxs-lookup"><span data-stu-id="7bd6b-106">That is, UDTs less than or equal to 8,000 bytes behave the same way as in SQL Server 2005, but larger UDTs are supported and report their size as "unlimited".</span></span>  
  
 <span data-ttu-id="7bd6b-107">如需詳細資訊，請參閱[大型 Clr 使用者自訂類型 &#40;OLE DB&#41;](../ole-db/large-clr-user-defined-types-ole-db.md)和[大型 Clr 使用者定義類型 &#40;ODBC&#41;](../odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="7bd6b-107">For more information, see [Large CLR User-Defined Types &#40;OLE DB&#41;](../ole-db/large-clr-user-defined-types-ole-db.md) and [Large CLR User-Defined Types &#40;ODBC&#41;](../odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="use-cases"></a><span data-ttu-id="7bd6b-108">使用案例</span><span class="sxs-lookup"><span data-stu-id="7bd6b-108">Use Cases</span></span>  
 <span data-ttu-id="7bd6b-109">對於 ODBC，大型 UDT 的支援包括能夠以片段當做資料執行中 (data-at-execution) 參數傳送 UDT 值。</span><span class="sxs-lookup"><span data-stu-id="7bd6b-109">For ODBC, support for large UDTs includes the ability to send UDT values in pieces as data-at-execution parameters.</span></span> <span data-ttu-id="7bd6b-110">這項作業是使用 SQLPutData 來完成。</span><span class="sxs-lookup"><span data-stu-id="7bd6b-110">This is done by using SQLPutData.</span></span>  
  
 <span data-ttu-id="7bd6b-111">對於 OLE DB，大型 UDT 的支援包括能夠使用 ISequentialStream 繫結，在伺服器來回串流 UDT 值。</span><span class="sxs-lookup"><span data-stu-id="7bd6b-111">For OLE DB, support for large UDTs includes the ability to stream UDT values to and from the server by using ISequentialStream binding.</span></span>  
  
 <span data-ttu-id="7bd6b-112">小於或等於 8,000 個位元組的 UDT 行為如同在 SQL Server 2005 中的行為。</span><span class="sxs-lookup"><span data-stu-id="7bd6b-112">UDTs less than or equal to 8,000 bytes will behave as they did in SQL Server 2005.</span></span> <span data-ttu-id="7bd6b-113">對於 OLE DB，您仍然可以使用 ISequentialStream 繫結來串流處理小型 UDT。</span><span class="sxs-lookup"><span data-stu-id="7bd6b-113">For OLE DB, you can still stream small UDTs by using ISequentialStream binding.</span></span>  
  
 <span data-ttu-id="7bd6b-114">原生程式碼有時候必須了解 CLR UDT 的內容，但不必具現化 Managed 物件。</span><span class="sxs-lookup"><span data-stu-id="7bd6b-114">Sometimes native code will have to understand the contents of CLR UDTs, but will not have to instantiate managed objects.</span></span> <span data-ttu-id="7bd6b-115">如果是這種情況，您可以使用自訂序列化，將伺服器上的 UDT 值轉換為用戶端熟知的格式。</span><span class="sxs-lookup"><span data-stu-id="7bd6b-115">If this is the case, you can use custom serialization to convert UDT values on the server into a well known format for clients.</span></span>  
  
 <span data-ttu-id="7bd6b-116">對於擁有現有資料存取程式碼的應用程式，您可以透過原生 API 擷取 UDT，並使用混合模式應用程式中的 C++ CLI Interop 進行具現化，藉以利用用戶端上的 CLR UDT 行為。</span><span class="sxs-lookup"><span data-stu-id="7bd6b-116">For applications that have existing data access code, you can exploit CLR UDT behavior on the client by retrieving UDTs through native APIs and instantiating them by using C++ CLI interop in mixed mode applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd6b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bd6b-117">See Also</span></span>  
 [<span data-ttu-id="7bd6b-118">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="7bd6b-118">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
