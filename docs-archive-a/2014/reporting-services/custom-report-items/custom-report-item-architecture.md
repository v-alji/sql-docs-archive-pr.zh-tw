---
title: 自訂報表項目架構 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, architecture
ms.assetid: 2a88ea46-c9f8-4dd7-aad1-16de11da4f06
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a053eb55547da9030eebe9036667cca2e14606f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585151"
---
# <a name="custom-report-item-architecture"></a><span data-ttu-id="dc14d-102">自訂報表項目架構</span><span class="sxs-lookup"><span data-stu-id="dc14d-102">Custom Report Item Architecture</span></span>
  <span data-ttu-id="dc14d-103">自訂報表項目是報表定義語言 (RDL) 的延伸模組，可讓開發人員新增 RDL 中原本就支援的功能，或是擴充現有控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="dc14d-103">A custom report item is an extension to the Report Definition Language (RDL) that allows developers to add functionality that's not natively supported in RDL or extend the functionality of existing controls.</span></span> <span data-ttu-id="dc14d-104">自訂報表項目有兩個主要元件：執行階段元件與設計階段元件。</span><span class="sxs-lookup"><span data-stu-id="dc14d-104">There are two main components to a custom report item: the run-time component and the design-time component.</span></span> <span data-ttu-id="dc14d-105">這些元件會實作成 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 組件，而且可用任何 符合 CLS 規範的語言來撰寫。</span><span class="sxs-lookup"><span data-stu-id="dc14d-105">These components are implemented as [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] assemblies, and can be written in any CLS-compliant language.</span></span>  
  
## <a name="the-run-time-component"></a><span data-ttu-id="dc14d-106">執行階段元件</span><span class="sxs-lookup"><span data-stu-id="dc14d-106">The Run-Time Component</span></span>  
 <span data-ttu-id="dc14d-107">自訂報表項目的執行階段元件會在執行階段由報表處理器進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="dc14d-107">The run-time component for a custom report item is called by the report processor at run time.</span></span> <span data-ttu-id="dc14d-108">執行階段元件會接受報表處理器在執行階段所傳遞的資料、處理這個資料，並傳回包含已轉譯之自訂報表項目的影像。</span><span class="sxs-lookup"><span data-stu-id="dc14d-108">The run-time component accepts data passed by the report processor at run time, processes this data, and returns an image containing the rendered custom report item.</span></span>  
  
 <span data-ttu-id="dc14d-109">![自訂報表項目執行階段元件](../../../2014/reporting-services/media/customreportitemrun-timecomponentarchitecture.gif "自訂報表項目執行階段元件")</span><span class="sxs-lookup"><span data-stu-id="dc14d-109">![Custom report item run-time component](../../../2014/reporting-services/media/customreportitemrun-timecomponentarchitecture.gif "Custom report item run-time component")</span></span>  
  
## <a name="the-design-time-component"></a><span data-ttu-id="dc14d-110">設計階段元件</span><span class="sxs-lookup"><span data-stu-id="dc14d-110">The Design-Time Component</span></span>  
 <span data-ttu-id="dc14d-111">設計階段元件允許在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 的報表設計師介面中定義和操作自訂報表項目。</span><span class="sxs-lookup"><span data-stu-id="dc14d-111">The design-time component allows the custom report item to be defined and manipulated in the Report Designer interface in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="dc14d-112">設計階段元件是由幾個子控制項所組成，這些子控制項可控制設計環境中自訂報表項目的外觀與屬性。</span><span class="sxs-lookup"><span data-stu-id="dc14d-112">The design-time component consists of several sub-controls that control the appearance and properties of the custom report item in the design environment.</span></span>  
  
 <span data-ttu-id="dc14d-113">![自訂報表項目設計階段元件](../../../2014/reporting-services/media/customreportitemdesign-timecomponentarchitecture.gif "自訂報表項目設計階段元件")</span><span class="sxs-lookup"><span data-stu-id="dc14d-113">![Custom report item design-time component](../../../2014/reporting-services/media/customreportitemdesign-timecomponentarchitecture.gif "Custom report item design-time component")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc14d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc14d-114">See Also</span></span>  
 <span data-ttu-id="dc14d-115">[建立自訂報表專案執行時間元件](../custom-report-items/creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="dc14d-115">[Creating a Custom Report Item Run-Time Component](../custom-report-items/creating-a-custom-report-item-run-time-component.md) </span></span>  
 <span data-ttu-id="dc14d-116">[建立自訂報表專案設計階段元件](../custom-report-items/creating-a-custom-report-item-design-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="dc14d-116">[Creating a Custom Report Item Design-Time Component](../custom-report-items/creating-a-custom-report-item-design-time-component.md) </span></span>  
 [<span data-ttu-id="dc14d-117">操作說明：部署自訂報表項目</span><span class="sxs-lookup"><span data-stu-id="dc14d-117">How to: Deploy a Custom Report Item</span></span>](../custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
