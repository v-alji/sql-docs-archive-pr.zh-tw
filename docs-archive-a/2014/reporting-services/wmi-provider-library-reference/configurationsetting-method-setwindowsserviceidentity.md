---
title: SetWindowsServiceIdentity 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 15d1b7fa5fc6d69a963785cdaf976c80623c47f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706033"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="603a2-102">SetWindowsServiceIdentity 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="603a2-102">SetWindowsServiceIdentity Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="603a2-103">讓報表伺服器 Windows 服務以指定之 Windows 使用者的身分執行，並且授與此帳戶足夠的檔案系統權限，以便允許報表伺服器運作。</span><span class="sxs-lookup"><span data-stu-id="603a2-103">Makes the Report Server Windows service run as a specified Windows user, and grants this account sufficient file system permissions to allow the report server to operate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="603a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="603a2-104">Syntax</span></span>  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="603a2-105">參數</span><span class="sxs-lookup"><span data-stu-id="603a2-105">Parameters</span></span>  
 <span data-ttu-id="603a2-106">*UseBuiltInAccount*</span><span class="sxs-lookup"><span data-stu-id="603a2-106">*UseBuiltInAccount*</span></span>  
 <span data-ttu-id="603a2-107">指出指定的帳戶是否為內建 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="603a2-107">Indicates whether the specified account is a built-in Windows account.</span></span>  
  
 <span data-ttu-id="603a2-108">*帳戶*</span><span class="sxs-lookup"><span data-stu-id="603a2-108">*Account*</span></span>  
 <span data-ttu-id="603a2-109">要用來執行 Windows 服務的 Windows 帳戶，其格式為 "DOMAIN\alias"。</span><span class="sxs-lookup"><span data-stu-id="603a2-109">The Windows account to use to run the Windows service, in the format "DOMAIN\alias".</span></span>  
  
 <span data-ttu-id="603a2-110">*密碼*</span><span class="sxs-lookup"><span data-stu-id="603a2-110">*Password*</span></span>  
 <span data-ttu-id="603a2-111">此帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="603a2-111">The password for the account.</span></span>  
  
 <span data-ttu-id="603a2-112">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="603a2-112">*HRESULT*</span></span>  
 <span data-ttu-id="603a2-113">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="603a2-113">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="603a2-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="603a2-114">Return Value</span></span>  
 <span data-ttu-id="603a2-115">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="603a2-115">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="603a2-116">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="603a2-116">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="603a2-117">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="603a2-117">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="603a2-118">備註</span><span class="sxs-lookup"><span data-stu-id="603a2-118">Remarks</span></span>  
 <span data-ttu-id="603a2-119">當*UseBuiltInAccount*參數設定為 `true` ，而且報表伺服器正在 MICROSOFT [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] 或 Windows XP 上執行時，會忽略*Name*、 *Domain*和*Password*參數的值，並使用本機系統帳戶。</span><span class="sxs-lookup"><span data-stu-id="603a2-119">When the *UseBuiltInAccount* parameter is set to `true` and the report server is running on Microsoft [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] or Windows XP, the value of the *Name*, *Domain*, and *Password* parameters are ignored and the Local system account is used.</span></span>  
  
 <span data-ttu-id="603a2-120">當*UseBuiltInAccount*參數設定為 `true` ，而且報表伺服器在 Windows server 2003 上執行時，會忽略*網域*和*密碼*屬性，而且 [名稱] 欄位必須包含 "Builtin\NetworkService" 或 "Builtin\System" 或 "Builtin\LocalService"。</span><span class="sxs-lookup"><span data-stu-id="603a2-120">When the *UseBuiltInAccount* parameter is set to `true` and the report server is running on Windows Server 2003, the *Domain* and *Password* properties are ignored, and the name field must contain either "Builtin\NetworkService" or "Builtin\System" or "Builtin\LocalService".</span></span>  
  
 <span data-ttu-id="603a2-121">SetWindowsServiceIdentity 方法會在報表伺服器安裝目錄中設定檔案與資料夾的檔案權限。</span><span class="sxs-lookup"><span data-stu-id="603a2-121">The SetWindowsServiceIdentity method sets file permissions on files and folders in the report server installation directory.</span></span>  
  
 <span data-ttu-id="603a2-122">*帳戶*參數中指定的帳號需要 `LogonAsService` Windows 中的許可權。</span><span class="sxs-lookup"><span data-stu-id="603a2-122">The account specified in the *Account* parameter requires `LogonAsService` rights in Windows.</span></span> <span data-ttu-id="603a2-123">此方法會將這個權限授與指定的帳戶。</span><span class="sxs-lookup"><span data-stu-id="603a2-123">The method grants this right to the specified account.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="603a2-124">需求</span><span class="sxs-lookup"><span data-stu-id="603a2-124">Requirements</span></span>  
 <span data-ttu-id="603a2-125">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="603a2-125">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="603a2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="603a2-126">See Also</span></span>  
 [<span data-ttu-id="603a2-127">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="603a2-127">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
