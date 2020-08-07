---
title: IsSharePointIntegrated 屬性 (WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0c92ebe586d37053b47f90ca98c31b3068a7b91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594896"
---
# <a name="issharepointintegrated-property-wmi-msreportserver_instance"></a><span data-ttu-id="6ceb0-102">IsSharePointIntegrated 屬性 (WMI MSReportServer_Instance)</span><span class="sxs-lookup"><span data-stu-id="6ceb0-102">IsSharePointIntegrated Property (WMI MSReportServer_Instance)</span></span>
  <span data-ttu-id="6ceb0-103">指定報表伺服器是否處於 SharePoint 整合模式。</span><span class="sxs-lookup"><span data-stu-id="6ceb0-103">Specifies whether the report server is in SharePoint integrated mode.</span></span> <span data-ttu-id="6ceb0-104">從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 開始，此屬性一律傳回 `False`，因為在 SharePoint 模式中，[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體是 SharePoint 共用服務且不受 WMI 提供者控制。</span><span class="sxs-lookup"><span data-stu-id="6ceb0-104">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], this property always returns `False` because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instances are SharePoint shared services and are not controlled by WMI providers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ceb0-105">語法</span><span class="sxs-lookup"><span data-stu-id="6ceb0-105">Syntax</span></span>  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a><span data-ttu-id="6ceb0-106">屬性值</span><span class="sxs-lookup"><span data-stu-id="6ceb0-106">Property Values</span></span>  
 <span data-ttu-id="6ceb0-107">指出報表伺服器是否處於 SharePoint 整合模式的 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="6ceb0-107">A `Boolean` value that indicates whether the report server is in SharePoint integrated mode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ceb0-108">需求</span><span class="sxs-lookup"><span data-stu-id="6ceb0-108">Requirements</span></span>  
 <span data-ttu-id="6ceb0-109">**命名空間：** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ceb0-109">**Namespace:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ceb0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ceb0-110">See Also</span></span>  
 <span data-ttu-id="6ceb0-111">[MSReportServer_Instance 成員](msreportserver-instance-members.md) </span><span class="sxs-lookup"><span data-stu-id="6ceb0-111">[MSReportServer_Instance Members](msreportserver-instance-members.md) </span></span>  
 [<span data-ttu-id="6ceb0-112">MSReportServer_ConfigurationSetting 類別</span><span class="sxs-lookup"><span data-stu-id="6ceb0-112">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
  
