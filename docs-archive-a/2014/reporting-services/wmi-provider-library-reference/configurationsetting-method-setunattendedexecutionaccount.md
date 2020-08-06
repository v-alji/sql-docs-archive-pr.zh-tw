---
title: SetUnattendedExecutionAccount 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetUnattendedExecutionAccount method
ms.assetid: 1ba6be6f-b05c-4ea0-af98-cd0780290b70
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 73cf4c633c51de1e3e6b878c66d73ee710e98df6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706049"
---
# <a name="setunattendedexecutionaccount-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="02927-102">SetUnattendedExecutionAccount 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="02927-102">SetUnattendedExecutionAccount Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="02927-103">指定用來自動執行報表的帳戶。</span><span class="sxs-lookup"><span data-stu-id="02927-103">Specifies the account used to execute reports unattended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02927-104">語法</span><span class="sxs-lookup"><span data-stu-id="02927-104">Syntax</span></span>  
  
```vb  
Public Sub SetUnattendedExecutionAccount(UserName as String, _  
    Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetUnattendedExecutionAccount (string UserName,   
    string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02927-105">參數</span><span class="sxs-lookup"><span data-stu-id="02927-105">Parameters</span></span>  
 <span data-ttu-id="02927-106">*UserName*</span><span class="sxs-lookup"><span data-stu-id="02927-106">*UserName*</span></span>  
 <span data-ttu-id="02927-107">要用於自動執行的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="02927-107">A Windows account to be used for unattended executions.</span></span>  
  
 <span data-ttu-id="02927-108">*密碼*</span><span class="sxs-lookup"><span data-stu-id="02927-108">*Password*</span></span>  
 <span data-ttu-id="02927-109">指定之帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="02927-109">The password for the specified account.</span></span>  
  
 <span data-ttu-id="02927-110">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="02927-110">*HRESULT*</span></span>  
 <span data-ttu-id="02927-111">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="02927-111">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02927-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="02927-112">Return Value</span></span>  
 <span data-ttu-id="02927-113">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="02927-113">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="02927-114">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="02927-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="02927-115">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="02927-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02927-116">備註</span><span class="sxs-lookup"><span data-stu-id="02927-116">Remarks</span></span>  
 <span data-ttu-id="02927-117">SetUnattendedExecutionAccount 方法不會驗證報表伺服器是否能夠登入成為指定的使用者。</span><span class="sxs-lookup"><span data-stu-id="02927-117">The SetUnattendedExecutionAccount method does not verify whether the report server can log in as the specified user.</span></span>  
  
 <span data-ttu-id="02927-118">在報表伺服器 Windows 服務的內容中，您無法使用 SetUnattendedExecutionAccount 方法來執行自動執行作業。</span><span class="sxs-lookup"><span data-stu-id="02927-118">It is not possible to use the SetUnattendedExecutionAccount method to run unattended executions in the context of the report server Windows service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02927-119">需求</span><span class="sxs-lookup"><span data-stu-id="02927-119">Requirements</span></span>  
 <span data-ttu-id="02927-120">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02927-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02927-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02927-121">See Also</span></span>  
 [<span data-ttu-id="02927-122">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="02927-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
