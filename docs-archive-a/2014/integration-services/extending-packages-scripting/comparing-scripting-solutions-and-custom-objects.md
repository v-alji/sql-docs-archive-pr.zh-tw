---
title: 比較指令碼解決方案和自訂物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- managed tasks [Integration Services]
- Script task [Integration Services], vs. custom managed tasks
- SSIS Script task, vs. custom managed tasks
- custom tasks [Integration Services], scripts
ms.assetid: c0aea822-a21e-44e1-a3d3-8777bd0a1c34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: acf6faf9cdd78e951b8298c4e3b144d3444fb1ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592161"
---
# <a name="comparing-scripting-solutions-and-custom-objects"></a><span data-ttu-id="9962f-102">比較指令碼方案和自訂物件</span><span class="sxs-lookup"><span data-stu-id="9962f-102">Comparing Scripting Solutions and Custom Objects</span></span>
  <span data-ttu-id="9962f-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 指令碼工作或是指令碼元件可以實作許多可能會應用於自訂 Managed 工作或資料流程元件的相同功能。</span><span class="sxs-lookup"><span data-stu-id="9962f-103">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Script task or Script component can implement much of the same functionality that is possible in a custom managed task or data flow component.</span></span> <span data-ttu-id="9962f-104">以下是可協助您針對需求選擇適當類型之工作的一些考量：</span><span class="sxs-lookup"><span data-stu-id="9962f-104">Here are some considerations to help you choose the appropriate type of task for your needs:</span></span>  
  
-   <span data-ttu-id="9962f-105">如果組態或功能是個別封裝特有的，您應該使用指令碼工作或指令碼元件，而不是開發自訂物件。</span><span class="sxs-lookup"><span data-stu-id="9962f-105">If the configuration or functionality is specific to an individual package, you should use the Script task or the Script component instead of a developing a custom object.</span></span>  
  
-   <span data-ttu-id="9962f-106">如果功能是一般性的，而且未來可能用於其他封裝或是由其他開發人員使用，您應該建立自訂物件，而不是使用指令碼方案。</span><span class="sxs-lookup"><span data-stu-id="9962f-106">If the functionality is generic, and might be used in the future for other packages and by other developers, you should create a custom object instead of using a scripting solution.</span></span> <span data-ttu-id="9962f-107">您可以在任何封裝中使用自訂物件，然而指令碼只能在建立它的封裝中使用。</span><span class="sxs-lookup"><span data-stu-id="9962f-107">You can use a custom object in any package, whereas a script can be used only in the package for which it was created.</span></span>  
  
-   <span data-ttu-id="9962f-108">如果程式碼將在相同的封裝中重複使用，您應該考慮建立自訂物件。</span><span class="sxs-lookup"><span data-stu-id="9962f-108">If the code will be reused within the same package, you should consider creating a custom object.</span></span> <span data-ttu-id="9962f-109">將程式碼從某個指令碼工作或元件複製到其他指令碼工作或元件，將會降低可維護性，因為這將使得維護和更新程式碼的多個複本更加困難。</span><span class="sxs-lookup"><span data-stu-id="9962f-109">Copying code from one Script task or component to another leads to reduced maintainability by making it more difficult to maintain and update multiple copies of the code.</span></span>  
  
-   <span data-ttu-id="9962f-110">如果實作在一段時間後將會變更，請考慮使用自訂物件。</span><span class="sxs-lookup"><span data-stu-id="9962f-110">If the implementation will change over time, consider using a custom object.</span></span> <span data-ttu-id="9962f-111">自訂物件可以和父封裝分開開發和部署，然而對指令碼方案的更新則需要重新部署整個封裝。</span><span class="sxs-lookup"><span data-stu-id="9962f-111">Custom objects can be developed and deployed separately from the parent package, whereas an update made to a scripting solution requires the redeployment of the whole package.</span></span>  
  
<span data-ttu-id="9962f-112">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="9962f-112">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="9962f-113">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="9962f-113">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="9962f-114">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="9962f-114">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="9962f-115">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="9962f-115">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9962f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9962f-116">See Also</span></span>  
 [<span data-ttu-id="9962f-117">使用自訂物件擴充封裝</span><span class="sxs-lookup"><span data-stu-id="9962f-117">Extending Packages with Custom Objects</span></span>](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
  
  
