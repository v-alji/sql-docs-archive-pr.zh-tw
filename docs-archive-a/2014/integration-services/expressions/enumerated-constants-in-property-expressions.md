---
title: 屬性運算式中的列舉常數 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], expressions
- dynamic properties
- updating package properties
- enumerated constants [Integration Services]
- property expressions [Integration Services]
ms.assetid: a4418315-38e2-4ad3-8784-576163b25d6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9cb4ae32bf564e98d8cfc843e9497b15222fa79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701482"
---
# <a name="enumerated-constants-in-property-expressions"></a><span data-ttu-id="760ba-102">屬性運算式中的列舉常數</span><span class="sxs-lookup"><span data-stu-id="760ba-102">Enumerated Constants in Property Expressions</span></span>
  <span data-ttu-id="760ba-103">如果屬性運算式包含來自列舉值成員清單的值，運算式必須使用列舉值成員的數值來取代成員的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="760ba-103">If property expressions include values from an enumerator member list, the expression must use the numeric value of the enumerator member instead of the friendly name of the member.</span></span> <span data-ttu-id="760ba-104">例如，如果運算式設定了 `LoggingMode` 屬性，您就必須使用數值 2 來取代易記名稱 Disabled。</span><span class="sxs-lookup"><span data-stu-id="760ba-104">For example, if an expression sets the `LoggingMode` property then you must use the numeric value 2 instead of the friendly name Disabled.</span></span>  
  
 <span data-ttu-id="760ba-105">此主題列出相當於列舉值易記名稱的數值，但僅限屬性運算式中常用之成員所屬的列舉值。</span><span class="sxs-lookup"><span data-stu-id="760ba-105">This topic lists only the numeric values equivalent to friendly names of enumerators whose members are commonly used in property expressions.</span></span> <span data-ttu-id="760ba-106">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 物件模型包含其他許多列舉值，您在設計物件模型程式以程式設計方式建立封裝，或是對自訂封裝元素 (例如工作和資料流程元件) 進行編碼時，都會使用這些列舉值。</span><span class="sxs-lookup"><span data-stu-id="760ba-106">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model includes many additional enumerators that you use when you program the object model to build packages programmatically or code custom package elements such as tasks and data flow components.</span></span>  
  
 <span data-ttu-id="760ba-107">除了封裝和封裝物件適用的自訂屬性以外， [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的 [屬性] 視窗還包含一組可用於封裝、工作以及「Foreach 迴圈」、「For 迴圈」和「時序」等容器的屬性。</span><span class="sxs-lookup"><span data-stu-id="760ba-107">In addition to the custom properties for packages and package objects, the Properties window in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] includes a set of properties that are available to packages, tasks, and the Foreach Loop, For Loop, and Sequence containers.</span></span> <span data-ttu-id="760ba-108">由枚舉器-、、和的值所設定的通用屬性 `ForceExecutionResult` `LoggingMode` `IsolationLevel` `Transaction Option` 會列在 [通用屬性] 區段中。</span><span class="sxs-lookup"><span data-stu-id="760ba-108">The common properties that are set by values from enumerators-`ForceExecutionResult`, `LoggingMode`, `IsolationLevel`, and `Transaction Option`-are listed in Common Properties section.</span></span>  
  
 <span data-ttu-id="760ba-109">下列章節提供有關列舉常數的資訊：</span><span class="sxs-lookup"><span data-stu-id="760ba-109">The following sections provide information about enumerated constants:</span></span>  
  
 [<span data-ttu-id="760ba-110">套件</span><span class="sxs-lookup"><span data-stu-id="760ba-110">Package</span></span>](#Package)  
  
 [<span data-ttu-id="760ba-111">Foreach 迴圈列舉值</span><span class="sxs-lookup"><span data-stu-id="760ba-111">Foreach Loop Enumerators</span></span>](#Foreach)  
  
 [<span data-ttu-id="760ba-112">工作</span><span class="sxs-lookup"><span data-stu-id="760ba-112">Tasks</span></span>](#Tasks)  
  
 [<span data-ttu-id="760ba-113">維護計畫工作</span><span class="sxs-lookup"><span data-stu-id="760ba-113">Maintenance Plan Tasks</span></span>](#MaintenancePlanTasks)  
  
 [<span data-ttu-id="760ba-114">Common Properties</span><span class="sxs-lookup"><span data-stu-id="760ba-114">Common Properties</span></span>](#CommonProperties)  
  
##  <a name="package"></a><a name="Package"></a> <span data-ttu-id="760ba-115">封裝</span><span class="sxs-lookup"><span data-stu-id="760ba-115">Package</span></span>  
 <span data-ttu-id="760ba-116">下列表格列出使用來自列舉值的值所設定之封裝屬性的易記名稱和數值相等項。</span><span class="sxs-lookup"><span data-stu-id="760ba-116">The following tables lists the friendly names and the numeric value equivalents for properties of packages that you set by using values from an enumerator.</span></span>  
  
 <span data-ttu-id="760ba-117">`PackageType`屬性：使用來自列舉的值進行設定 `DTSPackageType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-117">`PackageType` property-Set by using values from the `DTSPackageType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-118">DTSPackageType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-118">Friendly name in DTSPackageType</span></span>|<span data-ttu-id="760ba-119">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-119">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="760ba-120">預設</span><span class="sxs-lookup"><span data-stu-id="760ba-120">Default</span></span>|<span data-ttu-id="760ba-121">0</span><span class="sxs-lookup"><span data-stu-id="760ba-121">0</span></span>|  
|<span data-ttu-id="760ba-122">DTSWizard</span><span class="sxs-lookup"><span data-stu-id="760ba-122">DTSWizard</span></span>|<span data-ttu-id="760ba-123">1</span><span class="sxs-lookup"><span data-stu-id="760ba-123">1</span></span>|  
|<span data-ttu-id="760ba-124">DTSDesigner</span><span class="sxs-lookup"><span data-stu-id="760ba-124">DTSDesigner</span></span>|<span data-ttu-id="760ba-125">2</span><span class="sxs-lookup"><span data-stu-id="760ba-125">2</span></span>|  
|<span data-ttu-id="760ba-126">SQLReplication</span><span class="sxs-lookup"><span data-stu-id="760ba-126">SQLReplication</span></span>|<span data-ttu-id="760ba-127">3</span><span class="sxs-lookup"><span data-stu-id="760ba-127">3</span></span>|  
|<span data-ttu-id="760ba-128">DTSDesigner100</span><span class="sxs-lookup"><span data-stu-id="760ba-128">DTSDesigner100</span></span>|<span data-ttu-id="760ba-129">5</span><span class="sxs-lookup"><span data-stu-id="760ba-129">5</span></span>|  
|<span data-ttu-id="760ba-130">SQLDBMaint</span><span class="sxs-lookup"><span data-stu-id="760ba-130">SQLDBMaint</span></span>|<span data-ttu-id="760ba-131">6</span><span class="sxs-lookup"><span data-stu-id="760ba-131">6</span></span>|  
  
 <span data-ttu-id="760ba-132">`CheckpointUsage`屬性：使用來自列舉的值進行設定 `DTSCheckpointUsage` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-132">`CheckpointUsage` property-Set by using values from the `DTSCheckpointUsage` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-133">DTSCheckpointUsage 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-133">Friendly name in DTSCheckpointUsage</span></span>|<span data-ttu-id="760ba-134">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-134">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="760ba-135">永不</span><span class="sxs-lookup"><span data-stu-id="760ba-135">Never</span></span>|<span data-ttu-id="760ba-136">0</span><span class="sxs-lookup"><span data-stu-id="760ba-136">0</span></span>|  
|<span data-ttu-id="760ba-137">IfExists</span><span class="sxs-lookup"><span data-stu-id="760ba-137">IfExists</span></span>|<span data-ttu-id="760ba-138">1</span><span class="sxs-lookup"><span data-stu-id="760ba-138">1</span></span>|  
|<span data-ttu-id="760ba-139">一律</span><span class="sxs-lookup"><span data-stu-id="760ba-139">Always</span></span>|<span data-ttu-id="760ba-140">2</span><span class="sxs-lookup"><span data-stu-id="760ba-140">2</span></span>|  
  
 <span data-ttu-id="760ba-141">`PackagePriorityClass`屬性：使用來自列舉的值進行設定 `DTSPriorityClass` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-141">`PackagePriorityClass` property-Set by using values from the `DTSPriorityClass` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-142">DTSPriorityClass 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-142">Friendly name in DTSPriorityClass</span></span>|<span data-ttu-id="760ba-143">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-143">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="760ba-144">預設</span><span class="sxs-lookup"><span data-stu-id="760ba-144">Default</span></span>|<span data-ttu-id="760ba-145">0</span><span class="sxs-lookup"><span data-stu-id="760ba-145">0</span></span>|  
|<span data-ttu-id="760ba-146">AboveNormal</span><span class="sxs-lookup"><span data-stu-id="760ba-146">AboveNormal</span></span>|<span data-ttu-id="760ba-147">1</span><span class="sxs-lookup"><span data-stu-id="760ba-147">1</span></span>|  
|<span data-ttu-id="760ba-148">正常</span><span class="sxs-lookup"><span data-stu-id="760ba-148">Normal</span></span>|<span data-ttu-id="760ba-149">2</span><span class="sxs-lookup"><span data-stu-id="760ba-149">2</span></span>|  
|<span data-ttu-id="760ba-150">BelowNormal</span><span class="sxs-lookup"><span data-stu-id="760ba-150">BelowNormal</span></span>|<span data-ttu-id="760ba-151">3</span><span class="sxs-lookup"><span data-stu-id="760ba-151">3</span></span>|  
|<span data-ttu-id="760ba-152">閒置</span><span class="sxs-lookup"><span data-stu-id="760ba-152">Idle</span></span>|<span data-ttu-id="760ba-153">4</span><span class="sxs-lookup"><span data-stu-id="760ba-153">4</span></span>|  
  
 <span data-ttu-id="760ba-154">`ProtectionLevel`屬性：使用來自列舉的值進行設定 `DTSProtectionLevel` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-154">`ProtectionLevel` property-Set by using values from the `DTSProtectionLevel` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-155">DTSProtectionLevel 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-155">Friendly name in DTSProtectionLevel</span></span>|<span data-ttu-id="760ba-156">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-156">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="760ba-157">DontSaveSensitive</span><span class="sxs-lookup"><span data-stu-id="760ba-157">DontSaveSensitive</span></span>|<span data-ttu-id="760ba-158">0</span><span class="sxs-lookup"><span data-stu-id="760ba-158">0</span></span>|  
|<span data-ttu-id="760ba-159">EncryptSensitiveWithUserKey</span><span class="sxs-lookup"><span data-stu-id="760ba-159">EncryptSensitiveWithUserKey</span></span>|<span data-ttu-id="760ba-160">1</span><span class="sxs-lookup"><span data-stu-id="760ba-160">1</span></span>|  
|<span data-ttu-id="760ba-161">EncryptSensitiveWithPassword</span><span class="sxs-lookup"><span data-stu-id="760ba-161">EncryptSensitiveWithPassword</span></span>|<span data-ttu-id="760ba-162">2</span><span class="sxs-lookup"><span data-stu-id="760ba-162">2</span></span>|  
|<span data-ttu-id="760ba-163">EncryptAllWithPassword</span><span class="sxs-lookup"><span data-stu-id="760ba-163">EncryptAllWithPassword</span></span>|<span data-ttu-id="760ba-164">3</span><span class="sxs-lookup"><span data-stu-id="760ba-164">3</span></span>|  
|<span data-ttu-id="760ba-165">EncryptAllWithUserKey</span><span class="sxs-lookup"><span data-stu-id="760ba-165">EncryptAllWithUserKey</span></span>|<span data-ttu-id="760ba-166">4</span><span class="sxs-lookup"><span data-stu-id="760ba-166">4</span></span>|  
|<span data-ttu-id="760ba-167">ServerStorage</span><span class="sxs-lookup"><span data-stu-id="760ba-167">ServerStorage</span></span>|<span data-ttu-id="760ba-168">5</span><span class="sxs-lookup"><span data-stu-id="760ba-168">5</span></span>|  
  
##  <a name="precedence-constraints"></a><a name="PrecedenceConstraints"></a> <span data-ttu-id="760ba-169">優先順序條件約束</span><span class="sxs-lookup"><span data-stu-id="760ba-169">Precedence Constraints</span></span>  
 <span data-ttu-id="760ba-170">`EvalOp`屬性：使用來自列舉的值進行設定 `DTSPrecedenceEvalOp` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-170">`EvalOp` property-Set by using values from the `DTSPrecedenceEvalOp` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-171">DTSPrecedenceEvalOp 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-171">Friendly name in DTSPrecedenceEvalOp</span></span>|<span data-ttu-id="760ba-172">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-172">Numeric value</span></span>|  
|------------------------------------------|-------------------|  
|<span data-ttu-id="760ba-173">運算是</span><span class="sxs-lookup"><span data-stu-id="760ba-173">Expression</span></span>|<span data-ttu-id="760ba-174">1</span><span class="sxs-lookup"><span data-stu-id="760ba-174">1</span></span>|  
|<span data-ttu-id="760ba-175">條件約束</span><span class="sxs-lookup"><span data-stu-id="760ba-175">Constraint</span></span>|<span data-ttu-id="760ba-176">2</span><span class="sxs-lookup"><span data-stu-id="760ba-176">2</span></span>|  
|<span data-ttu-id="760ba-177">ExpressionAndConstraint</span><span class="sxs-lookup"><span data-stu-id="760ba-177">ExpressionAndConstraint</span></span>|<span data-ttu-id="760ba-178">3</span><span class="sxs-lookup"><span data-stu-id="760ba-178">3</span></span>|  
|<span data-ttu-id="760ba-179">ExpressionOrConstraint</span><span class="sxs-lookup"><span data-stu-id="760ba-179">ExpressionOrConstraint</span></span>|<span data-ttu-id="760ba-180">4</span><span class="sxs-lookup"><span data-stu-id="760ba-180">4</span></span>|  
  
 <span data-ttu-id="760ba-181">`Value`屬性：使用來自列舉的值進行設定 `DTSExecResult` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-181">`Value` property-Set by using values from the `DTSExecResult` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-182">易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-182">Friendly Name</span></span>|<span data-ttu-id="760ba-183">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-183">Numeric Value</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="760ba-184">Success</span><span class="sxs-lookup"><span data-stu-id="760ba-184">Success</span></span>|<span data-ttu-id="760ba-185">0</span><span class="sxs-lookup"><span data-stu-id="760ba-185">0</span></span>|  
|<span data-ttu-id="760ba-186">失敗</span><span class="sxs-lookup"><span data-stu-id="760ba-186">Failure</span></span>|<span data-ttu-id="760ba-187">1</span><span class="sxs-lookup"><span data-stu-id="760ba-187">1</span></span>|  
|<span data-ttu-id="760ba-188">Completion</span><span class="sxs-lookup"><span data-stu-id="760ba-188">Completion</span></span>|<span data-ttu-id="760ba-189">2</span><span class="sxs-lookup"><span data-stu-id="760ba-189">2</span></span>|  
|<span data-ttu-id="760ba-190">已取消</span><span class="sxs-lookup"><span data-stu-id="760ba-190">Canceled</span></span>|<span data-ttu-id="760ba-191">3</span><span class="sxs-lookup"><span data-stu-id="760ba-191">3</span></span>|  
  
##  <a name="foreach-loop-enumerators"></a><a name="Foreach"></a> <span data-ttu-id="760ba-192">Foreach 迴圈列舉值</span><span class="sxs-lookup"><span data-stu-id="760ba-192">Foreach Loop Enumerators</span></span>  
 <span data-ttu-id="760ba-193">「Foreach 迴圈」包含一組列舉值，其屬性可由屬性運算式設定。</span><span class="sxs-lookup"><span data-stu-id="760ba-193">The Foreach Loop includes a set of enumerators with properties that can be set by property expressions.</span></span>  
  
### <a name="foreach-ado-enumerator"></a><span data-ttu-id="760ba-194">Foreach ADO 列舉值</span><span class="sxs-lookup"><span data-stu-id="760ba-194">Foreach ADO Enumerator</span></span>  
 <span data-ttu-id="760ba-195">`Type`屬性：使用來自列舉的值進行設定 `ADOEnumerationType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-195">`Type` property-Set by using values from the `ADOEnumerationType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-196">ADOEnumerationType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-196">Friendly name in ADOEnumerationType</span></span>|<span data-ttu-id="760ba-197">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-197">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="760ba-198">EnumerateTables</span><span class="sxs-lookup"><span data-stu-id="760ba-198">EnumerateTables</span></span>|<span data-ttu-id="760ba-199">0</span><span class="sxs-lookup"><span data-stu-id="760ba-199">0</span></span>|  
|<span data-ttu-id="760ba-200">EnumerateAllRows</span><span class="sxs-lookup"><span data-stu-id="760ba-200">EnumerateAllRows</span></span>|<span data-ttu-id="760ba-201">1</span><span class="sxs-lookup"><span data-stu-id="760ba-201">1</span></span>|  
|<span data-ttu-id="760ba-202">EnumerateRowsInFirstTable</span><span class="sxs-lookup"><span data-stu-id="760ba-202">EnumerateRowsInFirstTable</span></span>|<span data-ttu-id="760ba-203">2</span><span class="sxs-lookup"><span data-stu-id="760ba-203">2</span></span>|  
  
### <a name="foreach-nodelist-enumerator"></a><span data-ttu-id="760ba-204">Foreach NodeList 列舉值</span><span class="sxs-lookup"><span data-stu-id="760ba-204">Foreach Nodelist Enumerator</span></span>  
 <span data-ttu-id="760ba-205">`SourceDocumentType`、 `InnerXPathStringSourceType` 和**OuterXPathStringSourceType**屬性：使用來自列舉的值進行設定 `SourceType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-205">`SourceDocumentType`, `InnerXPathStringSourceType`, and **OuterXPathStringSourceType** properties-Set by using values from the `SourceType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-206">SourceType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-206">Friendly name in SourceType</span></span>|<span data-ttu-id="760ba-207">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-207">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="760ba-208">FileConnection</span><span class="sxs-lookup"><span data-stu-id="760ba-208">FileConnection</span></span>|<span data-ttu-id="760ba-209">0</span><span class="sxs-lookup"><span data-stu-id="760ba-209">0</span></span>|  
|<span data-ttu-id="760ba-210">變數</span><span class="sxs-lookup"><span data-stu-id="760ba-210">Variable</span></span>|<span data-ttu-id="760ba-211">1</span><span class="sxs-lookup"><span data-stu-id="760ba-211">1</span></span>|  
|<span data-ttu-id="760ba-212">DirectInput</span><span class="sxs-lookup"><span data-stu-id="760ba-212">DirectInput</span></span>|<span data-ttu-id="760ba-213">2</span><span class="sxs-lookup"><span data-stu-id="760ba-213">2</span></span>|  
  
 <span data-ttu-id="760ba-214">`EnumerationType`屬性：使用來自列舉的值進行設定 `EnumerationType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-214">`EnumerationType` property-Set by using values from the `EnumerationType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-215">EnumerationType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-215">Friendly name in EnumerationType</span></span>|<span data-ttu-id="760ba-216">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-216">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="760ba-217">導覽器</span><span class="sxs-lookup"><span data-stu-id="760ba-217">Navigator</span></span>|<span data-ttu-id="760ba-218">0</span><span class="sxs-lookup"><span data-stu-id="760ba-218">0</span></span>|  
|<span data-ttu-id="760ba-219">節點</span><span class="sxs-lookup"><span data-stu-id="760ba-219">Node</span></span>|<span data-ttu-id="760ba-220">1</span><span class="sxs-lookup"><span data-stu-id="760ba-220">1</span></span>|  
|<span data-ttu-id="760ba-221">NodeText</span><span class="sxs-lookup"><span data-stu-id="760ba-221">NodeText</span></span>|<span data-ttu-id="760ba-222">2</span><span class="sxs-lookup"><span data-stu-id="760ba-222">2</span></span>|  
|<span data-ttu-id="760ba-223">ElementCollection</span><span class="sxs-lookup"><span data-stu-id="760ba-223">ElementCollection</span></span>|<span data-ttu-id="760ba-224">3</span><span class="sxs-lookup"><span data-stu-id="760ba-224">3</span></span>|  
  
 <span data-ttu-id="760ba-225">`InnerElementType`屬性：使用來自列舉的值進行設定 `InnerElementType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-225">`InnerElementType` property-Set by using values from the `InnerElementType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-226">InnerElementType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-226">Friendly name in InnerElementType</span></span>|<span data-ttu-id="760ba-227">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-227">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="760ba-228">導覽器</span><span class="sxs-lookup"><span data-stu-id="760ba-228">Navigator</span></span>|<span data-ttu-id="760ba-229">0</span><span class="sxs-lookup"><span data-stu-id="760ba-229">0</span></span>|  
|<span data-ttu-id="760ba-230">節點</span><span class="sxs-lookup"><span data-stu-id="760ba-230">Node</span></span>|<span data-ttu-id="760ba-231">1</span><span class="sxs-lookup"><span data-stu-id="760ba-231">1</span></span>|  
|<span data-ttu-id="760ba-232">NodeText</span><span class="sxs-lookup"><span data-stu-id="760ba-232">NodeText</span></span>|<span data-ttu-id="760ba-233">2</span><span class="sxs-lookup"><span data-stu-id="760ba-233">2</span></span>|  
  
##  <a name="tasks"></a><a name="Tasks"></a> <span data-ttu-id="760ba-234">工作</span><span class="sxs-lookup"><span data-stu-id="760ba-234">Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="760ba-235">包含許多工作，其屬性可由屬性運算式設定。</span><span class="sxs-lookup"><span data-stu-id="760ba-235">includes numerous tasks with properties that can be set by property expressions.</span></span>  
  
### <a name="analysis-services-execute-ddl-task"></a><span data-ttu-id="760ba-236">Analysis Services 執行 DDL 工作</span><span class="sxs-lookup"><span data-stu-id="760ba-236">Analysis Services Execute DDL Task</span></span>  
 <span data-ttu-id="760ba-237">`SourceType`屬性：使用來自列舉的值進行設定 `DDLSourceType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-237">`SourceType` property-Set by using values from the `DDLSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-238">DDLSourceType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-238">Friendly name in DDLSourceType</span></span>|<span data-ttu-id="760ba-239">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-239">Numeric value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="760ba-240">DirectInput</span><span class="sxs-lookup"><span data-stu-id="760ba-240">DirectInput</span></span>|<span data-ttu-id="760ba-241">0</span><span class="sxs-lookup"><span data-stu-id="760ba-241">0</span></span>|  
|<span data-ttu-id="760ba-242">FileConnection</span><span class="sxs-lookup"><span data-stu-id="760ba-242">FileConnection</span></span>|<span data-ttu-id="760ba-243">1</span><span class="sxs-lookup"><span data-stu-id="760ba-243">1</span></span>|  
|<span data-ttu-id="760ba-244">變數</span><span class="sxs-lookup"><span data-stu-id="760ba-244">Variable</span></span>|<span data-ttu-id="760ba-245">2</span><span class="sxs-lookup"><span data-stu-id="760ba-245">2</span></span>|  
  
### <a name="bulk-insert-task"></a><span data-ttu-id="760ba-246">大量插入工作</span><span class="sxs-lookup"><span data-stu-id="760ba-246">Bulk Insert Task</span></span>  
 <span data-ttu-id="760ba-247">`DataFileType`屬性：使用來自列舉的值進行設定 `DTSBulkInsert_DataFileType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-247">`DataFileType` property-Set by using values from the `DTSBulkInsert_DataFileType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-248">DTSBulkInsert_DataFileType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-248">Friendly name in DTSBulkInsert_DataFileType</span></span>|<span data-ttu-id="760ba-249">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-249">Numeric value</span></span>|  
|--------------------------------------------------|-------------------|  
|<span data-ttu-id="760ba-250">DTSBulkInsert_DataFileType_Char</span><span class="sxs-lookup"><span data-stu-id="760ba-250">DTSBulkInsert_DataFileType_Char</span></span>|<span data-ttu-id="760ba-251">0</span><span class="sxs-lookup"><span data-stu-id="760ba-251">0</span></span>|  
|<span data-ttu-id="760ba-252">DTSBulkInsert_DataFileType_Native</span><span class="sxs-lookup"><span data-stu-id="760ba-252">DTSBulkInsert_DataFileType_Native</span></span>|<span data-ttu-id="760ba-253">1</span><span class="sxs-lookup"><span data-stu-id="760ba-253">1</span></span>|  
|<span data-ttu-id="760ba-254">DTSBulkInsert_DataFileType_WideChar</span><span class="sxs-lookup"><span data-stu-id="760ba-254">DTSBulkInsert_DataFileType_WideChar</span></span>|<span data-ttu-id="760ba-255">2</span><span class="sxs-lookup"><span data-stu-id="760ba-255">2</span></span>|  
|<span data-ttu-id="760ba-256">DTSBulkInsert_DataFileType_WideNative</span><span class="sxs-lookup"><span data-stu-id="760ba-256">DTSBulkInsert_DataFileType_WideNative</span></span>|<span data-ttu-id="760ba-257">3</span><span class="sxs-lookup"><span data-stu-id="760ba-257">3</span></span>|  
  
### <a name="execute-sql-task"></a><span data-ttu-id="760ba-258">執行 SQL 工作</span><span class="sxs-lookup"><span data-stu-id="760ba-258">Execute SQL Task</span></span>  
 <span data-ttu-id="760ba-259">`ResultSetType`屬性：使用來自列舉的值進行設定 `ResultSetType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-259">`ResultSetType` property-Set by using values from the `ResultSetType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-260">ResultSetType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-260">Friendly name in ResultSetType</span></span>|<span data-ttu-id="760ba-261">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-261">Numeric Value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="760ba-262">ResultSetType_None</span><span class="sxs-lookup"><span data-stu-id="760ba-262">ResultSetType_None</span></span>|<span data-ttu-id="760ba-263">1</span><span class="sxs-lookup"><span data-stu-id="760ba-263">1</span></span>|  
|<span data-ttu-id="760ba-264">ResultSetType_SingleRow</span><span class="sxs-lookup"><span data-stu-id="760ba-264">ResultSetType_SingleRow</span></span>|<span data-ttu-id="760ba-265">2</span><span class="sxs-lookup"><span data-stu-id="760ba-265">2</span></span>|  
|<span data-ttu-id="760ba-266">ResultSetType_Rowset</span><span class="sxs-lookup"><span data-stu-id="760ba-266">ResultSetType_Rowset</span></span>|<span data-ttu-id="760ba-267">3</span><span class="sxs-lookup"><span data-stu-id="760ba-267">3</span></span>|  
|<span data-ttu-id="760ba-268">ResultSetType_XML</span><span class="sxs-lookup"><span data-stu-id="760ba-268">ResultSetType_XML</span></span>|<span data-ttu-id="760ba-269">4</span><span class="sxs-lookup"><span data-stu-id="760ba-269">4</span></span>|  
  
 <span data-ttu-id="760ba-270">`SqlStatementSourceType`屬性：使用來自列舉的值進行設定 `SqlStatementSourceType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-270">`SqlStatementSourceType` property-Set by using values from the `SqlStatementSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-271">SqlStatementSourceType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-271">Friendly name in SqlStatementSourceType</span></span>|<span data-ttu-id="760ba-272">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-272">Numeric Value</span></span>|  
|---------------------------------------------|-------------------|  
|<span data-ttu-id="760ba-273">DirectInput</span><span class="sxs-lookup"><span data-stu-id="760ba-273">DirectInput</span></span>|<span data-ttu-id="760ba-274">1</span><span class="sxs-lookup"><span data-stu-id="760ba-274">1</span></span>|  
|<span data-ttu-id="760ba-275">FileConnection</span><span class="sxs-lookup"><span data-stu-id="760ba-275">FileConnection</span></span>|<span data-ttu-id="760ba-276">2</span><span class="sxs-lookup"><span data-stu-id="760ba-276">2</span></span>|  
|<span data-ttu-id="760ba-277">變數</span><span class="sxs-lookup"><span data-stu-id="760ba-277">Variable</span></span>|<span data-ttu-id="760ba-278">3</span><span class="sxs-lookup"><span data-stu-id="760ba-278">3</span></span>|  
  
### <a name="file-system-task"></a><span data-ttu-id="760ba-279">檔案系統工作</span><span class="sxs-lookup"><span data-stu-id="760ba-279">File System Task</span></span>  
 <span data-ttu-id="760ba-280">`Operation`屬性：使用來自列舉的值進行設定 `DTSFileSystemOperation` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-280">`Operation` property-Set by using values from the `DTSFileSystemOperation` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-281">DTSFileSystemOperation 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-281">Friendly name in DTSFileSystemOperation</span></span>|<span data-ttu-id="760ba-282">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-282">Numeric value</span></span>|  
|---------------------------------------------|-------------------|  
|<span data-ttu-id="760ba-283">CopyFile</span><span class="sxs-lookup"><span data-stu-id="760ba-283">CopyFile</span></span>|<span data-ttu-id="760ba-284">0</span><span class="sxs-lookup"><span data-stu-id="760ba-284">0</span></span>|  
|<span data-ttu-id="760ba-285">MoveFile</span><span class="sxs-lookup"><span data-stu-id="760ba-285">MoveFile</span></span>|<span data-ttu-id="760ba-286">1</span><span class="sxs-lookup"><span data-stu-id="760ba-286">1</span></span>|  
|<span data-ttu-id="760ba-287">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="760ba-287">DeleteFile</span></span>|<span data-ttu-id="760ba-288">2</span><span class="sxs-lookup"><span data-stu-id="760ba-288">2</span></span>|  
|<span data-ttu-id="760ba-289">RenameFile</span><span class="sxs-lookup"><span data-stu-id="760ba-289">RenameFile</span></span>|<span data-ttu-id="760ba-290">3</span><span class="sxs-lookup"><span data-stu-id="760ba-290">3</span></span>|  
|<span data-ttu-id="760ba-291">SetAttributes</span><span class="sxs-lookup"><span data-stu-id="760ba-291">SetAttributes</span></span>|<span data-ttu-id="760ba-292">4</span><span class="sxs-lookup"><span data-stu-id="760ba-292">4</span></span>|  
|<span data-ttu-id="760ba-293">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="760ba-293">CreateDirectory</span></span>|<span data-ttu-id="760ba-294">5</span><span class="sxs-lookup"><span data-stu-id="760ba-294">5</span></span>|  
|<span data-ttu-id="760ba-295">CopyDirectory</span><span class="sxs-lookup"><span data-stu-id="760ba-295">CopyDirectory</span></span>|<span data-ttu-id="760ba-296">6</span><span class="sxs-lookup"><span data-stu-id="760ba-296">6</span></span>|  
|<span data-ttu-id="760ba-297">MoveDirectory</span><span class="sxs-lookup"><span data-stu-id="760ba-297">MoveDirectory</span></span>|<span data-ttu-id="760ba-298">7</span><span class="sxs-lookup"><span data-stu-id="760ba-298">7</span></span>|  
|<span data-ttu-id="760ba-299">DeleteDirectory</span><span class="sxs-lookup"><span data-stu-id="760ba-299">DeleteDirectory</span></span>|<span data-ttu-id="760ba-300">8</span><span class="sxs-lookup"><span data-stu-id="760ba-300">8</span></span>|  
|<span data-ttu-id="760ba-301">DeleteDirectoryContent</span><span class="sxs-lookup"><span data-stu-id="760ba-301">DeleteDirectoryContent</span></span>|<span data-ttu-id="760ba-302">9</span><span class="sxs-lookup"><span data-stu-id="760ba-302">9</span></span>|  
  
 <span data-ttu-id="760ba-303">`Attributes`屬性：使用來自列舉的值進行設定 `DTSFileSystemAttributes` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-303">`Attributes` property-Set by using values from the `DTSFileSystemAttributes` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-304">DTSFileSystemAttributes 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-304">Friendly name in DTSFileSystemAttributes</span></span>|<span data-ttu-id="760ba-305">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-305">Numeric value</span></span>|  
|----------------------------------------------|-------------------|  
|<span data-ttu-id="760ba-306">正常</span><span class="sxs-lookup"><span data-stu-id="760ba-306">Normal</span></span>|<span data-ttu-id="760ba-307">0</span><span class="sxs-lookup"><span data-stu-id="760ba-307">0</span></span>|  
|<span data-ttu-id="760ba-308">封存</span><span class="sxs-lookup"><span data-stu-id="760ba-308">Archive</span></span>|<span data-ttu-id="760ba-309">1</span><span class="sxs-lookup"><span data-stu-id="760ba-309">1</span></span>|  
|<span data-ttu-id="760ba-310">Hidden</span><span class="sxs-lookup"><span data-stu-id="760ba-310">Hidden</span></span>|<span data-ttu-id="760ba-311">2</span><span class="sxs-lookup"><span data-stu-id="760ba-311">2</span></span>|  
|<span data-ttu-id="760ba-312">唯讀</span><span class="sxs-lookup"><span data-stu-id="760ba-312">ReadOnly</span></span>|<span data-ttu-id="760ba-313">4</span><span class="sxs-lookup"><span data-stu-id="760ba-313">4</span></span>|  
|<span data-ttu-id="760ba-314">系統</span><span class="sxs-lookup"><span data-stu-id="760ba-314">System</span></span>|<span data-ttu-id="760ba-315">8</span><span class="sxs-lookup"><span data-stu-id="760ba-315">8</span></span>|  
  
### <a name="ftp-task"></a><span data-ttu-id="760ba-316">FTP 工作</span><span class="sxs-lookup"><span data-stu-id="760ba-316">FTP Task</span></span>  
 <span data-ttu-id="760ba-317">`Operation`屬性：使用來自列舉的值進行設定 `DTSFTPOp` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-317">`Operation` property-Set by using values from the `DTSFTPOp` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-318">DTSFTPOp 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-318">Friendly name in DTSFTPOp</span></span>|<span data-ttu-id="760ba-319">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-319">Numeric value</span></span>|  
|-------------------------------|-------------------|  
|<span data-ttu-id="760ba-320">Send</span><span class="sxs-lookup"><span data-stu-id="760ba-320">Send</span></span>|<span data-ttu-id="760ba-321">0</span><span class="sxs-lookup"><span data-stu-id="760ba-321">0</span></span>|  
|<span data-ttu-id="760ba-322">接收</span><span class="sxs-lookup"><span data-stu-id="760ba-322">Receive</span></span>|<span data-ttu-id="760ba-323">1</span><span class="sxs-lookup"><span data-stu-id="760ba-323">1</span></span>|  
|<span data-ttu-id="760ba-324">DeleteLocal</span><span class="sxs-lookup"><span data-stu-id="760ba-324">DeleteLocal</span></span>|<span data-ttu-id="760ba-325">2</span><span class="sxs-lookup"><span data-stu-id="760ba-325">2</span></span>|  
|<span data-ttu-id="760ba-326">DeleteRemote</span><span class="sxs-lookup"><span data-stu-id="760ba-326">DeleteRemote</span></span>|<span data-ttu-id="760ba-327">3</span><span class="sxs-lookup"><span data-stu-id="760ba-327">3</span></span>|  
|<span data-ttu-id="760ba-328">MakeDirLocal</span><span class="sxs-lookup"><span data-stu-id="760ba-328">MakeDirLocal</span></span>|<span data-ttu-id="760ba-329">4</span><span class="sxs-lookup"><span data-stu-id="760ba-329">4</span></span>|  
|<span data-ttu-id="760ba-330">MakeDirRemote</span><span class="sxs-lookup"><span data-stu-id="760ba-330">MakeDirRemote</span></span>|<span data-ttu-id="760ba-331">5</span><span class="sxs-lookup"><span data-stu-id="760ba-331">5</span></span>|  
|<span data-ttu-id="760ba-332">RemoveDirLocal</span><span class="sxs-lookup"><span data-stu-id="760ba-332">RemoveDirLocal</span></span>|<span data-ttu-id="760ba-333">6</span><span class="sxs-lookup"><span data-stu-id="760ba-333">6</span></span>|  
|<span data-ttu-id="760ba-334">RemoveDirRemote</span><span class="sxs-lookup"><span data-stu-id="760ba-334">RemoveDirRemote</span></span>|<span data-ttu-id="760ba-335">7</span><span class="sxs-lookup"><span data-stu-id="760ba-335">7</span></span>|  
  
### <a name="message-queue-task"></a><span data-ttu-id="760ba-336">Message Queue Task</span><span class="sxs-lookup"><span data-stu-id="760ba-336">Message Queue Task</span></span>  
 <span data-ttu-id="760ba-337">`MessageType`屬性：使用來自列舉的值進行設定 `MQMessageType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-337">`MessageType` property-Set by using values from the `MQMessageType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-338">MQMessageType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-338">Friendly name in MQMessageType</span></span>|<span data-ttu-id="760ba-339">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-339">Numeric value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="760ba-340">DTSMQMessageType_String</span><span class="sxs-lookup"><span data-stu-id="760ba-340">DTSMQMessageType_String</span></span>|<span data-ttu-id="760ba-341">0</span><span class="sxs-lookup"><span data-stu-id="760ba-341">0</span></span>|  
|<span data-ttu-id="760ba-342">DTSMQMessageType_DataFile</span><span class="sxs-lookup"><span data-stu-id="760ba-342">DTSMQMessageType_DataFile</span></span>|<span data-ttu-id="760ba-343">1</span><span class="sxs-lookup"><span data-stu-id="760ba-343">1</span></span>|  
|<span data-ttu-id="760ba-344">DTSMQMessageType_Variables</span><span class="sxs-lookup"><span data-stu-id="760ba-344">DTSMQMessageType_Variables</span></span>|<span data-ttu-id="760ba-345">2</span><span class="sxs-lookup"><span data-stu-id="760ba-345">2</span></span>|  
|<span data-ttu-id="760ba-346">DTSMQMessagType_StringMessageToVariable</span><span class="sxs-lookup"><span data-stu-id="760ba-346">DTSMQMessagType_StringMessageToVariable</span></span>|<span data-ttu-id="760ba-347">3</span><span class="sxs-lookup"><span data-stu-id="760ba-347">3</span></span>|  
  
 <span data-ttu-id="760ba-348">`StringCompareType`屬性：使用來自列舉的值進行設定 `MQStringMessageCompare` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-348">`StringCompareType` property-Set by using values from the `MQStringMessageCompare` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-349">MQStringMessageCompare 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-349">Friendly name in MQStringMessageCompare</span></span>|<span data-ttu-id="760ba-350">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-350">Numeric value</span></span>|  
|---------------------------------------------|-------------------|  
|<span data-ttu-id="760ba-351">DTSMQStringMessageCompare_None</span><span class="sxs-lookup"><span data-stu-id="760ba-351">DTSMQStringMessageCompare_None</span></span>|<span data-ttu-id="760ba-352">0</span><span class="sxs-lookup"><span data-stu-id="760ba-352">0</span></span>|  
|<span data-ttu-id="760ba-353">DTSMQStringMessageCompare_Exact</span><span class="sxs-lookup"><span data-stu-id="760ba-353">DTSMQStringMessageCompare_Exact</span></span>|<span data-ttu-id="760ba-354">1</span><span class="sxs-lookup"><span data-stu-id="760ba-354">1</span></span>|  
|<span data-ttu-id="760ba-355">DTSMQStringMessageCompare_IgnoreCase</span><span class="sxs-lookup"><span data-stu-id="760ba-355">DTSMQStringMessageCompare_IgnoreCase</span></span>|<span data-ttu-id="760ba-356">2</span><span class="sxs-lookup"><span data-stu-id="760ba-356">2</span></span>|  
|<span data-ttu-id="760ba-357">DTSMQStringMessageCompare_Contains</span><span class="sxs-lookup"><span data-stu-id="760ba-357">DTSMQStringMessageCompare_Contains</span></span>|<span data-ttu-id="760ba-358">3</span><span class="sxs-lookup"><span data-stu-id="760ba-358">3</span></span>|  
  
 <span data-ttu-id="760ba-359">`TaskType`屬性：使用來自列舉的值進行設定 `MQType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-359">`TaskType` property-Set by using values from the `MQType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-360">MQType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-360">Friendly name in MQType</span></span>|<span data-ttu-id="760ba-361">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-361">Numeric value</span></span>|  
|-----------------------------|-------------------|  
|<span data-ttu-id="760ba-362">DTSMQType_Sender</span><span class="sxs-lookup"><span data-stu-id="760ba-362">DTSMQType_Sender</span></span>|<span data-ttu-id="760ba-363">0</span><span class="sxs-lookup"><span data-stu-id="760ba-363">0</span></span>|  
|<span data-ttu-id="760ba-364">DTSMQType_Receiver</span><span class="sxs-lookup"><span data-stu-id="760ba-364">DTSMQType_Receiver</span></span>|<span data-ttu-id="760ba-365">1</span><span class="sxs-lookup"><span data-stu-id="760ba-365">1</span></span>|  
  
### <a name="send-mail-task"></a><span data-ttu-id="760ba-366">傳送郵件工作</span><span class="sxs-lookup"><span data-stu-id="760ba-366">Send Mail Task</span></span>  
 <span data-ttu-id="760ba-367">`MessageSourceType`屬性：使用來自列舉的值進行設定 `SendMailMessageSourceType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-367">`MessageSourceType` property-Set by using values from the `SendMailMessageSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-368">SendMailMessageSourceType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-368">Friendly Name in SendMailMessageSourceType</span></span>|<span data-ttu-id="760ba-369">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-369">Numeric Value</span></span>|  
|------------------------------------------------|-------------------|  
|<span data-ttu-id="760ba-370">DirectInput</span><span class="sxs-lookup"><span data-stu-id="760ba-370">DirectInput</span></span>|<span data-ttu-id="760ba-371">0</span><span class="sxs-lookup"><span data-stu-id="760ba-371">0</span></span>|  
|<span data-ttu-id="760ba-372">FileConnection</span><span class="sxs-lookup"><span data-stu-id="760ba-372">FileConnection</span></span>|<span data-ttu-id="760ba-373">1</span><span class="sxs-lookup"><span data-stu-id="760ba-373">1</span></span>|  
|<span data-ttu-id="760ba-374">變數</span><span class="sxs-lookup"><span data-stu-id="760ba-374">Variable</span></span>|<span data-ttu-id="760ba-375">2</span><span class="sxs-lookup"><span data-stu-id="760ba-375">2</span></span>|  
  
 <span data-ttu-id="760ba-376">`Priority`屬性：使用來自列舉的值進行設定 `MailPriority` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-376">`Priority` property-Set by using values from the `MailPriority` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-377">MailPriority 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-377">Friendly Name in MailPriority</span></span>|<span data-ttu-id="760ba-378">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-378">Numeric Value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="760ba-379">高</span><span class="sxs-lookup"><span data-stu-id="760ba-379">High</span></span>|<span data-ttu-id="760ba-380">1</span><span class="sxs-lookup"><span data-stu-id="760ba-380">1</span></span>|  
|<span data-ttu-id="760ba-381">正常</span><span class="sxs-lookup"><span data-stu-id="760ba-381">Normal</span></span>|<span data-ttu-id="760ba-382">3</span><span class="sxs-lookup"><span data-stu-id="760ba-382">3</span></span>|  
|<span data-ttu-id="760ba-383">低</span><span class="sxs-lookup"><span data-stu-id="760ba-383">Low</span></span>|<span data-ttu-id="760ba-384">5</span><span class="sxs-lookup"><span data-stu-id="760ba-384">5</span></span>|  
  
### <a name="transfer-database-task"></a><span data-ttu-id="760ba-385">傳送資料庫工作</span><span class="sxs-lookup"><span data-stu-id="760ba-385">Transfer Database Task</span></span>  
 <span data-ttu-id="760ba-386">`Action`屬性：使用來自列舉的值進行設定 `TransferAction` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-386">`Action` property-Set by using values from the `TransferAction` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-387">TransferAction 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-387">Friendly name in TransferAction</span></span>|<span data-ttu-id="760ba-388">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-388">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="760ba-389">[複製]</span><span class="sxs-lookup"><span data-stu-id="760ba-389">Copy</span></span>|<span data-ttu-id="760ba-390">0</span><span class="sxs-lookup"><span data-stu-id="760ba-390">0</span></span>|  
|<span data-ttu-id="760ba-391">移動</span><span class="sxs-lookup"><span data-stu-id="760ba-391">Move</span></span>|<span data-ttu-id="760ba-392">1</span><span class="sxs-lookup"><span data-stu-id="760ba-392">1</span></span>|  
  
 <span data-ttu-id="760ba-393">`Method`屬性：使用來自列舉的值進行設定 `TransferMethod` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-393">`Method` property-Set by using values from the `TransferMethod` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-394">TransferMethod 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-394">Friendly name in TransferMethod</span></span>|<span data-ttu-id="760ba-395">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-395">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="760ba-396">DatabaseOffline</span><span class="sxs-lookup"><span data-stu-id="760ba-396">DatabaseOffline</span></span>|<span data-ttu-id="760ba-397">0</span><span class="sxs-lookup"><span data-stu-id="760ba-397">0</span></span>|  
|<span data-ttu-id="760ba-398">DatabaseOnline</span><span class="sxs-lookup"><span data-stu-id="760ba-398">DatabaseOnline</span></span>|<span data-ttu-id="760ba-399">1</span><span class="sxs-lookup"><span data-stu-id="760ba-399">1</span></span>|  
  
### <a name="transfer-error-messages-task"></a><span data-ttu-id="760ba-400">傳送錯誤訊息工作</span><span class="sxs-lookup"><span data-stu-id="760ba-400">Transfer Error Messages Task</span></span>  
 <span data-ttu-id="760ba-401">`IfObjectExists`屬性：使用來自列舉的值進行設定 `IfObjectExists` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-401">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-402">IfObjectExists 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-402">Friendly Name in IfObjectExists</span></span>|<span data-ttu-id="760ba-403">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-403">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="760ba-404">FailTask</span><span class="sxs-lookup"><span data-stu-id="760ba-404">FailTask</span></span>|<span data-ttu-id="760ba-405">0</span><span class="sxs-lookup"><span data-stu-id="760ba-405">0</span></span>|  
|<span data-ttu-id="760ba-406">Overwrite</span><span class="sxs-lookup"><span data-stu-id="760ba-406">Overwrite</span></span>|<span data-ttu-id="760ba-407">1</span><span class="sxs-lookup"><span data-stu-id="760ba-407">1</span></span>|  
|<span data-ttu-id="760ba-408">Skip</span><span class="sxs-lookup"><span data-stu-id="760ba-408">Skip</span></span>|<span data-ttu-id="760ba-409">2</span><span class="sxs-lookup"><span data-stu-id="760ba-409">2</span></span>|  
  
### <a name="transfer-jobs-task"></a><span data-ttu-id="760ba-410">傳送作業工作</span><span class="sxs-lookup"><span data-stu-id="760ba-410">Transfer Jobs Task</span></span>  
 <span data-ttu-id="760ba-411">`IfObjectExists`屬性：使用來自列舉的值進行設定 `IfObjectExists` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-411">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-412">IfObjectExists 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-412">Friendly Name in IfObjectExists</span></span>|<span data-ttu-id="760ba-413">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-413">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="760ba-414">FailTask</span><span class="sxs-lookup"><span data-stu-id="760ba-414">FailTask</span></span>|<span data-ttu-id="760ba-415">0</span><span class="sxs-lookup"><span data-stu-id="760ba-415">0</span></span>|  
|<span data-ttu-id="760ba-416">Overwrite</span><span class="sxs-lookup"><span data-stu-id="760ba-416">Overwrite</span></span>|<span data-ttu-id="760ba-417">1</span><span class="sxs-lookup"><span data-stu-id="760ba-417">1</span></span>|  
|<span data-ttu-id="760ba-418">Skip</span><span class="sxs-lookup"><span data-stu-id="760ba-418">Skip</span></span>|<span data-ttu-id="760ba-419">2</span><span class="sxs-lookup"><span data-stu-id="760ba-419">2</span></span>|  
  
### <a name="transfer-logins-task"></a><span data-ttu-id="760ba-420">傳送登入工作</span><span class="sxs-lookup"><span data-stu-id="760ba-420">Transfer Logins Task</span></span>  
 <span data-ttu-id="760ba-421">`IfObjectExists`屬性：使用來自列舉的值進行設定 `IfObjectExists` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-421">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-422">IfObjectExists 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-422">Friendly name in IfObjectExists</span></span>|<span data-ttu-id="760ba-423">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-423">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="760ba-424">FailTask</span><span class="sxs-lookup"><span data-stu-id="760ba-424">FailTask</span></span>|<span data-ttu-id="760ba-425">0</span><span class="sxs-lookup"><span data-stu-id="760ba-425">0</span></span>|  
|<span data-ttu-id="760ba-426">Overwrite</span><span class="sxs-lookup"><span data-stu-id="760ba-426">Overwrite</span></span>|<span data-ttu-id="760ba-427">1</span><span class="sxs-lookup"><span data-stu-id="760ba-427">1</span></span>|  
|<span data-ttu-id="760ba-428">Skip</span><span class="sxs-lookup"><span data-stu-id="760ba-428">Skip</span></span>|<span data-ttu-id="760ba-429">2</span><span class="sxs-lookup"><span data-stu-id="760ba-429">2</span></span>|  
  
 <span data-ttu-id="760ba-430">`LoginsToTransfer`屬性：使用來自列舉的值進行設定 `LoginsToTransfer` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-430">`LoginsToTransfer` property-Set by using values from the `LoginsToTransfer` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-431">LoginsToTransfer 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-431">Friendly name in LoginsToTransfer</span></span>|<span data-ttu-id="760ba-432">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-432">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="760ba-433">AllLogins</span><span class="sxs-lookup"><span data-stu-id="760ba-433">AllLogins</span></span>|<span data-ttu-id="760ba-434">0</span><span class="sxs-lookup"><span data-stu-id="760ba-434">0</span></span>|  
|<span data-ttu-id="760ba-435">SelectedLogins</span><span class="sxs-lookup"><span data-stu-id="760ba-435">SelectedLogins</span></span>|<span data-ttu-id="760ba-436">1</span><span class="sxs-lookup"><span data-stu-id="760ba-436">1</span></span>|  
|<span data-ttu-id="760ba-437">AllLoginsFromSelectedDatabases</span><span class="sxs-lookup"><span data-stu-id="760ba-437">AllLoginsFromSelectedDatabases</span></span>|<span data-ttu-id="760ba-438">2</span><span class="sxs-lookup"><span data-stu-id="760ba-438">2</span></span>|  
  
### <a name="transfer-master-stored-procedures-task"></a><span data-ttu-id="760ba-439">傳送主要預存程序工作</span><span class="sxs-lookup"><span data-stu-id="760ba-439">Transfer Master Stored Procedures Task</span></span>  
 <span data-ttu-id="760ba-440">`IfObjectExists`屬性：使用來自列舉的值進行設定 `IfObjectExists` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-440">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-441">IfObjectExists 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-441">Friendly name in IfObjectExists</span></span>|<span data-ttu-id="760ba-442">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-442">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="760ba-443">FailTask</span><span class="sxs-lookup"><span data-stu-id="760ba-443">FailTask</span></span>|<span data-ttu-id="760ba-444">0</span><span class="sxs-lookup"><span data-stu-id="760ba-444">0</span></span>|  
|<span data-ttu-id="760ba-445">Overwrite</span><span class="sxs-lookup"><span data-stu-id="760ba-445">Overwrite</span></span>|<span data-ttu-id="760ba-446">1</span><span class="sxs-lookup"><span data-stu-id="760ba-446">1</span></span>|  
|<span data-ttu-id="760ba-447">Skip</span><span class="sxs-lookup"><span data-stu-id="760ba-447">Skip</span></span>|<span data-ttu-id="760ba-448">2</span><span class="sxs-lookup"><span data-stu-id="760ba-448">2</span></span>|  
  
### <a name="transfer-sql-server-objects-task"></a><span data-ttu-id="760ba-449">傳送 SQL Server 物件工作</span><span class="sxs-lookup"><span data-stu-id="760ba-449">Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="760ba-450">`ExistingData`屬性：使用來自列舉的值進行設定 `ExistingData` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-450">`ExistingData` property-Set by using values from the `ExistingData` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-451">ExistingData 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-451">Friendly name in ExistingData</span></span>|<span data-ttu-id="760ba-452">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-452">Numeric Value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="760ba-453">Replace</span><span class="sxs-lookup"><span data-stu-id="760ba-453">Replace</span></span>|<span data-ttu-id="760ba-454">0</span><span class="sxs-lookup"><span data-stu-id="760ba-454">0</span></span>|  
|<span data-ttu-id="760ba-455">附加</span><span class="sxs-lookup"><span data-stu-id="760ba-455">Append</span></span>|<span data-ttu-id="760ba-456">1</span><span class="sxs-lookup"><span data-stu-id="760ba-456">1</span></span>|  
  
### <a name="web-service-task"></a><span data-ttu-id="760ba-457">Web 服務工作</span><span class="sxs-lookup"><span data-stu-id="760ba-457">Web Service Task</span></span>  
 <span data-ttu-id="760ba-458">`OutputType`屬性：使用來自列舉的值進行設定 `DTSOutputType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-458">`OutputType` property-Set by using values from the `DTSOutputType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-459">DTSOutputType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-459">Friendly name in DTSOutputType</span></span>|<span data-ttu-id="760ba-460">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-460">Numeric value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="760ba-461">檔案</span><span class="sxs-lookup"><span data-stu-id="760ba-461">File</span></span>|<span data-ttu-id="760ba-462">0</span><span class="sxs-lookup"><span data-stu-id="760ba-462">0</span></span>|  
|<span data-ttu-id="760ba-463">變數</span><span class="sxs-lookup"><span data-stu-id="760ba-463">Variable</span></span>|<span data-ttu-id="760ba-464">1</span><span class="sxs-lookup"><span data-stu-id="760ba-464">1</span></span>|  
  
### <a name="wmi-data-reader-task"></a><span data-ttu-id="760ba-465">WMI 資料讀取器工作</span><span class="sxs-lookup"><span data-stu-id="760ba-465">WMI Data Reader Task</span></span>  
 <span data-ttu-id="760ba-466">`OverwriteDestination`屬性：使用來自列舉的值進行設定 `OverwriteDestination` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-466">`OverwriteDestination` property-Set by using values from the `OverwriteDestination` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-467">OverwriteDestination 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-467">Friendly name in OverwriteDestination</span></span>|<span data-ttu-id="760ba-468">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-468">Numeric value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="760ba-469">OverwriteDestination</span><span class="sxs-lookup"><span data-stu-id="760ba-469">OverwriteDestination</span></span>|<span data-ttu-id="760ba-470">0</span><span class="sxs-lookup"><span data-stu-id="760ba-470">0</span></span>|  
|<span data-ttu-id="760ba-471">AppendToDestination</span><span class="sxs-lookup"><span data-stu-id="760ba-471">AppendToDestination</span></span>|<span data-ttu-id="760ba-472">1</span><span class="sxs-lookup"><span data-stu-id="760ba-472">1</span></span>|  
|<span data-ttu-id="760ba-473">KeepOriginal</span><span class="sxs-lookup"><span data-stu-id="760ba-473">KeepOriginal</span></span>|<span data-ttu-id="760ba-474">2</span><span class="sxs-lookup"><span data-stu-id="760ba-474">2</span></span>|  
  
 <span data-ttu-id="760ba-475">`OutputType`屬性：使用來自列舉的值進行設定 `OutputType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-475">`OutputType` property-Set by using values from the `OutputType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-476">OutputType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-476">Friendly name in OutputType</span></span>|<span data-ttu-id="760ba-477">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-477">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="760ba-478">DataTable</span><span class="sxs-lookup"><span data-stu-id="760ba-478">DataTable</span></span>|<span data-ttu-id="760ba-479">0</span><span class="sxs-lookup"><span data-stu-id="760ba-479">0</span></span>|  
|<span data-ttu-id="760ba-480">PropertyValue</span><span class="sxs-lookup"><span data-stu-id="760ba-480">PropertyValue</span></span>|<span data-ttu-id="760ba-481">1</span><span class="sxs-lookup"><span data-stu-id="760ba-481">1</span></span>|  
|<span data-ttu-id="760ba-482">PropertyNameAndValue</span><span class="sxs-lookup"><span data-stu-id="760ba-482">PropertyNameAndValue</span></span>|<span data-ttu-id="760ba-483">2</span><span class="sxs-lookup"><span data-stu-id="760ba-483">2</span></span>|  
  
 <span data-ttu-id="760ba-484">`DestinationType`屬性：使用來自列舉的值進行設定 `DestinationType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-484">`DestinationType` property-Set by using values from the `DestinationType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-485">DestinationType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-485">Friendly name in DestinationType</span></span>|<span data-ttu-id="760ba-486">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-486">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="760ba-487">FileConnection</span><span class="sxs-lookup"><span data-stu-id="760ba-487">FileConnection</span></span>|<span data-ttu-id="760ba-488">0</span><span class="sxs-lookup"><span data-stu-id="760ba-488">0</span></span>|  
|<span data-ttu-id="760ba-489">變數</span><span class="sxs-lookup"><span data-stu-id="760ba-489">Variable</span></span>|<span data-ttu-id="760ba-490">1</span><span class="sxs-lookup"><span data-stu-id="760ba-490">1</span></span>|  
  
 <span data-ttu-id="760ba-491">`WqlQuerySourceType`屬性：使用來自列舉的值進行設定 `QuerySourceType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-491">`WqlQuerySourceType` property-Set by using values from the `QuerySourceType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-492">QuerySourceType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-492">Friendly Name in QuerySourceType</span></span>|<span data-ttu-id="760ba-493">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-493">Numeric Value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="760ba-494">FileConnection</span><span class="sxs-lookup"><span data-stu-id="760ba-494">FileConnection</span></span>|<span data-ttu-id="760ba-495">0</span><span class="sxs-lookup"><span data-stu-id="760ba-495">0</span></span>|  
|<span data-ttu-id="760ba-496">DirectInput</span><span class="sxs-lookup"><span data-stu-id="760ba-496">DirectInput</span></span>|<span data-ttu-id="760ba-497">1</span><span class="sxs-lookup"><span data-stu-id="760ba-497">1</span></span>|  
|<span data-ttu-id="760ba-498">變數</span><span class="sxs-lookup"><span data-stu-id="760ba-498">Variable</span></span>|<span data-ttu-id="760ba-499">2</span><span class="sxs-lookup"><span data-stu-id="760ba-499">2</span></span>|  
  
 <span data-ttu-id="760ba-500">WMI 事件監看員 `ActionAtEvent` 屬性：使用來自列舉的值進行設定 `ActionAtEvent` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-500">WMI Event Watcher `ActionAtEvent` property-Set by using values from the `ActionAtEvent` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-501">ActionAtEvent 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-501">Friendly Name in ActionAtEvent</span></span>|<span data-ttu-id="760ba-502">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-502">Numeric Value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="760ba-503">LogTheEventAndFireDTSEvent</span><span class="sxs-lookup"><span data-stu-id="760ba-503">LogTheEventAndFireDTSEvent</span></span>|<span data-ttu-id="760ba-504">0</span><span class="sxs-lookup"><span data-stu-id="760ba-504">0</span></span>|  
|<span data-ttu-id="760ba-505">LogTheEvent</span><span class="sxs-lookup"><span data-stu-id="760ba-505">LogTheEvent</span></span>|<span data-ttu-id="760ba-506">1</span><span class="sxs-lookup"><span data-stu-id="760ba-506">1</span></span>|  
  
 <span data-ttu-id="760ba-507">`ActionAtTimeout`屬性：使用來自列舉的值進行設定 `ActionAtTimeout` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-507">`ActionAtTimeout` property-Set by using values from the `ActionAtTimeout` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-508">ActionAtTimeout 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-508">Friendly name in ActionAtTimeout</span></span>|<span data-ttu-id="760ba-509">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-509">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="760ba-510">LogTimeoutAndFireDTSEvent</span><span class="sxs-lookup"><span data-stu-id="760ba-510">LogTimeoutAndFireDTSEvent</span></span>|<span data-ttu-id="760ba-511">0</span><span class="sxs-lookup"><span data-stu-id="760ba-511">0</span></span>|  
|<span data-ttu-id="760ba-512">LogTimeout</span><span class="sxs-lookup"><span data-stu-id="760ba-512">LogTimeout</span></span>|<span data-ttu-id="760ba-513">1</span><span class="sxs-lookup"><span data-stu-id="760ba-513">1</span></span>|  
  
 <span data-ttu-id="760ba-514">`AfterEvent`屬性：使用來自列舉的值進行設定 `AfterEvent` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-514">`AfterEvent` property-Set by using values from the `AfterEvent` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-515">AfterEvent 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-515">Friendly name in AfterEvent</span></span>|<span data-ttu-id="760ba-516">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-516">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="760ba-517">ReturnWithSuccess</span><span class="sxs-lookup"><span data-stu-id="760ba-517">ReturnWithSuccess</span></span>|<span data-ttu-id="760ba-518">0</span><span class="sxs-lookup"><span data-stu-id="760ba-518">0</span></span>|  
|<span data-ttu-id="760ba-519">ReturnWithFailure</span><span class="sxs-lookup"><span data-stu-id="760ba-519">ReturnWithFailure</span></span>|<span data-ttu-id="760ba-520">1</span><span class="sxs-lookup"><span data-stu-id="760ba-520">1</span></span>|  
|<span data-ttu-id="760ba-521">WatchfortheEventAgain</span><span class="sxs-lookup"><span data-stu-id="760ba-521">WatchfortheEventAgain</span></span>|<span data-ttu-id="760ba-522">2</span><span class="sxs-lookup"><span data-stu-id="760ba-522">2</span></span>|  
  
 <span data-ttu-id="760ba-523">`AfterTimeout`屬性：使用來自列舉的值進行設定 `AfterTimeout` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-523">`AfterTimeout` property-Set by using values from the `AfterTimeout` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-524">AfterTimeout 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-524">Friendly name in AfterTimeout</span></span>|<span data-ttu-id="760ba-525">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-525">Numeric value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="760ba-526">ReturnWithSuccess</span><span class="sxs-lookup"><span data-stu-id="760ba-526">ReturnWithSuccess</span></span>|<span data-ttu-id="760ba-527">0</span><span class="sxs-lookup"><span data-stu-id="760ba-527">0</span></span>|  
|<span data-ttu-id="760ba-528">ReturnWithFailure</span><span class="sxs-lookup"><span data-stu-id="760ba-528">ReturnWithFailure</span></span>|<span data-ttu-id="760ba-529">1</span><span class="sxs-lookup"><span data-stu-id="760ba-529">1</span></span>|  
|<span data-ttu-id="760ba-530">WatchfortheEventAgain</span><span class="sxs-lookup"><span data-stu-id="760ba-530">WatchfortheEventAgain</span></span>|<span data-ttu-id="760ba-531">2</span><span class="sxs-lookup"><span data-stu-id="760ba-531">2</span></span>|  
  
 <span data-ttu-id="760ba-532">`WqlQuerySourceType`屬性：使用來自列舉的值進行設定 `QuerySourceType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-532">`WqlQuerySourceType` property-Set by using values from the `QuerySourceType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-533">QuerySourceType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-533">Friendly name in QuerySourceType</span></span>|<span data-ttu-id="760ba-534">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-534">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="760ba-535">FileConnection</span><span class="sxs-lookup"><span data-stu-id="760ba-535">FileConnection</span></span>|<span data-ttu-id="760ba-536">0</span><span class="sxs-lookup"><span data-stu-id="760ba-536">0</span></span>|  
|<span data-ttu-id="760ba-537">DirectInput</span><span class="sxs-lookup"><span data-stu-id="760ba-537">DirectInput</span></span>|<span data-ttu-id="760ba-538">1</span><span class="sxs-lookup"><span data-stu-id="760ba-538">1</span></span>|  
|<span data-ttu-id="760ba-539">變數</span><span class="sxs-lookup"><span data-stu-id="760ba-539">Variable</span></span>|<span data-ttu-id="760ba-540">2</span><span class="sxs-lookup"><span data-stu-id="760ba-540">2</span></span>|  
  
### <a name="xml-task"></a><span data-ttu-id="760ba-541">XML 工作</span><span class="sxs-lookup"><span data-stu-id="760ba-541">XML Task</span></span>  
 <span data-ttu-id="760ba-542">`OperationType`屬性：使用來自列舉的值進行設定 `DTSXMLOperation` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-542">`OperationType` property-Set by using values from the `DTSXMLOperation` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-543">DTSXMLOperation 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-543">Friendly name in DTSXMLOperation</span></span>|<span data-ttu-id="760ba-544">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-544">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="760ba-545">Validate</span><span class="sxs-lookup"><span data-stu-id="760ba-545">Validate</span></span>|<span data-ttu-id="760ba-546">0</span><span class="sxs-lookup"><span data-stu-id="760ba-546">0</span></span>|  
|<span data-ttu-id="760ba-547">XSLT</span><span class="sxs-lookup"><span data-stu-id="760ba-547">XSLT</span></span>|<span data-ttu-id="760ba-548">1</span><span class="sxs-lookup"><span data-stu-id="760ba-548">1</span></span>|  
|<span data-ttu-id="760ba-549">XPATH</span><span class="sxs-lookup"><span data-stu-id="760ba-549">XPATH</span></span>|<span data-ttu-id="760ba-550">2</span><span class="sxs-lookup"><span data-stu-id="760ba-550">2</span></span>|  
|<span data-ttu-id="760ba-551">合併</span><span class="sxs-lookup"><span data-stu-id="760ba-551">Merge</span></span>|<span data-ttu-id="760ba-552">3</span><span class="sxs-lookup"><span data-stu-id="760ba-552">3</span></span>|  
|<span data-ttu-id="760ba-553">Diff</span><span class="sxs-lookup"><span data-stu-id="760ba-553">Diff</span></span>|<span data-ttu-id="760ba-554">4</span><span class="sxs-lookup"><span data-stu-id="760ba-554">4</span></span>|  
|<span data-ttu-id="760ba-555">Patch</span><span class="sxs-lookup"><span data-stu-id="760ba-555">Patch</span></span>|<span data-ttu-id="760ba-556">5</span><span class="sxs-lookup"><span data-stu-id="760ba-556">5</span></span>|  
  
 <span data-ttu-id="760ba-557">`SourceType`、 `SecondOperandType` 和 `XPathSourceType` 屬性：使用來自列舉的值進行設定 `DTSXMLSourceType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-557">`SourceType`, `SecondOperandType`, and `XPathSourceType` properties-Set by using values from the `DTSXMLSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-558">DTSXMLSourceType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-558">Friendly name in DTSXMLSourceType</span></span>|<span data-ttu-id="760ba-559">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-559">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="760ba-560">FileConnection</span><span class="sxs-lookup"><span data-stu-id="760ba-560">FileConnection</span></span>|<span data-ttu-id="760ba-561">0</span><span class="sxs-lookup"><span data-stu-id="760ba-561">0</span></span>|  
|<span data-ttu-id="760ba-562">變數</span><span class="sxs-lookup"><span data-stu-id="760ba-562">Variable</span></span>|<span data-ttu-id="760ba-563">1</span><span class="sxs-lookup"><span data-stu-id="760ba-563">1</span></span>|  
|<span data-ttu-id="760ba-564">DirectInput</span><span class="sxs-lookup"><span data-stu-id="760ba-564">DirectInput</span></span>|<span data-ttu-id="760ba-565">2</span><span class="sxs-lookup"><span data-stu-id="760ba-565">2</span></span>|  
  
 <span data-ttu-id="760ba-566">`DestinationType`和**DiffGramDestinationType**屬性：使用來自列舉的值進行設定 `DTSXMLSaveResultTo` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-566">`DestinationType` and **DiffGramDestinationType** properties-Set by using values from the `DTSXMLSaveResultTo` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-567">DTSXMLSaveResultTo 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-567">Friendly name in DTSXMLSaveResultTo</span></span>|<span data-ttu-id="760ba-568">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-568">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="760ba-569">FileConnection</span><span class="sxs-lookup"><span data-stu-id="760ba-569">FileConnection</span></span>|<span data-ttu-id="760ba-570">0</span><span class="sxs-lookup"><span data-stu-id="760ba-570">0</span></span>|  
|<span data-ttu-id="760ba-571">變數</span><span class="sxs-lookup"><span data-stu-id="760ba-571">Variable</span></span>|<span data-ttu-id="760ba-572">1</span><span class="sxs-lookup"><span data-stu-id="760ba-572">1</span></span>|  
  
 <span data-ttu-id="760ba-573">`ValidationType`屬性：使用來自列舉的值進行設定 `DTSXMLValidationType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-573">`ValidationType` property-Set by using values from the `DTSXMLValidationType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-574">DTSXMLValidationType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-574">Friendly name in DTSXMLValidationType</span></span>|<span data-ttu-id="760ba-575">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-575">Numeric value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="760ba-576">DTD</span><span class="sxs-lookup"><span data-stu-id="760ba-576">DTD</span></span>|<span data-ttu-id="760ba-577">0</span><span class="sxs-lookup"><span data-stu-id="760ba-577">0</span></span>|  
|<span data-ttu-id="760ba-578">XSD</span><span class="sxs-lookup"><span data-stu-id="760ba-578">XSD</span></span>|<span data-ttu-id="760ba-579">1</span><span class="sxs-lookup"><span data-stu-id="760ba-579">1</span></span>|  
  
 <span data-ttu-id="760ba-580">`XPathOperation`屬性：使用來自列舉的值進行設定 `DTSXMLXPathOperation` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-580">`XPathOperation` property-Set by using values from the `DTSXMLXPathOperation` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-581">DTSXMLXPathOperation 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-581">Friendly name in DTSXMLXPathOperation</span></span>|<span data-ttu-id="760ba-582">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-582">Numeric Value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="760ba-583">評估</span><span class="sxs-lookup"><span data-stu-id="760ba-583">Evaluation</span></span>|<span data-ttu-id="760ba-584">0</span><span class="sxs-lookup"><span data-stu-id="760ba-584">0</span></span>|  
|<span data-ttu-id="760ba-585">值</span><span class="sxs-lookup"><span data-stu-id="760ba-585">Values</span></span>|<span data-ttu-id="760ba-586">1</span><span class="sxs-lookup"><span data-stu-id="760ba-586">1</span></span>|  
|<span data-ttu-id="760ba-587">NodeList</span><span class="sxs-lookup"><span data-stu-id="760ba-587">NodeList</span></span>|<span data-ttu-id="760ba-588">2</span><span class="sxs-lookup"><span data-stu-id="760ba-588">2</span></span>|  
  
 <span data-ttu-id="760ba-589">`DiffOptions`屬性：使用來自列舉的值進行設定 `DTSXMLDiffOptions` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-589">`DiffOptions` property-Set by using values from the `DTSXMLDiffOptions` enumeration.</span></span> <span data-ttu-id="760ba-590">此列舉值中的選項不會互斥。</span><span class="sxs-lookup"><span data-stu-id="760ba-590">The options in this enumerator are not mutually exclusive.</span></span> <span data-ttu-id="760ba-591">若要使用多個選項，請提供要套用之選項的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="760ba-591">To use multiple options, provide a comma-separated list of the options to apply.</span></span>  
  
|<span data-ttu-id="760ba-592">DTSXMLDiffOptions 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-592">Friendly name in DTSXMLDiffOptions</span></span>|<span data-ttu-id="760ba-593">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-593">Numeric Value</span></span>|  
|----------------------------------------|-------------------|  
|<span data-ttu-id="760ba-594">None</span><span class="sxs-lookup"><span data-stu-id="760ba-594">None</span></span>|<span data-ttu-id="760ba-595">0</span><span class="sxs-lookup"><span data-stu-id="760ba-595">0</span></span>|  
|<span data-ttu-id="760ba-596">IgnoreChildOrder</span><span class="sxs-lookup"><span data-stu-id="760ba-596">IgnoreChildOrder</span></span>|<span data-ttu-id="760ba-597">1</span><span class="sxs-lookup"><span data-stu-id="760ba-597">1</span></span>|  
|<span data-ttu-id="760ba-598">IgnoreComments</span><span class="sxs-lookup"><span data-stu-id="760ba-598">IgnoreComments</span></span>|<span data-ttu-id="760ba-599">2</span><span class="sxs-lookup"><span data-stu-id="760ba-599">2</span></span>|  
|<span data-ttu-id="760ba-600">IgnorePI</span><span class="sxs-lookup"><span data-stu-id="760ba-600">IgnorePI</span></span>|<span data-ttu-id="760ba-601">4</span><span class="sxs-lookup"><span data-stu-id="760ba-601">4</span></span>|  
|<span data-ttu-id="760ba-602">IgnoreWhitespace</span><span class="sxs-lookup"><span data-stu-id="760ba-602">IgnoreWhitespace</span></span>|<span data-ttu-id="760ba-603">8</span><span class="sxs-lookup"><span data-stu-id="760ba-603">8</span></span>|  
|<span data-ttu-id="760ba-604">IgnoreNamespaces</span><span class="sxs-lookup"><span data-stu-id="760ba-604">IgnoreNamespaces</span></span>|<span data-ttu-id="760ba-605">16</span><span class="sxs-lookup"><span data-stu-id="760ba-605">16</span></span>|  
|<span data-ttu-id="760ba-606">IgnorePrefixes</span><span class="sxs-lookup"><span data-stu-id="760ba-606">IgnorePrefixes</span></span>|<span data-ttu-id="760ba-607">32</span><span class="sxs-lookup"><span data-stu-id="760ba-607">32</span></span>|  
|<span data-ttu-id="760ba-608">IgnoreXmlDecl</span><span class="sxs-lookup"><span data-stu-id="760ba-608">IgnoreXmlDecl</span></span>|<span data-ttu-id="760ba-609">64</span><span class="sxs-lookup"><span data-stu-id="760ba-609">64</span></span>|  
|<span data-ttu-id="760ba-610">IgnoreDtd</span><span class="sxs-lookup"><span data-stu-id="760ba-610">IgnoreDtd</span></span>|<span data-ttu-id="760ba-611">128</span><span class="sxs-lookup"><span data-stu-id="760ba-611">128</span></span>|  
  
 <span data-ttu-id="760ba-612">`DiffAlgorithm`屬性：使用來自列舉的值進行設定 `DTSXMLDiffAlgorithm` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-612">`DiffAlgorithm` property-Set by using values from the `DTSXMLDiffAlgorithm` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-613">DTSXMLDiffAlgorithm 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-613">Friendly name in DTSXMLDiffAlgorithm</span></span>|<span data-ttu-id="760ba-614">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-614">Numeric value</span></span>|  
|------------------------------------------|-------------------|  
|<span data-ttu-id="760ba-615">Auto</span><span class="sxs-lookup"><span data-stu-id="760ba-615">Auto</span></span>|<span data-ttu-id="760ba-616">0</span><span class="sxs-lookup"><span data-stu-id="760ba-616">0</span></span>|  
|<span data-ttu-id="760ba-617">快速</span><span class="sxs-lookup"><span data-stu-id="760ba-617">Fast</span></span>|<span data-ttu-id="760ba-618">1</span><span class="sxs-lookup"><span data-stu-id="760ba-618">1</span></span>|  
|<span data-ttu-id="760ba-619">精確</span><span class="sxs-lookup"><span data-stu-id="760ba-619">Precise</span></span>|<span data-ttu-id="760ba-620">2</span><span class="sxs-lookup"><span data-stu-id="760ba-620">2</span></span>|  
  
##  <a name="maintenance-plan-tasks"></a><a name="MaintenancePlanTasks"></a> <span data-ttu-id="760ba-621">維護計畫工作</span><span class="sxs-lookup"><span data-stu-id="760ba-621">Maintenance Plan Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="760ba-622">包含一組工作，用以執行要在維護計畫和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝中使用的 SQL Server 工作。</span><span class="sxs-lookup"><span data-stu-id="760ba-622">includes a set of tasks that perform SQL Server tasks for use in maintenance plans and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="760ba-623">不支援以程式設計方式處理這些工作，而且程式設計參考文件集也不包括這些工作及其列舉值的 API 文件集。</span><span class="sxs-lookup"><span data-stu-id="760ba-623">does not support working with these tasks programmatically and programming reference documentation does not include API documentation of these tasks and their enumerators.</span></span>  
  
### <a name="all-maintenance-tasks"></a><span data-ttu-id="760ba-624">所有維護工作</span><span class="sxs-lookup"><span data-stu-id="760ba-624">All Maintenance Tasks</span></span>  
 <span data-ttu-id="760ba-625">所有維護工作都使用下列列舉來設定指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="760ba-625">All maintenance tasks use the following enumerations to set the specified properties.</span></span>  
  
 <span data-ttu-id="760ba-626">`DatabaseSelectionType`屬性：使用來自列舉的值進行設定 `DatabaseSelection` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-626">`DatabaseSelectionType` property-Set by using values from the `DatabaseSelection` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-627">DatabaseSelection 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-627">Friendly name in DatabaseSelection</span></span>|<span data-ttu-id="760ba-628">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-628">Numeric value</span></span>|  
|----------------------------------------|-------------------|  
|<span data-ttu-id="760ba-629">None</span><span class="sxs-lookup"><span data-stu-id="760ba-629">None</span></span>|<span data-ttu-id="760ba-630">0</span><span class="sxs-lookup"><span data-stu-id="760ba-630">0</span></span>|  
|<span data-ttu-id="760ba-631">全部</span><span class="sxs-lookup"><span data-stu-id="760ba-631">All</span></span>|<span data-ttu-id="760ba-632">1</span><span class="sxs-lookup"><span data-stu-id="760ba-632">1</span></span>|  
|<span data-ttu-id="760ba-633">系統</span><span class="sxs-lookup"><span data-stu-id="760ba-633">System</span></span>|<span data-ttu-id="760ba-634">2</span><span class="sxs-lookup"><span data-stu-id="760ba-634">2</span></span>|  
|<span data-ttu-id="760ba-635">User</span><span class="sxs-lookup"><span data-stu-id="760ba-635">User</span></span>|<span data-ttu-id="760ba-636">3</span><span class="sxs-lookup"><span data-stu-id="760ba-636">3</span></span>|  
|<span data-ttu-id="760ba-637">特定</span><span class="sxs-lookup"><span data-stu-id="760ba-637">Specific</span></span>|<span data-ttu-id="760ba-638">4</span><span class="sxs-lookup"><span data-stu-id="760ba-638">4</span></span>|  
  
 <span data-ttu-id="760ba-639">`TableSelectionType`屬性：使用來自列舉的值進行設定 `TableSelection` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-639">`TableSelectionType` property-Set by using values from the `TableSelection` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-640">TableSelection 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-640">Friendly name in TableSelection</span></span>|<span data-ttu-id="760ba-641">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-641">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="760ba-642">None</span><span class="sxs-lookup"><span data-stu-id="760ba-642">None</span></span>|<span data-ttu-id="760ba-643">0</span><span class="sxs-lookup"><span data-stu-id="760ba-643">0</span></span>|  
|<span data-ttu-id="760ba-644">全部</span><span class="sxs-lookup"><span data-stu-id="760ba-644">All</span></span>|<span data-ttu-id="760ba-645">1</span><span class="sxs-lookup"><span data-stu-id="760ba-645">1</span></span>|  
|<span data-ttu-id="760ba-646">特定</span><span class="sxs-lookup"><span data-stu-id="760ba-646">Specific</span></span>|<span data-ttu-id="760ba-647">2</span><span class="sxs-lookup"><span data-stu-id="760ba-647">2</span></span>|  
  
 <span data-ttu-id="760ba-648">`ObjectTypeSelection`屬性：使用來自列舉的值進行設定 `ObjectType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-648">`ObjectTypeSelection` property-Set by using values from the `ObjectType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-649">ObjectType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-649">Friendly name in ObjectType</span></span>|<span data-ttu-id="760ba-650">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-650">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="760ba-651">Table</span><span class="sxs-lookup"><span data-stu-id="760ba-651">Table</span></span>|<span data-ttu-id="760ba-652">0</span><span class="sxs-lookup"><span data-stu-id="760ba-652">0</span></span>|  
|<span data-ttu-id="760ba-653">檢視</span><span class="sxs-lookup"><span data-stu-id="760ba-653">View</span></span>|<span data-ttu-id="760ba-654">1</span><span class="sxs-lookup"><span data-stu-id="760ba-654">1</span></span>|  
|<span data-ttu-id="760ba-655">TableView</span><span class="sxs-lookup"><span data-stu-id="760ba-655">TableView</span></span>|<span data-ttu-id="760ba-656">2</span><span class="sxs-lookup"><span data-stu-id="760ba-656">2</span></span>|  
  
### <a name="back-up-database-task"></a><span data-ttu-id="760ba-657">備份資料庫工作</span><span class="sxs-lookup"><span data-stu-id="760ba-657">Back Up Database Task</span></span>  
 <span data-ttu-id="760ba-658">`DestinationCreationType`屬性：使用來自列舉的值進行設定 `DestinationType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-658">`DestinationCreationType` property-Set by using values from the `DestinationType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-659">DestinationType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-659">Friendly name in DestinationType</span></span>|<span data-ttu-id="760ba-660">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-660">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="760ba-661">Auto</span><span class="sxs-lookup"><span data-stu-id="760ba-661">Auto</span></span>|<span data-ttu-id="760ba-662">0</span><span class="sxs-lookup"><span data-stu-id="760ba-662">0</span></span>|  
|<span data-ttu-id="760ba-663">手動</span><span class="sxs-lookup"><span data-stu-id="760ba-663">Manual</span></span>|<span data-ttu-id="760ba-664">1</span><span class="sxs-lookup"><span data-stu-id="760ba-664">1</span></span>|  
  
 <span data-ttu-id="760ba-665">`ExistingBackupsAction`屬性：使用來自列舉的值進行設定 `ActionForExistingBackups` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-665">`ExistingBackupsAction` property-Set by using values from the `ActionForExistingBackups` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-666">ActionForExistingBackups 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-666">Friendly name in ActionForExistingBackups</span></span>|<span data-ttu-id="760ba-667">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-667">Numeric value</span></span>|  
|-----------------------------------------------|-------------------|  
|<span data-ttu-id="760ba-668">附加</span><span class="sxs-lookup"><span data-stu-id="760ba-668">Append</span></span>|<span data-ttu-id="760ba-669">0</span><span class="sxs-lookup"><span data-stu-id="760ba-669">0</span></span>|  
|<span data-ttu-id="760ba-670">Overwrite</span><span class="sxs-lookup"><span data-stu-id="760ba-670">Overwrite</span></span>|<span data-ttu-id="760ba-671">1</span><span class="sxs-lookup"><span data-stu-id="760ba-671">1</span></span>|  
  
 <span data-ttu-id="760ba-672">`BackupAction`屬性：使用來自列舉的值進行設定 `BackupTaskType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-672">`BackupAction` property-Set by using values from the `BackupTaskType` enumeration.</span></span> <span data-ttu-id="760ba-673">此屬性可搭配 `BackupIsIncremental` 屬性使用，以定義工作執行的備份類型。</span><span class="sxs-lookup"><span data-stu-id="760ba-673">This property works with the `BackupIsIncremental` property to define the type of backup that the task performs.</span></span>  
  
|<span data-ttu-id="760ba-674">BackupTaskType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-674">Friendly name in BackupTaskType</span></span>|<span data-ttu-id="760ba-675">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-675">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="760ba-676">資料庫</span><span class="sxs-lookup"><span data-stu-id="760ba-676">Database</span></span>|<span data-ttu-id="760ba-677">0</span><span class="sxs-lookup"><span data-stu-id="760ba-677">0</span></span>|  
|<span data-ttu-id="760ba-678">檔案</span><span class="sxs-lookup"><span data-stu-id="760ba-678">Files</span></span>|<span data-ttu-id="760ba-679">1</span><span class="sxs-lookup"><span data-stu-id="760ba-679">1</span></span>|  
|<span data-ttu-id="760ba-680">Log</span><span class="sxs-lookup"><span data-stu-id="760ba-680">Log</span></span>|<span data-ttu-id="760ba-681">2</span><span class="sxs-lookup"><span data-stu-id="760ba-681">2</span></span>|  
  
 <span data-ttu-id="760ba-682">`BackupDevice`屬性：使用來自管理物件的值 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SMO) 列舉進行設定 `DeviceType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-682">`BackupDevice` property-Set by using values from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) `DeviceType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-683">DeviceType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-683">Friendly name in DeviceType</span></span>|<span data-ttu-id="760ba-684">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-684">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="760ba-685">LogicalDevice</span><span class="sxs-lookup"><span data-stu-id="760ba-685">LogicalDevice</span></span>|<span data-ttu-id="760ba-686">0</span><span class="sxs-lookup"><span data-stu-id="760ba-686">0</span></span>|  
|<span data-ttu-id="760ba-687">磁帶</span><span class="sxs-lookup"><span data-stu-id="760ba-687">Tape</span></span>|<span data-ttu-id="760ba-688">1</span><span class="sxs-lookup"><span data-stu-id="760ba-688">1</span></span>|  
|<span data-ttu-id="760ba-689">檔案</span><span class="sxs-lookup"><span data-stu-id="760ba-689">File</span></span>|<span data-ttu-id="760ba-690">2</span><span class="sxs-lookup"><span data-stu-id="760ba-690">2</span></span>|  
|<span data-ttu-id="760ba-691">Pipe</span><span class="sxs-lookup"><span data-stu-id="760ba-691">Pipe</span></span>|<span data-ttu-id="760ba-692">3</span><span class="sxs-lookup"><span data-stu-id="760ba-692">3</span></span>|  
|<span data-ttu-id="760ba-693">VirtualDevice</span><span class="sxs-lookup"><span data-stu-id="760ba-693">VirtualDevice</span></span>|<span data-ttu-id="760ba-694">4</span><span class="sxs-lookup"><span data-stu-id="760ba-694">4</span></span>|  
  
### <a name="maintenance-cleanup-task"></a><span data-ttu-id="760ba-695">維護清除工作</span><span class="sxs-lookup"><span data-stu-id="760ba-695">Maintenance Cleanup Task</span></span>  
 <span data-ttu-id="760ba-696">`FileTypeSelected`屬性：使用來自列舉的值進行設定 `FileType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-696">`FileTypeSelected` property-Set by using values from the `FileType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-697">FileType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-697">Friendly name in FileType</span></span>|<span data-ttu-id="760ba-698">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-698">Numeric value</span></span>|  
|-------------------------------|-------------------|  
|<span data-ttu-id="760ba-699">FileBackup</span><span class="sxs-lookup"><span data-stu-id="760ba-699">FileBackup</span></span>|<span data-ttu-id="760ba-700">0</span><span class="sxs-lookup"><span data-stu-id="760ba-700">0</span></span>|  
|<span data-ttu-id="760ba-701">FileReport</span><span class="sxs-lookup"><span data-stu-id="760ba-701">FileReport</span></span>|<span data-ttu-id="760ba-702">1</span><span class="sxs-lookup"><span data-stu-id="760ba-702">1</span></span>|  
  
 <span data-ttu-id="760ba-703">`OlderThanTimeUnitType`屬性：使用來自列舉的值進行設定 `TimeUnitType` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-703">`OlderThanTimeUnitType` property-Set by using values from the `TimeUnitType` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-704">TimeUnitType 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-704">Friendly Name in TimeUnitType</span></span>|<span data-ttu-id="760ba-705">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-705">Numeric Value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="760ba-706">Day</span><span class="sxs-lookup"><span data-stu-id="760ba-706">Day</span></span>|<span data-ttu-id="760ba-707">0</span><span class="sxs-lookup"><span data-stu-id="760ba-707">0</span></span>|  
|<span data-ttu-id="760ba-708">週</span><span class="sxs-lookup"><span data-stu-id="760ba-708">Week</span></span>|<span data-ttu-id="760ba-709">1</span><span class="sxs-lookup"><span data-stu-id="760ba-709">1</span></span>|  
|<span data-ttu-id="760ba-710">Month</span><span class="sxs-lookup"><span data-stu-id="760ba-710">Month</span></span>|<span data-ttu-id="760ba-711">2</span><span class="sxs-lookup"><span data-stu-id="760ba-711">2</span></span>|  
|<span data-ttu-id="760ba-712">Year</span><span class="sxs-lookup"><span data-stu-id="760ba-712">Year</span></span>|<span data-ttu-id="760ba-713">3</span><span class="sxs-lookup"><span data-stu-id="760ba-713">3</span></span>|  
  
### <a name="update-statistics-task"></a><span data-ttu-id="760ba-714">更新統計資料工作</span><span class="sxs-lookup"><span data-stu-id="760ba-714">Update Statistics Task</span></span>  
 <span data-ttu-id="760ba-715">`UpdateType`屬性：使用來自管理物件的值 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SMO) 列舉進行設定 `StatisticsTarget` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-715">`UpdateType` property-Set by using values from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) `StatisticsTarget` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-716">StatisticsTarget 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-716">Friendly name in StatisticsTarget</span></span>|<span data-ttu-id="760ba-717">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-717">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="760ba-718">資料行</span><span class="sxs-lookup"><span data-stu-id="760ba-718">Column</span></span>|<span data-ttu-id="760ba-719">1</span><span class="sxs-lookup"><span data-stu-id="760ba-719">1</span></span>|  
|<span data-ttu-id="760ba-720">索引</span><span class="sxs-lookup"><span data-stu-id="760ba-720">Index</span></span>|<span data-ttu-id="760ba-721">2</span><span class="sxs-lookup"><span data-stu-id="760ba-721">2</span></span>|  
|<span data-ttu-id="760ba-722">全部</span><span class="sxs-lookup"><span data-stu-id="760ba-722">All</span></span>|<span data-ttu-id="760ba-723">3</span><span class="sxs-lookup"><span data-stu-id="760ba-723">3</span></span>|  
  
##  <a name="common-properties"></a><a name="CommonProperties"></a> <span data-ttu-id="760ba-724">通用屬性</span><span class="sxs-lookup"><span data-stu-id="760ba-724">Common Properties</span></span>  
 <span data-ttu-id="760ba-725">封裝、工作以及「Foreach 迴圈」、「For 迴圈」和「時序」等容器可以使用下列列舉來設定指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="760ba-725">Packages, tasks, and the Foreach Loop, For Loop, and Sequence containers can use the following enumerations to set the specified properties.</span></span>  
  
 <span data-ttu-id="760ba-726">`ForceExecutionResult`屬性：使用來自列舉的值進行設定 `DTSForcedExecResult` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-726">`ForceExecutionResult` property-Set by using values from the `DTSForcedExecResult` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-727">DTSForcedExecResult 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-727">Friendly name in DTSForcedExecResult</span></span>|<span data-ttu-id="760ba-728">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-728">Numeric value</span></span>|  
|------------------------------------------|-------------------|  
|<span data-ttu-id="760ba-729">None</span><span class="sxs-lookup"><span data-stu-id="760ba-729">None</span></span>|<span data-ttu-id="760ba-730">-1</span><span class="sxs-lookup"><span data-stu-id="760ba-730">-1</span></span>|  
|<span data-ttu-id="760ba-731">Success</span><span class="sxs-lookup"><span data-stu-id="760ba-731">Success</span></span>|<span data-ttu-id="760ba-732">0</span><span class="sxs-lookup"><span data-stu-id="760ba-732">0</span></span>|  
|<span data-ttu-id="760ba-733">失敗</span><span class="sxs-lookup"><span data-stu-id="760ba-733">Failure</span></span>|<span data-ttu-id="760ba-734">1</span><span class="sxs-lookup"><span data-stu-id="760ba-734">1</span></span>|  
|<span data-ttu-id="760ba-735">Completion</span><span class="sxs-lookup"><span data-stu-id="760ba-735">Completion</span></span>|<span data-ttu-id="760ba-736">2</span><span class="sxs-lookup"><span data-stu-id="760ba-736">2</span></span>|  
  
 <span data-ttu-id="760ba-737">`IsolationLevel`屬性-由 .NET Framework 列舉所設定 `IsolationLevel` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-737">`IsolationLevel` property-Set by the .NET Framework `IsolationLevel` enumeration.</span></span> <span data-ttu-id="760ba-738">如需詳細資訊，請參閱 [MSDN Library](https://go.microsoft.com/fwlink?LinkId=17313)中的＜.NET Framework 類別庫＞。</span><span class="sxs-lookup"><span data-stu-id="760ba-738">For more information, see the .NET Framework Class Library in the [MSDN Library](https://go.microsoft.com/fwlink?LinkId=17313).</span></span>  
  
 <span data-ttu-id="760ba-739">`LoggingMode`屬性：使用來自列舉的值進行設定 `DTSLoggingMode` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-739">`LoggingMode` property-Set by using values from the `DTSLoggingMode` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-740">DTSLoggingMode 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-740">Friendly name in DTSLoggingMode</span></span>|<span data-ttu-id="760ba-741">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-741">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="760ba-742">UseParentSetting</span><span class="sxs-lookup"><span data-stu-id="760ba-742">UseParentSetting</span></span>|<span data-ttu-id="760ba-743">0</span><span class="sxs-lookup"><span data-stu-id="760ba-743">0</span></span>|  
|<span data-ttu-id="760ba-744">啟用</span><span class="sxs-lookup"><span data-stu-id="760ba-744">Enabled</span></span>|<span data-ttu-id="760ba-745">1</span><span class="sxs-lookup"><span data-stu-id="760ba-745">1</span></span>|  
|<span data-ttu-id="760ba-746">已停用</span><span class="sxs-lookup"><span data-stu-id="760ba-746">Disabled</span></span>|<span data-ttu-id="760ba-747">2</span><span class="sxs-lookup"><span data-stu-id="760ba-747">2</span></span>|  
  
 <span data-ttu-id="760ba-748">`TransactionOption`屬性：使用來自列舉的值進行設定 `DTSTransactionOption` 。</span><span class="sxs-lookup"><span data-stu-id="760ba-748">`TransactionOption` property-Set by using values from the `DTSTransactionOption` enumeration.</span></span>  
  
|<span data-ttu-id="760ba-749">DTSTransactionOption 中的易記名稱</span><span class="sxs-lookup"><span data-stu-id="760ba-749">Friendly name in DTSTransactionOption</span></span>|<span data-ttu-id="760ba-750">數值</span><span class="sxs-lookup"><span data-stu-id="760ba-750">Numeric value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="760ba-751">NotSupported</span><span class="sxs-lookup"><span data-stu-id="760ba-751">NotSupported</span></span>|<span data-ttu-id="760ba-752">0</span><span class="sxs-lookup"><span data-stu-id="760ba-752">0</span></span>|  
|<span data-ttu-id="760ba-753">支援</span><span class="sxs-lookup"><span data-stu-id="760ba-753">Supported</span></span>|<span data-ttu-id="760ba-754">1</span><span class="sxs-lookup"><span data-stu-id="760ba-754">1</span></span>|  
|<span data-ttu-id="760ba-755">必要</span><span class="sxs-lookup"><span data-stu-id="760ba-755">Required</span></span>|<span data-ttu-id="760ba-756">2</span><span class="sxs-lookup"><span data-stu-id="760ba-756">2</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="760ba-757">相關工作</span><span class="sxs-lookup"><span data-stu-id="760ba-757">Related Tasks</span></span>  
 [<span data-ttu-id="760ba-758">新增或變更屬性運算式</span><span class="sxs-lookup"><span data-stu-id="760ba-758">Add or Change a Property Expression</span></span>](add-or-change-a-property-expression.md)  
  
## <a name="see-also"></a><span data-ttu-id="760ba-759">另請參閱</span><span class="sxs-lookup"><span data-stu-id="760ba-759">See Also</span></span>  
 <span data-ttu-id="760ba-760">[在封裝中使用屬性運算式](use-property-expressions-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="760ba-760">[Use Property Expressions in Packages](use-property-expressions-in-packages.md) </span></span>  
 <span data-ttu-id="760ba-761">[Integration Services &#40;SSIS&#41; 封裝](../integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="760ba-761">[Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md) </span></span>  
 <span data-ttu-id="760ba-762">[Integration Services 容器](../control-flow/integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="760ba-762">[Integration Services Containers](../control-flow/integration-services-containers.md) </span></span>  
 <span data-ttu-id="760ba-763">[Integration Services 工作](../control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="760ba-763">[Integration Services Tasks](../control-flow/integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="760ba-764">優先順序條件約束</span><span class="sxs-lookup"><span data-stu-id="760ba-764">Precedence Constraints</span></span>](../control-flow/precedence-constraints.md)  
  
  
