---
title: 建立自訂報表項目執行階段元件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, creating
ms.assetid: b3e15a4a-98f8-4dbb-b847-bbcb20327051
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 50c5c0211bc5cd1359af9d1493782bd9d96c2b3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585157"
---
# <a name="creating-a-custom-report-item-run-time-component"></a><span data-ttu-id="1a9a0-102">建立自訂報表項目執行階段元件</span><span class="sxs-lookup"><span data-stu-id="1a9a0-102">Creating a Custom Report Item Run-Time Component</span></span>
  <span data-ttu-id="1a9a0-103">自訂報表專案執行時間元件會 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 使用任何符合 CLS 標準的語言實作為元件，並在執行時間由報表處理器呼叫。</span><span class="sxs-lookup"><span data-stu-id="1a9a0-103">The custom report item run-time component is implemented as a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] component using any CLS-compliant language, and is called by the report processor at run time.</span></span> <span data-ttu-id="1a9a0-104">您可藉由修改自訂報表項目對應的設計階段元件，在設計環境中定義執行階段元件的屬性。</span><span class="sxs-lookup"><span data-stu-id="1a9a0-104">You define the properties for the run-time component in the design environment by modifying the custom report item's corresponding design-time component.</span></span>  

<!--
Replacing the following multiValue.....

ms.technology: 
  - "docset-sql-devref"
  - "reporting-services-native"

.....with the following single value.....

ms.technology: reporting-services
.

(GeneMi = MightyPen  ,  2019-04-20  ,  DevO= 1515083)
-->

 <span data-ttu-id="1a9a0-105">如需完全實作的自訂報表項目的範例，請參閱 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (SQL Server Reporting Services 產品範例)。</span><span class="sxs-lookup"><span data-stu-id="1a9a0-105">For a sample of a fully implemented custom report item, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="definition-and-instance-objects"></a><span data-ttu-id="1a9a0-106">定義和執行個體物件</span><span class="sxs-lookup"><span data-stu-id="1a9a0-106">Definition and Instance Objects</span></span>  
 <span data-ttu-id="1a9a0-107">在實作自訂報表項目之前，了解「定義物件」\*\* 和「執行個體物件」\*\* 之間的差異很重要。</span><span class="sxs-lookup"><span data-stu-id="1a9a0-107">Before implementing a custom report item it is important to understand the difference between *definition objects* and *instance objects*.</span></span> <span data-ttu-id="1a9a0-108">定義物件提供自訂報表項目的 RDL 表示法，而執行個體物件是定義物件的評估版本。</span><span class="sxs-lookup"><span data-stu-id="1a9a0-108">Definition objects provide the RDL representation of the custom report item whereas instance objects are the evaluated versions of the definition objects.</span></span> <span data-ttu-id="1a9a0-109">報表上每個項目只有一個定義物件。</span><span class="sxs-lookup"><span data-stu-id="1a9a0-109">There is only one definition object for each item on the report.</span></span> <span data-ttu-id="1a9a0-110">在包含運算式的定義物件上存取屬性時，您會取得未評估過的運算式字串。</span><span class="sxs-lookup"><span data-stu-id="1a9a0-110">When accessing properties on a definition object that contain expressions, you will get the unevaluated expression string.</span></span> <span data-ttu-id="1a9a0-111">執行個體物件包含已評估的定義物件版本，而且與項目的定義物件可能具有一對多的關聯性。</span><span class="sxs-lookup"><span data-stu-id="1a9a0-111">Instance objects contain the evaluated versions of the definition objects and can have a one-to-many relationship with an item's definition object.</span></span> <span data-ttu-id="1a9a0-112">例如，如果報表具有 <xref:Microsoft.ReportingServices.OnDemandReportRendering.Tablix> 資料區，而該資料區在詳細資料列中包含 <xref:Microsoft.ReportingServices.OnDemandReportRendering.CustomReportItem>，則只會有一個定義物件，但資料區中的每個資料列都會有一個執行個體物件。</span><span class="sxs-lookup"><span data-stu-id="1a9a0-112">For example, if a report has a <xref:Microsoft.ReportingServices.OnDemandReportRendering.Tablix> data region that contains a <xref:Microsoft.ReportingServices.OnDemandReportRendering.CustomReportItem> in a detail row, there will be only one definition object but there will be an instance object for each row in the data region.</span></span>  
  
## <a name="implementing-the-icustomreportitem-interface"></a><span data-ttu-id="1a9a0-113">實作 ICustomReportItem 介面</span><span class="sxs-lookup"><span data-stu-id="1a9a0-113">Implementing the ICustomReportItem Interface</span></span>  
 <span data-ttu-id="1a9a0-114">若要建立 `CustomReportItem` 執行階段元件，您需要實作定義於 Microsoft.ReportingServices.ProcessingCore.dll 的 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> 介面：</span><span class="sxs-lookup"><span data-stu-id="1a9a0-114">To create a `CustomReportItem` run-time component you will need to implement the <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> interface that is defined in the Microsoft.ReportingServices.ProcessingCore.dll:</span></span>  
  
```csharp  
namespace Microsoft.ReportingServices.OnDemandReportRendering  
{  
    public interface ICustomReportItem  
    {  
        void GenerateReportItemDefinition(CustomReportItem customReportItem);  
void EvaluateReportItemInstance(CustomReportItem customReportItem);  
    }  
}  
```  
  
 <span data-ttu-id="1a9a0-115">在實作 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> 介面之後，將為您產生兩個方法 Stub：<xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> 和 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A>。</span><span class="sxs-lookup"><span data-stu-id="1a9a0-115">After you have implemented the <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> interface, two method stubs will be generated for you: <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> and <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A>.</span></span> <span data-ttu-id="1a9a0-116">系統會先呼叫 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> 方法，並用它來設定定義屬性及建立 <xref:Microsoft.ReportingServices.OnDemandReportRendering.Image> 物件，此物件將同時包含用於轉譯項目的定義屬性和執行個體屬性。</span><span class="sxs-lookup"><span data-stu-id="1a9a0-116">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> method is called first and is used for setting definition properties and creating the <xref:Microsoft.ReportingServices.OnDemandReportRendering.Image> object that will contain both the definition and instance properties that are used for rendering the item.</span></span> <span data-ttu-id="1a9a0-117">在評估定義物件之後會呼叫 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A> 方法，這個方法提供用於轉譯項目的執行個體物件。</span><span class="sxs-lookup"><span data-stu-id="1a9a0-117">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A> method is called after the definition objects have been evaluated, and it provides the instance objects that will be used for rendering the item.</span></span>  
  
 <span data-ttu-id="1a9a0-118">以下是自訂報表項目的範例實作，此實作會將控制項的名稱轉譯為影像。</span><span class="sxs-lookup"><span data-stu-id="1a9a0-118">The following is an example implementation of a custom report item that renders the name of the control as an image.</span></span>  
  
```csharp  
namespace Microsoft.Samples.ReportingServices  
{  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.Specialized;  
    using System.Drawing.Imaging;  
    using System.IO;  
    using System.Text;  
    using Microsoft.ReportingServices.OnDemandReportRendering;  
  
    public class PolygonsCustomReportItem : ICustomReportItem  
    {  
        #region ICustomReportItem Members  
  
        public void GenerateReportItemDefinition(CustomReportItem cri)  
        {  
            // Create the Image object that will be   
            // used to render the custom report item  
            cri.CreateCriImageDefinition();  
            Image polygonImage = (Image)cri.GeneratedReportItem;  
        }  
  
        public void EvaluateReportItemInstance(CustomReportItem cri)  
        {  
            // Get the Image definition  
            Image polygonImage = (Image)cri.GeneratedReportItem;  
  
            // Create the image for the custom report item  
            polygonImage.ImageInstance.ImageData = DrawImage(cri);  
        }  
  
        #endregion  
  
        /// <summary>  
        /// Creates an image of the CustomReportItem's name  
        /// </summary>  
        private byte[] DrawImage(CustomReportItem customReportItem)  
        {  
            int width = 1;          // pixels  
            int height = 1;         // pixels  
            int resolution = 75;    // dpi  
  
            System.Drawing.Bitmap bitmap = new System.Drawing.Bitmap(width, height);  
            bitmap.SetResolution(resolution, resolution);  
  
            System.Drawing.Graphics graphics = System.Drawing.Graphics.FromImage(bitmap);  
            graphics.PageUnit = System.Drawing.GraphicsUnit.Pixel;  
  
            // Get the Font for the Text  
            System.Drawing.Font font = new System.Drawing.Font(System.Drawing.FontFamily.GenericMonospace,  
                12, System.Drawing.FontStyle.Regular);  
  
            // Get the Brush for drawing the Text  
            System.Drawing.Brush brush = new System.Drawing.SolidBrush(System.Drawing.Color.LightGreen);  
  
            // Get the measurements for the image  
            System.Drawing.SizeF maxStringSize = graphics.MeasureString(customReportItem.Name, font);  
            width = (int)(maxStringSize.Width + 2 * font.GetHeight(resolution));  
            height = (int)(maxStringSize.Height + 2 * font.GetHeight(resolution));  
  
            bitmap.Dispose();  
            bitmap = new System.Drawing.Bitmap(width, height);  
            bitmap.SetResolution(resolution, resolution);  
  
            graphics.Dispose();  
            graphics = System.Drawing.Graphics.FromImage(bitmap);  
            graphics.PageUnit = System.Drawing.GraphicsUnit.Pixel;  
  
            // Draw the text  
            graphics.DrawString(customReportItem.Name, font, brush, font.GetHeight(resolution),   
                font.GetHeight(resolution));  
  
            // Create the byte array of the image data  
            MemoryStream memoryStream = new MemoryStream();  
            bitmap.Save(memoryStream, ImageFormat.Bmp);  
            memoryStream.Position = 0;  
            byte[] imageData = new byte[memoryStream.Length];  
            memoryStream.Read(imageData, 0, imageData.Length);  
  
            return imageData;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a9a0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a9a0-119">See Also</span></span>  
 <span data-ttu-id="1a9a0-120">[自訂報表專案架構](custom-report-item-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="1a9a0-120">[Custom Report Item Architecture](custom-report-item-architecture.md) </span></span>  
 <span data-ttu-id="1a9a0-121">[建立自訂報表專案設計階段元件](creating-a-custom-report-item-design-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="1a9a0-121">[Creating a Custom Report Item Design-Time Component](creating-a-custom-report-item-design-time-component.md) </span></span>  
 <span data-ttu-id="1a9a0-122">[自訂報表專案類別庫](custom-report-item-class-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="1a9a0-122">[Custom Report Item Class Libraries](custom-report-item-class-libraries.md) </span></span>  
 [<span data-ttu-id="1a9a0-123">操作說明：部署自訂報表項目</span><span class="sxs-lookup"><span data-stu-id="1a9a0-123">How to: Deploy a Custom Report Item</span></span>](how-to-deploy-a-custom-report-item.md)  
  
  
