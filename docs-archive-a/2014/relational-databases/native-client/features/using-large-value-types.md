---
title: 使用大數值類型 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- large value data types
- SQLNCLI, large value types
- SQL Server Native Client, large value types
- data access [SQL Server Native Client], large value types
- SQL Server Native Client ODBC driver, large value data types
- SQL Server Native Client OLE DB provider, large value data types
ms.assetid: 4a58b05c-8848-44bb-8704-f9f409efa5af
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a2e93ee36eb4bfadf18c5b78f552380d1c94266
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598323"
---
# <a name="using-large-value-types"></a><span data-ttu-id="2621f-102">使用大數值類型</span><span class="sxs-lookup"><span data-stu-id="2621f-102">Using Large Value Types</span></span>
  <span data-ttu-id="2621f-103">在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 之前，使用大數值資料類型時需要進行特殊處理。</span><span class="sxs-lookup"><span data-stu-id="2621f-103">Before [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], working with large value data types required special handling.</span></span> <span data-ttu-id="2621f-104">大數值資料類型是指那些最大資料列大小超過 8 KB 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="2621f-104">Large value data types are those that exceed the maximum row size of 8 KB.</span></span> [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]<span data-ttu-id="2621f-105">引進**Varchar**、 **Nvarchar**和**Varbinary**資料類型的 max 規範，允許儲存**最**大可達 2 ^ 31-1 個位元組的值。</span><span class="sxs-lookup"><span data-stu-id="2621f-105">introduced a **max** specifier for **varchar**, **nvarchar** and **varbinary** data types to allow storage of values as large as 2^31 -1 bytes.</span></span> <span data-ttu-id="2621f-106">資料表資料行和 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 變數可以指定\*\*Varchar (max) \*\*、 \*\*Nvarchar (max) **或**Varbinary (max) \*\*資料類型。</span><span class="sxs-lookup"><span data-stu-id="2621f-106">Table columns and [!INCLUDE[tsql](../../../includes/tsql-md.md)] variables may specify **varchar(max)**, **nvarchar(max)** or **varbinary(max)** data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2621f-107">大數值資料類型的最大大小可介於 1 和 8 KB 之間，或者也可以指定為無限制。</span><span class="sxs-lookup"><span data-stu-id="2621f-107">Large value data types can have a maximum size between 1 and 8 KB, or they can be specified as unlimited.</span></span>  
  
 <span data-ttu-id="2621f-108">先前，只有 **text**、**ntext** 和 **image** 之類的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型可以達到此種長度。</span><span class="sxs-lookup"><span data-stu-id="2621f-108">Previously, only [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types such as **text**, **ntext** and **image** could attain such lengths.</span></span> <span data-ttu-id="2621f-109">**Varchar**、 **Nvarchar**和**Varbinary**的**max**規範使這些資料類型成為多餘的。</span><span class="sxs-lookup"><span data-stu-id="2621f-109">The **max** specifier for **varchar**, **nvarchar** and **varbinary** made these data types redundant.</span></span> <span data-ttu-id="2621f-110">不過，因為 long 資料類型仍可使用，所以大部分 OLE DB 和 ODBC 資料存取元件的介面都仍保持原樣。</span><span class="sxs-lookup"><span data-stu-id="2621f-110">However, because long data types are still available, most of the interfaces to the OLE DB and ODBC data access components will remain the same.</span></span> <span data-ttu-id="2621f-111">為了與先前的版本保持回溯相容性，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者中的 DBCOLUMNFLAGS_ISLONG 旗標以及 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式中的 SQL_LONGVARCHAR 仍會繼續使用。</span><span class="sxs-lookup"><span data-stu-id="2621f-111">For backward compatibility with prior releases, the DBCOLUMNFLAGS_ISLONG flag in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, and the SQL_LONGVARCHAR in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver remain in use.</span></span> <span data-ttu-id="2621f-112">當新類型設定為無限制的最大長度時，針對 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 和更新版本所撰寫的提供者和驅動程式仍會為其繼續使用這些詞彙。</span><span class="sxs-lookup"><span data-stu-id="2621f-112">Providers and drivers written against [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and later continue to use these terms for the new types when set to unlimited maximum length.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2621f-113">您也可以將 **varchar(max)**、**nvarchar(max)** 和 **varbinary(max)** 資料類型指定為預存程序的輸入和輸出參數類型、函數傳回型別，或者指定於 [CAST 和 CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql) 函數。</span><span class="sxs-lookup"><span data-stu-id="2621f-113">You can also specify **varchar(max)**, **nvarchar(max)**, and **varbinary(max)** data types as input and output parameter types of stored procedures, function return types, or in [CAST and CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql) functions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2621f-114">如果複寫資料，您可能需要將 [[最大文字複寫大小] 伺服器設定選項](../../../database-engine/configure-windows/configure-the-max-text-repl-size-server-configuration-option.md)設為-1。</span><span class="sxs-lookup"><span data-stu-id="2621f-114">If replicating data you may need to configure the [max text repl size server configuration option](../../../database-engine/configure-windows/configure-the-max-text-repl-size-server-configuration-option.md) to -1.</span></span>  
  
## <a name="sql-server-native-client-ole-db-provider"></a><span data-ttu-id="2621f-115">SQL Server Native Client OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="2621f-115">SQL Server Native Client OLE DB Provider</span></span>  
 <span data-ttu-id="2621f-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會分別公開\*\*Varchar (max) \*\*、 **Varbinary (max) **和**Nvarchar (**) 、DBTYPE_STR 和 DBTYPE_BYTES 的最大 DBTYPE_WSTR 類型。</span><span class="sxs-lookup"><span data-stu-id="2621f-116">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **varchar(max)**, **varbinary(max)**, and **nvarchar(max)** types as DBTYPE_STR, DBTYPE_BYTES, and DBTYPE_WSTR, respectively.</span></span>  
  
 <span data-ttu-id="2621f-117">在 **max** 大小設定為無限制的資料行中，**varchar(max)**、**varbinary(max)** 和 **nvarchar(max)** 資料類型會在傳回資料行資料類型的核心 OLE DB 結構描述資料列集和介面中表示為 ISLONG。</span><span class="sxs-lookup"><span data-stu-id="2621f-117">The data types **varchar(max)**, **varbinary(max)**, and **nvarchar(max)** in columns with the **max** size set to unlimited are represented as an ISLONG through the core OLE DB schema rowsets and interfaces returning column data types.</span></span>  
  
 <span data-ttu-id="2621f-118">命令物件的**IAccessor**實已變更為允許系結為 DBTYPE_IUNKNOWN。</span><span class="sxs-lookup"><span data-stu-id="2621f-118">The command object's **IAccessor** implementation has been changed to allow binding as DBTYPE_IUNKNOWN.</span></span> <span data-ttu-id="2621f-119">如果取用者指定 DBTYPE_IUNKNOWN 並將 *pObject* 設定為 null，則提供者會將 **ISequentialStream** 介面傳回給取用者，讓取用者可以將 **varchar(max)**、**nvarchar(max)** 或 **varbinary(max)** 用資料流的形式傳出輸出變數。</span><span class="sxs-lookup"><span data-stu-id="2621f-119">If the consumer specifies DBTYPE_IUNKNOWN and sets *pObject* to null, the provider will return the **ISequentialStream** interface to the consumer so that the consumer can stream **varchar(max)**, **nvarchar(max)**, or **varbinary(max)** data out of output variables.</span></span>  
  
 <span data-ttu-id="2621f-120">以資料流傳輸的輸出參數值會在任何結果資料列之後傳回。</span><span class="sxs-lookup"><span data-stu-id="2621f-120">Streamed output parameter values are returned after any result rows.</span></span> <span data-ttu-id="2621f-121">如果應用程式藉由呼叫 **IMultipleResults::GetResult** (而不取用所有的傳回輸出參數值) 嘗試繼續前往下一個結果集，就會傳回 DB_E_OBJECTOPEN。</span><span class="sxs-lookup"><span data-stu-id="2621f-121">If the application attempts to move on to the next result set by calling **IMultipleResults::GetResult** without consuming all the returned output parameter values, DB_E_OBJECTOPEN will be returned.</span></span>  
  
 <span data-ttu-id="2621f-122">為了支援串流， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者需要以順序存取可變長度參數。</span><span class="sxs-lookup"><span data-stu-id="2621f-122">In order to support streaming, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider requires variable length parameters to be accessed in sequential order.</span></span> <span data-ttu-id="2621f-123">這表示每當 **varchar(max)**、**nvarchchar(max)** 或 **varbinary(max)** 資料行或輸出參數繫結至 DBTYPE_IUNKNOWN 時，DBPROP_ACCESSORDER 就必須設定為 DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS 或 DBPROPVAL_AO_SEQUENTIAL。</span><span class="sxs-lookup"><span data-stu-id="2621f-123">This means that DBPROP_ACCESSORDER must be set to either DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS or DBPROPVAL_AO_SEQUENTIAL whenever **varchar(max)**, **nvarchchar(max)**, or **varbinary(max)** columns or output parameters are bound to DBTYPE_IUNKNOWN.</span></span> <span data-ttu-id="2621f-124">如果未遵守這項存取順序的限制，則對 **IRowset::GetData** 的呼叫會失敗，且傳回 DBSTATUS_E_UNAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2621f-124">Calls to **IRowset::GetData** will fail with DBSTATUS_E_UNAVAILABLE if this access order restriction is not adhered to.</span></span> <span data-ttu-id="2621f-125">當沒有任何使用 DBTYPE_IUNKNOWN 的輸出繫結時，這項限制就不適用。</span><span class="sxs-lookup"><span data-stu-id="2621f-125">This restriction does not apply when there are no output bindings using DBTYPE_IUNKNOWN.</span></span>  
  
 <span data-ttu-id="2621f-126">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者也支援將輸出參數系結為大數值資料類型的 DBTYPE_IUNKNOWN，以加速預存程式傳回大數數值型別做為傳回值，以當做 DBTYPE_IUNKNOWN 公開為用戶端的情況。</span><span class="sxs-lookup"><span data-stu-id="2621f-126">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider also supports binding output parameters as DBTYPE_IUNKNOWN for large value data types to facilitate scenarios where a stored procedure returns large value types as return values that are exposed as DBTYPE_IUNKNOWN to the client.</span></span>  
  
 <span data-ttu-id="2621f-127">為了使用這些類型，應用程式具有下列選項：</span><span class="sxs-lookup"><span data-stu-id="2621f-127">To work with these types, an application has the following options:</span></span>  
  
-   <span data-ttu-id="2621f-128">繫結為具有資料行基底類型所支援繫結的類型 (例如，對於 nvarchar(max)，繫結為可繫結到 nvarchar 的類型)。</span><span class="sxs-lookup"><span data-stu-id="2621f-128">Bind as a type that has supported bindings with the base type of the column (eg for nvarchar(max), bind as a type that can be bound to nvarchar).</span></span> <span data-ttu-id="2621f-129">如果緩衝區不夠大，就會進行截斷，這與基底類型完全相同，只是現在使用的是較大數值。</span><span class="sxs-lookup"><span data-stu-id="2621f-129">If the buffer is not big enough truncation will occur, exactly as for the base type, albeit that larger values are now available.</span></span>  
  
-   <span data-ttu-id="2621f-130">繫結為具有資料行基底類型所支援轉換的類型，並同時指定 DBTYPE_BYREF。</span><span class="sxs-lookup"><span data-stu-id="2621f-130">Bind as a type that has supported conversions with the base type of the column and also specify DBTYPE_BYREF.</span></span>  
  
-   <span data-ttu-id="2621f-131">繫結為 DBTYPE_IUNKNOWN 並使用資料流。</span><span class="sxs-lookup"><span data-stu-id="2621f-131">Bind as DBTYPE_IUNKNOWN and use streaming.</span></span>  
  
 <span data-ttu-id="2621f-132">報告資料行的大小上限時， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者將會報告：</span><span class="sxs-lookup"><span data-stu-id="2621f-132">When reporting the maximum size of a column, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider will report:</span></span>  
  
-   <span data-ttu-id="2621f-133">為**Varchar (** 2000 \*\*) \*\*資料行定義的大小上限（例如）為2000，或</span><span class="sxs-lookup"><span data-stu-id="2621f-133">The defined maximum size, which for example, is 2000 for a **varchar(** 2000 **)** column, or</span></span>  
  
-   <span data-ttu-id="2621f-134">"unlimited" 這個值，如果是 **varchar(max)** 資料行則等於 ~0。</span><span class="sxs-lookup"><span data-stu-id="2621f-134">The value "unlimited" which in the case of a **varchar(max)** column equals ~0.</span></span> <span data-ttu-id="2621f-135">這個值會針對 DBCOLUMN_COLUMNSIZE 中繼資料屬性設定。</span><span class="sxs-lookup"><span data-stu-id="2621f-135">This value is set for the DBCOLUMN_COLUMNSIZE metadata property.</span></span>  
  
 <span data-ttu-id="2621f-136">標準轉換規則適用於 **varchar(max)** 資料行，代表任何對 **varchar(** 2000 **)** 資料行有效的轉換也對 **varchar(max)** 資料行有效。</span><span class="sxs-lookup"><span data-stu-id="2621f-136">The standard conversion rules will apply to a **varchar(max)** column, meaning that any conversion that is valid for a **varchar(** 2000 **)** column will also be valid for a **varchar(max)** column.</span></span> <span data-ttu-id="2621f-137">相同的規則也適用於 **nvarchar(max)** 和 **varbinary(max)** 資料行。</span><span class="sxs-lookup"><span data-stu-id="2621f-137">The same is true for **nvarchar(max)** and **varbinary(max)** columns.</span></span>  
  
 <span data-ttu-id="2621f-138">在擷取大數值類型時，最有效的方法是繫結為 DBTYPE_IUNKNOWN，並將資料列集屬性 DBPROP_ACCESSORDER 設定為 DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS。</span><span class="sxs-lookup"><span data-stu-id="2621f-138">When retrieving large value types, the most efficient approach is to bind as DBTYPE_IUNKNOWN and set the rowset property DBPROP_ACCESSORDER to DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS.</span></span> <span data-ttu-id="2621f-139">這樣會導致數值直接從網路以資料流的方式傳出，而不必經過中間的緩衝作業，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2621f-139">This will cause the value to be streamed directly from the network with no intermediate buffering, as in the following example:</span></span>  
  
```  
#define UNICODE  
#define _UNICODE  
#define DBINITCONSTANTS  
#define INITGUID  
#define OLEDBVER 0x0250  // To include the correct interfaces.  
  
#include <stdio.h>  
#include <tchar.h>  
#include <stddef.h>  
#include <iostream>  
  
using std::cout;  
using std::endl;  
  
#include <windows.h>  
  
#include <oledb.h>  
#include "sqlncli.h"  
#include <oledberr.h>  
  
#define CHKHR_GOTO(hr, errMsg, Label) \  
   if (FAILED(hr)) \  
   { \  
      cout << errMsg << endl; \  
      goto Label; \  
   }  
  
#define MAX_COL_SIZE 8000  
  
// ROUNDUP on all platforms pointers must be aligned properly.  
#define ROUNDUP_AMOUNT 8  
#define ROUNDUP_(size,amount) (((ULONG)(size)+((amount)-1))&~((amount)-1))  
#define ROUNDUP(size) ROUNDUP_(size, ROUNDUP_AMOUNT)  
  
HRESULT InitializeAndEstablishConnection(IDBInitialize** ppIDBInitialize);  
void UnInitializeConnection(IDBInitialize* pIDBInitialize);  
HRESULT CreateAndSetCommand(IDBInitialize* pIDBInitialize, ICommandText** ppICommandText);  
HRESULT ProcessResultSet(IRowset* pIRowset);  
  
void DisplayTime()  
{  
   SYSTEMTIME st;  
   GetSystemTime(&st);  
   cout<< st.wHour << ":" << st.wMinute << ":" << st.wSecond << "." << st.wMilliseconds << endl;  
}  
  
void main()  
{  
   HRESULT hr;  
   IDBInitialize* pIDBInitialize = NULL;  
   ICommandText* pICommandText = NULL;  
   IMultipleResults* pIMultipleResults = NULL;  
   IRowset* pIRowset = NULL;  
  
   hr = InitializeAndEstablishConnection(&pIDBInitialize);  
   CHKHR_GOTO(hr, L"Failed to establish connection.", _ExitMain);  
  
   hr = CreateAndSetCommand(pIDBInitialize, &pICommandText);  
   CHKHR_GOTO(hr, L"Failed to set up command object.", _ExitMain);  
  
   DisplayTime();  
  
   hr = pICommandText->Execute(NULL,   
      IID_IMultipleResults,   
      NULL,   
      NULL,   
     (IUnknown **) &pIMultipleResults);  
  
   CHKHR_GOTO(hr, L"Failed to execute command.", _ExitMain);  
  
   while (1)  
   {  
      hr = pIMultipleResults->GetResult(  
         NULL,   
         DBRESULTFLAG_DEFAULT,   
         IID_IRowset,   
         NULL,   
         (IUnknown**)&pIRowset);  
  
   CHKHR_GOTO(hr, L"Failed to obtain a results from MR object.", _ExitMain);  
  
   if (hr == DB_S_NORESULT)  
      break;  
  
      if (pIRowset)  
      {  
         hr = ProcessResultSet(pIRowset);   
         CHKHR_GOTO(hr, L"Failed to process the current Rowset.", _ExitMain);  
  
         pIRowset->Release();  
         pIRowset = NULL;  
      }  
   }  
  
   DisplayTime();  
  
_ExitMain:  
  
   if (pIRowset)  
   {  
      pIRowset->Release();  
      pIRowset = NULL;  
   }  
  
   if (pIMultipleResults)  
   {  
      pIMultipleResults->Release();  
      pIMultipleResults = NULL;  
   }  
  
   if (pICommandText)  
   {  
      pICommandText->Release();  
      pICommandText = NULL;  
   }  
  
   UnInitializeConnection(pIDBInitialize);  
   return;  
};  
  
HRESULT InitializeAndEstablishConnection(IDBInitialize** ppIDBInitialize)  
{  
   HRESULT hr;  
   IDBInitialize* pIDBInitialize = NULL;  
   IDBProperties* pIDBProperties = NULL;  
  
   const int NUM_DBINIT_PROPS = 3;  
   const wchar_t* const g_wszServer = L".";  
   const wchar_t* const g_wszCatalog = L"AdventureWorks";  
   const wchar_t* const g_wszSecurity = L"SSPI";  
  
   DBPROPSET rgdbPropSetInit[1];  
   DBPROP rgdbPropInit [NUM_DBINIT_PROPS];  
  
   *ppIDBInitialize = NULL;  
   hr = CoInitialize(NULL);  
   CHKHR_GOTO(hr, L"Failed to initialize COM.", _ExitInitialize);  
  
   hr = CoCreateInstance(CLSID_SQLNCLI11,   
      NULL,   
      CLSCTX_INPROC_SERVER,  
      IID_IDBInitialize,   
      (void**)&pIDBInitialize);  
  
   CHKHR_GOTO(hr, L"Failed to create SQLNCLI11 DataSource object.", _ExitInitialize);  
  
   for(int idxProp = 0; idxProp < NUM_DBINIT_PROPS; idxProp++)   
   {  
      VariantInit(&rgdbPropInit[idxProp].vValue);  
   }  
  
   rgdbPropInit[0].dwPropertyID = DBPROP_INIT_DATASOURCE;  
   rgdbPropInit[0].vValue.vt = VT_BSTR;  
   rgdbPropInit[0].vValue.bstrVal= SysAllocString(g_wszServer);  
   rgdbPropInit[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgdbPropInit[0].colid = DB_NULLID;  
  
   if (rgdbPropInit[0].vValue.bstrVal == NULL)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitInitialize;  
   }  
  
   rgdbPropInit[1].dwPropertyID = DBPROP_INIT_CATALOG;  
   rgdbPropInit[1].vValue.vt = VT_BSTR;  
   rgdbPropInit[1].vValue.bstrVal= SysAllocString(g_wszCatalog);  
   rgdbPropInit[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgdbPropInit[1].colid = DB_NULLID;  
  
   if (rgdbPropInit[1].vValue.bstrVal == NULL)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitInitialize;  
   }  
  
   rgdbPropInit[2].dwPropertyID = DBPROP_AUTH_INTEGRATED;  
   rgdbPropInit[2].vValue.vt = VT_BSTR;  
   rgdbPropInit[2].vValue.bstrVal= SysAllocString(g_wszSecurity);  
   rgdbPropInit[2].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgdbPropInit[2].colid = DB_NULLID;  
  
   if (rgdbPropInit[2].vValue.bstrVal == NULL)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitInitialize;  
   }  
  
   rgdbPropSetInit[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgdbPropSetInit[0].cProperties = NUM_DBINIT_PROPS;  
   rgdbPropSetInit[0].rgProperties = rgdbPropInit;  
  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);  
   CHKHR_GOTO(hr, L"Failed to QI DataSource object for IDBProperties.", _ExitInitialize);  
  
   hr = pIDBProperties->SetProperties(1, rgdbPropSetInit);   
   CHKHR_GOTO(hr, L"Failed to set DataSource object Properties.", _ExitInitialize);  
  
   pIDBProperties->Release();  
   pIDBProperties = NULL;  
  
   hr = pIDBInitialize->Initialize();  
   CHKHR_GOTO(hr, L"Failed to establish connection with the server.", _ExitInitialize);  
  
_ExitInitialize:  
  
   if (pIDBProperties)  
   {  
      pIDBProperties->Release();  
      pIDBProperties = NULL;  
   }  
  
   if (FAILED(hr))  
   {  
      if (pIDBInitialize)  
      {  
         pIDBInitialize->Release();  
         pIDBInitialize = NULL;  
      }  
   }  
  
   *ppIDBInitialize = pIDBInitialize;  
   return hr;  
}  
  
void UnInitializeConnection(IDBInitialize* pIDBInitialize)  
{  
   if (pIDBInitialize)  
   {  
      pIDBInitialize->Uninitialize();  
      pIDBInitialize->Release();  
      pIDBInitialize = NULL;  
   }  
   CoUninitialize();  
}  
  
HRESULT CreateAndSetCommand(IDBInitialize* pIDBInitialize, ICommandText** ppICommandText)  
{  
   HRESULT hr;  
   IDBCreateSession* pIDBCreateSession = NULL;  
   IDBCreateCommand* pIDBCreateCommand = NULL;  
   ICommandText* pICommandText = NULL;  
   ICommandProperties* pICommandProperties = NULL;  
   DBPROPSET rgCmdPropSet[1];  
   DBPROP rgCmdProperties[1];  
  
const wchar_t* const g_wCmdString = L"declare @x xml, @y nvarchar(max); select @x = (SELECT * FROM Sales.SalesOrderHeader FOR XML AUTO); select @x;";  
  
   *ppICommandText = NULL;  
  
   if (!pIDBInitialize)  
   {  
      hr = E_FAIL;  
      goto _ExitCreateAndSetCommand;  
   }  
  
   hr = pIDBInitialize->QueryInterface(IID_IDBCreateSession, (void**) &pIDBCreateSession);  
   CHKHR_GOTO(hr, L"Failed to obtain IDBCreateSession interface from DSO.", _ExitCreateAndSetCommand);  
  
   hr = pIDBCreateSession->CreateSession(  
      NULL,   
      IID_IDBCreateCommand,   
      (IUnknown**) &pIDBCreateCommand);  
  
   CHKHR_GOTO(hr, L"Failed to Create a Session for command execution.", _ExitCreateAndSetCommand);  
  
   hr = pIDBCreateCommand->CreateCommand(  
      NULL,   
      IID_ICommandText,   
      (IUnknown**)&pICommandText);  
  
   CHKHR_GOTO(hr, L"Failed to Create a Command object.", _ExitCreateAndSetCommand);  
  
   hr = pICommandText->SetCommandText(DBGUID_DBSQL, g_wCmdString);  
   CHKHR_GOTO(hr, L"Failed to Set Command Text.", _ExitCreateAndSetCommand);  
  
   hr = pICommandText->QueryInterface(IID_ICommandProperties, (void**) &pICommandProperties);  
   CHKHR_GOTO(hr, L"Failed to obtain ICommandProperties interface from the command object.", _ExitCreateAndSetCommand);  
  
   rgCmdProperties[0].dwPropertyID = DBPROP_ACCESSORDER;  
   rgCmdProperties[0].vValue.vt = VT_I4;  
   rgCmdProperties[0].vValue.lVal = DBPROPVAL_AO_SEQUENTIAL;  
   rgCmdProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgCmdProperties[0].colid = DB_NULLID;  
  
   rgCmdPropSet[0].guidPropertySet = DBPROPSET_ROWSET;  
   rgCmdPropSet[0].cProperties = 1;  
   rgCmdPropSet[0].rgProperties = rgCmdProperties;  
  
   hr = pICommandProperties->SetProperties(1, rgCmdPropSet);   
   CHKHR_GOTO(hr, L"Failed to Set Command object Properties.", _ExitCreateAndSetCommand);  
  
_ExitCreateAndSetCommand:  
  
   if (pICommandProperties)  
   {  
      pICommandProperties->Release();  
      pICommandProperties = NULL;  
   }  
  
   if (pIDBCreateCommand)  
   {  
      pIDBCreateCommand->Release();  
      pIDBCreateCommand = NULL;  
   }  
  
   if (pIDBCreateSession)  
   {  
      pIDBCreateSession->Release();  
      pIDBCreateSession = NULL;  
   }  
  
   if (FAILED(hr))  
   {  
      if (pICommandText)  
      {  
         pICommandText->Release();  
         pICommandText = NULL;  
      }  
   }  
  
   *ppICommandText = pICommandText;  
   return hr;  
}  
  
HRESULT ProcessResultSet(IRowset* pIRowset)  
{  
   HRESULT hr;  
  
   IColumnsInfo* pIColumnsInfo = NULL;  
   DBCOLUMNINFO* pDBColumnInfo = NULL;  
   ULONG lNumCols = 0;  
   wchar_t* pStringsBuffer = NULL;  
  
   DBBINDING* pBindings = NULL;  
   DBOBJECT dbobj;  
   ULONG idxBinding;  
   IAccessor* pIAccessor = NULL;  
   HACCESSOR hAccessor = DB_NULL_HACCESSOR;  
   HROW hRows[1] = {DB_NULL_HROW};  
   HROW* pRow = &hRows[0];  
   BYTE* pBuffer = NULL;  
  
   ULONG lNumRowsRetrieved;  
   DBLENGTH dwOffset = 0;  
  
   hr = pIRowset->QueryInterface(IID_IColumnsInfo, (void **)&pIColumnsInfo);  
   CHKHR_GOTO(hr, L"Failed to QI Rowset for IColumnsInfo.", _ExitProcessResultSet);  
  
   hr = pIColumnsInfo->GetColumnInfo(&lNumCols, &pDBColumnInfo, &pStringsBuffer);  
   CHKHR_GOTO(hr, L"Failed to obtain Column Information.", _ExitProcessResultSet);  
  
   pBindings = new DBBINDING[lNumCols];  
  
   if (!pBindings)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitProcessResultSet;  
   }  
  
   memset(pBindings, 0, sizeof(DBBINDING) * lNumCols);  
  
   dbobj.dwFlags = STGM_READ;  
   dbobj.iid = IID_ISequentialStream;  
  
   for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)   
   {  
      pBindings[idxBinding].iOrdinal = idxBinding + 1;  
      pBindings[idxBinding].obStatus = dwOffset;  
      pBindings[idxBinding].obLength = dwOffset + sizeof(DBSTATUS);  
      pBindings[idxBinding].obValue = dwOffset + sizeof(DBSTATUS) + sizeof(DBLENGTH);  
  
      pBindings[idxBinding].pTypeInfo = NULL;  
      pBindings[idxBinding].pBindExt = NULL;  
      pBindings[idxBinding].dwPart = DBPART_VALUE | DBPART_LENGTH | DBPART_STATUS;  
      pBindings[idxBinding].dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
      pBindings[idxBinding].eParamIO = DBPARAMIO_NOTPARAM;  
      pBindings[idxBinding].bPrecision = pDBColumnInfo[idxBinding].bPrecision;  
      pBindings[idxBinding].bScale = pDBColumnInfo[idxBinding].bScale;  
  
      pBindings[idxBinding].cbMaxLen = 0;  
      pBindings[idxBinding].wType = DBTYPE_WSTR;  
  
   // Determine the maximum number of bytes required in our buffer to  
   // contain the Unicode string representation of the provider's native  
   // data type, including room for the NULL-termination character  
   switch( pDBColumnInfo[idxBinding].wType )  
   {  
      case DBTYPE_NULL:  
      case DBTYPE_EMPTY:  
      case DBTYPE_I1:  
      case DBTYPE_I2:  
      case DBTYPE_I4:  
      case DBTYPE_UI1:  
      case DBTYPE_UI2:  
      case DBTYPE_UI4:  
      case DBTYPE_R4:  
      case DBTYPE_BOOL:  
      case DBTYPE_I8:  
      case DBTYPE_UI8:  
      case DBTYPE_R8:  
      case DBTYPE_CY:  
      case DBTYPE_ERROR:  
      // When the above types are converted to a string, they  
      // will all fit into 25 characters, so use that plus space  
      // for the NULL-terminator.  
  
      pBindings[idxBinding].cbMaxLen = (25 + 1) * sizeof(WCHAR);  
      break;  
  
      case DBTYPE_DECIMAL:  
      case DBTYPE_NUMERIC:  
      case DBTYPE_DATE:  
      case DBTYPE_DBDATE:  
      case DBTYPE_DBTIMESTAMP:  
      case DBTYPE_GUID:  
      // Converted to a string, the above types will all fit into  
      // 50 characters, so use that plus space for the terminator.  
  
      pBindings[idxBinding].cbMaxLen = (50 + 1) * sizeof(WCHAR);  
      break;  
  
      case DBTYPE_BYTES:  
      // In converting DBTYPE_BYTES to a string, each byte  
      // becomes two characters (e.g. 0xFF -> "FF"), so we  
      // will use double the maximum size of the column plus  
      // include space for the NULL-terminator.  
  
      pBindings[idxBinding].cbMaxLen = (pDBColumnInfo[idxBinding].ulColumnSize * 2 + 1) * sizeof(WCHAR);  
      break;  
  
      case DBTYPE_STR:  
      case DBTYPE_WSTR:  
      case DBTYPE_BSTR:  
      // Going from a string to our string representation,  
      // we can just take the maximum size of the column,  
      // a count of characters, and include space for the  
      // terminator, which is not included in the column size.  
  
      pBindings[idxBinding].cbMaxLen = (pDBColumnInfo[idxBinding].ulColumnSize + 1) * sizeof(WCHAR);  
      break;  
  
      default:  
      // For any other type, we will simply use our maximum  
      // column buffer size, since the display size of these  
      // columns may be variable (e.g. DBTYPE_VARIANT) or  
      // unknown (e.g. provider-specific types).  
      pBindings[idxBinding].cbMaxLen = MAX_COL_SIZE;  
      break;  
   }  
  
   // If the provider's native data type for this column is  
   // DBTYPE_IUNKNOWN or this is a BLOB column and the user  
   // has requested that we bind BLOB columns as ISequentialStream  
   // objects, bind this column as an ISequentialStream object if  
   // the provider supports our creating another ISequentialStream  
   // binding.  
   if(pDBColumnInfo[idxBinding].dwFlags & DBCOLUMNFLAGS_ISLONG)  
   {  
      pBindings[idxBinding].wType = DBTYPE_IUNKNOWN;  
  
      pBindings[idxBinding].cbMaxLen = sizeof(ISequentialStream*);  
  
      pBindings[idxBinding].pObject = (DBOBJECT *)CoTaskMemAlloc(sizeof(DBOBJECT));  
  
      if (!pBindings[idxBinding].pObject)  
      {  
         hr = E_OUTOFMEMORY;  
         goto _ExitProcessResultSet;  
      }  
  
      // Direct the provider to create an ISequentialStream  
      // object over the data for this column.  
      pBindings[idxBinding].pObject->iid = IID_ISequentialStream;  
  
      // We want read access on the ISequentialStream  
      // object that the provider will create for us  
      pBindings[idxBinding].pObject->dwFlags = STGM_READ;  
      }  
  
      // Ensure that the bound maximum length is no more than the  
      // maximum column size in bytes that we've defined.  
      pBindings[idxBinding].cbMaxLen = min(pBindings[idxBinding].cbMaxLen, MAX_COL_SIZE);  
  
      // Update the offset past the end of this column's data, so  
      // that the next column will begin in the correct place in  
      // the buffer.  
      dwOffset = pBindings[idxBinding].cbMaxLen + pBindings[idxBinding].obValue;  
  
      // Ensure that the data for the next column will be correctly  
      // aligned for all platforms, or, if we're done with columns,  
      // that if we allocate space for multiple rows that the data  
      // for every row is correctly aligned.  
      dwOffset = ROUNDUP(dwOffset);  
   }  
  
   hr = pIRowset->QueryInterface(IID_IAccessor, (void **) &pIAccessor);  
   CHKHR_GOTO(hr, L"Failed to obtain Accessor interface", _ExitProcessResultSet);  
  
   hr = pIAccessor->CreateAccessor(DBACCESSOR_ROWDATA,  
      lNumCols,  
      pBindings,  
      0,  
      &hAccessor,  
      NULL);  
  
   CHKHR_GOTO(hr, L"Failed to create Accessor", _ExitProcessResultSet);  
   for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)   
   {  
      cout << pDBColumnInfo[idxBinding].pwszName << endl;  
   }  
  
   lNumRowsRetrieved = 0;  
  
   hr = pIRowset->GetNextRows(  
      NULL,  
      0,  
      1,  
      &lNumRowsRetrieved,  
      &pRow);  
  
   CHKHR_GOTO(hr, L"Failed to fetch a row from the rowset", _ExitProcessResultSet);  
  
   pBuffer = new BYTE[sizeof(DBSTATUS) + sizeof(DBLENGTH) + sizeof(IUnknown*)];  
  
   if (!pBuffer)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitProcessResultSet;  
   }  
  
   while(lNumRowsRetrieved && hr != DB_S_ENDOFROWSET)   
   {  
      memset(pBuffer, 0, sizeof(DBSTATUS) + sizeof(DBLENGTH) + sizeof(IUnknown*));  
  
      hr = pIRowset->GetData(hRows[0], hAccessor, pBuffer);  
      CHKHR_GOTO(hr, L"Failed to obtain row data", _ExitProcessResultSet);  
  
      for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)  
      {  
         if (pBindings[idxBinding].wType == DBTYPE_IUNKNOWN)  
         {  
            BYTE pbBuff[3000];  
            ULONG cbNeeded = sizeof(pbBuff)/sizeof(BYTE);  
            ULONG cbRead;  
            ULONG cbReadTotal = 0;  
            ISequentialStream* pISequentialStream = NULL;  
  
            IUnknown* pIUnknown = *((IUnknown**)(pBuffer + pBindings[idxBinding].obValue));  
            pIUnknown->QueryInterface(IID_ISequentialStream, (void**)&pISequentialStream);  
  
            do  
            {  
               hr = pISequentialStream->Read(pbBuff, cbNeeded, &cbRead);  
               cbReadTotal += cbRead;  
            }  
            while (SUCCEEDED(hr) && hr != S_FALSE && cbRead == cbNeeded);  
  
               cout << "Total Bytes Read: " << cbReadTotal << endl;  
  
               pISequentialStream->Release();  
               pISequentialStream = NULL;  
               pIUnknown->Release();  
               pIUnknown = NULL;  
            }  
         }  
  
         pIRowset->ReleaseRows(1, pRow, NULL, NULL, NULL);  
  
         hr = pIRowset->GetNextRows(NULL,  
            0,  
            1,  
            &lNumRowsRetrieved,  
            &pRow);  
  
         CHKHR_GOTO(hr, L"Failed to fetch a row from the rowset.", _ExitProcessResultSet);  
   }  
  
_ExitProcessResultSet:  
  
   pIRowset->ReleaseRows(1, pRow, NULL, NULL, NULL);  
   delete [] pBuffer;  
  
   if (pIAccessor)  
   {  
      if (hAccessor != DB_NULL_HACCESSOR)  
      {  
         pIAccessor->ReleaseAccessor(hAccessor, NULL);  
      }  
  
      pIAccessor->Release();  
      pIAccessor = NULL;  
   }  
  
   if (pBindings)  
   {  
      for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)  
      {  
         if (pBindings[idxBinding].pObject)  
         CoTaskMemFree(pBindings[idxBinding].pObject);  
      }  
   }  
  
   delete [] pBindings;  
  
   CoTaskMemFree(pDBColumnInfo);  
   CoTaskMemFree(pStringsBuffer);  
  
   if (pIColumnsInfo)  
   {  
      pIColumnsInfo->Release();  
      pIColumnsInfo = NULL;  
   }  
  
   return hr;  
}  
```  
  
 <span data-ttu-id="2621f-140">如需 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者如何公開大數值資料類型的詳細資訊，請參閱[BLOB 和 OLE 物件](../../native-client-ole-db-blobs/blobs-and-ole-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="2621f-140">For more information about how the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes large value data types, see [BLOBs and OLE Objects](../../native-client-ole-db-blobs/blobs-and-ole-objects.md).</span></span>  
  
## <a name="sql-server-native-client-odbc-driver"></a><span data-ttu-id="2621f-141">SQL Server Native Client ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="2621f-141">SQL Server Native Client ODBC Driver</span></span>  
 <span data-ttu-id="2621f-142">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會在接受或傳回 ODBC SQL 資料類型的 ODBC API 函式中，公開\*\*Varchar (max) \*\*、 \*\*Varbinary (max) **和**Nvarchar (max) \*\*類型做為 SQL_VARCHAR、SQL_VARBINARY 和 SQL_WVARCHAR。</span><span class="sxs-lookup"><span data-stu-id="2621f-142">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver exposes the **varchar(max)**, **varbinary(max)** and **nvarchar(max)** types as SQL_VARCHAR, SQL_VARBINARY, and SQL_WVARCHAR in ODBC API functions that accept or return ODBC SQL data types.</span></span>  
  
 <span data-ttu-id="2621f-143">在報告資料行的最大大小時，驅動程式會報告下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="2621f-143">When reporting the maximum size of a column, the driver will report either:</span></span>  
  
-   <span data-ttu-id="2621f-144">為\*\*Varchar (2000) \*\*資料行定義的大小上限（例如）為2000，或</span><span class="sxs-lookup"><span data-stu-id="2621f-144">The defined maximum size, which for example, is 2000 for a **varchar(2000)** column, or</span></span>  
  
-   <span data-ttu-id="2621f-145">值「無限制」，在\*\*Varchar (max) \*\*資料行等於0的情況下。</span><span class="sxs-lookup"><span data-stu-id="2621f-145">The value "unlimited" which in the case of a **varchar(max)** column equals 0.</span></span>  
  
 <span data-ttu-id="2621f-146">標準轉換規則適用于**Varchar (max) **資料行，這表示任何對**Varchar (** 2000 \*\*) **資料行有效的轉換也會對**Varchar (max) \*\*資料行有效。</span><span class="sxs-lookup"><span data-stu-id="2621f-146">The standard conversion rules apply to a **varchar(max)** column, meaning that any conversion that is valid for a **varchar(** 2000 **)** column will also be valid for a **varchar(max)** column.</span></span> <span data-ttu-id="2621f-147">相同的規則也適用於 **nvarchar(max)** 和 **varbinary(max)** 資料行。</span><span class="sxs-lookup"><span data-stu-id="2621f-147">The same is true for **nvarchar(max)** and **varbinary(max)** columns.</span></span>  
  
 <span data-ttu-id="2621f-148">下列是 ODBC API 函數的清單，這些函數經過改良，可用於大數值資料類型：</span><span class="sxs-lookup"><span data-stu-id="2621f-148">The following is a list of the ODBC API functions that have been enhanced to work with large value data types:</span></span>  
  
-   [<span data-ttu-id="2621f-149">SQLBindCol</span><span class="sxs-lookup"><span data-stu-id="2621f-149">SQLBindCol</span></span>](../../native-client-odbc-api/sqlbindcol.md)  
  
-   [<span data-ttu-id="2621f-150">SQLBindParameter</span><span class="sxs-lookup"><span data-stu-id="2621f-150">SQLBindParameter</span></span>](../../native-client-odbc-api/sqlbindparameter.md)  
  
-   [<span data-ttu-id="2621f-151">SQLColAttribute</span><span class="sxs-lookup"><span data-stu-id="2621f-151">SQLColAttribute</span></span>](../../native-client-odbc-api/sqlcolattribute.md)  
  
-   [<span data-ttu-id="2621f-152">SQLColumns</span><span class="sxs-lookup"><span data-stu-id="2621f-152">SQLColumns</span></span>](../../native-client-odbc-api/sqlcolumns.md)  
  
-   [<span data-ttu-id="2621f-153">SQLDescribeCol</span><span class="sxs-lookup"><span data-stu-id="2621f-153">SQLDescribeCol</span></span>](../../native-client-odbc-api/sqldescribecol.md)  
  
-   [<span data-ttu-id="2621f-154">SQLDescribeParam</span><span class="sxs-lookup"><span data-stu-id="2621f-154">SQLDescribeParam</span></span>](../../native-client-odbc-api/sqldescribeparam.md)  
  
-   [<span data-ttu-id="2621f-155">SQLGetData</span><span class="sxs-lookup"><span data-stu-id="2621f-155">SQLGetData</span></span>](../../native-client-odbc-api/sqlgetdata.md)  
  
-   [<span data-ttu-id="2621f-156">SQLGetTypeInfo</span><span class="sxs-lookup"><span data-stu-id="2621f-156">SQLGetTypeInfo</span></span>](../../native-client-odbc-api/sqlgettypeinfo.md)  
  
## <a name="see-also"></a><span data-ttu-id="2621f-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2621f-157">See Also</span></span>  
 [<span data-ttu-id="2621f-158">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="2621f-158">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
