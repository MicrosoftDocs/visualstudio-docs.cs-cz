---
title: Hodnoty metrik kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23dba7b7c29c05b55af2c461f36bdaa4b46b948f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667726"
---
# <a name="code-metrics-values"></a>Hodnoty metrik kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metriky kódu jsou sada softwarových opatření, která vývojářům poskytují lepší přehled o kódu, který vyvíjí. Díky využití metrik kódu můžou vývojáři pochopit, které typy a metody by se měly přepracovat nebo podrobně testovat. Vývojové týmy můžou identifikovat potenciální rizika, pochopit aktuální stav projektu a sledovat průběh během vývoje softwaru.

## <a name="software-measurements"></a>Měření softwaru
 V následujícím seznamu jsou uvedeny výsledky metrik kódu, které [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vypočítá:

- **Index udržovatelnosti** – vypočítá hodnotu indexu mezi 0 a 100, která představuje relativní snadné udržování kódu. Vysoká hodnota znamená lepší udržovatelnost. Barevná hodnocení lze použít k rychlé identifikaci problémů v kódu. Zelené hodnocení je mezi 20 a 100 a indikuje, že kód má dobrou udržovatelnost. Žluté hodnocení je mezi 10 a 19 a označuje, že je kód moderovanější. Červené hodnocení je hodnocení mezi 0 a 9 a označuje nízkou udržovatelnost.

- **Cyklomatická složitá** – měří strukturální složitost kódu. Vytvoří se tak, že se vypočítává počet různých cest kódu v toku programu. Program, který má složitý tok řízení, bude vyžadovat více testů pro dosažení dobrého pokrytí kódu a bude méně udržovatelný.

    > [!NOTE]
    > V některých případech se výpočet složitosti cyklomatická pro metodu v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] liší od předchozích verzí. Další informace najdete v části "změny v části výpočty složitosti kódu sady Visual Studio 2010" [řešení potíží s metrikami kódu](../code-quality/troubleshooting-code-metrics-issues.md).

- **Hloubka dědičnosti** – určuje počet definicí třídy, které se rozšířily do kořenového adresáře hierarchie tříd. Hlubší hierarchie je obtížnější pochopit, kde jsou konkrétní metody a pole definovány nebo/a předefinovány.

- **Párování tříd** – měří přihlašování k jedinečným třídám prostřednictvím parametrů, místních proměnných, návratových typů, volání metod, obecných nebo šablonových instancí, základních tříd, implementací rozhraní, polí definovaných pro externí typy a atributů. dekorace. Dobrý návrh softwaru určuje, že typy a metody by měly mít vysokou soudržnost a malý spoj. Vysoké propojení indikuje návrh, který je obtížné znovu použít a udržovat z důvodu jeho mnoha vzájemných závislostí na jiných typech.

- **Řádky kódu** – určuje přibližný počet řádků v kódu. Počet je založen na kódu IL a není tak přesný počet řádků v souboru zdrojového kódu. Velmi vysoký počet může ukazovat, že typ nebo metoda se snaží provést příliš mnoho práce a měla by být rozdělena. Může také indikovat, že typ nebo metoda může být obtížné udržovat.

## <a name="anonymous-methods"></a>Anonymní metody
 *Anonymní metoda* je pouze metoda, která nemá žádný název. Anonymní metody se nejčastěji používají k předání bloku kódu jako parametru delegáta. Výsledky metrik pro anonymní metodu, která je deklarována v členu, jako je například metoda nebo přistupující objekt, jsou přidruženy ke členu, který deklaruje metodu. Nejsou přidruženy ke členu, který volá metodu.

 Další informace o tom, jak metriky kódu považují anonymní metody, naleznete v tématu [anonymní metody a analýza kódu](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Generovaný kód
 Některé softwarové nástroje a kompilátory generují kód, který je přidán do projektu a který vývojář projektu buď nevidí, nebo by neměl být změněn. Ve většině případů metriky kódu ignorují generovaný kód při výpočtu hodnot metrik. To umožňuje hodnotám metriky odrážet, co může vývojář zobrazit a změnit.

 Kód vygenerovaný pro Windows Forms není ignorován, protože se jedná o kód, který může vývojář zobrazit a změnit.

## <a name="see-also"></a>Viz také
 [Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
