---
title: Možnosti stylu kódu a vyčištění kódu
description: Naučte se, jak nakonfigurovat Visual Studio pro použití předvoleb stylu kódu pomocí příkazů pro vyčištění kódu (Visual Studio 2019) a formátování dokumentu (Visual Studio 2017).
ms.custom: SEO-VS-2020
ms.date: 04/25/2019
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 0aafcb1740f0e17234d2e4da38630c1416c44e9c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841938"
---
# <a name="code-style-preferences"></a>Předvolby stylu kódu

Můžete definovat nastavení stylu kódu pro jednotlivé projekty pomocí [souboru EditorConfig](#code-styles-in-editorconfig-files)nebo pro veškerý kód, který upravíte v aplikaci Visual Studio na [stránce **Možnosti**](#code-styles-in-the-options-dialog-box)textového editoru. Pro kód jazyka C# můžete také nakonfigurovat aplikaci Visual Studio, aby používala Tyto předvolby stylu kódu pomocí příkazů pro **Vyčištění kódu** (visual Studio 2019) a **formátovat dokument** (Visual Studio 2017).

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [chování editoru v Visual Studio pro Mac](/visualstudio/mac/editor-behavior).

## <a name="code-styles-in-editorconfig-files"></a>Styly kódu v souborech EditorConfig

[Nastavení stylu kódu](/dotnet/fundamentals/code-analysis/code-style-rule-options) pro rozhraní .NET lze určit přidáním souboru [EditorConfig](create-portable-custom-editor-options.md) do projektu. Soubory EditorConfig jsou přidruženy k základu kódu a nikoli k účtu přizpůsobení sady Visual Studio. Nastavení v souboru EditorConfig mají přednost před styly kódu, které jsou uvedeny v dialogovém okně **Možnosti** . Soubor EditorConfig použijte, pokud chcete vymáhat styly kódování pro všechny přispěvatele do vašeho úložiště nebo projektu.

::: moniker range=">=vs-2019"

Můžete ručně naplnit soubor EditorConfig nebo můžete soubor automaticky vygenerovat na základě nastavení stylu kódu, které jste zvolili v dialogovém okně **Možnosti** sady Visual Studio. Tato stránka možností je k dispozici v **nabídce nástroje**–  >    >  **textový editor** > [**C#** nebo **Basic**] > **styl kódu**  >  **Obecné**. Klikněte na **Generovat soubor. editorconfig z nastavení** a automaticky vygenerujte soubor *. editorconfig* stylu kódování na základě nastavení na této stránce **Možnosti** .

![Generování souboru editorconfig z nastavení v aplikaci Visual Studio 2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>Styly kódu v dialogovém okně Možnosti

Předvolby stylu kódu lze nastavit pro všechny projekty C# a Visual Basic otevřením dialogového okna **Možnosti** v nabídce **nástroje** . V dialogovém okně **Možnosti** vyberte **textový editor** > [**C#** nebo **Basic**] > **styl kódu**  >  **Obecné**.

Každá položka v seznamu zobrazuje náhled předvolby, pokud je vybrána možnost:

::: moniker range="vs-2017"

![Možnosti stylu kódu](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Možnosti stylu kódu](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

Možnosti nastavené v tomto okně se vztahují na váš účet přizpůsobení sady Visual Studio a nejsou přidružené ke konkrétnímu projektu nebo základu kódu. Kromě toho nejsou vynutily při sestavování, včetně v sestaveních průběžné integrace (CI). Chcete-li přidružit předvolby stylu kódu k vašemu projektu a nechat styly vynutily během sestavování, určete předvolby v [souboru. editorconfig](#code-styles-in-editorconfig-files) , který je přidružen k projektu.

### <a name="preference-and-severity"></a>Preference a závažnost

U každého nastavení stylu kódu na této stránce můžete nastavit hodnoty **předvoleb** a **závažnosti** pomocí rozevíracích seznamu na každém řádku. Závažnost se dá nastavit jenom na **refaktoring**, **Návrh**, **varování** nebo **chybu**. Pokud chcete povolit [rychlé akce](../ide/quick-actions.md) pro styl kódu, zajistěte, aby bylo nastavení **závažnosti** nastaveno na jinou hodnotu než **refaktoring**. V  případě, že :::image type="icon" source="media/light-bulb-dropdown.png"::: :::image type="icon" source="media/error-bulb.png"::: :::image type="icon" source="media/screwdriver.png"::: se používá nepreferovaný styl, se v případě použití nepreferovaného stylu zobrazí žárovka s rychlými akcemi, chybová žárovka nebo ikona Screwdriver a můžete vybrat možnost v seznamu **rychlé akce** a automaticky přepisovat kód na preferovaný styl.

::: moniker range=">=vs-2019"

## <a name="enforce-code-styles-on-build"></a>Vymáhat styly kódu při sestavení

Počínaje verzí Visual Studio 2019 verze 16,8, která zahrnuje sadu .NET 5,0 RC2 SDK, můžete [vyhovět konvencím kódování .NET pro sestavení](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis) pro všechny projekty .NET. V době sestavení se porušení stylu kódu .NET zobrazí jako upozornění nebo chyby s předponou "IDE". To umožňuje striktně vymáhat konzistentní styly kódu v základu kódu.

::: moniker-end

## <a name="apply-code-styles"></a>Použít styly kódu

::: moniker range="vs-2017"

Můžete nakonfigurovat příkaz **formátovat dokument** (**Upravit**  >  **Rozšířený**  >  **Formát dokumentu**), chcete-li použít nastavení stylu kódu (ze souboru EditorConfig nebo možnosti **stylu kódu** ), spolu s běžným formátováním, které provádí (například odsazení). Pokud soubor *. editorconfig* pro projekt existuje, mají tato nastavení přednost.

> [!NOTE]
> Použití stylů kódu pomocí příkazu **formátovat dokument** je k dispozici pouze pro soubory kódu jazyka C#. Toto je experimentální funkce.

Nakonfigurujte nastavení, které má **formátovat dokument** použít na [stránce možnosti formátování](reference/options-text-editor-csharp-formatting.md#format-document-settings).

![Nastavení stylu kódu pro formát dokumentu v aplikaci Visual Studio 2017](media/format-document-settings-experiment.png)

> [!TIP]
> Pravidla konfigurovaná se závažností **none** se nepodílejí na čištění kódu, ale lze je individuálně použít prostřednictvím nabídky **rychlé akce a refaktoringu** .

Při prvním spuštění příkazu **Formát dokumentu** vás žlutý informační panel vyzve ke konfiguraci nastavení pro vyčištění kódu.

::: moniker-end

::: moniker range=">=vs-2019"

Pro soubory kódu jazyka C# má Visual Studio 2019 tlačítko pro **Vyčištění kódu** v dolní části editoru (klávesnice: **CTRL** + **K**, **CTRL** + **E**) pro použití stylů kódu ze souboru EditorConfig nebo ze stránky možností **stylu kódu** . Pokud soubor *. editorconfig* existuje pro projekt, jsou to nastavení, která mají přednost.

![Spustit čištění kódu v aplikaci Visual Studio 2019](media/execute-code-cleanup.png)

> [!TIP]
> Pravidla konfigurovaná se závažností **none** se nepodílejí na čištění kódu, ale lze je individuálně použít prostřednictvím nabídky **rychlé akce a refaktoringu** .

Nejprve nakonfigurujte styly kódu, které chcete použít (v jednom ze dvou profilů) v dialogovém okně **Konfigurovat vyčištění kódu** . Chcete-li otevřít toto dialogové okno, klikněte na šipku vedle ikony vyčištění kódu Broom a pak zvolte možnost **Konfigurovat vyčištění kódu**.

![Konfigurace vyčištění kódu v aplikaci Visual Studio 2019](media/configure-code-cleanup.png)

Po nakonfigurování vyčištění kódu můžete buď kliknout na ikonu Broom, nebo stisknout **kombinaci kláves CTRL** + **k**, **CTRL** + **E** a spustit program Vyčištění kódu. Můžete také spustit vyčištění kódu v celém projektu nebo řešení. Klikněte pravým tlačítkem myši na název projektu nebo řešení v **Průzkumník řešení**, vyberte **Analýza a vyčištění kódu** a pak vyberte **Spustit vyčištění kódu**.

![Spustit čištění kódu v celém projektu nebo řešení](media/run-code-cleanup-project-solution.png)

Pokud chcete, aby nastavení stylu kódu bylo použito při každém uložení souboru, může se stát, že v rozšíření [pro uložení bude provedeno vyčištění kódu](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave) .

::: moniker-end

## <a name="see-also"></a>Viz také

- [Rychlé akce](../ide/quick-actions.md)
- [Nastavení konvence kódování .NET pro EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)
- [Chování editoru (Visual Studio pro Mac)](/visualstudio/mac/editor-behavior)
