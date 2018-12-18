---
title: Načtení dílčích projektů
ms.date: 12/04/2018
ms.topic: conceptual
ms.prod: visual-studio-dev16
ms.technology: vs-ide-general
helpviewer_keywords:
- filtered solution
- solution filtering
author: gewarren
ms.author: stsu
manager: douge
ms.openlocfilehash: 655644e936bdfb1382e70d746f589b8fcfabf488
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896932"
---
# <a name="filtered-solutions-in-visual-studio"></a>Filtrované řešení v sadě Visual Studio

**Nové ve verzi Visual Studio. 2019 Preview 1**

Velké vývojářské týmy se často spolupracovat pomocí jediného velkých řešení s mnoha projektů. Jednotliví vývojáři však obvykle fungují na malou podmnožinu těchto projektů. Kvůli zvýšení výkonu při otevírání velkých řešení se Visual Studio. 2019 ve verzi Preview 1 představuje *filtrování řešení*. Filtrování umožňuje otevření řešení s pouze vybrané projekty řešení. Načítání dílčích projektů v řešení snižuje načtení řešení, sestavení a testování, čas spuštění a umožňuje víc zaměřené revize.

K dispozici jsou následující funkce:

- Získáte tak, že otevřete řešení bez jakéhokoli z jeho projektů načtení kód rychleji. Po otevření řešení, můžete si zvolit projekty, které chcete načíst.

- Při opětovném otevření řešení sady Visual Studio si pamatuje projekty, které byly načteny v předchozí relaci a načte pouze projekty.

- Můžete vytvořit soubor řešení filtr minimálně jedna konfigurace načtení projektu uložit nebo sdílet konfiguraci s členy týmu.

## <a name="open-a-filtered-solution"></a>Otevřete filtrované řešení

Chcete-li otevřít řešení s jenom některé z jeho projektů, načíst, postupujte takto:

1. Zvolte **souboru** > **otevřít** > **projekt či řešení** z řádku nabídek.

2. V **nový projekt** dialogového okna, vyberte řešení a potom vyberte **projekty se nenačtou**.

   ![Visual Studio otevřete projekt dialogové okno s nenačtou zaškrtnutých projektů](media/filtered-solutions/do-not-load-projects.png)

3. Zvolte **otevřít**.

   Řešení se otevře s všechny jeho projekty Nenačtené.

4. V **Průzkumníka řešení**, vyberte projekty, které chcete načíst (stiskněte **Ctrl** při výběru více než jeden projekt) a potom klikněte pravým tlačítkem na projekt a zvolte **znovu načíst projekt** .

   ![Znovu načíst více projektů v Průzkumníku řešení sady Visual Studio](media/filtered-solutions/reload-project.png)

   Visual Studio si budou pamatovat projekty, které se načtou při příštím otevření řešení místně.

## <a name="toggle-unloaded-project-visibility"></a>Přepnout viditelnost uvolnit projekt

Můžete také zobrazit buď všechny projekty v řešení nebo pouze ty načíst pomocí jedné z následujících možností v **Průzkumníka řešení**:

- Klikněte pravým tlačítkem na řešení a vyberte **zobrazit uvolněné projekty** nebo **skrýt uvolněné projekty**.

- Vyberte **zobrazit všechny soubory** tlačítko pro přepínání viditelnosti uvolněné projekty.

   ![Zobrazit tlačítko pro všechny soubory v Průzkumníku řešení sady Visual Studio](media/filtered-solutions/show-all-files.PNG)

## <a name="solution-filter-files"></a>Filtr souborů řešení

Pokud chcete sdílet vaše konfigurace načtení projektu nebo potvrzení do správy zdrojového kódu, můžete vytvořit filtr soubor řešení (má příponu *.slnf*). Když otevřete soubor řešení filtr, řešení se otevře v sadě Visual Studio se zadaným projektům načten a uvolněné projekty skryté. Je možné [přepnout](#toggle-unloaded-project-visibility) zobrazíte uvolněné projekty.

Filtr souborů řešení jsou vizuálně rozlišené ze souborů regulární řešení pomocí šifer další trychtýřového grafu ve na ikonu vedle řešení v **Průzkumníka řešení**. Název filtru a počet načtených projektů jsou také zobrazeny vedle názvu řešení.

![Soubor filtru řešení otevřít v Průzkumníku řešení sady Visual Studio](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Nové projekty při přidání do původní řešení po vytvoření souboru řešení filtr, zobrazí se jako uvolněné projekty v **Průzkumníka řešení**.

### <a name="create-a-solution-filter-file"></a>Vytvořit soubor řešení filtr

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení a vyberte **uložit jako filtr řešení**.

   ![Uložit jako filtr řešení nabídky v Průzkumníku řešení sady Visual Studio](media/filtered-solutions/save-as-solution-filter.png)

2. Zvolte název a umístění souboru filtru řešení.

Po vytvoření souboru filtru řešení, přidá se do vaší **poslední projekty a řešení** seznamu pro usnadnění přístupu:

![Otevřít nedávné v sadě Visual Studio](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Viz také:

- [Vlastní nastavení vnořování souborů v Průzkumníku řešení](file-nesting-solution-explorer.md)
- [Optimalizace výkonu sady Visual Studio](optimize-visual-studio-performance.md)