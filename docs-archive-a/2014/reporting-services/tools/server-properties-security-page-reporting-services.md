---
title: 伺服器屬性 (安全性頁面) - Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.security.f1
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f709d42bf593b4933d9fc1fdc423c195967df382
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597013"
---
# <a name="server-properties-security-page---reporting-services"></a><span data-ttu-id="5f34f-102">伺服器屬性 (安全性頁面) - Reporting Services</span><span class="sxs-lookup"><span data-stu-id="5f34f-102">Server Properties (Security Page) - Reporting Services</span></span>
  <span data-ttu-id="5f34f-103">您可以使用這個頁面來關閉可能會危害報表伺服器的功能。</span><span class="sxs-lookup"><span data-stu-id="5f34f-103">Use this page to turn off features that can potentially compromise a report server.</span></span> <span data-ttu-id="5f34f-104">雖然關閉這些功能會限制某些功能，但是也可能會透過減少特定威脅，改善報表伺服器的整體安全性。</span><span class="sxs-lookup"><span data-stu-id="5f34f-104">Turning off these features will limit some functionality, but can improve the overall security of the report server by mitigating specific threats.</span></span>  
  
 <span data-ttu-id="5f34f-105">若要開啟此頁面，請啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、連接至報表伺服器執行個體、以滑鼠右鍵按一下報表伺服器名稱，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5f34f-105">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="5f34f-106">按一下 [安全性]\*\*\*\*，即可開啟此頁面。</span><span class="sxs-lookup"><span data-stu-id="5f34f-106">Click **Security** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5f34f-107">選項</span><span class="sxs-lookup"><span data-stu-id="5f34f-107">Options</span></span>  
 <span data-ttu-id="5f34f-108">**為報表資料來源啟用 Windows 整合式安全性**</span><span class="sxs-lookup"><span data-stu-id="5f34f-108">**Enable Windows integrated security for report data sources**</span></span>  
 <span data-ttu-id="5f34f-109">指定是否可以使用要求報表之使用者的 Windows 安全性 Token 來建立報表資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="5f34f-109">Specify whether a connection to a report data source can be made using the Windows security token of the user who requested the report.</span></span>  
  
 <span data-ttu-id="5f34f-110">如果您關閉這項功能，就無法使用報表資料來源屬性中的 Windows 整合式安全性功能。</span><span class="sxs-lookup"><span data-stu-id="5f34f-110">If you turn off this feature, the Windows Integrated Security feature in the report data source property pages will be unavailable.</span></span> <span data-ttu-id="5f34f-111">如果報表資料來源是針對 Windows 整合式安全性所設定，而且您之後關閉了這項功能，則報表伺服器將立即更新所有資料來源連接屬性，以便提示使用者輸入認證。</span><span class="sxs-lookup"><span data-stu-id="5f34f-111">If report data sources are configured for Windows integrated security and you subsequently turn off this feature, the report server will immediately update all data source connection properties to prompt for credentials.</span></span>  
  
 <span data-ttu-id="5f34f-112">**啟用隨選報表**</span><span class="sxs-lookup"><span data-stu-id="5f34f-112">**Enable Ad Hoc Reporting**</span></span>  
 <span data-ttu-id="5f34f-113">指定使用者是否可以從報表產生器報表執行隨選查詢，而且當使用者按一下感興趣的資料時，系統就會自動產生新的報表。</span><span class="sxs-lookup"><span data-stu-id="5f34f-113">Specify whether users can perform ad hoc queries from a Report Builder report, where new reports are automatically generated when a user clicks data of interest.</span></span>  
  
 <span data-ttu-id="5f34f-114">設定這個選項會決定報表伺服器上的 `EnableLoadReportDefinition` 屬性設定為 `True` 或 `False`。</span><span class="sxs-lookup"><span data-stu-id="5f34f-114">Setting this option determines whether the `EnableLoadReportDefinition` property on the report server is set to `True` or `False`.</span></span> <span data-ttu-id="5f34f-115">如果您清除此選項，這個屬性將會設定為 `False` 而且報表伺服器將不會產生在資料瀏覽期間建立的點選連結報表。</span><span class="sxs-lookup"><span data-stu-id="5f34f-115">If you clear this option, the property will be set to `False` and report server will not generate clickthrough reports that are created during data exploration.</span></span> <span data-ttu-id="5f34f-116">`LoadReportDefinition` 方法的所有呼叫都會被封鎖。</span><span class="sxs-lookup"><span data-stu-id="5f34f-116">All calls to the `LoadReportDefinition` method will be blocked.</span></span>  
  
 <span data-ttu-id="5f34f-117">關閉此選項可減少惡意使用者利用 `LoadReportDefinition` 要求讓報表伺服器超過負載，藉以啟動阻斷服務攻擊的威脅。</span><span class="sxs-lookup"><span data-stu-id="5f34f-117">Turning off this option mitigates a threat whereby a malicious user launches a denial of service attack by overloading the report server with `LoadReportDefinition` requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f34f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f34f-118">See Also</span></span>  
 <span data-ttu-id="5f34f-119">[將報表伺服器屬性設定 &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="5f34f-119">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="5f34f-120">[連接到 Management Studio 中的報表伺服器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="5f34f-120">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="5f34f-121">[指定報表資料來源的認證和連接資訊] (.。[Management Studio F1 說明中的/Report-data/specify-credential-and-connection-information-for-report-data-sources.md 報表伺服器](report-server-in-management-studio-f1-help.md)</span><span class="sxs-lookup"><span data-stu-id="5f34f-121">[Specify Credential and Connection Information for Report Data Sources](../report-data/specify-credential-and-connection-information-for-report-data-sources.md [Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md)</span></span>  
  
  
