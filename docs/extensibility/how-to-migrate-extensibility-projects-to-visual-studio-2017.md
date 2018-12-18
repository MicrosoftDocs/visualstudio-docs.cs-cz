---
title: 'Postupy: migrace projektů rozšíření do sady Visual Studio 2017 | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 195d63e5ddb8b8536c1d0c1c4197270f5b3aa508
ms.sourcegitcommit: 331dbb12e11fcd7f5d15fab05f3c861e48126e43
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51826814"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Postupy: migrace projektů rozšíření do sady Visual Studio 2017

Tento dokument vysvětluje, jak upgradovat projekty rozšiřitelnosti sady Visual Studio 2017. Kromě popisující, jak aktualizovat soubory projektu, je také popisuje, jak upgradovat z verze manifestu rozšíření 2 (VSIX v2) na novou verzi 3 formát manifestu VSIX (VSIX v. 3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Instalace sady Visual Studio 2017 pomocí požadované úlohy

Ujistěte se, že vaše instalace zahrnuje následující úlohy:

* Vývoj desktopových aplikací .NET
* Vývoj rozšíření sady Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Otevřete řešení VSIX v sadě Visual Studio 2017

Všechny projekty VSIX se vyžadují jednosměrnou aktualizaci hlavní verze Visual Studio 2017.

Soubor projektu (například **.csproj*) bude aktualizovat:

* MinimumVisualStudioVersion – je nyní nastaveno na 15.0
* OldToolsVersion (Pokud již existuje) – nastaví na 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aktualizovat balíček Microsoft.VSSDK.BuildTools NuGet

>**Poznámka:** Pokud vaše řešení neobsahuje odkaz na balíček Microsoft.VSSDK.BuildTools NuGet, můžete tento krok přeskočit.

Aby bylo možné sestavit vaše rozšíření ve VSIX v. 3 nové formát (verze 3), vaše řešení se musela být vytvořená s novou VSSDK Build Tools. Tím se nainstaluje se sadou Visual Studio 2017, ale vaše rozšíření VSIX v2 může uchovávající odkaz na starší verzi prostřednictvím balíčku NuGet. Pokud ano, musíte ručně nainstalovat aktualizaci balíčku Microsoft.VSSDK.BuildTools NuGet pro vaše řešení.

Chcete-li aktualizovat odkazy NuGet Microsoft.VSSDK.BuildTools:

* Klikněte pravým tlačítkem na řešení a zvolte **spravovat balíčky NuGet pro řešení**.
* Přejděte **aktualizace** kartu.
* Vyberte **Microsoft.VSSDK.BuildTools (nejnovější verze)**.
* Stisknutím klávesy **aktualizace**.

![Nástroje VSSDK sestavení](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Proveďte změny v manifestu rozšíření VSIX

Pokud chcete mít jistotu, že uživatele instalace sady Visual Studio obsahuje všechna sestavení, které jsou potřebné ke spuštění rozšíření, zadejte všechny požadované součásti nebo balíčky v souboru manifestu rozšíření. Když se uživatel pokusí nainstalovat rozšíření, VSIXInstaller zkontroluje, pokud jsou nainstalované všechny požadované součásti. Pokud chybí některé, uživatel se vyzve k instalaci chybějících součástí jako součást procesu instalace rozšíření.

>**Poznámka:** minimálně všechna rozšíření určit základní součást editoru sady Visual Studio jako předpoklad.

* Upravit soubor manifestu rozšíření (obvykle nazvanou *source.extension.vsixmanifest*).
* Zajištění `InstallationTarget` zahrnuje 15.0.
* Přidáte požadavky pro instalaci požadované (jak je znázorněno v následujícím příkladu).
  * Doporučujeme, abyste že zadáte jenom ID komponenty pro požadavky na instalaci.
  * V části na konci tohoto dokumentu [pokyny k identifikaci ID součástí](#find-component-ids).

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Možnost: Použití návrháře provádět změny v manifestu rozšíření VSIX

Místo Přímá úprava manifestu XML, můžete použít novou **požadavky** kartě v Návrháři manifestu vyberte požadavky a XML aktualizují za vás.

>**Poznámka:** Manifest Designer pouze umožňuje vybrat součásti (ne úloh nebo balíčky), které jsou nainstalovány na aktuální instanci aplikace Visual Studio. Pokud je potřeba přidat předpokladem pro úlohy, balíček nebo komponenty, která není nainstalována, upravte přímo XML manifestu.

* Otevřít *source.extension.vsixmanifest [Design]* souboru.
* Vyberte **požadavky** kartu a stiskněte klávesu **nový** tlačítko.

  ![Návrhář manifestu VSIX](media/vsix-manifest-designer.png)

* **Přidejte nové požadované** otevře se okno.

  ![přidání požadovaných součástí souboru vsix](media/add-vsix-prerequisite.png)

* Klikněte na rozevírací seznam pro **název** a vyberte požadovaný kontrolu požadovaných součástí.
* Aktualizace verze, pokud je to nutné.

  >Poznámka: Pole verze budou předem vyplněná verzi aktuálně nainstalované komponenty, rozsah pokrývání uzlů až (ale bez zahrnutí) další hlavní verze komponenty.

  ![přidání požadovaných součástí roslyn](media/add-roslyn-prerequisite.png)

* Stisknutím klávesy **OK**.

## <a name="update-debug-settings-for-the-project"></a>Aktualizovat nastavení ladění pro projekt

Pokud chcete ladit vaše rozšíření v experimentální instanci sady Visual Studio, ujistěte se, že nastavení projektu pro **ladění** > **zahájení** má **spustit externí program:** nastavenou *devenv.exe* souboru instalace sady Visual Studio 2017.

To může vypadat: *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![spustit externí program](media/start-external-program.png)

>**Poznámka:** ladit spouštěcí akce je obvykle uložen ve *. csproj.user* souboru. Tento soubor je obvykle součástí *.gitignore* souboru a proto se neuloží, obvykle s jinými soubory projektu při potvrzené do správy zdrojového kódu. V důsledku toho pokud vaše řešení jste dali čerstvé ze správy zdrojového kódu je pravděpodobné, že projekt bude mít žádné hodnoty nastavené pro spouštěcí akci. Nové projekty VSIX vytvořené pomocí sady Visual Studio 2017 budou mít *. csproj.user* soubor vytvořený s výchozím nastavením odkazující na aktuální adresář instalace sady Visual Studio. Nicméně pokud provádíte migraci v2 rozšíření VSIX, je pravděpodobné, který *. csproj.user* soubor bude obsahovat odkazy na předchozí verze sady Visual Studio Instalační adresář. Nastavením této hodnoty pro **ladění** > **zahájení** vám umožní správné experimentální instanci sady Visual Studio ke spuštění při pokusu o ladění rozšíření.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Zkontrolujte, že rozšíření je sestavena správně (podle VSIX v. 3)

* Vytvoření projektu VSIX.
* Rozbalte generovaného souboru VSIX.
  * Ve výchozím nastavení, soubor VSIX umístěným uvnitř *bin/Debug* nebo *bin/Release* jako *[YourCustomExtension] VSIX*.
  * Přejmenovat *VSIX* k *ZIP* snadno zobrazit obsah.
* Kontrola existence tři soubory:
  * *Extension.vsixmanifest*
  * *manifest.JSON*
  * *CATALOG.JSON*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Zaškrtněte, pokud jsou nainstalované všechny požadované součásti

Test, které VSIX nainstaluje úspěšně na počítači nainstalované všechny požadované součásti.

>**Poznámka:** před instalací všechna rozšíření, ukončete všechny instance sady Visual Studio.

Pokus o instalaci rozšíření:

* V sadě Visual Studio 2017

![Instalátor VSIX v sadě Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Volitelné: Zkontrolujte v předchozích verzích sady Visual Studio.
  * Ukáže zpětné kompatibility.
  * By mělo fungovat pro Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Volitelné: Zkontrolujte, že kontrola verze instalačního programu VSIX nabízí široký výběr verze.
  * Zahrnuje předchozí verze sady Visual Studio (Pokud je nainstalovaná).
  * Zahrnuje Visual Studio 2017.

Pokud byl naposledy otevřen sady Visual Studio, může se zobrazit dialogové okno takto:

![VS spuštěných procesů](media/vs-running-processes.png)

Počkejte procesy, které chcete vypnout, nebo ručně ukončení úlohy. Procesy, které najdete pomocí uvedených názvu nebo s identifikátorem PID uvedený v závorkách.

>**Poznámka:** tyto procesy nebudou automaticky během vypnutý je spuštěna instance sady Visual Studio. Ujistěte se, že jste se vypnout všechny instance sady Visual Studio na počítači – včetně těch, které od jiných uživatelů, a potom pokoušet.

## <a name="check-when-missing-the-required-prerequisites"></a>Zaškrtněte, pokud chybí požadované součásti

* Pokuste se nainstalovat rozšíření na počítač s Visual Studio 2017 obsahuje tento nemá není všechny součásti, které jsou definované v rámci požadavků (viz výše).
* Zkontrolujte, zda instalace identifikuje chybějící součásti/s a uvádí jako předpoklad VSIXInstaller.
* Poznámka: Ke zvýšení úrovně oprávnění se bude vyžadovat, pokud všechny požadované součásti nutné k instalaci s příponou.

![Chybí požadavek vsixinstaller](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Při rozhodování o součásti

Při hledání závislostí, zjistíte, že jednu závislost namapovat na několik komponent. K určení závislostí, které je třeba zadat jako předpoklad, doporučujeme, abyste zvolili komponenty, která má funkci podobnou vaše rozšíření a také zvážit uživatelům a jaký druh komponenty by pravděpodobně nainstalovali nebo nebude vadit instalace. Doporučujeme také vytváření rozšíření způsobem, kde splňují nezbytné požadavky jenom minimální, které vám umožní rozšíření ke spuštění a další funkce, aby byly neaktivní, pokud některé součásti nejsou zjištěny.

Chcete-li poskytnout další pokyny, jsme identifikovali několik běžných typů rozšíření a jejich doporučené požadavky:

Typ rozšíření | Zobrazovaný název | ID
--- | --- | ---
Editor | Základním editoru sady Visual Studio  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# a Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Základní spravovaný úloze vývoje desktopových aplikací | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Ladicí program | Just-In-Time debugger | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Najít ID komponenty

Seznam součástí, které jsou seřazené podle produktu Visual Studio je na [ID pracovního vytížení a komponenta Visual Studio 2017](https://aka.ms/vs2017componentIDs). Pomocí těchto součástí ID pro ID vašich požadavků v manifestu.

Pokud si nejste jisti, která komponenta obsahuje konkrétní binární soubor, stáhněte si [komponenty -> binární mapování tabulky](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Existují čtyři sloupce v Excelovém listu: **název komponenty**, **ComponentId**, **verze**, a **binární / názvy souborů**.  Filtry můžete použít k vyhledání a najít konkrétní součásti a binární soubory.

Pro všechny odkazy nejprve určete, které jsou v základní součást editoru (Microsoft.VisualStudio.Component.CoreEditor).  Minimálně požadujeme, aby základní součást editoru zadat jako předpoklad pro všechna rozšíření. Odkazy, které zůstávají, které nejsou v základním editoru, přidejte filtry **binární soubory / názvy souborů** vyhledejte komponenty, které mají některý z podmnožinu těchto odkazů.

Příklady:

* Pokud máte rozšíření ladicího programu a vědět, že váš projekt obsahuje odkaz na *VSDebugEng.dll* a *VSDebug.dll*, klikněte na tlačítko filtru v **binární soubory a názvy souborů**záhlaví.  Vyhledejte "VSDebugEng.dll" a vyberte *OK*.  Dále klikněte na tlačítko filtru v **binární soubory a názvy souborů** záhlaví znovu a vyhledejte položku "VSDebug.dll".  Zaškrtněte políčko **přidat aktuální výběr do filtru** a vyberte **OK**.  Nyní si projít **název komponenty** najít komponentu, která je nejvhodnější související typ rozšíření. V tomto příkladu byste zvolili Just-In-Time ladicího programu a přidejte ji do vašeho vsixmanifest.
* Pokud víte, že váš projekt se zabývá prvky ladicího programu, můžete hledat "ladicí program" do vyhledávacího pole filtrovat zjistit, jaké součásti obsahují ladicí program v názvu.

## <a name="specify-a-visual-studio-2017-release"></a>Zadejte verzi sady Visual Studio 2017

Pokud rozšíření vyžaduje určitou verzi sady Visual Studio 2017, například to závisí na nová funkce od verze 15.3, je nutné zadat číslo sestavení do VSIX **InstallationTarget**. Například verze 15.3 má sestavení počet "15.0.26730.3". Zobrazí se mapování verzí čísla sestavení [tady](../install/visual-studio-build-numbers-and-release-dates.md). Použití "15.3" číslo verze nebude fungovat správně.

Pokud rozšíření vyžaduje 15.3 nebo novější, by deklarovat **InstallationTarget verze** jako [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
