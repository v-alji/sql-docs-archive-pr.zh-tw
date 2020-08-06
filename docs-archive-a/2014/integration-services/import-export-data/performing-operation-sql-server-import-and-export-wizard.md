---
title: 執行作業 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.performingoperation.f1
ms.assetid: 83259509-71d6-4a64-a7f2-4e9603b30bd4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b6cdac605da2288149909a3fb6e9f245e10eebf8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597936"
---
# <a name="performing-operation-sql-server-import-and-export-wizard"></a><span data-ttu-id="44cd1-102">正在執行作業 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="44cd1-102">Performing Operation (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="44cd1-103">使用 [**正在執行**作業] 頁面，即可查看匯入/匯出作業的進度和結果，並在必要時中斷操作。</span><span class="sxs-lookup"><span data-stu-id="44cd1-103">Use the **Performing Operation** page to view the progress and the results of the import/export operation, and to interrupt the operation if necessary.</span></span>  
  
 <span data-ttu-id="44cd1-104">若要深入瞭解此嚮導，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="44cd1-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="44cd1-105">若要瞭解用來啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="44cd1-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="44cd1-106">「SQL Server 匯入和匯出精靈」的用途在於將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="44cd1-106">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="44cd1-107">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="44cd1-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="44cd1-108">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="44cd1-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="44cd1-109">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="44cd1-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="44cd1-110">選項</span><span class="sxs-lookup"><span data-stu-id="44cd1-110">Options</span></span>  
 <span data-ttu-id="44cd1-111">**動作**</span><span class="sxs-lookup"><span data-stu-id="44cd1-111">**Action**</span></span>  
 <span data-ttu-id="44cd1-112">顯示屬於作業一部分的每個動作。</span><span class="sxs-lookup"><span data-stu-id="44cd1-112">Displays each action that is part of the operation.</span></span>  
  
 <span data-ttu-id="44cd1-113">**狀態**</span><span class="sxs-lookup"><span data-stu-id="44cd1-113">**Status**</span></span>  
 <span data-ttu-id="44cd1-114">顯示每個動作是成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="44cd1-114">Displays the success or failure of each action.</span></span>  
  
 <span data-ttu-id="44cd1-115">**Message**</span><span class="sxs-lookup"><span data-stu-id="44cd1-115">**Message**</span></span>  
 <span data-ttu-id="44cd1-116">顯示動作可能產生的參考訊息或錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="44cd1-116">Displays informational and error messages that the action might generate.</span></span>  
  
 <span data-ttu-id="44cd1-117">**Filter**</span><span class="sxs-lookup"><span data-stu-id="44cd1-117">**Filter**</span></span>  
 <span data-ttu-id="44cd1-118">選擇是否僅顯示錯誤、警告或成功的動作。</span><span class="sxs-lookup"><span data-stu-id="44cd1-118">Choose whether you want to display only errors, warnings, or successful actions.</span></span> <span data-ttu-id="44cd1-119">您可以選擇 [**顯示所有動作**]，以還原為預設顯示。</span><span class="sxs-lookup"><span data-stu-id="44cd1-119">You can revert to the default display by choosing **Show All Actions**.</span></span>  
  
 <span data-ttu-id="44cd1-120">**停止**</span><span class="sxs-lookup"><span data-stu-id="44cd1-120">**Stop**</span></span>  
 <span data-ttu-id="44cd1-121">如有必要，請使用 [**停止**] 按鈕來中斷操作。</span><span class="sxs-lookup"><span data-stu-id="44cd1-121">Interrupt the operation, if necessary, by using the **Stop** button.</span></span>  
  
 <span data-ttu-id="44cd1-122">**Report**</span><span class="sxs-lookup"><span data-stu-id="44cd1-122">**Report**</span></span>  
 <span data-ttu-id="44cd1-123">檢視結果的報表、將報表儲存至檔案、將報表複製到剪貼簿，或透過電子郵件傳送報表。</span><span class="sxs-lookup"><span data-stu-id="44cd1-123">View a report of the results, save the report to a file, copy the report to the clipboard, or send the report by e-mail.</span></span>  
  
  
