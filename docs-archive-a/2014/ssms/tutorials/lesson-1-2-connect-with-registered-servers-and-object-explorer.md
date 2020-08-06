---
title: 連接已註冊的伺服器和物件總管 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: d6b3911f-68b4-4483-831b-df89d6400add
author: stevestein
ms.author: sstein
ms.openlocfilehash: b4bc75ad7f3682765dc102064a5621cd541ccd12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686717"
---
# <a name="connect-with-registered-servers-and-object-explorer"></a><span data-ttu-id="b5c48-102">連接已註冊的伺服器和物件總管</span><span class="sxs-lookup"><span data-stu-id="b5c48-102">Connect with Registered Servers and Object Explorer</span></span>
  <span data-ttu-id="b5c48-103">本教學課程示範已註冊的伺服器和物件總管的用法。</span><span class="sxs-lookup"><span data-stu-id="b5c48-103">This tutorial demonstrates the use of Registered Servers and Object Explorer.</span></span>  
  
 <span data-ttu-id="b5c48-104">本教學課程會使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b5c48-104">This tutorial uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="b5c48-105">為了加強安全性，依預設，不會安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="b5c48-105">To help enhance security, by default, the sample databases are not installed.</span></span> <span data-ttu-id="b5c48-106">如需詳細資訊，請參閱 [安裝 SQL Server 範例和範例資料庫](http://sqlserversamples.codeplex.com)。</span><span class="sxs-lookup"><span data-stu-id="b5c48-106">For more information, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
## <a name="connecting-to-servers"></a><span data-ttu-id="b5c48-107">連接到伺服器</span><span class="sxs-lookup"><span data-stu-id="b5c48-107">Connecting to Servers</span></span>  
 <span data-ttu-id="b5c48-108">已註冊之伺服器元件的工具列有 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]的按鈕。</span><span class="sxs-lookup"><span data-stu-id="b5c48-108">The toolbar of the Registered Servers component has buttons for the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="b5c48-109">您可以註冊其中一種或多種伺服器類型，以便於管理。</span><span class="sxs-lookup"><span data-stu-id="b5c48-109">You can register one or more of these server types for convenient management.</span></span> <span data-ttu-id="b5c48-110">嘗試下列練習，以註冊 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b5c48-110">Try the following exercise to register the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
#### <a name="to-register-the-database"></a><span data-ttu-id="b5c48-111">註冊資料庫</span><span class="sxs-lookup"><span data-stu-id="b5c48-111">To register the database</span></span>  
  
1.  <span data-ttu-id="b5c48-112">必要的話，在 [已註冊的伺服器] 工具列上，按一下 [Database Engine]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="b5c48-112">On the Registered Servers toolbar, click **Database Engine** if you have to.</span></span> <span data-ttu-id="b5c48-113">(可能已選取它)。</span><span class="sxs-lookup"><span data-stu-id="b5c48-113">(It may already be selected.)</span></span>  
  
2.  <span data-ttu-id="b5c48-114">展開 [Database Engine]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5c48-114">Expand **Database Engine**.</span></span>  
  
3.  <span data-ttu-id="b5c48-115">以滑鼠右鍵按一下 [本機伺服器群組]\*\*\*\*，然後按一下 [新增伺服器註冊]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5c48-115">Right-click **Local Server Groups**, and then click **New Server Registration**.</span></span>  
  
4.  <span data-ttu-id="b5c48-116">在 [新增伺服器註冊]\*\*\*\* 對話方塊的 [伺服器名稱]\*\*\*\* 文字方塊中，輸入您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="b5c48-116">In the **New Server Registration** dialog box, in the **Server name** text box, type the name of your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="b5c48-117">在 [已註冊的伺服器名稱]\*\*\*\* 方塊中，輸入 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b5c48-117">In the **Registered server name** box, type [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
6.  <span data-ttu-id="b5c48-118">在 [**連接屬性**] 索引標籤的 [**連接到資料庫**] 清單中，選取 [] **\<Browse server...>** 。</span><span class="sxs-lookup"><span data-stu-id="b5c48-118">On the **Connection Properties** tab, in the **Connect to database** list, select **\<Browse server...>**.</span></span>  
  
7.  <span data-ttu-id="b5c48-119">在 [瀏覽資料庫]\*\*\*\* 對話方塊中，按一下 [是]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5c48-119">In the **Browse for Databases** dialog box, click **Yes**.</span></span>  
  
8.  <span data-ttu-id="b5c48-120">在 [瀏覽伺服器上的資料庫]\*\*\*\* 對話方塊中，選取 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5c48-120">In the **Browse Server for Database** dialog box, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **OK**.</span></span>  
  
9. <span data-ttu-id="b5c48-121">若要驗證伺服器已正確地註冊，請按一下 [測試]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5c48-121">To verify that the server has been registered correctly, click **Test**.</span></span>  
  
10. <span data-ttu-id="b5c48-122">在 [新增伺服器註冊]\*\*\*\* 對話方塊中，按一下 [儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5c48-122">In the **New Server Registration** dialog box, click **Save**.</span></span>  
  
## <a name="connecting-with-object-explorer"></a><span data-ttu-id="b5c48-123">連接物件總管</span><span class="sxs-lookup"><span data-stu-id="b5c48-123">Connecting with Object Explorer</span></span>  
 <span data-ttu-id="b5c48-124">如同已註冊的伺服器，[物件總管] 也可以連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b5c48-124">Like Registered Servers, Object Explorer can connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
#### <a name="to-connect-with-object-explorer"></a><span data-ttu-id="b5c48-125">連接物件總管</span><span class="sxs-lookup"><span data-stu-id="b5c48-125">To connect with Object Explorer</span></span>  
  
1.  <span data-ttu-id="b5c48-126">在物件總管的工具列上，按一下 [連接]\*\*\*\* 列出可能的連接類型，然後選取 [Database Engine]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5c48-126">On the toolbar of Object Explorer, click **Connect** for a list of possible connection types, and then select **Database Engine**.</span></span>  
  
2.  <span data-ttu-id="b5c48-127">在 [連接到伺服器]\*\*\*\* 對話方塊的 [伺服器名稱]\*\*\*\* 文字方塊中，輸入您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="b5c48-127">In the **Connect to Server** dialog box, in the **Server name** text box, type the name of your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="b5c48-128">按一下 [選項]\*\*\*\*，瀏覽所提供選擇。</span><span class="sxs-lookup"><span data-stu-id="b5c48-128">Click **Options** and explore the choices.</span></span>  
  
4.  <span data-ttu-id="b5c48-129">若要連接到伺服器，請按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5c48-129">To connect to the server, click **Connect**.</span></span> <span data-ttu-id="b5c48-130">如果已連接，此動作就會讓您返回 [物件總管]，並將焦點設在該伺服器上。</span><span class="sxs-lookup"><span data-stu-id="b5c48-130">If you are already connected, this action just returns you to Object Explorer and sets the focus on that server.</span></span>  
  
     <span data-ttu-id="b5c48-131">您可以利用 [物件總管] 來管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全性、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent、複寫和 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="b5c48-131">With Object Explorer you can administer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Security, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, Replication, and Database Mail.</span></span> <span data-ttu-id="b5c48-132">[物件總管] 只能管理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]和 [!INCLUDE[ssIS](../../includes/ssis-md.md)]的部分功能。</span><span class="sxs-lookup"><span data-stu-id="b5c48-132">Object Explorer can only manage some of the features of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssIS](../../includes/ssis-md.md)].</span></span> <span data-ttu-id="b5c48-133">這些元件每個都有其他專用工具。</span><span class="sxs-lookup"><span data-stu-id="b5c48-133">Each of those components has additional specialized tools.</span></span>  
  
5.  <span data-ttu-id="b5c48-134">在物件總管中，展開 [資料庫]\*\*\*\* 資料夾，然後選取 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b5c48-134">In Object Explorer, expand the **Databases** folder and select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
     <span data-ttu-id="b5c48-135">請注意，[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 會在另外一個資料夾中提供系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="b5c48-135">Notice that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] presents the system databases in a separate folder.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="b5c48-136">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="b5c48-136">Next Task in Lesson</span></span>  
 [<span data-ttu-id="b5c48-137">變更環境配置</span><span class="sxs-lookup"><span data-stu-id="b5c48-137">Change the Environment Layout</span></span>](lesson-1-3-change-the-environment-layout.md)  
  
  
