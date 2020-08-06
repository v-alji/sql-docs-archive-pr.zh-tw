---
title: 以指令碼編寫資料表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ea88d736-849e-4368-b55d-06aeee097bf3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 247c839d83768756c57297d47f952401a1c8fd46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594301"
---
# <a name="script-a-table"></a><span data-ttu-id="df59a-102">編寫資料表的指令碼</span><span class="sxs-lookup"><span data-stu-id="df59a-102">Script a Table</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="df59a-103">可以建立指令碼來選取、插入、更新和刪除資料表，以及建立、變更、卸除或執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="df59a-103">can create scripts to select, insert, update, and delete tables, and to create, alter, drop, or execute stored procedures.</span></span>  
  
 <span data-ttu-id="df59a-104">您有時會希望指令碼有多個選項，如先卸除程序，再建立程序，或先建立資料表，再變更資料表。</span><span class="sxs-lookup"><span data-stu-id="df59a-104">Sometimes you want a script with multiple options, such as drop a procedure and then create a procedure, or create a table then alter a table.</span></span> <span data-ttu-id="df59a-105">若要建立結合的指令碼，請將第一個指令碼儲存在 [查詢編輯器] 視窗中，再將第二個指令碼儲存在剪貼簿中，以便在視窗中將它貼在第一個指令碼之後。</span><span class="sxs-lookup"><span data-stu-id="df59a-105">To create combined scripts, save the first script to a Query Editor window and the second to the clipboard so you can paste it into the window after the first script.</span></span>  
  
## <a name="creating-an-update-script"></a><span data-ttu-id="df59a-106">建立更新指令碼</span><span class="sxs-lookup"><span data-stu-id="df59a-106">Creating an Update Script</span></span>  
  
#### <a name="to-create-the-insert-script-for-a-table"></a><span data-ttu-id="df59a-107">建立資料表的插入指令碼</span><span class="sxs-lookup"><span data-stu-id="df59a-107">To create the insert script for a table</span></span>  
  
1.  <span data-ttu-id="df59a-108">在物件總管中，展開您的伺服器，依序展開 [資料庫]\*\*\*\*、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 和 [資料表]\*\*\*\*，並以滑鼠右鍵按一下 [HumanResources.Employee]\*\*\*\*，然後指向 [產生資料表的指令碼為]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="df59a-108">In Object Explorer, expand your server, expand **Databases**, expand [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], expand **Tables**, right-click **HumanResources.Employee**, and then point to **Script Table As**.</span></span>  
  
2.  <span data-ttu-id="df59a-109">快速鍵功能表有七個可用的編寫指令碼選項：[CREATE 至]\*\*\*\*、[DROP 至]\*\*\*\*、[DROP 並 CREATE 至]\*\*\*\*、[SELECT 至]\*\*\*\*、[INSERT 至]\*\*\*\*、[UPDATE 至]\*\*\*\* 和 [DELETE 至]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="df59a-109">The shortcut menu has seven available scripting options: **CREATE To**, **DROP To**, **DROP and CREATE To**, **SELECT To**, **INSERT To**, **UPDATE To**, and **DELETE To**.</span></span> <span data-ttu-id="df59a-110">指向 [UPDATE To]\*\*\*\*，然後按一下 [新增查詢編輯器視窗]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="df59a-110">Point to **UPDATE To**, and then click **New Query Editor Window**.</span></span>  
  
3.  <span data-ttu-id="df59a-111">此時會開啟新的 [查詢編輯器] 視窗、建立連接，並提供完整的 UPDATE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="df59a-111">A new Query Editor window opens, makes a connection, and presents the entire update statement.</span></span>  
  
     <span data-ttu-id="df59a-112">這個練習說明編寫指令碼的功能遠遠超過只是編寫建立資料表或預存程序的指令碼。</span><span class="sxs-lookup"><span data-stu-id="df59a-112">This exercise demonstrates how the scripting feature can do more than just script the creation of a table or stored procedure.</span></span> <span data-ttu-id="df59a-113">這項新功能可協助您將操作資料的指令碼快速加入專案中，以及輕鬆地編寫執行預存程序的指令碼。</span><span class="sxs-lookup"><span data-stu-id="df59a-113">This new feature can help you quickly add data manipulation scripts to your project and easily script execution of stored procedures.</span></span> <span data-ttu-id="df59a-114">如果資料表和程序有許多欄位，這可以節省很多時間。</span><span class="sxs-lookup"><span data-stu-id="df59a-114">This can be a big timesaver for tables and procedures with many fields.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="df59a-115">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="df59a-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="df59a-116">摘要：撰寫 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="df59a-116">Summary: Writing Transact-SQL</span></span>](../../tutorials/summary-writing-transact-sql.md)  
  
  
