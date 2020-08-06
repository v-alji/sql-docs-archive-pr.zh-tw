---
title: FILESTREAM 支援 (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
author: rothja
ms.author: jroth
ms.openlocfilehash: cde3c2cd1b72773cfcf17eacedeb3276dd2f63da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597793"
---
# <a name="filestream-support-ole-db"></a><span data-ttu-id="fc5e0-102">FILESTREAM 支援 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="fc5e0-102">FILESTREAM Support (OLE DB)</span></span>
  <span data-ttu-id="fc5e0-103">從 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 開始，OLE DB 支援增強型 FILESTREAM 功能。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-103">Beginning with [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, OLE DB supports the enhanced FILESTREAM feature.</span></span> <span data-ttu-id="fc5e0-104">如需這項功能的詳細資訊，請參閱[FILESTREAM 支援](../features/filestream-support.md)。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-104">For more information about this feature, see [FILESTREAM Support](../features/filestream-support.md).</span></span> <span data-ttu-id="fc5e0-105">如需範例，請參閱 [Filestream 及 OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-105">For samples, see [Filestream and OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).</span></span>  
  
 <span data-ttu-id="fc5e0-106">若要傳送與接收大於 2 GB 的 `varbinary(max)` 值，應用程式會在參數和結果繫結中使用 `DBTYPE_IUNKNOWN`。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-106">To send and receive `varbinary(max)` values greater than 2 GB, an application uses `DBTYPE_IUNKNOWN` in parameter and result bindings.</span></span> <span data-ttu-id="fc5e0-107">若是參數，提供者必須針對 ISequentialStream 和傳回 ISequentialStream 的結果，呼叫 IUnknown::QueryInterface。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-107">For parameters the provider must call IUnknown::QueryInterface for ISequentialStream and for results that return ISequentialStream.</span></span>  
  
 <span data-ttu-id="fc5e0-108">若是 OLE DB，將會放寬與 ISequentialStream 值相關的檢查。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-108">For OLE DB, checking related to ISequentialStream values will be relaxed.</span></span> <span data-ttu-id="fc5e0-109">當*wType* `DBTYPE_IUNKNOWN` 在結構中時 `DBBINDING` ，可以 `DBPART_LENGTH` 從*dwPart*中省略，或將資料緩衝區) 中 offset *obLength*的資料 (長度設定為 ~ 0，藉以停用長度檢查。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-109">When *wType* is `DBTYPE_IUNKNOWN` in the `DBBINDING` struct, length checking can be disabled either by omitting `DBPART_LENGTH` from *dwPart* or by setting the length of the data (at offset *obLength* in the data buffer) to ~0.</span></span> <span data-ttu-id="fc5e0-110">在此情況下，提供者將不會檢查值的長度，而且將會透過資料流要求並傳回所有可用的資料。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-110">In this case, the provider will not check the length of the value and will request and return all of the data available through the stream.</span></span> <span data-ttu-id="fc5e0-111">這項變更將會套用到所有大型物件 (LOB) 類型與 XML，但是只會在連接到 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (或更新版本) 伺服器時才會套用。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-111">This change will be applied to all large object (LOB) types and XML, but only when connected to [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (or later) servers.</span></span> <span data-ttu-id="fc5e0-112">這將會提供開發人員更大的彈性，同時維持現有應用程式與下層伺服器的一致性與回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-112">This will provide greater flexibility for developers, while maintaining consistency and backwards compatibility for existing applications and downlevel servers.</span></span>  
  
 <span data-ttu-id="fc5e0-113">此變更會影響傳輸資料的所有介面，主要是 IRowset::GetData、ICommand::Execute 和 IRowsetFastLoad::InsertRow。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-113">This change affects all interfaces that transfer data, principally IRowset::GetData, ICommand::Execute, and IRowsetFastLoad::InsertRow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc5e0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc5e0-114">See Also</span></span>  
 [<span data-ttu-id="fc5e0-115">SQL Server Native Client 程式設計</span><span class="sxs-lookup"><span data-stu-id="fc5e0-115">SQL Server Native Client Programming</span></span>](../sql-server-native-client-programming.md)  
  
  
