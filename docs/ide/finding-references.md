---
title: Hledání odkazů v kódu
ms.date: 09/26/2017
ms.topic: conceptual
helpviewer_keywords:
- code editor, find all references
- find all references
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e4ef16ef88e871778fd4e0c755ffb156c374109
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592032"
---
# <a name="find-references-in-your-code"></a>Hledání odkazů v kódu

Pomocí příkazu **Najít všechny odkazy** můžete zjistit, kde jsou v rámci základu kódu odkazovány určité prvky kódu. Příkaz **Najít všechny odkazy** je k dispozici v nabídce kontext (klepnutí pravým tlačítkem myši) prvku, na který chcete najít odkazy. Pokud jste uživatelem klávesnice, stiskněte **shift + F12**.

Výsledky se zobrazí v ** \<** okně nástroje s názvem element> odkazy , kde *prvek* je název položky, kterou hledáte. Panel nástrojů v okně **odkazů** umožňuje:
- Změňte rozsah hledání v rozevíracím seznamu. Můžete se rozhodnout, že budete hledat pouze v změněných dokumentech až po celé řešení.
- Zkopírujte vybranou odkazovnou položku výběrem tlačítka **Kopírovat.**
- Zvolte tlačítka, chcete-li přejít na další nebo předchozí umístění v seznamu, nebo stiskněte klávesy **F8** a **Shift + F8.**
- Odstraňte všechny filtry na vrácených výsledcích výběrem tlačítka **Vymazat všechny filtry.**
- Způsob seskupení vrácených položek můžete změnit výběrem nastavení v rozevíracím seznamu **Skupina podle:** .
- Ponechte aktuální okno výsledků hledání výběrem tlačítka **Zachovat výsledky.** Když zvolíte toto tlačítko, aktuální výsledky hledání zůstanou v tomto okně a nové výsledky hledání se zobrazí v novém okně nástroje.
- Hledání řetězců ve výsledcích hledání zadáním textu do textového pole **Hledat všechny odkazy.**

Můžete také najet myší na libovolný výsledek hledání a zobrazit tak náhled odkazu.

![Okno nástroje Najít všechny reference](../ide/media/vside_findallreferences.png)

## <a name="navigate-to-references"></a>Přechod na odkazy
K navigaci na odkazy v okně **odkazů** můžete použít následující metody:

- Stisknutím **klávesy F8** přejdete na další odkaz nebo **shift + f8** přejděte na předchozí odkaz.
- Stisknutím klávesy **Enter** na odkaz nebo na ni poklepejte a přejděte na ni v kódu.
- V nabídce odkazu pravým tlačítkem myši (kontextová nabídka) zvolte příkazy **Přejít na předchozí umístění** nebo **Přejít na další umístění.**
- Zvolte klávesy **Šipka nahoru** a **Šipka dolů** (pokud jsou povolené v dialogovém okně **Možnosti).** Chcete-li tuto funkci povolit, **Tools** > zvolte na řádku nabídek karty**prostředí** > **Nástroje a** > karta Náhled**systému Windows** > **Preview Tab**a pak vyberte **možnost Povolit otevírání nových souborů na kartě Náhled** a Náhled vybraných souborů v polích Najít **výsledky.**

## <a name="change-reference-groupings"></a>Změna skupin odkazů
Ve výchozím nastavení jsou odkazy seskupeny podle projektu a potom podle definice. Toto pořadí seskupení však můžete změnit změnou nastavení v rozevíracím seznamu **Skupina podle:** na panelu nástrojů. Můžete jej například změnit z výchozího nastavení **aplikace Project a definice** na **definici a poté**na další nastavení.

**Definice** a **Aplikace Project** jsou dvě použitá výchozí seskupení, ale můžete přidat další výběrem příkazu **Seskupení** v nabídce pravým tlačítkem myši nebo v místní nabídce vybrané položky. Přidání dalších seskupení může být užitečné, pokud vaše řešení má velké množství souborů a cest.

## <a name="filter-by-reference-type-in-net"></a>Filtrování podle typu odkazu v rozhraní .NET
V jazyce C# nebo Visual Basic má okno Najít odkazy sloupec Kind, kde je uveden typ odkazu, který našel. Tento sloupec lze použít k filtrování podle typu odkazu kliknutím na ikonu filtru, která se zobrazí při najetí myší na záhlaví sloupce. Odkazy lze filtrovat podle čtení, zápisu, odkazu, názvu, oboru názvů a typu.

![Sloupec Najít odkazy na typ okna ](../ide/media/vside_findallreferencesKind.png)

## <a name="see-also"></a>Viz také

- [Navigace v kódu](../ide/navigating-code.md)
