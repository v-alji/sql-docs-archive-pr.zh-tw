---
title: 撰寫使用者定義類型的程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- validation [CLR integration]
- UDTs [CLR integration], coding
- UserDefined serialization format [CLR integration]
- Point UDT
- Parse method
- null values [CLR integration]
- ToString method
- ValidatePoint method
- attributes [CLR integration]
- coding user-defined types [CLR integration]
- Read method
- Write method
- nullability [CLR integration]
- user-defined types [CLR integration], coding
- Currency UDT
- validating UDT values
- exposing UDT properties [CLR integration]
ms.assetid: 1e5b43b3-4971-45ee-a591-3f535e2ac722
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e88c4d8162e5c7c921f5c5062f5b3c23df40a2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592719"
---
# <a name="coding-user-defined-types"></a><span data-ttu-id="74c62-102">編碼使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="74c62-102">Coding User-Defined Types</span></span>
  <span data-ttu-id="74c62-103">當您編碼使用者定義型別 (UDT) 定義時，您必須根據您是否將 UDT 實作為類別或結構以及您已選擇的格式和序列化選項來實作各種功能。</span><span class="sxs-lookup"><span data-stu-id="74c62-103">When coding your user-defined type (UDT) definition, you must implement various features, depending on whether you are implementing the UDT as a class or a structure, as well as on the format and serialization options you have chosen.</span></span>  
  
 <span data-ttu-id="74c62-104">本章節的範例說明如何將 `Point` UDT 實作為 `struct` (或 Visual Basic 中的 `Structure`)。</span><span class="sxs-lookup"><span data-stu-id="74c62-104">The example in this section illustrates implementing a `Point` UDT as a `struct` (or `Structure` in Visual Basic).</span></span> <span data-ttu-id="74c62-105">`Point` UDT 是由實作為屬性程序的 X 及 Y 座標組成。</span><span class="sxs-lookup"><span data-stu-id="74c62-105">The `Point` UDT consists of X and Y coordinates implemented as property procedures.</span></span>  
  
 <span data-ttu-id="74c62-106">定義 UDT 時需要下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="74c62-106">The following namespaces are required when defining a UDT:</span></span>  
  
```vb  
Imports System  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
```  
  
```csharp  
using System;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
```  
  
 <span data-ttu-id="74c62-107">`Microsoft.SqlServer.Server` 命名空間包含 UDT 之各種屬性所需的物件，而 `System.Data.SqlTypes` 命名空間則包含表示組件可用之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 原生資料類型的類別。</span><span class="sxs-lookup"><span data-stu-id="74c62-107">The `Microsoft.SqlServer.Server` namespace contains the objects required for various attributes of your UDT, and the `System.Data.SqlTypes` namespace contains the classes that represent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data types available to the assembly.</span></span> <span data-ttu-id="74c62-108">若要能夠正確運作，您的組件還需要其他的命名空間。</span><span class="sxs-lookup"><span data-stu-id="74c62-108">There may of course be additional namespaces that your assembly requires in order to function correctly.</span></span> <span data-ttu-id="74c62-109">`Point` UDT 也使用 `System.Text` 命名空間來處理字串。</span><span class="sxs-lookup"><span data-stu-id="74c62-109">The `Point` UDT also uses the `System.Text` namespace for working with strings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="74c62-110">使用 `/clr:pure` 編譯的 Visual C++ 資料庫物件 (例如 UDT) 不支援執行。</span><span class="sxs-lookup"><span data-stu-id="74c62-110">Visual C++ database objects, such as UDTs, compiled with `/clr:pure` are not supported for execution.</span></span>  
  
## <a name="specifying-attributes"></a><span data-ttu-id="74c62-111">指定屬性</span><span class="sxs-lookup"><span data-stu-id="74c62-111">Specifying Attributes</span></span>  
 <span data-ttu-id="74c62-112">屬性會決定如何使用序列化來建構 UDT 的儲存表示，並將 UDT 以傳值方式傳輸到用戶端。</span><span class="sxs-lookup"><span data-stu-id="74c62-112">Attributes determine how serialization is used to construct the storage representation of UDTs and to transmit UDTs by value to the client.</span></span>  
  
 <span data-ttu-id="74c62-113">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 是必要項目。</span><span class="sxs-lookup"><span data-stu-id="74c62-113">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` is required.</span></span> <span data-ttu-id="74c62-114">`Serializable` 屬性是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="74c62-114">The `Serializable` attribute is optional.</span></span> <span data-ttu-id="74c62-115">您還可指定 `Microsoft.SqlServer.Server.SqlFacetAttribute`，以提供 UDT 之傳回類型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="74c62-115">You can also specify the `Microsoft.SqlServer.Server.SqlFacetAttribute` to provide information about the return type of a UDT.</span></span> <span data-ttu-id="74c62-116">如需詳細資訊，請參閱 [CLR 常式的自訂屬性](../clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)。</span><span class="sxs-lookup"><span data-stu-id="74c62-116">For more information, see [Custom Attributes for CLR Routines](../clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md).</span></span>  
  
### <a name="point-udt-attributes"></a><span data-ttu-id="74c62-117">Point UDT 屬性</span><span class="sxs-lookup"><span data-stu-id="74c62-117">Point UDT Attributes</span></span>  
 <span data-ttu-id="74c62-118">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 會將 `Point` UDT 的儲存格式設定為 `Native`。</span><span class="sxs-lookup"><span data-stu-id="74c62-118">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` sets the storage format for the `Point` UDT to `Native`.</span></span> <span data-ttu-id="74c62-119">`IsByteOrdered` 會設為 `true`，可保證 SQL Server 中比較的結果，與在 Managed 程式碼中發生的比較相同。</span><span class="sxs-lookup"><span data-stu-id="74c62-119">`IsByteOrdered` is set to `true`, which guarantees that the results of comparisons are the same in SQL Server as if the same comparison had taken place in managed code.</span></span> <span data-ttu-id="74c62-120">UDT 會實作 `System.Data.SqlTypes.INullable` 介面，好讓 UDT 可感知 null。</span><span class="sxs-lookup"><span data-stu-id="74c62-120">The UDT implements the `System.Data.SqlTypes.INullable` interface to make the UDT null aware.</span></span>  
  
 <span data-ttu-id="74c62-121">下列程式碼片段顯示 `Point` UDT 的屬性。</span><span class="sxs-lookup"><span data-stu-id="74c62-121">The following code fragment shows the attributes for the `Point` UDT.</span></span>  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True)> _  
  Public Structure Point  
    Implements INullable  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true)]  
public struct Point : INullable  
{  
```  
  
## <a name="implementing-nullability"></a><span data-ttu-id="74c62-122">實作 Null 屬性</span><span class="sxs-lookup"><span data-stu-id="74c62-122">Implementing Nullability</span></span>  
 <span data-ttu-id="74c62-123">除了正確指定組件的屬性以外，UDT 還必須支援 Null 屬性。</span><span class="sxs-lookup"><span data-stu-id="74c62-123">In addition to specifying the attributes for your assemblies correctly, your UDT must also support nullability.</span></span> <span data-ttu-id="74c62-124">載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 UDT 可感知 Null，但是為了讓 UDT 能夠辨識 Null 值，UDT 必須實作 `System.Data.SqlTypes.INullable` 介面。</span><span class="sxs-lookup"><span data-stu-id="74c62-124">UDTs loaded into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are null-aware, but in order for the UDT to recognize a null value, the UDT must implement the `System.Data.SqlTypes.INullable` interface.</span></span>  
  
 <span data-ttu-id="74c62-125">您必須建立名為 `IsNull` 的屬性，需要此屬性來判斷在 CLR 程式碼內某值是否為 Null。</span><span class="sxs-lookup"><span data-stu-id="74c62-125">You must create a property named `IsNull`, which is needed to determine whether a value is null from within CLR code.</span></span> <span data-ttu-id="74c62-126">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 找到 UDT 的 Null 執行個體時，便會使用正常的 Null 處理方法來保存 UDT。</span><span class="sxs-lookup"><span data-stu-id="74c62-126">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finds a null instance of a UDT, the UDT is persisted using normal null-handling methods.</span></span> <span data-ttu-id="74c62-127">除非必要，否則伺服器不會浪費時間來序列化或還原序列化 UDT，而且它也不會浪費空間來儲存 Null UDT。</span><span class="sxs-lookup"><span data-stu-id="74c62-127">The server does not waste time serializing or deserializing the UDT if it does not have to, and it does not waste space to store a null UDT.</span></span> <span data-ttu-id="74c62-128">每次從 CLR 引入 UDT 時都會執行 Null 檢查，這表示使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL 建構來檢查 Null UDT 的作業一定都可運作。</span><span class="sxs-lookup"><span data-stu-id="74c62-128">This check for nulls is performed every time a UDT is brought over from the CLR, which means that using the [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL construct to check for null UDTs should always work.</span></span> <span data-ttu-id="74c62-129">伺服器也會使用 `IsNull` 屬性，以測試執行個體是否為 Null。</span><span class="sxs-lookup"><span data-stu-id="74c62-129">The `IsNull` property is also used by the server to test whether an instance is null.</span></span> <span data-ttu-id="74c62-130">伺服器一旦判定 UDT 為 Null，就可以使用其原生的 Null 處理。</span><span class="sxs-lookup"><span data-stu-id="74c62-130">Once the server determines that the UDT is null, it can use its native null handling.</span></span>  
  
 <span data-ttu-id="74c62-131">`get()` 的 `IsNull` 方法在任何情況下都不是特殊案例。</span><span class="sxs-lookup"><span data-stu-id="74c62-131">The `get()` method of `IsNull` is not special-cased in any way.</span></span> <span data-ttu-id="74c62-132">如果 `Point` 變數 `@p` 是 `Null`，則根據預設會將 `@p.IsNull` 評估為 "NULL"，而非 "1"。</span><span class="sxs-lookup"><span data-stu-id="74c62-132">If a `Point` variable `@p` is `Null`, then `@p.IsNull` will, by default, evaluate to "NULL", not "1".</span></span> <span data-ttu-id="74c62-133">這是因為 `SqlMethod(OnNullCall)` 方法的 `IsNull get()` 屬性預設為 false。</span><span class="sxs-lookup"><span data-stu-id="74c62-133">This is because the `SqlMethod(OnNullCall)` attribute of the `IsNull get()` method defaults to false.</span></span> <span data-ttu-id="74c62-134">因為此物件是 `Null`，所以當要求此屬性時，不會還原序列化此物件、不會呼叫此方法，而且會傳回 "NULL" 的預設值。</span><span class="sxs-lookup"><span data-stu-id="74c62-134">Because the object is `Null`, when the property is requested the object is not deserialized, the method is not called, and a default value of "NULL" is returned.</span></span>  
  
### <a name="example"></a><span data-ttu-id="74c62-135">範例</span><span class="sxs-lookup"><span data-stu-id="74c62-135">Example</span></span>  
 <span data-ttu-id="74c62-136">在下列範例中，`is_Null` 變數為私用，而且會針對 UDT 執行個體保留 Null 狀態。</span><span class="sxs-lookup"><span data-stu-id="74c62-136">In the following example, the `is_Null` variable is private and holds the state of null for the instance of the UDT.</span></span> <span data-ttu-id="74c62-137">您的程式碼必須維護對 `is_Null` 適當的值。</span><span class="sxs-lookup"><span data-stu-id="74c62-137">Your code must maintain an appropriate value for `is_Null`.</span></span> <span data-ttu-id="74c62-138">UDT 也必須有一個名為 `Null` 的靜態屬性，它會傳回 UDT 的 Null 值執行個體。</span><span class="sxs-lookup"><span data-stu-id="74c62-138">The UDT must also have a static property named `Null` that returns a null value instance of the UDT.</span></span> <span data-ttu-id="74c62-139">如果執行個體在資料庫中實際上為 Null，這可讓 UDT 傳回 Null 值。</span><span class="sxs-lookup"><span data-stu-id="74c62-139">This allows the UDT to return a null value if the instance is indeed null in the database.</span></span>  
  
```vb  
Private is_Null As Boolean  
  
Public ReadOnly Property IsNull() As Boolean _  
   Implements INullable.IsNull  
    Get  
        Return (is_Null)  
    End Get  
End Property  
  
Public Shared ReadOnly Property Null() As Point  
    Get  
        Dim pt As New Point  
        pt.is_Null = True  
        Return (pt)  
    End Get  
End Property  
```  
  
```csharp  
private bool is_Null;  
  
public bool IsNull  
{  
    get  
    {  
        return (is_Null);  
    }  
}  
  
public static Point Null  
{  
    get  
    {  
        Point pt = new Point();  
        pt.is_Null = true;  
        return pt;  
    }  
}  
```  
  
### <a name="is-null-vs-isnull"></a><span data-ttu-id="74c62-140">IS NULL vs. IsNull</span><span class="sxs-lookup"><span data-stu-id="74c62-140">IS NULL vs. IsNull</span></span>  
 <span data-ttu-id="74c62-141">假設有一個資料表包含 Points(id int, location Point) 結構描述 (其中 `Point` 為 CLR UDT) 及下列查詢：</span><span class="sxs-lookup"><span data-stu-id="74c62-141">Consider a table that contains the schema Points(id int, location Point), where `Point` is a CLR UDT, and the following queries:</span></span>  
  
```  
--Query 1  
SELECT ID  
FROM Points  
WHERE NOT (location IS NULL) -- Or, WHERE location IS NOT NULL;  
```  
  
```  
--Query 2:  
SELECT ID  
FROM Points  
WHERE location.IsNull = 0;  
```  
  
 <span data-ttu-id="74c62-142">這兩個查詢都會傳回非 `Null` 位置之點的識別碼。</span><span class="sxs-lookup"><span data-stu-id="74c62-142">Both queries return the IDs of points with non-`Null` locations.</span></span> <span data-ttu-id="74c62-143">查詢 1 會使用正常 null 處理，而且不需要還原序列化 UDT。</span><span class="sxs-lookup"><span data-stu-id="74c62-143">In Query 1, normal null-handling is used, and there no deserialization of UDTs is required.</span></span> <span data-ttu-id="74c62-144">另一方面，查詢 2 則必須還原序列化每一個非 `Null` 物件及呼叫 CLR，以取得 `IsNull` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="74c62-144">Query 2, on the other hand, has to deserialize each non-`Null` object and call into the CLR to obtain the value of the `IsNull` property.</span></span> <span data-ttu-id="74c62-145">我們可以清楚地看到，使用 `IS NULL` 將會呈現較佳的效能，因此絕對沒有理由要從 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼讀取 UDT 的 `IsNull` 屬性。</span><span class="sxs-lookup"><span data-stu-id="74c62-145">Clearly, using `IS NULL` will exhibit better performance and there should never be a reason to read the `IsNull` property of a UDT from [!INCLUDE[tsql](../../includes/tsql-md.md)] code.</span></span>  
  
 <span data-ttu-id="74c62-146">這樣為什麼要使用 `IsNull` 屬性呢？</span><span class="sxs-lookup"><span data-stu-id="74c62-146">So, what is the use of the `IsNull` property?</span></span> <span data-ttu-id="74c62-147">首先，需要用它來判斷來自 CLR 程式碼的某個值是否為 `Null`。</span><span class="sxs-lookup"><span data-stu-id="74c62-147">First, it is needed to determine whether a value is `Null` from within CLR code.</span></span> <span data-ttu-id="74c62-148">第二，伺服器需要一個方法來測試執行個體是否為 `Null`，所以伺服器會使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="74c62-148">Second, the server needs a way to test whether an instance is `Null`, so this property is used by the server.</span></span> <span data-ttu-id="74c62-149">當判斷出這個屬性為 `Null` 之後，它就可以使用它的原生 null 處理來加以處理。</span><span class="sxs-lookup"><span data-stu-id="74c62-149">After it determines it is `Null`, then it can use its native null handling to handle it.</span></span>  
  
## <a name="implementing-the-parse-method"></a><span data-ttu-id="74c62-150">實作 Parse 方法</span><span class="sxs-lookup"><span data-stu-id="74c62-150">Implementing the Parse Method</span></span>  
 <span data-ttu-id="74c62-151">`Parse` 及 `ToString` 方法允許與 UDT 的字串表示之間進行來回轉換。</span><span class="sxs-lookup"><span data-stu-id="74c62-151">The `Parse` and `ToString` methods allow for conversions to and from string representations of the UDT.</span></span> <span data-ttu-id="74c62-152">`Parse` 方法允許將字串轉換成 UDT。</span><span class="sxs-lookup"><span data-stu-id="74c62-152">The `Parse` method allows a string to be converted into a UDT.</span></span> <span data-ttu-id="74c62-153">它必須宣告為 `static` (或 Visual Basic 中的 `Shared`)，並採用型別 `System.Data.SqlTypes.SqlString` 的參數。</span><span class="sxs-lookup"><span data-stu-id="74c62-153">It must be declared as `static` (or `Shared` in Visual Basic), and take a parameter of type `System.Data.SqlTypes.SqlString`.</span></span>  
  
 <span data-ttu-id="74c62-154">下列程式碼會實作 `Parse` UDT 的 `Point` 方法，這樣會分隔 X 和 Y 座標。</span><span class="sxs-lookup"><span data-stu-id="74c62-154">The following code implements the `Parse` method for the `Point` UDT, which separates out the X and Y coordinates.</span></span> <span data-ttu-id="74c62-155">`Parse` 方法具有 `System.Data.SqlTypes.SqlString` 類型的單一引數，而且假設會以逗號分隔的字串來提供 X 和 Y 值。</span><span class="sxs-lookup"><span data-stu-id="74c62-155">The `Parse` method has a single argument of type `System.Data.SqlTypes.SqlString`, and assumes that X and Y values are supplied as a comma-delimited string.</span></span> <span data-ttu-id="74c62-156">將 `Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall` 屬性設定為 `false` 會避免從 Point 的 Null 執行個體呼叫 `Parse` 方法。</span><span class="sxs-lookup"><span data-stu-id="74c62-156">Setting the `Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall` attribute to `false` prevents the `Parse` method from being called from a null instance of Point.</span></span>  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
    return pt;  
}  
```  
  
## <a name="implementing-the-tostring-method"></a><span data-ttu-id="74c62-157">實作 ToString 方法</span><span class="sxs-lookup"><span data-stu-id="74c62-157">Implementing the ToString Method</span></span>  
 <span data-ttu-id="74c62-158">`ToString` 方法會將 `Point` UDT 轉換成字串值。</span><span class="sxs-lookup"><span data-stu-id="74c62-158">The `ToString` method converts the `Point` UDT to a string value.</span></span> <span data-ttu-id="74c62-159">在此情況下，會針對 `Point` 類型的 Null 執行個體傳回 "NULL" 字串。</span><span class="sxs-lookup"><span data-stu-id="74c62-159">In this case, the string "NULL" is returned for a Null instance of the `Point` type.</span></span> <span data-ttu-id="74c62-160">`ToString` 方法藉由使用 `Parse` 傳回以逗號分隔並包含 X 及 Y 座標值的 `System.Text.StringBuilder`，以反轉 `System.String` 方法。</span><span class="sxs-lookup"><span data-stu-id="74c62-160">The `ToString` method reverses the `Parse` method by using a `System.Text.StringBuilder` to return a comma-delimited `System.String` consisting of the X and Y coordinate values.</span></span> <span data-ttu-id="74c62-161">因為**InvokeIfReceiverIsNull**預設為 false，所以不需要檢查的 null 實例 `Point` 。</span><span class="sxs-lookup"><span data-stu-id="74c62-161">Because **InvokeIfReceiverIsNull** defaults to false, the check for a null instance of `Point` is unnecessary.</span></span>  
  
```vb  
Private _x As Int32  
Private _y As Int32  
  
Public Overrides Function ToString() As String  
    If Me.IsNull Then  
        Return "NULL"  
    Else  
        Dim builder As StringBuilder = New StringBuilder  
        builder.Append(_x)  
        builder.Append(",")  
        builder.Append(_y)  
        Return builder.ToString  
    End If  
End Function  
```  
  
```csharp  
private Int32 _x;  
private Int32 _y;  
  
public override string ToString()  
{  
    if (this.IsNull)  
        return "NULL";  
    else  
    {  
        StringBuilder builder = new StringBuilder();  
        builder.Append(_x);  
        builder.Append(",");  
        builder.Append(_y);  
        return builder.ToString();  
    }  
}  
```  
  
## <a name="exposing-udt-properties"></a><span data-ttu-id="74c62-162">公開 UDT 屬性</span><span class="sxs-lookup"><span data-stu-id="74c62-162">Exposing UDT Properties</span></span>  
 <span data-ttu-id="74c62-163">`Point` UDT 會公開實作為 `System.Int32` 類型之公用讀寫屬性的 X 及 Y 座標。</span><span class="sxs-lookup"><span data-stu-id="74c62-163">The `Point` UDT exposes X and Y coordinates that are implemented as public read-write properties of type `System.Int32`.</span></span>  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _x = Value  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _y = Value  
    End Set  
End Property  
```  
  
```csharp  
public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    set   
    {  
        _x = value;  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        _y = value;  
    }  
}  
```  
  
## <a name="validating-udt-values"></a><span data-ttu-id="74c62-164">驗證 UDT 值</span><span class="sxs-lookup"><span data-stu-id="74c62-164">Validating UDT Values</span></span>  
 <span data-ttu-id="74c62-165">當使用 UDT 資料時，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 會自動將二進位值轉換成 UDT 值。</span><span class="sxs-lookup"><span data-stu-id="74c62-165">When working with UDT data, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] automatically converts binary values to UDT values.</span></span> <span data-ttu-id="74c62-166">此轉換程序包括檢查適用於此類型之序列化格式的值，並確保可正確地將此值還原序列化。</span><span class="sxs-lookup"><span data-stu-id="74c62-166">This conversion process involves checking that values are appropriate for the serialization format of the type and ensuring that the value can be deserialized correctly.</span></span> <span data-ttu-id="74c62-167">如此可確保此值可以轉換回二進位格式。</span><span class="sxs-lookup"><span data-stu-id="74c62-167">This ensures that the value can be converted back to binary form.</span></span> <span data-ttu-id="74c62-168">如果是依照位元組排序的 UDT，這也可確保產生的二進位值會符合原始二進位值。</span><span class="sxs-lookup"><span data-stu-id="74c62-168">In the case of byte-ordered UDTs, this also ensures that the resulting binary value matches the original binary value.</span></span> <span data-ttu-id="74c62-169">如此可防止在資料庫中保留無效的值。</span><span class="sxs-lookup"><span data-stu-id="74c62-169">This prevents invalid values from being persisted in the database.</span></span> <span data-ttu-id="74c62-170">在某些情況下，這個層級的檢查可能不夠。</span><span class="sxs-lookup"><span data-stu-id="74c62-170">In some cases, this level of checking may be inadequate.</span></span> <span data-ttu-id="74c62-171">當要求 UDT 值位於預期的網域或範圍內時，可能需要其他驗證。</span><span class="sxs-lookup"><span data-stu-id="74c62-171">Additional validation may be required when UDT values are required to be in an expected domain or range.</span></span> <span data-ttu-id="74c62-172">例如，實作日期的 UDT 可能會要求日期值是一個正數，而且在某個有效值的範圍內。</span><span class="sxs-lookup"><span data-stu-id="74c62-172">For example, a UDT that implements a date might require the day value to be a positive number that falls within a certain range of valid values.</span></span>  
  
 <span data-ttu-id="74c62-173">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName` 的 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 屬性可在將資料指派給 UDT 或轉換成 UDT 時，讓您提供伺服器所執行之驗證方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="74c62-173">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName` property of the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` allows you to supply the name of a validation method that the server runs when data is assigned to a UDT or converted to a UDT.</span></span> <span data-ttu-id="74c62-174">在執行 bcp 公用程式、BULK INSERT、DBCC CHECKDB、DBCC CHECKFILEGROUP、DBCC CHECKTABLE、分散式查詢及表格式資料流 (TDS) 遠端程序呼叫 (RPC) 作業期間，也會呼叫 `ValidationMethodName`。</span><span class="sxs-lookup"><span data-stu-id="74c62-174">`ValidationMethodName` is also called during the running of the bcp utility, BULK INSERT, DBCC CHECKDB, DBCC CHECKFILEGROUP, DBCC CHECKTABLE, distributed query, and tabular data stream (TDS) remote procedure call (RPC) operations.</span></span> <span data-ttu-id="74c62-175">`ValidationMethodName` 的預設值是 null，表示沒有驗證方法。</span><span class="sxs-lookup"><span data-stu-id="74c62-175">The default value for `ValidationMethodName` is null, indicating that there is no validation method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="74c62-176">範例</span><span class="sxs-lookup"><span data-stu-id="74c62-176">Example</span></span>  
 <span data-ttu-id="74c62-177">下列程式碼片段顯示 `Point` 類別的宣告，該類別會指定 `ValidationMethodName` 的 `ValidatePoint`。</span><span class="sxs-lookup"><span data-stu-id="74c62-177">The following code fragment shows the declaration for the `Point` class, which specifies a `ValidationMethodName` of `ValidatePoint`.</span></span>  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True, _  
  ValidationMethodName:="ValidatePoint")> _  
  Public Structure Point  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true,   
  ValidationMethodName = "ValidatePoint")]  
public struct Point : INullable  
{  
```  
  
 <span data-ttu-id="74c62-178">如果已指定驗證方法，它必須具有類似以下程式碼片段的簽章。</span><span class="sxs-lookup"><span data-stu-id="74c62-178">If a validation method is specified, it must have a signature that looks like the following code fragment.</span></span>  
  
```vb  
Private Function ValidationFunction() As Boolean  
    If (validation logic here) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidationFunction()  
{  
    if (validation logic here)  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
 <span data-ttu-id="74c62-179">此驗證方法可以有任何範圍，而且應該在值為有效時傳回 `true`，否則會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="74c62-179">The validation method can have any scope and should return `true` if the value is valid, and `false` otherwise.</span></span> <span data-ttu-id="74c62-180">如果此方法傳回 `false` 或擲回例外狀況，則該值會被視為無效，並引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="74c62-180">If the method returns `false` or throws an exception, the value is treated as not valid and an error is raised.</span></span>  
  
 <span data-ttu-id="74c62-181">在以下範例中，程式碼只允許零值或大於 X 及 Y 座標的值。</span><span class="sxs-lookup"><span data-stu-id="74c62-181">In the example below, the code allows only values of zero or greater the X and Y coordinates.</span></span>  
  
```vb  
Private Function ValidatePoint() As Boolean  
    If (_x >= 0) And (_y >= 0) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidatePoint()  
{  
    if ((_x >= 0) && (_y >= 0))  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
### <a name="validation-method-limitations"></a><span data-ttu-id="74c62-182">驗證方法限制</span><span class="sxs-lookup"><span data-stu-id="74c62-182">Validation Method Limitations</span></span>  
 <span data-ttu-id="74c62-183">伺服器呼叫此驗證方法的時機是當伺服器執行轉換時，而不是當藉由設定個別屬性插入資料，或使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT 陳述式插入資料時。</span><span class="sxs-lookup"><span data-stu-id="74c62-183">The server calls the validation method when the server is performing conversions, not when data is inserted by setting individual properties or when data is inserted using a [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT statement.</span></span>  
  
 <span data-ttu-id="74c62-184">`Parse`如果您想要在所有情況下執行驗證方法，您必須從屬性 setter 和方法明確呼叫驗證方法。</span><span class="sxs-lookup"><span data-stu-id="74c62-184">You must explicitly call the validation method from property setters and the `Parse` method if you want the validation method to execute in all situations.</span></span> <span data-ttu-id="74c62-185">這不是硬性規定，在某些情況下可能也不適當。</span><span class="sxs-lookup"><span data-stu-id="74c62-185">This is not a requirement, and in some cases may not even be desirable.</span></span>  
  
### <a name="parse-validation-example"></a><span data-ttu-id="74c62-186">Parse 驗證範例</span><span class="sxs-lookup"><span data-stu-id="74c62-186">Parse Validation Example</span></span>  
 <span data-ttu-id="74c62-187">若要確保 `ValidatePoint` 方法是在 `Point` 類別中叫用，您必須從 `Parse` 方法和設定 X 和 Y 座標值的屬性程式呼叫它。</span><span class="sxs-lookup"><span data-stu-id="74c62-187">To ensure that the `ValidatePoint` method is invoked in the `Point` class, you must call it from the `Parse` method and from the property procedures that set the X and Y coordinate values.</span></span> <span data-ttu-id="74c62-188">下列程式碼片段顯示如何從函式呼叫 `ValidatePoint` 驗證方法 `Parse` 。</span><span class="sxs-lookup"><span data-stu-id="74c62-188">The following code fragment shows how to call the `ValidatePoint` validation method from the `Parse` function.</span></span>  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
  
    ' Call ValidatePoint to enforce validation  
    ' for string conversions.  
    If Not pt.ValidatePoint() Then  
        Throw New ArgumentException("Invalid XY coordinate values.")  
    End If  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
  
    // Call ValidatePoint to enforce validation  
    // for string conversions.  
    if (!pt.ValidatePoint())   
        throw new ArgumentException("Invalid XY coordinate values.");  
    return pt;  
}  
```  
  
### <a name="property-validation-example"></a><span data-ttu-id="74c62-189">Property 驗證範例</span><span class="sxs-lookup"><span data-stu-id="74c62-189">Property Validation Example</span></span>  
 <span data-ttu-id="74c62-190">下列程式碼片段顯示如何 `ValidatePoint` 從設定 X 和 Y 座標的屬性程式呼叫驗證方法。</span><span class="sxs-lookup"><span data-stu-id="74c62-190">The following code fragment shows how to call the `ValidatePoint` validation method from the property procedures that set the X and Y coordinates.</span></span>  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _x  
        _x = Value  
        If Not ValidatePoint() Then  
            _x = temp  
            Throw New ArgumentException("Invalid X coordinate value.")  
        End If  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _y  
        _y = Value  
        If Not ValidatePoint() Then  
            _y = temp  
            Throw New ArgumentException("Invalid Y coordinate value.")  
        End If  
    End Set  
End Property  
```  
  
```csharp  
    public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    // Call ValidatePoint to ensure valid range of Point values.  
    set   
    {  
        Int32 temp = _x;  
        _x = value;  
        if (!ValidatePoint())  
        {  
            _x = temp;  
            throw new ArgumentException("Invalid X coordinate value.");  
        }  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        Int32 temp = _y;  
        _y = value;  
        if (!ValidatePoint())  
        {  
            _y = temp;  
            throw new ArgumentException("Invalid Y coordinate value.");  
        }  
    }  
}  
```  
  
## <a name="coding-udt-methods"></a><span data-ttu-id="74c62-191">編碼 UDT 方法</span><span class="sxs-lookup"><span data-stu-id="74c62-191">Coding UDT Methods</span></span>  
 <span data-ttu-id="74c62-192">當編碼 UDT 方法時，請考慮使用的演算法是否可能隨著時間而改變。</span><span class="sxs-lookup"><span data-stu-id="74c62-192">When coding UDT methods, consider whether the algorithm used could possibly change over time.</span></span> <span data-ttu-id="74c62-193">如果會的話，您可能會想要考慮針對 UDT 使用的方法建立個別類別。</span><span class="sxs-lookup"><span data-stu-id="74c62-193">If so, you may want to consider creating a separate class for the methods your UDT uses.</span></span> <span data-ttu-id="74c62-194">如果演算法變更，您可在不影響 UDT 的情況下，以新的程式碼重新編譯該類別，並將組件載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="74c62-194">If the algorithm changes, you can recompile the class with the new code and load the assembly into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without affecting the UDT.</span></span> <span data-ttu-id="74c62-195">在許多情況下，您可使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY 陳述式重新載入 UDT，但是這樣做可能會導致現有資料發生問題。</span><span class="sxs-lookup"><span data-stu-id="74c62-195">In many cases UDTs can be reloaded using the [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement, but that could potentially cause problems with existing data.</span></span> <span data-ttu-id="74c62-196">例如，包含在 `Currency` **AdventureWorks**範例資料庫中的 UDT 會使用**ConvertCurrency**函數來轉換貨幣值，這會在不同的類別中執行。</span><span class="sxs-lookup"><span data-stu-id="74c62-196">For example, the `Currency` UDT included with the **AdventureWorks** sample database uses a **ConvertCurrency** function to convert currency values, which is implemented in a separate class.</span></span> <span data-ttu-id="74c62-197">轉換演算法在未來有可能以非預期的方式變更，或者可能需要新的功能。</span><span class="sxs-lookup"><span data-stu-id="74c62-197">It is possible that conversion algorithms may change in unpredictable ways in the future, or that new functionality may be required.</span></span> <span data-ttu-id="74c62-198">在規劃未來的變更時，將**ConvertCurrency**函數與 UDT 的執行區隔開， `Currency` 可提供更大的彈性。</span><span class="sxs-lookup"><span data-stu-id="74c62-198">Separating the **ConvertCurrency** function from the `Currency` UDT implementation provides greater flexibility when planning for future changes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="74c62-199">範例</span><span class="sxs-lookup"><span data-stu-id="74c62-199">Example</span></span>  
 <span data-ttu-id="74c62-200">`Point`類別包含三個簡單的方法來計算距離：**距離**、 **DistanceFrom**和**DistanceFromXY**。</span><span class="sxs-lookup"><span data-stu-id="74c62-200">The `Point` class contains three simple methods for calculating distance: **Distance**, **DistanceFrom** and **DistanceFromXY**.</span></span> <span data-ttu-id="74c62-201">每一個方法都會傳回 `double`，計算從 `Point` 到零的距離、從指定點到 `Point` 的距離，以及從指定之 X 及 Y 座標到 `Point` 的距離。</span><span class="sxs-lookup"><span data-stu-id="74c62-201">Each returns a `double` calculating the distance from `Point` to zero, the distance from a specified point to `Point`, and the distance from specified X and Y coordinates to `Point`.</span></span> <span data-ttu-id="74c62-202">**距離**和**DistanceFrom**每個呼叫**DistanceFromXY**，並示範如何針對每個方法使用不同的引數。</span><span class="sxs-lookup"><span data-stu-id="74c62-202">**Distance** and **DistanceFrom** each call **DistanceFromXY**, and demonstrate how to use different arguments for each method.</span></span>  
  
```vb  
' Distance from 0 to Point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function Distance() As Double  
    Return DistanceFromXY(0, 0)  
End Function  
  
' Distance from Point to the specified point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFrom(ByVal pFrom As Point) As Double  
    Return DistanceFromXY(pFrom.X, pFrom.Y)  
End Function  
  
' Distance from Point to the specified x and y values.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFromXY(ByVal ix As Int32, ByVal iy As Int32) _  
    As Double  
    Return Math.Sqrt(Math.Pow(ix - _x, 2.0) + Math.Pow(iy - _y, 2.0))  
End Function  
```  
  
```csharp  
// Distance from 0 to Point.  
[SqlMethod(OnNullCall = false)]  
public Double Distance()  
{  
    return DistanceFromXY(0, 0);  
}  
  
// Distance from Point to the specified point.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFrom(Point pFrom)  
{  
    return DistanceFromXY(pFrom.X, pFrom.Y);  
}  
  
// Distance from Point to the specified x and y values.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFromXY(Int32 iX, Int32 iY)  
{  
    return Math.Sqrt(Math.Pow(iX - _x, 2.0) + Math.Pow(iY - _y, 2.0));  
}  
```  
  
### <a name="using-sqlmethod-attributes"></a><span data-ttu-id="74c62-203">使用 SqlMethod 屬性</span><span class="sxs-lookup"><span data-stu-id="74c62-203">Using SqlMethod Attributes</span></span>  
 <span data-ttu-id="74c62-204">`Microsoft.SqlServer.Server.SqlMethodAttribute` 類別會提供可用來標示方法定義的自訂屬性，以便針對 Null 呼叫行為指定決定性以及指定方法是否為 mutator。</span><span class="sxs-lookup"><span data-stu-id="74c62-204">The `Microsoft.SqlServer.Server.SqlMethodAttribute` class provides custom attributes that can be used to mark method definitions in order to specify determinism, on null call behavior, and to specify whether a method is a mutator.</span></span> <span data-ttu-id="74c62-205">已假設這些屬性 (Property) 的預設值，而且只有在需要非預設值時才會使用自訂屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="74c62-205">Default values for these properties are assumed, and the custom attribute is only used when a non-default value is needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="74c62-206">`SqlMethodAttribute` 類別繼承自 `SqlFunctionAttribute` 類別，因此 `SqlMethodAttribute` 會繼承自 `FillRowMethodName` 而 `TableDefinition` 欄位會繼承自 `SqlFunctionAttribute`。</span><span class="sxs-lookup"><span data-stu-id="74c62-206">The `SqlMethodAttribute` class inherits from the `SqlFunctionAttribute` class, so `SqlMethodAttribute` inherits the `FillRowMethodName` and `TableDefinition` fields from `SqlFunctionAttribute`.</span></span> <span data-ttu-id="74c62-207">這意味著撰寫資料表值方法是可行的，不過情況不是這樣。</span><span class="sxs-lookup"><span data-stu-id="74c62-207">This implies that it is possible to write a table-valued method, which is not the case.</span></span> <span data-ttu-id="74c62-208">方法會編譯和元件部署，但在執行時間會引發有關傳回類型的錯誤，並 `IEnumerable` 出現下列訊息：「方法、屬性或 \<name> 元件 ' ' 中類別 ' ' 的欄位 ' ' \<class> 有不正確傳回 \<assembly> 類型。」</span><span class="sxs-lookup"><span data-stu-id="74c62-208">The method compiles and the assembly deploys, but an error about the `IEnumerable` return type is raised at runtime with the following message: "Method, property, or field '\<name>' in class '\<class>' in assembly '\<assembly>' has invalid return type."</span></span>  
  
 <span data-ttu-id="74c62-209">下表說明可在 UDT 方法中使用的部分相關 `Microsoft.SqlServer.Server.SqlMethodAttribute` 屬性，並列出其預設值。</span><span class="sxs-lookup"><span data-stu-id="74c62-209">The following table describes some of the relevant `Microsoft.SqlServer.Server.SqlMethodAttribute` properties that can be used in UDT methods, and lists their default values.</span></span>  
  
 <span data-ttu-id="74c62-210">DataAccess</span><span class="sxs-lookup"><span data-stu-id="74c62-210">DataAccess</span></span>  
 <span data-ttu-id="74c62-211">指出此函數是否包含對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本機執行個體中儲存之使用者資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="74c62-211">Indicates whether the function involves access to user data stored in the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="74c62-212">預設值是 `DataAccessKind`.`None`。</span><span class="sxs-lookup"><span data-stu-id="74c62-212">Default is `DataAccessKind`.`None`.</span></span>  
  
 <span data-ttu-id="74c62-213">IsDeterministic</span><span class="sxs-lookup"><span data-stu-id="74c62-213">IsDeterministic</span></span>  
 <span data-ttu-id="74c62-214">指出如果輸入值及資料庫狀態都相同，此函數是否會產生相同的輸出值。</span><span class="sxs-lookup"><span data-stu-id="74c62-214">Indicates whether the function produces the same output values given the same input values and the same database state.</span></span> <span data-ttu-id="74c62-215">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="74c62-215">Default is `false`.</span></span>  
  
 <span data-ttu-id="74c62-216">IsMutator</span><span class="sxs-lookup"><span data-stu-id="74c62-216">IsMutator</span></span>  
 <span data-ttu-id="74c62-217">指出此方法是否會導致 UDT 執行個體的狀態變更。</span><span class="sxs-lookup"><span data-stu-id="74c62-217">Indicates whether the method causes a state change in the UDT instance.</span></span> <span data-ttu-id="74c62-218">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="74c62-218">Default is `false`.</span></span>  
  
 <span data-ttu-id="74c62-219">IsPrecise</span><span class="sxs-lookup"><span data-stu-id="74c62-219">IsPrecise</span></span>  
 <span data-ttu-id="74c62-220">指出此函數是否包含不精確的計算，如浮點運算。</span><span class="sxs-lookup"><span data-stu-id="74c62-220">Indicates whether the function involves imprecise computations, such as floating point operations.</span></span> <span data-ttu-id="74c62-221">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="74c62-221">Default is `false`.</span></span>  
  
 <span data-ttu-id="74c62-222">OnNullCall</span><span class="sxs-lookup"><span data-stu-id="74c62-222">OnNullCall</span></span>  
 <span data-ttu-id="74c62-223">指出當指定 Null 參考輸入引數時，是否呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="74c62-223">Indicates whether the method is called when null reference input arguments are specified.</span></span> <span data-ttu-id="74c62-224">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="74c62-224">Default is `true`.</span></span>  
  
### <a name="example"></a><span data-ttu-id="74c62-225">範例</span><span class="sxs-lookup"><span data-stu-id="74c62-225">Example</span></span>  
 <span data-ttu-id="74c62-226">`Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator` 屬性可讓您將方法標示為允許 UDT 執行個體的狀態變更。</span><span class="sxs-lookup"><span data-stu-id="74c62-226">The `Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator` property allows you to mark a method that allows a change in the state of an instance of a UDT.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="74c62-227">不允許您在一個 UPDATE 陳述式的 SET 子句中，設定兩個 UDT 屬性。</span><span class="sxs-lookup"><span data-stu-id="74c62-227">does not allow you to set two UDT properties in the SET clause of one UPDATE statement.</span></span> <span data-ttu-id="74c62-228">但是，您可以將方法標示為 mutator，這樣會變更兩個成員。</span><span class="sxs-lookup"><span data-stu-id="74c62-228">However, you can have a method marked as a mutator that changes the two members.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="74c62-229">查詢中不允許使用 Mutator 方法。</span><span class="sxs-lookup"><span data-stu-id="74c62-229">Mutator methods are not allowed in queries.</span></span> <span data-ttu-id="74c62-230">它們只能在指派陳述式或資料修改陳述式中呼叫。</span><span class="sxs-lookup"><span data-stu-id="74c62-230">They can be called only in assignment statements or data modification statements.</span></span> <span data-ttu-id="74c62-231">如果標示為 mutator 的方法未傳回 `void` (或是 Visual Basic 中的 `Sub`)，CREATE TYPE 會失敗且發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="74c62-231">If a method marked as mutator does not return `void` (or is not a `Sub` in Visual Basic), CREATE TYPE fails with an error.</span></span>  
  
 <span data-ttu-id="74c62-232">下列陳述式假設存在著具有 `Triangles` 方法的 `Rotate` UDT。</span><span class="sxs-lookup"><span data-stu-id="74c62-232">The following statement assumes the existence of a `Triangles` UDT that has a `Rotate` method.</span></span> <span data-ttu-id="74c62-233">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE 陳述式會叫用 `Rotate` 方法：</span><span class="sxs-lookup"><span data-stu-id="74c62-233">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] update statement invokes the `Rotate` method:</span></span>  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 <span data-ttu-id="74c62-234">`Rotate` 方法是以將 `SqlMethod` 設為 `IsMutator` 的 `true` 屬性來裝飾的，以便 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以將方法標示為 Mutator 方法。</span><span class="sxs-lookup"><span data-stu-id="74c62-234">The `Rotate` method is decorated with the `SqlMethod` attribute setting `IsMutator` to `true` so that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can mark the method as a mutator method.</span></span> <span data-ttu-id="74c62-235">該程式碼還將 `OnNullCall` 設為 `false`，如此可向伺服器指出，如果任何輸入參數為 Null 參考，則該方法會傳回 Null 參考 (Visual Basic 中則為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="74c62-235">The code also sets `OnNullCall` to `false`, which indicates to the server that the method returns a null reference (`Nothing` in Visual Basic) if any of the input parameters are null references.</span></span>  
  
```vb  
<SqlMethod(IsMutator:=True, OnNullCall:=False)> _  
Public Sub Rotate(ByVal anglex as Double, _  
  ByVal angley as Double, ByVal anglez As Double)   
   RotateX(anglex)  
   RotateY(angley)  
   RotateZ(anglez)  
End Sub  
```  
  
```csharp  
[SqlMethod(IsMutator = true, OnNullCall = false)]  
public void Rotate(double anglex, double angley, double anglez)   
{  
   RotateX(anglex);  
   RotateY(angley);  
   RotateZ(anglez);  
}  
```  
  
## <a name="implementing-a-udt-with-a-user-defined-format"></a><span data-ttu-id="74c62-236">以使用者定義的格式實作 UDT</span><span class="sxs-lookup"><span data-stu-id="74c62-236">Implementing a UDT with a User-Defined Format</span></span>  
 <span data-ttu-id="74c62-237">以使用者定義的格式實作 UDT 時，您必須實作可將 Microsoft.SqlServer.Server.IBinarySerialize 介面實作為處理序列化及還原序列化 UDT 資料的 `Read` 及 `Write` 方法。</span><span class="sxs-lookup"><span data-stu-id="74c62-237">When implementing a UDT with a user-defined format, you must implement `Read` and `Write` methods that implement the Microsoft.SqlServer.Server.IBinarySerialize interface to handle serializing and deserializing UDT data.</span></span> <span data-ttu-id="74c62-238">您也必須指定 `MaxByteSize` 的 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 屬性。</span><span class="sxs-lookup"><span data-stu-id="74c62-238">You must also specify the `MaxByteSize` property of the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`.</span></span>  
  
### <a name="the-currency-udt"></a><span data-ttu-id="74c62-239">Currency UDT</span><span class="sxs-lookup"><span data-stu-id="74c62-239">The Currency UDT</span></span>  
 <span data-ttu-id="74c62-240">`Currency` UDT 隨附在 CLR 範例中，這些範例從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 開始就可以與 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="74c62-240">The `Currency` UDT is included with the CLR samples that can be installed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="74c62-241">`Currency` UDT 支援在特定文化特性的貨幣系統中處理貨幣金額。</span><span class="sxs-lookup"><span data-stu-id="74c62-241">The `Currency` UDT supports handling amounts of money in the monetary system of a particular culture.</span></span> <span data-ttu-id="74c62-242">您必須定義兩個欄位：針對 `string` 定義 `CultureInfo` (指定發行貨幣的一方，例如 en-us)，以及針對 `decimal` 定義 `CurrencyValue` (貨幣金額)。</span><span class="sxs-lookup"><span data-stu-id="74c62-242">You must define two fields: a `string` for `CultureInfo`, which specifies who issued the currency (en-us, for example) and a `decimal` for `CurrencyValue`, the amount of money.</span></span>  
  
 <span data-ttu-id="74c62-243">雖然伺服器不會用它來執行比較，但是 `Currency` UDT 會實作 `System.IComparable` 介面，而此介面會公開單一方法 `System.IComparable.CompareTo`。</span><span class="sxs-lookup"><span data-stu-id="74c62-243">Although it is not used by the server for performing comparisons, the `Currency` UDT implements the `System.IComparable` interface, which exposes a single method, `System.IComparable.CompareTo`.</span></span> <span data-ttu-id="74c62-244">這會在用戶端上使用，此時需要正確地比較或排序文化特性中的貨幣值。</span><span class="sxs-lookup"><span data-stu-id="74c62-244">This is used on the client side in situations where it is desirable to accurately compare or order currency values within cultures.</span></span>  
  
 <span data-ttu-id="74c62-245">在 CLR 上執行的程式碼會對貨幣值與文化特性分別進行比較。</span><span class="sxs-lookup"><span data-stu-id="74c62-245">Code running in the CLR compares the culture separately from the currency value.</span></span> <span data-ttu-id="74c62-246">如果是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，下列動作會決定比較：</span><span class="sxs-lookup"><span data-stu-id="74c62-246">For [!INCLUDE[tsql](../../includes/tsql-md.md)] code, the following actions determine the comparison:</span></span>  
  
1.  <span data-ttu-id="74c62-247">將 `IsByteOrdered` 屬性設為 True，告知 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用磁碟上保存的二進位表示進行比較。</span><span class="sxs-lookup"><span data-stu-id="74c62-247">Set the `IsByteOrdered` attribute to true, which tells [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use the persisted binary representation on disk for comparisons.</span></span>  
  
2.  <span data-ttu-id="74c62-248">針對 `Write` UDT 使用 `Currency` 方法，以判斷如何在磁碟上保存 UDT，以及如何針對 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作業來比較及排序 UDT 值。</span><span class="sxs-lookup"><span data-stu-id="74c62-248">Use the `Write` method for the `Currency` UDT to determine how the UDT is persisted on disk and therefore how UDT values are compared and ordered for [!INCLUDE[tsql](../../includes/tsql-md.md)] operations.</span></span>  
  
3.  <span data-ttu-id="74c62-249">使用下列二進位格式，儲存 `Currency` UDT：</span><span class="sxs-lookup"><span data-stu-id="74c62-249">Save the `Currency` UDT using the following binary format:</span></span>  
  
    1.  <span data-ttu-id="74c62-250">針對位元組 0-19 將文化特性儲存為 UTF-16 編碼的字串，並使用 null 字元填補到右邊。</span><span class="sxs-lookup"><span data-stu-id="74c62-250">Save the culture as a UTF-16 encoded string for bytes 0-19 with padding to the right with null characters.</span></span>  
  
    2.  <span data-ttu-id="74c62-251">使用位元組 20 以上 (含) 來包含貨幣的十進位值。</span><span class="sxs-lookup"><span data-stu-id="74c62-251">Use bytes 20 and above to contain the decimal value of the currency.</span></span>  
  
 <span data-ttu-id="74c62-252">填補的目的是確保文化特性與貨幣值完全分開，以便在將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼中的一個 UDT 與另一 UDT 進行比較時，會將文化特性位元組與文化特性位元組進行比較，並將貨幣位元組值與貨幣位元組值進行比較。</span><span class="sxs-lookup"><span data-stu-id="74c62-252">The purpose of the padding is to ensure that the culture is completely separated from the currency value, so that when one UDT is compared against another in [!INCLUDE[tsql](../../includes/tsql-md.md)] code, culture bytes are compared against culture bytes, and currency byte values are compared against currency byte values.</span></span>  
  
 <span data-ttu-id="74c62-253">如需 UDT 的完整程式代碼清單 `Currency` ，請遵循在[SQL Server 資料庫引擎範例](https://msftengprodsamples.codeplex.com/)中安裝 CLR 範例的指示。</span><span class="sxs-lookup"><span data-stu-id="74c62-253">For the complete code listing for the `Currency` UDT, follow the directions for installing the CLR samples in [SQL Server Database Engine Samples](https://msftengprodsamples.codeplex.com/).</span></span>  
  
### <a name="currency-attributes"></a><span data-ttu-id="74c62-254">Currency 屬性</span><span class="sxs-lookup"><span data-stu-id="74c62-254">Currency Attributes</span></span>  
 <span data-ttu-id="74c62-255">使用下列屬性定義 `Currency` UDT。</span><span class="sxs-lookup"><span data-stu-id="74c62-255">The `Currency` UDT is defined with the following attributes.</span></span>  
  
```vb  
<Serializable(), Microsoft.SqlServer.Server.SqlUserDefinedType( _  
    Microsoft.SqlServer.Server.Format.UserDefined, _  
    IsByteOrdered:=True, MaxByteSize:=32), _  
    CLSCompliant(False)> _  
Public Structure Currency  
Implements INullable, IComparable, _  
Microsoft.SqlServer.Server.IBinarySerialize  
```  
  
```csharp  
[Serializable]  
[SqlUserDefinedType(Format.UserDefined,   
    IsByteOrdered = true, MaxByteSize = 32)]  
    [CLSCompliant(false)]  
    public struct Currency : INullable, IComparable, IBinarySerialize  
    {  
```  
  
## <a name="creating-read-and-write-methods-with-ibinaryserialize"></a><span data-ttu-id="74c62-256">使用 IBinarySerialize 建立 Read 和 Write 方法</span><span class="sxs-lookup"><span data-stu-id="74c62-256">Creating Read and Write Methods with IBinarySerialize</span></span>  
 <span data-ttu-id="74c62-257">當您選擇 `UserDefined` 序列化格式時，您也必須實作 `IBinarySerialize` 介面，並建立您自己的 `Read` 和 `Write` 方法。</span><span class="sxs-lookup"><span data-stu-id="74c62-257">When you choose `UserDefined` serialization format, you also must implement the `IBinarySerialize` interface and create your own `Read` and `Write` methods.</span></span> <span data-ttu-id="74c62-258">下列來自 `Currency` UDT 的程序會使用 `System.IO.BinaryReader` 和 `System.IO.BinaryWriter`，從 UDT 讀取並寫入 UDT。</span><span class="sxs-lookup"><span data-stu-id="74c62-258">The following procedures from the `Currency` UDT use the `System.IO.BinaryReader` and `System.IO.BinaryWriter` to read from and write to the UDT.</span></span>  
  
```vb  
' IBinarySerialize methods  
' The binary layout is as follow:  
'    Bytes 0 - 19: Culture name, padded to the right with null  
'    characters, UTF-16 encoded  
'    Bytes 20+: Decimal value of money  
' If the culture name is empty, the currency is null.  
Public Sub Write(ByVal w As System.IO.BinaryWriter) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Write  
    If Me.IsNull Then  
        w.Write(nullMarker)  
        w.Write(System.Convert.ToDecimal(0))  
        Return  
    End If  
  
    If cultureName.Length > cultureNameMaxSize Then  
        Throw New ApplicationException(String.Format(CultureInfo.CurrentUICulture, _  
           "{0} is an invalid culture name for currency as it is too long.", cultureNameMaxSize))  
    End If  
  
    Dim paddedName As String = cultureName.PadRight(cultureNameMaxSize, CChar(vbNullChar))  
  
    For i As Integer = 0 To cultureNameMaxSize - 1  
        w.Write(paddedName(i))  
    Next i  
  
    ' Normalize decimal value to two places  
    currencyVal = Decimal.Floor(currencyVal * 100) / 100  
    w.Write(currencyVal)  
End Sub  
  
Public Sub Read(ByVal r As System.IO.BinaryReader) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Read  
    Dim name As Char() = r.ReadChars(cultureNameMaxSize)  
    Dim stringEnd As Integer = Array.IndexOf(name, CChar(vbNullChar))  
  
    If stringEnd = 0 Then  
        cultureName = Nothing  
        Return  
    End If  
  
    cultureName = New String(name, 0, stringEnd)  
    currencyVal = r.ReadDecimal()  
End Sub  
  
```  
  
```csharp  
// IBinarySerialize methods  
// The binary layout is as follow:  
//    Bytes 0 - 19:Culture name, padded to the right   
//    with null characters, UTF-16 encoded  
//    Bytes 20+:Decimal value of money  
// If the culture name is empty, the currency is null.  
public void Write(System.IO.BinaryWriter w)  
{  
    if (this.IsNull)  
    {  
        w.Write(nullMarker);  
        w.Write((decimal)0);  
        return;  
    }  
  
    if (cultureName.Length > cultureNameMaxSize)  
    {  
        throw new ApplicationException(string.Format(  
            CultureInfo.InvariantCulture,   
            "{0} is an invalid culture name for currency as it is too long.",   
            cultureNameMaxSize));  
    }  
  
    String paddedName = cultureName.PadRight(cultureNameMaxSize, '\0');  
    for (int i = 0; i < cultureNameMaxSize; i++)  
    {  
        w.Write(paddedName[i]);  
    }  
  
    // Normalize decimal value to two places  
    currencyValue = Decimal.Floor(currencyValue * 100) / 100;  
    w.Write(currencyValue);  
}  
public void Read(System.IO.BinaryReader r)  
{  
    char[] name = r.ReadChars(cultureNameMaxSize);  
    int stringEnd = Array.IndexOf(name, '\0');  
  
    if (stringEnd == 0)  
    {  
        cultureName = null;  
        return;  
    }  
  
    cultureName = new String(name, 0, stringEnd);  
    currencyValue = r.ReadDecimal();  
}  
```  
  
 <span data-ttu-id="74c62-259">如需 UDT 的完整程式代碼清單 `Currency` ，請參閱[SQL Server 資料庫引擎範例](https://msftengprodsamples.codeplex.com/)。</span><span class="sxs-lookup"><span data-stu-id="74c62-259">For the complete code listing for the `Currency` UDT, see [SQL Server Database Engine Samples](https://msftengprodsamples.codeplex.com/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c62-260">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74c62-260">See Also</span></span>  
 [<span data-ttu-id="74c62-261">建立使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="74c62-261">Creating a User-Defined Type</span></span>](creating-user-defined-types.md)  
  
