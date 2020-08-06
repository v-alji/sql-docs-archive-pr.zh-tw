---
title: SqlCoNtext 物件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- Windows identity [CLR integration]
- SqlContext object
- context [CLR integration]
ms.assetid: 67437853-8a55-44d9-9337-90689ebba730
author: rothja
ms.author: jroth
ms.openlocfilehash: 10f036e274925f7b28b79f619f8e24b3e8804140
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702986"
---
# <a name="sqlcontext-object"></a><span data-ttu-id="b9d49-102">SqlContext 物件</span><span class="sxs-lookup"><span data-stu-id="b9d49-102">SqlContext Object</span></span>
  <span data-ttu-id="b9d49-103">當您呼叫程序或函數、在 Common Language Runtime (CLR) 使用者定義型別上呼叫方法，或您的動作引發以任何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 語言定義的觸發程序時，會在伺服器中叫用 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b9d49-103">You invoke managed code in the server when you call a procedure or function, when you call a method on a common language runtime (CLR) user-defined type, or when your action fires a trigger defined in any of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework languages.</span></span> <span data-ttu-id="b9d49-104">因為要求執行此程式碼做為使用者連接的一部分，所以需要從伺服器上執行的程式碼，存取呼叫端的內容。</span><span class="sxs-lookup"><span data-stu-id="b9d49-104">Because execution of this code is requested as part of a user connection, access to the context of the caller from the code running in the server is required.</span></span> <span data-ttu-id="b9d49-105">此外，特定資料存取作業只有在呼叫端的內容下執行才會有效。</span><span class="sxs-lookup"><span data-stu-id="b9d49-105">In addition, certain data access operations may only be valid if run under the context of the caller.</span></span> <span data-ttu-id="b9d49-106">例如，對在觸發程序作業中使用之插入及刪除虛擬資料表的存取，只有在呼叫端的內容下才有效。</span><span class="sxs-lookup"><span data-stu-id="b9d49-106">For example, access to inserted and deleted pseudo-tables used in trigger operations is only valid under the context of the caller.</span></span>  
  
 <span data-ttu-id="b9d49-107">呼叫端的內容會在 `SqlContext` 物件中擷取。</span><span class="sxs-lookup"><span data-stu-id="b9d49-107">The context of the caller is abstracted in a `SqlContext` object.</span></span> <span data-ttu-id="b9d49-108">如需有關 `SqlTriggerContext` 方法和屬性的詳細資訊，請參閱 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 中的 `Microsoft.SqlServer.Server.SqlTriggerContext` 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="b9d49-108">For more information about the `SqlTriggerContext` methods and properties, see the `Microsoft.SqlServer.Server.SqlTriggerContext` class reference documentation in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
 <span data-ttu-id="b9d49-109">`SqlContext` 會提供下列元件的存取：</span><span class="sxs-lookup"><span data-stu-id="b9d49-109">`SqlContext` provides access to the following components:</span></span>  
  
-   <span data-ttu-id="b9d49-110">`SqlPipe`：`SqlPipe` 物件表示結果藉以流向用戶端的「管道」。</span><span class="sxs-lookup"><span data-stu-id="b9d49-110">`SqlPipe`: The `SqlPipe` object represents the "pipe" through which results flow to the client.</span></span> <span data-ttu-id="b9d49-111">如需物件的詳細資訊 `SqlPipe` ，請參閱[SqlPipe 物件](sqlpipe-object.md)。</span><span class="sxs-lookup"><span data-stu-id="b9d49-111">For more information about the `SqlPipe` object, see [SqlPipe Object](sqlpipe-object.md).</span></span>  
  
-   <span data-ttu-id="b9d49-112">`SqlTriggerContext`：`SqlTriggerContext` 物件只能在 CLR 觸發程序內擷取。</span><span class="sxs-lookup"><span data-stu-id="b9d49-112">`SqlTriggerContext`: The `SqlTriggerContext` object can only be retrieved from within a CLR trigger.</span></span> <span data-ttu-id="b9d49-113">它提供造成引發觸發程序的作業及已更新資料行之對應的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b9d49-113">It provides information about the operation that caused the trigger to fire and a map of the columns that were updated.</span></span> <span data-ttu-id="b9d49-114">如需物件的詳細資訊 `SqlTriggerContext` ，請參閱[SqlTriggerCoNtext 物件](sqltriggercontext-object.md)。</span><span class="sxs-lookup"><span data-stu-id="b9d49-114">For more information about the `SqlTriggerContext` object, see [SqlTriggerContext Object](sqltriggercontext-object.md).</span></span>  
  
-   <span data-ttu-id="b9d49-115">`IsAvailable`：`IsAvailable` 屬性用於判斷內容可用性。</span><span class="sxs-lookup"><span data-stu-id="b9d49-115">`IsAvailable`: The `IsAvailable` property is used to determine context availability.</span></span>  
  
-   <span data-ttu-id="b9d49-116">`WindowsIdentity`：`WindowsIdentity` 屬性用於擷取呼叫端的 Windows 識別。</span><span class="sxs-lookup"><span data-stu-id="b9d49-116">`WindowsIdentity`: The `WindowsIdentity` property is used to retrieve the Windows identity of the caller.</span></span>  
  
## <a name="determining-context-availability"></a><span data-ttu-id="b9d49-117">決定內容可用性</span><span class="sxs-lookup"><span data-stu-id="b9d49-117">Determining Context Availability</span></span>  
 <span data-ttu-id="b9d49-118">查詢 `SqlContext` 類別，以查看目前執行的程式碼是否同處理序執行。</span><span class="sxs-lookup"><span data-stu-id="b9d49-118">Query the `SqlContext` class to see if the currently executing code is running in-process.</span></span> <span data-ttu-id="b9d49-119">若要這樣做，請檢查 `IsAvailable` 物件的 `SqlContext` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b9d49-119">To do this, check the `IsAvailable` property of the `SqlContext` object.</span></span> <span data-ttu-id="b9d49-120">如果呼叫程式碼在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 內執行，且可存取其他 `IsAvailable` 成員，則 `True` 屬性是唯讀的，並會傳回 `SqlContext`。</span><span class="sxs-lookup"><span data-stu-id="b9d49-120">The `IsAvailable` property is read-only, and returns `True` if the calling code is running inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and if other `SqlContext` members can be accessed.</span></span> <span data-ttu-id="b9d49-121">如果 `IsAvailable` 屬性傳回 `False`，則使用的其他所有 `SqlContext` 成員會擲回 `InvalidOperationException`。</span><span class="sxs-lookup"><span data-stu-id="b9d49-121">If the `IsAvailable` property returns `False`, all the other `SqlContext` members throw an `InvalidOperationException`, if used.</span></span> <span data-ttu-id="b9d49-122">如果 `IsAvailable` 傳回 `False`，則開啟連接字串中包括 "context connection=true" 之連接物件的任何嘗試都會失敗。</span><span class="sxs-lookup"><span data-stu-id="b9d49-122">If `IsAvailable` returns `False`, any attempt to open a connection object that has "context connection=true" in the connection string fails.</span></span>  
  
## <a name="retrieving-windows-identity"></a><span data-ttu-id="b9d49-123">擷取 Windows 識別</span><span class="sxs-lookup"><span data-stu-id="b9d49-123">Retrieving Windows Identity</span></span>  
 <span data-ttu-id="b9d49-124">在處理序帳戶的內容中，永遠會叫用在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 內執行的 CLR 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b9d49-124">CLR code executing inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is always invoked in the context of the process account.</span></span> <span data-ttu-id="b9d49-125">如果程式碼應使用呼叫使用者的識別 (而非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序識別) 執行特定動作，則應透過 `WindowsIdentity` 物件的 `SqlContext` 屬性取得模擬 Token。</span><span class="sxs-lookup"><span data-stu-id="b9d49-125">If the code should perform certain actions using the identity of the calling user, instead of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process identity, then an impersonation token should be obtained through the `WindowsIdentity` property of the `SqlContext` object.</span></span> <span data-ttu-id="b9d49-126">`WindowsIdentity` 屬性會傳回表示呼叫端之 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 識別的 `WindowsIdentity` 執行個體，或者，如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證來驗證用戶端，則會傳回 Null。</span><span class="sxs-lookup"><span data-stu-id="b9d49-126">The `WindowsIdentity` property returns a `WindowsIdentity` instance representing the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows identity of the caller, or null if the client was authenticated using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="b9d49-127">只有以 `EXTERNAL_ACCESS` 或 `UNSAFE` 使用權限標記的組件才能存取此屬性。</span><span class="sxs-lookup"><span data-stu-id="b9d49-127">Only assemblies marked with `EXTERNAL_ACCESS` or `UNSAFE` permissions can access this property.</span></span>  
  
 <span data-ttu-id="b9d49-128">取得 `WindowsIdentity` 物件之後，呼叫端可以模擬用戶端帳戶，並代表它執行動作。</span><span class="sxs-lookup"><span data-stu-id="b9d49-128">After obtaining the `WindowsIdentity` object, callers can impersonate the client account and perform actions on their behalf.</span></span>  
  
 <span data-ttu-id="b9d49-129">如果開始執行預存程序或函數的用戶端連接至使用 Windows 驗證的伺服器，則只能透過 `SqlContext.WindowsIdentity` 使用呼叫端的識別。</span><span class="sxs-lookup"><span data-stu-id="b9d49-129">The identity of the caller is only available through `SqlContext.WindowsIdentity` if the client that initiated execution of the stored-procedure or function connected to the server using Windows Authentication.</span></span> <span data-ttu-id="b9d49-130">如果改用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，則此屬性為 Null，而且程式碼無法模擬呼叫端。</span><span class="sxs-lookup"><span data-stu-id="b9d49-130">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication was used instead, this property is null and the code is unable to impersonate the caller.</span></span>  
  
### <a name="example"></a><span data-ttu-id="b9d49-131">範例</span><span class="sxs-lookup"><span data-stu-id="b9d49-131">Example</span></span>  
 <span data-ttu-id="b9d49-132">下列範例示範如何取得呼叫用戶端的 Windows 識別以及模擬該用戶端。</span><span class="sxs-lookup"><span data-stu-id="b9d49-132">The following example shows how to get the Windows identity of the calling client and impersonate the client.</span></span>  
  
 <span data-ttu-id="b9d49-133">C#</span><span class="sxs-lookup"><span data-stu-id="b9d49-133">C#</span></span>  
  
```  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void WindowsIDTestProc()  
{  
    WindowsIdentity clientId = null;  
    WindowsImpersonationContext impersonatedUser = null;  
  
    // Get the client ID.  
    clientId = SqlContext.WindowsIdentity;  
  
    // This outer try block is used to thwart exception filter   
    // attacks which would prevent the inner finally   
    // block from executing and resetting the impersonation.  
    try  
    {  
        try  
        {  
            impersonatedUser = clientId.Impersonate();  
            if (impersonatedUser != null)  
            {  
                // Perform some action using impersonation.  
            }  
        }  
        finally  
        {  
            // Undo impersonation.  
            if (impersonatedUser != null)  
                impersonatedUser.Undo();  
        }  
    }  
    catch  
    {  
        throw;  
    }  
}  
```  
  
 <span data-ttu-id="b9d49-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9d49-134">Visual Basic</span></span>  
  
```  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  WindowsIDTestProcVB ()  
    Dim clientId As WindowsIdentity  
    Dim impersonatedUser As WindowsImpersonationContext  
  
    ' Get the client ID.  
    clientId = SqlContext.WindowsIdentity  
  
    ' This outer try block is used to thwart exception filter   
    ' attacks which would prevent the inner finally   
    ' block from executing and resetting the impersonation.  
  
    Try  
        Try  
  
            impersonatedUser = clientId.Impersonate()  
  
            If impersonatedUser IsNot Nothing Then  
                ' Perform some action using impersonation.  
            End If  
  
        Finally  
            ' Undo impersonation.  
            If impersonatedUser IsNot Nothing Then  
                impersonatedUser.Undo()  
            End If  
        End Try  
  
    Catch e As Exception  
  
        Throw e  
  
    End Try  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9d49-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9d49-135">See Also</span></span>  
 <span data-ttu-id="b9d49-136">[SqlPipe 物件](sqlpipe-object.md) </span><span class="sxs-lookup"><span data-stu-id="b9d49-136">[SqlPipe Object](sqlpipe-object.md) </span></span>  
 <span data-ttu-id="b9d49-137">[SqlTriggerCoNtext 物件](sqltriggercontext-object.md) </span><span class="sxs-lookup"><span data-stu-id="b9d49-137">[SqlTriggerContext Object](sqltriggercontext-object.md) </span></span>  
 <span data-ttu-id="b9d49-138">[CLR 觸發程式](../../database-engine/dev-guide/clr-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="b9d49-138">[CLR Triggers](../../database-engine/dev-guide/clr-triggers.md) </span></span>  
 [<span data-ttu-id="b9d49-139">ADO.NET 的 SQL Server 同處理序特定擴充</span><span class="sxs-lookup"><span data-stu-id="b9d49-139">SQL Server In-Process Specific Extensions to ADO.NET</span></span>](sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
