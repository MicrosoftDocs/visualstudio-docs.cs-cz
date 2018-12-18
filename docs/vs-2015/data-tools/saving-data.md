---
title: Ukládání dat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataRow.RowState
- DataSet.GetChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- DBDirect methods
- updating data
- data [Visual Studio], saving
- TableAdapter DBDirect methods
- databases, updating
- TableAdapter.Update method
- data [Visual Studio], updating
- saving data
- updating databases
ms.assetid: 21d2b115-62e4-4ac9-a873-dcbb535b8af8
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: dc671d60ff37e9853dc64a62cbc1b91a6914e0e3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249298"
---
# <a name="saving-data"></a>Ukládání dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ukládání dat je že proces uchování změněných dat v datovém modelu aplikace zpět do původního úložiště dat, obvykle relační databáze jako je SQL Server.  
  
 Aktualizace zdroje dat prostřednictvím datového modelu je obvykle dvoustupňový proces. Prvním krokem je aktualizace datového modelu s novými informacemi – nové záznamy, záznamy změněné ani odstraněné záznamy. Druhým krokem je uložit změny do datového modelu zpět do databáze.  
  
 Následující témata popisují koncepty a úloh přidružených k ukládání dat.  
  
## <a name="related-topics"></a>Související témata  
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)  
 Poskytuje přehled o tom, jak jsou v datové sadě provedeny změny a jak datovou sadu sleduje informace o změnách, aby bylo možné tyto změny uložit do databáze.  
  
 [Ukládání dat Entity](../data-tools/saving-entity-data.md)  
 Popisuje, jak uložit změny v [ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205) a [4.5 služby WCF Data](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) aplikací.