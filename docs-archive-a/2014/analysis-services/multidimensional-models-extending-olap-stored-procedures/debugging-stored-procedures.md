---
title: 偵錯工具預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- debugging stored procedures [Analysis Services]
- stored procedures [Analysis Services], debugging
ms.assetid: 34f51b85-02b3-40dd-bf93-375a9e522385
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4f5971fe611f06a413ca48b2bc91237a8c87ee8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700432"
---
# <a name="debugging-stored-procedures"></a><span data-ttu-id="feb3a-102">除錯預存程序</span><span class="sxs-lookup"><span data-stu-id="feb3a-102">Debugging Stored Procedures</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="feb3a-103">預存程序實際上是以 C# (或任何其他 CLR 或 COM 語言) 撰寫的 CLR 或 COM 程式庫 (通常是 DLL)。</span><span class="sxs-lookup"><span data-stu-id="feb3a-103">stored procedures are actually CLR or COM libraries (normally DLLs) that are written in C# (or any other CLR or COM language).</span></span> <span data-ttu-id="feb3a-104">因此，偵錯預存程序十分類似在 Visual Studio 偵錯環境中除錯任何其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="feb3a-104">Therefore, debugging a stored procedure is much like debugging any other application in the Visual Studio debugging environment.</span></span> <span data-ttu-id="feb3a-105">您可以使用整合偵錯功能，在 Visual Studio 開發環境中偵錯預存程序。</span><span class="sxs-lookup"><span data-stu-id="feb3a-105">You debug stored procedures in the Visual Studio development environment using the integrated debugging functions.</span></span> <span data-ttu-id="feb3a-106">它們可讓您在程序位置上停止，檢查記憶體和登錄值，變更變數，觀察訊息流量，以及仔細查看程式碼的運作方式。</span><span class="sxs-lookup"><span data-stu-id="feb3a-106">These allow you to stop at procedure locations, inspect memory and register values, change variables, observe message traffic and get a close look at how your code works.</span></span>  
  
### <a name="to-debug-a-stored-procedure"></a><span data-ttu-id="feb3a-107">偵錯預存程序</span><span class="sxs-lookup"><span data-stu-id="feb3a-107">To debug a stored procedure</span></span>  
  
1.  <span data-ttu-id="feb3a-108">開啟用於 Visual Studio 中建立 DLL 的專案。</span><span class="sxs-lookup"><span data-stu-id="feb3a-108">Open the project used to create the DLL in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="feb3a-109">在對應到您要偵錯之程序的方法或函數中建立中斷點。</span><span class="sxs-lookup"><span data-stu-id="feb3a-109">Create breakpoints in the method or function corresponding to the procedure you want to debug.</span></span>  
  
3.  <span data-ttu-id="feb3a-110">使用 Visual Studio 建立預存程序 DLL 的偵錯建置。</span><span class="sxs-lookup"><span data-stu-id="feb3a-110">Use Visual Studio to create a debug build of a stored procedure DLL.</span></span>  
  
4.  <span data-ttu-id="feb3a-111">將 DLL 部署到伺服器。</span><span class="sxs-lookup"><span data-stu-id="feb3a-111">Deploy the DLL to the server.</span></span> <span data-ttu-id="feb3a-112">如需將 DLL 部署至伺服器的詳細資訊，請參閱[建立預存程式](creating-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="feb3a-112">For more information about deploying the DLL to the server, see [Creating Stored Procedures](creating-stored-procedures.md).</span></span>  
  
5.  <span data-ttu-id="feb3a-113">您需要一個應用程式來呼叫您要測試的預存程序。</span><span class="sxs-lookup"><span data-stu-id="feb3a-113">You need an application that calls the stored procedure that you want to test.</span></span> <span data-ttu-id="feb3a-114">如果您還沒有這樣的應用程式，可使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的 MDX 查詢編輯器，建立一個 MDX 查詢來呼叫您要測試的預存程序。</span><span class="sxs-lookup"><span data-stu-id="feb3a-114">If you do not have one ready, you can use the MDX Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create an MDX query that calls the stored procedure that you want to test.</span></span>  
  
6.  <span data-ttu-id="feb3a-115">在 Visual Studio 中，附加至 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 處理序 (Msmdsrv.exe)。</span><span class="sxs-lookup"><span data-stu-id="feb3a-115">In Visual Studio, attach to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] process (Msmdsrv.exe).</span></span>  
  
    1.  <span data-ttu-id="feb3a-116">從 [**調試**] 功能表中，選擇 [**附加 toProcess**]。</span><span class="sxs-lookup"><span data-stu-id="feb3a-116">From the **Debug** menu, choose **Attatch toProcess**.</span></span>  
  
    2.  <span data-ttu-id="feb3a-117">在 [**附加 toProcess** ] 對話方塊中，選取 [**顯示所有使用者的進程**]。</span><span class="sxs-lookup"><span data-stu-id="feb3a-117">In the **Attatch toProcess** dialog box, select **Show processes from all users**.</span></span>  
  
    3.  <span data-ttu-id="feb3a-118">在 [**可使用的進程**] 清單中，按一下 [**處理**] 資料行中的 [ **Msmdsrv.exe**]。</span><span class="sxs-lookup"><span data-stu-id="feb3a-118">In the **Available Processes** list, in the **Process** column, click **Msmdsrv.exe**.</span></span> <span data-ttu-id="feb3a-119">如果在伺服器上執行一個以上的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體，您需要以您要使用之執行個體的識別碼來識別處理序。</span><span class="sxs-lookup"><span data-stu-id="feb3a-119">If there is more than one instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] running on the server, you need to identify the process by the ID of the instance you want to use.</span></span>  
  
    4.  <span data-ttu-id="feb3a-120">在 [**附加至**] 文字方塊中，確認已選取適當的程式類型。</span><span class="sxs-lookup"><span data-stu-id="feb3a-120">In the **Attach to** text box, make sure that the appropriate program type is selected.</span></span> <span data-ttu-id="feb3a-121">若為 CLR DLL，請依序按一下 [**選取**]、[**偵錯工具代碼類型**] 和 [**受管理**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="feb3a-121">For a CLR DLL, click **Select**, then click **Debug these code types**, then click **Managed**, then click **OK**.</span></span> <span data-ttu-id="feb3a-122">若為 COM DLL，請依序按一下 [**選取**]、[**偵錯工具代碼類型**] 和 [**原生**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="feb3a-122">For a COM DLL, click **Select**, then click **Debug these code types**, then click **Native**, then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="feb3a-123">按一下 [附加] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="feb3a-123">Click **Attach**.</span></span>  
  
7.  <span data-ttu-id="feb3a-124">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中，叫用程式或 MDX 指令碼來呼叫預存程序。</span><span class="sxs-lookup"><span data-stu-id="feb3a-124">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], invoke the program or MDX script that calls the stored procedure.</span></span> <span data-ttu-id="feb3a-125">當偵錯工具到達包含中斷點的那一行時就會中斷。</span><span class="sxs-lookup"><span data-stu-id="feb3a-125">The debugger breaks when it reaches a line containing a breakpoint.</span></span> <span data-ttu-id="feb3a-126">您可以在監看式視窗中評估變數、檢視地區設定和逐步執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="feb3a-126">You can evaluate variables in the watch window, view locals, and step through the code.</span></span>  
  
 <span data-ttu-id="feb3a-127">如果您在偵錯程式庫時發生問題，請確定對應的程式資料庫 (PDB) 檔案已複製到伺服器上的部署位置。</span><span class="sxs-lookup"><span data-stu-id="feb3a-127">If you have problems debugging a library, make sure that the corresponding program database (PDB) file was copied to the deployment location on the server.</span></span> <span data-ttu-id="feb3a-128">如果在註冊或部署期間未複製此檔案，您必須手動將它複製到與 DLL 相同的位置。</span><span class="sxs-lookup"><span data-stu-id="feb3a-128">If this file was not copied during registration or deployment, you must copy it manually to the same location as the DLL.</span></span> <span data-ttu-id="feb3a-129">若為機器碼 (COM DLL)，PDB 檔是位於 \debug 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="feb3a-129">For native code (COM DLL), the PDB file resides in the \debug subdirectory.</span></span> <span data-ttu-id="feb3a-130">若為 Managed 程式碼 (CLR DLL)，它位於 \WINDEBUG 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="feb3a-130">For managed code (CLR DLL), it resides in the \WINDEBUG subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb3a-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="feb3a-131">See Also</span></span>  
 <span data-ttu-id="feb3a-132">[多維度模型元件管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="feb3a-132">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="feb3a-133">定義預存程式</span><span class="sxs-lookup"><span data-stu-id="feb3a-133">Defining Stored Procedures</span></span>](defining-stored-procedures.md)  
  
  
