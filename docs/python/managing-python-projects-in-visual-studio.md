---
title: Správa projektů aplikací v Pythonu
description: Projekty v Visual Studio spravují závislosti mezi soubory a složitost relací v aplikaci.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c9a20ea3baee84657e26e2d98bb5726c20ceba9e
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254898"
---
# <a name="python-projects-in-visual-studio"></a>Projekty Pythonu v Visual Studio

Aplikace Pythonu se obvykle definují jenom pomocí složek a souborů, ale tato struktura může být složitá, protože se aplikace zvětšují a možná zahrnují automaticky generované soubory, JavaScript pro webové aplikace atd. Tuto Visual Studio spravuje projekt projektu. Projekt (soubor *.pyproj)* identifikuje všechny zdrojové soubory a soubory obsahu přidružené k projektu, obsahuje informace o sestavení pro každý soubor, udržuje informace pro integraci se systémy správy zdrojového kódu a pomáhá organizovat aplikaci do logických komponent.

![Projekt Python v Průzkumník řešení](media/projects-solution-explorer.png)

Kromě toho se projekty vždy spravují v rámci Visual Studio *řešení*, které může obsahovat libovolný počet projektů, které se mohou navzájem odkazovat. Projekt Pythonu může například odkazovat na projekt jazyka C++, který implementuje modul rozšíření. U této relace Visual Studio automaticky sestaví projekt C++ (v případě potřeby) při spuštění ladění projektu Pythonu. (Obecnou diskuzi najdete v tématu Řešení a [projekty v Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).)

Visual Studio poskytuje celou řadu šablon projektů Pythonu pro rychlé nastavení řady aplikačních struktur, včetně šablony pro vytvoření projektu z existujícího stromu složek a šablony pro vytvoření čistého prázdného projektu. Index [najdete v](#project-templates) tématu Šablony projektů.

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019 podporuje otevření složky obsahující kód Pythonu a spuštění tohoto kódu bez Visual Studio souborů projektu a řešení. Další informace najdete v tématu [Rychlý start: Otevření a spuštění kódu Pythonu ve složce](quickstart-05-python-visual-studio-open-folder.md). Použití souboru projektu má ale své výhody, jak je vysvětleno v této části.
::: moniker-end

> [!Tip]
> Bez projektu fungují všechny verze Visual Studio s kódem Pythonu. Můžete například otevřít samotný soubor Pythonu a využívat automatické dokončování, Technologii IntelliSense a ladění (kliknutím pravým tlačítkem v editoru a výběrem možnosti Začít **s laděním).** Vzhledem k tomu, že tento kód vždy používá výchozí globální prostředí, může se zobrazit nesprávné dokončení nebo chyby, pokud je kód určen pro jiné prostředí. Kromě toho Visual Studio všechny soubory a balíčky ve složce, ze které je otevřen jeden soubor, což může spotřebovávat značný čas procesoru.
>
> Je jednoduché vytvořit projekt Visual Studio existujícího kódu, jak je popsáno v tématu Vytvoření [projektu z existujících souborů](#create-project-from-existing-files).

![Ikona filmové kamery pro video](../install/media/video-icon.png "Přehrát video") [Deep Dive: Použití](https://youtu.be/Aq8eqApnugM) správy zdrojového kódu s projekty Pythonu (youtube.com, 8 min 55 s).

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Přidání souborů, přiřazení spouštěcího souboru a nastavení prostředí

Při vývoji aplikace obvykle potřebujete do projektu přidat nové soubory různých typů. Přidání takových souborů se provádí tak, že kliknete pravým tlačítkem na projekt a vyberete Přidat existující položku, pomocí které vyhledáte soubor, který chcete přidat, nebo přidat novou položku , která zobrazí dialogové okno s různými  >     >  šablonami položek. Jak je popsáno v [referenčních odkazech na](python-item-templates.md) šablony položek, možnosti zahrnují prázdné soubory Pythonu, třídu Pythonu, test jednotek a různé soubory související s webovými aplikacemi. Tyto možnosti můžete prozkoumat pomocí testovacího projektu a zjistit, co je k dispozici ve vaší verzi Visual Studio.

Každý projekt Pythonu má jeden přiřazený počáteční soubor, který se zobrazuje tučně **Průzkumník řešení**. Spouštěcí soubor je soubor, který se spustí při spuštění ladění **(F5** nebo ladění **spustit** ladění) nebo při spuštění projektu v interaktivním okně  >  **(Shift**  + **Alt** + **F5** nebo ladění spuštění projektu v  >  **Python Interactive).** Pokud ho chcete změnit, klikněte pravým tlačítkem na nový soubor a vyberte Nastavit jako položku po spuštění **(nebo** Nastavit jako spouštěcí **soubor** ve starších verzích Visual Studio).

> [!Tip]
> Pokud odeberete vybraný spouštěcí soubor z projektu a nevyberete nový, Visual Studio při pokusu o spuštění projektu neví, od čeho má pythonový soubor začít. V tomto případě Visual Studio 2017 verze 15.6 a novější zobrazí chybu. Dřívější verze buď otevřou okno výstupu se spuštěnou interpretem Pythonu, nebo uvidíte, že se zobrazí okno výstupu, ale pak téměř okamžitě zmizí. Pokud narazíte na jakékoli z těchto chování, zkontrolujte, že máte přiřazený spouštěcí soubor.
>
> Pokud chcete okno výstupu z nějakého důvodu nechat otevřené, klikněte pravým tlačítkem na projekt, vyberte **Vlastnosti,** vyberte kartu **Ladit** a pak přidejte do pole `-i` **Argumenty interpreta.** Tento argument způsobí, že interpret po dokončení programu přechádí do interaktivního režimu, čímž se okno nechá otevřené, dokud neskončíte stisknutím **kláves Ctrl** + **Z**  >  **Enter.**

::: moniker range="vs-2017"
Nový projekt je vždy přidružený k výchozímu globálnímu prostředí Pythonu. Pokud chcete projekt přidružit k jinému prostředí (včetně virtuálních prostředí), klikněte pravým tlačítkem na uzel **Prostředí Pythonu** v projektu, vyberte Přidat nebo odebrat prostředí **Pythonu** a vyberte požadovaná prostředí.
::: moniker-end
::: moniker range=">=vs-2019"
Nový projekt je vždy přidružený k výchozímu globálnímu prostředí Pythonu. Pokud chcete projekt přidružit k jinému prostředí (včetně virtuálních prostředí), klikněte pravým tlačítkem na uzel **Prostředí Pythonu** v projektu, vyberte Přidat **prostředí.** a vyberte požadovaná prostředí. Pomocí ovládacího prvku rozevíracího seznamu prostředí na panelu nástrojů můžete také vybrat prostředí a nebo do projektu přidat další.

![Příkaz Přidat prostředí na panelu nástrojů Pythonu](media/environments/environments-toolbar-2019.png)
::: moniker-end

Pokud chcete změnit aktivní prostředí, klikněte pravým tlačítkem na požadované prostředí v **Průzkumník řešení** **vyberte Aktivovat prostředí,** jak je znázorněno níže. Další informace najdete v [tématu Výběr prostředí pro projekt.](selecting-a-python-environment-for-a-project.md)

![Aktivace prostředí pro projekt Pythonu](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Šablony projektů

Visual Studio nabízí několik způsobů, jak nastavit projekt Pythonu, ať už od začátku, nebo z existujícího kódu. Pokud chcete použít šablonu, vyberte příkaz nabídky Soubor nový projekt nebo klikněte pravým tlačítkem na řešení v Průzkumník řešení a vyberte Přidat nový projekt . Oba tyto možnosti zobrazí níže dialogové okno Nový  >    >      >  projekt.  Pokud chcete zobrazit šablony specifické pro Python, vyhledejte "Python" nebo vyberte **nainstalovaný**  >  **uzel Pythonu:**

![Dialogové okno Nový projekt s šablonami Pythonu](media/projects-new-project-dialog.png)

::: moniker range="<=vs-2017"

Následující tabulka shrnuje šablony dostupné v Visual Studio 2017 (ne všechny šablony jsou dostupné ve všech předchozích verzích):

| Template (Šablona) | Description |
| --- | --- |
| [**Z existujícího kódu Pythonu**](#create-project-from-existing-files) | Vytvoří projekt Visual Studio existujícího kódu Pythonu ve struktuře složek.  |
| **Aplikace v Pythonu** | Základní struktura projektu pro novou aplikaci v Pythonu s jedním prázdným zdrojovým souborem. Ve výchozím nastavení se projekt spouští v interpretu konzoly výchozího globálního prostředí, které můžete změnit přiřazením [jiného prostředí](selecting-a-python-environment-for-a-project.md). |
| [**Cloudová služba Azure**](python-azure-cloud-service-project-template.md) | Projekt pro cloudovou službu Azure napsaný v Pythonu. |
| [**Webové projekty**](python-web-application-project-templates.md) | Projekty pro webové aplikace založené na různých architekturách, včetně Bottle, Django a Flask. |
| **Aplikace IronPython** | Podobá se šabloně aplikace Pythonu, ale ve výchozím nastavení používá IronPython, který umožňuje interoperabilitu .NET a ladění ve smíšeném režimu s jazyky .NET. |
| **Aplikace IronPython WPF** | Struktura projektu využívající IronPython s Windows Presentation Foundation XAML pro uživatelské rozhraní aplikace. Visual Studio poskytuje návrháře uživatelského rozhraní XAML, kód na pozadí je možné napsat v Pythonu a aplikace se spustí bez zobrazení konzoly. |
| **IronPython Silverlight Web Page** | Projekt IronPython, který běží v prohlížeči pomocí Silverlightu. Kód Pythonu aplikace je součástí webové stránky jako skript. Často používaný skript si stáhne kód JavaScriptu, který inicializuje IronPython spuštěný uvnitř Silverlightu, ze kterého může kód Pythonu interagovat s modelu DOM. |
| **IronPython Windows Forms Application** | Struktura projektu využívající IronPython s uživatelským rozhraním vytvořeným pomocí kódu s model Windows Forms. Aplikace se spustí bez zobrazení konzoly. |
| **Aplikace na pozadí (IoT)** | Podporuje nasazení projektů Pythonu tak, aby se na zařízeních spouštěl jako služby na pozadí. Další informace najdete v Dev Center Windows [IoT.](https://dev.windows.com/en-us/iot) |
| **Modul rozšíření Pythonu** | Tato šablona se zobrazí v části Visual C++, pokud jste nainstalovali nativní vývojové nástroje **Pythonu** s úlohou Pythonu v Visual Studio 2017 nebo novějším (viz [Instalace).](installing-python-support-in-visual-studio.md) Poskytuje základní strukturu pro knihovnu DLL rozšíření jazyka C++, podobně jako je popsáno v tématu Vytvoření rozšíření [C++ pro Python.](working-with-c-cpp-python-in-visual-studio.md) |
::: moniker-end

::: moniker range=">=vs-2019"

Následující tabulka shrnuje šablony dostupné v Visual Studio 2019 (ne všechny šablony jsou k dispozici ve všech předchozích verzích):

| Template (Šablona) | Description |
| --- | --- |
| [**Z existujícího kódu Pythonu**](#create-project-from-existing-files) | Vytvoří projekt Visual Studio existujícího kódu Pythonu ve struktuře složek.  |
| **Aplikace v Pythonu** | Základní struktura projektu pro novou aplikaci v Pythonu s jedním prázdným zdrojovým souborem. Ve výchozím nastavení se projekt spouští v interpretu konzoly výchozího globálního prostředí, které můžete změnit přiřazením [jiného prostředí](selecting-a-python-environment-for-a-project.md). |
| [**Webové projekty**](python-web-application-project-templates.md) | Projekty pro webové aplikace založené na různých architekturách, včetně Bottle, Django a Flask. |
| **Aplikace IronPython** | Podobá se šabloně aplikace Pythonu, ale ve výchozím nastavení používá IronPython, který umožňuje interoperabilitu .NET a ladění ve smíšeném režimu s jazyky .NET. |
| **Aplikace IronPython WPF** | Struktura projektu využívající IronPython s Windows Presentation Foundation XAML pro uživatelské rozhraní aplikace. Visual Studio poskytuje návrháře uživatelského rozhraní XAML, kód na pozadí je možné napsat v Pythonu a aplikace se spustí bez zobrazení konzoly. |
| **IronPython Silverlight Web Page** | Projekt IronPython, který běží v prohlížeči pomocí Silverlightu. Kód Pythonu aplikace je součástí webové stránky jako skript. Často používaný skript si stáhne kód JavaScriptu, který inicializuje IronPython spuštěný uvnitř Silverlightu, ze kterého může kód Pythonu interagovat s modelu DOM. |
| **IronPython Windows Forms Application** | Struktura projektu využívající IronPython s uživatelským rozhraním vytvořeným pomocí kódu s model Windows Forms. Aplikace se spustí bez zobrazení konzoly. |
| **Aplikace na pozadí (IoT)** | Podporuje nasazení projektů Pythonu tak, aby se na zařízeních spouštěl jako služby na pozadí. Další informace najdete v Dev Center Windows [IoT.](https://dev.windows.com/en-us/iot) |
| **Modul rozšíření Pythonu** | Tato šablona se zobrazí v části Visual C++, pokud jste nainstalovali nativní vývojové nástroje **Pythonu** s úlohou Pythonu v Visual Studio 2017 nebo novějším (viz [Instalace).](installing-python-support-in-visual-studio.md) Poskytuje základní strukturu pro knihovnu DLL rozšíření jazyka C++, podobně jako je popsáno v tématu Vytvoření rozšíření [C++ pro Python.](working-with-c-cpp-python-in-visual-studio.md) |
::: moniker-end

> [!Note]
> Vzhledem k tomu, že Python je interpretovaný jazyk, projekty Pythonu v Visual Studio nevytvářenou samostatný spustitelný soubor jako jiné kompilované jazykové projekty (například C#). Další informace najdete v dotazech a [odpovědích.](overview-of-python-tools-for-visual-studio.md#questions-and-answers)

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Vytvoření projektu z existujících souborů

> [!Important]
> Zde popsaný postup nepřesoudí ani nekopíruje původní zdrojové soubory. Pokud chcete pracovat s kopií, nejprve duplikujte složku.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Propojené soubory

Propojené soubory jsou soubory, které se převedou do projektu, ale obvykle se nacházejí mimo složky projektu aplikace. Zobrazují se v **Průzkumník řešení** jako běžné soubory s ikonou přeobrazované zkratky: Ikona ![ propojeného souboru](media/projects-linked-file-icon.png)

Propojené soubory jsou v *souboru .pyproj* určeny pomocí `<Compile Include="...">` elementu . Propojené soubory jsou implicitní, pokud používají relativní cestu mimo adresářovou strukturu, nebo explicitní, pokud používají cesty v **rámci Průzkumník řešení**:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Propojené soubory se ignorují za jakékoli z následujících podmínek:

- Propojený soubor obsahuje metadata propojení a cestu zadanou v atributu Include v adresáři projektu.
- Propojený soubor duplikuje soubor, který existuje v hierarchii projektu.
- Propojený soubor obsahuje metadata propojení a cesta k odkazu je relativní cesta mimo hierarchii projektu.
- Cesta odkazu má root.

### <a name="work-with-linked-files"></a>Práce s propojenými soubory

Pokud chcete přidat existující položku jako odkaz, klikněte pravým tlačítkem na složku v projektu, do které chcete soubor přidat, a pak vyberte **Přidat**  >  **existující položku**. V dialogovém okně, které se  zobrazí, vyberte soubor a v rozevíracím seznamu na tlačítku Přidat zvolte **Přidat jako** odkaz. Za předpokladu, že neexistují žádné konfliktní soubory, vytvoří tento příkaz odkaz ve vybrané složce. Odkaz se ale nepřidá, pokud už v projektu existuje soubor se stejným názvem nebo odkaz na tento soubor.

Pokud se pokusíte vytvořit odkaz na soubor, který už ve složkách projektu existuje, přidá se jako normální soubor, nikoli jako odkaz. Pokud chcete převést soubor na odkaz, vyberte **Soubor** Uložit jako a uložte ho do umístění  >   mimo hierarchii projektu. Visual Studio ho automaticky převede na odkaz. Podobně lze odkaz převést zpět pomocí příkazu **Soubor** Uložit jako a uložit soubor  >   někam do hierarchie projektu.

Pokud přesunete propojený soubor v **Průzkumník řešení**, odkaz se přesune, ale samotný soubor to neovlvlní. Podobně odstranění odkazu odebere odkaz, aniž by to ovlivnilo soubor.

Propojené soubory nelze přejmenovat.

## <a name="references"></a>Reference

Visual Studio projekty podporují přidávání odkazů na projekty a rozšíření, které se zobrazují v uzlu Odkazy v **Průzkumník řešení**: 

![Odkazy na rozšíření v projektech Pythonu](media/projects-extension-references.png)

Odkazy na rozšíření obvykle označují závislosti mezi projekty a se používají k poskytování Technologie IntelliSense v době návrhu nebo propojování v době kompilace. Projekty Pythonu používají odkazy podobným způsobem, ale vzhledem k dynamické povaze Pythonu se primárně používají při návrhu, aby poskytovaly vylepšenou technologii IntelliSense. Můžete je také použít k nasazení Microsoft Azure instalaci dalších závislostí.

### <a name="extension-modules"></a>Moduly rozšíření

Odkaz na soubor *.pyd* umožňuje technologii IntelliSense pro vygenerovaný modul. Visual Studio načte soubor *.pyd* do interpreta Pythonu a introspektuje jeho typy a funkce. Pokouší se také parsovat řetězce dokumentace pro funkce, které poskytují pomoc s podpisy.

Pokud se modul rozšíření kdykoli aktualizuje na disku, Visual Studio modul znovuanalyzuje na pozadí. Tato akce nemá žádný vliv na chování za běhu, ale některá dokončování nejsou k dispozici, dokud se analýza nedokoní.

Možná budete také muset přidat cestu [hledání do](search-paths.md) složky, která obsahuje modul.

### <a name="net-projects"></a>Projekty .NET

Při práci s IronPythonem můžete přidat odkazy na sestavení .NET a povolit technologii IntelliSense. U projektů .NET ve vašem řešení  klikněte pravým tlačítkem na uzel Odkazy v projektu Pythonu, vyberte Přidat **odkaz,** vyberte kartu **Projekty** a přejděte k požadovanému projektu. U knihoven DLL, které jste stáhli samostatně, vyberte kartu **Procházet** a přejděte na požadovanou knihovnu DLL.

Vzhledem k tomu, že odkazy v IronPythonu nejsou k dispozici, dokud není provedeno volání metody , musíte také přidat odpovídající volání sestavení, obvykle na `clr.AddReference('<AssemblyName>')` `clr.AddReference` začátek kódu. Například kód vytvořený šablonou projektu **IronPython model Windows Forms Application** Visual Studio v horní části souboru obsahuje dvě volání:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>Projekty WebPI

Můžete přidat odkazy na položky produktu WebPI pro nasazení do Microsoft Azure Cloud Services, kde můžete nainstalovat další komponenty prostřednictvím informačního kanálu WebPI. Zobrazený informační kanál je standardně specifický pro Python a zahrnuje Django, CPython a další základní komponenty. Můžete také vybrat vlastní informační kanál, jak je znázorněno níže. Při publikování do Microsoft Azure nainstaluje instalační úloha všechny odkazované produkty.

> [!IMPORTANT]
> Projekty WebPI nejsou k dispozici v Visual Studio 2017 nebo Visual Studio 2019.

![Odkazy WebPI](media/projects-webPI-components.png)
