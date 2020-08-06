---
title: 將資料採礦解決方案部署到舊版的 SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [Analysis Services]
- holdout [data mining]
- deploy [Analysis Services]
- time series [Analysis Services]
- deploying [Analysis Services - data mining]
- synchronization [Analysis Services]
- deployment [Analysis Services]
ms.assetid: 2715c245-f206-43af-8bf5-e6bd2585477a
author: minewiskan
ms.author: owend
ms.openlocfilehash: f09a37c078cf58f24db9a08e3ddcb68cb2638717
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599268"
---
# <a name="deploy-a-data-mining-solution-to-previous-versions-of-sql-server"></a><span data-ttu-id="0bfe7-102">將資料採礦方案部署到舊版的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="0bfe7-102">Deploy a Data Mining Solution to Previous Versions of SQL Server</span></span>
  <span data-ttu-id="0bfe7-103">本章節描述當您嘗試將 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] 執行個體內建立的資料採礦模型或資料採礦結構部署到使用 SQL Server 2005 Analysis Services 的資料庫，或是當您將 SQL Server 2005 中建立的模型部署到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]執行個體時，可能發生的相容性問題。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-103">This section describes known compatibility issues that may arise when you attempt to deploy a data mining model or data mining structure that was created in an instance of [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] to a database that uses SQL Server 2005 Analysis Services, or when you deploy models created in SQL Server 2005 to an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="0bfe7-104">不支援部署到 SQL Server 2000 Analysis Services 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-104">Deployment to an instance of SQL Server 2000 Analysis Services is not supported.</span></span>  
  
 [<span data-ttu-id="0bfe7-105">部署時間序列模型</span><span class="sxs-lookup"><span data-stu-id="0bfe7-105">Deploying Time Series Models</span></span>](#bkmk_TimeSeries)  
  
 [<span data-ttu-id="0bfe7-106">部署含鑑效組的模型</span><span class="sxs-lookup"><span data-stu-id="0bfe7-106">Deploying Models with Holdout</span></span>](#bkmk_Holdout)  
  
 [<span data-ttu-id="0bfe7-107">部署含篩選的模型</span><span class="sxs-lookup"><span data-stu-id="0bfe7-107">Deploying Models with Filters</span></span>](#bkmk_Filter)  
  
 [<span data-ttu-id="0bfe7-108">從資料庫備份還原</span><span class="sxs-lookup"><span data-stu-id="0bfe7-108">Restoring from Database Backups</span></span>](#bkmk_Backup)  
  
 [<span data-ttu-id="0bfe7-109">使用資料庫同步處理</span><span class="sxs-lookup"><span data-stu-id="0bfe7-109">Using Database Synchronization</span></span>](#bkmk_Synch)  
  
##  <a name="deploying-times-series-models"></a><a name="bkmk_TimeSeries"></a><span data-ttu-id="0bfe7-110">部署時間序列模型</span><span class="sxs-lookup"><span data-stu-id="0bfe7-110">Deploying Times Series Models</span></span>  
 <span data-ttu-id="0bfe7-111">Microsoft 時間序列演算法在 SQL Server 2008 中增強了功能，其方式是加入第二個補充性的演算法 ARIMA。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-111">The Microsoft Time Series algorithm was enhanced in SQL Server 2008 by the addition of a second, complementary algorithm, ARIMA.</span></span> <span data-ttu-id="0bfe7-112">如需時間序列演算法變更的詳細資訊，請參閱 [Microsoft 時間序列演算法](microsoft-time-series-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-112">For more information about the changes in the time series algorithm, see [Microsoft Time Series Algorithm](microsoft-time-series-algorithm.md).</span></span>  
  
 <span data-ttu-id="0bfe7-113">因此，使用新 ARIMA 演算法的時間序列採礦模型的行為可能與部署到 SQL Server 2005 Analysis Services 執行個體時不同。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-113">Therefore, time series mining models that use the new ARIMA algorithm may behave differently when deployed to an instance of SQL Server 2005 Analysis Services.</span></span>  
  
 <span data-ttu-id="0bfe7-114">如果您已明確設定 PREDICTION_SMOOTHING 參數來控制預測中 ARTXP 和 ARIMA 模型的混用，當您將此模型部署到 SQL Server 2005 執行個體時，Analysis Services 將會引發錯誤，指出此參數無效。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-114">If you have explicitly set the parameter PREDICTION_SMOOTHING to control the mixture of ARTXP and ARIMA models in prediction, when you deploy this model to an instance of SQL Server 2005, Analysis Services will raise an error stating that the parameter is not valid.</span></span> <span data-ttu-id="0bfe7-115">若要避免此錯誤，您必須刪除 PREDICTION_SMOOTHING 參數，並將模型轉換成純正的 ARTXP 模型。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-115">To prevent this error, you must delete the PREDICTION_SMOOTHING parameter and convert the models to a pure ARTXP model.</span></span>  
  
 <span data-ttu-id="0bfe7-116">相反地，如果您要將使用 SQL Server 2005 Analysis Services 建立的時間序列模型部署到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]執行個體，當您在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中開啟此採礦模型時，定義檔案會先轉換成新的格式，而且預設會將兩個新的參數加入到所有時間序列模型。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-116">Conversely, if you deploy a time series model that was created using SQL Server 2005 Analysis Services to an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], when you open the mining model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the definition files are first converted to the new format, and two new parameters are added by default to all time series models.</span></span> <span data-ttu-id="0bfe7-117">加入的 FORECAST_METHOD 參數具有預設值 MIXED，而且加入的 PREDICTION_SMOOTHING 參數具有預設值 0.5。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-117">The parameter FORECAST_METHOD is added with the default value of MIXED, and the parameter PREDICTION_SMOOTHING is added with the default value of 0.5.</span></span> <span data-ttu-id="0bfe7-118">但是，此模型將繼續只使用 ARTXP 進行預測，直到重新處理此模型為止。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-118">However, the model will continue to use only ARTXP for forecasting until you reprocess the model.</span></span> <span data-ttu-id="0bfe7-119">一旦您重新處理此模型之後，預測就會變更為使用 ARIMA 和 ARTXP 這兩者。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-119">As soon as you reprocess the model, prediction changes to use both ARIMA and ARTXP.</span></span>  
  
 <span data-ttu-id="0bfe7-120">因此，如果您要避免變更模型，應該只瀏覽模型，而絕對不要處理它。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-120">Therefore, if you wish to avoid changing the model, you should only browse the model and never process it.</span></span> <span data-ttu-id="0bfe7-121">另外，您也可以明確設定 FORECAST_METHOD 或 PREDICTION_SMOOTHING 參數。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-121">Alternatively, you could explicitly set the FORECAST_METHOD or PREDICTION_SMOOTHING parameters.</span></span>  
  
 <span data-ttu-id="0bfe7-122">如需設定混合模型的詳細資訊，請參閱 [Microsoft 時間序列演算法技術參考](microsoft-time-series-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-122">For detailed information about configuring mixed models, see [Microsoft Time Series Algorithm Technical Reference](microsoft-time-series-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="0bfe7-123">如果用於模型資料來源的提供者是 SQL Client Data Provider 10，您也必須修改資料來源定義來指定舊版的 SQL Server Native Client。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-123">If the provider that is used for the model's data source is SQL Client Data Provider 10, you must also modify the data source definition to specify the previous version of the SQL Server Native Client.</span></span> <span data-ttu-id="0bfe7-124">否則， [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 會產生錯誤，指出此提供者尚未註冊。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-124">Otherwise, [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] generates an error stating that the provider is not registered.</span></span>  
  
##  <a name="deploying-models-with-holdout"></a><a name="bkmk_Holdout"></a><span data-ttu-id="0bfe7-125">使用維持的部署模型</span><span class="sxs-lookup"><span data-stu-id="0bfe7-125">Deploying Models with Holdout</span></span>  
 <span data-ttu-id="0bfe7-126">如果您使用 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] 來建立包含用於測試資料採礦模型之鑑效組資料分割的採礦結構，此採礦結構可以部署到 SQL Server 2005 執行個體，但是資料分割資訊將會遺失。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-126">If you use [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] to create a mining structure that contains a holdout partition used for testing data mining models, the mining structure can be deployed to an instance of SQL Server 2005, but the partition information will be lost.</span></span>  
  
 <span data-ttu-id="0bfe7-127">當您在 SQL Server 2005 Analysis Services 中開啟此採礦結構時， [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 會引發錯誤，然後重新產生此結構來移除鑑效組資料分割。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-127">When you open the mining structure in SQL Server 2005 Analysis Services, [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] raises an error, and then regenerates the structure to remove the holdout partition.</span></span>  
  
 <span data-ttu-id="0bfe7-128">重建結構之後，屬性視窗中無法再使用維持的分割區大小。不過，值 \<ddl100_100:HoldoutMaxPercent> 30 \</ddl100_100:HoldoutMaxPercent>) 可能仍存在於 ASSL 腳本檔案中。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-128">After the structure has been rebuilt, the size of the holdout partition is no longer available in the Properties window; however, the value \<ddl100_100:HoldoutMaxPercent>30\</ddl100_100:HoldoutMaxPercent>) may still be present in the ASSL script file.</span></span>  
  
##  <a name="deploying-models-with-filters"></a><a name="bkmk_Filter"></a><span data-ttu-id="0bfe7-129">使用篩選部署模型</span><span class="sxs-lookup"><span data-stu-id="0bfe7-129">Deploying Models with Filters</span></span>  
 <span data-ttu-id="0bfe7-130">如果您使用 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] 將篩選套用到採礦模型，此模型可以部署到 SQL Server 2005 執行個體，但是篩選將不會套用。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-130">If you use [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] to apply a filter to a mining model, the model can be deployed to an instance of SQL Server 2005, but the filter will not be applied.</span></span>  
  
 <span data-ttu-id="0bfe7-131">當您開啟此採礦模型時， [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 會引發錯誤，然後重新產生此模型來移除篩選。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-131">When you open the mining model, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] raises an error, and then regenerates the model to remove the filter.</span></span>  
  
##  <a name="restoring-from-database-backups"></a><a name="bkmk_Backup"></a><span data-ttu-id="0bfe7-132">從資料庫備份還原</span><span class="sxs-lookup"><span data-stu-id="0bfe7-132">Restoring from Database Backups</span></span>  
 <span data-ttu-id="0bfe7-133">您無法將 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中建立的資料庫備份還原到 SQL Server 2005 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-133">You cannot restore a database backup that was created in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to an instance of SQL Server 2005.</span></span> <span data-ttu-id="0bfe7-134">如果您這樣做，SQL Server Management Studio 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-134">If you do so, SQL Server Management Studio generates an error.</span></span>  
  
 <span data-ttu-id="0bfe7-135">如果您建立 SQL Server 2005 Analysis Services 資料庫的備份，並將此備份還原到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]執行個體，則所有時間序列模型都會修改，如上節所述。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-135">If you create a backup of a SQL Server 2005 Analysis Services database and restore this backup on an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], all time series models are modified as described in the previous section.</span></span>  
  
##  <a name="using-database-synchronization"></a><a name="bkmk_Synch"></a><span data-ttu-id="0bfe7-136">使用資料庫同步處理</span><span class="sxs-lookup"><span data-stu-id="0bfe7-136">Using Database Synchronization</span></span>  
 <span data-ttu-id="0bfe7-137">不支援從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 到 SQL Server 2005 的資料庫同步處理。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-137">Database synchronization is not supported from [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to SQL Server 2005.</span></span>  
  
 <span data-ttu-id="0bfe7-138">如果您嘗試同步處理 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 資料庫，伺服器會傳回錯誤，而且資料庫同步處理會失敗。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-138">If you attempt to synchronize a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] database, the server returns an error and database synchronization fails.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bfe7-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bfe7-139">See Also</span></span>  
 [<span data-ttu-id="0bfe7-140">Analysis Services 回溯相容性</span><span class="sxs-lookup"><span data-stu-id="0bfe7-140">Analysis Services Backward Compatibility</span></span>](../analysis-services-backward-compatibility.md)  
  
  
