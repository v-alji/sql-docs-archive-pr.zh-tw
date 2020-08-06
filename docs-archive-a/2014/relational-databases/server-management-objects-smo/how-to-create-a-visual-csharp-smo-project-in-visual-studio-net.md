---
title: '在 Visual Studio .NET 中建立 Visual c # SMO 專案 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
author: stevestein
ms.author: sstein
ms.openlocfilehash: b78820fafd37675332e6703cabbb87e78bde5864
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597766"
---
# <a name="create-a-visual-c-smo-project-in-visual-studio-net"></a><span data-ttu-id="531f7-102">在 Visual Studio .NET 中建立 Visual C# SMO 專案</span><span class="sxs-lookup"><span data-stu-id="531f7-102">Create a Visual C# SMO Project in Visual Studio .NET</span></span>
  <span data-ttu-id="531f7-103">本節描述如何建立簡單的 SMO 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="531f7-103">This section describes how to build a simple SMO console application.</span></span>  
  
 <span data-ttu-id="531f7-104">此範例會匯入命名空間，讓程式可以參考 SMO 類型。</span><span class="sxs-lookup"><span data-stu-id="531f7-104">This example imports namespaces, which enables the program to reference SMO types.</span></span> <span data-ttu-id="531f7-105">`Agent` 命名空間的匯入是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="531f7-105">The import of the `Agent` namespace is optional.</span></span> <span data-ttu-id="531f7-106">請在撰寫使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的程式時使用該命名空間。</span><span class="sxs-lookup"><span data-stu-id="531f7-106">Use it when you are writing a program that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="531f7-107">若要與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體建立安全的連接，必須使用 `Common` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="531f7-107">The `Common` namespace is required to establish a secure connection to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="531f7-108">`SqlClient` 命名空間是用於處理 SQL 例外狀況錯誤。</span><span class="sxs-lookup"><span data-stu-id="531f7-108">The `SqlClient` namespace is used to process SQL exception errors.</span></span>  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a><span data-ttu-id="531f7-109">在 Visual Studio .NET 中建立 Visual C# SMO 專案</span><span class="sxs-lookup"><span data-stu-id="531f7-109">Creating a Visual C# SMO project in Visual Studio.NET</span></span>  
  
1.  <span data-ttu-id="531f7-110">啟動 [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (或 [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="531f7-110">Start [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (or [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).</span></span>  
  
2.  <span data-ttu-id="531f7-111">在 [檔案]\*\*\*\* 功能表上，按一下 [新增專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="531f7-111">On the **File** menu, click **NewProject.**</span></span> <span data-ttu-id="531f7-112">[新增專案]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="531f7-112">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="531f7-113">在 [**專案類型**] 對話方塊中，選取 [ **Visual c #**]，然後選取 [ **Windows**]。</span><span class="sxs-lookup"><span data-stu-id="531f7-113">In **Project Types** dialog box, select **Visual C#**, and then select **Windows**.</span></span> <span data-ttu-id="531f7-114">在 [ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 已安裝的範本] 窗格中，選取 [ **Windows 應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="531f7-114">In the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Installed Templates pane, select **Windows Application**.</span></span>  
  
4.  <span data-ttu-id="531f7-115"> (選擇性) 在 [**名稱**] 欄位中，輸入新應用程式的名稱</span><span class="sxs-lookup"><span data-stu-id="531f7-115">(Optional) In the **Name** field, type the name of the new application</span></span>  
  
5.  <span data-ttu-id="531f7-116">選取 Visual C# 應用程式類型。</span><span class="sxs-lookup"><span data-stu-id="531f7-116">Select the Visual C# application type.</span></span> <span data-ttu-id="531f7-117">在接下來的範例中，選取 [**主控台應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="531f7-117">For the examples that follow, select **Console Application**.</span></span>  
  
6.  <span data-ttu-id="531f7-118">在 [專案]\*\*\*\* 功能表上，選取 [新增參考]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="531f7-118">On the **Project** menu, select **Add Reference**.</span></span> <span data-ttu-id="531f7-119">[新增參考]\*\*\*\* 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="531f7-119">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="531f7-120">按一下 **[流覽]**，在資料夾中找出 SMO 元件 [!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)] ，然後選取下列檔案。</span><span class="sxs-lookup"><span data-stu-id="531f7-120">Click **Browse**, locate the SMO assemblies in the [!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)] folder, and then select the following files.</span></span> <span data-ttu-id="531f7-121">以下是建立 SMO 應用程式所需最少的檔案：</span><span class="sxs-lookup"><span data-stu-id="531f7-121">These are the minimum files that are required to build an SMO application:</span></span>  
  
     <span data-ttu-id="531f7-122">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="531f7-122">Microsoft.SqlServer.ConnectionInfo.dll</span></span>  
  
     <span data-ttu-id="531f7-123">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="531f7-123">Microsoft.SqlServer.Smo.dll</span></span>  
  
     <span data-ttu-id="531f7-124">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span><span class="sxs-lookup"><span data-stu-id="531f7-124">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span></span>  
  
     <span data-ttu-id="531f7-125">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="531f7-125">Microsoft.SqlServer.SqlEnum.dll</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="531f7-126">使用 `Ctrl` 鍵以選取一個以上的檔案。</span><span class="sxs-lookup"><span data-stu-id="531f7-126">Use the `Ctrl` key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="531f7-127">加入任何需要的其他 SMO 組件。</span><span class="sxs-lookup"><span data-stu-id="531f7-127">Add any additional SMO assemblies that are required.</span></span> <span data-ttu-id="531f7-128">例如，如果要特別開發 [!INCLUDE[ssSB](../../includes/sssb-md.md)]，請加入下列組件：</span><span class="sxs-lookup"><span data-stu-id="531f7-128">For example, if you are specifically programming [!INCLUDE[ssSB](../../includes/sssb-md.md)], add the following assemblies:</span></span>  
  
     <span data-ttu-id="531f7-129">Microsoft.SqlServer.ServiceBrokerEmum.dll</span><span class="sxs-lookup"><span data-stu-id="531f7-129">Microsoft.SqlServer.ServiceBrokerEmum.dll</span></span>  
  
9. <span data-ttu-id="531f7-130">按一下 **[開啟]** 。</span><span class="sxs-lookup"><span data-stu-id="531f7-130">Click **Open**.</span></span>  
  
10. <span data-ttu-id="531f7-131">在 [ **View** ] 功能表上，按一下 [程式**代碼**]。-或-選取 [Program1.cs [Design]] 視窗，然後按兩下 windows form 以顯示程式碼視窗。</span><span class="sxs-lookup"><span data-stu-id="531f7-131">On the **View** menu, click **Code**.-Or-Select the Program1.cs [Design] Windows and double-click the windows form to show the code window.</span></span>  
  
11. <span data-ttu-id="531f7-132">在程式碼的命名空間陳述式之前，輸入下列 `using` 陳述式來限定 SMO 命名空間中的類型：</span><span class="sxs-lookup"><span data-stu-id="531f7-132">In the code, before the namespace statement, type the following `using` statements to qualify the types in the SMO namespace:</span></span>  
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
12. <span data-ttu-id="531f7-133">SMO 在 Microsoft.SqlServer.Management.Smo 之下具有多個命名空間，例如 Microsoft.SqlServer.Management.Smo.Agent。</span><span class="sxs-lookup"><span data-stu-id="531f7-133">SMO has various namespaces under Microsoft.SqlServer.Management.Smo, such as Microsoft.SqlServer.Management.Smo.Agent.</span></span> <span data-ttu-id="531f7-134">需要時才新增命名空間。</span><span class="sxs-lookup"><span data-stu-id="531f7-134">Add these namespaces as they are required.</span></span>  
  
13. <span data-ttu-id="531f7-135">您現在可以加入您的 SMO 程式碼。</span><span class="sxs-lookup"><span data-stu-id="531f7-135">You can now add your SMO code.</span></span>  
  
  
