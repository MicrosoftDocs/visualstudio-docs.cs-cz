---
title: 'DA0504: maximální pracovní sada v bajtech pro proces, který se profiluje | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2c57e006196611b49909f3ad6bfc866a028a8621
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850874"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: Maximum Pracovní sady v bajtech pro profilovaný Proces
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID pravidla | DA0504 |  
| Kategorie | Správa prostředků |  
| Metoda profilování | Vše |  
| Zpráva | Tyto informace se shromáždily jenom pro informace. Čítač pracovní sady procesů měří využití fyzické paměti procesem, který vytváříte. Hodnota hlášené je maximální pozorována ve všech intervalech měření. |  
| Typ pravidla | Informace |  
  
 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.  
  
## <a name="rule-description"></a>Popis pravidla  
 Tato zpráva oznamuje maximální velikost fyzické paměti (v bajtech), kterou proces aktuálně používá. Pracovní sada procesu představuje stránky z adresního prostoru procesu, který je aktuálně umístěn ve fyzické paměti. Toto pravidlo oznamuje maximální hodnotu pro pracovní sadu procesu, zatímco profilace byla aktivní.  
  
 Nahlášená hodnota zahrnuje rezidentní stránky ze sdílených segmentů paměti, na které se odkazuje na daný proces. Sdílené knihovny DLL, které odkazují na procesy, jsou zahrnuté do sdílených segmentů paměti, které se počítají. Hodnota pracovní sady procesu může být vyšší než velikost virtuální paměti, kterou byl proces přidělen z důvodu sdílených segmentů paměti.  
  
 Velikost pracovní sady procesu odráží, kolik virtuální paměti proces aktivně používá. To je ovlivněno množstvím fyzické paměti (nebo paměti RAM), která je k dispozici pro spuštění aplikace a kolizí pro danou fyzickou paměť z jiných spuštěných procesů. Další informace o pracovních sadách procesů najdete v tématu [Work set](https://msdn.microsoft.com/library/cc441804.aspx) v dokumentaci ke službě Windows Memory Management na webu MSDN.  
  
## <a name="how-to-use-rule-data"></a>Jak používat data pravidla  
 Toto pravidlo shromáždí tato data měření z nástroje pro sledování výkonu systému Windows a sestavuje je pouze pro informace. Slouží k porovnání výkonu různých verzí nebo sestavení programu nebo pro pochopení výkonu aplikace v různých testovacích scénářích.  
  
 Dvakrát klikněte na zprávu v okně Seznam chyb, abyste přešli na [zobrazení značek](../profiling/marks-view.md) dat profilace. Vyhledejte sloupce čítače **Process\Working sady** a **paměti \ stránky/s** . Pak najděte maximální hodnotu **Process\Working sady** a porovnejte ji s hodnotou **paměť \ stránky/s** . Pro maximum pracovní sady se často používá interval, ve kterém se snížila doba vstupně-výstupních operací stránkování, zejména v případě, že je počítač omezen pamětí.
