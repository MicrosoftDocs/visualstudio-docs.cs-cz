---
title: Možnosti stylu kódu a vyčištění kódu
ms.date: 04/25/2019
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 9d540339ca25fc42fc05df4818a6d05204ccae0e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301858"
---
# <a name="code-style-preferences"></a>Předvolby stylu kódu

Nastavení stylu kódu pro každou projekt můžete definovat pomocí [souboru EditorConfig](#code-styles-in-editorconfig-files)nebo pro veškerý kód, který v aplikaci Visual Studio upravujete na stránce [ **Možnosti** ](#code-styles-in-the-options-dialog-box)textového editoru . Pro kód C# můžete také nakonfigurovat Visual Studio použít tyto předvolby stylu kódu pomocí příkazů **Vyčištění kódu** (Visual Studio 2019) a **Formát dokumentu** (Visual Studio 2017).

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu Editor behavior in Visual Studio for Mac](/visualstudio/mac/editor-behavior).

## <a name="code-styles-in-editorconfig-files"></a>Styly kódu v souborech EditorConfig

[Nastavení stylu kódu](../ide/editorconfig-code-style-settings-reference.md) pro rozhraní .NET lze zadat přidáním souboru [EditorConfig](create-portable-custom-editor-options.md) do projektu. EditorConfig soubory jsou přidruženy k základu kódu, nikoli visual studio individuální účet. Nastavení v souboru EditorConfig mají přednost před styly kódu, které jsou zadány v dialogovém okně **Možnosti.** Soubor EditorConfig použijte, pokud chcete vynutit styly kódování pro všechny přispěvatele do vašeho repo nebo projektu.

::: moniker range=">=vs-2019"

Můžete ručně naplnit soubor EditorConfig nebo můžete automaticky generovat soubor na základě nastavení stylu kódu, které jste zvolili v dialogovém okně **Možnosti** sady Visual Studio. Tato stránka možností je k dispozici na stránce **Tools** > **Options** > **Text Editor** > [**C#** nebo **Basic**] > Style **Code** > **General**. Chcete-li automaticky generovat kódovací styl *souboru Editorconfig* na základě nastavení na této stránce **Možnosti,** klepněte na **tlačítko Generovat soubor editorconfig z nastavení.**

![Generovat soubor editorconfig z nastavení v Sadě Visual Studio 2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>Styly kódu v dialogovém okně Možnosti

Předvolby stylu kódu lze nastavit pro všechny projekty jazyka C# a Visual Basic otevřením dialogového okna **Možnosti** z nabídky **Nástroje.** V dialogovém okně **Možnosti** vyberte **textový editor** > [**C#** nebo **Basic**] > **styl** > kódu**Obecné**.

Každá položka v seznamu zobrazuje náhled předvoleb, když je vybrána:

::: moniker range="vs-2017"

![Možnosti stylu kódu](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Možnosti stylu kódu](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

Možnosti nastavené v tomto okně platí pro váš účet přizpůsobení sady Visual Studio a nejsou přidruženy k určitému projektu nebo základu kódu. Kromě toho nejsou vynuceny v době sestavení, včetně sestavení průběžné integrace (CI). Pokud chcete přidružit předvolby stylu kódu k projektu a mít styly vynucené během sestavení, zadejte předvolby v [souboru .editorconfig,](#code-styles-in-editorconfig-files) který je přidružen k projektu.

### <a name="preference-and-severity"></a>Preference a závažnost

Pro každé nastavení stylu kódu na této stránce můžete nastavit hodnoty **předvoleb** a **závažnosti** pomocí rozevíracích seznamů na každém řádku. Závažnost lze nastavit na **pouze refaktoring**, **návrh**, **upozornění**nebo **chybu**. Pokud chcete povolit [rychlé akce](../ide/quick-actions.md) pro styl kódu, ujistěte se, že nastavení **závažnosti** je nastavena na něco jiného než **pouze refaktoring**. Při použití nepreferovaného stylu ![se zobrazí](media/error-bulb.png)žárovka](media/light-bulb-dropdown.png) ![Rychlé ![](media/screwdriver.png) **akce** , chybová žárovka s chybou žárovky nebo šroubovák šroubováku a můžete zvolit volbu v seznamu **Rychlé akce,** která automaticky přepíše kód na preferovaný styl.

## <a name="apply-code-styles"></a>Použití stylů kódu

::: moniker range="vs-2017"

Příkaz Formát **dokumentu** **(Upravit** > **dokument s rozšířeným** > **formátem)** můžete nakonfigurovat tak, aby použil nastavení stylu kódu (ze souboru EditorConfig nebo voleb **stylu kódu)** spolu s běžným formátováním (například odsazením). Pokud pro projekt existuje soubor *.editorconfig,* mají tato nastavení přednost.

> [!NOTE]
> Použití stylů kódu pomocí příkazu **Formát dokumentu** je k dispozici pouze pro soubory kódu Jazyka C#. Jedná se o experimentální funkci.

Nakonfigurujte nastavení, která mají **formát document** použít na [stránce Možnosti formátování](reference/options-text-editor-csharp-formatting.md#format-document-settings).

![Nastavení stylu kódu pro formátdokumentu ve Visual Studiu 2017](media/format-document-settings-experiment.png)

> [!TIP]
> Pravidla nakonfigurovaná se závažností **Žádné** se neúčastní čištění kódu, ale lze je jednotlivě použít prostřednictvím nabídky **Rychlé akce a Refaktorings.**

Při prvním spuštění příkazu **Formát dokumentu** se žlutý informační panel zobrazí výzvu ke konfiguraci nastavení čištění kódu.

::: moniker-end

::: moniker range=">=vs-2019"

Pro soubory kódu Jazyka C# visual studio 2019 má tlačítko **Vyčištění kódu** v dolní části editoru (klávesnice: **Ctrl**+**K**, **Ctrl**+**E**) použít styly kódu ze souboru EditorConfig nebo ze stránky možnosti **styl kódu.** Pokud pro projekt existuje soubor *.editorconfig,* jedná se o nastavení, která mají přednost.

![Spuštění vyčištění kódu v Sadě Visual Studio 2019](media/execute-code-cleanup.png)

> [!TIP]
> Pravidla nakonfigurovaná se závažností **Žádné** se neúčastní čištění kódu, ale lze je jednotlivě použít prostřednictvím nabídky **Rychlé akce a Refaktorings.**

Nejprve nakonfigurujte styly kódu, které chcete použít (v jednom ze dvou profilů) v dialogovém okně **Konfigurovat vyčištění kódu.** Chcete-li otevřít toto dialogové okno, klepněte na rozbalovací šipku vedle ikony koštěčištění kódu a pak zvolte **Konfigurovat vyčištění kódu**.

![Konfigurace vyčištění kódu v Sadě Visual Studio 2019](media/configure-code-cleanup.png)

Po nakonfigurování vyčištění kódu můžete buď kliknout na ikonu koštěteček, nebo stisknout **kombinaci kláves Ctrl**+**K**, **Ctrl**+**E** a spustit vyčištění kódu. Můžete také spustit vyčištění kódu v celém projektu nebo řešení. Klikněte pravým tlačítkem myši na název projektu nebo řešení v **Průzkumníku řešení**, vyberte **analyzovat a vyčistit kód**a pak vyberte Spustit vyčištění **kódu**.

![Spuštění vyčištění kódu v celém projektu nebo řešení](media/run-code-cleanup-project-solution.png)

Pokud chcete, aby nastavení stylu kódu bylo použito při každém uložení souboru, může se vám líbit [přípona Vyčištění kódu při uložení.](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave)

::: moniker-end

## <a name="see-also"></a>Viz také

- [Rychlé akce](../ide/quick-actions.md)
- [Nastavení konvence kódování .NET pro EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Chování editoru (Visual Studio pro Mac)](/visualstudio/mac/editor-behavior)
