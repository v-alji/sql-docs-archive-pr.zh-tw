---
title: 將權限授與使用者及警示管理員 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 166808e1-ada7-48d2-bda8-8f7c017fb3aa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5bf7f030871287379ce9fb32a1789b95cff0fc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606084"
---
# <a name="grant-permissions-to-users-and-alerting-administrators"></a><span data-ttu-id="aeb77-102">將權限授與使用者及警示管理員</span><span class="sxs-lookup"><span data-stu-id="aeb77-102">Grant Permissions to Users and Alerting Administrators</span></span>
  <span data-ttu-id="aeb77-103">使用者和警示系統管理員必須經過 SharePoint 權限的授與，才能建立、編輯、刪除及檢視資料警示。</span><span class="sxs-lookup"><span data-stu-id="aeb77-103">Before users and alerting administrators can create, edit, delete, and view data alerts they must be granted SharePoint permissions.</span></span> <span data-ttu-id="aeb77-104">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 資料警示功能沒有特殊權限可供使用，您需使用內建的 SharePoint 權限。</span><span class="sxs-lookup"><span data-stu-id="aeb77-104">There are no special permissions to use with the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] data alerting feature, you use the built-in SharePoint permissions.</span></span>  
  
 <span data-ttu-id="aeb77-105">**資訊工作者** - 權限必須包含「建立警示」和「檢視項目」的 SharePoint 權限。</span><span class="sxs-lookup"><span data-stu-id="aeb77-105">**Information workers**-Permissions must include the Create Alert and View Items SharePoint permissions.</span></span> <span data-ttu-id="aeb77-106">名稱為「設計」、「參與」、「讀取」及「僅檢視」的內建 SharePoint 權限等級包含「建立警示」和「檢視項目」的 SharePoint 權限。</span><span class="sxs-lookup"><span data-stu-id="aeb77-106">The built-in SharePoint permission levels named Design, Contribute, Read, and View Only include the Create Alert and View Items SharePoint permissions.</span></span> <span data-ttu-id="aeb77-107">您也可以使用支援使用者建立、編輯、執行及檢視資料警示所需的權限，建立自訂權限等級。</span><span class="sxs-lookup"><span data-stu-id="aeb77-107">You can also create a custom permission level with the permissions required to support users that create, edit, run, and view data alerts.</span></span>  
  
 <span data-ttu-id="aeb77-108">**警示系統管理員**-許可權必須包含「管理警示 SharePoint」許可權。</span><span class="sxs-lookup"><span data-stu-id="aeb77-108">**Alerting administrators**-Permissions must include the Manage Alert SharePoint permission.</span></span> <span data-ttu-id="aeb77-109">根據預設，只有「完整控制權」權限層級包含使用「小組網站」網站範本建立的這項網站權限。</span><span class="sxs-lookup"><span data-stu-id="aeb77-109">By default only the Full Control permission level includes this permission for sites created with the Team Site site template.</span></span> <span data-ttu-id="aeb77-110">如果您使用其他網站範本，則會看見不同的預設 SharePoint 群組清單。</span><span class="sxs-lookup"><span data-stu-id="aeb77-110">If you use other site templates, you will see different lists of default SharePoint groups.</span></span> <span data-ttu-id="aeb77-111">您可以使用支援警示系統管理員檢視及刪除資料警示所需的權限，將「管理警示」權限加入其中一個內建權限等級或建立自訂權限等級。</span><span class="sxs-lookup"><span data-stu-id="aeb77-111">You can add the Manage Alert permission to one of the built-in permission levels or create a custom permission level with the permission required to support alerting administrators that view and delete data alerts.</span></span>  
  
 <span data-ttu-id="aeb77-112">若要深入了解 SharePoint 權限，請參閱 [使用者權限與權限等級 (SharePoint Server 2010)](https://technet.microsoft.com/library/cc721640.aspx)。</span><span class="sxs-lookup"><span data-stu-id="aeb77-112">To learn more about SharePoint permissions, see [User permissions and permission levels (SharePoint Server 2010)](https://technet.microsoft.com/library/cc721640.aspx).</span></span>  
  
### <a name="to-grant-permissions"></a><span data-ttu-id="aeb77-113">授與權限</span><span class="sxs-lookup"><span data-stu-id="aeb77-113">To grant permissions</span></span>  
  
1.  <span data-ttu-id="aeb77-114">移至您要授與權限的 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="aeb77-114">Go to the SharePoint site to which you want to grant permissions.</span></span>  
  
2.  <span data-ttu-id="aeb77-115">在工具列上，按一下 **[網站動作]** ，然後按一下 **[網站權限]**。</span><span class="sxs-lookup"><span data-stu-id="aeb77-115">On the toolbar, click **Site Actions** and then click **Site Permissions**.</span></span>  
  
     <span data-ttu-id="aeb77-116">如果沒有看到此選項，表示您沒有足夠的權限以將權限授與給其他人。</span><span class="sxs-lookup"><span data-stu-id="aeb77-116">If you do not see this option, you do not sufficient permission to grant permissions to others.</span></span>  
  
3.  <span data-ttu-id="aeb77-117">按一下 [授與權限]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aeb77-117">Click **Grant Permissions**.</span></span>  
  
4.  <span data-ttu-id="aeb77-118">在 [使用者/群組]\*\*\*\* 中，輸入要授與權限的使用者名稱、群組名稱或電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="aeb77-118">In **Users/Groups**, type the user names, group names, or e-mail addresses you want grant permission to.</span></span>  
  
5.  <span data-ttu-id="aeb77-119">選取 **[加入使用者至 SharePoint 群組]** 或 **[直接授與使用者權限]** 選項。</span><span class="sxs-lookup"><span data-stu-id="aeb77-119">Select the **Add users to a SharePoint group** or **Grant users permission directly** option.</span></span> <span data-ttu-id="aeb77-120">根據您選取的是 **[新增使用者至 SharePoint 群組]** 或是 **[直接授與使用者權限]** 而定，執行下列其中一項操作：</span><span class="sxs-lookup"><span data-stu-id="aeb77-120">Depending on whether you selected **Add users to a SharePoint group** or **Grant users permissions directly** do one of the following:</span></span>  
  
    -   <span data-ttu-id="aeb77-121">如果您選取了 [新增使用者至 SharePoint 群組]\*\*\*\*，請選取下拉式清單中的權限等級。</span><span class="sxs-lookup"><span data-stu-id="aeb77-121">If you selected **Add users to a SharePoint group**, select a permission level in the drop-down list.</span></span>  
  
    -   <span data-ttu-id="aeb77-122">如果您選取了 **[直接授與使用者權限]**，請選取權限等級。</span><span class="sxs-lookup"><span data-stu-id="aeb77-122">If you selected **Grant users permissions directly**, select a permission level.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aeb77-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aeb77-123">See Also</span></span>  
 <span data-ttu-id="aeb77-124">[在 sharepoint 網站上設定報表伺服器專案的許可權 &#40;SharePoint 整合模式中的 Reporting Services&#41;](security/set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="aeb77-124">[Set Permissions for Report Server Items on a SharePoint Site &#40;Reporting Services in SharePoint Integrated Mode&#41;](security/set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="aeb77-125">Reporting Services 資料警示</span><span class="sxs-lookup"><span data-stu-id="aeb77-125">Reporting Services Data Alerts</span></span>](../ssms/agent/alerts.md)  
  
  
