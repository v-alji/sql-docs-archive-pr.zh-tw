---
title: 在 Visual Studio .NET 中建立 Visual Basic SMO 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic [SMO]
ms.assetid: d7a3892c-0f1c-4c4d-8480-b58dce3720bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 844d27ab6aadbc972c6282c79adb13e15d55c322
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709906"
---
# <a name="create-a-visual-basic-smo-project-in-visual-studio-net"></a><span data-ttu-id="5b01d-102">在 Visual Studio .NET 中建立 Visual Basic SMO 專案</span><span class="sxs-lookup"><span data-stu-id="5b01d-102">Create a Visual Basic SMO Project in Visual Studio .NET</span></span>
  <span data-ttu-id="5b01d-103">本節描述如何建立簡單的 SMO 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="5b01d-103">This section describes how to build a simple SMO console application.</span></span>  
  
 <span data-ttu-id="5b01d-104">此範例會匯入命名空間，讓程式可以參考 SMO 類型。</span><span class="sxs-lookup"><span data-stu-id="5b01d-104">This example imports namespaces, which enables the program to reference SMO types.</span></span> <span data-ttu-id="5b01d-105">`Agent` 命名空間的匯入是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="5b01d-105">The import of the `Agent` namespace is optional.</span></span> <span data-ttu-id="5b01d-106">請在撰寫使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的程式時使用該命名空間。</span><span class="sxs-lookup"><span data-stu-id="5b01d-106">Use it when you are writing a program that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="5b01d-107">若要與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體建立安全的連接，必須使用 `Common` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="5b01d-107">The `Common` namespace is required to establish a secure connection to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5b01d-108">`SqlClient` 命名空間是用於處理 SQL 例外狀況錯誤。</span><span class="sxs-lookup"><span data-stu-id="5b01d-108">The `SqlClient` namespace is used to process SQL exception errors.</span></span>  
  
### <a name="creating-a-visual-basic-smo-project-in-visual-studionet"></a><span data-ttu-id="5b01d-109">在 Visual Studio .NET 中建立 Visual Basic SMO 專案</span><span class="sxs-lookup"><span data-stu-id="5b01d-109">Creating a Visual Basic SMO project in Visual Studio.NET</span></span>  
  
1.  <span data-ttu-id="5b01d-110">啟動 [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (或 [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="5b01d-110">Start [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (or [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).</span></span>  
  
2.  <span data-ttu-id="5b01d-111">在 [檔案]\*\*\*\* 功能表上，按一下 [新增專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b01d-111">On the **File** menu, click **NewProject.**</span></span> <span data-ttu-id="5b01d-112">[新增專案]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="5b01d-112">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="5b01d-113">在 [**專案類型**] 對話方塊中，選取 [ **Visual Basic**]，然後選取 [ **Windows**]。</span><span class="sxs-lookup"><span data-stu-id="5b01d-113">In **Project Types** dialog box, select **Visual Basic**, and then select **Windows**.</span></span> <span data-ttu-id="5b01d-114">在 [ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 已安裝的範本] 窗格中，選取 [**主控台應用程式]。**</span><span class="sxs-lookup"><span data-stu-id="5b01d-114">In the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Installed Templates pane, select **Console Application.**</span></span>  
  
4.  <span data-ttu-id="5b01d-115"> (選擇性) 在 [**名稱**] 欄位中，輸入新應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="5b01d-115">(Optional) In the **Name** field, type the name of the new application.</span></span>  
  
5.  <span data-ttu-id="5b01d-116">按一下 **[確定]** 以載入 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 主控台應用程式範本。</span><span class="sxs-lookup"><span data-stu-id="5b01d-116">Click **OK** to load the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] console application template.</span></span>  
  
6.  <span data-ttu-id="5b01d-117">在 [專案]\*\*\*\* 功能表上，選取 [新增參考]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b01d-117">On the **Project** menu, select **Add Reference**.</span></span> <span data-ttu-id="5b01d-118">[新增參考]\*\*\*\* 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="5b01d-118">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="5b01d-119">按一下 **[流覽]**，在 C:\PROGRAM Files\Microsoft SQL Server\120\SDK\Assemblies 資料夾中找出 SMO 元件，然後選取下列檔案。</span><span class="sxs-lookup"><span data-stu-id="5b01d-119">Click **Browse**, locate the SMO assemblies in the C:\Program Files\Microsoft SQL Server\120\SDK\Assemblies folder, and then select the following files.</span></span> <span data-ttu-id="5b01d-120">以下是建立 SMO 應用程式所需最少的檔案：</span><span class="sxs-lookup"><span data-stu-id="5b01d-120">These are the minimum files that are required to build an SMO application:</span></span>  
  
     <span data-ttu-id="5b01d-121">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="5b01d-121">Microsoft.SqlServer.ConnectionInfo.dll</span></span>  
  
     <span data-ttu-id="5b01d-122">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="5b01d-122">Microsoft.SqlServer.SqlEnum.dll</span></span>  
  
     <span data-ttu-id="5b01d-123">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="5b01d-123">Microsoft.SqlServer.Smo.dll</span></span>  
  
     <span data-ttu-id="5b01d-124">Microsoft.SqlServer.Management.Sdk.Sfc</span><span class="sxs-lookup"><span data-stu-id="5b01d-124">Microsoft.SqlServer.Management.Sdk.Sfc</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5b01d-125">使用 `Ctrl` 鍵以選取一個以上的檔案。</span><span class="sxs-lookup"><span data-stu-id="5b01d-125">Use the `Ctrl` key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="5b01d-126">加入任何需要的其他 SMO 組件。</span><span class="sxs-lookup"><span data-stu-id="5b01d-126">Add any additional SMO assemblies that are required.</span></span> <span data-ttu-id="5b01d-127">例如，如果要特別開發 [!INCLUDE[ssSB](../../includes/sssb-md.md)]，請加入下列組件：</span><span class="sxs-lookup"><span data-stu-id="5b01d-127">For example, if you are specifically programming [!INCLUDE[ssSB](../../includes/sssb-md.md)], add the following assemblies:</span></span>  
  
     <span data-ttu-id="5b01d-128">Microsoft.SqlServer.ServiceBrokerEmum.dll</span><span class="sxs-lookup"><span data-stu-id="5b01d-128">Microsoft.SqlServer.ServiceBrokerEmum.dll</span></span>  
  
9. <span data-ttu-id="5b01d-129">按一下 **[開啟]** 。</span><span class="sxs-lookup"><span data-stu-id="5b01d-129">Click **Open**.</span></span>  
  
10. <span data-ttu-id="5b01d-130">在 [ **View** ] 功能表上，按一下 [程式**代碼**]。-或-選取 [Module1] 視窗以顯示程式碼視窗。</span><span class="sxs-lookup"><span data-stu-id="5b01d-130">On the **View** menu, click **Code**.-Or-Select the Module1.vb window to show the code window.</span></span>  
  
11. <span data-ttu-id="5b01d-131">在程式碼的任何宣告之前，輸入下列**Imports**語句，以限定 SMO 命名空間中的類型。</span><span class="sxs-lookup"><span data-stu-id="5b01d-131">In the code, before any declarations, type the following **Imports** statements to qualify the types in the SMO namespace.</span></span>  
  
    ```  
    Imports Microsoft.SqlServer.Management.Smo  
    Imports Microsoft.SqlServer.Management.Common  
    ```  
  
12. <span data-ttu-id="5b01d-132">SMO 在 Microsoft.SqlServer.Management.Smo 之下具有多個命名空間，例如 Microsoft.SqlServer.Management.Smo.Agent。</span><span class="sxs-lookup"><span data-stu-id="5b01d-132">SMO has various namespaces under Microsoft.SqlServer.Management.Smo, such as Microsoft.SqlServer.Management.Smo.Agent.</span></span> <span data-ttu-id="5b01d-133">需要時才新增命名空間。</span><span class="sxs-lookup"><span data-stu-id="5b01d-133">Add these namespaces as they are required.</span></span>  
  
13. <span data-ttu-id="5b01d-134">您現在可以加入您的 SMO 程式碼。</span><span class="sxs-lookup"><span data-stu-id="5b01d-134">You can now add your SMO code.</span></span>  
  
  
