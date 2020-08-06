---
title: 資料表值參數資料轉換和其他錯誤和警告 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
author: rothja
ms.author: jroth
ms.openlocfilehash: 45b9ba7f91b54548e096bbe47da6e01ba562f59d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585341"
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a><span data-ttu-id="d2ad1-102">資料表值參數資料轉換及其他錯誤和警告</span><span class="sxs-lookup"><span data-stu-id="d2ad1-102">Table-Valued Parameter Data Conversion and Other Errors and Warnings</span></span>
  <span data-ttu-id="d2ad1-103">資料表值參數資料行值可以在用戶端和伺服器資料類型之間轉換，其轉換方式與其他資料行和參數值相同。</span><span class="sxs-lookup"><span data-stu-id="d2ad1-103">Table-valued parameter column values can be converted between client and server data types in the same way as other column and parameter values.</span></span> <span data-ttu-id="d2ad1-104">因為資料表值參數可以包含多個資料行和多個資料列，所以能夠識別發生錯誤的實際值是很重要的一件事。</span><span class="sxs-lookup"><span data-stu-id="d2ad1-104">But because a table-valued parameter can contain multiple columns and multiple rows, it is important to be able to identify the actual value where the error occurred.</span></span>  
  
 <span data-ttu-id="d2ad1-105">當資料表值參數資料行中偵測到錯誤或警告時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 將會產生診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="d2ad1-105">When an error or warning is detected in a table-valued parameter column, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client will generate a diagnostic record.</span></span> <span data-ttu-id="d2ad1-106">錯誤訊息將會包含資料表值參數的參數編號，加上資料行序數和資料列號碼。</span><span class="sxs-lookup"><span data-stu-id="d2ad1-106">The error message will contain the parameter number of the table-valued parameter, plus the column ordinal and row number.</span></span> <span data-ttu-id="d2ad1-107">應用程式可以使用診斷記錄中的診斷欄位 SQL_DIAG_SS_TABLE_COLUMN_NUMBER 和 SQL_DIAG_SS_TABLE_ROW_NUMBER，以判斷哪些值與錯誤和警告有關。</span><span class="sxs-lookup"><span data-stu-id="d2ad1-107">An application can also use the diagnostic fields SQL_DIAG_SS_TABLE_COLUMN_NUMBER and SQL_DIAG_SS_TABLE_ROW_NUMBER within diagnostic records to determine which values are associated with errors and warnings.</span></span> <span data-ttu-id="d2ad1-108">這些診斷欄位會在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更新版本中提供。</span><span class="sxs-lookup"><span data-stu-id="d2ad1-108">These diagnostic fields are available in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions.</span></span>  
  
 <span data-ttu-id="d2ad1-109">診斷記錄的 SQLSTATE 和訊息元件將會在所有其他層面符合現有的 ODBC 行為。</span><span class="sxs-lookup"><span data-stu-id="d2ad1-109">The SQLSTATE and message components of diagnostic records will conform to existing ODBC behavior in all other respects.</span></span> <span data-ttu-id="d2ad1-110">也就是說，除了參數、資料列和資料行識別資訊以外，錯誤訊息與資料表值參數的值相同，與非資料表值參數相同。</span><span class="sxs-lookup"><span data-stu-id="d2ad1-110">That is, except for the parameter, row, and column identification information, error messages have the same values for table-valued parameters as they would for non-table-valued parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ad1-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2ad1-111">See Also</span></span>  
 [<span data-ttu-id="d2ad1-112">ODBC&#41;&#40;的資料表值參數</span><span class="sxs-lookup"><span data-stu-id="d2ad1-112">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
