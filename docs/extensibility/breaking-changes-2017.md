---
title: Nejnovější změny v sadě Visual Studio 2017 rozšiřitelnost
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b3a04c925ef897171de51c73c90973a12c3b17d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739967"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Změny v rozšiřitelnosti sady Visual Studio 2017

Visual Studio 2017 poskytuje [rychlejší a lehčí instalaci sady Visual Studio,](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) která snižuje dopad sady Visual Studio na uživatelské systémy a zároveň poskytuje uživatelům větší výběr nad nainstalovanými úlohami a funkcemi. Pro podporu těchto vylepšení jsme provedli změny modelu rozšiřitelnosti, včetně některých narušujících změn. Tento článek popisuje technické podrobnosti o těchto změnách a co lze udělat pro jejich řešení.

> [!NOTE]
> Některé informace jsou podrobnosti implementace v okamžiku a mohou být později změněny.

## <a name="changes-affecting-vsix-format-and-installation"></a>Změny ovlivňující formát a instalaci vsix

Visual Studio 2017 představilo formát VSIX v3 (verze 3), který podporuje zjednodušené prostředí pro instalaci.

Změny ve formátu VSIX zahrnují:

* Deklarace předpokladů nastavení. Aby bylo nutné splnit slib lehkého a rychle se instalujícího sady Visual Studio, instalační program nyní nabízí uživatelům další možnosti konfigurace. V důsledku toho, aby bylo zajištěno, že jsou nainstalovány funkce a součásti vyžadované rozšíření, rozšíření je třeba deklarovat jejich závislosti.

  * Instalační program Sady Visual Studio 2017 automaticky nabídne získání a instalaci nezbytných součástí pro uživatele v rámci instalace rozšíření.
  * Uživatelé jsou také upozorněni při pokusu o instalaci rozšíření, které nebylo vytvořeno pomocí nového formátu VSIX v3, i v případě, že byly označeny v jejich manifestu jako cílení verze 15.0.

* Rozšířené možnosti pro formát VSIX. Chcete-li dodat na [instalaci s nízkým dopadem](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) sady Visual Studio, která také podporuje souběžné instalace, jsme již uložit většinu konfiguračních dat do systémového registru a přesunuli sestavení specifické pro visual studio z GAC. Také jsme zvýšili možnosti formátu VSIX a instalačního modulu VSIX, což vám umožní používat jej spíše než MSI nebo EXE k instalaci rozšíření pro některé typy instalací.

Mezi nové funkce patří:

* Registrace do zadané instance sady Visual Studio.
* Instalace mimo [složku rozšíření](set-install-root.md).
* Detekce architektury procesoru.
* Závislost na jazykových balíčcích oddělených jazykem.
* Instalace s [podporou NGEN](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Vytvoření rozšíření pro Visual Studio 2017

Návrhářské nástroje pro vytváření nového formátu manifestu VSIX v3 jsou k dispozici v sadě Visual Studio 2017. Podrobnosti o použití návrhářských nástrojů nebo ručních aktualizacích projektu a manifestu pro vývoj rozšíření VSIX v3 najdete v doprovodném dokumentu [How to: Migrate rozšiřitelnost i v Sadě Visual Studio 2017.](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)

## <a name="change-visual-studio-user-data-path"></a>Změna: Cesta k uživatelským datům sady Visual Studio

Dříve mohla v každém počítači existovat pouze jedna instalace každé hlavní verze sady Visual Studio. Pro podporu souběžných instalací sady Visual Studio 2017 může v počítači uživatele existovat více cest uživatelských dat pro visual studio.

Kód spuštěný v rámci procesu sady Visual Studio by měl být aktualizován tak, aby používal Správce nastavení sady Visual Studio. Kód spuštěný mimo proces sady Visual Studio může najít uživatelskou cestu konkrétní instalace sady Visual Studio [podle pokynů zde](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Změna: Globální mezipaměť sestavení (GAC)

Většina sestavení jádra sady Visual Studio již nejsou nainstalovány do GAC. Následující změny byly provedeny tak, aby kód spuštěný v procesu sady Visual Studio stále najít požadovaná sestavení za běhu.

> [!NOTE]
> [INSTALLDIR] níže odkazuje na kořenový adresář instalace sady Visual Studio. *VSIXInstaller.exe* bude automaticky naplnit to, ale napsat vlastní kód nasazení, přečtěte si [vyhledání Visual Studio](locating-visual-studio.md).

* Sestavení, která byla nainstalována pouze do gac:

  Tato sestavení jsou nyní nainstalována pod <em>programem [INSTALLDIR]\Common7\IDE\*, *[INSTALLDIR]\Common7\IDE\PublicAssemblies</em> nebo *[INSTALLDIR]\Common7\IDE\PrivateAssemblies*. Tyto složky jsou součástí procesu visual studio sondování cesty.

* Sestavení, která byla nainstalována do cesty bez sondování a do gac:

  * Kopie v GAC byla odebrána z instalace.
  * Byl přidán soubor *.pkgdef,* který určuje základní položku kódu pro sestavení.

    Například:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    Za běhu subsystém usady Visual Studio pkgdef sloučí tyto položky do konfiguračního souboru runtime procesu sady Visual [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) Studio (v části *[VSAPPDATA]\devenv.exe.config)* jako prvky. Toto je doporučený způsob, jak nechat proces sady Visual Studio najít sestavení, protože se vyhýbá hledání prostřednictvím cesty zjišťování.

### <a name="reacting-to-this-breaking-change"></a>Reakce na tuto zlomka změna

* Pokud vaše rozšíření běží v rámci procesu Sady Visual Studio:

  * Váš kód bude moci najít sestavení jádra sady Visual Studio.
  * V případě potřeby zvažte použití souboru *.pkgdef* k určení cesty k sestavením.

* Pokud vaše rozšíření běží mimo proces sady Visual Studio:

  Zvažte vyhledání základních sestavení sady Visual Studio v části <em>\*[INSTALLDIR]\Common7\IDE , *[INSTALLDIR]\Common7\IDE\PublicAssemblies</em> nebo *[INSTALLDIR]\Common7\IDE\PrivateAssemblies* pomocí konfiguračního souboru nebo překládání sestavení.

## <a name="change-reduce-registry-impact"></a>Změna: Snížení dopadu registru

### <a name="global-com-registration"></a>Globální registrace komody

* Dříve visual studio nainstalovalo mnoho klíčů registru do HKEY_CLASSES_ROOT a HKEY_LOCAL_MACHINE podregistrů pro podporu nativní registrace com. Chcete-li tento dopad eliminovat, Visual Studio nyní používá [aktivaci bez registrace pro součásti modelu COM](https://msdn.microsoft.com/library/ms973913.aspx).
* V důsledku toho se většina souborů TLB / OLB / DLL pod položkou %ProgramFiles(x86)%\Common Files\Microsoft Shared\MSEnv již není nainstalována ve výchozím nastavení aplikací Visual Studio. Tyto soubory jsou nyní nainstalovány pod [INSTALLDIR] s odpovídajícími manifesty COM bez registrace používané procesem hostitele sady Visual Studio.
* V důsledku toho externí kód, který závisí na globální registraci COM pro rozhraní Visual Studio COM již nebude najít tyto registrace. Kód spuštěný v rámci procesu sady Visual Studio neuvidí rozdíl.

### <a name="visual-studio-registry"></a>Registr visual studia

* Dříve visual studio nainstalovalo mnoho klíčů registru do **HKEY_LOCAL_MACHINE** a **HKEY_CURRENT_USER** pod klíčem specifickým pro aplikaci Visual Studio:

  * **HKLM\Software\Microsoft\VisualStudio\{Version}**: Klíče registru vytvořené instalačními programy MSI a rozšířeními pro počítač.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}**: Klíče registru vytvořené aplikací Visual Studio pro uložení nastavení specifických pro uživatele.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}_Config**: Kopie výše uvedeného klíče HKLM sady Visual Studio a klíče registru sloučené z souborů *.pkgdef* příponami.

* Chcete-li snížit dopad na registr, visual studio nyní používá [funkci RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) k ukládání klíčů registru v soukromém binárním souboru pod *[VSAPPDATA]\privateregistry.bin*. V systémovém registru zůstává pouze velmi malý počet klíčů specifických pro aplikaci Visual Studio.
* Existující kód spuštěný v procesu sady Visual Studio není ovlivněn. Visual Studio přesměruje všechny operace registru pod hkcu Visual Studio specifické pro soukromý registr. Čtení a zápis do jiných umístění registru bude nadále používat systémový registr.
* Externí kód bude nutné načíst a číst z tohoto souboru pro položky registru sady Visual Studio.

### <a name="react-to-this-breaking-change"></a>Reagujte na tuto zlomící změnu

* Externí kód by měl být převeden na použití aktivace bez registrace pro komponenty modelu COM.
* Externí součásti můžete najít umístění Visual Studio [podle pokynů zde](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Doporučujeme, aby externí součásti používaly [Správce externích nastavení](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) namísto čtení a zápisu přímo do klíčů registru sady Visual Studio.
* Zkontrolujte, zda součásti, které vaše rozšíření používá, mohly implementovat jinou techniku pro registraci. Rozšíření ladicího programu mohou být například schopna využít nové [registrace com souboru msvsmon JSON](migrate-debugger-COM-registration.md).
