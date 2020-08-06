---
title: SqlServerAlias 類別 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- SqlServerAlias Class
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServerAlias class
ms.assetid: 475662b9-6985-45bf-b1e9-b0f26ef50443
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 46994409cc6a5119c9144eb7a3a4b9a8a9a22c44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606672"
---
# <a name="sqlserveralias-class"></a><span data-ttu-id="fb465-102">SqlServerAlias 類別</span><span class="sxs-lookup"><span data-stu-id="fb465-102">SqlServerAlias Class</span></span>
  <span data-ttu-id="fb465-103">[SqlServerAlias 類別](sqlserveralias-class.md)代表伺服器連接別名。</span><span class="sxs-lookup"><span data-stu-id="fb465-103">The [SqlServerAlias Class](sqlserveralias-class.md) class represents a server connection alias.</span></span>  
  
 <span data-ttu-id="fb465-104">當以下兩個情況同時發生時，就需要伺服器連接別名。</span><span class="sxs-lookup"><span data-stu-id="fb465-104">A server connection alias is required when both the following occur:</span></span>  
  
-   <span data-ttu-id="fb465-105">用戶端透過 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不是預設網路傳輸的網路傳輸來連接的實例。</span><span class="sxs-lookup"><span data-stu-id="fb465-105">The client is connecting to an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] over a network transport that is not the default network transport.</span></span>  
  
-   <span data-ttu-id="fb465-106">用戶端連接的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體會接聽替代具名管道。</span><span class="sxs-lookup"><span data-stu-id="fb465-106">The instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to which the client is connected listens on an alternate named pipe.</span></span>  
  
 <span data-ttu-id="fb465-107">**注意：**[SqlServerAlias 類別](sqlserveralias-class.md)會 `Put` 從 Provider 類別繼承方法。</span><span class="sxs-lookup"><span data-stu-id="fb465-107">**Note:** The [SqlServerAlias Class](sqlserveralias-class.md) inherits the `Put` method from the Provider class.</span></span> <span data-ttu-id="fb465-108">但是，它不會傳回如 `Provider::Put` 方法指示的任何結果。</span><span class="sxs-lookup"><span data-stu-id="fb465-108">However, it does not return any results as indicated by the `Provider::Put` method.</span></span> <span data-ttu-id="fb465-109">如需詳細資訊，請參閱 WMI 文件集。</span><span class="sxs-lookup"><span data-stu-id="fb465-109">For more information, see the WMI documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb465-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb465-110">See Also</span></span>  
 [<span data-ttu-id="fb465-111">設定用戶端通訊協定</span><span class="sxs-lookup"><span data-stu-id="fb465-111">Configure Client Protocols</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
