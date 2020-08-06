---
title: DatabaseLogonTimeout 屬性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonTimeout property
ms.assetid: 4a65162c-33de-485e-8fd3-2bd6bff8bf8d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4920f5ef2282478f4d12a19b0806cf6ff9632cac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706021"
---
# <a name="databaselogontimeout-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="db003-102">DatabaseLogonTimeout 屬性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="db003-102">DatabaseLogonTimeout Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="db003-103">指定嘗試登入報表伺服器資料庫失敗之前等候的秒數。</span><span class="sxs-lookup"><span data-stu-id="db003-103">Specifies the number of seconds to wait before an attempt to log on to the report server database fails.</span></span> <span data-ttu-id="db003-104">值為 **0** 表示無限的等候時間。</span><span class="sxs-lookup"><span data-stu-id="db003-104">A value of **0** indicates an infinite wait time.</span></span> <span data-ttu-id="db003-105">唯讀。</span><span class="sxs-lookup"><span data-stu-id="db003-105">Read only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db003-106">語法</span><span class="sxs-lookup"><span data-stu-id="db003-106">Syntax</span></span>  
  
```vb  
Public Dim DatabaseLogonTimeout As Int32  
```  
  
```csharp  
public Int32 DatabaseLogonTimeout;  
```  
  
## <a name="property-values"></a><span data-ttu-id="db003-107">屬性值</span><span class="sxs-lookup"><span data-stu-id="db003-107">Property Values</span></span>  
 <span data-ttu-id="db003-108">32 位元帶正負號的整數物件，代表秒數。</span><span class="sxs-lookup"><span data-stu-id="db003-108">A 32-bit signed integer object that represents the number of seconds.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="db003-109">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="db003-109">Example Code</span></span>  
 [<span data-ttu-id="db003-110">MSReportServer_ConfigurationSetting 類別</span><span class="sxs-lookup"><span data-stu-id="db003-110">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="db003-111">需求</span><span class="sxs-lookup"><span data-stu-id="db003-111">Requirements</span></span>  
 <span data-ttu-id="db003-112">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db003-112">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db003-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db003-113">See Also</span></span>  
 [<span data-ttu-id="db003-114">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="db003-114">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
