---
title: 指令碼產生精靈支援的物件
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: rothja
ms.author: jroth
ms.openlocfilehash: 5ddc1da0d2f87fc12dfbe034a683802f54b7d34f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599463"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a><span data-ttu-id="80a46-102">指令碼產生精靈支援的物件</span><span class="sxs-lookup"><span data-stu-id="80a46-102">Objects Supported by the Generate Scripts Wizard</span></span>
  <span data-ttu-id="80a46-103">[產生和發佈指令碼精靈] 支援 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]支援的物件子集。</span><span class="sxs-lookup"><span data-stu-id="80a46-103">The Generate and Publish Scripts wizard supports a subset of the objects supported by the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
## <a name="supported-objects"></a><span data-ttu-id="80a46-104">支援的物件</span><span class="sxs-lookup"><span data-stu-id="80a46-104">Supported Objects</span></span>  
 <span data-ttu-id="80a46-105">下表將列出 [產生和發佈指令碼精靈] 所支援可發行的物件。</span><span class="sxs-lookup"><span data-stu-id="80a46-105">The following table lists the objects that can be published supported by the Generate and Publish Scripts Wizard.</span></span>  
  
||||||  
|-|-|-|-|-|  
|<span data-ttu-id="80a46-106">應用程式角色</span><span class="sxs-lookup"><span data-stu-id="80a46-106">Application role</span></span>|<span data-ttu-id="80a46-107">資料庫角色</span><span class="sxs-lookup"><span data-stu-id="80a46-107">Database role</span></span>|<span data-ttu-id="80a46-108">結構描述</span><span class="sxs-lookup"><span data-stu-id="80a46-108">Schema</span></span>|<span data-ttu-id="80a46-109">使用者定義彙總</span><span class="sxs-lookup"><span data-stu-id="80a46-109">User-defined aggregate</span></span>|<span data-ttu-id="80a46-110">視圖<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="80a46-110">View<sup>1</sup></span></span>|  
|<span data-ttu-id="80a46-111">組件</span><span class="sxs-lookup"><span data-stu-id="80a46-111">Assembly</span></span>|<span data-ttu-id="80a46-112">DEFAULT 條件約束</span><span class="sxs-lookup"><span data-stu-id="80a46-112">DEFAULT constraint</span></span>|<span data-ttu-id="80a46-113">預存程式<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="80a46-113">Stored procedure<sup>1</sup></span></span>|<span data-ttu-id="80a46-114">使用者定義資料類型</span><span class="sxs-lookup"><span data-stu-id="80a46-114">User-defined data type</span></span>|<span data-ttu-id="80a46-115">XML 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="80a46-115">XML schema collection</span></span>|  
|<span data-ttu-id="80a46-116">CHECK 條件約束</span><span class="sxs-lookup"><span data-stu-id="80a46-116">CHECK constraint</span></span>|<span data-ttu-id="80a46-117">全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="80a46-117">Full-text catalog</span></span>|<span data-ttu-id="80a46-118">同義字</span><span class="sxs-lookup"><span data-stu-id="80a46-118">Synonym</span></span>|<span data-ttu-id="80a46-119">使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="80a46-119">User-defined function</span></span>||  
|<span data-ttu-id="80a46-120">CLR (common language runtime) 預存程式<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="80a46-120">CLR (common language runtime) stored procedure<sup>1</sup></span></span>|<span data-ttu-id="80a46-121">索引</span><span class="sxs-lookup"><span data-stu-id="80a46-121">Index</span></span>|<span data-ttu-id="80a46-122">Table</span><span class="sxs-lookup"><span data-stu-id="80a46-122">Table</span></span>|<span data-ttu-id="80a46-123">使用者定義資料表</span><span class="sxs-lookup"><span data-stu-id="80a46-123">User-defined table</span></span>||  
|<span data-ttu-id="80a46-124">CLR 使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="80a46-124">CLR user-defined function</span></span>|<span data-ttu-id="80a46-125">規則</span><span class="sxs-lookup"><span data-stu-id="80a46-125">Rule</span></span>|<span data-ttu-id="80a46-126">使用者<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="80a46-126">User<sup>2</sup></span></span>|<span data-ttu-id="80a46-127">使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="80a46-127">User-defined type</span></span>||  
  
 <span data-ttu-id="80a46-128"><sup>1</sup>已發佈但未加密。</span><span class="sxs-lookup"><span data-stu-id="80a46-128"><sup>1</sup> Published without encryption.</span></span>  
  
 <span data-ttu-id="80a46-129"><sup>2</sup>存在於資料庫中的任何非系統使用者都會發佈為角色。</span><span class="sxs-lookup"><span data-stu-id="80a46-129"><sup>2</sup> Any non-system users that exist in the database are published as Roles.</span></span>  
  
  
