---
title: 授與資料庫的存取權 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 45b6d6c8dcd9c04d18489807271802aafee785b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605982"
---
# <a name="granting-access-to-a-database"></a><span data-ttu-id="2d614-102">授與資料庫的存取權</span><span class="sxs-lookup"><span data-stu-id="2d614-102">Granting Access to a Database</span></span>
  <span data-ttu-id="2d614-103">Mary 現在已具有此 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體的存取權，但是沒有存取資料庫的權限。</span><span class="sxs-lookup"><span data-stu-id="2d614-103">Mary now has access to this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], but does not have permission to access the databases.</span></span> <span data-ttu-id="2d614-104">必須等到您將她授權為資料庫使用者之後，她才能存取預設的 **TestData** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2d614-104">She does not even have access to her default database **TestData** until you authorize her as a database user.</span></span>  
  
 <span data-ttu-id="2d614-105">若要授與 Mary 存取權，請切換到 **TestData** 資料庫，然後使用 CREATE USER 陳述式將其登入對應至名為 Mary 的使用者。</span><span class="sxs-lookup"><span data-stu-id="2d614-105">To grant Mary access, switch to the **TestData** database, and then use the CREATE USER statement to map her login to a user named Mary.</span></span>  
  
### <a name="to-create-a-user-in-a-database"></a><span data-ttu-id="2d614-106">若要在資料庫中建立使用者</span><span class="sxs-lookup"><span data-stu-id="2d614-106">To create a user in a database</span></span>  
  
1.  <span data-ttu-id="2d614-107">輸入並執行下列陳述式 (以您的電腦名稱取代 `computer_name` )，為 `Mary` 授與 `TestData` 資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="2d614-107">Type and execute the following statements (replacing `computer_name` with the name of your computer) to grant `Mary` access to the `TestData` database.</span></span>  
  
    ```  
    USE [TestData];  
    GO  
  
    CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
    GO  
  
    ```  
  
     <span data-ttu-id="2d614-108">現在 Mary 即具有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 和 `TestData` 資料庫兩者的存取權。</span><span class="sxs-lookup"><span data-stu-id="2d614-108">Now, Mary has access to both [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and the `TestData` database.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2d614-109">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="2d614-109">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2d614-110">建立視圖和預存程式</span><span class="sxs-lookup"><span data-stu-id="2d614-110">Creating Views and Stored Procedures</span></span>](lesson-2-3-creating-views-and-stored-procedures.md)  
  
  
