---
title: 在 Management Studio 中建立 Analysis Services 腳本 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services objects, scripts
- objects [Analysis Services], scripts
- scripts [Analysis Services], objects
ms.assetid: 4f1b965c-9ca6-427b-8f4d-0ce1eea7c0fe
author: minewiskan
ms.author: owend
ms.openlocfilehash: bb380e271510ea5a35860d4850bfaeed3aad8cf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698812"
---
# <a name="create-analysis-services-scripts-in-management-studio"></a><span data-ttu-id="dc547-102">在 Management Studio 中建立 Analysis Services 指令碼</span><span class="sxs-lookup"><span data-stu-id="dc547-102">Create Analysis Services Scripts in Management Studio</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="dc547-103">包含指令碼產生功能、範本和編輯器，您可以使用它們來編寫 Analysis Services 物件和工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="dc547-103">includes script generation features, templates, and editors that you can use to script Analysis Services objects and tasks.</span></span>  
  
## <a name="script-analysis-services-tasks-in-management-studio"></a><span data-ttu-id="dc547-104">在 Management Studio 中編寫 Analysis Services 工作的指令碼</span><span class="sxs-lookup"><span data-stu-id="dc547-104">Script Analysis Services Tasks in Management Studio</span></span>  
 <span data-ttu-id="dc547-105">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中編寫工作指令碼，是在工作導向的對話方塊中按一下其中一個指令碼選項來完成。</span><span class="sxs-lookup"><span data-stu-id="dc547-105">Scripting tasks in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is accomplished by clicking one of the Script options in a task-oriented dialog box.</span></span> <span data-ttu-id="dc547-106">用來執行備份或還原資料庫、處理物件或設計彙總等工作的所有對話方塊，在對話方塊頂端都包含指令碼選項。</span><span class="sxs-lookup"><span data-stu-id="dc547-106">All of the dialog boxes that you use to perform tasks such as backup or restore database, process an object, or design an aggregation, include a Script option at the top of the dialog box.</span></span> <span data-ttu-id="dc547-107">選取其中一個選項，會根據對話方塊中的資訊和設定來產生 XMLA 指令碼。</span><span class="sxs-lookup"><span data-stu-id="dc547-107">Selecting one of these options generates an XMLA script based on the information and settings in the dialog box.</span></span>  
  
 <span data-ttu-id="dc547-108">根據預設，產生的指令碼放在 XMLA 查詢編輯器中，但您也可以展開指令碼選項清單，將指令碼導向至 Windows 剪貼簿或檔案。</span><span class="sxs-lookup"><span data-stu-id="dc547-108">By default, the script is generated and placed in an XMLA query editor, but you can also expand the Script option list to direct the script to the Windows Clipboard or a file.</span></span>  
  
#### <a name="to-script-an-analysis-services-task"></a><span data-ttu-id="dc547-109">若要編寫 Analysis Services 工作的指令碼</span><span class="sxs-lookup"><span data-stu-id="dc547-109">To script an Analysis Services task</span></span>  
  
1.  <span data-ttu-id="dc547-110">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="dc547-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="dc547-111">以滑鼠右鍵按一下資料庫，然後按一下 [備份]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dc547-111">Right-click a database and click **Backup**.</span></span> <span data-ttu-id="dc547-112">這會開啟 [備份資料庫] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="dc547-112">This opens the Backup Database dialog box.</span></span> <span data-ttu-id="dc547-113">指定備份檔案的名稱，並選擇要用於此備份的選項。</span><span class="sxs-lookup"><span data-stu-id="dc547-113">Specify a backup file name and choose the options you want for this backup.</span></span>  
  
3.  <span data-ttu-id="dc547-114">按一下對話方塊頂端的 [指令碼]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dc547-114">Click **Script** at the top of the dialog box.</span></span> <span data-ttu-id="dc547-115">指令碼功能是 Management Studio 中所有以工作為基礎的對話方塊的一部分。</span><span class="sxs-lookup"><span data-stu-id="dc547-115">The Script feature is part of all task-based dialog boxes in Management Studio.</span></span> <span data-ttu-id="dc547-116">它有下列選項：[編寫動作的指令碼至新增查詢視窗]\*\*\*\* 可開啟查詢編輯器視窗、[編寫動作的指令碼至檔案]\*\*\*\* 可將 XMLA 指令碼儲存至檔案，或 [編寫動作的指令碼至剪貼簿]\*\*\*\* 可將 XMLA 指令碼儲存至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="dc547-116">It has the following options: **Script Action to New Query Window** to open the query editor window, **Script Action to File** to save the XMLA script to a file, or **Script Action to Clipboard** to save the XMLA script to the Clipboard.</span></span>  
  
     <span data-ttu-id="dc547-117">請注意，Analysis Services 指令碼不支援 Management Studio 中列為指令碼選項的 [編寫動作的指令碼至作業]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="dc547-117">Note that the **Script Action to Job** option that is listed as a script option in Management Studio is not supported for Analysis Services scripts.</span></span>  
  
4.  <span data-ttu-id="dc547-118">如果您選取預設選項 [編寫動作的指令碼至新增查詢視窗]\*\*\*\*，產生的指令碼會放在 XMLA 查詢視窗中。</span><span class="sxs-lookup"><span data-stu-id="dc547-118">If you select the default option, **Script Action to New Query Window**, a generated script is placed in an XMLA query window.</span></span>  
  
     <span data-ttu-id="dc547-119">您現在可以關閉 [備份資料庫] 對話方塊，然後編輯或直接執行 XMLA 指令碼。</span><span class="sxs-lookup"><span data-stu-id="dc547-119">You can now close the Backup Database dialog box and edit or run the XMLA script directly.</span></span>  
  
## <a name="script-analysis-services-objects-in-management-studio"></a><span data-ttu-id="dc547-120">在 Management Studio 中編寫 Analysis Services 物件的指令碼</span><span class="sxs-lookup"><span data-stu-id="dc547-120">Script Analysis Services Objects in Management Studio</span></span>  
 <span data-ttu-id="dc547-121">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中編寫物件指令碼，是在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件，然後選取 [CREATE 至]\*\*\*\*、[ALTER 至]\*\*\*\* 或 [DELETE 至]\*\*\*\* 來完成。</span><span class="sxs-lookup"><span data-stu-id="dc547-121">Scripting objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is accomplished by right-clicking an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and selecting either **Create to**, **Alter to**, or **Delete to**.</span></span> <span data-ttu-id="dc547-122">每一個這些選項可引導至視窗或檔案，但不論指令碼引導至何處，它將以 DDL 指令碼格式出現在 XMLA 包裝函數中。</span><span class="sxs-lookup"><span data-stu-id="dc547-122">Each of these options can be directed to a window or a file, but regardless of where the script is directed to, it will come in the form of a DDL script in an XMLA wrapper.</span></span> <span data-ttu-id="dc547-123">這類指令碼的一大好處，就是它們可以對任何您指向的伺服器執行。</span><span class="sxs-lookup"><span data-stu-id="dc547-123">One great advantage to such scripts is that they can be run against any server you point them at.</span></span> <span data-ttu-id="dc547-124">同時，可針對物件的大量建構、改變或刪除來反覆變更及執行指令碼的名稱。</span><span class="sxs-lookup"><span data-stu-id="dc547-124">Also, names in the scripts can be changed and run on an iterative basis for mass construction, alteration, or deletion of objects.</span></span>  
  
 <span data-ttu-id="dc547-125">可編寫指令碼的物件包含 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫的元素，包含資料來源、資料來源檢視、Cube、維度、採礦結構和角色。</span><span class="sxs-lookup"><span data-stu-id="dc547-125">Objects that you can script include the elements of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, including data sources, data source views, cubes, dimensions, mining structures, and roles.</span></span>  
  
 <span data-ttu-id="dc547-126">必要條件包含了解 XML for Analysis (XMLA)。</span><span class="sxs-lookup"><span data-stu-id="dc547-126">Prerequisites include an understanding of XML for Analysis (XMLA).</span></span> <span data-ttu-id="dc547-127">幸好 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 有自動建立 XMLA 指令碼的功能，可用來建立 Cube 等物件。</span><span class="sxs-lookup"><span data-stu-id="dc547-127">Fortunately, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] has a feature that automatically creates the XMLA script required to create objects, such as cubes.</span></span> <span data-ttu-id="dc547-128">此自動化功能有助於縮短 XMLA 的學習曲線。</span><span class="sxs-lookup"><span data-stu-id="dc547-128">This automation feature helps reduce the learning curve for XMLA.</span></span> <span data-ttu-id="dc547-129">如需如何使用 XMLA 的詳細資訊，請參閱 [在 Analysis Services 中使用 XMLA 進行開發](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="dc547-129">For more information about how to use XMLA, see [Developing with XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).</span></span> <span data-ttu-id="dc547-130">如需如何使用 XMLA 的詳細資訊，請參閱 [在 Analysis Services 中使用 XMLA 進行開發](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="dc547-130">For more information about how to use XMLA, see [Developing with XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dc547-131">編寫 Role 物件的指令碼時，請注意安全性權限包含在它們所保護的物件中，而非與它們相關聯的安全性角色。</span><span class="sxs-lookup"><span data-stu-id="dc547-131">When scripting the Role Object, be aware that security permissions are contained by the objects they secure rather than with the security role with which they are associated.</span></span>  
  
#### <a name="to-script-analysis-services-objects"></a><span data-ttu-id="dc547-132">若要編寫 Analysis Services 物件的指令碼</span><span class="sxs-lookup"><span data-stu-id="dc547-132">To script Analysis Services objects</span></span>  
  
1.  <span data-ttu-id="dc547-133">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="dc547-133">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="dc547-134">尋找您要建立指令碼的物件，來建立、改變或刪除物件。</span><span class="sxs-lookup"><span data-stu-id="dc547-134">Locate the object for which you want to create a script that either creates, alters, or deletes objects.</span></span>  
  
3.  <span data-ttu-id="dc547-135">以滑鼠右鍵按一下物件，指向 [編寫 Cube 的指令碼為]\*\*\*\*，然後指向 [CREATE 至]\*\*\*\*、[ALTER 至]\*\*\*\* 或 [DELETE 至]\*\*\*\*，再按下列其中一個選項：[新增查詢編輯器視窗]\*\*\*\* 可開啟查詢編輯器視窗、[檔案]\*\*\*\* 可將 XMLA 指令碼儲存至檔案，或 [剪貼簿]\*\*\*\* 可將 XMLA 指令碼儲存至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="dc547-135">Right-click the object, point to **Script Cube as**, point to **CREATE To**, **ALTER To**, or **Delete To**, and then click one of the following options: **New Query Editor Window** to open the query editor window, **File** to save the XMLA script to a file, or **Clipboard** to save the XMLA script to the Clipboard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dc547-136">一般而言，如果您要建立檔案的多個不同版本，請選取 [檔案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dc547-136">Typically, you would select **File** if you want to create multiple different versions of the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc547-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc547-137">See Also</span></span>  
 <span data-ttu-id="dc547-138">[在 Analysis Services 中編寫管理工作的腳本](../script-administrative-tasks-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="dc547-138">[Script Administrative Tasks in Analysis Services](../script-administrative-tasks-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="dc547-139">XMLA 查詢編輯器 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="dc547-139">XMLA Query Editor &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../xmla-query-editor-analysis-services-multidimensional-data.md)  
  
  
