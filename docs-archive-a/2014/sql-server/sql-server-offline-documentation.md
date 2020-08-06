---
title: SQL Server 2014 的離線檔
description: 瞭解如何安裝 SQL Server 2014 的離線檔。 使用 SQL Server Management Studio (SSMS) 來檢視離線內容。
ms.prod: sql
ms.technology: install
ms.topic: conceptual
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
author: markingmyname
ms.author: maghan
ms.reviewer: carlrab
ms.date: 07/19/2020
ms.openlocfilehash: bfd4adc658a203f8e2d22ef77ce0381084e36363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595374"
---
# <a name="install-sql-server-2014-offline-documentation"></a>安裝 SQL Server 2014 離線檔

本文說明如何下載和觀看離線 SQL Server 2014 內容。 離線內容可讓您在沒有網際網路連線的情況下存取文件 (但是一開始需要網際網路連線來下載文件)。

這項技術牽涉到使用 SQL Server Management Studio (SSMS) **的 [說明**] 功能表，以存取說明檢視器公用程式 ( # A0) 。

離線檔適用于2012-2019 範圍內的 SQL Server，也可能是其他較新版本的版本。 雖然您可[線上檢視舊版內容](https://docs.microsoft.com/previous-versions/sql/)，但離線選項提供一種存取舊版內容的便利方式。

- [SQL Server 2014](#sql-server-2014-offline-content)
- [SQL Server 2012](#sql-server-2012-offline-content)

如 SQL Server 2016 和更新版本，請參閱其版本特定的檔，以瞭解這些版本如何處理其離線檔。

## <a name="sql-server-2014-offline-content"></a>SQL Server 2014 離線內容

> [!IMPORTANT]
> SQL 2014 Transact-SQL 內容僅供離線使用。

下列步驟說明如何載入 SQL Server 2014 的離線內容。

1. 從下載中心下載 [Microsoft SQL Server 2014 的防火牆和 Proxy 受限環境產品文件](https://www.microsoft.com/download/details.aspx?id=42557) \(英文\) 內容，並將其儲存到資料夾。

2. 解壓縮檔案以查看 *.msha*檔案。

   ![SQL Server 2014 說明文件安裝檔](../sql-server/media/sql-server-offline-documentation/sql-2014-help-content-setup-msha.png)

3. 在 SSMS 中，選取 [說明] 功能表上的 [加入和移除說明內容]。

   ![說明檢視器新增移除內容](../sql-server/media/sql-server-offline-documentation/add-remove-content.png)

   說明檢視器會開啟至 [管理內容] 索引標籤。

4. 若要安裝最新說明內容，請選擇 [安裝來源] 底下的 [磁碟]，然後選擇省略符號 (...)。

   ![說明檢視器管理內容磁碟來源](../sql-server/media/sql-server-offline-documentation/install-source-disk.png)

   > [!NOTE]
   > [管理內容] 索引標籤上的 [本機存放區路徑] 會顯示內容在本機電腦上的所在位置。 若要變更位置，請選取 [移動]，並在 [到] 欄位中輸入不同資料夾路徑，然後選取 [確定]。
   如果變更本機存放區路徑後，說明安裝失敗，請關閉並重新開啟 Help Viewer。 請確定新的位置出現在本機存放區路徑中，然後再次嘗試安裝。

5. 尋找已解壓縮內容所在的資料夾。 選取資料夾中的 [HelpContentSetup.msha] 檔案，然後選取 [開啟]。

   ![開啟 SQL Server 2014 Help Content Setup.msha 檔案](../sql-server/media/sql-server-offline-documentation/sql-2014-open-msha.png)

6. 在搜尋列中輸入 *sql server 2014*。 當您看到有 2014 內容可供使用之後，選取您想要安裝至 [說明檢視器] 之每個內容套件 (書籍) 旁邊的 [新增]，然後選取 [更新]。

   ![[說明檢視器] 中的 SQL Server 2014 書籍搜尋](../sql-server/media/sql-server-offline-documentation/sql-2014-search.png)

   ![[說明檢視器] 中的 SQL Server 2014 書籍新增與更新](../sql-server/media/sql-server-offline-documentation/sql-2014-add-update.png)

    > [!NOTE]
    > 如果說明檢視器凍結 (在新增內容時停止回應) ，請將%LOCALAPPDATA%\Microsoft\HelpViewer2.x\ 中的快取 LastRefreshed = " \<mm/dd/yyyy> 00:00:00" 行 HlpViewer_SSMSx_en-us. settings 或 HlpViewer_VisualStudiox_en-us. 設定檔案變更為未來的某個日期。 如需此問題的詳細資訊，請參閱 [Visual Studio 說明檢視器凍結在啟動顯示畫面上](/visualstudio/welcome-to-visual-studio)。

7. 您可以在左側內容窗格底下搜尋 *sql server 2014*，以確認是否已安裝 SQL Server 2014 內容。

   ![SQL Server 2014 書籍已自動更新](../sql-server/media/sql-server-offline-documentation/sql-2014-content.png)

## <a name="sql-server-2012-offline-content"></a>SQL Server 2012 離線內容

下列步驟說明如何載入 SQL Server 2012 的離線內容

1. 從下載中心下載 [Microsoft SQL Server 2012 的防火牆和 Proxy 受限環境產品文件](https://www.microsoft.com/download/details.aspx?id=35750) \(英文\) 內容，並將其儲存到資料夾。

2. 解壓縮檔案以查看 *.msha*檔案。

   ![SQL Server 2012 說明內容安裝程式檔案](../sql-server/media/sql-server-offline-documentation/sql-2012-help-content-setup-msha.png)

3. 在 SSMS 中，選取 [說明] 功能表上的 [加入和移除說明內容]。

   ![說明檢視器新增移除內容](../sql-server/media/sql-server-offline-documentation/add-remove-content.png)

   說明檢視器會開啟至 [管理內容] 索引標籤。

4. 若要安裝最新說明內容，請選擇 [安裝來源] 底下的 [磁碟]，然後選擇省略符號 (...)。

   ![說明檢視器管理內容磁碟來源](../sql-server/media/sql-server-offline-documentation/install-source-disk.png)

   > [!NOTE]
   > [管理內容] 索引標籤上的 [本機存放區路徑] 會顯示內容在本機電腦上的所在位置。 若要變更位置，請選取 [移動]，並在 [到] 欄位中輸入不同資料夾路徑，然後選取 [確定]。
   如果變更本機存放區路徑後，說明安裝失敗，請關閉並重新開啟 Help Viewer。 請確定新的位置出現在本機存放區路徑中，然後再次嘗試安裝。

5. 尋找已解壓縮內容所在的資料夾。 選取資料夾中的 [HelpContentSetup.msha] 檔案，然後選取 [開啟]。

   ![開啟 SQL Server 2012 Help Content Setup.msha 檔案](../sql-server/media/sql-server-offline-documentation/sql-2012-open-msha.png)

6. 在搜尋列中輸入 *sql server 2012*。 當您看到有 2012 內容可供使用之後，選取您想要安裝至 [說明檢視器] 之每個內容套件 (書籍) 旁邊的 [新增]，然後選取 [更新]。

   ![[說明檢視器] 中的 SQL Server 2012 書籍搜尋](../sql-server/media/sql-server-offline-documentation/sql-2012-search.png)

   ![[說明檢視器] 中的 SQL Server 2012 書籍新增與更新](../sql-server/media/sql-server-offline-documentation/sql-2012-add-update.png)

    > [!NOTE]
    > 如果說明檢視器凍結 (在新增內容時停止回應) ，請將%LOCALAPPDATA%\Microsoft\HelpViewer2.x\ 中的快取 LastRefreshed = " \<mm/dd/yyyy> 00:00:00" 行 HlpViewer_SSMSx_en-us. settings 或 HlpViewer_VisualStudiox_en-us. 設定檔案變更為未來的某個日期。 如需此問題的詳細資訊，請參閱 [Visual Studio 說明檢視器凍結在啟動顯示畫面上](/visualstudio/welcome-to-visual-studio)。

7. 您可以在左側內容窗格底下搜尋 *sql server 2012*，以確認是否已載入 SQL Server 2012 內容。

   ![SQL Server 2012 文件已自動更新](../sql-server/media/sql-server-offline-documentation/sql-2012-content.png)

## <a name="view-offline-documentation"></a>檢視離線文件

您可以使用最新版 SQL Server Management Studio (SSMS) 中**的 [說明] 功能表來觀看**SQL Server 說明內容。

### <a name="view-offline-help-content-in-ssms"></a>在 SSMS 中檢視離線說明內容

若要在 SSMS 中檢視已安裝的說明，請從 [說明] 功能表中選取 [在說明檢視器中啟動]，以啟動 [說明檢視器]。

   ![在說明檢視器中啟動](../sql-server/media/sql-server-offline-documentation/helpviewer-view-offline.png)  

[說明檢視器] 會開啟至 [管理內容] 索引標籤，並在左窗格中顯示已安裝的說明目錄。 選取目錄中的文章以在右方窗格中顯示該文章。

> [!Important]
> 如果看不到內容窗格，請選取左邊界上的 [內容]。 選取圖釘圖示以將內容窗格保持開啟。  

   ![含內容的 [說明檢視器]](../sql-server/media/sql-server-offline-documentation/view-offline-all.png)
