---
title: MSSQLSERVER_617 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 88e9feb7c3ac5d8cf646d2243319b2b160b7757e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702910"
---
# <a name="mssqlserver_617"></a>MSSQLSERVER_617
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|617|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|NODESHASH|  
|訊息文字|嘗試取消資料庫識別碼 %d 中物件識別碼 %ld 的雜湊時，在雜湊表中找不到該描述項。 工作資料表遺漏一個項目。 請重新執行查詢。 如果資料指標與此有關，請先關閉，然後重新開啟資料指標。|  
  
## <a name="explanation"></a>說明  
 SQL Server 找不到特定項目的工作資料表。  
  
## <a name="user-action"></a>使用者動作  
  
1.  如果資料指標與此有關，請先關閉資料指標，然後重新開啟資料指標。  
  
2.  再次執行查詢。  
  
  
