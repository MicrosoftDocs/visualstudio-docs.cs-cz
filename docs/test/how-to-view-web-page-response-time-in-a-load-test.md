---
title: Doba odezvy stránky v zátěžovém testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf8bc1205658899a51cf1a50e83a9a8b34034b25
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594315"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Postupy: zobrazení doby odezvy webové stránky v zátěžovém testu pomocí Analyzéru zátěžového testu

Čas potřebný pro každou webovou stránku pro načtení se označuje jako *doba odezvy*. Když vytvoříte test výkonnosti webu, můžete nastavit cílovou dobu odpovědi pro každý požadavek webové stránky v testu výkonnosti webu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Při spuštění testu výkonnosti webu ve stresu v rámci zátěžového testu, bude možné analyzovat následující informace pro každou stránku:

- Průměrná doba odezvy stránky.

- Procento iterace testu, které splňují cílovou dobu odezvy stránky.

- Doba odezvy webové stránky můžete analyzovat pomocí zobrazení tabulek nebo zobrazení grafů **Analyzéru zátěžového testu**:

- Analýza odezvy webové stránky v tabulkovém zobrazení

- Analýza odezvy webové stránky v zobrazení grafů

## <a name="view-response-time-data-in-a-table"></a>Zobrazit data o době odezvy v tabulce

1. V **Analyzéru zátěžového testu**, zvolte **tabulky** na panelu nástrojů, abyste měli jistotu, že se zobrazí mřížku tabulky.

2. V **tabulky** rozevíracího seznamu vyberte **stránky**.

3. Data pro jednotlivé stránky se zobrazí v mřížce. Obvykle se zobrazí následující sloupce.

   |Záhlaví sloupce|Popis|
   |-|-|
   |**Stránka**|Název webové stránky.|
   |**Scénář**|Název scénáře. Důležité: Pokud máte více než jeden scénář v testu výkonnosti webu.|
   |**Test**|Název testu výkonnosti webu. Důležité: Pokud máte více než jeden výkon webového testu v zátěžovém testu.|
   |**Sítě**|Typ sítě.<br /><br /> Ve výchozím nastavení tato data nejsou shromažďována. Shromažďování těchto dat v **editoru zátěžových testů**v části **parametrů běhu** uzlu, vyberte uzel nastavení spuštění změnit. V **vlastnosti** okně pro **úložiště podrobností časování** vlastnosti, vyberte **AllIndividualDetails**.|
   |**Celkem**|Celkový počet požadavků, které byly provedeny pro webovou stránku. Toto je celkový součet pro všechny iterace v zátěžovém testu.|
   |**Uložit**|Průměrnou dobu odezvy stránky.<br /><br /> Ve výchozím nastavení tato data nejsou shromažďována. Shromažďování těchto dat v **editoru zátěžových testů**v části **parametrů běhu** uzlu, vyberte uzel nastavení spuštění změnit. V **vlastnosti** okně pro **úložiště podrobností časování** vlastnosti, vyberte **AllIndividualDetails**.|
   |**min**|Doba odezvy minimální stránky.<br /><br /> Ve výchozím nastavení tato data nejsou shromažďována. Shromažďování těchto dat v **editoru zátěžových testů**v části **parametrů běhu** uzlu, vyberte uzel nastavení spuštění změnit. V **vlastnosti** okně pro **úložiště podrobností časování** vlastnosti, vyberte **AllIndividualDetails**.|
   |**Medián**|Doba odezvy střední stránky.<br /><br /> Ve výchozím nastavení tato data nejsou shromažďována. Shromažďování těchto dat v **editoru zátěžových testů**v části **parametrů běhu** uzlu, vyberte uzel nastavení spuštění změnit. V **vlastnosti** okně pro **úložiště podrobností časování** vlastnosti, vyberte **AllIndividualDetails**.|
   |**90%**|Na 90. percentil dobu odezvy. To znamená, že 90 % stránky odpovědi rychleji, než tento počet a 10 % stránek odpověděl pomaleji.<br /><br /> Ve výchozím nastavení tato data nejsou shromažďována. Shromažďování těchto dat v **editoru zátěžových testů**v části **parametrů běhu** uzlu, vyberte uzel nastavení spuštění změnit. V **vlastnosti** okně pro **úložiště podrobností časování** vlastnosti, vyberte **AllIndividualDetails**.|
   |**95%**|95. percentil dobu odezvy. To znamená, že 95 % stránky odpovědi rychleji, než tento počet a 5 % stránek odpověděl pomaleji.|
   |**99%**|99. percentilu po dobu odezvy. To znamená, že 99 % stránky odpovědi rychleji, než tento počet a procento 1 na stránkách odpověděl pomaleji.<br /><br /> Ve výchozím nastavení tato data nejsou shromažďována. Shromažďování těchto dat v **editoru zátěžových testů**v části **parametrů běhu** uzlu, vyberte uzel nastavení spuštění změnit. V **vlastnosti** okně pro **úložiště podrobností časování** vlastnosti, vyberte **AllIndividualDetails**.|
   |**Max**|Doba odezvy maximální stránky.<br /><br /> Ve výchozím nastavení tato data nejsou shromažďována. Shromažďování těchto dat v **editoru zátěžových testů**v části **parametrů běhu** uzlu, vyberte uzel nastavení spuštění změnit. V **vlastnosti** okně pro **úložiště podrobností časování** vlastnosti, vyberte **AllIndividualDetails**.|
   |**Směrodatná odchylka**|Ve výchozím nastavení směrodatná odchylka data nejsou shromažďována. Shromažďování těchto dat v **editoru zátěžových testů**v části **parametrů běhu** uzlu, vyberte uzel nastavení spuštění změnit. V **vlastnosti** okně pro **úložiště podrobností časování** vlastnosti, vyberte **AllIndividualDetails**.|
   |**Doba vytvoření stránky**|Průměrná doba odezvy pro všechny požadavky, které byly provedeny pro webovou stránku.|
   |**Cíl**|Cílová doba stránky. Toto je konstantní hodnota pro stránku. **Poznámka:** cílová doba stránky se zobrazí jenom v případě, že cílem je definována pro požadavek v testu výkonnosti webu.|
   |**% Cíle schůzky**|Procento požadavků, které byly provedeny pro webovou stránku, která splněny cílovou dobu odezvy.|

   Další informace najdete v tématu [Analýza výsledků zátěžových testů a chyb v tabulkovém zobrazení](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Zobrazit data o době odezvy v grafu

V grafu zobrazíte změny v průběhu času během zátěžového testu můžete také zobrazit data o době odezvy. To je obzvláště užitečné, pokud vaše vzor zatížení zvýší při spuštění testů (například pokud používáte vzor zatížení kroku). Další informace najdete v tématu [vzory zatížení úpravy aktivity virtuálního uživatele modelu](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Chcete-li zobrazit data o době odezvy v grafu:

1. V **Analyzéru zátěžového testu**, zvolte **grafy** na panelu nástrojů, abyste měli jistotu, že se zobrazí grafu.

2. V **čítače** okna, rozbalte uzel scénář, který vás zajímá (například `Scenario1`).

3. Rozbalte uzel test výkonnosti webu, který vás zajímá.

4. Rozbalte uzel **stránky**.

5. Rozbalte uzel stránky, které vás zajímají.

6. Klikněte pravým tlačítkem na **% cíle schůzky stránky** a klikněte na tlačítko **zobrazit čítač v grafu**.

    Data je přidána do grafu.

7. Volitelné Opakujte předchozí krok pro **průměrný čas stránky**, **cíl doby odezvy stránky**a **Celkový počet stránek**.

   > [!NOTE]
   > **Cílová doba odezvy stránky** je konstantní.

   Další informace najdete v tématu [výsledků zátěžového testu analyzovat v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Viz také:

- [Analýza výsledků zátěžových testů a chyb v tabulkovém zobrazení](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Postupy: přístup k analýze výsledků zátěžového testu](../test/how-to-access-load-test-results-for-analysis.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
