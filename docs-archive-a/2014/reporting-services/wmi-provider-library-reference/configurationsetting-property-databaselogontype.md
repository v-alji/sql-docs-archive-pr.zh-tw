---
title: DatabaseLogonType 屬性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonType
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3bb5a4149c29fb7532b7140a2616dd856e6db2b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706018"
---
# <a name="databaselogontype-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="ae3d3-102">DatabaseLogonType 屬性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="ae3d3-102">DatabaseLogonType Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="ae3d3-103">指定報表伺服器會使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 服務帳戶、Windows 使用者帳戶或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入來存取報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="ae3d3-103">Specifies whether the report server uses a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows service account, a Windows user account, or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to access the report server database.</span></span> <span data-ttu-id="ae3d3-104">唯讀。</span><span class="sxs-lookup"><span data-stu-id="ae3d3-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae3d3-105">語法</span><span class="sxs-lookup"><span data-stu-id="ae3d3-105">Syntax</span></span>  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a><span data-ttu-id="ae3d3-106">屬性值</span><span class="sxs-lookup"><span data-stu-id="ae3d3-106">Property Values</span></span>  
 <span data-ttu-id="ae3d3-107">代表登入類型的 `integer` 物件。</span><span class="sxs-lookup"><span data-stu-id="ae3d3-107">An `integer` object that represents the login type.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="ae3d3-108">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="ae3d3-108">Example Code</span></span>  
 [<span data-ttu-id="ae3d3-109">MSReportServer_ConfigurationSetting 類別</span><span class="sxs-lookup"><span data-stu-id="ae3d3-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a><span data-ttu-id="ae3d3-110">備註</span><span class="sxs-lookup"><span data-stu-id="ae3d3-110">Remarks</span></span>  
 <span data-ttu-id="ae3d3-111">值為：</span><span class="sxs-lookup"><span data-stu-id="ae3d3-111">Values are:</span></span>  
  
-   <span data-ttu-id="ae3d3-112">0 代表 Windows 登入</span><span class="sxs-lookup"><span data-stu-id="ae3d3-112">0 for Windows login</span></span>  
  
-   <span data-ttu-id="ae3d3-113">1 代表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入</span><span class="sxs-lookup"><span data-stu-id="ae3d3-113">1 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login</span></span>  
  
-   <span data-ttu-id="ae3d3-114">2 代表要當做服務登入</span><span class="sxs-lookup"><span data-stu-id="ae3d3-114">2 to log in as a service</span></span>  
  
 <span data-ttu-id="ae3d3-115">如果您指定了 0 (Windows)，就必須將 [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) 屬性中的值設定為對應的有效 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ae3d3-115">If you specify 0 (Windows), you must set the value in the [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) property to a corresponding a valid Windows user account.</span></span>  
  
 <span data-ttu-id="ae3d3-116">如果您指定 1 (SQL Server)，請確定 [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) 的值對應至有效的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="ae3d3-116">If you specify 1 (SQL Server), make sure the value of the [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) corresponds to a valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
 <span data-ttu-id="ae3d3-117">如果您指定了 2 (Windows 服務)，報表伺服器就會使用 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 帳戶和 Windows 服務帳戶來存取報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="ae3d3-117">If you specify 2 (Windows service), the report server uses an [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] account and the Windows service account to access the report server database.</span></span> <span data-ttu-id="ae3d3-118">會忽略 DatabaseLogonAccount 屬性。</span><span class="sxs-lookup"><span data-stu-id="ae3d3-118">The DatabaseLogonAccount property is ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae3d3-119">需求</span><span class="sxs-lookup"><span data-stu-id="ae3d3-119">Requirements</span></span>  
 <span data-ttu-id="ae3d3-120">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae3d3-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae3d3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae3d3-121">See Also</span></span>  
 [<span data-ttu-id="ae3d3-122">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="ae3d3-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
