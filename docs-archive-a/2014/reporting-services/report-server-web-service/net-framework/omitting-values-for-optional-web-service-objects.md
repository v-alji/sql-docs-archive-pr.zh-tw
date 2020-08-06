---
title: 省略選擇性 Web 服務物件的值 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3858f73e1b332acfa1a1bbc640007f6f0884abff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688537"
---
# <a name="omitting-values-for-optional-web-service-objects"></a><span data-ttu-id="64305-102">省略選擇性 Web 服務物件的值</span><span class="sxs-lookup"><span data-stu-id="64305-102">Omitting Values for Optional Web Service Objects</span></span>
  <span data-ttu-id="64305-103">數個報表伺服器 Web 服務複雜類型的屬性具有隨附的屬性，稱為指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="64305-103">Properties of several of the Report Server Web service complex types have an accompanying property known as the Specified property.</span></span> <span data-ttu-id="64305-104">屬性的名稱是由原始的屬性名稱所組成，此名稱中附加了 "Specified" 這個字。</span><span class="sxs-lookup"><span data-stu-id="64305-104">The name of the property consists of the original property name with the word "Specified" appended to it.</span></span> <span data-ttu-id="64305-105">此屬性的存在表示有時可能會省略原始屬性的值。</span><span class="sxs-lookup"><span data-stu-id="64305-105">The presence of this property indicates that a value for the original property may sometimes be omitted.</span></span> <span data-ttu-id="64305-106">這是從 Web 服務描述語言 (WSDL) 翻譯為 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Proxy 類別的直接結果。</span><span class="sxs-lookup"><span data-stu-id="64305-106">This is a direct result of the translation from the Web Service Description Language (WSDL) to a [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] proxy class.</span></span> <span data-ttu-id="64305-107">例如，複雜類型 <xref:ReportService2010.DataSourceDefinition.Enabled%2A> 的 Web 服務屬性 <xref:ReportService2010.DataSourceDefinition> 具有名為 <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> 的隨附屬性。</span><span class="sxs-lookup"><span data-stu-id="64305-107">For example, the Web service property <xref:ReportService2010.DataSourceDefinition.Enabled%2A> of the complex type <xref:ReportService2010.DataSourceDefinition> has an accompanying property named <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>.</span></span> <span data-ttu-id="64305-108">如果您要建立應用程式而不想設定 <xref:ReportService2010.DataSourceDefinition.Enabled%2A> 屬性的值，您不需要提供 <xref:ReportService2010.DataSourceDefinition.Enabled%2A> 的值；系統會使用 `true` 預設值。</span><span class="sxs-lookup"><span data-stu-id="64305-108">If you are building an application and do not want to set a value for the <xref:ReportService2010.DataSourceDefinition.Enabled%2A> property, you do not have to supply a value for <xref:ReportService2010.DataSourceDefinition.Enabled%2A>; the default value of `true` is used.</span></span> <span data-ttu-id="64305-109">不過，您仍需要將 <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> 設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="64305-109">However, you still need to set <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> to `false`.</span></span> <span data-ttu-id="64305-110">如果您為 <xref:ReportService2010.DataSourceDefinition.Enabled%2A> 屬性提供值，則需要將 <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> 設定為等於 `true`。</span><span class="sxs-lookup"><span data-stu-id="64305-110">If you supply a value for the <xref:ReportService2010.DataSourceDefinition.Enabled%2A> property, you need to set <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> equal to `true`.</span></span> <span data-ttu-id="64305-111">這是針對可寫入屬性的情況。</span><span class="sxs-lookup"><span data-stu-id="64305-111">This is the case for writable properties.</span></span> <span data-ttu-id="64305-112">如果是唯讀屬性，則不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="64305-112">For read-only properties, you do not need to take any action.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="64305-113">如果無法使用上述的技術指定屬性，就可能導致無法預測的 Web 服務行為。</span><span class="sxs-lookup"><span data-stu-id="64305-113">Failure to specify a property using the above-mentioned technique can result in unpredictable Web service behavior.</span></span>  
  
 <span data-ttu-id="64305-114">通常需要您處理其他指定屬性的資料類型為 `Boolean` 、 `DateTime` 和 `Enumeration` 。</span><span class="sxs-lookup"><span data-stu-id="64305-114">The data types that usually require you to handle the additional Specified property are `Boolean`, `DateTime`, and `Enumeration`.</span></span>  
  
 <span data-ttu-id="64305-115">如需範例，請參閱 <xref:ReportService2010.ReportingService2010.CreateDataSource%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="64305-115">For an example, see <xref:ReportService2010.ReportingService2010.CreateDataSource%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64305-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64305-116">See Also</span></span>  
 <span data-ttu-id="64305-117">[使用 Web 服務和 .NET Framework 建置應用程式](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="64305-117">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="64305-118">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="64305-118">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
