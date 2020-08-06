---
title: SetDatabaseLogonTimeout 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetDatabaseLogonTimeout (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDatabaseLogonTimeout method
ms.assetid: b8773596-5b98-4355-a4ab-4412e1317c67
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bf93cd9158c3489db611446ac8523701f52831f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706066"
---
# <a name="setdatabaselogontimeout-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="0dfda-102">SetDatabaseLogonTimeout 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="0dfda-102">SetDatabaseLogonTimeout Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="0dfda-103">指定報表伺服器資料庫連接的預設逾時值。</span><span class="sxs-lookup"><span data-stu-id="0dfda-103">Specifies the default timeout value for report server database connections.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dfda-104">語法</span><span class="sxs-lookup"><span data-stu-id="0dfda-104">Syntax</span></span>  
  
```vb  
Public Sub SetDatabaseLogonTimeout(LogonTimeout as Int32, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetDatabaseLogonTimeout(Int32 LogonTimeout,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dfda-105">參數</span><span class="sxs-lookup"><span data-stu-id="0dfda-105">Parameters</span></span>  
 <span data-ttu-id="0dfda-106">*LogonTimeout*</span><span class="sxs-lookup"><span data-stu-id="0dfda-106">*LogonTimeout*</span></span>  
 <span data-ttu-id="0dfda-107">報表伺服器資料庫連接的預設逾時值 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="0dfda-107">The default time-out value, in seconds, for report server database connections.</span></span>  
  
 <span data-ttu-id="0dfda-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="0dfda-108">*HRESULT*</span></span>  
 <span data-ttu-id="0dfda-109">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="0dfda-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0dfda-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="0dfda-110">Return Value</span></span>  
 <span data-ttu-id="0dfda-111">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="0dfda-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="0dfda-112">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="0dfda-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="0dfda-113">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0dfda-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dfda-114">需求</span><span class="sxs-lookup"><span data-stu-id="0dfda-114">Requirements</span></span>  
 <span data-ttu-id="0dfda-115">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dfda-115">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dfda-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0dfda-116">See Also</span></span>  
 [<span data-ttu-id="0dfda-117">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="0dfda-117">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
