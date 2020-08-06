---
title: 以程式設計方式儲存套件 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2879c4213b2c9c0bf395c103de0d1bc37e4daab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594143"
---
# <a name="saving-a-package-programmatically"></a><span data-ttu-id="01a0a-102">以程式設計方式儲存封裝</span><span class="sxs-lookup"><span data-stu-id="01a0a-102">Saving a Package Programmatically</span></span>
  <span data-ttu-id="01a0a-103">在以程式設計方式建立新封裝或是修改現有封裝之後，通常會想要儲存變更。</span><span class="sxs-lookup"><span data-stu-id="01a0a-103">After building a new package programmatically, or modifying an existing one, you usually want to save your changes.</span></span>  
  
 <span data-ttu-id="01a0a-104">本主題中用以儲存封裝的所有方法需要 `Microsoft.SqlServer.ManagedDTS` 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="01a0a-104">All of the methods used in this topic to save packages require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="01a0a-105">在新專案中加入參考之後，請使用 `using` 或 `Imports` 陳述式來匯入 <xref:Microsoft.SqlServer.Dts.Runtime> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="01a0a-105">After you add the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
## <a name="saving-a-package-programmatically"></a><span data-ttu-id="01a0a-106">以程式設計方式儲存封裝</span><span class="sxs-lookup"><span data-stu-id="01a0a-106">Saving a Package Programmatically</span></span>  
 <span data-ttu-id="01a0a-107">若要以程式設計方式儲存套件，請呼叫 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application> 類別的下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="01a0a-107">To save a package programmatically, call one of the following methods of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application> class:</span></span>  
  
|<span data-ttu-id="01a0a-108">儲存位置</span><span class="sxs-lookup"><span data-stu-id="01a0a-108">Storage Location</span></span>|<span data-ttu-id="01a0a-109">要呼叫的方法</span><span class="sxs-lookup"><span data-stu-id="01a0a-109">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="01a0a-110">檔案</span><span class="sxs-lookup"><span data-stu-id="01a0a-110">File</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|<span data-ttu-id="01a0a-111">SSIS 封裝存放區</span><span class="sxs-lookup"><span data-stu-id="01a0a-111">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> <span data-ttu-id="01a0a-112">或</span><span class="sxs-lookup"><span data-stu-id="01a0a-112">or</span></span><br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="01a0a-113">用以搭配 SSIS 封裝存放區使用的 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 類別之方法，僅支援 "." 或是本機伺服器的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="01a0a-113">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store only support "." or the server name for the local server.</span></span> <span data-ttu-id="01a0a-114">您無法使用 "(本機)" 或者"localhost"。</span><span class="sxs-lookup"><span data-stu-id="01a0a-114">You cannot use "(local)" or "localhost".</span></span>  
  
<span data-ttu-id="01a0a-115">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="01a0a-115">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="01a0a-116">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="01a0a-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="01a0a-117">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="01a0a-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="01a0a-118">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="01a0a-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01a0a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01a0a-119">See Also</span></span>  
 [<span data-ttu-id="01a0a-120">儲存封裝</span><span class="sxs-lookup"><span data-stu-id="01a0a-120">Save Packages</span></span>](../save-packages.md)  
  
  
