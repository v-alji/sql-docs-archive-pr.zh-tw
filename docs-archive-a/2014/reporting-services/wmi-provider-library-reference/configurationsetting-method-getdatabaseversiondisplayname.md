---
title: GetDatabaseVersionDisplayName 方法 (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetDatabaseVersionDisplayName method
ms.assetid: e1286424-7043-4f12-a7ad-1cf69e81baa4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b39ce39a4f26964c148631c903869b0234e2b9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594915"
---
# <a name="getdatabaseversiondisplayname-method-wmi"></a><span data-ttu-id="5dec7-102">GetDatabaseVersionDisplayName 方法 (WMI)</span><span class="sxs-lookup"><span data-stu-id="5dec7-102">GetDatabaseVersionDisplayName Method (WMI)</span></span>
  <span data-ttu-id="5dec7-103">取得給定報表伺服器資料庫版本字串的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="5dec7-103">Gets the display name for a given report server database version string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dec7-104">語法</span><span class="sxs-lookup"><span data-stu-id="5dec7-104">Syntax</span></span>  
  
```vb  
Public Sub GetDatabaseVersionDisplayName(Version As String, DisplayName As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetDatabaseVersionDisplayName(string Version, string DisplayName, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dec7-105">參數</span><span class="sxs-lookup"><span data-stu-id="5dec7-105">Parameters</span></span>  
 <span data-ttu-id="5dec7-106">*版本*</span><span class="sxs-lookup"><span data-stu-id="5dec7-106">*Version*</span></span>  
 <span data-ttu-id="5dec7-107">包含報表伺服器資料庫之版本字串的字串。</span><span class="sxs-lookup"><span data-stu-id="5dec7-107">A string that contains the version string for a report server database.</span></span>  
  
 <span data-ttu-id="5dec7-108">*DisplayName*</span><span class="sxs-lookup"><span data-stu-id="5dec7-108">*DisplayName*</span></span>  
 <span data-ttu-id="5dec7-109">[out] 包含對應至所提供版本之顯示名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="5dec7-109">[out] A string that contains the display name that corresponds to the version supplied.</span></span>  
  
 <span data-ttu-id="5dec7-110">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="5dec7-110">*HRESULT*</span></span>  
 <span data-ttu-id="5dec7-111">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="5dec7-111">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5dec7-112">備註</span><span class="sxs-lookup"><span data-stu-id="5dec7-112">Remarks</span></span>  
 <span data-ttu-id="5dec7-113">下表將顯示資料庫版本與顯示字串的對應。</span><span class="sxs-lookup"><span data-stu-id="5dec7-113">The following table shows the mapping from database version to display string.</span></span>  
  
|<span data-ttu-id="5dec7-114">**版本**</span><span class="sxs-lookup"><span data-stu-id="5dec7-114">**Release**</span></span>|`Version`|<span data-ttu-id="5dec7-115">**顯示名稱**</span><span class="sxs-lookup"><span data-stu-id="5dec7-115">**Display Name**</span></span>|  
|-----------------|-----------------|----------------------|  
|<span data-ttu-id="5dec7-116">RS 2005 SP2</span><span class="sxs-lookup"><span data-stu-id="5dec7-116">RS 2005 SP2</span></span>|<span data-ttu-id="5dec7-117">@DBVersion = 'C.0.8.54'</span><span class="sxs-lookup"><span data-stu-id="5dec7-117">@DBVersion = 'C.0.8.54'</span></span>|<span data-ttu-id="5dec7-118">SQL Server 2005 SP2</span><span class="sxs-lookup"><span data-stu-id="5dec7-118">SQL Server 2005 SP2</span></span>|  
|<span data-ttu-id="5dec7-119">RS 2005 SP1</span><span class="sxs-lookup"><span data-stu-id="5dec7-119">RS 2005 SP1</span></span>|<span data-ttu-id="5dec7-120">@DBVersion = 'C.0.8.43'</span><span class="sxs-lookup"><span data-stu-id="5dec7-120">@DBVersion = 'C.0.8.43'</span></span>|<span data-ttu-id="5dec7-121">SQL Server 2005 SP1</span><span class="sxs-lookup"><span data-stu-id="5dec7-121">SQL Server 2005 SP1</span></span>|  
|<span data-ttu-id="5dec7-122">RS 2005 RTM</span><span class="sxs-lookup"><span data-stu-id="5dec7-122">RS 2005 RTM</span></span>|<span data-ttu-id="5dec7-123">@DBVersion = 'C.0.8.40'</span><span class="sxs-lookup"><span data-stu-id="5dec7-123">@DBVersion = 'C.0.8.40'</span></span>|<span data-ttu-id="5dec7-124">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="5dec7-124">SQL Server 2005</span></span>|  
|<span data-ttu-id="5dec7-125">RS 2000 SP2</span><span class="sxs-lookup"><span data-stu-id="5dec7-125">RS 2000 SP2</span></span>|<span data-ttu-id="5dec7-126">@DBVersion = 'C.0.6.54'</span><span class="sxs-lookup"><span data-stu-id="5dec7-126">@DBVersion = 'C.0.6.54'</span></span>|<span data-ttu-id="5dec7-127">SQL Server 2000 SP2</span><span class="sxs-lookup"><span data-stu-id="5dec7-127">SQL Server 2000 SP2</span></span>|  
|<span data-ttu-id="5dec7-128">RS 2000 SP1</span><span class="sxs-lookup"><span data-stu-id="5dec7-128">RS 2000 SP1</span></span>|<span data-ttu-id="5dec7-129">@DBVersion = 'C.0.6.51'</span><span class="sxs-lookup"><span data-stu-id="5dec7-129">@DBVersion = 'C.0.6.51'</span></span>|<span data-ttu-id="5dec7-130">SQL Server 2000 SP1</span><span class="sxs-lookup"><span data-stu-id="5dec7-130">SQL Server 2000 SP1</span></span>|  
|<span data-ttu-id="5dec7-131">RS 2000 RTM</span><span class="sxs-lookup"><span data-stu-id="5dec7-131">RS 2000 RTM</span></span>|<span data-ttu-id="5dec7-132">@DBVersion = 'C.0.6.43'</span><span class="sxs-lookup"><span data-stu-id="5dec7-132">@DBVersion = 'C.0.6.43'</span></span>|<span data-ttu-id="5dec7-133">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="5dec7-133">SQL Server 2000</span></span>|  
|<span data-ttu-id="5dec7-134">Hotfix</span><span class="sxs-lookup"><span data-stu-id="5dec7-134">Hotfix</span></span>||<span data-ttu-id="5dec7-135">最接近的適用版本</span><span class="sxs-lookup"><span data-stu-id="5dec7-135">Closest applicable version</span></span>|  
  
 <span data-ttu-id="5dec7-136">若為 *2000 之前的* Version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，就會傳回 ACT_E_BAD_VERSION 的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="5dec7-136">For a *Version* prior to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 an HRESULT of ACT_E_BAD_VERSION is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5dec7-137">傳回值</span><span class="sxs-lookup"><span data-stu-id="5dec7-137">Return Value</span></span>  
 <span data-ttu-id="5dec7-138">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="5dec7-138">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="5dec7-139">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="5dec7-139">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="5dec7-140">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="5dec7-140">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dec7-141">需求</span><span class="sxs-lookup"><span data-stu-id="5dec7-141">Requirements</span></span>  
 <span data-ttu-id="5dec7-142">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dec7-142">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dec7-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dec7-143">See Also</span></span>  
 [<span data-ttu-id="5dec7-144">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="5dec7-144">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
