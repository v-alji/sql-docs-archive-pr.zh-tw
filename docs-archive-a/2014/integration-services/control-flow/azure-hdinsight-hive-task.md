---
title: Azure HDInsight Hive 工作 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afphivetask.f1
- sql11.dts.designer.afphivetask.f1
ms.assetid: e1896c73-128a-4128-9814-3e01f7dfe19b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5905dee4a7a195a16d217b28b59cc10bb74dd9a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599133"
---
# <a name="azure-hdinsight-hive-task"></a><span data-ttu-id="4ed0a-102">Azure HDInsight Hive 工作</span><span class="sxs-lookup"><span data-stu-id="4ed0a-102">Azure HDInsight Hive Task</span></span>
<span data-ttu-id="4ed0a-103">使用 **Azure HDInsight Hive 工作** ，在 Azure HDInsight 叢集上執行 Hive 指令碼。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-103">Use the **Azure HDInsight Hive Task** to run Hive script on an Azure HDInsight cluster.</span></span>
     
<span data-ttu-id="4ed0a-104">若要新增 **Azure HDInsight Hive 工作**，請將其拖放至 SSIS 設計師，並按兩下或在其上按一下滑鼠右鍵，然後按一下 [編輯]  ，即可看到以下 [Azure HDInsight Hive Task Editor (Azure HDInsight Hive 工作編輯器)]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-104">To add an **Azure HDInsight Hive Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure HDInsight Hive Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="4ed0a-105">下列清單描述對話方塊中的欄位。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-105">The following list describes fields in this dialog box.</span></span>  
  
1.  <span data-ttu-id="4ed0a-106">針對 [HDInsightConnection]\*\*\*\* 欄位，選取現有的 Azure HDInsight 連線管理員或建立新的連線管理員，以參考用來執行指令碼的 Azure HDInsight 叢集。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-106">For the **HDInsightConnection** field, select an existing Azure HDInsight Connection Manager or create a new one that refers to the Azure HDInsight cluster used to execute the script.</span></span>
  
2.  <span data-ttu-id="4ed0a-107">針對 [AzureStorageConnection]\*\*\*\* 欄位，選取現有的 Azure 儲存體連線管理員或建立新的連線管理員，以參考與叢集相關聯的 Azure 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-107">For the **AzureStorageConnection** field, select an existing Azure Storage Connection Manager or create a new one that refers to the Azure Storage Account associated with the cluster.</span></span> <span data-ttu-id="4ed0a-108">只有在您想要下載指令碼執行輸出和錯誤記錄檔時才需要此欄位。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-108">This is only necessary if you want to download the script execution output and error logs.</span></span>
 
3.  <span data-ttu-id="4ed0a-109">針對 [BlobContainer]\*\*\*\* 欄位，指定與叢集相關聯的儲存體容器名稱。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-109">For the **BlobContainer** field, specify the storage container name associated with the cluster.</span></span> <span data-ttu-id="4ed0a-110">只有在您想要下載指令碼執行輸出和錯誤記錄檔時才需要此欄位。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-110">This is only necessary if you want to download the script execution output and error logs.</span></span>
  
4.  <span data-ttu-id="4ed0a-111">針對 [LocalLogFolder]\*\*\*\* 欄位，指定要下載指令碼執行輸出和錯誤記錄檔的目標資料夾。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-111">For the **LocalLogFolder** field, specify the folder to which the script execution output and error logs will be downloaded to.</span></span> <span data-ttu-id="4ed0a-112">只有在您想要下載指令碼執行輸出和錯誤記錄檔時才需要此欄位。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-112">This is only necessary if you want to download the script execution output and error logs.</span></span>   
  
5.  <span data-ttu-id="4ed0a-113">有兩個方法可以指定要執行的 Hive 指令碼：</span><span class="sxs-lookup"><span data-stu-id="4ed0a-113">There are two ways to specify the Hive script to execute:</span></span>
  
    1.  <span data-ttu-id="4ed0a-114">**內嵌指令碼**：透過在 [輸入指令碼]\*\*\*\* 對話方塊中鍵入要執行的內嵌指令碼，來指定 [指令碼]\*\*\*\* 欄位。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-114">**In-line script**: Specify the **Script** field by typing in-line the script to execute in the **Enter Script** dialog box.</span></span>
  
    2.  <span data-ttu-id="4ed0a-115">**指令檔**：將指令檔上傳至 Azure Blob 儲存體，並指定 [BlobName]\*\*\*\* 欄位。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-115">**Script file**: Upload the script file to Azure Blob Storage and specify the **BlobName** field.</span></span> <span data-ttu-id="4ed0a-116">如果 blob 不在與 HDInsight 叢集相關聯的預設儲存體帳戶或容器中，則必須指定 [ExternalStorageAccountName]\*\*\*\* 和 [ExternalBlobContainer]\*\*\*\* 欄位。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-116">If the blob is not in the default storage account or container associated with the HDInsight cluster, the **ExternalStorageAccountName** and **ExternalBlobContainer** fields must be specified.</span></span> <span data-ttu-id="4ed0a-117">若是外部 blob，請確定它已設定為可公開存取。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-117">For an external blob, make sure that it is configured as publicly accessible.</span></span>  
  
     <span data-ttu-id="4ed0a-118">如果指定兩者，則會使用指令檔並忽略內嵌指令碼。</span><span class="sxs-lookup"><span data-stu-id="4ed0a-118">If both are specified, script file will be used and the in-line script will be ignored.</span></span>
