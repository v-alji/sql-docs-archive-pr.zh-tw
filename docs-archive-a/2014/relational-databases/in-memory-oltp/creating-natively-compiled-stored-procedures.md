---
title: 建立原生編譯的預存程序 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e6b34010-cf62-4f65-bbdf-117f291cde7b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3e8e8139427c7f2ad92eea856be8da542f65e344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593390"
---
# <a name="creating-natively-compiled-stored-procedures"></a><span data-ttu-id="480cf-102">建立原生編譯的預存程序</span><span class="sxs-lookup"><span data-stu-id="480cf-102">Creating Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="480cf-103">原生編譯預存程序不會實作完整 [!INCLUDE[tsql](../../includes/tsql-md.md)] 可程式性和查詢介面區。</span><span class="sxs-lookup"><span data-stu-id="480cf-103">Natively compiled stored procedures do not implement the full [!INCLUDE[tsql](../../includes/tsql-md.md)] programmability and query surface area.</span></span> <span data-ttu-id="480cf-104">某些 [!INCLUDE[tsql](../../includes/tsql-md.md)] 建構無法在原生編譯的預存程序內使用。</span><span class="sxs-lookup"><span data-stu-id="480cf-104">There are certain [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs that cannot be used inside natively compiled stored procedures.</span></span> <span data-ttu-id="480cf-105">如需詳細資訊，請參閱原生[編譯預存程式中支援的結構](../in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md)。</span><span class="sxs-lookup"><span data-stu-id="480cf-105">For more information, see [Supported Constructs in Natively Compiled Stored Procedures](../in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).</span></span>  
  
 <span data-ttu-id="480cf-106">但有幾個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 功能只可供原生編譯的預存程序使用：</span><span class="sxs-lookup"><span data-stu-id="480cf-106">There are, however, several [!INCLUDE[tsql](../../includes/tsql-md.md)] features that are only supported for natively compiled stored procedures:</span></span>  
  
-   <span data-ttu-id="480cf-107">不可部分完成的區塊。</span><span class="sxs-lookup"><span data-stu-id="480cf-107">Atomic blocks.</span></span> <span data-ttu-id="480cf-108">如需詳細資訊，請參閱 [Atomic Blocks](atomic-blocks-in-native-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="480cf-108">For more information, see [Atomic Blocks](atomic-blocks-in-native-procedures.md).</span></span>  
  
-   <span data-ttu-id="480cf-109">原生編譯的預存程序中，變數和參數的 `NOT NULL` 條件約束。</span><span class="sxs-lookup"><span data-stu-id="480cf-109">`NOT NULL` constraints on parameters of and variables in natively compiled stored procedures.</span></span> <span data-ttu-id="480cf-110">您不能指派 `NULL` 值給宣告為 `NOT NULL` 的參數或變數。</span><span class="sxs-lookup"><span data-stu-id="480cf-110">You cannot assign `NULL` values to parameters or variables declared as `NOT NULL`.</span></span> <span data-ttu-id="480cf-111">如需詳細資訊，請參閱 [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="480cf-111">For more information, see [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql).</span></span>  
  
-   <span data-ttu-id="480cf-112">原生編譯預存程序的結構描述繫結。</span><span class="sxs-lookup"><span data-stu-id="480cf-112">Schema binding of natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="480cf-113">使用 [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)建立原生編譯的預存程序。</span><span class="sxs-lookup"><span data-stu-id="480cf-113">Natively compiled stored procedures are created using [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).</span></span> <span data-ttu-id="480cf-114">下列範例會顯示記憶體最佳化的資料表以及用來將資料列插入資料表中的原生編譯預存程序。</span><span class="sxs-lookup"><span data-stu-id="480cf-114">The following example shows a memory-optimized table and a natively compiled stored procedure used for inserting rows into the table.</span></span>  
  
```sql  
create table dbo.Ord  
(OrdNo integer not null primary key nonclustered,   
 OrdDate datetime not null,   
 CustCode nvarchar(5) not null)   
 with (memory_optimized=on)  
go  
  
create procedure dbo.OrderInsert(@OrdNo integer, @CustCode nvarchar(5))  
with native_compilation, schemabinding, execute as owner  
as   
begin atomic with  
(transaction isolation level = snapshot,  
language = N'English')  
  
  declare @OrdDate datetime = getdate();  
  insert into dbo.Ord (OrdNo, CustCode, OrdDate) values (@OrdNo, @CustCode, @OrdDate);  
end  
go  
```  
  
 <span data-ttu-id="480cf-115">在程式碼範例中，`NATIVE_COMPILATION` 表示這個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序是原生編譯的預存程序。</span><span class="sxs-lookup"><span data-stu-id="480cf-115">In the code sample, `NATIVE_COMPILATION` indicates that this [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure is a natively compiled stored procedure.</span></span> <span data-ttu-id="480cf-116">以下是必要的選項：</span><span class="sxs-lookup"><span data-stu-id="480cf-116">The following options are required:</span></span>  
  
|<span data-ttu-id="480cf-117">選項</span><span class="sxs-lookup"><span data-stu-id="480cf-117">Option</span></span>|<span data-ttu-id="480cf-118">描述</span><span class="sxs-lookup"><span data-stu-id="480cf-118">Description</span></span>|  
|------------|-----------------|  
|`SCHEMABINDING`|<span data-ttu-id="480cf-119">原生編譯的預存程序必須繫結至其所參考之物件的結構描述。</span><span class="sxs-lookup"><span data-stu-id="480cf-119">Natively compiled stored procedures must be bound to the schema of the objects it references.</span></span> <span data-ttu-id="480cf-120">這表示，此程序所參考的資料表將無法卸除。</span><span class="sxs-lookup"><span data-stu-id="480cf-120">This means that table references by the procedure cannot be dropped.</span></span> <span data-ttu-id="480cf-121">程式中參考的資料表必須包含其架構名稱，而且查詢中 \* 不允許 () 的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="480cf-121">Tables referenced in the procedure must include their schema name, and wildcards (\*) are not allowed in queries.</span></span> <span data-ttu-id="480cf-122">只有這個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本中的原生編譯預存程序才支援 `SCHEMABINDING`。</span><span class="sxs-lookup"><span data-stu-id="480cf-122">`SCHEMABINDING` is only supported for natively compiled stored procedures in this version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>|  
|`EXECUTE AS`|<span data-ttu-id="480cf-123">原生編譯的預存程序不支援 `EXECUTE AS CALLER` (預設執行內容)。</span><span class="sxs-lookup"><span data-stu-id="480cf-123">Natively compiled stored procedures do not support `EXECUTE AS CALLER`, which is the default execution context.</span></span> <span data-ttu-id="480cf-124">因此，需要指定執行內容。</span><span class="sxs-lookup"><span data-stu-id="480cf-124">Therefore, specifying the execution context is required.</span></span> <span data-ttu-id="480cf-125">支援選項 `EXECUTE AS OWNER` 、 `EXECUTE AS` *使用者*和 `EXECUTE AS SELF` 。</span><span class="sxs-lookup"><span data-stu-id="480cf-125">The options `EXECUTE AS OWNER`, `EXECUTE AS`*user*, and `EXECUTE AS SELF` are supported.</span></span>|  
|`BEGIN ATOMIC`|<span data-ttu-id="480cf-126">原生編譯的預存程序主體必須剛好由一個不可部分完成的區塊所組成。</span><span class="sxs-lookup"><span data-stu-id="480cf-126">The natively compiled stored procedure body must consist of exactly one atomic block.</span></span> <span data-ttu-id="480cf-127">不可部分完成的區塊保證會以不可部分完成的方式執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="480cf-127">Atomic blocks guarantee atomic execution of the stored procedure.</span></span> <span data-ttu-id="480cf-128">如果此程序在使用中交易的內容之外叫用，它將會開始新的交易，該交易會在不可部分完成的區塊結尾認可。</span><span class="sxs-lookup"><span data-stu-id="480cf-128">If the procedure is invoked outside the context of an active transaction, it will start a new transaction, which commits at the end of the atomic block.</span></span> <span data-ttu-id="480cf-129">原生編譯預存程序中不可部分完成的區塊有兩個必要選項：</span><span class="sxs-lookup"><span data-stu-id="480cf-129">Atomic blocks in natively compiled stored procedures have two required options:</span></span><br /><br /> <span data-ttu-id="480cf-130">`TRANSACTION ISOLATION LEVEL`.</span><span class="sxs-lookup"><span data-stu-id="480cf-130">`TRANSACTION ISOLATION LEVEL`.</span></span> <span data-ttu-id="480cf-131">如需支援的隔離等級，請參閱[交易隔離等級](../../database-engine/transaction-isolation-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="480cf-131">See [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md) for supported isolation levels.</span></span><br /><br /> <span data-ttu-id="480cf-132">`LANGUAGE`.</span><span class="sxs-lookup"><span data-stu-id="480cf-132">`LANGUAGE`.</span></span> <span data-ttu-id="480cf-133">預存程序的語言必須設定為其中一個可用語言或語言別名。</span><span class="sxs-lookup"><span data-stu-id="480cf-133">The language for the stored procedure must be set to one of the available languages or language aliases.</span></span>|  
  
 <span data-ttu-id="480cf-134">`EXECUTE AS` 和 Windows 登入可能會因為透過 `EXECUTE AS`執行模擬而發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="480cf-134">Regarding `EXECUTE AS` and Windows logins, an error can occur because of the impersonation done through `EXECUTE AS`.</span></span> <span data-ttu-id="480cf-135">如果使用者帳戶使用 Windows 驗證，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體所使用的服務帳戶與 Windows 登入的網域之間必須完全信任。</span><span class="sxs-lookup"><span data-stu-id="480cf-135">If a user account uses Windows Authentication, there must be full trust between the service account used for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance and the domain of the Windows login.</span></span> <span data-ttu-id="480cf-136">如果沒有完全信任，則在建立原生編譯的預存程式時，會傳回下列錯誤訊息： Msg 15404，無法取得有關 Windows NT 群組/使用者 ' username ' 的資訊，錯誤碼0x5。</span><span class="sxs-lookup"><span data-stu-id="480cf-136">If there is not full trust, the following error message is returned when creating a natively compiled stored procedure: Msg 15404, Could not obtain information about Windows NT group/user 'username', error code 0x5.</span></span>  
  
 <span data-ttu-id="480cf-137">如果要解決此錯誤，請使用下列動作之一：</span><span class="sxs-lookup"><span data-stu-id="480cf-137">To resolve this error, use one of the following:</span></span>  
  
-   <span data-ttu-id="480cf-138">使用與 Windows 使用者位於相同網域的帳戶來執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="480cf-138">Use an account from the same domain as the Windows user for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="480cf-139">如果 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用電腦帳戶 (例如「網路服務」或「本機系統」)，則包含 Windows 使用者的網域必須信任該電腦。</span><span class="sxs-lookup"><span data-stu-id="480cf-139">If [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is using a machine account such as Network Service or Local System, the machine must be trusted by the domain containing the Windows user.</span></span>  
  
-   <span data-ttu-id="480cf-140">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="480cf-140">Use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="480cf-141">建立原生編譯預存程序時，您可能也會看到錯誤 15517。</span><span class="sxs-lookup"><span data-stu-id="480cf-141">You may also see error 15517 when creating a natively compiled stored procedure.</span></span> <span data-ttu-id="480cf-142">如需詳細資訊，請參閱[MSSQLSERVER_15517](../errors-events/mssqlserver-15517-database-engine-error.md)。</span><span class="sxs-lookup"><span data-stu-id="480cf-142">For more information, see [MSSQLSERVER_15517](../errors-events/mssqlserver-15517-database-engine-error.md).</span></span>  
  
## <a name="updating-a-natively-compiled-stored-procedure"></a><span data-ttu-id="480cf-143">更新原生編譯預存程序</span><span class="sxs-lookup"><span data-stu-id="480cf-143">Updating a Natively Compiled Stored Procedure</span></span>  
 <span data-ttu-id="480cf-144">不支援對原生編譯的預存程序執行變更作業。</span><span class="sxs-lookup"><span data-stu-id="480cf-144">Performing alter operations on natively compiled stored procedures is not supported.</span></span> <span data-ttu-id="480cf-145">修改原生編譯預存程序的方法之一，是先卸除再重新建立預存程序︰</span><span class="sxs-lookup"><span data-stu-id="480cf-145">One way to modify a natively compiled stored procedure is to drop and recreate the stored procedure:</span></span>  
  
1.  <span data-ttu-id="480cf-146">在預存程序上產生權限的指令碼。</span><span class="sxs-lookup"><span data-stu-id="480cf-146">Generate script for the permissions on the stored procedure.</span></span>  
  
2.  <span data-ttu-id="480cf-147">選擇性地產生預存程序的指令碼並儲存為備份。</span><span class="sxs-lookup"><span data-stu-id="480cf-147">Optional, generate script for the stored procedure and save as a backup.</span></span>  
  
3.  <span data-ttu-id="480cf-148">卸除預存程序。</span><span class="sxs-lookup"><span data-stu-id="480cf-148">Drop the stored procedure.</span></span>  
  
4.  <span data-ttu-id="480cf-149">建立修改的預存程序。</span><span class="sxs-lookup"><span data-stu-id="480cf-149">Create the altered stored procedure.</span></span>  
  
5.  <span data-ttu-id="480cf-150">將指令碼撰寫的權限重新套用至預存程序。</span><span class="sxs-lookup"><span data-stu-id="480cf-150">Re-apply the scripted permissions to the stored procedure.</span></span>  
  
 <span data-ttu-id="480cf-151">此程序的缺點在於，應用程式將在步驟 3 開始到步驟 5 完成之間離線。</span><span class="sxs-lookup"><span data-stu-id="480cf-151">The disadvantage to this procedure is the application will be offline from the start of step 3 through the completion of step 5.</span></span> <span data-ttu-id="480cf-152">這段時間約為幾秒，且使用應用程式的用戶端可能會看見錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="480cf-152">This may take a few seconds and the client using the application may see error messages.</span></span>  
  
 <span data-ttu-id="480cf-153">(有效) 修改原生編譯預存程序的另一種方式是先建立新版的預存程序。</span><span class="sxs-lookup"><span data-stu-id="480cf-153">Another way to (effectively) modify a natively compiled stored procedure is to first create a new version of the stored procedure.</span></span> <span data-ttu-id="480cf-154">在這裡，原生編譯的預存程序擁有相關聯的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="480cf-154">Here, the natively compiled stored procedure has an associated version number.</span></span> <span data-ttu-id="480cf-155">我們會將舊版稱為 SP_Vold，新版稱為 SP_Vnew。</span><span class="sxs-lookup"><span data-stu-id="480cf-155">We will call the old version SP_Vold and the new version SP_Vnew.</span></span>  
  
1.  <span data-ttu-id="480cf-156">在 SP_Vold 上產生權限的指令碼。</span><span class="sxs-lookup"><span data-stu-id="480cf-156">Generate script for the permissions on SP_Vold.</span></span>  
  
2.  <span data-ttu-id="480cf-157">建立 SP_Vnew。</span><span class="sxs-lookup"><span data-stu-id="480cf-157">Create SP_Vnew.</span></span>  
  
3.  <span data-ttu-id="480cf-158">將 SP_Vold 的權限套用至 SP_Vnew。</span><span class="sxs-lookup"><span data-stu-id="480cf-158">Apply the permissions of SP_Vold to SP_Vnew.</span></span>  
  
4.  <span data-ttu-id="480cf-159">更新 SP_Vold 的參考以指向 SP_Vnew。</span><span class="sxs-lookup"><span data-stu-id="480cf-159">Update references to SP_Vold to point to SP_Vnew.</span></span> <span data-ttu-id="480cf-160">這項操作可透過不同的方式完成，例如：</span><span class="sxs-lookup"><span data-stu-id="480cf-160">This can be accomplished in different of ways, for example:</span></span>  
  
     <span data-ttu-id="480cf-161">使用包裝函式 (以磁碟為基礎) 預存程序，並將該程序修改為指向 SP_Vnew。</span><span class="sxs-lookup"><span data-stu-id="480cf-161">Use a wrapper (disk-based) stored procedure, and alter that procedure to point to SP_Vnew.</span></span> <span data-ttu-id="480cf-162">這個方法的缺點是間接造成的效能影響。</span><span class="sxs-lookup"><span data-stu-id="480cf-162">The disadvantage of this approach is the performance impact of the indirection.</span></span>  
  
    ```sql  
    ALTER PROCEDURE dbo.SP p1,...,pn  
    AS  
      EXEC dbo.SP_Vnew p1,...,pn  
    GO  
    ```  
  
5.  <span data-ttu-id="480cf-163">選擇性地卸除 SP_Vold。</span><span class="sxs-lookup"><span data-stu-id="480cf-163">Optional, drop SP_Vold.</span></span>  
  
 <span data-ttu-id="480cf-164">這個方法的優點是應用程式不會離線。</span><span class="sxs-lookup"><span data-stu-id="480cf-164">The advantage of this approach is that the application does not go offline.</span></span> <span data-ttu-id="480cf-165">不過，需要執行更多工作來維護參考，並確認參考一律指向最新版的預存程序。</span><span class="sxs-lookup"><span data-stu-id="480cf-165">However, more work is required to maintain the references and make sure they always point to the latest version of the stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="480cf-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="480cf-166">See Also</span></span>  
 [<span data-ttu-id="480cf-167">原生編譯的預存程序</span><span class="sxs-lookup"><span data-stu-id="480cf-167">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
