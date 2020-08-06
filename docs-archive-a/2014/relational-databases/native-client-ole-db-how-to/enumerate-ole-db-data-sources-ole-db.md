---
title: 列舉 OLE DB 資料來源 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [OLE DB]
ms.assetid: ba240060-3237-4fb8-b2fb-b87fda2b1e7a
author: rothja
ms.author: jroth
ms.openlocfilehash: 1173feef8de657c43563b40bec763f81d630014e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707485"
---
# <a name="enumerate-ole-db-data-sources-ole-db"></a><span data-ttu-id="d4c64-102">列舉 OLE DB 資料來源 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="d4c64-102">Enumerate OLE DB Data Sources (OLE DB)</span></span>
  <span data-ttu-id="d4c64-103">此範例會示範如何使用列舉值物件來列出可用的資料來源。</span><span class="sxs-lookup"><span data-stu-id="d4c64-103">This sample shows how to use the enumerator object to list the data sources available.</span></span>  
  
 <span data-ttu-id="d4c64-104">為了列出 SQLOLEDB 列舉值可見的資料來源，取用者會呼叫[ISourcesRowset：： GetSourcesRowset](https://go.microsoft.com/fwlink/?LinkId=120312)方法。</span><span class="sxs-lookup"><span data-stu-id="d4c64-104">To list the data sources visible to the SQLOLEDB enumerator, the consumer calls the [ISourcesRowset::GetSourcesRowset](https://go.microsoft.com/fwlink/?LinkId=120312) method.</span></span> <span data-ttu-id="d4c64-105">這個方法會傳回有關目前可見之資料來源的資訊資料列集。</span><span class="sxs-lookup"><span data-stu-id="d4c64-105">This method returns a rowset of information about the currently visible data sources.</span></span>  
  
 <span data-ttu-id="d4c64-106">根據所使用的網路程式庫而定，將會搜尋適當的網域來找出資料來源。</span><span class="sxs-lookup"><span data-stu-id="d4c64-106">Depending on the network library used, the appropriate domain is searched for the data sources.</span></span> <span data-ttu-id="d4c64-107">如果是具名管道，這就是用戶端登入的網域。</span><span class="sxs-lookup"><span data-stu-id="d4c64-107">For named pipes, it is the domain to which the client is logged on.</span></span> <span data-ttu-id="d4c64-108">如果是 AppleTalk，這就是預設區域。</span><span class="sxs-lookup"><span data-stu-id="d4c64-108">For AppleTalk, it is the default zone.</span></span> <span data-ttu-id="d4c64-109">如果是 SPX/IPX，這就是連結中找到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝清單。</span><span class="sxs-lookup"><span data-stu-id="d4c64-109">For SPX/IPX, it is the list of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations found in the bindery.</span></span> <span data-ttu-id="d4c64-110">如果是 Banyan VINES，這就是本機網路上找到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝。</span><span class="sxs-lookup"><span data-stu-id="d4c64-110">For Banyan VINES, it is the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations found on the local network.</span></span> <span data-ttu-id="d4c64-111">不支援多重通訊協定和 TCP/IP 通訊端。</span><span class="sxs-lookup"><span data-stu-id="d4c64-111">Multiprotocol and TCP/IP sockets are not supported.</span></span>  
  
 <span data-ttu-id="d4c64-112">當伺服器關閉或開啟時，可能會花上好幾分鐘的時間來更新這些網域中的資訊。</span><span class="sxs-lookup"><span data-stu-id="d4c64-112">When the server is turned off or on, it can take few minutes to update the information in these domains.</span></span>  
  
 <span data-ttu-id="d4c64-113">此範例需要 AdventureWorks 範例資料庫，您可以從 [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) (Microsoft SQL Server 範例和社群專案首頁) 下載。</span><span class="sxs-lookup"><span data-stu-id="d4c64-113">This sample requires the AdventureWorks sample database, which you can download from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d4c64-114">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="d4c64-114">When possible, use Windows Authentication.</span></span> <span data-ttu-id="d4c64-115">如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。</span><span class="sxs-lookup"><span data-stu-id="d4c64-115">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="d4c64-116">請避免將認證儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="d4c64-116">Avoid storing credentials in a file.</span></span> <span data-ttu-id="d4c64-117">如果您必須保存認證，您應該使用[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)將它們加密。</span><span class="sxs-lookup"><span data-stu-id="d4c64-117">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-enumerate-ole-db-data-sources"></a><span data-ttu-id="d4c64-118">若要列舉 OLE DB 資料來源</span><span class="sxs-lookup"><span data-stu-id="d4c64-118">To enumerate OLE DB data sources</span></span>  
  
1.  <span data-ttu-id="d4c64-119">呼叫 `ISourceRowset::GetSourcesRowset` 來擷取來源資料列集。</span><span class="sxs-lookup"><span data-stu-id="d4c64-119">Retrieve the source rowset by calling `ISourceRowset::GetSourcesRowset`.</span></span>  
  
2.  <span data-ttu-id="d4c64-120">呼叫 `GetColumnInfo::IColumnInfo` 來尋找列舉值資料列集的描述。</span><span class="sxs-lookup"><span data-stu-id="d4c64-120">Find the description of the enumerators rowset by calling `GetColumnInfo::IColumnInfo`.</span></span>  
  
3.  <span data-ttu-id="d4c64-121">從資料行資訊建立繫結結構。</span><span class="sxs-lookup"><span data-stu-id="d4c64-121">Create the binding structures from the column information.</span></span>  
  
4.  <span data-ttu-id="d4c64-122">呼叫 `IAccessor::CreateAccessor` 來建立資料列集存取子。</span><span class="sxs-lookup"><span data-stu-id="d4c64-122">Create the rowset accessor by calling `IAccessor::CreateAccessor`.</span></span>  
  
5.  <span data-ttu-id="d4c64-123">呼叫 `IRowset::GetNextRows` 來提取資料列。</span><span class="sxs-lookup"><span data-stu-id="d4c64-123">Fetch the rows by calling `IRowset::GetNextRows`.</span></span>  
  
6.  <span data-ttu-id="d4c64-124">呼叫 `IRowset::GetData` 來從資料列集的資料列複本擷取資料，然後加以處理。</span><span class="sxs-lookup"><span data-stu-id="d4c64-124">Retrieve data from the rowset's copy of the row by calling `IRowset::GetData`, and process it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4c64-125">範例</span><span class="sxs-lookup"><span data-stu-id="d4c64-125">Example</span></span>  
 <span data-ttu-id="d4c64-126">使用 ole32.lib 編譯並執行下列 C++ 程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="d4c64-126">Compile with ole32.lib and execute the following C++ code listing.</span></span> <span data-ttu-id="d4c64-127">這個應用程式會連接到電腦的預設 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d4c64-127">This application connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="d4c64-128">在某些 Windows 作業系統上，您必須將 (localhost) 或 (local) 變更為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4c64-128">On some Windows operating systems, you will need to change (localhost) or (local) to the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="d4c64-129">若要連線到具名執行個體，請將連接字串從 L"(local)" 變更為 L"(local)\\\name"，其中 name 是具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="d4c64-129">To connect to a named instance, change the connection string from L"(local)" to L"(local)\\\name" , where name is the named instance.</span></span> <span data-ttu-id="d4c64-130">根據預設，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 會安裝至具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="d4c64-130">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express installs to a named instance.</span></span> <span data-ttu-id="d4c64-131">請確認您的 INCLUDE 環境變數包含的目錄內含 sqlncli.h。</span><span class="sxs-lookup"><span data-stu-id="d4c64-131">Make sure your INCLUDE environment variable includes the directory that contains sqlncli.h.</span></span>  
  
```  
// compile with: ole32.lib  
#define UNICODE  
#define _UNICODE  
#define DBINITCONSTANTS  
#define INITGUID  
#define OLEDBVER 0x0250   // to include correct interfaces  
  
#include <windows.h>  
#include <stddef.h>  
#include <oledb.h>  
#include <oledberr.h>  
#include <sqlncli.h>  
#include <stdio.h>  
  
#define NUMROWS_CHUNK  5  
  
// AdjustLen supports binding on four-byte boundaries.  
_inline DBLENGTH AdjustLen(DBLENGTH cb) {   
   return ( (cb + 3) & ~3 );  
}  
  
// Get the characteristics of the rowset (the IColumnsInfo interface).  
HRESULT GetColumnInfo ( IRowset* pIRowset,   
                        DBORDINAL* pnCols,   
                        DBCOLUMNINFO** ppColumnsInfo,  
                        OLECHAR** ppColumnStrings ) {  
   IColumnsInfo* pIColumnsInfo;  
   HRESULT hr;  
  
   *pnCols = 0;  
   if (FAILED(pIRowset->QueryInterface(IID_IColumnsInfo, (void**) &pIColumnsInfo)))  
      return (E_FAIL);  
  
   hr = pIColumnsInfo->GetColumnInfo(pnCols, ppColumnsInfo, ppColumnStrings);  
  
   if (FAILED(hr)) {}   /* Process error */   
  
   pIColumnsInfo->Release();  
   return (hr);  
}  
  
// Create binding structures from column information. Binding structures  
// will be used to create an accessor that allows row value retrieval.  
void CreateDBBindings ( DBORDINAL nCols,   
                        DBCOLUMNINFO* pColumnsInfo,   
                        DBBINDING** ppDBBindings,  
                        BYTE** ppRowValues ) {  
   ULONG nCol;  
   DBLENGTH cbRow = 0;  
   DBLENGTH cbCol;  
   DBBINDING* pDBBindings;  
   BYTE* pRowValues;  
  
   pDBBindings = new DBBINDING[nCols];  
   if (!(pDBBindings /* = new DBBINDING[nCols] */ ))  
      return;  
  
   for ( nCol = 0 ; nCol < nCols ; nCol++ ) {  
      pDBBindings[nCol].iOrdinal = nCol + 1;  
      pDBBindings[nCol].pTypeInfo = NULL;  
      pDBBindings[nCol].pObject = NULL;  
      pDBBindings[nCol].pBindExt = NULL;  
      pDBBindings[nCol].dwPart = DBPART_VALUE;  
      pDBBindings[nCol].dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
      pDBBindings[nCol].eParamIO = DBPARAMIO_NOTPARAM;  
      pDBBindings[nCol].dwFlags = 0;  
      pDBBindings[nCol].wType = pColumnsInfo[nCol].wType;  
      pDBBindings[nCol].bPrecision = pColumnsInfo[nCol].bPrecision;  
      pDBBindings[nCol].bScale = pColumnsInfo[nCol].bScale;  
  
      cbCol = pColumnsInfo[nCol].ulColumnSize;  
  
      switch (pColumnsInfo[nCol].wType) {  
      case DBTYPE_STR: {  
            cbCol += 1;  
            break;  
         }  
  
      case DBTYPE_WSTR: {  
            cbCol = (cbCol + 1) * sizeof(WCHAR);  
            break;  
         }  
  
      default:  
         break;  
      }  
  
      pDBBindings[nCol].obValue = cbRow;  
      pDBBindings[nCol].cbMaxLen = cbCol;  
      cbRow += AdjustLen(cbCol);  
   }  
  
   pRowValues = new BYTE[cbRow];  
   *ppDBBindings = pDBBindings;  
   *ppRowValues = pRowValues;  
}  
  
int main() {  
   ISourcesRowset* pISourceRowset = NULL;      
   IRowset* pIRowset = NULL;          
   IAccessor* pIAccessor = NULL;  
   DBBINDING* pDBBindings = NULL;              
  
   HROW* pRows = new HROW[500];      
   HACCESSOR hAccessorRetrieve = NULL;          
   ULONG DSSeqNumber = 0;  
  
   HRESULT hr;  
   DBORDINAL nCols;  
   DBCOLUMNINFO* pColumnsInfo = NULL;  
   OLECHAR* pColumnStrings = NULL;  
   DBBINDSTATUS* pDBBindStatus = NULL;  
  
   BYTE* pRowValues = NULL;  
   DBCOUNTITEM cRowsObtained;  
   ULONG iRow;  
   char* pMultiByte = NULL;  
   short* psSourceType = NULL;  
   BYTE* pDatasource = NULL;  
  
   if (!pRows)  
      return (0);  
  
   // Initialize COM library.  
   CoInitialize(NULL);  
  
   // Initialize the enumerator.  
   if (FAILED(CoCreateInstance(CLSID_SQLNCLI11_ENUMERATOR,   
                               NULL,  
                               CLSCTX_INPROC_SERVER,   
                               IID_ISourcesRowset,   
                               (void**)&pISourceRowset))) {  
      // Process error.  
      return TRUE;  
   }  
  
   // Retrieve the source rowset.  
   hr = pISourceRowset->GetSourcesRowset(NULL, IID_IRowset, 0, NULL, (IUnknown**)&pIRowset);  
  
   pISourceRowset->Release();  
   if (FAILED(hr)) {  
      // Process error.  
      return TRUE;  
   }  
  
   // Get the description of the enumerator's rowset.  
   if (FAILED(hr = GetColumnInfo(pIRowset, &nCols, &pColumnsInfo, &pColumnStrings))) {  
      // Process error.  
      goto SAFE_EXIT;  
   }  
  
   // Create the binding structures.  
   CreateDBBindings(nCols, pColumnsInfo, &pDBBindings, &pRowValues);  
   pDBBindStatus = new DBBINDSTATUS[nCols];  
  
   if (sizeof(TCHAR) != sizeof(WCHAR))  
      pMultiByte = new char[pDBBindings[0].cbMaxLen];  
  
   if (FAILED(pIRowset->QueryInterface(IID_IAccessor, (void**)&pIAccessor))) {  
      // Process error.  
      goto SAFE_EXIT;  
   }  
  
   // Create the rowset accessor.  
   if (FAILED(hr = pIAccessor->CreateAccessor(DBACCESSOR_ROWDATA,   
                                              nCols,  
                                              pDBBindings,   
                                              0,   
                                              &hAccessorRetrieve,   
                                              pDBBindStatus))) {  
      // Process error.  
      goto SAFE_EXIT;  
   }  
  
   // Process all the rows, NUMROWS_CHUNK rows at a time.  
   while (SUCCEEDED(hr)) {  
      hr = pIRowset->GetNextRows(NULL, 0, NUMROWS_CHUNK, &cRowsObtained, &pRows);  
      if( FAILED(hr)) {  
         // process error  
      }  
      if (cRowsObtained == 0 || FAILED(hr))  
         break;  
  
      for (iRow = 0 ; iRow < cRowsObtained ; iRow++) {  
         // Get the rowset data.  
         if (SUCCEEDED(hr = pIRowset->GetData(pRows[iRow], hAccessorRetrieve, pRowValues))) {  
            psSourceType = (short *)(pRowValues + pDBBindings[3].obValue);  
  
            if (*psSourceType == DBSOURCETYPE_DATASOURCE) {  
               DSSeqNumber = DSSeqNumber + 1;   // Data source counter.  
               pDatasource = (pRowValues + pDBBindings[0].obValue);  
  
               if ( sizeof(TCHAR) != sizeof(WCHAR) ) {  
                  WideCharToMultiByte(CP_ACP,   
                                      0,  
                                      (WCHAR*)pDatasource,   
                                      -1,   
                                      pMultiByte,  
                                      static_cast<int>(pDBBindings[0].cbMaxLen),   
                                      NULL,   
                                      NULL);  
  
                  printf( "DataSource# %d\tName: %S\n",   
                          DSSeqNumber,   
                          (WCHAR *) pMultiByte );  
               }  
               else {  
                  printf( "DataSource# %d\tName: %S\n",   
                          DSSeqNumber,   
                          (WCHAR *) pDatasource );  
               }  
            }  
         }  
      }  
      pIRowset->ReleaseRows(cRowsObtained, pRows, NULL, NULL, NULL);  
   }  
  
   // Release COM library.  
   CoUninitialize();  
  
SAFE_EXIT:  
   // Do the clean-up.  
   return TRUE;  
}  
```  
  
  
