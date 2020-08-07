---
title: 大量匯入或大量匯出的資料格式 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], choosing
- bulk importing [SQL Server], data formats
ms.assetid: 73fe6741-9437-4b26-b030-28b863e74399
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b92ac8c038362ff18a1459a8bf3c55b6b596a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584505"
---
# <a name="data-formats-for-bulk-import-or-bulk-export-sql-server"></a><span data-ttu-id="795ba-102">大量匯入或大量匯出的資料格式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="795ba-102">Data Formats for Bulk Import or Bulk Export (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="795ba-103">可以接受字元資料格式或原生二進位資料格式的資料。</span><span class="sxs-lookup"><span data-stu-id="795ba-103">can accept data in character data format or native binary data format.</span></span> <span data-ttu-id="795ba-104">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和其他應用程式 (例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel) 之間，或其他資料庫伺服器 (例如 Oracle 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) 之間移動資料時，請使用字元格式。</span><span class="sxs-lookup"><span data-stu-id="795ba-104">Use character format when you move data between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and another application (such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel) or another database server (such as Oracle or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).</span></span> <span data-ttu-id="795ba-105">只有當您在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體之間傳送資料時，才能使用原生格式。</span><span class="sxs-lookup"><span data-stu-id="795ba-105">You can use native format only when you transfer data between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="795ba-106">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="795ba-106">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="795ba-107">大量匯入或匯出的資料格式</span><span class="sxs-lookup"><span data-stu-id="795ba-107">Data Formats for Bulk Import or Export</span></span>](#ComponentsAndConcepts)  
  
-   [<span data-ttu-id="795ba-108">相關工作</span><span class="sxs-lookup"><span data-stu-id="795ba-108">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="data-formats-for-bulk-import-or-export"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="795ba-109">大量匯入或匯出的資料格式</span><span class="sxs-lookup"><span data-stu-id="795ba-109">Data Formats for Bulk Import or Export</span></span>  
 <span data-ttu-id="795ba-110">下表根據資料的呈現方式和作業的來源或目標，指出一般適合使用的資料格式。</span><span class="sxs-lookup"><span data-stu-id="795ba-110">The following table indicates what data format is generally appropriate to use depending on how the data is represented and the source or target of the operation.</span></span>  
  
|<span data-ttu-id="795ba-111">作業</span><span class="sxs-lookup"><span data-stu-id="795ba-111">Operation</span></span>|<span data-ttu-id="795ba-112">原生</span><span class="sxs-lookup"><span data-stu-id="795ba-112">Native</span></span>|<span data-ttu-id="795ba-113">Unicode 原生</span><span class="sxs-lookup"><span data-stu-id="795ba-113">Unicode native</span></span>|<span data-ttu-id="795ba-114">字元</span><span class="sxs-lookup"><span data-stu-id="795ba-114">Character</span></span>|<span data-ttu-id="795ba-115">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="795ba-115">Unicode character</span></span>|  
|---------------|------------|--------------------|---------------|-----------------------|  
|<span data-ttu-id="795ba-116">使用不含任何擴充或雙位元組字集 (DBCS) 字元的資料檔，在多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之間進行大量傳送資料。</span><span class="sxs-lookup"><span data-stu-id="795ba-116">Bulk transfers of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that does not contain any extended or double-byte character set (DBCS) characters.</span></span> <span data-ttu-id="795ba-117">除非已使用格式檔案，否則必須以相同的方式定義這些資料表。</span><span class="sxs-lookup"><span data-stu-id="795ba-117">Unless a format file is used, these tables must be identically defined.</span></span>|<span data-ttu-id="795ba-118">是<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="795ba-118">Yes<sup>1</sup></span></span>|-|-|-|  
|<span data-ttu-id="795ba-119">若為 `sql_variant` 資料行，使用原生資料格式是最佳方法，因為原生資料格式會保留每個 `sql_variant` 值的中繼資料，但字元或 Unicode 格式則不會。</span><span class="sxs-lookup"><span data-stu-id="795ba-119">For `sql_variant` columns, use of native data format is best, because native data format preserves the metadata for each `sql_variant` value, unlike character or Unicode formats.</span></span>|<span data-ttu-id="795ba-120">是</span><span class="sxs-lookup"><span data-stu-id="795ba-120">Yes</span></span>|-|-|-|  
|<span data-ttu-id="795ba-121">使用含有擴充或 DBCS 字元的資料檔，在多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之間進行大量傳送資料。</span><span class="sxs-lookup"><span data-stu-id="795ba-121">Bulk transfers of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended or DBCS characters.</span></span>|-|<span data-ttu-id="795ba-122">是</span><span class="sxs-lookup"><span data-stu-id="795ba-122">Yes</span></span>|-|-|  
|<span data-ttu-id="795ba-123">從其他程式所產生的文字檔，大量匯入資料。</span><span class="sxs-lookup"><span data-stu-id="795ba-123">Bulk import of data from a text file that is generated by another program.</span></span>|-|-|<span data-ttu-id="795ba-124">是</span><span class="sxs-lookup"><span data-stu-id="795ba-124">Yes</span></span>|-|  
|<span data-ttu-id="795ba-125">將資料大量匯出至文字檔，以便使用於另一個程式之中。</span><span class="sxs-lookup"><span data-stu-id="795ba-125">Bulk export of data to a text file that is to be used in another program.</span></span>|-|-|<span data-ttu-id="795ba-126">是</span><span class="sxs-lookup"><span data-stu-id="795ba-126">Yes</span></span>|-|  
|<span data-ttu-id="795ba-127">使用含有 Unicode 資料但不含擴充或 DBCS 字元的資料檔，在多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之間進行大量傳送資料。</span><span class="sxs-lookup"><span data-stu-id="795ba-127">Bulk transfers of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains Unicode data and does not contain any extended or DBCS characters.</span></span>|-|-|-|<span data-ttu-id="795ba-128">是</span><span class="sxs-lookup"><span data-stu-id="795ba-128">Yes</span></span>|  
  
 <span data-ttu-id="795ba-129"><sup>1</sup> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用**bcp**時，從大量匯出資料的最快方法。</span><span class="sxs-lookup"><span data-stu-id="795ba-129"><sup>1</sup> Fastest method for the bulk export of data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when using **bcp**.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="795ba-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="795ba-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="795ba-131">使用原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="795ba-131">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="795ba-132">使用字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="795ba-132">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="795ba-133">使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="795ba-133">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="795ba-134">使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="795ba-134">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="795ba-135">從舊版 SQL Server 匯入原生與字元格式資料</span><span class="sxs-lookup"><span data-stu-id="795ba-135">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="795ba-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="795ba-136">See Also</span></span>  
 <span data-ttu-id="795ba-137">[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="795ba-137">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 [<span data-ttu-id="795ba-138">使用 bcp 指定相容性的資料格式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="795ba-138">Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;</span></span>](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)  
  
  
