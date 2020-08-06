---
title: SecureConnectionLevel 屬性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SecureConnectionLevel
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SecureConnectionLevel property
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5d1b3bccc8a7fee3899fa21208d83a718a33f5fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705997"
---
# <a name="secureconnectionlevel-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="94375-102">SecureConnectionLevel 屬性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="94375-102">SecureConnectionLevel Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="94375-103">傳回 RSReportServer.config 檔案中指定的安全連接層級。</span><span class="sxs-lookup"><span data-stu-id="94375-103">Returns the secure connection level specified in the RSReportServer.config file.</span></span> <span data-ttu-id="94375-104">唯讀。</span><span class="sxs-lookup"><span data-stu-id="94375-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94375-105">語法</span><span class="sxs-lookup"><span data-stu-id="94375-105">Syntax</span></span>  
  
```vb  
Public Dim SecureConnectionLevel As Integer  
```  
  
```csharp  
public Integer SecureConnectionLevel;  
```  
  
## <a name="property-values"></a><span data-ttu-id="94375-106">屬性值</span><span class="sxs-lookup"><span data-stu-id="94375-106">Property Values</span></span>  
 <span data-ttu-id="94375-107">代表安全連接層級的 `Integer` 值。</span><span class="sxs-lookup"><span data-stu-id="94375-107">An `Integer` value that represents the secure connection level.</span></span> <span data-ttu-id="94375-108">傳回值指出 SSL 是已設定或未設定。</span><span class="sxs-lookup"><span data-stu-id="94375-108">The return values indicate that the SSL is either configured or not.</span></span> <span data-ttu-id="94375-109">值大於或等於 1 時，表示 SSL 為開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="94375-109">A value of greater than or equal to 1 indicates that SSL is turned on.</span></span> <span data-ttu-id="94375-110">值為 0 時，表示 SSL 為關閉狀態。</span><span class="sxs-lookup"><span data-stu-id="94375-110">A value of 0 indicates that SSL is turned off.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="94375-111">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="94375-111">Example Code</span></span>  
 [<span data-ttu-id="94375-112">MSReportServer_ConfigurationSetting 類別</span><span class="sxs-lookup"><span data-stu-id="94375-112">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="94375-113">需求</span><span class="sxs-lookup"><span data-stu-id="94375-113">Requirements</span></span>  
 <span data-ttu-id="94375-114">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94375-114">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94375-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94375-115">See Also</span></span>  
 [<span data-ttu-id="94375-116">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="94375-116">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
