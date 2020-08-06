---
title: GenerateDatabaseUpgradeScript 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseUpgradeScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseUpgradeScript method
ms.assetid: 88534e8e-2877-41cd-b5c2-b1d33a0fd203
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6a619584b9f1cc095f8f624670386d388426e4a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594917"
---
# <a name="generatedatabaseupgradescript-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="3eea9-102">GenerateDatabaseUpgradeScript 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="3eea9-102">GenerateDatabaseUpgradeScript Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="3eea9-103">產生可用來將報表伺服器資料庫升級至 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 結構描述的指令碼。</span><span class="sxs-lookup"><span data-stu-id="3eea9-103">Generates a script that can be used to upgrade the report server database to the [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] schema.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eea9-104">語法</span><span class="sxs-lookup"><span data-stu-id="3eea9-104">Syntax</span></span>  
  
```vb  
Public Sub GenerateDatabaseUpgradeScript(DatabaseName as String, _  
    ServerVersion as String, ByRef Script as String, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GenerateDatabaseUpgradeScript (string DatabaseName,   
    string ServerVersion, out string Script,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3eea9-105">參數</span><span class="sxs-lookup"><span data-stu-id="3eea9-105">Parameters</span></span>  
 <span data-ttu-id="3eea9-106">*Databasename*</span><span class="sxs-lookup"><span data-stu-id="3eea9-106">*Databasename*</span></span>  
 <span data-ttu-id="3eea9-107">包含要升級之報表伺服器資料庫名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="3eea9-107">A string containing the name of the report server database to upgrade.</span></span>  
  
 <span data-ttu-id="3eea9-108">*ServerVersion*</span><span class="sxs-lookup"><span data-stu-id="3eea9-108">*ServerVersion*</span></span>  
 <span data-ttu-id="3eea9-109">包含報表伺服器版本的字串。</span><span class="sxs-lookup"><span data-stu-id="3eea9-109">A string containing the version of the report server.</span></span>  
  
 <span data-ttu-id="3eea9-110">*指令碼*</span><span class="sxs-lookup"><span data-stu-id="3eea9-110">*Script*</span></span>  
 <span data-ttu-id="3eea9-111">[out] 包含所產生之 SQL 指令碼的字串。</span><span class="sxs-lookup"><span data-stu-id="3eea9-111">[out] A string containing the generated SQL script.</span></span>  
  
 <span data-ttu-id="3eea9-112">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="3eea9-112">*HRESULT*</span></span>  
 <span data-ttu-id="3eea9-113">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="3eea9-113">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3eea9-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="3eea9-114">Return Value</span></span>  
 <span data-ttu-id="3eea9-115">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="3eea9-115">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="3eea9-116">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3eea9-116">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="3eea9-117">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3eea9-117">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3eea9-118">備註</span><span class="sxs-lookup"><span data-stu-id="3eea9-118">Remarks</span></span>  
 <span data-ttu-id="3eea9-119">產生的指令碼支援 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]和 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3eea9-119">The generated script supports [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eea9-120">需求</span><span class="sxs-lookup"><span data-stu-id="3eea9-120">Requirements</span></span>  
 <span data-ttu-id="3eea9-121">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eea9-121">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eea9-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eea9-122">See Also</span></span>  
 [<span data-ttu-id="3eea9-123">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="3eea9-123">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
