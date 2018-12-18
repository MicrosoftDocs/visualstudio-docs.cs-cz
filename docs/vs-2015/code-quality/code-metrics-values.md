---
title: Hodnoty metrik kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 22c42cb215999fcc4415f4d7541b8f4b95ac2d29
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782957"
---
# <a name="code-metrics-values"></a>Hodnoty metrik kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metriky kódu je sada softwarových opatření, která vývojářům poskytují lepší přehled o kódu, který že vyvíjí. S využitím metrik kódu, vývojáři můžete pochopit, jaké typy nebo metody by měly být přepracována nebo více důkladně otestovali. Vývojové týmy můžete identifikovat potenciální rizika, porozumět aktuálnímu stavu projektu a sledování průběhu během vývoje softwaru.  
  
## <a name="software-measurements"></a>Měření softwaru  
 Následující seznam ukazuje výsledky metrik kódu, který [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vypočítá:  
  
-   **Index udržovatelnosti** – vypočítá hodnotu indexu 0 až 100, který představuje relativní snadností údržbu kódu. Vysoká hodnota znamená vyšší udržovatelnosti. Barevně odlišeny hodnocení je možné rychle identifikovat míst v kódu. Zelená hodnocení je 20 až 100 a označuje, že kód je dobrou udržovatelnost. Žlutý hodnocení je od 10 do 19 a označuje, že je mírně udržovatelný kód. Červené hodnocení je hodnocení 0 až 9 a označuje nízkou udržovatelnost.  
  
-   **Cyklomatická složitost** – měří strukturální složitost kódu. Vytvoří se to vynásobením počtu odlišný kód cest v toku programu. Program, který se má komplexní řízení toku bude vyžadovat další testů k dosažení dobré kód pokrytí a bude méně udržovatelný.  
  
    > [!NOTE]
    >  V některých případech se výpočet cyklomatická složitost metody v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] se liší od předchozích verzí. Další informace najdete v tématu "Změny v aplikaci Visual Studio 2010 složité výpočty části kódu" z [potíží metriky kódu](../code-quality/troubleshooting-code-metrics-issues.md).  
  
-   **Hloubka dědičnosti** – označuje počet definice tříd, které rozšiřují do kořene hierarchie tříd. Čím hlouběji v hierarchii více obtížné pochopit, kde jsou definovány konkrétní metody a pole může být nebo / a Předefinovaná.  
  
-   **Třída párování** – měří párování na jedinečné třídy prostřednictvím parametrů, místní proměnné, návratové typy, volání metod, vytváření instancí obecného nebo šablony, základní třídy, implementací rozhraní, polí definovaných pro externí typy, a atribut dekorace. Software dobrý návrh přikazuje, typy a metody by měly mít vysokou soudržnost a nízkou párování. Vysoká párování označuje návrh, který je obtížné opakovaně používat a spravovat z důvodu jeho mnoho vzájemných závislostí na jiné typy.  
  
-   **Řádky kódu** – určuje přibližný počet řádků v kódu. Počet je založena na kód IL a není proto přesný počet řádků v souboru se zdrojovým kódem. Velmi vysoký počet může znamenat, že typ nebo metoda se pokouší příliš mnoho práce a by měl být rozdělení. Může také znamenat, že tento typ nebo metoda může být obtížné spravovat.  
  
## <a name="anonymous-methods"></a>Anonymní metody  
 *Anonymní metoda* je právě metodu, která nemá žádný název. Anonymní metody se nejčastěji používají k předání bloku kódu jako parametr delegátu. Výsledky metrik pro anonymní metody, která je deklarována v členu, například metoda nebo přístupový objekt, jsou spojeny s člena, který deklaruje metodu. Nejsou přidružené člena, který volá metodu.  
  
 Další informace o způsobu metriky kódu s anonymními metodami najdete v tématu [anonymní metody a analýza kódu](../code-quality/anonymous-methods-and-code-analysis.md).  
  
## <a name="generated-code"></a>Generovaný kód  
 Některé softwarové nástroje, kompilátory generují kód, který se přidá do projektu a že pro vývojáře projekt nezobrazí nebo by neměly měnit. Metriky kódu, většinou ignoruje generovaného kódu při výpočtu hodnoty metrik. To umožňuje hodnoty metrik tak, aby odrážely co může vývojář zobrazit a měnit.  
  
 Kód generovaný pro model Windows forms není ignorována, protože je kód, který se může zobrazit a měnit vývojáře.  
  
## <a name="see-also"></a>Viz také  
 [Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



