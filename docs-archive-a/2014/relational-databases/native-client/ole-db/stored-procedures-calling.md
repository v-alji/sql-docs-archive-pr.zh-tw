---
title: 呼叫預存程序 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- RPC escape sequence
- OLE DB, stored procedures
- parameters [SQL Server Native Client], OLE DB
- ODBC CALL escape sequence
- stored procedures [OLE DB], calling
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: 8e5738e5-4bbe-4f34-bd69-0c0633290bdd
author: rothja
ms.author: jroth
ms.openlocfilehash: 695848c8633d310f5e8ee21e9e738749d1550e4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706373"
---
# <a name="calling-a-stored-procedure-ole-db"></a><span data-ttu-id="33ad5-102">呼叫預存程序 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="33ad5-102">Calling a Stored Procedure (OLE DB)</span></span>
  <span data-ttu-id="33ad5-103">預存程序可以有零或多個參數。</span><span class="sxs-lookup"><span data-stu-id="33ad5-103">A stored procedure can have zero or more parameters.</span></span> <span data-ttu-id="33ad5-104">它也可以傳回值。</span><span class="sxs-lookup"><span data-stu-id="33ad5-104">It can also return a value.</span></span> <span data-ttu-id="33ad5-105">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者時，可以藉由下列方式傳遞預存程式的參數：</span><span class="sxs-lookup"><span data-stu-id="33ad5-105">When using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, parameters to a stored procedure can be passed by:</span></span>  
  
-   <span data-ttu-id="33ad5-106">將資料值寫入程式碼。</span><span class="sxs-lookup"><span data-stu-id="33ad5-106">Hard-coding the data value.</span></span>  
  
-   <span data-ttu-id="33ad5-107">使用參數標記 (?) 來指定參數、將程式變數繫結至參數標記，然後將資料值放在程式變數中。</span><span class="sxs-lookup"><span data-stu-id="33ad5-107">Using a parameter marker (?) to specify parameters, bind a program variable to the parameter marker, and then place the data value in the program variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33ad5-108">搭配 OLE DB 使用具名參數呼叫 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預存程序時，參數名稱開頭必須是 '\@' 字元。</span><span class="sxs-lookup"><span data-stu-id="33ad5-108">When calling [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stored procedures using named parameters with OLE DB, the parameter names must start with the '\@' character.</span></span> <span data-ttu-id="33ad5-109">這是一個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 特定的限制。</span><span class="sxs-lookup"><span data-stu-id="33ad5-109">This is a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specific restriction.</span></span> <span data-ttu-id="33ad5-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會比 MDAC 更嚴格地強制執行此限制。</span><span class="sxs-lookup"><span data-stu-id="33ad5-110">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider enforces this restriction more strictly than MDAC.</span></span>  
  
 <span data-ttu-id="33ad5-111">為支援參數，會在命令物件上公開 **ICommandWithParameters** 介面。</span><span class="sxs-lookup"><span data-stu-id="33ad5-111">To support parameters, the **ICommandWithParameters** interface is exposed on the command object.</span></span> <span data-ttu-id="33ad5-112">為使用參數，取用者會先呼叫 **ICommandWithParameters::SetParameterInfo** 方法 (或選擇性地準備呼叫 **GetParameterInfo** 方法的呼叫陳述式) 來描述提供者的參數。</span><span class="sxs-lookup"><span data-stu-id="33ad5-112">To use parameters, the consumer first describes the parameters to the provider by calling the **ICommandWithParameters::SetParameterInfo** method (or optionally prepares a calling statement that calls the **GetParameterInfo** method).</span></span> <span data-ttu-id="33ad5-113">接著，取用者會建立指定緩衝區結構的存取子，並將參數值放在此緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="33ad5-113">The consumer then creates an accessor that specifies the structure of a buffer and places parameter values in this buffer.</span></span> <span data-ttu-id="33ad5-114">最後，它會將存取子的控制代碼與緩衝區的指標傳遞到 **Execute** 的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="33ad5-114">Finally, it passes the handle of the accessor and a pointer to the buffer to **Execute**.</span></span> <span data-ttu-id="33ad5-115">稍後呼叫 **Execute** 時，取用者會將新的參數值放在緩衝區中，並利用存取子控制代碼和緩衝區指標呼叫 **Execute**。</span><span class="sxs-lookup"><span data-stu-id="33ad5-115">On later calls to **Execute**, the consumer places new parameter values in the buffer and calls **Execute** with the accessor handle and buffer pointer.</span></span>  
  
 <span data-ttu-id="33ad5-116">使用參數呼叫暫存預存程序的命令必須先呼叫 **ICommandWithParameters::SetParameterInfo** 來定義參數資訊，然後就可以成功準備命令。</span><span class="sxs-lookup"><span data-stu-id="33ad5-116">A command that calls a temporary stored procedure using parameters must first call **ICommandWithParameters::SetParameterInfo** to define the parameter information, before the command can be successfully prepared.</span></span> <span data-ttu-id="33ad5-117">這是因為暫存預存程序的內部名稱與用戶端所使用的外部名稱不同，而且 SQLOLEDB 無法查詢系統資料表來判斷暫存預存程序的參數資訊。</span><span class="sxs-lookup"><span data-stu-id="33ad5-117">This is because the internal name for a temporary stored procedure differs from the external name used by a client and SQLOLEDB cannot query the system tables to determine the parameter information for a temporary stored procedure.</span></span>  
  
 <span data-ttu-id="33ad5-118">以下是參數繫結程序中的步驟：</span><span class="sxs-lookup"><span data-stu-id="33ad5-118">These are the steps in the parameter binding process:</span></span>  
  
1.  <span data-ttu-id="33ad5-119">在 DBPARAMBINDINFO 結構的陣列中填入參數資訊；也就是參數名稱、參數資料類型的提供者專屬名稱，或標準資料類型名稱等等。</span><span class="sxs-lookup"><span data-stu-id="33ad5-119">Fill in the parameter information in an array of DBPARAMBINDINFO structures; that is, parameter name, provider-specific name for the data type of the parameter or a standard data type name, and so on.</span></span> <span data-ttu-id="33ad5-120">陣列中的每個結構會描述一個參數。</span><span class="sxs-lookup"><span data-stu-id="33ad5-120">Each structure in the array describes one parameter.</span></span> <span data-ttu-id="33ad5-121">接著，就會將此陣列傳遞到 **SetParameterInfo** 方法。</span><span class="sxs-lookup"><span data-stu-id="33ad5-121">This array is then passed to the **SetParameterInfo** method.</span></span>  
  
2.  <span data-ttu-id="33ad5-122">呼叫 **ICommandWithParameters::SetParameterInfo** 方法來描述提供者的參數。</span><span class="sxs-lookup"><span data-stu-id="33ad5-122">Call the **ICommandWithParameters::SetParameterInfo** method to describe parameters to the provider.</span></span> <span data-ttu-id="33ad5-123">**SetParameterInfo** 會指定每個參數的原生資料類型。</span><span class="sxs-lookup"><span data-stu-id="33ad5-123">**SetParameterInfo** specifies the native data type of each parameter.</span></span> <span data-ttu-id="33ad5-124">**SetParameterInfo** 引數為：</span><span class="sxs-lookup"><span data-stu-id="33ad5-124">**SetParameterInfo** arguments are:</span></span>  
  
    -   <span data-ttu-id="33ad5-125">用於設定類型資訊之參數的數目。</span><span class="sxs-lookup"><span data-stu-id="33ad5-125">The number of parameters for which to set type information.</span></span>  
  
    -   <span data-ttu-id="33ad5-126">用於設定類型資訊之參數序數的陣列。</span><span class="sxs-lookup"><span data-stu-id="33ad5-126">An array of parameter ordinals for which to set type information.</span></span>  
  
    -   <span data-ttu-id="33ad5-127">DBPARAMBINDINFO 結構的陣列。</span><span class="sxs-lookup"><span data-stu-id="33ad5-127">An array of DBPARAMBINDINFO structures.</span></span>  
  
3.  <span data-ttu-id="33ad5-128">使用 **IAccessor::CreateAccessor** 命令建立參數存取子。</span><span class="sxs-lookup"><span data-stu-id="33ad5-128">Create a parameter accessor by using the **IAccessor::CreateAccessor** command.</span></span> <span data-ttu-id="33ad5-129">存取子會指定緩衝區的結構，並將參數值放在緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="33ad5-129">The accessor specifies the structure of a buffer and places parameter values in the buffer.</span></span> <span data-ttu-id="33ad5-130">**CreateAccessor** 命令會從一組繫結建立存取子。</span><span class="sxs-lookup"><span data-stu-id="33ad5-130">The **CreateAccessor** command creates an accessor from a set of bindings.</span></span> <span data-ttu-id="33ad5-131">這些繫結可由取用者使用 DBBINDING 結構的陣列描述。</span><span class="sxs-lookup"><span data-stu-id="33ad5-131">These bindings are described by the consumer by using an array of DBBINDING structures.</span></span> <span data-ttu-id="33ad5-132">每個繫結都會與取用者緩衝區的單一參數產生關聯，而且會包含資訊，例如：</span><span class="sxs-lookup"><span data-stu-id="33ad5-132">Each binding associates a single parameter to the buffer of the consumer and contains information such as:</span></span>  
  
    -   <span data-ttu-id="33ad5-133">套用繫結之參數的序數。</span><span class="sxs-lookup"><span data-stu-id="33ad5-133">The ordinal of the parameter to which the binding applies.</span></span>  
  
    -   <span data-ttu-id="33ad5-134">繫結的項目 (資料值、其長度及其狀態)。</span><span class="sxs-lookup"><span data-stu-id="33ad5-134">What is bound (the data value, its length, and its status).</span></span>  
  
    -   <span data-ttu-id="33ad5-135">緩衝區中對每一個部分的位移。</span><span class="sxs-lookup"><span data-stu-id="33ad5-135">The offset in the buffer to each of these parts.</span></span>  
  
    -   <span data-ttu-id="33ad5-136">存在於取用者緩衝區內之資料值的長度和類型。</span><span class="sxs-lookup"><span data-stu-id="33ad5-136">The length and type of the data value as it exists in the buffer of the consumer.</span></span>  
  
     <span data-ttu-id="33ad5-137">存取子是由其類型為 HACCESSOR 的控制代碼識別。</span><span class="sxs-lookup"><span data-stu-id="33ad5-137">An accessor is identified by its handle, which is of type HACCESSOR.</span></span> <span data-ttu-id="33ad5-138">此控制代碼會由 **CreateAccessor** 方法傳回。</span><span class="sxs-lookup"><span data-stu-id="33ad5-138">This handle is returned by the **CreateAccessor** method.</span></span> <span data-ttu-id="33ad5-139">每當取用者完成使用存取子時，取用者必須呼叫 **ReleaseAccessor** 方法來釋放所保留的記憶體。</span><span class="sxs-lookup"><span data-stu-id="33ad5-139">Whenever the consumer finishes using an accessor, the consumer must call the **ReleaseAccessor** method to release the memory it holds.</span></span>  
  
     <span data-ttu-id="33ad5-140">當取用者呼叫 **ICommand::Execute** 之類的方法時，它會將控制代碼傳遞到存取子以及緩衝區本身的指標。</span><span class="sxs-lookup"><span data-stu-id="33ad5-140">When the consumer calls a method, such as **ICommand::Execute**, it passes the handle to an accessor and a pointer to a buffer itself.</span></span> <span data-ttu-id="33ad5-141">提供者會使用此存取子決定如何傳送包含在緩衝區中的資料。</span><span class="sxs-lookup"><span data-stu-id="33ad5-141">The provider uses this accessor to determine how to transfer the data contained in the buffer.</span></span>  
  
4.  <span data-ttu-id="33ad5-142">填入 DBPARAMS 結構。</span><span class="sxs-lookup"><span data-stu-id="33ad5-142">Fill in the DBPARAMS structure.</span></span> <span data-ttu-id="33ad5-143">從中取用輸入參數值的取用者變數以及寫入輸出參數的取用者變數在執行階段都會傳遞到 DBPARAMS 結構的 **ICommand::Execute** 中。</span><span class="sxs-lookup"><span data-stu-id="33ad5-143">The consumer variables from which input parameter values are taken and to which output parameter values are written are passed at run time to **ICommand::Execute** in the DBPARAMS structure.</span></span> <span data-ttu-id="33ad5-144">DBPARAMS 結構包含三個元素：</span><span class="sxs-lookup"><span data-stu-id="33ad5-144">The DBPARAMS structure includes three elements:</span></span>  
  
    -   <span data-ttu-id="33ad5-145">根據存取子控制代碼指定的繫結，提供者從其中擷取輸入參數資料的緩衝區指標以及提供者傳回輸出參數資料的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="33ad5-145">A pointer to the buffer from which the provider retrieves input parameter data and to which the provider returns output parameter data, according to the bindings specified by the accessor handle.</span></span>  
  
    -   <span data-ttu-id="33ad5-146">緩衝區中的參數集數目。</span><span class="sxs-lookup"><span data-stu-id="33ad5-146">The number of sets of parameters in the buffer.</span></span>  
  
    -   <span data-ttu-id="33ad5-147">存取子控制代碼會在步驟 3 中建立。</span><span class="sxs-lookup"><span data-stu-id="33ad5-147">The accessor handle created in Step 3.</span></span>  
  
5.  <span data-ttu-id="33ad5-148">使用 **ICommand::Execute** 執行命令。</span><span class="sxs-lookup"><span data-stu-id="33ad5-148">Execute the command by using **ICommand::Execute**.</span></span>  
  
## <a name="methods-of-calling-a-stored-procedure"></a><span data-ttu-id="33ad5-149">呼叫預存程序的方法</span><span class="sxs-lookup"><span data-stu-id="33ad5-149">Methods of Calling a Stored Procedure</span></span>  
 <span data-ttu-id="33ad5-150">在中執行預存程式時 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者支援：</span><span class="sxs-lookup"><span data-stu-id="33ad5-150">When executing a stored procedure in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the:</span></span>  
  
-   <span data-ttu-id="33ad5-151">ODBC CALL 逸出序列。</span><span class="sxs-lookup"><span data-stu-id="33ad5-151">ODBC CALL escape sequence.</span></span>  
  
-   <span data-ttu-id="33ad5-152">遠端程序呼叫 (RPC) 逸出序列。</span><span class="sxs-lookup"><span data-stu-id="33ad5-152">Remote procedure call (RPC) escape sequence.</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="33ad5-153">EXECUTE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="33ad5-153">EXECUTE statement.</span></span>  
  
### <a name="odbc-call-escape-sequence"></a><span data-ttu-id="33ad5-154">ODBC CALL 逸出序列</span><span class="sxs-lookup"><span data-stu-id="33ad5-154">ODBC CALL Escape Sequence</span></span>  
 <span data-ttu-id="33ad5-155">如果您知道參數資訊，請呼叫 **ICommandWithParameters::SetParameterInfo** 方法來描述提供者的參數。</span><span class="sxs-lookup"><span data-stu-id="33ad5-155">If you know parameter information, call **ICommandWithParameters::SetParameterInfo** method to describe the parameters to the provider.</span></span> <span data-ttu-id="33ad5-156">否則，在呼叫預存程序中使用 ODBC CALL 語法時，提供者會呼叫 Helper 函數來尋找預存程序參數資訊。</span><span class="sxs-lookup"><span data-stu-id="33ad5-156">Otherwise, when the ODBC CALL syntax is used in calling a stored procedure, the provider calls a helper function to find the stored procedure parameter information.</span></span>  
  
 <span data-ttu-id="33ad5-157">如果您不確定參數資訊 (參數中繼資料)，建議使用 ODBC CALL 語法。</span><span class="sxs-lookup"><span data-stu-id="33ad5-157">If you are not sure about the parameter information (parameter metadata), ODBC CALL syntax is recommended.</span></span>  
  
 <span data-ttu-id="33ad5-158">使用 ODBC CALL 逸出序列呼叫程序的一般語法為：</span><span class="sxs-lookup"><span data-stu-id="33ad5-158">The general syntax for calling a procedure by using the ODBC CALL escape sequence is:</span></span>  
  
 <span data-ttu-id="33ad5-159">{[**？ =**]**呼叫**_procedure_name_[\*\* (**[*參數*] [**，**[*parameter*]] .。。**) \*\*]}</span><span class="sxs-lookup"><span data-stu-id="33ad5-159">{[**?=**]**call**_procedure_name_[**(**[*parameter*][**,**[*parameter*]]...**)**]}</span></span>  
  
 <span data-ttu-id="33ad5-160">例如：</span><span class="sxs-lookup"><span data-stu-id="33ad5-160">For example:</span></span>  
  
```  
{call SalesByCategory('Produce', '1995')}  
```  
  
### <a name="rpc-escape-sequence"></a><span data-ttu-id="33ad5-161">RPC 逸出序列</span><span class="sxs-lookup"><span data-stu-id="33ad5-161">RPC Escape Sequence</span></span>  
 <span data-ttu-id="33ad5-162">RPC 逸出序列類似於呼叫預存程序的 ODBC CALL 語法。</span><span class="sxs-lookup"><span data-stu-id="33ad5-162">The RPC escape sequence is similar to the ODBC CALL syntax of calling a stored procedure.</span></span> <span data-ttu-id="33ad5-163">如果您要呼叫程序數次，RPC 逸出序列會在呼叫預存程序的三種方法之間，提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="33ad5-163">If you will call the procedure multiple times, the RPC escape sequence provides most optimal performance among the three methods of calling a stored procedure.</span></span>  
  
 <span data-ttu-id="33ad5-164">當 RPC 逸出序列用於執行預存程序時，提供者不會呼叫任何 Helper 函數來判斷參數資訊 (如果是 ODBC CALL 語法，則會這麼做)。</span><span class="sxs-lookup"><span data-stu-id="33ad5-164">When the RPC escape sequence is used to execute a stored procedure, the provider does not call any helper function to determine the parameter information (as it does in the case of ODBC CALL syntax).</span></span> <span data-ttu-id="33ad5-165">RPC 語法比 ODBC CALL 語法簡單，因此命令集的剖析速度較快，可以增進效能。</span><span class="sxs-lookup"><span data-stu-id="33ad5-165">The RPC syntax is simpler than the ODBC CALL syntax, so the command is parsed faster, improving performance.</span></span> <span data-ttu-id="33ad5-166">在此情況下，您需要執行 **ICommandWithParameters::SetParameterInfo** 來提供參數資訊。</span><span class="sxs-lookup"><span data-stu-id="33ad5-166">In this case, you need to provide the parameter information by executing **ICommandWithParameters::SetParameterInfo**.</span></span>  
  
 <span data-ttu-id="33ad5-167">RPC 逸出序列要求您擁有傳回值。</span><span class="sxs-lookup"><span data-stu-id="33ad5-167">The RPC escape sequence requires you to have a return value.</span></span> <span data-ttu-id="33ad5-168">如果預存程序沒有傳回值，伺服器預設會傳回 0。</span><span class="sxs-lookup"><span data-stu-id="33ad5-168">If the stored procedure does not return a value, the server returns a 0 by default.</span></span> <span data-ttu-id="33ad5-169">此外，您無法在預存程序上開啟 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料指標。</span><span class="sxs-lookup"><span data-stu-id="33ad5-169">In addition, you cannot open a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cursor on the stored procedure.</span></span> <span data-ttu-id="33ad5-170">預存程序會以隱含的方式準備，而 **ICommandPrepare::Prepare** 的呼叫將會失敗。</span><span class="sxs-lookup"><span data-stu-id="33ad5-170">The stored procedure is prepared implicitly and the call to **ICommandPrepare::Prepare** will fail.</span></span> <span data-ttu-id="33ad5-171">由於無法準備 RPC 呼叫，因此，您無法查詢資料行中繼資料；IColumnsInfo::GetColumnInfo 和 IColumnsRowset::GetColumnsRowset 將會傳回 DB_E_NOTPREPARED。</span><span class="sxs-lookup"><span data-stu-id="33ad5-171">Because of the inability to prepare an RPC call, you can not query column metadata; IColumnsInfo::GetColumnInfo and IColumnsRowset::GetColumnsRowset will return DB_E_NOTPREPARED.</span></span>  
  
 <span data-ttu-id="33ad5-172">如果您知道所有參數中繼資料，RPC 逸出序列是執行預存程序的建議方式。</span><span class="sxs-lookup"><span data-stu-id="33ad5-172">If you know all the parameter metadata, RPC escape sequence is the recommended way to execute stored procedures.</span></span>  
  
 <span data-ttu-id="33ad5-173">這是呼叫預存程序之 RPC 逸出序列的範例：</span><span class="sxs-lookup"><span data-stu-id="33ad5-173">This is an example of RPC escape sequence for calling a stored procedure:</span></span>  
  
```  
{rpc SalesByCategory}  
```  
  
 <span data-ttu-id="33ad5-174">如需示範 RPC 逸出序列的範例應用程式，請參閱[執行預存程序 &#40;使用 RPC 語法&#41; 與處理傳回碼和輸出參數 &#40;OLE DB&#41;](../../native-client-ole-db-how-to/results/execute-stored-procedure-with-rpc-and-process-output.md)。</span><span class="sxs-lookup"><span data-stu-id="33ad5-174">For a sample application that demonstrates an RPC escape sequence, see [Execute a Stored Procedure &#40;Using RPC Syntax&#41; and Process Return Codes and Output Parameters &#40;OLE DB&#41;](../../native-client-ole-db-how-to/results/execute-stored-procedure-with-rpc-and-process-output.md).</span></span>  
  
### <a name="transact-sql-execute-statement"></a><span data-ttu-id="33ad5-175">Transact-SQL EXECUTE 陳述式</span><span class="sxs-lookup"><span data-stu-id="33ad5-175">Transact-SQL EXECUTE Statement</span></span>  
 <span data-ttu-id="33ad5-176">ODBC CALL 逸出序列和 RPC 逸出序列都是呼叫預存程序而非 [EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) 陳述式的慣用方法。</span><span class="sxs-lookup"><span data-stu-id="33ad5-176">The ODBC CALL escape sequence and the RPC escape sequence are the preferred methods for calling a stored procedure rather than the [EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) statement.</span></span> <span data-ttu-id="33ad5-177">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會使用的 RPC 機制 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 來優化命令處理。</span><span class="sxs-lookup"><span data-stu-id="33ad5-177">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses the RPC mechanism of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to optimize command processing.</span></span> <span data-ttu-id="33ad5-178">此 RPC 通訊協定會排除在伺服器上完成的許多參數處理與陳述式剖析，藉以增加效能。</span><span class="sxs-lookup"><span data-stu-id="33ad5-178">This RPC protocol increases performance by eliminating much of the parameter processing and statement parsing done on the server.</span></span>  
  
 <span data-ttu-id="33ad5-179">這是 [!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE** 陳述式的範例：</span><span class="sxs-lookup"><span data-stu-id="33ad5-179">This is an example of the [!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE** statement:</span></span>  
  
```  
EXECUTE SalesByCategory 'Produce', '1995'  
```  
  
## <a name="see-also"></a><span data-ttu-id="33ad5-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33ad5-180">See Also</span></span>  
 [<span data-ttu-id="33ad5-181">預存程式</span><span class="sxs-lookup"><span data-stu-id="33ad5-181">Stored Procedures</span></span>](stored-procedures.md)  
  
  
