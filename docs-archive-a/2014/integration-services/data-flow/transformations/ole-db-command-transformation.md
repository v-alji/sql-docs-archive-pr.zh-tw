---
title: OLE DB 命令轉換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbcommandtrans.f1
helpviewer_keywords:
- statements [Integration Services]
- OLE DB Command transformation
ms.assetid: baa6735c-5acf-4759-b077-1216aca16c6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a6b0498d0ae5fa61a00cc7f6fc89e4dc506cd25a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710789"
---
# <a name="ole-db-command-transformation"></a><span data-ttu-id="e0f30-102">OLE DB 命令轉換</span><span class="sxs-lookup"><span data-stu-id="e0f30-102">OLE DB Command Transformation</span></span>
  <span data-ttu-id="e0f30-103">OLE DB 命令轉換為資料流程中每個資料列執行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e0f30-103">The OLE DB Command transformation runs an SQL statement for each row in a data flow.</span></span> <span data-ttu-id="e0f30-104">例如，可以執行在資料庫資料表中插入、更新或刪除資料列的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e0f30-104">For example, you can run an SQL statement that inserts, updates, or deletes rows in a database table.</span></span>  
  
 <span data-ttu-id="e0f30-105">您可以利用下列方式設定 OLE DB 命令轉換：</span><span class="sxs-lookup"><span data-stu-id="e0f30-105">You can configure the OLE DB Command Transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="e0f30-106">提供轉換為每個資料列執行的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e0f30-106">Provide the SQL statement that the transformation runs for each row.</span></span>  
  
-   <span data-ttu-id="e0f30-107">指定 SQL 陳述式逾時之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="e0f30-107">Specify the number of seconds before the SQL statement times out.</span></span>  
  
-   <span data-ttu-id="e0f30-108">指定預設字碼頁。</span><span class="sxs-lookup"><span data-stu-id="e0f30-108">Specify the default code page.</span></span>  
  
 <span data-ttu-id="e0f30-109">SQL 陳述式通常包含參數。</span><span class="sxs-lookup"><span data-stu-id="e0f30-109">Typically, the SQL statement includes parameters.</span></span> <span data-ttu-id="e0f30-110">參數值儲存在轉換輸入的外部資料行內，且將輸入資料行對應到外部資料行會將其同時對應到參數。</span><span class="sxs-lookup"><span data-stu-id="e0f30-110">The parameter values are stored in external columns in the transformation input, and mapping an input column to an external column maps an input column to a parameter.</span></span> <span data-ttu-id="e0f30-111">例如，若要利用資料列在 **ProductKey** 資料行中的值找到 **DimProduct** 資料表中的資料列，然後予以刪除，您可以將名為 **Param_0** 的外部資料行對應到名為 **ProductKey** 的輸入資料行，然後執行 SQL 陳述式 `DELETE FROM DimProduct WHERE ProductKey = ?`。</span><span class="sxs-lookup"><span data-stu-id="e0f30-111">For example, to locate rows in the **DimProduct** table by the value in their **ProductKey** column and then delete them, you can map the external column named **Param_0** to the input column named **ProductKey,** and then run the SQL statement `DELETE FROM DimProduct WHERE ProductKey = ?`..</span></span> <span data-ttu-id="e0f30-112">OLE DB 命令轉換提供了參數名稱，您無法對它們進行修改。</span><span class="sxs-lookup"><span data-stu-id="e0f30-112">The OLE DB Command transformation provides the parameter names and you cannot modify them.</span></span> <span data-ttu-id="e0f30-113">這些參數名稱為 **Param_0**、 **Param_1**等。</span><span class="sxs-lookup"><span data-stu-id="e0f30-113">The parameter names are **Param_0**, **Param_1**, and so on.</span></span>  
  
 <span data-ttu-id="e0f30-114">如果您使用 [進階編輯器]  對話方塊設定 OLE DB 命令轉換，SQL 陳述式中的參數可自動對應到轉換輸入的外部資料行上，按一下 [重新整理]  按鈕可以定義每個參數的特性。</span><span class="sxs-lookup"><span data-stu-id="e0f30-114">If you configure the OLE DB Command transformation by using the **Advanced Editor** dialog box, the parameters in the SQL statement may be mapped automatically to external columns in the transformation input, and the characteristics of each parameter defined, by clicking the **Refresh** button.</span></span> <span data-ttu-id="e0f30-115">但是，如果 OLE DB 命令轉換使用的 OLE DB 提供者不支援從參數中衍生參數資訊，您必須手動設定外部資料行。</span><span class="sxs-lookup"><span data-stu-id="e0f30-115">However, if the OLE DB provider that the OLE DB Command transformation uses does not support deriving parameter information from the parameter, you must configure the external columns manually.</span></span> <span data-ttu-id="e0f30-116">這表示您必須將每個參數的資料行加入轉換的外部輸入，更新資料行名稱以使用類似 **Param_0**的名稱，指定 DBParamInfoFlags 屬性的值，並將包含參數值的輸入資料行對應到外部資料行。</span><span class="sxs-lookup"><span data-stu-id="e0f30-116">This means that you must add a column for each parameter to the external input to the transformation, update the column names to use names like **Param_0**, specify the value of the DBParamInfoFlags property, and map the input columns that contain parameter values to the external columns.</span></span>  
  
 <span data-ttu-id="e0f30-117">DBParamInfoFlags 的值代表參數的特性。</span><span class="sxs-lookup"><span data-stu-id="e0f30-117">The value of DBParamInfoFlags represents the characteristics of the parameter.</span></span> <span data-ttu-id="e0f30-118">例如，值 **1** 指定參數為輸入參數，值 **65** 指定參數為可以包含 Null 值的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="e0f30-118">For example, the value **1** specifies that the parameter is an input parameter, and the value **65** specifies that the parameter is an input parameter and may contain a null value.</span></span> <span data-ttu-id="e0f30-119">該值必須與 OLE DB DBPARAMFLAGSENUM 列舉中的值相符。</span><span class="sxs-lookup"><span data-stu-id="e0f30-119">The values must match the values in the OLE DB DBPARAMFLAGSENUM enumeration.</span></span> <span data-ttu-id="e0f30-120">如需詳細資訊，請參閱 OLE DB 參考文件集。</span><span class="sxs-lookup"><span data-stu-id="e0f30-120">For more information, see the OLE DB reference documentation.</span></span>  
  
 <span data-ttu-id="e0f30-121">OLE DB 命令轉換包括 `SQLCommand` 自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="e0f30-121">The OLE DB Command transformation includes the `SQLCommand` custom property.</span></span> <span data-ttu-id="e0f30-122">屬性運算式可以在載入封裝時更新這個屬性。</span><span class="sxs-lookup"><span data-stu-id="e0f30-122">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="e0f30-123">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](../../expressions/integration-services-ssis-expressions.md)、[在封裝中使用屬性運算式](../../expressions/use-property-expressions-in-packages.md)和[轉換自訂屬性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e0f30-123">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="e0f30-124">這個轉換有一個輸入、一個規則輸出及一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="e0f30-124">This transformation has one input, one regular output, and one error output.</span></span>  
  
## <a name="logging"></a><span data-ttu-id="e0f30-125">記錄</span><span class="sxs-lookup"><span data-stu-id="e0f30-125">Logging</span></span>  
 <span data-ttu-id="e0f30-126">您可以記錄 OLE DB 命令轉換對外部資料提供者執行的呼叫。</span><span class="sxs-lookup"><span data-stu-id="e0f30-126">You can log the calls that the OLE DB Command transformation makes to external data providers.</span></span> <span data-ttu-id="e0f30-127">您可以使用這項記錄功能，疑難排解 OLE DB 命令轉換對外部資料來源執行的連接和命令。</span><span class="sxs-lookup"><span data-stu-id="e0f30-127">You can use this logging capability to troubleshoot the connections and commands to external data sources that the OLE DB Command transformation performs.</span></span> <span data-ttu-id="e0f30-128">若要記錄 OLE DB 命令轉換對外部資料提供者執行的呼叫，請啟用封裝記錄，然後在封裝層級選取 [診斷]  事件。</span><span class="sxs-lookup"><span data-stu-id="e0f30-128">To log the calls that the OLE DB Command transformation makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="e0f30-129">如需詳細資訊，請參閱 [封裝執行的疑難排解工具](../../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="e0f30-129">For more information, see [Troubleshooting Tools for Package Execution](../../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e0f30-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="e0f30-130">Related Tasks</span></span>  
 <span data-ttu-id="e0f30-131">您可以使用 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或物件模型來設定轉換。</span><span class="sxs-lookup"><span data-stu-id="e0f30-131">You can configure the transformation by either using the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or the object model.</span></span> <span data-ttu-id="e0f30-132">如需使用 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師來設定轉換的詳細資訊，請參閱  [設定 OLE DB 命令轉換](../../configure-the-ole-db-command-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="e0f30-132">For details about configuring the transformation using the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] designer, see  [Configure the OLE DB Command Transformation](../../configure-the-ole-db-command-transformation.md).</span></span> <span data-ttu-id="e0f30-133">如需有關以程式設計方式來設定此轉換的詳細資訊，請參閱《開發人員指南》。</span><span class="sxs-lookup"><span data-stu-id="e0f30-133">See the Developer Guide for details about programmatically configuring this transformation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f30-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0f30-134">See Also</span></span>  
 <span data-ttu-id="e0f30-135">[資料流程](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="e0f30-135">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="e0f30-136">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="e0f30-136">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
