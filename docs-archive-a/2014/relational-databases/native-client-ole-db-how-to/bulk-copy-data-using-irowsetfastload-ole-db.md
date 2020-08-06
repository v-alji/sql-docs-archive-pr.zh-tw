---
title: 使用 IRowsetFastLoad 大量複製資料 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- bulk copy [ODBC]
- bulk copy [ODBC], data files
- bulk copy [ODBC], about bulk copy
ms.assetid: 0b8908d1-fd6d-47a9-9e30-514cee8f60c8
author: rothja
ms.author: jroth
ms.openlocfilehash: f3f336e33b34d538f858e1e20c506f44da7ebdec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702902"
---
# <a name="bulk-copy-data-using-irowsetfastload-ole-db"></a><span data-ttu-id="47456-102">使用 IRowsetFastLoad 大量複製資料 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="47456-102">Bulk Copy Data Using IRowsetFastLoad (OLE DB)</span></span>
  <span data-ttu-id="47456-103">此範例會示範如何使用 IRowsetFastLoad，將記錄大量複製到資料表中。</span><span class="sxs-lookup"><span data-stu-id="47456-103">This sample shows the use of IRowsetFastLoad for bulk copying of records into a table.</span></span>  
  
 <span data-ttu-id="47456-104">取用者會將其大量複製的需求通知 SQLOLEDB，方法是將 SQLOLEDB 提供者特有的屬性 SSPROP_ENABLEFASTLOAD 設定為 VARIANT_TRUE。</span><span class="sxs-lookup"><span data-stu-id="47456-104">The consumer notifies SQLOLEDB of its need for bulk copying by setting the SQLOLEDB provider-specific property SSPROP_ENABLEFASTLOAD to VARIANT_TRUE.</span></span> <span data-ttu-id="47456-105">在資料來源上設定該屬性後，取用者會建立 SQLOLEDB 工作階段。</span><span class="sxs-lookup"><span data-stu-id="47456-105">With the property set on the data source, the consumer creates a SQLOLEDB session.</span></span> <span data-ttu-id="47456-106">新的工作階段可以讓取用者存取 `IRowsetFastLoad`。</span><span class="sxs-lookup"><span data-stu-id="47456-106">The new session allows the consumer access to `IRowsetFastLoad`.</span></span>  
  
 <span data-ttu-id="47456-107">完整的範例會示範使用 `IRowsetFastLoad` 將記錄大量複製到資料表中。</span><span class="sxs-lookup"><span data-stu-id="47456-107">A complete sample is available that illustrates the use of `IRowsetFastLoad` for bulk copying of the records into a table.</span></span> <span data-ttu-id="47456-108">在這個範例中，10 筆記錄會加入至資料表 **IRFLTable**。</span><span class="sxs-lookup"><span data-stu-id="47456-108">In this sample, 10 records are added to the table **IRFLTable**.</span></span> <span data-ttu-id="47456-109">您必須在資料庫中建立資料表**IRFLTable** 。</span><span class="sxs-lookup"><span data-stu-id="47456-109">You need to create the table **IRFLTable** in the database.</span></span>  
  
 <span data-ttu-id="47456-110">此範例需要 AdventureWorks 範例資料庫，您可以從 [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) (Microsoft SQL Server 範例和社群專案首頁) 下載。</span><span class="sxs-lookup"><span data-stu-id="47456-110">This sample requires the AdventureWorks sample database, which you can download from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="47456-111">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="47456-111">When possible, use Windows Authentication.</span></span> <span data-ttu-id="47456-112">如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。</span><span class="sxs-lookup"><span data-stu-id="47456-112">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="47456-113">請避免將認證儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="47456-113">Avoid storing credentials in a file.</span></span> <span data-ttu-id="47456-114">如果您必須保存認證，您應該使用[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)將它們加密。</span><span class="sxs-lookup"><span data-stu-id="47456-114">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-bulk-copy-data-into-a-sql-server-table"></a><span data-ttu-id="47456-115">若要大量複製資料到 SQL Server 資料表中</span><span class="sxs-lookup"><span data-stu-id="47456-115">To bulk copy data into a SQL Server table</span></span>  
  
1.  <span data-ttu-id="47456-116">建立資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="47456-116">Establish a connection to the data source.</span></span>  
  
2.  <span data-ttu-id="47456-117">將 SQLOLEDB 提供者特有的資料來源屬性 SSPROP_ENABLEFASTLOAD 設定為 VARIANT_TRUE。</span><span class="sxs-lookup"><span data-stu-id="47456-117">Set the SQLOLEDB provider-specific data source property SSPROP_ENABLEFASTLOAD to VARIANT_TRUE.</span></span> <span data-ttu-id="47456-118">當這個屬性設定為 VARIANT_TRUE 之後，新建立的工作階段就會允許使用者存取 `IRowsetFastLoad`。</span><span class="sxs-lookup"><span data-stu-id="47456-118">With this property set to VARIANT_TRUE, the newly created session allows the consumer access to `IRowsetFastLoad`.</span></span>  
  
3.  <span data-ttu-id="47456-119">建立要求 `IOpenRowset` 介面的工作階段。</span><span class="sxs-lookup"><span data-stu-id="47456-119">Create a session requesting the `IOpenRowset` interface.</span></span>  
  
4.  <span data-ttu-id="47456-120">呼叫 `IOpenRowset::OpenRowset`，以便開啟包含資料表中所有資料列的資料列集 (使用大量複製作業複製資料)。</span><span class="sxs-lookup"><span data-stu-id="47456-120">Call `IOpenRowset::OpenRowset` to open a rowset that includes all the rows from the table (in which data is to be copied using bulk-copy operation).</span></span>  
  
5.  <span data-ttu-id="47456-121">進行必要的繫結，並且使用 `IAccessor::CreateAccessor` 來建立存取子。</span><span class="sxs-lookup"><span data-stu-id="47456-121">Do the necessary bindings and create an accessor using `IAccessor::CreateAccessor`.</span></span>  
  
6.  <span data-ttu-id="47456-122">設定要將資料複製到資料表的來源記憶體緩衝區。</span><span class="sxs-lookup"><span data-stu-id="47456-122">Set up the memory buffer from which the data will be copied to the table.</span></span>  
  
7.  <span data-ttu-id="47456-123">呼叫 `IRowsetFastLoad::InsertRow`，以便大量複製資料到資料表中。</span><span class="sxs-lookup"><span data-stu-id="47456-123">Call `IRowsetFastLoad::InsertRow` to bulk copy the data in to the table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47456-124">範例</span><span class="sxs-lookup"><span data-stu-id="47456-124">Example</span></span>  
 <span data-ttu-id="47456-125">在這個範例中，10 筆記錄會加入至資料表 IRFLTable。</span><span class="sxs-lookup"><span data-stu-id="47456-125">In this example, 10 records are added to the table IRFLTable.</span></span> <span data-ttu-id="47456-126">您必須在資料庫中建立資料表 IRFLTable。</span><span class="sxs-lookup"><span data-stu-id="47456-126">You need to create the table IRFLTable in the database.</span></span> <span data-ttu-id="47456-127">IA64 不支援此範例。</span><span class="sxs-lookup"><span data-stu-id="47456-127">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="47456-128">執行第一個 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 程式碼清單，以便建立應用程式所使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="47456-128">Execute the first ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing to create the table used by the application.</span></span>  
  
 <span data-ttu-id="47456-129">使用 ole32.lib oleaut32.lib 編譯並執行下列 C++ 程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="47456-129">Compile with ole32.lib oleaut32.lib and execute the following C++ code listing.</span></span> <span data-ttu-id="47456-130">這個應用程式會連接到電腦的預設 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="47456-130">This application connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="47456-131">在某些 Windows 作業系統上，您必須將 (localhost) 或 (local) 變更為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="47456-131">On some Windows operating systems, you will need to change (localhost) or (local) to the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="47456-132">若要連線到具名執行個體，請將連接字串從 L"(local)" 變更為 L"(local)\\\name"，其中 name 是具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="47456-132">To connect to a named instance, change the connection string from L"(local)" to L"(local)\\\name" , where name is the named instance.</span></span> <span data-ttu-id="47456-133">根據預設，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 會安裝至具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="47456-133">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express installs to a named instance.</span></span> <span data-ttu-id="47456-134">請確認您的 INCLUDE 環境變數包含的目錄內含 sqlncli.h。</span><span class="sxs-lookup"><span data-stu-id="47456-134">Make sure your INCLUDE environment variable includes the directory that contains sqlncli.h.</span></span>  
  
 <span data-ttu-id="47456-135">執行第三個 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 程式碼清單，以便刪除應用程式所使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="47456-135">Execute the third ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing to delete the table used by the application.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'IRFLTable')  
     DROP TABLE IRFLTable  
GO  
  
CREATE TABLE IRFLTable (col_vchar varchar(30))  
```  
  
```  
// compile with: ole32.lib oleaut32.lib  
#define DBINITCONSTANTS  
#define OLEDBVER 0x0250   // to include correct interfaces  
  
#include <oledb.h>  
#include <oledberr.h>  
#include <stdio.h>  
#include <stddef.h>   // for offsetof  
#include <sqlncli.h>  
  
// @type UWORD    | 2 byte unsigned integer.  
typedef unsigned short UWORD;  
  
// @type SDWORD   | 4 byte signed integer.  
typedef signed long SDWORD;  
  
WCHAR g_wszTable[] = L"IRFLTable";  
WCHAR g_strTestLOC[100] = L"localhost";  
WCHAR g_strTestDBName[] = L"AdventureWorks";  
const UWORD g_cOPTION = 4;  
const UWORD MAXPROPERTIES = 5;  
const ULONG DEFAULT_CBMAXLENGTH = 20;  
IMalloc* g_pIMalloc = NULL;  
IDBInitialize* g_pIDBInitialize = NULL;  
  
// Given an ICommand pointer, properties, and query, a rowsetpointer is returned.  
HRESULT CreateSessionCommand( DBPROPSET* rgPropertySets, ULONG ulcPropCount, CLSID clsidProv );  
  
// Use to set properties and execute a given query.  
HRESULT ExecuteQuery ( IDBCreateCommand* pIDBCreateCommand,  
                       WCHAR* pwszQuery,  
                       DBPROPSET* rgPropertySets,  
                       ULONG ulcPropCount,   
                       LONG* pcRowsAffected,  
                       IRowset** ppIRowset,  
                       BOOL fSuccessOnly = TRUE );  
  
// Use to set up options for call to IDBInitialize::Initialize.  
void SetupOption ( DBPROPID PropID, WCHAR *wszVal, DBPROP * pDBProp );  
  
// Sets fastload property on/off for session.  
HRESULT SetFastLoadProperty(BOOL fSet);  
  
// IRowsetFastLoad inserting data.  
HRESULT FastLoadData();  
  
// How to lay out each column in memory.  
struct COLUMNDATA {  
   DBLENGTH dwLength;   // Length of data (not space allocated).  
   DWORD dwStatus;   // Status of column.  
   BYTE bData[1];   // Store data here as a variant.  
};  
  
#define COLUMN_ALIGNVAL 8  
  
#define ROUND_UP(Size, Amount)(((DWORD)(Size) + ((Amount)-1)) & ~((Amount)-1))  
  
int main() {  
   HRESULT hr = NOERROR;  
   HRESULT hr2 = NOERROR;  
  
   // OLE initialized?  
   BOOL fInitialized = FALSE;  
  
   // One property set for initializing.  
   DBPROPSET rgPropertySets[1];  
  
   // Properties within above property set.  
   DBPROP rgDBProperties[g_cOPTION];   
  
   IDBCreateCommand* pIDBCreateCommand = NULL;  
   IRowset* pIRowset = NULL;  
   DBPROPSET* rgProperties = NULL;  
   IAccessor* pIAccessor = NULL;  
  
   // Basic initialization.  
   if ( FAILED(CoInitialize(NULL)) )  
      goto cleanup;  
   else  
      fInitialized = TRUE;  
  
   hr = CoGetMalloc(MEMCTX_TASK, &g_pIMalloc);  
   if ((!g_pIMalloc) || FAILED(hr))  
      goto cleanup;  
  
   // Set up property set for call to IDBInitialize in CreateSessionCommand.  
   rgPropertySets[0].rgProperties = rgDBProperties;  
   rgPropertySets[0].cProperties = g_cOPTION;  
   rgPropertySets[0].guidPropertySet = DBPROPSET_DBINIT;  
  
   SetupOption(DBPROP_INIT_CATALOG, g_strTestDBName, &rgDBProperties[0]);  
  
   SetupOption(DBPROP_AUTH_INTEGRATED, L"SSPI", &rgDBProperties[1]);  
  
   SetupOption(DBPROP_INIT_DATASOURCE, g_strTestLOC, &rgDBProperties[3]);  
  
   if (!SUCCEEDED( hr = CreateSessionCommand(rgPropertySets, 1, CLSID_SQLNCLI11)))  
      goto cleanup;  
  
   // Get IRowsetFastLoad and insert data into IRFLTable.  
   if (FAILED(hr = FastLoadData()))  
      goto cleanup;  
  
cleanup:  
   // Release memory.  
   if (rgProperties && rgProperties->rgProperties)  
      delete [](rgProperties->rgProperties);  
   if (rgProperties)  
      delete []rgProperties;  
   if (pIDBCreateCommand)  
      pIDBCreateCommand->Release();  
  
   if (pIAccessor)  
      pIAccessor->Release();  
  
   if (pIRowset)  
      pIRowset->Release();  
   if (g_pIMalloc)  
      g_pIMalloc->Release();  
  
   if (g_pIDBInitialize) {      
      hr2 = g_pIDBInitialize->Uninitialize();  
      if (FAILED(hr2))  
         printf("Uninitialize failed\n");  
   }  
  
   if (fInitialized)  
      CoUninitialize();  
  
   if (SUCCEEDED(hr))  
      printf("Test completed successfully.\n\n");  
   else  
      printf("Test failed.\n\n");  
}  
  
HRESULT FastLoadData() {  
   HRESULT hr = E_FAIL;  
   HRESULT hr2 = E_FAIL;  
   DBID TableID;  
  
   IDBCreateSession* pIDBCreateSession = NULL;  
   IOpenRowset* pIOpenRowsetFL = NULL;  
   IRowsetFastLoad* pIFastLoad = NULL;  
  
   IAccessor* pIAccessor = NULL;  
   HACCESSOR hAccessor = 0;  
   DBBINDSTATUS oneStatus = 0;  
  
   DBBINDING oneBinding;  
   ULONG ulOffset = 0;  
   TableID.uName.pwszName = NULL;  
   LONG i = 0;  
   void* pData = NULL;  
   COLUMNDATA* pcolData = NULL;  
  
   TableID.eKind = DBKIND_NAME;  
   // if ( !(TableID.uName.pwszName = new WCHAR[wcslen(g_wszTable) + 2]) )  
   LPOLESTR x = TableID.uName.pwszName = new WCHAR[wcslen(g_wszTable) + 2];  
   if (!x)  
      return E_FAIL;  
   wcsncpy_s(TableID.uName.pwszName, wcslen(g_wszTable) + 2, g_wszTable, wcslen(g_wszTable)+1);  
   TableID.uName.pwszName[wcslen(g_wszTable)+1] = (WCHAR) NULL;  
  
   // Get the fastload pointer.  
   if (FAILED(hr = SetFastLoadProperty(TRUE)))  
      goto cleanup;  
  
   if ( FAILED( hr =   
      g_pIDBInitialize->QueryInterface( IID_IDBCreateSession, (void **) &pIDBCreateSession )))  
      goto cleanup;  
  
   if ( FAILED( hr =   
      pIDBCreateSession->CreateSession( NULL, IID_IOpenRowset, (IUnknown **) &pIOpenRowsetFL )))  
      goto cleanup;  
  
   // Get IRowsetFastLoad initialized to use the test table.  
   if (FAILED(hr =   
      pIOpenRowsetFL->OpenRowset(NULL,   
                                 &TableID,   
                                 NULL,   
                                 IID_IRowsetFastLoad,   
                                 0,   
                                 NULL,   
                                 (LPUNKNOWN *)&pIFastLoad)))  
      goto cleanup;  
  
   // Set up custom bindings.  
   oneBinding.dwPart = DBPART_VALUE | DBPART_LENGTH | DBPART_STATUS;  
   oneBinding.iOrdinal = 1;  
   oneBinding.pTypeInfo = NULL;  
   oneBinding.obValue = ulOffset + offsetof(COLUMNDATA,bData);  
   oneBinding.obLength = ulOffset + offsetof(COLUMNDATA,dwLength);  
   oneBinding.obStatus = ulOffset + offsetof(COLUMNDATA,dwStatus);  
   oneBinding.cbMaxLen = 30;   // Size of varchar column.  
   oneBinding.pTypeInfo = NULL;  
   oneBinding.pObject = NULL;  
   oneBinding.pBindExt = NULL;  
   oneBinding.dwFlags = 0;  
   oneBinding.eParamIO = DBPARAMIO_NOTPARAM;  
   oneBinding.dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
   oneBinding.bPrecision= 0;     
   oneBinding.bScale = 0;    
   oneBinding.wType = DBTYPE_STR;    
   ulOffset = oneBinding.cbMaxLen + offsetof(COLUMNDATA, bData);  
   ulOffset = ROUND_UP( ulOffset, COLUMN_ALIGNVAL );  
  
   if ( FAILED( hr =   
      pIFastLoad->QueryInterface(IID_IAccessor, (void **) &pIAccessor)))   
      return hr;  
  
   if (FAILED(hr = pIAccessor->CreateAccessor( DBACCESSOR_ROWDATA,   
                                               1,   
                                               &oneBinding,   
                                               ulOffset,   
                                               &hAccessor,   
                                               &oneStatus)))  
      return hr;  
  
   // Set up memory buffer.  
   pData = new BYTE[40];  
   if (!(pData /* = new BYTE[40]*/ )) {  
      hr = E_FAIL;  
      goto cleanup;  
   }  
  
   pcolData = (COLUMNDATA*)pData;  
   pcolData->dwLength = (SDWORD)strlen("Show the data") + 1;  
   pcolData->dwStatus = 0;  
   memcpy(&(pcolData->bData), "Show the data", strlen("Show the data") + 1);  
  
   for ( i = 0 ; i < 10 ; i++ )  
      if (FAILED(hr = pIFastLoad->InsertRow(hAccessor, pData)))  
         goto cleanup;  
  
   if (FAILED(hr = pIFastLoad->Commit(TRUE)))  
      printf("Error on IRFL::Commit\n");  
  
cleanup:  
   if (FAILED(hr2 = SetFastLoadProperty(FALSE)))  
      printf("SetFastLoadProperty(FALSE) failed with %x", hr2);  
  
   if (pIAccessor && hAccessor)  
      if (FAILED(pIAccessor->ReleaseAccessor(hAccessor, NULL)))  
         hr = E_FAIL;  
  
   if (pIAccessor)  
      pIAccessor->Release();  
  
   if (pIFastLoad)  
      pIFastLoad->Release();  
  
   if (pIOpenRowsetFL)  
      pIOpenRowsetFL->Release();  
  
   if (pIDBCreateSession)  
      pIDBCreateSession->Release();  
  
   if (TableID.uName.pwszName)  
      delete []TableID.uName.pwszName;  
  
   return hr;  
}  
  
HRESULT SetFastLoadProperty(BOOL fSet) {  
   HRESULT hr = S_OK;  
   IDBProperties* pIDBProps = NULL;  
   DBPROP rgProps[1];  
   DBPROPSET PropSet;  
  
   VariantInit(&rgProps[0].vValue);  
  
   rgProps[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgProps[0].colid = DB_NULLID;  
   rgProps[0].vValue.vt = VT_BOOL;  
   rgProps[0].dwPropertyID = SSPROP_ENABLEFASTLOAD;  
  
   if (fSet == TRUE)  
      rgProps[0].vValue.boolVal = VARIANT_TRUE;  
   else  
      rgProps[0].vValue.boolVal = VARIANT_FALSE;  
  
   PropSet.rgProperties = rgProps;  
   PropSet.cProperties = 1;  
   PropSet.guidPropertySet = DBPROPSET_SQLSERVERDATASOURCE;  
  
   if (SUCCEEDED(hr = g_pIDBInitialize->QueryInterface(IID_IDBProperties, (LPVOID *)&pIDBProps)))  
      hr = pIDBProps->SetProperties(1, &PropSet);  
  
   VariantClear(&rgProps[0].vValue);   
  
   if (pIDBProps)  
      pIDBProps->Release();  
  
   return hr;  
}  
  
HRESULT CreateSessionCommand( DBPROPSET* rgPropertySets,// @parm [in] property sets  
                              ULONG ulcPropCount,   // @parm [in] count of prop sets.  
                              CLSID clsidProv) {  // @parm [in] Provider CLSID.  
  
   HRESULT hr = NOERROR;  
   IDBCreateSession* pIDBCreateSession = NULL;  
   IDBProperties* pIDBProperties = NULL;  
   UWORD i = 0, j = 0;   // indexes.  
  
   if (ulcPropCount && !rgPropertySets) {  
      hr = E_INVALIDARG;  
      return hr;  
   }  
  
   if (!SUCCEEDED(hr = CoCreateInstance(clsidProv,   
                                        NULL,CLSCTX_INPROC_SERVER,  
                                        IID_IDBInitialize,  
                                        (void **)&g_pIDBInitialize)))  
      goto CLEANUP;  
  
   if (!SUCCEEDED(hr = g_pIDBInitialize->QueryInterface( IID_IDBProperties,  
                                                         (void **)&pIDBProperties)))  
      goto CLEANUP;  
  
   if (!SUCCEEDED(hr = pIDBProperties->SetProperties(ulcPropCount, rgPropertySets)))  
      goto CLEANUP;  
  
   if (!SUCCEEDED(hr = g_pIDBInitialize->Initialize())) {  
      printf("Call to initialize failed.\n");  
      goto CLEANUP;  
   }  
  
CLEANUP:  
   if (pIDBProperties)  
      pIDBProperties->Release();  
   if (pIDBCreateSession)  
      pIDBCreateSession->Release();  
  
   for (i = 0 ; i < ulcPropCount ; i++)  
      for (j = 0 ; j < rgPropertySets[i].cProperties ; j++)  
         VariantClear(&(rgPropertySets[i].rgProperties[j]).vValue);  
   return hr;  
}  
  
void SetupOption (DBPROPID PropID, WCHAR *wszVal, DBPROP * pDBProp ) {  
   pDBProp->dwPropertyID = PropID;  
   pDBProp->dwOptions = DBPROPOPTIONS_REQUIRED;  
   pDBProp->colid = DB_NULLID;  
   pDBProp->vValue.vt = VT_BSTR;  
   pDBProp->vValue.bstrVal = SysAllocStringLen(wszVal, wcslen(wszVal));  
}  
```  
  
```  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'IRFLTable')  
     DROP TABLE IRFLTable  
GO  
```  
  
  
