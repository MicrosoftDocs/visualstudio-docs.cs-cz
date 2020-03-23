---
title: Načtení podmnožinu projektů
ms.date: 04/22/2019
ms.prod: visual-studio-dev16
ms.topic: conceptual
helpviewer_keywords:
- filtered solution
- solution filtering
author: jillre
ms.author: stsu
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4c44d267ef5686d04e9549601e05866aabbfb62d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72650841"
---
# <a name="filtered-solutions-in-visual-studio"></a>Filtrovaná řešení v sadě Visual Studio

Velké vývojové týmy často spolupracují pomocí jednoho velkého řešení s mnoha projekty. Jednotliví vývojáři však obvykle pracují na malé podmnožině těchto projektů. Chcete-li zvýšit výkon při otevírání velkých řešení, Visual Studio 2019 představil *filtrování řešení*. Filtrování řešení umožňuje otevřít řešení pouze s načtenými selektivními projekty. Načtení podmnožiny projektů v řešení snižuje zatížení řešení, sestavení a zkušební běh a umožňuje více zaměřené kontroly.

K dispozici jsou následující funkce:

- Ke kódu se můžete dostat rychleji otevřením řešení bez načtení některého z jeho projektů. Po otevření řešení můžete selektivně zvolit, které projekty se mají načíst.

- Při opětovném otevření řešení Visual Studio si pamatuje, které projekty byly načteny v předchozí relaci a načte pouze tyto projekty.

- Můžete vytvořit soubor filtru řešení pro uložení jedné nebo více konfigurací zatížení projektu nebo sdílet konfiguraci se spoluhráči.

## <a name="open-a-filtered-solution"></a>Otevření filtrovaného roztoku

Řešení můžete otevřít bez načtení některého z jeho projektů přímo z dialogového okna **Otevřít projekt** nebo z [příkazového řádku](#command-line).

### <a name="open-project-dialog"></a>Dialogové okno Otevřít projekt

Otevření řešení bez načtení některého z jeho projektů pomocí dialogového okna **Otevřít projekt:**

1. Z řádku nabídek zvolte **Otevřít** > **Open** > **projekt/řešení** souboru.

2. V dialogovém okně **Otevřít projekt** vyberte řešení a pak vyberte **Nenačítat projekty**.

   ![Dialogové okno Open Project v Visual Studiu s nenačítat projekty zaškrtnuté](media/filtered-solutions/do-not-load-projects.png)

3. Zvolte **Otevřít**.

   Řešení se otevře se všemi jeho projekty uvolněny.

4. V **Průzkumníku řešení**vyberte projekty, které chcete načíst (stisknutím **klávesy Ctrl** a kliknutím vyberte více než jeden projekt) a potom klikněte pravým tlačítkem myši na projekt a zvolte Znovu **načíst project**.

   ![Opětovné načtení více projektů v Průzkumníku řešení sady Visual Studio](media/filtered-solutions/reload-project.png)

   Visual Studio si zapamatuje, které projekty jsou načteny při příštím otevření řešení místně.

### <a name="command-line"></a>Příkazový řádek

(Novinka ve Visual Studiu 2019 verze 16.1.)

Chcete-li otevřít řešení bez načítání některého z [`/donotloadprojects`](../ide/reference/donotloadprojects-devenv-exe.md) jeho projektů z příkazového řádku, použijte přepínač, jak je znázorněno v následujícím příkladu:

```cmd
devenv /donotloadprojects MySln.sln
```

## <a name="toggle-unloaded-project-visibility"></a>Přepnout neuvolněnou viditelnost projektu

Můžete si vybrat, zda chcete zobrazit buď všechny projekty v řešení, nebo jen načtené pomocí jedné z následujících možností v **Průzkumníku řešení**:

- Klikněte pravým tlačítkem myši na řešení a vyberte **zobrazit nezatížené projekty** nebo **Skrýt nezatížené projekty**.

- Výběrem uzlu řešení povolíte tlačítko **Zobrazit všechny soubory;** potom klepněte na tlačítko pro přepnutí viditelnosti nezatížených projektů.

   ![Tlačítko Zobrazit všechny soubory v Průzkumníku řešení sady Visual Studio](media/filtered-solutions/show-all-files.PNG)

## <a name="load-project-dependencies"></a>Načtení závislostí projektu

V řešení, kde jsou načteny pouze vybrané projekty, nemusí mít načteny všechny závislosti projektu projektu. Pomocí možnosti **Načíst závislosti projektu** možnost zajistit, že všechny projekty, které projekt závisí na jsou také načteny. Klikněte pravým tlačítkem myši na jeden nebo více načtených projektů v **Průzkumníku řešení** a zvolte **Načíst závislosti projektu**.

![Načtení závislostí projektů ve Visual Studiu 2019](media/filtered-solutions/load-project-dependencies.png)

## <a name="solution-filter-files"></a>Soubory filtrů řešení

Pokud chcete sdílet konfiguraci načítání projektu nebo ji potvrdit do správy zdrojového kódu, můžete vytvořit soubor filtru řešení (má příponu *.slnf*). Při otevření souboru filtru řešení se řešení otevře v sadě Visual Studio se načtenými zadanými projekty a všemi nezatíženými projekty. Můžete [přepnout zobrazení](#toggle-unloaded-project-visibility) uvolněné projekty.

Soubory filtrů řešení jsou vizuálně odlišeny od běžných souborů řešení dalším trychtýřovým glyfem v ikoně vedle řešení v **Průzkumníku řešení**. Název filtru a počet načtených projektů jsou také zobrazeny vedle názvu řešení.

![Soubor filtru řešení otevřený v Průzkumníku řešení Sady Visual Studio](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Pokud jsou nové projekty přidány do původního řešení po vytvoření souboru filtru řešení, zobrazí se jako uvolněné projekty v **Průzkumníku řešení**.

### <a name="create-a-solution-filter-file"></a>Vytvoření souboru filtru řešení

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na řešení a vyberte **možnost Uložit jako filtr řešení**.

   ![Nabídka Uložit jako filtr řešení v Průzkumníkovi řešení sady Visual Studio](media/filtered-solutions/save-as-solution-filter.png)

2. Zvolte název a umístění souboru filtru řešení.

Po vytvoření souboru filtru řešení se přidá do seznamu **Nedávné projekty a řešení** pro snadný přístup:

![Otevřít poslední v Sadě Visual Studio](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Viz také

- [Přizpůsobení vnořování souborů v Průzkumníku řešení](file-nesting-solution-explorer.md)
- [Optimalizace výkonu sady Visual Studio](optimize-visual-studio-performance.md)
