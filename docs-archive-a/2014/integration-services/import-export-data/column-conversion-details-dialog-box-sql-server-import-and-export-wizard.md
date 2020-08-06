---
title: 資料行轉換詳細資料對話方塊 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9207e76191060c56acad37db734827579a83aae0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597946"
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a><span data-ttu-id="c9ccc-102">資料行轉換詳細資訊對話方塊 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="c9ccc-102">Column Conversion Details Dialog Box (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="c9ccc-103">使用 [**資料行轉換詳細資訊**] 對話方塊，即可查看有關個別資料行的詳細轉換資訊。</span><span class="sxs-lookup"><span data-stu-id="c9ccc-103">Use the **Column Conversion Details** dialog box to review detailed conversion information about an individual column.</span></span> <span data-ttu-id="c9ccc-104">這項轉換資訊包含來源和目的地的資料行資料類型，以及精靈將要執行的轉換。</span><span class="sxs-lookup"><span data-stu-id="c9ccc-104">This conversion information contains the column's data type at the source and the destination, and the conversion that the wizard will perform.</span></span> <span data-ttu-id="c9ccc-105">此外，這個頁面也會列出精靈用來判斷所需資料類型轉換的資料類型對應檔案。</span><span class="sxs-lookup"><span data-stu-id="c9ccc-105">This page also lists the data type mapping files that the wizard uses to determine the data type conversions that are required.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="c9ccc-106">會在安裝期間安裝這些資料類型對應檔案。</span><span class="sxs-lookup"><span data-stu-id="c9ccc-106">installs these data type mapping files during setup.</span></span>  
  
 <span data-ttu-id="c9ccc-107">**開啟資料行轉換詳細資訊對話方塊**</span><span class="sxs-lookup"><span data-stu-id="c9ccc-107">**To open the Column Conversion Details dialog box**</span></span>  
  
1.  <span data-ttu-id="c9ccc-108">在 [匯入和匯出嚮導] 的 [**審核資料類型問題**] 頁面上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，于 [**資料表**] 清單中選取資料表。</span><span class="sxs-lookup"><span data-stu-id="c9ccc-108">On the **Review Data Type Issues** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard, in the **Table** list, select a table.</span></span>  
  
2.  <span data-ttu-id="c9ccc-109">在 [**資料類型對應**] 清單中，按兩下包含您要查看其轉換詳細資料之資料行的資料列。</span><span class="sxs-lookup"><span data-stu-id="c9ccc-109">In the **Data type mapping** list, double-click the row that contains the column for which you want to view conversion details.</span></span>  
  
 <span data-ttu-id="c9ccc-110">若要深入瞭解「匯 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 入和匯出嚮導」，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="c9ccc-110">To learn more about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="c9ccc-111">若要瞭解啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="c9ccc-111">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="c9ccc-112">「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈」的用途是將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="c9ccc-112">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="c9ccc-113">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="c9ccc-113">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="c9ccc-114">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="c9ccc-114">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="c9ccc-115">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="c9ccc-115">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
  
