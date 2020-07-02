---
title: Sbalení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
ms.assetid: d1476758-9d35-4d74-b63c-310661932ecd
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 907d075f597799edd582c9f2bae693eac92c0b2c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544960"
---
# <a name="outlining"></a>Sbalování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete zvolit, že chcete skrýt nějaký kód ze zobrazení sbalením oblasti kódu tak, aby se zobrazila pod znaménkem plus (+). Sbalenou oblast rozbalíte kliknutím na symbol plus. (Nebo můžete stisknutím kombinace kláves CTRL + M + M sbalit oblast a potom CTRL + M + M znovu rozbalit.) Můžete také sbalit oblast sbalení dvojitým kliknutím na libovolný řádek v oblasti okraje osnovy, který se zobrazí pouze nalevo od kódu. Když najedete myší na sbalenou oblast, zobrazí se obsah sbalené oblasti jako ToolTip.

 Oblasti v okraji osnovy jsou zvýrazněny také při přesunutí ukazatele myši na okraj myší. Výchozí zvýraznění barvy se v některých konfiguracích barev může zdát nezřetelné. Můžete ho změnit v **nabídce Nástroje/možnosti/prostředí/písma a barvy/sbalitelná oblast**.

 Když pracujete v předčárovém kódu, můžete rozbalit oddíly, na kterých chcete pracovat, sbalit je po dokončení a pak přejít na jiné oddíly. Pokud nechcete, aby se zobrazovalo sbalení, můžete pomocí příkazu **zastavit sbalení** odebrat informace o přehledu, aniž byste narušili váš podkladový kód.

 Tyto akce mají vliv na příkazy **zpět** a **znovu** v nabídce **Upravit** . Operace **kopírování**, **vyjmutí**, **vložení**a přetažení uchovávají informace o sbalení, ale ne stav sbalitelné oblasti. Když například kopírujete sbalenou oblast, operace **vložení** Vloží zkopírovaný text jako rozbalenou oblast.

> [!CAUTION]
> Když změníte oblast s přířádkou, může dojít ke ztrátě osnovy. Například odstranění nebo vyhledání a nahrazení operací může vymazat konec oblasti.

 Následující příkazy lze najít v podnabídce **Upravit/osnova** .

|Příkaz|Popis|
|-|-|
|Skrýt výběr|(CTRL + M, CTRL + H) – Sbalí vybraný blok kódu, který by normálně nebyl k dispozici pro sbalení, například `if` blok. Chcete-li odebrat vlastní oblast, použijte příkaz **zastavit skrývání aktuálního** umístění (nebo CTRL + M, CTRL + U). Není k dispozici v Visual Basic.|
|Přepnout rozšíření osnovy|– Vrátí aktuální skrytý nebo rozbalený stav v rámci nejvnitřnější sekce sbalení, když je kurzor umístěný ve vnořeném sbaleném oddílu.|
|Přepnout všechna sbalení|(CTRL + M, CTRL + L) – nastaví všechny oblasti na stejný sbalený nebo rozbalený stav. Pokud jsou některé oblasti rozbalené a některé sbalené, sbalené oblasti se rozbalí.|
|Zastavit sbalení|(CTRL + M, CTRL + P) – Odebere všechny informace o sbalení celého dokumentu.|
|Zastavit skrývání aktuálního|(CTRL + M, CTRL + U) – odebere informace o Sbalení aktuálně vybrané uživatelem definované oblasti. Není k dispozici v Visual Basic.|
|Sbalit do definic|(CTRL + M, CTRL + O) – sbalí členy všech typů.|
|Sbalit blok:\<logical boundary>|(Visual C++) Sbalí oblast ve funkci, která obsahuje bod vložení. Například pokud bod vložení leží uvnitř smyčky, je smyčka skrytá.|
|Sbalit vše v:\<logical structures>|(Visual C++) Sbalí všechny struktury uvnitř funkce.|

 Můžete také použít sadu Visual Studio SDK k definování textových oblastí, které chcete rozbalit nebo sbalit. Viz [Návod: sbalení](../extensibility/walkthrough-outlining.md).
