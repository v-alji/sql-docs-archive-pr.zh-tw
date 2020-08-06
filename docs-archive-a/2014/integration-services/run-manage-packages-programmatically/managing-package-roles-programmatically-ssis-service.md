---
title: 以程式設計方式管理套件角色 (SSIS 服務) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, roles
- roles [Integration Services]
- packages [Integration Services], roles
ms.assetid: 2e0ca0d5-d4f5-421d-b17d-a48b37b923e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dff54f3f90d9e008ae21c83c2a8fdc3f7440a5c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707666"
---
# <a name="managing-package-roles-programmatically-ssis-service"></a><span data-ttu-id="7acb9-102">以程式設計方式管理封裝角色 (SSIS 服務)</span><span class="sxs-lookup"><span data-stu-id="7acb9-102">Managing Package Roles Programmatically (SSIS Service)</span></span>
  <span data-ttu-id="7acb9-103">當您以程式設計方式使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝時，可能會想要判斷有哪些角色可供套用至封裝，或是判斷或設定套用至個別封裝的角色。</span><span class="sxs-lookup"><span data-stu-id="7acb9-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine which roles are available to apply to packages, or to determine or set the roles applied to an individual package.</span></span> <span data-ttu-id="7acb9-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 命名空間的 <xref:Microsoft.SqlServer.Dts.Runtime> 類別，提供各種方法以滿足這些需求。</span><span class="sxs-lookup"><span data-stu-id="7acb9-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides a variety of methods to satisfy these requirements.</span></span>

 <span data-ttu-id="7acb9-105">角色只能套用到儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** 資料庫的套件。</span><span class="sxs-lookup"><span data-stu-id="7acb9-105">Roles apply only to packages stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** database.</span></span> <span data-ttu-id="7acb9-106">如需套件角色的詳細資訊，請參閱 [Integration Services 角色 &#40;SSIS 服務&#41;](../security/integration-services-roles-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="7acb9-106">For more information about package roles, see [Integration Services Roles &#40;SSIS Service&#41;](../security/integration-services-roles-ssis-service.md).</span></span>

 <span data-ttu-id="7acb9-107">本主題中討論的所有方法都需要 `Microsoft.SqlServer.ManagedDTS` 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="7acb9-107">All the methods discussed in this topic require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="7acb9-108">在新專案中加入參考之後，請使用 `using` 或 `Imports` 陳述式匯入 <xref:Microsoft.SqlServer.Dts.Runtime> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="7acb9-108">After you add the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace by using a `using` or `Imports` statement.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="7acb9-109">用以搭配 SSIS 封裝存放區使用的 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 類別之方法，僅支援 "."、localhost 或是本機伺服器的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="7acb9-109">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store support only ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="7acb9-110">您無法使用 "(local)"。</span><span class="sxs-lookup"><span data-stu-id="7acb9-110">You cannot use "(local)".</span></span>

## <a name="determining-which-roles-are-available"></a><span data-ttu-id="7acb9-111">判斷可以使用哪些角色</span><span class="sxs-lookup"><span data-stu-id="7acb9-111">Determining Which Roles Are Available</span></span>
 <span data-ttu-id="7acb9-112">若要判斷有哪些角色可供儲存在特定伺服器上的封裝使用，請呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> 類別的 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 方法。</span><span class="sxs-lookup"><span data-stu-id="7acb9-112">To determine which roles are available for the packages stored on a particular server, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class.</span></span>

## <a name="determining-which-roles-are-assigned"></a><span data-ttu-id="7acb9-113">判斷已指派哪些角色</span><span class="sxs-lookup"><span data-stu-id="7acb9-113">Determining Which Roles Are Assigned</span></span>
 <span data-ttu-id="7acb9-114">若要判斷已將哪些角色指派到特定封裝，請呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7acb9-114">To determine which roles have already been assigned to a particular package, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A> method.</span></span> <span data-ttu-id="7acb9-115">若要將角色指派到套件，請呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7acb9-115">To assign roles to a package, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A> method.</span></span>

<span data-ttu-id="7acb9-116">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="7acb9-116">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="7acb9-117">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="7acb9-117">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="7acb9-118">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="7acb9-118">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="7acb9-119">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="7acb9-119">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="7acb9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7acb9-120">See Also</span></span>
 [<span data-ttu-id="7acb9-121">Integration Services 角色 &#40;SSIS 服務&#41;</span><span class="sxs-lookup"><span data-stu-id="7acb9-121">Integration Services Roles &#40;SSIS Service&#41;</span></span>](../security/integration-services-roles-ssis-service.md)


