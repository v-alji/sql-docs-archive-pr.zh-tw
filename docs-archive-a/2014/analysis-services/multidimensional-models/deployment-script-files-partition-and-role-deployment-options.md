---
title: 指定資料分割和角色部署選項 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- partitions [Analysis Services], deployment options
- Analysis Services deployments, roles
- Analysis Services deployments, partitions
- Analysis Services Deployment Wizard, roles
- Analysis Services Deployment Wizard, partitions
- deploying [Analysis Services], roles
- roles [Analysis Services], deployment options
- deploying [Analysis Services], partitions
- modifying role deployments
- modifying partition deployments
ms.assetid: e9b9ca57-a5cc-4fc0-87b5-305257038d56
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c8dd7bcb482c2d28a18e3039f5acb777b121202
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599697"
---
# <a name="specifying-partition-and-role-deployment-options"></a><span data-ttu-id="38639-102">指定資料分割和角色部署選項</span><span class="sxs-lookup"><span data-stu-id="38639-102">Specifying Partition and Role Deployment Options</span></span>
  <span data-ttu-id="38639-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]部署嚮導會從 d 檔案讀取分割區和角色部署選項 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="38639-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the partition and role deployment options from the \<*project name*>.deploymentoptions file.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="38639-104">當您建立專案時，會建立這個檔案 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="38639-104">creates this file when you build the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="38639-105">建立 d 檔案時，會使用目前專案的資料分割和角色部署選項 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="38639-105">uses the partition and role deployment options of the current project when the \<*project name*>.deploymentoptions file is created.</span></span> <span data-ttu-id="38639-106">如需組態設定的詳細資訊，請參閱 [了解用來建立部署指令碼的輸入檔](deployment-script-files-input-used-to-create-deployment-script.md)。</span><span class="sxs-lookup"><span data-stu-id="38639-106">For more information about configuration settings, see [Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md).</span></span>  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a><span data-ttu-id="38639-107">檢閱資料分割和角色部署選項</span><span class="sxs-lookup"><span data-stu-id="38639-107">Reviewing the Partition and Role Deployment Options</span></span>  
 <span data-ttu-id="38639-108">D 檔案中的部署選項 \<*project name*> 包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="38639-108">The deployment options in the \<*project name*>.deploymentoptions file include the following:</span></span>  
  
 <span data-ttu-id="38639-109">**資料分割部署選項**</span><span class="sxs-lookup"><span data-stu-id="38639-109">**Partition deployment options**</span></span>  
 <span data-ttu-id="38639-110">\<*project name*>D 檔案會指定是否保留或覆寫目的地資料庫中的現有分割區 (預設) 。</span><span class="sxs-lookup"><span data-stu-id="38639-110">The \<*project name*>.deploymentoptions file specifies whether existing partitions in the destination database are retained or overwritten (default).</span></span> <span data-ttu-id="38639-111">如果保留現有的資料分割，則只會部署新的資料分割，而所有現有的量值群組上的資料分割與彙總設計都會保持不變。</span><span class="sxs-lookup"><span data-stu-id="38639-111">If existing partitions are retained, only new partitions will be deployed, and the partitions and aggregation designs on all existing measure groups are left unchanged.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38639-112">如果刪除存在有資料分割的量值群組，則也會自動刪除資料分割。</span><span class="sxs-lookup"><span data-stu-id="38639-112">If the measure group in which the partition exists is deleted, the partition is automatically deleted.</span></span>  
  
 <span data-ttu-id="38639-113">**角色部署選項**</span><span class="sxs-lookup"><span data-stu-id="38639-113">**Role deployment options**</span></span>  
 <span data-ttu-id="38639-114">D 檔案會 \<*project name*> 指定下列其中一個角色部署選項：</span><span class="sxs-lookup"><span data-stu-id="38639-114">The \<*project name*>.deploymentoptions file specifies one of the following role deployment options:</span></span>  
  
-   <span data-ttu-id="38639-115">保留目的地資料庫中之現有的角色和角色成員，僅部署新角色和角色成員。</span><span class="sxs-lookup"><span data-stu-id="38639-115">Existing roles and role members in the destination database are retained, and only new roles and role members are deployed.</span></span>  
  
-   <span data-ttu-id="38639-116">以正在部署的角色和成員取代目的地資料庫中之所有現有的角色和成員。</span><span class="sxs-lookup"><span data-stu-id="38639-116">All existing roles and members in the destination database are replaced by the roles and members being deployed.</span></span>  
  
-   <span data-ttu-id="38639-117">保留目的地資料庫中之現有的角色和角色成員，而且不部署新角色。</span><span class="sxs-lookup"><span data-stu-id="38639-117">Existing roles and role members in the destination database are retained, and no new roles are deployed.</span></span>  
  
-   <span data-ttu-id="38639-118">**注意** ：保留現有角色與成員時，與這些角色相關聯的權限會重設為無。</span><span class="sxs-lookup"><span data-stu-id="38639-118">**Note** When existing roles and members are retained, the permissions associated with those roles are reset to none.</span></span> <span data-ttu-id="38639-119">安全性權限包含在它們所保護的物件中，而非與它們相關聯的安全性角色。</span><span class="sxs-lookup"><span data-stu-id="38639-119">Security permissions are contained by the objects they secure, not by the security roles with which they are associated.</span></span> <span data-ttu-id="38639-120">如需如何使用 Analysis Services 部署嚮導來處理此行為的詳細資訊，請參閱 Microsoft 知識庫中的「保留角色和成員」。</span><span class="sxs-lookup"><span data-stu-id="38639-120">For more information about how to work with this behavior by using the Analysis Service Deployment Wizard, see 'Retain Roles and Members' in the Microsoft Knowledge Base.</span></span>  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a><span data-ttu-id="38639-121">修改資料分割和角色部署選項</span><span class="sxs-lookup"><span data-stu-id="38639-121">Modifying the Partition and Role Deployment Options</span></span>  
 <span data-ttu-id="38639-122">您可能必須 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 使用與 d 檔案中儲存的不同分割區和角色選項，來部署專案 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="38639-122">You may have to deploy the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project using different partition and role options than those stored in the \<*project name*>.deploymentoptions file.</span></span> <span data-ttu-id="38639-123">例如，您可能會想要保留現有的分割區、角色和角色成員，而不是取代所有現有的分割區、角色和成員，如 d 檔案中所示 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="38639-123">For example, you may want to retain existing partitions, roles, and role members, instead of replacing all existing partitions, roles, and members as indicated in the \<*project name*>.deploymentoptions file.</span></span>  
  
 <span data-ttu-id="38639-124">若要在專案中修改資料分割和角色的部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，您無法變更專案內的資料分割和角色設定，因為中的 [ *\<project name>* **屬性頁面**] 對話方塊 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 並未顯示這些選項。</span><span class="sxs-lookup"><span data-stu-id="38639-124">To modify the deployment of partitions and roles in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you cannot change the partition and roles settings within the project because the *\<project name>* **Properties Pages** dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] does not display these options.</span></span> <span data-ttu-id="38639-125">如果您想要變更角色和分割區的部署選項，您必須在 d 檔案內變更此資訊 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="38639-125">If you want to change the deployment options for roles and partitions, you must change this information within the \<*project name*>.deploymentoptions file itself.</span></span> <span data-ttu-id="38639-126">下列程式描述如何變更 d 檔案內的資料分割和角色部署選項 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="38639-126">The following procedure describes how to change the partition and role deployment options within the \<*project name*>.deploymentoptions file.</span></span>  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a><span data-ttu-id="38639-127">在已產生輸入檔之後，變更資料分割或角色的部署</span><span class="sxs-lookup"><span data-stu-id="38639-127">To change the deployment of partitions or roles after the input files have been generated</span></span>  
  
-   <span data-ttu-id="38639-128">以互動方式執行 [[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈]，並在 [Partition and Role Deployment Options (資料分割和角色部署選項)]\*\*\*\* 頁面上，指定資料分割和角色的新部署選項。</span><span class="sxs-lookup"><span data-stu-id="38639-128">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard interactively, and on the **Partition and Role Deployment Options** page, specify new deployment options for the partitions and roles.</span></span>  
  
     <span data-ttu-id="38639-129">-或-</span><span class="sxs-lookup"><span data-stu-id="38639-129">-or-</span></span>  
  
-   <span data-ttu-id="38639-130">在命令提示字元下執行 [ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈]，並將精靈設定為以回應檔案模式執行。</span><span class="sxs-lookup"><span data-stu-id="38639-130">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt, and set the wizard to run in answer file mode.</span></span> <span data-ttu-id="38639-131"> (需回應檔案模式的詳細資訊，請參閱執行[Analysis Services 部署嚮導](running-the-analysis-services-deployment-wizard.md)。 ) </span><span class="sxs-lookup"><span data-stu-id="38639-131">(For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).)</span></span>  
  
     <span data-ttu-id="38639-132">-或-</span><span class="sxs-lookup"><span data-stu-id="38639-132">-or-</span></span>  
  
-   <span data-ttu-id="38639-133">\<*project name*>在任何文字編輯器中開啟 d，並手動變更選項。</span><span class="sxs-lookup"><span data-stu-id="38639-133">Open the \<*project name*>.deploymentoptions in any text editor and manually change the options.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38639-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38639-134">See Also</span></span>  
 <span data-ttu-id="38639-135">[指定安裝目標](deployment-script-files-specifying-the-installation-target.md) </span><span class="sxs-lookup"><span data-stu-id="38639-135">[Specifying the Installation Target](deployment-script-files-specifying-the-installation-target.md) </span></span>  
 <span data-ttu-id="38639-136">[指定解決方案部署的設定](deployment-script-files-solution-deployment-config-settings.md) </span><span class="sxs-lookup"><span data-stu-id="38639-136">[Specifying Configuration Settings for Solution Deployment](deployment-script-files-solution-deployment-config-settings.md) </span></span>  
 [<span data-ttu-id="38639-137">指定處理選項</span><span class="sxs-lookup"><span data-stu-id="38639-137">Specifying Processing Options</span></span>](deployment-script-files-specifying-processing-options.md)  
  
  
