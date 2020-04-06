---
title: 'Postup: Migrace projektů rozšiřitelnosti do Visual Studia 2017 | Dokumenty společnosti Microsoft'
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b0cae0261b185ee08400e5f3d25735634663f54a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710984"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Postup: Migrace projektů rozšiřitelnosti do Visual Studia 2017

Tento dokument vysvětluje, jak upgradovat projekty rozšiřitelnosti do Visual Studia 2017. Kromě popisu, jak aktualizovat soubory projektu, popisuje také, jak upgradovat z rozšíření manifestu verze 2 (VSIX v2) na novou verzi 3 VSIX manifest formátu (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Instalace Visual Studia 2017 s požadovanými úlohami

Ujistěte se, že vaše instalace obsahuje následující úlohy:

* Vývoj stolních počítačů .NET
* Vývoj rozšíření sady Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Otevření řešení VSIX v sadě Visual Studio 2017

Všechny projekty VSIX bude vyžadovat hlavní verzi jednosměrný upgrade na Visual Studio 2017.

Soubor projektu (například **.csproj*) bude aktualizován:

* MinimumVisualStudioVersion - nyní nastavena na 15,0
* OldToolsVersion (pokud dříve existuje) - nyní nastavena na 14,0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aktualizace balíčku Microsoft.VSSDK.BuildTools NuGet

> [!Note]
> Pokud vaše řešení neodkazuje na balíček Microsoft.VSSDK.BuildTools NuGet, můžete tento krok přeskočit.

Aby bylo možné vytvořit rozšíření v novém formátu VSIX v3 (verze 3), vaše řešení bude muset být postaveno s novými nástroji pro sestavení VSSDK. To se nainstaluje s Visual Studio 2017, ale vaše rozšíření VSIX v2 může být s odkazem na starší verzi přes NuGet. Pokud ano, budete muset ručně nainstalovat aktualizaci balíčku Microsoft.VSSDK.BuildTools NuGet pro vaše řešení.

Aktualizace odkazů NuGet na Microsoft.VSSDK.BuildTools:

* Klikněte pravým tlačítkem myši na řešení a zvolte **Spravovat balíčky NuGet pro řešení**.
* Přejděte na kartu **Aktualizace.**
* Vyberte **Microsoft.VSSDK.BuildTools (nejnovější verze)**.
* Stiskněte **tlačítko Aktualizovat**.

![Nástroje pro sestavení VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Provádění změn v manifestu rozšíření VSIX

Chcete-li zajistit, aby instalace sady Visual Studio uživatelem obsahuje všechna sestavení potřebná ke spuštění rozšíření, zadejte všechny nezbytné součásti nebo balíčky v souboru manifestu rozšíření. Když se uživatel pokusí nainstalovat rozšíření, VSIXInstaller zkontroluje, zda jsou nainstalovány všechny požadavky. Pokud některé chybí, bude uživatel vyzván k instalaci chybějících součástí jako součást procesu instalace rozšíření.

> [!Note]
> Minimálně všechna rozšíření by měla určit součást základního editoru sady Visual Studio jako předpoklad.

* Upravte soubor manifestu přípony (obvykle nazývaný *source.extension.vsixmanifest).*
* Ujistěte se, že `InstallationTarget` obsahuje 15.0.
* Přidejte požadované požadavky na instalaci (jak je znázorněno v příkladu níže).
  * Doporučujeme zadat pouze ID součásti pro požadavky na instalaci.
  * Pokyny [k identifikaci ID součástí](#find-component-ids)naleznete v části na konci tohoto dokumentu .

Příklad:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Možnost: Pomocí návrháře můžete provést změny v manifestu rozšíření VSIX.

Místo přímé úpravy xml manifestu můžete pomocí nové karty Požadavky v **Návrháři** manifestu vybrat požadavky a xml bude aktualizován za vás.

> [!Note]
> Návrhář manifestu vám umožní pouze vybrat součásti (nikoli úlohy nebo balíčky), které jsou nainstalovány v aktuální instanci sady Visual Studio. Pokud potřebujete přidat předpoklad pro úlohu, balíček nebo součást, která není aktuálně nainstalována, upravte přímo xml manifestu.

* Soubor Open *source.extension.vsixmanifest [Design].*
* Vyberte **kartu Požadavky** a stiskněte **tlačítko Nový.**

   ![Návrhář manifestu VSIX](media/vsix-manifest-designer.png)

* Otevře se okno **Přidat nový požadavek.**

   ![přidat vsix předpoklad](media/add-vsix-prerequisite.png)

* Klikněte na rozbalovací pro **název** a vyberte požadovaný předpoklad.
* V případě potřeby aktualizujte verzi.

   > [!Note]
   > Pole verze bude předem vyplněno verzí aktuálně nainstalované součásti s rozsahem zahrnujícím (ale nevčetně) další hlavní verze součásti.

   ![přidat roslyn předpoklad](media/add-roslyn-prerequisite.png)

* Stiskněte **OK**.

## <a name="update-debug-settings-for-the-project"></a>Aktualizace nastavení ladění projektu

Pokud chcete ladit rozšíření v experimentální instanci sady Visual Studio, **Debug** > ujistěte se, že nastavení projektu pro**akce Ladění Start** má spustit externí **program:** hodnota nastavena na soubor *devenv.exe* instalace sady Visual Studio 2017.

Může vypadat takto: *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![spuštění externího programu](media/start-external-program.png)

> [!Note]
> Akce spuštění ladění je obvykle uložena v souboru *.csproj.user.* Tento soubor je obvykle součástí souboru *.gitignore,* a proto není obvykle uložen s jinými soubory projektu, pokud jsou potvrzeny do správy zdrojového kódu. Jako takové, pokud jste vytáhli vaše řešení čerstvé ze správy zdrojového kódu je pravděpodobné, že projekt bude mít žádné hodnoty nastavené pro spustit akci. Nové projekty VSIX vytvořené pomocí sady Visual Studio 2017 budou mít vytvořený soubor *.csproj.user* s výchozími hodnotami směřujícími na aktuální instalační adresář sady Visual Studio. Pokud však migrujete rozšíření VSIX v2, je pravděpodobné, že soubor *.csproj.user* bude obsahovat odkazy na instalační adresář předchozí verze sady Visual Studio. Nastavení hodnoty **Debug** > **akce** Ladění start umožní správné visual studio experimentální instance ke spuštění při pokusu o ladění rozšíření.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Zkontrolujte, zda se rozšíření staví správně (jako VSIX v3)

* Sestavte projekt VSIX.
* Rozbalte generované VSIX.
  * Ve výchozím nastavení je soubor VSIX v *přihrádce/ladění* nebo *přihrádce/uvolnění* jako *[YourCustomExtension].vsix*.
  * *Přejmenováním .vsix* na *.zip* můžete obsah snadno zobrazit.
* Zkontrolujte existenci tří souborů:
  * *extension.vsixmanifest*
  * *manifest.json*
  * *katalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Kontrola, kdy jsou nainstalovány všechny požadované požadavky

Otestujte, že VSIX nainstaluje úspěšně na počítači se všemi nainstalovanými požadovanými požadavky.

> [!Note]
> Před instalací jakékoli rozšíření vypněte všechny instance sady Visual Studio.

Pokus o instalaci rozšíření:

* Ve Visual Studiu 2017

![Instalační program VSIX v sadě Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Volitelné: Zkontrolujte předchozí verze sady Visual Studio.
  * Dokazuje zpětnou kompatibilitu.
  * By měl fungovat pro Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Volitelné: Zkontrolujte, zda VSIX Installer Version Checker nabízí výběr verzí.
  * Zahrnuje předchozí verze sady Visual Studio (pokud je nainstalován).
  * Zahrnuje Visual Studio 2017.

Pokud visual studio bylo nedávno otevřeno, může se zobrazit dialogové okno, jako je tento:

![vs spuštěné procesy](media/vs-running-processes.png)

Počkejte na ukončení procesů nebo ruční ukončení úloh. Procesy můžete najít podle uvedeného názvu nebo pomocí pid uvedeného v závorce.

> [!Note]
> Tyto procesy se automaticky neukončí, pokud je spuštěna instance sady Visual Studio. Ujistěte se, že jste vypnuli všechny instance sady Visual Studio v počítači – včetně těch od jiných uživatelů, a pak pokračujte v opakování.

## <a name="check-when-missing-the-required-prerequisites"></a>Kontrola, pokud chybí požadované požadavky

* Pokus o instalaci rozšíření v počítači s Visual Studio 2017, který neobsahuje všechny součásti definované v požadavky (výše).
* Zkontrolujte, zda instalace identifikuje chybějící součásti a uvádí je jako předpoklad v VSIXInstaller.
* Poznámka: Pokud je třeba s rozšířením nainstalovat nějaké požadavky, bude vyžadována nadmořská výška.

![vsixinstaller chybí předpoklad](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Rozhodnout o součástech

Při vyhlížení závislostí zjistíte, že jedna závislost může být mapována na více součástí. Chcete-li určit, které závislosti byste měli zadat jako předpoklad, doporučujeme zvolit komponentu, která má podobnou funkci jako vaše rozšíření, a také zvážit uživatele a jaký typ součástí by s největší pravděpodobností nainstalovali nebo by jim instalace nevadila. Doporučujeme také vytvořit rozšíření tak, aby požadované požadavky splňovaly pouze minimum, které umožní spuštění rozšíření, a pro další funkce je mají být spící, pokud některé součásti nejsou detekovány.

Abychom vám poskytli další pokyny, identifikovali jsme několik běžných typů rozšíření a jejich navrhované předpoklady:

Typ rozšíření | Zobrazovaný název | ID
--- | --- | ---
Editor | Základní editor Visual Studia | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# a Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Jádro spravovaného pracovního vytížení plochy | Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core
Ladicí program | Ladicí program Just-In-Time | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Hledání ID součástí

Seznam součástí seřazených podle produktu Visual Studio je na [id úloh y Visual Studia 2017 a ID komponent](/visualstudio/install/workload-and-component-ids?view=vs-2019). Použijte tato ID komponent y pro vaše předpokladID v manifestu.

Pokud si nejste jisti, která komponenta obsahuje konkrétní binární soubor, stáhněte si [tabulku mapování Binární součást ->](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

V listu aplikace Excel jsou čtyři sloupce: **Název součásti**, **ComponentId**, **Verze**a **Binární / Názvy souborů**.  Pomocí filtrů můžete vyhledávat a vyhledávat konkrétní součásti a binární soubory.

Pro všechny odkazy nejprve určete, které z nich jsou v součásti základního editoru (Microsoft.VisualStudio.Component.CoreEditor).  Minimálně požadujeme, aby součást základního editoru byla specifikována jako předpoklad pro všechna rozšíření. Z odkazů, které jsou ponechány, které nejsou v editoru jádra, přidejte filtry v části **Názvy binárních souborů / Názvy souborů,** abyste našli součásti, které mají některou z podmnožiny těchto odkazů.

Příklady:

* Pokud máte rozšíření ladicího programu a víte, že váš projekt obsahuje odkaz na *VSDebugEng.dll* a *VSDebug.dll*, klikněte na tlačítko filtru v záhlaví **Binární soubory / Názvy souborů.**  Vyhledejte "VSDebugEng.dll" a vyberte *OK*.  Dále klikněte na tlačítko filtru v záhlaví **Binární soubory / Názvy souborů** znovu a vyhledejte "VSDebug.dll".  Zaškrtněte políčko **Přidat aktuální výběr k filtrování** a vyberte **OK**.  Nyní projděte **název komponenty** a vyhledejte komponentu, která nejvíce souvisí s typem rozšíření. V tomto příkladu byste zvolili ladicí program Just-In-Time a přidejte jej do vsixmanifestu.
* Pokud víte, že váš projekt se zabývá ladicí prvky, můžete hledat na "ladicí program" ve vyhledávacím poli filtru zobrazíte, jaké součásti obsahují ladicí program v jeho názvu.

## <a name="specify-a-visual-studio-2017-release"></a>Určení verze Visual Studia 2017

Pokud vaše rozšíření vyžaduje konkrétní verzi Sady Visual Studio 2017, například závisí na funkci vydané v 15.3, je nutné zadat číslo sestavení v VSIX **InstallationTarget**. Například verze 15.3 má číslo sestavení '15.0.26730.3'. Můžete vidět mapování verzí k sestavení čísla [zde](../install/visual-studio-build-numbers-and-release-dates.md). Použití čísla vydání '15.3' nebude fungovat správně.

Pokud vaše rozšíření vyžaduje 15.3 nebo vyšší, deklarujete **verzi InstallationTarget** jako [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
