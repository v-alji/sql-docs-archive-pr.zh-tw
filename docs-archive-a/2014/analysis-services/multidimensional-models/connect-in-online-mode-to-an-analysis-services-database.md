---
title: 以線上模式連接到 Analysis Services 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, connecting
ms.assetid: 33041234-7106-404f-a289-8e904f32aff2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 363beb7132eae92907198979fe2d9892c5d07b79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705645"
---
# <a name="connect-in-online-mode-to-an-analysis-services-database"></a><span data-ttu-id="7eaf6-102">在連線模式下連接至 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="7eaf6-102">Connect in Online Mode to an Analysis Services Database</span></span>
  <span data-ttu-id="7eaf6-103">您可以直接連接到現有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的資料庫，並直接修改該資料庫內的物件。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-103">You can connect directly to an existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and directly modify objects within that database.</span></span> <span data-ttu-id="7eaf6-104">當您直接連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫時，對物件的變更會立即發生，而且 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中不會建立任何 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-104">When you connect directly to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, changes to objects occur immediately and no [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project is created within [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-connect-directly-to-an-analysis-services-database-by-using-sql-server-data-tools"></a><span data-ttu-id="7eaf6-105">若要使用 SQL Server 資料工具直接連接到 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="7eaf6-105">To Connect Directly to an Analysis Services Database by using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="7eaf6-106">開啟 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-106">Open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="7eaf6-107">指向 **[檔案]** 功能表上的 **[開啟舊檔]** ，再按一下 **[Analysis Services 資料庫]**。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-107">On the **File** menu, point to **Open** and then click **Analysis Services Database**.</span></span>  
  
3.  <span data-ttu-id="7eaf6-108">選取 **[連接到現有的資料庫]**。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-108">Select **Connect to existing database**.</span></span>  
  
4.  <span data-ttu-id="7eaf6-109">指定伺服器名稱和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-109">Specify the server name and the database name.</span></span>  
  
     <span data-ttu-id="7eaf6-110">您可以輸入資料庫名稱或是查詢伺服器，以檢視伺服器上現有的資料庫。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-110">You can either type the database name or query the server to view the existing databases on the server.</span></span>  
  
5.  <span data-ttu-id="7eaf6-111">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-111">Click **OK**.</span></span>  
  
     <span data-ttu-id="7eaf6-112">您現在可以直接編輯 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫中的任何物件。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-112">You can now directly edit any objects within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eaf6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7eaf6-113">See Also</span></span>  
 <span data-ttu-id="7eaf6-114">[在開發階段使用 Analysis Services 專案和資料庫](work-with-analysis-services-projects-and-databases-in-development.md) </span><span class="sxs-lookup"><span data-stu-id="7eaf6-114">[Working with Analysis Services Projects and Databases During the Development Phase](work-with-analysis-services-projects-and-databases-in-development.md) </span></span>  
 [<span data-ttu-id="7eaf6-115">使用 SQL Server 資料工具 &#40;SSDT&#41; 建立多維度模型</span><span class="sxs-lookup"><span data-stu-id="7eaf6-115">Creating Multidimensional Models Using SQL Server Data Tools &#40;SSDT&#41;</span></span>](creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)  
  
  
