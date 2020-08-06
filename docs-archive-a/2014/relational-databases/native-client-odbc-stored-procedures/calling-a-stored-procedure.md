---
title: 呼叫預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- ODBC, stored procedures
- stored procedures [ODBC], calling
- SQL Server Native Client ODBC driver, stored procedures
- ODBC CALL escape sequence
- escape sequences [SQL Server]
- CALL statement
ms.assetid: d13737f4-f641-45bf-b56c-523e2ffc080f
author: rothja
ms.author: jroth
ms.openlocfilehash: c6fa704e45e4e85b479ae8a40a3e567bea1ec5e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709318"
---
# <a name="calling-a-stored-procedure"></a><span data-ttu-id="d7bea-102">呼叫預存程序</span><span class="sxs-lookup"><span data-stu-id="d7bea-102">Calling a Stored Procedure</span></span>
  <span data-ttu-id="d7bea-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式同時支援 ODBC 呼叫 escape 序列和 [!INCLUDE[tsql](../../includes/tsql-md.md)] [EXECUTE](/sql/t-sql/language-elements/execute-transact-sql)語句來執行預存程式; odbc 呼叫 escape 序列是慣用的方法。</span><span class="sxs-lookup"><span data-stu-id="d7bea-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports both the ODBC CALL escape sequence and the [!INCLUDE[tsql](../../includes/tsql-md.md)][EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) statement for executing stored procedures; the ODBC CALL escape sequence is the preferred method.</span></span> <span data-ttu-id="d7bea-104">使用 ODBC 語法可讓應用程式擷取預存程序的傳回碼，而且會最佳化 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式，使用最初開發的通訊協定，在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的電腦之間傳送遠端程序 (RPC) 呼叫。</span><span class="sxs-lookup"><span data-stu-id="d7bea-104">Using ODBC syntax enables an application to retrieve the return codes of stored procedures and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver is also optimized to use a protocol originally developed for sending remote procedure (RPC) calls between computers running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d7bea-105">此 RPC 通訊協定會排除在伺服器上完成的許多參數處理與陳述式剖析，藉以增加效能。</span><span class="sxs-lookup"><span data-stu-id="d7bea-105">This RPC protocol increases performance by eliminating much of the parameter processing and statement parsing done on the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7bea-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用具有 ODBC (的具名引數來呼叫預存程式時，如需詳細資訊，請參閱[依名稱 (具名引數) ](https://go.microsoft.com/fwlink/?LinkID=209721)) 系結參數。參數名稱必須以 ' \@ ' 字元開頭。</span><span class="sxs-lookup"><span data-stu-id="d7bea-106">When calling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures using named parameters with ODBC (for more information, see [Binding Parameters by Name (Named Parameters)](https://go.microsoft.com/fwlink/?LinkID=209721)), the parameter names must start with the '\@' character.</span></span> <span data-ttu-id="d7bea-107">這是一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特定的限制。</span><span class="sxs-lookup"><span data-stu-id="d7bea-107">This is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specific restriction.</span></span> <span data-ttu-id="d7bea-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會比 Microsoft Data Access Components (MDAC) 更嚴格地強制執行此限制。</span><span class="sxs-lookup"><span data-stu-id="d7bea-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver enforces this restriction more strictly than the Microsoft Data Access Components (MDAC).</span></span>  
  
 <span data-ttu-id="d7bea-109">用來呼叫程序的 ODBC CALL 逸出序列為：</span><span class="sxs-lookup"><span data-stu-id="d7bea-109">The ODBC CALL escape sequence for calling a procedure is:</span></span>  
  
 <span data-ttu-id="d7bea-110">{[**？ =**]**呼叫**_procedure_name_[ ( [*參數*] [**，**[*parameter*]] ... ) ]}</span><span class="sxs-lookup"><span data-stu-id="d7bea-110">{[**?=**]**call**_procedure_name_[([*parameter*][**,**[*parameter*]]...)]}</span></span>  
  
 <span data-ttu-id="d7bea-111">其中*procedure_name*會指定程式的名稱，而*參數*會指定程式參數。</span><span class="sxs-lookup"><span data-stu-id="d7bea-111">where *procedure_name* specifies the name of a procedure and *parameter* specifies a procedure parameter.</span></span> <span data-ttu-id="d7bea-112">只有使用 ODBC CALL 逸出序列的陳述式才會支援具名參數。</span><span class="sxs-lookup"><span data-stu-id="d7bea-112">Named parameters are only supported in statements using the ODBC CALL escape sequence.</span></span>  
  
 <span data-ttu-id="d7bea-113">程序可以有零或多個參數。</span><span class="sxs-lookup"><span data-stu-id="d7bea-113">A procedure can have zero or more parameters.</span></span> <span data-ttu-id="d7bea-114">它也可以傳回值 (如語法開頭的選用參數標記 ?= 所指示)。</span><span class="sxs-lookup"><span data-stu-id="d7bea-114">It can also return a value (as indicated by the optional parameter marker ?= at the start of the syntax).</span></span> <span data-ttu-id="d7bea-115">如果參數是輸入參數或輸入/輸出參數，則可以是常值或參數標記。</span><span class="sxs-lookup"><span data-stu-id="d7bea-115">If a parameter is an input or an input/output parameter, it can be a literal or a parameter marker.</span></span> <span data-ttu-id="d7bea-116">如果參數是輸出參數，它必須是參數標記，因為輸出不明。</span><span class="sxs-lookup"><span data-stu-id="d7bea-116">If the parameter is an output parameter, it must be a parameter marker because the output is unknown.</span></span> <span data-ttu-id="d7bea-117">參數標記必須與[SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)系結，才能執行程序呼叫語句。</span><span class="sxs-lookup"><span data-stu-id="d7bea-117">Parameter markers must be bound with [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) before the procedure call statement is executed.</span></span>  
  
 <span data-ttu-id="d7bea-118">輸入和輸入/輸出參數可以從程序呼叫省略。</span><span class="sxs-lookup"><span data-stu-id="d7bea-118">Input and input/output parameters can be omitted from procedure calls.</span></span> <span data-ttu-id="d7bea-119">如果呼叫包含括號但沒有任何參數的程序，驅動程式會引導資料來源使用第一個參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="d7bea-119">If a procedure is called with parentheses but without any parameters, the driver instructs the data source to use the default value for the first parameter.</span></span> <span data-ttu-id="d7bea-120">例如：</span><span class="sxs-lookup"><span data-stu-id="d7bea-120">For example:</span></span>  
  
 <span data-ttu-id="d7bea-121">{**call** _procedure_name_ \*\* ( ) \*\*}</span><span class="sxs-lookup"><span data-stu-id="d7bea-121">{**call** _procedure_name_**( )**}</span></span>  
  
 <span data-ttu-id="d7bea-122">如果程序沒有任何參數，該程序可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="d7bea-122">If the procedure does not have any parameters, the procedure can fail.</span></span> <span data-ttu-id="d7bea-123">如果呼叫沒有括號的程序，驅動程式不會傳送任何參數值。</span><span class="sxs-lookup"><span data-stu-id="d7bea-123">If a procedure is called without parentheses, the driver does not send any parameter values.</span></span> <span data-ttu-id="d7bea-124">例如：</span><span class="sxs-lookup"><span data-stu-id="d7bea-124">For example:</span></span>  
  
 <span data-ttu-id="d7bea-125">{**call** _procedure_name_}</span><span class="sxs-lookup"><span data-stu-id="d7bea-125">{**call** _procedure_name_}</span></span>  
  
 <span data-ttu-id="d7bea-126">在程序呼叫中可以針對輸入和輸入/輸出參數指定常值。</span><span class="sxs-lookup"><span data-stu-id="d7bea-126">Literals can be specified for input and input/output parameters in procedure calls.</span></span> <span data-ttu-id="d7bea-127">例如，程序 InsertOrder 有五個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="d7bea-127">For example, the procedure InsertOrder has five input parameters.</span></span> <span data-ttu-id="d7bea-128">以下對 InsertOrder 的呼叫會省略第一個參數、提供第二個參數的常值，然後將參數標記用於第三、第四和第五個參數</span><span class="sxs-lookup"><span data-stu-id="d7bea-128">The following call to InsertOrder omits the first parameter, provides a literal for the second parameter, and uses a parameter marker for the third, fourth, and fifth parameters.</span></span> <span data-ttu-id="d7bea-129">(參數會循序編號，從 1 這個值開始)。</span><span class="sxs-lookup"><span data-stu-id="d7bea-129">(Parameters are numbered sequentially, beginning with a value of 1.)</span></span>  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}  
```  
  
 <span data-ttu-id="d7bea-130">請注意，如果省略了某個參數，將它與其他參數分隔的逗號仍然必須出現。</span><span class="sxs-lookup"><span data-stu-id="d7bea-130">Note that if a parameter is omitted, the comma delimiting it from other parameters must still appear.</span></span> <span data-ttu-id="d7bea-131">如果省略了輸入或輸入/輸出參數，程序就會使用參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="d7bea-131">If an input or input/output parameter is omitted, the procedure uses the default value of the parameter.</span></span> <span data-ttu-id="d7bea-132">指定輸入或輸入/輸出參數預設值的其他方法是，將繫結至參數之長度/指標緩衝區的值設定成 SQL_DEFAULT_PARAM，或使用 DEFAULT 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d7bea-132">Other ways to specify the default value of an input or input/output parameter are to set the value of the length/indicator buffer bound to the parameter to SQL_DEFAULT_PARAM, or to use the DEFAULT keyword.</span></span>  
  
 <span data-ttu-id="d7bea-133">如果省略了輸入/輸出參數，或者如果有提供參數的常值，驅動程式就會捨棄輸出值。</span><span class="sxs-lookup"><span data-stu-id="d7bea-133">If an input/output parameter is omitted, or if a literal is supplied for the parameter, the driver discards the output value.</span></span> <span data-ttu-id="d7bea-134">同樣地，如果省略了程序傳回值的參數標記，驅動程式就會捨棄傳回值。</span><span class="sxs-lookup"><span data-stu-id="d7bea-134">Similarly, if the parameter marker for the return value of a procedure is omitted, the driver discards the return value.</span></span> <span data-ttu-id="d7bea-135">最後，如果應用程式指定的程序傳回值參數不會傳回值，驅動程式會將繫結至參數之長度/指標緩衝區的值設定為 SQL_NULL_DATA。</span><span class="sxs-lookup"><span data-stu-id="d7bea-135">Finally, if an application specifies a return value parameter for a procedure that does not return a value, the driver sets the value of the length/indicator buffer bound to the parameter to SQL_NULL_DATA.</span></span>  
  
## <a name="delimiters-in-call-statements"></a><span data-ttu-id="d7bea-136">CALL 陳述式中的分隔符號</span><span class="sxs-lookup"><span data-stu-id="d7bea-136">Delimiters in CALL Statements</span></span>  
 <span data-ttu-id="d7bea-137">依預設，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式也支援 ODBC { CALL } 逸出序列專屬的相容性選項。</span><span class="sxs-lookup"><span data-stu-id="d7bea-137">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver by default also supports a compatibility option specific to the ODBC { CALL } escape sequence.</span></span> <span data-ttu-id="d7bea-138">驅動程式會接受 CALL 陳述式以及只有單一一組分隔完整預存程序名稱的雙引號：</span><span class="sxs-lookup"><span data-stu-id="d7bea-138">The driver accepts CALL statements with only a single set of double quotation marks delimiting the entire stored procedure name:</span></span>  
  
```  
{ CALL "master.dbo.sp_who" }  
```  
  
 <span data-ttu-id="d7bea-139">依預設，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式也接受遵循 ISO 規則，並將每個分隔符號括在雙引號中的 CALL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="d7bea-139">By default the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver also accepts CALL statements that follow the ISO rules and enclose each identifier in double quotation marks:</span></span>  
  
```  
{ CALL "master"."dbo"."sp_who" }  
```  
  
 <span data-ttu-id="d7bea-140">不過，利用預設值執行時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式不支援使用引號識別碼的形式與包含 ISO 標準未指定為合法識別碼之字元的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d7bea-140">When running with the default settings, however, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support using either form of quoted identifier with identifiers that contain characters not specified as legal in identifiers by the ISO standard.</span></span> <span data-ttu-id="d7bea-141">例如，驅動程式無法使用引號識別碼的 CALL 語句來存取名為 **"My. Proc"** 的預存程式：</span><span class="sxs-lookup"><span data-stu-id="d7bea-141">For example, the driver cannot access a stored procedure named **"My.Proc"** using a CALL statement with quoted identifiers:</span></span>  
  
```  
{ CALL "MyDB"."MyOwner"."My.Proc" }  
```  
  
 <span data-ttu-id="d7bea-142">這個陳述式會由驅動程式解譯為：</span><span class="sxs-lookup"><span data-stu-id="d7bea-142">This statement is interpreted by the driver as:</span></span>  
  
```  
{ CALL MyDB.MyOwner.My.Proc }  
```  
  
 <span data-ttu-id="d7bea-143">伺服器會引發錯誤，指出名為**MyDB**的連結伺服器不存在。</span><span class="sxs-lookup"><span data-stu-id="d7bea-143">The server raises an error that a linked server named **MyDB** does not exist.</span></span>  
  
 <span data-ttu-id="d7bea-144">此問題在使用有括號的識別碼時不存在，因為此陳述式會正確解譯：</span><span class="sxs-lookup"><span data-stu-id="d7bea-144">The issue does not exist when using bracketed identifiers, this statement is interpreted correctly:</span></span>  
  
```  
{ CALL [MyDB].[MyOwner].[My.Table] }  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7bea-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7bea-145">See Also</span></span>  
 [<span data-ttu-id="d7bea-146">執行預存程序</span><span class="sxs-lookup"><span data-stu-id="d7bea-146">Running Stored Procedures</span></span>](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
