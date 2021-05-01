---
title: Načtení podmnožiny projektů
description: Přečtěte si o filtrování řešení a o tom, jak umožňuje rychle načíst podmnožinu projektů v řešení.
ms.custom: SEO-VS-2020
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- filtered solution
- solution filtering
author: TerryGLee
ms.author: stsu
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: ea30edbaac7248af8e1a58b76aebd66cf44befba
ms.sourcegitcommit: a667ce8394a800906d633737f4fcbc77f0fcba7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2021
ms.locfileid: "108298727"
---
# <a name="filtered-solutions-in-visual-studio"></a>Filtrovaná řešení v aplikaci Visual Studio

Velké vývojové týmy často spolupracují pomocí jediného velkého řešení s mnoha projekty. Nicméně jednotliví vývojáři obvykle pracují na malé podmnožině těchto projektů. Pro zlepšení výkonu při otevírání rozsáhlých řešení Visual Studio 2019 zavedlo *filtrování řešení*. Filtrování řešení umožňuje otevřít řešení s načtenými pouze selektivními projekty. Načtení podmnožiny projektů v řešení snižuje dobu načtení, sestavení a testovací běh, a umožňuje tak více zaměřené revize.

K dispozici jsou následující funkce:

- Kód můžete rychleji získat tak, že otevřete řešení bez načtení některého z jeho projektů. Po otevření řešení můžete selektivně zvolit, které projekty se mají načíst.

- Po opětovném otevření řešení se v aplikaci Visual Studio pamatuje, které projekty byly načteny do předchozí relace a jsou načteny pouze do těchto projektů.

- Můžete vytvořit soubor filtru řešení, pomocí kterého uložíte jednu nebo více konfigurací projektu, nebo sdílíte konfiguraci s ostatními týmu.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows.

## <a name="open-a-filtered-solution"></a>Otevření filtrovaného řešení

Řešení můžete otevřít bez načtení některého z jeho projektů přímo z dialogového okna **Otevřít projekt** nebo pomocí [příkazového řádku](#command-line).

### <a name="open-project-dialog"></a>Otevřít dialog projektu

Chcete-li otevřít řešení bez načtení některého z jeho projektů pomocí dialogového okna **Otevřít projekt** :

1. V řádku nabídek vyberte **soubor**  >  **otevřít**  >  **projekt nebo řešení** .

2. V dialogovém okně **Otevřít projekt** vyberte řešení a pak vyberte **nenačíst projekty**.

   ![Visual Studio – dialogové okno otevřít projekt se zaškrtnutými možnostmi nenačíst projekty](media/filtered-solutions/do-not-load-projects.png)

3. Klikněte na tlačítko **otevřít**.

   Řešení se otevře se všemi jeho projekty se Nenačtené.

4. V **Průzkumník řešení** vyberte projekty, které chcete načíst (stisknutím klávesy **CTRL** vyberte více než jeden projekt) a pak klikněte pravým tlačítkem na projekt a zvolte **znovu načíst projekt**.

   ![Opětovné načtení více projektů v aplikaci Visual Studio Průzkumník řešení](media/filtered-solutions/reload-project.png)

   Visual Studio si zapamatuje, které projekty se načtou při příštím otevření řešení v místním prostředí.

### <a name="command-line"></a>Příkazový řádek

(Novinka v aplikaci Visual Studio 2019 verze 16,1.)

Chcete-li otevřít řešení bez načtení některého z jeho projektů z příkazového řádku, použijte [`/donotloadprojects`](../ide/reference/donotloadprojects-devenv-exe.md) přepínač, jak je znázorněno v následujícím příkladu:

```cmd
devenv /donotloadprojects MySln.sln
```

## <a name="toggle-unloaded-project-visibility"></a>Přepnout Viditelnost nenačtených projektů

Můžete se rozhodnout, zda chcete zobrazit všechny projekty v řešení, nebo pouze načtené pomocí jedné z následujících možností v **Průzkumník řešení**:

- Klikněte pravým tlačítkem na řešení a vyberte **Zobrazit uvolněné projekty** nebo **Skrýt uvolněné projekty**.

- Vyberte uzel řešení a povolte tlačítko **Zobrazit všechny soubory** ; pak klikněte na tlačítko a přepněte viditelnost nenačtených projektů.

   ![Tlačítko Zobrazit všechny soubory v aplikaci Visual Studio Průzkumník řešení](media/filtered-solutions/show-all-files.PNG)

## <a name="load-project-dependencies"></a>Načíst závislosti projektu

V řešení, kde jsou načteny pouze vybrané projekty, nemusí být načteny všechny závislosti projektu projektu. Pomocí možnosti nabídky **načíst závislosti projektů** zajistěte, aby všechny projekty, na kterých je projekt závislý, byly také načteny. V **Průzkumník řešení** klikněte pravým tlačítkem na jeden nebo více načtených projektů a vyberte **načíst závislosti projektu**.

![Načtení závislostí projektu v aplikaci Visual Studio 2019](media/filtered-solutions/load-project-dependencies.png)

## <a name="solution-filter-files"></a>Soubory filtru řešení

Pokud chcete sdílet projekt – načíst konfiguraci nebo potvrdit ho do správy zdrojového kódu, můžete vytvořit soubor filtru řešení (má příponu *. slnf*). Když otevřete soubor filtru řešení, otevře se řešení v aplikaci Visual Studio se zadanými projekty a všechny uvolněné projekty jsou skryté. Můžete [přepínat](#toggle-unloaded-project-visibility) a zobrazit uvolněné projekty.

Soubory filtru řešení jsou vizuálně odlišené od běžných souborů řešení podle dalšího trychtýřového glyfu v ikoně vedle řešení v **Průzkumník řešení**. Název filtru a počet načtených projektů jsou také zobrazeny vedle názvu řešení.

![Soubor filtru řešení je otevřený v aplikaci Visual Studio Průzkumník řešení](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Pokud jsou do původního řešení přidány nové projekty po vytvoření souboru filtru řešení, zobrazí se jako Nenačtené projekty v **Průzkumník řešení**.

### <a name="create-a-solution-filter-file"></a>Vytvoření souboru filtru řešení

1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Uložit jako filtr řešení**.

   ![Nabídka Uložit jako filtr řešení v aplikaci Visual Studio Průzkumník řešení](media/filtered-solutions/save-as-solution-filter.png)

2. Vyberte název a umístění souboru filtru řešení.

Po vytvoření souboru filtru řešení se tento soubor přidá do seznamu **posledních projektů a řešení** pro snadný přístup:

![Otevřít nedávné v aplikaci Visual Studio](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Viz také

- [Přizpůsobení vnořování souborů v Průzkumníku řešení](file-nesting-solution-explorer.md)
- [Optimalizace výkonu sady Visual Studio](optimize-visual-studio-performance.md)
