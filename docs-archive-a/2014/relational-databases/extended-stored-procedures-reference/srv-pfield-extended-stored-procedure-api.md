---
title: srv_pfield (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_pfield
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_pfield
ms.assetid: a61e4c1f-e65b-48ea-a7d1-3e1544af389d
author: rothja
ms.author: jroth
ms.openlocfilehash: 90680d59dbf36ad3f713fd7a09d07553890a8668
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709481"
---
# <a name="srv_pfield-extended-stored-procedure-api"></a><span data-ttu-id="cca39-102">srv_pfield (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="cca39-102">srv_pfield (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="cca39-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="cca39-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="cca39-104">傳回資料庫連接的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cca39-104">Returns information about a database connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cca39-105">語法</span><span class="sxs-lookup"><span data-stu-id="cca39-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_pfield (  
SRV_PROC *  
srvproc  
,  
int   
field  
,  
int *  
len  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="cca39-106">引數</span><span class="sxs-lookup"><span data-stu-id="cca39-106">Arguments</span></span>  
 <span data-ttu-id="cca39-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="cca39-107">*srvproc*</span></span>  
 <span data-ttu-id="cca39-108">識別資料庫連接的指標。</span><span class="sxs-lookup"><span data-stu-id="cca39-108">Pointer identifying a database connection.</span></span>  
  
 <span data-ttu-id="cca39-109">*欄位*</span><span class="sxs-lookup"><span data-stu-id="cca39-109">*field*</span></span>  
 <span data-ttu-id="cca39-110">指定連接上要傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="cca39-110">Specifies data on the connection to return.</span></span>  
  
|<span data-ttu-id="cca39-111">值</span><span class="sxs-lookup"><span data-stu-id="cca39-111">Value</span></span>|<span data-ttu-id="cca39-112">傳回</span><span class="sxs-lookup"><span data-stu-id="cca39-112">Returns</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="cca39-113">SRV_APPLNAME</span><span class="sxs-lookup"><span data-stu-id="cca39-113">SRV_APPLNAME</span></span>|<span data-ttu-id="cca39-114">用戶端建立連接時所提供的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="cca39-114">The application name provided by the client when it established the connection.</span></span>|  
|<span data-ttu-id="cca39-115">SRV_BCPFLAG</span><span class="sxs-lookup"><span data-stu-id="cca39-115">SRV_BCPFLAG</span></span>|<span data-ttu-id="cca39-116">如果用戶端正在準備進行大量複製作業，則為 TRUE 的旗標，否則為 FALSE 的旗標。</span><span class="sxs-lookup"><span data-stu-id="cca39-116">A flag that is TRUE if the client is preparing for a bulk copy operation; otherwise, FALSE.</span></span>|  
|<span data-ttu-id="cca39-117">SRV_CLIB</span><span class="sxs-lookup"><span data-stu-id="cca39-117">SRV_CLIB</span></span>|<span data-ttu-id="cca39-118">讓用戶端與伺服器溝通之程式庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="cca39-118">The name of the library that enables the client to talk to a server.</span></span>|  
|<span data-ttu-id="cca39-119">SRV_CPID</span><span class="sxs-lookup"><span data-stu-id="cca39-119">SRV_CPID</span></span>|<span data-ttu-id="cca39-120">用戶端來源電腦上的用戶端處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="cca39-120">The client process ID on the client source computer.</span></span>|  
|<span data-ttu-id="cca39-121">SRV_HOST</span><span class="sxs-lookup"><span data-stu-id="cca39-121">SRV_HOST</span></span>|<span data-ttu-id="cca39-122">用戶端建立連接時所提供的用戶端電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="cca39-122">The name of the client's machine provided by the client when it established the connection.</span></span>|  
|<span data-ttu-id="cca39-123">SRV_LIBVERS</span><span class="sxs-lookup"><span data-stu-id="cca39-123">SRV_LIBVERS</span></span>|<span data-ttu-id="cca39-124">用戶端程式庫的版本。</span><span class="sxs-lookup"><span data-stu-id="cca39-124">The version of the client library.</span></span>|  
|<span data-ttu-id="cca39-125">SRV_LSECURE</span><span class="sxs-lookup"><span data-stu-id="cca39-125">SRV_LSECURE</span></span>|<span data-ttu-id="cca39-126">旗標。</span><span class="sxs-lookup"><span data-stu-id="cca39-126">A flag.</span></span> <span data-ttu-id="cca39-127">如果連接使用整合安全性登入，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="cca39-127">TRUE if the connection used integrated security to login.</span></span>|  
|<span data-ttu-id="cca39-128">SRV_NETWORK_MODULE</span><span class="sxs-lookup"><span data-stu-id="cca39-128">SRV_NETWORK_MODULE</span></span>|<span data-ttu-id="cca39-129">連接使用的網路程式庫 DLL 名稱。</span><span class="sxs-lookup"><span data-stu-id="cca39-129">The name of the Net-Library DLL used by the connection.</span></span>|  
|<span data-ttu-id="cca39-130">SRV_NETWORK_VERSION</span><span class="sxs-lookup"><span data-stu-id="cca39-130">SRV_NETWORK_VERSION</span></span>|<span data-ttu-id="cca39-131">連接使用的網路程式庫 DLL 版本。</span><span class="sxs-lookup"><span data-stu-id="cca39-131">The version of the Net-Library DLL used by the connection.</span></span>|  
|<span data-ttu-id="cca39-132">SRV_NETWORK_CONNECTION</span><span class="sxs-lookup"><span data-stu-id="cca39-132">SRV_NETWORK_CONNECTION</span></span>|<span data-ttu-id="cca39-133">傳遞到用於目前 *srvproc* 連線之網路程式庫 DLL 的連接字串。</span><span class="sxs-lookup"><span data-stu-id="cca39-133">The connection string passed to the Net-Library DLL used for the current *srvproc* connection.</span></span>|  
|<span data-ttu-id="cca39-134">SRV_PIPEHANDLE</span><span class="sxs-lookup"><span data-stu-id="cca39-134">SRV_PIPEHANDLE</span></span>|<span data-ttu-id="cca39-135">包含連接用戶端之管道控制碼的字串，如果用戶端連接到不使用具名管道的網路，則為 NULL。</span><span class="sxs-lookup"><span data-stu-id="cca39-135">A string containing the pipe handle of a connected client, or NULL if the client is connected on a network that does not use named pipes.</span></span> <span data-ttu-id="cca39-136">若要搭配 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 使用此控制碼當做有效的管道控制碼，請將此字串轉換為整數。</span><span class="sxs-lookup"><span data-stu-id="cca39-136">To use this handle as a valid pipe handle with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, convert this string to an integer.</span></span>|  
|<span data-ttu-id="cca39-137">SRV_RMTSERVER</span><span class="sxs-lookup"><span data-stu-id="cca39-137">SRV_RMTSERVER</span></span>|<span data-ttu-id="cca39-138">用戶端處理序所登入的伺服器。</span><span class="sxs-lookup"><span data-stu-id="cca39-138">The server from which the client process is logged in.</span></span> <span data-ttu-id="cca39-139">如果登入來自用戶端，此值為空字串。</span><span class="sxs-lookup"><span data-stu-id="cca39-139">If the login is from a client, this value is an empty string.</span></span>|  
|<span data-ttu-id="cca39-140">SRV_ROWSENT</span><span class="sxs-lookup"><span data-stu-id="cca39-140">SRV_ROWSENT</span></span>|<span data-ttu-id="cca39-141">*srvproc* 已經針對目前結果集所傳送的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="cca39-141">The number of rows already sent by *srvproc* for the current set of results.</span></span>|  
|<span data-ttu-id="cca39-142">SRV_SPID</span><span class="sxs-lookup"><span data-stu-id="cca39-142">SRV_SPID</span></span>|<span data-ttu-id="cca39-143">*srvproc* 的伺服器執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="cca39-143">The server thread ID of the *srvproc*.</span></span> <span data-ttu-id="cca39-144">對於擴充預存程序，此值與 **sys.sysprocesses** 的 **kpid** 資料行相同，而且可以隨時變更。</span><span class="sxs-lookup"><span data-stu-id="cca39-144">For extended stored procedures, this value is the same as the **kpid** column of **sys.sysprocesses**, and it can change over time.</span></span>|  
|<span data-ttu-id="cca39-145">SRV_SPROC_CODEPAGE</span><span class="sxs-lookup"><span data-stu-id="cca39-145">SRV_SPROC_CODEPAGE</span></span>|<span data-ttu-id="cca39-146">伺服器用於解譯多位元組資料的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="cca39-146">Codepage that the server uses to interpret multbyte data.</span></span>|  
|<span data-ttu-id="cca39-147">SRV_STATUS</span><span class="sxs-lookup"><span data-stu-id="cca39-147">SRV_STATUS</span></span>|<span data-ttu-id="cca39-148">*srvproc* 的目前狀態：執行中或已關閉</span><span class="sxs-lookup"><span data-stu-id="cca39-148">The current status of *srvproc*: running or closed</span></span>|  
|<span data-ttu-id="cca39-149">SRV_TYPE</span><span class="sxs-lookup"><span data-stu-id="cca39-149">SRV_TYPE</span></span>|<span data-ttu-id="cca39-150">*srvproc* 的連線類型。</span><span class="sxs-lookup"><span data-stu-id="cca39-150">The connection type of *srvproc*.</span></span> <span data-ttu-id="cca39-151">如果傳回伺服器，*srvproc* 來自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cca39-151">If server is returned, *srvproc* is from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cca39-152">如果傳回用戶端，*srvproc* 來自 DB 程式庫或 ODBC 用戶端。</span><span class="sxs-lookup"><span data-stu-id="cca39-152">If client is returned, *srvproc* is from a DB-Library or ODBC client.</span></span>|  
|<span data-ttu-id="cca39-153">SRV_USER</span><span class="sxs-lookup"><span data-stu-id="cca39-153">SRV_USER</span></span>|<span data-ttu-id="cca39-154">連接的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="cca39-154">The user name of the connection.</span></span>|  
|||  
  
 <span data-ttu-id="cca39-155">*len*</span><span class="sxs-lookup"><span data-stu-id="cca39-155">*len*</span></span>  
 <span data-ttu-id="cca39-156">這是指向 **int** 變數的指標，該變數含有傳回 *field* 值的長度。</span><span class="sxs-lookup"><span data-stu-id="cca39-156">Is a pointer to an **int** variable that contains the length of the returned *field* value.</span></span> <span data-ttu-id="cca39-157">如果 *len* 是 NULL，則不會傳回字串的長度。</span><span class="sxs-lookup"><span data-stu-id="cca39-157">If *len* is NULL, the length of the string is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="cca39-158">傳回</span><span class="sxs-lookup"><span data-stu-id="cca39-158">Returns</span></span>  
 <span data-ttu-id="cca39-159">以 Null 結束的字串指標，其中包含指定之欄位在 SRV_PROC 結構中的目前值。</span><span class="sxs-lookup"><span data-stu-id="cca39-159">A pointer to a null-terminated string containing the current value for the specified field in the SRV_PROC structure.</span></span> <span data-ttu-id="cca39-160">如果欄位是空的，則會傳回空字串的有效指標，而且 *len* 包含 0。</span><span class="sxs-lookup"><span data-stu-id="cca39-160">If the field is empty, a valid pointer to an empty string is returned and *len* contains 0.</span></span> <span data-ttu-id="cca39-161">如果欄位不明，會傳回 NULL，而且 *len* 包含值 -1。</span><span class="sxs-lookup"><span data-stu-id="cca39-161">If the field is unknown, NULL is returned and *len* contains the value -1.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cca39-162">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="cca39-162">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="cca39-163">如需安全性檢閱和測試的資訊，請參閱[資訊安全開發人員中心](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="cca39-163">For information about security review and testing, see the [Security Developer Center](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
