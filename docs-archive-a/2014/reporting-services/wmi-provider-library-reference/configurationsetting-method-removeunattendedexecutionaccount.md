---
title: RemoveUnattendedExecutionAccount 方法 (WMI MSReportServer_ConfigurationSetting) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- RemoveUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- RemoveUnattendedExecutionAccount method
ms.assetid: 77e371c1-7c26-44f9-9119-7c8dc838db32
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: efe0523c9aa13315399c043367ef05a63da46e91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703750"
---
# <a name="removeunattendedexecutionaccount-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="ca9c7-102">RemoveUnattendedExecutionAccount 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="ca9c7-102">RemoveUnattendedExecutionAccount Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="ca9c7-103">從報表伺服器組態檔中移除自動執行帳戶項目。</span><span class="sxs-lookup"><span data-stu-id="ca9c7-103">Deletes the unattended execution account entry from the report server configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca9c7-104">語法</span><span class="sxs-lookup"><span data-stu-id="ca9c7-104">Syntax</span></span>  
  
```vb  
Public Sub RemoveUnattendedExecutionAccount(ByRef HRESULT as Int32)  
```  
  
```csharp  
public void RemoveUnattendedExecutionAccount (out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca9c7-105">參數</span><span class="sxs-lookup"><span data-stu-id="ca9c7-105">Parameters</span></span>  
 <span data-ttu-id="ca9c7-106">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="ca9c7-106">*HRESULT*</span></span>  
 <span data-ttu-id="ca9c7-107">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="ca9c7-107">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca9c7-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="ca9c7-108">Return Value</span></span>  
 <span data-ttu-id="ca9c7-109">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="ca9c7-109">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="ca9c7-110">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="ca9c7-110">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="ca9c7-111">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca9c7-111">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca9c7-112">需求</span><span class="sxs-lookup"><span data-stu-id="ca9c7-112">Requirements</span></span>  
 <span data-ttu-id="ca9c7-113">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca9c7-113">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca9c7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca9c7-114">See Also</span></span>  
 [<span data-ttu-id="ca9c7-115">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="ca9c7-115">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
