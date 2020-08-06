---
title: SQLGetStmtAttr |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetStmtAttr function
ms.assetid: e64f4f94-eb73-4477-9745-080b6cbdc751
author: rothja
ms.author: jroth
ms.openlocfilehash: f1f9b6a0c0668540b566c9b3d7ede781c97a1dbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596677"
---
# <a name="sqlgetstmtattr"></a><span data-ttu-id="84a19-102">SQLGetStmtAttr</span><span class="sxs-lookup"><span data-stu-id="84a19-102">SQLGetStmtAttr</span></span>
  <span data-ttu-id="84a19-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會擴充 SQLGetStmtAttr，以公開驅動程式特定的語句屬性。</span><span class="sxs-lookup"><span data-stu-id="84a19-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver extends SQLGetStmtAttr to expose driver-specific statement attributes.</span></span>  
  
 <span data-ttu-id="84a19-104">[SQLSetStmtAttr](sqlsetstmtattr.md)會列出同時為讀取和寫入的語句屬性。</span><span class="sxs-lookup"><span data-stu-id="84a19-104">[SQLSetStmtAttr](sqlsetstmtattr.md) lists statement attributes that are both read and write.</span></span> <span data-ttu-id="84a19-105">本主題將列出唯讀的陳述式屬性。</span><span class="sxs-lookup"><span data-stu-id="84a19-105">This topic lists the read only statement attributes.</span></span>  
  
## <a name="sql_sopt_ss_current_command"></a><span data-ttu-id="84a19-106">SQL_SOPT_SS_CURRENT_COMMAND</span><span class="sxs-lookup"><span data-stu-id="84a19-106">SQL_SOPT_SS_CURRENT_COMMAND</span></span>  
 <span data-ttu-id="84a19-107">SQL_SOPT_SS_CURRENT_COMMAND 屬性會公開命令批次的目前命令。</span><span class="sxs-lookup"><span data-stu-id="84a19-107">The SQL_SOPT_SS_CURRENT_COMMAND attribute exposes the current command of a command batch.</span></span> <span data-ttu-id="84a19-108">傳回值是一個整數，可指定此命令在批次中的位置。</span><span class="sxs-lookup"><span data-stu-id="84a19-108">The return is an integer that specifies the location of the command in the batch.</span></span> <span data-ttu-id="84a19-109">*Valueptr 是*值的類型是 SQLLEN。</span><span class="sxs-lookup"><span data-stu-id="84a19-109">The *ValuePtr* value is of type SQLLEN.</span></span>  
  
## <a name="sql_sopt_ss_nocount_status"></a><span data-ttu-id="84a19-110">SQL_SOPT_SS_NOCOUNT_STATUS</span><span class="sxs-lookup"><span data-stu-id="84a19-110">SQL_SOPT_SS_NOCOUNT_STATUS</span></span>  
 <span data-ttu-id="84a19-111">SQL_SOPT_SS_NOCOUNT_STATUS 屬性工作表示 NOCOUNT 選項的目前設定，其控制是否在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 呼叫[SQLRowCount](sqlrowcount.md)時，報告語句所影響的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="84a19-111">The SQL_SOPT_SS_NOCOUNT_STATUS attribute indicates the current setting of the NOCOUNT option, which controls whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reports the numbers of rows affected by a statement when [SQLRowCount](sqlrowcount.md) is called.</span></span> <span data-ttu-id="84a19-112">*Valueptr 是*值的類型是 SQLLEN。</span><span class="sxs-lookup"><span data-stu-id="84a19-112">The *ValuePtr* value is of type SQLLEN.</span></span>  
  
|<span data-ttu-id="84a19-113">值</span><span class="sxs-lookup"><span data-stu-id="84a19-113">Value</span></span>|<span data-ttu-id="84a19-114">描述</span><span class="sxs-lookup"><span data-stu-id="84a19-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84a19-115">SQL_NC_OFF</span><span class="sxs-lookup"><span data-stu-id="84a19-115">SQL_NC_OFF</span></span>|<span data-ttu-id="84a19-116">NOCOUNT 為 OFF。</span><span class="sxs-lookup"><span data-stu-id="84a19-116">NOCOUNT is OFF.</span></span> <span data-ttu-id="84a19-117">SQLRowCount 會傳回受影響的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="84a19-117">SQLRowCount returns number of rows affected.</span></span>|  
|<span data-ttu-id="84a19-118">SQL_NC_ON</span><span class="sxs-lookup"><span data-stu-id="84a19-118">SQL_NC_ON</span></span>|<span data-ttu-id="84a19-119">NOCOUNT 為 ON。</span><span class="sxs-lookup"><span data-stu-id="84a19-119">NOCOUNT is ON.</span></span> <span data-ttu-id="84a19-120">SQLRowCount 不會傳回受影響的資料列數目，且傳回的值為0。</span><span class="sxs-lookup"><span data-stu-id="84a19-120">The number of rows affected is not returned by SQLRowCount and the returned value is 0.</span></span>|  
  
 <span data-ttu-id="84a19-121">如果 SQLRowCount 傳回0，應用程式應該測試 SQL_SOPT_SS_NOCOUNT_STATUS。</span><span class="sxs-lookup"><span data-stu-id="84a19-121">If SQLRowCount returns 0, the application should test SQL_SOPT_SS_NOCOUNT_STATUS.</span></span> <span data-ttu-id="84a19-122">如果傳回 SQL_NC_ON，則 SQLRowCount 中0的值只 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會指出尚未傳回資料列計數。</span><span class="sxs-lookup"><span data-stu-id="84a19-122">If SQL_NC_ON is returned, the value of 0 from SQLRowCount only indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has not returned a row count.</span></span> <span data-ttu-id="84a19-123">如果傳回 SQL_NC_OFF，表示 NOCOUNT 是關閉的，而 SQLRowCount 的值為 0 時，表示陳述式沒有影響任何資料列。</span><span class="sxs-lookup"><span data-stu-id="84a19-123">If SQL_NC_OFF is returned, it means that NOCOUNT is off and the value of 0 from SQLRowCount indicates that the statement did not affect any rows.</span></span>  
  
 <span data-ttu-id="84a19-124">當 SQL_SOPT_SS_NOCOUNT_STATUS 為 SQL_NC_OFF 時，應用程式不應該顯示 SQLRowCount 的值。</span><span class="sxs-lookup"><span data-stu-id="84a19-124">Applications should not display the value of SQLRowCount when SQL_SOPT_SS_NOCOUNT_STATUS is SQL_NC_OFF.</span></span> <span data-ttu-id="84a19-125">大型批次或預存程序可包含多個 SET NOCOUNT 陳述式，因此無法假設 SQL_SOPT_SS_NOCOUNT_STATUS 仍為常數。</span><span class="sxs-lookup"><span data-stu-id="84a19-125">Large batches or stored procedures can contain multiple SET NOCOUNT statements, so it cannot be assumed that SQL_SOPT_SS_NOCOUNT_STATUS remains constant.</span></span> <span data-ttu-id="84a19-126">每次 SQLRowCount 傳回0時，都應該測試此選項。</span><span class="sxs-lookup"><span data-stu-id="84a19-126">This option should be tested each time SQLRowCount returns 0.</span></span>  
  
## <a name="sql_sopt_ss_querynotification_msgtext"></a><span data-ttu-id="84a19-127">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT</span><span class="sxs-lookup"><span data-stu-id="84a19-127">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT</span></span>  
 <span data-ttu-id="84a19-128">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT 屬性會傳回查詢通知要求的訊息文字。</span><span class="sxs-lookup"><span data-stu-id="84a19-128">The SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT attribute returns the message text for the query notification request.</span></span>  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a><span data-ttu-id="84a19-129">SQLGetStmtAttr 和資料表值參數</span><span class="sxs-lookup"><span data-stu-id="84a19-129">SQLGetStmtAttr and Table-valued Parameters</span></span>  
 <span data-ttu-id="84a19-130">使用資料表值參數時，可以呼叫 SQLGetStmtAttr 來取得應用程式參數描述元 (APD) 中 SQL_SOPT_SS_PARAM_FOCUS 的值。</span><span class="sxs-lookup"><span data-stu-id="84a19-130">SQLGetStmtAttr can be called to get the value of SQL_SOPT_SS_PARAM_FOCUS in the application parameter descriptor (APD) when working with table-valued parameters.</span></span> <span data-ttu-id="84a19-131">如需 SQL_SOPT_SS_PARAM_FOCUS 的詳細資訊，請參閱[SQLSetStmtAttr](sqlsetstmtattr.md)。</span><span class="sxs-lookup"><span data-stu-id="84a19-131">For more information on SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="84a19-132">如需資料表值參數的詳細資訊，請參閱[ODBC&#41;&#40;的資料表值參數](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="84a19-132">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84a19-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84a19-133">See Also</span></span>  
 <span data-ttu-id="84a19-134">[SQLSetStmtAttr 函式](https://go.microsoft.com/fwlink/?LinkId=59370) </span><span class="sxs-lookup"><span data-stu-id="84a19-134">[SQLSetStmtAttr Function](https://go.microsoft.com/fwlink/?LinkId=59370) </span></span>  
 [<span data-ttu-id="84a19-135">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="84a19-135">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
