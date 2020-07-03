---
title: 'Postupy: migrace rozšiřujících projektů do sady Visual Studio 2017 | Microsoft Docs'
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 37f7259c1133ea51e004b5f6b2061427ff71dea0
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905844"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Postupy: migrace rozšiřujících projektů do sady Visual Studio 2017

Tento dokument vysvětluje, jak upgradovat projekty rozšíření na Visual Studio 2017. Kromě popisu, jak aktualizovat soubory projektu, také popisuje, jak upgradovat z manifestu rozšíření verze 2 (VSIX v2) na nový formát manifestu VSIX verze 3 (VSIX V3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Instalace sady Visual Studio 2017 s požadovanými úlohami

Ujistěte se, že vaše instalace zahrnuje následující úlohy:

* Vývoj pro desktopy .NET
* Vývoj rozšíření sady Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Otevřít řešení VSIX v aplikaci Visual Studio 2017

Všechny projekty VSIX budou vyžadovat jednosměrný upgrade hlavní verze na Visual Studio 2017.

Soubor projektu (například **. csproj*) bude aktualizován:

* MinimumVisualStudioVersion – teď je nastavená na 15,0.
* OldToolsVersion (Pokud už existuje) – teď je nastavená na 14,0.

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aktualizace balíčku NuGet Microsoft. VSSDK. BuildTools

> [!Note]
> Pokud vaše řešení neodkazuje na balíček NuGet Microsoft. VSSDK. BuildTools, můžete tento krok přeskočit.

Aby bylo možné sestavit rozšíření v novém formátu VSIX V3 (verze 3), bude nutné vaše řešení sestavit pomocí nových nástrojů pro sestavení VSSDK. Tato akce bude nainstalována se sadou Visual Studio 2017, ale rozšíření VSIX v2 může obsahovat odkaz na starší verzi prostřednictvím NuGet. Pokud ano, budete muset ručně nainstalovat aktualizaci balíčku NuGet Microsoft. VSSDK. BuildTools pro vaše řešení.

Aktualizace odkazů na NuGet na Microsoft. VSSDK. BuildTools:

* Klikněte pravým tlačítkem na řešení a vyberte **Spravovat balíčky NuGet pro řešení**.
* Přejděte na kartu **aktualizace** .
* Vyberte **Microsoft. VSSDK. BuildTools (nejnovější verze)**.
* Stiskněte **aktualizovat**.

![Nástroje pro sestavení VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Provedení změn v manifestu rozšíření VSIX

Chcete-li zajistit, aby instalace aplikace Visual Studio pro uživatele měla všechna sestavení potřebná ke spuštění rozšíření, zadejte všechny požadované součásti nebo balíčky v souboru manifestu rozšíření. Když se uživatel pokusí nainstalovat rozšíření, VSIXInstaller zkontroluje, jestli jsou nainstalované všechny požadované součásti. Pokud chybí nějaké, zobrazí se uživateli výzva k instalaci chybějících součástí v rámci procesu instalace rozšíření.

> [!Note]
> Minimálně všechna rozšíření by měla jako předpoklad určovat komponentu základního editoru sady Visual Studio.

* Upravte soubor manifestu rozšíření (obvykle se nazývá *source. extension. vsixmanifest*).
* Zajistěte `InstallationTarget` , aby zahrnovaly 15,0.
* Přidejte požadavky na požadovanou instalaci (jak je znázorněno v následujícím příkladu).
  * Doporučujeme zadat pouze ID součástí pro požadavky na instalaci.
  * [Pokyny k identifikaci ID součástí](#find-component-ids)najdete v části na konci tohoto dokumentu.

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Možnost: použití návrháře k provádění změn manifestu rozšíření VSIX

Místo toho, abyste přímo upravovali XML manifestu, můžete použít kartu nové **požadavky** v Návrháři manifestu k výběru požadavků a kód XML bude aktualizován za vás.

> [!Note]
> Návrhář manifestu vám umožní vybrat komponenty (ne úlohy nebo balíčky), které jsou nainstalované v aktuální instanci sady Visual Studio. Pokud potřebujete přidat předpoklad pro úlohu, balíček nebo komponentu, která není aktuálně nainstalovaná, upravte XML manifest přímo.

* Otevřete soubor *source. extension. vsixmanifest [Design]* .
* Vyberte kartu **požadované součásti** a stiskněte tlačítko **Nový** .

   ![Návrhář manifestu VSIX](media/vsix-manifest-designer.png)

* Otevře se okno **Přidat nové požadované součásti** .

   ![Přidat požadavky VSIX](media/add-vsix-prerequisite.png)

* Klikněte na rozevírací seznam pro **název** a vyberte požadovaný požadavek.
* V případě potřeby aktualizujte verzi.

   > [!Note]
   > Pole verze se předem vyplní verzí aktuálně nainstalované komponenty a rozsah pokrývá až (ale ne včetně) další hlavní verze součásti.

   ![Přidat požadavky Roslyn](media/add-roslyn-prerequisite.png)

* Stiskněte **OK**.

## <a name="update-debug-settings-for-the-project"></a>Aktualizovat nastavení ladění pro projekt

Pokud chcete ladit rozšíření v experimentální instanci aplikace Visual Studio, ujistěte se, že nastavení projektu pro **Debug**  >  **akci spustit** pro ladění má hodnotu **spustit externí program:** hodnota nastavenou na *devenv.exe* soubor instalace sady Visual Studio 2017.

Může to vypadat takto: *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![spustit externí program](media/start-external-program.png)

> [!Note]
> Akce spustit ladění je obvykle uložena v souboru *. csproj. User* . Tento soubor je obvykle obsažen v souboru *. gitignore* , a proto není obvykle uložen s jinými soubory projektu při potvrzení do správy zdrojových kódů. V takovém případě, pokud jste řešení stáhli ze správy zdrojového kódu, je nejspíš, že projekt nebude mít nastavené žádné hodnoty pro akci spustit. Nové projekty VSIX vytvořené pomocí sady Visual Studio 2017 budou mít vytvořený soubor *. csproj. User* s výchozím nastavením, který odkazuje na aktuální instalační adresář sady Visual Studio. Pokud však migrujete rozšíření VSIX v2, je pravděpodobný, že soubor *. csproj. User* bude obsahovat odkazy na předchozí instalační adresář verze sady Visual Studio. Nastavením hodnoty pro **Debug**  >  **akci spustit** ladění umožníte, aby se při pokusu o ladění rozšíření spouštěla správná experimentální instance sady Visual Studio.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Ověřte, zda se rozšíření správně sestavuje (jako VSIX V3).

* Sestavte projekt VSIX.
* Rozbalte vygenerovaný VSIX.
  * Ve výchozím nastavení je soubor VSIX umístěný uvnitř *bin/Debug* nebo *bin/Release* jako *[YourCustomExtension]. vsix*.
  * Chcete-li snadno zobrazit obsah, přejmenujte soubor *. vsix* na *. zip* .
* Kontrolovat existenci tří souborů:
  * *Přípona. vsixmanifest*
  * *manifest.jsna*
  * *catalog.jsna*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Zkontroluje, jestli jsou nainstalované všechny požadované součásti.

Otestujte úspěšné instalace VSIX na počítači, na kterém jsou nainstalované všechny požadované součásti.

> [!Note]
> Před instalací jakéhokoli rozšíření ukončete všechny instance sady Visual Studio.

Pokus o instalaci rozšíření:

* V aplikaci Visual Studio 2017

![Instalační program VSIX v aplikaci Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Volitelné: Projděte si předchozí verze sady Visual Studio.
  * Ukáže zpětnou kompatibilitu.
  * By měla fungovat pro Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Volitelné: Kontrola verze instalačního programu VSIX nabízí možnost výběru verzí.
  * Zahrnuje předchozí verze sady Visual Studio (pokud jsou nainstalovány).
  * Zahrnuje Visual Studio 2017.

Pokud se Visual Studio nedávno otevřelo, může se zobrazit dialogové okno podobné tomuto:

![běžící procesy vs](media/vs-running-processes.png)

Počkejte, než se procesy ukončí, nebo úlohy ukončete ručně. Procesy můžete najít podle uvedeného názvu nebo pomocí identifikátoru PID uvedeného v závorkách.

> [!Note]
> Tyto procesy nebudou automaticky vypnuty, dokud je spuštěna instance aplikace Visual Studio. Ujistěte se, že jste všechny instance sady Visual Studio vypnuli na počítači, včetně počítačů jiných uživatelů, a potom zkuste pokračovat znovu.

## <a name="check-when-missing-the-required-prerequisites"></a>Zjistit, zda chybějící požadované součásti chybí

* Pokuste se nainstalovat rozšíření na počítači se sadou Visual Studio 2017, který neobsahuje všechny součásti definované v požadavcích (výše).
* Ověřte, že instalace identifikuje chybějící komponentu/s, a vypíše je jako požadavky v VSIXInstaller.
* Poznámka: zvýšení oprávnění se bude vyžadovat, pokud je potřeba nainstalovat všechny požadované součásti s rozšířením.

![VSIXInstaller chybějící požadavek](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Rozhodnutí o součástech

Při vyhledávání závislostí zjistíte, že jedna závislost může mapovat na více komponent. Chcete-li určit závislosti, které byste měli určit jako předpoklady, doporučujeme vám zvolit součást, která má podobnou funkci jako vaše rozšíření, a také zvážit uživatele a typy komponent, které by s největší pravděpodobně nainstalovaly nebo nemusely instalovat. Navrhujeme také sestavení vašich rozšíření tak, aby požadované požadavky splňovaly jenom minimum, které umožní, aby bylo rozšíření spuštěné a další funkce byly neaktivní, pokud některé součásti nejsou zjištěny.

Abychom vám pomohli získat další pokyny, zjistili jsme několik běžných typů rozšíření a jejich doporučené požadavky:

Typ rozšíření | Zobrazovaný název | ID
--- | --- | ---
Editor | Základní editor sady Visual Studio | Microsoft. VisualStudio. Component. CoreEditor
Roslyn | C# a Visual Basic | Microsoft. VisualStudio. Component. Roslyn. LanguageServices
WPF | Jádro úlohy spravované plochy | Microsoft. VisualStudio. Component. ManagedDesktop. Core
Ladicí program | Ladicí program za běhu | Microsoft. VisualStudio. Component. Debugger. JustInTime

## <a name="find-component-ids"></a>Najít ID součástí

Seznam komponent seřazený podle produktu Visual Studio je v rámci [úloh sady Visual studio 2017 a ID komponent](/visualstudio/install/workload-and-component-ids?view=vs-2019). Pro ID požadovaných součástí v manifestu použijte tato ID.

Pokud si nejste jistí, která součást obsahuje konkrétní binární soubor, stáhněte [tabulku mapování binárních souborů Component->](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

V excelovém listu jsou čtyři sloupce: **název komponenty**, **ComponentID**, **verze**a **binární/název souboru**.  Filtry můžete použít k vyhledání a vyhledání konkrétních komponent a binárních souborů.

Pro všechny vaše odkazy nejprve určete, která z nich je v komponentě Core Editor (Microsoft. VisualStudio. Component. CoreEditor).  Minimální je, že vyžaduje, aby byla součást základního editoru zadána jako předpoklad pro všechna rozšíření. Z odkazů, které nejsou v základním editoru, přidejte filtry v části **názvy binárních souborů/souborů** , abyste našli komponenty, které mají kteroukoli z podmnožiny těchto odkazů.

Příklady:

* Máte-li rozšíření ladicího programu a víte, že váš projekt obsahuje odkaz na *VSDebugEng.dll* a *VSDebug.dll*, klikněte na tlačítko Filtr v hlavičce **názvů binárních souborů/souborů** .  Vyhledejte "VSDebugEng.dll" a vyberte *OK*.  Potom znovu klikněte na tlačítko Filtr v záhlaví **binární soubory/soubory** a vyhledejte "VSDebug.dll".  Zaškrtněte políčko **Přidat aktuální výběr k filtrování** a vyberte **OK**.  Nyní se podívejte na **název komponenty** a vyhledejte komponentu, která se nejvíce vztahuje k vašemu typu rozšíření. V tomto příkladu jste zvolili ladicí program za běhu a přidáte ho do svého nástroje vsixmanifest.
* Pokud víte, že projekt pracuje s prvky ladicího programu, můžete vyhledat text "Debugger" v poli hledání filtru a zjistit, jaké komponenty obsahují v názvu ladicí program.

## <a name="specify-a-visual-studio-2017-release"></a>Zadejte verzi sady Visual Studio 2017

Pokud vaše rozšíření vyžaduje konkrétní verzi sady Visual Studio 2017, závisí například na funkci vydané v 15,3, je nutné zadat číslo sestavení do VSIX **InstallationTarget**. Například verze 15,3 má číslo buildu "15.0.26730.3". [Tady](../install/visual-studio-build-numbers-and-release-dates.md)vidíte mapování verzí k sestavování čísel. Použití čísla vydané verze 15,3 nebude fungovat správně.

Pokud vaše rozšíření vyžaduje 15,3 nebo vyšší, deklarujete **verzi InstallationTarget** jako [15.0.26730.3, 16,0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
