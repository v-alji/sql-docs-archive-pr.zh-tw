---
title: 轉換成封裝部署模型對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.bids.converttolegacydeployment.f1
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b52932ad26f8cebd2e67b0025f4b881241119f6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596841"
---
# <a name="convert-to-package-deployment-model-dialog-box"></a><span data-ttu-id="36d27-102">轉換成封裝部署模型對話方塊</span><span class="sxs-lookup"><span data-stu-id="36d27-102">Convert to Package Deployment Model Dialog Box</span></span>
  <span data-ttu-id="36d27-103">**[轉換成封裝部署模型]** 命令可讓您在檢查專案和專案中的每個封裝是否與該模型相容之後，將封裝轉換成封裝部署模型。</span><span class="sxs-lookup"><span data-stu-id="36d27-103">The **Convert to Package Deployment Model** command allows you to convert a package to the package deployment model after checking the project and each package in the project for compatibility with that model.</span></span> <span data-ttu-id="36d27-104">如果某個封裝使用專案部署模型獨有的功能 (例如參數)，則無法轉換該封裝。</span><span class="sxs-lookup"><span data-stu-id="36d27-104">If a package uses features unique to the project deployment model, such as parameters, then the package cannot be converted.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="36d27-105">工作清單</span><span class="sxs-lookup"><span data-stu-id="36d27-105">Task List</span></span>  
 <span data-ttu-id="36d27-106">將封裝轉換成封裝部署模型需要兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="36d27-106">Converting a package to the package deployment model requires two steps.</span></span>  
  
1.  <span data-ttu-id="36d27-107">當您從 **[專案]** 功能表選取 **[轉換成封裝部署模型]** 命令時，會檢查專案和每個封裝是否與此模型相容。</span><span class="sxs-lookup"><span data-stu-id="36d27-107">When you select the **Convert to Package Deployment Model** command from the **Project** menu, the project and each package are checked for compatibility with this model.</span></span> <span data-ttu-id="36d27-108">結果會顯示在 **[結果]** 資料表中。</span><span class="sxs-lookup"><span data-stu-id="36d27-108">The results are displayed in the **Results** table.</span></span>  
  
     <span data-ttu-id="36d27-109">如果專案或封裝無法通過相容性測試，按一下 **[結果]** 資料行中的 **[失敗]** ，可取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="36d27-109">If the project or a package fails the compatibility test, click **Failed** in the **Result** column for more information.</span></span> <span data-ttu-id="36d27-110">按一下 **[儲存報表]** ，將此資訊的副本儲存到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="36d27-110">Click **Save Report** to save a copy of this information to a text file.</span></span>  
  
2.  <span data-ttu-id="36d27-111">如果專案和所有封裝通過相容性測試，則按一下 **[確定]** 以轉換封裝。</span><span class="sxs-lookup"><span data-stu-id="36d27-111">If the project and all packages pass the compatibility test, then click **OK** to convert the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36d27-112">若要將專案轉換為專案部署模型，請使用 **[Integration Services 專案轉換精靈]**。</span><span class="sxs-lookup"><span data-stu-id="36d27-112">To convert a project to the project deployment model, use the **Integration Services Project Conversion Wizard**.</span></span> <span data-ttu-id="36d27-113">如需相關資訊，請參閱 [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="36d27-113">For more information, see [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d27-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36d27-114">See Also</span></span>  
 <span data-ttu-id="36d27-115">[專案和套件的部署](packages/deploy-integration-services-ssis-projects-and-packages.md) </span><span class="sxs-lookup"><span data-stu-id="36d27-115">[Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md) </span></span>  
 <span data-ttu-id="36d27-116">[&#40;SSIS&#41;的套件部署](packages/legacy-package-deployment-ssis.md) </span><span class="sxs-lookup"><span data-stu-id="36d27-116">[Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md) </span></span>  
 [<span data-ttu-id="36d27-117">Integration Services 專案轉換精靈</span><span class="sxs-lookup"><span data-stu-id="36d27-117">Integration Services Project Conversion Wizard</span></span>](../../2014/integration-services/integration-services-project-conversion-wizard.md)  
  
  
