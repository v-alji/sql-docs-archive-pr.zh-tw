---
title: bcp_columns |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_columns
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_columns function
ms.assetid: 5376f6fe-9508-439a-8c66-778d77f19ac3
author: rothja
ms.author: jroth
ms.openlocfilehash: 028bb80e88a29b366e3a489abae06c8b3b30cdf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698158"
---
# <a name="bcp_columns"></a><span data-ttu-id="0c4a8-102">bcp_columns</span><span class="sxs-lookup"><span data-stu-id="0c4a8-102">bcp_columns</span></span>
  <span data-ttu-id="0c4a8-103">設定在使用者檔案中可搭配大量複製在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中進出作業的資料行總數。</span><span class="sxs-lookup"><span data-stu-id="0c4a8-103">Sets the total number of columns found in the user file for use with a bulk copy into or out of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0c4a8-104">[bcp_setbulkmode](bcp-setbulkmode.md)可以用來取代 bcp_columns 和[bcp_colfmt](bcp-colfmt.md)。</span><span class="sxs-lookup"><span data-stu-id="0c4a8-104">[bcp_setbulkmode](bcp-setbulkmode.md) can be used instead of bcp_columns and [bcp_colfmt](bcp-colfmt.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c4a8-105">語法</span><span class="sxs-lookup"><span data-stu-id="0c4a8-105">Syntax</span></span>  
  
```  
  
RETCODE bcp_columns (  
HDBC   
hdbc  
,  
INT   
nColumns  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="0c4a8-106">引數</span><span class="sxs-lookup"><span data-stu-id="0c4a8-106">Arguments</span></span>  
 <span data-ttu-id="0c4a8-107">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="0c4a8-107">*hdbc*</span></span>  
 <span data-ttu-id="0c4a8-108">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="0c4a8-108">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="0c4a8-109">*nColumns*</span><span class="sxs-lookup"><span data-stu-id="0c4a8-109">*nColumns*</span></span>  
 <span data-ttu-id="0c4a8-110">這是使用者檔案中的資料行總數。</span><span class="sxs-lookup"><span data-stu-id="0c4a8-110">Is the total number of columns in the user file.</span></span> <span data-ttu-id="0c4a8-111">即使您準備要將資料從使用者檔案大量複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表，而不想複製使用者檔案中的所有資料行，還是必須將*nColumns*設定為使用者檔案資料行的總數。</span><span class="sxs-lookup"><span data-stu-id="0c4a8-111">Even if you are preparing to bulk copy data from the user file to an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table and do not intend to copy all columns in the user file, you must still set *nColumns* to the total number of user-file columns.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="0c4a8-112">傳回</span><span class="sxs-lookup"><span data-stu-id="0c4a8-112">Returns</span></span>  
 <span data-ttu-id="0c4a8-113">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="0c4a8-113">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c4a8-114">備註</span><span class="sxs-lookup"><span data-stu-id="0c4a8-114">Remarks</span></span>  
 <span data-ttu-id="0c4a8-115">只有在使用有效的檔案名呼叫[bcp_init](bcp-init.md)之後，才能呼叫此函式。</span><span class="sxs-lookup"><span data-stu-id="0c4a8-115">This function can be called only after [bcp_init](bcp-init.md) has been called with a valid file name.</span></span>  
  
 <span data-ttu-id="0c4a8-116">只有打算使用與預設值不同的使用者檔案格式時，才可以呼叫此函數。</span><span class="sxs-lookup"><span data-stu-id="0c4a8-116">You should call this function only if you intend to use a user-file format that differs from the default.</span></span> <span data-ttu-id="0c4a8-117">如需預設使用者檔案格式之描述的詳細資訊，請參閱**bcp_init**。</span><span class="sxs-lookup"><span data-stu-id="0c4a8-117">For more information about a description of the default user-file format, see **bcp_init**.</span></span>  
  
 <span data-ttu-id="0c4a8-118">呼叫之後 `bcp_columns` ，您必須針對使用者檔案中的每個資料行呼叫[bcp_colfmt](bcp-colfmt.md)，以完整定義自訂檔案格式。</span><span class="sxs-lookup"><span data-stu-id="0c4a8-118">After calling `bcp_columns`, you must call [bcp_colfmt](bcp-colfmt.md)for each column in the user file to completely define a custom file format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c4a8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c4a8-119">See Also</span></span>  
 [<span data-ttu-id="0c4a8-120">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="0c4a8-120">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
