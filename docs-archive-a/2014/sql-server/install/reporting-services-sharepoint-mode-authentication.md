---
title: Reporting Services SharePoint 模式驗證 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade SharePoint Mode [Reporting Services]
- SharePoint integration
- SharePoint Mode
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3b1316a1a49726ab0754f39160125425fec116d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705933"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a><span data-ttu-id="c3550-102">Reporting Services SharePoint 模式驗證</span><span class="sxs-lookup"><span data-stu-id="c3550-102">Reporting Services SharePoint Mode Authentication</span></span>
  <span data-ttu-id="c3550-103">您可以使用 \*\*\*\*[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 頁面，來指定目前 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝中所用服務帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="c3550-103">Use the **Reporting Services SharePoint Mode Authentication** page of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to specify the credentials of the service account that is used in the current [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation.</span></span> <span data-ttu-id="c3550-104">認證將會用於建立新的 SharePoint 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="c3550-104">The credentials will be used to create a new SharePoint application pool.</span></span> <span data-ttu-id="c3550-105">此外，也會建立一個新的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="c3550-105">Also, one new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint service application will be created.</span></span> <span data-ttu-id="c3550-106">服務應用程式名稱會包含上一個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3550-106">The service application name will contain the name of the previous [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c3550-107">選項</span><span class="sxs-lookup"><span data-stu-id="c3550-107">Options</span></span>  
  
-   <span data-ttu-id="c3550-108">**[SSRS 應用程式集區帳戶名稱]** 選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="c3550-108">The **SSRS Application Pool Account Name:** option is read only.</span></span> <span data-ttu-id="c3550-109">此值是用您所升級的現有 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝中的目前值來自動填入。</span><span class="sxs-lookup"><span data-stu-id="c3550-109">The value is automatically populated with the current value from the existing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation that you are upgrading.</span></span>  
  
-   <span data-ttu-id="c3550-110">如果應用程式集區帳戶不需要密碼， **[SSRS 應用程式集區帳戶密碼]** 選項就會停用。</span><span class="sxs-lookup"><span data-stu-id="c3550-110">The **SSRS Application Pool Account Password:** option will be disabled if the application pool account does not require a password.</span></span> <span data-ttu-id="c3550-111">例如，"NT Authority\NetworkService"。</span><span class="sxs-lookup"><span data-stu-id="c3550-111">For example, "NT Authority\NetworkService".</span></span> <span data-ttu-id="c3550-112">如果應用程式集區帳戶需要密碼，您必須輸入正確密碼，才能繼續升級。</span><span class="sxs-lookup"><span data-stu-id="c3550-112">If the application pool account does require a password, you cannot continue with upgrade until you type the correct password.</span></span>  
  
 <span data-ttu-id="c3550-113">如需詳細資訊，請參閱[升級和遷移 Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628) (https://go.microsoft.com/fwlink/?LinkID=245628) 。</span><span class="sxs-lookup"><span data-stu-id="c3550-113">For more information, see [Upgrade and Migrate Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628) (https://go.microsoft.com/fwlink/?LinkID=245628).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3550-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3550-114">See Also</span></span>  
 [<span data-ttu-id="c3550-115">升級和移轉 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="c3550-115">Upgrade and Migrate Reporting Services</span></span>](https://go.microsoft.com/fwlink/?LinkID=245628)  
  
  
