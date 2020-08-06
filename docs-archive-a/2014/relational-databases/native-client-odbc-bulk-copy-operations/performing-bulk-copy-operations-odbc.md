---
title: " (ODBC) 執行大量複製作業 |Microsoft Docs"
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC]
- ODBC, bulk copy operations
- minimally logged operations [SQL Server Native Client]
- bulk copy [ODBC], about bulk copy
ms.assetid: 5c793405-487c-4f52-88b8-0091d529afb3
author: rothja
ms.author: jroth
ms.openlocfilehash: f2647ebca703eab46d7be0e1cfc2490a65384ee6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708286"
---
# <a name="performing-bulk-copy-operations-odbc"></a><span data-ttu-id="37cce-102">執行大量複製作業 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="37cce-102">Performing Bulk Copy Operations (ODBC)</span></span>
  <span data-ttu-id="37cce-103">ODBC 標準不直接支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="37cce-103">The ODBC standard does not directly support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk copy operations.</span></span> <span data-ttu-id="37cce-104">連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 或更新版本的值行個體時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式支援執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大量複製作業的 DB-Library 函數。</span><span class="sxs-lookup"><span data-stu-id="37cce-104">When connected to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports the DB-Library functions that perform [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk copy operations.</span></span> <span data-ttu-id="37cce-105">此驅動程式專屬的延伸模組提供一個簡單的升級路徑給使用大量複製函數的現有 DB-Library 應用程式。</span><span class="sxs-lookup"><span data-stu-id="37cce-105">This driver-specific extension provides an easy upgrade path for existing DB-Library applications that use bulk copy functions.</span></span> <span data-ttu-id="37cce-106">特定的大量複製支援位於下列檔案中：</span><span class="sxs-lookup"><span data-stu-id="37cce-106">The specialized bulk copy support is in the following files:</span></span>  
  
-   <span data-ttu-id="37cce-107">sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="37cce-107">sqlncli.h</span></span>  
  
     <span data-ttu-id="37cce-108">包括適用於大量複製函數的函數原型與常數定義。</span><span class="sxs-lookup"><span data-stu-id="37cce-108">Includes function prototypes and constant definitions for bulk copy functions.</span></span> <span data-ttu-id="37cce-109">sqlncli.h 必須包含在執行大量複製作業的 ODBC 應用程式中，而且必須在應用程式編譯時的 include 路徑中。</span><span class="sxs-lookup"><span data-stu-id="37cce-109">sqlncli.h must be included in the ODBC application performing bulk copy operations and must be in the application's include path when it is compiled.</span></span>  
  
-   <span data-ttu-id="37cce-110">sqlncli11.lib</span><span class="sxs-lookup"><span data-stu-id="37cce-110">sqlncli11.lib</span></span>  
  
     <span data-ttu-id="37cce-111">必須位於連結器 (Linker) 的程式庫路徑中，並指定為要連結的檔案。</span><span class="sxs-lookup"><span data-stu-id="37cce-111">Must be in the library path of the linker and specified as a file to be linked.</span></span> <span data-ttu-id="37cce-112">sqlncli11.lib 是透過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式散發。</span><span class="sxs-lookup"><span data-stu-id="37cce-112">sqlncli11.lib is distributed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
-   <span data-ttu-id="37cce-113">sqlncli11.dll</span><span class="sxs-lookup"><span data-stu-id="37cce-113">sqlncli11.dll</span></span>  
  
     <span data-ttu-id="37cce-114">在執行時間必須存在。</span><span class="sxs-lookup"><span data-stu-id="37cce-114">Must be present at execution time.</span></span> <span data-ttu-id="37cce-115">sqlncli11.dll 是透過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式散發。</span><span class="sxs-lookup"><span data-stu-id="37cce-115">sqlncli11.dll is distributed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="37cce-116">ODBC **SQLBulkOperations**函數與大量複製函數沒有任何關聯性 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="37cce-116">The ODBC **SQLBulkOperations** function has no relationship to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk copy functions.</span></span> <span data-ttu-id="37cce-117">應用程式必須使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 專用的大量複製函數才能執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="37cce-117">Applications must use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific bulk-copy functions to perform bulk copy operations.</span></span>  
  
## <a name="minimally-logging-bulk-copies"></a><span data-ttu-id="37cce-118">最低限度記錄的大量複製</span><span class="sxs-lookup"><span data-stu-id="37cce-118">Minimally Logging Bulk Copies</span></span>  
 <span data-ttu-id="37cce-119">利用完整復原模式，大量載入所執行的所有資料列插入作業都會完整記錄在交易記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="37cce-119">With the Full Recovery model, all row-insert operations performed by bulk load are fully logged in the transaction log.</span></span> <span data-ttu-id="37cce-120">對於大型資料載入，這可能會導致交易記錄檔迅速填滿。</span><span class="sxs-lookup"><span data-stu-id="37cce-120">For large data loads, this can cause the transaction log to fill rapidly.</span></span> <span data-ttu-id="37cce-121">在某些情況下，可以用最低限度記錄。</span><span class="sxs-lookup"><span data-stu-id="37cce-121">Under certain conditions, minimally logging is possible.</span></span> <span data-ttu-id="37cce-122">最低限度記錄會降低大量載入作業填滿記錄檔空間的可能性，而且也比完整記錄更有效率。</span><span class="sxs-lookup"><span data-stu-id="37cce-122">Minimal logging reduces the possibility of a bulk load operation filling the log space and is also more efficient than full logging.</span></span>  
  
 <span data-ttu-id="37cce-123">如需使用最低限度記錄的詳細資訊，請參閱[大量匯入的最低限度記錄的必要條件](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md)。</span><span class="sxs-lookup"><span data-stu-id="37cce-123">For information on using minimal logging, see [Prerequisites for Minimal Logging in Bulk Import](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37cce-124">備註</span><span class="sxs-lookup"><span data-stu-id="37cce-124">Remarks</span></span>  
 <span data-ttu-id="37cce-125">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本中使用 bcp.exe 時，如果在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 之前沒有錯誤，則可能會看到錯誤。</span><span class="sxs-lookup"><span data-stu-id="37cce-125">When using bcp.exe in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later, you might see errors in situations where there were no errors prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="37cce-126">這是因為在更新版本中，bcp.exe 不再執行隱含資料類型轉換。</span><span class="sxs-lookup"><span data-stu-id="37cce-126">This is because in the later versions, bcp.exe no longer performs implicit data type conversion.</span></span> <span data-ttu-id="37cce-127">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 之前，如果目標資料表有 money 資料類型，則 bcp.exe 會將數值資料轉換為 money 資料類型。</span><span class="sxs-lookup"><span data-stu-id="37cce-127">Prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], bcp.exe converted numeric data to a money data type, if the target table had a money data type.</span></span> <span data-ttu-id="37cce-128">不過，在這種情況下，bcp.exe 只會截斷額外的欄位。</span><span class="sxs-lookup"><span data-stu-id="37cce-128">However, in that situation, bcp.exe simply truncated extra fields.</span></span> <span data-ttu-id="37cce-129">從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 開始，當檔案和目標資料表之間的資料類型不符時，如果有任何資料必須截斷才能容納到目標資料表，bcp.exe 將會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="37cce-129">Beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], if data types do not match between the file and the target table, bcp.exe will raise an error if there is any data that would have to be truncated to fit into the target table.</span></span> <span data-ttu-id="37cce-130">若要解決此錯誤，請修正資料以符合目標資料類型。</span><span class="sxs-lookup"><span data-stu-id="37cce-130">To resolve this error, fix the data to match the target data type.</span></span> <span data-ttu-id="37cce-131">或者，使用 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 之前版本的 bcp.exe。</span><span class="sxs-lookup"><span data-stu-id="37cce-131">Optionally, use bcp.exe from a release prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37cce-132">本節內容</span><span class="sxs-lookup"><span data-stu-id="37cce-132">In This Section</span></span>  
  
-   [<span data-ttu-id="37cce-133">使用資料檔案與格式檔案</span><span class="sxs-lookup"><span data-stu-id="37cce-133">Using Data Files and Format Files</span></span>](using-data-files-and-format-files.md)  
  
-   [<span data-ttu-id="37cce-134">從程式變數中大量複製</span><span class="sxs-lookup"><span data-stu-id="37cce-134">Bulk Copying from Program Variables</span></span>](bulk-copying-from-program-variables.md)  
  
-   [<span data-ttu-id="37cce-135">管理大量複製批次大小</span><span class="sxs-lookup"><span data-stu-id="37cce-135">Managing Bulk Copy Batch Sizes</span></span>](managing-bulk-copy-batch-sizes.md)  
  
-   [<span data-ttu-id="37cce-136">大量複製 Text 與 Image 資料</span><span class="sxs-lookup"><span data-stu-id="37cce-136">Bulk Copying Text and Image Data</span></span>](bulk-copying-text-and-image-data.md)  
  
-   [<span data-ttu-id="37cce-137">從 DB-Library 轉換成 ODBC 大量複製</span><span class="sxs-lookup"><span data-stu-id="37cce-137">Converting from DB-Library to ODBC Bulk Copy</span></span>](converting-from-db-library-to-odbc-bulk-copy.md)  
  
## <a name="see-also"></a><span data-ttu-id="37cce-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37cce-138">See Also</span></span>  
 <span data-ttu-id="37cce-139">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="37cce-139">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="37cce-140">資料的大量匯入及匯出 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="37cce-140">Bulk Import and Export of Data &#40;SQL Server&#41;</span></span>](../import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
