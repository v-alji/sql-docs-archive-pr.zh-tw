---
title: 外部工具的引數 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- arguments [SQL Server Management Studio]
- external tools [SQL Server Management Studio]
ms.assetid: 3991c13a-f23f-450b-a2ba-19391c399735
author: stevestein
ms.author: sstein
ms.openlocfilehash: 71a7fb99eee3286d21a405e9564d046847406a1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606010"
---
# <a name="arguments-for-external-tools"></a><span data-ttu-id="a5e5f-102">外部工具的引數</span><span class="sxs-lookup"><span data-stu-id="a5e5f-102">Arguments for External Tools</span></span>
  <span data-ttu-id="a5e5f-103">引數是 Studio 環境提供的變數，適用於從 [工具]  功能表中啟動外部工具之時。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-103">Arguments are variables that the Studio environment supplies values for when an external tool is launched from the **Tools** menu.</span></span> <span data-ttu-id="a5e5f-104">您可以使用 [外部工具] 對話方塊，將 [記事本] 之類的外部工具加入 [工具] 功能表中。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-104">External tools such as Notepad can be added to the **Tools** menu using the **External Tools** dialog box.</span></span>  
  
 <span data-ttu-id="a5e5f-105">下表列出外部工具的引數。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-105">The following table lists arguments for external tools.</span></span>  
  
|<span data-ttu-id="a5e5f-106">名稱</span><span class="sxs-lookup"><span data-stu-id="a5e5f-106">Name</span></span>|<span data-ttu-id="a5e5f-107">引數</span><span class="sxs-lookup"><span data-stu-id="a5e5f-107">Argument</span></span>|<span data-ttu-id="a5e5f-108">描述</span><span class="sxs-lookup"><span data-stu-id="a5e5f-108">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="a5e5f-109">**項目路徑**</span><span class="sxs-lookup"><span data-stu-id="a5e5f-109">**Item Path**</span></span>|<span data-ttu-id="a5e5f-110">$(ItemPath)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-110">$(ItemPath)</span></span>|<span data-ttu-id="a5e5f-111">目前來源的完整檔案名稱 (定義為磁碟機 + 路徑 + 檔案名稱)；如果非來源窗格在作用中，便是空白。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-111">The complete file name of the current source (defined as drive + path + file name); blank if a non-source window is active.</span></span>|  
|<span data-ttu-id="a5e5f-112">**項目目錄**</span><span class="sxs-lookup"><span data-stu-id="a5e5f-112">**Item Directory**</span></span>|<span data-ttu-id="a5e5f-113">$(ItemDir)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-113">$(ItemDir)</span></span>|<span data-ttu-id="a5e5f-114">目前來源的目錄 (定義為磁碟機 + 路徑)；如果非來源窗格在作用中，便是空白。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-114">The directory of the current source (defined as drive + path); blank if a non-source window is active.</span></span>|  
|<span data-ttu-id="a5e5f-115">**項目檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="a5e5f-115">**Item File Name**</span></span>|<span data-ttu-id="a5e5f-116">$(ItemFilename)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-116">$(ItemFilename)</span></span>|<span data-ttu-id="a5e5f-117">目前來源的檔案名稱 (定義為檔案名稱)；如果非來源窗格在作用中，便是空白。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-117">The file name of the current source (defined as file name); blank if a non-source window is active.</span></span>|  
|<span data-ttu-id="a5e5f-118">**項目副檔名**</span><span class="sxs-lookup"><span data-stu-id="a5e5f-118">**Item extension**</span></span>|<span data-ttu-id="a5e5f-119">$(ItemExt)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-119">$(ItemExt)</span></span>|<span data-ttu-id="a5e5f-120">目前來源的副檔名。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-120">The file name extension of the current source.</span></span>|  
|<span data-ttu-id="a5e5f-121">**目前第** <sup>1</sup>行</span><span class="sxs-lookup"><span data-stu-id="a5e5f-121">**Current Line** <sup>1</sup></span></span>|<span data-ttu-id="a5e5f-122">$(CurLine)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-122">$(CurLine)</span></span>|<span data-ttu-id="a5e5f-123">在編輯器中，游標所在的目前這一行位置。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-123">The current line position of the cursor in the editor.</span></span>|  
|<span data-ttu-id="a5e5f-124">**目前資料行**1</span><span class="sxs-lookup"><span data-stu-id="a5e5f-124">**Current Column**1</span></span>|<span data-ttu-id="a5e5f-125">$(CurCol)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-125">$(CurCol)</span></span>|<span data-ttu-id="a5e5f-126">在編輯器中，游標所在的目前資料行位置。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-126">The current column position of the cursor in the editor.</span></span>|  
|<span data-ttu-id="a5e5f-127">**目前文字**1</span><span class="sxs-lookup"><span data-stu-id="a5e5f-127">**Current Text**1</span></span>|<span data-ttu-id="a5e5f-128">$(CurText)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-128">$(CurText)</span></span>|<span data-ttu-id="a5e5f-129">目前的文字 (在目前游標位置之下的文字，如果選擇了某單行，便是這一行)。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-129">The current text (the word under the current cursor position, or a single-line selection, if there is one).</span></span>|  
|<span data-ttu-id="a5e5f-130">**目標路徑**</span><span class="sxs-lookup"><span data-stu-id="a5e5f-130">**Target Path**</span></span>|<span data-ttu-id="a5e5f-131">$(TargetPath)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-131">$(TargetPath)</span></span>|<span data-ttu-id="a5e5f-132">目標的完整檔案名稱 (定義為磁碟機 + 路徑 + 檔案名稱)。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-132">The complete file name of the target (defined as drive + path + file name).</span></span>|  
|<span data-ttu-id="a5e5f-133">**目標目錄**</span><span class="sxs-lookup"><span data-stu-id="a5e5f-133">**Target Directory**</span></span>|<span data-ttu-id="a5e5f-134">$(TargetDir)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-134">$(TargetDir)</span></span>|<span data-ttu-id="a5e5f-135">目標的目錄。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-135">The directory of the target.</span></span>|  
|<span data-ttu-id="a5e5f-136">**目標名稱**</span><span class="sxs-lookup"><span data-stu-id="a5e5f-136">**Target Name**</span></span>|<span data-ttu-id="a5e5f-137">$(TargetName)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-137">$(TargetName)</span></span>|<span data-ttu-id="a5e5f-138">目標的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-138">The file name of the target.</span></span>|  
|<span data-ttu-id="a5e5f-139">**目標副檔名**</span><span class="sxs-lookup"><span data-stu-id="a5e5f-139">**Target Extension**</span></span>|<span data-ttu-id="a5e5f-140">$(TargetExt)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-140">$(TargetExt)</span></span>|<span data-ttu-id="a5e5f-141">目標的副檔名。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-141">The file name extension of the target.</span></span>|  
|<span data-ttu-id="a5e5f-142">**專案目錄**</span><span class="sxs-lookup"><span data-stu-id="a5e5f-142">**Project Directory**</span></span>|<span data-ttu-id="a5e5f-143">$(ProjDir)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-143">$(ProjDir)</span></span>|<span data-ttu-id="a5e5f-144">目前專案的目錄 (定義為磁碟機 + 路徑)。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-144">The directory of the current project (defined as drive + path).</span></span>|  
|<span data-ttu-id="a5e5f-145">**專案檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="a5e5f-145">**Project File Name**</span></span>|<span data-ttu-id="a5e5f-146">$(ProjFileName)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-146">$(ProjFileName)</span></span>|<span data-ttu-id="a5e5f-147">目標專案的檔案名稱 (定義為磁碟機 + 路徑 + 檔案名稱)。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-147">The file name of the current project (defined as drive + path + file name).</span></span>|  
|<span data-ttu-id="a5e5f-148">**方案目錄**</span><span class="sxs-lookup"><span data-stu-id="a5e5f-148">**Solution Directory**</span></span>|<span data-ttu-id="a5e5f-149">$(SolutionDir)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-149">$(SolutionDir)</span></span>|<span data-ttu-id="a5e5f-150">目前方案的目錄 (定義為磁碟機 + 路徑)。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-150">The directory of the current solution (defined as drive + path).</span></span>|  
|<span data-ttu-id="a5e5f-151">**方案檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="a5e5f-151">**Solution File Name**</span></span>|<span data-ttu-id="a5e5f-152">$(SolutionFileName)</span><span class="sxs-lookup"><span data-stu-id="a5e5f-152">$(SolutionFileName)</span></span>|<span data-ttu-id="a5e5f-153">目標方案的檔案名稱 (定義為磁碟機 + 路徑 + 檔案名稱)。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-153">The file name of the current solution (defined as drive + path + file name).</span></span>|  
  
 <span data-ttu-id="a5e5f-154"><sup>1</sup>目前這一行、目前的資料行或目前的文字是以文字編輯器中游標的位置為基礎，如狀態列所示。</span><span class="sxs-lookup"><span data-stu-id="a5e5f-154"><sup>1</sup> The current line, current column, or current text is based on the position of the cursor in the text editor as shown in the status bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e5f-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5e5f-155">See Also</span></span>  
 <span data-ttu-id="a5e5f-156">[外部工具對話方塊](external-tools-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="a5e5f-156">[External Tools Dialog Box](external-tools-dialog-box.md) </span></span>  
 [<span data-ttu-id="a5e5f-157">一般使用者介面元素</span><span class="sxs-lookup"><span data-stu-id="a5e5f-157">General User Interface Elements</span></span>](general-user-interface-elements.md)  
  
  
