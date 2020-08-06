---
title: Master Data Services |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 87d8c588c3893a5aadf950a60681ec60d50309de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596756"
---
# <a name="master-data-services"></a><span data-ttu-id="8a745-102">Master Data Services</span><span class="sxs-lookup"><span data-stu-id="8a745-102">Master Data Services</span></span>
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] <span data-ttu-id="8a745-103">(MDS) 是用於主要資料管理的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 方案。</span><span class="sxs-lookup"><span data-stu-id="8a745-103">(MDS) is the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] solution for master data management.</span></span> <span data-ttu-id="8a745-104">主要資料管理 (MDM) 描述組織探索與定義非交易之資料清單所付出的心力，其目標在於編譯可維護的主要清單。</span><span class="sxs-lookup"><span data-stu-id="8a745-104">Master data management (MDM) describes the efforts made by an organization to discover and define non-transactional lists of data, with the goal of compiling maintainable master lists.</span></span> <span data-ttu-id="8a745-105">MDM 專案一般包含內部商業程序的評估與重組，以及 MDM 技術的實作。</span><span class="sxs-lookup"><span data-stu-id="8a745-105">An MDM project generally includes an evaluation and restructuring of internal business processes along with the implementation of MDM technology.</span></span> <span data-ttu-id="8a745-106">成功的 MDM 方案結果是可以分析的可靠集中式資料，以進行更好的商業性決策。</span><span class="sxs-lookup"><span data-stu-id="8a745-106">The result of a successful MDM solution is reliable, centralized data that can be analyzed, resulting in better business decisions.</span></span>

 <span data-ttu-id="8a745-107">透過適當的訓練，大部分商務使用者應該都可以實作 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 方案。</span><span class="sxs-lookup"><span data-stu-id="8a745-107">With the right training, most business users should be able to implement a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] solution.</span></span> <span data-ttu-id="8a745-108">此外，您還可以使用 MDS 管理任何網域；這不是單指管理客戶、產品或帳戶的清單。</span><span class="sxs-lookup"><span data-stu-id="8a745-108">In addition, you can use MDS to manage any domain; it's not specific to managing lists of customers, products, or accounts.</span></span> <span data-ttu-id="8a745-109">第一次安裝 MDS 時，不會包含任何網域的結構-您可以藉由建立模型來定義所需的網域。</span><span class="sxs-lookup"><span data-stu-id="8a745-109">When MDS is first installed, it does not include the structure for any domains-you define the domains you need by creating models for them.</span></span>

 <span data-ttu-id="8a745-110">其他 Master Data Services 功能包括階層、更細微的安全性、交易、資料版本控制，以及商務規則。</span><span class="sxs-lookup"><span data-stu-id="8a745-110">Other Master Data Services features include hierarchies, granular security, transactions, data versioning, and business rules.</span></span>

 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]<span data-ttu-id="8a745-111">包含下列元件和工具：</span><span class="sxs-lookup"><span data-stu-id="8a745-111">includes the following components and tools:</span></span>

-   [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]<span data-ttu-id="8a745-112">，用來建立及設定 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫和 Web 應用程式的工具。</span><span class="sxs-lookup"><span data-stu-id="8a745-112">, a tool you use to create and configure [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] databases and web applications.</span></span>

-   [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]<span data-ttu-id="8a745-113">，可用來執行管理工作 (例如建立模型或商務規則)，而且使用者可以存取更新資料的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8a745-113">, a web application you use to perform administrative tasks (like creating a model or business rule), and that users access to update data.</span></span>

-   <span data-ttu-id="8a745-114">MDSModelDeploy.exe，您用來建立模型物件與資料的封裝，讓您可以將其部署至其他環境的一個工具。</span><span class="sxs-lookup"><span data-stu-id="8a745-114">MDSModelDeploy.exe, a tool you use to create packages of your model objects and data so you can deploy them to other environments.</span></span>

-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] <span data-ttu-id="8a745-115">Web 服務，開發人員可用來擴充或開發 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 的自訂方案。</span><span class="sxs-lookup"><span data-stu-id="8a745-115">web service, which developers can use to extend or develop custom solutions for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span>

-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]<span data-ttu-id="8a745-116">[!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]，用來管理資料及建立新的實體和屬性。</span><span class="sxs-lookup"><span data-stu-id="8a745-116">[!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)], which you use to manage data and create new entities and attributes.</span></span>

 <span data-ttu-id="8a745-117">如需 MDS 資源的摘要，請參閱[SQL Server Master Data Services 入口網站](https://go.microsoft.com/fwlink/?LinkID=214272)。</span><span class="sxs-lookup"><span data-stu-id="8a745-117">For a summary of MDS resources, see the [SQL Server Master Data Services Portal](https://go.microsoft.com/fwlink/?LinkID=214272).</span></span>

|||
|-|-|
|<span data-ttu-id="8a745-118">**依區域瀏覽內容**</span><span class="sxs-lookup"><span data-stu-id="8a745-118">**Browse Content by Area**</span></span><br /> <span data-ttu-id="8a745-119">![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示") [Master Data Services 總覽](master-data-services-overview-mds.md)</span><span class="sxs-lookup"><span data-stu-id="8a745-119">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Master Data Services Overview](master-data-services-overview-mds.md)</span></span><br /><br /> <span data-ttu-id="8a745-120">![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示") [Master Data Services 功能和](../../2014/master-data-services/master-data-services-features-and-tasks.md)工作</span><span class="sxs-lookup"><span data-stu-id="8a745-120">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Master Data Services Features and Tasks](../../2014/master-data-services/master-data-services-features-and-tasks.md)</span></span><br /><br /> <span data-ttu-id="8a745-121">![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示")[技術參考 (Master Data Services) ](technical-reference-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="8a745-121">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Technical Reference (Master Data Services)](technical-reference-master-data-services.md)</span></span><br /><br /> <span data-ttu-id="8a745-122">![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示")[開發人員指南 (Master Data Services) ](develop/master-data-services-developer-documentation.md)</span><span class="sxs-lookup"><span data-stu-id="8a745-122">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Developer's Guide (Master Data Services)](develop/master-data-services-developer-documentation.md)</span></span>||


