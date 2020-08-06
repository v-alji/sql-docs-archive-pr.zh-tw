---
title: 訂閱者屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.subscribers.f1
helpviewer_keywords:
- Subscriber Properties dialog box
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81ab9cf5f277ccfe1044e5a7083f019db9d843ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708165"
---
# <a name="subscriber-properties"></a><span data-ttu-id="ad0ff-102">訂閱者屬性</span><span class="sxs-lookup"><span data-stu-id="ad0ff-102">Subscriber Properties</span></span>
  <span data-ttu-id="ad0ff-103">[訂閱者屬性]  對話方塊包含執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 之前 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 版本訂閱者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ad0ff-103">The **Subscriber Properties** dialog box contains information relevant to Subscribers running versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="ad0ff-104">選項。</span><span class="sxs-lookup"><span data-stu-id="ad0ff-104">Options</span></span>  
 <span data-ttu-id="ad0ff-105">**代理程式至訂閱者的連接**</span><span class="sxs-lookup"><span data-stu-id="ad0ff-105">**Agent Connection to the Subscriber**</span></span>  
 <span data-ttu-id="ad0ff-106">散發代理程式和合併代理程式從散發者連接至訂閱者所用的內容。這個選項只適用於 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以前的版本。</span><span class="sxs-lookup"><span data-stu-id="ad0ff-106">The context under which the Distribution Agent and Merge Agent connect from the Distributor to the Subscriber This applies only to versions before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="ad0ff-107">選取 **[模擬代理程式處理帳戶]** ，即可使用散發者端之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 帳戶的內容與訂閱者建立連接，或指定 **[SQL Server 驗證]** ，然後輸入 **[登入]** 和 **[密碼]** 的值。</span><span class="sxs-lookup"><span data-stu-id="ad0ff-107">Select **Impersonate agent process account** to make connections to the Subscriber using the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent account at the Distributor, or specify **SQL Server Authentication**, and then enter a value for **Login** and **Password**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="ad0ff-108">建議您選取 **[模擬代理程式處理帳戶]** 。</span><span class="sxs-lookup"><span data-stu-id="ad0ff-108">recommends that you select **Impersonate agent process account**.</span></span>  
  
 <span data-ttu-id="ad0ff-109">若為 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本，每個訂閱的連接資訊會在「新增訂閱精靈」中指定，而且可在 **[訂閱屬性]** 對話方塊中進行變更。</span><span class="sxs-lookup"><span data-stu-id="ad0ff-109">For [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions, connection information is specified for each subscription in the New Subscription Wizard and can be changed in the **Subscription Properties** dialog box.</span></span>  
  
 <span data-ttu-id="ad0ff-110">**預設代理程式排程**</span><span class="sxs-lookup"><span data-stu-id="ad0ff-110">**Default Agent Schedules**</span></span>  
 <span data-ttu-id="ad0ff-111">執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以前 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]版本的訂閱者在「新增訂閱精靈」中使用的預設排程。</span><span class="sxs-lookup"><span data-stu-id="ad0ff-111">The default schedule used in the New Subscription Wizard for Subscribers running versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span>  
  
 <span data-ttu-id="ad0ff-112">**其他**</span><span class="sxs-lookup"><span data-stu-id="ad0ff-112">**Miscellaneous**</span></span>  
 <span data-ttu-id="ad0ff-113">包含訂閱者和訂閱者類型上的資訊。</span><span class="sxs-lookup"><span data-stu-id="ad0ff-113">Includes information on the Subscriber and Subscriber type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad0ff-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad0ff-114">See Also</span></span>  
 [<span data-ttu-id="ad0ff-115">檢視及修改散發者和發行者屬性</span><span class="sxs-lookup"><span data-stu-id="ad0ff-115">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

 [<span data-ttu-id="ad0ff-116">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="ad0ff-116">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
