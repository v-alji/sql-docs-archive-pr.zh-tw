---
title: 匯入和匯出知識 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 12537c9d-31e4-40b0-a411-cb343abbe96a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6bd5c4f1acde5d25068ac19a7416069704793345
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686480"
---
# <a name="importing-and-exporting-knowledge"></a><span data-ttu-id="64092-102">匯入和匯出知識</span><span class="sxs-lookup"><span data-stu-id="64092-102">Importing and Exporting Knowledge</span></span>
  <span data-ttu-id="64092-103">您可以直接在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 應用程式中建立知識庫和定義域，也可以將知識匯入知識庫或從中匯出知識。</span><span class="sxs-lookup"><span data-stu-id="64092-103">You can create knowledge bases and domains directly in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application, or you can import knowledge into, or export it from, a knowledge base.</span></span> <span data-ttu-id="64092-104">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 應用程式中，您可以使用資料檔案進行匯入和匯出作業，或使用 Excel 檔案進行匯入作業。</span><span class="sxs-lookup"><span data-stu-id="64092-104">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application, you can use a data file for import and export operations, or an Excel file for import operations.</span></span> <span data-ttu-id="64092-105">使用的資料檔案是 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 所建立的加密檔案，副檔名為 .dqs。</span><span class="sxs-lookup"><span data-stu-id="64092-105">The data file used is an encrypted file that is created by [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) with a .dqs extension.</span></span> <span data-ttu-id="64092-106">由 Microsoft Excel 建立的檔案可以具有 .xlsx、.xls 或 .csv 的副檔名。</span><span class="sxs-lookup"><span data-stu-id="64092-106">The files created by Microsoft Excel can have an extension of .xlsx, .xls, or .csv.</span></span> <span data-ttu-id="64092-107">這些作業可讓您更有彈性地建置並共用執行資料清理和比對所用的知識。</span><span class="sxs-lookup"><span data-stu-id="64092-107">These operations give you more flexibility in building and sharing the knowledge that you use to perform data cleansing and matching.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="64092-108">您可以從命令提示字元執行 DQSInstaller.exe 檔案，一次將 *中的「所有」*[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 知識庫匯出至 DQS 備份檔案 (.dqsb)。</span><span class="sxs-lookup"><span data-stu-id="64092-108">You can export *all* the knowledge bases in your [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb) at once by running the DQSInstaller.exe file from the command prompt.</span></span> <span data-ttu-id="64092-109">同樣地，您也可以從命令提示字元執行 DQSInstaller.exe 檔案，一次將 DQS 備份檔案 (.dqsb) 中的「所有」 \*\* 知識庫匯入 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="64092-109">Similarly, you can import *all* the knowledge bases from a DQS backup file (.dqsb) to your [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] at once by running the DQSInstaller.exe file from the command prompt.</span></span> <span data-ttu-id="64092-110">如需有關執行此作業的詳細資訊，請參閱《DQS 安裝指南》中的＜ [使用 DQSInstaller.exe 匯出及匯入 DQS 知識庫](install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md) ＞。</span><span class="sxs-lookup"><span data-stu-id="64092-110">For information about doing so, see [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md) in the DQS installation guide.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64092-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="64092-111">In This Section</span></span>  
 <span data-ttu-id="64092-112">您可以執行下列匯入和匯出作業：</span><span class="sxs-lookup"><span data-stu-id="64092-112">You can perform the following import and export operations:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="64092-113">將知識庫中的定義域匯出至 .dqs 資料檔案</span><span class="sxs-lookup"><span data-stu-id="64092-113">Export a domain in a knowledge base to a .dqs data file</span></span>|[<span data-ttu-id="64092-114">將定義域匯出成 .dqs 檔案</span><span class="sxs-lookup"><span data-stu-id="64092-114">Export a Domain to a .dqs File</span></span>](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md)|  
|<span data-ttu-id="64092-115">將 .dqs 資料檔案中的定義域匯入現有的知識庫中</span><span class="sxs-lookup"><span data-stu-id="64092-115">Import a domain from a .dqs data file into an existing knowledge base</span></span>|[<span data-ttu-id="64092-116">從 .dqs 檔案匯入定義域</span><span class="sxs-lookup"><span data-stu-id="64092-116">Import a Domain from a .dqs File</span></span>](../../2014/data-quality-services/import-a-domain-from-a-dqs-file.md)|  
|<span data-ttu-id="64092-117">將整個知識庫匯出至 .dqs 資料檔案</span><span class="sxs-lookup"><span data-stu-id="64092-117">Export an entire knowledge base to a .dqs data file</span></span>|[<span data-ttu-id="64092-118">將知識庫匯出到 .dqs 檔案</span><span class="sxs-lookup"><span data-stu-id="64092-118">Export a Knowledge Base to a .dqs File</span></span>](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)|  
|<span data-ttu-id="64092-119">將整個知識庫匯入 .dqs 資料檔案中</span><span class="sxs-lookup"><span data-stu-id="64092-119">Import an entire knowledge base to a .dqs data file</span></span>|[<span data-ttu-id="64092-120">從 .dqs 檔案匯入知識庫</span><span class="sxs-lookup"><span data-stu-id="64092-120">Import a Knowledge Base from a .dqs File</span></span>](../../2014/data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)|  
|<span data-ttu-id="64092-121">將 Excel 檔案中的值匯入定義域中</span><span class="sxs-lookup"><span data-stu-id="64092-121">Import values from an Excel file into a domain</span></span>|[<span data-ttu-id="64092-122">將 Excel 檔案中的值匯入定義域中</span><span class="sxs-lookup"><span data-stu-id="64092-122">Import Values from an Excel File into a Domain</span></span>](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md)|  
|<span data-ttu-id="64092-123">將 Excel 檔案中的定義域匯入知識庫</span><span class="sxs-lookup"><span data-stu-id="64092-123">Import domains from an Excel file into a knowledge base</span></span>|[<span data-ttu-id="64092-124">在知識探索中匯入 Excel 檔案中的定義域</span><span class="sxs-lookup"><span data-stu-id="64092-124">Import Domains from an Excel File in Knowledge Discovery</span></span>](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md)|  
|<span data-ttu-id="64092-125">將清理期間蒐集的知識匯入知識庫中</span><span class="sxs-lookup"><span data-stu-id="64092-125">Import knowledge gathered during cleansing into a knowledge base</span></span>|[<span data-ttu-id="64092-126">將清理專案值匯入定義域中</span><span class="sxs-lookup"><span data-stu-id="64092-126">Import Cleansing Project Values into a Domain</span></span>](../../2014/data-quality-services/import-cleansing-project-values-into-a-domain.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="64092-127">相關工作</span><span class="sxs-lookup"><span data-stu-id="64092-127">Related Tasks</span></span>  
  
|<span data-ttu-id="64092-128">工作描述</span><span class="sxs-lookup"><span data-stu-id="64092-128">Task Description</span></span>|<span data-ttu-id="64092-129">主題</span><span class="sxs-lookup"><span data-stu-id="64092-129">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="64092-130">藉由執行知識探索以及以互動方式管理知識來建立知識庫</span><span class="sxs-lookup"><span data-stu-id="64092-130">Building a knowledge base by running knowledge discovery and interactively managing knowledge</span></span>|[<span data-ttu-id="64092-131">建立知識庫</span><span class="sxs-lookup"><span data-stu-id="64092-131">Building a Knowledge Base</span></span>](../../2014/data-quality-services/building-a-knowledge-base.md)|  
|<span data-ttu-id="64092-132">建立單一定義域，並將知識加入至定義域。</span><span class="sxs-lookup"><span data-stu-id="64092-132">Creating a single domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="64092-133">管理定義域</span><span class="sxs-lookup"><span data-stu-id="64092-133">Managing a Domain</span></span>](../../2014/data-quality-services/managing-a-domain.md)|  
|<span data-ttu-id="64092-134">建立複合定義域，並將知識加入至定義域。</span><span class="sxs-lookup"><span data-stu-id="64092-134">Creating a composite domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="64092-135">管理複合定義域</span><span class="sxs-lookup"><span data-stu-id="64092-135">Managing a Composite Domain</span></span>](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  
