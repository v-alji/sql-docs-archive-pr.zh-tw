---
title: ListInstalledSharePointVersions 方法 (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListInstalledSharePointVersions method
ms.assetid: 8f0a5e9f-23f1-41e5-9a90-dfec19ef1df7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0ceee23876461cf31cbd265ea39ae015ddcbc49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594914"
---
# <a name="listinstalledsharepointversions-method-wmi"></a><span data-ttu-id="fbe47-102">ListInstalledSharePointVersions 方法 (WMI)</span><span class="sxs-lookup"><span data-stu-id="fbe47-102">ListInstalledSharePointVersions Method (WMI)</span></span>
  <span data-ttu-id="fbe47-103">傳回一組 Token，這些 Token 代表與報表伺服器安裝在同一部電腦上的 Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]或 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="fbe47-103">Returns a set of tokens that represent the versions of Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] that are installed on the same computer as the report server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbe47-104">語法</span><span class="sxs-lookup"><span data-stu-id="fbe47-104">Syntax</span></span>  
  
```vb  
Public Sub ListInstalledSharePointVersions(ByRef VersionTokens() _  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] VersionTokens,   
    out Int32 Length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbe47-105">參數</span><span class="sxs-lookup"><span data-stu-id="fbe47-105">Parameters</span></span>  
 <span data-ttu-id="fbe47-106">*VersionTokens[]*</span><span class="sxs-lookup"><span data-stu-id="fbe47-106">*VersionTokens[]*</span></span>  
 <span data-ttu-id="fbe47-107">[out] 包含一些 Token 的陣列，這些 Token 代表與已安裝之報表伺服器相容的 SharePoint 產品或技術版本。</span><span class="sxs-lookup"><span data-stu-id="fbe47-107">[out] An array that contains the tokens that represent the version of a SharePoint product or technology that is compatible with the installed report server.</span></span>  
  
 <span data-ttu-id="fbe47-108">*長度*</span><span class="sxs-lookup"><span data-stu-id="fbe47-108">*Length*</span></span>  
 <span data-ttu-id="fbe47-109">[out] 版本 Token 陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="fbe47-109">[out] The length of the version tokens array.</span></span>  
  
 <span data-ttu-id="fbe47-110">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="fbe47-110">*HRESULT*</span></span>  
 <span data-ttu-id="fbe47-111">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="fbe47-111">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbe47-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="fbe47-112">Return Value</span></span>  
 <span data-ttu-id="fbe47-113">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="fbe47-113">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="fbe47-114">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="fbe47-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="fbe47-115">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="fbe47-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbe47-116">備註</span><span class="sxs-lookup"><span data-stu-id="fbe47-116">Remarks</span></span>  
 <span data-ttu-id="fbe47-117">傳回的每個 Token 都代表與目前已安裝之報表伺服器相容的 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 或 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="fbe47-117">Each token that is returned represents a version of [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] or [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] that is compatible with the currently installed report server.</span></span> <span data-ttu-id="fbe47-118">如果特定的 SharePoint 版本與先前的 SharePoint 版本相容，就會針對每個相容的 SharePoint 版本傳回 Token。</span><span class="sxs-lookup"><span data-stu-id="fbe47-118">If a particular version of SharePoint is compatible with previous SharePoint versions, tokens for each compatible SharePoint version are returned.</span></span>  
  
 <span data-ttu-id="fbe47-119">下面是所傳回 SharePoint Token 的表格。</span><span class="sxs-lookup"><span data-stu-id="fbe47-119">The following is a table of the SharePoint tokens that are returned.</span></span>  
  
|<span data-ttu-id="fbe47-120">**版本 Token**</span><span class="sxs-lookup"><span data-stu-id="fbe47-120">**Version Tokens**</span></span>|<span data-ttu-id="fbe47-121">**說明**</span><span class="sxs-lookup"><span data-stu-id="fbe47-121">**Description**</span></span>|  
|------------------------|---------------------|  
|<span data-ttu-id="fbe47-122">WSS_V2_Compatible</span><span class="sxs-lookup"><span data-stu-id="fbe47-122">WSS_V2_Compatible</span></span>|<span data-ttu-id="fbe47-123">已安裝與 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 2.0 相容的 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、[!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、[!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、[!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 或 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 安裝。</span><span class="sxs-lookup"><span data-stu-id="fbe47-123">A [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation is installed that is compatible with [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 2.0.</span></span>|  
|<span data-ttu-id="fbe47-124">WSS_V3_Compatible</span><span class="sxs-lookup"><span data-stu-id="fbe47-124">WSS_V3_Compatible</span></span>|<span data-ttu-id="fbe47-125">安裝了與 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]3.0 相容的 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]、 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 或 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 安裝。</span><span class="sxs-lookup"><span data-stu-id="fbe47-125">A [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation is installed that is compatible with [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0.</span></span>|  
|<span data-ttu-id="fbe47-126">WSS_V4_Compatible</span><span class="sxs-lookup"><span data-stu-id="fbe47-126">WSS_V4_Compatible</span></span>|<span data-ttu-id="fbe47-127">安裝了與 Office 14 相容的 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 或 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 安裝。</span><span class="sxs-lookup"><span data-stu-id="fbe47-127">A [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation is installed that is compatible with Office 14.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fbe47-128">需求</span><span class="sxs-lookup"><span data-stu-id="fbe47-128">Requirements</span></span>  
 <span data-ttu-id="fbe47-129">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbe47-129">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbe47-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbe47-130">See Also</span></span>  
 [<span data-ttu-id="fbe47-131">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="fbe47-131">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
