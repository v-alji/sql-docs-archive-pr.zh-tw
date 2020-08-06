---
title: 取得大型資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- DBPROP_ACCESSORDER property
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: a31c5632-96aa-483f-a307-004c5149fbc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 38602df026d2e752a758672dde23a59a26ad4917
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709286"
---
# <a name="getting-large-data"></a><span data-ttu-id="a5c9d-102">取得大型資料</span><span class="sxs-lookup"><span data-stu-id="a5c9d-102">Getting Large Data</span></span>
  <span data-ttu-id="a5c9d-103">一般而言，取用者應該隔離的程式碼會 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 從處理不透過**ISequentialStream**介面指標參考之資料的其他程式碼，建立原生用戶端 OLE DB 提供者儲存物件。</span><span class="sxs-lookup"><span data-stu-id="a5c9d-103">In general, consumers should isolate code that creates a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider storage object from other code that handles data not referenced through an **ISequentialStream** interface pointer.</span></span>  
  
 <span data-ttu-id="a5c9d-104">本主題會參考可供下列函數使用的功能：</span><span class="sxs-lookup"><span data-stu-id="a5c9d-104">This topic refers to functionality available with the following functions:</span></span>  
  
-   <span data-ttu-id="a5c9d-105">IRowset:GetData</span><span class="sxs-lookup"><span data-stu-id="a5c9d-105">IRowset:GetData</span></span>  
  
-   <span data-ttu-id="a5c9d-106">IRow::GetColumns</span><span class="sxs-lookup"><span data-stu-id="a5c9d-106">IRow::GetColumns</span></span>  
  
-   <span data-ttu-id="a5c9d-107">ICommand::Execute</span><span class="sxs-lookup"><span data-stu-id="a5c9d-107">ICommand::Execute</span></span>  
  
 <span data-ttu-id="a5c9d-108">如果資料列集屬性群組中的 DBPROP_ACCESSORDER 屬性 () 設定為 DBPROPVAL_AO_SEQUENTIAL 或 DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS 的其中一個值，取用者應該只在呼叫**GetNextRows**方法時提取單一資料列，因為 BLOB 資料不會經過緩衝處理。</span><span class="sxs-lookup"><span data-stu-id="a5c9d-108">If the DBPROP_ACCESSORDER property (in the rowset property group) is set to either of the values DBPROPVAL_AO_SEQUENTIAL or DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS, the consumer should fetch only a single row of data in a call to the **GetNextRows** method because BLOB data is not buffered.</span></span> <span data-ttu-id="a5c9d-109">如果 DBPROP_ACCESSORDER 的值設定為 DBPROPVAL_AO_RANDOM，取用者可以在 **GetNextRows** 中提取資料的多個資料列。</span><span class="sxs-lookup"><span data-stu-id="a5c9d-109">If the value of DBPROP_ACCESSORDER is set to DBPROPVAL_AO_RANDOM, the consumer can fetch multiple rows of data in **GetNextRows**.</span></span>  
  
 <span data-ttu-id="a5c9d-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者不會從取得大型資料， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 直到取用者要求這麼做為止。</span><span class="sxs-lookup"><span data-stu-id="a5c9d-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not retrieve large data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] until requested to do so by the consumer.</span></span> <span data-ttu-id="a5c9d-111">取用者應該在一個存取子中繫結所有短資料，然後在需要時，使用一或多個暫存的存取子來擷取大型資料值。</span><span class="sxs-lookup"><span data-stu-id="a5c9d-111">The consumer should bind all short data in one accessor, and then use one or more temporary accessors to retrieve large data values as required.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5c9d-112">範例</span><span class="sxs-lookup"><span data-stu-id="a5c9d-112">Example</span></span>  
 <span data-ttu-id="a5c9d-113">此範例會從單一資料行擷取大型資料值：</span><span class="sxs-lookup"><span data-stu-id="a5c9d-113">This example retrieves a large data value from a single column:</span></span>  
  
```  
HRESULT GetUnboundData  
    (  
    IRowset* pIRowset,  
    HROW hRow,  
    ULONG nCol,   
    BYTE* pUnboundData  
    )  
    {  
    UINT                cbRow = sizeof(IUnknown*) + sizeof(ULONG);  
    BYTE*               pRow = new BYTE[cbRow];  
  
    DBOBJECT            dbobject;  
  
    IAccessor*          pIAccessor = NULL;  
    HACCESSOR           haccessor;  
  
    DBBINDING           dbbinding;  
    ULONG               ulbindstatus;  
  
    ULONG               dwStatus;  
    ISequentialStream*  pISequentialStream;  
    ULONG               cbRead;  
  
    HRESULT             hr;  
  
    // Set up the DBOBJECT structure.  
    dbobject.dwFlags = STGM_READ;  
    dbobject.iid = IID_ISequentialStream;  
  
    // Create the DBBINDING, requesting a storage-object pointer from  
    // The SQL Server Native Client OLE DB provider.  
    dbbinding.iOrdinal = nCol;  
    dbbinding.obValue = 0;  
    dbbinding.obStatus = sizeof(IUnknown*);  
    dbbinding.obLength = 0;  
    dbbinding.pTypeInfo = NULL;  
    dbbinding.pObject = &dbobject;  
    dbbinding.pBindExt = NULL;  
    dbbinding.dwPart = DBPART_VALUE | DBPART_STATUS;  
    dbbinding.dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
    dbbinding.eParamIO = DBPARAMIO_NOTPARAM;  
    dbbinding.cbMaxLen = 0;  
    dbbinding.dwFlags = 0;  
    dbbinding.wType = DBTYPE_IUNKNOWN;  
    dbbinding.bPrecision = 0;  
    dbbinding.bScale = 0;  
  
    if (FAILED(hr = pIRowset->  
        QueryInterface(IID_IAccessor, (void**) &pIAccessor)))  
        {  
        // Process QueryInterface failure.  
        return (hr);  
        }  
  
    // Create the accessor.  
    if (FAILED(hr = pIAccessor->CreateAccessor(DBACCESSOR_ROWDATA, 1,  
        &dbbinding, 0, &haccessor, &ulbindstatus)))  
        {  
        // Process error from CreateAccessor.  
        pIAccessor->Release();  
        return (hr);  
        }  
  
    // Read and process BLOCK_SIZE bytes at a time.  
    if (SUCCEEDED(hr = pIRowset->GetData(hRow, haccessor, pRow)))  
        {  
        dwStatus = *((ULONG*) (pRow + dbbinding.obStatus));  
  
        if (dwStatus == DBSTATUS_S_ISNULL)  
            {  
            // Process NULL data  
            }  
        else if (dwStatus == DBSTATUS_S_OK)  
            {  
            pISequentialStream = *((ISequentialStream**)   
                (pRow + dbbinding.obValue));  
  
            do  
                {  
                if (SUCCEEDED(hr =  
                    pISequentialStream->Read(pUnboundData,  
                    BLOCK_SIZE, &cbRead)))  
                    {  
                    pUnboundData += cbRead;  
                    }  
                }  
            while (SUCCEEDED(hr) && cbRead >= BLOCK_SIZE);  
  
            pISequentialStream->Release();  
            }  
        }  
    else  
        {  
        // Process error from GetData.  
        }  
  
    pIAccessor->ReleaseAccessor(haccessor, NULL);  
    pIAccessor->Release();  
    delete [] pRow;  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5c9d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5c9d-114">See Also</span></span>  
 <span data-ttu-id="a5c9d-115">[Blob 和 OLE 物件](blobs-and-ole-objects.md) </span><span class="sxs-lookup"><span data-stu-id="a5c9d-115">[BLOBs and OLE Objects](blobs-and-ole-objects.md) </span></span>  
 [<span data-ttu-id="a5c9d-116">使用大數值類型</span><span class="sxs-lookup"><span data-stu-id="a5c9d-116">Using Large Value Types</span></span>](../native-client/features/using-large-value-types.md)  
  
  
