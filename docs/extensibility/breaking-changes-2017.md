---
title: Rozbíjející změny v rozšíření sady Visual Studio 2017 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a7ed5322c131bd9f3b758b31169676865880fd7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826489"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Změny v rozšíření sady Visual Studio 2017

Pomocí sady Visual Studio 2017, teď nabízíme [rychlejší, nenáročný prostředí instalace sady Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) zároveň dává uživatelům větší výběr úloh a funkcí, které sníží to dopad sady Visual Studio v systémech uživatelů které se instalují. Pro podporu těchto vylepšení jsme udělali změny model rozšiřitelnosti a odstraňuje některé narušující změny provedené rozšiřitelnost sady Visual Studio. Tento dokument ale popisuje technické podrobnosti o tyto změny a co se dá dělat k jejich řešení. Mějte prosím na paměti, že některé informace se podrobnosti implementace v daném okamžiku a může být později změnit.

## <a name="changes-affecting-vsix-format-and-installation"></a>Změny, které mají vliv formát VSIX a instalace

Zavádíme VSIX v. 3 (verze 3) formát pro podporu prostředí odlehčené instalace.

Změny formátu VSIX patří:

* Prohlášení o požadovaných součástí instalace. K doručování na příslib odlehčený, rychlý instalace sady Visual Studio, instalační program teď nabízí další možnosti konfigurace pro uživatele. Kvůli tomu aby bylo zajištěno, že jsou nainstalované funkce a součásti vyžadované pro rozšíření, bude rozšíření potřeba deklarovat jejich závislosti.
  * Instalační program sady Visual Studio 2017 automaticky nabídne získat a nainstalovat komponenty potřebné pro daného uživatele jako součást instalace příslušného rozšíření.
  * Uživatelům zobrazí upozornění také při pokusu o instalaci rozšíření, které nebylo vytvořené pomocí nového formátu VSIX v3, i když bylo označeno ve svém manifestu jako cílení na verzi 15.0.
* Vylepšené funkce pro formát VSIX. Dodržujeme [nízkým dopadem instalace](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) sady Visual Studio, která podporuje také nainstaluje vedle sebe, už většina konfigurační data uložit do registru systému jsme přesunuli Visual Studio konkrétní sestavení z mezipaměti GAC. Také jsme zvýšili funkce formát VSIX a instalace modulu VSIX, abyste mohli používat ho místo MSI nebo EXE instalace rozšíření pro některé typy instalace.

  Mezi nové schopnosti patří:

  * Registrace do zadané instance sady Visual Studio.
  * Instalace mimo [složku rozšíření](set-install-root.md).
  * Zjišťování na architektuře procesoru.
  * Závislost na oddělené jazyk jazykových sad.
  * Instalace s [podpora technologie NGEN](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Vytváření rozšíření pro Visual Studio 2017

Návrhářské nástroje pro vytváření nového formát manifestu VSIX v3 je teď dostupná v sadě Visual Studio 2017. Zobrazit související dokument [postupy: migrace projektů rozšíření do sady Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) podrobnosti o použití návrhářské nástroje nebo provádění ruční aktualizací do projektu a manifest pro vývoj rozšíření VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Změna: Cesta k datům uživatele sady Visual Studio

Dříve může existovat pouze jedna instalace každá hlavní verze produktu Visual Studio na každém počítači. Pro podporu-souběžnými instalacemi sady Visual Studio 2017, může existovat více cesty k datům uživatelů pro sadu Visual Studio na počítači uživatele.

Chcete-li použít nastavení správce sady Visual Studio se musí aktualizovat kód spuštěný v procesu sady Visual Studio. Kód spuštěný mimo proces sady Visual Studio můžete najít cestu uživatele konkrétní instalaci sady Visual Studio [podle pokynů tady](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Změna: Globální mezipaměť sestavení (GAC)

Většina základních sestavení sady Visual Studio jsou již nainstalovány do mezipaměti GAC. Byly provedeny následující změny tak, aby kód spuštěný v procesu sady Visual Studio, stále můžete najít požadovaná sestavení za běhu.

> [!NOTE]
> [INSTALLDIR] tady odkazuje na kořenový adresář instalace sady Visual Studio. *VSIXInstaller.exe* se to automaticky vyplní, ale k psaní kódu, vlastní nasazení, přečtěte si prosím [vyhledání sady Visual Studio](locating-visual-studio.md).

* Sestavení, které byly nainstalovány pouze do GAC:
  * Tato sestavení jsou teď nainstalované v adresáři <em>[INSTALLDIR] \Common7\IDE\*, * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> nebo *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*. Tyto složky jsou součástí definovaných cest proces sady Visual Studio.

* Sestavení, které byly nainstalovány do cesty – testování a do mezipaměti GAC:
  * Kopie v mezipaměti GAC byl odebrán z instalačního programu.
  * A *.pkgdef* soubor se přidal k určení základní záznam kódu pro sestavení.

    Příklad:

    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    Za běhu, sloučí subsystému pkgdef sady Visual Studio tyto položky do konfigurační soubor procesu Visual Studio modulu runtime (v části *[VSAPPDATA]\devenv.exe.config*) jako [ `<codeBase>` ](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) elementy. Toto je doporučeným způsobem, jak umožnit proces sady Visual Studio najít sestavení, protože se eliminuje prohledávat zjišťování cesty.

### <a name="reacting-to-this-breaking-change"></a>Reakce na tento zásadní změna

* Pokud v rámci procesu Visual Studio běží vaše rozšíření:
  * Váš kód bude moct vyhledat sestavení sady Visual Studio core.
  * Zvažte použití *.pkgdef* soubor v případě potřeby zadejte cestu k sestavení.
* Pokud vaše rozšíření běží mimo proces sady Visual Studio:
  * Vezměte v úvahu hledáte Visual Studio core sestavení v rámci <em>[INSTALLDIR] \Common7\IDE\*, * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> nebo *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*použitím překladač konfigurační soubor nebo sestavení.

## <a name="change-reduce-registry-impact"></a>Změn: Registru dopad

### <a name="global-com-registration"></a>Globální registrace modelu COM

* Dříve nainstalované sady Visual Studio do HKEY_CLASSES_ROOT a HKEY_LOCAL_MACHINE podregistry pro podporu nativních registrace modelu COM mnoho klíče registru. Chcete-li odstranit tento dopad, Visual Studio nyní používá [Bezregistrační aktivace komponent COM](https://msdn.microsoft.com/library/ms973913.aspx).
* V důsledku toho většina vyrovnávací paměti TLB / OLB / knihovny DLL v části % ProgramFiles (x86) %\Common Files\Microsoft Shared\MSEnv nebudou nainstalované ve výchozím nastavení sada Visual Studio. Tyto soubory jsou teď nainstalované v [INSTALLDIR] s odpovídající manifesty COM bez registrace používá hostitelský proces sady Visual Studio.
* V důsledku toho najdete externí kód, který využívá globální registrace modelu COM pro rozhraní Visual Studio COM už tyto registrace. Kód spuštěný v procesu sady Visual Studio se nezobrazí rozdíl.

### <a name="visual-studio-registry"></a>Visual Studio registru

* Dříve nainstalované sady Visual Studio mnoho klíče registru do systému **HKEY_LOCAL_MACHINE** a **HKEY_CURRENT_USER** podregistry v rámci Visual Studio konkrétní klíče:
  * **HKLM\Software\Microsoft\VisualStudio\{verze}**: klíče registru vytvořené pomocí Instalační služby MSI a rozšíření vázaná na počítač.
  * **HKCU\Software\Microsoft\VisualStudio\{verze}**: vytvořených pomocí Visual Studia ukládat uživatelská nastavení klíče registru.
  * **HKCU\Software\Microsoft\VisualStudio\{verze} _Config**: kopii výše uvedené klíče Visual Studio HKLM a klíče registru sloučením *.pkgdef* souborů podle přípony.
* Pokud chcete snížit dopad na registru, Visual Studio nyní používá [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) funkce pro ukládání klíčů registru v privátní binárního souboru v rámci *[VSAPPDATA]\privateregistry.bin*. Velmi malý počet Visual Studio zkratky specifické pro zůstat v systémovém registru.

* Stávající kód spuštěný v procesu sady Visual Studio to neovlivní. Visual Studio přesměruje do privátního registru, všechny operace registru pod klíčem konkrétní HKCU Visual Studio. Čtení a zápis do jiných umístění registru bude nadále používat systémového registru.
* Externí kód bude potřebovat k načtení a čtení z tohoto souboru pro položky registru sady Visual Studio.

### <a name="reacting-to-this-breaking-change"></a>Reakce na tento zásadní změna

* Pro účely Bezregistrační aktivace komponent COM také mají být převedeny externí kód.
* Externí komponenty můžete vyhledat umístění sady Visual Studio [podle pokynů tady](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* Doporučujeme použít externí komponenty [externí prostřednictvím Správce nastavení](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) místo čtení/zápis přímo na klíče registru sady Visual Studio.
* Zkontrolujte, jestli komponenty, které používá vaše rozšíření může implementovat další techniku pro registraci. Rozšíření ladicího programu může být například moct využívat nové [msvsmon registrace modelu COM soubor JSON](migrate-debugger-COM-registration.md).
