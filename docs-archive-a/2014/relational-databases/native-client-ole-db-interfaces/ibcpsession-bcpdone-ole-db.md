---
title: IBCPSession::BCPDone (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPDone (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPDone method
ms.assetid: 19cd6e55-432a-450e-a15c-54d50eb53dee
author: rothja
ms.author: jroth
ms.openlocfilehash: f67b0d525d535b9b68e671777de694adfa4deb01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599504"
---
# <a name="ibcpsessionbcpdone-ole-db"></a><span data-ttu-id="95f0e-102">IBCPSession::BCPDone (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="95f0e-102">IBCPSession::BCPDone (OLE DB)</span></span>
  <span data-ttu-id="95f0e-103">認可要傳送至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的其餘資料列。</span><span class="sxs-lookup"><span data-stu-id="95f0e-103">Commits the remaining rows to be sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95f0e-104">語法</span><span class="sxs-lookup"><span data-stu-id="95f0e-104">Syntax</span></span>  
  
```  
  
HRESULT BCPDone(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="95f0e-105">備註</span><span class="sxs-lookup"><span data-stu-id="95f0e-105">Remarks</span></span>  
 <span data-ttu-id="95f0e-106">呼叫 **BCPDone** 方法之後，您就無法針對 [IBCPSession](ibcpsession-ole-db.md) 介面呼叫任何其他作業。</span><span class="sxs-lookup"><span data-stu-id="95f0e-106">No other operation can be called on the [IBCPSession](ibcpsession-ole-db.md) interface after calling the **BCPDone** method.</span></span> <span data-ttu-id="95f0e-107">唯一的可能性是呼叫 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 方法來起始新的大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="95f0e-107">The only possibility is to call the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method to initiate a new bulk copy operation.</span></span> <span data-ttu-id="95f0e-108">這就類似於呼叫 [IRowsetFastLoad::Commit](irowsetfastload-commit-ole-db.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="95f0e-108">This is similar to calling the [IRowsetFastLoad::Commit](irowsetfastload-commit-ole-db.md) method.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="95f0e-109">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="95f0e-109">Return Code Values</span></span>  
 <span data-ttu-id="95f0e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="95f0e-110">S_OK</span></span>  
 <span data-ttu-id="95f0e-111">此方法已成功。</span><span class="sxs-lookup"><span data-stu-id="95f0e-111">The method succeeded.</span></span>  
  
 <span data-ttu-id="95f0e-112">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="95f0e-112">E_UNEXPECTED</span></span>  
 <span data-ttu-id="95f0e-113">此方法的呼叫是非預期的。</span><span class="sxs-lookup"><span data-stu-id="95f0e-113">The call to the method was unexpected.</span></span> <span data-ttu-id="95f0e-114">例如，在呼叫這個方法之前，不會呼叫 **BCPInit** 方法。</span><span class="sxs-lookup"><span data-stu-id="95f0e-114">For example, the **BCPInit** method was not called before calling this method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95f0e-115">範例</span><span class="sxs-lookup"><span data-stu-id="95f0e-115">Example</span></span>  
 <span data-ttu-id="95f0e-116">此範例會示範如何使用 **IBCPSession** 介面。</span><span class="sxs-lookup"><span data-stu-id="95f0e-116">This sample shows how to use the **IBCPSession** interface.</span></span>  
  
 <span data-ttu-id="95f0e-117">在執行這個範例之前，必須先執行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="95f0e-117">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] must be executed before running this sample:</span></span>  
  
```  
create table fltest(col1 int, col2 int, col3 image)  
insert into fltest values (1, 1, 0x0FF)  
insert into fltest values (2, 2, 0xF00)  
insert into fltest values (3, 3, 0xBAD)  
insert into fltest values (4, 4, 0xFAD)  
```  
  
 <span data-ttu-id="95f0e-118">此範例會連接到 master 資料庫。</span><span class="sxs-lookup"><span data-stu-id="95f0e-118">The sample connects to the master database.</span></span>  
  
 <span data-ttu-id="95f0e-119">當此範例執行時，它會在專案目錄中建立 outfile.dat。</span><span class="sxs-lookup"><span data-stu-id="95f0e-119">When the sample runs, it creates outfile.dat in the project directory.</span></span> <span data-ttu-id="95f0e-120">outfile.dat 會包含在原生 (二進位) 模式下從資料表複製的資料。</span><span class="sxs-lookup"><span data-stu-id="95f0e-120">The outfile.dat contains the data copied from the table in native (binary) mode.</span></span>  
  
 <span data-ttu-id="95f0e-121">您應該使用 BCP，透過下列命令將這份資料新增回資料表中：</span><span class="sxs-lookup"><span data-stu-id="95f0e-121">You could use BCP to add this data back into the table with the following command:</span></span>  
  
 <span data-ttu-id="95f0e-122">**bcp master..fltest in outfile.dat -n -T -S** *伺服器*</span><span class="sxs-lookup"><span data-stu-id="95f0e-122">**bcp master..fltest in outfile.dat -n -T -S** *server*</span></span>  
  
 <span data-ttu-id="95f0e-123">編譯此範例時，將會需要指定 sqlncli11.lib。</span><span class="sxs-lookup"><span data-stu-id="95f0e-123">You will need to specify sqlncli11.lib when compiling this sample.</span></span>  
  
```  
#define DBINITCONSTANTS   // Defined to initialize constants in oledb.h  
#define INITGUID  
#define MAX_ROWS  100  
  
#include <windows.h>  
#include <sqlext.h>  
#include <sqlncli.h>  
#include <oledberr.h>  
#include <stdio.h>  
  
#define SAFE_RELEASE(p) { \  
   if (p) { \  
   (p)->Release(); \  
   (p)=NULL; \  
   } \  
}  
  
// DumpErrorInfo queries error interfaces, retrieving available status or error information.  
void DumpErrorInfo ( IUnknown* pObjectWithError, REFIID IID_InterfaceWithError ) {  
   // Interfaces used in the example.  
   IErrorInfo * pIErrorInfoAll = NULL;  
   IErrorInfo * pIErrorInfoRecord = NULL;  
   IErrorRecords * pIErrorRecords = NULL;  
   ISupportErrorInfo * pISupportErrorInfo = NULL;  
   ISQLErrorInfo * pISQLErrorInfo = NULL;  
   ISQLServerErrorInfo * pISQLServerErrorInfo = NULL;  
  
   // Number of error records.  
   ULONG nRecs;  
   ULONG nRec;  
  
   // Basic error information from GetBasicErrorInfo.  
   ERRORINFO errorinfo;  
  
   // IErrorInfo values.  
   BSTR bstrDescription;  
   BSTR bstrSource;  
  
   // ISQLErrorInfo parameters.  
   BSTR bstrSQLSTATE;  
   LONG lNativeError;  
  
   // ISQLServerErrorInfo parameter pointers.  
   SSERRORINFO * pSSErrorInfo = NULL;  
   OLECHAR * pSSErrorStrings = NULL;  
  
   // Hard-code a US English locale for the example.  
   DWORD MYLOCALEID = 0x0409;  
  
   // Only ask for error information if the interface supports it.  
   if (FAILED(pObjectWithError->QueryInterface(IID_ISupportErrorInfo, (void**) &pISupportErrorInfo))) {  
      wprintf(L"SupportErrorErrorInfo interface not supported\r\n");  
      return;  
   }  
  
   if (FAILED(pISupportErrorInfo->InterfaceSupportsErrorInfo(IID_InterfaceWithError))) {  
      wprintf(L"InterfaceWithError interface not supported\r\n");  
      return;  
   }  
  
   // Do not test the return of GetErrorInfo. It can succeed and return  
   // a NULL pointer in pIErrorInfoAll. Simply test the pointer.  
   GetErrorInfo(0, &pIErrorInfoAll);  
  
   if (pIErrorInfoAll != NULL) {  
      // Test to see if it's a valid OLE DB IErrorInfo interface exposing a list of records.  
      if (SUCCEEDED(pIErrorInfoAll->QueryInterface(IID_IErrorRecords, (void**) &pIErrorRecords))) {  
         pIErrorRecords->GetRecordCount(&nRecs);  
  
         // Within each record, retrieve information from each of the defined interfaces.  
         for (nRec = 0; nRec < nRecs; nRec++) {  
            // From IErrorRecords, get the HRESULT and a reference to the ISQLErrorInfo interface.  
            pIErrorRecords->GetBasicErrorInfo(nRec, &errorinfo);  
            pIErrorRecords->GetCustomErrorObject(nRec,IID_ISQLErrorInfo, (IUnknown**) &pISQLErrorInfo);  
  
            // Display the HRESULT, then use the ISQLErrorInfo.  
            wprintf(L"HRESULT:\t%#X\r\n", errorinfo.hrError);  
  
            if (pISQLErrorInfo != NULL) {  
               pISQLErrorInfo->GetSQLInfo(&bstrSQLSTATE, &lNativeError);  
  
               // Display the SQLSTATE and native error values.  
               wprintf(L"SQLSTATE:\t%s\r\nNative Error:\t%ld\r\n", bstrSQLSTATE, lNativeError);  
  
               // SysFree BSTR references.  
               SysFreeString(bstrSQLSTATE);  
  
               // Get the ISQLServerErrorInfo interface from ISQLErrorInfo before releasing the reference.  
               pISQLErrorInfo->QueryInterface( IID_ISQLServerErrorInfo, (void**) &pISQLServerErrorInfo);   
  
               pISQLErrorInfo->Release();  
            }  
  
            // Test to ensure the reference is valid, then get error information from ISQLServerErrorInfo.  
            if (pISQLServerErrorInfo != NULL) {  
               pISQLServerErrorInfo->GetErrorInfo(&pSSErrorInfo, &pSSErrorStrings);  
  
               // ISQLServerErrorInfo::GetErrorInfo succeeds even when it has nothing to return.   
               // Test the pointers before using.  
               if (pSSErrorInfo) {  
                  // Display the state and severity from the returned information.   
                  // The error message comes from IErrorInfo::GetDescription.  
                  wprintf(L"Error state:\t%d\r\nSeverity:\t%d\r\n", pSSErrorInfo->bState, pSSErrorInfo->bClass);  
  
                  // IMalloc::Free needed to release references on returned values.  
                  CoTaskMemFree(pSSErrorStrings);  
                  CoTaskMemFree(pSSErrorInfo);  
               }  
  
               pISQLServerErrorInfo->Release();  
            }  
  
            if (SUCCEEDED(pIErrorRecords->GetErrorInfo(nRec, MYLOCALEID, &pIErrorInfoRecord))) {  
               // Get the source and description (error message) from the record's IErrorInfo.  
               pIErrorInfoRecord->GetSource(&bstrSource);  
               pIErrorInfoRecord->GetDescription(&bstrDescription);  
  
               if (bstrSource != NULL) {  
                  wprintf(L"Source:\t\t%s\r\n", bstrSource);  
                  SysFreeString(bstrSource);  
               }  
  
               if (bstrDescription != NULL) {  
                  wprintf(L"Error message:\t%s\r\n", bstrDescription);  
                  SysFreeString(bstrDescription);  
               }  
  
               pIErrorInfoRecord->Release();  
            }  
         }  
         pIErrorRecords->Release();  
      }  
      else {  
         // IErrorInfo is valid; get the source and description to see what it is.  
         pIErrorInfoAll->GetSource(&bstrSource);  
         pIErrorInfoAll->GetDescription(&bstrDescription);  
  
         if (bstrSource != NULL) {  
            wprintf(L"Source:\t\t%s\r\n", bstrSource);  
            SysFreeString(bstrSource);  
         }  
  
         if (bstrDescription != NULL) {  
            wprintf(L"Error message:\t%s\r\n", bstrDescription);  
            SysFreeString(bstrDescription);  
         }  
      }  
  
      pIErrorInfoAll->Release();  
   }  
   else   
      wprintf(L"GetErrorInfo has not returned ErrorInfo.\r\n");  
  
   pISupportErrorInfo->Release();  
   return;  
}  
  
IDBCreateSession *Connect () {  
   // constant definitions  
   static LPCWSTR pwszProviderString = L"server=(local)\\dschwart3;Database=master;Trusted_Connection=yes;";  
   static LPCWSTR pwszDataSource     = NULL;  
   static LPCWSTR pwszUserID         = NULL;  
   static LPCWSTR pwszPassword       = NULL;  
  
   IDBInitialize    * pIDBInitialize      = NULL;  
   IDBProperties    * pIDBProperties      = NULL;  
   IDBCreateSession * pIDBCreateSession   = NULL;  
  
   HRESULT hr;  
  
   // Obtain the provider's clsid  
   CLSID clsidProv = CLSID_SQLNCLI10;  
  
   // Initialize COM  
   CoInitialize(NULL);  
  
   hr = CoCreateInstance(clsidProv, NULL, CLSCTX_ALL, IID_IDBInitialize,(void **)&pIDBInitialize);  
   if (!SUCCEEDED(hr))   
      return NULL;  
  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);  
   if (!SUCCEEDED(hr))   
      return NULL;  
  
   // Set Init properties  
   {  
      DBPROPSET rgPropSets[1];  
      ULONG     cPropSets   = 0;  
      DBPROP    rgInitProperties[10];  
  
      // Initialize Data source properties (connection info)  
      {  
         ULONG cProperties = 0;  
  
         // DBPROP_INIT_DATASOURCE  
         if (pwszDataSource) {  
            rgInitProperties[cProperties].dwPropertyID    = DBPROP_INIT_DATASOURCE;  
            rgInitProperties[cProperties].dwOptions       = DBPROPOPTIONS_REQUIRED;  
            rgInitProperties[cProperties].dwStatus        = DBPROPSTATUS_OK;  
            rgInitProperties[cProperties].colid           = DB_NULLID;  
            rgInitProperties[cProperties].vValue.vt       = VT_BSTR;  
            V_BSTR(&rgInitProperties[cProperties].vValue) = SysAllocString(pwszDataSource);                 
            cProperties++;  
         }  
  
         // DBPROP_AUTH_USERID  
         if (pwszUserID) {  
            rgInitProperties[cProperties].dwPropertyID    = DBPROP_AUTH_USERID;  
            rgInitProperties[cProperties].dwOptions       = DBPROPOPTIONS_REQUIRED;  
            rgInitProperties[cProperties].dwStatus        = DBPROPSTATUS_OK;  
            rgInitProperties[cProperties].colid           = DB_NULLID;  
            rgInitProperties[cProperties].vValue.vt       = VT_BSTR;  
            V_BSTR(&rgInitProperties[cProperties].vValue) = SysAllocString(pwszUserID);  
            cProperties++;  
         }  
  
         // DBPROP_AUTH_PASSWORD  
         if (pwszPassword) {  
            rgInitProperties[cProperties].dwPropertyID    = DBPROP_AUTH_PASSWORD;  
            rgInitProperties[cProperties].dwOptions       = DBPROPOPTIONS_REQUIRED;  
            rgInitProperties[cProperties].dwStatus        = DBPROPSTATUS_OK;  
            rgInitProperties[cProperties].colid           = DB_NULLID;  
            rgInitProperties[cProperties].vValue.vt       = VT_BSTR;  
            V_BSTR(&rgInitProperties[cProperties].vValue) = SysAllocString(pwszPassword);  
            cProperties++;  
         }  
  
         // DBPROP_INIT_PROVIDERSTRING  
         if (pwszProviderString) {  
            rgInitProperties[cProperties].dwPropertyID    = DBPROP_INIT_PROVIDERSTRING;  
            rgInitProperties[cProperties].dwOptions       = DBPROPOPTIONS_REQUIRED;  
            rgInitProperties[cProperties].dwStatus        = DBPROPSTATUS_OK;  
            rgInitProperties[cProperties].colid           = DB_NULLID;  
            rgInitProperties[cProperties].vValue.vt       = VT_BSTR;  
            V_BSTR(&rgInitProperties[cProperties].vValue) = SysAllocString(pwszProviderString);  
            cProperties++;  
         }  
  
         if (cProperties) {  
            rgPropSets[cPropSets].cProperties = cProperties;  
            rgPropSets[cPropSets].rgProperties = rgInitProperties;  
            rgPropSets[cPropSets].guidPropertySet = DBPROPSET_DBINIT;  
            cPropSets++;  
         }  
      }  
  
      // Initialize  
      hr = pIDBProperties->SetProperties(cPropSets, rgPropSets);  
      if (!SUCCEEDED(hr)) {  
         DumpErrorInfo(pIDBProperties, IID_IDBProperties);  
         return NULL;  
      }  
   }  
  
   SAFE_RELEASE(pIDBProperties);  
  
   hr = pIDBInitialize->Initialize();  
   if (!SUCCEEDED(hr)) {  
      DumpErrorInfo(pIDBInitialize, IID_IDBInitialize);  
      return NULL;  
   }  
  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);  
   if (!SUCCEEDED(hr)) {   
      DumpErrorInfo(pIDBInitialize, IID_IDBInitialize);  
      return NULL;  
   }  
  
   // Set SQL Server Specific properties  
   {  
      DBPROPSET rgPropSets[1];  
      ULONG cPropSets = 0;  
      DBPROP rgSqlProperties[10];  
  
      // Initialize the DBProps for fastload and BCP  
      {  
         ULONG cProperties = 0;  
  
         // SSPROP_ENABLEFASTLOAD  
         {  
            rgSqlProperties[cProperties].dwPropertyID   = SSPROP_ENABLEFASTLOAD;  
            rgSqlProperties[cProperties].dwOptions      = DBPROPOPTIONS_REQUIRED;  
            rgSqlProperties[cProperties].dwStatus       = DBPROPSTATUS_OK;  
            rgSqlProperties[cProperties].colid          = DB_NULLID;  
            rgSqlProperties[cProperties].vValue.vt      = VT_BOOL;  
            V_BOOL(&rgSqlProperties[cProperties].vValue)= VARIANT_TRUE;  
            cProperties++;  
         }  
  
         // SSPROP_ENABLEBULKCOPY  
         {  
            rgSqlProperties[cProperties].dwPropertyID   = SSPROP_ENABLEBULKCOPY;  
            rgSqlProperties[cProperties].dwOptions      = DBPROPOPTIONS_REQUIRED;  
            rgSqlProperties[cProperties].dwStatus       = DBPROPSTATUS_OK;  
            rgSqlProperties[cProperties].colid          = DB_NULLID;  
            rgSqlProperties[cProperties].vValue.vt      = VT_BOOL;  
            V_BOOL(&rgSqlProperties[cProperties].vValue)= VARIANT_TRUE;  
            cProperties++;  
         }  
  
         rgPropSets[cPropSets].cProperties = cProperties;  
         rgPropSets[cPropSets].rgProperties = rgSqlProperties;  
         rgPropSets[cPropSets].guidPropertySet = DBPROPSET_SQLSERVERDATASOURCE;  
         cPropSets++;  
      }  
  
      hr = pIDBProperties->SetProperties(cPropSets, rgPropSets);  
      if (!SUCCEEDED(hr)) {   
         DumpErrorInfo(pIDBProperties, IID_IDBProperties);  
         return NULL;  
      }  
   }  
  
   SAFE_RELEASE(pIDBProperties);  
  
   hr = pIDBInitialize->QueryInterface(IID_IDBCreateSession, (void **)&pIDBCreateSession);  
   if (!SUCCEEDED(hr)) {   
      DumpErrorInfo(pIDBInitialize, IID_IDBInitialize);  
      return NULL;  
   }  
  
   SAFE_RELEASE(pIDBInitialize);  
  
   return pIDBCreateSession;  
}  
  
void wmain() {  
   static LPCWSTR pwszTableName   = L"fltest";  
   static LPCWSTR pwszOutFileName = L"outfile.dat";  
   static LPCWSTR pwszErrFileName = L"errfile.txt";  
  
   DBROWCOUNT icRowsCopied = 0;  
  
   IDBCreateSession * pIDBCreateSession = NULL;  
   IBCPSession * pIBCPSession = NULL;  
  
   HRESULT hr;  
  
   pIDBCreateSession = Connect();  
   if (!pIDBCreateSession) {   
      printf("Failed to connect\r\n");  
      exit(1);  
   }  
  
   // get an IBCPSession interface  
   hr = pIDBCreateSession->CreateSession(NULL, IID_IBCPSession, (IUnknown**) &pIBCPSession);  
  
   if (FAILED(hr)) {  
      printf("Failed to obtain an IBCPSession interface\r\n");  
      DumpErrorInfo(pIDBCreateSession, IID_IDBCreateSession);  
      exit(1);  
   }  
  
   SAFE_RELEASE(pIDBCreateSession);  
  
   // Initialize BCP  
  
   // Here we create the mapping between file and table, identifying  
   // which is the source and which is the destination through the final parameter  
   // (here we are copying out of the table and into the file).  
   hr = pIBCPSession->BCPInit(pwszTableName, pwszOutFileName, pwszErrFileName, BCP_DIRECTION_OUT);  
  
   if (FAILED(hr)) {  
      printf("BCPInit failed.\r\n");  
      DumpErrorInfo(pIBCPSession, IID_IBCPSession);  
      exit(1);  
   }  
  
   // You can set SSPROP_ASYNCH_BULKCOPY to TRUE to improve client latency here,  
   // at which point BCPExec can return DB_S_ASYNCHRONOUS.  
   do {  
      hr = pIBCPSession->BCPExec(&icRowsCopied);  
   } while (hr == DB_S_ASYNCHRONOUS);  
  
   if (FAILED(hr)) {  
      printf("BCPExec failed.\r\n");  
      DumpErrorInfo(pIBCPSession, IID_IBCPSession);  
      exit(1);  
   }  
  
   // flush the rest of the rows and finalize the transaction -- the process is complete.  
   hr = pIBCPSession->BCPDone();  
   if (FAILED(hr)) {  
      printf("BCPDone failed.\r\n");  
      DumpErrorInfo(pIBCPSession, IID_IBCPSession);  
      exit(1);  
   }  
  
   SAFE_RELEASE(pIBCPSession);  
  
   CoUninitialize();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="95f0e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95f0e-124">See Also</span></span>  
 <span data-ttu-id="95f0e-125">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="95f0e-125">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="95f0e-126">執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="95f0e-126">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
