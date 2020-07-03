---
title: Postup převodu rozšíření
ms.date: 06/25/2017
ms.topic: how-to
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: madsk
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: ff2865080b7d36f1a7c3b8a7680d867b92ec9c08
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905783"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-20192017-and-visual-studio-2015"></a>Postupy: zajištění kompatibility rozšíření se sadou Visual Studio 2019/2017 a sadou Visual Studio 2015

Tento dokument vysvětluje, jak zajistit, aby se projekty rozšiřitelnosti mezi Visual Studio 2015 a Visual Studio 2019 nebo Visual Studio 2017. Po dokončení tohoto upgradu bude projekt moci otevřít, sestavit, nainstalovat a spustit jak v rámci sady Visual Studio 2015, tak v systému Visual Studio 2019 nebo 2017. V rámci reference se můžou některá rozšíření, která se můžou odkázat mezi Visual Studio 2015 a Visual Studio 2019 nebo 2017, najít v [ukázkách rozšiřitelnosti sady vs SDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Pokud máte v úmyslu pouze sestavit v aplikaci Visual Studio 2019/2017, ale chcete, aby výstupní VSIX běželo jak v rámci sady Visual Studio 2015, tak i v aplikaci Visual Studio 2019/2017, přečtěte si [dokument migrace rozšíření](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

> [!NOTE]
> V důsledku změn v aplikaci Visual Studio mezi verzemi některé věci, které pracovaly v jedné verzi, nefungují v jiné. Ujistěte se, že funkce, ke kterým se snažíte získat přístup, jsou k dispozici v obou verzích nebo rozšíření budou mít neočekávané výsledky.

Tady je přehled kroků, které v tomto dokumentu dokončíte k tomu, abyste se mohli zakládat na VSIX cestu:

1. Importujte správné balíčky NuGet.
2. Aktualizovat manifest rozšíření:
    * Cíl instalace
    * Požadavky
3. Aktualizovat CSProj:
    * Aktualizace `<MinimumVisualStudioVersion>` .
    * Přidejte `<VsixType>` vlastnost.
    * Přidejte vlastnost ladění `($DevEnvDir)` 3 časy.
    * Přidejte podmínky pro import nástrojů sestavení a cílů.

4. Sestavení a testování

## <a name="environment-setup"></a>Nastavení prostředí

V tomto dokumentu se předpokládá, že máte na svém počítači nainstalovanou následující:

* Sada Visual Studio 2015 s nainstalovanou sadou VS SDK
* Visual Studio 2019 nebo 2017 s nainstalovanou úlohou rozšíření

## <a name="recommended-approach"></a>Doporučený postup

Důrazně doporučujeme tento upgrade spustit pomocí sady Visual Studio 2015 místo sady Visual Studio 2019 nebo 2017. Hlavní výhodou vývoje v aplikaci Visual Studio 2015 je zajistit, aby neodkazovala na sestavení, která nejsou k dispozici v aplikaci Visual Studio 2015. Pokud vyvíjíte v aplikaci Visual Studio 2019 nebo 2017, existuje riziko, že můžete zavést závislost na sestavení, které existuje pouze v aplikaci Visual Studio 2019 nebo 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Zajistěte, aby neexistovaly žádné odkazy na project.js

Později v tomto dokumentu vložíme podmíněné příkazy import do souboru **. csproj* . Tato činnost nebude fungovat, pokud jsou odkazy na NuGet uložené v *project.js*. Proto doporučujeme přesunout všechny odkazy NuGet na soubor *packages.config* .
Pokud projekt obsahuje *project.jsv* souboru:

* Poznamenejte si odkazy v *project.jsna*.
* Z **Průzkumník řešení**odstraňte *project.jsv* souboru z projektu. Tím se odstraní *project.jsv* souboru a odebere se z projektu.
* Přidejte do projektu odkazy NuGet zpátky:
  * Klikněte pravým tlačítkem na **řešení** a vyberte **Spravovat balíčky NuGet pro řešení**.
  * Visual Studio automaticky vytvoří soubor *packages.config* .

> [!NOTE]
> Pokud váš projekt obsahuje balíčky EnvDTE, může být nutné přidat kliknutím pravým tlačítkem na **odkazy** vybrat **Přidat odkaz** a přidat příslušný odkaz. Použití balíčků NuGet může při pokusu o sestavení projektu vytvořit chyby.

## <a name="add-appropriate-build-tools"></a>Přidat vhodné nástroje sestavení

Musíme přidat nástroje pro sestavení, které nám umožní sestavení a ladění odpovídajícím způsobem. Společnost Microsoft vytvořila sestavení pro tento název s názvem Microsoft. VisualStudio. SDK. BuildTasks.

K sestavení a nasazení nového vsixv3 v rámci sady Visual Studio 2015 a 2019/2017 budete potřebovat následující balíčky NuGet:

Verze | Sestavené nástroje
--- | ---
Visual Studio 2015 | Microsoft. VisualStudio. SDK. BuildTasks. 14.0
Visual Studio 2019 nebo 2017 | Microsoft. VSSDK. BuildTool

Postupujte následovně:

* Přidejte do projektu balíček NuGet Microsoft. VisualStudio. SDK. BuildTasks. 14.0.
* Pokud projekt neobsahuje Microsoft. VSSDK. BuildTools, přidejte ho.
* Ujistěte se, že verze Microsoft. VSSDK. BuildTools je 15. x nebo vyšší.

## <a name="update-extension-manifest"></a>Aktualizovat manifest rozšíření

### <a name="1-installation-targets"></a>1. cíle instalace

Musíme aplikaci Visual Studio sdělit, které verze se mají cílit na sestavení VSIX. Obvykle jsou tyto odkazy buď na verzi 14,0 (Visual Studio 2015), verze 15,0 (Visual Studio 2017) nebo verze 16,0 (Visual Studio 2019). V našem případě chceme vytvořit VSIX, který bude instalovat rozšíření pro obě, takže musíme cílit na obě verze. Pokud chcete, aby váš VSIX sestavil a instaloval ve verzích starších než 14,0, můžete to udělat nastavením dřívější číslo verze. verze 10,0 a starší však již nejsou podporovány.

* Otevřete soubor *source. extension. vsixmanifest* v aplikaci Visual Studio.
* Otevřete kartu **cíle instalace** .
* Změňte **rozsah verzí** na [14,0, 17,0). ' [' Oznamuje aplikaci Visual Studio, aby zahrnovala 14,0 a všechny verze v minulosti. ")" Oznamuje aplikaci Visual Studio, aby zahrnovala všechny verze až do, ale ne včetně verze 17,0.
* Uložte všechny změny a zavřete všechny instance aplikace Visual Studio.

![Obrázek cílů instalace](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. přidání požadovaných součástí do souboru *extension. vsixmanifest*

Jako požadavek potřebujeme základní editor sady Visual Studio. Otevřete Visual Studio a pomocí aktualizovaného návrháře manifestu vložte požadavky.

Postup ručního provedení:

* V Průzkumníku souborů přejděte do adresáře projektu.
* Otevřete soubor *extension. vsixmanifest* pomocí textového editoru.
* Přidejte následující značku:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Uložte soubor a zavřete ho.

> [!NOTE]
> Možná budete muset ručně upravit požadovanou verzi, abyste zajistili, že je kompatibilní se všemi verzemi sady Visual Studio 2019 nebo 2017. Důvodem je, že návrhář vloží minimální verzi jako aktuální verzi sady Visual Studio (například 15.0.26208.0). Ale vzhledem k tomu, že jiní uživatelé můžou mít starší verzi, budete ji chtít ručně upravit na 15,0.

V tomto okamžiku by měl váš soubor manifestu vypadat přibližně takto:

![Příklad předpokladů](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Úprava souboru projektu (MyProject. csproj)

Důrazně doporučujeme mít při provádění tohoto kroku otevřený odkaz na upravený. csproj. [Tady](https://github.com/Microsoft/VSSDK-Extensibility-Samples)můžete najít několik příkladů. Vyberte libovolnou ukázku rozšiřitelnosti, vyhledejte soubor *. csproj* pro referenci a proveďte následující kroky:

* V **Průzkumníku souborů**přejděte do adresáře projektu.
* Otevřete soubor *MyProject. csproj* pomocí textového editoru.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. aktualizace MinimumVisualStudioVersion

* Nastavte minimální verzi sady Visual Studio na `$(VisualStudioVersion)` a přidejte do ní podmíněný příkaz. Přidejte tyto značky, pokud neexistují. Ujistěte se, že jsou značky nastaveny níže:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. přidejte vlastnost VsixType.

* Přidejte následující značku `<VsixType>v3</VsixType>` do skupiny vlastností.

> [!NOTE]
> Doporučuje se přidat pod `<OutputType></OutputType>` značku.

### <a name="3-add-the-debugging-properties"></a>3. Přidejte vlastnosti ladění

* Přidejte následující skupinu vlastností:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartProgram>$(DevEnvDir)devenv.exe</StartProgram>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Odstraňte všechny instance následujícího příkladu kódu ze souboru *. csproj* a všech souborů *. csproj. User* :

```xml
<StartAction>Program</StartAction>
<StartProgram>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartProgram>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Přidání podmínek do importů nástrojů sestavení

* Přidejte další podmíněné příkazy do `<import>` značek, které mají odkaz Microsoft. VSSDK. BuildTools. Vložte `'$(VisualStudioVersion)' != '14.0' And` na začátek příkazu Condition. Tyto příkazy se zobrazí v záhlaví a zápatí souboru csproj.

Příklad:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Přidejte další podmíněné příkazy do `<import>` značek, které mají sadu Microsoft. VisualStudio. SDK. BuildTasks. 14.0. Vložte `'$(VisualStudioVersion)' == '14.0' And` na začátek příkazu Condition. Tyto příkazy se zobrazí v záhlaví a zápatí souboru csproj.

Příklad:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Přidejte další podmíněné příkazy do `<Error>` značek, které mají odkaz Microsoft. VSSDK. BuildTools. Provedete to vložením `'$(VisualStudioVersion)' != '14.0' And` na začátek příkazu Condition. Tyto příkazy se zobrazí v zápatí souboru csproj.

Příklad:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Přidejte další podmíněné příkazy do `<Error>` značek, které mají sadu Microsoft. VisualStudio. SDK. BuildTasks. 14.0. Vložte `'$(VisualStudioVersion)' == '14.0' And` na začátek příkazu Condition. Tyto příkazy se zobrazí v zápatí souboru csproj.

Příklad:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Uložte soubor CSPROJ a zavřete jej. 
  * Všimněte si, že pokud používáte více než jeden projekt v řešení, nastavte tento projekt jako spouštěný projekt pomocí možnosti "nastavit jako spouštěný projekt" v místní nabídce projekt). Tím zajistíte, že Visual Studio po uvolnění znovu otevře tento projekt.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2019-or-2017"></a>Test instalace rozšíření v aplikaci Visual Studio 2015 a Visual Studio 2019 nebo 2017

V tomto okamžiku by měl být projekt připravený k vytvoření nového vsixv3, který se dá nainstalovat na Visual Studio 2015 i Visual Studio 2017.

* Otevřete projekt v aplikaci Visual Studio 2015.
* Sestavte projekt a potvrďte výstup, který VSIX vytvoří správně.
* Přejděte do adresáře projektu.
* Otevřete složku *\bin\debug* .
* Dvakrát klikněte na soubor VSIX a nainstalujte své rozšíření do sady Visual Studio 2015 a Visual Studio 2019/2017.
* Ujistěte se, že se v **Tools**  >  části **nainstalováno** zobrazuje rozšíření v části**rozšíření a aktualizace** nástrojů.
* Pokuste se spustit nebo použít rozšíření pro kontrolu, že funguje.

![Najít VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> Pokud váš projekt přestane reagovat na zprávu o **otevření souboru**, vynutit vypnutí sady Visual Studio, přejděte do adresáře projektu, zobrazte skryté složky a odstraňte složku *. vs* .
 
