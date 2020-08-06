---
title: SMTPServer 屬性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SMTPServer
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SMTPServer property
ms.assetid: 8bcceeba-e1a0-44ef-bda1-600c6925e1db
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b706834c80fa0ff126d35beffbfdc84ef92cefe6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705985"
---
# <a name="smtpserver-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="c568f-102">SMTPServer 屬性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="c568f-102">SMTPServer Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="c568f-103">從報表伺服器組態檔中取得 SMTP 伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="c568f-103">Gets the SMTP server property from the report server configuration file.</span></span> <span data-ttu-id="c568f-104">唯讀。</span><span class="sxs-lookup"><span data-stu-id="c568f-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c568f-105">語法</span><span class="sxs-lookup"><span data-stu-id="c568f-105">Syntax</span></span>  
  
```vb  
Public Dim SMTPServer As String  
```  
  
```csharp  
public string SMTPServer;  
```  
  
## <a name="property-values"></a><span data-ttu-id="c568f-106">屬性值</span><span class="sxs-lookup"><span data-stu-id="c568f-106">Property Values</span></span>  
 <span data-ttu-id="c568f-107">唯讀 `String` 物件，包含 RSReportServer.config 檔中的 `SMTPServer` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="c568f-107">A read-only `String` object containing the value of the `SMTPServer` property from the RSReportServer.config file.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="c568f-108">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="c568f-108">Example Code</span></span>  
 [<span data-ttu-id="c568f-109">MSReportServer_ConfigurationSetting 類別</span><span class="sxs-lookup"><span data-stu-id="c568f-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="c568f-110">需求</span><span class="sxs-lookup"><span data-stu-id="c568f-110">Requirements</span></span>  
 <span data-ttu-id="c568f-111">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c568f-111">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c568f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c568f-112">See Also</span></span>  
 [<span data-ttu-id="c568f-113">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="c568f-113">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
