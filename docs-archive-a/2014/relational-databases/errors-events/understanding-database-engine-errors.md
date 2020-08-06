---
title: 了解資料庫引擎錯誤 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], about errors
- errors [SQL Server], Database Engine
- errors [SQL Server]
- Database Engine [SQL Server], errors
ms.assetid: ddaca9d3-956f-46a5-8cd3-a7a15ec75878
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aa8747066433488a8517d2931ad51f082075a66f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596693"
---
# <a name="understanding-database-engine-errors"></a><span data-ttu-id="231be-102">了解 Database Engine 錯誤</span><span class="sxs-lookup"><span data-stu-id="231be-102">Understanding Database Engine Errors</span></span>
  <span data-ttu-id="231be-103">下表描述 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 所引發錯誤的屬性。</span><span class="sxs-lookup"><span data-stu-id="231be-103">Errors raised by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] have the attributes described in the following table.</span></span>  
  
|<span data-ttu-id="231be-104">屬性</span><span class="sxs-lookup"><span data-stu-id="231be-104">Attribute</span></span>|<span data-ttu-id="231be-105">描述</span><span class="sxs-lookup"><span data-stu-id="231be-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="231be-106">錯誤號碼</span><span class="sxs-lookup"><span data-stu-id="231be-106">Error number</span></span>|<span data-ttu-id="231be-107">每一則錯誤訊息都有唯一的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="231be-107">Each error message has a unique error number.</span></span>|  
|<span data-ttu-id="231be-108">錯誤訊息字串</span><span class="sxs-lookup"><span data-stu-id="231be-108">Error message string</span></span>|<span data-ttu-id="231be-109">錯誤訊息包含錯誤原因的診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="231be-109">The error message contains diagnostic information about the cause of the error.</span></span> <span data-ttu-id="231be-110">許多錯誤訊息都有用來插入資訊 (例如產生錯誤的物件名稱) 的替代變數。</span><span class="sxs-lookup"><span data-stu-id="231be-110">Many error messages have substitution variables in which information, such as the name of the object generating the error, is inserted.</span></span>|  
|<span data-ttu-id="231be-111">Severity</span><span class="sxs-lookup"><span data-stu-id="231be-111">Severity</span></span>|<span data-ttu-id="231be-112">嚴重性指出錯誤的嚴重程度。</span><span class="sxs-lookup"><span data-stu-id="231be-112">The severity indicates how serious the error is.</span></span> <span data-ttu-id="231be-113">嚴重性低 (例如 1 或 2) 的錯誤是參考訊息或低階警告。</span><span class="sxs-lookup"><span data-stu-id="231be-113">Errors that have a low severity, such as 1 or 2, are information messages or low-level warnings.</span></span> <span data-ttu-id="231be-114">嚴重性高的錯誤指出應該儘快處理的問題。</span><span class="sxs-lookup"><span data-stu-id="231be-114">Errors that have a high severity indicate problems that should be addressed as soon as possible.</span></span> <span data-ttu-id="231be-115">如需有關嚴重性的詳細資訊，請參閱 [Database Engine 錯誤嚴重性](database-engine-error-severities.md)。</span><span class="sxs-lookup"><span data-stu-id="231be-115">For more information about severities, see [Database Engine Error Severities](database-engine-error-severities.md).</span></span>|  
|<span data-ttu-id="231be-116">State</span><span class="sxs-lookup"><span data-stu-id="231be-116">State</span></span>|<span data-ttu-id="231be-117">對於 [!INCLUDE[ssDE](../../includes/ssde-md.md)]，程式碼的多個點都可能會產生某些錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="231be-117">Some error messages can be raised at multiple points in the code for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="231be-118">例如，在許多不同情況下，都有可能產生 1105 錯誤。</span><span class="sxs-lookup"><span data-stu-id="231be-118">For example, an 1105 error can be raised for several different conditions.</span></span> <span data-ttu-id="231be-119">每個產生錯誤的特定狀況，都會指派唯一的狀態碼。</span><span class="sxs-lookup"><span data-stu-id="231be-119">Each specific condition that raises an error assigns a unique state code.</span></span><br /><br /> <span data-ttu-id="231be-120">檢視內含已知問題之資訊的資料庫時 (例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知識庫)，可以使用狀態碼來判斷所記錄的問題與您遇到的錯誤是否相同。</span><span class="sxs-lookup"><span data-stu-id="231be-120">When you are viewing databases that contain information about known issues, such as the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base, you can use the state number to determine whether the recorded issue is the same as the error you have encountered.</span></span> <span data-ttu-id="231be-121">例如，如果知識庫文件描述狀態為 2 的 1105 錯誤，而您收到之 1105 錯誤訊息的狀態為 3，則錯誤原因可能不是文件中所報告的原因。</span><span class="sxs-lookup"><span data-stu-id="231be-121">For example, if a Knowledge Base Article describes an 1105 error that has a state of 2 and the 1105 error message you received had a state of 3, the error probably has a different cause than the one reported in the article.</span></span><br /><br /> <span data-ttu-id="231be-122">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 支援工程師也可以使用錯誤中的狀態碼，來找出原始程式碼中引發錯誤碼的位置。</span><span class="sxs-lookup"><span data-stu-id="231be-122">A [!INCLUDE[msCoName](../../includes/msconame-md.md)] support engineer can also use the state code from an error to find the location in the source code where that error code is being raised.</span></span> <span data-ttu-id="231be-123">這項資訊可能會提供如何診斷問題的其他想法。</span><span class="sxs-lookup"><span data-stu-id="231be-123">This information might provide additional ideas on how to diagnose the problem.</span></span>|  
|<span data-ttu-id="231be-124">程序名稱</span><span class="sxs-lookup"><span data-stu-id="231be-124">Procedure name</span></span>|<span data-ttu-id="231be-125">這是發生錯誤之預存程序或觸發程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="231be-125">Is the name of the stored procedure or trigger in which the error has occurred.</span></span>|  
|<span data-ttu-id="231be-126">行號</span><span class="sxs-lookup"><span data-stu-id="231be-126">Line number</span></span>|<span data-ttu-id="231be-127">指出批次、預存程序、觸發程序或函數中的哪個陳述式產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="231be-127">Indicates which statement in a batch, stored procedure, trigger, or function generated the error.</span></span>|  
  
 <span data-ttu-id="231be-128">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體中的所有系統和使用者自訂的錯誤訊息都包含在 **sys.messages** 目錄檢視中。</span><span class="sxs-lookup"><span data-stu-id="231be-128">All system and user-defined error messages in an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] are contained in the **sys.messages** catalog view.</span></span> <span data-ttu-id="231be-129">您可以使用 RAISERROR 陳述式，將使用者自訂的錯誤傳回給應用程式。</span><span class="sxs-lookup"><span data-stu-id="231be-129">You can use the RAISERROR statement to return user-defined errors to an application.</span></span>  
  
 <span data-ttu-id="231be-130">所有資料庫 API，例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] **SQLClient** 命名空間、ActiveX Data Objects (ADO)、OLE DB 和開放式資料庫連線 (ODBC)，都會報告基本錯誤屬性。</span><span class="sxs-lookup"><span data-stu-id="231be-130">All database APIs, such as the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] **SQLClient** namespace, ActiveX Data Objects (ADO), OLE DB, and Open Database Connectivity (ODBC), report the basic error attributes.</span></span> <span data-ttu-id="231be-131">這項資訊包括錯誤號碼和訊息字串。</span><span class="sxs-lookup"><span data-stu-id="231be-131">This information includes the error number and message string.</span></span> <span data-ttu-id="231be-132">不過，並非所有 API 都會報告所有其他錯誤屬性。</span><span class="sxs-lookup"><span data-stu-id="231be-132">However, not all the APIs report all the other error attributes.</span></span>  
  
 <span data-ttu-id="231be-133">您可以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼中，使用相關聯之 CATCH 區塊範圍內的 ERROR_LINE、ERROR_MESSAGE、ERROR_NUMBER、ERROR_PROCEDURE、ERROR_SEVERITY 和 ERROR_STATE 等函數，來取得在 TRY…CATCH 建構的 TRY 區塊範圍內出現之錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="231be-133">Information about an error that occurs in the scope of the TRY block of a TRY...CATCH construct can be obtained in [!INCLUDE[tsql](../../includes/tsql-md.md)] code by using functions such as ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY, and ERROR_STATE in the scope of the associated CATCH block.</span></span> <span data-ttu-id="231be-134">如需詳細資訊，請參閱 [TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="231be-134">For more information, see [TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="231be-135">範例</span><span class="sxs-lookup"><span data-stu-id="231be-135">Examples</span></span>  
 <span data-ttu-id="231be-136">下列範例會查詢 `sys.messages` 目錄檢視，以傳回 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中具有英文文字 (`1033`) 之所有系統和使用者自訂錯誤訊息的清單。</span><span class="sxs-lookup"><span data-stu-id="231be-136">The following example queries the `sys.messages` catalog view to return a list of all system and user-defined error messages in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that have English text (`1033`).</span></span>  
  
```  
SELECT  
    message_id,  
    language_id,  
    severity,  
    is_event_logged,  
    text  
  FROM sys.messages  
  WHERE language_id = 1033;  
```  
  
 <span data-ttu-id="231be-137">如需詳細資訊，請參閱 [sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages)。</span><span class="sxs-lookup"><span data-stu-id="231be-137">For more information, see [sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="231be-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="231be-138">See Also</span></span>  
 <span data-ttu-id="231be-139">[sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) </span><span class="sxs-lookup"><span data-stu-id="231be-139">[sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) </span></span>  
 <span data-ttu-id="231be-140">[RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="231be-140">[RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql) </span></span>  
 <span data-ttu-id="231be-141">[@@ERROR &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="231be-141">[@@ERROR &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-transact-sql) </span></span>  
 <span data-ttu-id="231be-142">[TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="231be-142">[TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql) </span></span>  
 <span data-ttu-id="231be-143">[ERROR_LINE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-line-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="231be-143">[ERROR_LINE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-line-transact-sql) </span></span>  
 <span data-ttu-id="231be-144">[ERROR_MESSAGE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-message-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="231be-144">[ERROR_MESSAGE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-message-transact-sql) </span></span>  
 <span data-ttu-id="231be-145">[ERROR_NUMBER &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-number-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="231be-145">[ERROR_NUMBER &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-number-transact-sql) </span></span>  
 <span data-ttu-id="231be-146">[ERROR_PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="231be-146">[ERROR_PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-procedure-transact-sql) </span></span>  
 <span data-ttu-id="231be-147">[ERROR_SEVERITY &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-severity-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="231be-147">[ERROR_SEVERITY &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-severity-transact-sql) </span></span>  
 [<span data-ttu-id="231be-148">ERROR_STATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="231be-148">ERROR_STATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/error-state-transact-sql)  
  
  
