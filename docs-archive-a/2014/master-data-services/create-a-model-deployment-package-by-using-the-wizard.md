---
title: 使用精靈建立模型部署套件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], creating
- models [Master Data Services], creating a deployment package
- creating packages [Master Data Services]
ms.assetid: b24ec4c2-1378-4c72-ac69-4ec2647030f0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: abb30f9d8e08d8eec8e04960b61575da3a1dbcc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606392"
---
# <a name="create-a-model-deployment-package-by-using-the-wizard"></a><span data-ttu-id="3924d-102">使用精靈建立模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="3924d-102">Create a Model Deployment Package by Using the Wizard</span></span>
  <span data-ttu-id="3924d-103">使用 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 模型部署精靈僅建立模型物件的封裝。</span><span class="sxs-lookup"><span data-stu-id="3924d-103">Use the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] model deployment wizard to create a package of the model objects only.</span></span> <span data-ttu-id="3924d-104">如果您需要在套件中包含資料，請參閱 [使用 MDSModelDeploy 建立模型部署封裝](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)。</span><span class="sxs-lookup"><span data-stu-id="3924d-104">If you need to include data in the package, see [Create a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3924d-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="3924d-105">Prerequisites</span></span>  
 <span data-ttu-id="3924d-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="3924d-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="3924d-107">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式中，您必須擁有存取 [系統管理]\*\*\*\* 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="3924d-107">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="3924d-108">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="3924d-108">You must be a model administrator.</span></span> <span data-ttu-id="3924d-109">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3924d-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="3924d-110">模型必須存在，才能建立其封裝。</span><span class="sxs-lookup"><span data-stu-id="3924d-110">A model must exist for you to create a package of.</span></span> <span data-ttu-id="3924d-111">如需詳細資訊，請參閱[建立模型 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3924d-111">For more information, see [Create a Model &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md).</span></span>  
  
### <a name="to-create-a-model-deployment-package"></a><span data-ttu-id="3924d-112">若要建立模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="3924d-112">To create a model deployment package</span></span>  
  
1.  <span data-ttu-id="3924d-113">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="3924d-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="3924d-114">在 [模型檢視]\*\*\*\* 頁面上，從功能表列指向 [系統]\*\*\*\*，然後按一下 [部署]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3924d-114">On the **Model View** page, from the menu bar, point to **System** and click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="3924d-115">按一下 [模型部署精靈]\*\*\*\* 上的 [建立]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3924d-115">On the **Model Deployment Wizard**, click **Create**.</span></span>  
  
4.  <span data-ttu-id="3924d-116">在 [建立封裝]\*\*\*\* 頁面上，選取 [模型]\*\*\*\* 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="3924d-116">On the **Create Package** page, select a model from the **Model** list.</span></span>  
  
5.  <span data-ttu-id="3924d-117">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="3924d-117">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="3924d-118">按一下 [下載] 。</span><span class="sxs-lookup"><span data-stu-id="3924d-118">Click **Download**.</span></span>  
  
7.  <span data-ttu-id="3924d-119">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="3924d-119">Save the file.</span></span>  
  
8.  <span data-ttu-id="3924d-120">按一下 [關閉]\*\*\*\* 以關閉精靈。</span><span class="sxs-lookup"><span data-stu-id="3924d-120">Click **Close** to close the wizard.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3924d-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3924d-121">Next Steps</span></span>  
  
-   [<span data-ttu-id="3924d-122">使用精靈部署模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="3924d-122">Deploy a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="3924d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3924d-123">See Also</span></span>  
 [<span data-ttu-id="3924d-124">部署模型 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3924d-124">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
