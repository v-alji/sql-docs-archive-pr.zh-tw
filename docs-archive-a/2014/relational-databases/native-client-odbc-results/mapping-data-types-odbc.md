---
title: " (ODBC) 對應資料類型 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [ODBC]
- result sets [ODBC], data types
- ODBC data types, mapping
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], mapping
- sql_variant data type
- SQL Server Native Client ODBC driver, data types
ms.assetid: 4ba0924d-9fca-4c48-aced-0a8d817b3dde
author: rothja
ms.author: jroth
ms.openlocfilehash: 545e738afb6b3283b2ff2f3830921da8ed13202f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709334"
---
# <a name="mapping-data-types-odbc"></a><span data-ttu-id="9fe62-102">對應資料類型 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="9fe62-102">Mapping Data Types (ODBC)</span></span>
  <span data-ttu-id="9fe62-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL 資料類型對應至 ODBC sql 資料類型。</span><span class="sxs-lookup"><span data-stu-id="9fe62-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver maps [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL data types to ODBC SQL data types.</span></span> <span data-ttu-id="9fe62-104">下列章節討論 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL 資料類型和它們所對應的 ODBC SQL 資料類型。</span><span class="sxs-lookup"><span data-stu-id="9fe62-104">The sections below discuss the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL data types and the ODBC SQL data types to which they map.</span></span> <span data-ttu-id="9fe62-105">這些章節也討論 ODBC SQL 資料類型及其對應的 ODBC C 資料類型，以及支援的和預設的轉換。</span><span class="sxs-lookup"><span data-stu-id="9fe62-105">They also discuss the ODBC SQL data types and their corresponding ODBC C data types, and the supported and default conversions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9fe62-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**時間戳記**資料類型會對應至 SQL_BINARY 或 SQL_VARBINARY 的 ODBC 資料類型，因為**timestamp**資料行中的值不是**datetime**值，而是\*\*BINARY (8) **或**VARBINARY (8) \*\*值，指出資料列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上的活動順序。</span><span class="sxs-lookup"><span data-stu-id="9fe62-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**timestamp** data type maps to the SQL_BINARY or SQL_VARBINARY ODBC data type because the values in **timestamp** columns are not **datetime** values, but **binary(8)** or **varbinary(8)** values that indicate the sequence of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] activity on the row.</span></span> <span data-ttu-id="9fe62-107">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式遇到奇數位元組的 SQL_C_WCHAR (Unicode) 值，則尾端的奇數位元組會被截斷。</span><span class="sxs-lookup"><span data-stu-id="9fe62-107">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver encounters a SQL_C_WCHAR (Unicode) value that is an odd number of bytes, the trailing odd byte is truncated.</span></span>  
  
## <a name="dealing-with-sql_variant-data-type-in-odbc"></a><span data-ttu-id="9fe62-108">處理 ODBC 中的 sql_variant 資料類型</span><span class="sxs-lookup"><span data-stu-id="9fe62-108">Dealing with sql_variant Data Type in ODBC</span></span>  
 <span data-ttu-id="9fe62-109">**sql_variant** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 除了大型物件 (lob) （例如**text**、 **Ntext**和**image**）以外，SQL_variant 資料類型資料行可以包含其中的任何資料類型。</span><span class="sxs-lookup"><span data-stu-id="9fe62-109">The **sql_variant** data type column can contain any of the data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] except large objects (LOBs), such as **text**, **ntext**, and **image**.</span></span> <span data-ttu-id="9fe62-110">例如，資料行可能包含某些資料列的**Smallint**值、其他資料列的**浮點**值，以及餘數中的**char/Nchar**值。</span><span class="sxs-lookup"><span data-stu-id="9fe62-110">For example, the column could contain **smallint** values for some rows, **float** values for other rows, and **char/nchar** values in the remainder.</span></span>  
  
 <span data-ttu-id="9fe62-111">**Sql_variant**資料類型類似于 Microsoft Visual Basic 中的**variant**資料類型??。</span><span class="sxs-lookup"><span data-stu-id="9fe62-111">The **sql_variant** data type is similar to the **Variant** data type in Microsoft Visual Basic??.</span></span>  
  
### <a name="retrieving-data-from-the-server"></a><span data-ttu-id="9fe62-112">從伺服器擷取資料</span><span class="sxs-lookup"><span data-stu-id="9fe62-112">Retrieving Data from the Server</span></span>  
 <span data-ttu-id="9fe62-113">ODBC 沒有 variant 類型的概念，會限制在中使用**SQL_variant**資料類型與 ODBC 驅動程式 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9fe62-113">ODBC does not have a concept of variant types, limiting the use of the **sql_variant** data type with an ODBC driver in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9fe62-114">在中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，如果指定了 binding，則**SQL_variant**資料類型必須系結至其中一個已記載的 ODBC 資料類型。</span><span class="sxs-lookup"><span data-stu-id="9fe62-114">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if binding is specified, the **sql_variant** data type must be bound to one of the documented ODBC data types.</span></span> <span data-ttu-id="9fe62-115">**SQL_CA_SS_VARIANT_TYPE**，NATIVE Client ODBC 驅動程式特定的新屬性會將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL_variant**資料行中實例的資料類型傳回給使用者。</span><span class="sxs-lookup"><span data-stu-id="9fe62-115">**SQL_CA_SS_VARIANT_TYPE**, a new attribute specific to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, returns the data type of an instance in the **sql_variant** column to the user.</span></span>  
  
 <span data-ttu-id="9fe62-116">如果未指定系結，則可以使用[SQLGetData](../native-client-odbc-api/sqlgetdata.md)函數來判斷實例在**SQL_variant**資料行中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="9fe62-116">If no binding is specified, the [SQLGetData](../native-client-odbc-api/sqlgetdata.md) function can be used to determine the data type of an instance in the **sql_variant** column.</span></span>  
  
 <span data-ttu-id="9fe62-117">若要取得**SQL_variant**資料，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="9fe62-117">To retrieve **sql_variant** data follow these steps.</span></span>  
  
1.  <span data-ttu-id="9fe62-118">呼叫**SQLFetch** ，以定位至抓取的資料列。</span><span class="sxs-lookup"><span data-stu-id="9fe62-118">Call **SQLFetch** to position to the row retrieved.</span></span>  
  
2.  <span data-ttu-id="9fe62-119">呼叫**SQLGetData**，並指定類型的 SQL_C_BINARY，並將資料長度指定為0。</span><span class="sxs-lookup"><span data-stu-id="9fe62-119">Call **SQLGetData**, specifying SQL_C_BINARY for the type and 0 for the data length.</span></span> <span data-ttu-id="9fe62-120">這會強制驅動程式讀取**SQL_variant**標頭。</span><span class="sxs-lookup"><span data-stu-id="9fe62-120">This forces the driver to read the **sql_variant** header.</span></span> <span data-ttu-id="9fe62-121">標頭會在**SQL_variant**資料行中提供該實例的資料類型。</span><span class="sxs-lookup"><span data-stu-id="9fe62-121">The header provides the data type of that instance in the **sql_variant** column.</span></span> <span data-ttu-id="9fe62-122">**SQLGetData**會傳回值的大小 (以位元組) 。</span><span class="sxs-lookup"><span data-stu-id="9fe62-122">**SQLGetData** returns the size (in bytes) of the value.</span></span>  
  
3.  <span data-ttu-id="9fe62-123">藉由指定**SQL_CA_SS_VARIANT_TYPE**做為其屬性值來呼叫[SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) 。</span><span class="sxs-lookup"><span data-stu-id="9fe62-123">Call [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) by specifying **SQL_CA_SS_VARIANT_TYPE** as its attribute value.</span></span> <span data-ttu-id="9fe62-124">此函式會將**SQL_variant**資料行中實例的 C 資料類型傳回至用戶端。</span><span class="sxs-lookup"><span data-stu-id="9fe62-124">This function will return the C data type of the instance in the **sql_variant** column to the client.</span></span>  
  
 <span data-ttu-id="9fe62-125">下列程式碼片段顯示前述的步驟。</span><span class="sxs-lookup"><span data-stu-id="9fe62-125">Here is a code segment showing the preceding steps.</span></span>  
  
```  
while ((retcode = SQLFetch (hstmt))==SQL_SUCCESS)  
{  
    if (retcode != SQL_SUCCESS && retcode != SQL_SUCCESS_WITH_INFO)  
    {  
        SQLError (NULL, NULL, hstmt, NULL,   
                    &lNativeError,szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    retcode = SQLGetData (hstmt, 1, SQL_C_BINARY,   
                                pBuff,0,&Indicator);//Figure out the length  
    if (retcode != SQL_SUCCESS_WITH_INFO && retcode != SQL_SUCCESS)  
    {  
        SQLError (NULL, NULL, hstmt, NULL, &lNativeError,   
                    szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    printf_s ("Byte length : %d ",Indicator); //Print out the byte length  
  
    int iValue = 0;  
    retcode = SQLColAttribute (hstmt, 1, SQL_CA_SS_VARIANT_TYPE, NULL,   
                                        NULL,NULL,&iValue);  //Figure out the type  
    printf_s ("Sub type = %d ",iValue);//Print the type, the return is C_type of the column]  
  
// Set up a new binding or do the SQLGetData on that column with   
// the appropriate type  
}  
```  
  
 <span data-ttu-id="9fe62-126">如果使用者使用[SQLBindCol](../native-client-odbc-api/sqlbindcol.md)建立系結，驅動程式會讀取中繼資料和資料。</span><span class="sxs-lookup"><span data-stu-id="9fe62-126">If the user creates the binding using [SQLBindCol](../native-client-odbc-api/sqlbindcol.md), the driver reads the metadata and the data.</span></span> <span data-ttu-id="9fe62-127">驅動程式會接著將資料轉換為繫結中指定的適當 ODBC 類型。</span><span class="sxs-lookup"><span data-stu-id="9fe62-127">The driver then converts the data to the appropriate ODBC type specified in the binding.</span></span>  
  
### <a name="sending-data-to-the-server"></a><span data-ttu-id="9fe62-128">將資料傳送到伺服器</span><span class="sxs-lookup"><span data-stu-id="9fe62-128">Sending Data to the Server</span></span>  
 <span data-ttu-id="9fe62-129">**SQL_SS_VARIANT** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是 Native Client ODBC 驅動程式特定的新資料類型，會用於傳送至**SQL_variant**資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="9fe62-129">**SQL_SS_VARIANT**, a new data type specific to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, is used for data sent to an **sql_variant** column.</span></span> <span data-ttu-id="9fe62-130">使用參數將資料傳送至伺服器時 (例如，插入 TableName 值 (?,? ) # A3， [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)是用來指定包含 C 類型和對應類型的參數資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9fe62-130">When sending data to the server using parameters (for example, INSERT INTO TableName VALUES (?,?)), [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) is used to specify the parameter information including the C type and the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type.</span></span> <span data-ttu-id="9fe62-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會將 C 資料類型轉換成其中一個適當的**SQL_variant**子類型。</span><span class="sxs-lookup"><span data-stu-id="9fe62-131">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver will convert the C data type to one of the appropriate **sql_variant** subtypes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe62-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fe62-132">See Also</span></span>  
 [<span data-ttu-id="9fe62-133">&#40;ODBC&#41;處理結果</span><span class="sxs-lookup"><span data-stu-id="9fe62-133">Processing Results &#40;ODBC&#41;</span></span>](processing-results-odbc.md)  
  
  
