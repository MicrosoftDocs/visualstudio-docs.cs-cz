---
title: Správa aplikačních projektů Pythonu
description: Projekty v sadě Visual Studio spravují závislosti mezi soubory a složitost vztahů v aplikaci.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d50cbfbd517073544ebd172627d24bd7c3878fa5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302810"
---
# <a name="python-projects-in-visual-studio"></a>Projekty Pythonu v sadě Visual Studio

Aplikace Pythonu jsou obvykle definovány pouze pomocí složek a souborů, ale tato struktura se může stát složitým, protože aplikace se zvětšují a možná zahrnují automaticky generované soubory, JavaScript pro webové aplikace a tak dále. Projekt sady Visual Studio pomáhá spravovat tuto složitost. Projekt (soubor *Pyproj)* identifikuje všechny zdrojové a obsahové soubory přidružené k projektu, obsahuje informace o sestavení pro každý soubor, udržuje informace pro integraci se systémy správy zdrojového kódu a pomáhá uspořádat aplikaci do logických součástí.

![Projekt Pythonu v Průzkumníku řešení](media/projects-solution-explorer.png)

Kromě toho projekty jsou vždy spravovány v rámci *řešení*sady Visual Studio , které mohou obsahovat libovolný počet projektů, které mohou odkazovat na sebe. Například projekt Pythonu může odkazovat na projekt Jazyka C++, který implementuje rozšiřující modul. V tomto vztahu Visual Studio automaticky vytvoří projekt Jazyka C++ (v případě potřeby) při spuštění ladění projektu Pythonu. (Obecné informace naleznete v tématu [Řešení a projekty v sadě Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).)

Visual Studio poskytuje celou řadu šablon projektů Pythonu pro rychlé nastavení řady aplikačních struktur, včetně šablony pro vytvoření projektu z existujícího stromu složek a šablony pro vytvoření čistého a prázdného projektu. Viz [Šablony projektů](#project-templates) pro index.

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019 podporuje otevření složky obsahující kód Pythonu a spuštění tohoto kódu bez vytváření souborů projektu a řešení sady Visual Studio. Další informace naleznete v [tématu Úvodní příručka: Otevření a spuštění kódu Pythonu ve složce](quickstart-05-python-visual-studio-open-folder.md). Použití souboru projektu však přináší výhody, jak je vysvětleno v této části.
::: moniker-end

> [!Tip]
> Bez projektu všechny verze Visual Studia dobře fungují s kódem Pythonu. Můžete například otevřít soubor Pythonu sám a vychutnat si automatické dokončování, Technologie IntelliSense a ladění (kliknutím pravým tlačítkem myši v editoru a výběrem **možnosti Začít s laděním).** Vzhledem k tomu, že takový kód vždy používá výchozí globální prostředí, může se však zobrazit nesprávné dokončení nebo chyby, pokud je kód určen pro jiné prostředí. Kromě toho Visual Studio analyzuje všechny soubory a balíčky ve složce, ze které je otevřen jeden soubor, což může spotřebovat značné množství času procesoru.
>
> Je to jednoduchá záležitost vytvořit projekt sady Visual Studio z existujícího kódu, jak je popsáno v [vytvořit projekt z existujících souborů](#create-project-from-existing-files).

|   |   |
|---|---|
| ![ikona filmové kamery pro video](../install/media/video-icon.png "Podívejte se na video") | [Podrobné informace: Používejte sjazykistiku zdrojového kódu s projekty Pythonu](https://youtu.be/Aq8eqApnugM) (youtube.com, 8m 55s). |

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Přidání souborů, přiřazení spouštěcího souboru a nastavení prostředí

Při vývoji aplikace je obvykle nutné přidat do projektu nové soubory různých typů. Přidání těchto souborů se provádí klepnutím pravým tlačítkem myši na projekt a výběrem možnosti **Přidat** > **existující položku,** se kterou procházíte souborem, který chcete přidat, nebo **přidat** > **novou položku**, která vyvolá dialog s různými šablonami položek. Jak je popsáno v odkazu na [šablony položek,](python-item-templates.md) možnosti zahrnují prázdné soubory Pythonu, třídu Pythonu, test částí a různé soubory související s webovými aplikacemi. Tyto možnosti můžete prozkoumat pomocí testovacího projektu a zjistit, co je k dispozici ve vaší verzi sady Visual Studio.

Každý projekt Pythonu má jeden přiřazený soubor se spuštěním, který je zobrazen tučným písmem v **Průzkumníku řešení**. Spouštěcí soubor je soubor, který je spuštěn při spuštění ladění **(F5** nebo **Ladění** > **Start Ladění**) nebo při spuštění projektu v **interaktivním** okně (**Shift**+**Alt**+**F5** nebo **Debug** > Execute Project v**Pythonu Interactive**). Chcete-li jej změnit, klepněte pravým tlačítkem myši na nový soubor a vyberte možnost **Nastavit jako položku po spuštění** (nebo Nastavit jako spouštěcí **soubor** ve starších verzích sady Visual Studio).

> [!Tip]
> Pokud odeberete vybraný spouštěcí soubor z projektu a nevyberete nový, Visual Studio neví, s jakým souborem Pythonu začít při pokusu o spuštění projektu. V tomto případě Visual Studio 2017 verze 15.6 a novější ukazuje chybu; starší verze buď otevřít výstupní okno s interpretem Pythonu běží, nebo se zobrazí výstupní okno, ale pak zmizí téměř okamžitě. Pokud narazíte na některé z těchto chování, zkontrolujte, zda máte přiřazený spouštěcí soubor.
>
> Pokud chcete z nějakého důvodu ponechat výstupní okno otevřené, klikněte pravým tlačítkem myši `-i` na projekt, vyberte příkaz **Vlastnosti**, vyberte kartu **Ladění** a přidejte ji do pole **Argumenty interpretu.** Tento argument způsobí, že interpret přejde do interaktivního režimu po dokončení programu, čímž se okno ponechá otevřené, dokud nezadáte **klávesu Ctrl**+**Z** > **Enter.**

::: moniker range="vs-2017"
Nový projekt je vždy spojen s výchozím globálním prostředím Pythonu. Chcete-li projekt přidružit k jinému prostředí (včetně virtuálních prostředí), klikněte pravým tlačítkem myši na uzel **Prostředí Pythonu** v projektu, vyberte **přidat nebo odebrat prostředí Pythonu**a vyberte ty, které chcete.
::: moniker-end
::: moniker range=">=vs-2019"
Nový projekt je vždy spojen s výchozím globálním prostředím Pythonu. Chcete-li projekt přidružit k jinému prostředí (včetně virtuálních prostředí), klepněte pravým tlačítkem myši na uzel **Prostředí Pythonu** v projektu, vyberte **přidat prostředí..** a vyberte požadované prostředí. Můžete také použít ovládací prvek rozevíracího kódu prostředí na panelu nástrojů k výběru a prostředí nebo přidat další do projektu.

![Příkaz Přidat prostředí na panelu nástrojů Pythonu](media/environments/environments-toolbar-2019.png)
::: moniker-end

Chcete-li změnit aktivní prostředí, klepněte pravým tlačítkem myši na požadované prostředí v **Průzkumníku řešení** a vyberte **možnost Aktivovat prostředí,** jak je znázorněno níže. Další informace naleznete v [tématu Výběr prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

![Aktivace prostředí pro projekt Pythonu](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Šablony projektů

Visual Studio nabízí řadu způsobů, jak nastavit projekt Pythonu, od začátku nebo z existujícího kódu. Chcete-li použít šablonu, vyberte příkaz Nabídka**Nový projekt** **nebo** > **New** > klepněte pravým tlačítkem myši na řešení v **Průzkumníku řešení** a vyberte **Přidat** > nový**projekt**, které obě zobrazí dialogové okno Nový **projekt** níže. Chcete-li zobrazit šablony specifické pro Python, vyhledejte buď "Python", nebo vyberte **nainstalovaný** > uzel**Pythonu:**

![Dialogové okno Nový projekt se šablonami Pythonu](media/projects-new-project-dialog.png)

Následující tabulka shrnuje šablony dostupné v Sadě Visual Studio 2017 a novějších (ne všechny šablony jsou dostupné ve všech předchozích verzích):

| Šablona | Popis |
| --- | --- |
| [**Z existujícího kódu Pythonu**](#create-project-from-existing-files) | Vytvoří projekt sady Visual Studio z existujícího kódu Pythonu ve struktuře složek.  |
| **Aplikace Python** | Základní struktura projektu pro novou aplikaci Pythonu s jedním prázdným zdrojovým souborem. Ve výchozím nastavení je projekt spuštěn v interpretu konzoly výchozího globálního prostředí, které můžete změnit [přiřazením jiného prostředí](selecting-a-python-environment-for-a-project.md). |
| [**Cloudová služba Azure**](python-azure-cloud-service-project-template.md) | Projekt pro cloudovou službu Azure napsaný v Pythonu. |
| [**Webové projekty**](python-web-application-project-templates.md) | Projekty pro webové aplikace založené na různých architekturách, včetně Bottle, Django a Flask. |
| **Aplikace IronPython** | Podobně jako šablona aplikace Python, ale ve výchozím nastavení používá IronPython, který umožňuje interop rozhraní .NET a ladění ve smíšeném režimu s jazyky .NET. |
| **Aplikace Ironpython WPF** | Struktura projektu pomocí IronPython s Windows Presentation Foundation XAML soubory pro uživatelské rozhraní aplikace. Visual Studio poskytuje návrháře uživatelského prostředí XAML, kód na pozadí lze zapsat v Pythonu a aplikace běží bez zobrazení konzoly. |
| **Webová stránka IronPython Silverlight** | Projekt IronPython, který běží v prohlížeči pomocí Silverlight. Kód Pythonu aplikace je součástí webové stránky jako skript. Značka často používaný skript stáhne některé JavaScript kód, který inicializuje IronPython běží uvnitř Silverlight, ze kterého váš kód Pythonu můžete komunikovat s DOM. |
| **Aplikace Ironpython Windows Forms** | Struktura projektu pomocí IronPython s uI vytvořené pomocí kódu s Windows Forms. Aplikace běží bez zobrazení konzoly. |
| **Aplikace na pozadí (IoT)** | Podporuje nasazení projektů Pythonu ke spuštění jako služby na pozadí na zařízeních. Další informace najdete v [Centru pro Windows IoT Dev Center.](https://dev.windows.com/en-us/iot) |
| **Modul rozšíření Pythonu** | Tato šablona se zobrazí v části Visual C++, pokud jste nainstalovali **nativní vývojové nástroje Pythonu** s úlohami Pythonu v Sadě Visual Studio 2017 nebo novějším (viz [Instalace).](installing-python-support-in-visual-studio.md) Poskytuje základní strukturu pro dll rozšíření C++, podobně jako to, co je popsáno na [vytvořit rozšíření C++ pro Python](working-with-c-cpp-python-in-visual-studio.md). |

> [!Note]
> Vzhledem k tomu, že Python je interpretovaný jazyk, projekty Pythonu v sadě Visual Studio nevytvářejí samostatný spustitelný soubor jako ostatní kompilované jazykové projekty (například C#). Další informace naleznete v [tématu Otázky a odpovědi](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Vytvoření projektu z existujících souborů

> [!Important]
> Zde popsaný proces nepřesouvá ani nekopíruje původní zdrojové soubory. Pokud chcete pracovat s kopií, nejprve ji duplikujte.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Propojené soubory

Propojené soubory jsou soubory, které jsou přeneseny do projektu, ale obvykle jsou umístěny mimo složky projektu aplikace. Zobrazují se v **Průzkumníku řešení** jako normální ![soubory s překrytou ikonou zástupce: Ikona propojeného souboru](media/projects-linked-file-icon.png)

Propojené soubory jsou určeny v souboru `<Compile Include="...">` *.pyproj* pomocí prvku. Propojené soubory jsou implicitní, pokud používají relativní cestu mimo adresářovou strukturu, nebo explicitní, pokud používají cesty v **Průzkumníku řešení**:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Propojené soubory jsou ignorovány za některé z následujících podmínek:

- Propojený soubor obsahuje metadata propojení a cestu zadanou v atributu Zahrnout, který se nachází v adresáři projektu.
- Propojený soubor duplikuje soubor, který existuje v hierarchii projektu.
- Propojený soubor obsahuje metadata propojení a cesta propojení je relativní cesta mimo hierarchii projektu.
- Cesta odkazu je zakořeněna

### <a name="work-with-linked-files"></a>Práce s propojenými soubory

Chcete-li přidat existující položku jako odkaz, klepněte pravým tlačítkem myši na složku v projektu, do které chcete soubor přidat, a pak **vyberte** > přidat**existující položku**. V zobrazeném dialogovém okně vyberte soubor a z rozevíracího okna na tlačítku **Přidat** zvolte **Přidat jako odkaz.** Za předpokladu, že neexistují žádné konfliktní soubory, vytvoří tento příkaz ve vybrané složce odkaz. Odkaz však není přidán, pokud již existuje soubor se stejným názvem nebo odkaz na tento soubor již existuje v projektu.

Pokud se pokusíte vytvořit odkaz na soubor, který již existuje ve složkách projektu, bude přidán jako normální soubor a nikoli jako odkaz. Chcete-li soubor převést na propojení, vyberte **Soubor** > **Uložit jako,** chcete-li soubor uložit do umístění mimo hierarchii projektu. Visual Studio jej automaticky převede na odkaz. Podobně lze odkaz převést zpět pomocí **souboru** > **Uložit jako** uložit soubor někde v hierarchii projektu.

Pokud přesunete propojený soubor v **Průzkumníku řešení**, odkaz se přesune, ale skutečný soubor není ovlivněn. Podobně odstranění odkazu odstraní propojení bez ovlivnění souboru.

Propojené soubory nelze přejmenovat.

## <a name="references"></a>Odkazy

Projekty sady Visual Studio podporují přidávání odkazů na projekty a rozšíření, které se zobrazí pod uzlem **Reference** v **Průzkumníku řešení**:

![Odkazy na rozšíření v projektech Pythonu](media/projects-extension-references.png)

Odkazy na rozšíření obvykle označují závislosti mezi projekty a používají se k poskytování technologie IntelliSense v době návrhu nebo propojení v době kompilace. Projekty Pythonu používají odkazy podobným způsobem, ale vzhledem k dynamické povaze Pythonu se používají především v době návrhu k zajištění vylepšeného technologie IntelliSense. Lze je také použít pro nasazení v Microsoft Azure k instalaci dalších závislostí.

### <a name="extension-modules"></a>Rozšiřující moduly

Odkaz na soubor *.pyd* umožňuje intelliSense pro generovaný modul. Visual Studio načte soubor *Pyd* do interpretu Pythonu a introspektuje jeho typy a funkce. Také se pokusí analyzovat řetězce doc pro funkce poskytnout nápovědu k podpisu.

Pokud kdykoli modul rozšíření je aktualizován na disku, Visual Studio znovu analyzuje modul na pozadí. Tato akce nemá žádný vliv na chování za běhu, ale některé dokončení nejsou k dispozici, dokud není dokončena analýza.

Může být také nutné přidat [cestu hledání](search-paths.md) do složky obsahující modul.

### <a name="net-projects"></a>Projekty .NET

Při práci s IronPython, můžete přidat odkazy na sestavení .NET povolit IntelliSense. U projektů .NET ve vašem řešení klikněte pravým tlačítkem myši na uzel **Reference** v projektu Pythonu, vyberte **Přidat odkaz**, vyberte kartu **Projekty** a přejděte k požadovanému projektu. U knihoven DLL, které jste stáhli samostatně, vyberte místo toho kartu **Procházet** a přejděte na požadovanou knihovnu DLL.

Vzhledem k tomu, že odkazy v `clr.AddReference('<AssemblyName>')` IronPython nejsou k dispozici, `clr.AddReference` dokud volání je provedena, je také nutné přidat odpovídající volání sestavení, obvykle na začátku kódu. Například kód vytvořený šablonou projektu **Aplikace IronPython Windows Forms v** sadě Visual Studio obsahuje dvě volání v horní části souboru:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>Projekty WebPI

Můžete přidat odkazy na položky produktu WebPI pro nasazení do Cloudových služeb Microsoft Azure, kde můžete nainstalovat další součásti prostřednictvím informačního kanálu WebPI. Ve výchozím nastavení je zobrazený informační kanál specifický pro Python a zahrnuje Django, CPython a další základní součásti. Můžete si také vybrat svůj vlastní zdroj, jak je znázorněno níže. Při publikování do Microsoft Azure nainstaluje úloha instalace všechny odkazované produkty.

> [!IMPORTANT]
> Projekty WebPI nejsou dostupné ve Visual Studiu 2017 nebo Visual Studiu 2019.

![Odkazy na webpi](media/projects-webPI-components.png)
