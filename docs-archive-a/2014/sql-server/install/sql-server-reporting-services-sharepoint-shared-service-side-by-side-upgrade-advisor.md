---
title: Microsoft SQL Server Reporting Services SharePoint 共用服務已並存安裝 (Upgrade Advisor) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6ae1017e-129b-4702-9ea7-00ac9b024062
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b8a26fedd892dfb26dea4616efd46d3b3748b508
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598119"
---
# <a name="microsoft-sql-server-reporting-services-sharepoint-shared-service-is-installed-side-by-side-upgrade-advisor"></a><span data-ttu-id="225da-102">已並存安裝 Microsoft SQL Server Reporting Services SharePoint 共用服務 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="225da-102">Microsoft SQL Server Reporting Services SharePoint Shared Service is Installed Side by Side (Upgrade Advisor)</span></span>
  <span data-ttu-id="225da-103">Upgrade Advisor 偵測到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 共用服務與舊版並存安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="225da-103">Upgrade Advisor detected [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Shared service is installed side by side with a previous version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
||  
|-|  
|<span data-ttu-id="225da-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="225da-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="225da-105">元件</span><span class="sxs-lookup"><span data-stu-id="225da-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="225da-106">描述</span><span class="sxs-lookup"><span data-stu-id="225da-106">Description</span></span>  
 <span data-ttu-id="225da-107">Upgrade Advisor 偵測到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sharepoint 共用服務與舊版並存安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，而該版本不是以 SharePoint 共用服務架構為基礎。</span><span class="sxs-lookup"><span data-stu-id="225da-107">Upgrade Advisor detected [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Shared service is installed side by side with a previous version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] that is not based on the SharePoint shared service architecture.</span></span> <span data-ttu-id="225da-108">由於電腦上已並存安裝新舊 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 相關技術，因此升級遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="225da-108">Because the computer has both older and newer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint related technologies installed side by side, upgrade is blocked.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="225da-109">更正動作</span><span class="sxs-lookup"><span data-stu-id="225da-109">Corrective Action</span></span>  
 <span data-ttu-id="225da-110">若要繼續升級，您必須解除安裝其中一個現有的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝。</span><span class="sxs-lookup"><span data-stu-id="225da-110">To continue with upgrade, you must uninstall one of the existing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installations.</span></span> <span data-ttu-id="225da-111">移除其中一個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝之後，請重新執行 Upgrade Advisor，以便確認沒有其他升級問題。</span><span class="sxs-lookup"><span data-stu-id="225da-111">After removing one of the installations of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], re-run Upgrade Advisor to confirm that there are no other upgrade issues.</span></span>  
  
  
