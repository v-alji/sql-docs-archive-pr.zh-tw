---
title: 將資料行加入至採礦結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- columns [data mining], mining structure columns
- adding columns
ms.assetid: 3f879344-9f66-4178-851a-e8c5ccccf4cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 093d78b36ab3aae6600b890a8137025c9dc9134e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598063"
---
# <a name="add-columns-to-a-mining-structure"></a><span data-ttu-id="0d273-102">將資料行加入至採礦結構</span><span class="sxs-lookup"><span data-stu-id="0d273-102">Add Columns to a Mining Structure</span></span>
  <span data-ttu-id="0d273-103">使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的資料採礦設計師，即可將資料行加入至您在資料採礦精靈中定義的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="0d273-103">Use Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to add columns to a mining structure after you have defined it in the Data Mining Wizard.</span></span> <span data-ttu-id="0d273-104">您可以加入已存在於用來定義採礦結構之資料來源檢視中的任何資料行。</span><span class="sxs-lookup"><span data-stu-id="0d273-104">You can add any column that exists in the data source view that was used to define the mining structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d273-105">您可以將資料行的多份複本加入採礦結構；不過應該避免在同一模型中使用一個以上的資料行執行個體，以避免在來源及衍生的資料行之間產生錯誤的關聯。</span><span class="sxs-lookup"><span data-stu-id="0d273-105">You can add multiple copies of columns to a mining structure; however, you should avoid using more than one instance of the column within the same model, to avoid false correlations between the source and the derived column.</span></span>  
  
### <a name="to-add-a-column-to-a-mining-structure"></a><span data-ttu-id="0d273-106">若要將資料行加入至採礦結構</span><span class="sxs-lookup"><span data-stu-id="0d273-106">To add a column to a mining structure</span></span>  
  
1.  <span data-ttu-id="0d273-107">選取資料採礦設計師中的 **[採礦結構]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0d273-107">Select the **Mining Structure** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="0d273-108">以滑鼠右鍵按一下採礦結構，並選取 [加入資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d273-108">Right-click the mining structure and select **Add a Column**.</span></span>  
  
     <span data-ttu-id="0d273-109">就會開啟 **[選取資料行]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0d273-109">The **Select a Column** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="0d273-110">在 **[來源資料表]** 之下，選取資料來源檢視中該資料行所在的資料表。</span><span class="sxs-lookup"><span data-stu-id="0d273-110">Under **Source table**, select the table in the data source view where the column resides.</span></span>  
  
4.  <span data-ttu-id="0d273-111">在 **[來源資料行]** 之下，選取您要加入至採礦結構的資料行。</span><span class="sxs-lookup"><span data-stu-id="0d273-111">Under **Source column**, select the column that you want to add to the mining structure.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="0d273-112">如果您要加入的資料行已存在，其副本會併入結構中，並在名稱後面附加「1」。</span><span class="sxs-lookup"><span data-stu-id="0d273-112">If you add a column that already exists, a copy will be included in the structure, and the name appended with a "1".</span></span> <span data-ttu-id="0d273-113">您可藉由在採礦結構資料行的 **[名稱]** 屬性中輸入新名稱，將複製資料行的名稱變更為更具描述性的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d273-113">You can change the name of the copied column to something more descriptive by typing a new name in the **Name** property of the mining structure column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d273-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d273-114">See Also</span></span>  
 [<span data-ttu-id="0d273-115">採礦結構工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="0d273-115">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
