---
title: 設定表格式模型資料庫的記憶體內部或 DirectQuery 存取 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a5d439a9-5be1-4145-90e8-90777d80e98b
author: minewiskan
ms.author: owend
ms.openlocfilehash: a607bc6c11f35736487932bdf10d239afc8b5355
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687242"
---
# <a name="configure-in-memory-or-directquery-access-for-a-tabular-model-database"></a><span data-ttu-id="93951-102">為表格式模型資料庫設定 In-Memory 或 DirectQuery 存取</span><span class="sxs-lookup"><span data-stu-id="93951-102">Configure In-Memory or DirectQuery Access for a Tabular Model Database</span></span>
  <span data-ttu-id="93951-103">本主題描述如何變更已經部署之表格式模型的連接屬性，以便在 DirectQuery 模式中啟用此模型。</span><span class="sxs-lookup"><span data-stu-id="93951-103">This topic describes how to change the connection properties of a tabular model that has already been deployed, to enable use of the model in Direct Query mode.</span></span>  
  
 <span data-ttu-id="93951-104">如需有關這些屬性的詳細資訊，以及最常見案例的設定，請參閱[DirectQuery 部署案例 &#40;SSAS 表格式&#41;](../directquery-deployment-scenarios-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="93951-104">For more information about these properties, and configuration for the most common scenarios, see [DirectQuery Deployment Scenarios &#40;SSAS Tabular&#41;](../directquery-deployment-scenarios-ssas-tabular.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93951-105">需求</span><span class="sxs-lookup"><span data-stu-id="93951-105">Requirements</span></span>  
 <span data-ttu-id="93951-106">在表格式模型中啟用 DirectQuery 模式為多步驟的程序。</span><span class="sxs-lookup"><span data-stu-id="93951-106">Enabling the use of Direct Query mode on a tabular model is a multistep process.</span></span> <span data-ttu-id="93951-107">您必須：</span><span class="sxs-lookup"><span data-stu-id="93951-107">You must:</span></span>  
  
1.  <span data-ttu-id="93951-108">確定此模型並沒有任何功能可能在 DirectQuery 模式中造成驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="93951-108">Ensure that the model does not have features which might cause validation errors in Direct Query mode.</span></span>  
  
2.  <span data-ttu-id="93951-109">在此模型上變更儲存模式來支援 DirectQuery。</span><span class="sxs-lookup"><span data-stu-id="93951-109">Change the storage mode on the model to support Direct Query.</span></span>  
  
3.  <span data-ttu-id="93951-110">在支援混合或純 DirectQuery 模式之查詢的模式中部署此模型。</span><span class="sxs-lookup"><span data-stu-id="93951-110">Deploy the model in a mode that supports queries in either a hybrid or pure Direct Query mode.</span></span>  
  
4.  <span data-ttu-id="93951-111">在部署的資料庫上編輯連接字串，以支援 DirectQuery 模式。</span><span class="sxs-lookup"><span data-stu-id="93951-111">Edit the connection string on the deployed database to support Direct Query mode.</span></span>  
  
 <span data-ttu-id="93951-112">本主題假設您已經建立和驗證您的模型，而且只需要從類似 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 的用戶端啟用 DirectQuery 存取。</span><span class="sxs-lookup"><span data-stu-id="93951-112">This topic assumes that you have created and validated your model, and only need to enable Direct Query access from a client such as [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="93951-113">程序</span><span class="sxs-lookup"><span data-stu-id="93951-113">Procedure</span></span>  
  
#### <a name="change-the-connection-string-properties-of-the-model"></a><span data-ttu-id="93951-114">變更模型的連接字串屬性</span><span class="sxs-lookup"><span data-stu-id="93951-114">Change the Connection String Properties of the Model</span></span>  
  
1.  <span data-ttu-id="93951-115">在 SQL Server Management Studio 中，開啟部署模型的目標執行個體。</span><span class="sxs-lookup"><span data-stu-id="93951-115">In SQL Server Management Studio, open the instance to which you deployed the model.</span></span>  
  
2.  <span data-ttu-id="93951-116">在物件總管中，以滑鼠右鍵按一下模型資料庫的名稱，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="93951-116">In Object Explorer, right-click the name of the model database, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="93951-117">找出屬性（ **DirectQueryMode**）。</span><span class="sxs-lookup"><span data-stu-id="93951-117">Locate the property, **DirectQueryMode**.</span></span> <span data-ttu-id="93951-118">若要啟用關聯式資料來源，這個屬性必須設定為下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="93951-118">To enable use of the relational data source, this property must be set to one of these values:</span></span>  
  
    -   <span data-ttu-id="93951-119">**DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="93951-119">**DirectQuery**</span></span>  
  
    -   <span data-ttu-id="93951-120">**InMemoryWithDirectQuery**</span><span class="sxs-lookup"><span data-stu-id="93951-120">**InMemoryWithDirectQuery**</span></span>  
  
    -   <span data-ttu-id="93951-121">**DirectQueryWithInMemory**</span><span class="sxs-lookup"><span data-stu-id="93951-121">**DirectQueryWithInMemory**</span></span>  
  
  
