---
title: 設定追蹤定義預設值 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], defaults
ms.assetid: ab9fc570-797d-411e-814f-1c46d2d5feae
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90b031de11f166a40e79ce4289eba508ba923c52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585723"
---
# <a name="set-trace-definition-defaults-sql-server-profiler"></a><span data-ttu-id="de6fd-102">設定追蹤定義預設值 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="de6fd-102">Set Trace Definition Defaults (SQL Server Profiler)</span></span>
  <span data-ttu-id="de6fd-103">追蹤定義預設值是指用於每個提供者或伺服器的預設追蹤範本。</span><span class="sxs-lookup"><span data-stu-id="de6fd-103">The trace definition default is the default trace template that is used for each provider or server.</span></span> <span data-ttu-id="de6fd-104">您可為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]設定預設追蹤範本。</span><span class="sxs-lookup"><span data-stu-id="de6fd-104">You can set default trace templates for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
### <a name="to-set-trace-definition-defaults"></a><span data-ttu-id="de6fd-105">若要設定追蹤定義預設值</span><span class="sxs-lookup"><span data-stu-id="de6fd-105">To set trace definition defaults</span></span>  
  
1.  <span data-ttu-id="de6fd-106">在 [檔案]  功能表上，選取 [範本]  ，然後按一下 [編輯範本]  。</span><span class="sxs-lookup"><span data-stu-id="de6fd-106">On the **File** menu, select **Templates**, and then click **Edit Template.**</span></span>  
  
2.  <span data-ttu-id="de6fd-107">在 [追蹤範本屬性]  對話方塊的 [一般]  索引標籤上，從 [選取伺服器類型]  清單中選取伺服器類型。</span><span class="sxs-lookup"><span data-stu-id="de6fd-107">In the **Trace Template Properties** dialog box, on the **General**tab, select a server type from the **Select server type**list.</span></span>  
  
3.  <span data-ttu-id="de6fd-108">在 [選取範本名稱]  清單中，選取您要用做追蹤定義預設值的範本名稱。</span><span class="sxs-lookup"><span data-stu-id="de6fd-108">In the **Select template name**list, select the name of the template that you want to use as the trace definition default.</span></span>  
  
4.  <span data-ttu-id="de6fd-109">選取 [作為所選取伺服器類型的預設範本]  。</span><span class="sxs-lookup"><span data-stu-id="de6fd-109">Select **Use as a default template for selected server type**.</span></span>  
  
5.  <span data-ttu-id="de6fd-110">如有需要，請按一下 [事件選取範圍]  索引標籤以修改範本。</span><span class="sxs-lookup"><span data-stu-id="de6fd-110">If necessary, click the **Events Selection**tab to modify the template.</span></span>  
  
6.  <span data-ttu-id="de6fd-111">按一下 [檔案]  。</span><span class="sxs-lookup"><span data-stu-id="de6fd-111">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de6fd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de6fd-112">See Also</span></span>  
 <span data-ttu-id="de6fd-113">[SQL Server Profiler 範本](sql-server-profiler-templates.md) </span><span class="sxs-lookup"><span data-stu-id="de6fd-113">[SQL Server Profiler Templates](sql-server-profiler-templates.md) </span></span>  
 [<span data-ttu-id="de6fd-114">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="de6fd-114">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
