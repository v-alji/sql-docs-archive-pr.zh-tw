---
title: 建立資料表的 SQL 陳述式 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createtablesql.f1
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d3fc2054711708a27691f2d7219c33749f11b977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597940"
---
# <a name="create-table-sql-statement-sql-server-import-and-export-wizard"></a><span data-ttu-id="8ccd3-102">建立資料表的 SQL 陳述式 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="8ccd3-102">Create Table SQL Statement (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="8ccd3-103">使用 [**建立資料表的 SQL 語句**] 對話方塊，即可查看自動產生的語句，或針對您的用途加以修改。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-103">Use the **Create Table SQL Statement** dialog box to view the statement that was generated automatically, or to modify it for your purposes.</span></span> <span data-ttu-id="8ccd3-104">如果您修改此陳述式，就可能也必須對資料行對應進行相關的變更，而且此後必須手動維護已編輯的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-104">If you modify this statement, you may also have to make associated changes to column mapping, and you will have to maintain the edited SQL statement manually thereafter.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="8ccd3-105">會根據連接的資料來源來產生預設 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-105">generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="8ccd3-106">這個預設 CREATE TABLE 陳述式將不會包含 FILESTREAM 屬性，即使來源資料表包含有宣告 FILESTREAM 屬性的資料行亦然。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-106">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="8ccd3-107">若要執行具有 FILESTREAM 屬性的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 元件，請先在目的地資料庫上實作 FILESTREAM 儲存體。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-107">To run an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="8ccd3-108">然後在 **[建立資料表]** 對話方塊中，將 FILESTREAM 屬性加入至 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-108">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="8ccd3-109">如需詳細資訊，請參閱[二進位大型物件 &#40;Blob&#41; 資料 &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-109">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="8ccd3-110">若要深入瞭解此嚮導，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-110">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="8ccd3-111">若要瞭解用來啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-111">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="8ccd3-112">「SQL Server 匯入和匯出精靈」的用途在於將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-112">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="8ccd3-113">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-113">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="8ccd3-114">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-114">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="8ccd3-115">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-115">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8ccd3-116">選項。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-116">Options</span></span>  
 <span data-ttu-id="8ccd3-117">**SQL 語句**</span><span class="sxs-lookup"><span data-stu-id="8ccd3-117">**SQL statement**</span></span>  
 <span data-ttu-id="8ccd3-118">顯示自動產生的 SQL 陳述式並進行編輯。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-118">Displays the auto-generated SQL statement and lets it be edited.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ccd3-119">如果要在 SQL 陳述式中包含歸位字元，請按 CTRL+ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-119">If you want to include a carriage return in the SQL statement, press CTRL+ENTER.</span></span> <span data-ttu-id="8ccd3-120">如果只按 ENTER 鍵，對話方塊就會關閉。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-120">If you press only ENTER, the dialog box closes.</span></span>  
  
 <span data-ttu-id="8ccd3-121">**自動產生**</span><span class="sxs-lookup"><span data-stu-id="8ccd3-121">**Autogenerate**</span></span>  
 <span data-ttu-id="8ccd3-122">按一下 [自動產生]\*\*\*\*，還原預設的 SQL 陳述式 (如果已修改的話)。</span><span class="sxs-lookup"><span data-stu-id="8ccd3-122">Restore the default SQL statement, if you have modified it, by clicking **Autogenerate**.</span></span>  
  
  
