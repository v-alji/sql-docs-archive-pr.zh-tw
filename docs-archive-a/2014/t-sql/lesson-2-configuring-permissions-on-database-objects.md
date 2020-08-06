---
title: 第 2 課：設定資料庫物件的權限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
helpviewer_keywords:
- database permissions
ms.assetid: f964b66a-ec32-44c2-a185-6a0f173bfa22
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: fcc6ee3ddf9be072b51bd568fd3e72eb6c871785
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708013"
---
# <a name="lesson-2-configuring-permissions-on-database-objects"></a><span data-ttu-id="49eaa-102">第 2 課：設定資料庫物件的權限</span><span class="sxs-lookup"><span data-stu-id="49eaa-102">Lesson 2: Configuring Permissions on Database Objects</span></span>
  <span data-ttu-id="49eaa-103">授與使用者存取資料庫的權限包括三個步驟。</span><span class="sxs-lookup"><span data-stu-id="49eaa-103">Granting a user access to a database involves three steps.</span></span> <span data-ttu-id="49eaa-104">首先，請建立登入。</span><span class="sxs-lookup"><span data-stu-id="49eaa-104">First, you create a login.</span></span> <span data-ttu-id="49eaa-105">登入可讓使用者連接到 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="49eaa-105">The login lets the user connect to the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="49eaa-106">接著，請將登入設定為指定之資料庫的使用者。</span><span class="sxs-lookup"><span data-stu-id="49eaa-106">Then you configure the login as a user in the specified database.</span></span> <span data-ttu-id="49eaa-107">最後，請授與該使用者存取資料庫物件的權限。</span><span class="sxs-lookup"><span data-stu-id="49eaa-107">And finally, you grant that user permission to database objects.</span></span> <span data-ttu-id="49eaa-108">這一課會示範這三個步驟，並且說明如何將檢視和預存程序建立為物件。</span><span class="sxs-lookup"><span data-stu-id="49eaa-108">This lesson shows you these three steps, and shows you how to create a view and a stored procedure as the object.</span></span>  
  
 <span data-ttu-id="49eaa-109">這個課程包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="49eaa-109">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="49eaa-110">建立登入</span><span class="sxs-lookup"><span data-stu-id="49eaa-110">Creating a Login</span></span>](lesson-2-1-creating-a-login.md)  
  
-   [<span data-ttu-id="49eaa-111">授與資料庫的存取權</span><span class="sxs-lookup"><span data-stu-id="49eaa-111">Granting Access to a Database</span></span>](lesson-2-2-granting-access-to-a-database.md)  
  
-   [<span data-ttu-id="49eaa-112">建立視圖和預存程式</span><span class="sxs-lookup"><span data-stu-id="49eaa-112">Creating Views and Stored Procedures</span></span>](lesson-2-3-creating-views-and-stored-procedures.md)  
  
-   [<span data-ttu-id="49eaa-113">授與資料庫物件的存取權</span><span class="sxs-lookup"><span data-stu-id="49eaa-113">Granting Access to a Database Object</span></span>](lesson-2-4-granting-access-to-a-database-object.md)  
  
-   [<span data-ttu-id="49eaa-114">摘要：設定資料庫物件的權限</span><span class="sxs-lookup"><span data-stu-id="49eaa-114">Summary: Configuring Permissions on Database Objects</span></span>](lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="49eaa-115">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="49eaa-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="49eaa-116">建立登入</span><span class="sxs-lookup"><span data-stu-id="49eaa-116">Creating a Login</span></span>](lesson-2-1-creating-a-login.md)  
  
  
