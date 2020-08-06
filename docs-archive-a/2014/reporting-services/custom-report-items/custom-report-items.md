---
title: 自訂報表項目 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- extending Reporting Services
- Reporting Services, extending
- custom report items
ms.assetid: 64dcaf2c-1af5-4937-8ff7-98f1ec3b367e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 86b819cb4d305e537a52a2e7f25cdfa3aefa5f9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708994"
---
# <a name="custom-report-items"></a><span data-ttu-id="cfbae-102">自訂報表項目</span><span class="sxs-lookup"><span data-stu-id="cfbae-102">Custom Report Items</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="cfbae-103">提供一組豐富的工具，以建立和發行企業報表、管理安全性與訂閱以及透過完整的 API 來擴充和報告功能。</span><span class="sxs-lookup"><span data-stu-id="cfbae-103">provides a rich set of tools for building and publishing enterprise reports, managing security and subscriptions, and extending the reporting functionality through a comprehensive API.</span></span> <span data-ttu-id="cfbae-104">報表是利用稱為「報表定義語言」(RDL) 的以 XML 為基礎之語言來定義。</span><span class="sxs-lookup"><span data-stu-id="cfbae-104">Reports are defined using an XML-based language called Report Definition Language (RDL).</span></span> <span data-ttu-id="cfbae-105">RDL 提供描述報表之配置、查詢資訊以及項目類型的指示。</span><span class="sxs-lookup"><span data-stu-id="cfbae-105">RDL provides a set of instructions that describe layout, query information, and item types for a report.</span></span> <span data-ttu-id="cfbae-106">您可以撰寫自訂報表項目來擴充 RDL。</span><span class="sxs-lookup"><span data-stu-id="cfbae-106">It is possible to extend RDL by writing a custom report item.</span></span> <span data-ttu-id="cfbae-107">自訂報表項目是由執行階段元件 (由報表處理器在執行階段所呼叫) 以及設計階段元件 (允許在報表設計師中使用自訂報表項目) 所組成。</span><span class="sxs-lookup"><span data-stu-id="cfbae-107">The custom report item consists of a run-time component, which is called by the report processor at run time, and a design-time component, which allows the custom report item to be available in Report Designer.</span></span>  
  
 <span data-ttu-id="cfbae-108">如需完全實作的自訂報表項目的範例，請參閱 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (SQL Server Reporting Services 產品範例)。</span><span class="sxs-lookup"><span data-stu-id="cfbae-108">For a sample of a fully implemented custom report item, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="custom-report-item-scenarios"></a><span data-ttu-id="cfbae-109">自訂報表項目案例</span><span class="sxs-lookup"><span data-stu-id="cfbae-109">Custom Report Item Scenarios</span></span>  
 <span data-ttu-id="cfbae-110">需要將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 整合到其應用程式的開發人員，可能需要在 RDL 中原本不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="cfbae-110">Developers who need to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into their applications may require functionality that is not natively supported in RDL.</span></span> <span data-ttu-id="cfbae-111">這可能包括的項目如：對應控制項、水平清單、單欄式清單以及可再旋轉的矩陣。</span><span class="sxs-lookup"><span data-stu-id="cfbae-111">This may include items such as: map controls, horizontal lists, columnar lists, and repivotable matrixes.</span></span> <span data-ttu-id="cfbae-112">執行階段自訂報表項目元件可以使用應用程式來開發和散發以滿足此需求。</span><span class="sxs-lookup"><span data-stu-id="cfbae-112">A run-time custom report item component can be developed and distributed with an application to fill this need.</span></span>  
  
 <span data-ttu-id="cfbae-113">除了提供本來不支援的功能之外，有些開發人員可能會想要使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 已隨附的控制項替代版本來擴充現有功能。</span><span class="sxs-lookup"><span data-stu-id="cfbae-113">In addition to providing functionality that isn't natively supported, some developers may want to extend existing functionality with alternative versions of controls that are already included with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="cfbae-114">在這個案例中，開發人員可以提供三個元件：執行階段元件、設計階段元件以及設計階段報表項目轉換元件 (可依需求將現有的報表項目轉換為自訂報表項目)。</span><span class="sxs-lookup"><span data-stu-id="cfbae-114">In this scenario, a developer could provide three components: a run-time component, a design-time component, and a design-time report item conversion component that converts an existing report item into a custom report item on demand.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cfbae-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="cfbae-115">In This Section</span></span>  
 [<span data-ttu-id="cfbae-116">自訂報表項目架構</span><span class="sxs-lookup"><span data-stu-id="cfbae-116">Custom Report Item Architecture</span></span>](custom-report-item-architecture.md)  
 <span data-ttu-id="cfbae-117">描述組成自訂報表項目的元件。</span><span class="sxs-lookup"><span data-stu-id="cfbae-117">Describes the components that make up a custom report item.</span></span>  
  
 [<span data-ttu-id="cfbae-118">自訂報表項目實作需求</span><span class="sxs-lookup"><span data-stu-id="cfbae-118">Custom Report Item Implementation Requirements</span></span>](custom-report-item-implementation-requirements.md)  
 <span data-ttu-id="cfbae-119">描述建立自訂報表項目的必要元件。</span><span class="sxs-lookup"><span data-stu-id="cfbae-119">Describes prerequisites for creating a custom report item.</span></span>  
  
 [<span data-ttu-id="cfbae-120">建立自訂報表項目執行階段元件</span><span class="sxs-lookup"><span data-stu-id="cfbae-120">Creating a Custom Report Item Run-Time Component</span></span>](creating-a-custom-report-item-run-time-component.md)  
 <span data-ttu-id="cfbae-121">描述如何建立自訂報表項目執行階段元件。</span><span class="sxs-lookup"><span data-stu-id="cfbae-121">Describes how to create a custom report item run-time component.</span></span>  
  
 [<span data-ttu-id="cfbae-122">建立自訂報表項目設計階段元件</span><span class="sxs-lookup"><span data-stu-id="cfbae-122">Creating a Custom Report Item Design-Time Component</span></span>](creating-a-custom-report-item-design-time-component.md)  
 <span data-ttu-id="cfbae-123">描述如何建立自訂報表項目設計階段元件。</span><span class="sxs-lookup"><span data-stu-id="cfbae-123">Describes how to create a custom report item design-time component.</span></span>  
  
 [<span data-ttu-id="cfbae-124">操作說明：部署自訂報表項目</span><span class="sxs-lookup"><span data-stu-id="cfbae-124">How to: Deploy a Custom Report Item</span></span>](how-to-deploy-a-custom-report-item.md)  
 <span data-ttu-id="cfbae-125">描述如何部署自訂報表項目</span><span class="sxs-lookup"><span data-stu-id="cfbae-125">Describes how to deploy a custom report item.</span></span>  
  
 [<span data-ttu-id="cfbae-126">自訂報表項目類別庫</span><span class="sxs-lookup"><span data-stu-id="cfbae-126">Custom Report Item Class Libraries</span></span>](custom-report-item-class-libraries.md)  
 <span data-ttu-id="cfbae-127">描述在 `Microsoft.ReportDesigner` 命名空間中自訂報表項目基礎結構類別與 Managed 包裝函數類別</span><span class="sxs-lookup"><span data-stu-id="cfbae-127">Describes the custom report item infrastructure classes and managed wrapper classes in the `Microsoft.ReportDesigner` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfbae-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfbae-128">See Also</span></span>  
 [<span data-ttu-id="cfbae-129">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="cfbae-129">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
