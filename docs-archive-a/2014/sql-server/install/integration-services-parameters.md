---
title: Integration Services 參數 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, parameters
ms.assetid: b1bb3ea3-8097-4e76-b9c2-78a0f46a23bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 76a5ebe7018fdc58f02a4d2454d40f172c752c4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708086"
---
# <a name="integration-services-parameters"></a><span data-ttu-id="3decf-102">Integration Services 參數</span><span class="sxs-lookup"><span data-stu-id="3decf-102">Integration Services Parameters</span></span>
  <span data-ttu-id="3decf-103">針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ，您可以決定要分析 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 電腦上的封裝，或 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝檔案中的檔案。</span><span class="sxs-lookup"><span data-stu-id="3decf-103">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you can decide to analyze [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages on the computer, or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package files in the file system.</span></span> <span data-ttu-id="3decf-104">如果您要分析檔案系統中的檔案，請提供包含 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝之資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="3decf-104">If you analyze files in the file system, provide a path to the folder that contains the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3decf-105">選項</span><span class="sxs-lookup"><span data-stu-id="3decf-105">Options</span></span>  
 <span data-ttu-id="3decf-106">**分析電腦上的 SSIS 封裝**</span><span class="sxs-lookup"><span data-stu-id="3decf-106">**Analyze SSIS packages on Computer**</span></span>  
 <span data-ttu-id="3decf-107">選取此選項，即可分析電腦上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="3decf-107">Select this option to analyze [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages on the computer.</span></span> <span data-ttu-id="3decf-108">預設會選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="3decf-108">By default, this option is selected.</span></span>  
  
 <span data-ttu-id="3decf-109">**分析 SSIS 封裝檔案**</span><span class="sxs-lookup"><span data-stu-id="3decf-109">**Analyze SSIS package files**</span></span>  
 <span data-ttu-id="3decf-110">選取此選項，即可分析檔案系統中的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="3decf-110">Select this option to analyze [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages in the file system.</span></span>  
  
 <span data-ttu-id="3decf-111">**SSIS 封裝的路徑**</span><span class="sxs-lookup"><span data-stu-id="3decf-111">**Path to SSIS packages**</span></span>  
 <span data-ttu-id="3decf-112">找出保存 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的 UNC 或本機路徑。</span><span class="sxs-lookup"><span data-stu-id="3decf-112">Locate a UNC or local path that holds your [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="3decf-113">您不需要加入檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="3decf-113">You do not have to include file names.</span></span> <span data-ttu-id="3decf-114">如果您輸入的路徑無法存取，就無法按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="3decf-114">If the path you have entered cannot be accessed, you cannot click **Next**.</span></span> <span data-ttu-id="3decf-115">根據預設，此路徑是空白的。</span><span class="sxs-lookup"><span data-stu-id="3decf-115">By default, the path is blank.</span></span> <span data-ttu-id="3decf-116">只有當您選取 [**分析 SSIS 封裝**檔案] 時，才會啟用此欄位。</span><span class="sxs-lookup"><span data-stu-id="3decf-116">This field is enabled only when you select **Analyze SSIS package files**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3decf-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3decf-117">See Also</span></span>  
 <span data-ttu-id="3decf-118">[使用 Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="3decf-118">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="3decf-119">Upgrade Advisor 使用者介面參考</span><span class="sxs-lookup"><span data-stu-id="3decf-119">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
