---
title: 為資料處理延伸模組實作命令類別 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], commands
- Command class
- commands [Reporting Services]
ms.assetid: 465ef8d1-c503-407c-8afd-58d620e344ee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f07b9beb798b1cd33ec2fee6af890a09a516b2f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708957"
---
# <a name="implementing-a-command-class-for-a-data-processing-extension"></a><span data-ttu-id="40caf-102">為資料處理延伸模組實作命令類別</span><span class="sxs-lookup"><span data-stu-id="40caf-102">Implementing a Command Class for a Data Processing Extension</span></span>
  <span data-ttu-id="40caf-103">**Command** 物件會構成要求，並將它傳遞到資料來源。</span><span class="sxs-lookup"><span data-stu-id="40caf-103">The **Command** object formulates a request and passes it on to the data source.</span></span> <span data-ttu-id="40caf-104">命令文字可採用許多不同的語法形式，包括文字與 XML。</span><span class="sxs-lookup"><span data-stu-id="40caf-104">The command text can take many different syntactical forms, including text and XML.</span></span> <span data-ttu-id="40caf-105">如果傳回結果，**Command** 物件會傳回結果以作為 **DataReader** 物件。</span><span class="sxs-lookup"><span data-stu-id="40caf-105">If results are returned, the **Command** object returns results as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="40caf-106">若要建立 **Command** 類別，請實作 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>。</span><span class="sxs-lookup"><span data-stu-id="40caf-106">To create a **Command** class, implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>.</span></span> <span data-ttu-id="40caf-107">實作 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 方法以傳回結果集作為 **DataReader** 物件。</span><span class="sxs-lookup"><span data-stu-id="40caf-107">Implement the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method to return a result set as a **DataReader** object.</span></span> <span data-ttu-id="40caf-108">**Command** 類別的 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 方法應該包括實作，它需要 <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior> 列舉作為引數。</span><span class="sxs-lookup"><span data-stu-id="40caf-108">The <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method of your **Command** class should include an implementation that takes a <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior> enumeration as an argument.</span></span> <span data-ttu-id="40caf-109">如果您將資料處理延伸模組部署到報表設計師，請提供實作以處理 <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> 方法中的 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 案例。</span><span class="sxs-lookup"><span data-stu-id="40caf-109">If you deploy your data processing extension to Report Designer, provide an implementation that handles a <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> case in the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="40caf-110">僅限結構描述實作是用以提供具有欄位清單的報表設計師。</span><span class="sxs-lookup"><span data-stu-id="40caf-110">A schema-only implementation is used to supply Report Designer with a fields list.</span></span> <span data-ttu-id="40caf-111"><xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 方法傳回的 **DataReader** 物件，需要在結果集中包含欄位或是資料行中的類型與名稱資訊。</span><span class="sxs-lookup"><span data-stu-id="40caf-111">The **DataReader** object returned by the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method needs to contain type and name information for the fields, or columns, in your result set.</span></span>  
  
 <span data-ttu-id="40caf-112">(選擇性) 您的 **Command** 類別可以實作 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>。</span><span class="sxs-lookup"><span data-stu-id="40caf-112">Optionally, your **Command** class can implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>.</span></span> <span data-ttu-id="40caf-113">這個介面允許實作類別以分析查詢，並在查詢中傳回參數清單。</span><span class="sxs-lookup"><span data-stu-id="40caf-113">This interface enables an implementing class to analyze a query and return a list of parameters in the query.</span></span> <span data-ttu-id="40caf-114"><xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> 介面的功能只能用於報表設計師中。</span><span class="sxs-lookup"><span data-stu-id="40caf-114">The functionality of the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> interface is only used in Report Designer.</span></span> <span data-ttu-id="40caf-115">當您實作 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> 時，允許每當在預覽模式執行報表時，提示報表設計師的使用者所需的參數。</span><span class="sxs-lookup"><span data-stu-id="40caf-115">When you implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>, you enable users of Report Designer to be prompted for parameters whenever a report is run in preview mode.</span></span> <span data-ttu-id="40caf-116">此外，您可以在 [資料集] 對話方塊的 [參數] 索引標籤中檢視參數。</span><span class="sxs-lookup"><span data-stu-id="40caf-116">In addition, you can view the parameters in the **Parameters** tab of the **Data Set** dialog.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40caf-117">如果自訂資料處理延伸模組不支援參時，就不應該實作 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>。</span><span class="sxs-lookup"><span data-stu-id="40caf-117">You should not implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> if your custom data processing extension does not support parameters.</span></span>  
  
 <span data-ttu-id="40caf-118">如需範例 **Command** 類別實作，請參閱 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (SQL Server Reporting Services 產品範例)。</span><span class="sxs-lookup"><span data-stu-id="40caf-118">For a sample **Command** class implementation, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40caf-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40caf-119">See Also</span></span>  
 <span data-ttu-id="40caf-120">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="40caf-120">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="40caf-121">[實作資料處理延伸模組](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="40caf-121">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="40caf-122">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="40caf-122">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
