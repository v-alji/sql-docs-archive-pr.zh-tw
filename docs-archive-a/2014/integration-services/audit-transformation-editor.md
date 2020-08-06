---
title: Audit 轉換編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittransformation.f1
helpviewer_keywords:
- Audit Transformation Editor
ms.assetid: 32786a34-5870-4fde-83c7-ec74d62404b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: af6490643a0bef60cca961dc9a0564c5f6b46484
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707737"
---
# <a name="audit-transformation-editor"></a><span data-ttu-id="6dae3-102">稽核轉換編輯器</span><span class="sxs-lookup"><span data-stu-id="6dae3-102">Audit Transformation Editor</span></span>
  <span data-ttu-id="6dae3-103">稽核轉換可讓封裝中的資料流程包含有關封裝執行的環境資料。</span><span class="sxs-lookup"><span data-stu-id="6dae3-103">The Audit transformation enables the data flow in a package to include data about the environment in which the package runs.</span></span> <span data-ttu-id="6dae3-104">例如，可以將封裝、電腦與操作員的名稱加入資料流程。</span><span class="sxs-lookup"><span data-stu-id="6dae3-104">For example, the name of the package, computer, and operator can be added to the data flow.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="6dae3-105">包括提供此資訊的系統變數。</span><span class="sxs-lookup"><span data-stu-id="6dae3-105">includes system variables that provide this information.</span></span>  
  
 <span data-ttu-id="6dae3-106">若要深入了解稽核轉換，請參閱＜ [Audit Transformation](data-flow/transformations/audit-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="6dae3-106">To learn more about the Audit transformation, see [Audit Transformation](data-flow/transformations/audit-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="6dae3-107">選項</span><span class="sxs-lookup"><span data-stu-id="6dae3-107">Options</span></span>  
 <span data-ttu-id="6dae3-108">**輸出資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="6dae3-108">**Output column name**</span></span>  
 <span data-ttu-id="6dae3-109">提供包含稽核資訊之新輸出資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="6dae3-109">Provide the name for a new output column that will contain the audit information.</span></span>  
  
 <span data-ttu-id="6dae3-110">**Audit 類型**</span><span class="sxs-lookup"><span data-stu-id="6dae3-110">**Audit type**</span></span>  
 <span data-ttu-id="6dae3-111">選取可用的系統變數以提供稽核資訊。</span><span class="sxs-lookup"><span data-stu-id="6dae3-111">Select an available system variable to supply the audit information.</span></span>  
  
|<span data-ttu-id="6dae3-112">值</span><span class="sxs-lookup"><span data-stu-id="6dae3-112">Value</span></span>|<span data-ttu-id="6dae3-113">描述</span><span class="sxs-lookup"><span data-stu-id="6dae3-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6dae3-114">**執行執行個體 GUID**</span><span class="sxs-lookup"><span data-stu-id="6dae3-114">**Execution instance GUID**</span></span>|<span data-ttu-id="6dae3-115">插入唯一識別封裝之執行執行個體的 GUID。</span><span class="sxs-lookup"><span data-stu-id="6dae3-115">Insert the GUID that uniquely identifies the execution instance of the package.</span></span>|  
|<span data-ttu-id="6dae3-116">**封裝識別碼**</span><span class="sxs-lookup"><span data-stu-id="6dae3-116">**Package ID**</span></span>|<span data-ttu-id="6dae3-117">插入唯一識別封裝的 GUID。</span><span class="sxs-lookup"><span data-stu-id="6dae3-117">Insert the GUID that uniquely identifies the package.</span></span>|  
|<span data-ttu-id="6dae3-118">**封裝名稱**</span><span class="sxs-lookup"><span data-stu-id="6dae3-118">**Package name**</span></span>|<span data-ttu-id="6dae3-119">插入封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="6dae3-119">Insert the package name.</span></span>|  
|<span data-ttu-id="6dae3-120">**版本識別碼**</span><span class="sxs-lookup"><span data-stu-id="6dae3-120">**Version ID**</span></span>|<span data-ttu-id="6dae3-121">插入唯一識別封裝版本的 GUID。</span><span class="sxs-lookup"><span data-stu-id="6dae3-121">Insert the GUID that uniquely identifies the version of the package.</span></span>|  
|<span data-ttu-id="6dae3-122">**執行開始時間**</span><span class="sxs-lookup"><span data-stu-id="6dae3-122">**Execution start time**</span></span>|<span data-ttu-id="6dae3-123">插入封裝開始執行的時間。</span><span class="sxs-lookup"><span data-stu-id="6dae3-123">Insert the time at which package execution started.</span></span>|  
|<span data-ttu-id="6dae3-124">**電腦名稱**</span><span class="sxs-lookup"><span data-stu-id="6dae3-124">**Machine name**</span></span>|<span data-ttu-id="6dae3-125">插入啟動封裝的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="6dae3-125">Insert the name of the computer on which the package was launched.</span></span>|  
|<span data-ttu-id="6dae3-126">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="6dae3-126">**User name**</span></span>|<span data-ttu-id="6dae3-127">插入啟動封裝之使用者的登入名稱。</span><span class="sxs-lookup"><span data-stu-id="6dae3-127">Insert the login name of the user who launched the package.</span></span>|  
|<span data-ttu-id="6dae3-128">**工作名稱**</span><span class="sxs-lookup"><span data-stu-id="6dae3-128">**Task name**</span></span>|<span data-ttu-id="6dae3-129">插入與稽核轉換相關聯之資料流程工作的名稱。</span><span class="sxs-lookup"><span data-stu-id="6dae3-129">Insert the name of the Data Flow task with which the Audit transformation is associated.</span></span>|  
|<span data-ttu-id="6dae3-130">**工作識別碼**</span><span class="sxs-lookup"><span data-stu-id="6dae3-130">**Task ID**</span></span>|<span data-ttu-id="6dae3-131">插入唯一識別與稽核轉換相關聯之資料流程工作的 GUID。</span><span class="sxs-lookup"><span data-stu-id="6dae3-131">Insert the GUID that uniquely identifies the Data Flow task with which the Audit transformation is associated.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6dae3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dae3-132">See Also</span></span>  
 [<span data-ttu-id="6dae3-133">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="6dae3-133">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
