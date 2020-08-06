---
title: 資料表值參數的 ODBC SQL 類型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL_SS_TABLE
ms.assetid: 6725bfb9-5f10-4115-be09-fd9c9f5779ea
author: rothja
ms.author: jroth
ms.openlocfilehash: c8ed46bf117c9158ae5b60c10ebd89e3d348f77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598858"
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a><span data-ttu-id="4cb9e-102">資料表值參數的 ODBC SQL 類型</span><span class="sxs-lookup"><span data-stu-id="4cb9e-102">ODBC SQL Type for Table-Valued Parameters</span></span>
  <span data-ttu-id="4cb9e-103">資料表值參數的支援是由新的 ODBC SQL 類型，也就是 SQL_SS_TABLE 所提供。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-103">Support for table-valued parameters is provided by a new ODBC SQL type, SQL_SS_TABLE.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cb9e-104">備註</span><span class="sxs-lookup"><span data-stu-id="4cb9e-104">Remarks</span></span>  
 <span data-ttu-id="4cb9e-105">SQL_SS_TABLE 無法轉換為其他任何 ODBC 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-105">SQL_SS_TABLE cannot be converted to any other ODBC or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>  
  
 <span data-ttu-id="4cb9e-106">如果在 SQLBindParameter 的*ValueType*參數中使用 SQL_SS_TABLE 做為 C 資料類型，或嘗試在應用程式參數描述項中設定 SQL_DESC_TYPE (APD) 記錄至 SQL_SS_TABLE，則會傳回 SQL_ERROR，並使用 SQLSTATE = Hy003 以及「不正確應用程式緩衝區類型」來產生診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-106">If SQL_SS_TABLE is used as a C data type in the *ValueType* parameter of SQLBindParameter, or an attempt is made to set SQL_DESC_TYPE in an application parameter descriptor (APD) record to SQL_SS_TABLE, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY003, "Invalid application buffer type".</span></span>  
  
 <span data-ttu-id="4cb9e-107">如果 SQL_DESC_TYPE 在 IPD 記錄中設定為 SQL_SS_TABLE，而且對應的應用程式參數描述項記錄不是 SQL_C_DEFAULT，則會傳回 SQL_ERROR，並產生包含 SQLSTATE=HY003 以及「無效的應用程式緩衝區類型」的診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-107">If SQL_DESC_TYPE is set to SQL_SS_TABLE in an IPD record and the corresponding application parameter descriptor record is not SQL_C_DEFAULT, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY003, "Invalid application buffer type".</span></span> <span data-ttu-id="4cb9e-108">SQLSetDescField、SQLSetDescRec 或 SQLBindParameter 的*ParameterType*可能會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-108">This can occur with the *ParameterType* of a SQLSetDescField, SQLSetDescRec or SQLBindParameter.</span></span>  
  
 <span data-ttu-id="4cb9e-109">如果在呼叫 SQLGetData 時 SQL_SS_TABLE *TargetType*參數，SQL_ERROR 會傳回，而且會產生含有 SQLSTATE = hy003 以及，「不正確應用程式緩衝區類型」的診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-109">If the *TargetType* parameter is SQL_SS_TABLE when calling SQLGetData, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY003, "Invalid application buffer type".</span></span>  
  
 <span data-ttu-id="4cb9e-110">資料表值參數資料行無法當做 SQL_SS_TABLE 類型繫結。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-110">A table-valued parameter column cannot be bound as type SQL_SS_TABLE.</span></span> <span data-ttu-id="4cb9e-111">如果 `SQLBindParameter` 使用設定為 SQL_SS_TABLE 的*ParameterType*來呼叫，則會傳回 SQL_ERROR，並產生含有 SQLSTATE = HY004，「不正確 SQL 資料類型」的診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-111">If `SQLBindParameter` is called with *ParameterType* set to SQL_SS_TABLE, SQL_ERROR is returned and a diagnostic record is generated with SQLSTATE=HY004, "Invalid SQL data type".</span></span> <span data-ttu-id="4cb9e-112">SQLSetDescField 和 SQLSetDescRec 也會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-112">This can also occur with SQLSetDescField and SQLSetDescRec.</span></span>  
  
 <span data-ttu-id="4cb9e-113">資料表值參數資料行值與參數和結果資料行的資料轉換選項相同。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-113">Table-valued parameter column values have the same data conversion options as parameters and result columns.</span></span>  
  
 <span data-ttu-id="4cb9e-114">資料表值參數在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或更新版本中僅能是輸入參數。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-114">A table-valued parameter can only be an input parameter in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span> <span data-ttu-id="4cb9e-115">如果嘗試將 SQL_DESC_PARAMETER_TYPE 設定為 SQL_PARAM_INPUT via SQLBindParameter 或 SQLSetDescField 以外的值，則會傳回 SQL_ERROR，並將診斷記錄新增至具有 SQLSTATE = HY105 和訊息「不正確參數類型」的語句中。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-115">If an attempt is made to set SQL_DESC_PARAMETER_TYPE to a value other than SQL_PARAM_INPUT via SQLBindParameter or SQLSetDescField, SQL_ERROR is returned and a diagnostic record is added to the statement with SQLSTATE=HY105 and the message "Invalid parameter type".</span></span>  
  
 <span data-ttu-id="4cb9e-116">資料表值參數資料行無法在*StrLen_or_IndPtr*中使用 SQL_DEFAULT_PARAM，因為資料表值參數不支援每個資料列的預設值。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-116">Table-valued parameter columns cannot use SQL_DEFAULT_PARAM in *StrLen_or_IndPtr*, because per-row default values are not supported with table-valued parameters.</span></span> <span data-ttu-id="4cb9e-117">不過，應用程式會將資料行屬性 SQL_CA_SS_COL_HAS_DEFAULT_VALUE 設定為 1。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-117">Instead, an application can set the column attribute SQL_CA_SS_COL_HAS_DEFAULT_VALUE to 1.</span></span> <span data-ttu-id="4cb9e-118">這表示資料行的所有資料列都會有預設值。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-118">This means that the column will have default values for all rows.</span></span> <span data-ttu-id="4cb9e-119">如果*StrLen_or_IndPtr*設定為 SQL_DEFAULT_PARAM，SQLExecute 或 SQLExecDirect 會傳回 SQL_ERROR，而診斷記錄將會加入具有 SQLSTATE = HY090 和訊息「不正確字串或緩衝區長度」的語句中。</span><span class="sxs-lookup"><span data-stu-id="4cb9e-119">If *StrLen_or_IndPtr* is set to SQL_DEFAULT_PARAM, SQLExecute or SQLExecDirect will return SQL_ERROR, and a diagnostic record will be added to the statement with SQLSTATE=HY090 and the message "Invalid string or buffer length".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb9e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cb9e-120">See Also</span></span>  
 [<span data-ttu-id="4cb9e-121">ODBC&#41;&#40;的資料表值參數</span><span class="sxs-lookup"><span data-stu-id="4cb9e-121">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
