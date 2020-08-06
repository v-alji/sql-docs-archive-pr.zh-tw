---
title: GetAdminSiteUrl 方法 (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetAdminSiteUrl method
ms.assetid: fbc5bf3c-120c-4aec-a4f2-f5391bd415f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cae1a6f7e363ddce8c47c00eb5ef25fc832e59c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594916"
---
# <a name="getadminsiteurl-method-wmi"></a><span data-ttu-id="9b74e-102">GetAdminSiteUrl 方法 (WMI)</span><span class="sxs-lookup"><span data-stu-id="9b74e-102">GetAdminSiteUrl Method (WMI)</span></span>
  <span data-ttu-id="9b74e-103">取得與報表伺服器整合之 Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]或 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 伺服陣列的管理中心網站的絕對 URL。</span><span class="sxs-lookup"><span data-stu-id="9b74e-103">Gets the absolute URL for the Central Administration Web site for the Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] farm that the report server is integrated with.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b74e-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b74e-104">Syntax</span></span>  
  
```vb  
Public Sub GetAdminSiteUrl(ByRef AdminSiteUrl as String, _  
ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GetAdminSiteUrl(out string AdminSiteUrl, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b74e-105">參數</span><span class="sxs-lookup"><span data-stu-id="9b74e-105">Parameters</span></span>  
 <span data-ttu-id="9b74e-106">*AdminSiteUrl*</span><span class="sxs-lookup"><span data-stu-id="9b74e-106">*AdminSiteUrl*</span></span>  
 <span data-ttu-id="9b74e-107">[out] 一個字串，其中包含與報表伺服器整合之 SharePoint 伺服陣列的管理中心網站的絕對 URL。</span><span class="sxs-lookup"><span data-stu-id="9b74e-107">[out] A string that contains the absolute URL for the Central Administration Web site for the SharePoint farm that the report server is integrated with.</span></span>  
  
 <span data-ttu-id="9b74e-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="9b74e-108">*HRESULT*</span></span>  
 <span data-ttu-id="9b74e-109">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="9b74e-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b74e-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="9b74e-110">Return Value</span></span>  
 <span data-ttu-id="9b74e-111">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="9b74e-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="9b74e-112">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="9b74e-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="9b74e-113">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="9b74e-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b74e-114">需求</span><span class="sxs-lookup"><span data-stu-id="9b74e-114">Requirements</span></span>  
 <span data-ttu-id="9b74e-115">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b74e-115">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b74e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b74e-116">See Also</span></span>  
 [<span data-ttu-id="9b74e-117">MSReportServer_ConfigurationSetting 方法</span><span class="sxs-lookup"><span data-stu-id="9b74e-117">MSReportServer_ConfigurationSetting Methods</span></span>](msreportserver-configurationsetting-methods.md)  
  
  
