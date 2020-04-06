---
title: Přidání odkazů pomocí nástroje NuGet a sady Extension SDK
ms.date: 08/02/2019
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad7fc9132647988aee46a2bb07e992505109d33c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702436"
---
# <a name="nuget-versus-sdk-as-a-project-reference"></a>NuGet versus SDK jako odkaz na projekt

Tento článek je navržen tak, aby vývojářům pomohl vybrat, zda mají svůj software balit jako balíček NuGet nebo jako sadu SDK (Software Development Kit). Konkrétně popisuje rozdíly mezi těmito dvěma, když jsou odkazovány v projektu sady Visual Studio.

- [NuGet](/nuget) je open source systém pro správu balíčků, který zjednodušuje proces začlenění knihoven do projektu. Pro rozhraní .NET (včetně .NET Core) je NuGet mechanismus podporovaný společností Microsoft pro sdílení kódu. NuGet definuje, jak jsou vytvářeny, hostovány a spotřebovány balíčky pro rozhraní .NET, a poskytuje nástroje pro každou z těchto rolí. V sadě Visual Studio přidáte balíčky NuGet do projektu pomocí uživatelského rozhraní [Správce balíčků.](/nuget/consume-packages/install-use-packages-visual-studio)

- Sada [SDK](../extensibility/creating-a-software-development-kit.md) je kolekce souborů, které Visual Studio považuje za jednu referenční položku. Dialogové okno Správce odkazů v sadě Visual Studio obsahuje seznam všech sad SDK, které jsou relevantní pro aktuální projekt, když zvolíte **Přidat odkaz**. Když přidáte sadu SDK do projektu, můžete získat přístup ke všemu obsahu této sady SDK prostřednictvím nástroje IntelliSense, okna panelu nástrojů, návrhářů, prohlížeče objektů, msbuildu, nasazení, ladění a balení.

## <a name="which-mechanism-should-i-use"></a>Jaký mechanismus mám použít?

Následující tabulka vám pomůže porovnat odkazující funkce sady SDK s odkazujícífunkce NuGet.

| Funkce | Podpora pro SDK | Poznámky sady SDK | Podpora NuGet | Poznámky nugetu |
| - | - | - |---------------| - |
| Mechanismus odkazuje na jednu entitu a pak jsou k dispozici všechny soubory a funkce. | Ano | Sadu SDK přidáte pomocí dialogového okna **Správce odkazů** a všechny soubory a funkce jsou k dispozici během pracovního postupu vývoje. | Ano | |
| MSBuild automaticky spotřebovává sestavení a soubory metadat systému Windows (*.winmd*). | Ano | Odkazy v sadě SDK jsou automaticky předány kompilátoru. | Ano | |
| MSBuild automaticky spotřebovává soubory .h nebo LIB. | Ano | Soubor *SDKName.props* říká Visual Studio, jak nastavit adresář Visual C++ a tak dále, pro automatickou spotřebu souborů *.h* nebo *LIB.* | Ne | |
| MSBuild automaticky spotřebovává soubory *JS* nebo *.css.* | Ano | V **Průzkumníku řešení**můžete rozbalit referenční uzel sady JavaScript SDK tak, aby `<source include/>` zobrazoval jednotlivé soubory *JS* nebo *CSS,* a pak generovat značky přetažením těchto souborů do jejich zdrojových souborů. Sada SDK podporuje nastavení f5 a automatického balení. | Ano | |
| Nástroj MSBuild automaticky přidá ovládací prvek do **panelu nástrojů**. | Ano | **Panel nástrojů** může využívat sady SDK a zobrazovat ovládací prvky na zadaných kartách. | Ne | |
| Mechanismus podporuje Visual Studio Installer pro rozšíření (VSIX). | Ano | VSIX má speciální manifest a logiku pro vytváření balíčků SDK | Ano | VSIX lze vložit do jiného instalačního programu. |
| **Prohlížeč objektů** vyjmenovává odkazy. | Ano | **Prohlížeč objektů** automaticky získá seznam odkazů v sadách SDK a vytvoří jejich výčet. | Ne | |
| Soubory a odkazy se automaticky přidají do dialogového okna **Správce odkazů** (odkazy nápovědy a tak dále se automaticky naplní) | Ano | Dialogové okno **Správce odkazů** automaticky vytvoří výčet sad SDK spolu s odkazy nápovědy a seznamem závislostí sady SDK. | Ne | NuGet poskytuje vlastní dialogové okno **Spravovat balíčky NuGet.** |
| Mechanismus podporuje více architektur. | Ano | Sady SDK mohou doručovat více konfigurací. MSBuild spotřebovává příslušné soubory pro každou konfiguraci projektu. | Ne | |
| Mechanismus podporuje více konfigurací. | Ano | Sady SDK mohou doručovat více konfigurací. V závislosti na architektuře projektu MSBuild spotřebovává příslušné soubory pro každou architekturu projektu. | Ne | |
| Mechanismus může určit "nekopírovat." | Ano | V závislosti na tom, zda jsou soubory vynechány ve složce *\redist* nebo *\designtime,* můžete určit, které soubory chcete zkopírovat do balíčku náročné aplikace. | Ne | Deklarujete, které soubory chcete zkopírovat v manifestu balíčku. |
| Obsah se zobrazí v lokalizovaných souborech. | Ano | Lokalizované dokumenty XML v sadách SDK jsou automaticky zahrnuty pro lepší možnosti návrhu. | Ne | |
| MSBuild podporuje spotřebovává více verzí sady SDK současně. | Ano | Sada SDK podporuje spotřebovávat více verzí současně. | Ne | Tohle není odkazování. V projektu nelze mít více než jednu verzi souborů NuGet. |
| Mechanismus podporuje určení příslušných cílových rozhraní, verzí sady Visual Studio a typů projektů. | Ano | Dialogové okno **Správce odkazů** a **panel nástrojů** zobrazují pouze sady SDK, které se vztahují k projektu, aby uživatelé mohli snadněji zvolit příslušné sady SDK. | Y (částečná) | Pivot je cílová architektura. V uživatelském rozhraní není filtrování. V době instalace může vrátit chybu. |
| Mechanismus podporuje určení registračních informací pro nativní winmds. | Ano | V souboru *SDKManifest.xml*můžete určit korelaci mezi souborem .winmd a souborem DLL . | Ne | |
| Mechanismus podporuje určení závislostí na jiných sadách SDK. | Ano | Sada SDK pouze upozorní uživatele; uživatel je musí stále instalovat a odkazovat na ně ručně. | Ano | NuGet je automaticky vytáhne; uživatel není upozorněn. |
| Mechanismus se [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] integruje s koncepty, jako je manifest aplikace a ID rozhraní. | Ano | Sada SDK musí předat koncepty, [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] které jsou specifické pro tak, aby obaly a[!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]F5 správně fungovaly s sadami SDK, které jsou k dispozici v . | Ne | |
| Mechanismus se integruje s kanálem ladění aplikací pro [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikace. | Ano | Sada SDK [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]musí předat specifické koncepty tak, aby obaly a f5 správně fungovaly s sadami SDK dostupnými v . [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] | Ano | NuGet obsah se stane součástí projektu. Není třeba věnovat pozornost žádné zvláštní f5. |
| Mechanismus se integruje s manifesty aplikací. | Ano | Sada SDK [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]musí předat specifické koncepty tak, aby obaly a f5 správně fungovaly s sadami SDK dostupnými v . [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] | Ano | NuGet obsah se stane součástí projektu. Není třeba věnovat pozornost žádné zvláštní f5. |
| Mechanismus nasazuje soubory bez odkazu (například nasadit [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] testovací rámec, na kterém spustit testy aplikací). | Ano | Pokud soubory přetáhnete do složky *\redist,* budou soubory nasazeny automaticky. | Ano | |
| Mechanismus automaticky přidá sady SDK platformy v ide sady Visual Studio. | Ano | Pokud přetáhnete [!INCLUDE[win8](../debugger/includes/win8_md.md)] sdk nebo Windows Phone SDK v určitém umístění s určitým rozložením, sada SDK je automaticky integrována se všemi funkcemi sady Visual Studio. | Ne | |
| Mechanismus podporuje čistý vývojářský počítač. (To znamená, že není vyžadována žádná instalace a jednoduché načítání ze správy zdrojového kódu bude fungovat.) | Ne | Vzhledem k tomu, že odkazujete na sdk, je nutné zkontrolovat řešení a sadu SDK samostatně. Sada SDK můžete rezervovat ze dvou výchozích umístění mimo registr, ze kterých sada MSBuild iterates SDK (podrobnosti naleznete v [tématu Vytvoření sady Software Development Kit](../extensibility/creating-a-software-development-kit.md)). Alternativně, pokud vlastní umístění se skládá z sad SDK, můžete zadat následující kód v souboru projektu:<br /><br />`<PropertyGroup>`<br />&nbsp;&nbsp;`<SDKReferenceDirectoryRoot>`<br />&nbsp;&nbsp;`C:\MySDKs`<br />&nbsp;&nbsp;`</SDKReferenceDirectoryRoot>`<br />`</PropertyGroup>`<br /><br /> Potom zkontrolujte sady SDK do tohoto umístění. | Ano | Můžete rezervovat řešení a Visual Studio okamžitě rozpozná a funguje na soubory. |
| Můžete se připojit k velké existující komunitě autorů balíčků. | Není dostupné. | Komunita je nová. | Ano | |
| Můžete se připojit k velké existující komunitě zákazníků balíčků. | Není dostupné. | Komunita je nová. | Ano | |
| Můžete se připojit k ekosystému partnerů (vlastní galerie, repozitáře a tak dále). | Není dostupné. | Mezi dostupná úložiště patří Visual Studio Marketplace, Microsoft Download Center a [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. | Ano | |
| Mechanismus se integruje se servery sestavení průběžné integrace pro vytváření balíčků i spotřebu. | Ano | Sada SDK musí předat umístění se změnami (vlastnost SDKReferenceDirectoryRoot) na příkazovém řádku službě MSBuild. | Ano | |
| Mechanismus podporuje stabilní i předběžné verze balíčků. | Ano | Sada SDK podporuje přidávání odkazů na více verzí. | Ano | |
| Mechanismus podporuje automatickou aktualizaci nainstalovaných balíčků. | Ano | Pokud je dodáván jako VSIX nebo část automatické aktualizace Sady Visual Studio, Sada SDK poskytuje automatická oznámení. | Ano | |
| Mechanismus obsahuje samostatný soubor *EXE* pro vytváření a využívání balíčků. | Ano | Sada SDK obsahuje *soubor MSBuild.exe*. | Ano | |
| Balíčky lze zkontrolovat do správy verzí. | Ano | Nelze vrácení se změnami nic mimo uzel Dokumenty, což znamená, že sady SDK rozšíření nemusí být vráceny se změnami. Velikost sady Extension SDK může být velká. | Ano | |
| K vytváření a využívání balíčků můžete použít rozhraní prostředí PowerShell. | Y (spotřeba), N (tvorba) | Žádné nástroje pro vytvoření sady SDK. Spotřeba je provádění MSBuild na příkazovém řádku. | Ano | |
| Pro podporu ladění můžete použít balíček Symbol. | Ano | Pokud soubory *PDB* přetáhnete do sady SDK, budou automaticky zachyceny. | Ano | |
| Mechanismus podporuje automatické aktualizace správce balíčků. | Není dostupné. | Sada SDK získá revidována s MSBuild. | Ano | |
| Mechanismus podporuje zjednodušený formát manifestu. | Ano | *Soubor SDKManifest.xml* podporuje mnoho atributů, ale obvykle je nutná malá podmnožina. | Ano | |
| Mechanismus je k dispozici pro všechny edice sady Visual Studio. | Ano | Sada SDK podporuje všechny edice sady Visual Studio. | Ano | NuGet podporuje všechny edice sady Visual Studio. |

## <a name="see-also"></a>Viz také

- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)
- [Správa referencí v projektu (Visual Studio pro Mac)](/visualstudio/mac/managing-references-in-a-project)
