---
title: Správa projektů aplikace v Pythonu
description: Projekty v sadě Visual Studio Správa závislostí mezi soubory a složité vztahy v aplikaci.
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409067"
---
# <a name="python-projects-in-visual-studio"></a>Projekty v Pythonu v sadě Visual Studio

Aplikace Pythonu se obvykle definují použití pouze souborů a složek, ale tato struktura se může stát složité aplikace větší možná zahrnují automaticky generované soubory jazyka JavaScript pro webové aplikace, a tak dále. Projekt sady Visual Studio pomáhá spravovat Tato složitost. Projekt (soubor *. pyproj* ) identifikuje všechny zdrojové a obsahové soubory přidružené k vašemu projektu, obsahuje informace o sestavení každého souboru, uchovává informace pro integraci se systémy správy zdrojového kódu a pomáhá organizovat aplikace do logických komponent.

![Projekt v Pythonu v Průzkumníku řešení](media/projects-solution-explorer.png)

Kromě toho projekty jsou vždy spravovány v rámci *řešení*sady Visual Studio, které mohou obsahovat libovolný počet projektů, které mohou odkazovat na sebe navzájem. Například projekt Python může odkazovat na projektu C++, která implementuje modul rozšíření. S tuto relaci sady Visual Studio automaticky sestavení projektu C++ (v případě potřeby) při spuštění ladění projektu Pythonu. (Obecné diskuze najdete v tématu [řešení a projekty v aplikaci Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).)

Visual Studio poskytuje celou řadu šablon projektů Python rychle nastavit počet struktury aplikace, včetně šablonu pro vytvoření projektu z existujících stromovou strukturu složek a šablonu pro vytvoření projektu vyčistit, prázdný. Viz [šablony projektu](#project-templates) pro index.

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019 podporuje otevření složky obsahující kód Pythonu a spuštění tohoto kódu bez vytváření projektů a souborů řešení sady Visual Studio. Další informace najdete v tématu [rychlý Start: otevření a spuštění kódu Pythonu ve složce](quickstart-05-python-visual-studio-open-folder.md). Existují však výhody použití souboru projektu, jak je vysvětleno v této části.
::: moniker-end

> [!Tip]
> Bez projektu fungují všechny verze sady Visual Studio dobře s kódem Pythonu. Můžete například otevřít soubor Python sám o sobě a využít automatické dokončování, IntelliSense a ladění (kliknutím pravým tlačítkem v editoru a výběrem možnosti **Spustit s laděním**). Protože takový kód vždy používá výchozího globálního prostředí, ale může se zobrazit chyby nebo nesprávný dokončování Pokud kód je určená pro jiné prostředí. Kromě toho sada Visual Studio analyzuje všech souborů a balíčků ve složce ze kterého je otevřít jeden soubor, který může spotřebovat významný čas procesoru.
>
> Je jednoduché vytvořit projekt sady Visual Studio z existujícího kódu, jak je popsáno v tématu [Vytvoření projektu z existujících souborů](#create-project-from-existing-files).

|   |   |
|---|---|
| ![ikona filmové kamery pro video](../install/media/video-icon.png "Přehrát video") | [Hluboká podrobně: použití správy zdrojového kódu v projektech Pythonu](https://youtu.be/Aq8eqApnugM) (YouTube.com, 8 min 55s). |

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Přidejte soubory, přiřaďte spouštěcí soubor a nastavení prostředí

Při vývoji vaší aplikace, je obvykle potřeba přidat do projektu nové soubory různých typů. Přidání takových souborů probíhá tak, že kliknete pravým tlačítkem na projekt a vyberete **přidat** > **existující položku** , se kterou hledáte soubor, který chcete přidat, nebo **Přidat** > **novou položku**, která zobrazí dialog s nejrůznějšími šablonami položek. Jak je popsáno v referenčních informacích k [šablonám položek](python-item-templates.md) , možnosti zahrnují prázdné soubory Pythonu, třídu Python, testování částí a různé soubory související s webovými aplikacemi. Můžete prozkoumat tyto možnosti pomocí projektu testů se dozvíte, co je k dispozici ve vaší verzi sady Visual Studio.

Každý projekt v Pythonu má jeden přiřazený spouštěcí soubor, který je v **Průzkumník řešení**zobrazený tučným písmem. Spouštěcí soubor je soubor, který je spuštěn při spuštění ladění (**F5** nebo **ladění** > **Spustit ladění**) nebo při spuštění projektu v **interaktivním** okně (**SHIFT**+**ALT**+**F5** ** > nebo** **v interaktivním spuštění projektu v Pythonu**). Pokud ho chcete změnit, klikněte pravým tlačítkem myši na nový soubor a vyberte **nastavit jako položku po spuštění** (nebo **nastavit jako spouštěcí soubor** ve starších verzích sady Visual Studio).

> [!Tip]
> Pokud odeberete vybraný spouštěcí soubor z projektu a nevyberete nový, Visual Studio nezjistí, který soubor Pythonu má začít při pokusu o spuštění projektu. V takovém případě ukazuje chybu; Visual Studio 2017 verze 15.6 a novější starší verze buď otevřít okno výstupu překladač Pythonu s, nebo se zobrazí v okně výstupu se zobrazí, ale zmizí téměř okamžitě. Pokud dojde k některé z těchto projevů, zkontrolujte, že máte přiřazenou spouštěcí soubor.
>
> Pokud chcete zachovat otevřené okno výstup z jakéhokoli důvodu, klikněte pravým tlačítkem myši na projekt, vyberte možnost **vlastnosti**, vyberte kartu **ladění** a poté přidejte `-i` do pole **argumenty interpretu** . Tento argument způsobí, že překladač přejde do interaktivního režimu po dokončení programu a zůstane otevřené okno, dokud nezadáte **Ctrl**+**Z** > **ENTER** k ukončení.

::: moniker range="vs-2017"
Nový projekt je vždy přidružena výchozí globální prostředí Pythonu. Pokud chcete projekt přidružit k jinému prostředí (včetně virtuálních prostředí), klikněte pravým tlačítkem myši na uzel **prostředí Pythonu** v projektu, vyberte **Přidat nebo odebrat prostředí Pythonu**a vyberte ty, které chcete.
::: moniker-end
::: moniker range=">=vs-2019"
Nový projekt je vždy přidružena výchozí globální prostředí Pythonu. Chcete-li přidružit projekt k jinému prostředí (včetně virtuálních prostředí), klikněte pravým tlačítkem myši na uzel **prostředí Python** v projektu, vyberte možnost **Přidat prostředí..** a vyberte požadované položky. Můžete také použít rozevírací ovládací prvek prostředí na panelu nástrojů k výběru a prostředí nebo k přidání dalšího do projektu.

![Přidání příkazu prostředí na panel nástrojů Pythonu](media/environments/environments-toolbar-2019.png)
::: moniker-end

Pokud chcete změnit aktivní prostředí, klikněte pravým tlačítkem na požadované prostředí v **Průzkumník řešení** a vyberte **aktivovat prostředí** , jak je znázorněno níže. Další informace najdete v tématu [Výběr prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

![Aktivace prostředí k projektu Pythonu](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Šablony projektů

Sada Visual Studio poskytuje několik způsobů, jak nastavit projektu Pythonu, od začátku nebo z existujícího kódu. Chcete-li použít šablonu, vyberte **soubor** > **Nový** > nabídce **projekt** , nebo klikněte pravým tlačítkem myši na řešení v **Průzkumník řešení** a vyberte **Přidat** > **Nový projekt**, obě z nich přepněte níže v dialogovém okně **Nový projekt** . Chcete-li zobrazit šablony specifické pro Python, buď vyhledejte "Python", nebo vyberte **nainstalovaný** > uzel **Python** :

![Dialogové okno nového projektu s využitím Pythonu šablon](media/projects-new-project-dialog.png)

Následující tabulka shrnuje šablony dostupné v aplikaci Visual Studio 2017 a novějších (ne všechny šablony jsou k dispozici ve všech předchozích verzích):

| Šablona | Popis |
| --- | --- |
| [**Z existujícího kódu Pythonu**](#create-project-from-existing-files) | Vytvoří projekt aplikace Visual Studio z existujícího kódu Pythonu ve struktuře složek.  |
| **Aplikace Pythonu** | Struktura základního projektu pro novou aplikaci v Pythonu s jeden, prázdný zdrojový soubor. Ve výchozím nastavení je projekt spuštěn v překladači konzoly výchozího globálního prostředí, které můžete změnit [přiřazením jiného prostředí](selecting-a-python-environment-for-a-project.md). |
| [**Cloudová služba Azure**](python-azure-cloud-service-project-template.md) | Projekt pro cloudovou službu Azure napsané v Pythonu. |
| [**Webové projekty**](python-web-application-project-templates.md) | Projekty pro webové aplikace založené na různé architektury, včetně Bottle, Django, Flask. |
| **Aplikace Ironpythonu** | Podobně jako šablonu aplikace Pythonu, ale používá IronPython ve výchozí povolení .NET spolupráce a pracující v kombinovaném režimu ladění s jazyky rozhraní .NET. |
| **Aplikace WPF v Ironpythonu** | Struktura projektu použití IronPython soubory Windows Presentation Foundation XAML pro uživatelské rozhraní vaší aplikace. Visual Studio poskytuje Návrhář v jazyce XAML, může být použití modelu code-behind napsané v Pythonu a spuštění aplikace bez zobrazení konzoly. |
| **Webová stránka Ironpythonu Silverlight** | IronPython projekt, který běží v prohlížeči pomocí technologie Silverlight. Kód aplikace Python je součástí webovou stránku jako skript. Často používaný text značky skriptu stáhne kódu jazyka JavaScript, která inicializuje Ironpythonu běžících v rámci programu Silverlight, ze kterého kódu Pythonu můžete pracovat s modelu DOM. |
| **Aplikace Ironpythonu model Windows Forms** | Struktura projektu pomocí uživatelského rozhraní, které jsou vytvořené pomocí kódu pomocí Windows Forms Ironpythonu. Aplikace se spouští bez zobrazení konzoly. |
| **Aplikace na pozadí (IoT)** | Podporuje nasazování projektů v Pythonu ke spuštění jako služby na pozadí na zařízeních. Další informace najdete v [centru vývojářů pro Windows IoT](https://dev.windows.com/en-us/iot) . |
| **Rozšiřující modul Pythonu** | Tato šablona se zobrazí v C++ části vizuál, pokud jste nainstalovali **nativní vývojové nástroje Pythonu** s úlohou Pythonu v aplikaci Visual Studio 2017 nebo novějším (viz [instalace](installing-python-support-in-visual-studio.md)). Poskytuje základní strukturu pro C++ rozšiřující knihovnu DLL, podobně jako to, co je popsáno v tématu [vytvoření C++ rozšíření pro Python](working-with-c-cpp-python-in-visual-studio.md). |

> [!Note]
> Protože je interpretovaný jazyk Python, projekty v Pythonu v sadě Visual Studio nevytvářejí samostatný spustitelný soubor jako ostatní projekty kompilované jazyka (C#, například). Další informace najdete v tématu [otázky a odpovědi](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Vytvoření projektu z existujících souborů

> [!Important]
> Proces je zde popsáno, ne přesuňte nebo zkopírujte původním zdrojovým souborům. Pokud chcete pracovat s kopií, duplicitní první složku.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Připojené soubory

Propojené soubory jsou soubory, které přesměrují do projektu se ale obvykle se nacházejí mimo složky projektu aplikace. Zobrazují se v **Průzkumník řešení** jako běžné soubory s ikonou zástupce překrytí: ikona ![propojených souborů](media/projects-linked-file-icon.png)

Propojené soubory jsou zadány v souboru *. pyproj* pomocí elementu `<Compile Include="...">`. Propojené soubory jsou implicitní, pokud používají relativní cestu mimo adresářovou strukturu nebo explicitní, pokud používají cesty v rámci **Průzkumník řešení**:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Propojených souborů jsou ignorovány pod následující podmínky:

- Propojený soubor obsahuje metadata odkaz a cestě zadané v atributu život zahrnout adresáře projektu
- Propojený soubor duplikuje soubor, který existuje v rámci hierarchie projektu
- Propojený soubor obsahuje metadata odkaz a odkaz cesta je relativní cesta mimo hierarchii projektu
- Cesta odkazu je kořenem.

### <a name="work-with-linked-files"></a>Práce s připojené soubory

Chcete-li přidat existující položku jako odkaz, klikněte pravým tlačítkem myši na složku v projektu, kam chcete přidat soubor, a pak vyberte **přidat** > **existující položka**. V dialogovém okně, které se zobrazí, vyberte soubor a v rozevíracím **seznamu klikněte na tlačítko** **Přidat jako odkaz** . Za předpokladu, že neexistují žádné konfliktní soubory, tento příkaz vytvoří odkaz ve vybrané složce. Odkaz není však přidat, pokud již existuje soubor se stejným názvem nebo odkaz na tento soubor v projektu již existuje.

Pokud se pokusíte k odkazování na soubor, který již existuje ve složce projektu se přidá jako normální soubor, nikoli jako odkaz. Chcete-li převést soubor na odkaz, vyberte **soubor** > **Uložit jako** a uložte soubor do umístění mimo hierarchii projektu. Visual Studio ho automaticky převede na odkaz. Podobně lze odkaz převést zpět pomocí **souboru** > **Uložit jako** k uložení souboru někam v rámci hierarchie projektu.

Pokud přesunete propojený soubor v **Průzkumník řešení**, odkaz se přesune, ale skutečný soubor nebude ovlivněn. Podobně odstraněním propojení odebere propojení bez ovlivnění souboru.

Nelze přejmenovat, propojené soubory.

## <a name="references"></a>Odkazy

Projekty sady Visual Studio podporují přidávání odkazů na projekty a rozšíření, které se zobrazí pod uzlem **odkazy** v **Průzkumník řešení**:

![Reference na rozšíření v projektů v Pythonu](media/projects-extension-references.png)

Reference na rozšíření obvykle označují závislostí mezi projekty a se používají k zajištění technologie IntelliSense v době návrhu nebo propojení v době kompilace. Projekty v Pythonu pomocí odkazů na podobným způsobem, ale kvůli dynamické povaze Python se primárně používají v době návrhu k poskytování technologie IntelliSense. Můžete také používají pro nasazení do služby Microsoft Azure Chcete-li nainstalovat další závislosti.

### <a name="extension-modules"></a>Rozšiřující moduly

Odkaz na soubor *. PYD* umožňuje technologii IntelliSense pro vygenerovaný modul. Visual Studio načte soubor *. PYD* do interpretu Pythonu a introspects jeho typy a funkce. Pokusy o také k analýze řetězce doc pro funkce k poskytování Nápověda k podpisu.

Pokud kdykoli dojde k aktualizaci rozšíření modulu na disku, Visual Studio znovu analyzovala modulu na pozadí. Tato akce nemá žádný vliv na chování za běhu, ale některá dokončení nejsou k dispozici, dokud nebude Analýza dokončena.

Je také možné, že budete muset přidat [cestu pro hledání](search-paths.md) do složky obsahující modul.

### <a name="net-projects"></a>Projekty .NET

Při práci s IronPython, je možné přidat odkazy na sestavení .NET k povolení technologie IntelliSense. Pro projekty .NET v rámci vašeho řešení klikněte pravým tlačítkem myši na uzel **odkazy** v projektu Python, vyberte možnost **Přidat odkaz**, vyberte kartu **projekty** a přejděte k požadovanému projektu. U knihoven DLL, které jste stáhli samostatně, vyberte místo toho kartu **Procházet** a přejděte k požadované knihovně DLL.

Protože odkazy v Ironpythonu nejsou k dispozici, dokud není provedeno volání `clr.AddReference('<AssemblyName>')`, je také nutné přidat příslušné `clr.AddReference` volání do sestavení, obvykle na začátku kódu. Například kód vytvořený šablonou projektu **ironpythonu model Windows Forms aplikace** v aplikaci Visual Studio obsahuje dvě volání v horní části souboru:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>Projekty instalace webové platformy

Odkazy na položky produktů instalace webové platformy pro nasazení můžete přidat do Microsoft Azure Cloud Services, kde ji můžete nainstalovat další součásti přes instalaci webové platformy informačního kanálu. Ve výchozím nastavení zobrazit informační kanál je specifické pro Python a zahrnuje Django, CPython a další součásti core. Můžete také vybrat vlastní informační kanál, jak je znázorněno níže. Při publikování do Microsoft Azure, úlohu instalační program nainstaluje všechny odkazované produktů.

> [!IMPORTANT]
> Projekty WebPI nejsou k dispozici v aplikaci Visual Studio 2017 nebo Visual Studio 2019.

![Odkazy WebPI](media/projects-webPI-components.png)
