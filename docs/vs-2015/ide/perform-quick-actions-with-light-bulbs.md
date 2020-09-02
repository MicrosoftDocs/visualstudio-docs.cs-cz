---
title: Provádění rychlých akcí pomocí žárovek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 990ee487-cf9a-4b89-9784-e7b47c220e8c
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 78ac9b0aba4e56b2240ef65783231d31d77e5144
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670341"
---
# <a name="perform-quick-actions-with-light-bulbs"></a>Rychlé akce pomocí žárovek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Žárovky jsou novou funkcí produktivity v aplikaci Visual Studio 2015. Jsou to ikony, které se zobrazí v editoru sady Visual Studio a na které můžete kliknout a provést tak rychlé akce, včetně refaktoringu chyb. Žárovky přinášejí chybovou opravu a pomoc při refaktoringu do jednoho ohniskového bodu, často přímo na řádku, ve kterém píšete.

 ![Ikona malé žárovky](../ide/media/vs2015-lightbulbsmall.png "VS2015_LightBulbSmall")

 V jazyce C# a Visual Basic se zobrazí žárovka, pokud je červená vlnovka a Visual Studio obsahuje návrhy na to, jak problém vyřešit. Pokud máte například chybu označenou červenou vlnovkou, žárovka se zobrazí v případě, že jsou pro tuto chybu k dispozici opravy. V jazyce C++ když přidáte novou funkci do hlavičkového souboru, zobrazí se žárovka, která nabízí pro vytvoření zástupné implementace této funkce. Pro libovolný jazyk mohou třetí strany poskytovat vlastní diagnostiku a návrhy, například jako součást sady SDK, a žárovky Visual Studio budou na základě těchto pravidel rozsvítit.

## <a name="to-see-a-light-bulb"></a>Chcete-li zobrazit žárovku

1. V mnoha případech se v případě, že se blikající kurzor myši nachází na řádku s chybou, při přesunu blikajícího kurzoru na řádek, který je v tomto případě chyba, zobrazuje žárovky na pravé straně. Když se zobrazí červená vlnovka, můžete na ni najeďte myší, aby se zobrazila žárovka. Můžete také vyvolat žárovku, která se zobrazí, když pomocí myši nebo klávesnice přejdete kamkoli na řádek, kde k problému dochází.

2. Stiskněte **kombinaci kláves CTRL +.** kdekoli na řádku, aby se mohla vyvolat žárovka, a přejít přímo na seznam potenciálních oprav.

   ![Žárovka při najetí myší](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

## <a name="to-see-potential-fixes"></a>Chcete-li zobrazit možné opravy
 Kliknutím na šipku dolů nebo na odkaz Zobrazit možné opravy zobrazíte seznam rychlých akcí, které může žárovka trvat.

 ![Rozbalení žárovky](../ide/media/vs2015-lightbulb-hover-expanded.png "VS2015_LightBulb_hover_expanded")

## <a name="to-do-a-refactoring"></a>Postup refaktoringu
 Můžete i nadále provádět refaktorování kliknutím pravým tlačítkem myši na nabídku a vyvolat kontextovou nabídku, ale můžete také stisknout kombinaci kláves CTRL +. pro zobrazení možností refaktoringu. Na následujícím obrázku je refaktoring metody extrakce nabízena po stisknutí kombinace kláves CTRL +. někam na řádku, který obsahuje `Math.Abs` volání:

 ![Žárovka ukazující možnosti refaktoringu](../ide/media/vs2015-lightbulbs-refactor.png "VS2015_LightBulbs_refactor")
