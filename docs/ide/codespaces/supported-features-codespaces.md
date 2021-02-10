---
title: Podporované funkce sady Visual Studio (Preview)
description: Přečtěte si o funkcích rozhraní IDE sady Visual Studio, které jsou k dispozici při práci se službou GitHub Codespaces
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 1a94915748f6c7cedb19a0b27c67eb67d6086963
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971138"
---
# <a name="supported-visual-studio-features-preview"></a>Podporované funkce sady Visual Studio (Preview)

Visual Studio poskytuje bohatou vývojové prostředí při připojování k codespace. Získáte nástroje pro vnitřní smyčku sady Visual Studio, se kterými jste obeznámeni s úpravami, laděním, testováním a verzí zdrojového kódu a také funkcí produktivity, jako jsou šablony projektů, navigace v kódu a IntelliSense.

V aktuální [veřejné beta verzi](https://github.com/features/codespaces)GitHub Codespaces nemusí některé funkce sady Visual Studio mít plnou podporu nebo můžou být zpočátku chybějící. Následující části popisují, co můžete očekávat v rámci sady Visual Studio a GitHub Codespaces beta a co můžete v budoucnu nahlížet. 

Nejedná se tedy o **vyčerpávající seznam**, ale k vysvětlení obecných možností sady Visual Studio, pokud se připojíte k codespace.

> [!NOTE]
> Pokud při používání codespaces se sadou Visual Studio dojde k nějaké funkci, dejte nám prosím o problému na [komunitě vývojářů sady Visual Studio](https://aka.ms/feedback/suggest?space=8)problém. To nám pomůže upřednostnit nejdůležitější funkce.

> [!NOTE]
> Níže popsané funkce jsou pro Visual Studio, ne pro dva další klienty GitHub Codespaces; Visual Studio Code a Editor v prohlížeči.

## <a name="edit-and-navigation"></a>Úpravy a navigace

Při získávání funkcí inteligentního jazyka jako IntelliSense, navigace v kódu, diagnostika a návrhy byste si měli všimnout malého rozdílu v úpravě zdrojového kódu v codespace.

* IntelliSense
* Navigace v kódu *
* Formátování kódu pomocí formátu dokumentu
* Zvýrazňování syntaxe
* Rychlé informace *
* HTML, CSS, editory Razor * – částečná podpora.
* JavaScript a editor TypeScript * – částečná podpora.

Ještě není k dispozici:

* IntelliSense * – některé filtry automatického dokončování/seznamu členů nejsou k dispozici. Dokončení pro neimportované typy a IntelliSense v okně kukátka ještě není k dispozici.
* Navigace v kódu *-většina příkazů je podporována. Přejít na základní a vyhledat v souborech se specifikací cesty se zatím nepodporují.
* Rychlé informace *-barvy v rychlých informacích se nepodporují.
* HTML, CSS, editory Razor * – diagnostika, dokončování technologií IntelliSense, rychlé informace, inteligentní odsazení. V současné době není podporovaná sémantika barev, navigační příkazy atd.
* JavaScript a editor TypeScript *-bloky skriptu (například obsah JavaScriptu v souborech HTML a CSHTML) a sémantické zvýrazňování se ještě nepodporují. Známé problémy s funkcemi žárovky a linting.
* Zobrazení cílů CMake
* Editor nastavení projektů CMake
* Ctrl + F7 (soubor kompilace)
* CodeLens
* Fragmenty kódu
* IntelliCode

## <a name="application-types-and-configuration"></a>Typy a konfigurace aplikací

Většina typů aplikací a konfigurací projektu je podporovaná, ale budete muset kód projektu upravit přímo bez nutnosti pomáhat vizuálním návrhářům. Další pokyny ke konfiguraci najdete v tématu [Postup přizpůsobení codespace](customize-codespaces.md).

* Šablony projektů a položek
* Projekty .NET Core a ASP.NET Core
* Konzolové aplikace C++ – podporovaná CMake a vcxproj
* Aplikace C++ určené pro Linux – většinou podporované pro jiné než grafické rozhraní. Možnost instalovat a zřídit WSL, technologii IntelliSense specifickou pro platformu a sestavení.
* Úpravy souborů projektu – nejčastěji se podporují. Chybí některé dokončování, zvýrazňování syntaxe a rozšířené možnosti úprav.
* Účty GitHubu – můžete použít k vytvoření a připojení k Codespaces a přístup k prostředkům dostupným pro účet na GitHubu.
* Azure CLI – nesdílí přihlášený účet identity sady Visual Studio nebo účty klíčů. Přihlášení založené na prohlížeči není podporované, ale v rámci integrovaného terminálu se můžete ověřit pomocí: `az login --use-device-code` .

Ještě není k dispozici:

* Návrháři uživatelského rozhraní – WinForms, WPF a Návrháři prostředků
* Přetypování aplikace projektů WinForms a WPF je k dispozici pouze v rámci příznaku funkce.
* Projekty Visual Basic a F #
* .NET Framework cílené projekty
* Docker Compose projekty
* Stránky vlastností projektu
* Možnosti ověřování v šablonách ASP.NET Core
* Aplikace, které vyžadují instalaci grafického uživatelského rozhraní (včetně instalačního programu pro čokolády), jsou podporované na všech aplikacích, které se dají nainstalovat s terminálem, ale skutečné grafické rozhraní (GUI) nebude k dispozici okamžitě. Povolení přístupu k GUI na celé Live Share obrazovce je aktuální alternativní řešení. Konzoly pro správu nejsou k dispozici. Aplikace, které vyžadují restart k instalaci, se nepodporují.
* Spravované identity pro prostředky Azure v nástroji Visual Studio
* Prostředky intranetu (privátní síť) – v současné době se codespaces nebude moci připojit k jakémukoli prostředku, který vyžaduje síť VPN.
* Rozšíření – při použití Codespaces se sadou Visual Studio se nepodporují žádná rozšíření.

## <a name="debugging"></a>Ladění

Základní ladění vnitřních smyček je podporováno, včetně nastavení zarážek, základní krokování do kódu, kontroly proměnných a oken místní, automatické hodnoty a kukátko. Některé další okna, přizpůsobení a nástroje pro vizualizaci nejsou podporovány.

* Zarážky
* Základní krokování
* Místní hodnoty, automatické hodnoty, sledování oken * – částečná podpora.
* Tipy serveru symbolů, zdrojového serveru a importu/exportu dat jsou všechny částečně podporované.

Ještě není k dispozici:

* V okně zpětného překladu se zarážky *-návěští zarážek, datové zarážky a nastavení zarážky. Import a export zarážek je částečně podporován.
* Lokální hodnoty, automatické hodnoty, sledování oken * – některé funkce, jako je například dokončování příkazů ve vyhledávacím poli a navigace vyhledávacího pole.
* Přizpůsobení uživatelského rozhraní – vlastnosti Pinnable a skrytí parametrů šablony nejsou podporované.
* Vizualizace – kód C++ natvis je částečně podporován. Okno zpětný překlad, vizuální diagnostika XAML, vlastní vizualizace rozhraní .NET a vizualizace datové sady nejsou podporovány.
* Další okna ladicího programu – procesy jsou v systému Windows částečně podporovány. Okno paralelní zásobníky – zobrazení úkolů, centrum diagnostiky a dialogové okno Najít zdroj/symbol se nepodporuje.
* Některé pracovní postupy ladicího programu – připojit k procesu, ladicí program JIT (just in time), ladění výpisu a profilování a IntelliTrace se nepodporují. C++ Pouze můj kód krokování je částečně podporováno.
* Příkaz Upravit a pokračovat – není podporován pro spravovaný i nativní kód.
* Funkce vlákna – zablokování/rozmrazení vláken, přejmenování vlákna a zobrazení vláken ve zdroji se nepodporují.
* Další funkce krokování – automatický krok nad vlastnostmi a operátory (.NET Core) a krok do specifických není podporován. 

## <a name="features"></a>Funkce

Při práci se sadou Visual Studio připojenými k codespace získáte stejné funkce usnadnění jako při práci místně.

* Správa zdrojového kódu – kompletní podpora Gitu prostřednictvím nového [integrovaného prostředí Git](../git-with-visual-studio.md). Aby byly podmoduly Git klonovány ve codespace, může být nutné spustit `git submodule update` z terminálu.
* Usnadnění – existuje jeden známý problém s asistenční technologií, která nemá přístup k appcastingi laděné aplikace. Kromě tohoto omezení nevěříme, že existují žádné jiné problémy s kompatibilitou, které ještě neexistují v místním prostředí sady Visual Studio. Dejte nám prosím jistotu, jestli zjistíte chyby tím, že napíšete problém na [komunitě vývojářů](https://aka.ms/feedback/report?space=8).
* Publikování – podporuje publikování do Azure prostřednictvím akcí GitHubu.
* Připojené služby – podpora pro App Insights, Trezor klíčů, úložiště, SQL, Redis, Cosmos, openAPI a gRPC se podporují částečně.
* Průzkumník testů * – nejčastěji se podporuje.

Ještě není k dispozici:

* Průzkumník testů * – některé funkce, jako je například výběr výchozí architektury, spuštění testů paralelně, seznamy stop atd. Známé problémy při ladění testu jednotek, spuštění nastavení a některých dalších podnikových funkcí. Profilace testů jednotek není podporována.
* Uživatelské rozhraní Správce balíčků NuGet – příkazový řádek NuGet je podporovaný.
* Funkce pro podnikové testování – Live Unit Testing, napodobeniny Microsoftu, pokrytí kódu a IntelliTest se nepodporuje.
* Pokročilé scénáře publikování – selektivní publikování, publikování FTP, náhled změn, panel nástrojů pro rychlé publikování atd.

## <a name="see-also"></a>Viz také

* [Co je GitHub Codespaces?](codespaces-overview.md)
* [Jak používat Visual Studio s codespace](use-visual-studio-with-codespaces.md)
* [Přizpůsobení codespace](customize-codespaces.md)
