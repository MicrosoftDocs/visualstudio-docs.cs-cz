---
title: Hledání odkazů v kódu
ms.date: 09/26/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code editor, find all references
- find all references
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8ac09eace078ef60f36bd57e9a2c4a1e5f1c510c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942318"
---
# <a name="find-references-in-your-code"></a>Najít odkazy v kódu

Můžete použít **najít všechny odkazy** příkazu najděte, kde jsou elementy konkrétní kódu odkazovat v celé vaší základu kódu. **Najít všechny odkazy** příkaz je k dispozici v nabídce kontextu (klikněte pravým tlačítkem) elementu, které chcete najít odkazy na. Nebo, pokud se uživatel klávesnice, stiskněte klávesu **Shift + F12**.

Výsledky se zobrazí v okně nástroje s názvem  **<element> odkazy**, kde *element* je název položky, které chcete vyhledat. V panelu nástrojů **odkazy** okno umožňuje:
- Změňte rozsah vyhledávání v rozevíracím seznamu. Můžete hledat pouze v změněné dokumenty až celé řešení.
- Kopírovat vybrané odkazovaná položka výběrem **kopie** tlačítko.
- Zvolte tlačítek přejdete do umístění v seznamu, nebo klikněte na tlačítko Další nebo předchozí **F8** a **Shift + F8** klíče Uděláte to tak.
- Odebere všechny filtry u vrácených výsledků výběrem **vymazat všechny filtry** tlačítko.
- Změnit jak vrácené položky jsou seskupené podle výběr nastavení **Seskupit podle:** rozevíracího seznamu.
- Zachovat aktuální výsledků hledání tak, že zvolíte **zachovat výsledky** tlačítko. Pokud toto tlačítko, aktuální výsledky hledání zůstane v tomto okně a nové výsledky hledání se zobrazí v novém okně nástroje.
- Hledat řetězce v rámci výsledky hledání tak, že zadáte text v **hledání najít všechny odkazy** textové pole.

Můžete také ukazatele myši nad některý z výsledků hledání můžete zobrazit náhled odkazu.

![Najít všechny odkazy na okno nástroje](../ide/media/vside_findallreferences.png)

## <a name="navigate-to-references"></a>Přejděte na odkazy
Můžete použít následující metody přejděte na odkazy v **odkazy** okno:

- Stiskněte klávesu **F8** přejít na odkaz na další nebo **Shift + F8** přejít na předchozí odkaz.
- Stiskněte **Enter** klíče na odkaz, nebo na ni dvakrát kliknete, přejděte k němu v kódu.
- V místní nabídce odkazu, vyberte **přejděte do předchozího umístění** nebo **přejděte do následujícího umístění** příkazy.
- Vyberte **šipka nahoru** a **šipka dolů** klíče (pokud jsou povolené v **možnosti** dialogové okno). Chcete-li povolit tuto funkci na řádku nabídek zvolte **nástroje** > **možnosti** > **prostředí**  >   **Karty a okna** > **karta Náhled**a pak vyberte **povolit nové soubory otevřít na kartě preview** a **náhled vybrané soubory v Výsledky hledání** polí.

## <a name="change-reference-groupings"></a>Změna odkaz seskupení
Ve výchozím nastavení odkazy jsou seskupené podle projekt, pak podle definice. Toto seskupení pořadí však můžete změnit změnou nastavení v **Seskupit podle:** rozevírací seznam na panelu nástrojů. Například můžete změnit z výchozí nastavení **projektu pak definice** k **definice pak projekt**, i na další nastavení.

**Definice** a **projektu** se používají dvě výchozí seskupení, ale jiné můžete přidat výběrem **seskupení** na vybrané položky místní nabídky. Přidání další seskupení může být užitečné, pokud vaše řešení obsahuje mnoho souborů a cesty.

## <a name="see-also"></a>Viz také

- [Navigace v kódu](../ide/navigating-code.md)