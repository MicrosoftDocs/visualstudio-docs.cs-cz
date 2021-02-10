---
title: Správa projektů aplikace v Pythonu
description: Projekty v aplikaci Visual Studio spravují závislosti mezi soubory a složitostí vztahů v aplikaci.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 09203557fd9adcd6580dfafa981d6ed4f80eca16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936454"
---
# <a name="python-projects-in-visual-studio"></a>Projekty Pythonu v aplikaci Visual Studio

Aplikace Pythonu se obvykle definují jenom pomocí složek a souborů, ale tato struktura se může stát složitá, protože aplikace se stanou větší a možná budou zahrnovat automaticky generované soubory, JavaScript pro webové aplikace atd. Projekt sady Visual Studio pomáhá spravovat tuto složitost. Projekt (soubor *. pyproj* ) identifikuje všechny zdrojové a obsahové soubory přidružené k vašemu projektu, obsahuje informace o sestavení každého souboru, uchovává informace pro integraci se systémy správy zdrojového kódu a pomáhá organizovat aplikace do logických komponent.

![Projekt Pythonu v Průzkumník řešení](media/projects-solution-explorer.png)

Kromě toho projekty jsou vždy spravovány v rámci *řešení* sady Visual Studio, které mohou obsahovat libovolný počet projektů, které mohou odkazovat na sebe navzájem. Například projekt Pythonu může odkazovat na projekt C++, který implementuje rozšiřující modul. V této relaci Visual Studio automaticky vytvoří projekt C++ (Pokud je to potřeba) při zahájení ladění projektu Pythonu. (Obecné diskuze najdete v tématu [řešení a projekty v aplikaci Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).)

Sada Visual Studio poskytuje celou řadu šablon projektů Pythonu k rychlému nastavení řady aplikačních struktur, včetně šablony pro vytvoření projektu z existujícího stromu složky a šablony pro vytvoření čistého, prázdného projektu. Viz [šablony projektu](#project-templates) pro index.

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019 podporuje otevření složky obsahující kód Pythonu a spuštění tohoto kódu bez vytváření projektů a souborů řešení sady Visual Studio. Další informace najdete v tématu [rychlý Start: otevření a spuštění kódu Pythonu ve složce](quickstart-05-python-visual-studio-open-folder.md). Existují však výhody použití souboru projektu, jak je vysvětleno v této části.
::: moniker-end

> [!Tip]
> Bez projektu fungují všechny verze sady Visual Studio dobře s kódem Pythonu. Můžete například otevřít soubor Python sám o sobě a využít automatické dokončování, IntelliSense a ladění (kliknutím pravým tlačítkem v editoru a výběrem možnosti **Spustit s laděním**). Vzhledem k tomu, že tento kód vždy používá výchozí globální prostředí, můžete však zobrazit nesprávná dokončení nebo chyby, pokud je kód určen pro jiné prostředí. Kromě toho Visual Studio analyzuje všechny soubory a balíčky ve složce, ze které je otevřen jeden soubor, což by mohlo spotřebovat značný čas procesoru.
>
> Je jednoduché vytvořit projekt sady Visual Studio z existujícího kódu, jak je popsáno v tématu [Vytvoření projektu z existujících souborů](#create-project-from-existing-files).

![ikona filmové kamery pro video](../install/media/video-icon.png "Přehrát video") s [hloubkovým podrobně: použití správy zdrojového kódu v projektech pythonu](https://youtu.be/Aq8eqApnugM) (YouTube.com, 8 min 55s).

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Přidejte soubory, přiřaďte spouštěcí soubor a nastavte prostředí.

Při vývoji aplikace obvykle musíte do projektu přidat nové soubory různých typů. Přidání takových souborů je provedeno kliknutím pravým tlačítkem myši na projekt a vybráním možnosti **Přidat**  >  **existující položku** , pomocí které můžete vyhledat soubor, který chcete přidat, nebo **Přidat**  >  **novou položku**, která zobrazí dialog s nejrůznějšími šablonami položek. Jak je popsáno v referenčních informacích k [šablonám položek](python-item-templates.md) , možnosti zahrnují prázdné soubory Pythonu, třídu Python, testování částí a různé soubory související s webovými aplikacemi. Můžete prozkoumat tyto možnosti pomocí testovacího projektu a zjistit, co je ve vaší verzi sady Visual Studio k dispozici.

Každý projekt v Pythonu má jeden přiřazený spouštěcí soubor, který je v **Průzkumník řešení** zobrazený tučným písmem. Spouštěcí soubor je soubor, který je spuštěn při spuštění ladění (**F5** nebo **ladění**  >  **spuštění** ladění) nebo při spuštění projektu v **interaktivním** okně (**SHIFT** + **ALT** + **F5** nebo **ladění**  >  **spuštění projektu v jazyce Python Interactive**). Pokud ho chcete změnit, klikněte pravým tlačítkem myši na nový soubor a vyberte **nastavit jako položku po spuštění** (nebo **nastavit jako spouštěcí soubor** ve starších verzích sady Visual Studio).

> [!Tip]
> Pokud odeberete vybraný spouštěcí soubor z projektu a nevyberete nový, Visual Studio nezjistí, který soubor Pythonu má začít při pokusu o spuštění projektu. V tomto případě se v systému Visual Studio 2017 verze 15,6 a novější zobrazuje chyba. předchozí verze buď otevřou okno výstup se spuštěným překladačem Pythonu, nebo se zobrazí okno výstup, ale nakonec zmizí téměř okamžitě. Pokud se setkáte s některým z těchto chování, ověřte, zda máte přiřazený spouštěcí soubor.
>
> Pokud chcete zachovat otevřené okno výstup z jakéhokoli důvodu, klikněte pravým tlačítkem myši na projekt, vyberte možnost **vlastnosti**, vyberte kartu **ladění** a poté přidejte `-i` do pole **argumenty interpretu** . Tento argument způsobí, že překladač přejde do interaktivního režimu po dokončení programu, takže okno zůstane otevřené, dokud nezadáte **klávesu CTRL** + **Z**  >  **ENTER** k ukončení.

::: moniker range="vs-2017"
Nový projekt je vždy přidružen k výchozímu globálnímu prostředí Python. Pokud chcete projekt přidružit k jinému prostředí (včetně virtuálních prostředí), klikněte pravým tlačítkem myši na uzel **prostředí Pythonu** v projektu, vyberte **Přidat nebo odebrat prostředí Pythonu** a vyberte ty, které chcete.
::: moniker-end
::: moniker range=">=vs-2019"
Nový projekt je vždy přidružen k výchozímu globálnímu prostředí Python. Chcete-li přidružit projekt k jinému prostředí (včetně virtuálních prostředí), klikněte pravým tlačítkem myši na uzel **prostředí Python** v projektu, vyberte možnost **Přidat prostředí..** a vyberte požadované položky. Můžete také použít rozevírací ovládací prvek prostředí na panelu nástrojů k výběru a prostředí nebo k přidání dalšího do projektu.

![Přidání příkazu prostředí na panel nástrojů Pythonu](media/environments/environments-toolbar-2019.png)
::: moniker-end

Pokud chcete změnit aktivní prostředí, klikněte pravým tlačítkem na požadované prostředí v **Průzkumník řešení** a vyberte **aktivovat prostředí** , jak je znázorněno níže. Další informace najdete v tématu [Výběr prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

![Aktivace prostředí pro projekt v Pythonu](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Šablony projektů

Sada Visual Studio poskytuje několik způsobů, jak vytvořit projekt v Pythonu, ať už od začátku, nebo z existujícího kódu. Chcete-li použít šablonu, vyberte **příkaz soubor**  >  nabídky **Nový**  >  **projekt** nebo klikněte pravým tlačítkem myši na řešení v **Průzkumník řešení** a vyberte možnost **Přidat**  >  **Nový projekt**, obě z nich přepněte níže v dialogovém okně **Nový projekt** . Pokud chcete zobrazit šablony specifické pro Python, buď vyhledejte "Python", nebo vyberte **nainstalovaný**  >  uzel **Pythonu** :

![Dialog Nový projekt se šablonami Pythonu](media/projects-new-project-dialog.png)

Následující tabulka shrnuje šablony dostupné v aplikaci Visual Studio 2017 a novějších (ne všechny šablony jsou k dispozici ve všech předchozích verzích):

| Template (Šablona) | Description |
| --- | --- |
| [**Z existujícího kódu Pythonu**](#create-project-from-existing-files) | Vytvoří projekt sady Visual Studio z existujícího kódu Pythonu ve struktuře složek.  |
| **Aplikace Pythonu** | Základní struktura projektu pro novou aplikaci v Pythonu s jedním prázdným zdrojovým souborem. Ve výchozím nastavení je projekt spuštěn v překladači konzoly výchozího globálního prostředí, které můžete změnit [přiřazením jiného prostředí](selecting-a-python-environment-for-a-project.md). |
| [**Cloudová služba Azure**](python-azure-cloud-service-project-template.md) | Projekt pro cloudovou službu Azure napsanou v Pythonu |
| [**Webové projekty**](python-web-application-project-templates.md) | Projekty pro webové aplikace založené na různých rozhraních, včetně láhví, Django a baňky. |
| **Aplikace Ironpythonu** | Podobně jako v šabloně aplikace Python, ale používá Ironpythonu ve výchozím nastavení a povoluje ladění rozhraní .NET a ladění v kombinovaném režimu s použitím jazyků .NET. |
| **Aplikace WPF v Ironpythonu** | Struktura projektu s použitím Ironpythonu s Windows Presentation Foundation soubory XAML pro uživatelské rozhraní aplikace. Visual Studio poskytuje návrháře uživatelského rozhraní XAML, kód na pozadí lze zapsat v Pythonu a aplikace se spouští bez zobrazení konzoly. |
| **Webová stránka Ironpythonu Silverlight** | Projekt Ironpythonu, který běží v prohlížeči pomocí programu Silverlight. Kód Pythonu aplikace je součástí webové stránky jako skript. Standardní značka skriptu si vyžádá nějaký kód JavaScriptu, který inicializuje Ironpythonu běžící v rámci Silverlight, ze kterého může kód Pythonu pracovat s modelem DOM. |
| **Aplikace Ironpythonu model Windows Forms** | Struktura projektu pomocí Ironpythonu s uživatelským rozhraním vytvořeným pomocí kódu s model Windows Forms. Aplikace se spustí bez zobrazení konzoly. |
| **Aplikace na pozadí (IoT)** | Podporuje nasazování projektů v jazyce Python pro spuštění jako služeb na pozadí na zařízeních. Další informace najdete v [centru vývojářů pro Windows IoT](https://dev.windows.com/en-us/iot) . |
| **Rozšiřující modul Pythonu** | Tato šablona se zobrazí v části Visual C++, pokud jste nainstalovali **nativní vývojové nástroje Pythonu** s úlohou Pythonu v aplikaci Visual Studio 2017 nebo novějším (viz [instalace](installing-python-support-in-visual-studio.md)). Poskytuje základní strukturu pro rozšiřující knihovnu DLL jazyka C++, podobně jako to, co je popsáno v tématu [Vytvoření rozšíření c++ pro Python](working-with-c-cpp-python-in-visual-studio.md). |

> [!Note]
> Vzhledem k tomu, že Python je interpretovaný jazyk, projekty Pythonu v aplikaci Visual Studio neposkytují samostatný spustitelný soubor jako jiné kompilované jazykové projekty (například C#). Další informace najdete v tématu [otázky a odpovědi](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Vytvořit projekt z existujících souborů

> [!Important]
> Proces popsaný tady nepřesouvá ani nekopíruje původní zdrojové soubory. Pokud chcete pracovat s kopií, nejprve složku duplikujte.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Propojené soubory

Propojené soubory jsou soubory, které se přenesou do projektu, ale obvykle se nacházejí mimo složky projektu aplikace. Zobrazují se v **Průzkumník řešení** jako normální soubory s ikonou zástupce překrytí: ![ ikona propojeného souboru](media/projects-linked-file-icon.png)

Propojené soubory jsou zadány v souboru *. pyproj* pomocí `<Compile Include="...">` elementu. Propojené soubory jsou implicitní, pokud používají relativní cestu mimo adresářovou strukturu nebo explicitní, pokud používají cesty v rámci **Průzkumník řešení**:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Propojené soubory se ignorují při splnění následujících podmínek:

- Propojený soubor obsahuje metadata odkazů a cestu zadanou v atributu Include umístěnou v adresáři projektu.
- Propojený soubor duplikuje soubor, který existuje v hierarchii projektu.
- Propojený soubor obsahuje metadata odkazů a cesta odkazu je relativní cesta mimo hierarchii projektu.
- Cesta k odkazu je rootovaná.

### <a name="work-with-linked-files"></a>Práce s propojenými soubory

Chcete-li přidat existující položku jako odkaz, klikněte pravým tlačítkem myši na složku v projektu, kam chcete přidat soubor, a pak vyberte **Přidat**  >  **existující položku**. V dialogovém okně, které se zobrazí, vyberte soubor a v rozevíracím **seznamu klikněte na tlačítko** **Přidat jako odkaz** . V případě, že nejsou k dispozici žádné konfliktní soubory, tento příkaz vytvoří odkaz ve vybrané složce. Odkaz však není přidán, pokud již existuje soubor se stejným názvem nebo odkazem na tento soubor již v projektu existuje.

Pokud se pokusíte propojit soubor, který již existuje ve složkách projektu, je přidán jako normální soubor, nikoli jako odkaz. Chcete-li převést soubor na odkaz, vyberte **soubor**  >  **Uložit jako** a uložte soubor do umístění mimo hierarchii projektu. Visual Studio ho automaticky převede na odkaz. Podobně je možné odkaz převést zpět pomocí **souboru**  >  **Uložit jako** k uložení souboru někam v rámci hierarchie projektu.

Pokud přesunete propojený soubor v **Průzkumník řešení**, odkaz se přesune, ale skutečný soubor nebude ovlivněn. Podobně odstranění odkazu odstraní propojení bez ovlivnění souboru.

Propojené soubory nelze přejmenovat.

## <a name="references"></a>Reference

Projekty sady Visual Studio podporují přidávání odkazů na projekty a rozšíření, které se zobrazí pod uzlem **odkazy** v **Průzkumník řešení**:

![Odkazy na rozšíření v projektech Pythonu](media/projects-extension-references.png)

Odkazy na rozšíření obvykle označují závislosti mezi projekty a slouží k poskytování technologie IntelliSense v době návrhu nebo propojení v době kompilace. Projekty Pythonu používají odkazy podobným způsobem, ale v důsledku dynamické povahy Pythonu jsou primárně používány v době návrhu k zajištění vylepšené technologie IntelliSense. Můžou se taky používat k nasazení Microsoft Azure k instalaci dalších závislostí.

### <a name="extension-modules"></a>Moduly rozšíření

Odkaz na soubor *. PYD* umožňuje technologii IntelliSense pro vygenerovaný modul. Visual Studio načte soubor *. PYD* do interpretu Pythonu a introspects jeho typy a funkce. Také se pokusí analyzovat řetězce dokumentů pro funkce, které poskytují nápovědu k podpisu.

Pokud je v každém okamžiku aktualizovaný modul rozšíření na disku, Visual Studio znovu analyzuje modul na pozadí. Tato akce nemá žádný vliv na chování za běhu, ale některá dokončení nejsou k dispozici, dokud nebude Analýza dokončena.

Je také možné, že budete muset přidat [cestu pro hledání](search-paths.md) do složky obsahující modul.

### <a name="net-projects"></a>Projekty .NET

Při práci s Ironpythonu můžete přidat odkazy na sestavení .NET, aby bylo možné technologii IntelliSense povolit. Pro projekty .NET v rámci vašeho řešení klikněte pravým tlačítkem myši na uzel **odkazy** v projektu Python, vyberte možnost **Přidat odkaz**, vyberte kartu **projekty** a přejděte k požadovanému projektu. U knihoven DLL, které jste stáhli samostatně, vyberte místo toho kartu **Procházet** a přejděte k požadované knihovně DLL.

Protože odkazy v Ironpythonu nejsou k dispozici `clr.AddReference('<AssemblyName>')` , dokud není provedeno volání, je také nutné přidat příslušné `clr.AddReference` volání sestavení, obvykle na začátku kódu. Například kód vytvořený šablonou projektu **ironpythonu model Windows Forms aplikace** v aplikaci Visual Studio obsahuje dvě volání v horní části souboru:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>Projekty WebPI

Můžete přidat odkazy na WebPI položky produktu pro nasazení do Microsoft Azure Cloud Services, kde můžete nainstalovat další komponenty prostřednictvím informačního kanálu WebPI. Ve výchozím nastavení je informační kanál zobrazen specifický pro Python a zahrnuje Django, CPython a další základní komponenty. Můžete také vybrat vlastní kanál, jak je znázorněno níže. Při publikování na Microsoft Azure nainstaluje úloha instalace všechny odkazované produkty.

> [!IMPORTANT]
> Projekty WebPI nejsou k dispozici v aplikaci Visual Studio 2017 nebo Visual Studio 2019.

![Odkazy na WebPI](media/projects-webPI-components.png)
