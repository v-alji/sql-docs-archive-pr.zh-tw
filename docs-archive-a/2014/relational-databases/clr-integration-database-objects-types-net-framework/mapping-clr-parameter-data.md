---
title: 對應 CLR 參數資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlBinary data type
- SqlInt16 data type
- SqlMoney data type
- SqlString data type
- SqlSingle data type
- data types [CLR integration]
- SqlInt64 data type
- SqlDateTime data type
- SqlXml data type
- SqlBoolean data type
- SqlDecimal data type
- SqlBytes data type
- mapping data types [CLR integration]
- SqlChars data type
- SqlInt32 data type
ms.assetid: 89b43ee9-b9ad-4281-a4bf-c7c8d116daa2
author: rothja
ms.author: jroth
ms.openlocfilehash: 7025c5180eac793534961af63df9ac701c95c03f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709638"
---
# <a name="mapping-clr-parameter-data"></a><span data-ttu-id="71589-102">對應 CLR 參數資料</span><span class="sxs-lookup"><span data-stu-id="71589-102">Mapping CLR Parameter Data</span></span>
  <span data-ttu-id="71589-103">下表列出 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型、其在 common language runtime 中的對等專案， ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 命名空間中的 clr) `System.Data.SqlTypes` ，以及其在 .NET Framework 中的原生 CLR 對應項 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="71589-103">The following table lists [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, their equivalents in the common language runtime (CLR) for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the `System.Data.SqlTypes` namespace, and their native CLR equivalents in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="71589-104">**SQL Server 資料類型**</span><span class="sxs-lookup"><span data-stu-id="71589-104">**SQL Server data type**</span></span>|<span data-ttu-id="71589-105">類型 (在 System.Data.SqlTypes 或 Microsoft.SqlServer.Types 中)</span><span class="sxs-lookup"><span data-stu-id="71589-105">Type (in System.Data.SqlTypes or Microsoft.SqlServer.Types)</span></span>|<span data-ttu-id="71589-106">**CLR 資料類型 (.NET Framework)**</span><span class="sxs-lookup"><span data-stu-id="71589-106">**CLR data type (.NET Framework)**</span></span>|  
|`bigint`|`SqlInt64`|<span data-ttu-id="71589-107">**Int64、Nullable\<Int64>**</span><span class="sxs-lookup"><span data-stu-id="71589-107">**Int64, Nullable\<Int64>**</span></span>|  
|`binary`|`SqlBytes, SqlBinary`|`Byte[]`|  
|`bit`|`SqlBoolean`|<span data-ttu-id="71589-108">**布林值，可為 Null\<Boolean>**</span><span class="sxs-lookup"><span data-stu-id="71589-108">**Boolean, Nullable\<Boolean>**</span></span>|  
|`char`|<span data-ttu-id="71589-109">無</span><span class="sxs-lookup"><span data-stu-id="71589-109">None</span></span>|<span data-ttu-id="71589-110">無</span><span class="sxs-lookup"><span data-stu-id="71589-110">None</span></span>|  
|`cursor`|<span data-ttu-id="71589-111">無</span><span class="sxs-lookup"><span data-stu-id="71589-111">None</span></span>|<span data-ttu-id="71589-112">無</span><span class="sxs-lookup"><span data-stu-id="71589-112">None</span></span>|  
|`date`|`SqlDateTime`|<span data-ttu-id="71589-113">**DateTime，Nullable\<DateTime>**</span><span class="sxs-lookup"><span data-stu-id="71589-113">**DateTime, Nullable\<DateTime>**</span></span>|  
|`datetime`|`SqlDateTime`|<span data-ttu-id="71589-114">**DateTime，Nullable\<DateTime>**</span><span class="sxs-lookup"><span data-stu-id="71589-114">**DateTime, Nullable\<DateTime>**</span></span>|  
|`datetime2`|<span data-ttu-id="71589-115">無</span><span class="sxs-lookup"><span data-stu-id="71589-115">None</span></span>|<span data-ttu-id="71589-116">**DateTime，Nullable\<DateTime>**</span><span class="sxs-lookup"><span data-stu-id="71589-116">**DateTime, Nullable\<DateTime>**</span></span>|  
|`DATETIMEOFFSET`|`None`|<span data-ttu-id="71589-117">**DateTimeOffset，Nullable\<DateTimeOffset>**</span><span class="sxs-lookup"><span data-stu-id="71589-117">**DateTimeOffset, Nullable\<DateTimeOffset>**</span></span>|  
|`decimal`|`SqlDecimal`|<span data-ttu-id="71589-118">**十進位、可為 Null\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="71589-118">**Decimal, Nullable\<Decimal>**</span></span>|  
|`float`|`SqlDouble`|<span data-ttu-id="71589-119">**Double、Nullable\<Double>**</span><span class="sxs-lookup"><span data-stu-id="71589-119">**Double, Nullable\<Double>**</span></span>|  
|`geography`|`SqlGeography`<br /><br /> <span data-ttu-id="71589-120">`SqlGeography`定義在 Microsoft.SqlServer.Types.dll 中，這會與 SQL Server 一起安裝，而且可以從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [功能套件](https://www.microsoft.com/download/details.aspx?id=53164)下載。</span><span class="sxs-lookup"><span data-stu-id="71589-120">`SqlGeography` is defined in Microsoft.SqlServer.Types.dll, which is installed with SQL Server and can be downloaded from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][feature pack](https://www.microsoft.com/download/details.aspx?id=53164).</span></span>|<span data-ttu-id="71589-121">無</span><span class="sxs-lookup"><span data-stu-id="71589-121">None</span></span>|  
|`geometry`|`SqlGeometry`<br /><br /> <span data-ttu-id="71589-122">`SqlGeometry`定義在 Microsoft.SqlServer.Types.dll 中，這會與 SQL Server 一起安裝，而且可以從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [功能套件](https://www.microsoft.com/download/details.aspx?id=53164)下載。</span><span class="sxs-lookup"><span data-stu-id="71589-122">`SqlGeometry` is defined in Microsoft.SqlServer.Types.dll, which is installed with SQL Server and can be downloaded from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][feature pack](https://www.microsoft.com/download/details.aspx?id=53164).</span></span>|<span data-ttu-id="71589-123">無</span><span class="sxs-lookup"><span data-stu-id="71589-123">None</span></span>|  
|`hierarchyid`|`SqlHierarchyId`<br /><br /> <span data-ttu-id="71589-124">`SqlHierarchyId`定義在 Microsoft.SqlServer.Types.dll 中，這會與 SQL Server 一起安裝，而且可以從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [功能套件](https://www.microsoft.com/download/details.aspx?id=53164)下載。</span><span class="sxs-lookup"><span data-stu-id="71589-124">`SqlHierarchyId` is defined in Microsoft.SqlServer.Types.dll, which is installed with SQL Server and can be downloaded from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][feature pack](https://www.microsoft.com/download/details.aspx?id=53164).</span></span>|<span data-ttu-id="71589-125">無</span><span class="sxs-lookup"><span data-stu-id="71589-125">None</span></span>|  
|`image`|<span data-ttu-id="71589-126">無</span><span class="sxs-lookup"><span data-stu-id="71589-126">None</span></span>|<span data-ttu-id="71589-127">無</span><span class="sxs-lookup"><span data-stu-id="71589-127">None</span></span>|  
|`int`|`SqlInt32`|<span data-ttu-id="71589-128">**Int32，Nullable\<Int32>**</span><span class="sxs-lookup"><span data-stu-id="71589-128">**Int32, Nullable\<Int32>**</span></span>|  
|`money`|`SqlMoney`|<span data-ttu-id="71589-129">**十進位、可為 Null\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="71589-129">**Decimal, Nullable\<Decimal>**</span></span>|  
|`nchar`|`SqlChars, SqlString`|`String, Char[]`|  
|`ntext`|<span data-ttu-id="71589-130">無</span><span class="sxs-lookup"><span data-stu-id="71589-130">None</span></span>|<span data-ttu-id="71589-131">無</span><span class="sxs-lookup"><span data-stu-id="71589-131">None</span></span>|  
|`numeric`|`SqlDecimal`|<span data-ttu-id="71589-132">**十進位、可為 Null\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="71589-132">**Decimal, Nullable\<Decimal>**</span></span>|  
|`nvarchar`|`SqlChars, SqlString`<br /><br /> <span data-ttu-id="71589-133">`SQLChars` 比較適合資料傳輸和存取，而 `SQLString` 比較適合執行 String 作業。</span><span class="sxs-lookup"><span data-stu-id="71589-133">`SQLChars` is a better match for data transfer and access, and `SQLString` is a better match for performing String operations.</span></span>|`String, Char[]`|  
|`nvarchar(1), nchar(1)`|`SqlChars, SqlString`|<span data-ttu-id="71589-134">**Char、String、Char []、Nullable\<char>**</span><span class="sxs-lookup"><span data-stu-id="71589-134">**Char, String, Char[], Nullable\<char>**</span></span>|  
|`real`|<span data-ttu-id="71589-135">`SqlSingle` (`SqlSingle` 的範圍，但大於 `real`)</span><span class="sxs-lookup"><span data-stu-id="71589-135">`SqlSingle` (the range of `SqlSingle`, however, is larger than `real`)</span></span>|<span data-ttu-id="71589-136">**單一、可為 Null\<Single>**</span><span class="sxs-lookup"><span data-stu-id="71589-136">**Single, Nullable\<Single>**</span></span>|  
|`rowversion`|<span data-ttu-id="71589-137">無</span><span class="sxs-lookup"><span data-stu-id="71589-137">None</span></span>|`Byte[]`|  
|`smallint`|`SqlInt16`|<span data-ttu-id="71589-138">**Int16，Nullable\<Int16>**</span><span class="sxs-lookup"><span data-stu-id="71589-138">**Int16, Nullable\<Int16>**</span></span>|  
|`smallmoney`|`SqlMoney`|<span data-ttu-id="71589-139">**十進位、可為 Null\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="71589-139">**Decimal, Nullable\<Decimal>**</span></span>|  
|`sql_variant`|<span data-ttu-id="71589-140">無</span><span class="sxs-lookup"><span data-stu-id="71589-140">None</span></span>|`Object`|  
|`table`|<span data-ttu-id="71589-141">無</span><span class="sxs-lookup"><span data-stu-id="71589-141">None</span></span>|<span data-ttu-id="71589-142">無</span><span class="sxs-lookup"><span data-stu-id="71589-142">None</span></span>|  
|`text`|<span data-ttu-id="71589-143">無</span><span class="sxs-lookup"><span data-stu-id="71589-143">None</span></span>|<span data-ttu-id="71589-144">無</span><span class="sxs-lookup"><span data-stu-id="71589-144">None</span></span>|  
|`time`|<span data-ttu-id="71589-145">無</span><span class="sxs-lookup"><span data-stu-id="71589-145">None</span></span>|<span data-ttu-id="71589-146">**TimeSpan、可為 Null\<TimeSpan>**</span><span class="sxs-lookup"><span data-stu-id="71589-146">**TimeSpan, Nullable\<TimeSpan>**</span></span>|  
|`timestamp`|<span data-ttu-id="71589-147">無</span><span class="sxs-lookup"><span data-stu-id="71589-147">None</span></span>|<span data-ttu-id="71589-148">無</span><span class="sxs-lookup"><span data-stu-id="71589-148">None</span></span>|  
|`tinyint`|`SqlByte`|<span data-ttu-id="71589-149">**Byte、Nullable\<Byte>**</span><span class="sxs-lookup"><span data-stu-id="71589-149">**Byte, Nullable\<Byte>**</span></span>|  
|`uniqueidentifier`|`SqlGuid`|<span data-ttu-id="71589-150">**Guid，可為 Null\<Guid>**</span><span class="sxs-lookup"><span data-stu-id="71589-150">**Guid, Nullable\<Guid>**</span></span>|  
|`User-defined type(UDT)`|<span data-ttu-id="71589-151">無</span><span class="sxs-lookup"><span data-stu-id="71589-151">None</span></span>|<span data-ttu-id="71589-152">繫結到相同組件或相依組件中之使用者定義型別的相同類別。</span><span class="sxs-lookup"><span data-stu-id="71589-152">The same class that is bound to the user-defined type in the same assembly or a dependent assembly.</span></span>|  
|<span data-ttu-id="71589-153">**varbinary**</span><span class="sxs-lookup"><span data-stu-id="71589-153">**varbinary**</span></span>|`SqlBytes, SqlBinary`|`Byte[]`|  
|`varbinary(1), binary(1)`|`SqlBytes, SqlBinary`|<span data-ttu-id="71589-154">**byte、Byte []、Nullable\<byte>**</span><span class="sxs-lookup"><span data-stu-id="71589-154">**byte, Byte[], Nullable\<byte>**</span></span>|  
|`varchar`|<span data-ttu-id="71589-155">無</span><span class="sxs-lookup"><span data-stu-id="71589-155">None</span></span>|<span data-ttu-id="71589-156">無</span><span class="sxs-lookup"><span data-stu-id="71589-156">None</span></span>|  
|`xml`|`SqlXml`|<span data-ttu-id="71589-157">無</span><span class="sxs-lookup"><span data-stu-id="71589-157">None</span></span>|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a><span data-ttu-id="71589-158">利用 Out 參數自動轉換資料類型</span><span class="sxs-lookup"><span data-stu-id="71589-158">Automatic Data Type Conversion with Out Parameters</span></span>  
 <span data-ttu-id="71589-159">CLR 方法可以利用 `out` 修飾詞 (Microsoft Visual C#) 或 `<Out()> ByRef` (Microsoft Visual Basic) 標示輸入參數，以便將資訊傳回到呼叫程式碼或程式。如果輸入參數在 `System.Data.SqlTypes` 命名空間中為 CLR 資料類型，而且呼叫程式會將其對等的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型指定為輸入參數，當 CLR 方法傳回資料類型時，會自動進行類型轉換。</span><span class="sxs-lookup"><span data-stu-id="71589-159">A CLR method can return information to the calling code or program by marking an input parameter with the `out` modifier (Microsoft Visual C#) or `<Out()> ByRef` (Microsoft Visual Basic) If the input parameter is a CLR data type in the `System.Data.SqlTypes` namespace, and the calling program specifies its equivalent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type as the input parameter, a type conversion occurs automatically when the CLR method returns the data type.</span></span>  
  
 <span data-ttu-id="71589-160">例如，下列 CLR 預存程序所擁有的 `SqlInt32` CLR 資料類型輸入參數會以 `out` (C#) 或 `<Out()> ByRef` (Visual Basic) 標示：</span><span class="sxs-lookup"><span data-stu-id="71589-160">For example, the following CLR stored procedure has an input parameter of `SqlInt32` CLR data type that is marked with `out` (C#) or `<Out()> ByRef` (Visual Basic):</span></span>  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ ... }  
```  
  
```vb  
<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
...  
End Sub  
```  
  
 <span data-ttu-id="71589-161">在資料庫中建置與建立組件之後，就會使用下列 Transact-SQL，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中建立預存程序，這會將 `int` 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型指定為 OUTPUT 參數：</span><span class="sxs-lookup"><span data-stu-id="71589-161">After the assembly is built and created in the database, the stored procedure is created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with the following Transact-SQL, which specifies a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of `int` as an OUTPUT parameter:</span></span>  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 <span data-ttu-id="71589-162">呼叫 CLR 預存程序時，`SqlInt32` 資料類型會自動轉換為 `int` 資料類型，並傳回到呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="71589-162">When the CLR stored procedure is called, the `SqlInt32` data type is automatically converted to an `int` data type, and returned to the calling program.</span></span>  
  
 <span data-ttu-id="71589-163">不過，並非所有 CLR 資料類型都可以透過 out 參數，自動轉換為其對等的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="71589-163">Not all CLR data types can be automatically converted to their equivalent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types through an out parameter, however.</span></span> <span data-ttu-id="71589-164">下表列出這些例外。</span><span class="sxs-lookup"><span data-stu-id="71589-164">The following table lists these exceptions.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71589-165">**CLR 資料類型 (SQL Server)**</span><span class="sxs-lookup"><span data-stu-id="71589-165">**CLR data type (SQL Server)**</span></span>|<span data-ttu-id="71589-166">**SQL Server 資料類型**</span><span class="sxs-lookup"><span data-stu-id="71589-166">**SQL Server data type**</span></span>|  
|`Decimal`|<span data-ttu-id="71589-167">SMALLMONEY</span><span class="sxs-lookup"><span data-stu-id="71589-167">smallmoney</span></span>|  
|`SqlMoney`|<span data-ttu-id="71589-168">SMALLMONEY</span><span class="sxs-lookup"><span data-stu-id="71589-168">smallmoney</span></span>|  
|`Decimal`|<span data-ttu-id="71589-169">money</span><span class="sxs-lookup"><span data-stu-id="71589-169">money</span></span>|  
|`DateTime`|<span data-ttu-id="71589-170">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="71589-170">smalldatetime</span></span>|  
|`SQLDateTime`|<span data-ttu-id="71589-171">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="71589-171">smalldatetime</span></span>|  
  
## <a name="change-history"></a><span data-ttu-id="71589-172">變更記錄</span><span class="sxs-lookup"><span data-stu-id="71589-172">Change History</span></span>  
  
|<span data-ttu-id="71589-173">更新的內容</span><span class="sxs-lookup"><span data-stu-id="71589-173">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="71589-174">已在對應資料表中加入 `SqlGeography`、`SqlGeometry` 和 `SqlHierarchyId` 類型。</span><span class="sxs-lookup"><span data-stu-id="71589-174">Added `SqlGeography`, `SqlGeometry`, and `SqlHierarchyId` types to the mapping table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71589-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71589-175">See Also</span></span>  
 [<span data-ttu-id="71589-176">.NET Framework 的 SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="71589-176">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
