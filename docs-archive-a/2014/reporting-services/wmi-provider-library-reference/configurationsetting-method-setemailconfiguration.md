---
title: SetEmailConfiguration 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEmailConfiguration method
ms.assetid: b40a2224-2c90-4d32-892f-1fe73a0591ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 19068d7d7fff8c31c455ef76e8d2c2caa26b743f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706062"
---
# <a name="setemailconfiguration-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="95bf7-102">SetEmailConfiguration 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="95bf7-102">SetEmailConfiguration Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="95bf7-103">設定報表伺服器用來傳送電子郵件的電子郵件傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="95bf7-103">Configures the e-mail delivery extension used by the report server to send e-mail.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95bf7-104">語法</span><span class="sxs-lookup"><span data-stu-id="95bf7-104">Syntax</span></span>  
  
```vb  
Public Sub SetEmailConfiguration(ByVal SendUsingSMTPServer As Boolean, _  
    ByVal SMTPServer As String, ByVal SenderEmailAddress As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetEmailConfiguration (Boolean SendUsingSMTPServer,   
   string SMTPServer, string SenderEmailAddress,   
   out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95bf7-105">參數</span><span class="sxs-lookup"><span data-stu-id="95bf7-105">Parameters</span></span>  
 <span data-ttu-id="95bf7-106">*SendUsingSMTPServer*</span><span class="sxs-lookup"><span data-stu-id="95bf7-106">*SendUsingSMTPServer*</span></span>  
 <span data-ttu-id="95bf7-107">指出伺服器是否要使用 SMTP 伺服器來傳送電子郵件的布林值。</span><span class="sxs-lookup"><span data-stu-id="95bf7-107">A Boolean value indicating whether the server is to use the SMTP server to send email.</span></span> <span data-ttu-id="95bf7-108">這個值只能設定為 true。</span><span class="sxs-lookup"><span data-stu-id="95bf7-108">This value can only be set to true.</span></span> <span data-ttu-id="95bf7-109">預設值為 false。</span><span class="sxs-lookup"><span data-stu-id="95bf7-109">Default value is false.</span></span>  
  
 <span data-ttu-id="95bf7-110">*SMTPServer*</span><span class="sxs-lookup"><span data-stu-id="95bf7-110">*SMTPServer*</span></span>  
 <span data-ttu-id="95bf7-111">包含 SMTP 伺服器之名稱或 IP 位址的字串。</span><span class="sxs-lookup"><span data-stu-id="95bf7-111">A string containing the name or IP address of an SMTP server.</span></span>  
  
 <span data-ttu-id="95bf7-112">*SenderEmailAddress*</span><span class="sxs-lookup"><span data-stu-id="95bf7-112">*SenderEmailAddress*</span></span>  
 <span data-ttu-id="95bf7-113">在報表伺服器所傳送的電子郵件中，用於「寄件者:」欄位的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="95bf7-113">The e-mail address used in the 'From:' field for e-mails sent from the report server.</span></span>  
  
 <span data-ttu-id="95bf7-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="95bf7-114">*HRESULT*</span></span>  
 <span data-ttu-id="95bf7-115">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="95bf7-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95bf7-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="95bf7-116">Return Value</span></span>  
 <span data-ttu-id="95bf7-117">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="95bf7-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="95bf7-118">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="95bf7-118">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="95bf7-119">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="95bf7-119">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95bf7-120">備註</span><span class="sxs-lookup"><span data-stu-id="95bf7-120">Remarks</span></span>  
 <span data-ttu-id="95bf7-121">當*SendUsingSMTPServer*參數設定為時 `true` ，報表伺服器設定檔中的**SendUsing**專案會設定為1。</span><span class="sxs-lookup"><span data-stu-id="95bf7-121">When the *SendUsingSMTPServer* parameter is set to `true`, the **SendUsing** entry in the report server configuration file is set to 1.</span></span> <span data-ttu-id="95bf7-122">當*SendUsingSMTPServer*設定為時 `false` ，未設定**SendUsing**專案。</span><span class="sxs-lookup"><span data-stu-id="95bf7-122">When *SendUsingSMTPServer* is set to `false`, the **SendUsing** entry is not configured.</span></span>  
  
 <span data-ttu-id="95bf7-123">這個方法無法讓使用者將報表伺服器組態檔中的 **SendUsing** 項目設定為 1 以外的值。</span><span class="sxs-lookup"><span data-stu-id="95bf7-123">This method does not provide a way for users to set the **SendUsing** entry in the report server configuration file to a value other than 1.</span></span> <span data-ttu-id="95bf7-124">若要針對 SMTP 郵件以外的任何項目設定報表伺服器，您必須手動編輯此組態檔。</span><span class="sxs-lookup"><span data-stu-id="95bf7-124">To configure the report server for anything other than SMTP mail, you must edit the configuration file manually.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95bf7-125">需求</span><span class="sxs-lookup"><span data-stu-id="95bf7-125">Requirements</span></span>  
 <span data-ttu-id="95bf7-126">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95bf7-126">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95bf7-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95bf7-127">See Also</span></span>  
 [<span data-ttu-id="95bf7-128">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="95bf7-128">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
