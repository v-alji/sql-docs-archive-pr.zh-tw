---
title: IsSharePointIntegrated 屬性 (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: c548fed8-5e04-4faf-8b10-b37c86178056
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a1f3f38c23546ddf4dfb52c2a3af7c122af10cbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598201"
---
# <a name="issharepointintegrated-property-wmi"></a><span data-ttu-id="6eabd-102">IsSharePointIntegrated 屬性 (WMI)</span><span class="sxs-lookup"><span data-stu-id="6eabd-102">IsSharePointIntegrated Property (WMI)</span></span>
  <span data-ttu-id="6eabd-103">指定報表伺服器是否處於 SharePoint 整合模式。</span><span class="sxs-lookup"><span data-stu-id="6eabd-103">Specifies whether the report server is in SharePoint integrated mode.</span></span> <span data-ttu-id="6eabd-104">從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 開始，此屬性一律傳回 `False`，因為在 SharePoint 模式中，[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體是 SharePoint 共用服務且不受 WMI 提供者控制。</span><span class="sxs-lookup"><span data-stu-id="6eabd-104">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], this property always returns `False` because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instances are SharePoint shared services and are not controlled by WMI providers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eabd-105">語法</span><span class="sxs-lookup"><span data-stu-id="6eabd-105">Syntax</span></span>  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a><span data-ttu-id="6eabd-106">屬性值</span><span class="sxs-lookup"><span data-stu-id="6eabd-106">Property Values</span></span>  
 <span data-ttu-id="6eabd-107">`Boolean` 物件，指出報表伺服器是否在 SharePoint 整合模式下。</span><span class="sxs-lookup"><span data-stu-id="6eabd-107">A `Boolean` object that indicates whether the report server is in SharePoint integrated mode.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="6eabd-108">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="6eabd-108">Example Code</span></span>  
 [<span data-ttu-id="6eabd-109">MSReportServer_ConfigurationSetting 類別</span><span class="sxs-lookup"><span data-stu-id="6eabd-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="6eabd-110">需求</span><span class="sxs-lookup"><span data-stu-id="6eabd-110">Requirements</span></span>  
 <span data-ttu-id="6eabd-111">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eabd-111">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eabd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6eabd-112">See Also</span></span>  
 [<span data-ttu-id="6eabd-113">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="6eabd-113">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
