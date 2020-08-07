---
title: 第1課：建立 Web 服務用戶端專案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0070daa6-56b0-4663-83b2-44c96acafad8
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: eda9413867c4ca6d44a5cf98b82be9bddc04d0f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703542"
---
# <a name="lesson-1-creating-the-web-service-client-project"></a><span data-ttu-id="0b1f0-102">第 1 課：建立 Web 服務用戶端專案</span><span class="sxs-lookup"><span data-stu-id="0b1f0-102">Lesson 1: Creating the Web Service Client Project</span></span>
  <span data-ttu-id="0b1f0-103">在這個逐步解說中，您會建立存取報表伺服器 Web 服務的簡單主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b1f0-103">For this walkthrough, you will create a simple console application that accesses the Report Server Web service.</span></span> <span data-ttu-id="0b1f0-104">這個逐步解說假設您是在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中進行開發工作。</span><span class="sxs-lookup"><span data-stu-id="0b1f0-104">This walkthrough assumes you are developing in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span>  
  
### <a name="to-create-a-console-application"></a><span data-ttu-id="0b1f0-105">若要建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="0b1f0-105">To create a console application</span></span>  
  
1.  <span data-ttu-id="0b1f0-106">在 [**檔案**] 功能表上，指向 [**新增**]，然後按一下 [**專案**] 以開啟 [**新增專案**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0b1f0-106">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="0b1f0-107">在左窗格的 [**已安裝的範本**] 底下，按一下 [ **Visual Basic** ] 或 [ **Visual c #** ] 節點，然後從展開的清單中選取專案類型的類別。</span><span class="sxs-lookup"><span data-stu-id="0b1f0-107">In the left pane, under **Installed Templates**, click either **Visual Basic** or the **Visual C#** node, and select a category of project types from the expanded list.</span></span>  
  
3.  <span data-ttu-id="0b1f0-108">選擇 [**主控台應用程式**] 專案類型。</span><span class="sxs-lookup"><span data-stu-id="0b1f0-108">Choose the **Console Application** project type.</span></span>  
  
4.  <span data-ttu-id="0b1f0-109">在 [**名稱**] 方塊中，輸入專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0b1f0-109">In the **Name** box, enter a name for your project.</span></span> <span data-ttu-id="0b1f0-110">輸入 [名稱] `GetPropertiesSample` 。</span><span class="sxs-lookup"><span data-stu-id="0b1f0-110">Type the name `GetPropertiesSample`.</span></span>  
  
5.  <span data-ttu-id="0b1f0-111">在 [**位置**] 方塊中，輸入您要儲存專案的路徑，或按一下 **[流覽]** 以流覽至資料夾。</span><span class="sxs-lookup"><span data-stu-id="0b1f0-111">In the **Location** box, enter the path where you want to save your project, or click **Browse** to navigate to the folder.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]<span data-ttu-id="0b1f0-112">專案的折迭視圖會顯示在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="0b1f0-112">A collapsed view of your project appears in Solution Explorer.</span></span>  
  
     <span data-ttu-id="0b1f0-113">在 [方案總管] 中，展開專案節點。</span><span class="sxs-lookup"><span data-stu-id="0b1f0-113">In Solution Explorer, expand the project node.</span></span> <span data-ttu-id="0b1f0-114">) 的預設名稱為 Program.cs (Module1 的檔案 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 已新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="0b1f0-114">A file with the default name of Program.cs (Module1.vb for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) has been added to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b1f0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b1f0-115">See Also</span></span>  
 <span data-ttu-id="0b1f0-116">[第2課：加入 Web 參考](../../2014/tutorials/lesson-2-adding-a-web-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0b1f0-116">[Lesson 2: Adding a Web Reference](../../2014/tutorials/lesson-2-adding-a-web-reference.md) </span></span>  
 [<span data-ttu-id="0b1f0-117">使用 Visual Basic 或 Visual C&#35; &#40;SSRS 教學課程來存取報表伺服器 Web 服務&#41;</span><span class="sxs-lookup"><span data-stu-id="0b1f0-117">Accessing the Report Server Web Service Using Visual Basic or Visual C&#35; &#40;SSRS Tutorial&#41;</span></span>](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
