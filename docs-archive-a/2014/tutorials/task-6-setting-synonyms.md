---
title: 工作6：設定同義字 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b7d35ee9-d1c9-41d9-bbc5-0ca7db93e54d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bde0c0ec7f230ba2325aa01328b191fd8fd67fa6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584893"
---
# <a name="task-6-setting-synonyms"></a><span data-ttu-id="70a08-102">工作 6：設定同義字</span><span class="sxs-lookup"><span data-stu-id="70a08-102">Task 6: Setting Synonyms</span></span>
  <span data-ttu-id="70a08-103">在這項工作中，您會將**Country**網域的兩個定義域值（**美國**和**美國**）設定為以**美國**做為前置值的同義字。</span><span class="sxs-lookup"><span data-stu-id="70a08-103">In this task, you set two domain values, **USA** and **United States**, of the **Country** domain as synonyms with **United States** as the leading value.</span></span> <span data-ttu-id="70a08-104">建立**國家/地區**網域時，已選取 [**使用前置值**] 選項，所以**country**網域的任何**美國**值都會輸出為 [**美國**]， ([美國] 是前置值) 。</span><span class="sxs-lookup"><span data-stu-id="70a08-104">Since the **Use Leading Values** option was selected when creating the **Country** domain, any **USA** values for the **Country** domain will be output as **United States** (as United States is the leading value).</span></span> <span data-ttu-id="70a08-105">如需詳細資訊，請參閱[變更定義域值](https://msdn.microsoft.com/library/hh510408.aspx)。</span><span class="sxs-lookup"><span data-stu-id="70a08-105">See [Change Domain Values](https://msdn.microsoft.com/library/hh510408.aspx) for more details.</span></span>

1.  <span data-ttu-id="70a08-106">從網域清單中選取 [**國家/地區**]。</span><span class="sxs-lookup"><span data-stu-id="70a08-106">Select **Country** from the list of domains.</span></span>

2.  <span data-ttu-id="70a08-107">切換至 [**定義域值**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="70a08-107">Switch to the **Domain Values** tab.</span></span>

3.  <span data-ttu-id="70a08-108">按一下工具列上的 [**加入新的定義域值**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="70a08-108">Click **Add new domain value** button on the toolbar.</span></span>

4.  <span data-ttu-id="70a08-109">輸入**USA**作為值，然後按**enter**。</span><span class="sxs-lookup"><span data-stu-id="70a08-109">Type **USA** for the value and press **ENTER**.</span></span>

5.  <span data-ttu-id="70a08-110">使用 CTRL 或 SHIFT**鍵，以**滑鼠右鍵按一下選取的專案 **，然後按一下**[**設為同義字**]。</span><span class="sxs-lookup"><span data-stu-id="70a08-110">Multiselect **United States** and **USA** using CTRL or SHIFT keys, right-click the selected items, and then click **Set as Synonyms**.</span></span> <span data-ttu-id="70a08-111">DQS 會將這些值分組在一起，並將其中一個值指定為將用來取代其他值的前置值。</span><span class="sxs-lookup"><span data-stu-id="70a08-111">DQS groups these values and designate one of the values as the leading value that the other values are replaced with.</span></span>

     <span data-ttu-id="70a08-112">![[設為同義字] 功能表](../../2014/tutorials/media/et-settingsynonyms-01.jpg "[設為同義字] 功能表")</span><span class="sxs-lookup"><span data-stu-id="70a08-112">![Set as Synonyms Menu](../../2014/tutorials/media/et-settingsynonyms-01.jpg "Set as Synonyms Menu")</span></span>

6.  <span data-ttu-id="70a08-113">請注意，**美國**已設定為前置值。</span><span class="sxs-lookup"><span data-stu-id="70a08-113">Notice that **United States** is set as the leading value.</span></span> <span data-ttu-id="70a08-114">如果您想要讓 USA 成為前置值，可以用滑鼠右鍵按一下 [美國]，然後選取 [**設定為前置**選項]。</span><span class="sxs-lookup"><span data-stu-id="70a08-114">If you want USA to be the leading value, you can right-click on USA and select **Set as Leading** option.</span></span> <span data-ttu-id="70a08-115">在本教學課程中，我們會使用**美國**做為前置值。</span><span class="sxs-lookup"><span data-stu-id="70a08-115">For this tutorial, we use **United States** as the leading value.</span></span>

     <span data-ttu-id="70a08-116">![United States 和 USA 為同義字](../../2014/tutorials/media/et-settingsynonyms-02.jpg "United States 和 USA 為同義字")</span><span class="sxs-lookup"><span data-stu-id="70a08-116">![United States and USA as Synonyms](../../2014/tutorials/media/et-settingsynonyms-02.jpg "United States and USA as Synonyms")</span></span>

## <a name="next-step"></a><span data-ttu-id="70a08-117">後續步驟</span><span class="sxs-lookup"><span data-stu-id="70a08-117">Next Step</span></span>
 [<span data-ttu-id="70a08-118">工作 7：建立複合定義域</span><span class="sxs-lookup"><span data-stu-id="70a08-118">Task 7: Creating a Composite Domain</span></span>](../../2014/tutorials/task-7-creating-a-composite-domain.md)


