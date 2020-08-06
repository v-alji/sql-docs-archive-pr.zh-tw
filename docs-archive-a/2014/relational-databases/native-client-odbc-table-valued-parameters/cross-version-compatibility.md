---
title: 跨版本相容性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: rothja
ms.author: jroth
ms.openlocfilehash: af434713946f5c568ee71644a7403f9496a8c16f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598859"
---
# <a name="cross-version-compatibility"></a><span data-ttu-id="6c9cf-102">跨版本相容性</span><span class="sxs-lookup"><span data-stu-id="6c9cf-102">Cross-Version Compatibility</span></span>
  <span data-ttu-id="6c9cf-103">當早於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 用戶端或伺服器執行個體預期處理資料表值參數時，可能會發生跨版本衝突。</span><span class="sxs-lookup"><span data-stu-id="6c9cf-103">Cross-version conflicts can occur when client or server instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] are expected to process table-valued parameters.</span></span>  
  
 <span data-ttu-id="6c9cf-104">一般而言，資料表值參數功能僅適用於 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 用戶端 (使用 SQL Server Native Client 10.0)，或連接到 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (或更新版本) 伺服器的更新版本。</span><span class="sxs-lookup"><span data-stu-id="6c9cf-104">In general, table-valued parameter functionality is only available to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] clients (using SQL Server Native Client 10.0) or later that are connected to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later) servers.</span></span> <span data-ttu-id="6c9cf-105">只有當連接到 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (或更新版本的) 伺服器時，目錄函數結果集中的新資料行才會出現。</span><span class="sxs-lookup"><span data-stu-id="6c9cf-105">New columns in catalog function result sets will only be present when connected to a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later) server.</span></span>  
  
 <span data-ttu-id="6c9cf-106">如果利用舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 編譯的用戶端應用程式執行要求資料表值參數的陳述式，伺服器會透過資料轉換錯誤偵測到這個狀況，而且 ODBC 會將此狀況傳回為 SQLSTATE 07006 以及「限制的資料類型屬性違規」訊息。</span><span class="sxs-lookup"><span data-stu-id="6c9cf-106">If a client application compiled with an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client executes statements that expect table-valued parameters, the server detects this condition through a data conversion error, and ODBC returns this as a SQLSTATE 07006 and the message "Restricted data type attribute violation".</span></span>  
  
 <span data-ttu-id="6c9cf-107">如果以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client 10.0 或更新版本編譯的用戶端應用程式在連接到早于的伺服器實例時嘗試使用資料表值參數 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client 將會偵測到此情況，而 SQLBindCol、SQLBindParameter、SQLSetDescFields 和 SQLSetDescRec 呼叫將會失敗，並出現 SQLSTATE 07006 和訊息「限制的資料類型屬性違規 (此連接 SQL Server 的版本不支援資料表值參數) 」。</span><span class="sxs-lookup"><span data-stu-id="6c9cf-107">If a client application that was compiled with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 or later tries to use table-valued parameters when connected to a server instance earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client will detect this, and SQLBindCol, SQLBindParameter, SQLSetDescFields, and SQLSetDescRec calls will fail with SQLSTATE 07006 and the message "Restricted data type attribute violation (the version of SQL Server for this connection does not support table-valued parameters)".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c9cf-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c9cf-108">See Also</span></span>  
 [<span data-ttu-id="6c9cf-109">ODBC&#41;&#40;的資料表值參數</span><span class="sxs-lookup"><span data-stu-id="6c9cf-109">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
