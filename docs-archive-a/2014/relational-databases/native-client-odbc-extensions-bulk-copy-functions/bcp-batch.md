---
title: bcp_batch |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_batch
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
author: rothja
ms.author: jroth
ms.openlocfilehash: 24cdf6e2934c2b80a55d8fa1fcc572a976b636ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595939"
---
# <a name="bcp_batch"></a><span data-ttu-id="c4843-102">bcp_batch</span><span class="sxs-lookup"><span data-stu-id="c4843-102">bcp_batch</span></span>
  <span data-ttu-id="c4843-103">認可先前從程式變數大量複製並由 bcp_sendrow 傳送至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的[bcp_sendrow](bcp-sendrow.md)所有資料列。</span><span class="sxs-lookup"><span data-stu-id="c4843-103">Commits all rows previously bulk copied from program variables and sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4843-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4843-104">Syntax</span></span>  
  
```  
  
DBINT bcp_batch (HDBC  
hdbc  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="c4843-105">引數</span><span class="sxs-lookup"><span data-stu-id="c4843-105">Arguments</span></span>  
 <span data-ttu-id="c4843-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="c4843-106">*hdbc*</span></span>  
 <span data-ttu-id="c4843-107">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="c4843-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="c4843-108">傳回</span><span class="sxs-lookup"><span data-stu-id="c4843-108">Returns</span></span>  
 <span data-ttu-id="c4843-109">最後一次呼叫**bcp_batch**之後所儲存的資料列數，如果發生錯誤，則為-1。</span><span class="sxs-lookup"><span data-stu-id="c4843-109">The number of rows saved after the last call to **bcp_batch**, or -1 in case of error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4843-110">備註</span><span class="sxs-lookup"><span data-stu-id="c4843-110">Remarks</span></span>  
 <span data-ttu-id="c4843-111">大量複製批次會定義交易。</span><span class="sxs-lookup"><span data-stu-id="c4843-111">Bulk copy batches define transactions.</span></span> <span data-ttu-id="c4843-112">當應用程式使用[bcp_bind](bcp-bind.md)和**bcp_sendrow**將程式變數中的資料列大量複製到 SQL Server 資料表時，只有在程式呼叫**bcp_batch**或[bcp_done](bcp-done.md)時，才會認可這些資料列。</span><span class="sxs-lookup"><span data-stu-id="c4843-112">When an application uses [bcp_bind](bcp-bind.md) and **bcp_sendrow** to bulk copy rows from program variables to SQL Server tables, the rows are committed only when the program calls **bcp_batch** or [bcp_done](bcp-done.md).</span></span>  
  
 <span data-ttu-id="c4843-113">您可以**bcp_batch**每*n*個數據列，或在傳入資料中有牢靠時， (與遙測應用程式) 。</span><span class="sxs-lookup"><span data-stu-id="c4843-113">You can call **bcp_batch** once every *n* rows or when there is a lull in incoming data (as in a telemetry application).</span></span> <span data-ttu-id="c4843-114">如果應用程式不會呼叫**bcp_batch**只有在呼叫**bcp_done**時，才會認可大量複製的資料列。</span><span class="sxs-lookup"><span data-stu-id="c4843-114">If an application does not call **bcp_batch** the bulk copied rows are committed only when **bcp_done** is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4843-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4843-115">See Also</span></span>  
 [<span data-ttu-id="c4843-116">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="c4843-116">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
