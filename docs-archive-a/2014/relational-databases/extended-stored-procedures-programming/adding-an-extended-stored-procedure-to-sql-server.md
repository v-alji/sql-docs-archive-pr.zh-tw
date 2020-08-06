---
title: 將擴充預存程式加入至 SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], adding
- adding extended stored procedures
- collations [SQL Server], extended stored procedures
ms.assetid: 10f1bb74-3b43-4efd-b7ab-7a85a8600a50
author: rothja
ms.author: jroth
ms.openlocfilehash: 03ac8c2a0fa9ce77db59d50b3a7b9da42415e013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598399"
---
# <a name="adding-an-extended-stored-procedure-to-sql-server"></a><span data-ttu-id="a5b03-102">將擴充預存程序加入至 SQL Server</span><span class="sxs-lookup"><span data-stu-id="a5b03-102">Adding an Extended Stored Procedure to SQL Server</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="a5b03-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="a5b03-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="a5b03-104">包含擴充預存程序的 DLL 會當做 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="a5b03-104">A DLL that contains extended stored procedure functions acts as an extension to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a5b03-105">若要安裝 DLL，請將檔案複製到包含標準 DLL 檔案的目錄，如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (C:\Program FILES\MICROSOFT SQL Server\MSSQL12.0.*x*\MSSQL\Binn 預設) 。</span><span class="sxs-lookup"><span data-stu-id="a5b03-105">To install the DLL, copy the file to a directory, such as the one that contains the standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL files (C:\Program Files\Microsoft SQL Server\MSSQL12.0.*x*\MSSQL\Binn by default).</span></span>  
  
 <span data-ttu-id="a5b03-106">在擴充預存程序 DLL 已經複製到伺服器之後，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員必須向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 註冊 DLL 中的每個擴充預存程序函數。</span><span class="sxs-lookup"><span data-stu-id="a5b03-106">After the extended stored procedure DLL has been copied to the server, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator must register to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] each extended stored procedure function in the DLL.</span></span> <span data-ttu-id="a5b03-107">這項作業是使用 sp_addextendedproc 系統預存程序完成的。</span><span class="sxs-lookup"><span data-stu-id="a5b03-107">This is done using the sp_addextendedproc system stored procedure.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a5b03-108">系統管理員應該先徹底檢閱擴充預存程序，確定其中不含任何有害或惡意的程式碼，然後再將擴充預存程序加入至伺服器並將執行權限授與其他使用者。</span><span class="sxs-lookup"><span data-stu-id="a5b03-108">The system administrator should thoroughly review an extended stored procedure to ensure that it does not contain harmful or malicious code before adding it to the server and granting execute permissions to other users.</span></span>  <span data-ttu-id="a5b03-109">驗證所有使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="a5b03-109">Validate all user input.</span></span> <span data-ttu-id="a5b03-110">在使用者輸入完成驗證前，請勿加以串連。</span><span class="sxs-lookup"><span data-stu-id="a5b03-110">Do not concatenate user input before validating it.</span></span> <span data-ttu-id="a5b03-111">請勿執行由未經驗證之使用者輸入所建構的命令。</span><span class="sxs-lookup"><span data-stu-id="a5b03-111">Never execute a command constructed from unvalidated user input.</span></span>  
  
 <span data-ttu-id="a5b03-112">sp_addextendedproc 的第一個參數會指定函數的名稱，而第二個參數會指定函數所在之 DLL 的名稱。</span><span class="sxs-lookup"><span data-stu-id="a5b03-112">The first parameter of sp_addextendedproc specifies the name of the function, and the second parameter specifies the name of the DLL in which that function resides.</span></span> <span data-ttu-id="a5b03-113">建議您指定 DLL 的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="a5b03-113">It is recommended that you specify the complete path of the DLL.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a5b03-114">在升級到 SQL Server 2005 或更新版本之後，沒有用完整路徑註冊的現有 DLL 將無法運作。</span><span class="sxs-lookup"><span data-stu-id="a5b03-114">Existing DLLs that were not registered with a complete path will not work after upgrading to SQL Server 2005 or later.</span></span> <span data-ttu-id="a5b03-115">若要更正這個問題，請利用 sp_dropextendedproc 來取消註冊 DLL，再利用 sp_addextendedproc 並指定完整路徑來重新註冊它。</span><span class="sxs-lookup"><span data-stu-id="a5b03-115">To correct the problem, use sp_dropextendedproc to unregister the DLL, and then reregister it with sp_addextendedproc, specifying the complete path.</span></span>  
  
 <span data-ttu-id="a5b03-116">在 `sp_addextendedproc` 中指定的函數名稱必須與 DLL 中的函數名稱完全相同 (包括大小寫)。</span><span class="sxs-lookup"><span data-stu-id="a5b03-116">The name of the function specified in `sp_addextendedproc` must be exactly the same, including the case, as the function's name in the DLL.</span></span> <span data-ttu-id="a5b03-117">例如，此命令會註冊 `xp_hello,` 函數 (位於名為 `xp_hello.dll` 的 dll 中) 當做 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 擴充預存程序：</span><span class="sxs-lookup"><span data-stu-id="a5b03-117">For example, this command registers a function `xp_hello,` located in a dll named `xp_hello.dll`, as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] extended stored procedure:</span></span>  
  
```  
sp_addextendedproc 'xp_hello', 'c:\Program Files\Microsoft SQL Server\MSSQL12.0.MSSQLSERVER\MSSQL\Binn\xp_hello.dll';  
```  
  
 <span data-ttu-id="a5b03-118">如果在 `sp_addextendedproc` 中指定的函數名稱並未與 DLL 中的函數名稱完全相符，系統將會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中註冊新名稱，但是此名稱將無法使用。</span><span class="sxs-lookup"><span data-stu-id="a5b03-118">If the name of the function specified in `sp_addextendedproc` does not exactly match the function name in the DLL, the new name will be registered in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but the name will not be usable.</span></span> <span data-ttu-id="a5b03-119">例如，雖然 `xp_Hello` 會註冊為位於的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 擴充預存程式 `xp_hello.dll` ，但 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如果您稍後使用呼叫函式，將無法在 DLL 中找到該函式 `xp_Hello` 。</span><span class="sxs-lookup"><span data-stu-id="a5b03-119">For example, although `xp_Hello` is registered as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] extended stored procedure located in `xp_hello.dll`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not be able to find the function in the DLL if you use `xp_Hello` to call the function later.</span></span>  
  
```  
--Register the function (xp_hello) with an initial upper case  
sp_addextendedproc 'xp_Hello', 'c:\xp_hello.dll';  
  
--Use the newly registered name to call the function  
DECLARE @txt varchar(33);  
EXEC xp_Hello @txt OUTPUT;  
  
--This is the error message  
Server: Msg 17750, Level 16, State 1, Procedure xp_Hello, Line 1  
Could not load the DLL xp_hello.dll, or one of the DLLs it references. Reason: 127(The specified procedure could not be found.).  
```  
  
 <span data-ttu-id="a5b03-120">如果在 `sp_addextendedproc` 中指定的函數名稱與 DLL 中的函數名稱完全相符，而且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的定序不會區分大小寫，使用者就可以使用名稱的任何大小寫字母組合來呼叫此擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="a5b03-120">If the name of the function specified in `sp_addextendedproc` matches exactly the function name in the DLL, and the collation of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is case-insensitive, the user can call the extended stored procedure using any combination of lower- and upper-case letters of the name.</span></span>  
  
```  
--Register the function (xp_hello)  
sp_addextendedproc 'xp_hello', 'c:\xp_hello.dll';  
  
--The following will succeed in calling xp_hello  
DECLARE @txt varchar(33);  
EXEC xp_Hello @txt OUTPUT;  
  
DECLARE @txt varchar(33);  
EXEC xp_HelLO @txt OUTPUT;  
  
DECLARE @txt varchar(33);  
EXEC xp_HELLO @txt OUTPUT;  
```  
  
 <span data-ttu-id="a5b03-121">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的定序會區分大小寫時，如果使用不同的大小寫來呼叫此擴充預存程序，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 就無法呼叫此擴充預存程序，即使它使用完全相同的名稱和定序註冊成 DLL 中的函數也一樣。</span><span class="sxs-lookup"><span data-stu-id="a5b03-121">When the collation of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is case-sensitive, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not be able to call the extended stored procedure -- even if it was registered with exactly the same name and collation as the function in the DLL -- if the procedure is called with a different case.</span></span>  
  
```  
--Register the function (xp_hello)  
sp_addextendedproc 'xp_hello', 'c:\xp_hello.dll';  
  
--The following will result in an error  
DECLARE @txt varchar(33);  
EXEC xp_HELLO @txt OUTPUT;  
  
--This is the error  
Server: Msg 2812, Level 16, State 62, Line 1  
```  
  
 <span data-ttu-id="a5b03-122">您不需要停止並重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a5b03-122">It is not necessary to stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b03-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5b03-123">See Also</span></span>  
 <span data-ttu-id="a5b03-124">[sp_addextendedproc &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a5b03-124">[sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span></span>  
 [<span data-ttu-id="a5b03-125">sp_dropextendedproc &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a5b03-125">sp_dropextendedproc &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
