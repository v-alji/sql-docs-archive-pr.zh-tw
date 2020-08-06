---
title: 將套件儲存為套件範本 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- reusing packages
- templates [Integration Services]
ms.assetid: efe66cec-3933-4f6e-8d35-fe3d300de66c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 30bddb5a343e7c7aef279bc66c25be30a2cf1a12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698425"
---
# <a name="save-a-package-as-a-package-template"></a><span data-ttu-id="d59a4-102">將封裝儲存為封裝範本</span><span class="sxs-lookup"><span data-stu-id="d59a4-102">Save a Package as a Package Template</span></span>
  <span data-ttu-id="d59a4-103">本主題描述當您在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中建立新的 Integration Services 封裝時，如何指定及使用自訂封裝做為範本。</span><span class="sxs-lookup"><span data-stu-id="d59a4-103">This topic describes how to designate and use custom packages as templates when you create new Integration Services packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="d59a4-104">根據預設，當您將新封裝加入 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案中時， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 會使用可建立空白封裝的封裝範本。</span><span class="sxs-lookup"><span data-stu-id="d59a4-104">By default, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] uses a package template that creates an empty package when you add a new package to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="d59a4-105">您不能置換這個預設範本，但是可以加入新的範本。</span><span class="sxs-lookup"><span data-stu-id="d59a4-105">You cannot replace this default template, but you can add new templates.</span></span>  
  
 <span data-ttu-id="d59a4-106">您可以指定將多個封裝當作範本使用。</span><span class="sxs-lookup"><span data-stu-id="d59a4-106">You can designate multiple packages to use as templates.</span></span> <span data-ttu-id="d59a4-107">不過您必須先建立封裝，才能將自訂封裝實作成範本。</span><span class="sxs-lookup"><span data-stu-id="d59a4-107">Before you can implement custom packages as templates, you must create the packages.</span></span>  
  
 <span data-ttu-id="d59a4-108">使用自訂封裝作為範本以建立封裝時，新封裝將擁有與範本相同的名稱和 GUID。</span><span class="sxs-lookup"><span data-stu-id="d59a4-108">When you create package using custom packages as templates, the new packages have the same name and GUID as the template.</span></span> <span data-ttu-id="d59a4-109">為了區分這些封裝，您應該更新 `Name` 屬性的值，並為 `ID` 屬性產生新的 GUID。</span><span class="sxs-lookup"><span data-stu-id="d59a4-109">To differentiate among packages you should update the value of the `Name` property and generate a new GUID for the `ID` property.</span></span> <span data-ttu-id="d59a4-110">如需詳細資訊，請參閱 [在 SQL Server 資料工具中建立封裝](create-packages-in-sql-server-data-tools.md) 和 [設定封裝屬性](set-package-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d59a4-110">For more information, see [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) and [Set Package Properties](set-package-properties.md).</span></span>  
  
### <a name="to-designate-a-custom-package-as-a-package-template"></a><span data-ttu-id="d59a4-111">若要將自訂封裝指定成封裝範本</span><span class="sxs-lookup"><span data-stu-id="d59a4-111">To designate a custom package as a package template</span></span>  
  
1.  <span data-ttu-id="d59a4-112">在檔案系統中，尋找要用來當作範本的封裝。</span><span class="sxs-lookup"><span data-stu-id="d59a4-112">In the file system, locate the package that you want to use as template.</span></span>  
  
2.  <span data-ttu-id="d59a4-113">將封裝複製到 DataTransformationItems 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d59a4-113">Copy the package to the DataTransformationItems folder.</span></span> <span data-ttu-id="d59a4-114">依預設，這個資料夾位於 C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject。</span><span class="sxs-lookup"><span data-stu-id="d59a4-114">By default this folder is in C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject.</span></span>  
  
3.  <span data-ttu-id="d59a4-115">對想要當作範本使用的每個封裝重複步驟 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="d59a4-115">Repeat steps 1 and 2 for each package that you want to use as a template.</span></span>  
  
### <a name="to-use-a-custom-package-as-a-package-template"></a><span data-ttu-id="d59a4-116">若要使用自訂封裝作為封裝範本</span><span class="sxs-lookup"><span data-stu-id="d59a4-116">To use a custom package as a package template</span></span>  
  
1.  <span data-ttu-id="d59a4-117">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟您要在其中建立封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="d59a4-117">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in which you want to create a package.</span></span>  
  
2.  <span data-ttu-id="d59a4-118">在方案總管中，以滑鼠右鍵按一下專案，指向 [加入]  ，然後按一下 [新增項目]  。</span><span class="sxs-lookup"><span data-stu-id="d59a4-118">In Solution Explorer, right-click the project, point to **Add**, and then click **New Item**.</span></span>  
  
3.  <span data-ttu-id="d59a4-119">在 [新增項目 -\<project name>] 對話方塊中，按一下要當作範本使用的套件。</span><span class="sxs-lookup"><span data-stu-id="d59a4-119">In the **Add New Item -\<project name>** dialog box, click the package that you want to use as a template.</span></span>  
  
     <span data-ttu-id="d59a4-120">範本清單中包含名稱為 [新增 SSIS 封裝] 的預設封裝範本。</span><span class="sxs-lookup"><span data-stu-id="d59a4-120">The list of templates includes the default package template named New SSIS Package.</span></span> <span data-ttu-id="d59a4-121">封裝圖示識別可當作封裝範本使用的範本。</span><span class="sxs-lookup"><span data-stu-id="d59a4-121">The package icon identifies templates that can be used as package templates.</span></span>  
  
4.  <span data-ttu-id="d59a4-122">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="d59a4-122">Click **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59a4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d59a4-123">See Also</span></span>  
 <span data-ttu-id="d59a4-124">[在 SQL Server Data Tools 中建立封裝](create-packages-in-sql-server-data-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d59a4-124">[Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) </span></span>  
 [<span data-ttu-id="d59a4-125">Integration Services &#40;SSIS&#41; 封裝</span><span class="sxs-lookup"><span data-stu-id="d59a4-125">Integration Services &#40;SSIS&#41; Packages</span></span>](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
