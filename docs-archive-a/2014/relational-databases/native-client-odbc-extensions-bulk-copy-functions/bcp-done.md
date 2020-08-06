---
title: bcp_done |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_done
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_done function
ms.assetid: e59b3f16-5b59-40da-880f-f3edf657d1ee
author: rothja
ms.author: jroth
ms.openlocfilehash: cb9b0cbcc927fcd10c2d81b3c5c3d39bb80a8e9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584478"
---
# <a name="bcp_done"></a><span data-ttu-id="ab638-102">bcp_done</span><span class="sxs-lookup"><span data-stu-id="ab638-102">bcp_done</span></span>
  <span data-ttu-id="ab638-103">結束從程式變數進行大量複製，以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [bcp_sendrow](bcp-sendrow.md)執行。</span><span class="sxs-lookup"><span data-stu-id="ab638-103">Ends a bulk copy from program variables to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performed with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab638-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab638-104">Syntax</span></span>  
  
```  
  
DBINT bcp_done (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="ab638-105">引數</span><span class="sxs-lookup"><span data-stu-id="ab638-105">Arguments</span></span>  
 <span data-ttu-id="ab638-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="ab638-106">*hdbc*</span></span>  
 <span data-ttu-id="ab638-107">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="ab638-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="ab638-108">傳回</span><span class="sxs-lookup"><span data-stu-id="ab638-108">Returns</span></span>  
 <span data-ttu-id="ab638-109">在最後一次呼叫[bcp_batch](bcp-batch.md)之後永久儲存的資料列數，如果發生錯誤，則為-1。</span><span class="sxs-lookup"><span data-stu-id="ab638-109">The number of rows permanently saved after the last call to [bcp_batch](bcp-batch.md) or -1 in case of error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab638-110">備註</span><span class="sxs-lookup"><span data-stu-id="ab638-110">Remarks</span></span>  
 <span data-ttu-id="ab638-111">呼叫[bcp_sendrow](bcp-sendrow.md)或[bcp_moretext](bcp-moretext.md)的最後一次呼叫之後**bcp_done** 。</span><span class="sxs-lookup"><span data-stu-id="ab638-111">Call **bcp_done** after the last call to [bcp_sendrow](bcp-sendrow.md) or [bcp_moretext](bcp-moretext.md).</span></span> <span data-ttu-id="ab638-112">複製所有資料之後，無法呼叫**bcp_done**會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab638-112">Failure to call **bcp_done** after copying all data results in errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab638-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab638-113">See Also</span></span>  
 [<span data-ttu-id="ab638-114">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="ab638-114">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
