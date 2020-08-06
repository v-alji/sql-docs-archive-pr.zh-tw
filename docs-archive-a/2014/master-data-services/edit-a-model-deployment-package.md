---
title: 編輯模型部署套件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6b0fdb7d-83dd-4392-9011-4ae642c471f1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b8bfd7083e2ba763d15a405266260b5a096c8378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607417"
---
# <a name="edit-a-model-deployment-package"></a><span data-ttu-id="c077d-102">編輯模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="c077d-102">Edit a Model Deployment Package</span></span>
  <span data-ttu-id="c077d-103">此主題描述如何在 MDS 中部署模型的選定部分，而不是整個模型。</span><span class="sxs-lookup"><span data-stu-id="c077d-103">This topic describes how to deploy selected parts of a model in MDS, rather than an entire model.</span></span> <span data-ttu-id="c077d-104">若要這樣做，請使用模型封裝編輯器編輯 MDS 模型封裝。</span><span class="sxs-lookup"><span data-stu-id="c077d-104">To do so, you edit an MDS model package using the Model Package Editor.</span></span>  
  
 <span data-ttu-id="c077d-105">模型封裝編輯器精靈可讓您選取要併入 MDS 封裝中的特定實體、衍生階層、訂閱檢視和模型中的商務規則，並在之後加以部署。</span><span class="sxs-lookup"><span data-stu-id="c077d-105">The Model Package Editor wizard enables you to select the specific entities, derived hierarchies, subscription views, and business rules in a model that you want to include in an MDS package, and then later deploy.</span></span> <span data-ttu-id="c077d-106">您可以不處理模型中不想要部署的部分。</span><span class="sxs-lookup"><span data-stu-id="c077d-106">You can leave out those parts of the model that you do not want to deploy.</span></span> <span data-ttu-id="c077d-107">當您選取實體時，也會自動選取該實體中的所有相依物件。</span><span class="sxs-lookup"><span data-stu-id="c077d-107">When you select an entity, all of the dependent objects in that entity are also automatically selected.</span></span>  
  
 <span data-ttu-id="c077d-108">您會使用模型封裝編輯器來選取封裝檔案中模型的部分，這個檔案是由 MDSModelDeploy 工具 (它所建立的封裝檔案包含物件和資料) 或模型部署精靈 (它所建立的檔案只包含模型結構) 所建立。</span><span class="sxs-lookup"><span data-stu-id="c077d-108">You use the Model Package Editor to select parts of a model in a package file that was created by either the MDSModelDeploy tool (which creates a package file that includes objects and data) or the Model Deployment wizard (which creates a file that includes only the model structure).</span></span> <span data-ttu-id="c077d-109">在編輯封裝中的模型之後，您會使用 MDSModelDeploy 工具來部署物件和資料，或是使用模型部署精靈，只部署模型結構。</span><span class="sxs-lookup"><span data-stu-id="c077d-109">After editing the model in the package, you use the MDSModelDeploy tool to deploy objects and data, or the Model Deployment wizard to deploy just the model structure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c077d-110">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="c077d-110">Prerequisites</span></span>  
 <span data-ttu-id="c077d-111">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="c077d-111">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="c077d-112">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="c077d-112">You must be a model administrator.</span></span> <span data-ttu-id="c077d-113">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c077d-113">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="c077d-114">模型封裝必須存在，才能供您編輯。</span><span class="sxs-lookup"><span data-stu-id="c077d-114">A model package must exist for you to edit.</span></span> <span data-ttu-id="c077d-115">如需詳細資訊，請參閱[部署模型 &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md) 和 [使用精靈建立模型部署封裝](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)或[使用 MDSModelDeploy 建立模型部署封裝](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)。</span><span class="sxs-lookup"><span data-stu-id="c077d-115">For more information, see [Deploying Models &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md) and [Create a Model Deployment Package by Using the Wizard](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md) or [Create a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
### <a name="to-edit-a-model-deployment-package"></a><span data-ttu-id="c077d-116">若要編輯模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="c077d-116">To edit a model deployment package</span></span>  
  
1.  <span data-ttu-id="c077d-117">在 MDS 伺服器上的 Windows Explorer 中，移至*磁片磁碟機*： \PROGRAM Files\Microsoft SQL Server\120\Master Data services\configuration。</span><span class="sxs-lookup"><span data-stu-id="c077d-117">In Windows Explorer on the MDS server, move to *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
2.  <span data-ttu-id="c077d-118">執行 ModelPackageEditor.exe。</span><span class="sxs-lookup"><span data-stu-id="c077d-118">Execute ModelPackageEditor.exe.</span></span>  
  
3.  <span data-ttu-id="c077d-119">在模型封裝編輯器精靈中，按一下 [瀏覽]\*\*\*\*，並移至包含套件的資料夾，然後選取套件，再按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c077d-119">In the Model Package Editor wizard, click **Browse**, move to the folder containing your packages, select a package, and then click **Open**.</span></span> <span data-ttu-id="c077d-120">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="c077d-120">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="c077d-121">選取這些實體、衍生階層、訂閱檢視或是您想要部署的商務規則。</span><span class="sxs-lookup"><span data-stu-id="c077d-121">Select those entities, derived hierarchies, subscriptions views, or business rules that you want to deploy.</span></span> <span data-ttu-id="c077d-122">取消選取您不想要部署的項目。</span><span class="sxs-lookup"><span data-stu-id="c077d-122">Deselect those that you do not want to deploy.</span></span> <span data-ttu-id="c077d-123">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="c077d-123">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="c077d-124">驗證要部署之選取項目的清單。</span><span class="sxs-lookup"><span data-stu-id="c077d-124">Verify the list of selections to deploy.</span></span> <span data-ttu-id="c077d-125">若要變更，請按一下 [上一步]\*\*\*\*，並重複步驟 4。</span><span class="sxs-lookup"><span data-stu-id="c077d-125">To change, click **Back** and repeat step 4.</span></span>  
  
6.  <span data-ttu-id="c077d-126">按一下 [瀏覽]\*\*\*\* 移至您想要用來儲存部分套件的資料夾，然後輸入部分套件的檔案名稱 (副檔名為 .pkg)。</span><span class="sxs-lookup"><span data-stu-id="c077d-126">Click **Browse**, move to the folder that you want to save the partial package in, and then enter the file name of the partial package (with a .pkg extension).</span></span> <span data-ttu-id="c077d-127">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="c077d-127">Click **Save**.</span></span>  
  
7.  <span data-ttu-id="c077d-128">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="c077d-128">Click **Finish**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c077d-129">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c077d-129">Next Steps</span></span>  
  
-   [<span data-ttu-id="c077d-130">使用精靈部署模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="c077d-130">Deploy a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)  
  
-   [<span data-ttu-id="c077d-131">使用 MDSModelDeploy 部署模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="c077d-131">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  
