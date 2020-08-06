---
title: 開發、測試和生產資料庫 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- production databases [SQL Server]
- testing databases
- database testing [SQL Server]
ms.assetid: cb403330-8cbe-41c6-bd23-bc432d50f173
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98ac88aec42b53012e0f57233a089bddbd3c8cae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688409"
---
# <a name="development-test-and-production-databases-visual-database-tools"></a><span data-ttu-id="979be-102">開發、測試和生產資料庫 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="979be-102">Development, Test, and Production Databases (Visual Database Tools)</span></span>
  <span data-ttu-id="979be-103">如果您有兩個結構完全相同的資料庫，您可以變更其中一個資料庫，然後再將這些變更傳播到另一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="979be-103">If you have two databases with identical structure, you can make changes in one database and propagate those changes to the other.</span></span> <span data-ttu-id="979be-104">例如，如果您具備個人開發資料庫和群組測試資料庫，您可以修改開發資料庫，然後將這些變更傳播到測試資料庫。</span><span class="sxs-lookup"><span data-stu-id="979be-104">For example, if you have a personal development database and a group-wide test database, you can modify the development database, then propagate those changes to the test database.</span></span>  
  
 <span data-ttu-id="979be-105">若要完成此工作，請在單一工作階段中對開發資料庫執行所有的修改，建立工作階段的變更指令碼 (Change Script)，然後在測試資料庫中執行此指令碼。</span><span class="sxs-lookup"><span data-stu-id="979be-105">To accomplish this, perform all the modifications in a single session with the development database, create a Change Script of your session and later run the script on the test database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="979be-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="979be-106">See Also</span></span>  
 [<span data-ttu-id="979be-107">多使用者環境 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="979be-107">Multiuser Environments &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
