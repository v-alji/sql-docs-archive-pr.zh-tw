---
title: 在 SQL Server Native Client 中使用 OUTPUT 子句搭配 OLE DB |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 53deeb99-c088-4fde-844b-b2d91d6de1eb
author: rothja
ms.author: jroth
ms.openlocfilehash: a425ec6269040c72836571b8fa8b51bba4ed8c32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706417"
---
# <a name="using-the-output-clause-with-ole-db-in-sql-server-native-client"></a><span data-ttu-id="14d82-102">在 SQL Server Native Client 中使用 OUTPUT 子句搭配 OLE DB</span><span class="sxs-lookup"><span data-stu-id="14d82-102">Using the OUTPUT Clause with OLE DB in SQL Server Native Client</span></span>
  <span data-ttu-id="14d82-103">如果您在 INSERT、UPDATE、DELETE 或 MERGE 命令中使用 OUTPUT 子句，受影響的資料列計數就無法使用。</span><span class="sxs-lookup"><span data-stu-id="14d82-103">If you use an OUTPUT clause in an INSERT, UPDATE, DELETE, or MERGE command, the count of affected rows is not available.</span></span> <span data-ttu-id="14d82-104">應用程式必須計算 OUTPUT 子句所傳回的資料列集中的資料列數。</span><span class="sxs-lookup"><span data-stu-id="14d82-104">The application must count the number of rows in the rowset that is returned by the OUTPUT clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14d82-105">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14d82-105">See Also</span></span>  
 [<span data-ttu-id="14d82-106">建立 SQL Server Native Client OLE DB 提供者應用程式</span><span class="sxs-lookup"><span data-stu-id="14d82-106">Creating a SQL Server Native Client OLE DB Provider Application</span></span>](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
