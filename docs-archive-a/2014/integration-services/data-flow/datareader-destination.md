---
title: DataReader 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.datareaderdest.f1
helpviewer_keywords:
- DataReader destination
- destinations [Integration Services], DataReader
ms.assetid: 56fcc4bf-c901-42c3-a71d-110039293431
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 40cfe5d99c33eb19d415f204173005a64bde7855
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709822"
---
# <a name="datareader-destination"></a><span data-ttu-id="18277-102">DataReader 目的地</span><span class="sxs-lookup"><span data-stu-id="18277-102">DataReader Destination</span></span>
  <span data-ttu-id="18277-103">DataReader 目的地使用 ADO.NET `DataReader` 介面公開資料流程中的資料。</span><span class="sxs-lookup"><span data-stu-id="18277-103">The DataReader destination exposes the data in a data flow by using the ADO.NET `DataReader` interface.</span></span> <span data-ttu-id="18277-104">然後，資料可以由其他應用程式取用。</span><span class="sxs-lookup"><span data-stu-id="18277-104">The data can then be consumed by other applications.</span></span> <span data-ttu-id="18277-105">例如，您可以設定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表的資料來源，以使用執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件的結果。</span><span class="sxs-lookup"><span data-stu-id="18277-105">For example, you can configure the data source of a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report to use the result of running a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="18277-106">若要這樣做，請建立實作 DataReader 目的地的資料流程。</span><span class="sxs-lookup"><span data-stu-id="18277-106">To do this, you create a data flow that implements the DataReader destination.</span></span>  
  
 <span data-ttu-id="18277-107">如需以程式設計方式存取和讀取 DataReader 目的地之值的詳細資訊，請參閱 [載入本機封裝的輸出](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)。</span><span class="sxs-lookup"><span data-stu-id="18277-107">For information about accessing and reading values in the DataReader destination programmatically, see [Loading the Output of a Local Package](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md).</span></span>  
  
## <a name="configuration-of-the-datareader-destination"></a><span data-ttu-id="18277-108">設定 DataReader 目的地</span><span class="sxs-lookup"><span data-stu-id="18277-108">Configuration of the DataReader Destination</span></span>  
 <span data-ttu-id="18277-109">您可以指定 DataReader 目的地的逾時值，並指示逾時發生時目的地是否失敗。</span><span class="sxs-lookup"><span data-stu-id="18277-109">You can specify a time-out value for the DataReader destination and indicate whether the destination should fail if a time-out occurs.</span></span> <span data-ttu-id="18277-110">如果應用程式未在指定時間內要求資料，便會發生逾時。</span><span class="sxs-lookup"><span data-stu-id="18277-110">A time-out occurs if the application does not ask for data within the specified time.</span></span>  
  
 <span data-ttu-id="18277-111">DataReader 目的地有一個輸入。</span><span class="sxs-lookup"><span data-stu-id="18277-111">The DataReader destination has one input.</span></span> <span data-ttu-id="18277-112">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="18277-112">It does not support an error output.</span></span>  
  
 <span data-ttu-id="18277-113">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="18277-113">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="18277-114">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="18277-114">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="18277-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="18277-115">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="18277-116">資料讀取元目的地自訂屬性</span><span class="sxs-lookup"><span data-stu-id="18277-116">DataReader Destination Custom Properties</span></span>](datareader-destination-custom-properties.md)  
  
 <span data-ttu-id="18277-117">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="18277-117">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
