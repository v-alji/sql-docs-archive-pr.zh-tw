---
title: 在 SQL Server Data Tools 中複製封裝 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], copying
- copying packages
- regenerating package GUID
- updating package properties
ms.assetid: 03edc659-e76d-48c0-a749-5f1899b6b507
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bd6ed4dd66ee4755181f5df6f3c1b5466b3f26b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596839"
---
# <a name="copy-a-package-in-sql-server-data-tools"></a><span data-ttu-id="f0471-102">在 SQL Server Data Tools 中複製封裝</span><span class="sxs-lookup"><span data-stu-id="f0471-102">Copy a Package in SQL Server Data Tools</span></span>
  <span data-ttu-id="f0471-103">此主題描述如何透過複製現有的封裝來建立新的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝，以及如何更新這個新封裝的 `Name` 和 `GUID` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f0471-103">This topic describes how to create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package by copying an existing package, and how to update the `Name` and `GUID` properties of the new package.</span></span>  
  
### <a name="to-copy-a-package"></a><span data-ttu-id="f0471-104">若要複製封裝</span><span class="sxs-lookup"><span data-stu-id="f0471-104">To copy a package</span></span>  
  
1.  <span data-ttu-id="f0471-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含要複製之封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="f0471-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package that you want to copy.</span></span>  
  
2.  <span data-ttu-id="f0471-106">在 [方案總管] 中，按兩下封裝。</span><span class="sxs-lookup"><span data-stu-id="f0471-106">In Solution Explorer, double-click the package.</span></span>  
  
3.  <span data-ttu-id="f0471-107">確認是否已在「方案總管」中選取要複製的封裝，或「SSIS 設計師」中包含封裝的索引標籤是否為使用中的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f0471-107">Verify either the package to copy is selected in Solution Explorer or the tab in SSIS Designer that contains the package is the active tab</span></span>  
  
4.  <span data-ttu-id="f0471-108">在 [檔案] 功能表上按一下 [另存新檔] **\<package name>** 。</span><span class="sxs-lookup"><span data-stu-id="f0471-108">On the **File** menu, click **Save \<package name> As**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f0471-109">您必須先在 SSIS 設計師中開啟封裝，[另存新檔]  選項才會出現在 [檔案]  功能表上。</span><span class="sxs-lookup"><span data-stu-id="f0471-109">The package must be opened in SSIS Designer before the **Save As** option appears on the **File** menu.</span></span>  
  
5.  <span data-ttu-id="f0471-110">(選擇性) 瀏覽到不同的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f0471-110">Optionally, browse to a different folder.</span></span>  
  
6.  <span data-ttu-id="f0471-111">更新封裝檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="f0471-111">Update the name of the package file.</span></span> <span data-ttu-id="f0471-112">請務必保留 .dtsx 的副檔名。</span><span class="sxs-lookup"><span data-stu-id="f0471-112">Make sure that you retain the .dtsx file extension.</span></span>  
  
7.  <span data-ttu-id="f0471-113">按一下 [檔案]  。</span><span class="sxs-lookup"><span data-stu-id="f0471-113">Click **Save**.</span></span>  
  
8.  <span data-ttu-id="f0471-114">出現系統提示時，選擇是否更新封裝物件的名稱，以符合檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f0471-114">At the prompt, choose whether to update the name of the package object to match the file name.</span></span> <span data-ttu-id="f0471-115">如果您按一下 [**是]**， `Name` 就會更新封裝的屬性。</span><span class="sxs-lookup"><span data-stu-id="f0471-115">If you click **Yes**, the `Name` property of the package is updated.</span></span> <span data-ttu-id="f0471-116">新的封裝便會加入 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案，並在「 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師」中開啟。</span><span class="sxs-lookup"><span data-stu-id="f0471-116">The new package is added to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project and opened in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
9. <span data-ttu-id="f0471-117">(選擇性) 按一下 **[控制流程]** 索引標籤的背景，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="f0471-117">Optionally, click in the background of the **Control Flow** tab, and the click **Properties**.</span></span>  
  
10. <span data-ttu-id="f0471-118">在 [屬性] 視窗中，按一下識別碼屬性的值，然後在下拉式清單中按一下 [\<Generate New ID>]。</span><span class="sxs-lookup"><span data-stu-id="f0471-118">In the Properties window, click the value of the ID property, and then in the drop-down list click **\<Generate New ID>**.</span></span>  
  
11. <span data-ttu-id="f0471-119">在 **[檔案]** 功能表上按一下 **[儲存選取項目]** 以儲存新封裝。</span><span class="sxs-lookup"><span data-stu-id="f0471-119">On the **File** menu, click **Save Selected Items** to save the new package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0471-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0471-120">See Also</span></span>  
 <span data-ttu-id="f0471-121">[儲存封裝的複本](../../2014/integration-services/save-a-copy-of-a-package.md) </span><span class="sxs-lookup"><span data-stu-id="f0471-121">[Save a Copy of a Package](../../2014/integration-services/save-a-copy-of-a-package.md) </span></span>  
 <span data-ttu-id="f0471-122">[在 SQL Server Data Tools 中建立封裝](create-packages-in-sql-server-data-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f0471-122">[Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) </span></span>  
 [<span data-ttu-id="f0471-123">Integration Services &#40;SSIS&#41; 封裝</span><span class="sxs-lookup"><span data-stu-id="f0471-123">Integration Services &#40;SSIS&#41; Packages</span></span>](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
