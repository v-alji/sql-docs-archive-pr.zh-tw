---
title: 在物件總管中隱藏系統物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- hiding system objects
- system objects [SQL Server]
- objects [SQL Server], hiding
- Object Explorer, hiding objects
ms.assetid: c01d8804-838c-4f75-b78c-80e41e4fffdc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1e039446191154144dd6660fa6e8d3b4b65d1013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584255"
---
# <a name="hide-system-objects-in-object-explorer"></a><span data-ttu-id="2ab64-102">在物件總管中隱藏系統物件</span><span class="sxs-lookup"><span data-stu-id="2ab64-102">Hide System Objects in Object Explorer</span></span>
  <span data-ttu-id="2ab64-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 [物件總管] 中隱藏系統物件。</span><span class="sxs-lookup"><span data-stu-id="2ab64-103">This topic describes how to hide system objects in Object Explorer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="2ab64-104">物件總管的 [資料庫]  節點包含諸如系統資料庫的系統物件。</span><span class="sxs-lookup"><span data-stu-id="2ab64-104">The **Databases** node of Object Explorer contains system objects such as the system databases.</span></span> <span data-ttu-id="2ab64-105">使用 [工具]  /[選項]  頁面，隱藏系統物件。</span><span class="sxs-lookup"><span data-stu-id="2ab64-105">Use the **Tools**/**Options** pages to hide the system objects.</span></span> <span data-ttu-id="2ab64-106">某些系統物件 (如系統函數和系統資料類型) 不受這個設定所影響。</span><span class="sxs-lookup"><span data-stu-id="2ab64-106">Some system objects, such as system functions and system data types, are not affected by this setting.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2ab64-107">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2ab64-107">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-hide-system-objects-in-object-explorer"></a><span data-ttu-id="2ab64-108">若要在物件總管中隱藏系統物件</span><span class="sxs-lookup"><span data-stu-id="2ab64-108">To hide system objects in Object Explorer</span></span>  
  
1.  <span data-ttu-id="2ab64-109">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="2ab64-109">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="2ab64-110">在 [環境/啟動]  頁面上，選取 [在物件總管中隱藏系統物件]  ，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2ab64-110">On the **Environment/Startup** page, select **Hide system objects in Object Explorer**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="2ab64-111">在 [SQL Server Management Studio]  對話方塊中，按一下 [確定]  ，以確認必須重新啟動 SQL Server Management Studio，這個變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="2ab64-111">In the **SQL Server Management Studio** dialog box, click **OK** to acknowledge that SQL Server Management Studio must be restarted for this change to take effect.</span></span>  
  
4.  <span data-ttu-id="2ab64-112">關閉並重新開啟 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="2ab64-112">Close and reopen SQL Server Management Studio.</span></span>  
  
  
