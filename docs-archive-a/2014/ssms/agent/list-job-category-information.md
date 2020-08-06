---
title: 列出作業類別目錄資訊 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 924e2b064980b2ea7068230610414262995da1a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704681"
---
# <a name="list-job-category-information"></a><span data-ttu-id="468a3-102">列出作業類別目錄資訊</span><span class="sxs-lookup"><span data-stu-id="468a3-102">List Job Category Information</span></span>
  <span data-ttu-id="468a3-103">如何 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用或 SQL Server 管理物件，在中列出作業類別目錄資訊 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="468a3-103">How to list job category information in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  

  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="468a3-104">Security</span><span class="sxs-lookup"><span data-stu-id="468a3-104">Security</span></span>  
 <span data-ttu-id="468a3-105">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="468a3-105">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  

  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="468a3-106">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="468a3-106">Using Transact-SQL</span></span>  
  
#### <a name="to-list-job-category-information"></a><span data-ttu-id="468a3-107">若要列出作業類別目錄資訊</span><span class="sxs-lookup"><span data-stu-id="468a3-107">To list job category information</span></span>  
  
1.  <span data-ttu-id="468a3-108">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="468a3-108">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="468a3-109">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="468a3-109">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="468a3-110">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="468a3-110">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
 <span data-ttu-id="468a3-111">如需詳細資訊，請參閱[sp_help_category &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="468a3-111">For more information, see [sp_help_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql).</span></span>  
  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="468a3-112">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="468a3-112">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="468a3-113">**若要列出作業類別目錄資訊**</span><span class="sxs-lookup"><span data-stu-id="468a3-113">**To list job category information**</span></span>  
  
 <span data-ttu-id="468a3-114">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `JobCategory` 類別。</span><span class="sxs-lookup"><span data-stu-id="468a3-114">Use the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell..</span></span> <span data-ttu-id="468a3-115">如需詳細資訊，請參閱[SQL Server 管理物件 &#40;SMO&#41; 程式設計手冊](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="468a3-115">For more information, see [SQL Server Management Objects &#40;SMO&#41; Programming Guide](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md).</span></span>  
