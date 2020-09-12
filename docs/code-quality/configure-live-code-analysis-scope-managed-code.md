---
title: Konfigurace oboru dynamických analýz kódu pro .NET
ms.date: 09/01/2020
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 57ff963de193360712e92b76f3cafd7a75ee6b89
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90035414"
---
# <a name="configure-live-code-analysis-for-net"></a>Konfigurace Live Code Analysis pro .NET

Visual Studio provádí spoustu živých analýz kódu, označovaných také jako *Analýza na pozadí*, zatímco upravujete zdrojové soubory v editoru. U některých z nich je vyžadována minimální analýza přijatelného prostředí pro úpravu prostředí Visual Studio IDE. Některé z nich jsou pro lepší odezvu funkcí IDE. I když je některé z nich, je možné povolit další funkce IDE, jako jsou diagnostika a opravy kódu z analyzátorů Roslyn. Na základě těchto funkcí je možné tyto analýzy seskupit následujícím způsobem:

- **Výpočet diagnostiky na pozadí**: Analýza chyb, varování a návrhů ve zdrojových souborech. Tyto diagnostiky se zobrazují jako položky v seznamu chyb a jako vlnovky v editoru. Můžou být klasifikované do dvou kategorií:
  - Diagnostika kompilátoru C# a Visual Basic
  - Diagnostika analyzátoru Roslyn, která zahrnuje:

    - Integrované analyzátory IDE pro návrhy stylu kódu
    - Předdefinované analyzátory CA pro návrhy kvality kódu
    - Balíčky analyzátoru třetích stran [nainstalované](./install-roslyn-analyzers.md) pro projekty v aktuálním řešení.

- **Další analýzy na pozadí**: analýza pro zlepšení rychlosti odezvy a interakce sady Visual Studio pro funkce IDE. Mezi příklady takových analýz patří:
  - Analýza otevřených souborů na pozadí
  - Kompilace projektů na pozadí s otevřenými soubory k přijetí symbolů pro lepší odezvu určitých funkcí IDE.
  - Vytváření syntaxí a mezipamětí symbolů.
  - Zjišťování přidružení návrháře pro zdrojové soubory, jako jsou formuláře, ovládací prvky atd.

## <a name="default-analysis-scope"></a>Výchozí obor analýzy

Ve výchozím nastavení se dynamická analýza kódu pro výpočet diagnostiky spustí pro všechny soubory, které jsou _otevřeny_ v aplikaci Visual Studio. Některé z _dalších analýz na pozadí_ zmíněných výše jsou spouštěny pro všechny projekty, které mají alespoň jeden otevřený soubor. I když je u celého řešení prováděno málo analýz na pozadí.

## <a name="custom-analysis-scope"></a>Rozsah vlastní analýzy

Výchozí obor každé analýzy na pozadí byl vyladěn pro optimální prostředí uživatele, funkčnost a výkon většiny scénářů a řešení zákazníků. Existují však případy, kdy si zákazníci můžou chtít tento rozsah přizpůsobit a snížit nebo zvýšit analýzu na pozadí. Například:

- Režim úspory napájení: Pokud uživatelé běží na přenosném počítači, můžou chtít snížit spotřebu energie při delším výdrži baterie. V tomto scénáři by chtěli minimalizovat analýzu na pozadí.
- Analýza kódu na vyžádání: Pokud uživatelé chtějí vypnout provádění živého analyzátoru a ručně spustit analýzu kódu na vyžádání, měli byste minimalizovat analýzu na pozadí. Viz [Postupy: ruční spuštění analýzy kódu na vyžádání](./how-to-run-code-analysis-manually-for-managed-code.md).
- Úplná analýza řešení: Pokud uživatelé chtějí vždycky zobrazit veškerou diagnostiku ve všech souborech v řešení bez ohledu na to, zda jsou otevřeny v editoru nebo nikoli. V tomto scénáři by chtěli maximalizovat rozsah analýzy na pozadí na celé řešení.

Počínaje verzí Visual Studio 2019 verze 16,5 mohou uživatelé explicitně přizpůsobit rozsah všech živých analýz kódu, včetně výpočtů diagnostiky pro projekty C# a Visual Basic. Dostupné obory analýzy:

- **Aktuální dokument**: minimalizuje obor analýzy živého kódu tak, aby byl spuštěn pouze pro aktuální nebo viditelný soubor v editoru.
- **Otevřete dokumenty**: výchozí obor analýzy živého kódu, jak je popsáno v předchozí části.
- **Celé řešení**: maximalizuje obor analýzy živého kódu, který se má spustit pro všechny soubory a projekty v celém řešení.

V dialogovém okně Možnosti nástrojů můžete zvolit jeden z výše uvedených vlastních oborů analýzy pomocí následujících kroků:

1. Chcete-li otevřít dialogové okno **Možnosti** , na panelu nabídek v aplikaci Visual Studio **Tools**vyberte  >  **možnost**nástroje.

2. V dialogovém okně **Možnosti** vyberte možnost **textový editor**  >  **C#** nebo **základní**  >  **Upřesnit**.

3. Vyberte požadovaný **obor analýzy pozadí** pro přizpůsobení oboru analýzy. Až skončíte, klikněte na **OK** .

![Rozsah analýzy.](./media/background-analysis-scope.png)

> [!NOTE]
> Před verzí sady Visual Studio 2019 verze 16,5 mohou uživatelé přizpůsobit rozsah analýzy pro výpočty diagnostiky na celé řešení pomocí zaškrtávacího políčka **Povolit kompletní analýzu řešení** v části **nástroje**  >  **Options**  >  **textový editor**  >  **C#** nebo **základní**  >  karta**Upřesnit** . V předchozích verzích sady Visual Studio není podporována podpora pro minimalizaci oboru analýzy na pozadí.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Automaticky minimalizovat obor analýzy živých kódů

Pokud aplikace Visual Studio zjistí, že je k dispozici 200 MB nebo méně systémové paměti, automaticky minimalizuje obor analýzy živého kódu na aktuální dokument. V takovém případě se zobrazí výstraha informující o tom, že aplikace Visual Studio zakázala některé funkce. Tlačítko umožňuje přejít zpět na obor předchozí analýzy, pokud chcete.

![Text výstrahy, která minimalizuje rozsah analýzy](./media/fsa_alert.png)

## <a name="see-also"></a>Viz také

- [Automatické pozastavení funkce](./automatic-feature-suspension.md)
- [Požadavek na funkci režimu úspory napájení](https://github.com/dotnet/roslyn/issues/38429)
