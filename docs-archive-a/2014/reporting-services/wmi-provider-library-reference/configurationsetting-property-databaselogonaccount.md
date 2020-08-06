---
title: DatabaseLogonAccount 屬性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonAccount
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonAccount property
ms.assetid: 55f2863f-1ac1-4519-b512-e7f11c0ea5ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f9e844ff1d1447bd5abfefad8e82939575c7f47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706029"
---
# <a name="databaselogonaccount-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="d07db-102">DatabaseLogonAccount 屬性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="d07db-102">DatabaseLogonAccount Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="d07db-103">指定連接至報表伺服器資料庫時報表伺服器所使用的登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="d07db-103">Specifies the logon account that the report server uses when connecting to the report server database.</span></span> <span data-ttu-id="d07db-104">唯讀。</span><span class="sxs-lookup"><span data-stu-id="d07db-104">Read only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d07db-105">語法</span><span class="sxs-lookup"><span data-stu-id="d07db-105">Syntax</span></span>  
  
```vb  
Public Dim DatabaseLogonAccount As String  
```  
  
```csharp  
public string DatabaseLogonAccount;  
```  
  
## <a name="property-values"></a><span data-ttu-id="d07db-106">屬性值</span><span class="sxs-lookup"><span data-stu-id="d07db-106">Property Values</span></span>  
 <span data-ttu-id="d07db-107">代表登入帳戶名稱的 `String` 物件。</span><span class="sxs-lookup"><span data-stu-id="d07db-107">A `String` object that represents the logon account name.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="d07db-108">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="d07db-108">Example Code</span></span>  
 [<span data-ttu-id="d07db-109">MSReportServer_ConfigurationSetting 類別</span><span class="sxs-lookup"><span data-stu-id="d07db-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a><span data-ttu-id="d07db-110">備註</span><span class="sxs-lookup"><span data-stu-id="d07db-110">Remarks</span></span>  
 <span data-ttu-id="d07db-111">這個屬性的有效值會因 [DatabaseLogonType](configurationsetting-property-databaselogontype.md) 屬性的值而不同。</span><span class="sxs-lookup"><span data-stu-id="d07db-111">Valid values for this property will vary depending on the value of the [DatabaseLogonType](configurationsetting-property-databaselogontype.md) property.</span></span>  
  
 <span data-ttu-id="d07db-112">如果[DatabaseLogonType](configurationsetting-property-databaselogontype.md)屬性設定為，則會忽略這個屬性 `2 (Service)` 。</span><span class="sxs-lookup"><span data-stu-id="d07db-112">This property is ignored if the [DatabaseLogonType](configurationsetting-property-databaselogontype.md) property is set to `2 (Service)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d07db-113">需求</span><span class="sxs-lookup"><span data-stu-id="d07db-113">Requirements</span></span>  
 <span data-ttu-id="d07db-114">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d07db-114">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d07db-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d07db-115">See Also</span></span>  
 [<span data-ttu-id="d07db-116">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="d07db-116">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
