---
title: 其他檔案 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio], miscellaneous
- projects [SQL Server Management Studio], files
- solutions [SQL Server Management Studio], files
- miscellaneous files folder [SQL Server]
ms.assetid: 3c952b0b-8f5f-4d86-9e5d-616c10b9df0d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f65c04326e791fa3684a06213c3042a42f2f2ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702246"
---
# <a name="miscellaneous-files"></a><span data-ttu-id="9a438-102">其他檔案</span><span class="sxs-lookup"><span data-stu-id="9a438-102">Miscellaneous Files</span></span>
  <span data-ttu-id="9a438-103">任何專案的外部檔案稱為「其他檔案」  (Miscellaneous file)。</span><span class="sxs-lookup"><span data-stu-id="9a438-103">Files that are external to any project are called *miscellaneous files*.</span></span> <span data-ttu-id="9a438-104">您開啟了某個方案之後，便可以開啟和修改關聯於這個專案的其他檔案。</span><span class="sxs-lookup"><span data-stu-id="9a438-104">When you have a solution open, you can open and modify miscellaneous files related to the project.</span></span> <span data-ttu-id="9a438-105">如果副檔名沒有相關的專案程式碼編輯器，這個檔案便會分類為其他檔案。</span><span class="sxs-lookup"><span data-stu-id="9a438-105">A file is classified as a miscellaneous file if the file extension is not associated with the project code editor.</span></span> <span data-ttu-id="9a438-106">例如，在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指令碼專案中，會將副檔名為 .txt 或 .mdx 的檔案當作其他檔案來處理。</span><span class="sxs-lookup"><span data-stu-id="9a438-106">For example, in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Scripts Project, files with the extension .txt or .mdx will be treated as miscellaneous files.</span></span> <span data-ttu-id="9a438-107">在 MDX 專案中，副檔名為 .txt 或 .sql 的檔案會當作其他檔案來處理。</span><span class="sxs-lookup"><span data-stu-id="9a438-107">In an MDX project, files with the extension of .txt or .sql will be treated as miscellaneous files.</span></span> <span data-ttu-id="9a438-108">若要使副檔名與程式碼編輯器相關聯，請參閱使副檔名與程式[代碼編輯器產生關聯](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="9a438-108">To associate a file extension with a code editor, see [Associate File Extensions to a Code Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).</span></span>  
  
 <span data-ttu-id="9a438-109">基於許多原因，能夠將其他檔案加入專案中非常有用。</span><span class="sxs-lookup"><span data-stu-id="9a438-109">There are a number of reasons why it is useful to be able to add miscellaneous files to your project.</span></span> <span data-ttu-id="9a438-110">您可能會有某個檔案不一定是已獲辨識的指令碼，但對於方案的開發而言，卻不可或缺。</span><span class="sxs-lookup"><span data-stu-id="9a438-110">You might have a file that is not necessarily a recognized script but integral to the solution's development.</span></span> <span data-ttu-id="9a438-111">常見的範例包括開發附註或指示、資料檔，以及程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="9a438-111">Common examples include development notes or instructions, data files, and code clips.</span></span>  
  
 <span data-ttu-id="9a438-112">其他檔案的運用非常靈活。</span><span class="sxs-lookup"><span data-stu-id="9a438-112">Miscellaneous files provide flexibility.</span></span> <span data-ttu-id="9a438-113">例如，假設您有一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指令碼專案，其中有許多在資料庫中建立資料表和預存程序的指令碼。</span><span class="sxs-lookup"><span data-stu-id="9a438-113">For example, suppose you have a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Scripts Project that has several scripts for creation of tables and stored procedures in your database.</span></span> <span data-ttu-id="9a438-114">另外，您也有許多資料表的資料檔，副檔名為 .BCP，還有在 README.TXT 檔內的執行指示。</span><span class="sxs-lookup"><span data-stu-id="9a438-114">You also have several data files for the tables with file extensions .BCP and execution instructions in a README.TXT file.</span></span> <span data-ttu-id="9a438-115">您可以將資料和 README 檔當作其他檔案附加至專案，以便利用專案系統的原始檔控制和其他功能。</span><span class="sxs-lookup"><span data-stu-id="9a438-115">You can attach the data and the README files as miscellaneous files to the project to take advantage of source control and other features of the project system.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="9a438-116">功能表和工具列會隨著所開啟之檔案的格式而不同。</span><span class="sxs-lookup"><span data-stu-id="9a438-116">menus and toolbars change according to the format of the file you open.</span></span> <span data-ttu-id="9a438-117">例如，當您開啟文字檔時，會出現 [文字編輯器] 工具列。</span><span class="sxs-lookup"><span data-stu-id="9a438-117">When you open a text file, for example, the Text Editor toolbar appears.</span></span> <span data-ttu-id="9a438-118">如果您開啟 XML 結構描述檔，便會開啟 [XML 結構描述] 工具列。</span><span class="sxs-lookup"><span data-stu-id="9a438-118">If you open an XML Schema file, the XML Schema toolbar appears.</span></span> <span data-ttu-id="9a438-119">當您編輯 XML 結構描述時，無法使用 [文字編輯器] 工具列。</span><span class="sxs-lookup"><span data-stu-id="9a438-119">While editing your XML Schema, the Text Editor toolbar is unavailable.</span></span> <span data-ttu-id="9a438-120">當您在專案檔和其他檔案之間切換時，其他檔案的相關命令和工具列會取代所有專案相關命令和工具列。</span><span class="sxs-lookup"><span data-stu-id="9a438-120">When you switch between a project file and a miscellaneous file, all project-related commands and toolbars are replaced by those relevant to the miscellaneous file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a438-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a438-121">See Also</span></span>  
 <span data-ttu-id="9a438-122">[管理方案和專案的檔案](files-that-manage-solutions-and-projects.md) </span><span class="sxs-lookup"><span data-stu-id="9a438-122">[Files That Manage Solutions and Projects](files-that-manage-solutions-and-projects.md) </span></span>  
 <span data-ttu-id="9a438-123">[解決方案 &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="9a438-123">[Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="9a438-124">專案 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="9a438-124">Projects &#40;SQL Server Management Studio&#41;</span></span>](projects-sql-server-management-studio.md)  
  
  
