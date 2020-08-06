---
title: 通知操作員工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.notifyoperatortask.f1
helpviewer_keywords:
- Notify Operator task
- notifications [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 6c816c68-c6d6-44e4-bb34-c8e060a958a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ed5158a4ec5cfe8374fedbb2afbca1294b58f05e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708526"
---
# <a name="notify-operator-task"></a><span data-ttu-id="f91c7-102">通知操作員工作</span><span class="sxs-lookup"><span data-stu-id="f91c7-102">Notify Operator Task</span></span>
  <span data-ttu-id="f91c7-103">「通知操作員」工作會傳送通知訊息給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 操作員。</span><span class="sxs-lookup"><span data-stu-id="f91c7-103">The Notify Operator task sends notification messages to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operators.</span></span> <span data-ttu-id="f91c7-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 操作員是可接收電子通知的人員或群組使用的別名。</span><span class="sxs-lookup"><span data-stu-id="f91c7-104">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator is an alias for a person or group that can receive electronic notifications.</span></span> <span data-ttu-id="f91c7-105">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 運算子的詳細資訊，請參閱 [運算子](../../ssms/agent//operators.md)。</span><span class="sxs-lookup"><span data-stu-id="f91c7-105">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] operators, see [Operators](../../ssms/agent//operators.md).</span></span>  
  
 <span data-ttu-id="f91c7-106">藉由使用「通知操作員」工作，封裝即可透過電子郵件、呼叫器或 **網路傳送**通知一或多位操作員。</span><span class="sxs-lookup"><span data-stu-id="f91c7-106">By using the Notify Operator task, a package can notify one or more operators via e-mail, pager, or **net send**.</span></span> <span data-ttu-id="f91c7-107">每一位操作員都可藉由不同的方法收到通知。</span><span class="sxs-lookup"><span data-stu-id="f91c7-107">Each operator can be notified by different methods.</span></span> <span data-ttu-id="f91c7-108">例如，OperatorA 可藉由電子郵件和呼叫器收到通知，而 OperatorB 則藉由呼叫器和 **網路傳送**收到通知。</span><span class="sxs-lookup"><span data-stu-id="f91c7-108">For example, OperatorA is notified by e-mail and pager, and OperatorB is notified by pager and **net send**.</span></span> <span data-ttu-id="f91c7-109">從工作接收通知的操作員必須為「通知操作員」工作上 **OperatorNotify** 集合的成員。</span><span class="sxs-lookup"><span data-stu-id="f91c7-109">The operators who receive notifications from the task must be members of the **OperatorNotify** collection on the Notify Operator task.</span></span>  
  
 <span data-ttu-id="f91c7-110">「通知操作員」工作是唯一不會封裝 Transact-SQL 陳述式或 DBCC 命令的資料庫維護工作。</span><span class="sxs-lookup"><span data-stu-id="f91c7-110">The Notify Operator task is the only database maintenance task that does not encapsulate a Transact-SQL statement or a DBCC command.</span></span>  
  
## <a name="configuration-of-the-notify-operator-task"></a><span data-ttu-id="f91c7-111">設定通知操作員工作</span><span class="sxs-lookup"><span data-stu-id="f91c7-111">Configuration of the Notify Operator Task</span></span>  
 <span data-ttu-id="f91c7-112">您可以透過 [ [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師] 設定屬性。</span><span class="sxs-lookup"><span data-stu-id="f91c7-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="f91c7-113">這項工作位於「 **設計師」中** [工具箱] **的** [維護計畫工作] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 區段。</span><span class="sxs-lookup"><span data-stu-id="f91c7-113">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="f91c7-114">如需有關可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="f91c7-114">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="f91c7-115">通知操作員工作 &#40;維護計畫&#41;</span><span class="sxs-lookup"><span data-stu-id="f91c7-115">Notify Operator Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/notify-operator-task-maintenance-plan.md)  
  
 <span data-ttu-id="f91c7-116">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="f91c7-116">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="f91c7-117">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="f91c7-117">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
