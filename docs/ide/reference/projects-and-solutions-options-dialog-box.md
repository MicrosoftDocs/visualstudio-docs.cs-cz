---
title: Dialogové okno Projekty a řešení, Možnosti
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ed60e07c625665f92838cfbc671b03c605fda0d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567642"
---
# <a name="options-dialog-box-projects-and-solutions--general"></a>Dialogové okno Možnosti: \> Projekty a řešení obecně

Na této stránce můžete definovat chování sady Visual Studio související s projekty a řešeními. Chcete-li získat přístup k těmto možnostem, vyberte**možnost Možnosti** **nástrojů** > , rozbalte **položku Projekty a řešení**a pak vyberte **Obecné**.

Následující možnosti jsou k dispozici na stránce **Obecné.**

## <a name="always-show-error-list-if-build-finishes-with-errors"></a>Vždy zobrazit seznam chyb, pokud sestavení skončí s chybami

Otevře okno **Seznam chyb** při dokončování sestavení pouze v případě, že se projektu nepodařilo sestavit. Zobrazí se chyby, ke kterým dochází během procesu sestavení. Pokud je tato možnost vymazána, stále dochází k chybám, ale okno se po dokončení sestavení neotevře. Tato možnost je ve výchozím nastavení povolená.

## <a name="track-active-item-in-solution-explorer"></a>Sledování aktivní položky v Průzkumníku řešení

Když je tato volba vybraná, **Průzkumník řešení** se automaticky otevře a vybere se aktivní položka. Vybraná položka se mění při práci s různými soubory v projektu nebo řešení nebo s různými součástmi v návrháři. Pokud tato možnost není zaškrtnuta, výběr v **Průzkumníku řešení** se automaticky nezmění. Tato možnost je ve výchozím nastavení povolená.

## <a name="show-advanced-build-configurations"></a>Zobrazit pokročilé konfigurace sestavení

Když je tato volba vybraná, volby konfigurace sestavení se zobrazí v dialogovém okně **Stránky vlastností projektu** a v dialogovém okně **Stránky vlastností řešení.** Pokud tato možnost není zaškrtnuta, možnosti konfigurace sestavení se nezobrazí v dialogovém okně **Stránky vlastností projektu** a v dialogovém okně **Stránky vlastností řešení** pro projekty jazyka Visual Basic a C#, které obsahují jednu konfiguraci nebo dvě konfigurace ladění a vydání. Pokud projekt má uživatelsky definovanou konfiguraci, zobrazí se možnosti konfigurace sestavení.

Pokud není vybraná volba, příkazy v nabídce **Sestavení,** například **Řešení sestavení**, Řešení **znovu sestavení**a Čisté **řešení**, se provádějí v konfiguraci vydání a příkazy v nabídce **Ladění,** například **Start Debugging** a **Start Without Debugging**, se provádějí v konfiguraci ladění.

## <a name="always-show-solution"></a>Vždy ukázat řešení

Pokud je tato možnost vybrána, řešení a všechny příkazy, které fungují na řešení jsou vždy zobrazeny v ide. Pokud není zaškrtnuto, všechny projekty jsou vytvořeny jako samostatné projekty a nevidíte řešení v Průzkumníku řešení nebo příkazy, které působí na řešení v rozhraní IDE, pokud řešení obsahuje pouze jeden projekt.

::: moniker range="vs-2017"

## <a name="save-new-projects-when-created"></a>Uložení nových projektů při vytvoření

Když je tato volba vybraná, můžete určit umístění projektu v dialogovém okně **Nový projekt.** Pokud je tato tato tato kniha nezaškrtnutá, jsou všechny nové projekty vytvořeny jako dočasné projekty. Při práci s dočasnými projekty můžete vytvořit projekt a experimentovat s ním, aniž byste museli zadávat umístění disku.

::: moniker-end

## <a name="warn-user-when-the-project-location-is-not-trusted"></a>Upozornit uživatele, pokud umístění projektu není důvěryhodné

Pokud se pokusíte vytvořit nový projekt nebo otevřít existující projekt v umístění, které není plně důvěryhodné (například na cestě UNC nebo cestě HTTP), zobrazí se zpráva. Tuto možnost použijte k určení, zda se zpráva zobrazí při každém pokusu o vytvoření nebo otevření projektu v umístění, které není plně důvěryhodné.

## <a name="show-output-window-when-build-starts"></a>Zobrazit okno Výstupu při spuštění sestavení

Automaticky zobrazí [okno Výstup](../../ide/reference/output-window.md) v ide na počátku sestavení řešení.

## <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Výzva k symbolickému přejmenování při přejmenování souborů

Pokud je tato možnost vybrána, visual studio zobrazí okno se zprávou s dotazem, zda by měl také přejmenovat všechny odkazy v projektu na prvek kódu.

## <a name="prompt-before-moving-files-to-a-new-location"></a>Dotázat se před přesunutím souborů do nového umístění

Pokud je tato možnost vybrána, zobrazí sada Visual Studio potvrzovací okno před změnou umístění souborů pomocí akcí v **Průzkumníku řešení**.

## <a name="reopen-documents-on-solution-load"></a>Opětovné otevření dokumentů při načtení řešení

Pokud je vybrána, dokumenty, které byly ponechány otevřené při předchozím uzavření řešení, se automaticky otevřou při otevření řešení.

Opětovné otevření určitých typů souborů nebo návrhářů může zpozdit načtení řešení. Zrušením zaškrtnutí této možnosti [můžete zlepšit výkon načítání řešení,](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) pokud nechcete obnovit předchozí kontext řešení.

::: moniker range=">=vs-2019"

## <a name="restore-solution-explorer-project-hierarchy-state-on-solution-load"></a>Obnovit stav hierarchie projektu Průzkumníka řešení při načtení řešení

Když je tato volba vybraná, obnoví stav uzlů v Průzkumníku řešení s ohledem na to, zda byly rozbaleny nebo sbaleny při posledním otevření řešení. Odznačte tuto volbu, chcete-li zkrátit dobu načítání řešení pro velká řešení.

> [!TIP]
> Pokud tuto možnost zakážete, snadným způsobem přechodu na aktivní dokument v Průzkumníku řešení je výběr **možnost Synchronizovat s aktivním dokumentem** na panelu nástrojů **Průzkumník řešení.**
>
> ![Synchronizace s aktivním dokumentem v Průzkumníku řešení](media/sync-active-document.png)

## <a name="open-sdk-style-project-files-with-double-click-or-the-enter-key"></a>Otevření souborů projektu ve stylu sady SDK s poklepáním nebo klávesou Enter

Pokud je tato volba vybraná a v editoru se poklepáním na uzel projektu ve stylu sady SDK vyberte a pak stiskněte **Klávesu Enter**, soubor projektu (například soubor \*.csproj) se otevře jako XML v editoru. Když to nevyberete, poklepáním na uzel projektu ve stylu sady SDK v Průzkumníkovi řešení nebo jeho výběrem a stisknutím **klávesy Enter** bude efekt pouze rozbalení nebo sbalení uzlu.

Pokud tuto možnost nemáte vybranou a chcete upravit soubor projektu ve stylu sady SDK, klepněte pravým tlačítkem myši na uzel projektu v Průzkumníku řešení a vyberte **upravit soubor projektu**. U jiných typů projektů je nutné nejprve uvolnit projekt před úpravou v sadě Visual Studio.

> [!TIP]
> *Projekt ve stylu sady SDK*nebo projekt [SDK](../../msbuild/how-to-use-project-sdk.md)má novější, efektivnější formát souboru projektu, který byl zaveden pomocí msbuild 15.0. Projekt ve stylu sady SDK obsahuje `Sdk` atribut `Project` prvku, například `<Project Sdk="Microsoft.NET.Sdk">`. Visual Studio vytvoří projekt ve stylu sady SDK při vytváření nového projektu .NET Core z jedné ze šablon sady Visual Studio, například.

::: moniker-end

## <a name="see-also"></a>Viz také

- [Dialogové okno Možnosti: \> Umístění projektů a řešení](projects-solutions-locations-options.md)
- [Dialogové okno Možnosti, Projekty a řešení, Sestavení a spuštění](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Dialogové okno Možnosti, Projekty a řešení, Webové projekty](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
