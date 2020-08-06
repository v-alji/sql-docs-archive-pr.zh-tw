---
title: Integration Services 服務的存取權 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- viewing packages while running
- displaying packacges while running
- security [Integration Services], running packages
- packages [Integration Services], security
- current packages running
- Integration Services packages, security
- SQL Server Integration Services packages, security
ms.assetid: 1088aafc-14c5-4e7d-9930-606a24c3049b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7dd6fbed4bedc285069306ab4c400f0f67f9f293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592825"
---
# <a name="access-to-the-integration-services-service"></a><span data-ttu-id="7bf33-102">對 Integration Services 服務的存取權</span><span class="sxs-lookup"><span data-stu-id="7bf33-102">Access to the Integration Services Service</span></span>
  <span data-ttu-id="7bf33-103">封裝保護等級可限制已獲允許編輯和執行封裝的人員。</span><span class="sxs-lookup"><span data-stu-id="7bf33-103">Package protection levels can limit who is allowed to edit and execute a package.</span></span> <span data-ttu-id="7bf33-104">您需要額外的保護措施來限制有誰能夠檢視目前在伺服器上執行的封裝清單，以及有誰能夠停止目前在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中執行的封裝。</span><span class="sxs-lookup"><span data-stu-id="7bf33-104">Additional protection is needed to limit who can view the list of packages currently running on a server and who can stop currently executing packages in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="7bf33-105">會使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服務列出正在執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7bf33-105">uses the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] service to list running packages.</span></span> <span data-ttu-id="7bf33-106">Windows Administrators 群組的成員可以檢視和停止所有目前正在執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7bf33-106">Members of the Windows Administrators group can view and stop all currently running packages.</span></span> <span data-ttu-id="7bf33-107">非 Administrators 群組成員的使用者只能檢視和停止他們所啟動的封裝。</span><span class="sxs-lookup"><span data-stu-id="7bf33-107">Users who are not members of the Administrators group can view and stop only packages that they started.</span></span>  
  
 <span data-ttu-id="7bf33-108">限制存取執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服務的電腦很重要，特別是可列舉遠端資料夾的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="7bf33-108">It is important to restrict access to computers that run an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] service, especially an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] service that can enumerate remote folders.</span></span> <span data-ttu-id="7bf33-109">任何已驗證的使用者都可以要求列舉封裝。</span><span class="sxs-lookup"><span data-stu-id="7bf33-109">Any authenticated user can request the enumeration of packages.</span></span> <span data-ttu-id="7bf33-110">服務即使找不到該服務，仍會列舉資料夾。</span><span class="sxs-lookup"><span data-stu-id="7bf33-110">Even if the service doesn not find the service, the service enumerates folders.</span></span> <span data-ttu-id="7bf33-111">這些資料夾名稱對惡意使用者可能很有用。</span><span class="sxs-lookup"><span data-stu-id="7bf33-111">These folder names may be useful to a malicious user.</span></span> <span data-ttu-id="7bf33-112">如果管理員已設定服務來列舉遠端電腦上的資料夾，則使用者還可查看他們通常無法看到的資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="7bf33-112">If an administrator has configured the service to enumerate folders on a remote machine, users may also be able to see folder names that they would normally not be able to see.</span></span>  
  
  
