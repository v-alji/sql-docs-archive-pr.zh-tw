---
title: 使用者定義類型需求 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- UDTs [CLR integration], requirements
- serialization
- Native serialization format [CLR integration]
- attributes [CLR integration]
- XML serialization [CLR integration]
- user-defined types [CLR integration], requirements
- user-defined serialization [CLR integration]
- user-defined types [CLR integration], Native serialization
- UDTs [CLR integration], Native serialization
ms.assetid: bedc3372-50eb-40f2-bcf2-d6db6a63b7e6
author: rothja
ms.author: jroth
ms.openlocfilehash: d4e692a4523829713cd95daf62374f84a74b6584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592718"
---
# <a name="user-defined-type-requirements"></a><span data-ttu-id="aab9f-102">使用者定義型別需求</span><span class="sxs-lookup"><span data-stu-id="aab9f-102">User-Defined Type Requirements</span></span>
  <span data-ttu-id="aab9f-103">建立使用者定義型別時，您必須進行幾項重要的設計決策， (要安裝在中的 UDT) [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="aab9f-103">You must make several important design decisions when creating a user-defined type (UDT) to be installed in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="aab9f-104">對於大部分的 UDT 而言，雖然將 UDT 當做類別來建立也是一種選擇，但是建議將 UDT 當做結構來建立。</span><span class="sxs-lookup"><span data-stu-id="aab9f-104">For most UDTs, creating the UDT as a structure is recommended, although creating it as a class is also an option.</span></span> <span data-ttu-id="aab9f-105">UDT 定義必須符合建立 UDT 的規格，才能讓它使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 註冊。</span><span class="sxs-lookup"><span data-stu-id="aab9f-105">The UDT definition must conform to the specifications for creating UDTs in order for it to be registered with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="requirements-for-implementing-udts"></a><span data-ttu-id="aab9f-106">實作 UDT 的需求</span><span class="sxs-lookup"><span data-stu-id="aab9f-106">Requirements for Implementing UDTs</span></span>  
 <span data-ttu-id="aab9f-107">若要在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中執行，UDT 必須實作 UDT 定義中的下列需求：</span><span class="sxs-lookup"><span data-stu-id="aab9f-107">To run in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], your UDT must implement the following requirements in the UDT definition:</span></span>  
  
 <span data-ttu-id="aab9f-108">UDT 必須指定 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`。</span><span class="sxs-lookup"><span data-stu-id="aab9f-108">The UDT must specify the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`.</span></span> <span data-ttu-id="aab9f-109">雖然 `System.SerializableAttribute` 是選擇性使用的，但仍建議使用。</span><span class="sxs-lookup"><span data-stu-id="aab9f-109">The use of the `System.SerializableAttribute` is optional, but recommended.</span></span>  
  
-   <span data-ttu-id="aab9f-110">UDT 必須藉由建立公用 `System.Data.SqlTypes.INullable` ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 中為 `static`) `Shared` 方法，在類別或結構中實作 `Null` 介面。</span><span class="sxs-lookup"><span data-stu-id="aab9f-110">The UDT must implement the `System.Data.SqlTypes.INullable` interface in the class or structure by creating a public `static` (`Shared` in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic) `Null` method.</span></span> <span data-ttu-id="aab9f-111">依預設，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 能夠辨識 Null。</span><span class="sxs-lookup"><span data-stu-id="aab9f-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is null-aware by default.</span></span> <span data-ttu-id="aab9f-112">若要讓在 UDT 中執行的程式碼能夠辨識 Null 值，此為必要選項。</span><span class="sxs-lookup"><span data-stu-id="aab9f-112">This is necessary for code executing in the UDT to be able to recognize a null value.</span></span>  
  
-   <span data-ttu-id="aab9f-113">UDT 必須包含可支援從物件字串表示法進行剖析的公用 `static` (或 `Shared`) `Parse` 方法，以及轉換為物件字串表示法的公用 `ToString` 方法。</span><span class="sxs-lookup"><span data-stu-id="aab9f-113">The UDT must contain a public `static` (or `Shared`) `Parse` method that supports parsing from, and a public `ToString` method for converting to a string representation of the object.</span></span>  
  
-   <span data-ttu-id="aab9f-114">含有使用者定義序列化格式的 UDT 必須實作 `System.Data.IBinarySerialize` 介面，並提供 `Read` 和 `Write` 方法。</span><span class="sxs-lookup"><span data-stu-id="aab9f-114">A UDT with a user-defined serialization format must implement the `System.Data.IBinarySerialize` interface and provide a `Read` and a `Write` method.</span></span>  
  
-   <span data-ttu-id="aab9f-115">UDT 必須實作 `System.Xml.Serialization.IXmlSerializable`，或如果必須覆寫標準序列化，所有的公用欄位和屬性都必須屬於可 XML 序列化或可使用 `XmlIgnore` 屬性來修飾的類型。</span><span class="sxs-lookup"><span data-stu-id="aab9f-115">The UDT must implement `System.Xml.Serialization.IXmlSerializable`, or all public fields and properties must be of types that are XML serializable or decorated with the `XmlIgnore` attribute if overriding standard serialization is required.</span></span>  
  
-   <span data-ttu-id="aab9f-116">一個 UDT 物件必須僅有一個序列化。</span><span class="sxs-lookup"><span data-stu-id="aab9f-116">There must be only one serialization of a UDT object.</span></span> <span data-ttu-id="aab9f-117">如果序列化或還原序列化常式識別一個以上的特定物件表示法，則驗證會失敗。</span><span class="sxs-lookup"><span data-stu-id="aab9f-117">Validation fails if the serialize or deserialize routines recognize more than one representation of a particular object.</span></span>  
  
-   <span data-ttu-id="aab9f-118">`SqlUserDefinedTypeAttribute.IsByteOrdered` 必須是 `true`，才能按照位元組順序比較資料。</span><span class="sxs-lookup"><span data-stu-id="aab9f-118">`SqlUserDefinedTypeAttribute.IsByteOrdered` must be `true` to compare data in byte order.</span></span> <span data-ttu-id="aab9f-119">如果沒有實作 IComparable 介面，而且 `SqlUserDefinedTypeAttribute.IsByteOrdered` 是 `false`，位元組順序比較就會失敗。</span><span class="sxs-lookup"><span data-stu-id="aab9f-119">If the IComparable interface is not implemented and `SqlUserDefinedTypeAttribute.IsByteOrdered` is `false`, byte order comparisons will fail.</span></span>  
  
-   <span data-ttu-id="aab9f-120">以類別定義的 UDT 必須具有不使用引數的公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="aab9f-120">A UDT defined in a class must have a public constructor that takes no arguments.</span></span> <span data-ttu-id="aab9f-121">您可以選擇性地建立其他多載類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="aab9f-121">You can optionally create additional overloaded class constructors.</span></span>  
  
-   <span data-ttu-id="aab9f-122">UDT 必須將資料元素公開為公用欄位或屬性程序。</span><span class="sxs-lookup"><span data-stu-id="aab9f-122">The UDT must expose data elements as public fields or property procedures.</span></span>  
  
-   <span data-ttu-id="aab9f-123">公用名稱的長度不能超過128個字元，而且必須符合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [資料庫識別碼](../databases/database-identifiers.md)中所定義之識別碼的命名規則。</span><span class="sxs-lookup"><span data-stu-id="aab9f-123">Public names cannot be longer than 128 characters, and must conform to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] naming rules for identifiers as defined in [Database Identifiers](../databases/database-identifiers.md).</span></span>  
  
-   <span data-ttu-id="aab9f-124">`sql_variant` 資料行無法包含 UDT 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="aab9f-124">`sql_variant` columns cannot contain instances of a UDT.</span></span>  
  
-   <span data-ttu-id="aab9f-125">因為 [!INCLUDE[tsql](../../includes/tsql-md.md)] 類型系統不會從 UDT 辨識繼承階層，所以無法從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存取繼承成員。</span><span class="sxs-lookup"><span data-stu-id="aab9f-125">Inherited members are not accessible from [!INCLUDE[tsql](../../includes/tsql-md.md)] because the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type system is not aware of the inheritance hierarchy among UDTs.</span></span> <span data-ttu-id="aab9f-126">不過，結構化類別時可以使用繼承，並可以在型別的 Managed 程式碼實作中呼叫此類方法。</span><span class="sxs-lookup"><span data-stu-id="aab9f-126">However, you can use inheritance when you structure your classes and you can call such methods in the managed code implementation of the type.</span></span>  
  
-   <span data-ttu-id="aab9f-127">成員不可多載，但類別建構函式除外。</span><span class="sxs-lookup"><span data-stu-id="aab9f-127">Members cannot be overloaded, except for the class constructor.</span></span> <span data-ttu-id="aab9f-128">如果您有建立多載方法，則當您註冊組件或是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中建立類型時，就不會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="aab9f-128">If you do create an overloaded method, no error is raised when you register the assembly or create the type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="aab9f-129">多載方法的偵測會於執行階段發生，而不是在建立類型時發生。</span><span class="sxs-lookup"><span data-stu-id="aab9f-129">Detection of the overloaded method occurs at run time, not when the type is created.</span></span> <span data-ttu-id="aab9f-130">在叫用之前，多載方法會一直存在於類別中。</span><span class="sxs-lookup"><span data-stu-id="aab9f-130">Overloaded methods can exist in the class as long as they are never invoked.</span></span> <span data-ttu-id="aab9f-131">一旦叫用多載方法，將會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="aab9f-131">Once you invoke the overloaded method, an error is raised.</span></span>  
  
-   <span data-ttu-id="aab9f-132">任何 `static` (或 `Shared`) 成員都必須宣告為常數或唯讀。</span><span class="sxs-lookup"><span data-stu-id="aab9f-132">Any `static` (or `Shared`) members must be declared as constants or as read-only.</span></span> <span data-ttu-id="aab9f-133">靜態成員無法時常變動。</span><span class="sxs-lookup"><span data-stu-id="aab9f-133">Static members cannot be mutable.</span></span>  
  
-   <span data-ttu-id="aab9f-134">如果 `SqlUserDefinedTypeAttribute.MaxByteSize` 欄位設定為 -1，則序列化的 UDT 可以與大型物件 (LOB) 的大小限制 (目前為 2 GB) 一樣大。</span><span class="sxs-lookup"><span data-stu-id="aab9f-134">If the `SqlUserDefinedTypeAttribute.MaxByteSize` field is set to -1, the serialized UDT can be as large as the large object (LOB) size limit (currently 2 GB).</span></span> <span data-ttu-id="aab9f-135">UDT 的大小不得超過 `MaxByteSized` 欄位中指定的值。</span><span class="sxs-lookup"><span data-stu-id="aab9f-135">The size of the UDT cannot exceed the value specified in the `MaxByteSized` field.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aab9f-136">儘管伺服器不會使用它來執行比較，但您可以選擇性地實作能夠公開單一方法 `System.IComparable` 的 `CompareTo` 介面。</span><span class="sxs-lookup"><span data-stu-id="aab9f-136">Although it is not used by the server for performing comparisons, you can optionally implement the `System.IComparable` interface, which exposes a single method, `CompareTo`.</span></span> <span data-ttu-id="aab9f-137">在需要對 UDT 值進行精確比較或排序的情況下，將會在用戶端上使用它。</span><span class="sxs-lookup"><span data-stu-id="aab9f-137">This is used on the client side in situations in which it is desirable to accurately compare or order UDT values.</span></span>  
  
## <a name="native-serialization"></a><span data-ttu-id="aab9f-138">原生序列化</span><span class="sxs-lookup"><span data-stu-id="aab9f-138">Native Serialization</span></span>  
 <span data-ttu-id="aab9f-139">若要為 UDT 選擇正確的序列化屬性，必須視您嘗試建立的 UDT 型別而定。</span><span class="sxs-lookup"><span data-stu-id="aab9f-139">Choosing the right serialization attributes for your UDT depends on the type of UDT you are trying to create.</span></span> <span data-ttu-id="aab9f-140">`Native` 序列化格式使用很簡單的結構，其可以讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將有效率的 UDT 原生表示法儲存在磁碟上。</span><span class="sxs-lookup"><span data-stu-id="aab9f-140">The `Native` serialization format utilizes a very simple structure that enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to store an efficient native representation of the UDT on disk.</span></span> <span data-ttu-id="aab9f-141">如果 UDT 是簡單的，並且僅包含下列型別的欄位，則建議使用 `Native` 格式：</span><span class="sxs-lookup"><span data-stu-id="aab9f-141">The `Native` format is recommended if the UDT is simple and only contains fields of the following types:</span></span>  
  
 <span data-ttu-id="aab9f-142">**bool**、 **byte**、 **sbyte**、 **short**、 **ushort**、 **int**、 **uint**、 **long**、 **ulong**、 **float**、 **double**、 **SqlByte**、 **SqlInt16**、 **SqlInt32**、 **SqlInt64**、 **SqlDateTime**、 **SqlSingle**、 **SqlDouble**、 **SqlMoney**、 **SqlBoolean**</span><span class="sxs-lookup"><span data-stu-id="aab9f-142">**bool**, **byte**, **sbyte**, **short**, **ushort**, **int**, **uint**, **long**, **ulong**, **float**, **double**, **SqlByte**, **SqlInt16**, **SqlInt32**, **SqlInt64**, **SqlDateTime**, **SqlSingle**, **SqlDouble**, **SqlMoney**, **SqlBoolean**</span></span>  
  
 <span data-ttu-id="aab9f-143">由上述類型的欄位所組成的實數值型別，是格式的理想候選項目 `Native` ，例如 `structs` 在 Visual c # 中， (，或是在 `Structures` Visual Basic) 中已知。</span><span class="sxs-lookup"><span data-stu-id="aab9f-143">Value types that are composed of fields of the above types are good candidates for `Native` format, such as `structs` in Visual C#, (or `Structures` as they are known in Visual Basic).</span></span> <span data-ttu-id="aab9f-144">例如，使用 `Native` 序列化格式指定的 UDT 可能包含也使用 `Native` 格式指定之其他 UDT 的欄位。</span><span class="sxs-lookup"><span data-stu-id="aab9f-144">For example, a UDT specified with the `Native` serialization format may contain a field of another UDT that was also specified with the `Native` format.</span></span> <span data-ttu-id="aab9f-145">如果 UDT 定義較為複雜，且包含不在上面清單中的資料型別，則必須改為指定 `UserDefined` 序列化格式。</span><span class="sxs-lookup"><span data-stu-id="aab9f-145">If the UDT definition is more complex and contains data types not on the above list, you must specify the `UserDefined` serialization format instead.</span></span>  
  
 <span data-ttu-id="aab9f-146">`Native` 格式具有下列需求：</span><span class="sxs-lookup"><span data-stu-id="aab9f-146">The `Native` format has the following requirements:</span></span>  
  
-   <span data-ttu-id="aab9f-147">型別不可指定 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.MaxByteSize` 的值。</span><span class="sxs-lookup"><span data-stu-id="aab9f-147">The type must not specify a value for `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.MaxByteSize`.</span></span>  
  
-   <span data-ttu-id="aab9f-148">所有欄位都必須為可序列化。</span><span class="sxs-lookup"><span data-stu-id="aab9f-148">All fields must be serializable.</span></span>  
  
-   <span data-ttu-id="aab9f-149">如果 UDT 是以類別而非以結構來定義，`System.Runtime.InteropServices.StructLayoutAttribute` 就必須指定為 `StructLayout.LayoutKindSequential`。</span><span class="sxs-lookup"><span data-stu-id="aab9f-149">The `System.Runtime.InteropServices.StructLayoutAttribute` must be specified as `StructLayout.LayoutKindSequential` if the UDT is defined in a class and not a structure.</span></span> <span data-ttu-id="aab9f-150">此屬性可以控制資料欄位的實體配置，並用於強制以成員出現的順序對成員進行配置。</span><span class="sxs-lookup"><span data-stu-id="aab9f-150">This attribute controls the physical layout of the data fields and is used to force the members to be laid out in the order in which they appear.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="aab9f-151">會使用此屬性來判定具有多個值之 UDT 的欄位順序。</span><span class="sxs-lookup"><span data-stu-id="aab9f-151">uses this attribute to determine the field order for UDTs with multiple values.</span></span>  
  
 <span data-ttu-id="aab9f-152">如需以序列化定義之 UDT 的範例 `Native` ，請參閱撰寫[使用者定義類型的程式碼](creating-user-defined-types-coding.md)中的 Point udt。</span><span class="sxs-lookup"><span data-stu-id="aab9f-152">For an example of a UDT defined with `Native` serialization, see the Point UDT in [Coding User-Defined Types](creating-user-defined-types-coding.md).</span></span>  
  
## <a name="userdefined-serialization"></a><span data-ttu-id="aab9f-153">UserDefined 序列化</span><span class="sxs-lookup"><span data-stu-id="aab9f-153">UserDefined Serialization</span></span>  
 <span data-ttu-id="aab9f-154">`UserDefined` 屬性的 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 格式設定可讓開發人員完全控制二進位格式。</span><span class="sxs-lookup"><span data-stu-id="aab9f-154">The `UserDefined` format setting for the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` attribute gives the developer full control over the binary format.</span></span> <span data-ttu-id="aab9f-155">將 `Format` 屬性指定為 `UserDefined` 時，您必須在程式碼中進行下列動作：</span><span class="sxs-lookup"><span data-stu-id="aab9f-155">When specifying the `Format` attribute property as `UserDefined`, you must do the following in your code:</span></span>  
  
-   <span data-ttu-id="aab9f-156">指定選擇性的 `IsByteOrdered` 屬性。</span><span class="sxs-lookup"><span data-stu-id="aab9f-156">Specify the optional `IsByteOrdered` attribute property.</span></span> <span data-ttu-id="aab9f-157">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="aab9f-157">The default value is `false`.</span></span>  
  
-   <span data-ttu-id="aab9f-158">指定 `MaxByteSize` 的 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 屬性。</span><span class="sxs-lookup"><span data-stu-id="aab9f-158">Specify the `MaxByteSize` property of the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`.</span></span>  
  
-   <span data-ttu-id="aab9f-159">藉由實作 `Read` 介面，撰寫程式碼以實作 UDT 的 `Write` 及 `System.Data.Sql.IBinarySerialize` 方法。</span><span class="sxs-lookup"><span data-stu-id="aab9f-159">Write code to implement `Read` and `Write` methods for the UDT by implementing the `System.Data.Sql.IBinarySerialize` interface.</span></span>  
  
 <span data-ttu-id="aab9f-160">如需以序列化定義之 UDT 的範例 `UserDefined` ，請參閱[編碼使用者定義類型](creating-user-defined-types-coding.md)中的 Currency udt。</span><span class="sxs-lookup"><span data-stu-id="aab9f-160">For an example of a UDT defined with `UserDefined` serialization, see the Currency UDT in [Coding User-Defined Types](creating-user-defined-types-coding.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aab9f-161">UDT 欄位必須使用原生序列化，或保存下來進行索引。</span><span class="sxs-lookup"><span data-stu-id="aab9f-161">UDT fields must use native serialization or be persisted in order to be indexed.</span></span>  
  
## <a name="serialization-attributes"></a><span data-ttu-id="aab9f-162">序列化屬性</span><span class="sxs-lookup"><span data-stu-id="aab9f-162">Serialization Attributes</span></span>  
 <span data-ttu-id="aab9f-163">屬性會決定如何使用序列化來建構 UDT 的儲存表示，並將 UDT 以傳值方式傳輸到用戶端。</span><span class="sxs-lookup"><span data-stu-id="aab9f-163">Attributes determine how serialization is used to construct the storage representation of UDTs and to transmit UDTs by value to the client.</span></span> <span data-ttu-id="aab9f-164">建立 UDT 時，您必須指定 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`。</span><span class="sxs-lookup"><span data-stu-id="aab9f-164">You are required to specify the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` when creating the UDT.</span></span> <span data-ttu-id="aab9f-165">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 屬性表示類別為 UDT，並指定該 UDT 的儲存。</span><span class="sxs-lookup"><span data-stu-id="aab9f-165">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` attribute indicates that the class is a UDT and specifies the storage for the UDT.</span></span> <span data-ttu-id="aab9f-166">您可以選擇性地指定 `Serializable` 屬性，但是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中不需要執行這項動作。</span><span class="sxs-lookup"><span data-stu-id="aab9f-166">You can optionally specify the `Serializable` attribute, although [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not require this.</span></span>  
  
 <span data-ttu-id="aab9f-167">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 具有下列屬性。</span><span class="sxs-lookup"><span data-stu-id="aab9f-167">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` has the following properties.</span></span>  
  
 `Format`  
 <span data-ttu-id="aab9f-168">指定序列化格式，其可以為 `Native` 或 `UserDefined`，這必須視 UDT 的資料類型而定。</span><span class="sxs-lookup"><span data-stu-id="aab9f-168">Specifies the serialization format, which can be `Native` or `UserDefined`, depending on the data types of the UDT.</span></span>  
  
 `IsByteOrdered`  
 <span data-ttu-id="aab9f-169">決定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如何在 UDT 上執行二進位比較的 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="aab9f-169">A `Boolean` value that determines how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs binary comparisons on the UDT.</span></span>  
  
 `IsFixedLength`  
 <span data-ttu-id="aab9f-170">表示此 UDT 的所有執行個體是否為相同長度。</span><span class="sxs-lookup"><span data-stu-id="aab9f-170">Indicates whether all instances of this UDT are the same length.</span></span>  
  
 `MaxByteSize`  
 <span data-ttu-id="aab9f-171">執行個體的大小最大值 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="aab9f-171">The maximum size of the instance, in bytes.</span></span> <span data-ttu-id="aab9f-172">您必須使用 `MaxByteSize` 序列化格式指定 `UserDefined`。</span><span class="sxs-lookup"><span data-stu-id="aab9f-172">You must specify `MaxByteSize` with the `UserDefined` serialization format.</span></span> <span data-ttu-id="aab9f-173">如果 UDT 已指定使用者定義的序列化，對此 UDT 而言，`MaxByteSize` 是指 UDT 在其序列化形式 (由使用者所定義) 的總大小。</span><span class="sxs-lookup"><span data-stu-id="aab9f-173">For a UDT with user-defined serialization specified, `MaxByteSize` refers to the total size of the UDT in its serialized form as defined by the user.</span></span> <span data-ttu-id="aab9f-174">`MaxByteSize` 的值必須在 1 到 8000 的範圍內，或設定為 -1，表示 UDT 大於 8000 個位元組 (總大小不得超過 LOB 大小的上限)。</span><span class="sxs-lookup"><span data-stu-id="aab9f-174">The value of `MaxByteSize` must be in the range of 1 to 8000, or set to -1 to indicate that the UDT is greater than 8000 bytes (the total size cannot exceed the maximum LOB size).</span></span> <span data-ttu-id="aab9f-175">以一個具有 10 個字元字串之屬性的 UDT (`System.Char`) 為例。</span><span class="sxs-lookup"><span data-stu-id="aab9f-175">Consider a UDT with a property of a string of 10 characters (`System.Char`).</span></span> <span data-ttu-id="aab9f-176">當 UDT 使用 BinaryWriter 序列化時，序列化字串的總大小是 UDT 個位元組：每個 Unicode 2-16 字元兩個位元組，乘以字元的最大數目，再加上序列化二進位資料流所造成的兩個控制位元組負擔。</span><span class="sxs-lookup"><span data-stu-id="aab9f-176">When the UDT is serialized by using a BinaryWriter, the total size of the serialized string is 22 bytes: 2 bytes per Unicode UTF-16 character, multiplied by the maximum number of characters, plus 2 control bytes of overhead incurred from serializing a binary stream.</span></span> <span data-ttu-id="aab9f-177">因此，在決定 `MaxByteSize` 的值時，必須考慮序列化 UDT 的總大小：以二進位形式序列化資料的大小，加上序列化所耗用的位元組。</span><span class="sxs-lookup"><span data-stu-id="aab9f-177">Therefore, when determining the value of `MaxByteSize`, the total size of the serialized UDT must be considered: the size of the data serialized in binary form plus the overhead incurred by serialization.</span></span>  
  
 `ValidationMethodName`  
 <span data-ttu-id="aab9f-178">用於驗證 UDT 執行個體之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="aab9f-178">The name of the method used to validate instances of the UDT.</span></span>  
  
### <a name="setting-isbyteordered"></a><span data-ttu-id="aab9f-179">設定 IsByteOrdered</span><span class="sxs-lookup"><span data-stu-id="aab9f-179">Setting IsByteOrdered</span></span>  
 <span data-ttu-id="aab9f-180">將 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.IsByteOrdered` 屬性設為 `true` 時，您即已保證序列化的二進位資料可以用於資訊的語意排序。</span><span class="sxs-lookup"><span data-stu-id="aab9f-180">When the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.IsByteOrdered` property is set to `true`, you are in effect guaranteeing that the serialized binary data can be used for semantic ordering of the information.</span></span> <span data-ttu-id="aab9f-181">因此，每個位元組排序的 UDT 物件執行個體只能有一個序列化表示法。</span><span class="sxs-lookup"><span data-stu-id="aab9f-181">Thus, each instance of a byte-ordered UDT object can only have one serialized representation.</span></span> <span data-ttu-id="aab9f-182">當在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中對已序列化的位元組執行比較作業時，其結果應與在 Managed 程式碼中執行比較作業的結果相同。</span><span class="sxs-lookup"><span data-stu-id="aab9f-182">When a comparison operation is performed in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the serialized bytes, its results should be the same as if the same comparison operation had taken place in managed code.</span></span> <span data-ttu-id="aab9f-183">將 `IsByteOrdered` 設為 `true` 時，還可支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="aab9f-183">The following features are also supported when `IsByteOrdered` is set to `true`:</span></span>  
  
-   <span data-ttu-id="aab9f-184">在此型別之資料行上建立索引的功能。</span><span class="sxs-lookup"><span data-stu-id="aab9f-184">The ability to create indexes on columns of this type.</span></span>  
  
-   <span data-ttu-id="aab9f-185">在此類型的資料行上建立主索引鍵及外部索引鍵，以及建立 CHECK 條件約束及 UNIQUE 條件約束的功能。</span><span class="sxs-lookup"><span data-stu-id="aab9f-185">The ability to create primary and foreign keys as well as CHECK and UNIQUE constraints on columns of this type.</span></span>  
  
-   <span data-ttu-id="aab9f-186">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] ORDER BY、GROUP BY 及 PARTITION BY 子句的功能。</span><span class="sxs-lookup"><span data-stu-id="aab9f-186">The ability to use [!INCLUDE[tsql](../../includes/tsql-md.md)] ORDER BY, GROUP BY, and PARTITION BY clauses.</span></span> <span data-ttu-id="aab9f-187">在這些情況下，類型的二進位表示法用於決定順序。</span><span class="sxs-lookup"><span data-stu-id="aab9f-187">In these cases, the binary representation of the type is used to determine the order.</span></span>  
  
-   <span data-ttu-id="aab9f-188">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中使用比較運算子的功能。</span><span class="sxs-lookup"><span data-stu-id="aab9f-188">The ability to use comparison operators in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
-   <span data-ttu-id="aab9f-189">保留此類型之計算資料行的功能。</span><span class="sxs-lookup"><span data-stu-id="aab9f-189">The ability to persist computed columns of this type.</span></span>  
  
 <span data-ttu-id="aab9f-190">請注意，當 `Native` 設定為 `UserDefined` 時，`IsByteOrdered` 及 `true` 序列化格式可以支援下列比較運算子：</span><span class="sxs-lookup"><span data-stu-id="aab9f-190">Note that both the `Native` and `UserDefined` serialization formats support the following comparison operators when `IsByteOrdered` is set to `true`:</span></span>  
  
-   <span data-ttu-id="aab9f-191">等於 (=)</span><span class="sxs-lookup"><span data-stu-id="aab9f-191">Equal to (=)</span></span>  
  
-   <span data-ttu-id="aab9f-192">不等於 (!=)</span><span class="sxs-lookup"><span data-stu-id="aab9f-192">Not equal to (!=)</span></span>  
  
-   <span data-ttu-id="aab9f-193">大於 (>)</span><span class="sxs-lookup"><span data-stu-id="aab9f-193">Greater than (>)</span></span>  
  
-   <span data-ttu-id="aab9f-194">小於 (\<)</span><span class="sxs-lookup"><span data-stu-id="aab9f-194">Less than (\<)</span></span>  
  
-   <span data-ttu-id="aab9f-195">大於或等於 (>=)</span><span class="sxs-lookup"><span data-stu-id="aab9f-195">Greater than or equal to (>=)</span></span>  
  
-   <span data-ttu-id="aab9f-196">小於或等於 (&lt;=)</span><span class="sxs-lookup"><span data-stu-id="aab9f-196">Less than or equal to (<=)</span></span>  
  
### <a name="implementing-nullability"></a><span data-ttu-id="aab9f-197">實作 Null 屬性</span><span class="sxs-lookup"><span data-stu-id="aab9f-197">Implementing Nullability</span></span>  
 <span data-ttu-id="aab9f-198">除了必須正確地指定組件的屬性外，您的類別還必須能夠支援 Null 屬性。</span><span class="sxs-lookup"><span data-stu-id="aab9f-198">In addition to specifying the attributes for your assemblies correctly, your class must also support nullability.</span></span> <span data-ttu-id="aab9f-199">載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 UDT 可辨識 Null，但是為了讓 UDT 能夠辨識 Null 值，此類別必須實作 `INullable` 介面。</span><span class="sxs-lookup"><span data-stu-id="aab9f-199">UDTs loaded into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are null-aware, but in order for the UDT to recognize a null value, the class must implement the `INullable` interface.</span></span> <span data-ttu-id="aab9f-200">如需詳細資訊以及如何在 UDT 中執行 null 屬性的範例，請參閱撰寫[使用者定義類型](creating-user-defined-types-coding.md)的程式碼。</span><span class="sxs-lookup"><span data-stu-id="aab9f-200">For more information and an example of how to implement nullability in a UDT, see [Coding User-Defined Types](creating-user-defined-types-coding.md).</span></span>  
  
### <a name="string-conversions"></a><span data-ttu-id="aab9f-201">字串轉換</span><span class="sxs-lookup"><span data-stu-id="aab9f-201">String Conversions</span></span>  
 <span data-ttu-id="aab9f-202">若要支援字串與 UDT 的來回轉換，則必須在您的類別中提供 `Parse` 方法及 `ToString` 方法。</span><span class="sxs-lookup"><span data-stu-id="aab9f-202">To support string conversion to and from the UDT, you must provide a `Parse` method and a `ToString` method in your class.</span></span> <span data-ttu-id="aab9f-203">`Parse` 方法允許將字串轉換成 UDT。</span><span class="sxs-lookup"><span data-stu-id="aab9f-203">The `Parse` method allows a string to be converted into a UDT.</span></span> <span data-ttu-id="aab9f-204">它必須宣告為 `static` (或 Visual Basic 中的 `Shared`)，並採用型別 `System.Data.SqlTypes.SqlString` 的參數。</span><span class="sxs-lookup"><span data-stu-id="aab9f-204">It must be declared as `static` (or `Shared` in Visual Basic), and take a parameter of type `System.Data.SqlTypes.SqlString`.</span></span> <span data-ttu-id="aab9f-205">如需如何執行和方法的詳細資訊和範例 `Parse` `ToString` ，請參閱撰寫[使用者定義類型](creating-user-defined-types-coding.md)的程式碼。</span><span class="sxs-lookup"><span data-stu-id="aab9f-205">For more information and an example of how to implement the `Parse` and `ToString` methods, see [Coding User-Defined Types](creating-user-defined-types-coding.md).</span></span>  
  
## <a name="xml-serialization"></a><span data-ttu-id="aab9f-206">XML 序列化</span><span class="sxs-lookup"><span data-stu-id="aab9f-206">XML Serialization</span></span>  
 <span data-ttu-id="aab9f-207">UDT 必須藉由符合 XML 序列化合約，來支援 `xml` 資料類型間的轉換。</span><span class="sxs-lookup"><span data-stu-id="aab9f-207">UDTs must support conversion to and from the `xml` data type by conforming to the contract for XML serialization.</span></span> <span data-ttu-id="aab9f-208">`System.Xml.Serialization` 命名空間 (Namespace) 包含用於將物件序列化為 XML 格式文件或資料流的類別。</span><span class="sxs-lookup"><span data-stu-id="aab9f-208">The `System.Xml.Serialization` namespace contains classes that are used to serialize objects into XML format documents or streams.</span></span> <span data-ttu-id="aab9f-209">您可以選擇使用 `xml` 介面 (該介面可提供 XML 序列化和還原序列化的自訂格式)，以便實作 `IXmlSerializable` 序列化。</span><span class="sxs-lookup"><span data-stu-id="aab9f-209">You can choose to implement `xml` serialization by using the `IXmlSerializable` interface, which provides custom formatting for XML serialization and deserialization.</span></span>  
  
 <span data-ttu-id="aab9f-210">除了能夠執行 UDT 到 `xml` 的明確轉換外，XML 序列化還可讓您：</span><span class="sxs-lookup"><span data-stu-id="aab9f-210">In addition to performing explicit conversions from UDT to `xml`, XML serialization enables you to:</span></span>  
  
-   <span data-ttu-id="aab9f-211">轉換至 `Xquery` 資料類型後，在 UDT 執行個體的值上使用 `xml`。</span><span class="sxs-lookup"><span data-stu-id="aab9f-211">Use `Xquery` over values of UDT instances after conversion to the `xml` data type.</span></span>  
  
-   <span data-ttu-id="aab9f-212">搭配 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的原生 XML Web 服務使用參數化查詢和 Web 方法中的 UDT。</span><span class="sxs-lookup"><span data-stu-id="aab9f-212">Use UDTs in parameterized queries and Web methods with Native XML Web Services in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="aab9f-213">使用 UDT 接收 XML 資料的大量載入。</span><span class="sxs-lookup"><span data-stu-id="aab9f-213">Use UDTs to receive a bulk load of XML data.</span></span>  
  
-   <span data-ttu-id="aab9f-214">序列化包含具有 UDT 資料行之資料表的 DataSet。</span><span class="sxs-lookup"><span data-stu-id="aab9f-214">Serialize DataSets that contain tables with UDT columns.</span></span>  
  
 <span data-ttu-id="aab9f-215">在 FOR XML 查詢中不會序列化 UDT。</span><span class="sxs-lookup"><span data-stu-id="aab9f-215">UDTs are not serialized in FOR XML queries.</span></span> <span data-ttu-id="aab9f-216">若要執行顯示 UDT 之 XML 序列化的 FOR XML 查詢，請在 SELECT 陳述式中將每個 UDT 資料行明確轉換為 `xml` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="aab9f-216">To execute a FOR XML query that displays the XML serialization of UDTs, explicitly convert each UDT column to the `xml` data type in the SELECT statement.</span></span> <span data-ttu-id="aab9f-217">您還可以將資料行明確轉換為 `varbinary`、`varchar` 或 `nvarchar`。</span><span class="sxs-lookup"><span data-stu-id="aab9f-217">You can also explicitly convert the columns to `varbinary`, `varchar`, or `nvarchar`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aab9f-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aab9f-218">See Also</span></span>  
 [<span data-ttu-id="aab9f-219">建立使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="aab9f-219">Creating a User-Defined Type</span></span>](creating-user-defined-types.md)  
  
  
