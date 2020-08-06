---
title: 建立擴充預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- warnings [SQL Server]
- extended stored procedures [SQL Server], debugging
- extended stored procedures [SQL Server], creating
- messages [SQL Server], extended stored procedures
ms.assetid: 9f7c0cdb-6d88-44c0-b049-29953ae75717
author: rothja
ms.author: jroth
ms.openlocfilehash: d243b27b8542ec5fe10d795de1729d6c1fe484c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598397"
---
# <a name="creating-extended-stored-procedures"></a><span data-ttu-id="6a5ca-102">建立擴充預存程序</span><span class="sxs-lookup"><span data-stu-id="6a5ca-102">Creating Extended Stored Procedures</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="6a5ca-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="6a5ca-104">擴充預存程序是包含原型的函數：</span><span class="sxs-lookup"><span data-stu-id="6a5ca-104">An extended stored procedure is a function with a prototype:</span></span>  
  
 <span data-ttu-id="6a5ca-105">SRVRETCODE *xp_extendedProcName* **(** SRVPROC **\*);**</span><span class="sxs-lookup"><span data-stu-id="6a5ca-105">SRVRETCODE *xp_extendedProcName* **(** SRVPROC **\*);**</span></span>  
  
 <span data-ttu-id="6a5ca-106">使用前置詞 xp_ 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-106">Using the prefix xp_ is optional.</span></span> <span data-ttu-id="6a5ca-107">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中參考時，無論安裝在伺服器上的字碼頁/排序次序為何，擴充預存程序名稱都會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-107">Extended stored procedure names are case sensitive when referenced in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, regardless of code page/sort order installed on the server.</span></span> <span data-ttu-id="6a5ca-108">當您建立 DLL 時：</span><span class="sxs-lookup"><span data-stu-id="6a5ca-108">When you build a DLL:</span></span>  
  
-   <span data-ttu-id="6a5ca-109">如果需要進入點，撰寫 DllMain 函數。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-109">If an entry point is necessary, write a DllMain function.</span></span>  
  
     <span data-ttu-id="6a5ca-110">此函數是選擇性的；如果您在原始程式碼中沒有提供此函數，編譯器會連結其自己的版本，這個版本只會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-110">This function is optional; if you do not provide it in source code, the compiler links its own version, which does nothing but return TRUE.</span></span> <span data-ttu-id="6a5ca-111">如果您提供 DllMain 函數，當執行緒或處理序附加到 DLL 或從 DLL 卸離時，作業系統會呼叫此函數。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-111">If you provide a DllMain function, the operating system calls this function when a thread or process attaches to or detaches from the DLL.</span></span>  
  
-   <span data-ttu-id="6a5ca-112">系統必須匯出從 DLL 外部呼叫的所有函數 (所有擴充預存程序函數)。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-112">All functions called from outside the DLL (all extended stored procedure Efunctions) must be exported.</span></span>  
  
     <span data-ttu-id="6a5ca-113">您可以藉由在 .def 檔案的 [匯出] 區段中列出函式的名稱來匯出函式，也可以在原始程式碼中的函式名稱前面加上 __declspec (dllexport) ，Microsoft 編譯器擴充功能 (請注意，_declspec \_ ( # A4 的開頭為兩個底線) 。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-113">You can export a function by listing its name in the EXPORTS section of a .def file, or you can prefix the function name in the source code with __declspec(dllexport), a Microsoft compiler extension (Note that \__declspec() begins with two underscores).</span></span>  
  
 <span data-ttu-id="6a5ca-114">建立擴充預存程序 DLL 時需要這些檔案。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-114">These files are required for creating an extended stored procedure DLL.</span></span>  
  
|<span data-ttu-id="6a5ca-115">檔案</span><span class="sxs-lookup"><span data-stu-id="6a5ca-115">File</span></span>|<span data-ttu-id="6a5ca-116">描述</span><span class="sxs-lookup"><span data-stu-id="6a5ca-116">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="6a5ca-117">Srv.h</span><span class="sxs-lookup"><span data-stu-id="6a5ca-117">Srv.h</span></span>|<span data-ttu-id="6a5ca-118">擴充預存程序 API 標頭檔案</span><span class="sxs-lookup"><span data-stu-id="6a5ca-118">Extended Stored Procedure API header file</span></span>|  
|<span data-ttu-id="6a5ca-119">Opends60.lib</span><span class="sxs-lookup"><span data-stu-id="6a5ca-119">Opends60.lib</span></span>|<span data-ttu-id="6a5ca-120">Opends60.dll 的匯入程式庫</span><span class="sxs-lookup"><span data-stu-id="6a5ca-120">Import library for Opends60.dll</span></span>|  
  
 <span data-ttu-id="6a5ca-121">若要建立擴充預存程序 DLL，建立動態連結程式庫類型的專案。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-121">To create an extended stored procedure DLL, create a project of type Dynamic Link Library.</span></span> <span data-ttu-id="6a5ca-122">如需有關建立 DLL 的詳細資訊，請參閱開發環境文件集。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-122">For more information about creating a DLL, see the development environment documentation.</span></span>  
  
 <span data-ttu-id="6a5ca-123">強烈建議您所有擴充預存程序 DLL 都實作並匯出下列函數：</span><span class="sxs-lookup"><span data-stu-id="6a5ca-123">It is highly recommended that all extended stored procedure DLLs implement and export the following function:</span></span>  
  
```  
__declspec(dllexport) ULONG __GetXpVersion()  
{  
   return ODS_VERSION;  
}  
```  
  
> [!NOTE]  
>  <span data-ttu-id="6a5ca-124">__declspec (dllexport) 是 Microsoft 專用的編譯器副檔名。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-124">__declspec(dllexport) is a Microsoft-specific compiler extension.</span></span> <span data-ttu-id="6a5ca-125">如果您的編譯器不支援此指示詞，您應該在 DEF 檔案的 EXPORTS 區段下匯出這個函數。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-125">If your compiler does not support this directive, you should export this function in your DEF file under the EXPORTS section.</span></span>  
  
 <span data-ttu-id="6a5ca-126">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以追蹤旗標（T260）啟動時，或如果具有系統管理員許可權的使用者執行 DBCC TRACEON (260) ，而且如果擴充預存程式 DLL 不支援 __GetXpVersion ( # A3，則會出現警告訊息 (錯誤8131：擴充預存程式 dll '% ' 未匯出 _GetXpVersion \_ # A6。 ( 會列印到錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-126">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started with the trace flag -T260 or if a user with system administrator privileges runs DBCC TRACEON (260), and if the extended stored procedure DLL does not support __GetXpVersion(), a warning message (Error 8131: Extended stored procedure DLL '%' does not export \__GetXpVersion().) is printed to the error log.</span></span> <span data-ttu-id="6a5ca-127"> (請注意， \_ _GetXpVersion ( # A2 會以兩個底線開頭。 ) </span><span class="sxs-lookup"><span data-stu-id="6a5ca-127">(Note that \__GetXpVersion() begins with two underscores.)</span></span>  
  
 <span data-ttu-id="6a5ca-128">如果擴充預存程序 DLL 匯出 __GetXpVersion()，但是函數所傳回的版本低於伺服器所需要的版本，敘述函數所傳回之版本以及伺服器所需之版本的警告訊息就會列印到錯誤記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-128">If the extended stored procedure DLL exports __GetXpVersion(), but the version returned by the function is less than that required by the server, a warning message stating the version returned by the function and the version expected by the server is printed to the error log.</span></span> <span data-ttu-id="6a5ca-129">如果您收到此訊息，則會從 _GetXpVersion ( # A1 傳回不正確的值 \_ ，或使用較舊版本的 srv 來進行編譯。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-129">If you get this message, you are returning an incorrect value from \__GetXpVersion(), or you are compiling with an older version of srv.h.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6a5ca-130">SetErrorMode 是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 函數，不應該在擴充預存程序中呼叫。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-130">SetErrorMode, a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 function, should not be called in extended stored procedures.</span></span>  
  
 <span data-ttu-id="6a5ca-131">建議長時間執行的擴充預存程序應該定期呼叫 srv_got_attention，讓該程序可以在連接遭到清除或批次遭到中止時自行結束。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-131">It is recommended that a long-running extended stored procedure should call srv_got_attention periodically so that the procedure can terminate itself if the connection is killed or the batch is aborted.</span></span>  
  
 <span data-ttu-id="6a5ca-132">若要為擴充預存程序 DLL 偵錯，將其複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Binn 目錄。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-132">To debug an extended stored procedure DLL, copy it to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Binn directory.</span></span> <span data-ttu-id="6a5ca-133">若要指定偵錯工具的可執行檔，請輸入可執行檔的路徑和檔案名 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (例如 C:\PROGRAM Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe) 。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-133">To specify the executable for the debugging session, enter the path and file name of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executable file (for example, C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe).</span></span> <span data-ttu-id="6a5ca-134">如需 sqlservr.exe 引數的詳細資訊，請參閱[Sqlservr.exe 應用程式](../../tools/sqlservr-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6a5ca-134">For information about sqlservr arguments, see [sqlservr Application](../../tools/sqlservr-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a5ca-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a5ca-135">See Also</span></span>  
 [<span data-ttu-id="6a5ca-136">srv_got_attention &#40;擴充預存程式 API&#41;</span><span class="sxs-lookup"><span data-stu-id="6a5ca-136">srv_got_attention &#40;Extended Stored Procedure API&#41;</span></span>](../extended-stored-procedures-reference/srv-got-attention-extended-stored-procedure-api.md)  
  
  
