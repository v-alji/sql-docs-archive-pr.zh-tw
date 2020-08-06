---
title: 新增現有套件的複本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.addcopyexistingpackage.f1
helpviewer_keywords:
- Add Copy of Existing Package dialog box
ms.assetid: ed530b0d-438d-4c93-8e91-13f2b2b6a8b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d535e24fbd13e62cecdb9970a8b9b576b00ddb03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595256"
---
# <a name="add-copy-of-existing-package"></a><span data-ttu-id="fd3fe-102">加入現有封裝的副本</span><span class="sxs-lookup"><span data-stu-id="fd3fe-102">Add Copy of Existing Package</span></span>
  <span data-ttu-id="fd3fe-103">使用 **[加入現有封裝的副本]** 對話方塊，即可將 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、檔案系統，或 SSIS 封裝存放區中所儲存之封裝的副本，加入至 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="fd3fe-103">Use the **Add Copy of Existing Package** dialog box to add a copy of a package stored in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the file system, or the SSIS Package Store to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fd3fe-104">選項。</span><span class="sxs-lookup"><span data-stu-id="fd3fe-104">Options</span></span>  
 <span data-ttu-id="fd3fe-105">**封裝位置**</span><span class="sxs-lookup"><span data-stu-id="fd3fe-105">**Package location**</span></span>  
 <span data-ttu-id="fd3fe-106">選取要從中複製封裝之儲存位置的類型。</span><span class="sxs-lookup"><span data-stu-id="fd3fe-106">Select the type of storage location from which to copy the package.</span></span>  
  
 <span data-ttu-id="fd3fe-107">**Server**</span><span class="sxs-lookup"><span data-stu-id="fd3fe-107">**Server**</span></span>  
 <span data-ttu-id="fd3fe-108">如果是從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或 SSIS 封裝存放區複製，請鍵入伺服器名稱，或是從清單中選取伺服器。</span><span class="sxs-lookup"><span data-stu-id="fd3fe-108">If copying from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or the SSIS Package Store, type a server name or select a server from the list.</span></span>  
  
 <span data-ttu-id="fd3fe-109">**驗證類型**</span><span class="sxs-lookup"><span data-stu-id="fd3fe-109">**Authentication type**</span></span>  
 <span data-ttu-id="fd3fe-110">如果是從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]複製，請選取驗證類型。</span><span class="sxs-lookup"><span data-stu-id="fd3fe-110">If copying from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], select an authentication type.</span></span>  
  
 <span data-ttu-id="fd3fe-111">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="fd3fe-111">**User name**</span></span>  
 <span data-ttu-id="fd3fe-112">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請提供使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="fd3fe-112">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="fd3fe-113">**密碼**</span><span class="sxs-lookup"><span data-stu-id="fd3fe-113">**Password**</span></span>  
 <span data-ttu-id="fd3fe-114">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請提供密碼。</span><span class="sxs-lookup"><span data-stu-id="fd3fe-114">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="fd3fe-115">**封裝路徑**</span><span class="sxs-lookup"><span data-stu-id="fd3fe-115">**Package path**</span></span>  
 <span data-ttu-id="fd3fe-116">輸入封裝路徑，或是按一下瀏覽按鈕 ([...])  ，並找出要複製的封裝。</span><span class="sxs-lookup"><span data-stu-id="fd3fe-116">Type the package path, or click the browse button **(...)** and locate the package to copy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd3fe-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd3fe-117">See Also</span></span>  
 <span data-ttu-id="fd3fe-118">[儲存封裝的副本](../../2014/integration-services/save-copy-of-package.md) </span><span class="sxs-lookup"><span data-stu-id="fd3fe-118">[Save Copy of Package](../../2014/integration-services/save-copy-of-package.md) </span></span>  
 <span data-ttu-id="fd3fe-119">[匯入封裝對話方塊 UI 參考](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fd3fe-119">[Import Package Dialog Box UI Reference](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="fd3fe-120">[匯出封裝對話方塊 UI 參考](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fd3fe-120">[Export Package Dialog Box UI Reference](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="fd3fe-121">[儲存封裝](save-packages.md) </span><span class="sxs-lookup"><span data-stu-id="fd3fe-121">[Save Packages](save-packages.md) </span></span>  
 [<span data-ttu-id="fd3fe-122">匯入和匯出封裝 &#40;SSIS 服務&#41;</span><span class="sxs-lookup"><span data-stu-id="fd3fe-122">Import and Export Packages &#40;SSIS Service&#41;</span></span>](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
