---
title: Průlomové změny v rozšíření Visual Studio 2017
description: Seznamte se s technickými podrobnostmi o zásadních změnách v modelu rozšiřitelnosti v aplikaci Visual Studio 2017 a k tomu, abyste je mohli řešit.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c07d48eb63c727701c3b6fcde9d405f9c96abec1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068190"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Změny v rozšíření sady Visual Studio 2017

Visual Studio 2017 nabízí [rychlejší a světlejší prostředí pro instalaci sady Visual Studio](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) , které snižuje dopad sady Visual Studio na uživatelské systémy a zároveň dává uživatelům větší možnosti pro úlohy a funkce, které jsou nainstalovány. Pro podporu těchto vylepšení jsme provedli změny v modelu rozšiřitelnosti, včetně některých nezměněných změn. Tento článek popisuje technické podrobnosti o těchto změnách a o tom, co se dá udělat, abyste je mohli řešit.

> [!NOTE]
> Některé informace jsou podrobné informace o implementaci k určitému časovému okamžiku a mohou být později změněny.

## <a name="changes-affecting-vsix-format-and-installation"></a>Změny ovlivňující formát VSIX a instalaci

Visual Studio 2017 zavedlo formát VSIX V3 (verze 3), který podporuje odlehčené instalace.

Změny ve formátu VSIX zahrnují:

* Deklarace požadavků na instalaci Za účelem doplňování odlehčené a rychlé instalace sady Visual Studio nabízí instalační program nyní pro uživatele další možnosti konfigurace. V důsledku toho musí rozšíření deklarovat své závislosti, aby bylo zajištěno, že jsou nainstalované součásti a součásti požadované rozšířením.

  * Instalační program sady Visual Studio 2017 automaticky nabídne získání a instalaci nezbytných součástí pro uživatele jako součást instalace rozšíření.
  * Uživatelé jsou také upozorněni při pokusu o instalaci rozšíření, které nebylo vytvořeno pomocí nového formátu VSIX v3, i když byly označeny v manifestu jako cílený na verzi 15,0.

* Rozšířené možnosti pro formát VSIX Aby bylo možné doručovat instalaci sady Visual Studio s [nízkými důsledky](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) , která podporuje i souběžné instalace, již neukládáme většinu konfiguračních dat do systémového registru a přesunuli sestavení specifická pro sadu Visual Studio z GAC. Zvýšili jsme také možnosti formátu VSIX a instalačního modulu VSIX, což vám umožní použít ho místo MSI nebo EXE k instalaci rozšíření pro některé typy instalace.

Mezi nové funkce patří:

* Registrace do zadané instance sady Visual Studio.
* Instalace mimo [složku rozšíření](set-install-root.md).
* Detekce architektury procesoru.
* Závislost na jazykových sadách oddělených jazykem
* Instalace s [podporou Ngen](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Sestavení rozšíření pro Visual Studio 2017

Nástroje návrháře pro vytváření nového formátu manifestu VSIX V3 jsou k dispozici v aplikaci Visual Studio 2017. V doprovodném dokumentu najdete [Postup: migrace rozšiřujících projektů do sady Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) pro podrobnosti o používání nástrojů návrháře nebo provedení ruční aktualizace projektu a manifestu pro vývoj rozšíření VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Změna: cesta k uživatelským datům sady Visual Studio

Dříve mohli na každém počítači existovat pouze jedna instalace každé hlavní verze sady Visual Studio. Aby bylo možné podporovat souběžné instalace sady Visual Studio 2017, může v počítači uživatele existovat více cest k datům uživatelů pro sadu Visual Studio.

Kód spuštěný uvnitř procesu sady Visual Studio by měl být aktualizován tak, aby používal správce nastavení sady Visual Studio. Kód spuštěný mimo proces sady Visual Studio může najít cestu uživatele konkrétní instalace sady Visual Studio [podle pokynů uvedených tady](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Změna: globální mezipaměť sestavení (GAC)

Většina základních sestavení sady Visual Studio již není nainstalována do GAC. Byly provedeny následující změny, aby kód spuštěný v procesu sady Visual Studio mohl stále vyhledat požadovaná sestavení v době běhu.

> [!NOTE]
> [INSTALLDIR] níže odkazuje na kořenový adresář instalace aplikace Visual Studio. *VSIXInstaller.exe* to automaticky naplní, ale pokud chcete napsat vlastní kód nasazení, přečtěte si prosím [umístění sady Visual Studio](locating-visual-studio.md).

* Sestavení, která byla nainstalována pouze do globální mezipaměti sestavení (GAC):

  Tato sestavení jsou nyní nainstalována v rámci <em>[INSTALLDIR] \Common7\IDE \* , * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> nebo *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*. Tyto složky jsou součástí cest zjišťování procesu sady Visual Studio.

* Sestavení, která byla nainstalována do cesty bez zjišťování a do globální mezipaměti sestavení (GAC):

  * Kopie v mezipaměti GAC byla odebrána z instalačního programu.
  * Byl přidán soubor *. pkgdef* , který určuje základní položku kódu pro sestavení.

    Například:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    V době spuštění sloučí podsystém pkgdef sady Visual Studio tyto položky do konfiguračního souboru modulu runtime procesu sady Visual Studio (pod *[VSAPPDATA] \devenv.exe.config*) jako [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) elementy. Toto je doporučený způsob, jak nechat proces sady Visual Studio najít vaše sestavení, protože se zabrání v hledání prostřednictvím cest pro zjišťování.

### <a name="reacting-to-this-breaking-change"></a>Reakce na tuto změnu přerušení

* Pokud je vaše rozšíření spuštěné v rámci procesu sady Visual Studio:

  * Váš kód bude moci najít základní sestavení sady Visual Studio.
  * Zvažte použití souboru *. pkgdef* k určení cesty k sestavení v případě potřeby.

* Pokud je vaše rozšíření spuštěné mimo proces sady Visual Studio:

  Zvažte možnost Hledat základní sestavení sady Visual Studio v části <em>[INSTALLDIR] \Common7\IDE \* , * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> nebo *[INSTALLDIR] \Common7\IDE\PrivateAssemblies* pomocí konfiguračního souboru nebo překladače sestavení.

## <a name="change-reduce-registry-impact"></a>Změna: zmenšení dopadu registru

### <a name="global-com-registration"></a>Globální registrace COM

* Dříve Visual Studio nainstalovalo mnoho klíčů registru do HKEY_CLASSES_ROOT a HKEY_LOCAL_MACHINE podregistry pro podporu nativní registrace modelu COM. Aby se tento dopad vyloučil, Visual Studio teď používá [aktivaci bez registrace pro komponenty com](/previous-versions/dotnet/articles/ms973913(v=msdn.10)).
* V důsledku toho většina souborů TLB/OLB/DLL pod% ProgramFiles (x86)% \ Common Files\Microsoft Shared\MSEnv již není ve výchozím nastavení sady Visual Studio nainstalována. Tyto soubory jsou nyní nainstalovány v rámci [INSTALLDIR] s Registration-Free odpovídajícími manifesty COM, které používá hostitelský proces sady Visual Studio.
* Výsledkem je, že externí kód, který závisí na globální registraci COM pro rozhraní COM sady Visual Studio, již nebude tyto registrace najít. Kód spuštěný uvnitř procesu sady Visual Studio neuvidí rozdíl.

### <a name="visual-studio-registry"></a>Registr sady Visual Studio

* Dříve aplikace Visual Studio nainstalovala mnoho klíčů registru do **HKEY_LOCAL_MACHINE** systému a **HKEY_CURRENT_USER** podregistry v rámci klíče specifického pro Visual Studio:

  * **HKLM\Software\Microsoft\VisualStudio \{ Verze}**: klíče registru vytvořené instalačními programy MSI a rozšířeními vázanými na počítač.
  * **HKCU\Software\Microsoft\VisualStudio \{ Verze}**: klíče registru vytvořené v aplikaci Visual Studio k ukládání nastavení specifických pro uživatele.
  * **HKCU\Software\Microsoft\VisualStudio \{ Version} _Config**: výše uvedený klíč sady Visual Studio HKLM a klíče registru sloučené ze souborů *. pkgdef* podle rozšíření.

* Aby se snížil dopad v registru, Visual Studio teď používá funkci [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) k ukládání klíčů registru do privátního binárního souboru v *[VSAPPDATA] \privateregistry.bin*. V systémovém registru zůstane pouze velmi malý počet klíčů specifických pro sadu Visual Studio.
* Existující kód spuštěný uvnitř procesu sady Visual Studio nemá vliv. Visual Studio bude přesměrovat všechny operace registru v rámci klíče HKCU sady Visual Studio do privátního registru. Čtení a zápis do jiných umístění registru bude pokračovat v používání systémového registru.
* Externí kód bude potřebovat načíst a číst z tohoto souboru pro položky registru sady Visual Studio.

### <a name="react-to-this-breaking-change"></a>Reagovat na tuto zásadní změnu

* Externí kód by měl být převeden tak, aby používal i Registration-Free aktivaci pro součásti modelu COM.
* Externí komponenty mohou najít umístění sady Visual Studio [podle pokynů uvedených tady](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Doporučujeme, aby externí komponenty používaly [Správce externích nastavení](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) namísto čtení/zápisu přímo do klíčů registru sady Visual Studio.
* Ověřte, zda komponenty používané rozšířením mohou být implementovány jiným způsobem pro registraci. Například rozšíření ladicího programu může být schopné využít novou [registraci souboru com msvsmon JSON](migrate-debugger-COM-registration.md).