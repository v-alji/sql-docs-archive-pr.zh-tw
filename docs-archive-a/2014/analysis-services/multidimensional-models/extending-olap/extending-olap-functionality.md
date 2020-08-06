---
title: 擴充 OLAP 功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 49a17ff3-94e9-4969-84fc-37d49e63933b
author: minewiskan
ms.author: owend
ms.openlocfilehash: d64d1ac46e2571aa6f8065a8ea42e4cc43aa589e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607105"
---
# <a name="extending-olap-functionality"></a><span data-ttu-id="91a2e-102">擴充 OLAP 功能</span><span class="sxs-lookup"><span data-stu-id="91a2e-102">Extending OLAP functionality</span></span>
  <span data-ttu-id="91a2e-103">身為程式設計人員，您可以撰寫組件、個人化延伸模組和預存程序，以便提供您想要在多個資料庫應用程式中使用和重新訂定用途的功能，藉以擴充 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="91a2e-103">As a programmer, you can extend Analysis Services by writing assemblies, personalized extensions, and stored procedures that provide functionality you want to use and repurpose in multiple database applications.</span></span> <span data-ttu-id="91a2e-104">組件是用來將新程序和函數加入至 MDX 語言或經由個人化增益集，進而擴充多維度模型功能。</span><span class="sxs-lookup"><span data-stu-id="91a2e-104">Assemblies are used to extend multidimensional models functionality by adding new procedures and functions to the MDX language or by means of the personalization addin.</span></span>  
  
 <span data-ttu-id="91a2e-105">預存程序可用來呼叫外部常式，讓通用程式碼只需要開發一次並儲存在單一位置，藉以簡化 Analysis Services 資料庫的開發和實作。</span><span class="sxs-lookup"><span data-stu-id="91a2e-105">Stored procedures can be used to call external routines, simplifying Analysis Services database development and implementation by allowing common code to be developed once and stored in a single location.</span></span> <span data-ttu-id="91a2e-106">預存程序可用來將 MDX 的原生功能未提供的商務功能，加入您的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="91a2e-106">Stored procedures can be used to add business functionality to your applications that is not provided by the native functionality of MDX.</span></span>  
  
 <span data-ttu-id="91a2e-107">個人化是指您加入至 Cube 以提供依照使用者變更之行為的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="91a2e-107">Personalizations are custom objects that you add to a cube to provide a behavior that varies by user.</span></span> <span data-ttu-id="91a2e-108">個人化並非 Cube 中的永久物件，而是用戶端應用程式在使用者工作階段期間動態套用的物件。</span><span class="sxs-lookup"><span data-stu-id="91a2e-108">Personalizations are not permanent objects in the cube, but are objects that the client application applies dynamically during the user's session.</span></span> <span data-ttu-id="91a2e-109">範例包括根據存取資料的人員變更金額的貨幣、提供個別化 KPI，或一般線上購買客戶的目標建議清單。</span><span class="sxs-lookup"><span data-stu-id="91a2e-109">Examples include changing the currency of a monetary value depending on the person accessing the data, providing individualized KPIs, or a targeted suggestion list for regular customers who purchase online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91a2e-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="91a2e-110">In This Section</span></span>  
 [<span data-ttu-id="91a2e-111">通過個人化擴充 OLAP</span><span class="sxs-lookup"><span data-stu-id="91a2e-111">Extending OLAP through personalizations</span></span>](extending-olap-through-personalizations.md)  
  
 [<span data-ttu-id="91a2e-112">Analysis Services 個人化延伸模組</span><span class="sxs-lookup"><span data-stu-id="91a2e-112">Analysis Services Personalization Extensions</span></span>](analysis-services-personalization-extensions.md)  
  
 [<span data-ttu-id="91a2e-113">定義預存程式</span><span class="sxs-lookup"><span data-stu-id="91a2e-113">Defining Stored Procedures</span></span>](../../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
