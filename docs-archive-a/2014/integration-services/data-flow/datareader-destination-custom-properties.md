---
title: DataReader 目的地自訂屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 62b6f628614d533e1bebcce071ce4761e73e08f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596821"
---
# <a name="datareader-destination-custom-properties"></a><span data-ttu-id="6319e-102">DataReader 目的地自訂屬性</span><span class="sxs-lookup"><span data-stu-id="6319e-102">DataReader Destination Custom Properties</span></span>
  <span data-ttu-id="6319e-103">DataReader 目的地同時具有自訂屬性以及所有資料流程元件通用的屬性。</span><span class="sxs-lookup"><span data-stu-id="6319e-103">The DataReader destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="6319e-104">下表描述的是 DataReader 目的地的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="6319e-104">The following table describes the custom properties of the DataReader destination.</span></span> <span data-ttu-id="6319e-105">除了 `DataReader` 以外的所有屬性都是可讀寫的。</span><span class="sxs-lookup"><span data-stu-id="6319e-105">All properties except for `DataReader` are read/write.</span></span>  
  
|<span data-ttu-id="6319e-106">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="6319e-106">Property name</span></span>|<span data-ttu-id="6319e-107">資料類型</span><span class="sxs-lookup"><span data-stu-id="6319e-107">Data Type</span></span>|<span data-ttu-id="6319e-108">描述</span><span class="sxs-lookup"><span data-stu-id="6319e-108">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="6319e-109">DataReader</span><span class="sxs-lookup"><span data-stu-id="6319e-109">DataReader</span></span>|<span data-ttu-id="6319e-110">String</span><span class="sxs-lookup"><span data-stu-id="6319e-110">String</span></span>|<span data-ttu-id="6319e-111">DataReader 目的地的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="6319e-111">The class name of the DataReader destination.</span></span>|  
|<span data-ttu-id="6319e-112">FailOnTimeout</span><span class="sxs-lookup"><span data-stu-id="6319e-112">FailOnTimeout</span></span>|<span data-ttu-id="6319e-113">Boolean</span><span class="sxs-lookup"><span data-stu-id="6319e-113">Boolean</span></span>|<span data-ttu-id="6319e-114">指出發生 `ReadTimeout` 時是否會失敗。</span><span class="sxs-lookup"><span data-stu-id="6319e-114">Indicates whether to fail when a `ReadTimeout` occurs.</span></span> <span data-ttu-id="6319e-115">此屬性的預設值為 **False**。</span><span class="sxs-lookup"><span data-stu-id="6319e-115">The default value of this property is **False**.</span></span>|  
|<span data-ttu-id="6319e-116">ReadTimeout</span><span class="sxs-lookup"><span data-stu-id="6319e-116">ReadTimeout</span></span>|<span data-ttu-id="6319e-117">整數</span><span class="sxs-lookup"><span data-stu-id="6319e-117">Integer</span></span>|<span data-ttu-id="6319e-118">發生逾時之前的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="6319e-118">The number of milliseconds before a time-out occurs.</span></span> <span data-ttu-id="6319e-119">此屬性的預設值為 30000 (30 秒)。</span><span class="sxs-lookup"><span data-stu-id="6319e-119">The default value of this property is 30000 (30 seconds).</span></span>|  
  
 <span data-ttu-id="6319e-120">DataReader 目的地的輸入和輸入資料行沒有任何自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="6319e-120">The input and the input columns of the DataReader destination have no custom properties.</span></span>  
  
 <span data-ttu-id="6319e-121">如需詳細資訊，請參閱 [DataReader 目的地](datareader-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="6319e-121">For more information, see [DataReader Destination](datareader-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6319e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6319e-122">See Also</span></span>  
 [<span data-ttu-id="6319e-123">Common Properties</span><span class="sxs-lookup"><span data-stu-id="6319e-123">Common Properties</span></span>](../common-properties.md)  
  
  
