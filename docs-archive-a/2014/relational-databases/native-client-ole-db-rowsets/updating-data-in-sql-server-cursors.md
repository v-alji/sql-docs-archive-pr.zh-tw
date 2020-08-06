---
title: 更新 SQL Server 資料指標中的資料 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
ms.assetid: 732dafee-f2d5-4aef-aad7-3a8bf3b1e876
author: rothja
ms.author: jroth
ms.openlocfilehash: 42e6221a85c30e3adb97df3a11c9cbdc49216b4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593373"
---
# <a name="updating-data-in-sql-server-cursors"></a><span data-ttu-id="923b2-102">更新 SQL Server 資料指標中的資料</span><span class="sxs-lookup"><span data-stu-id="923b2-102">Updating Data in SQL Server Cursors</span></span>
  <span data-ttu-id="923b2-103">透過資料指標提取和更新資料時 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 原生用戶端 OLE DB 提供者消費者應用程式會受到適用于任何其他用戶端應用程式的相同考慮和條件約束所系結。</span><span class="sxs-lookup"><span data-stu-id="923b2-103">When fetching and updating data through [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer application is bound by the same considerations and constraints that apply to any other client application.</span></span>  
  
 <span data-ttu-id="923b2-104">只有在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料指標中的資料列會參與並行的資料存取控制。</span><span class="sxs-lookup"><span data-stu-id="923b2-104">Only rows in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors participate in concurrent data-access control.</span></span> <span data-ttu-id="923b2-105">取用者要求可修改的資料列集時，並行控制會由 DBPROP_LOCKMODE 所控制。</span><span class="sxs-lookup"><span data-stu-id="923b2-105">When the consumer requests a modifiable rowset, the concurrency control is controlled by DBPROP_LOCKMODE.</span></span> <span data-ttu-id="923b2-106">若要修改並行存取控制的層級，取用者會先設定 DBPROP_LOCKMODE 屬性，然後再開啟資料列集。</span><span class="sxs-lookup"><span data-stu-id="923b2-106">To modify the level of concurrent access control, the consumer sets the DBPROP_LOCKMODE property before opening the rowset.</span></span>  
  
 <span data-ttu-id="923b2-107">如果用戶端應用程式設計讓交易長時間保持開啟狀態，交易隔離等級可能會對資料列定位造成重大落後。</span><span class="sxs-lookup"><span data-stu-id="923b2-107">Transaction isolation levels can cause significant lags in row positioning if client application design lets transactions remain open for long periods of time.</span></span> <span data-ttu-id="923b2-108">根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會使用 DBPROPVAL_TI_READCOMMITTED 所指定的讀取認可隔離等級。</span><span class="sxs-lookup"><span data-stu-id="923b2-108">By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses the read-committed isolation level specified by DBPROPVAL_TI_READCOMMITTED.</span></span> <span data-ttu-id="923b2-109">當資料列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 集並行為唯讀時，Native Client OLE DB 提供者支援中途讀取隔離。</span><span class="sxs-lookup"><span data-stu-id="923b2-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports dirty read isolation when the rowset concurrency is read-only.</span></span> <span data-ttu-id="923b2-110">因此，取用者可以在可修改的資料列集中要求較高的隔離等級，但是無法成功要求任何較低的等級。</span><span class="sxs-lookup"><span data-stu-id="923b2-110">Therefore, the consumer can request a higher level of isolation in a modifiable rowset but cannot request any lower level successfully.</span></span>  
  
## <a name="immediate-and-delayed-update-modes"></a><span data-ttu-id="923b2-111">立即和延遲更新模式</span><span class="sxs-lookup"><span data-stu-id="923b2-111">Immediate and Delayed Update Modes</span></span>  
 <span data-ttu-id="923b2-112">在立即更新模式下，**IRowsetChange::SetData** 的每個呼叫會造成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的往返。</span><span class="sxs-lookup"><span data-stu-id="923b2-112">In immediate update mode, each call to **IRowsetChange::SetData** causes a round trip to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="923b2-113">如果取用者對單一資料列進行多個變更，利用單一 **SetData** 呼叫提交所有變更會更有效率。</span><span class="sxs-lookup"><span data-stu-id="923b2-113">If the consumer makes multiple changes to a single row, it is more efficient to submit all changes with a single **SetData** call.</span></span>  
  
 <span data-ttu-id="923b2-114">在延遲更新模式下，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的往返是針對 **IRowsetUpdate::Update** 之 *cRows* 和 *rghRows* 參數中指示的每個資料列進行。</span><span class="sxs-lookup"><span data-stu-id="923b2-114">In delayed update mode, a roundtrip is made to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for each row indicated in the *cRows* and *rghRows* parameters of **IRowsetUpdate::Update**.</span></span>  
  
 <span data-ttu-id="923b2-115">在任一種模式下，當資料列集沒有開啟任何交易物件時，往返代表不同的交易。</span><span class="sxs-lookup"><span data-stu-id="923b2-115">In either mode, a roundtrip represents a distinct transaction when no transaction object is open for the rowset.</span></span>  
  
 <span data-ttu-id="923b2-116">當您使用**IRowsetUpdate：： Update**時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會嘗試處理每一個指定的資料列。</span><span class="sxs-lookup"><span data-stu-id="923b2-116">When you are using **IRowsetUpdate::Update**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider tries to process each indicated row.</span></span> <span data-ttu-id="923b2-117">因為任何資料列的資料、長度或狀態值無效，而發生錯誤，不會停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者處理。</span><span class="sxs-lookup"><span data-stu-id="923b2-117">An error occurring because of invalid data, length, or status values for any row does not stop [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider processing.</span></span> <span data-ttu-id="923b2-118">參與更新的其他所有資料列或沒有任何資料列可能會遭到修改。</span><span class="sxs-lookup"><span data-stu-id="923b2-118">All or none of the other rows participating in the update may be modified.</span></span> <span data-ttu-id="923b2-119">當*prgRowStatus* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者傳回 DB_S_ERRORSOCCURRED 時，取用者必須檢查傳回的 prgRowStatus 陣列，以判斷任何特定資料列的失敗。</span><span class="sxs-lookup"><span data-stu-id="923b2-119">The consumer must examine the returned *prgRowStatus* array to determine failure for any specific row when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns DB_S_ERRORSOCCURRED.</span></span>  
  
 <span data-ttu-id="923b2-120">取用者不應該假設資料列會以任何特定順序處理。</span><span class="sxs-lookup"><span data-stu-id="923b2-120">A consumer should not assume that rows are processed in any specific order.</span></span> <span data-ttu-id="923b2-121">如果取用者需要透過一個以上的單一資料列進行資料修改的排序處理，取用者應該以應用程式邏輯建立該順序，並開啟交易來包含程序。</span><span class="sxs-lookup"><span data-stu-id="923b2-121">If a consumer requires ordered processing of data modification over more than a single row, the consumer should establish that order in the application logic and open a transaction to enclose the process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="923b2-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="923b2-122">See Also</span></span>  
 [<span data-ttu-id="923b2-123">更新資料列集內的資料</span><span class="sxs-lookup"><span data-stu-id="923b2-123">Updating Data in Rowsets</span></span>](updating-data-in-rowsets.md)  
  
  
