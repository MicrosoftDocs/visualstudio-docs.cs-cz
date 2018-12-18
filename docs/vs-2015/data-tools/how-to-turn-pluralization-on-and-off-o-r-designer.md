---
title: 'Postupy: vypnutí pluralizace a zapnutí (O R Designer) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1f4491f25a861b8556ae5018e526349d6a17187a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279107"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Postupy: vypnutí pluralizace a zapnutí (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Ve výchozím nastavení se při přetažení databázových objektů, které mají jména končící na s nebo dokumentu z **Průzkumníka serveru**/**Průzkumník databáze** na [LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), názvy generovaných tříd entit se změnil z množném čísle k jednotném čísle. To slouží k reprezentaci přesněji skutečnost, že třída vytvořenou instanci entity se mapuje na jeden záznam dat. Příkladem je přidání tabulky Zákazníci [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] výsledky v třídu entity s názvem zákazníka, protože třída bude obsahovat data pro jediného zákazníka.  
  
> [!NOTE]
>  Pluralizace je ve výchozím pouze v anglické jazykové verzi sady Visual Studio.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>K zapnutí a vypnutí pluralizace  
  
1.  Na **nástroje** nabídky, klikněte na tlačítko **možnosti**.  
  
2.  V **možnosti** dialogového okna rozbalte **databázové nástroje**.  
  
> [!NOTE]
>  Vyberte **zobrazit všechna nastavení** Pokud **databázové nástroje** uzel není viditelný.  
  
1.  Klikněte na tlačítko **O/R Designer**.  
  
2.  Nastavte **Pluralizaci názvů** k **povoleno** = **False** nastavit [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tak, aby neměnil názvy tříd.  
  
3.  Nastavte **Pluralizaci názvů** k **povoleno** = **True** použít pluralizace pravidla pro názvy tříd objektů, které jsou přidány do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>Viz také  
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

