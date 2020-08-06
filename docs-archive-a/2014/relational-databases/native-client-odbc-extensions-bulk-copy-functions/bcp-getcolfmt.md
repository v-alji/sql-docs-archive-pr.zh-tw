---
title: bcp_getcolfmt |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_getcolfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_getcolfmt function
ms.assetid: f8bdada5-7b2d-4475-8c98-f93e9d77b130
author: rothja
ms.author: jroth
ms.openlocfilehash: aabc811a5aa0babe5119c4ef0ed0e649586d73cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594062"
---
# <a name="bcp_getcolfmt"></a><span data-ttu-id="1d79a-102">bcp_getcolfmt</span><span class="sxs-lookup"><span data-stu-id="1d79a-102">bcp_getcolfmt</span></span>
  <span data-ttu-id="1d79a-103">用來尋找資料行格式屬性值。</span><span class="sxs-lookup"><span data-stu-id="1d79a-103">Used to find the column format property value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d79a-104">語法</span><span class="sxs-lookup"><span data-stu-id="1d79a-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_getcolfmt (  
HDBC   
hdbc  
,  
INT   
field  
,  
INT   
property  
,  
void*   
pValue  
,  
INT   
cbvalue,  
INT*   
pcbLen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="1d79a-105">引數</span><span class="sxs-lookup"><span data-stu-id="1d79a-105">Arguments</span></span>  
 <span data-ttu-id="1d79a-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="1d79a-106">*hdbc*</span></span>  
 <span data-ttu-id="1d79a-107">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="1d79a-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="1d79a-108">*欄位*</span><span class="sxs-lookup"><span data-stu-id="1d79a-108">*field*</span></span>  
 <span data-ttu-id="1d79a-109">這是擷取屬性的資料行編號。</span><span class="sxs-lookup"><span data-stu-id="1d79a-109">Is the column number for which the property is retrieved.</span></span>  
  
 <span data-ttu-id="1d79a-110">*property*</span><span class="sxs-lookup"><span data-stu-id="1d79a-110">*property*</span></span>  
 <span data-ttu-id="1d79a-111">這是其中一個屬性常數。</span><span class="sxs-lookup"><span data-stu-id="1d79a-111">Is one of the property constants.</span></span>  
  
 <span data-ttu-id="1d79a-112">*pValue*</span><span class="sxs-lookup"><span data-stu-id="1d79a-112">*pValue*</span></span>  
 <span data-ttu-id="1d79a-113">這是要擷取屬性值之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="1d79a-113">Is the pointer to the buffer from which to retrieve the property value.</span></span>  
  
 <span data-ttu-id="1d79a-114">*cbValue*</span><span class="sxs-lookup"><span data-stu-id="1d79a-114">*cbValue*</span></span>  
 <span data-ttu-id="1d79a-115">這是屬性緩衝區的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="1d79a-115">Is the length of the property buffer in bytes.</span></span>  
  
 <span data-ttu-id="1d79a-116">*pcbLen*</span><span class="sxs-lookup"><span data-stu-id="1d79a-116">*pcbLen*</span></span>  
 <span data-ttu-id="1d79a-117">屬性緩衝區中傳回之資料長度的指標。</span><span class="sxs-lookup"><span data-stu-id="1d79a-117">Pointer to length of the data that is being returned in the property buffer.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="1d79a-118">傳回</span><span class="sxs-lookup"><span data-stu-id="1d79a-118">Returns</span></span>  
 <span data-ttu-id="1d79a-119">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="1d79a-119">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d79a-120">備註</span><span class="sxs-lookup"><span data-stu-id="1d79a-120">Remarks</span></span>  
 <span data-ttu-id="1d79a-121">資料行格式屬性值列在[bcp_setcolfmt](bcp-setcolfmt.md)主題中。</span><span class="sxs-lookup"><span data-stu-id="1d79a-121">Column format property values are listed in the [bcp_setcolfmt](bcp-setcolfmt.md) topic.</span></span> <span data-ttu-id="1d79a-122">資料行格式屬性值是藉由呼叫**bcp_setcolfmt**函數來設定，而**bcp_getcolfmt**函數則是用來尋找資料行格式屬性值。</span><span class="sxs-lookup"><span data-stu-id="1d79a-122">The column format property values are set by calling the **bcp_setcolfmt** function, and the **bcp_getcolfmt** function is used to find the column format property value.</span></span>  
  
 <span data-ttu-id="1d79a-123">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]相較于舊版，連接到 (或更新版本的) 伺服器電腦時，可能會發現行為變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1d79a-123">Behavior changes may be observed when connecting to a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (or later) server computer, compared to earlier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions.</span></span> <span data-ttu-id="1d79a-124">如需詳細資訊，請參閱[中繼資料探索](../native-client/features/metadata-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="1d79a-124">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
## <a name="bcp_getcolfmt-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="1d79a-125">bcp_getcolfmt 對於增強型日期和時間功能的支援</span><span class="sxs-lookup"><span data-stu-id="1d79a-125">bcp_getcolfmt Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="1d79a-126">與日期/時間類型的屬性搭配使用的類型， `BCP_FMT_TYPE` 會如[針對增強型日期和時間類型的大量複製變更中所指定 &#40;OLE DB 和 ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="1d79a-126">The types used with the `BCP_FMT_TYPE` property for date/time types are as specified in [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>  
  
 <span data-ttu-id="1d79a-127">如需詳細資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="1d79a-127">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d79a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d79a-128">See Also</span></span>  
 [<span data-ttu-id="1d79a-129">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="1d79a-129">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
