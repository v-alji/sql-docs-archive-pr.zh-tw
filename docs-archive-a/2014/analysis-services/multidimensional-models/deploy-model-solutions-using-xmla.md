---
title: 使用 XMLA 部署模型方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- XML scripts [Analysis Services]
- scripts [Analysis Services], deployment
- deploying [Analysis Services], XML scripts
- Analysis Services deployments, XML scripts
ms.assetid: a8cb1837-fcac-4730-bea4-a72cf94d9f7c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b78490c5ab6ad3ba5e52bb82d4be254e3f5f102b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708765"
---
# <a name="deploy-model-solutions-using-xmla"></a><span data-ttu-id="f36c9-102">使用 XMLA 部署模型方案</span><span class="sxs-lookup"><span data-stu-id="f36c9-102">Deploy Model Solutions Using XMLA</span></span>
  <span data-ttu-id="f36c9-103">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，[編寫資料庫的指令碼為]\*\*\*\* 命令的 [CREATE 至]\*\*\*\* 選項會建立整個 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫或其中一個構成物件的 XML 指令碼。</span><span class="sxs-lookup"><span data-stu-id="f36c9-103">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], the **CREATE To** option of the **Script Database As** command creates an XML script of an entire [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or one of its constituent objects.</span></span> <span data-ttu-id="f36c9-104">產生的指令碼可在另一部電腦上執行，來重建 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫的結構描述 (中繼資料)。</span><span class="sxs-lookup"><span data-stu-id="f36c9-104">The resulting script can then be run on another computer to recreate the schema (metadata) of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="f36c9-105">此指令碼會產生整個資料庫，而且使用此指令碼時，沒有可累加更新已部署物件的機制。</span><span class="sxs-lookup"><span data-stu-id="f36c9-105">The script generates the entire database, and there is no mechanism for incrementally updating already deployed objects when using the script.</span></span> <span data-ttu-id="f36c9-106">執行指令碼及部署資料庫之後，必須先加以處理，使用者才可以瀏覽新建的資料庫。</span><span class="sxs-lookup"><span data-stu-id="f36c9-106">After running the script and deploying the database, the newly created database must be processed before users can browse it.</span></span>  
  
 <span data-ttu-id="f36c9-107">如需 [編寫資料庫的指令碼為]\*\*\*\* 命令的詳細資訊，請參閱[記錄和編寫 Analysis Services 資料庫的指令碼](document-and-script-an-analysis-services-database.md)。</span><span class="sxs-lookup"><span data-stu-id="f36c9-107">For more information about the **Script Database As** command, see [Document and Script an Analysis Services Database](document-and-script-an-analysis-services-database.md).</span></span>  
  
## <a name="modifying-object-properties-in-the-xml-script"></a><span data-ttu-id="f36c9-108">在 XML 指令碼中修改物件屬性</span><span class="sxs-lookup"><span data-stu-id="f36c9-108">Modifying Object Properties in the XML Script</span></span>  
 <span data-ttu-id="f36c9-109">使用 [編寫資料庫的指令碼為]\*\*\*\* 命令時，您不能修改資料庫物件的特定屬性 (例如資料庫名稱、資料來源連接字串和安全性設定)。</span><span class="sxs-lookup"><span data-stu-id="f36c9-109">When using the **Script Database As** command, you cannot modify specific properties (such as the database name, data source connection strings, and security settings) of the database objects.</span></span> <span data-ttu-id="f36c9-110">這些屬性必須在產生指令碼之後，於指令碼中手動修改；或在執行指令碼之後，在已部署的資料庫中加以修改。</span><span class="sxs-lookup"><span data-stu-id="f36c9-110">These properties must either be manually modified in the script after the script has been generated or modified in the deployed database after running the script.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f36c9-111">如果您針對資料來源或模擬目的在連接字串中指定密碼，XML 指令碼將不會包含這項資訊。</span><span class="sxs-lookup"><span data-stu-id="f36c9-111">The XML script will not contain the password if this is specified in either the connection string for a data source or for impersonation purposes.</span></span> <span data-ttu-id="f36c9-112">由於在這種狀況下需要使用密碼進行處理，所以您必須在 XML 指令碼執行之前手動加入密碼，或在 XML 指令碼執行之後加入密碼。</span><span class="sxs-lookup"><span data-stu-id="f36c9-112">Since the password is required for processing purposes in this scenario, you will either need to add this manually to the XML script before it executes or add it after the XML script executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f36c9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f36c9-113">See Also</span></span>  
 <span data-ttu-id="f36c9-114">[使用部署嚮導部署模型方案](deploy-model-solutions-using-the-deployment-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="f36c9-114">[Deploy Model Solutions Using the Deployment Wizard](deploy-model-solutions-using-the-deployment-wizard.md) </span></span>  
 [<span data-ttu-id="f36c9-115">同步處理 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="f36c9-115">Synchronize Analysis Services Databases</span></span>](synchronize-analysis-services-databases.md)  
  
  
