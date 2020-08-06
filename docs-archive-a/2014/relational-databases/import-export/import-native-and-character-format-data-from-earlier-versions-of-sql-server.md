---
title: 從舊版 SQL Server 匯入原生與字元格式資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- earlier versions [SQL Server], import and export data formats
- -V switch
- data formats [SQL Server], earlier versions
- previous versions [SQL Server], import and export data formats
ms.assetid: e644696f-9017-428e-a5b3-d445d1c630b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 274c984d6ecec8af8f5bea27496450a45fc2f1df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598378"
---
# <a name="import-native-and-character-format-data-from-earlier-versions-of-sql-server"></a><span data-ttu-id="0e240-102">從舊版 SQL Server 匯入原生與字元格式資料</span><span class="sxs-lookup"><span data-stu-id="0e240-102">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>
  <span data-ttu-id="0e240-103">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，您可以透過 **-V** 參數使用 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]bcp [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]，從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 、 **或** 匯入原生與字元格式資料。</span><span class="sxs-lookup"><span data-stu-id="0e240-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can use **bcp** to import native and character format data from [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] by using the **-V** switch.</span></span> <span data-ttu-id="0e240-104">**-V** 參數會讓 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用指定之舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的資料類型，而資料檔案格式將會與舊版中的資料檔案格式相同。</span><span class="sxs-lookup"><span data-stu-id="0e240-104">The **-V** switch causes [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to use data types from the specified earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and the data file format are the same as the format in that earlier version.</span></span>  
  
 <span data-ttu-id="0e240-105">若要為資料檔案指定舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請使用 **-V** 參數搭配下列其中一個限定詞：</span><span class="sxs-lookup"><span data-stu-id="0e240-105">To specify an earlier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version for a data file, use the **-V** switch with one of the following qualifiers:</span></span>  
  
|<span data-ttu-id="0e240-106">SQL Server 版本</span><span class="sxs-lookup"><span data-stu-id="0e240-106">SQL Server version</span></span>|<span data-ttu-id="0e240-107">Qualifier</span><span class="sxs-lookup"><span data-stu-id="0e240-107">Qualifier</span></span>|  
|------------------------|---------------|  
|[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]|<span data-ttu-id="0e240-108">**-V80**</span><span class="sxs-lookup"><span data-stu-id="0e240-108">**-V80**</span></span>|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|<span data-ttu-id="0e240-109">**-V90**</span><span class="sxs-lookup"><span data-stu-id="0e240-109">**-V90**</span></span>|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|<span data-ttu-id="0e240-110">**-V100**</span><span class="sxs-lookup"><span data-stu-id="0e240-110">**-V100**</span></span>|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|<span data-ttu-id="0e240-111">**-V 110**</span><span class="sxs-lookup"><span data-stu-id="0e240-111">**-V 110**</span></span>|  
  
## <a name="interpretation-of-data-types"></a><span data-ttu-id="0e240-112">資料類型的解譯</span><span class="sxs-lookup"><span data-stu-id="0e240-112">Interpretation of Data Types</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="0e240-113">及更新的版本支援一些新的類型。</span><span class="sxs-lookup"><span data-stu-id="0e240-113">and later versions have support for some new types.</span></span> <span data-ttu-id="0e240-114">如果您想要將新的資料類型匯入舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，您必須以舊版 **bcp** 用戶端可讀取的格式儲存該資料類型。</span><span class="sxs-lookup"><span data-stu-id="0e240-114">When you want to import a new data type into an earlier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version, the data type must be stored in a format that readable by the older **bcp** clients.</span></span> <span data-ttu-id="0e240-115">下表摘述如何轉換新資料類型，以便與舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]相容。</span><span class="sxs-lookup"><span data-stu-id="0e240-115">The following table summarizes how the new data types are converted for compatibility with the earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="0e240-116">SQL Server 2005 的新資料類型</span><span class="sxs-lookup"><span data-stu-id="0e240-116">New data types in SQL Server 2005</span></span>|<span data-ttu-id="0e240-117">與 6*x*版相容的資料類型</span><span class="sxs-lookup"><span data-stu-id="0e240-117">Compatible data types in version 6*x*</span></span>|<span data-ttu-id="0e240-118">與 70 版相容的資料類型</span><span class="sxs-lookup"><span data-stu-id="0e240-118">Compatible data types in version 70</span></span>|<span data-ttu-id="0e240-119">與 80 版相容的資料類型</span><span class="sxs-lookup"><span data-stu-id="0e240-119">Compatible data types in version 80</span></span>|  
|---------------------------------------|-------------------------------------------|-----------------------------------------|-----------------------------------------|  
|`bigint`|`decimal`|`decimal`|*|  
|`sql_variant`|`text`|`nvarchar(4000)`|*|  
|`varchar(max)`|`text`|`text`|`text`|  
|`nvarchar(max)`|`ntext`|`ntext`|`ntext`|  
|`varbinary(max)`|`image`|`image`|`image`|  
|<span data-ttu-id="0e240-120">XML</span><span class="sxs-lookup"><span data-stu-id="0e240-120">XML</span></span>|`ntext`|`ntext`|`ntext`|  
|<span data-ttu-id="0e240-121">UDT<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0e240-121">UDT<sup>1</sup></span></span>|`image`|`image`|`image`|  
  
 <span data-ttu-id="0e240-122">\*這個類型是原生支援的。</span><span class="sxs-lookup"><span data-stu-id="0e240-122">\* This type is natively supported.</span></span>  
  
 <span data-ttu-id="0e240-123"><sup>1</sup> UDT 表示使用者定義的類型。</span><span class="sxs-lookup"><span data-stu-id="0e240-123"><sup>1</sup> UDT indicates a user defined type.</span></span>  
  
## <a name="exporting-using--v-80"></a><span data-ttu-id="0e240-124">使用 -V 80 匯出</span><span class="sxs-lookup"><span data-stu-id="0e240-124">Exporting using -V 80</span></span>  
 <span data-ttu-id="0e240-125">當您使用 **-V80**參數大量匯出資料時， `nvarchar(max)` 、 `varchar(max)` 、 `varbinary(max)` 、XML 和原生模式中的 UDT 資料會與4位元組前置詞一起儲存，就像、和資料一樣， `text` 而不是使用 `image` `ntext` 8 位元組前置詞，這是 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本的預設值。</span><span class="sxs-lookup"><span data-stu-id="0e240-125">When you bulk export data by using the **-V80** switch, `nvarchar(max)`, `varchar(max)`, `varbinary(max)`, XML, and UDT data in native mode are stored with a 4-byte prefix, like `text`, `image`, and `ntext` data, rather than with an 8-byte prefix, which is the default for [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span>  
  
## <a name="copying-date-values"></a><span data-ttu-id="0e240-126">複製日期值</span><span class="sxs-lookup"><span data-stu-id="0e240-126">Copying Date Values</span></span>  
 <span data-ttu-id="0e240-127">**bcp** 會使用 ODBC 大量複製 API。</span><span class="sxs-lookup"><span data-stu-id="0e240-127">**bcp** uses the ODBC bulk copy API.</span></span> <span data-ttu-id="0e240-128">因此，若要將日期值匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]， **bcp** 會使用 ODBC 日期格式 (*yyyy-mm-dd hh:mm:ss*[ *.f...* ])。</span><span class="sxs-lookup"><span data-stu-id="0e240-128">Therefore, to import date values into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **bcp** uses the ODBC date format (*yyyy-mm-dd hh:mm:ss*[*.f...*]).</span></span>  
  
 <span data-ttu-id="0e240-129">**Bcp**命令會使用和值的 ODBC 預設格式來匯出字元格式資料檔案 `datetime` `smalldatetime` 。</span><span class="sxs-lookup"><span data-stu-id="0e240-129">The **bcp** command exports character format data files using the ODBC default format for `datetime` and `smalldatetime` values.</span></span> <span data-ttu-id="0e240-130">例如，包含日期 `12 Aug 1998` 的 `datetime` 資料行會以字元字串 `1998-08-12 00:00:00.000` 大量複製到資料檔案。</span><span class="sxs-lookup"><span data-stu-id="0e240-130">For example, a `datetime` column containing the date `12 Aug 1998` is bulk copied to a data file as the character string `1998-08-12 00:00:00.000`.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0e240-131">`smalldatetime`使用**bcp**將資料匯入欄位時，請確定秒的值是00.000，否則作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="0e240-131">When importing data into a `smalldatetime` field using **bcp**, be sure the value for seconds is 00.000; otherwise the operation will fail.</span></span> <span data-ttu-id="0e240-132">`smalldatetime` 資料類型只會保留最接近分鐘數的數值。</span><span class="sxs-lookup"><span data-stu-id="0e240-132">The `smalldatetime` data type only holds values to the nearest minute.</span></span> <span data-ttu-id="0e240-133">BULK INSERT 及 INSERT ...SELECT \* FROM OPENROWSET(BULK...) 在這個案例中將不會失敗，但會截斷秒數值。</span><span class="sxs-lookup"><span data-stu-id="0e240-133">BULK INSERT and INSERT ... SELECT \* FROM OPENROWSET(BULK...) will not fail in this instance but will truncate the seconds value.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="0e240-134">相關工作</span><span class="sxs-lookup"><span data-stu-id="0e240-134">Related Tasks</span></span>  
 <span data-ttu-id="0e240-135">**若要使用大量匯入或大量匯出的資料格式**</span><span class="sxs-lookup"><span data-stu-id="0e240-135">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="0e240-136">使用字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e240-136">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="0e240-137">使用原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e240-137">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="0e240-138">使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e240-138">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="0e240-139">使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e240-139">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 
  
## <a name="see-also"></a><span data-ttu-id="0e240-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e240-140">See Also</span></span>  
 <span data-ttu-id="0e240-141">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="0e240-141">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="0e240-142">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e240-142">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="0e240-143">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e240-143">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="0e240-144">[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e240-144">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="0e240-145">[SQL Server Database Engine 回溯相容性](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="0e240-145">[SQL Server Database Engine Backward Compatibility](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span></span>  
 [<span data-ttu-id="0e240-146">CAST 和 CONVERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0e240-146">CAST and CONVERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/cast-and-convert-transact-sql)  
  
  
