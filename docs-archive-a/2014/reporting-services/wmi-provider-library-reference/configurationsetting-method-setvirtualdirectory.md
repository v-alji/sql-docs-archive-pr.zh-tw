---
title: SetVirtualDirectory 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SetVirtualDirectory method
ms.assetid: 1a25cb1d-38d5-401a-970b-87b642a780e4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7f45181f3f6a791f5cb64a7519285b6d2a87dd36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706041"
---
# <a name="setvirtualdirectory-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="0d3d6-102">SetVirtualDirectory 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="0d3d6-102">SetVirtualDirectory Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="0d3d6-103">針對給定的應用程式設定虛擬目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d3d6-103">Sets the name of the virtual directory for a given application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d3d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d3d6-104">Syntax</span></span>  
  
```vb  
Public Sub SetVirtualDirectory(ByVal Application As String, _  
    ByVal VirtualDirectory As String, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetVirtualDirectory(string Application, string VirtualDirectory,   
       int Lcid,out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d3d6-105">參數</span><span class="sxs-lookup"><span data-stu-id="0d3d6-105">Parameters</span></span>  
 <span data-ttu-id="0d3d6-106">*應用程式*</span><span class="sxs-lookup"><span data-stu-id="0d3d6-106">*Application*</span></span>  
 <span data-ttu-id="0d3d6-107">要設定虛擬目錄之應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d3d6-107">The name of application for which to set the virtual directory.</span></span>  
  
 <span data-ttu-id="0d3d6-108">*VirtualDirectory*</span><span class="sxs-lookup"><span data-stu-id="0d3d6-108">*VirtualDirectory*</span></span>  
 <span data-ttu-id="0d3d6-109">虛擬目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d3d6-109">The name of the virtual directory.</span></span>  
  
 <span data-ttu-id="0d3d6-110">*lcid*</span><span class="sxs-lookup"><span data-stu-id="0d3d6-110">*lcid*</span></span>  
 <span data-ttu-id="0d3d6-111">虛擬目錄的地區設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="0d3d6-111">The locale id for the virtual directory.</span></span>  
  
 <span data-ttu-id="0d3d6-112">*錯誤*</span><span class="sxs-lookup"><span data-stu-id="0d3d6-112">*Error*</span></span>  
 <span data-ttu-id="0d3d6-113">[out] 發生之錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="0d3d6-113">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="0d3d6-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="0d3d6-114">*HRESULT*</span></span>  
 <span data-ttu-id="0d3d6-115">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="0d3d6-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d3d6-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="0d3d6-116">Return Value</span></span>  
 <span data-ttu-id="0d3d6-117">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="0d3d6-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="0d3d6-118">值為 0 表示方法呼叫成功。錯誤碼則表示呼叫不成功。</span><span class="sxs-lookup"><span data-stu-id="0d3d6-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d3d6-119">備註</span><span class="sxs-lookup"><span data-stu-id="0d3d6-119">Remarks</span></span>  
 <span data-ttu-id="0d3d6-120">應用程式只能針對所有 URL 保留項目設有一個虛擬目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="0d3d6-120">An application can have only one virtual directory name for all URL reservations.</span></span>  
  
 <span data-ttu-id="0d3d6-121">VirtualDirectory 必須符合虛擬目錄的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="0d3d6-121">VirtualDirectory must conform to naming conventions for virtual directories.</span></span> <span data-ttu-id="0d3d6-122">VirtualDirectory 不得為空字串或空白。</span><span class="sxs-lookup"><span data-stu-id="0d3d6-122">VirtualDirectory must not be empty string or blank.</span></span>  
  
 <span data-ttu-id="0d3d6-123">更新 \Configuration\URLReservations\Application\VirtualDirectory 元素的值。</span><span class="sxs-lookup"><span data-stu-id="0d3d6-123">Updates the value of the \Configuration\URLReservations\Application\VirtualDirectory element.</span></span> <span data-ttu-id="0d3d6-124">即使尚未建立任何 URL 保留項目，也會成功。</span><span class="sxs-lookup"><span data-stu-id="0d3d6-124">Succeeds even if no URL reservations have been created yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d3d6-125">需求</span><span class="sxs-lookup"><span data-stu-id="0d3d6-125">Requirements</span></span>  
 <span data-ttu-id="0d3d6-126">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d3d6-126">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d3d6-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d3d6-127">See Also</span></span>  
 [<span data-ttu-id="0d3d6-128">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="0d3d6-128">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
