---
title: SQL Server Compact Edition 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlservercompactdest.f1
helpviewer_keywords:
- destinations [Integration Services], SQL Server Compact
- SQL Server Compact, destination
- inserting data
ms.assetid: 697742ba-cc14-414d-8187-1845ad0dd99b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bfeb0bfce54c9ebefb5c526656be6b736dc0d82b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599113"
---
# <a name="sql-server-compact-edition-destination"></a><span data-ttu-id="e5e72-102">SQL Server Compact Edition 目的地</span><span class="sxs-lookup"><span data-stu-id="e5e72-102">SQL Server Compact Edition Destination</span></span>
  <span data-ttu-id="e5e72-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目的地會將資料寫入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e5e72-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination writes data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact databases.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5e72-104">在 64 位元電腦上，您必須以 32 位元模式執行連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 資料來源的封裝。</span><span class="sxs-lookup"><span data-stu-id="e5e72-104">On a 64-bit computer, you must run packages that connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources in 32-bit mode.</span></span> <span data-ttu-id="e5e72-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用來連接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Compact 資料來源的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 提供者只有提供 32 位元版本。</span><span class="sxs-lookup"><span data-stu-id="e5e72-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact provider that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] uses to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources is available only in a 32-bit version.</span></span>  
  
 <span data-ttu-id="e5e72-106">您可以透過指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目的地將資料插入所在的資料表名稱來設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目的地。</span><span class="sxs-lookup"><span data-stu-id="e5e72-106">You configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination by specifying the name of the table into which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination inserts the data.</span></span> <span data-ttu-id="e5e72-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目的地的 TableName 自訂屬性包含資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="e5e72-107">The custom property TableName of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination contains the table name.</span></span>  
  
 <span data-ttu-id="e5e72-108">此目的地會使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 連線管理員連接到資料來源，且連線管理員會指定要使用的 OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="e5e72-108">This destination uses an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager to connect to a data source, and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="e5e72-109">如需詳細資訊，請參閱 [SQL Server Compact Edition 連線管理員](../connection-manager/sql-server-compact-edition-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="e5e72-109">For more information, see [SQL Server Compact Edition Connection Manager](../connection-manager/sql-server-compact-edition-connection-manager.md).</span></span>  
  
 <span data-ttu-id="e5e72-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目的地包括 TableName 自訂屬性；屬性運算式可以在載入封裝時更新這個屬性。</span><span class="sxs-lookup"><span data-stu-id="e5e72-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination includes the TableName custom property, which can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="e5e72-111">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](../expressions/integration-services-ssis-expressions.md)、[在封裝中使用屬性運算式](../expressions/use-property-expressions-in-packages.md)和 [SQL Server Compact Edition 目的地自訂屬性](sql-server-compact-edition-destination-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e5e72-111">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md), and [SQL Server Compact Edition Destination Custom Properties](sql-server-compact-edition-destination-custom-properties.md).</span></span>  
  
 <span data-ttu-id="e5e72-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目的地具有一個輸入，且不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="e5e72-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination has one input and does not support an error output.</span></span>  
  
## <a name="configuration-of-the-sql-server-compact-edition-destination"></a><span data-ttu-id="e5e72-113">設定 SQL Server Compact Edition 目的地</span><span class="sxs-lookup"><span data-stu-id="e5e72-113">Configuration of the SQL Server Compact Edition Destination</span></span>  
 <span data-ttu-id="e5e72-114">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="e5e72-114">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="e5e72-115">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="e5e72-115">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="e5e72-116">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="e5e72-116">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e5e72-117">Common Properties</span><span class="sxs-lookup"><span data-stu-id="e5e72-117">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="e5e72-118">SQL Server 目的地自訂屬性</span><span class="sxs-lookup"><span data-stu-id="e5e72-118">SQL Server Destination Custom Properties</span></span>](sql-server-destination-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="e5e72-119">相關工作</span><span class="sxs-lookup"><span data-stu-id="e5e72-119">Related Tasks</span></span>  
 <span data-ttu-id="e5e72-120">如需如何設定此元件屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="e5e72-120">For more information about how to set properties of this component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e72-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5e72-121">See Also</span></span>  
 [<span data-ttu-id="e5e72-122">資料流程</span><span class="sxs-lookup"><span data-stu-id="e5e72-122">Data Flow</span></span>](data-flow.md)  
  
  
