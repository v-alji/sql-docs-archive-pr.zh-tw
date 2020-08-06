---
title: srv_message_handler (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_message_handler
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_message_handler
ms.assetid: 41bcd057-436f-4fa8-8293-fc8057a30877
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e7b6472ed4fabb6dc2d545eb51a1e026635ce19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593397"
---
# <a name="srv_message_handler-extended-stored-procedure-api"></a><span data-ttu-id="541df-102">srv_message_handler (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="541df-102">srv_message_handler (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="541df-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="541df-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="541df-104">呼叫安裝的擴充預存程序 API 訊息處理常式。</span><span class="sxs-lookup"><span data-stu-id="541df-104">Calls the installed Extended Stored Procedure API message handler.</span></span> <span data-ttu-id="541df-105">此函數通常用來 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 從擴充預存程式呼叫，以記錄錯誤 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記錄檔或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 應用程式記錄檔中由擴充預存程式) 所定義的錯誤 (。</span><span class="sxs-lookup"><span data-stu-id="541df-105">This function is usually used to call [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from an extended stored procedure to log an error (defined by the extended stored procedure) in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log file or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="541df-106">語法</span><span class="sxs-lookup"><span data-stu-id="541df-106">Syntax</span></span>  
  
```  
  
int srv_message_handler (  
SRV_PROC *  
srvproc  
,  
int  
errornum  
,  
BYTE   
severity  
,  
BYTE  
state  
,  
int  
oserrnum  
,  
char *  
errtext  
,  
int  
errtextlen  
,  
char *  
oserrtext  
,  
int  
oserrtextlen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="541df-107">引數</span><span class="sxs-lookup"><span data-stu-id="541df-107">Arguments</span></span>  
 <span data-ttu-id="541df-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="541df-108">*srvproc*</span></span>  
 <span data-ttu-id="541df-109">是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="541df-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="541df-110">*srvproc* 參數所包含的資訊可用來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="541df-110">The *srvproc* parameter contains information that is used to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="541df-111">*errornum*</span><span class="sxs-lookup"><span data-stu-id="541df-111">*errornum*</span></span>  
 <span data-ttu-id="541df-112">這是擴充預存程序所定義的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="541df-112">Is an error number defined by the extended stored procedure.</span></span> <span data-ttu-id="541df-113">這個數字的範圍必須是從 50,001 到 2,147,483,647。</span><span class="sxs-lookup"><span data-stu-id="541df-113">This number must be from 50,001 through 2,147,483,647.</span></span>  
  
 <span data-ttu-id="541df-114">*severity*</span><span class="sxs-lookup"><span data-stu-id="541df-114">*severity*</span></span>  
 <span data-ttu-id="541df-115">這是錯誤的標準 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 嚴重性值。</span><span class="sxs-lookup"><span data-stu-id="541df-115">Is a standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] severity value for the error.</span></span> <span data-ttu-id="541df-116">這個數字的範圍必須是從 0 到 24。</span><span class="sxs-lookup"><span data-stu-id="541df-116">This number must be from 0 through 24.</span></span>  
  
 <span data-ttu-id="541df-117">*state*</span><span class="sxs-lookup"><span data-stu-id="541df-117">*state*</span></span>  
 <span data-ttu-id="541df-118">這是錯誤的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 狀態值。</span><span class="sxs-lookup"><span data-stu-id="541df-118">Is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] state value for the error.</span></span>  
  
 <span data-ttu-id="541df-119">*oserrnum*</span><span class="sxs-lookup"><span data-stu-id="541df-119">*oserrnum*</span></span>  
 <span data-ttu-id="541df-120">這是作業系統錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="541df-120">Is the operating-system error number.</span></span> <span data-ttu-id="541df-121">忽略這個引數。</span><span class="sxs-lookup"><span data-stu-id="541df-121">This argument is ignored.</span></span>  
  
 <span data-ttu-id="541df-122">*errtext*</span><span class="sxs-lookup"><span data-stu-id="541df-122">*errtext*</span></span>  
 <span data-ttu-id="541df-123">這是擴充預存程序錯誤 *errornum* 的描述。</span><span class="sxs-lookup"><span data-stu-id="541df-123">Is the description of the extended stored procedure error *errornum*.</span></span>  
  
 <span data-ttu-id="541df-124">*errtextlen*</span><span class="sxs-lookup"><span data-stu-id="541df-124">*errtextlen*</span></span>  
 <span data-ttu-id="541df-125">這是擴充預存程序錯誤字串 *errtext* 的長度。</span><span class="sxs-lookup"><span data-stu-id="541df-125">Is the length of the extended stored procedure error string *errtext*.</span></span>  
  
 <span data-ttu-id="541df-126">*oserrtext*</span><span class="sxs-lookup"><span data-stu-id="541df-126">*oserrtext*</span></span>  
 <span data-ttu-id="541df-127">這是作業系統錯誤 *oserrnum* 的描述。</span><span class="sxs-lookup"><span data-stu-id="541df-127">Is the description of the operating-system error *oserrnum*.</span></span> <span data-ttu-id="541df-128">忽略這個引數。</span><span class="sxs-lookup"><span data-stu-id="541df-128">This argument is ignored.</span></span>  
  
 <span data-ttu-id="541df-129">*oserrtextlen*</span><span class="sxs-lookup"><span data-stu-id="541df-129">*oserrtextlen*</span></span>  
 <span data-ttu-id="541df-130">這是作業系統錯誤字串 *oserrtext* 的長度。</span><span class="sxs-lookup"><span data-stu-id="541df-130">Is the length of the operating-system error string *oserrtext*.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="541df-131">傳回</span><span class="sxs-lookup"><span data-stu-id="541df-131">Returns</span></span>  
 <span data-ttu-id="541df-132">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="541df-132">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="541df-133">備註</span><span class="sxs-lookup"><span data-stu-id="541df-133">Remarks</span></span>  
 <span data-ttu-id="541df-134">**srv_message_handler** 函式讓擴充預存程序可以與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的集中式錯誤記錄和報告功能進行整合。</span><span class="sxs-lookup"><span data-stu-id="541df-134">The **srv_message_handler** function enables an extended stored procedure to integrate with the centralized error logging and reporting features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="541df-135">您可以從擴充預存程序為事件建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 警示，而 SQL Server Agent 會針對這些警示條件進行監視。</span><span class="sxs-lookup"><span data-stu-id="541df-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alerts can be established for events from extended stored procedures, and SQL Server Agent will monitor for these alert conditions.</span></span>  
  
 <span data-ttu-id="541df-136">如果錯誤訊息較長，就會截斷為 412 個位元組。</span><span class="sxs-lookup"><span data-stu-id="541df-136">If the error message is longer, it is truncated to 412 bytes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="541df-137">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="541df-137">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="541df-138">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="541df-138">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
