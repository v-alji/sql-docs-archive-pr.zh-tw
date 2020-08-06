---
title: 資料執行中和 Text、Ntext 或 Image 資料行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- data-at-execution
- ODBC data-at-execution
- image columns [ODBC]
ms.assetid: 67ffb1a6-f38d-4712-ba64-96bdd41ec2b2
author: rothja
ms.author: jroth
ms.openlocfilehash: 404fade34862fe4705ec440eef7f466a9073250b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709321"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a><span data-ttu-id="7f369-102">資料執行中和 Text、ntext 或 Image 資料行</span><span class="sxs-lookup"><span data-stu-id="7f369-102">Data-at-Execution and Text, ntext, or Image Columns</span></span>
  <span data-ttu-id="7f369-103">ODBC 資料執行中是一種功能，可讓應用程式針對繫結的資料行或參數使用相當大量的資料。</span><span class="sxs-lookup"><span data-stu-id="7f369-103">ODBC data-at-execution is a feature that enables applications to work with extremely large amounts of data on bound columns or parameters.</span></span> <span data-ttu-id="7f369-104">當您抓取非常大的**text**、 **Ntext**或**image**資料行時，應用程式可能無法只配置大型緩衝區、將資料行系結至緩衝區，以及提取資料列。</span><span class="sxs-lookup"><span data-stu-id="7f369-104">When retrieving very large **text**, **ntext**, or **image** columns, an application may not be able to simply allocate a huge buffer, bind the column into the buffer, and fetch the row.</span></span> <span data-ttu-id="7f369-105">更新非常大的**text**、 **Ntext**或**image**資料行時，應用程式可能無法只配置大型緩衝區、將它系結至 SQL 語句中的參數標記，然後執行語句。</span><span class="sxs-lookup"><span data-stu-id="7f369-105">When updating very large **text**, **ntext**, or **image** columns, the application might not be able to simply allocate a huge buffer, bind it to a parameter marker in an SQL statement, and then execute the statement.</span></span> <span data-ttu-id="7f369-106">在這些情況下，應用程式必須使用[SQLGetData](../native-client-odbc-api/sqlgetdata.md)或[SQLPutData](../native-client-odbc-api/sqlputdata.md)搭配其資料執行中選項。</span><span class="sxs-lookup"><span data-stu-id="7f369-106">In these cases, the application must use [SQLGetData](../native-client-odbc-api/sqlgetdata.md) or [SQLPutData](../native-client-odbc-api/sqlputdata.md) with its data-at-execution options.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f369-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f369-107">See Also</span></span>  
 [<span data-ttu-id="7f369-108">管理 Text 和 Image 資料行</span><span class="sxs-lookup"><span data-stu-id="7f369-108">Managing Text and Image Columns</span></span>](managing-text-and-image-columns.md)  
  
  
