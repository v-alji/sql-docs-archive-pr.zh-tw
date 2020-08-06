---
title: 部署專案之後設定參數值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c9dcca4d-f1a0-45ec-b078-f4d372589baf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 39572594e429b61de0641c6e6929e84105138f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709753"
---
# <a name="set-parameter-values-after-the-project-is-deployed"></a><span data-ttu-id="c96b2-102">部署專案之後設定參數值</span><span class="sxs-lookup"><span data-stu-id="c96b2-102">Set Parameter Values After the Project Is Deployed</span></span>
  <span data-ttu-id="c96b2-103">部署精靈可讓您在將專案部署到目錄時，設定伺服器預設參數值。</span><span class="sxs-lookup"><span data-stu-id="c96b2-103">The Deployment Wizard allows you to set server default parameter values when you deploy your project to the catalog.</span></span> <span data-ttu-id="c96b2-104">專案在目錄中之後，您可以使用 SQL Server Management Studio (SSMS) 物件總管或 Transact-SQL 來設定伺服器預設值。</span><span class="sxs-lookup"><span data-stu-id="c96b2-104">After your project is in the catalog, you can use SQL Server Management Studio (SSMS) Object Explorer or Transact-SQL to set server default values.</span></span>  
  
### <a name="to-set-server-defaults-with-ssms-object-explorer"></a><span data-ttu-id="c96b2-105">若要使用 SSMS 物件總管來設定伺服器預設值，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c96b2-105">To set server defaults with SSMS Object Explorer:</span></span>  
  
1.  <span data-ttu-id="c96b2-106">選取並以滑鼠右鍵按一下 [Integration Services]\*\*\*\* 節點底下的專案。</span><span class="sxs-lookup"><span data-stu-id="c96b2-106">Select and right-click the project under the **Integration Services** node.</span></span>  
  
2.  <span data-ttu-id="c96b2-107">按一下 **[屬性]** ，以開啟 **[專案屬性]** 對話方塊視窗。</span><span class="sxs-lookup"><span data-stu-id="c96b2-107">Click **Properties** to open the **Project Properties** dialog window.</span></span>  
  
3.  <span data-ttu-id="c96b2-108">按一下 **[選取頁面]** 底下的 **[參數]**，以開啟參數頁面。</span><span class="sxs-lookup"><span data-stu-id="c96b2-108">Open the parameters page by clicking **Parameters** under **Select a page**.</span></span>  
  
4.  <span data-ttu-id="c96b2-109">在 **[參數]** 清單選取所需的參數。</span><span class="sxs-lookup"><span data-stu-id="c96b2-109">Select the desired parameter in the **Parameters** list.</span></span> <span data-ttu-id="c96b2-110">附註： **[容器]** 資料行有助於區分專案參數與封裝參數。</span><span class="sxs-lookup"><span data-stu-id="c96b2-110">Note: The **Container** column helps distinguish project parameters from package parameters.</span></span>  
  
5.  <span data-ttu-id="c96b2-111">在 **[值]** 資料行中，指定所需的伺服器預設參數值。</span><span class="sxs-lookup"><span data-stu-id="c96b2-111">In the **Value** column, specify the desired server default parameter value.</span></span>  
  
 <span data-ttu-id="c96b2-112">若要使用 Transact-SQL 設定伺服器預設值，請使用 [catalog.set_object_parameter_value &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database) 預存程序。</span><span class="sxs-lookup"><span data-stu-id="c96b2-112">To set server defaults with Transact-SQL, use the [catalog.set_object_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database) stored procedure.</span></span> <span data-ttu-id="c96b2-113">若要檢視目前的伺服器預設值，請查詢 [catalog.object_parameters &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) 檢視。</span><span class="sxs-lookup"><span data-stu-id="c96b2-113">To view current server defaults, query the [catalog.object_parameters &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) view.</span></span> <span data-ttu-id="c96b2-114">若要清除伺服器預設值，請使用 [catalog.clear_object_parameter_value &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database) 預存程序。</span><span class="sxs-lookup"><span data-stu-id="c96b2-114">To clear a server default value, use the [catalog.clear_object_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database) stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c96b2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c96b2-115">See Also</span></span>  
 [<span data-ttu-id="c96b2-116">Integration Services &#40;SSIS&#41; 參數</span><span class="sxs-lookup"><span data-stu-id="c96b2-116">Integration Services &#40;SSIS&#41; Parameters</span></span>](integration-services-ssis-package-and-project-parameters.md)  
  
  
