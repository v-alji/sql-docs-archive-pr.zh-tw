---
title: 授與 Integration Services 服務的許可權 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0c2caa68-7834-4ea0-bd77-4f3a7c86d634
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0e7ab0c2f482e5a0b1bfeaa06f38ec5a886420a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592135"
---
# <a name="grant-permissions-to-integration-services-service"></a><span data-ttu-id="a0fca-102">授予 Integration Services 服務的權限</span><span class="sxs-lookup"><span data-stu-id="a0fca-102">Grant Permissions to Integration Services Service</span></span>
  <span data-ttu-id="a0fca-103">在舊版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中，當您安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 時，Users 群組中的所有使用者預設都能存取 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="a0fca-103">In previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], by default when you installed [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] all users in the Users group had access to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="a0fca-104">當您安裝目前版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]時，使用者無法存取 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="a0fca-104">When you install the current release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], users do not have access to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="a0fca-105">因此，服務預設是安全的。</span><span class="sxs-lookup"><span data-stu-id="a0fca-105">The service is secure by default.</span></span> <span data-ttu-id="a0fca-106">安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 之後，管理員必須授與該服務的存取權。</span><span class="sxs-lookup"><span data-stu-id="a0fca-106">After [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is installed, the administrator must grant access to the service.</span></span>  
  
### <a name="to-grant-access-to-the-integration-services-service"></a><span data-ttu-id="a0fca-107">授與 Integration Services 服務的存取權</span><span class="sxs-lookup"><span data-stu-id="a0fca-107">To grant access to the Integration Services service</span></span>  
  
1.  <span data-ttu-id="a0fca-108">執行 Dcomcnfg.exe。</span><span class="sxs-lookup"><span data-stu-id="a0fca-108">Run Dcomcnfg.exe.</span></span> <span data-ttu-id="a0fca-109">Dcomcnfg.exe 提供使用者介面，可供修改登錄中的某些設定。</span><span class="sxs-lookup"><span data-stu-id="a0fca-109">Dcomcnfg.exe provides a user interface for modifying certain settings in the registry.</span></span>  
  
2.  <span data-ttu-id="a0fca-110">在 [元件服務]\*\*\*\* 對話方塊中，展開 [元件服務] > [電腦] > [我的電腦] > [DCOM 組態] 節點。</span><span class="sxs-lookup"><span data-stu-id="a0fca-110">In the **Component Services** dialog, expand the Component Services > Computers > My Computer > DCOM Config node.</span></span>  
  
3.  <span data-ttu-id="a0fca-111">以滑鼠右鍵按一下**Microsoft SQL Server Integration Services 12.0**，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="a0fca-111">Right-click **Microsoft SQL Server Integration Services 12.0**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="a0fca-112">在 **[安全性]** 索引標籤上，按一下 **[啟動和啟用權限]** 區域中的 **[編輯]** 。</span><span class="sxs-lookup"><span data-stu-id="a0fca-112">On the **Security** tab, click **Edit** in the **Launch and Activation Permissions** area.</span></span>  
  
5.  <span data-ttu-id="a0fca-113">加入使用者並指派適當的權限，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="a0fca-113">Add users and assign appropriate permissions, and then click Ok.</span></span>  
  
6.  <span data-ttu-id="a0fca-114">重複步驟 4 - 5，以設定存取權限。</span><span class="sxs-lookup"><span data-stu-id="a0fca-114">Repeat steps 4 - 5 for Access Permissions.</span></span>  
  
7.  <span data-ttu-id="a0fca-115">啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="a0fca-115">Restart SQL Server Management Studio.</span></span>  
  
8.  <span data-ttu-id="a0fca-116">重新啟動 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="a0fca-116">Restart the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Service.</span></span>  
  
  
