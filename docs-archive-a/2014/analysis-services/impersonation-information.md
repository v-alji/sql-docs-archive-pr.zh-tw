---
title: 模擬資訊 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 42319d60-ccd0-46b8-af0b-f0968c390d8a
author: minewiskan
ms.author: owend
ms.openlocfilehash: f9226fdbe8656aecf0f9173976c67ee386040d6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687326"
---
# <a name="impersonation-information"></a><span data-ttu-id="743f6-102">模擬資訊</span><span class="sxs-lookup"><span data-stu-id="743f6-102">Impersonation Information</span></span>
  <span data-ttu-id="743f6-103">使用 **[模擬資訊]** 頁面可指定 Analysis Services 將用來連接資料來源的認證。</span><span class="sxs-lookup"><span data-stu-id="743f6-103">Use the **Impersonation Information** page to specify the credentials that Analysis Services will use to connect to the data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="743f6-104">選項</span><span class="sxs-lookup"><span data-stu-id="743f6-104">Options</span></span>  
 <span data-ttu-id="743f6-105">**使用特定的 Windows 使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="743f6-105">**Use a specific Windows user name and password**</span></span>  
 <span data-ttu-id="743f6-106">選取此選項即可讓 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件使用指定之 Windows 使用者帳戶的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="743f6-106">Select this option to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object use the security credentials of a specified Windows user account.</span></span> <span data-ttu-id="743f6-107">指定的認證將用於處理、ROLAP 查詢、非正規繫結、本機 Cube、採礦模型、遠端資料分割、連結物件以及從目標到來源的同步處理。</span><span class="sxs-lookup"><span data-stu-id="743f6-107">The specified credentials will be used for processing, ROLAP queries, out-of-line bindings, local cubes, mining models, remote partitions, linked objects, and synchronization from target to source.</span></span> <span data-ttu-id="743f6-108">但如果是資料採礦延伸模組 (DMX) OPENQUERY 陳述式，將忽略這個選項，而且會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="743f6-108">However, for Data Mining Extensions (DMX) OPENQUERY statements, this option is ignored and the credentials of the current user will be used.</span></span>  
  
 <span data-ttu-id="743f6-109">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="743f6-109">**User name**</span></span>  
 <span data-ttu-id="743f6-110">輸入選定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件所要使用之使用者帳戶的網域和名稱。</span><span class="sxs-lookup"><span data-stu-id="743f6-110">Type the domain and name of the user account to be used by the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="743f6-111">請使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="743f6-111">Use the following format:</span></span>  
  
 <span data-ttu-id="743f6-112">*\<Domain name>* **\\** *\<User account name>*</span><span class="sxs-lookup"><span data-stu-id="743f6-112">*\<Domain name>* **\\** *\<User account name>*</span></span>  
  
 <span data-ttu-id="743f6-113">唯有選取 **[使用特定的使用者名稱和密碼]** 之後，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="743f6-113">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="743f6-114">**密碼**</span><span class="sxs-lookup"><span data-stu-id="743f6-114">**Password**</span></span>  
 <span data-ttu-id="743f6-115">輸入選定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件所要使用之使用者帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="743f6-115">Type the password of the user account to be used by the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="743f6-116">唯有選取 **[使用特定的使用者名稱和密碼]** 之後，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="743f6-116">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="743f6-117">**使用服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="743f6-117">**Use the service account**</span></span>  
 <span data-ttu-id="743f6-118">選取此選項即可讓 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件使用與管理該物件之 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服務相關聯的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="743f6-118">Select this option to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object use the security credentials associated with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] service that manages the object.</span></span> <span data-ttu-id="743f6-119">服務帳戶認證將用於處理、ROLAP 查詢、遠端資料分割、連結物件以及從目標到來源的同步處理。</span><span class="sxs-lookup"><span data-stu-id="743f6-119">The service account credentials will be used for processing, ROLAP queries, remote partitions, linked objects, and synchronization from target to source.</span></span> <span data-ttu-id="743f6-120">但如果是資料採礦延伸模組 (DMX) OPENQUERY 陳述式、本機 Cube 和採礦模型，將會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="743f6-120">However, for Data Mining Extensions (DMX) OPENQUERY statements, local cubes, and mining models, the credentials of the current user will be used.</span></span> <span data-ttu-id="743f6-121">非正規 (out-of-line) 繫結不支援此選項。</span><span class="sxs-lookup"><span data-stu-id="743f6-121">This option is not supported for out-of-line bindings.</span></span>  
  
 <span data-ttu-id="743f6-122">**使用目前使用者的認證**</span><span class="sxs-lookup"><span data-stu-id="743f6-122">**Use the credentials of the current user**</span></span>  
 <span data-ttu-id="743f6-123">選取此選項即可讓 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件使用目前使用者的安全性認證來進行非正規 (out-of-line) 繫結、DMX OPENQUERY、本機 Cube 和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="743f6-123">Select this option to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object use the security credentials of the current user for out-of-line bindings, DMX OPENQUERY, local cubes, and mining models.</span></span> <span data-ttu-id="743f6-124">處理、ROLAP 查詢、遠端資料分割、連結物件以及從目標到來源的同步處理不支援此選項。</span><span class="sxs-lookup"><span data-stu-id="743f6-124">This option is not supported for processing, ROLAP queries, remote partitions, linked objects, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="743f6-125">**都會**</span><span class="sxs-lookup"><span data-stu-id="743f6-125">**Inherit**</span></span>  
 <span data-ttu-id="743f6-126">選取此選項可使用定義於資料庫層級的模擬行為，伺服器管理員已經使用 `DataSourceImpersonation` 資料庫屬性來設定此行為。</span><span class="sxs-lookup"><span data-stu-id="743f6-126">Select this option to use the impersonation behavior, defined at the database level, which has been set by the server administrator using the `DataSourceImpersonation` database property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="743f6-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="743f6-127">See Also</span></span>  
 <span data-ttu-id="743f6-128">[多維度模型中的資料來源](multidimensional-models/data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="743f6-128">[Data Sources in Multidimensional Models](multidimensional-models/data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="743f6-129">&#40;SSAS 多維度&#41;支援的資料來源</span><span class="sxs-lookup"><span data-stu-id="743f6-129">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
