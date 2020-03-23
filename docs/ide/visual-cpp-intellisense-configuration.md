---
title: Konfigurace projektu C++ pro IntelliSense
ms.date: 10/08/2018
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 8c43c48a797619f86f81e219e31ccf2afab5ba87
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279310"
---
# <a name="configure-a-c-project-for-intellisense"></a>Konfigurace projektu C++ pro IntelliSense

V některých případech může být nutné ručně nakonfigurovat projekt jazyka C++, aby technologie IntelliSense fungovala správně. U projektů MSBuild (založených na souborech .vcxproj) můžete upravit nastavení ve vlastnostech projektu. U projektů, které nejsou součástí msbuild, upravíte nastavení v souboru CppProperties.json v kořenovém adresáři projektu. V některých případech může být nutné vytvořit soubor nápovědy, který pomůže systému IntelliSense porozumět definicím maker. IDE sady Visual Studio vám pomůže identifikovat a opravit problémy technologie IntelliSense.

## <a name="single-file-intellisense"></a>Technologie IntelliSense s jedním souborem

Když otevřete soubor, který není součástí projektu, Visual Studio poskytuje některé intelliSense podporu, ale ve výchozím nastavení žádné chyby vlnovky jsou zobrazeny. Pokud **navigační panel** říká *různé soubory*, pak to pravděpodobně vysvětluje, proč se nezobrazují chyby vlnovky pod nesprávným kódem, nebo proč není definováno makro preprocesoru.

## <a name="check-the-error-list"></a>Kontrola seznamu chyb

Pokud soubor není otevřen v režimu jednoho souboru a technologie IntelliSense nefunguje správně, je prvním místem kontroly okno Seznam chyb. Pokud chcete zobrazit všechny chyby Technologie IntelliSense pro aktuální zdrojový soubor spolu se všemi zahrnutými soubory hlaviček, zvolte **Build + IntelliSense** v rozevíracím seznamu:

![Technologie VC++ IntelliSense v seznamu chyb](media/vcpp-intellisense-error-list.png)

Technologie IntelliSense vytváří maximálně 1000 chyb. Pokud existuje více než 1000 chyb v hlavičkových souborech zahrnutých ve zdrojovém souboru, pak zdrojový soubor zobrazuje pouze jednu chybovou vlnovku na samém začátku zdrojového souboru.

## <a name="ensure-include-paths-are-correct"></a>Ujistěte se, že #include cesty jsou správné

### <a name="msbuild-projects"></a>Projekty MSBuild

Pokud spustíte sestavení mimo prostředí IDE sady Visual Studio a sestavení jsou úspěšná, ale technologie IntelliSense je nesprávná, je možné, že váš příkazový řádek není synchronizován s nastavením projektu pro jednu nebo více konfigurací. Klikněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a ujistěte se, že všechny **#include** cesty jsou správné pro aktuální konfiguraci a platformu. Pokud jsou cesty identické ve všech konfiguracích a platformách, můžete vybrat **všechny konfigurace** a všechny **platformy** a potom ověřit, zda jsou cesty správné.

![VC++ zahrnout adresáře](media/vcpp-intellisense-include-paths.png)

Chcete-li zobrazit aktuální hodnoty maker sestavení, například **VC_IncludePath**, vyberte řádek Zahrnout adresáře a klepněte na rozevírací seznam vpravo. Pak ** \<** zvolte Upravit>a klikněte na tlačítko **Makra.**

### <a name="makefile-projects"></a>Projekty makefile

U projektů Makefile, které jsou založeny na šabloně projektu NMake, zvolte **NMake** v levém podokně a pak v kategorii **IntelliSense** zvolte **Zahrnout cestu hledání:**

![Projekt makefile zahrnuje cesty](media/vcpp-intellisense-makefile-include-paths.png)

### <a name="open-folder-projects"></a>Projekty Otevřít složku

Pro projekty CMake se ujistěte, že #include cesty jsou zadány správně pro všechny konfigurace v CMakeLists.txt. Jiné typy projektů mohou vyžadovat soubor CppProperties.json. Další informace naleznete [v tématu Konfigurace technologie IntelliSense pomocí souboru CppProperties.json](/cpp/build/open-folder-projects-cpp#configure-code-navigation-with-cpppropertiesjson). Ujistěte se, že cesty jsou správné pro každou konfiguraci, která je definována v souboru.

Pokud je v souboru CppProperties.json chyba syntaxe, technologie IntelliSense v ohrožených souborech bude nesprávná. Visual Studio zobrazí chybu v okně výstup.

## <a name="tag-parser-issues"></a>Problémy s analyzátorem značek

Analyzátor značek je "fuzzy" Analyzátor Jazyka C++, který se používá pro procházení a navigaci. Je velmi rychlý, ale nepokouší se zcela pochopit každý konstrukt kódu.

Například nevyhodnocuje makra preprocesoru, a proto může nesprávně analyzovat kód, který je velmi využívá. Když analyzátor značek narazí na neznámý kód konstrukce, může přeskočit celou oblast kódu.

Existují dva běžné způsoby, ve kterém se tento problém projevuje v sadě Visual Studio:

1. Pokud navigační panel zobrazuje nejvnitřnější makro, byla aktuální definice funkce přeskočena:

   ![Analyzátor tagů přeskočí definici funkce](media/vcpp-intellisense-tag-parser-macro.png)

1. IDE nabízí k vytvoření definice funkce, která je již definována:

   ![Analyzátor tagů nabízí definování existující funkce](media/vcpp-intellisense-tag-parser-function.png)

Chcete-li tyto druhy problémů vyřešit, přidejte do kořenového adresáře řešení soubor s názvem **cpp.hint.** Další informace naleznete v tématu [Soubory nápovědy](/cpp/build/reference/hint-files).

Chyby analyzátoru značek se zobrazí v okně **Seznam chyb.**

## <a name="validate-project-settings-with-diagnostic-logging"></a>Ověření nastavení projektu pomocí protokolování diagnostiky

Chcete-li zkontrolovat, zda kompilátor IntelliSense používá správné možnosti kompilátoru, včetně maker Zahrnout cesty a Preprocesor, zapněte diagnostické protokolování příkazů IntelliSense v **nástrojích > možnostech > textového editoru > C/C++ > rozšířené > diagnostické protokolování**. Nastavte **povolit protokolování** na hodnotu True, **úroveň protokolování** na 5 (nejpodrobnější) a **filtr protokolování** na hodnotu 8 (protokolování technologie IntelliSense).

Ve výstupním okně se nyní zobrazí příkazové řádky, které jsou předány kompilátoru IntelliSense. Zde je ukázkový výstup:

```output
[IntelliSense] Configuration Name: Debug|Win32
[IntelliSense] Toolset IntelliSense Identifier:
[IntelliSense] command line options:
/c
/I.
/IC:\Repo\Includes
/DWIN32
/DDEBUG
/D_DEBUG
/Zc:wchar_t-
/Zc:forScope
/Yustdafx.h
```

Tyto informace vám mohou pomoci pochopit, proč technologie IntelliSense poskytuje nepřesné informace. Například pokud adresář Include projektu obsahuje **$(MyVariable)\Include**a diagnostický protokol zobrazuje **/I\Zahrnout** jako cestu zahrnout, znamená to, že **$(MyVariable)** nebyla vyhodnocena a byla odebrána z cesty konečné zahrnutí.

## <a name="about-the-intellisense-build"></a>O sestavení Technologie IntelliSense

Visual Studio používá vyhrazený kompilátor Jazyka C++ k vytvoření a údržbě databáze, která pohání všechny funkce Technologie IntelliSense. Aby byla databáze IntelliSense synchronizována s kódem, aplikace Visual Studio automaticky spustí sestavení pouze technologie IntelliSense jako úlohy na pozadí v reakci na určité změny provedené v nastavení projektu nebo zdrojových souborech.

V některých případech však visual studio nemusí aktualizovat databázi IntelliSense včas. Například při spuštění **příkazu git pull** nebo **git checkout** může visual studio trvat až hodinu, než zjistí změny v souborech. Opětovné prohledání všech souborů v řešení můžete vynutit kliknutím pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a výběrem **možnosti Znovu prohledávat řešení**.

## <a name="troubleshooting-intellisense-build-failures"></a>Poradce při potížích s chybami sestavení technologie IntelliSense

Sestavení technologie IntelliSense nevytváří binární soubory, ale může stále selhat. Jednou z možných příčin selhání jsou soubory .props nebo .targets. Ve Visual Studiu 2017 verze 15.6 a novější, inkapomuje se chyby sestavení pouze technologie IntelliSense do okna Výstup. Chcete-li je zobrazit, nastavte **zobrazit výstup z** **řešení**:

![Výstupní okno pro chyby řešení](media/vcpp-intellisense-output-window.png)

Chybová zpráva vás může povolit trasování v době návrhu:

```output
error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
configuration 'Debug|x64'. IntelliSense might be unavailable.
Set environment variable TRACEDESIGNTIME=true and restart
Visual Studio to investigate.
```

Pokud nastavíte proměnnou prostředí TRACEDESIGNTIME na hodnotu true a restartujete sadu Visual Studio, zobrazí se v adresáři %TEMP%soubor protokolu, který může pomoci diagnostikovat selhání sestavení.

Další informace o proměnné prostředí TRACEDESIGNTIME naleznete v tématu [Roslyn](https://github.com/dotnet/roslyn/wiki/Diagnosing-Project-System-Build-Errors) a [Common Project System](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Informace v těchto článcích jsou relevantní pro projekty jazyka C++.

## <a name="see-also"></a>Viz také

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
