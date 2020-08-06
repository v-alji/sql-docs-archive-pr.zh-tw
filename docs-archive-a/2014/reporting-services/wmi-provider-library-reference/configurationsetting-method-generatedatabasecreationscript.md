---
title: GenerateDatabaseCreationScript 方法 (WMI MSReportServer_ConfigurationSetting) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e798aa25bec1cc478a6ec2cbdd0c21f44fa8215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594920"
---
# <a name="generatedatabasecreationscript-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="3c818-102">GenerateDatabaseCreationScript 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="3c818-102">GenerateDatabaseCreationScript Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="3c818-103">產生可用來建立報表伺服器資料庫的 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="3c818-103">Generates a SQL Script that can be used to create a report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c818-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c818-104">Syntax</span></span>  
  
```vb  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c818-105">參數</span><span class="sxs-lookup"><span data-stu-id="3c818-105">Parameters</span></span>  
 <span data-ttu-id="3c818-106">*Databasename*</span><span class="sxs-lookup"><span data-stu-id="3c818-106">*Databasename*</span></span>  
 <span data-ttu-id="3c818-107">包含要建立之報表伺服器資料庫名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="3c818-107">A string containing the name of the report server database to create.</span></span>  
  
 <span data-ttu-id="3c818-108">*Lcid*</span><span class="sxs-lookup"><span data-stu-id="3c818-108">*Lcid*</span></span>  
 <span data-ttu-id="3c818-109">用於當地語系化角色名稱的值。</span><span class="sxs-lookup"><span data-stu-id="3c818-109">Value used for localization of role names.</span></span>  
  
 <span data-ttu-id="3c818-110">*IsSharePointMode*</span><span class="sxs-lookup"><span data-stu-id="3c818-110">*IsSharePointMode*</span></span>  
 <span data-ttu-id="3c818-111">指出要以原生模式或 SharePoint 模式建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="3c818-111">Indicates whether to create database in native mode or SharePoint mode.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3c818-112">從開始 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ， *IsSharePointMode* = `True` 不支援 IsSharePointMode，因為在 sharepoint 模式中， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 是 sharepoint 共用服務，且不受 WMI 提供者控制。</span><span class="sxs-lookup"><span data-stu-id="3c818-112">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], *IsSharePointMode*=`True` is not supported because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is a SharePoint shared service and is not controlled by the WMI provider.</span></span> <span data-ttu-id="3c818-113">您應該一律將此參數設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="3c818-113">You should always set this parameter to `False`.</span></span>  
  
 <span data-ttu-id="3c818-114">*指令碼*</span><span class="sxs-lookup"><span data-stu-id="3c818-114">*Script*</span></span>  
 <span data-ttu-id="3c818-115">[out] 包含所產生之 SQL 指令碼的字串。</span><span class="sxs-lookup"><span data-stu-id="3c818-115">[out] A string containing the generated SQL script.</span></span>  
  
 <span data-ttu-id="3c818-116">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="3c818-116">*HRESULT*</span></span>  
 <span data-ttu-id="3c818-117">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="3c818-117">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c818-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="3c818-118">Return Value</span></span>  
 <span data-ttu-id="3c818-119">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="3c818-119">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="3c818-120">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3c818-120">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="3c818-121">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3c818-121">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c818-122">備註</span><span class="sxs-lookup"><span data-stu-id="3c818-122">Remarks</span></span>  
 <span data-ttu-id="3c818-123">這個方法會產生 SQL 指令碼，以便針對目前所連接之報表伺服器的版本建立報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="3c818-123">This method generates an SQL script that creates report server databases for the version of the report server currently connected to.</span></span>  
  
 <span data-ttu-id="3c818-124">在 *DatabaseName* 參數中提供的值必須符合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫命名慣例。</span><span class="sxs-lookup"><span data-stu-id="3c818-124">The value supplied in the *DatabaseName* parameter must conform to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database naming conventions.</span></span>  
  
 <span data-ttu-id="3c818-125">產生指令碼時，此方法不會檢查資料庫是否存在。</span><span class="sxs-lookup"><span data-stu-id="3c818-125">The method does not check the existence of the database when generating the script.</span></span>  
  
 <span data-ttu-id="3c818-126">產生指令碼時，此方法不會檢查報表伺服器資料庫是否存在。</span><span class="sxs-lookup"><span data-stu-id="3c818-126">This method does not check for the existence of the report server database when generating the script.</span></span>  
  
 <span data-ttu-id="3c818-127">產生的指令碼支援 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 和 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3c818-127">The generated script supports [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c818-128">需求</span><span class="sxs-lookup"><span data-stu-id="3c818-128">Requirements</span></span>  
 <span data-ttu-id="3c818-129">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c818-129">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c818-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c818-130">See Also</span></span>  
 [<span data-ttu-id="3c818-131">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="3c818-131">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
