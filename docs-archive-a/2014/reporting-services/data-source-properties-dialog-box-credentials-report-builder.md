---
title: 資料來源屬性對話方塊、認證 (報表產生器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10017"
ms.assetid: 4531f09f-d653-4c05-a120-d7788838bc99
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e47ba571e2b0adf2738499c1d027a4edde86e3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597638"
---
# <a name="data-source-properties-dialog-box-credentials-report-builder"></a><span data-ttu-id="235dd-102">資料來源屬性對話方塊、認證 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="235dd-102">Data Source Properties Dialog Box, Credentials (Report Builder)</span></span>
  <span data-ttu-id="235dd-103">選取 **[資料來源屬性]** 對話方塊上的 **[認證]** ，即可顯示和修改要連接到報表中內嵌資料來源的認證。</span><span class="sxs-lookup"><span data-stu-id="235dd-103">Select **Credentials** on the **Data Source Properties** dialog box to display and modify credentials to connect to an embedded data source in the report.</span></span> <span data-ttu-id="235dd-104">您所提供的認證會用來存取資料來源，以便預覽報表。</span><span class="sxs-lookup"><span data-stu-id="235dd-104">The credentials that you provide are used to access the data source for previewing reports.</span></span> <span data-ttu-id="235dd-105">如需認證的詳細資訊，請參閱 [在報表產生器中指定認證](../../2014/reporting-services/specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="235dd-105">For more information about credentials, see [Specify Credentials in Report Builder](../../2014/reporting-services/specify-credentials-in-report-builder.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="235dd-106">選項</span><span class="sxs-lookup"><span data-stu-id="235dd-106">Options</span></span>  
 <span data-ttu-id="235dd-107">**使用 Windows 驗證 (整合式安全性)**</span><span class="sxs-lookup"><span data-stu-id="235dd-107">**Use Windows Authentication (integrated security)**</span></span>  
 <span data-ttu-id="235dd-108">選取此選項即可使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="235dd-108">Select this option to use Windows Authentication.</span></span>  
  
 <span data-ttu-id="235dd-109">**使用此使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="235dd-109">**Use this user name and password**</span></span>  
 <span data-ttu-id="235dd-110">選取此選項即可提供特定的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="235dd-110">Select this option to provide a specific user name and password.</span></span> <span data-ttu-id="235dd-111">若為內嵌資料來源：當您將報表伺服器專案發行至目標伺服器時，使用者名稱和密碼就會儲存成資料庫的預存認證。</span><span class="sxs-lookup"><span data-stu-id="235dd-111">For embedded data sources: when you publish the report server project to the target server, the user name and password are saved as the stored credentials for the database.</span></span> <span data-ttu-id="235dd-112">如果您想要使用該使用者名稱和密碼當做 Windows 認證，就可以在目標伺服器上變更已發行共用資料來源的屬性。</span><span class="sxs-lookup"><span data-stu-id="235dd-112">If you want to use the user name and password as Windows credentials, you can change the properties for the published shared data source on the target server.</span></span> <span data-ttu-id="235dd-113">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [線上叢書](https://go.microsoft.com/fwlink/?linkid=121312)》中 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 文件的[建立、刪除或修改共用資料來源 &#40;報表管理員&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="235dd-113">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) in the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
 <span data-ttu-id="235dd-114">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="235dd-114">**User name**</span></span>  
 <span data-ttu-id="235dd-115">輸入使用者名稱以登入資料來源。</span><span class="sxs-lookup"><span data-stu-id="235dd-115">Type a user name to log on to the data source.</span></span>  
  
 <span data-ttu-id="235dd-116">**密碼**</span><span class="sxs-lookup"><span data-stu-id="235dd-116">**Password**</span></span>  
 <span data-ttu-id="235dd-117">輸入密碼以登入資料來源。</span><span class="sxs-lookup"><span data-stu-id="235dd-117">Type a password to log on to the data source.</span></span>  
  
 <span data-ttu-id="235dd-118">**提示輸入認證**</span><span class="sxs-lookup"><span data-stu-id="235dd-118">**Prompt for credentials**</span></span>  
 <span data-ttu-id="235dd-119">選取此選項即可在執行報表時提示輸入認證。</span><span class="sxs-lookup"><span data-stu-id="235dd-119">Select this option to prompt for credentials when the report runs.</span></span>  
  
 <span data-ttu-id="235dd-120">**輸入提示字串**</span><span class="sxs-lookup"><span data-stu-id="235dd-120">**Enter prompt string**</span></span>  
 <span data-ttu-id="235dd-121">輸入句子，以指示使用者提供資料來源的登入認證。</span><span class="sxs-lookup"><span data-stu-id="235dd-121">Type a sentence to instruct the user to provide login credentials for the data source.</span></span>  
  
 <span data-ttu-id="235dd-122">**無認證**</span><span class="sxs-lookup"><span data-stu-id="235dd-122">**No credentials**</span></span>  
 <span data-ttu-id="235dd-123">選取此選項就不會提供資料來源的認證。</span><span class="sxs-lookup"><span data-stu-id="235dd-123">Select this option to provide no credentials for the data source.</span></span> <span data-ttu-id="235dd-124">只有在資料來源未接受認證，或是使用一些其他方式傳送認證時，這個選項才有用。</span><span class="sxs-lookup"><span data-stu-id="235dd-124">This option only works if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
 <span data-ttu-id="235dd-125">針對某些資料延伸模組，您就必須在報表伺服器上設定自動執行帳戶。</span><span class="sxs-lookup"><span data-stu-id="235dd-125">From some data extensions, the unattended execution account must be configured on the report server.</span></span>  
  
 <span data-ttu-id="235dd-126">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [線上叢書](https://go.microsoft.com/fwlink/?linkid=121312)》之 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 文件中[從外部資料來源加入資料 &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) 和[設定自動執行帳戶 &#40;SSRS 組態管理員&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) 中對應資料來源類型的主題。</span><span class="sxs-lookup"><span data-stu-id="235dd-126">For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="235dd-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="235dd-127">See Also</span></span>  
 <span data-ttu-id="235dd-128">[對話方塊、窗格和嚮導的報表產生器說明](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="235dd-128">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="235dd-129">[資料來源屬性對話方塊、一般 &#40;報表產生器&#41;](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="235dd-129">[Data Source Properties Dialog Box, General &#40;Report Builder&#41;](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md) </span></span>  
 <span data-ttu-id="235dd-130">[加入及驗證資料連線或資料來源 &#40;報表產生器和 SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="235dd-130">[Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="235dd-131">將資料加入報表 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="235dd-131">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-data/report-datasets-ssrs.md)  
  
  
