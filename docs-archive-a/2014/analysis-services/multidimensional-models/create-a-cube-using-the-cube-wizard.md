---
title: 使用 Cube Wizard 建立 Cube |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], creating
ms.assetid: d46d659c-3a4e-4364-94ac-f5eb6ba0ec25
author: minewiskan
ms.author: owend
ms.openlocfilehash: 441c296c0fd71b2a9c2b8332743da6224839a471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705641"
---
# <a name="create-a-cube-using-the-cube-wizard"></a><span data-ttu-id="ccd2e-102">使用 Cube 精靈來建立 Cube</span><span class="sxs-lookup"><span data-stu-id="ccd2e-102">Create a Cube Using the Cube Wizard</span></span>
  <span data-ttu-id="ccd2e-103">您可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的 [Cube 精靈] 來建立新的 Cube。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-103">You can create a new cube by using the Cube Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-create-a-new-cube"></a><span data-ttu-id="ccd2e-104">建立新的 Cube</span><span class="sxs-lookup"><span data-stu-id="ccd2e-104">To create a new cube</span></span>  
  
1.  <span data-ttu-id="ccd2e-105">在**方案總管**中，以滑鼠右鍵按一下 [ **cube**]，然後按一下 [**新增 Cube**]。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-105">In **Solution Explorer**, right-click **Cubes**, and then click **New Cube**.</span></span>  
  
2.  <span data-ttu-id="ccd2e-106">在 [Cube 精靈] 的 [選取建立方法]\*\*\*\* 頁面上，選取 [使用現有的資料表]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-106">On the **Select Creation Method** page of the Cube Wizard, select **Use existing tables**, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ccd2e-107">您可能偶爾必須在不使用現有資料表的情況下建立 Cube。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-107">You might occasionally have to create a cube without using existing tables.</span></span> <span data-ttu-id="ccd2e-108">若要建立空白的 Cube，請選取 [建立空白 Cube]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-108">To create an empty cube, select **Create an empty cube**.</span></span> <span data-ttu-id="ccd2e-109">若要產生資料表，請選取 [在資料來源中建立資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-109">To generate tables, select **Generate tables in the data source**.</span></span>  
  
3.  <span data-ttu-id="ccd2e-110">在 [選取量值群組資料表]\*\*\*\* 頁面上，執行下列程序：</span><span class="sxs-lookup"><span data-stu-id="ccd2e-110">On the **Select Measure Group Tables** page, do the following procedures:</span></span>  
  
    1.  <span data-ttu-id="ccd2e-111">在 [資料來源檢視]\*\*\*\* 清單中，選取資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-111">In the **Data source view** list, select a data source view.</span></span>  
  
    2.  <span data-ttu-id="ccd2e-112">在 [量值群組資料表]\*\*\*\* 清單中，選取將用來建立量值群組的資料表。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-112">In the **Measure group tables** list, select the tables that will be used to create measure groups.</span></span>  
  
    3.  <span data-ttu-id="ccd2e-113">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-113">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="ccd2e-114">在 [選取量值]\*\*\*\* 頁面上，選取您要包含在 Cube 中的量值，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-114">On the **Select Measures** page, select the measures that you want to include in the cube, and then click **Next**.</span></span>  
  
     <span data-ttu-id="ccd2e-115">(選擇性) 您可以變更量值和量值群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-115">Optionally, you can change the names of the measures and measure groups.</span></span>  
  
5.  <span data-ttu-id="ccd2e-116">在 [選取現有維度]\*\*\*\* 頁面上，選取您要包含在 Cube 中的現有維度，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-116">On the **Select Existing Dimensions** page, select the existing dimensions to include in the cube, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ccd2e-117">如果維度已經存在任何選取量值群組的資料庫中，就會顯示 [選取現有維度]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-117">The **Select Existing Dimensions** page appears if dimensions already exist in the database for any of the selected measure groups.</span></span>  
  
6.  <span data-ttu-id="ccd2e-118">在 [選取新維度]\*\*\*\* 頁面上，選取要建立的新維度，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-118">On the **Select New Dimensions** page, select the new dimensions to create, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ccd2e-119">如果有任何資料表適合當作維度資料表，而且這些資料表尚未由現有的維度使用，就會顯示 [選取新維度]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-119">The **Select New Dimensions** page appears if any tables would be good candidates for dimension tables, and the tables have not already been used by existing dimensions.</span></span>  
  
7.  <span data-ttu-id="ccd2e-120">在 [選取遺漏維度索引鍵]\*\*\*\* 頁面上，選取維度的索引鍵，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-120">On the **Select Missing Dimension Keys** page, select a key for the dimension, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ccd2e-121">如果您指定的任何維度資料表沒有定義索引鍵，就會顯示 [選取遺漏維度索引鍵]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-121">The **Select Missing Dimension Keys** page appears if any of the dimension tables that you specified do not have a key defined.</span></span>  
  
8.  <span data-ttu-id="ccd2e-122">在 [正在完成精靈]\*\*\*\* 頁面上，輸入新 Cube 的名稱，然後檢閱 Cube 的結構。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-122">On the **Completing the Wizard** page, enter a name for the new cube and review the cube structure.</span></span> <span data-ttu-id="ccd2e-123">如果您要進行任何變更，按一下 [上一步]\*\*\*\*，否則，按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-123">If you want to make changes, click **Back**; otherwise, click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ccd2e-124">在您完成「Cube 精靈」之後，可以使用「Cube 設計師」來設定 Cube。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-124">You can use Cube Designer after you complete the Cube Wizard to configure the cube.</span></span> <span data-ttu-id="ccd2e-125">此外，您也可以使用「維度設計師」，在您建立的維度中加入、移除和設定屬性與階層。</span><span class="sxs-lookup"><span data-stu-id="ccd2e-125">You can also use Dimension Designer to add, remove, and configure attributes and hierarchies in the dimensions that you created.</span></span>  
  
  
