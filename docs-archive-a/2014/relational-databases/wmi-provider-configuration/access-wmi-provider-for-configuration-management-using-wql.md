---
title: 使用 WQL 存取設定管理的 WMI 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b58297c5e292ceb18a6e2e50e2b25b9aa352e2fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584311"
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a><span data-ttu-id="c8252-102">使用 WQL 存取組態管理的 WMI 提供者</span><span class="sxs-lookup"><span data-stu-id="c8252-102">Access WMI Provider for Configuration Management using WQL</span></span>
  <span data-ttu-id="c8252-103">本節描述如何針對電腦管理的 WMI 提供者執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Management Instrumentation 查詢語言 (WQL) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c8252-103">This section describes how to execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Management Instrumentation Query Language (WQL) statements against the WMI Provider for Computer Management.</span></span>  
  
 <span data-ttu-id="c8252-104">此範例使用 WQL 編輯器 WBEMtest.exe 來針對 WMI 提供者執行 WQL 查詢，以列舉 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務、網路通訊協定和別名。</span><span class="sxs-lookup"><span data-stu-id="c8252-104">The example uses a WQL editor, WBEMtest.exe, to run WQL queries against the WMI Provider to enumerate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, network protocols, and aliases.</span></span>  
  
### <a name="querying-services-using-wbemtest"></a><span data-ttu-id="c8252-105">使用 WBEMtest 查詢服務</span><span class="sxs-lookup"><span data-stu-id="c8252-105">Querying services using WBEMtest</span></span>  
  
1.  <span data-ttu-id="c8252-106">在 [**開始**] 功能表中，按一下 [**執行**]，然後輸入 `WBEMtest` 。</span><span class="sxs-lookup"><span data-stu-id="c8252-106">From the **Start** menu, click **Run**, and then enter `WBEMtest`.</span></span>  
  
2.  <span data-ttu-id="c8252-107">[WBEMtest.exe] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="c8252-107">The WBEMtest.exe dialog appears.</span></span> <span data-ttu-id="c8252-108">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="c8252-108">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="c8252-109">在第一個文字欄位中，輸入電腦管理的 WMI 提供者命名空間：root\Microsoft\SqlServer\ComputerManagement11。</span><span class="sxs-lookup"><span data-stu-id="c8252-109">In the first text field, type the WMI Provider for Computer Management namespace: root\Microsoft\SqlServer\ComputerManagement11.</span></span> <span data-ttu-id="c8252-110">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="c8252-110">Click **Connect**.</span></span>  
  
4.  <span data-ttu-id="c8252-111">按一下 **[查詢]**。</span><span class="sxs-lookup"><span data-stu-id="c8252-111">Click **Query**.</span></span> <span data-ttu-id="c8252-112">輸入會傳回目前在本機電腦上執行之服務的查詢：**選取 [ \* 從 SqlService]。**</span><span class="sxs-lookup"><span data-stu-id="c8252-112">Type a query that returns the current services running on the local computer: **SELECT \* FROM SqlService.**</span></span> <span data-ttu-id="c8252-113">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="c8252-113">Click **Apply**.</span></span>  
  
5.  <span data-ttu-id="c8252-114">加入 `WHERE ServiceName = "MSSQLSERVER"` 來進一步精簡查詢。</span><span class="sxs-lookup"><span data-stu-id="c8252-114">Further refine the query by adding `WHERE ServiceName = "MSSQLSERVER"`.</span></span>  
  
  
