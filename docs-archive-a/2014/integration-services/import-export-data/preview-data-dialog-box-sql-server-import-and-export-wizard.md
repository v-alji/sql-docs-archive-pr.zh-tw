---
title: 預覽資料對話方塊 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.previewdata.f1
ms.assetid: 423ac26a-ba02-4fdf-88b4-07995fe4a97e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 17debc001d8ba7826fe845c006e944e5a3dc87a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597929"
---
# <a name="preview-data-dialog-box-sql-server-import-and-export-wizard"></a><span data-ttu-id="70f3d-102">預覽資料對話方塊 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="70f3d-102">Preview Data Dialog Box (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="70f3d-103">使用 [**預覽資料**] 對話方塊，即可查看匯 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 入和匯出嚮導將傳送至資料來源的查詢。</span><span class="sxs-lookup"><span data-stu-id="70f3d-103">Use the **Preview Data** dialog box to see the query that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard will send to the data source.</span></span> <span data-ttu-id="70f3d-104">您還可以使用此對話方塊，最多預覽 200 個取樣資料的資料列。</span><span class="sxs-lookup"><span data-stu-id="70f3d-104">You can also use this dialog box to preview up to 200 rows of sample data.</span></span>  
  
 <span data-ttu-id="70f3d-105">若要深入瞭解「匯 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 入和匯出嚮導」，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="70f3d-105">To learn more about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="70f3d-106">若要瞭解啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="70f3d-106">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="70f3d-107">「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈」的用途是將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="70f3d-107">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="70f3d-108">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="70f3d-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="70f3d-109">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="70f3d-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="70f3d-110">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="70f3d-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
 <span data-ttu-id="70f3d-111">**開啟預覽資料對話方塊**</span><span class="sxs-lookup"><span data-stu-id="70f3d-111">**To open the Preview Data dialog box**</span></span>  
  
-   <span data-ttu-id="70f3d-112">在 [匯入和匯出嚮導] 的 [**選取來源資料表和視圖**] 頁面上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，按一下 [**預覽**]。</span><span class="sxs-lookup"><span data-stu-id="70f3d-112">On the **Select Source Tables and Views** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard, click **Preview**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="70f3d-113">選項</span><span class="sxs-lookup"><span data-stu-id="70f3d-113">Options</span></span>  
 <span data-ttu-id="70f3d-114">**Source**</span><span class="sxs-lookup"><span data-stu-id="70f3d-114">**Source**</span></span>  
 <span data-ttu-id="70f3d-115">顯示此精靈將傳送至資料來源的查詢。</span><span class="sxs-lookup"><span data-stu-id="70f3d-115">Displays the query that the wizard will send to the data source.</span></span>  
  
 <span data-ttu-id="70f3d-116">**取樣資料方格**</span><span class="sxs-lookup"><span data-stu-id="70f3d-116">**Sample data grid**</span></span>  
 <span data-ttu-id="70f3d-117">最多顯示 200 個查詢傳回之取樣資料的資料列。</span><span class="sxs-lookup"><span data-stu-id="70f3d-117">Displays up to 200 rows of sample data that the query returned.</span></span>  
  
  
