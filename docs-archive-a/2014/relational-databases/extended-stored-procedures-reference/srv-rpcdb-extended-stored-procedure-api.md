---
title: srv_rpcdb (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcdb
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcdb
ms.assetid: d52bfd22-7a7c-4ab0-af65-df96ff359e6f
author: rothja
ms.author: jroth
ms.openlocfilehash: c951a4a821bbd49748182d9ddf5df017344a174d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707569"
---
# <a name="srv_rpcdb-extended-stored-procedure-api"></a><span data-ttu-id="27a9b-102">srv_rpcdb (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="27a9b-102">srv_rpcdb (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="27a9b-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="27a9b-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="27a9b-104">傳回目前遠端預存程序的資料庫名稱元件。</span><span class="sxs-lookup"><span data-stu-id="27a9b-104">Returns the database name component for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27a9b-105">語法</span><span class="sxs-lookup"><span data-stu-id="27a9b-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_rpcdb (  
SRV_PROC * srvproc,int *len );  
```  
  
## <a name="arguments"></a><span data-ttu-id="27a9b-106">引數</span><span class="sxs-lookup"><span data-stu-id="27a9b-106">Arguments</span></span>  
 <span data-ttu-id="27a9b-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="27a9b-107">*srvproc*</span></span>  
 <span data-ttu-id="27a9b-108">是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="27a9b-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="27a9b-109">擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="27a9b-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="27a9b-110">*len*</span><span class="sxs-lookup"><span data-stu-id="27a9b-110">*len*</span></span>  
 <span data-ttu-id="27a9b-111">`int` 變數的指標，此變數會接收資料庫名稱的長度。</span><span class="sxs-lookup"><span data-stu-id="27a9b-111">Is a pointer to an `int` variable that receives the length of the database name.</span></span> <span data-ttu-id="27a9b-112">如果 *len* 為 NULL，則不會傳回資料庫名稱的長度。</span><span class="sxs-lookup"><span data-stu-id="27a9b-112">If *len* is NULL, the length of the database name is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="27a9b-113">傳回</span><span class="sxs-lookup"><span data-stu-id="27a9b-113">Returns</span></span>  
 <span data-ttu-id="27a9b-114">目前遠端預存程序的資料庫名稱部分以 null 結尾字串的 DBCHAR 指標。</span><span class="sxs-lookup"><span data-stu-id="27a9b-114">A DBCHAR pointer to the null-terminated string for the database name part of the current remote stored procedure.</span></span> <span data-ttu-id="27a9b-115">如果沒有目前遠端預存程序，則會傳回 NULL 且 *len* 參數設定為 - 1。</span><span class="sxs-lookup"><span data-stu-id="27a9b-115">If there is no current remote stored procedure, NULL is returned and the *len* parameter is set to - 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27a9b-116">備註</span><span class="sxs-lookup"><span data-stu-id="27a9b-116">Remarks</span></span>  
 <span data-ttu-id="27a9b-117">函數只會傳回遠端預存程序物件名稱的資料庫元件。</span><span class="sxs-lookup"><span data-stu-id="27a9b-117">This function returns only the database component of the remote stored procedure object name.</span></span> <span data-ttu-id="27a9b-118">其中不包含擁有人、遠端預存程序名稱和遠端預存程序號碼的選擇性規範。</span><span class="sxs-lookup"><span data-stu-id="27a9b-118">It does not include the optional specifiers for owner, remote stored procedure name, and remote stored procedure number.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="27a9b-119">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="27a9b-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="27a9b-120">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="27a9b-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
