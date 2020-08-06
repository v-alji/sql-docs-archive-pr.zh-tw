---
title: 發行資料庫 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 98b2914e-7147-40af-ba7d-87253bbe8bf9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 652f2341d24c19e6c5ce34196b0e1c4dc5b09084
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595099"
---
# <a name="publish-a-database-sql-server-management-studio"></a><span data-ttu-id="a4104-102">發行資料庫 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a4104-102">Publish a Database (SQL Server Management Studio)</span></span>
  <span data-ttu-id="a4104-103">您可以使用 **[產生和發佈指令碼]** 精靈，將整個資料庫或個別的資料庫物件發行至 Web 主控提供者。</span><span class="sxs-lookup"><span data-stu-id="a4104-103">You can use the **Generate and Publish Scripts Wizard** to publish an entire database or individual database objects to a Web hosting provider.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4104-104">本主題所述的功能在過去是由發行資料庫精靈所提供。</span><span class="sxs-lookup"><span data-stu-id="a4104-104">The functionality described in this topic used to be provided by the Publish Database Wizard.</span></span> <span data-ttu-id="a4104-105">發行功能已經加入至產生和發佈指令碼精靈，而且發行資料庫精靈已經停用。</span><span class="sxs-lookup"><span data-stu-id="a4104-105">The publishing functionality has been added to the Generate and Publish Scripts Wizard, and the Publish Database Wizard has been discontinued.</span></span>  
  
## <a name="generate-and-publish-scripts-wizard"></a><span data-ttu-id="a4104-106">[產生和發佈指令碼]</span><span class="sxs-lookup"><span data-stu-id="a4104-106">Generate and Publish Scripts Wizard</span></span>  
 <span data-ttu-id="a4104-107">產生和發佈指令碼精靈可用來將資料庫或選定的資料庫物件發行至 Web 主控提供者。</span><span class="sxs-lookup"><span data-stu-id="a4104-107">The Generate and Publish Scripts Wizard can be used to publish a database or selected database objects to a Web hosting provider.</span></span> <span data-ttu-id="a4104-108">SQL Server Web 主控提供者是與 Web 服務之間的連接介面。</span><span class="sxs-lookup"><span data-stu-id="a4104-108">A SQL Server Web hosting provider is a connectivity interface to a Web service.</span></span> <span data-ttu-id="a4104-109">此 Web 服務是使用 CodePlex 上 SQL Server Hosting Toolkit 中的資料庫發行服務專案所建立。</span><span class="sxs-lookup"><span data-stu-id="a4104-109">The Web service is created by using the Database Publishing Services project from the SQL Server Hosting Toolkit on CodePlex.</span></span> <span data-ttu-id="a4104-110">此 Web 服務可讓 Web 主控者客戶輕鬆地使用產生和發佈指令碼精靈，將他們的資料庫發行到此服務。</span><span class="sxs-lookup"><span data-stu-id="a4104-110">The Web service makes it easy for the Web hoster customers to publish their databases to the service by using the Generate and Publish Scripts Wizard.</span></span> <span data-ttu-id="a4104-111">如需有關下載 SQL Server Hosting Toolkit 的詳細資訊，請參閱 [SQL Server 資料庫發行服務](https://go.microsoft.com/fwlink/?LinkId=142025)。</span><span class="sxs-lookup"><span data-stu-id="a4104-111">For more information about downloading the SQL Server Hosting Toolkit, see [SQL Server Database Publishing Services](https://go.microsoft.com/fwlink/?LinkId=142025).</span></span>  
  
 <span data-ttu-id="a4104-112">產生和發佈指令碼精靈也可以用來建立傳輸資料庫的指令碼。</span><span class="sxs-lookup"><span data-stu-id="a4104-112">The Generate and Publish Scripts Wizard can also be used to create a script for transferring a database.</span></span>  
  
#### <a name="to-publish-a-database-to-a-web-service"></a><span data-ttu-id="a4104-113">若要將資料庫發行到 Web 服務</span><span class="sxs-lookup"><span data-stu-id="a4104-113">To publish a database to a Web service</span></span>  
  
1.  <span data-ttu-id="a4104-114">在物件總管中，展開 [資料庫]  ，以滑鼠右鍵按一下資料庫，指向 [工作]  ，然後按一下 [產生和發佈指令碼]  。</span><span class="sxs-lookup"><span data-stu-id="a4104-114">In Object Explorer, expand **Databases**, right-click a database, point to **Tasks**, and then click **Generate and Publish Scripts**.</span></span> <span data-ttu-id="a4104-115">遵循精靈中的步驟，以便編寫要發行之資料庫物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="a4104-115">Follow the steps in the wizard to script the database objects for publishing.</span></span>  
  
2.  <span data-ttu-id="a4104-116">在 **[選擇物件]** 頁面上，選取要發行至 Web 主控服務的物件。</span><span class="sxs-lookup"><span data-stu-id="a4104-116">On the **Choose Objects** page, select the objects to be published to the Web hosting service.</span></span>  
  
3.  <span data-ttu-id="a4104-117">在 **[設定指令碼編寫選項]** 頁面上，選取 **[發佈到 Web 服務]** 。</span><span class="sxs-lookup"><span data-stu-id="a4104-117">On the **Set Scripting Options** page, select **Publish to Web Service**.</span></span>  
  
    1.  <span data-ttu-id="a4104-118">在 **[提供者]** 方塊中，指定您的 Web 服務提供者。</span><span class="sxs-lookup"><span data-stu-id="a4104-118">In the **Provider** box, specify the provider for your Web service.</span></span> <span data-ttu-id="a4104-119">如果您尚未設定 Web 主控提供者，請選取 **[管理提供者]** ，並使用 **[管理提供者]** 對話方塊來設定 Web 服務的提供者。</span><span class="sxs-lookup"><span data-stu-id="a4104-119">If you have not configured a Web hosting provider, select **Manage Providers** and use the **Manage Providers** dialog box to configure a provider for your Web service.</span></span>  
  
    2.  <span data-ttu-id="a4104-120">若要指定進階發行選項，請選取 **[發佈到 Web 服務]** 區段中的 **[進階]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a4104-120">To specify advanced publishing options, select the **Advanced** button in the **Publish to Web Service** section.</span></span>  
  
4.  <span data-ttu-id="a4104-121">在 **[摘要]** 頁面中，檢閱您的選取。</span><span class="sxs-lookup"><span data-stu-id="a4104-121">On the **Summary** page, review your selections.</span></span> <span data-ttu-id="a4104-122">按 **[上一步]** 可變更您的選取。</span><span class="sxs-lookup"><span data-stu-id="a4104-122">Click **Previous** to change your selections.</span></span> <span data-ttu-id="a4104-123">按 **[下一步]** ，發佈您選取的物件。</span><span class="sxs-lookup"><span data-stu-id="a4104-123">Click **Next** to publish the objects you selected.</span></span>  
  
5.  <span data-ttu-id="a4104-124">在 **[儲存或發佈指令碼]** 頁面上，監視發行的進度。</span><span class="sxs-lookup"><span data-stu-id="a4104-124">On the **Save or Publish Scripts** page, monitor the progress of the publication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4104-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4104-125">See Also</span></span>  
 <span data-ttu-id="a4104-126">[產生指令碼 &#40;SQL Server Management Studio&#41;](../scripting/generate-scripts-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a4104-126">[Generate Scripts &#40;SQL Server Management Studio&#41;](../scripting/generate-scripts-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="a4104-127">複製資料庫至其他伺服器</span><span class="sxs-lookup"><span data-stu-id="a4104-127">Copy Databases to Other Servers</span></span>](copy-databases-to-other-servers.md)  
  
  
