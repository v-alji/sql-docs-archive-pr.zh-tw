---
title: 稽核轉換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittrans.f1
helpviewer_keywords:
- environment data in packages [Integration Services]
- Audit transformation
ms.assetid: 8c143682-9c81-4150-83d6-1d9678151d37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e8e302f6dd1dc5666ae65af2eb9705a4922915c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687062"
---
# <a name="audit-transformation"></a><span data-ttu-id="b2eff-102">稽核轉換</span><span class="sxs-lookup"><span data-stu-id="b2eff-102">Audit Transformation</span></span>
  <span data-ttu-id="b2eff-103">稽核轉換可讓封裝中的資料流程包含有關封裝執行的環境資料。</span><span class="sxs-lookup"><span data-stu-id="b2eff-103">The Audit transformation enables the data flow in a package to include data about the environment in which the package runs.</span></span> <span data-ttu-id="b2eff-104">例如，可以將封裝、電腦與操作員的名稱加入資料流程。</span><span class="sxs-lookup"><span data-stu-id="b2eff-104">For example, the name of the package, computer, and operator can be added to the data flow.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="b2eff-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包含提供此資訊的系統變數。</span><span class="sxs-lookup"><span data-stu-id="b2eff-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] includes system variables that provide this information.</span></span>  
  
## <a name="system-variables"></a><span data-ttu-id="b2eff-106">系統變數</span><span class="sxs-lookup"><span data-stu-id="b2eff-106">System Variables</span></span>  
 <span data-ttu-id="b2eff-107">下表描述「稽核」轉換可使用的系統變數。</span><span class="sxs-lookup"><span data-stu-id="b2eff-107">The following table describes the system variables that the Audit transformation can use.</span></span>  
  
|<span data-ttu-id="b2eff-108">系統變數</span><span class="sxs-lookup"><span data-stu-id="b2eff-108">System variable</span></span>|<span data-ttu-id="b2eff-109">索引</span><span class="sxs-lookup"><span data-stu-id="b2eff-109">Index</span></span>|<span data-ttu-id="b2eff-110">描述</span><span class="sxs-lookup"><span data-stu-id="b2eff-110">Description</span></span>|  
|---------------------|-----------|-----------------|  
|`ExecutionInstanceGUID`|<span data-ttu-id="b2eff-111">0</span><span class="sxs-lookup"><span data-stu-id="b2eff-111">0</span></span>|<span data-ttu-id="b2eff-112">識別封裝執行執行個體的 GUID。</span><span class="sxs-lookup"><span data-stu-id="b2eff-112">The GUID that identifies the execution instance of the package.</span></span>|  
|`PackageID`|<span data-ttu-id="b2eff-113">1</span><span class="sxs-lookup"><span data-stu-id="b2eff-113">1</span></span>|<span data-ttu-id="b2eff-114">封裝的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="b2eff-114">The unique identifier of the package.</span></span>|  
|`PackageName`|<span data-ttu-id="b2eff-115">2</span><span class="sxs-lookup"><span data-stu-id="b2eff-115">2</span></span>|<span data-ttu-id="b2eff-116">封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="b2eff-116">The package name.</span></span>|  
|`VersionID`|<span data-ttu-id="b2eff-117">3</span><span class="sxs-lookup"><span data-stu-id="b2eff-117">3</span></span>|<span data-ttu-id="b2eff-118">封裝的版本。</span><span class="sxs-lookup"><span data-stu-id="b2eff-118">The version of the package.</span></span>|  
|`ExecutionStartTime`|<span data-ttu-id="b2eff-119">4</span><span class="sxs-lookup"><span data-stu-id="b2eff-119">4</span></span>|<span data-ttu-id="b2eff-120">封裝開始執行的時間。</span><span class="sxs-lookup"><span data-stu-id="b2eff-120">The time the package started to run.</span></span>|  
|`MachineName`|<span data-ttu-id="b2eff-121">5</span><span class="sxs-lookup"><span data-stu-id="b2eff-121">5</span></span>|<span data-ttu-id="b2eff-122">電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="b2eff-122">The computer name.</span></span>|  
|`UserName`|<span data-ttu-id="b2eff-123">6</span><span class="sxs-lookup"><span data-stu-id="b2eff-123">6</span></span>|<span data-ttu-id="b2eff-124">啟動封裝之人員的登入名稱。</span><span class="sxs-lookup"><span data-stu-id="b2eff-124">The login name of the person who started the package.</span></span>|  
|`TaskName`|<span data-ttu-id="b2eff-125">7</span><span class="sxs-lookup"><span data-stu-id="b2eff-125">7</span></span>|<span data-ttu-id="b2eff-126">與「稽核」轉換相關聯的「資料流程」工作名稱。</span><span class="sxs-lookup"><span data-stu-id="b2eff-126">The name of the Data Flow task with which the Audit transformation is associated.</span></span>|  
|<span data-ttu-id="b2eff-127">**TaskId**</span><span class="sxs-lookup"><span data-stu-id="b2eff-127">**TaskId**</span></span>|<span data-ttu-id="b2eff-128">8</span><span class="sxs-lookup"><span data-stu-id="b2eff-128">8</span></span>|<span data-ttu-id="b2eff-129">「資料流程」工作的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="b2eff-129">The unique identifier of the Data Flow task.</span></span>|  
  
## <a name="configuration-of-the-audit-transformation"></a><span data-ttu-id="b2eff-130">設定稽核轉換</span><span class="sxs-lookup"><span data-stu-id="b2eff-130">Configuration of the Audit Transformation</span></span>  
 <span data-ttu-id="b2eff-131">您可藉由提供要加入至轉換輸出的新輸出資料行名稱來設定「稽核」轉換，然後將系統變數對應到輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="b2eff-131">You configure the Audit transformation by providing the name of a new output column to add to the transformation output, and then mapping the system variable to the output column.</span></span> <span data-ttu-id="b2eff-132">您可以將單一系統變數對應到多個資料行。</span><span class="sxs-lookup"><span data-stu-id="b2eff-132">You can map a single system variable to multiple columns.</span></span>  
  
 <span data-ttu-id="b2eff-133">此轉換有一個輸入和一個輸出。</span><span class="sxs-lookup"><span data-stu-id="b2eff-133">This transformation has one input and one output.</span></span> <span data-ttu-id="b2eff-134">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="b2eff-134">It does not support an error output.</span></span>  
  
 <span data-ttu-id="b2eff-135">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="b2eff-135">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="b2eff-136">如需可在 **[稽核轉換編輯器]** 對話方塊中設定之屬性的詳細資訊，請參閱 [Audit Transformation Editor](../../audit-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="b2eff-136">For more information about the properties that you can set in the **Audit Transformation Editor** dialog box, see [Audit Transformation Editor](../../audit-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="b2eff-137">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="b2eff-137">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="b2eff-138">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="b2eff-138">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="b2eff-139">Common Properties</span><span class="sxs-lookup"><span data-stu-id="b2eff-139">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="b2eff-140">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="b2eff-140">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="b2eff-141">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="b2eff-141">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
