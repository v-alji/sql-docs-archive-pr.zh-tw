---
title: 使用資料類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DataType object
- SQL Server Management Objects, data types
- data types [SMO]
- SMO [SQL Server], data types
ms.assetid: 1e0e736a-c709-4d89-aeb2-b32dcfd641fa
author: stevestein
ms.author: sstein
ms.openlocfilehash: cbffc1c59eb12fa0f448a7fcb26157d5e18dba3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592558"
---
# <a name="working-with-data-types"></a><span data-ttu-id="3f1cb-102">使用資料類型</span><span class="sxs-lookup"><span data-stu-id="3f1cb-102">Working with Data Types</span></span>
  <span data-ttu-id="3f1cb-103">資料有許多類型和大小，例如已定義長度的字串、具有特定精確度的數字，或是使用者定義資料類型 (有自己的規則集合的另一個物件)。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-103">Data comes in many types and sizes, such as a string that has a defined length, a number that has specific accuracy, or a user-defined data type that is another object that has its own set of rules.</span></span> <span data-ttu-id="3f1cb-104"><xref:Microsoft.SqlServer.Management.Smo.DataType>物件會分類資料類型，以便能夠正確地處理它 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-104">The <xref:Microsoft.SqlServer.Management.Smo.DataType> object classifies the type of data so that it can be handled correctly by [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3f1cb-105"><xref:Microsoft.SqlServer.Management.Smo.DataType> 物件與可接受資料的物件有關聯。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-105">The <xref:Microsoft.SqlServer.Management.Smo.DataType> object is associated with objects that accept data.</span></span> <span data-ttu-id="3f1cb-106">下列 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) 物件可接受必須由 <xref:Microsoft.SqlServer.Management.Smo.DataType> 物件屬性所定義的資料：</span><span class="sxs-lookup"><span data-stu-id="3f1cb-106">The following [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) objects accept data that must be defined by a <xref:Microsoft.SqlServer.Management.Smo.DataType> object property:</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Column>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedAggregateParameter>  
  
 <span data-ttu-id="3f1cb-107">接受資料之物件的 `DataType` 屬性可利用幾種方式來加以設定。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-107">The `DataType` property for objects that accept data can be set in several ways.</span></span>  
  
-   <span data-ttu-id="3f1cb-108">使用預設建構函式，並明確指定 <xref:Microsoft.SqlServer.Management.Smo.DataType> 物件屬性。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-108">Use the default constructor and specify <xref:Microsoft.SqlServer.Management.Smo.DataType> object properties explicitly</span></span>  
  
-   <span data-ttu-id="3f1cb-109">使用多載的建構函式，並將 <xref:Microsoft.SqlServer.Management.Smo.DataType> 屬性指定為參數。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-109">Use an overloaded constructor and specify the <xref:Microsoft.SqlServer.Management.Smo.DataType> properties as parameters.</span></span>  
  
-   <span data-ttu-id="3f1cb-110">在物件建構函式中指定 <xref:Microsoft.SqlServer.Management.Smo.DataType> 為內嵌。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-110">Specify the <xref:Microsoft.SqlServer.Management.Smo.DataType> inline in the object constructor.</span></span>  
  
-   <span data-ttu-id="3f1cb-111">使用 <xref:Microsoft.SqlServer.Management.Smo.DataType> 類別的其中一個靜態成員，例如 `Int`。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-111">Use one of the static members of the <xref:Microsoft.SqlServer.Management.Smo.DataType> class, for example `Int`.</span></span> <span data-ttu-id="3f1cb-112">事實上，這樣會傳回 <xref:Microsoft.SqlServer.Management.Smo.DataType> 物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-112">This will in fact return an instance of a <xref:Microsoft.SqlServer.Management.Smo.DataType> object.</span></span>  
  
 <span data-ttu-id="3f1cb-113"><xref:Microsoft.SqlServer.Management.Smo.DataType> 物件有好幾個屬性會定義資料的類型。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-113">The <xref:Microsoft.SqlServer.Management.Smo.DataType> object has several properties that define the type of data.</span></span> <span data-ttu-id="3f1cb-114">例如，<xref:Microsoft.SqlServer.Management.Smo.SqlDataType> 屬性會指定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-114">For example, the <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> property specifies the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type.</span></span> <span data-ttu-id="3f1cb-115">代表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型的常數值會列在 <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> 列舉中。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-115">The constant values that represent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types are listed in the <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> enumeration.</span></span> <span data-ttu-id="3f1cb-116">這是指像是 `varchar`、`nchar`、`currency`、`integer`、`float` 和 `datetime` 等資料類型。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-116">This refers to data types such as `varchar`, `nchar`, `currency`, `integer`, `float`, and `datetime`.</span></span>  
  
 <span data-ttu-id="3f1cb-117">當建立該資料類型時，必須為資料設定特定的屬性。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-117">When the data type is established, specific properties must be set for the data.</span></span> <span data-ttu-id="3f1cb-118">例如，如果它是 `nchar` 類型，字串資料的長度必須在 `Length` 屬性中設定。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-118">For example, if it is an `nchar` type, the length of the string data must be set in the `Length` property.</span></span> <span data-ttu-id="3f1cb-119">這同樣適用於數值，您必須為數值指定有效位數及小數位數。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-119">The same applies for numeric values, where you would have to specify precision and scale.</span></span>  
  
 <span data-ttu-id="3f1cb-120"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> 和 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> 資料類型指的是包含使用者定義之資料類型定義的物件。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-120"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> and <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> data types refer to objects that contain the definition of the type of data defined by the user.</span></span> <span data-ttu-id="3f1cb-121"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> 是根據 <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> 列舉中的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-121">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> is based on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types from the <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> enumeration.</span></span> <span data-ttu-id="3f1cb-122"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>是以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .net 資料類型為基礎。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-122">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> is based on [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET data types.</span></span> <span data-ttu-id="3f1cb-123">一般來說，這些代表特定類型的資料，資料庫會因為組織所定義的商務規則而經常重複使用這些資料。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-123">Typically, these would represent data of a specific type that is frequently reused by the database because of business rules defined by the organization.</span></span> <span data-ttu-id="3f1cb-124">例如，儲存金錢數量和貨幣單位的資料類型對於處理多種貨幣的公司會很有幫助。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-124">For example, a data type that stores an amount of money and a currency denominator would be helpful in a company that deals in multiple currencies.</span></span>  
  
 <span data-ttu-id="3f1cb-125"><xref:Microsoft.SqlServer.Management.Smo.SqlDataType> 列舉包含所有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 支援之資料類型的清單。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-125">The <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> enumeration contains a list of all the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-supported data types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3f1cb-126">範例</span><span class="sxs-lookup"><span data-stu-id="3f1cb-126">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-basic"></a><span data-ttu-id="3f1cb-127">在 Visual Basic 中使用建構函式內的規格來建構 DataType 物件</span><span class="sxs-lookup"><span data-stu-id="3f1cb-127">Constructing a DataType Object with the Specification in the Constructor in Visual Basic</span></span>  
 <span data-ttu-id="3f1cb-128">此程式碼範例示範如何使用此建構函式來建立以不同 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型為根據的資料類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-128">This code example shows how to use the constructor to create instances of data types that are based on different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f1cb-129"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> 和 XML 類型全都需要一個名稱值，才能識別此物件。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-129">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, and XML types all require a name value to identify the object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes1](SMO How to#SMO_VBDataTypes1)]  -->  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-c"></a><span data-ttu-id="3f1cb-130">在 Visual C# 中使用建構函式內的規格來建構 DataType 物件</span><span class="sxs-lookup"><span data-stu-id="3f1cb-130">Constructing a DataType Object with the Specification in the Constructor in Visual C#</span></span>  
 <span data-ttu-id="3f1cb-131">此程式碼範例示範如何使用此建構函式來建立以不同 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型為根據的資料類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-131">This code example shows how to use the constructor to create instances of data types that are based on different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f1cb-132"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> 和 XML 類型全都需要一個名稱值，才能識別此物件。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-132">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, and XML types all require a name value to identify the object.</span></span>  
  
```  
{   
//Declare a DataType object variable and define the data type in the constructor.   
DataType dt;   
//For the decimal data type the following two arguments specify precision, and scale.   
dt = new DataType(SqlDataType.Decimal, 10, 2);   
}  
```  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-basic"></a><span data-ttu-id="3f1cb-133">在 Visual Basic 中使用預設建構函式來建構 DataType 物件</span><span class="sxs-lookup"><span data-stu-id="3f1cb-133">Constructing a DataType Object by Using the Default Constructor in Visual Basic</span></span>  
 <span data-ttu-id="3f1cb-134">此程式碼範例示範如何使用預設建構函式來建立以不同 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型為根據的資料類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-134">This code example shows how to use the default constructor to create instances of data types that are based on different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="3f1cb-135">然後會使用這些屬性來指定資料類型。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-135">The properties are then used to specify the data type.</span></span>  
  
 <span data-ttu-id="3f1cb-136">**注意**<xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、和 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> XML 類型全都需要名稱值來識別物件。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-136">**Note** The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, and XML types all require a name value to identify the object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes2](SMO How to#SMO_VBDataTypes2)]  -->  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-c"></a><span data-ttu-id="3f1cb-137">在 Visual C# 中使用預設建構函式來建構 DataType 物件</span><span class="sxs-lookup"><span data-stu-id="3f1cb-137">Constructing a DataType Object by Using the Default Constructor in Visual C#</span></span>  
 <span data-ttu-id="3f1cb-138">此程式碼範例示範如何使用預設建構函式來建立以不同 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型為根據的資料類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-138">This code example shows how to use the default constructor to create instances of data types that are based on different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="3f1cb-139">然後會使用這些屬性來指定資料類型。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-139">The properties are then used to specify the data type.</span></span>  
  
 <span data-ttu-id="3f1cb-140">**注意**<xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、和 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> XML 類型全都需要名稱值來識別物件。</span><span class="sxs-lookup"><span data-stu-id="3f1cb-140">**Note** The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, and XML types all require a name value to identify the object.</span></span>  
  
```  
{   
//Declare and create a DataType object variable.   
DataType dt;   
dt = new DataType();   
//Define the data type by setting the SqlDataType property.   
dt.SqlDataType = SqlDataType.VarChar;   
//The VarChar data type requires a value for the MaximumLength property.   
dt.MaximumLength = 100;   
}  
```  
  
  
