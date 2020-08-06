---
title: 變更 SQL Server 驗證使用者密碼 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 1ed37ded-5671-46a4-b609-eea886dfae20
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c00012746e5995c7954152d1fd6d3e354c94ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702898"
---
# <a name="change-a-sql-server-authentication-user-password-ole-db"></a><span data-ttu-id="22a6c-102">變更 SQL Server 驗證使用者密碼 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="22a6c-102">Change a SQL Server Authentication User Password (OLE DB)</span></span>
  <span data-ttu-id="22a6c-103">此範例顯示如何使用 OLE DB 變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證下，使用者帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="22a6c-103">This sample shows how to use OLE DB to change the password of a user account under [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="22a6c-104">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="22a6c-104">When possible, use Windows Authentication.</span></span> <span data-ttu-id="22a6c-105">如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。</span><span class="sxs-lookup"><span data-stu-id="22a6c-105">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="22a6c-106">請避免將認證儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="22a6c-106">Avoid storing credentials in a file.</span></span> <span data-ttu-id="22a6c-107">如果您必須保存認證，您應該使用[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)將它們加密。</span><span class="sxs-lookup"><span data-stu-id="22a6c-107">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22a6c-108">範例</span><span class="sxs-lookup"><span data-stu-id="22a6c-108">Example</span></span>  
 <span data-ttu-id="22a6c-109">建立之前，請更新 .C++ 程式碼來指定使用者識別碼、舊密碼與新密碼。</span><span class="sxs-lookup"><span data-stu-id="22a6c-109">Before building, update the .C++ code to specify the user ID, old password, and new password.</span></span>  
  
 <span data-ttu-id="22a6c-110">這個應用程式會連接到電腦的預設 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="22a6c-110">This application connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="22a6c-111">在某些 Windows 作業系統上，您必須將 (localhost) 或 (local) 變更為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="22a6c-111">On some Windows operating systems, you will need to change (localhost) or (local) to the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="22a6c-112">若要連線到具名執行個體，請將連接字串從 L"(local)" 變更為 L"(local)\\\name"，其中 name 是具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="22a6c-112">To connect to a named instance, change the connection string from L"(local)" to L"(local)\\\name" , where name is the named instance.</span></span> <span data-ttu-id="22a6c-113">根據預設，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 會安裝至具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="22a6c-113">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express installs to a named instance.</span></span> <span data-ttu-id="22a6c-114">請確認您的 INCLUDE 環境變數包含的目錄內含 sqlncli.h。</span><span class="sxs-lookup"><span data-stu-id="22a6c-114">Make sure your INCLUDE environment variable includes the directory that contains sqlncli.h.</span></span>  
  
 <span data-ttu-id="22a6c-115">使用 ole32.lib oleaut32.lib 編譯。</span><span class="sxs-lookup"><span data-stu-id="22a6c-115">Compile with ole32.lib oleaut32.lib.</span></span>  
  
 <span data-ttu-id="22a6c-116">若要建立此範例，您將需要已知其密碼的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="22a6c-116">To build this sample, you will need a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication user account for which you know the password.</span></span> <span data-ttu-id="22a6c-117">若要允許在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證下登入，請開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio、以滑鼠右鍵按一下 [物件總管] 中的 [伺服器] 節點，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="22a6c-117">To allow logins under [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio, right click on the Server node in Object Explorer, and select Properties.</span></span> <span data-ttu-id="22a6c-118">選取 [安全性]，然後啟用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 驗證模式。</span><span class="sxs-lookup"><span data-stu-id="22a6c-118">Select Security and enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Authentication mode.</span></span> <span data-ttu-id="22a6c-119">若要在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證下加入使用者帳戶，請以滑鼠右鍵按一下 [物件總管] 中的 [安全性] 節點，然後選取 [加入]。</span><span class="sxs-lookup"><span data-stu-id="22a6c-119">To add a user account under [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, right click the Security node in Object Explorer and select Add.</span></span>  
  
 <span data-ttu-id="22a6c-120">您將執行此範例的伺服器必須針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，至少啟用一個登入。</span><span class="sxs-lookup"><span data-stu-id="22a6c-120">The server on which you will run this sample must have at least one login enabled for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="22a6c-121">您也必須啟用伺服器以允許 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證登入。</span><span class="sxs-lookup"><span data-stu-id="22a6c-121">The server must also be enabled to allow [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication logins.</span></span>  
  
```  
// compile with: ole32.lib oleaut32.lib  
void InitializeAndEstablishConnection();  
  
#define STATUSDUMP(status)  case status : wprintf(L"status"); break;  
  
#define UNICODE  
#define DBINITCONSTANTS  
#define INITGUID  
  
#include <assert.h>  
#include <windows.h>  
#include <stdio.h>  
#include <stddef.h>  
#include <IOSTREAM>  
#include <cguid.h>  
#include <oledb.h>  
#include <oledberr.h>  
  
#include <SQLNCLI.h>  
  
LPMALLOC pMalloc = NULL;  
IDBInitialize * pIDBInitialize = NULL;  
HRESULT hr;  
  
void DumpErrorInfo (IUnknown* pObjectWithError, REFIID IID_InterfaceWithError);  
void DumpErrorInfo (IUnknown* pObjectWithError, REFIID IID_InterfaceWithError, BOOL &has_sql_errors);  
  
int main() {  
   // All the initialization activities in a separate function.  
   InitializeAndEstablishConnection();  
  
   if ( FAILED( pIDBInitialize->Uninitialize() ) )  
      // Uninitialize is not required, but fails if an interface was not released.  
      printf("Problem uninitializing.\n");  
  
   pIDBInitialize->Release();  
   CoUninitialize();  
};  
  
void InitializeAndEstablishConnection() {  
   IDBProperties * pIDBProperties = NULL;  
   const ULONG nInitProps = 4;  
   DBPROP InitProperties[nInitProps];  
   const ULONG nSSInitProps = 1;  
   DBPROP SSInitProperties[nSSInitProps];  
  
   const ULONG nPropSet = 2;  
   DBPROPSET rgInitPropSet[nPropSet];  
  
   // Initialize the COM library.  
   CoInitialize(NULL);  
   CoGetMalloc(1, &pMalloc);  
  
   CLSID clsid;  
   CLSIDFromProgID(L"SQLNCLI11", &clsid);  
  
   // Obtain access to the SQLOLEDB provider.  
   hr = CoCreateInstance( clsid, NULL, CLSCTX_INPROC_SERVER, IID_IDBInitialize, (void **) &pIDBInitialize);  
   if (FAILED(hr))  
      printf("Failed in CoCreateInstance().\n");  
  
   // Initialize the property values needed to establish the connection.  
   for (int i = 0; i < nInitProps; i++)  
      VariantInit(&InitProperties[i].vValue);  
  
   // Specify database name.  
   InitProperties[0].dwPropertyID = DBPROP_INIT_CATALOG;  
   InitProperties[0].vValue.vt = VT_BSTR;  
   // Change the following line to use any database on your server  
   InitProperties[0].vValue.bstrVal = SysAllocString(L"master");  
   InitProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   InitProperties[0].colid = DB_NULLID;  
  
   InitProperties[1].dwPropertyID = DBPROP_AUTH_USERID;  
   InitProperties[1].vValue.vt = VT_BSTR;  
   // Modify the following line to add the user ID of a SQL Server Authentication account on your server  
   InitProperties[1].vValue.bstrVal = SysAllocString(L"");  
   InitProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
   InitProperties[1].colid = DB_NULLID;  
  
   InitProperties[2].dwPropertyID = DBPROP_AUTH_PASSWORD;  
   InitProperties[2].vValue.vt = VT_BSTR;  
   // Modify the following line to add the new SQL Server Authentication password  
   InitProperties[2].vValue.bstrVal = SysAllocString(L"");  
   InitProperties[2].dwOptions = DBPROPOPTIONS_REQUIRED;  
   InitProperties[2].colid = DB_NULLID;  
  
   InitProperties[3].dwPropertyID = DBPROP_INIT_DATASOURCE;  
   InitProperties[3].vValue.vt = VT_BSTR;  
   InitProperties[3].vValue.bstrVal = SysAllocString(L"(local)");  
   InitProperties[3].dwOptions = DBPROPOPTIONS_REQUIRED;  
   InitProperties[3].colid = DB_NULLID;  
  
   SSInitProperties[0].dwPropertyID = SSPROP_AUTH_OLD_PASSWORD;  
   SSInitProperties[0].vValue.vt = VT_BSTR;  
   // Modify the following line to specify the existing SQL Server Authentication password  
   SSInitProperties[0].vValue.bstrVal = SysAllocString(L"");  
   SSInitProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   SSInitProperties[0].colid = DB_NULLID;  
  
   rgInitPropSet[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgInitPropSet[0].cProperties = nInitProps;  
   rgInitPropSet[0].rgProperties = InitProperties;  
  
   rgInitPropSet[1].guidPropertySet = DBPROPSET_SQLSERVERDBINIT;  
   rgInitPropSet[1].cProperties = nSSInitProps;  
   rgInitPropSet[1].rgProperties = SSInitProperties;  
  
   // Set initialization properties.  
   hr = pIDBInitialize->QueryInterface( IID_IDBProperties, (void **)&pIDBProperties);  
  
   if (FAILED(hr))  
      printf("Failed to obtain IDBProperties interface.\n");  
  
   hr = pIDBProperties->SetProperties( nPropSet, rgInitPropSet);  
  
   if (FAILED(hr))  
      printf("Failed to set initialization properties.\n");  
  
   pIDBProperties->Release();  
  
   // establish connection to the data source.  
   DWORD now = GetTickCount();  
  
   if ( FAILED(pIDBInitialize->Initialize()) ) {  
      printf("Problem in initializing.\n");  
      DumpErrorInfo(pIDBInitialize, IID_IDBInitialize);  
   }  
  
   DWORD tookms = GetTickCount() - now;  
   printf("Connection took %d ms.\n", tookms);  
}  
  
// DumpErrorInfo queries SQLOLEDB error interfaces, retrieving available status  
// or error information. This version is called when SQL Server errors are not expected.  
void DumpErrorInfo (IUnknown* pObjectWithError, REFIID IID_InterfaceWithError) {  
   BOOL has_sql_errors;  
   DumpErrorInfo (pObjectWithError, IID_InterfaceWithError, has_sql_errors);  
}  
  
// DumpErrorInfo queries SQLOLEDB error interfaces, retrieving available status   
// or error information. This version is called when an SQL Server error could occur.  
void DumpErrorInfo (IUnknown* pObjectWithError, REFIID IID_InterfaceWithError, BOOL &has_sql_errors ) {  
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
  
   // Hard-code an English (United States) locale for the example.  
   DWORD MYLOCALEID = 0x0409;  
  
   has_sql_errors = 0;  
  
   // Only ask for error information if the interface supports it.  
   if (FAILED(pObjectWithError->QueryInterface(IID_ISupportErrorInfo, (void**) &pISupportErrorInfo)))     
      wprintf(L"SupportErrorErrorInfo interface not supported\n");  
   else if (FAILED(pISupportErrorInfo->InterfaceSupportsErrorInfo(IID_InterfaceWithError)))     
      wprintf(L"InterfaceWithError interface not supported\n");  
  
   // Do not test the return of GetErrorInfo. It can succeed and return  
   // a NULL pointer in pIErrorInfoAll. Simply test the pointer.  
   GetErrorInfo(0, &pIErrorInfoAll);  
  
   // Test to see if it's a valid OLE DB IErrorInfo interface exposing a list of records.  
   if (pIErrorInfoAll != NULL)  {  
      if (SUCCEEDED(pIErrorInfoAll->QueryInterface(IID_IErrorRecords, (void**) &pIErrorRecords))) {  
         pIErrorRecords->GetRecordCount(&nRecs);  
  
         // Within each record, retrieve information from each of the defined interfaces.  
         for (nRec = 0; nRec < nRecs; nRec++) {  
            ULONG errorno = nRecs - nRec - 1;  
            // From IErrorRecords, get the HRESULT and a reference to the ISQLErrorInfo interface.  
            pIErrorRecords->GetBasicErrorInfo(errorno, &errorinfo);  
            pIErrorRecords->GetCustomErrorObject(errorno,IID_ISQLErrorInfo, (IUnknown**) &pISQLErrorInfo);  
  
            // Display the HRESULT, then use the ISQLErrorInfo.  
            wprintf(L"HRESULT:\t%#X\n", errorinfo.hrError);  
  
            if (pISQLErrorInfo != NULL) {  
               pISQLErrorInfo->GetSQLInfo(&bstrSQLSTATE, &lNativeError);  
               // Display SQLSTATE and native error values.  
               wprintf(L"SQLSTATE:\t%s\nNative Error:\t%ld\n", bstrSQLSTATE, lNativeError);  
  
               // SysFree BSTR references.  
               SysFreeString(bstrSQLSTATE);  
  
               // Get the ISQLServerErrorInfo interface from  
               // ISQLErrorInfo before releasing the reference.  
               pISQLErrorInfo->QueryInterface(IID_ISQLServerErrorInfo, (void**) &pISQLServerErrorInfo);  
  
               pISQLErrorInfo->Release();  
            }  
  
            // Test to ensure the reference is valid, then get error information from ISQLServerErrorInfo.  
            if (pISQLServerErrorInfo != NULL) {  
               pISQLServerErrorInfo->GetErrorInfo(&pSSErrorInfo, &pSSErrorStrings);  
  
               // ISQLServerErrorInfo::GetErrorInfo succeeds even when it  
               // has nothing to return. Test the pointers before using.  
               if (pSSErrorInfo) {  
                  // Display the state and severity from the returned  
                  // information. The error message comes from  
                  // IErrorInfo::GetDescription.  
                  wprintf(L"Error state:\t%d\nSeverity:\t%d\n", pSSErrorInfo->bState, pSSErrorInfo->bClass);  
                  wprintf(L"Procedure:\t%s\nLine:\t%d\n", pSSErrorInfo->pwszProcedure, pSSErrorInfo->wLineNumber);  
  
                  has_sql_errors++;  
  
                  // IMalloc::Free needed to release references on returned values.  
                  pMalloc->Free(pSSErrorStrings);  
                  pMalloc->Free(pSSErrorInfo);  
               }  
  
               pISQLServerErrorInfo->Release();  
            }  
  
            if (SUCCEEDED(pIErrorRecords->GetErrorInfo(errno, MYLOCALEID, &pIErrorInfoRecord))) {  
               // Get the source and description (error message) from the record's IErrorInfo.  
               pIErrorInfoRecord->GetSource(&bstrSource);  
               pIErrorInfoRecord->GetDescription(&bstrDescription);  
  
               if (bstrSource != NULL) {  
                  wprintf(L"Source:\t\t%s\n", bstrSource);  
                  SysFreeString(bstrSource);  
               }  
  
               if (bstrDescription != NULL) {  
                  wprintf(L"Error message:\t%s\n", bstrDescription);  
                  SysFreeString(bstrDescription);  
               }  
  
               pIErrorInfoRecord->Release();  
            }  
         }  
  
         pIErrorRecords->Release();  
      }  
      else {  
         // IErrorInfo is valid; get the source and  
         // description to see what it is.  
         pIErrorInfoAll->GetSource(&bstrSource);  
         pIErrorInfoAll->GetDescription(&bstrDescription);  
  
         if (bstrSource != NULL) {  
            wprintf(L"Source:\t\t%s\n", bstrSource);  
            SysFreeString(bstrSource);  
         }  
  
         if (bstrDescription != NULL) {  
            wprintf(L"Error message:\t%s\n", bstrDescription);  
            SysFreeString(bstrDescription);  
         }  
      }  
  
      pIErrorInfoAll->Release();  
   }  
   else  
      wprintf(L"GetErrorInfo failed.\n");  
  
   if (pISupportErrorInfo != NULL)  
      pISupportErrorInfo->Release();  
}  
```  
  
  
