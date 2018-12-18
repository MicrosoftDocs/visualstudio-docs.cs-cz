---
title: Konfigurace projektu C++ pro IntelliSense
ms.date: 10/08/2018
ms.technology: vs-ide-general
ms.topic: conceptual
author: mblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 3772c2c910188aacb675f267d20f5e0f16565001
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836636"
---
# <a name="configure-a-c-project-for-intellisense"></a>Konfigurace projektu C++ pro IntelliSense

V některých případech můžete potřebovat ručně konfigurovat projektu v jazyce C++ k získání funkce IntelliSense funguje správně. Pro projekty MSBuild (podle souborů .vcxproj) můžete upravit nastavení ve vlastnostech projektu. Pro projekty bez MSBuild upravte nastavení v souboru CppProperties.json v kořenovém adresáři projektu. V některých případech budete muset vytvořit pomocný parametr souboru, který usnadní pochopení definic – makro technologie IntelliSense. Integrované vývojové prostředí sady Visual Studio pomáhá identifikovat a opravit problémy technologie IntelliSense.



## <a name="single-file-intellisense"></a>IntelliSense s jedním souborem

Při otevření souboru, který není zahrnutý v projektu sady Visual Studio poskytuje podporu technologie IntelliSense, ale ve výchozím nastavení jsou uvedeny žádné podtržení vlnovkou u chyb. Pokud **navigační panel** říká *různé soubory*, potom to pravděpodobně vysvětluje, proč se nezobrazují podtržení vlnovkou u chyb v rámci nesprávný kód nebo proč preprocesor makro není definované.

## <a name="check-the-error-list"></a>Najdete v seznamu chyb

Pokud soubor není otevřen v režimu jednoho souboru a IntelliSense nepracuje správně, je prvním místem, kde můžete zkontrolovat okna Seznam chyb. Chcete-li zobrazit všechny chyby technologie IntelliSense pro aktuální zdrojový soubor spolu s všechny soubory zahrnuté záhlaví, zvolte **sestavení + IntelliSense** v rozevíracím seznamu:

![VC ++ IntelliSense v seznamu chyb](media/vcpp-intellisense-error-list.png)

Technologie IntelliSense produkuje maximálně 1000 chyby. Pokud existuje více než 1000 chyby v souborech hlaviček, které jsou zahrnuté ve zdrojovém souboru, zdrojový soubor zobrazuje pouze jediné chyby vlnovku na začátku zdrojového souboru.

## <a name="ensure-include-paths-are-correct"></a>Zajištění #include správnost cesty

### <a name="msbuild-projects"></a>Projekty MSBuild

Je-li spustit vaše sestavení mimo rozhraní IDE sady Visual Studio a sestavení jsou úspěšné, ale technologie IntelliSense je nesprávná, je možné, že příkazový řádek je mimo rozsah synchronizace s nastavení projektu pro jednu nebo několik konfigurací. Klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a ujistěte se, že všechny **#include** cesty jsou správné pro aktuální konfiguraci a platformu. Pokud cesty jsou stejné ve všech konfigurací a platforem, můžete si vybrat **všechny konfigurace** a **všechny platformy** a pak ověřte správnost cesty.

![VC ++ adresáře souborů k zahrnutí](media/vcpp-intellisense-include-paths.png)

 Pokud chcete zobrazit aktuální hodnoty pro makra sestavení, jako **VC_IncludePath**, vyberte řádek adresáře souborů k zahrnutí a klikněte na rozevírací nabídku na pravé straně. Klikněte na tlačítko  **\<Upravit >** a klikněte na **makra** tlačítko.

### <a name="makefile-projects"></a>Projekty makefile

Pro projekty souborů pravidel, které jsou založeny na šabloně NMake projektu, zvolte **NMake** v levém podokně a pak zvolte **cesty hledání zahrnutí** pod **IntelliSense** kategorie:

![Cesty zahrnutí projektu souboru pravidel](media/vcpp-intellisense-makefile-include-paths.png)

Další informace najdete v tématu [postupy: povolení technologie IntelliSense pro projekty souborů pravidel](/cpp/ide/how-to-enable-intellisense-for-makefile-projects).

### <a name="open-folder-projects"></a>Otevřete složku projekty

Pro projekty CMake, ujistěte se, že #include cesty jsou správně zadané u všech konfigurací v soubor CMakeLists.txt. Ostatní typy projektů může vyžadovat souboru CppProperties.json. Další informace najdete v tématu [konfigurace technologie IntelliSense s CppProperties.json](/cpp/ide/non-msbuild-projects#cppproperties). Zkontrolujte správnost cesty pro každou konfiguraci, která je definována v souboru.

Pokud je v souboru CppProperties.json chybu syntaxe, IntelliSense v souborech ovlivněné bude nepřesná. Visual Studio se zobrazí chyby v okně výstup.

## <a name="tag-parser-issues"></a>Problémy analyzátoru značky

Analyzátor značek je "přibližné" analyzátor jazyka C++, který se používá k procházení a navigace. Je velmi rychlé zpracování, ale nebude pokoušet o úplně pochopili konstrukci kódu pro každý.

Například nevyhodnocuje makra preprocesoru, a proto ho může správně analyzovat kód, který značně používá z nich. Když analyzátor značek, zaznamená konstrukce neznámého kódu, přeskočte tento kód celé oblasti.

Existují dva běžné způsoby, ve kterých se tyto potíže projeví v sadě Visual Studio:

1. Na navigačním panelu se zobrazí vnitřní – makro, byla přeskočena aktuální definice funkce:

   ![Analyzátor značek přeskočí definice funkce](media/vcpp-intellisense-tag-parser-macro.png)

1. Rozhraní IDE, nabídne vám vytvoření definice funkce pro funkci, která je už definovaný:

   ![Analyzátor značek nabízí k definování stávající – funkce](media/vcpp-intellisense-tag-parser-function.png)

Chcete-li tyto druhy problémů vyřešit, přidejte do ní soubor **cpp.hint** do kořenového adresáře řešení. Další informace najdete v tématu [soubory pokynů](/cpp/ide/hint-files).

**Visual Studio 2017 verze 15.7** chyby analyzátoru značky se zobrazí v okně Seznam chyb.

## <a name="validate-project-settings-with-diagnostic-logging"></a>Ověření nastavení projektu pomocí protokolování diagnostiky

Chcete-li zkontrolovat, zda kompilátor technologie IntelliSense je pomocí možnosti kompilátoru správný, včetně cesty zahrnutí a makra preprocesoru, zapněte diagnostické protokolování z IntelliSense příkazové řádky v **nástroje > Možnosti > textový Editor > C/C++ > Upřesnit > Diagnostické protokolování**. Nastavte **povolit protokolování** na hodnotu True, **úrovně protokolování** do 5 (nejpodrobnější), a **protokolování filtru** 8 (protokolování technologie IntelliSense).

V okně Výstup se teď zobrazí příkazové řádky, které jsou předány kompilátoru technologie IntelliSense. Tady je ukázkový výstup:

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

Tyto informace vám můžou pomoct porozumět proč poskytuje nepřesné informace technologie IntelliSense. Pokud adresář vkládaných váš projekt obsahuje třeba **$(MyVariable) \Include**a zobrazí se protokol diagnostiky **/I\Include** jako cestu k zahrnutí, znamená to, že **$(MyVariable)** nebyl vyhodnocen a byl odebrán z konečné cesty vložených souborů.

## <a name="about-the-intellisense-build"></a>Informace o sestavení technologie IntelliSense

Visual Studio používá vyhrazené kompilátor C++ k vytváření a údržbě databáze, které využívá všechny funkce technologie IntelliSense. Pro synchronizaci databáze IntelliSense s kódem, Visual Studio automaticky spustí sestavení jenom IntelliSense jako úlohy na pozadí v reakci na určité změny v nastavení projektu nebo zdrojové soubory.

Nicméně v některých případech nemusí sady Visual Studio aktualizace databáze IntelliSense včas. Například při spuštění **o přijetí změn git** nebo **git checkout** příkazu, Visual Studio může trvat až hodinu zjišťovat změny v souborech. Můžete vynutit opětovné prohledání všech souborů v řešení kliknutím pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a zvolíte **znovu prohledat řešení**.

## <a name="troubleshooting-intellisense-build-failures"></a>Řešení potíží se selháním sestavení technologie IntelliSense

Výsledkem sestavování technologie IntelliSense není binární soubory, ale stále může selhat. Jednou z možných příčin selhání je vlastní .props nebo .targets souborů. V sadě Visual Studio 2017 verze 15.6 pouze technologie IntelliSense sestavení chyby se Zaprotokolují v okně výstup. Chcete-li zobrazit, nastavte **zobrazit výstup z:** k **řešení**:

![Řešení chyb v okně Výstup](media/vcpp-intellisense-output-window.png)

Chybová zpráva může dát pokyn k povolení trasování návrhu:

```output
 error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
 configuration 'Debug|x64'. IntelliSense might be unavailable.
 Set environment variable TRACEDESIGNTIME=true and restart
 Visual Studio to investigate.
```

Pokud jste nastavili proměnnou prostředí TRACEDESIGNTIME na hodnotu true a restartujte aplikaci Visual Studio, zobrazí se soubor protokolu v adresáři % TEMP %, která vám může pomoci diagnostikovat selhání sestavení.

Další informace o proměnnou prostředí TRACEDESIGNTIME najdete v tématu [Roslyn](https://github.com/dotnet/roslyn/wiki/Diagnosing-Project-System-Build-Errors) a [Common Project System](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Informace v těchto článcích jsou relevantní pro projekty C++.

## <a name="see-also"></a>Viz také

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
