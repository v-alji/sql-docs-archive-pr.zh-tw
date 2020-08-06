---
title: 第5課：新增套件部署模型的套件設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ee03d624ac7144cf6aef0829bcb7835fe5af9c53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688026"
---
# <a name="lesson-5-adding-package-configurations-for-the-package-deployment-model"></a><span data-ttu-id="255a5-102">第 5 課：新增封裝部署模型的封裝組態</span><span class="sxs-lookup"><span data-stu-id="255a5-102">Lesson 5: Adding Package Configurations for the Package Deployment Model</span></span>
  <span data-ttu-id="255a5-103">封裝組態可讓您從開發環境之外設定執行階段屬性和變數。</span><span class="sxs-lookup"><span data-stu-id="255a5-103">Package configurations let you set run-time properties and variables from outside of the development environment.</span></span> <span data-ttu-id="255a5-104">組態可讓您開發彈性且易於部署和散發的封裝。</span><span class="sxs-lookup"><span data-stu-id="255a5-104">Configurations allow you to develop packages that are flexible and easy to both deploy and distribute.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="255a5-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 會提供下列組態類型：</span><span class="sxs-lookup"><span data-stu-id="255a5-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] offers the following configuration types:</span></span>  
  
-   <span data-ttu-id="255a5-106">XML 組態檔</span><span class="sxs-lookup"><span data-stu-id="255a5-106">XML configuration file</span></span>  
  
-   <span data-ttu-id="255a5-107">環境變數</span><span class="sxs-lookup"><span data-stu-id="255a5-107">Environment variable</span></span>  
  
-   <span data-ttu-id="255a5-108">登錄項目</span><span class="sxs-lookup"><span data-stu-id="255a5-108">Registry entry</span></span>  
  
-   <span data-ttu-id="255a5-109">父封裝變數</span><span class="sxs-lookup"><span data-stu-id="255a5-109">Parent package variable</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="255a5-110">資料表</span><span class="sxs-lookup"><span data-stu-id="255a5-110">table</span></span>  
  
 <span data-ttu-id="255a5-111">在這一課，您將修改在＜ [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ＞中建立的簡單 [ssISnoversion](lesson-4-add-error-flow-redirection-with-ssis.md) 封裝，以便使用封裝部署模型並利用封裝組態。</span><span class="sxs-lookup"><span data-stu-id="255a5-111">In this lesson, you will modify the simple [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that you created in [Lesson 4: Adding Error Flow Redirection](lesson-4-add-error-flow-redirection-with-ssis.md) to use the Package Deployment Model and take advantage of package configurations.</span></span> <span data-ttu-id="255a5-112">您也可以複製此教學課程所包含之已完成的第 4 課封裝。</span><span class="sxs-lookup"><span data-stu-id="255a5-112">You can also copy the completed Lesson 4 package that is included with the tutorial.</span></span> <span data-ttu-id="255a5-113">使用封裝組態精靈，您可以建立一個 XML 組態，利用一個對應至 Directory 屬性的封裝層級變數，來更新 Foreach 迴圈容器的 `Directory` 屬性。</span><span class="sxs-lookup"><span data-stu-id="255a5-113">Using the Package Configuration Wizard, you will create an XML configuration that updates the `Directory` property of the Foreach Loop container by using a package-level variable mapped to the Directory property.</span></span> <span data-ttu-id="255a5-114">建立組態檔之後，您可以從開發環境之外修改變數的值，並將已修改的屬性指向新的範例資料夾。</span><span class="sxs-lookup"><span data-stu-id="255a5-114">Once you have created the configuration file, you will modify the value of the variable from outside of the development environment and point the modified property to a new sample data folder.</span></span> <span data-ttu-id="255a5-115">當您再次執行封裝時，設定檔會填入變數的值，而變數會接著更新 `Directory` 屬性。</span><span class="sxs-lookup"><span data-stu-id="255a5-115">When you run the package again, the configuration file populates the value of the variable, and the variable in turn updates the `Directory` property.</span></span> <span data-ttu-id="255a5-116">因此，封裝會反覆執行新儲存資料的資料夾之檔案，而不反覆執行以寫入程式碼的方式寫入封裝內之原始資料夾的檔案。</span><span class="sxs-lookup"><span data-stu-id="255a5-116">As a result, the package iterates through the files in the new data folder, rather than iterating through the files in the original folder that was hard-coded in the package.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="255a5-117">這個教學課程需要 **AdventureWorksDW2012** 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="255a5-117">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="255a5-118">如需如何安裝和部署 **AdventureWorksDW2012**的詳細資訊，請參閱 [CodePlex 上的 Reporting Services 產品範例](https://go.microsoft.com/fwlink/?LinkID=526910)。</span><span class="sxs-lookup"><span data-stu-id="255a5-118">For more information about how to install and deploy **AdventureWorksDW2012**, see [Reporting Services Product Samples on CodePlex](https://go.microsoft.com/fwlink/?LinkID=526910).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="255a5-119">課程工作</span><span class="sxs-lookup"><span data-stu-id="255a5-119">Lesson Tasks</span></span>  
 <span data-ttu-id="255a5-120">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="255a5-120">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="255a5-121">步驟 1:複製第 4 課的封裝</span><span class="sxs-lookup"><span data-stu-id="255a5-121">Step 1: Copying the Lesson 4 Package</span></span>](lesson-5-1-copying-the-lesson-4-package.md)  
  
-   [<span data-ttu-id="255a5-122">步驟 2:啟用和設定封裝組態</span><span class="sxs-lookup"><span data-stu-id="255a5-122">Step 2: Enabling and Configuring Package Configurations</span></span>](lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
-   [<span data-ttu-id="255a5-123">步驟 3：修改 Directory 屬性組態值</span><span class="sxs-lookup"><span data-stu-id="255a5-123">Step 3: Modifying the Directory Property Configuration Value</span></span>](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
-   [<span data-ttu-id="255a5-124">步驟 4：測試第 5 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="255a5-124">Step 4: Testing the Lesson 5 Tutorial Package</span></span>](lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="255a5-125">開始課程</span><span class="sxs-lookup"><span data-stu-id="255a5-125">Start the Lesson</span></span>  
  
-   [<span data-ttu-id="255a5-126">步驟 1:複製第 4 課的封裝</span><span class="sxs-lookup"><span data-stu-id="255a5-126">Step 1: Copying the Lesson 4 Package</span></span>](lesson-5-1-copying-the-lesson-4-package.md)  
  
  
