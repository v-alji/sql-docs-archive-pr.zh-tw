---
title: 模型方法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
ms.assetid: d3e658c9-bb22-480b-a3d5-bcde8f537ab2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0b93b43383a4b0e5bf19d7c6be9c415d7c91e57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704865"
---
# <a name="model-methods"></a><span data-ttu-id="0f30c-102">模型方法</span><span class="sxs-lookup"><span data-stu-id="0f30c-102">Model Methods</span></span>
  <span data-ttu-id="0f30c-103">您可以使用這些方法來管理模型。</span><span class="sxs-lookup"><span data-stu-id="0f30c-103">You can use these methods to manage models.</span></span>  
  
|<span data-ttu-id="0f30c-104">方法</span><span class="sxs-lookup"><span data-stu-id="0f30c-104">Method</span></span>|<span data-ttu-id="0f30c-105">動作</span><span class="sxs-lookup"><span data-stu-id="0f30c-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GenerateModel%2A>|<span data-ttu-id="0f30c-106">以共用資料來源為基礎產生預設模型。</span><span class="sxs-lookup"><span data-stu-id="0f30c-106">Generates a default model on top of a shared data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPermissions%2A>|<span data-ttu-id="0f30c-107">擷取與模型項目關聯的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="0f30c-107">Retrieves the user permissions that are associated with the model item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPolicies%2A>|<span data-ttu-id="0f30c-108">擷取與模型項目關聯的原則。</span><span class="sxs-lookup"><span data-stu-id="0f30c-108">Retrieves the policies that are associated with a model item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetUserModel%2A>|<span data-ttu-id="0f30c-109">為目前使用者傳回模型的語意部分。</span><span class="sxs-lookup"><span data-stu-id="0f30c-109">Returns the semantic piece of a model for the current user.</span></span>|  
|<xref:ReportService2010.ReportingService2010.InheritModelItemParentSecurity%2A>|<span data-ttu-id="0f30c-110">刪除與模型項目關聯的原則，並讓模型項目繼承其父項的原則。</span><span class="sxs-lookup"><span data-stu-id="0f30c-110">Deletes the policies that are associated with a model item and causes the model item to inherit the policies from its parent.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelDrillthroughReports%2A>|<span data-ttu-id="0f30c-111">列出與模型中實體關聯的鑽研報表。</span><span class="sxs-lookup"><span data-stu-id="0f30c-111">Lists drillthrough reports that are associated with an entity in a model.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelItemChildren%2A>|<span data-ttu-id="0f30c-112">傳回模型項目子元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="0f30c-112">Returns an array of model item child elements.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelItemTypes%2A>|<span data-ttu-id="0f30c-113">傳回支援的模型項目類型清單。</span><span class="sxs-lookup"><span data-stu-id="0f30c-113">Returns a list of supported model item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelPerspectives%2A>|<span data-ttu-id="0f30c-114">列出使用者可使用的模型和檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="0f30c-114">Lists models and perspectives that are available to the user.</span></span>|  
|<xref:ReportService2010.ReportingService2010.RegenerateModel%2A>|<span data-ttu-id="0f30c-115">根據資料來源結構描述的變更，更新現有的模型。</span><span class="sxs-lookup"><span data-stu-id="0f30c-115">Updates an existing model based on changes to the data source schema.</span></span>|  
|<xref:ReportService2010.ReportingService2010.RemoveAllModelItemPolicies%2A>|<span data-ttu-id="0f30c-116">刪除指定模型中與模型項目關聯的所有原則。</span><span class="sxs-lookup"><span data-stu-id="0f30c-116">Deletes all policies that are associated with model items in the specified model.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetModelDrillthroughReports%2A>|<span data-ttu-id="0f30c-117">將一組鑽研報告與模型產生關聯。</span><span class="sxs-lookup"><span data-stu-id="0f30c-117">Associates a set of drillthrough reports together with a model.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetModelItemPolicies%2A>|<span data-ttu-id="0f30c-118">在模型項目上設定安全性原則。</span><span class="sxs-lookup"><span data-stu-id="0f30c-118">Sets security policies on a model item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f30c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f30c-119">See Also</span></span>  
 <span data-ttu-id="0f30c-120">[使用 Web 服務和 .NET Framework 建置應用程式](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="0f30c-120">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="0f30c-121">[報表伺服器 Web 服務](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="0f30c-121">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="0f30c-122">[報表伺服器 Web 服務方法](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="0f30c-122">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="0f30c-123">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0f30c-123">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
