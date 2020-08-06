---
title: 步驟 3：修改 Directory 屬性組態值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a71a7a181322d60caca98da4ddf3261cbce99c9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593435"
---
# <a name="step-3-modifying-the-directory-property-configuration-value"></a><span data-ttu-id="6228c-102">步驟 3：修改 Directory 屬性組態值</span><span class="sxs-lookup"><span data-stu-id="6228c-102">Step 3: Modifying the Directory Property Configuration Value</span></span>
  <span data-ttu-id="6228c-103">在這項工作中，您會修改儲存在 SSISTutorial.dtsConfig 檔案中有關套件層級變數 `User::varFolderName`之 Value 屬性的組態設定。</span><span class="sxs-lookup"><span data-stu-id="6228c-103">In this task, you will modify the configuration setting, stored in the SSISTutorial.dtsConfig file, for the Value property of the package-level variable `User::varFolderName`.</span></span> <span data-ttu-id="6228c-104">這個變數會更新 Foreach 迴圈容器的 Directory 屬性。</span><span class="sxs-lookup"><span data-stu-id="6228c-104">The variable updates the Directory property of the Foreach Loop container.</span></span> <span data-ttu-id="6228c-105">修改過的值將指向 `New Sample Data` 您在上一項工作中建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6228c-105">The modified value will point to the `New Sample Data` folder that you created in the previous task.</span></span> <span data-ttu-id="6228c-106">在修改組態設定及執行套件之後，該變數將使用從組態檔擴展的值而不是原本設定在套件中的目錄值來更新 Directory 屬性。</span><span class="sxs-lookup"><span data-stu-id="6228c-106">After you modify the configuration setting and run the package, the Directory property will be updated by the variable, using the value populated from the configuration file instead of the directory value originally configured in the package.</span></span>  
  
### <a name="to-modify-the-configuration-setting-of-the-directory-property"></a><span data-ttu-id="6228c-107">若要修改 Directory 屬性的組態設定</span><span class="sxs-lookup"><span data-stu-id="6228c-107">To modify the configuration setting of the Directory property</span></span>  
  
1.  <span data-ttu-id="6228c-108">在記事本或任何其他文字編輯器中，尋找及開啟您在上一項工作中使用封裝組態精靈所建立的 SSISTutorial.dtsConfig 組態檔。</span><span class="sxs-lookup"><span data-stu-id="6228c-108">In Notepad or any other text editor, locate and open the SSISTutorial.dtsConfig configuration file that you created by using the Package Configuration Wizard in the previous task.</span></span>  
  
2.  <span data-ttu-id="6228c-109">變更**ConfiguredValue**元素的值，使其符合 `New Sample Data` 您在上一個工作中建立的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="6228c-109">Change the value of the **ConfiguredValue** element to match the path of the `New Sample Data` folder that you created in the previous task.</span></span> <span data-ttu-id="6228c-110">請勿用引號括住路徑。</span><span class="sxs-lookup"><span data-stu-id="6228c-110">Do not surround the path in quotes.</span></span> <span data-ttu-id="6228c-111">如果 `New Sample Data` 資料夾位於磁片磁碟機的根層級 (例如 C： \\) ，則更新的 XML 應該類似于下列範例：</span><span class="sxs-lookup"><span data-stu-id="6228c-111">If the `New Sample Data` folder is at the root level of your drive (for example, C:\\), the updated XML should be similar to the following sample:</span></span>  
  
     `<?xml version="1.0"?><DTSConfiguration><DTSConfigurationHeading><DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFA61D3FA}" GeneratedDate="6/10/2012 8:16:50 AM"/></DTSConfigurationHeading><Configuration ConfiguredType="Property" Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"><ConfiguredValue></ConfiguredValue></Configuration></DTSConfiguration>`  
  
     <span data-ttu-id="6228c-112">當然，您的檔案中的標題資訊、、 `GeneratedBy` `GeneratedFromPackageID` 和**GeneratedDate**會有所不同。</span><span class="sxs-lookup"><span data-stu-id="6228c-112">The heading information, `GeneratedBy`, `GeneratedFromPackageID`, and **GeneratedDate** will be different in your file, of course.</span></span> <span data-ttu-id="6228c-113">要注意的元素是 `Configuration` 元素。</span><span class="sxs-lookup"><span data-stu-id="6228c-113">The element to note is the `Configuration` element.</span></span> <span data-ttu-id="6228c-114">`Value` 變數的 `User::varFolderName` 屬性現在將會包含 C:\New Sample Data。</span><span class="sxs-lookup"><span data-stu-id="6228c-114">The `Value` property of the variable, `User::varFolderName`, now contains C:\New Sample Data.</span></span>  
  
3.  <span data-ttu-id="6228c-115">儲存變更，然後關閉文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="6228c-115">Save the change, and then close the text editor.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6228c-116">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="6228c-116">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6228c-117">步驟 4：測試第 5 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="6228c-117">Step 4: Testing the Lesson 5 Tutorial Package</span></span>](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
