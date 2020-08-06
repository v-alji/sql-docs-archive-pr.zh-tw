---
title: 資料來源屬性對話方塊、認證 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.credentials.f1
- "10100"
ms.assetid: 14c3eeb6-d37b-4fda-967b-43afcdb48119
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 491da16e6cd38db54c4d27bd8497ca7fdfaae5b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596548"
---
# <a name="data-source-properties-dialog-box-credentials"></a><span data-ttu-id="bab8c-102">資料來源屬性對話方塊、認證</span><span class="sxs-lookup"><span data-stu-id="bab8c-102">Data Source Properties Dialog Box, Credentials</span></span>
  <span data-ttu-id="bab8c-103">選取 **[資料來源屬性]** 對話方塊上的 **[認證]** ，來顯示和修改要連接到報表中資料來源的認證。</span><span class="sxs-lookup"><span data-stu-id="bab8c-103">Select **Credentials** on the **Data Source Properties** dialog box to display and modify credentials to connect to a data source in the report.</span></span> <span data-ttu-id="bab8c-104">您所提供的認證會用來存取資料來源，並快取資料副本，以預覽報表。</span><span class="sxs-lookup"><span data-stu-id="bab8c-104">The credentials that you provide are used to access the data source and to cache a copy of the data for previewing reports.</span></span> <span data-ttu-id="bab8c-105">如需如何快取預覽資料的詳細資訊，請參閱 [預覽報表](reports/previewing-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="bab8c-105">For more information about how preview data is cached, see [Previewing Reports](reports/previewing-reports.md).</span></span> <span data-ttu-id="bab8c-106">如需認證的詳細資訊，請參閱 [指定報表資料來源的認證及連接資訊](report-data/specify-credential-and-connection-information-for-report-data-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="bab8c-106">For more information about credentials, see [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="bab8c-107">選項</span><span class="sxs-lookup"><span data-stu-id="bab8c-107">Options</span></span>  
 <span data-ttu-id="bab8c-108">**使用 Windows 驗證 (整合式安全性)**</span><span class="sxs-lookup"><span data-stu-id="bab8c-108">**Use Windows Authentication (integrated security)**</span></span>  
 <span data-ttu-id="bab8c-109">選取此選項即可使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="bab8c-109">Select this option to use Windows Authentication.</span></span>  
  
 <span data-ttu-id="bab8c-110">**使用此使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="bab8c-110">**Use this user name and password**</span></span>  
 <span data-ttu-id="bab8c-111">選取此選項即可提供特定的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="bab8c-111">Select this option to provide a specific user name and password.</span></span> <span data-ttu-id="bab8c-112">若為共用資料來源：當您將報表伺服器專案發行至目標伺服器時，使用者名稱和密碼就會儲存成資料庫的預存認證。</span><span class="sxs-lookup"><span data-stu-id="bab8c-112">For shared data sources: when you publish the report server project to the target server, the user name and password are saved as the stored credentials for the database.</span></span> <span data-ttu-id="bab8c-113">如果您想要使用該使用者名稱和密碼當做 Windows 認證，就可以在目標伺服器上編輯已發行共用資料來源的屬性。</span><span class="sxs-lookup"><span data-stu-id="bab8c-113">If you want to use the user name and password as Windows credentials, you can edit the properties for the published shared data source on the target server.</span></span> <span data-ttu-id="bab8c-114">如需詳細資訊，請參閱[建立、刪除或修改共用資料來源 &#40;報表管理員&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="bab8c-114">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md).</span></span>  
  
 <span data-ttu-id="bab8c-115">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="bab8c-115">**User name**</span></span>  
 <span data-ttu-id="bab8c-116">輸入使用者名稱以登入資料來源。</span><span class="sxs-lookup"><span data-stu-id="bab8c-116">Type a user name to log in to the data source.</span></span>  
  
 <span data-ttu-id="bab8c-117">**密碼**</span><span class="sxs-lookup"><span data-stu-id="bab8c-117">**Password**</span></span>  
 <span data-ttu-id="bab8c-118">輸入密碼以登入資料來源。</span><span class="sxs-lookup"><span data-stu-id="bab8c-118">Type a password to log in to the data source.</span></span>  
  
 <span data-ttu-id="bab8c-119">**提示輸入認證**</span><span class="sxs-lookup"><span data-stu-id="bab8c-119">**Prompt for credentials**</span></span>  
 <span data-ttu-id="bab8c-120">選取此選項即可在執行報表時提示輸入認證。</span><span class="sxs-lookup"><span data-stu-id="bab8c-120">Select this option to prompt for credentials when the report is run.</span></span>  
  
 <span data-ttu-id="bab8c-121">**輸入提示字串**</span><span class="sxs-lookup"><span data-stu-id="bab8c-121">**Enter prompt string**</span></span>  
 <span data-ttu-id="bab8c-122">輸入句子，以指示使用者提供資料來源的登入認證。</span><span class="sxs-lookup"><span data-stu-id="bab8c-122">Type a sentence to instruct the user to provide login credentials for the data source.</span></span>  
  
 <span data-ttu-id="bab8c-123">**無認證**</span><span class="sxs-lookup"><span data-stu-id="bab8c-123">**No credentials**</span></span>  
 <span data-ttu-id="bab8c-124">選取此選項就不會提供資料來源的認證。</span><span class="sxs-lookup"><span data-stu-id="bab8c-124">Select this option to provide no credentials for the data source.</span></span> <span data-ttu-id="bab8c-125">只有在資料來源未接受認證，或是使用一些其他方式傳送認證時，這個選項才有用。</span><span class="sxs-lookup"><span data-stu-id="bab8c-125">This option only works if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab8c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bab8c-126">See Also</span></span>  
 <span data-ttu-id="bab8c-127">[資料來源屬性對話方塊、一般](../../2014/reporting-services/data-source-properties-dialog-box-general.md) </span><span class="sxs-lookup"><span data-stu-id="bab8c-127">[Data Source Properties Dialog Box, General](../../2014/reporting-services/data-source-properties-dialog-box-general.md) </span></span>  
 <span data-ttu-id="bab8c-128">[指定報表資料來源的認證及連接資訊](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="bab8c-128">[Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span></span>  
 [<span data-ttu-id="bab8c-129">Data Connections, Data Sources, and Connection Strings in Reporting Services</span><span class="sxs-lookup"><span data-stu-id="bab8c-129">Data Connections, Data Sources, and Connection Strings in Reporting Services</span></span>](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
