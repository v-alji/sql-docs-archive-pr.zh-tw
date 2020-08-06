---
title: 摘要：設定資料庫物件的權限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- configuring permissions on databases
ms.assetid: d0ecf297-27af-43a4-918c-31c354b3a96e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: eb6265513d467f352b0ae890dd3f119a7f5fffb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605973"
---
# <a name="summary-configuring-permissions-on-database-objects"></a><span data-ttu-id="78b08-102">摘要：設定資料庫物件的權限</span><span class="sxs-lookup"><span data-stu-id="78b08-102">Summary: Configuring Permissions on Database Objects</span></span>
  <span data-ttu-id="78b08-103">登入可讓使用者有權連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="78b08-103">Logins give users permissions to connect to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="78b08-104">使用者就是可以存取特定資料庫的登入身分。</span><span class="sxs-lookup"><span data-stu-id="78b08-104">Users are logins that can access a specific database.</span></span> <span data-ttu-id="78b08-105">使用 GRANT 陳述式可授與使用者讀取資料以及存取和變更資料的權限。</span><span class="sxs-lookup"><span data-stu-id="78b08-105">Use the GRANT statement to give users permission to read and to access and change the data.</span></span>  
  
 <span data-ttu-id="78b08-106">檢視是單一的 SELECT 陳述式，對使用者來說就像是資料表；</span><span class="sxs-lookup"><span data-stu-id="78b08-106">A view is a single SELECT statement and looks like a table to the user.</span></span> <span data-ttu-id="78b08-107">而預存程序則是以批次方式執行的一個或多個 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="78b08-107">A stored procedure is one or more [!INCLUDE[tsql](../includes/tsql-md.md)] statements that execute as a batch.</span></span>  
  
## <a name="next-lesson-in-tutorial"></a><span data-ttu-id="78b08-108">教學課程的下一課</span><span class="sxs-lookup"><span data-stu-id="78b08-108">Next Lesson in Tutorial</span></span>  
 [<span data-ttu-id="78b08-109">課程 3：刪除資料庫物件</span><span class="sxs-lookup"><span data-stu-id="78b08-109">Lesson 3: Deleting Database Objects</span></span>](lesson-3-1-deleting-database-objects.md)  
  
  
