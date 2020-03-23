---
title: Konfigurace oboru analýzy živého kódu pro spravovaný kód
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 300e3f276a45cfe2115311c7d27eedce365616cf
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432236"
---
# <a name="how-to-configure-live-code-analysis-scope-for-managed-code"></a>Postup: Konfigurace oboru analýzy živého kódu pro spravovaný kód

## <a name="what-is-live-code-analysis-for-managed-code"></a>Co je "Analýza živého kódu" pro spravovaný kód?
Visual Studio provádí spoustu živých analýz kódu, označované také jako *analýza pozadí*, zatímco upravujete zdrojové soubory v editoru. Některé z těchto je požadováno minimální analýzy pro přijatelné prostředí visual studio IDE úpravy. Některé z těchto funkcí jsou určeny pro lepší odezvu pro funkce ide. Zatímco některé z nich je povolit další funkce IDE, jako je například diagnostika a opravy kódu z analyzátorů Roslyn. Na základě funkčnosti lze tyto analýzy seskupit takto:

- **Výpočet diagnostiky na pozadí**: Analýza pro výpočet chyb, upozornění a návrhů ve zdrojových souborech. Tato diagnostika se zobrazí jako položky v seznamu chyb a jako klikyháky v editoru. Mohou být rozděleny do dvou kategorií:
    - Diagnostika kompilátoru jazyka C# a Visual Basic
    - Diagnostika analyzátoru Roslyn, která zahrnuje:

        - Integrované analyzátory IDE pro návrhy stylů kódu a
        - Balíčky analyzátorů třetích stran [nainstalované](./install-roslyn-analyzers.md) pro projekty v aktuálním řešení.

- **Další analýzy na pozadí**: Analýza ke zlepšení odezvy a interakce sady Visual Studio pro funkce ide. Některé příklady takových analýz jsou:
    - Analýza otevřených souborů na pozadí.
    - Pozadí kompilace projektů s otevřenými soubory realizovat symboly pro lepší odezvu některých funkcí IDE.
    - Vytváření mezipamětí syntaxe a symbolů.
    - Zjišťování přidružení návrháře pro zdrojové soubory, jako jsou formuláře, ovládací prvky atd.

## <a name="default-analysis-scope"></a>Výchozí obor analýzy

Ve výchozím nastavení se provádí analýza živého kódu pro výpočty diagnostiky na pozadí pro všechny soubory, které jsou _otevřeny_ v sadě Visual Studio. Několik dalších výše _uvedených podkladových analýz_ provádí pro všechny projekty, které mají alespoň jeden otevřený soubor. Zatímco pro celé řešení se provádí jen málo analýz pozadí.

## <a name="custom-analysis-scope"></a>Vlastní obor analýzy

Výchozí rozsah každé analýzy pozadí byl vyladěn pro optimální uživatelské prostředí, funkce a výkon pro většinu zákaznických scénářů a řešení. Existují však případy, kdy zákazníci mohou chtít přizpůsobit tento obor tak, aby snížil nebo zvýšil analýzu pozadí. Například:

- Režim úspory energie: Pokud uživatelé běží na baterii notebooku, mohou chtít minimalizovat spotřebu energie pro delší životnost baterie. V tomto scénáři by chtěli minimalizovat analýzu na pozadí.
- Analýza kódu na vyžádání: Pokud uživatelé dávají přednost vypnutí spuštění živého analyzátoru a ručnímu spuštění analýzy kódu na vyžádání, budou chtít minimalizovat analýzu na pozadí. Viz [Postup: Ruční spuštění analýzy kódu na vyžádání](./how-to-run-code-analysis-manually-for-managed-code.md).
- Úplná analýza řešení: Pokud uživatelé chtějí vždy vidět všechny diagnostiky ve všech souborech v řešení, bez ohledu na to, zda jsou otevřeny v editoru nebo ne. V tomto scénáři by chtěli maximalizovat rozsah analýzy na pozadí celé řešení.

Počínaje Visual Studio 2019 verze 16.5, uživatelé mohou explicitně přizpůsobit rozsah všech analýz y živého kódu, včetně výpočtu diagnostiky, pro projekty jazyka C# a Visual Basic. Dostupné obory analýzy jsou:

- **Aktuální dokument**: Minimalizuje obor analýzy živého kódu, aby se spouštěl pouze pro aktuální nebo viditelný soubor v editoru.
- **Otevřené dokumenty**: Výchozí obor analýzy živého kódu, jak je popsáno ve výše uvedené části.
- **Celé řešení**: Maximalizuje obor analýzy živého kódu, který se má provést pro všechny soubory a projekty v celém řešení.

Jeden z výše uvedených vlastních oborů analýzy můžete zvolit v dialogovém okně Možnosti nástrojů pomocí následujících kroků:

1. Chcete-li otevřít dialogové okno **Možnosti,** zvolte na řádku nabídek v sadě Visual Studio **možnostI** > **nástroje**.

2. V dialogovém okně **Možnosti** zvolte **Textový editor** > **C#** nebo **Základní** > **upřesnit**.

3. Vyberte požadovaný **obor analýzy pozadí** pro přizpůsobení oboru analýzy. Až budete hotovi, zvolte **OK.**

![Rozsah analýzy.](./media/background-analysis-scope.png)

> [!NOTE]
> Před Visual Studio 2019 verze 16.5, uživatelé mohou přizpůsobit obor analýzy pro výpočet diagnostiky na celé řešení pomocí **povolit úplnou analýzu řešení** zaškrtávací políčko **z nástroje** > **možnosti** > textový**editor** > **C#** nebo **základní** > **rozšířené** karty. Neexistuje žádná podpora pro minimalizaci oboru analýzy pozadí v předchozích verzích sady Visual Studio.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Automatické minimalizace oboru analýzy živého kódu

Pokud Visual Studio zjistí, že 200 MB nebo méně systémové paměti je k dispozici, automaticky minimalizuje obor analýzy živého kódu na "Aktuální dokument". Pokud k tomu dojde, zobrazí se výstraha informující o tom, že sada Visual Studio zakázala některé funkce. Tlačítko umožňuje přepnout zpět do oboru předchozí analýzy, pokud chcete.

![Výstražný text minimalizace oboru analýzy](./media/fsa_alert.png)

## <a name="see-also"></a>Viz také

- [Automatické pozastavení funkce](./automatic-feature-suspension.md)
- [Požadavek funkce úspory energie](https://github.com/dotnet/roslyn/issues/38429)
