---
title: Jak zpětná rozšíření
ms.date: 06/25/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: gregvanl
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 826089f1018bc6156cd49bab3afb19e7bb34a47d
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750729"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Postupy: provést rozšíření kompatibilní s Visual Studio 2017 a Visual Studio 2015

Tento dokument vysvětluje, jak vytvořit projekty rozšiřitelnosti přenosu mezi Visual Studio 2015 a Visual Studio 2017. Po dokončení tohoto upgradu, projekt bude moct otevírat, sestavení, nainstalovat a spustit v sadě Visual Studio 2015 a Visual Studio 2017. Jako odkaz, nějaké rozšíření, které se dají zpátečního převodu mezi Visual Studio 2015 a Visual Studio 2017 najdete v [ukázky rozšiřitelnosti VS SDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Pokud chcete pouze na sestavení v sadě Visual Studio 2017, ale má výstup VSIX ke spuštění v sadě Visual Studio 2015 a Visual Studio 2017, pak se podívejte [dokumentu migrace rozšíření](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

> [!NOTE]
> Z důvodu změn v sadě Visual Studio mezi verzemi nefungují některé věci, které fungovaly v jedné verzi v jiném. Zkontrolujte, že se pokoušíte získat přístup k funkce jsou dostupné v obou verzích nebo rozšíření bude mít neočekávané výsledky.

Tady je přehled kroků, které dokončíte v tomto dokumentu ho zpátečního převodu VSIX:

1. Importujte správné balíčky NuGet.
2. Aktualizujte Manifest rozšíření:
    * Cíl instalace
    * Požadavky
3. Aktualizace souboru CSProj:
    * Aktualizace `<MinimumVisualStudioVersion>`.
    * Přidat `<VsixType>` vlastnost.
    * Přidat vlastnost ladění `($DevEnvDir)` 3 místech.
    * Přidání podmínek pro import nástroje sestavení a cíle.

4. Sestavení a testování

## <a name="environment-setup"></a>Nastavení prostředí

Tento dokument předpokládá, že máte v počítači byly nainstalovány následující:

* Visual Studio 2015 se sadou VS SDK nainstalovaná
* Visual Studio 2017 s nainstalovaná rozšíření úloha

## <a name="recommended-approach"></a>Doporučený postup

Důrazně doporučujeme spustit tento upgrade pomocí sady Visual Studio 2015, místo sady Visual Studio 2017. Hlavní výhodou vývoje v sadě Visual Studio 2015 je zajistit odkaz sestavení, která nejsou k dispozici v sadě Visual Studio 2015. Pokud tak učiníte vývoje v sadě Visual Studio 2017, existuje riziko, že může dojít ke vzniku závislost na sestavení, která existuje pouze v sadě Visual Studio 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Ujistěte se, že neexistuje žádný odkaz na project.json

Dále v tomto dokumentu jsme se vloží příkazy podmíněné importu v k vaší **.csproj* souboru.  To nebude fungovat, pokud vaše odkazy na NuGet se ukládají v *project.json*. V důsledku toho doporučujeme přesunout všechny odkazy NuGet *souboru packages.config* souboru.
Pokud váš projekt obsahuje *project.json* souboru:

* Poznamenejte si odkazy v *project.json*.
* Z **Průzkumníka řešení**, odstranit *project.json* soubor z projektu. Tím se odstraní *project.json* souboru a odebere z projektu.
* Přidáte že odkazy na NuGet zpátky do projektu:
    * Klikněte pravým tlačítkem na **řešení** a zvolte **spravovat balíčky NuGet pro řešení**.
    * Visual Studio automaticky vytvoří *souboru packages.config* souboru za vás.

> [!NOTE]
> Pokud váš projekt obsahoval EnvDTE balíčky, může potřebovat přidat kliknutím pravým tlačítkem na **odkazy** výběr **přidat odkaz na** a přidejte příslušný odkaz.  Pomocí balíčků NuGet může vytvořit chyby při pokusu o svůj projekt sestavit.

## <a name="add-appropriate-build-tools"></a>Přidat nástroje pro sestavení

Opravdu potřebujeme přidat nástroje pro vytváření, které vám umožní nám umožňuje vytvářet a ladit odpovídajícím způsobem. Společnost Microsoft vytvořila sestavení pro tento volané Microsoft.VisualStudio.Sdk.BuildTasks.

K vytvoření a nasazení VSIXv3 v sadě Visual Studio 2015 a 2017, budete potřebovat následující balíčky NuGet:

Version | Nástroje pro sestavení
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

Postup:

* Do projektu přidejte balíček NuGet Microsoft.VisualStudio.Sdk.BuildTasks.14.0.
* Pokud projekt neobsahuje Microsoft.VSSDK.BuildTools, přidejte ji.
* Ujistěte se verze balíčku Microsoft.VSSDK.BuildTools je 15.x nebo vyšší.

## <a name="update-extension-manifest"></a>Aktualizujte manifest rozšíření

### <a name="1-installation-targets"></a>1. Instalace cíle

Je potřeba zjistit, jaké verze zacílené pro vytváření rozšíření VSIX sady Visual Studio.  Tyto odkazy jsou obvykle, verze 14.0 (Visual Studio 2015) nebo verze 15.0 (Visual Studio 2017).  V našem případě chceme sestavení VSIX, který bude instalovat rozšíření pro obě, takže potřebujeme mít obě verze.  Pokud chcete sestavit a nainstalovat do verze starší než 14.0 VSIX, to můžete udělat tak, že nastavíte číslo starší verze; verze 10.0 a starší se však již nejsou podporovány.

* Otevřít *source.extension.vsixmanifest* souboru v sadě Visual Studio.
* Otevřít **cíle instalace** kartu.
* Změnit **rozsah verzí** k [14,0, 16,0).  ' [' Říká sady Visual Studio pro verze 14,0 a všechny minulé ho.  Tím ')' říká sady Visual Studio pro všechny verze 15.0 až, ale bez zahrnutí verze 16.0.
* Uložte všechny změny a zavřete všechny instance sady Visual Studio.

![Obrázek cíle instalace](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Požadavky pro přidání *extension.vsixmanifest* souboru

Požadavky jsou novou funkcí sady Visual Studio 2017.  V tomto případě potřebujeme základním editoru sady Visual Studio jako předpoklad. Protože návrháře aplikace Visual Studio 2015 VSIX nezpracovává nové `Prerequisites` části, bude nutné upravit tuto část ručně v kódu XML.  Alternativně můžete otevřít Visual Studio 2017 a použijte aktualizované manifest designer k vložení požadavky.

Chcete-li to provést ručně:

* Přejděte do adresáře projektu v Průzkumníku souborů.
* Otevřít *extension.vsixmanifest* souboru v textovém editoru.
* Přidejte následující značku:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Soubor uložte a zavřete.

> [!NOTE]
> Pokud budete chtít dosáhnout pomocí návrháře VSIX v sadě Visual Studio 2017, musíte ručně upravit požadované verze zajistit, že je kompatibilní se všemi verzemi sady Visual Studio 2017.  Je to proto, že návrhář vloží minimální verze jako aktuální verze sady Visual Studio (například 15.0.26208.0).  Ale protože jiní uživatelé mohou mít starší verzi, můžete ručně upravit na 15.0.

Váš soubor manifestu v tomto okamžiku by měl vypadat přibližně takto:

![Příklad požadavky](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Úprava souboru projektu (myproject.csproj)

Důrazně doporučujeme mít odkaz na upravenou .csproj otevřít v průběhu tohoto kroku.  Můžete najít několik příkladů [tady](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  Vyberte libovolnou ukázku rozšiřitelnosti, vyhledejte *.csproj* pro odkaz na soubor a proveďte následující kroky:

* Přejděte do adresáře projektu v **Průzkumníka souborů**.
* Otevřít *myproject.csproj* souboru v textovém editoru.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Aktualizace MinimumVisualStudioVersion

* Nastavte minimální sady visual studio verzi `$(VisualStudioVersion)` a přidejte podmíněný příkaz pro něj.  Pokud ještě neexistují, přidejte tyto značky.  Ujistěte se, že značky jsou nastavené, jak je uvedeno níže:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Přidáte vlastnost VsixType.

* Přidejte následující značku `<VsixType>v3</VsixType>` do vlastností skupiny.

> [!NOTE]
> Doporučuje se přidat níže `<OutputType></OutputType>` značky.

### <a name="3-add-the-debugging-properties"></a>3. Přidání vlastnosti ladění

* Přidejte následující vlastnosti skupiny:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Odstranit všechny instance v následujícím příkladu kódu z *.csproj* soubor a všechny *. csproj.user* soubory:

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Přidání podmínky do importy nástroje sestavení

* Přidávat další podmíněné příkazy `<import>` značky, které mají Microsoft.VSSDK.BuildTools odkaz.  Vložit `'$(VisualStudioVersion)' != '14.0' And` do přední části příkaz podmínky.  Tyto příkazy se zobrazí v záhlaví a zápatí souboru csproj.

Příklad:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Přidávat další podmíněné příkazy `<import>` značky, které mají Microsoft.VisualStudio.Sdk.BuildTasks.14.0. Vložit `'$(VisualStudioVersion)' == '14.0' And` do přední části příkaz podmínky. Tyto příkazy se zobrazí v záhlaví a zápatí souboru csproj.

Příklad:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Přidávat další podmíněné příkazy `<Error>` značky, které mají Microsoft.VSSDK.BuildTools odkaz.  To provést vložením `'$(VisualStudioVersion)' != '14.0' And` do přední části příkaz podmínky. Tyto příkazy se zobrazí v zápatí souboru csproj.

Příklad:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Přidávat další podmíněné příkazy `<Error>` značky, které mají Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  Vložit `'$(VisualStudioVersion)' == '14.0' And` do přední části příkaz podmínky. Tyto příkazy se zobrazí v zápatí souboru csproj.

Příklad:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Uložte soubor csproj a zavřete ho.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Testování nainstaluje rozšíření v sadě Visual Studio 2015 a Visual Studio 2017

V tomto okamžiku by měl být projektu připravení sestavit VSIXv3, který můžete nainstalovat na Visual Studio 2015 a Visual Studio 2017.

* Otevřete svůj projekt v sadě Visual Studio 2015.
* Sestavte projekt a potvrďte ve výstupu, který VSIX se sestaví správně.
* Přejděte do adresáře projektu.
* Otevřít *\bin\Debug* složky.
* Poklikejte na soubor VSIX a instalace rozšíření v sadě Visual Studio 2015 a Visual Studio 2017.
* Ujistěte se, že vidíte rozšíření v **nástroje** > **rozšíření a aktualizace** v **nainstalováno** oddílu.
* Pokus o spuštění/použití rozšíření ke kontrole, že funguje.

![Najít rozšíření VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> Pokud váš projekt přestane reagovat s touto zprávou **otevírání souboru**vynutit ukončení sady Visual Studio, přejděte do adresáře projektu, zobrazit skryté složky a odstranit *.vs* složky.