---
title: IBCPSession2::BCPSetBulkMode | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BCPSetBulkMode function
ms.assetid: babba19f-e67b-450c-b0e6-523a0f9d23ab
author: rothja
ms.author: jroth
ms.openlocfilehash: 9605ff9b8effde1b4a77ba0d8554c719a8a8d1e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599500"
---
# <a name="ibcpsession2bcpsetbulkmode"></a><span data-ttu-id="1702a-102">IBCPSession2::BCPSetBulkMode</span><span class="sxs-lookup"><span data-stu-id="1702a-102">IBCPSession2::BCPSetBulkMode</span></span>
  <span data-ttu-id="1702a-103">IBCPSession2::BCPSetBulkMode 提供了 [IBCPSession::BCPColFmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md) 的替代方式，可用於指定資料行格式。</span><span class="sxs-lookup"><span data-stu-id="1702a-103">IBCPSession2::BCPSetBulkMode provides an alternative to [IBCPSession::BCPColFmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md) for specifying the column format.</span></span> <span data-ttu-id="1702a-104">不同於設定個別資料行格式屬性的 IBCPSession::BCPColFmt，IBCPSession2::BCPSetBulkMode 會設定所有屬性。</span><span class="sxs-lookup"><span data-stu-id="1702a-104">Unlike IBCPSession::BCPColFmt, which sets individual column format attributes, IBCPSession2::BCPSetBulkMode sets all attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1702a-105">語法</span><span class="sxs-lookup"><span data-stu-id="1702a-105">Syntax</span></span>  
  
```  
  
HRESULT BCPSetBulkMode (  
      int property,  
   void * pField,  
   int cbField,  
   void * pRow,  
   int cbRow  
);  
```  
  
## <a name="arguments"></a><span data-ttu-id="1702a-106">引數</span><span class="sxs-lookup"><span data-stu-id="1702a-106">Arguments</span></span>  
 <span data-ttu-id="1702a-107">*property*</span><span class="sxs-lookup"><span data-stu-id="1702a-107">*property*</span></span>  
 <span data-ttu-id="1702a-108">類型為 BYTE 的常數。</span><span class="sxs-lookup"><span data-stu-id="1702a-108">A constant of type BYTE.</span></span> <span data-ttu-id="1702a-109">如需常數的清單，請參閱＜備註＞一節中的表格。</span><span class="sxs-lookup"><span data-stu-id="1702a-109">See the table in the Remarks section for a list of the constants.</span></span>  
  
 <span data-ttu-id="1702a-110">*pField*</span><span class="sxs-lookup"><span data-stu-id="1702a-110">*pField*</span></span>  
 <span data-ttu-id="1702a-111">欄位結束字元值的指標。</span><span class="sxs-lookup"><span data-stu-id="1702a-111">The pointer to the field terminator value.</span></span>  
  
 <span data-ttu-id="1702a-112">cbField</span><span class="sxs-lookup"><span data-stu-id="1702a-112">cbField</span></span>  
 <span data-ttu-id="1702a-113">欄位結束字元值的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="1702a-113">The length in bytes of the field terminator value.</span></span>  
  
 <span data-ttu-id="1702a-114">pRow</span><span class="sxs-lookup"><span data-stu-id="1702a-114">pRow</span></span>  
 <span data-ttu-id="1702a-115">資料列結束字元值的指標。</span><span class="sxs-lookup"><span data-stu-id="1702a-115">The pointer to the row terminator value.</span></span>  
  
 <span data-ttu-id="1702a-116">cbRow</span><span class="sxs-lookup"><span data-stu-id="1702a-116">cbRow</span></span>  
 <span data-ttu-id="1702a-117">資料列結束字元值的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="1702a-117">The length in bytes of the row terminator value.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="1702a-118">傳回</span><span class="sxs-lookup"><span data-stu-id="1702a-118">Returns</span></span>  
 <span data-ttu-id="1702a-119">IBCPSession2::BCPSetBulkMode 可能會傳回下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="1702a-119">IBCPSession2::BCPSetBulkMode can return one of the following:</span></span>  
  
|||  
|-|-|  
|`S_OK`|<span data-ttu-id="1702a-120">此方法已成功。</span><span class="sxs-lookup"><span data-stu-id="1702a-120">The method succeeded.</span></span>|  
|`E_FAIL`|<span data-ttu-id="1702a-121">發生提供者特有的錯誤，如需詳細資訊，請使用 ISQLServerErrorInfo 介面。</span><span class="sxs-lookup"><span data-stu-id="1702a-121">A provider specific error occurred, for detailed information use the ISQLServerErrorInfo interface.</span></span>|  
|`E_UNEXPECTED`|<span data-ttu-id="1702a-122">此方法的呼叫是非預期的。</span><span class="sxs-lookup"><span data-stu-id="1702a-122">The call to the method was unexpected.</span></span> <span data-ttu-id="1702a-123">例如，在 `IBCPSession2::BCPInit` 呼叫 IBCPSession2：： BCPSetBulkMode 之前，不會呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="1702a-123">For example, the `IBCPSession2::BCPInit` method was not called before calling IBCPSession2::BCPSetBulkMode.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="1702a-124">此引數無效。</span><span class="sxs-lookup"><span data-stu-id="1702a-124">The argument was invalid.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="1702a-125">記憶體不足的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1702a-125">Out of memory error.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1702a-126">備註</span><span class="sxs-lookup"><span data-stu-id="1702a-126">Remarks</span></span>  
 <span data-ttu-id="1702a-127">IBCPSession2::BCPSetBulkMode 可用來大量複製查詢或資料表。</span><span class="sxs-lookup"><span data-stu-id="1702a-127">IBCPSession2::BCPSetBulkMode can be used to bulk copy out of either a query or a table.</span></span> <span data-ttu-id="1702a-128">當 IBCPSession2::BCPSetBulkMode 用來大量複製查詢陳述式時，您必須先呼叫此方法，再呼叫 `IBCPSession::BCPControl(BCP_OPTIONS_HINTS, ...)` 來指定查詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="1702a-128">When IBCPSession2::BCPSetBulkMode is used to bulk copy out of a query statement, it must be called before calling `IBCPSession::BCPControl(BCP_OPTIONS_HINTS, ...)` to specify the query statement.</span></span>  
  
 <span data-ttu-id="1702a-129">您應該避免在單一命令文字中結合 RPC 呼叫語法與批次查詢語法 (例如 `{rpc func};SELECT * from Tbl`)。</span><span class="sxs-lookup"><span data-stu-id="1702a-129">You should avoid combining RPC call syntax with batch query syntax (`{rpc func};SELECT * from Tbl`, for example) in a single command text.</span></span>  <span data-ttu-id="1702a-130">這樣做會導致 ICommandPrepare::Prepare 傳回錯誤並且讓您無法擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1702a-130">This will cause ICommandPrepare::Prepare to return an error and prevent you from retrieving metadata.</span></span> <span data-ttu-id="1702a-131">如果您需要在單一命令文字中結合預存程序執行與批次查詢，請使用 ODBC CALL 語法 (例如 `{call func}; SELECT * from Tbl`)。</span><span class="sxs-lookup"><span data-stu-id="1702a-131">Use ODBC CALL syntax (`{call func}; SELECT * from Tbl`, for example) if you need to combine stored procedure execution and batch query in a single command text.</span></span>  
  
 <span data-ttu-id="1702a-132">下表將列出 *property* 參數的常數。</span><span class="sxs-lookup"><span data-stu-id="1702a-132">The following table lists the constants for the *property* parameter.</span></span>  
  
|<span data-ttu-id="1702a-133">屬性</span><span class="sxs-lookup"><span data-stu-id="1702a-133">Property</span></span>|<span data-ttu-id="1702a-134">描述</span><span class="sxs-lookup"><span data-stu-id="1702a-134">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="1702a-135">BCP_OUT_CHARACTER_MODE</span><span class="sxs-lookup"><span data-stu-id="1702a-135">BCP_OUT_CHARACTER_MODE</span></span>|<span data-ttu-id="1702a-136">指定字元輸出模式。</span><span class="sxs-lookup"><span data-stu-id="1702a-136">Specifies character output mode.</span></span><br /><br /> <span data-ttu-id="1702a-137">對應至 BCP.EXE 中的-c 選項，以及 IBCPSession：： BCPColFmt，並將*eUserDataType*屬性設定為 `BCP_TYPE_SQLCHARACTER` 。</span><span class="sxs-lookup"><span data-stu-id="1702a-137">Corresponds to the -c option in BCP.EXE, and to IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_SQLCHARACTER`.</span></span>|  
|<span data-ttu-id="1702a-138">BCP_OUT_WIDE_CHARACTER_MODE</span><span class="sxs-lookup"><span data-stu-id="1702a-138">BCP_OUT_WIDE_CHARACTER_MODE</span></span>|<span data-ttu-id="1702a-139">指定 Unicode 輸出模式。</span><span class="sxs-lookup"><span data-stu-id="1702a-139">Specifies Unicode output mode.</span></span><br /><br /> <span data-ttu-id="1702a-140">對應至 BCP.EXE 和 IBCPSession：： BCPColFmt 中的-w 選項，並將*eUserDataType*屬性設定為 `BCP_TYPE_SQLNCHAR` 。</span><span class="sxs-lookup"><span data-stu-id="1702a-140">Corresponds to the -w option in BCP.EXE and IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_SQLNCHAR`.</span></span>|  
|<span data-ttu-id="1702a-141">BCP_OUT_NATIVE_TEXT_MODE</span><span class="sxs-lookup"><span data-stu-id="1702a-141">BCP_OUT_NATIVE_TEXT_MODE</span></span>|<span data-ttu-id="1702a-142">指定非字元類型的原生類型和字元類型的 Unicode。</span><span class="sxs-lookup"><span data-stu-id="1702a-142">Specifies native types for non-character types and Unicode for character types.</span></span><br /><br /> <span data-ttu-id="1702a-143">對應至 BCP.EXE 和 IBCPSession：： BCPColFmt 中的-N 選項，其中*eUserDataType*屬性設定為， `BCP_TYPE_SQLNCHAR` 如果資料行類型是字串或 `BCP_TYPE_DEFAULT` 不是字串。</span><span class="sxs-lookup"><span data-stu-id="1702a-143">Corresponds to the -N option in BCP.EXE and IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_SQLNCHAR` if the column type is a string or `BCP_TYPE_DEFAULT` if not a string.</span></span>|  
|<span data-ttu-id="1702a-144">BCP_OUT_NATIVE_MODE</span><span class="sxs-lookup"><span data-stu-id="1702a-144">BCP_OUT_NATIVE_MODE</span></span>|<span data-ttu-id="1702a-145">指定原生資料庫類型。</span><span class="sxs-lookup"><span data-stu-id="1702a-145">Specifies native database types.</span></span><br /><br /> <span data-ttu-id="1702a-146">對應至 BCP.EXE 和 IBCPSession：： BCPColFmt 中的-n 選項，並將*eUserDataType*屬性設定為 `BCP_TYPE_DEFAULT` 。</span><span class="sxs-lookup"><span data-stu-id="1702a-146">Corresponds to the -n option in BCP.EXE and IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_DEFAULT`.</span></span>|  
  
 <span data-ttu-id="1702a-147">您可以針對不會與 IBCPSession2::BCPSetBulkMode 發生衝突的 IBCPSession::BCPControl 選項呼叫 IBCPSession::BCPControl 和 IBCPSession2::BCPSetBulkMode。</span><span class="sxs-lookup"><span data-stu-id="1702a-147">You can call IBCPSession::BCPControl and IBCPSession2::BCPSetBulkMode for IBCPSession::BCPControl options that do not conflict with IBCPSession2::BCPSetBulkMode.</span></span> <span data-ttu-id="1702a-148">例如，您可以使用 `BCP_OPTION_FIRST` 和 IBCPSession2：： BCPSetBulkMode 來呼叫 IBCPSession：： BCPControl。</span><span class="sxs-lookup"><span data-stu-id="1702a-148">For example, you can call IBCPSession::BCPControl with `BCP_OPTION_FIRST` and IBCPSession2::BCPSetBulkMode.</span></span>  
  
 <span data-ttu-id="1702a-149">您無法使用 `BCP_OPTION_TEXTFILE` 和 IBCPSession2：： BCPSetBulkMode 來呼叫 IBCPSession：： BCPControl。</span><span class="sxs-lookup"><span data-stu-id="1702a-149">You cannot call IBCPSession::BCPControl with `BCP_OPTION_TEXTFILE` and IBCPSession2::BCPSetBulkMode.</span></span>  
  
 <span data-ttu-id="1702a-150">如果您嘗試使用一連串包含 IBCPSession::BCPColFmt、IBCPSession::BCPControl 和 IBCPSession::BCPReadFmt 的函式呼叫來呼叫 IBCPSession2::BCPSetBulkMode，其中一個函式呼叫就會傳回順序錯誤失敗。</span><span class="sxs-lookup"><span data-stu-id="1702a-150">If you attempt to call IBCPSession2::BCPSetBulkMode with a sequence of function calls that includes IBCPSession::BCPColFmt, IBCPSession::BCPControl, and IBCPSession::BCPReadFmt, one of the function calls will return a sequence error failure.</span></span> <span data-ttu-id="1702a-151">如果您選擇要更正失敗，請呼叫 IBCPSession::BCPInit 來重設設定並重新開始。</span><span class="sxs-lookup"><span data-stu-id="1702a-151">If you choose to correct the failure, call IBCPSession::BCPInit to reset the settings and start over.</span></span>  
  
 <span data-ttu-id="1702a-152">下表將呈現產生函數順序錯誤之函數呼叫的部分範例。</span><span class="sxs-lookup"><span data-stu-id="1702a-152">The following table presents some examples of function calls that result in a function sequence error:</span></span>  
  
 <span data-ttu-id="1702a-153">呼叫順序</span><span class="sxs-lookup"><span data-stu-id="1702a-153">Call sequence</span></span>  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_IN);  
BCPSetBulkMode();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPSetBulkMode();  
BCPReadFmt();  
```  
  
```  
BCPInit(NULL, "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_HINTS, "select ...");  
BCPSetBulkMode();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPSetBulkMode();  
BCPColFmt();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPReadFmt();  
BCPColFmt();  
```  
  
```  
BCPInit(NULL, "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPSetBulkMode();  
BCPControl(BCP_OPTION_HINTS, "select ...");  
BCPReadFmt();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPColumns();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPSetColFmt();  
```  
  
## <a name="example"></a><span data-ttu-id="1702a-154">範例</span><span class="sxs-lookup"><span data-stu-id="1702a-154">Example</span></span>  
 <span data-ttu-id="1702a-155">下列範例會使用不同的 IBCPSession2::BCPSetBulkMode 設定來建立四個檔案。</span><span class="sxs-lookup"><span data-stu-id="1702a-155">The following sample creates four files using different settings of IBCPSession2::BCPSetBulkMode.</span></span>  
  
```  
  
// compile with: sqlncli11.lib oleaut32.lib ole32.lib  
  
#include <stdio.h>  
#include "sqlncli.h"  
  
IDBInitialize*  g_pIDBInitialize = NULL;  
IBCPSession2 * g_pIBcpSession = NULL;  
class COLEDBPropSet : public DBPROPSET {  
public:  
   COLEDBPropSet() {  
      rgProperties = NULL;  
      cProperties = 0;  
   };  
   COLEDBPropSet(const GUID& guid) {  
      rgProperties = NULL;  
      cProperties = 0;  
      guidPropertySet = guid;  
   };  
   ~COLEDBPropSet() {  
      for ( ULONG i = 0 ; i < cProperties ; i++ )  
         VariantClear(&rgProperties[i].vValue);  
      CoTaskMemFree(rgProperties);  
   }  
   void SetGUID(const GUID& guid) {  
      guidPropertySet = guid;  
   };  
   bool AddProperty(DWORD dwPropertyID, bool bValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID = dwPropertyID;  
      rgProperties[cProperties].vValue.vt = VT_BOOL;  
      rgProperties[cProperties].vValue.boolVal = (bValue) ? VARIANT_TRUE : VARIANT_FALSE;  
      cProperties++;  
      return true;  
   };  
   bool AddProperty(DWORD dwPropertyID, long nValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID  = dwPropertyID;  
      rgProperties[cProperties].vValue.vt     = VT_I4;  
      rgProperties[cProperties].vValue.lVal   = nValue;  
      cProperties++;  
      return true;  
   };  
   bool AddProperty(DWORD dwPropertyID,LPCWSTR szValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID = dwPropertyID;  
      rgProperties[cProperties].vValue.vt = VT_BSTR;  
      rgProperties[cProperties].vValue.bstrVal = SysAllocString(szValue);  
      cProperties++;  
      return true;  
   };  
   bool Add() {  
      DBPROP* p = (DBPROP*)CoTaskMemRealloc(rgProperties, (cProperties + 1) * sizeof(DBPROP));  
      if (p != NULL) {  
         rgProperties = p;  
         rgProperties[cProperties].dwOptions = DBPROPOPTIONS_REQUIRED;  
         rgProperties[cProperties].colid = DB_NULLID;  
         rgProperties[cProperties].vValue.vt = VT_EMPTY;  
         return true;  
      }  
      else  
         return false;  
   };  
};  
  
void OLEDBCleanUp() {  
   if (g_pIDBInitialize) {  
      g_pIDBInitialize->Release();  
      g_pIDBInitialize = NULL;  
   }  
   if (g_pIBcpSession) {  
      g_pIBcpSession->Release();  
      g_pIBcpSession = NULL;  
   }  
}  
  
BOOL MakeOLEDBConnect(LPWSTR  pServer) {  
   BOOL ret = true;  
   IDBProperties * pIDBProperties = NULL;  
   IDBCreateSession * pIDBCreateSession = NULL;  
   COLEDBPropSet PropSet(DBPROPSET_DBINIT);  
   COLEDBPropSet BcpProperty(DBPROPSET_SQLSERVERDATASOURCE);  
   try {  
      HRESULT hr = CoInitializeEx(NULL,COINIT_MULTITHREADED);   
      hr = CoCreateInstance(SQLNCLI_CLSID, NULL, CLSCTX_INPROC_SERVER, IID_IDBInitialize, (LPVOID *)&g_pIDBInitialize);  
      if (FAILED(hr)) {  
         printf("CoCreateInstance failed\n");  
         return false;  
      }  
      PropSet.AddProperty(DBPROP_INIT_DATASOURCE, (LPWSTR)pServer);  
      PropSet.AddProperty(DBPROP_AUTH_INTEGRATED, L"SSPI");  
      hr = g_pIDBInitialize->QueryInterface(IID_IDBProperties, (void**) &pIDBProperties);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->QueryInterface(IID_IDBProperties...) failed\n");  
         throw false;  
      }  
      hr = pIDBProperties->SetProperties(1, &PropSet);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->SetProperties(...) failed\n");  
         throw false;  
      }  
      hr = g_pIDBInitialize->Initialize();  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->Initialize() failed\n");  
         throw false;  
      }  
      BcpProperty.AddProperty(SSPROP_ENABLEFASTLOAD, true);  
      BcpProperty.AddProperty(SSPROP_ENABLEBULKCOPY, true);  
      hr = pIDBProperties->SetProperties(1, &BcpProperty);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->SetProperties() for bcp failed\n");  
         throw false;  
      }  
      hr = g_pIDBInitialize->QueryInterface(IID_IDBCreateSession, (void**) &pIDBCreateSession);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->QueryInterface(IID_IDBCreateSession..) failed\n");  
         throw false;  
      }  
  
      hr = pIDBCreateSession->CreateSession(NULL, IID_IBCPSession2, (IUnknown**) &g_pIBcpSession);  
      if (FAILED(hr)) {  
         printf("g_pIDBCreateSession->CreateSession() failed\n");  
         throw false;  
      }  
   }  
   catch(...) {  
      ret = false;  
   }  
   if (pIDBProperties)  
      pIDBProperties->Release();  
   if (pIDBCreateSession)  
      pIDBCreateSession->Release();  
   return ret;  
}  
  
BOOL BCPSetBulkMode(LPWSTR pszServer, LPTSTR pszQureryOut, char BCPType, LPWSTR pszDataFile) {  
   HRESULThr;  
   if (!MakeOLEDBConnect(pszServer))  
      return false;  
   hr = g_pIBcpSession->BCPInit(NULL, pszDataFile, NULL, BCP_DIRECTION_OUT );   // bcp init for queryout  
   if (FAILED(hr)) {  
      printf("BCP init failed\n");  
      OLEDBCleanUp();  
      return false;  
   }  
   // setbulkmode  
   char ColTerm[] = "\t";  
   char RowTerm[] = "\r\n";  
   wchar_t wColTerm[] = L"\t";  
   wchar_t wRowTerm[] = L"\r\n";  
   BYTE * pColTerm = NULL;  
   int cbColTerm = NULL;  
   BYTE * pRowTerm = 0;  
   int cbRowTerm = 0;  
   int bulkmode = -1;  
  
   if(BCPType == 'c') {   // bcp -c  
      pColTerm = (BYTE*)ColTerm;  
      pRowTerm = (BYTE*)RowTerm;  
      cbColTerm = 1;  
      cbRowTerm = 2;  
      bulkmode = BCP_OUT_CHARACTER_MODE;  
   }  
   else  
      if(BCPType == 'w') {   // bcp -w  
         pColTerm = (BYTE*)wColTerm;  
         pRowTerm = (BYTE*)wRowTerm;  
         cbColTerm = 2;  
         cbRowTerm = 4;  
         bulkmode = BCP_OUT_WIDE_CHARACTER_MODE;  
      }  
      else  
         if (BCPType == 'n')   // bcp -n  
            bulkmode = BCP_OUT_NATIVE_MODE;  
         else  
            if (BCPType == 'N')   // bcp -n  
               bulkmode = BCP_OUT_NATIVE_TEXT_MODE;  
            else {  
               printf("unknown bcp mode\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            hr = g_pIBcpSession->BCPSetBulkMode(bulkmode, pColTerm, cbColTerm, pRowTerm, cbRowTerm);  
            if (FAILED(hr)) {  
               printf("BCPSetBulkMode failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
  
            // set queryout TSQL statement  
            hr = g_pIBcpSession->BCPControl(BCP_OPTION_HINTS, pszQureryOut);  
            if (FAILED(hr)) {  
               printf("BCPControl failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            // bcp copy  
            DBROWCOUNT nRowsInserted = 0;  
            hr = g_pIBcpSession->BCPExec(&nRowsInserted);  
            if (FAILED(hr)) {  
               printf("BCPExec failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            printf("bcp done\n");  
            OLEDBCleanUp();  
            return true;  
}  
  
int main() {  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -c test', 1,2") , 'c', L"bcpc.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -w test', 1,2") , 'w', L"bcpw.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -c test', 1,2") , 'n', L"bcpn.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -w test', 1,2") , 'N', L"bcp_N.dat");  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1702a-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1702a-156">See Also</span></span>  
 [<span data-ttu-id="1702a-157">IBCPSession2 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="1702a-157">IBCPSession2 &#40;OLE DB&#41;</span></span>](ibcpsession2-ole-db.md)  
  
  
