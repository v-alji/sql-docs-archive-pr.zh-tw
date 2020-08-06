---
title: 第6課：搭配專案部署模型使用參數 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4bdc6b9dfc019822d6cf1bd9ec7d89ffcc5ea5e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593434"
---
# <a name="lesson-6-using-parameters-with-the-project-deployment-model"></a><span data-ttu-id="70ea4-102">第 6 課：搭配專案部署模型使用參數</span><span class="sxs-lookup"><span data-stu-id="70ea4-102">Lesson 6: Using Parameters with the Project Deployment Model</span></span>
  <span data-ttu-id="70ea4-103">SQL Server 2012 引進了新的部署模型，讓您可以將專案部署到 Integration Services 伺服器。</span><span class="sxs-lookup"><span data-stu-id="70ea4-103">SQL Server 2012 introduces a new deployment model where you can deploy your projects to the Integration Services server.</span></span> <span data-ttu-id="70ea4-104">Integration Services 伺服器可讓您管理及執行封裝，以及設定封裝的執行值。</span><span class="sxs-lookup"><span data-stu-id="70ea4-104">The Integration Services server enables you to manage and run packages, and to configure runtime values for packages.</span></span>  
  
 <span data-ttu-id="70ea4-105">在這一課，您將修改在[第5課：新增封裝部署模型的封裝](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)設定中所建立的封裝，以使用專案部署模型。</span><span class="sxs-lookup"><span data-stu-id="70ea4-105">In this lesson, you will modify the package that you created in [Lesson 5: Adding Package Configurations for the Package Deployment Model](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) to use the Project Deployment Model.</span></span> <span data-ttu-id="70ea4-106">您會以參數取代組態值來指定範例資料位置。</span><span class="sxs-lookup"><span data-stu-id="70ea4-106">You replace the configuration value with a parameter to specify the sample data location.</span></span> <span data-ttu-id="70ea4-107">您也可以複製此教學課程所包含之已完成的第 5 課封裝。</span><span class="sxs-lookup"><span data-stu-id="70ea4-107">You can also copy the completed Lesson 5 package that is included with the tutorial.</span></span>  
  
 <span data-ttu-id="70ea4-108">使用 Integration Services 專案組態精靈時，您可將專案轉換成專案部署模型，並可使用參數 (而非組態值) 來設定目錄屬性。</span><span class="sxs-lookup"><span data-stu-id="70ea4-108">Using the Integration Services Project Configuration Wizard, you will convert the project to the Project Deployment Model and use a Parameter rather than a configuration value to set the Directory property.</span></span> <span data-ttu-id="70ea4-109">這一課的部分內容涵蓋了將現有的 SSIS 封裝轉換成新專案部署模型的步驟。</span><span class="sxs-lookup"><span data-stu-id="70ea4-109">This lesson partially covers the steps you would follow to convert existing SSIS packages to the new Project Deployment Model.</span></span>  
  
 <span data-ttu-id="70ea4-110">當您重新執行套件時，Integration Services 服務會使用參數來填入變數的值，然後此變數會更新目錄屬性。</span><span class="sxs-lookup"><span data-stu-id="70ea4-110">When you run the package again, the Integration Services service uses the parameter to populate the value of the variable, and the variable in turn updates the Directory property.</span></span> <span data-ttu-id="70ea4-111">因此，封裝會反覆執行此參數值所指定之新資料夾中的檔案，而不反覆執行封裝組態檔中所設定之資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="70ea4-111">As a result, the package iterates through the files in the new data folder specified by the parameter value rather than the folder that was set in the package configuration file.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="70ea4-112">這個教學課程需要 **AdventureWorksDW2012** 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="70ea4-112">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="70ea4-113">如需如何安裝及部署 **AdventureWorksDW2012**的詳細資訊，請參閱 [安裝 SQL Server 範例和範例資料庫的考量](https://technet.microsoft.com/library/ms161556%28v=sql.105%29)。</span><span class="sxs-lookup"><span data-stu-id="70ea4-113">For more information about how to install and deploy **AdventureWorksDW2012**, see [Considerations for Installing SQL Server Samples and Sample Databases](https://technet.microsoft.com/library/ms161556%28v=sql.105%29).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="70ea4-114">課程工作</span><span class="sxs-lookup"><span data-stu-id="70ea4-114">Lesson Tasks</span></span>  
 <span data-ttu-id="70ea4-115">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="70ea4-115">This lesson contains the following tasks:</span></span>  
  
1.  [<span data-ttu-id="70ea4-116">步驟 1:複製第 5 課的封裝</span><span class="sxs-lookup"><span data-stu-id="70ea4-116">Step 1: Copying the Lesson 5 Package</span></span>](lesson-6-1-copying-the-lesson-5-package.md)  
  
2.  [<span data-ttu-id="70ea4-117">步驟 2:將專案轉換成專案部署模型</span><span class="sxs-lookup"><span data-stu-id="70ea4-117">Step 2: Converting the Project to the Project Deployment Model</span></span>](lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [<span data-ttu-id="70ea4-118">步驟 3：測試第 6 課的封裝</span><span class="sxs-lookup"><span data-stu-id="70ea4-118">Step 3: Testing the Lesson 6 Package</span></span>](lesson-6-3-testing-the-lesson-6-package.md)  
  
4.  [<span data-ttu-id="70ea4-119">步驟 4：部署第 6 課的封裝</span><span class="sxs-lookup"><span data-stu-id="70ea4-119">Step 4: Deploying the Lesson 6 Package</span></span>](lesson-6-4-deploying-the-lesson-6-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="70ea4-120">開始課程</span><span class="sxs-lookup"><span data-stu-id="70ea4-120">Start the Lesson</span></span>  
 [<span data-ttu-id="70ea4-121">步驟 1:複製第 5 課的封裝</span><span class="sxs-lookup"><span data-stu-id="70ea4-121">Step 1: Copying the Lesson 5 Package</span></span>](lesson-6-1-copying-the-lesson-5-package.md)  
  
  
