---
title: 查詢選項執行 (ANSI 頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.ansi.f1
ms.assetid: c90d7cdf-3309-46f4-b900-220521bb9552
author: rothja
ms.author: jroth
ms.openlocfilehash: 013a7a318ed7f8db9156700f789ae64cf3e4e017
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704370"
---
# <a name="query-options-execution-ansi-page"></a><span data-ttu-id="e1bcd-102">查詢選項執行 (ANSI 頁面)</span><span class="sxs-lookup"><span data-stu-id="e1bcd-102">Query Options Execution (ANSI Page)</span></span>
  <span data-ttu-id="e1bcd-103">使用此頁面來指定 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 將使用 ISO (ANSI) standard 中指定的全部或部分設定來執行查詢。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-103">Use this page to specify that [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will run the queries using all or a portion of the settings specified in the ISO (ANSI) standard.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="e1bcd-104">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="e1bcd-104">UI element list</span></span>  
 <span data-ttu-id="e1bcd-105">**SET ANSI_DEFAULTS**</span><span class="sxs-lookup"><span data-stu-id="e1bcd-105">**SET ANSI_DEFAULTS**</span></span>  
 <span data-ttu-id="e1bcd-106">選取所有的預設 ANSI 設定。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-106">Select all of the default ISO settings.</span></span> <span data-ttu-id="e1bcd-107">依預設，此方塊無法使用，因為只設定了某些 ISO 設定。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-107">This box is unavailable by default, because only some of the ISO settings are configured.</span></span>  
  
 <span data-ttu-id="e1bcd-108">**SET QUOTED_IDENTIFIER**</span><span class="sxs-lookup"><span data-stu-id="e1bcd-108">**SET QUOTED_IDENTIFIER**</span></span>  
 <span data-ttu-id="e1bcd-109">用引號來圍住物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-109">Surround object identifiers with quotation marks.</span></span> <span data-ttu-id="e1bcd-110">預設會選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-110">This option is selected by default.</span></span>  
  
 <span data-ttu-id="e1bcd-111">**SET ANSI_NULL_DFLT_ON**</span><span class="sxs-lookup"><span data-stu-id="e1bcd-111">**SET ANSI_NULL_DFLT_ON**</span></span>  
 <span data-ttu-id="e1bcd-112">針對在 CREATE TABLE 或 ALTER TABLE 陳述式期間未明確定義為 NOTNULL 的所有使用者自訂的資料類型或資料行，允許 Null 值 (預設的狀態)。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-112">Allow null values for all user-defined data types or columns that are not explicitly defined as NOTNULL during a CREATE TABLE or ALTER TABLE statement (the default state).</span></span> <span data-ttu-id="e1bcd-113">預設會選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-113">This option is selected by default.</span></span>  
  
 <span data-ttu-id="e1bcd-114">**SET IMPLICIT_TRANSACTIONS**</span><span class="sxs-lookup"><span data-stu-id="e1bcd-114">**SET IMPLICIT_TRANSACTIONS**</span></span>  
 <span data-ttu-id="e1bcd-115">依預設，不會選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-115">This option is not selected by default.</span></span>  
  
 <span data-ttu-id="e1bcd-116">**SET CURSOR_CLOSE_ON_COMMIT**</span><span class="sxs-lookup"><span data-stu-id="e1bcd-116">**SET CURSOR_CLOSE_ON_COMMIT**</span></span>  
 <span data-ttu-id="e1bcd-117">在認可交易之後，會自動關閉任何開啟的資料指標 (符合 ISO)。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-117">Close any open cursors automatically (in compliance with ISO) when a transaction is committed.</span></span> <span data-ttu-id="e1bcd-118">在清除之後 (設定為 OFF)，資料指標會在交易界限之間保持開啟，只有在關閉連接或明確關閉資料指標時才會關閉。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-118">When cleared (set to OFF), cursors remain open across transaction boundaries, closing only when the connection is closed or when they are explicitly closed.</span></span> <span data-ttu-id="e1bcd-119">依預設，不會選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-119">This option is not selected by default.</span></span>  
  
 <span data-ttu-id="e1bcd-120">**SET ANSI_PADDING**</span><span class="sxs-lookup"><span data-stu-id="e1bcd-120">**SET ANSI_PADDING**</span></span>  
 <span data-ttu-id="e1bcd-121">控制資料行用來儲存值的方式，比資料行的定義大小還短，以及資料行儲存**char**、 **Varchar**、 **binary**和**Varbinary**資料尾端空白之值的方式。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-121">Controls the way the column stores values shorter than the defined size of the column, and the way the column stores values that have trailing blanks in **char**, **varchar**, **binary**, and **varbinary** data.</span></span> <span data-ttu-id="e1bcd-122">這項設定只會影響新資料行的定義。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-122">This setting affects only the definition of new columns.</span></span> <span data-ttu-id="e1bcd-123">建立好資料行之後， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會根據建立資料行之時的設定來儲存值。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-123">After the column is created, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stores the values based on the setting when the column was created.</span></span> <span data-ttu-id="e1bcd-124">這項設定後來的變更並不會影響現有的資料行。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-124">Existing columns are not affected by a later change to this setting.</span></span> <span data-ttu-id="e1bcd-125">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-125">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="e1bcd-126">**SET ANSI_WARNINGS**</span><span class="sxs-lookup"><span data-stu-id="e1bcd-126">**SET ANSI_WARNINGS**</span></span>  
 <span data-ttu-id="e1bcd-127">指定數個錯誤狀況的 ISO 標準行為：</span><span class="sxs-lookup"><span data-stu-id="e1bcd-127">Specifies ISO standard behavior for several error conditions:</span></span>  
  
-   <span data-ttu-id="e1bcd-128">如果選取此核取方塊，而 Null 值出現在彙總函式 (例如，SUM、AVG、MAX、MIN、STDEV、STDEVP、VAR、VARP 或 COUNT) 中，就會產生警告訊息。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-128">When this check box is selected, if null values appear in aggregate functions (such as SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP, or COUNT), a warning message is generated.</span></span> <span data-ttu-id="e1bcd-129">當**關閉**時，不會發出任何警告。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-129">When **OFF**, no warning is issued.</span></span>  
  
-   <span data-ttu-id="e1bcd-130">在清除了這個核取方塊之後，除以零及算術溢位錯誤，都會造成陳述式的復原並產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-130">When this check box is cleared, divide-by-zero and arithmetic overflow errors cause the statement to be rolled back and an error message is generated.</span></span> <span data-ttu-id="e1bcd-131">設定為 OFF 時，除以零及算術溢位錯誤會造成傳回 Null 值。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-131">When OFF, divide-by-zero and arithmetic overflow errors cause null values to be returned.</span></span> <span data-ttu-id="e1bcd-132">如果在 character、Unicode 或 binary 資料行中嘗試 INSERT 或 UPDATE 作業，且新值長度超過資料行的大小上限時，除以零或算術溢位錯誤會造成傳回 Null 值。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-132">The behavior in which a divide-by-zero or arithmetic overflow error causes null values to be returned occurs if an INSERTor UPDATEoperation is attempted on a character, Unicode, or binary column in which the length of a new value exceeds the maximum size of the column.</span></span> <span data-ttu-id="e1bcd-133">如果**SET ANSI_WARNINGS**是 ON，則會依 ISO 標準的指定取消插入或更新作業。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-133">If **SET ANSI_WARNINGS** is ON, the INSERT or UPDATE operation is canceled as specified by the ISO standard.</span></span> <span data-ttu-id="e1bcd-134">字元資料行尾端的空格會被忽略，二進位資料行尾端的 Null 也會被忽略。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-134">Trailing blanks are ignored for character columns, and trailing nulls are ignored for binary columns.</span></span> <span data-ttu-id="e1bcd-135">當它是 OFF 時，便會將資料截斷成為資料行大小，陳述式會繼續作業。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-135">When OFF, data is truncated to the size of the column and the statement succeeds.</span></span>  
  
 <span data-ttu-id="e1bcd-136">預設會選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-136">This option is selected by default.</span></span>  
  
 <span data-ttu-id="e1bcd-137">**SET ANSI_NULLS**</span><span class="sxs-lookup"><span data-stu-id="e1bcd-137">**SET ANSI_NULLS**</span></span>  
 <span data-ttu-id="e1bcd-138">指定搭配 null 值一起使用時，等於 (`=`) 和不等於 (`<>`) 比較運算子的 ISO 相容行為。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-138">Specifies ISO compliant behavior of the Equal (`=`) and Not Equal to (`<>`) comparison operators when used with null values.</span></span> <span data-ttu-id="e1bcd-139">如果選取 **SET ANSI_NULLS** ，所有針對 Null 值的比較，都會評估為 UNKNOWN，也就是符合 ISO 的行為。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-139">When **SET ANSI_NULLS** is selected, all comparisons against a null value evaluate to UNKNOWN, the ISO compliant behavior.</span></span> <span data-ttu-id="e1bcd-140">如果未選取 **SET ANSI_NULLS** ，且如果資料值為 NULL，則所有資料針對 Null 值比較，都會評估為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-140">When **SET ANSI_NULLS** is not selected, comparisons of all data against a null value evaluate to TRUE if the data value is NULL.</span></span> <span data-ttu-id="e1bcd-141">預設會選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-141">This option is selected by default.</span></span>  
  
 <span data-ttu-id="e1bcd-142">**重設為預設值**</span><span class="sxs-lookup"><span data-stu-id="e1bcd-142">**Reset to Default**</span></span>  
 <span data-ttu-id="e1bcd-143">將此頁面上的所有值重設為原始預設值。</span><span class="sxs-lookup"><span data-stu-id="e1bcd-143">Resets all values on this page to the original default values.</span></span>  
  
  
