---
title: DatabaseQueryTimeout 屬性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseQueryTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e92e3e0f6752ea99fe89c962ebe96e343c0195b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706014"
---
# <a name="databasequerytimeout-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="176f0-102">DatabaseQueryTimeout 屬性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="176f0-102">DatabaseQueryTimeout Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="176f0-103">指定在報表伺服器認定命令失敗，或是花太多時間執行之前必須經過的秒數。</span><span class="sxs-lookup"><span data-stu-id="176f0-103">Specifies the number of seconds that must elapse before the report server assumes the command failed or took too much time to perform.</span></span> <span data-ttu-id="176f0-104">報表伺服器會針對 SQL 目錄，而不是報表資料來源排定查詢的時間。</span><span class="sxs-lookup"><span data-stu-id="176f0-104">The report server is timing the querying against the SQL catalog, not a data source for the report.</span></span> <span data-ttu-id="176f0-105">讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="176f0-105">Read/write.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="176f0-106">語法</span><span class="sxs-lookup"><span data-stu-id="176f0-106">Syntax</span></span>  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a><span data-ttu-id="176f0-107">屬性值</span><span class="sxs-lookup"><span data-stu-id="176f0-107">Property Values</span></span>  
 <span data-ttu-id="176f0-108">代表查詢允許執行之秒數的 32 位元不帶正負號的 `integer` 物件。</span><span class="sxs-lookup"><span data-stu-id="176f0-108">A 32-bit unsigned `integer` object that represents the number of seconds that the query is allowed to run.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="176f0-109">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="176f0-109">Example Code</span></span>  
 [<span data-ttu-id="176f0-110">MSReportServer_ConfigurationSetting 類別</span><span class="sxs-lookup"><span data-stu-id="176f0-110">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="176f0-111">需求</span><span class="sxs-lookup"><span data-stu-id="176f0-111">Requirements</span></span>  
 <span data-ttu-id="176f0-112">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="176f0-112">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="176f0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="176f0-113">See Also</span></span>  
 [<span data-ttu-id="176f0-114">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="176f0-114">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
