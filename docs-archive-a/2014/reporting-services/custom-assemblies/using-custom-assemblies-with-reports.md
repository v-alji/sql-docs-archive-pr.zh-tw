---
title: 將自訂組件與報表搭配使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f77b9da44ebb57617bd45e43d1e1e847e9074662
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688622"
---
# <a name="using-custom-assemblies-with-reports"></a><span data-ttu-id="7faee-102">將自訂組件與報表搭配使用</span><span class="sxs-lookup"><span data-stu-id="7faee-102">Using Custom Assemblies with Reports</span></span>
  <span data-ttu-id="7faee-103">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中，您可以為報表項目值、樣式和格式撰寫自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="7faee-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can write custom code for report item values, styles, and formatting.</span></span> <span data-ttu-id="7faee-104">例如，您可以使用自訂程式碼來根據地區設定格式化貨幣，以特殊格式設定某些值的旗標，或是為您的公司套用其他實施中的商務規則。</span><span class="sxs-lookup"><span data-stu-id="7faee-104">For example, you can use custom code to format currencies based on locale, flag certain values with special formatting, or apply other business rules that are in practice for your company.</span></span> <span data-ttu-id="7faee-105">在您的報表中包含此程式碼的其中一個方法是，使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 您可以從報表定義檔案中參考的來建立自訂程式碼元件。</span><span class="sxs-lookup"><span data-stu-id="7faee-105">One way to include this code in your reports is to create a custom code assembly using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] that you can reference from within your report definition files.</span></span> <span data-ttu-id="7faee-106">伺服器會在報表執行時呼叫自訂組件中的函數。</span><span class="sxs-lookup"><span data-stu-id="7faee-106">The server calls the functions in your custom assemblies when a report is run.</span></span> <span data-ttu-id="7faee-107">自訂組件可用以擷取您計劃在報表中使用的特定函數。</span><span class="sxs-lookup"><span data-stu-id="7faee-107">Custom assemblies can be used to retrieve specialized functions that you plan to use in your reports.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7faee-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="7faee-108">In This Section</span></span>  
 [<span data-ttu-id="7faee-109">參考在 RDL 檔案中的組件</span><span class="sxs-lookup"><span data-stu-id="7faee-109">Referencing Assemblies in an RDL File</span></span>](referencing-assemblies-in-an-rdl-file.md)  
 <span data-ttu-id="7faee-110">描述如何參考報表定義語言檔案中的自訂組件。</span><span class="sxs-lookup"><span data-stu-id="7faee-110">Describes how to reference your custom assemblies in a report definition language file.</span></span>  
  
 [<span data-ttu-id="7faee-111">部署自訂組件</span><span class="sxs-lookup"><span data-stu-id="7faee-111">Deploying a Custom Assembly</span></span>](deploying-a-custom-assembly.md)  
 <span data-ttu-id="7faee-112">描述如何將自訂組件部署到報表設計師與報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="7faee-112">Describes how to deploy a custom assembly to Report Designer and the report server.</span></span>  
  
 [<span data-ttu-id="7faee-113">使用強式名稱自訂組件</span><span class="sxs-lookup"><span data-stu-id="7faee-113">Using Strong-Named Custom Assemblies</span></span>](using-strong-named-custom-assemblies.md)  
 <span data-ttu-id="7faee-114">描述如何使用自訂組件與強式名稱。</span><span class="sxs-lookup"><span data-stu-id="7faee-114">Describes how to use custom assemblies with strong names.</span></span>  
  
 [<span data-ttu-id="7faee-115">自訂組件中的判斷提示權限</span><span class="sxs-lookup"><span data-stu-id="7faee-115">Asserting Permissions in Custom Assemblies</span></span>](asserting-permissions-in-custom-assemblies.md)  
 <span data-ttu-id="7faee-116">描述如何使用有限且特定的權限來部署自訂組件，以及如何判斷提示程式碼中的權限。</span><span class="sxs-lookup"><span data-stu-id="7faee-116">Describes how to deploy custom assemblies with limited and specific permissions and how to assert those permissions in code.</span></span>  
  
 [<span data-ttu-id="7faee-117">透過運算式存取自訂組件</span><span class="sxs-lookup"><span data-stu-id="7faee-117">Accessing Custom Assemblies Through Expressions</span></span>](accessing-custom-assemblies-through-expressions.md)  
 <span data-ttu-id="7faee-118">描述如何呼叫自訂組件方法做為報表定義中的報表運算式。</span><span class="sxs-lookup"><span data-stu-id="7faee-118">Describes how to call custom assembly methods as report expressions in your report definitions.</span></span>  
  
 [<span data-ttu-id="7faee-119">初始化自訂組件物件</span><span class="sxs-lookup"><span data-stu-id="7faee-119">Initializing Custom Assembly Objects</span></span>](initializing-custom-assembly-objects.md)  
 <span data-ttu-id="7faee-120">描述如何初始化從報表呼叫之自訂組件物件的值。</span><span class="sxs-lookup"><span data-stu-id="7faee-120">Describes how to initialize values for custom assembly objects called from a report.</span></span>  
  
 [<span data-ttu-id="7faee-121">如何：針對自訂組件進行偵錯</span><span class="sxs-lookup"><span data-stu-id="7faee-121">How to: Debug Custom Assemblies</span></span>](how-to-debug-custom-assemblies.md)  
 <span data-ttu-id="7faee-122">說明如何偵錯您的自訂組件程式碼。</span><span class="sxs-lookup"><span data-stu-id="7faee-122">Describes how to debug your custom assembly code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7faee-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7faee-123">See Also</span></span>  
 [<span data-ttu-id="7faee-124">報表定義語言 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7faee-124">Report Definition Language &#40;SSRS&#41;</span></span>](../reports/report-definition-language-ssrs.md)  
  
  
