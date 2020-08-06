---
title: 產生指令碼
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 9711c617-3c68-4e5a-aea3-befc64d51524
author: rothja
ms.author: jroth
ms.openlocfilehash: 199d5e0c98d220861ee0dfb48a44a71675d8ba87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606221"
---
# <a name="generate-scripts-sql-server-management-studio"></a><span data-ttu-id="c5f58-102">產生指令碼 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="c5f58-102">Generate Scripts (SQL Server Management Studio)</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="c5f58-103">提供兩種產生 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼的機制。</span><span class="sxs-lookup"><span data-stu-id="c5f58-103">provides two mechanisms for generating [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="c5f58-104">您可以使用 [**產生和發佈腳本] Wizard**來建立多個物件的腳本。</span><span class="sxs-lookup"><span data-stu-id="c5f58-104">You can create scripts for multiple objects by using the **Generate and Publish Scripts Wizard.**.</span></span> <span data-ttu-id="c5f58-105">您也可以使用**物件總管**中的 [編寫組件的指令碼為] 功能表，為個別物件或多個物件產生指令碼。</span><span class="sxs-lookup"><span data-stu-id="c5f58-105">You can also generate a script for individual objects or multiple objects by using the **Script as** menu in **Object Explorer**.</span></span>  
  
1.  <span data-ttu-id="c5f58-106">**選擇方法：**  [[產生和發佈指令碼精靈]](#GenPubScriptWiz)、[物件總管的 [編寫組件的指令碼為] 功能表](#OEScriptAsMenu)</span><span class="sxs-lookup"><span data-stu-id="c5f58-106">**Choose a method:**  [Generate and Publish Scripts Wizard](#GenPubScriptWiz), [Object Explorer Script As Menu](#OEScriptAsMenu)</span></span>  
  
2.  <span data-ttu-id="c5f58-107">**使用 [編寫組件的指令碼為] 功能表**  [編寫單一物件的指令碼](#ScriptSingleObject)、 [使用物件總管編寫兩個物件的指令碼](#ScriptTwoObjectsOE)、 [使用物件總管詳細資料編寫兩個物件的指令碼](#ScriptTwoObjectsOED)</span><span class="sxs-lookup"><span data-stu-id="c5f58-107">**To use the Script As menu:**  [Script a Single Object](#ScriptSingleObject), [Script Two Objects Using Object Explorer](#ScriptTwoObjectsOE), [Script Two Objects Using Object Explorer Details](#ScriptTwoObjectsOED)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="c5f58-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="c5f58-108">Before You Begin</span></span>  
 <span data-ttu-id="c5f58-109">選擇最符合您需求的機制。</span><span class="sxs-lookup"><span data-stu-id="c5f58-109">Choose the mechanism that best meets your requirements.</span></span>  
  
###  <a name="generate-and-publish-scripts-wizard"></a><a name="GenPubScriptWiz"></a> <span data-ttu-id="c5f58-110">[產生和發佈指令碼精靈]</span><span class="sxs-lookup"><span data-stu-id="c5f58-110">Generate and Publish Scripts Wizard</span></span>  
 <span data-ttu-id="c5f58-111">使用 [產生和發佈指令碼精靈]，為多個物件建立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="c5f58-111">Use the **Generate and Publish Scripts Wizard** to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] script for many objects.</span></span> <span data-ttu-id="c5f58-112">此精靈會產生資料庫中所有物件的指令碼，或是您所選取之物件子集的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c5f58-112">The wizard generates a script of all the objects in a database, or a subset of the objects that you select.</span></span> <span data-ttu-id="c5f58-113">此精靈具有許多適用於指令碼的選項，例如是否要包含權限、定序及條件約束等。</span><span class="sxs-lookup"><span data-stu-id="c5f58-113">The wizard has many options for your scripts, such as whether to include permissions, collation, constraints, and so on.</span></span> <span data-ttu-id="c5f58-114">如需有關使用此精靈的指示，請參閱 [產生和發佈指令碼精靈](generate-and-publish-scripts-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="c5f58-114">For instructions on using the wizard, see [Generate and Publish Scripts Wizard](generate-and-publish-scripts-wizard.md).</span></span>  
  
###  <a name="object-explorer-script-as-menu"></a><a name="OEScriptAsMenu"></a> <span data-ttu-id="c5f58-115">物件總管的 [編寫組件的指令碼為] 功能表</span><span class="sxs-lookup"><span data-stu-id="c5f58-115">Object Explorer Script As Menu</span></span>  
 <span data-ttu-id="c5f58-116">您可以使用物件總管的 [編寫組件的指令碼為]\*\*\*\* 功能表，編寫單一物件、多個物件或單一物件之多個陳述式的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c5f58-116">You can use the **Object Explorer Script as** menu to script a single object, script multiple objects, or script multible statements for a single objects.</span></span> <span data-ttu-id="c5f58-117">您可以選擇數種指令碼的其中一種，例如建立、變更或卸除物件。</span><span class="sxs-lookup"><span data-stu-id="c5f58-117">You can choose one of several types of scripts; for example to create, alter, or drop the object.</span></span> <span data-ttu-id="c5f58-118">您可以將指令碼儲存到 [查詢編輯器] 視窗，或是儲存到檔案或剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="c5f58-118">You can save the script in a Query Editor window, to a file, or to the Clipboard.</span></span> <span data-ttu-id="c5f58-119">指令碼是使用 Unicode 格式所建立。</span><span class="sxs-lookup"><span data-stu-id="c5f58-119">The script is created in Unicode format.</span></span>  
  
##  <a name="to-generate-a-script-of-a-single-object"></a><a name="ScriptSingleObject"></a> <span data-ttu-id="c5f58-120">產生單一物件的指令碼</span><span class="sxs-lookup"><span data-stu-id="c5f58-120">To generate a script of a single object</span></span>  
 <span data-ttu-id="c5f58-121">**編寫單一物件的指令碼**</span><span class="sxs-lookup"><span data-stu-id="c5f58-121">**To script a single object**</span></span>  
  
1.  <span data-ttu-id="c5f58-122">在 [物件總管] 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="c5f58-122">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="c5f58-123">展開 [資料庫]，然後展開含有要編寫指令碼之物件的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c5f58-123">Expand **Databases**, and then expand the database containing the object to be scripted.</span></span>  
  
3.  <span data-ttu-id="c5f58-124">展開物件的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="c5f58-124">Expand the category of the object.</span></span> <span data-ttu-id="c5f58-125">例如，展開 [資料表] 或 [檢視表] 節點。</span><span class="sxs-lookup"><span data-stu-id="c5f58-125">For example, expand the **Tables** or **Views** node.</span></span>  
  
4.  <span data-ttu-id="c5f58-126">以滑鼠右鍵按一下物件，並指向 [**編寫腳本 \<object type> 為**]，例如，指向 [**編寫資料表的腳本為**]。</span><span class="sxs-lookup"><span data-stu-id="c5f58-126">Right-click the object, point to **Script \<object type> as**, For example, point to **Script Table as**.</span></span>  
  
5.  <span data-ttu-id="c5f58-127">指向指令碼類型，例如 [CREATE 至] 或 [ALTER 至]。</span><span class="sxs-lookup"><span data-stu-id="c5f58-127">Point to the script type, such as **Create to** or **Alter to**.</span></span>  
  
6.  <span data-ttu-id="c5f58-128">選取儲存指令碼的位置，例如 [新增查詢編輯器視窗] 或 [剪貼簿]。</span><span class="sxs-lookup"><span data-stu-id="c5f58-128">Select the location to save the script, such as **New Query Editor Window** or **Clipboard**.</span></span>  
  
##  <a name="to-generate-a-script-of-two-objects-using-object-explorer"></a><a name="ScriptTwoObjectsOE"></a><span data-ttu-id="c5f58-129">若要使用物件總管產生兩個物件的腳本</span><span class="sxs-lookup"><span data-stu-id="c5f58-129">To generate a script of two objects using Object Explorer</span></span>  
 <span data-ttu-id="c5f58-130">**使用物件總管編寫兩個物件的指令碼**</span><span class="sxs-lookup"><span data-stu-id="c5f58-130">**To script two objects using Object Explorer**</span></span>  
  
 <span data-ttu-id="c5f58-131">有時候，您可能會希望指令碼有多個選項，例如先卸除程序，再建立程序，或先建立資料表，再變更資料表。</span><span class="sxs-lookup"><span data-stu-id="c5f58-131">Sometimes you may want a script with multiple options, such as drop a procedure and then create a procedure, or create a table and then alter a table.</span></span> <span data-ttu-id="c5f58-132">如果您需要建立一個參考不同類型之物件 (例如資料表、檢視表及預存程序) 的指令碼，也可以使用下列程序以產生多個物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c5f58-132">The processes below for generating scripts of multiple objects also work if you need to create a script that references different types of objects, such as tables, views, and stored procedures.</span></span>  
  
1.  <span data-ttu-id="c5f58-133">在 [物件總管] 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="c5f58-133">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="c5f58-134">展開 [資料庫]，然後展開含有要編寫指令碼之物件的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c5f58-134">Expand **Databases**, and then expand the database containing the objects to be scripted.</span></span>  
  
3.  <span data-ttu-id="c5f58-135">以滑鼠右鍵按一下要編寫腳本的第一個物件，指向 [**編寫腳本 \<object type> 為**]，然後在 [**另存**新檔] 選項中選擇 [追加**查詢編輯器] 視窗**做為輸出目的地。</span><span class="sxs-lookup"><span data-stu-id="c5f58-135">Right-click the first object to be scripted, point to **Script \<object type> as**, and in the **Save as** selections chooses **New Query Editor Window** as the output destination.</span></span>  
  
4.  <span data-ttu-id="c5f58-136">導覽至您想要編寫指令碼的第二個物件。</span><span class="sxs-lookup"><span data-stu-id="c5f58-136">Navigate to the second object you want to script.</span></span>  
  
5.  <span data-ttu-id="c5f58-137">以滑鼠右鍵按一下物件，並指向 [**編寫腳本 \<object type> 為**]，然後在 [**另存**新檔] 選項中選擇 [**剪貼**簿] 做為輸出目的地。</span><span class="sxs-lookup"><span data-stu-id="c5f58-137">Right-click the object, point to **Script \<object type> as**, and in the **Save as** selections chooses **Clipboard** as the output destination.</span></span>  
  
6.  <span data-ttu-id="c5f58-138">在針對第一個物件開啟的 [查詢編輯器] 視窗中，從剪貼簿貼上第二個物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c5f58-138">In the Query Editor window opened for the first object, paste the script for the second object from the clipboard.</span></span>  
  
##  <a name="to-generate-a-script-of-two-objects-using-object-explorer-details"></a><a name="ScriptTwoObjectsOED"></a><span data-ttu-id="c5f58-139">若要使用物件總管詳細資料產生兩個物件的腳本</span><span class="sxs-lookup"><span data-stu-id="c5f58-139">To generate a script of two objects using Object Explorer Details</span></span>  
 <span data-ttu-id="c5f58-140">**使用物件總管詳細資料編寫兩個物件的指令碼**</span><span class="sxs-lookup"><span data-stu-id="c5f58-140">**To script two objects using Object Explorer Details**</span></span>  
  
 <span data-ttu-id="c5f58-141">您可以使用 [物件總管詳細資料]\*\*\*\* 窗格，產生相同類別目錄之多個物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c5f58-141">You can use the **Object Explorer Details** pane to generate a script for mutliple objects of the same category.</span></span>  
  
1.  <span data-ttu-id="c5f58-142">在 [物件總管] 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="c5f58-142">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="c5f58-143">展開 [資料庫]，然後展開含有要編寫指令碼之物件的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c5f58-143">Expand **Databases**, and then expand the database containing the objects to be scripted.</span></span>  
  
3.  <span data-ttu-id="c5f58-144">展開想要編寫指令碼之物件類型的類別目錄節點，例如 [資料表] 節點。</span><span class="sxs-lookup"><span data-stu-id="c5f58-144">Expand the category node of the types of object you want to script, such as the **Tables** node.</span></span>  
  
4.  <span data-ttu-id="c5f58-145">選取 **F7** 或是開啟 [檢視] 功能表並選取 [物件總管詳細資料]，開啟 [物件總管詳細資料] 窗格。</span><span class="sxs-lookup"><span data-stu-id="c5f58-145">Open the **Object Explorer Details** pane by either selecting **F7**, or opening the **View** menu and selecting **Object Explorer Details**.</span></span>  
  
5.  <span data-ttu-id="c5f58-146">以滑鼠左鍵按一下您想要編寫指令碼的其中一個物件。</span><span class="sxs-lookup"><span data-stu-id="c5f58-146">Left-click one of the objects you want to script.</span></span>  
  
6.  <span data-ttu-id="c5f58-147">Crtl + 以滑鼠左鍵按一下您想要編寫指令碼的第二個物件。</span><span class="sxs-lookup"><span data-stu-id="c5f58-147">Crtl + left-click the second object you want to script.</span></span>  
  
7.  <span data-ttu-id="c5f58-148">以滑鼠右鍵按一下其中一個選取的物件，然後選取 [**編寫腳本 \<object type> 為**]。</span><span class="sxs-lookup"><span data-stu-id="c5f58-148">Right-click one of the selected objects, and select **Script \<object type> as**.</span></span>  
  
  
