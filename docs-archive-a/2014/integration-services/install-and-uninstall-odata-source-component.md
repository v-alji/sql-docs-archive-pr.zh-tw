---
title: 安裝和卸載 OData 來源元件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fad0a86c6226f408b0495569d0a853dd7340aeca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596192"
---
# <a name="install-and-uninstall-odata-source-component"></a><span data-ttu-id="318e9-102">安裝及解除安裝 OData 來源元件</span><span class="sxs-lookup"><span data-stu-id="318e9-102">Install and Uninstall OData Source Component</span></span>
  <span data-ttu-id="318e9-103">本主題提供在電腦上安裝或移除 OData 來源元件的指示。</span><span class="sxs-lookup"><span data-stu-id="318e9-103">This topic provides instructions for installing or removing OData Source Component on your computer.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="318e9-104">安裝</span><span class="sxs-lookup"><span data-stu-id="318e9-104">Installation</span></span>  
 <span data-ttu-id="318e9-105">OData 來源元件要求必須在電腦上安裝以下必要元件。</span><span class="sxs-lookup"><span data-stu-id="318e9-105">The OData Source Component requires following prerequisite components to be installed on your computer.</span></span>  
  
-   <span data-ttu-id="318e9-106">SQL Server Data Tools (為了設計封裝)</span><span class="sxs-lookup"><span data-stu-id="318e9-106">SQL Server Data Tools (to design packages)</span></span>  
  
-   <span data-ttu-id="318e9-107">SQL Server Integration Services (為了在 Visual Studio 外面執行封裝)</span><span class="sxs-lookup"><span data-stu-id="318e9-107">SQL Server Integration Services (to run packages outside Visual Studio)</span></span>  
  
 <span data-ttu-id="318e9-108">若要安裝 OData 來源元件，請下載[SQL Server 2014 功能套件](https://go.microsoft.com/fwlink/p/?LinkId=391999)，然後執行下列其中一個 MSI 檔案。</span><span class="sxs-lookup"><span data-stu-id="318e9-108">To install the OData Source Component, download [SQL Server 2014 Feature Pack](https://go.microsoft.com/fwlink/p/?LinkId=391999) and run one of the following MSI files.</span></span>  
  
-   <span data-ttu-id="318e9-109">64 位元平台適用的 ODataSourceForSQLServer2014-amd64.msi</span><span class="sxs-lookup"><span data-stu-id="318e9-109">ODataSourceForSQLServer2014-amd64.msi for 64bit platforms</span></span>  
  
-   <span data-ttu-id="318e9-110">32 位元平台適用的 ODataSourceForSQLServer2014-x86.msi</span><span class="sxs-lookup"><span data-stu-id="318e9-110">ODataSourceForSQLServer2014-x86.msi for 32bit platforms</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="318e9-111">64 位元安裝程式將會同時安裝 32 位元和 64 位元版的 OData 來源元件。</span><span class="sxs-lookup"><span data-stu-id="318e9-111">The 64bit installer will install both 32bit and 64bit versions of the OData Source Component.</span></span> <span data-ttu-id="318e9-112">如果您使用 32 位元作業系統，您只需要執行 32 位元的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="318e9-112">You only need to run the 32bit installer if you are using a 32bit OS.</span></span>  
  
## <a name="uninstallation"></a><span data-ttu-id="318e9-113">解除安裝</span><span class="sxs-lookup"><span data-stu-id="318e9-113">Uninstallation</span></span>  
 <span data-ttu-id="318e9-114">您可以從 [**程式和功能**] 功能表中卸載 OData 來源元件。</span><span class="sxs-lookup"><span data-stu-id="318e9-114">The OData Source component can be uninstalled from the **Programs and Features** menu.</span></span> <span data-ttu-id="318e9-115">尋找**MICROSOFT SQL SERVER SSIS OData 來源元件 (x64) **專案，然後按一下 [**卸載**]。</span><span class="sxs-lookup"><span data-stu-id="318e9-115">Find the **Microsoft SQL Server SSIS OData Source Component (x64)** entry and click **Uninstall**.</span></span>  
  
  
