---
title: Rozhodli jste databázový objekt od nepodporovaného poskytovatele databáze. | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1027be99525081ad4df959908b856727e9ebe399
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211695"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Vybrali jste databázový objekt od nepodporovaného poskytovatele databáze.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) Podporuje pouze zprostředkovatele dat .NET Framework pro SQL Server (<xref:System.Data.SqlClient>). I když můžete kliknout na **OK** a pokračovat v práci s objekty od poskytovatelů Nepodporovaná databáze, vám může dojít k neočekávanému chování za běhu.  
  
> [!NOTE]
>  Jsou podporovány pouze datová připojení, které používají zprostředkovatele dat .NET Framework pro SQL Server.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Klikněte na tlačítko **OK** pokračujte návrhu tříd entit, které mapují na připojení, které používá nepodporovaného poskytovatele databáze. Při použití nepodporované databázové poskytovatelů, může dojít k neočekávanému chování.  
  
     -nebo-  
  
-   Klikněte na tlačítko **zrušit**.  
  
     Tato akce je zastavená. Vytvořit nebo použít datové připojení, který používá zprostředkovatele .NET Framework pro SQL Server.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Zprostředkovatelé dat .NET framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)

