---
title: 編碼及解碼 SQL Server 識別碼 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: bb9fe0d3-e432-42d3-b324-64dc908b544a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 88e7ebbc81d9c3cb91b1bf678075c5b5d0884890
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687950"
---
# <a name="encode-and-decode-sql-server-identifiers"></a><span data-ttu-id="cfa0e-102">編碼及解碼 SQL Server 識別碼</span><span class="sxs-lookup"><span data-stu-id="cfa0e-102">Encode and Decode SQL Server Identifiers</span></span>
  <span data-ttu-id="cfa0e-103">SQL Server 分隔識別碼有時會包含 Windows PowerShell 路徑中不支援的字元。</span><span class="sxs-lookup"><span data-stu-id="cfa0e-103">SQL Server delimited identifiers sometimes contain characters not supported in Windows PowerShell paths.</span></span> <span data-ttu-id="cfa0e-104">編碼這些字元的十六進位值，就可以指定這些字元。</span><span class="sxs-lookup"><span data-stu-id="cfa0e-104">These characters can be specified by encoding their hexadecimal values.</span></span>  
  
1.  <span data-ttu-id="cfa0e-105">**開始之前：**  [限制事項](#LimitationsRestrictions)</span><span class="sxs-lookup"><span data-stu-id="cfa0e-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)</span></span>  
  
2.  <span data-ttu-id="cfa0e-106">**處理特殊字元：**  [編碼識別碼](#EncodeIdent)、 [解碼識別碼](#DecodeIdent)</span><span class="sxs-lookup"><span data-stu-id="cfa0e-106">**To process special characters:**  [Encoding an Identifier](#EncodeIdent), [Decoding an Identifier](#DecodeIdent)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="cfa0e-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="cfa0e-107">Before You Begin</span></span>  
 <span data-ttu-id="cfa0e-108">Windows PowerShell 路徑名稱中不支援的字元可以表示或編碼為 "%" 字元，後面接著代表該字元之位模式的十六進位值，如 " **%** xx"。</span><span class="sxs-lookup"><span data-stu-id="cfa0e-108">Characters that are not supported in Windows PowerShell path names can be represented, or encoded, as the "%" character followed by the hexadecimal value for the bit pattern that represents the character, as in "**%** xx".</span></span> <span data-ttu-id="cfa0e-109">編碼一定可以用來處理 Windows PowerShell 路徑中不支援的字元。</span><span class="sxs-lookup"><span data-stu-id="cfa0e-109">Encoding can always be used to handle characters that are not supported in Windows PowerShell paths.</span></span>  
  
 <span data-ttu-id="cfa0e-110">**Encode-SqlName** Cmdlet 會將 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別碼作為輸入。</span><span class="sxs-lookup"><span data-stu-id="cfa0e-110">The **Encode-SqlName** cmdlet takes as input a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifier.</span></span> <span data-ttu-id="cfa0e-111">它會輸出一個字串，其中包含編碼為 "%xx" 之 Windows PowerShell 語言不支援的所有字元。</span><span class="sxs-lookup"><span data-stu-id="cfa0e-111">It outputs a string with all the characters that are not supported by the Windows PowerShell language encoded with "%xx".</span></span> <span data-ttu-id="cfa0e-112">**Decode-SqlName** Cmdlet 會將編碼的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別碼作為輸入，並傳回原始識別碼。</span><span class="sxs-lookup"><span data-stu-id="cfa0e-112">The **Decode-SqlName** cmdlet takes as input an encoded [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifier and returns the original identifier.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="cfa0e-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="cfa0e-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="cfa0e-114">`Encode-Sqlname` 和 `Decode-Sqlname` Cmdlet 只能編碼或解碼 SQL Server 分隔識別碼中允許的字元，但在 PowerShell 路徑中則不予支援。</span><span class="sxs-lookup"><span data-stu-id="cfa0e-114">The `Encode-Sqlname` and `Decode-Sqlname` cmdlets only encode or decode the characters that are allowed in SQL Server delimited identifiers, but are not supported in PowerShell paths.</span></span> <span data-ttu-id="cfa0e-115">下列為 **Encode-SqlName** 所編碼和 **Decode-SqlName**所解碼的字元：</span><span class="sxs-lookup"><span data-stu-id="cfa0e-115">These are the characters encoded by **Encode-SqlName** and decoded by **Decode-SqlName**:</span></span>  
  
|||||||||||||  
|-|-|-|-|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="cfa0e-116">**字元**</span><span class="sxs-lookup"><span data-stu-id="cfa0e-116">**Character**</span></span>|\ |/|<span data-ttu-id="cfa0e-117">:</span><span class="sxs-lookup"><span data-stu-id="cfa0e-117">:</span></span>|%|\<|>|*|<span data-ttu-id="cfa0e-118">?</span><span class="sxs-lookup"><span data-stu-id="cfa0e-118">?</span></span>|<span data-ttu-id="cfa0e-119">[</span><span class="sxs-lookup"><span data-stu-id="cfa0e-119">[</span></span>|<span data-ttu-id="cfa0e-120">]</span><span class="sxs-lookup"><span data-stu-id="cfa0e-120">]</span></span>|<span data-ttu-id="cfa0e-121">&#124;</span><span class="sxs-lookup"><span data-stu-id="cfa0e-121">&#124;</span></span>|  
|<span data-ttu-id="cfa0e-122">**十六進位編碼**</span><span class="sxs-lookup"><span data-stu-id="cfa0e-122">**Hexadecimal Encoding**</span></span>|<span data-ttu-id="cfa0e-123">%5C</span><span class="sxs-lookup"><span data-stu-id="cfa0e-123">%5C</span></span>|<span data-ttu-id="cfa0e-124">%2F</span><span class="sxs-lookup"><span data-stu-id="cfa0e-124">%2F</span></span>|<span data-ttu-id="cfa0e-125">%3A</span><span class="sxs-lookup"><span data-stu-id="cfa0e-125">%3A</span></span>|<span data-ttu-id="cfa0e-126">%25</span><span class="sxs-lookup"><span data-stu-id="cfa0e-126">%25</span></span>|<span data-ttu-id="cfa0e-127">%3C</span><span class="sxs-lookup"><span data-stu-id="cfa0e-127">%3C</span></span>|<span data-ttu-id="cfa0e-128">%3E</span><span class="sxs-lookup"><span data-stu-id="cfa0e-128">%3E</span></span>|<span data-ttu-id="cfa0e-129">%2A</span><span class="sxs-lookup"><span data-stu-id="cfa0e-129">%2A</span></span>|<span data-ttu-id="cfa0e-130">%3F</span><span class="sxs-lookup"><span data-stu-id="cfa0e-130">%3F</span></span>|<span data-ttu-id="cfa0e-131">%5B</span><span class="sxs-lookup"><span data-stu-id="cfa0e-131">%5B</span></span>|<span data-ttu-id="cfa0e-132">%5D</span><span class="sxs-lookup"><span data-stu-id="cfa0e-132">%5D</span></span>|<span data-ttu-id="cfa0e-133">%7C</span><span class="sxs-lookup"><span data-stu-id="cfa0e-133">%7C</span></span>|  
  
##  <a name="encoding-an-identifier"></a><a name="EncodeIdent"></a> <span data-ttu-id="cfa0e-134">編碼識別碼</span><span class="sxs-lookup"><span data-stu-id="cfa0e-134">Encoding an Identifier</span></span>  
 <span data-ttu-id="cfa0e-135">**編碼 PowerShell 路徑中的 SQL Server 識別碼**</span><span class="sxs-lookup"><span data-stu-id="cfa0e-135">**To encode a SQL Server identifier in a PowerShell path**</span></span>  
  
-   <span data-ttu-id="cfa0e-136">使用兩種方法的其中一種來編碼 SQL Server 識別碼：</span><span class="sxs-lookup"><span data-stu-id="cfa0e-136">Use one of two methods to encode a SQL Server identifier:</span></span>  
  
    -   <span data-ttu-id="cfa0e-137">使用語法 %XX 指定不支援字元的十六進位代碼，其中 XX 是十六進位代碼。</span><span class="sxs-lookup"><span data-stu-id="cfa0e-137">Specify the hexadecimal code for the unsupported character using the syntax %XX, where XX is the hexadecimal code.</span></span>  
  
    -   <span data-ttu-id="cfa0e-138">識別碼會以加上引號的字串形式傳遞給 `Encode-Sqlname` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cfa0e-138">Pass the identifier as a quoted string to the `Encode-Sqlname` cmdlet</span></span>  
  
### <a name="examples-encoding"></a><span data-ttu-id="cfa0e-139">範例 (編碼)</span><span class="sxs-lookup"><span data-stu-id="cfa0e-139">Examples (Encoding)</span></span>  
 <span data-ttu-id="cfa0e-140">此範例指定 ":" 字元 (%3A) 的編碼版本：</span><span class="sxs-lookup"><span data-stu-id="cfa0e-140">This example specifies the encoded version of the ":" character (%3A):</span></span>  
  
```  
Set-Location Table%3ATest  
```  
  
 <span data-ttu-id="cfa0e-141">您也可以使用 **Encode-SqlName** 來建立 Windows PowerShell 所支援的名稱：</span><span class="sxs-lookup"><span data-stu-id="cfa0e-141">Alternatively, you can use **Encode-SqlName** to build a name supported by Windows PowerShell:</span></span>  
  
```powershell
Set-Location (Encode-SqlName "Table:Test")  
```  
  
##  <a name="decoding-an-identifier"></a><a name="DecodeIdent"></a> <span data-ttu-id="cfa0e-142">解碼識別碼</span><span class="sxs-lookup"><span data-stu-id="cfa0e-142">Decoding an Identifier</span></span>  
 <span data-ttu-id="cfa0e-143">**解碼 PowerShell 路徑中的 SQL Server 識別碼**</span><span class="sxs-lookup"><span data-stu-id="cfa0e-143">**To decode a SQL Server identifier from a PowerShell path**</span></span>  
  
 <span data-ttu-id="cfa0e-144">`Decode-Sqlname` Cmdlet 可用來將十六進位編碼取代為該編碼所代表的字元。</span><span class="sxs-lookup"><span data-stu-id="cfa0e-144">Use the `Decode-Sqlname` cmdlet to replace the hexadecimal encodings with the characters represented by the encoding.</span></span>  
  
### <a name="examples-decoding"></a><span data-ttu-id="cfa0e-145">範例 (解碼)</span><span class="sxs-lookup"><span data-stu-id="cfa0e-145">Examples (Decoding)</span></span>  
 <span data-ttu-id="cfa0e-146">此範例會傳回 "Table:Test"：</span><span class="sxs-lookup"><span data-stu-id="cfa0e-146">This example returns "Table:Test":</span></span>  
  
```powershell
Decode-SqlName "Table%3ATest"  
```  
  
## <a name="see-also"></a><span data-ttu-id="cfa0e-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfa0e-147">See Also</span></span>  
 <span data-ttu-id="cfa0e-148">[PowerShell 中的 SQL Server 識別碼](sql-server-identifiers-in-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="cfa0e-148">[SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md) </span></span>  
 <span data-ttu-id="cfa0e-149">[SQL Server PowerShell 提供者](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="cfa0e-149">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="cfa0e-150">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="cfa0e-150">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
