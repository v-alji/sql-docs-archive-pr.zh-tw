---
title: ConnectionPoolSize 屬性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- ConnectionPoolSize
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ConnectionPoolSize property
ms.assetid: b80c8e5d-b725-4fe4-aec6-02fb18ec4434
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 24a180fde90ff406d40a0f0c89bf82dfe5138b88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706030"
---
# <a name="connectionpoolsize-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="931c8-102">ConnectionPoolSize 屬性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="931c8-102">ConnectionPoolSize Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="931c8-103">報表伺服器用來與主控報表伺服器資料庫之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體進行通訊的連接集區大小。</span><span class="sxs-lookup"><span data-stu-id="931c8-103">The connection pool size used by the report server to communicate with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the report server database.</span></span> <span data-ttu-id="931c8-104">唯讀。</span><span class="sxs-lookup"><span data-stu-id="931c8-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="931c8-105">語法</span><span class="sxs-lookup"><span data-stu-id="931c8-105">Syntax</span></span>  
  
```vb  
Public Dim ConnectionPoolSize As UInt32  
```  
  
```csharp  
public UInt32 ConnectionPoolSize;  
```  
  
## <a name="property-values"></a><span data-ttu-id="931c8-106">屬性值</span><span class="sxs-lookup"><span data-stu-id="931c8-106">Property Values</span></span>  
 <span data-ttu-id="931c8-107">唯讀的**整數**物件，會傳回的值 `768` 。</span><span class="sxs-lookup"><span data-stu-id="931c8-107">A read-only **integer** object that returns a value of `768`.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="931c8-108">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="931c8-108">Example Code</span></span>  
 [<span data-ttu-id="931c8-109">MSReportServer_ConfigurationSetting 類別</span><span class="sxs-lookup"><span data-stu-id="931c8-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="931c8-110">需求</span><span class="sxs-lookup"><span data-stu-id="931c8-110">Requirements</span></span>  
 <span data-ttu-id="931c8-111">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="931c8-111">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="931c8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="931c8-112">See Also</span></span>  
 [<span data-ttu-id="931c8-113">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="931c8-113">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
