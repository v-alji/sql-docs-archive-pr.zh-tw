---
title: 多使用者環境 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- users [SQL Server], multiuser environments
- conflict resolution [Visual Database Tools]
- multiple users making database changes
- multiuser environments [Visual Database Tools]
- database modifications [SQL Server]
- version control [Visual Database Tools]
- Visual Database Tools [SQL Server], multiuser environments
ms.assetid: 330bd48c-9427-4967-b58e-b7c492d5ee36
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2e219ecda25f477aa459de674a43d9c2360376ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593745"
---
# <a name="multiuser-environments-visual-database-tools"></a><span data-ttu-id="4fe0a-102">多使用者環境 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="4fe0a-102">Multiuser Environments (Visual Database Tools)</span></span>
  <span data-ttu-id="4fe0a-103">在多使用者環境中，其他使用者可以連接並變更您正在使用的相同資料庫。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-103">A multiuser environment is one in which other users can connect and make changes to the same database that you are working with.</span></span> <span data-ttu-id="4fe0a-104">因此數個使用者可同時使用同一個資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-104">As a result, several users might be working with the same database objects at the same time.</span></span> <span data-ttu-id="4fe0a-105">也就是說，當您在多使用者環境中進行變更時，其他使用者所做的變更可能會影響資料庫，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-105">Thus, a multiuser environment introduces the possibility of the database being affected by changes made by other users while you are making changes, and vice versa.</span></span>  
  
 <span data-ttu-id="4fe0a-106">在多使用者環境中使用資料庫的重點即為存取權限。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-106">A key issue when working with databases in a multiuser environment is access permissions.</span></span> <span data-ttu-id="4fe0a-107">您具備的資料庫權限將決定您可以使用資料庫的工作範圍。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-107">The permissions you have for the database determine the extent of the work you can do with the database.</span></span> <span data-ttu-id="4fe0a-108">例如，若要變更資料庫中的物件，您必須擁有資料庫的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-108">For example, to make changes to objects in a database, you must have the appropriate write permissions for the database.</span></span> <span data-ttu-id="4fe0a-109">如需資料庫權限的詳細資訊，請參閱您的資料庫文件。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-109">For more information about permissions in your database, see your database documentation.</span></span> <span data-ttu-id="4fe0a-110">如需詳細資訊，請參閱[權限和 Visual Database Tools &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-110">For more information see [Permissions and Visual Database Tools &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="4fe0a-111">當您儲存對資料表所做的變更時，[資料表設計師] 會驗證自您上次儲存變更以來資料庫沒有被修改過。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-111">When you save changes made to tables, Table Designer verifies that the database has not been modified since you last saved changes.</span></span> <span data-ttu-id="4fe0a-112">如果其他使用者變更該資料庫，您將接獲通知表示資料庫已被修改過。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-112">If another user has made changes, you will be notified that the database has been modified.</span></span> <span data-ttu-id="4fe0a-113">您可能需要調整這些變更。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-113">You may need to reconcile these changes.</span></span> <span data-ttu-id="4fe0a-114">如需詳細資訊，請參閱[協調多位使用者所做的變更 &#40;Visual Database Tools&#41;](reconcile-changes-made-by-multiple-users-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-114">For more information, see [Reconcile Changes Made by Multiple Users &#40;Visual Database Tools&#41;](reconcile-changes-made-by-multiple-users-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="4fe0a-115">在多使用者環境中必須注意某些特殊考量，以避免使變更發生衝突。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-115">In a multiuser environment there are special considerations to keep in mind to avoid conflicting changes.</span></span> <span data-ttu-id="4fe0a-116">如需詳細資訊，請參閱[資料庫演進問題 &#40;Visual Database Tools&#41;](issues-of-database-evolution-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-116">For more information, see [Issues of Database Evolution &#40;Visual Database Tools&#41;](issues-of-database-evolution-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="4fe0a-117">一個避免問題的方法是，在進行變更時使用資料庫的複本，例如測試資料庫，然後建立變更指令碼 (Change Script)，先在離線時解決衝突後，再於原始資料庫上執行該指令碼，以進行這些變更。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-117">One way to avoid problems is to work in a copy of the database, such as a test database, when you make changes, then you can create a change script that you can run to make those changes on the original database after resolving conflicts offline.</span></span> <span data-ttu-id="4fe0a-118">如需詳細資訊，請參閱[開發、測試和生產資料庫 &#40;Visual Database Tools&#41;](development-test-and-production-databases-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-118">For more information see [Development, Test, and Production Databases &#40;Visual Database Tools&#41;](development-test-and-production-databases-visual-database-tools.md).</span></span>  
  
  
