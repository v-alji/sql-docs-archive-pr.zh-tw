---
title: 驗證預存程序 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8fa6b01d950c87768d10b0252c1ccbab2b932fe1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596067"
---
# <a name="validation-stored-procedure-master-data-services"></a><span data-ttu-id="22d3f-102">驗證預存程序 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="22d3f-102">Validation Stored Procedure (Master Data Services)</span></span>
  <span data-ttu-id="22d3f-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，驗證版本，以便將商務規則套用到模型版本中的所有成員。</span><span class="sxs-lookup"><span data-stu-id="22d3f-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], validate a version to apply business rules to all members in the model version.</span></span>  
  
 <span data-ttu-id="22d3f-104">本主題說明如何使用 **mdm.udpValidateModel** 預存程序來驗證資料。</span><span class="sxs-lookup"><span data-stu-id="22d3f-104">This topic explains how to use the **mdm.udpValidateModel** stored procedure to validate data.</span></span> <span data-ttu-id="22d3f-105">如果您是 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式的管理員，可以改用使用者介面來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="22d3f-105">If you are an administrator in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you can do validation in the UI instead.</span></span> <span data-ttu-id="22d3f-106">如需詳細資訊，請參閱 [根據商務規則驗證版本 &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="22d3f-106">For more information, see [Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22d3f-107">如果您在暫存處理序完成之前，即叫用驗證，則不會驗證尚未完成暫存的成員。</span><span class="sxs-lookup"><span data-stu-id="22d3f-107">If you invoke validation before the staging process is complete, members that have not finished staging will not be validated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22d3f-108">範例</span><span class="sxs-lookup"><span data-stu-id="22d3f-108">Example</span></span>  
  
```  
DECLARE @ModelName nVarchar(50) = 'Customer'   
DECLARE @Model_id int   
DECLARE @UserName nvarchar(50)= 'DOMAIN\user_name'   
DECLARE @User_ID int   
DECLARE @Version_ID int   
  
SET @User_ID = (SELECT ID    
                 FROM mdm.tblUser u   
                 WHERE u.UserName = @UserName)   
SET @Model_ID = (SELECT Top 1 Model_ID   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_Name = @ModelName)   
SET @Version_ID = (SELECT MAX(ID)   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_ID = @Model_ID)  
  
EXECUTE mdm.udpValidateModel @User_ID, @Model_ID, @Version_ID, 1  
  
```  
  
## <a name="parameters"></a><span data-ttu-id="22d3f-109">參數</span><span class="sxs-lookup"><span data-stu-id="22d3f-109">Parameters</span></span>  
 <span data-ttu-id="22d3f-110">此處理序的參數如下：</span><span class="sxs-lookup"><span data-stu-id="22d3f-110">The parameters of this procedure are as follows:</span></span>  
  
|<span data-ttu-id="22d3f-111">參數</span><span class="sxs-lookup"><span data-stu-id="22d3f-111">Parameter</span></span>|<span data-ttu-id="22d3f-112">描述</span><span class="sxs-lookup"><span data-stu-id="22d3f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22d3f-113">UserID</span><span class="sxs-lookup"><span data-stu-id="22d3f-113">UserID</span></span>|<span data-ttu-id="22d3f-114">使用者識別碼。</span><span class="sxs-lookup"><span data-stu-id="22d3f-114">The user ID.</span></span>|  
|<span data-ttu-id="22d3f-115">Model_ID</span><span class="sxs-lookup"><span data-stu-id="22d3f-115">Model_ID</span></span>|<span data-ttu-id="22d3f-116">模型識別碼。</span><span class="sxs-lookup"><span data-stu-id="22d3f-116">The model ID.</span></span>|  
|<span data-ttu-id="22d3f-117">Version_ID</span><span class="sxs-lookup"><span data-stu-id="22d3f-117">Version_ID</span></span>|<span data-ttu-id="22d3f-118">版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="22d3f-118">The version ID.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="22d3f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22d3f-119">See Also</span></span>  
 <span data-ttu-id="22d3f-120">[資料匯入 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="22d3f-120">[Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md) </span></span>  
 [<span data-ttu-id="22d3f-121">根據商務規則驗證版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="22d3f-121">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](validate-a-version-against-business-rules-master-data-services.md)  
  
  
