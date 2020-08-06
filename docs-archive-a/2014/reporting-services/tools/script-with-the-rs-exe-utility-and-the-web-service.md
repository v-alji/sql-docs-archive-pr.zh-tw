---
title: 利用 rs.exe 公用程式與 Web 服務編寫指令碼 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Web service [Reporting Services], scripts
- rs utility
- XML Web service [Reporting Services], scripts
- Report Server Web service, scripts
- scripts [Reporting Services], Web service
ms.assetid: 0ec5ac6e-b3cf-49cd-96f6-6b4b7dc29982
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d84bb8722fd31a08ff7788ad31c601b377c23d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597019"
---
# <a name="script-with-the-rsexe-utility-and-the-web-service"></a><span data-ttu-id="dc16a-102">利用 rs.exe 公用程式與 Web 服務編寫指令碼</span><span class="sxs-lookup"><span data-stu-id="dc16a-102">Script with the rs.exe Utility and the Web Service</span></span>
  <span data-ttu-id="dc16a-103">開發人員與報表伺服器管理員可以在報表伺服器上，透過使用 **rs** 公用程式 (RS.exe) 來執行作業。</span><span class="sxs-lookup"><span data-stu-id="dc16a-103">Developers and report server administrators can perform operations on a report server through the use of the **rs** utility (RS.exe).</span></span> <span data-ttu-id="dc16a-104">利用這個公用程式，您可以使用以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 撰寫的指令碼，透過程式設計方式管理報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="dc16a-104">Using this utility, you can programmatically administer a report server using scripts written with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="dc16a-105">指令碼可用於執行任何報表伺服器 Web 服務作業。</span><span class="sxs-lookup"><span data-stu-id="dc16a-105">scripts can be used to run any of the Report Server Web service operations.</span></span> <span data-ttu-id="dc16a-106">使用指令碼時，可以將安全性複製到伺服器上的多個報表、新增和刪除項目、將報表伺服器項目從一部伺服器複製到另外一部或多部伺服器。</span><span class="sxs-lookup"><span data-stu-id="dc16a-106">Scripting can be used to copy security to multiple reports on a server, to add and delete items, to copy report server items from one server to another and more.</span></span> <span data-ttu-id="dc16a-107">如需指令碼環境的詳細資訊，請參閱 [執行 Reporting Services 指令碼檔案](run-a-reporting-services-script-file.md)。</span><span class="sxs-lookup"><span data-stu-id="dc16a-107">For more information about the scripting environment, see [Run a Reporting Services Script File](run-a-reporting-services-script-file.md).</span></span> <span data-ttu-id="dc16a-108">指令碼檔案採用特定格式，並以 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET 撰寫。</span><span class="sxs-lookup"><span data-stu-id="dc16a-108">Script files take a certain format and are written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET.</span></span> <span data-ttu-id="dc16a-109">如需詳細資訊，請參閱 [格式化 Reporting Services 指令碼檔案](format-a-reporting-services-script-file.md)。</span><span class="sxs-lookup"><span data-stu-id="dc16a-109">For more information, see [Format a Reporting Services Script File](format-a-reporting-services-script-file.md).</span></span>  
  
 <span data-ttu-id="dc16a-110">如需指令碼範例，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="dc16a-110">For script samples, see the following:</span></span>  
  
 <span data-ttu-id="dc16a-111">[在報表伺服器之間遷移內容的範例 Reporting Services rs.exe 腳本](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="dc16a-111">[Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>  
  
 <span data-ttu-id="dc16a-112">[SQL Server Reporting Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=177889)。</span><span class="sxs-lookup"><span data-stu-id="dc16a-112">[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc16a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc16a-113">See Also</span></span>  
 <span data-ttu-id="dc16a-114">[編寫部署和管理工作的指令碼](script-deployment-and-administrative-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="dc16a-114">[Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md) </span></span>  
 <span data-ttu-id="dc16a-115">[報表伺服器 Web 服務](../report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="dc16a-115">[Report Server Web Service](../report-server-web-service/report-server-web-service.md) </span></span>  
 <span data-ttu-id="dc16a-116">[技術參考 &#40;SSRS&#41;](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dc16a-116">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="dc16a-117">RS.exe 公用程式 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="dc16a-117">RS.exe Utility &#40;SSRS&#41;</span></span>](rs-exe-utility-ssrs.md)  
  
  
