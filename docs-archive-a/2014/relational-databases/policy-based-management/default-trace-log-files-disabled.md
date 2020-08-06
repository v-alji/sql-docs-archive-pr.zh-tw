---
title: 預設追蹤記錄檔已停用 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0fed8fb006427b4dda9d99c57cbabca8538efcad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594007"
---
# <a name="default-trace-log-files-disabled"></a><span data-ttu-id="dcbe8-102">預設追蹤記錄檔已停用</span><span class="sxs-lookup"><span data-stu-id="dcbe8-102">Default Trace Log Files Disabled</span></span>
  <span data-ttu-id="dcbe8-103">此規則會檢查 sp_configure 預存程序 default trace enabled 選項的值，以判斷預設追蹤是否設定為 ON (1) 或 OFF (0)。</span><span class="sxs-lookup"><span data-stu-id="dcbe8-103">This rule checks the value of the sp_configure stored procedure default trace enabled option to determine whether default trace is set ON (1) or OFF (0).</span></span> <span data-ttu-id="dcbe8-104">當啟用這個選項時，預設追蹤會提供有關組態及 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]之 DDL 變更的資訊。</span><span class="sxs-lookup"><span data-stu-id="dcbe8-104">When this option is enabled, default tracing provides information about configuration and DDL changes to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="dcbe8-105">在某些情況下，當客戶和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務及支援中心在排除 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的問題時，這項資訊對於他們很有幫助。</span><span class="sxs-lookup"><span data-stu-id="dcbe8-105">In some cases, this information can be helpful for customers and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support when they troubleshooting issues with the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="dcbe8-106">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="dcbe8-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="dcbe8-107">使用 sp_configure 預存程序，將 default trace enabled 設定為 1 的值來啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="dcbe8-107">Use the sp_configure stored procedure to enable tracing by setting the value of default trace enabled to 1.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="dcbe8-108">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="dcbe8-108">For More Information</span></span>  
 [<span data-ttu-id="dcbe8-109">伺服器組態選項 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dcbe8-109">Server Configuration Options &#40;SQL Server&#41;</span></span>](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="dcbe8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcbe8-110">See Also</span></span>  
 [<span data-ttu-id="dcbe8-111">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="dcbe8-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
