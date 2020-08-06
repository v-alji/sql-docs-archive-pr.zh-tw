---
title: 測試使用者的權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8c109eebb4bf06bf7605ca3b7b5930ce18951e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596749"
---
# <a name="test-a-user39s-permissions-master-data-services"></a><span data-ttu-id="3fc60-102">測試使用者的權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3fc60-102">Test a User&#39;s Permissions (Master Data Services)</span></span>
  <span data-ttu-id="3fc60-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以建立測試使用者並登入 Web 應用程式來測試權限。當使用者嘗試存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] URL 時，就會驗證使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="3fc60-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can create a test user and log into the web application to test permissions.When a user attempts to access the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] URL, the user's credentials are authenticated.</span></span> <span data-ttu-id="3fc60-104">在 Internet Explorer 中，安全性設定會控制這項驗證是自動發生，還是使用者必須輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="3fc60-104">In Internet Explorer, security settings control whether this occurs automatically or if the user must enter a user name and password.</span></span> <span data-ttu-id="3fc60-105">若要變更這些設定，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3fc60-105">To change these settings, complete the following steps:</span></span>  
  
### <a name="to-test-a-users-security"></a><span data-ttu-id="3fc60-106">測試使用者的安全性</span><span class="sxs-lookup"><span data-stu-id="3fc60-106">To test a user's security</span></span>  
  
1.  <span data-ttu-id="3fc60-107">在 Internet Explorer 7 及更新版本中，依序按一下 **[工具]**、 **[網際網路選項]** 和 **[安全性]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3fc60-107">In Internet Explorer 7 and later, click **Tools**, **Internet Options**, and then click the **Security** tab.</span></span>  
  
2.  <span data-ttu-id="3fc60-108">依序按一下 **[近端內部網路]** 和 **[自訂等級]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3fc60-108">Click **Local Intranet** and then the **Custom Level** button.</span></span>  
  
3.  <span data-ttu-id="3fc60-109">在 **[使用者驗證]** 區段中，選擇 **[提示輸入使用者名稱及密碼]**。</span><span class="sxs-lookup"><span data-stu-id="3fc60-109">In the **User Authentication** section, choose **Prompt for user name and password**.</span></span>  
  
4.  <span data-ttu-id="3fc60-110">下次您開啟瀏覽器視窗時，將提示您輸入使用者名和密碼。</span><span class="sxs-lookup"><span data-stu-id="3fc60-110">The next time you open the browser window, you will be prompted for a user name and password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc60-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fc60-111">See Also</span></span>  
 [<span data-ttu-id="3fc60-112">安全性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc60-112">Security &#40;Master Data Services&#41;</span></span>](security-master-data-services.md)  
  
  
