---
title: 查看 Analysis Services 專案的 XML (SSDT) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Analysis Services], viewing XML
ms.assetid: dd1a4bc6-57b5-47df-8619-09f921aa6351
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1c320145be2073c741498bed0f10732ac8d528e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707917"
---
# <a name="view-the-xml-for-an-analysis-services-project-ssdt"></a><span data-ttu-id="d2415-102">檢視 Analysis Services 專案的 XML (SSDT)</span><span class="sxs-lookup"><span data-stu-id="d2415-102">View the XML for an Analysis Services Project (SSDT)</span></span>
  <span data-ttu-id="d2415-103">當您在專案模式中使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫時， [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 會針對專案資料夾中的每一個物件建立 XML 定義。</span><span class="sxs-lookup"><span data-stu-id="d2415-103">When you are working with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in project mode, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] creates an XML definition for each object within the project folder.</span></span> <span data-ttu-id="d2415-104">您可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中檢視每一個物件之 XML 檔案的內容，</span><span class="sxs-lookup"><span data-stu-id="d2415-104">You can view the contents of the XML file for each object within [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="d2415-105">您也可以直接編輯 XML 檔案；但是，大多數情況下不建議您這樣做，因為您所做的變更可能會讓 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]無法讀取該 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="d2415-105">You can also edit the XML file directly; however, this is not recommended in most circumstances as you may make changes that make the XML unreadable by [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d2415-106">您無法檢視整個專案的 xml 程式碼，但是可以檢視每一個物件的程式碼，因為每一個物件都有個別檔案存在。</span><span class="sxs-lookup"><span data-stu-id="d2415-106">You cannot view the xml code for an entire project, but rather you view the code for each object because a separate file exists for each object.</span></span> <span data-ttu-id="d2415-107">若要查看整個專案的程式碼，唯一的方法就是建立專案，並在 .asdatabase 檔案中查看 ASSL 程式碼 \<project name> 。</span><span class="sxs-lookup"><span data-stu-id="d2415-107">The only way to view the code for an entire project is to build the project and view the ASSL code in the \<project name>.asdatabase file.</span></span>  
  
### <a name="to-view-the-xml-code-for-an-object"></a><span data-ttu-id="d2415-108">檢視物件的 XML 程式碼</span><span class="sxs-lookup"><span data-stu-id="d2415-108">To view the XML code for an object</span></span>  
  
1.  <span data-ttu-id="d2415-109">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中開啟 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="d2415-109">Open the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="d2415-110">以滑鼠右鍵按一下方案總管中的物件，然後按一下 [檢視程式碼]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d2415-110">Right-click the object in Solution Explorer and then click **View Code**.</span></span>  
  
     <span data-ttu-id="d2415-111">此物件的 XML 程式碼即會出現在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="d2415-111">The XML code for the object appears in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2415-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2415-112">See Also</span></span>  
 [<span data-ttu-id="d2415-113">建立多個 Analysis Services 專案 &#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="d2415-113">Build Analysis Services Projects &#40;SSDT&#41;</span></span>](build-analysis-services-projects-ssdt.md)  
  
  
