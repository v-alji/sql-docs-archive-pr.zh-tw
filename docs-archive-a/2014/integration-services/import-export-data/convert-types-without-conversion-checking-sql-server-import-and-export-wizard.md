---
title: 轉換類型而不進行轉換檢查 (SQL Server 匯入和匯出嚮導) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.nomappingfile.f1
ms.assetid: 87d9d3e5-477f-4117-a37f-bff53ea3e14d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3874bcad23994fdcf69ade948239760d5c871917
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597939"
---
# <a name="convert-types-without-conversion-checking-sql-server-import-and-export-wizard"></a><span data-ttu-id="98dce-102">轉換類型但不檢查轉換 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="98dce-102">Convert Types without Conversion Checking (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="98dce-103">使用 [**轉換類型但不轉換**] 頁面，即可在 wizard 找不到一或多個 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型轉換和對應檔案時，檢查 wizard 所執行的對應。</span><span class="sxs-lookup"><span data-stu-id="98dce-103">Use the **Convert Types without Conversion Checking** page to review the mappings that the wizard performs when the wizard cannot locate one or more of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type conversion and mapping files.</span></span> <span data-ttu-id="98dce-104">這個頁面含有一些資訊，可協助您識別遺失的檔案。</span><span class="sxs-lookup"><span data-stu-id="98dce-104">This page includes information that helps you identify the missing file or files.</span></span>  
  
 <span data-ttu-id="98dce-105">若要深入瞭解此嚮導，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="98dce-105">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="98dce-106">若要瞭解啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="98dce-106">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="98dce-107">「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈」的用途是將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="98dce-107">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="98dce-108">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="98dce-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="98dce-109">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="98dce-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="98dce-110">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="98dce-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
  
