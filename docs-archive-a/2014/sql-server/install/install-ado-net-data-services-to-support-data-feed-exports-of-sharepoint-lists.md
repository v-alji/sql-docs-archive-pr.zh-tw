---
title: 安裝 ADO.NET 資料服務以支援 SharePoint 清單的資料摘要匯出 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fb47804daee38427f48baefdf3997edda5fb90b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593773"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a><span data-ttu-id="78914-102">如何：安裝 ADO.NET Data Services 以支援 SharePoint 清單的資料摘要匯出</span><span class="sxs-lookup"><span data-stu-id="78914-102">Install ADO.NET Data Services to support data feed exports of SharePoint lists</span></span>
  <span data-ttu-id="78914-103">從 SharePoint 清單匯出資料摘要需要 ADO.NET Data Services。</span><span class="sxs-lookup"><span data-stu-id="78914-103">ADO.NET Data Services is required for a data feed export of SharePoint lists.</span></span> <span data-ttu-id="78914-104">SharePoint 2010 不會在 SharePoint 必要安裝程式中包含這個元件，所以您必須手動安裝它。</span><span class="sxs-lookup"><span data-stu-id="78914-104">SharePoint 2010 does not include this component in the SharePoint Prerequisite Installer program, so you must install it manually.</span></span>  
  
 <span data-ttu-id="78914-105">如果沒有此程序，當您嘗試使用匯出為資料摘要的 SharePoint 清單時，會出現下列錯誤：「基於安全理由，這份 XML 文件禁止使用 DTD。</span><span class="sxs-lookup"><span data-stu-id="78914-105">Without this prerequisite, you will get the following error when you attempt to use a SharePoint list that was exported as a data feed: "For security reasons DTD is prohibited in this XML document.</span></span> <span data-ttu-id="78914-106">若要啟用 DTD 處理，請將 XmlReaderSettings 上的 ProhibitDtd 屬性設定為 false，並且將這項設定傳入 XmlReader.Create 方法。」</span><span class="sxs-lookup"><span data-stu-id="78914-106">To enable DTD processing set the ProhibitDtd property on XmlReaderSettings to false and pass the settings into XmlReader.Create method."</span></span>  
  
 <span data-ttu-id="78914-107">使用下列程序，在您想要讓清單當做資料摘要匯出的每一部 SharePoint 伺服器上安裝 ADO.NET Data Services。</span><span class="sxs-lookup"><span data-stu-id="78914-107">Use the following instructions to install ADO.NET Data Services on every SharePoint server for which you want to allow lists to be exported as data feeds.</span></span>  
  
### <a name="download-and-install-adonet-data-services"></a><span data-ttu-id="78914-108">下載及安裝 ADO.NET Data Services</span><span class="sxs-lookup"><span data-stu-id="78914-108">Download and install ADO.NET Data Services</span></span>  
  
1.  <span data-ttu-id="78914-109">如需 sharepoint 2010 的硬體和軟體需求檔，請參閱[ (sharepoint 2010 的硬體和軟體需求) ](https://go.microsoft.com/fwlink/?LinkId=169734)</span><span class="sxs-lookup"><span data-stu-id="78914-109">Go to the hardware and software requirements documentation for SharePoint 2010, [Hardware and Software Requirements (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734)</span></span>  
  
2.  <span data-ttu-id="78914-110">在 [**存取適用的軟體**] 中，尋找對應到您所使用之作業系統的 ADO.NET 資料服務3.5 連結 (windows SERVER 2008 SP2 或 windows Server 2008 R2) 。</span><span class="sxs-lookup"><span data-stu-id="78914-110">In **Access to applicable software**, find the link for ADO.NET Data Services 3.5 that corresponds to the operating system you are using (either Windows Server 2008 SP2 or Windows Server 2008 R2).</span></span>  
  
3.  <span data-ttu-id="78914-111">按一下該連結，並執行安裝程式來安裝服務。</span><span class="sxs-lookup"><span data-stu-id="78914-111">Click the link and run the setup program that installs the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78914-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78914-112">See Also</span></span>  
 [<span data-ttu-id="78914-113">PowerPivot for SharePoint 2010 安裝</span><span class="sxs-lookup"><span data-stu-id="78914-113">PowerPivot for SharePoint 2010 Installation</span></span>](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
