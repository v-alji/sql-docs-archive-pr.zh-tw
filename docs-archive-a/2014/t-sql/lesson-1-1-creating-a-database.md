---
title: 建立資料庫 (教學課程) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tutorial creating a database
ms.assetid: e1e2c83f-dfad-4bb8-aa7a-09d3f69517ae
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 99d5439c289b5d4e71786d4c6734f158f6bba371
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597484"
---
# <a name="creating-a-database-tutorial"></a><span data-ttu-id="3bd76-102">建立資料庫 (教學課程)</span><span class="sxs-lookup"><span data-stu-id="3bd76-102">Creating a Database (Tutorial)</span></span>
  <span data-ttu-id="3bd76-103">和許多 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式一樣，CREATE DATABASE 陳述式也有一個必要參數，那就是資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="3bd76-103">Like many [!INCLUDE[tsql](../includes/tsql-md.md)] statements, the CREATE DATABASE statement has a required parameter: the name of the database.</span></span> <span data-ttu-id="3bd76-104">CREATE DATABASE 另外還有許多選擇性參數，例如，要用來放置資料庫檔案的磁碟位置。</span><span class="sxs-lookup"><span data-stu-id="3bd76-104">CREATE DATABASE also has many optional parameters, such as the disk location where you want to put the database files.</span></span> <span data-ttu-id="3bd76-105">當您執行 CREATE DATABASE 但未指定任何選擇性參數時， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 多半會使用這些參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="3bd76-105">When you execute CREATE DATABASE without the optional parameters, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] uses default values for many of these parameters.</span></span> <span data-ttu-id="3bd76-106">這個教學課程使用的選擇性語法參數非常少。</span><span class="sxs-lookup"><span data-stu-id="3bd76-106">This tutorial uses very few of the optional syntax parameters.</span></span>  
  
### <a name="to-create-a-database"></a><span data-ttu-id="3bd76-107">若要建立資料庫</span><span class="sxs-lookup"><span data-stu-id="3bd76-107">To create a database</span></span>  
  
1.  <span data-ttu-id="3bd76-108">在 [查詢編輯器] 視窗中，輸入下列程式碼 (但不要執行)：</span><span class="sxs-lookup"><span data-stu-id="3bd76-108">In a Query Editor window, type but do not execute the following code:</span></span>  
  
    ```  
    CREATE DATABASE TestData  
    GO  
    ```  
  
2.  <span data-ttu-id="3bd76-109">使用指標選取 `CREATE DATABASE`這兩個字，然後按 **F1**鍵。</span><span class="sxs-lookup"><span data-stu-id="3bd76-109">Use the pointer to select the words `CREATE DATABASE`, and then press **F1**.</span></span> <span data-ttu-id="3bd76-110">這時應該會開啟《SQL Server 線上叢書》中的＜CREATE DATABASE＞主題。</span><span class="sxs-lookup"><span data-stu-id="3bd76-110">The CREATE DATABASE topic in SQL Server Books Online should open.</span></span> <span data-ttu-id="3bd76-111">您可以利用這種方式找到 CREATE DATABASE 以及在這個教學課程中所使用之其他陳述式的完整語法。</span><span class="sxs-lookup"><span data-stu-id="3bd76-111">You can use this technique to find the complete syntax for CREATE DATABASE and for the other statements that are used in this tutorial.</span></span>  
  
3.  <span data-ttu-id="3bd76-112">在 [查詢編輯器] 中按 **F5** ，執行陳述式並建立名為 `TestData`的資料庫。</span><span class="sxs-lookup"><span data-stu-id="3bd76-112">In Query Editor, press **F5** to execute the statement and create a database named `TestData`.</span></span>  
  
 <span data-ttu-id="3bd76-113">當您建立資料庫時， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會建立 **model** 資料庫的複本，並且將此複本重新命名為資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="3bd76-113">When you create a database, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] makes a copy of the **model** database, and renames the copy to the database name.</span></span> <span data-ttu-id="3bd76-114">除非您在選擇性參數中指定了非常大的資料庫初始大小，否則這項作業應該只需要幾秒鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="3bd76-114">This operation should only take several seconds, unless you specify a large initial size of the database as an optional parameter.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3bd76-115">如果在單一批次中提交了一個以上的陳述式，可用關鍵字 GO 來分隔陳述式；</span><span class="sxs-lookup"><span data-stu-id="3bd76-115">The keyword GO separates statements when more than one statement is submitted in a single batch.</span></span> <span data-ttu-id="3bd76-116">如果批次中只包含一個陳述式，則 GO 可有可無。</span><span class="sxs-lookup"><span data-stu-id="3bd76-116">GO is optional when the batch contains only one statement.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="3bd76-117">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="3bd76-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="3bd76-118">建立資料表 &#40;教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="3bd76-118">Creating a Table &#40;Tutorial&#41;</span></span>](lesson-1-2-creating-a-table.md)  
  
## <a name="see-also"></a><span data-ttu-id="3bd76-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bd76-119">See Also</span></span>  
 [<span data-ttu-id="3bd76-120">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3bd76-120">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
