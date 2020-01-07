---
title: Projekty a řešení, dialogové okno Možnosti
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567642"
---
# <a name="options-dialog-box-projects-and-solutions--general"></a>Dialogové okno Možnosti: projekty a řešení \> obecné

Pomocí této stránky můžete definovat chování sady Visual Studio související s projekty a řešeními. Chcete-li získat přístup k těmto možnostem, vyberte možnost **nástroje** > **Možnosti**, rozbalte položku **projekty a řešení**a pak vyberte možnost **Obecné**.

Na stránce **Obecné** jsou k dispozici následující možnosti.

## <a name="always-show-error-list-if-build-finishes-with-errors"></a>Při dokončení buildu vždycky zobrazit Seznam chyb s chybami

Otevře okno **Seznam chyb** při dokončování sestavení, pouze pokud se projekt nepovedlo sestavit. Zobrazí se chyby, ke kterým dojde během procesu sestavení. Pokud je tato možnost smazána, k chybám stále dochází, ale okno není po dokončení sestavení otevřeno. Tato možnost je ve výchozím nastavení povolená.

## <a name="track-active-item-in-solution-explorer"></a>Sledovat aktivní položku v Průzkumník řešení

Když se tato možnost vybere, **Průzkumník řešení** se automaticky otevře a vybere se aktivní položka. Vybraná položka se mění při práci s různými soubory v projektu nebo řešení nebo v různých součástech v návrháři. Pokud je tato možnost vymazána, výběr v **Průzkumník řešení** se nemění automaticky. Tato možnost je ve výchozím nastavení povolená.

## <a name="show-advanced-build-configurations"></a>Zobrazit pokročilé konfigurace sestavení

Je-li vybrána tato možnost, možnosti konfigurace sestavení se zobrazí v dialogovém okně **stránky vlastností projektu** a v dialogovém okně **stránky vlastností řešení** . Pokud je zaškrtnuto, možnosti konfigurace sestavení se nezobrazují v dialogovém okně **stránky vlastností projektu** a v dialogovém okně **stránky vlastností řešení** pro Visual Basic a C# projekty, které obsahují jednu konfiguraci nebo dvě konfigurace ladění a vydání. Pokud má projekt uživatelsky definované konfigurace, zobrazí se možnosti konfigurace sestavení.

Pokud není vybráno, příkazy v nabídce **sestavení** , jako je **sestavení řešení**, **opětovné sestavení**řešení a **Vyčištění**, jsou prováděny v konfiguraci vydané verze a příkazy v nabídce **ladění** , jako je například **Spustit ladění** a **Spustit bez ladění**, jsou prováděny v konfiguraci ladění.

## <a name="always-show-solution"></a>Vždy zobrazit řešení

Je-li toto políčko zaškrtnuto, řešení a všechny příkazy, které fungují na řešení, jsou vždy zobrazeny v integrovaném vývojovém prostředí. Pokud je zaškrtnuto, všechny projekty jsou vytvořeny jako samostatné projekty a toto řešení se nezobrazuje v Průzkumník řešení nebo příkazy, které fungují na řešeních v rozhraní IDE, pokud řešení obsahuje pouze jeden projekt.

::: moniker range="vs-2017"

## <a name="save-new-projects-when-created"></a>Uložit nové projekty při vytvoření

Když je tato možnost vybrána, můžete v dialogovém okně **Nový projekt** zadat umístění pro projekt. Po zaškrtnutí budou všechny nové projekty vytvořeny jako dočasné projekty. Při práci s dočasnými projekty můžete vytvořit a experimentovat s projektem bez nutnosti zadávat umístění na disku.

::: moniker-end

## <a name="warn-user-when-the-project-location-is-not-trusted"></a>Upozornit uživatele, pokud umístění projektu není důvěryhodné

Pokud se pokusíte vytvořit nový projekt nebo otevřít existující projekt v umístění, které není plně důvěryhodné (například na cestě UNC nebo v cestě HTTP), zobrazí se zpráva. Tuto možnost použijte, chcete-li určit, zda se zpráva zobrazí při každém pokusu o vytvoření nebo otevření projektu v umístění, které není plně důvěryhodné.

## <a name="show-output-window-when-build-starts"></a>Zobrazit okno výstup při zahájení sestavování

Automaticky zobrazí [okno výstup](../../ide/reference/output-window.md) v integrovaném vývojovém prostředí na začátku sestavení řešení.

## <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Při přejmenování souborů zobrazit výzvu k zadání symbolického názvu

Je-li vybrána tato možnost, aplikace Visual Studio zobrazí okno se zprávou s dotazem, zda by měla být také přejmenovány všechny odkazy v projektu na prvek kódu.

## <a name="prompt-before-moving-files-to-a-new-location"></a>Dotázat se před přesunutím souborů na nové umístění

Je-li vybrána tato možnost, aplikace Visual Studio zobrazí okno potvrzovací zprávy před změnou umístění souborů pomocí akcí v **Průzkumník řešení**.

## <a name="reopen-documents-on-solution-load"></a>Znovu otevřít dokumenty při načtení řešení

Když je tato možnost vybraná, dokumenty, které zůstaly otevřené, se po otevření řešení automaticky otevřou.

Opětovné otevření určitých typů souborů nebo návrhářů může zpozdit zatížení řešení. Zrušte tuto možnost, pokud chcete [zlepšit výkon při načítání řešení](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) , pokud nechcete obnovit předchozí kontext řešení.

::: moniker range=">=vs-2019"

## <a name="restore-solution-explorer-project-hierarchy-state-on-solution-load"></a>Obnovit Průzkumník řešení stav hierarchie projektu při načtení řešení

Pokud je tato možnost vybrána, obnoví stav uzlů v Průzkumník řešení s ohledem na to, zda byly rozbaleny nebo sbaleny při posledním otevření řešení. Zrušením výběru této možnosti můžete zkrátit dobu načítání řešení u velkých řešení.

> [!TIP]
> Pokud tuto možnost zakážete, snadný způsob, jak přejít na aktivní dokument v Průzkumník řešení, je výběrem možnosti **synchronizovat s aktivním dokumentem** na panelu nástrojů **Průzkumník řešení** .
>
> ![Synchronizovat s aktivním dokumentem v Průzkumník řešení](media/sync-active-document.png)

## <a name="open-sdk-style-project-files-with-double-click-or-the-enter-key"></a>Otevřete soubory projektu ve stylu sady SDK dvojitým kliknutím nebo klávesou ENTER.

Pokud je vybrána tato možnost a dvakrát kliknete na uzel projektu ve stylu sady SDK v Průzkumník řešení nebo jej vyberete a potom stisknete klávesu **ENTER**, soubor projektu (například \*soubor. csproj) se otevře jako XML v editoru. Pokud je tato možnost Odstraněná, poklikejte na uzel projektu ve stylu sady SDK v Průzkumník řešení nebo jeho výběr a stisknutí klávesy **ENTER** má vliv na rozbalení nebo sbalení pouze uzlu.

Pokud tuto možnost nemáte zaškrtnuté a chcete upravit soubor projektu ve stylu sady SDK, klikněte pravým tlačítkem myši na uzel projektu v Průzkumník řešení a vyberte **Upravit soubor projektu**. Pro jiné typy projektů je nutné nejprve uvolnit projekt před jeho úpravou v aplikaci Visual Studio.

> [!TIP]
> *Projekt ve stylu sady SDK*nebo [sada SDK projektu](../../msbuild/how-to-use-project-sdk.md)mají novější a efektivnější formát souboru projektu, který byl představen nástrojem MSBuild 15,0. Projekt ve stylu sady SDK obsahuje atribut `Sdk` u prvku `Project`, například `<Project Sdk="Microsoft.NET.Sdk">`. Sada Visual Studio vytvoří projekt ve stylu sady SDK při vytváření nového projektu .NET Core v jedné ze šablon sady Visual Studio, například.

::: moniker-end

## <a name="see-also"></a>Viz také:

- [Dialogové okno Možnosti: projekty a řešení \> umístění](projects-solutions-locations-options.md)
- [Dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Dialogové okno Možnosti, Projekty a řešení, Webové projekty](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
