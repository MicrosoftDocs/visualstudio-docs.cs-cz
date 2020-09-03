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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77279310"
---
# <a name="configure-a-c-project-for-intellisense"></a>Konfigurace projektu C++ pro IntelliSense

V některých případech může být nutné ručně nakonfigurovat projekt C++ pro správné fungování technologie IntelliSense. Pro projekty MSBuild (na základě souborů. vcxproj) můžete upravit nastavení ve vlastnostech projektu. Pro projekty jiné než MSBuild upravíte nastavení v CppProperties.jssouboru v kořenovém adresáři projektu. V některých případech může být nutné vytvořit soubor pokynů, který IntelliSense pomůže pochopit definice maker. Integrované vývojové prostředí sady Visual Studio vám pomůže identifikovat a opravit problémy IntelliSense.

## <a name="single-file-intellisense"></a>IntelliSense s jedním souborem

Když otevřete soubor, který není zahrnutý v projektu, Visual Studio poskytuje podporu technologie IntelliSense, ale ve výchozím nastavení se nezobrazují žádné chybové vlnovky. Pokud **navigační panel** říká *různé soubory*, pak to pravděpodobně vysvětlí, proč se nezobrazuje Vlnová chyba v nesprávném kódu, nebo proč není definováno makro preprocesoru.

## <a name="check-the-error-list"></a>Podívejte se na Seznam chyb

Pokud soubor není otevřen v režimu s jedním souborem a technologie IntelliSense nepracuje správně, první místo, kde se má kontrolovat, je Seznam chyb okno. Chcete-li zobrazit všechny chyby technologie IntelliSense pro aktuální zdrojový soubor společně se všemi zahrnutými hlavičkými soubory, v rozevíracím seznamu vyberte možnost **sestavení + IntelliSense** :

![VC + + IntelliSense v Seznam chyb](media/vcpp-intellisense-error-list.png)

Technologie IntelliSense generuje maximálně 1000 chyb. Pokud v hlavičkových souborech obsažených ve zdrojovém souboru dojde k více než 1000 chybám, pak zdrojový soubor zobrazí jenom jednu chybu vlnovkou na začátku ve zdrojovém souboru.

## <a name="ensure-include-paths-are-correct"></a>Ujistěte se, že jsou cesty #include správné.

### <a name="msbuild-projects"></a>Projekty MSBuild

Pokud spustíte vaše sestavení mimo prostředí Visual Studio IDE a vaše sestavení jsou úspěšná, ale technologie IntelliSense není správná, je možné, že se příkazový řádek nesynchronizuje s nastavením projektu pro jednu nebo více konfigurací. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a ujistěte se, že všechny cesty **#include** jsou správné pro aktuální konfiguraci a platformu. Pokud jsou cesty identické ve všech konfiguracích a platformách, můžete vybrat **všechny konfigurace** a **všechny platformy** a pak ověřit, jestli jsou cesty správné.

![Adresáře zahrnutí VC + +](media/vcpp-intellisense-include-paths.png)

Chcete-li zobrazit aktuální hodnoty pro makra sestavení, například **VC_IncludePath**, vyberte řádek zahrnout adresáře a klikněte na rozevírací seznam na pravé straně. Pak zvolte **\<Edit>** a klikněte na tlačítko **makra** .

### <a name="makefile-projects"></a>Projekty makefile

Pro projekty makefile, které jsou založeny na šabloně projektu NMake, zvolte v levém podokně možnost **NMAKE** a v kategorii **IntelliSense** zvolte možnost **zahrnout cestu pro vyhledávání** :

![Projekt makefile obsahuje cesty](media/vcpp-intellisense-makefile-include-paths.png)

### <a name="open-folder-projects"></a>Projekty Otevřít složku

V případě projektů CMake se ujistěte, že jsou #include cesty správně zadány pro všechny konfigurace v CMakeLists.txt. Jiné typy projektů mohou vyžadovat CppProperties.jsv souboru. Další informace najdete v tématu [Konfigurace technologie IntelliSense s CppProperties.jsna](/cpp/build/open-folder-projects-cpp#configure-code-navigation-with-cpppropertiesjson). Ujistěte se, že cesty jsou správné pro každou konfiguraci, která je definována v souboru.

Pokud dojde k chybě syntaxe v CppProperties.jssouboru, IntelliSense v ovlivněných souborech bude nesprávný. V aplikaci Visual Studio se zobrazí chyba v okno Výstup.

## <a name="tag-parser-issues"></a>Problémy analyzátoru značek

Analyzátor značek je "nepřibližný" analyzátor C++, který se používá pro procházení a navigaci. Je velmi rychlé, ale nepokouší se úplně pochopit každou konstrukci kódu.

Například nevyhodnotí makra preprocesoru, a proto může nesprávně analyzovat kód, který je pro něj těžké použít. Když analyzátor značek narazí na neznámou konstrukci kódu, může přeskočit tuto celou oblast kódu.

Existují dva běžné způsoby, jak tyto problémy manifestují v aplikaci Visual Studio:

1. Pokud navigační panel zobrazuje nejvnitřnější makro, aktuální definice funkce byla vynechána:

   ![Analyzátor značek přeskočí definici funkce.](media/vcpp-intellisense-tag-parser-macro.png)

1. Rozhraní IDE nabízí vytvoření definice funkce pro funkci, která je již definována:

   ![Nabídky analyzátoru značek pro definování existující funkce](media/vcpp-intellisense-tag-parser-function.png)

Chcete-li opravit tyto druhy problémů, přidejte soubor s názvem **cpp. Hint** do kořenové složky adresáře řešení. Další informace najdete v tématu [soubory pokynů](/cpp/build/reference/hint-files).

V okně **Seznam chyb** se zobrazí chyby analyzátoru značek.

## <a name="validate-project-settings-with-diagnostic-logging"></a>Ověření nastavení projektu pomocí diagnostického protokolování

Chcete-li ověřit, zda kompilátor technologie IntelliSense používá správné možnosti kompilátoru, včetně zahrnutí cest a makra preprocesoru, zapněte diagnostické protokolování příkazového řádku technologie IntelliSense v **nástrojích > možnosti > textový Editor > C/C++ > rozšířené > diagnostické protokolování**. Nastavte **Povolit protokolování** na hodnotu true, **úroveň protokolování** na 5 (nejvíc verbose) a **Filtr protokolování** na 8 (protokolování IntelliSense).

Okno Výstup nyní zobrazí příkazové řádky, které jsou předány kompilátoru technologie IntelliSense. Zde je ukázkový výstup:

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

Tyto informace vám pomohou pochopit, proč technologie IntelliSense poskytuje nepřesné informace. Například Pokud adresář include vašeho projektu obsahuje **$ (MojePromenna) \Include**a diagnostický protokol ukazuje **/I\Include** jako cestu include, znamená to, že **$ (MojePromenna)** se nevyhodnotila a byla odebrána z poslední cesty include.

## <a name="about-the-intellisense-build"></a>O sestavení IntelliSense

Visual Studio používá vyhrazený kompilátor C++ k vytvoření a údržbě databáze, která je základem všech funkcí technologie IntelliSense. Aby byla databáze IntelliSense stále synchronizovaná s kódem, Visual Studio automaticky spouští pouze IntelliSense sestavení jako úlohy na pozadí v reakci na určité změny provedené v nastavení projektu nebo ve zdrojových souborech.

V některých případech ale Visual Studio nemusí databázi IntelliSense včas aktualizovat. Pokud například spustíte příkaz **Git Pull** nebo **Git** Replaced, může Visual Studio trvat až hodinu, než zjistí změny v souborech. Opětovnou kontrolu všech souborů v řešení můžete vynutit tak, že kliknete pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a zvolíte možnost **znovu prohledat řešení**.

## <a name="troubleshooting-intellisense-build-failures"></a>Řešení potíží při vytváření sestavení IntelliSense

Sestavení technologie IntelliSense nevytváří binární soubory, ale přesto může selhat. Jednou z možných příčin selhání jsou vlastní soubory. props nebo. targets. V aplikaci Visual Studio 2017 verze 15,6 a novější jsou chyby sestavení pouze technologie IntelliSense protokolovány do okna výstup. Pokud je chcete zobrazit, nastavte **Zobrazit výstup z** do **řešení**:

![Okno výstup pro chyby řešení](media/vcpp-intellisense-output-window.png)

Chybová zpráva vám může dát pokyn k povolení trasování v době návrhu:

```output
error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
configuration 'Debug|x64'. IntelliSense might be unavailable.
Set environment variable TRACEDESIGNTIME=true and restart
Visual Studio to investigate.
```

Pokud nastavíte proměnnou prostředí TRACEDESIGNTIME na hodnotu true a restartujete sadu Visual Studio, zobrazí se soubor protokolu v adresáři% TEMP%, který může vést k diagnostice selhání sestavení.

Další informace o proměnné prostředí TRACEDESIGNTIME naleznete v tématu [Roslyn](https://github.com/dotnet/roslyn/wiki/Diagnosing-Project-System-Build-Errors) a [Common Project System](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Informace v těchto článcích jsou relevantní pro projekty v jazyce C++.

## <a name="see-also"></a>Viz také

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
