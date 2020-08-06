---
title: Reporting Services 登入對話方塊 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 232ee51614a668b07263c3e3a4182f23652135bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704834"
---
# <a name="reporting-services-login-dialog-box-ssrs"></a><span data-ttu-id="1e53a-102">Reporting Services 登入對話方塊 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="1e53a-102">Reporting Services Login Dialog Box (SSRS)</span></span>
  <span data-ttu-id="1e53a-103">使用 **[Reporting Services 登入]** 對話方塊，即可提供發行報表至報表伺服器的認證。</span><span class="sxs-lookup"><span data-stu-id="1e53a-103">Use the **Reporting Services Login** dialog box to provide credentials to publish reports to the report server.</span></span>  
  
-   <span data-ttu-id="1e53a-104">**注意**如果這是您第一次將報表發行至報表伺服器，因為設定了專案的部署屬性**TargetServerURL** ，請確認您指定的伺服器名稱類似于 `http://localhost/reportserver` ，而不是 `http://localhost/reports` 。</span><span class="sxs-lookup"><span data-stu-id="1e53a-104">**Note** If this is the first time you have published a report to a report server since set you set the deployment property **TargetServerURL** for a project, verify that the server name you specified is similar to `http://localhost/reportserver`, and not `http://localhost/reports`.</span></span> <span data-ttu-id="1e53a-105">如果是指定本機伺服器的 `reports` 目錄，而不是 `reportserver` 目錄，則會間接導致此對話方塊開啟。</span><span class="sxs-lookup"><span data-stu-id="1e53a-105">Specifying the `reports` directory on the local server instead of the `reportserver` directory indirectly causes this dialog box to open.</span></span> <span data-ttu-id="1e53a-106">如需設定 **TargetServerURL** 的詳細資訊，請參閱[設定部署屬性 &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1e53a-106">For more information about setting **TargetServerURL**, see [Set Deployment Properties &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1e53a-107">選項</span><span class="sxs-lookup"><span data-stu-id="1e53a-107">Options</span></span>  
 <span data-ttu-id="1e53a-108">**Server**</span><span class="sxs-lookup"><span data-stu-id="1e53a-108">**Server**</span></span>  
 <span data-ttu-id="1e53a-109">顯示報表伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="1e53a-109">Displays the name of the report server.</span></span> <span data-ttu-id="1e53a-110">例如： `http://localhost/reportserver` 。</span><span class="sxs-lookup"><span data-stu-id="1e53a-110">For example, `http://localhost/reportserver`.</span></span> <span data-ttu-id="1e53a-111">如果報表伺服器使用的是預設通訊埠 80 以外的通訊埠，請加入該通訊埠號碼。</span><span class="sxs-lookup"><span data-stu-id="1e53a-111">For report servers that use a different port than default port 80, include the port number.</span></span> <span data-ttu-id="1e53a-112">例如： `http://localhost:81/reportserver` 。</span><span class="sxs-lookup"><span data-stu-id="1e53a-112">For example, `http://localhost:81/reportserver`.</span></span>  
  
 <span data-ttu-id="1e53a-113">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="1e53a-113">**User name**</span></span>  
 <span data-ttu-id="1e53a-114">輸入使用者名稱以登入 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="1e53a-114">Type the user name to log in to the Web service.</span></span>  
  
 <span data-ttu-id="1e53a-115">**密碼**</span><span class="sxs-lookup"><span data-stu-id="1e53a-115">**Password**</span></span>  
 <span data-ttu-id="1e53a-116">輸入密碼以登入 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="1e53a-116">Type the password to log in to the Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e53a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e53a-117">See Also</span></span>  
 <span data-ttu-id="1e53a-118">[Reporting Services 中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="1e53a-118">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="1e53a-119">[指定報表資料來源的認證和連接資訊](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)[報表設計師 F1](report-designer-f1-help.md)說明</span><span class="sxs-lookup"><span data-stu-id="1e53a-119">[Specify Credential and Connection Information for Report Data Sources](../report-data/specify-credential-and-connection-information-for-report-data-sources.md) [Report Designer F1 Help](report-designer-f1-help.md)</span></span>  
  
  
