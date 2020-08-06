---
title: 從 SQL Server Management Studio 執行 Windows PowerShell | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0330e833aaa3344416a31aa700a2b1f6bb4a6e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595152"
---
# <a name="run-windows-powershell-from-sql-server-management-studio"></a><span data-ttu-id="67cf4-102">從 SQL Server Management Studio 執行 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="67cf4-102">Run Windows PowerShell from SQL Server Management Studio</span></span>
  <span data-ttu-id="67cf4-103">您可以從 **的** [物件總管] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中啟動 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="67cf4-103">You can start Windows PowerShell sessions from **Object Explorer** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]<span data-ttu-id="67cf4-104">會啟動 Windows PowerShell、載入 `sqlps` 模組，並將路徑內容設定為**物件總管**樹狀目錄中的相關聯節點。</span><span class="sxs-lookup"><span data-stu-id="67cf4-104">launches Windows PowerShell, loads the `sqlps` module, and sets the path context to the associated node in the **Object Explorer** tree.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="67cf4-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="67cf4-105">Before You Begin</span></span>  
 <span data-ttu-id="67cf4-106">當您在**物件總管**中指定物件的執行中 powershell 時， [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會啟動已載入和註冊 powershell 嵌入式管理單元的 Windows powershell 會話。</span><span class="sxs-lookup"><span data-stu-id="67cf4-106">When you specify running PowerShell for an object in **Object Explorer**, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] starts a Windows PowerShell session in which the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins have been loaded and registered.</span></span> <span data-ttu-id="67cf4-107">此工作階段的路徑會預設為您在 [物件總管] 中按一下滑鼠右鍵之物件的位置。</span><span class="sxs-lookup"><span data-stu-id="67cf4-107">The path for the session is preset to the location of the object you right clicked in Object Explorer.</span></span> <span data-ttu-id="67cf4-108">例如，如果您以滑鼠右鍵按一下物件總管中的 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫物件，並選取 [啟動 PowerShell]\*\*\*\* 時，Windows PowerShell 路徑會設定為以下內容：</span><span class="sxs-lookup"><span data-stu-id="67cf4-108">For example, if you right-click the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database object in Object Explorer and select **Start PowerShell**, the Windows PowerShell path is set to the following:</span></span>  
  
```
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## <a name="to-run-powershell-from-sql-server-management-studio"></a><span data-ttu-id="67cf4-109">從 SQL Server Management Studio 執行 PowerShell</span><span class="sxs-lookup"><span data-stu-id="67cf4-109">To run PowerShell from SQL Server Management Studio</span></span> 
  
1.  <span data-ttu-id="67cf4-110">開啟**物件總管**。</span><span class="sxs-lookup"><span data-stu-id="67cf4-110">Open **Object Explorer**.</span></span>  
  
2.  <span data-ttu-id="67cf4-111">導覽至要進行處理之物件的節點。</span><span class="sxs-lookup"><span data-stu-id="67cf4-111">Navigate to the node for the object to be worked on.</span></span>  
  
3.  <span data-ttu-id="67cf4-112">以滑鼠右鍵按一下物件，並選取 [啟動 PowerShell]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="67cf4-112">Right-click the object and select **Start PowerShell**.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="67cf4-113">權限</span><span class="sxs-lookup"><span data-stu-id="67cf4-113">Permissions</span></span>  
 <span data-ttu-id="67cf4-114">從 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]開啟 PowerShell 時，它不會以系統管理員權限執行，這可能會阻礙某些活動 (例如 WMI 的呼叫)。</span><span class="sxs-lookup"><span data-stu-id="67cf4-114">When opened from [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], PowerShell does not run with Administrator privileges which may prevent some activities such as calls to WMI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67cf4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67cf4-115">See Also</span></span>  
 [<span data-ttu-id="67cf4-116">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="67cf4-116">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
