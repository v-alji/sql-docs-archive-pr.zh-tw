---
title: 使用 SQL Server Management Studio 在 SSIS 伺服器上執行封裝 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 56dc1bf8-99d4-41dc-bdc4-f64f1ccfd688
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d17009988dea54621d4fd7ef542cf452bfe95c6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687961"
---
# <a name="run-a-package-on-the-ssis-server-using-sql-server-management-studio"></a><span data-ttu-id="8e489-102">使用 SQL Server Management Studio 在 SSIS 伺服器上執行套件</span><span class="sxs-lookup"><span data-stu-id="8e489-102">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>
  <span data-ttu-id="8e489-103">將專案部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器之後，即可在伺服器上執行封裝。</span><span class="sxs-lookup"><span data-stu-id="8e489-103">After you deploy your project to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, you can run the package on the server.</span></span>  
  
 <span data-ttu-id="8e489-104">您可以使用作業報表，檢視已在伺服器上執行過或目前正在執行之封裝的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8e489-104">You can use operations reports to view information about packages that have run, or are currently running, on the server.</span></span> <span data-ttu-id="8e489-105">如需詳細資訊，請參閱 [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8e489-105">For more information, see [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).</span></span>  
  
### <a name="to-run-a-package-on-the-server-using-sql-server-management-studio"></a><span data-ttu-id="8e489-106">使用 SQL Server Management Studio 在伺服器上執行封裝</span><span class="sxs-lookup"><span data-stu-id="8e489-106">To run a package on the server using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="8e489-107">開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 並連接至包含 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 目錄的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8e489-107">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that contains the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog.</span></span>  
  
2.  <span data-ttu-id="8e489-108">依序展開 [物件總管] 中的 **[Integration Services 目錄]** 節點和 **[SSISDB]** 節點，然後導覽至已部署之專案中包含的封裝。</span><span class="sxs-lookup"><span data-stu-id="8e489-108">In Object Explorer, expand the **Integration Services Catalogs** node, expand the **SSISDB** node, and navigate to the package contained in the project you deployed.</span></span>  
  
3.  <span data-ttu-id="8e489-109">以滑鼠右鍵按一下封裝名稱，然後選取 [執行]  。</span><span class="sxs-lookup"><span data-stu-id="8e489-109">Right-click the package name and select **Execute**.</span></span>  
  
4.  <span data-ttu-id="8e489-110">使用 **[執行封裝]** 對話方塊中， **[參數]** 、 **[連線管理員]** 和 **[進階]** 標籤上的設定，設定封裝執行。</span><span class="sxs-lookup"><span data-stu-id="8e489-110">Configure the package execution by using the settings on the **Parameters**, **Connection Managers**, and **Advanced** tabs in the **Execute Package** dialog box.</span></span>  
  
5.  <span data-ttu-id="8e489-111">按一下 **[確定]** 以執行封裝。</span><span class="sxs-lookup"><span data-stu-id="8e489-111">Click **OK** to run the package.</span></span>  
  
     <span data-ttu-id="8e489-112">-或-</span><span class="sxs-lookup"><span data-stu-id="8e489-112">-or-</span></span>  
  
     <span data-ttu-id="8e489-113">使用預存程序來執行封裝。</span><span class="sxs-lookup"><span data-stu-id="8e489-113">Use stored procedures to run the package.</span></span> <span data-ttu-id="8e489-114">按一下 [指令碼]  ，產生用以建立執行之執行個體與啟動執行之執行個體的 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8e489-114">Click **Script** to generate the Transact-SQL statement that creates an instance of the execution and starts an instance of the execution.</span></span> <span data-ttu-id="8e489-115">此陳述式包含了對 catalog.create_execution、catalog.set_execution_parameter_value 和 catalog.start_execution 預存程序的呼叫。</span><span class="sxs-lookup"><span data-stu-id="8e489-115">The statement includes a call to the catalog.create_execution, catalog.set_execution_parameter_value, and catalog.start_execution stored procedures.</span></span> <span data-ttu-id="8e489-116">如需這些預存程序的詳細資訊，請參閱 [catalog.create_execution &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database)、[catalog.set_execution_parameter_value &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) 和 [catalog.start_execution &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="8e489-116">For more information about these stored procedures, see [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database), [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database), and [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).</span></span>  
  
  
