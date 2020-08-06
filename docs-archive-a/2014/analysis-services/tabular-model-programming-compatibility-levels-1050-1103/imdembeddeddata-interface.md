---
title: IMDEmbedded 介面 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 9dba8c68-4bef-4c2b-815c-c286f1a1939b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 331f8c33f7748e6591acd6d6ecda7a03ef7d8137
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594234"
---
# <a name="imdembedded-interface"></a><span data-ttu-id="47e69-102">IMDEmbedded 介面</span><span class="sxs-lookup"><span data-stu-id="47e69-102">IMDEmbedded Interface</span></span>
  <span data-ttu-id="47e69-103">IMDEmbedded 介面是用來管理內嵌 PowerPivot 資料庫或表格式模型資料庫的公用介面。</span><span class="sxs-lookup"><span data-stu-id="47e69-103">The IMDEmbedded interface is a public interface used to manage an embedded PowerPivot database or a tabular model database.</span></span> <span data-ttu-id="47e69-104">此介面繼承自 `IPersistStream` 介面，</span><span class="sxs-lookup"><span data-stu-id="47e69-104">The interface inherits from the `IPersistStream` interface.</span></span> <span data-ttu-id="47e69-105">允許下列作業：</span><span class="sxs-lookup"><span data-stu-id="47e69-105">The interface allows for the following operations:</span></span>  
  
-   <span data-ttu-id="47e69-106">取得容器文件中之內嵌資料流的識別碼。</span><span class="sxs-lookup"><span data-stu-id="47e69-106">Get an identifier to the embedded stream in the container document.</span></span>  
  
-   <span data-ttu-id="47e69-107">取得包含文件 URL。</span><span class="sxs-lookup"><span data-stu-id="47e69-107">Set the URL of the containing document.</span></span>  
  
-   <span data-ttu-id="47e69-108">設定旗標，指出內嵌應用程式是否在主控環境中。</span><span class="sxs-lookup"><span data-stu-id="47e69-108">Set a flag to indicate if the embedding application is in a hosted environment.</span></span>  
  
-   <span data-ttu-id="47e69-109">設定內嵌應用程式所使用之暫存檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="47e69-109">Set the path to temporary files used by the embedding application.</span></span>  
  
-   <span data-ttu-id="47e69-110">取消目前的內嵌作業。</span><span class="sxs-lookup"><span data-stu-id="47e69-110">Cancel the current embedded operation.</span></span>  
  
-   <span data-ttu-id="47e69-111">取得要用來內嵌物件之資料流的估計大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="47e69-111">Get the estimated size (in bytes) of the stream to save the embedded object.</span></span> <span data-ttu-id="47e69-112">繼承自 `IPersistStream`。</span><span class="sxs-lookup"><span data-stu-id="47e69-112">Inherited from `IPersistStream`.</span></span>  
  
-   <span data-ttu-id="47e69-113">確認內嵌資料庫自上次儲存後是否已經變更。</span><span class="sxs-lookup"><span data-stu-id="47e69-113">Verify if the embedded database has changed since it was last saved.</span></span> <span data-ttu-id="47e69-114">繼承自 `IPersistStream`。</span><span class="sxs-lookup"><span data-stu-id="47e69-114">Inherited from `IPersistStream`.</span></span>  
  
-   <span data-ttu-id="47e69-115">將內嵌資料庫載入至本機或同處理序引擎。</span><span class="sxs-lookup"><span data-stu-id="47e69-115">Load the embedded database to the local or in-process engine.</span></span> <span data-ttu-id="47e69-116">繼承自 `IPersistStream`。</span><span class="sxs-lookup"><span data-stu-id="47e69-116">Inherited from `IPersistStream`.</span></span>  
  
-   <span data-ttu-id="47e69-117">將本機或同處理序資料庫儲存至容器文件中的內嵌資料流。</span><span class="sxs-lookup"><span data-stu-id="47e69-117">Save the local or in-process database to the embedded stream in the container document.</span></span> <span data-ttu-id="47e69-118">繼承自 `IPersistStream`。</span><span class="sxs-lookup"><span data-stu-id="47e69-118">Inherited from `IPersistStream`.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="47e69-119">參考</span><span class="sxs-lookup"><span data-stu-id="47e69-119">Reference</span></span>  
 <span data-ttu-id="47e69-120">下列參考記載 `IMDEmbedded` **msmd.h**標頭檔中所提供的介面。</span><span class="sxs-lookup"><span data-stu-id="47e69-120">The following reference documents the `IMDEmbedded` interface as presented in **msmd.h** header file.</span></span>  
  
### <a name="source-file-pxoembeddeddataidl"></a><span data-ttu-id="47e69-121">來源檔案：PXOEmbeddedData.idl</span><span class="sxs-lookup"><span data-stu-id="47e69-121">Source file: PXOEmbeddedData.idl</span></span>  
  
```  
[  
  local,                            
  object,                           
  uuid(6B6691CF-5453-41c2-ADD9-4F320B7FD421),                       
  pointer_default(unique)           
]  
interface IMDEmbeddedData : IPersistStream  
{  
 [id(1), helpstring("Set flag indicating if the application is in a hosted environment")]   
 HRESULT SetHosted(  
  [in] BOOL in_fIsHosted);  
  
 [id(2), helpstring("Set the URL for the document containing the embedded stream")]   
 HRESULT SetContainerURL(  
  [in] BSTR in_bstrURL);  
  
 [id(3), helpstring("Get identifier used to look up embedded stream in container document")]   
 HRESULT GetStreamIdentifier(  
  [out, retval] BSTR* out_pbstrStreamId);  
  
 [id(4), helpstring("Set the path used by the embedding application for temporary files")]   
 HRESULT SetTempDirPath(  
  [in]  BSTR in_bstrPath);  
  
 [id(5), helpstring("Cancel the current operation")]   
 HRESULT Cancel();  
};  
```  
  
### <a name="imdembeddeddatagetstreamidentifier"></a><span data-ttu-id="47e69-122">IMDEmbeddedData::GetStreamIdentifier</span><span class="sxs-lookup"><span data-stu-id="47e69-122">IMDEmbeddedData::GetStreamIdentifier</span></span>  
  
```  
HRESULT GetStreamIdentifier (  
    [out, retval] BSTR * out_pbstrStreamId  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="47e69-123">描述</span><span class="sxs-lookup"><span data-stu-id="47e69-123">Description</span></span>  
 <span data-ttu-id="47e69-124">取得主應用程式用來識別容器文件中之內嵌資料流的識別碼。</span><span class="sxs-lookup"><span data-stu-id="47e69-124">Gets the identifier used by the host application to the embedded stream in the container document.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="47e69-125">參數</span><span class="sxs-lookup"><span data-stu-id="47e69-125">Parameters</span></span>  
 <span data-ttu-id="47e69-126">*out_pbstrStreamId*</span><span class="sxs-lookup"><span data-stu-id="47e69-126">*out_pbstrStreamId*</span></span>  
 <span data-ttu-id="47e69-127">指定資料流識別碼的位置。</span><span class="sxs-lookup"><span data-stu-id="47e69-127">Specifies the location of the stream identifier.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="47e69-128">傳回值</span><span class="sxs-lookup"><span data-stu-id="47e69-128">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="47e69-129">成功傳回資料流識別碼。</span><span class="sxs-lookup"><span data-stu-id="47e69-129">The stream identifier was successfully returned.</span></span>  
  
 `S_FALSE`  
 <span data-ttu-id="47e69-130">沒有資料流識別碼。</span><span class="sxs-lookup"><span data-stu-id="47e69-130">There is no stream identifier.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="47e69-131">存取資料流識別碼時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="47e69-131">An error occurred accessing the stream identifier.</span></span>  
  
#### <a name="remarks"></a><span data-ttu-id="47e69-132">備註</span><span class="sxs-lookup"><span data-stu-id="47e69-132">Remarks</span></span>  
 <span data-ttu-id="47e69-133">若要確認目前連接是否包含內嵌資料庫，使用者應該從 OLE DB 連接屬性檢查 DBPROP_MSMD_EMBEDDED_DATA 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="47e69-133">To verify if the current connection contains an embedded database, the user should check the value of the DBPROP_MSMD_EMBEDDED_DATA property from the OLE DB connection properties.</span></span>  
  
 <span data-ttu-id="47e69-134">DBPROP_MSMD_EMBEDDED_DATA 的可能值如下：</span><span class="sxs-lookup"><span data-stu-id="47e69-134">The possible values for DBPROP_MSMD_EMBEDDED_DATA are:</span></span>  
  
|<span data-ttu-id="47e69-135">名稱</span><span class="sxs-lookup"><span data-stu-id="47e69-135">Name</span></span>|<span data-ttu-id="47e69-136">值</span><span class="sxs-lookup"><span data-stu-id="47e69-136">Value</span></span>|<span data-ttu-id="47e69-137">定義</span><span class="sxs-lookup"><span data-stu-id="47e69-137">Definition</span></span>|  
|----------|-----------|----------------|  
|<span data-ttu-id="47e69-138">DBPROPVAL_EMBED_NONE</span><span class="sxs-lookup"><span data-stu-id="47e69-138">DBPROPVAL_EMBED_NONE</span></span>|<span data-ttu-id="47e69-139">0x00</span><span class="sxs-lookup"><span data-stu-id="47e69-139">0x00</span></span>|<span data-ttu-id="47e69-140">沒有可用的內嵌資料庫</span><span class="sxs-lookup"><span data-stu-id="47e69-140">No embedded database available</span></span>|  
|<span data-ttu-id="47e69-141">DBPROPVAL_EMBED_EMBEDDED</span><span class="sxs-lookup"><span data-stu-id="47e69-141">DBPROPVAL_EMBED_EMBEDDED</span></span>|<span data-ttu-id="47e69-142">0x01</span><span class="sxs-lookup"><span data-stu-id="47e69-142">0x01</span></span>|<span data-ttu-id="47e69-143">目前應用程式包含內嵌資料庫</span><span class="sxs-lookup"><span data-stu-id="47e69-143">The current application contains the embedded database</span></span>|  
|<span data-ttu-id="47e69-144">DBPROPVAL_EMBED_LINKED</span><span class="sxs-lookup"><span data-stu-id="47e69-144">DBPROPVAL_EMBED_LINKED</span></span>|<span data-ttu-id="47e69-145">0x02</span><span class="sxs-lookup"><span data-stu-id="47e69-145">0x02</span></span>|<span data-ttu-id="47e69-146">內嵌資料庫裝載於遠端應用程式 (即 SharePoint Server)</span><span class="sxs-lookup"><span data-stu-id="47e69-146">The embedded database is hosted in a remote application (i.e. SharePoint Server)</span></span>|  
  
#### <a name="source"></a><span data-ttu-id="47e69-147">來源</span><span class="sxs-lookup"><span data-stu-id="47e69-147">Source</span></span>  
  
```  
[id(1), helpstring("Get identifier used to look up embedded stream in container document")]   
 HRESULT GetStreamIdentifier(  
  [out, retval] BSTR* out_pbstrStreamId);  
```  
  
### <a name="imdembeddeddatasetcontainerurl"></a><span data-ttu-id="47e69-148">IMDEmbeddedData::SetContainerURL</span><span class="sxs-lookup"><span data-stu-id="47e69-148">IMDEmbeddedData::SetContainerURL</span></span>  
  
```  
HRESULT SetContainerURL (  
    [in] BSTR in_bstrURL  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="47e69-149">描述</span><span class="sxs-lookup"><span data-stu-id="47e69-149">Description</span></span>  
 <span data-ttu-id="47e69-150">設定包含內嵌資料流之檔案的 URL。</span><span class="sxs-lookup"><span data-stu-id="47e69-150">Sets the URL for the file containing the embedded stream.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="47e69-151">參數</span><span class="sxs-lookup"><span data-stu-id="47e69-151">Parameters</span></span>  
 <span data-ttu-id="47e69-152">*in_bstrURL*</span><span class="sxs-lookup"><span data-stu-id="47e69-152">*in_bstrURL*</span></span>  
 <span data-ttu-id="47e69-153">指定包含文件 URL。</span><span class="sxs-lookup"><span data-stu-id="47e69-153">Specifies the URL for the containing document.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="47e69-154">傳回值</span><span class="sxs-lookup"><span data-stu-id="47e69-154">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="47e69-155">成功設定容器 URL。</span><span class="sxs-lookup"><span data-stu-id="47e69-155">The container URL was successfully set.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="47e69-156">設定容器 URL 時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="47e69-156">An error occurred while setting the container URL.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="47e69-157">來源</span><span class="sxs-lookup"><span data-stu-id="47e69-157">Source</span></span>  
  
```  
[id(2), helpstring("Set the URL for the document containing the embedded stream")]   
 HRESULT SetContainerURL(  
  [in] BSTR in_bstrURL);  
```  
  
### <a name="imdembeddeddatasethosted"></a><span data-ttu-id="47e69-158">IMDEmbeddedData::SetHosted</span><span class="sxs-lookup"><span data-stu-id="47e69-158">IMDEmbeddedData::SetHosted</span></span>  
  
```  
HRESULT SetHosted (  
    [in] BOOL in_fIsHosted  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="47e69-159">描述</span><span class="sxs-lookup"><span data-stu-id="47e69-159">Description</span></span>  
 <span data-ttu-id="47e69-160">設定旗標，指出內嵌應用程式是否在主控環境中。</span><span class="sxs-lookup"><span data-stu-id="47e69-160">Set a flag to indicate if the embedding application is in a hosted environment.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="47e69-161">參數</span><span class="sxs-lookup"><span data-stu-id="47e69-161">Parameters</span></span>  
 <span data-ttu-id="47e69-162">*in_ftHosted*</span><span class="sxs-lookup"><span data-stu-id="47e69-162">*in_ftHosted*</span></span>  
 <span data-ttu-id="47e69-163">如果呼叫端裝載於服務應用程式 (如 IIS)，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="47e69-163">TRUE if caller is in a hosted in a service application (like IIS).</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="47e69-164">傳回值</span><span class="sxs-lookup"><span data-stu-id="47e69-164">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="47e69-165">成功設定旗標。</span><span class="sxs-lookup"><span data-stu-id="47e69-165">The flag was successfully set.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="47e69-166">設定旗標時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="47e69-166">An error occurred while setting the flag.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="47e69-167">來源</span><span class="sxs-lookup"><span data-stu-id="47e69-167">Source</span></span>  
  
```  
[id(5), helpstring("Set flag indicating if the application is in a hosted environment")]   
 HRESULT SetHosted(  
  [in]  BOOL in_fIsHosted);  
```  
  
### <a name="imdembeddeddatasettempdirpath"></a><span data-ttu-id="47e69-168">IMDEmbeddedData::SetTempDirPath</span><span class="sxs-lookup"><span data-stu-id="47e69-168">IMDEmbeddedData::SetTempDirPath</span></span>  
  
```  
HRESULT SetTempDirPath (  
    [in] BSTR in_bstrPath  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="47e69-169">描述</span><span class="sxs-lookup"><span data-stu-id="47e69-169">Description</span></span>  
 <span data-ttu-id="47e69-170">設定內嵌應用程式所使用之暫存檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="47e69-170">Set the path to temporary files used by the embedding application.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="47e69-171">參數</span><span class="sxs-lookup"><span data-stu-id="47e69-171">Parameters</span></span>  
 <span data-ttu-id="47e69-172">*in_bstrPath*</span><span class="sxs-lookup"><span data-stu-id="47e69-172">*in_bstrPath*</span></span>  
 <span data-ttu-id="47e69-173">主應用程式用於暫存檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="47e69-173">The path used by the host application for temporary files.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="47e69-174">傳回值</span><span class="sxs-lookup"><span data-stu-id="47e69-174">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="47e69-175">成功設定暫存檔目錄。</span><span class="sxs-lookup"><span data-stu-id="47e69-175">The temporary file directory was successfully set.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="47e69-176">設定路徑時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="47e69-176">An error occurred while setting the path.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="47e69-177">來源</span><span class="sxs-lookup"><span data-stu-id="47e69-177">Source</span></span>  
  
```  
[id(4), helpstring("Set the path used by the host application for temporary files")]   
 HRESULT SetTempDirPath(  
  [in]  BSTR in_bstrPath);  
```  
  
### <a name="imdembeddeddatacancel"></a><span data-ttu-id="47e69-178">IMDEmbeddedData::Cancel</span><span class="sxs-lookup"><span data-stu-id="47e69-178">IMDEmbeddedData::Cancel</span></span>  
  
```  
HRESULT Cancel ( void )  
```  
  
#### <a name="description"></a><span data-ttu-id="47e69-179">描述</span><span class="sxs-lookup"><span data-stu-id="47e69-179">Description</span></span>  
 <span data-ttu-id="47e69-180">取消目前的內嵌資料庫作業。</span><span class="sxs-lookup"><span data-stu-id="47e69-180">Cancels the current embedded database operation</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="47e69-181">參數</span><span class="sxs-lookup"><span data-stu-id="47e69-181">Parameters</span></span>  
 <span data-ttu-id="47e69-182">無。</span><span class="sxs-lookup"><span data-stu-id="47e69-182">None.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="47e69-183">傳回值</span><span class="sxs-lookup"><span data-stu-id="47e69-183">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="47e69-184">成功取消作業。</span><span class="sxs-lookup"><span data-stu-id="47e69-184">The operation was successfully cancelled.</span></span>  
  
 `DB_E_CANTCANCEL`  
 <span data-ttu-id="47e69-185">目前沒有進行中的可取消作業。</span><span class="sxs-lookup"><span data-stu-id="47e69-185">No cancellable operation is currently in progress.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="47e69-186">取消內嵌作業時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="47e69-186">An error occurred while cancelling the embedded operation.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="47e69-187">來源</span><span class="sxs-lookup"><span data-stu-id="47e69-187">Source</span></span>  
  
```  
[id(5), helpstring("Cancel the current operation")]   
 HRESULT Cancel();  
```  
  
### <a name="imdembeddeddatagetsizemax-ipersiststreamgetsizemax"></a><span data-ttu-id="47e69-188">IMDEmbeddedData::GetSizeMax (IPersistStream::GetSizeMax)</span><span class="sxs-lookup"><span data-stu-id="47e69-188">IMDEmbeddedData::GetSizeMax (IPersistStream::GetSizeMax)</span></span>  
  
```  
HRESULT GetSizeMax (  
    [out] ULARGE_INTEGER * out_pcbSize  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="47e69-189">描述</span><span class="sxs-lookup"><span data-stu-id="47e69-189">Description</span></span>  
 <span data-ttu-id="47e69-190">取得要用來儲存內嵌物件之資料流的估計大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="47e69-190">Gets the estimated size (in bytes) of the stream to save the embedded object.</span></span> <span data-ttu-id="47e69-191">繼承自 `IPersistStream`。</span><span class="sxs-lookup"><span data-stu-id="47e69-191">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="47e69-192">參數</span><span class="sxs-lookup"><span data-stu-id="47e69-192">Parameters</span></span>  
 <span data-ttu-id="47e69-193">*in_bstrPath*</span><span class="sxs-lookup"><span data-stu-id="47e69-193">*in_bstrPath*</span></span>  
 <span data-ttu-id="47e69-194">內嵌資料庫影像的估計大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="47e69-194">The estimated size (in bytes) of the embedded database image.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="47e69-195">傳回值</span><span class="sxs-lookup"><span data-stu-id="47e69-195">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="47e69-196">成功取得大小。</span><span class="sxs-lookup"><span data-stu-id="47e69-196">The size was successfully obtained.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="47e69-197">取得大小時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="47e69-197">An error occurred while obtaining the size.</span></span>  
  
### <a name="imdembeddeddataisdirty-ipersiststreamisdirty"></a><span data-ttu-id="47e69-198">IMDEmbeddedData::IsDirty (IPersistStream::IsDirty)</span><span class="sxs-lookup"><span data-stu-id="47e69-198">IMDEmbeddedData::IsDirty (IPersistStream::IsDirty)</span></span>  
  
```  
HRESULT IsDirty ( void )  
```  
  
#### <a name="description"></a><span data-ttu-id="47e69-199">描述</span><span class="sxs-lookup"><span data-stu-id="47e69-199">Description</span></span>  
 <span data-ttu-id="47e69-200">確認內嵌資料庫自上次儲存後是否已經變更。</span><span class="sxs-lookup"><span data-stu-id="47e69-200">Verifies if the embedded database has changed since it was last saved.</span></span> <span data-ttu-id="47e69-201">繼承自 `IPersistStream`。</span><span class="sxs-lookup"><span data-stu-id="47e69-201">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="47e69-202">參數</span><span class="sxs-lookup"><span data-stu-id="47e69-202">Parameters</span></span>  
 <span data-ttu-id="47e69-203">無</span><span class="sxs-lookup"><span data-stu-id="47e69-203">none</span></span>  
  
#### <a name="return-values"></a><span data-ttu-id="47e69-204">傳回值</span><span class="sxs-lookup"><span data-stu-id="47e69-204">Return Value(s)</span></span>  
 `S_OK`  
 <span data-ttu-id="47e69-205">資料庫自上次儲存後已經變更。</span><span class="sxs-lookup"><span data-stu-id="47e69-205">The database has changed since it was last saved.</span></span>  
  
 `S_FALSE`  
 <span data-ttu-id="47e69-206">資料庫自上次儲存後尚未變更。</span><span class="sxs-lookup"><span data-stu-id="47e69-206">The database has not changed since it was last saved.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="47e69-207">取得資料庫狀態時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="47e69-207">An error occurred while obtaining the database state.</span></span>  
  
### <a name="imdembeddeddataload-ipersiststreamload"></a><span data-ttu-id="47e69-208">IMDEmbeddedData::Load (IPersistStream::Load)</span><span class="sxs-lookup"><span data-stu-id="47e69-208">IMDEmbeddedData::Load (IPersistStream::Load)</span></span>  
  
```  
HRESULT Load (   
    [in] IStream * in_pStm   
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="47e69-209">描述</span><span class="sxs-lookup"><span data-stu-id="47e69-209">Description</span></span>  
 <span data-ttu-id="47e69-210">將內嵌資料庫載入至本機或同處理序引擎。</span><span class="sxs-lookup"><span data-stu-id="47e69-210">Loads the embedded database to the local or in-process engine.</span></span> <span data-ttu-id="47e69-211">繼承自 `IPersistStream`。</span><span class="sxs-lookup"><span data-stu-id="47e69-211">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="47e69-212">參數</span><span class="sxs-lookup"><span data-stu-id="47e69-212">Parameters</span></span>  
 <span data-ttu-id="47e69-213">*in_pStm*</span><span class="sxs-lookup"><span data-stu-id="47e69-213">*in_pStm*</span></span>  
 <span data-ttu-id="47e69-214">載入內嵌資料庫之來源資料流介面的指標。</span><span class="sxs-lookup"><span data-stu-id="47e69-214">A pointer to a stream interface from where to load the embedded database.</span></span>  
  
#### <a name="return-values"></a><span data-ttu-id="47e69-215">傳回值</span><span class="sxs-lookup"><span data-stu-id="47e69-215">Return Value(s)</span></span>  
 `S_OK`  
 <span data-ttu-id="47e69-216">成功載入資料庫。</span><span class="sxs-lookup"><span data-stu-id="47e69-216">The database was successfully loaded.</span></span>  
  
 `E_OUTOFMEMORY`  
 <span data-ttu-id="47e69-217">記憶體不足，無法載入資料庫。</span><span class="sxs-lookup"><span data-stu-id="47e69-217">Not enough memory to load the database.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="47e69-218">載入資料庫時發生錯誤 (不同於 `E_OUTOFMEMORY`)。</span><span class="sxs-lookup"><span data-stu-id="47e69-218">An error occurred while loading the database, different than `E_OUTOFMEMORY`.</span></span>  
  
### <a name="imdembeddeddatasave-ipersiststreamsave"></a><span data-ttu-id="47e69-219">IMDEmbeddedData::Save (IPersistStream::Save)</span><span class="sxs-lookup"><span data-stu-id="47e69-219">IMDEmbeddedData::Save (IPersistStream::Save)</span></span>  
  
```  
HRESULT Save (   
    [in] IStream * in_pStm,  
    [in] BOOL in_fClearDirty  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="47e69-220">描述</span><span class="sxs-lookup"><span data-stu-id="47e69-220">Description</span></span>  
 <span data-ttu-id="47e69-221">將本機或同處理序資料庫儲存至容器文件中的內嵌資料流。</span><span class="sxs-lookup"><span data-stu-id="47e69-221">Saves the local or in-process database to the embedded stream in the container document.</span></span> <span data-ttu-id="47e69-222">繼承自 `IPersistStream`。</span><span class="sxs-lookup"><span data-stu-id="47e69-222">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="47e69-223">參數</span><span class="sxs-lookup"><span data-stu-id="47e69-223">Parameters</span></span>  
 <span data-ttu-id="47e69-224">*in_pStm*</span><span class="sxs-lookup"><span data-stu-id="47e69-224">*in_pStm*</span></span>  
 <span data-ttu-id="47e69-225">要用來儲存內嵌資料庫之資料流介面的指標。</span><span class="sxs-lookup"><span data-stu-id="47e69-225">A pointer to a stream interface to where to save the embedded database.</span></span>  
  
 <span data-ttu-id="47e69-226">*in_fClearDirty*</span><span class="sxs-lookup"><span data-stu-id="47e69-226">*in_fClearDirty*</span></span>  
 <span data-ttu-id="47e69-227">旗標，指出是否應該在這項作業後清除記錄變更旗標。</span><span class="sxs-lookup"><span data-stu-id="47e69-227">A flag that indicates whether the dirty flag should be cleared after this operation.</span></span>  
  
#### <a name="return-values"></a><span data-ttu-id="47e69-228">傳回值</span><span class="sxs-lookup"><span data-stu-id="47e69-228">Return Value(s)</span></span>  
 `S_OK`  
 <span data-ttu-id="47e69-229">成功儲存資料庫。</span><span class="sxs-lookup"><span data-stu-id="47e69-229">The database was successfully saved.</span></span>  
  
 `STG_E_CANTSAVE`  
 <span data-ttu-id="47e69-230">儲存資料庫時發生錯誤 (不同於 `STG_E_MEDIUMFULL`)。</span><span class="sxs-lookup"><span data-stu-id="47e69-230">An error occurred while saving the database, different than `STG_E_MEDIUMFULL`.</span></span>  
  
 `STG_E_MEDIUMFULL`  
 <span data-ttu-id="47e69-231">因為儲存裝置上沒有剩餘空間，無法儲存資料庫。</span><span class="sxs-lookup"><span data-stu-id="47e69-231">The database could not be saved because there is no space left on the storage device.</span></span>  
  
  
