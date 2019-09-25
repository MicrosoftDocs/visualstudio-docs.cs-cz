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
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254206"
---
# <a name="python-projects-in-visual-studio"></a>Projekty v Pythonu v sadě Visual Studio

Aplikace Pythonu se obvykle definují použití pouze souborů a složek, ale tato struktura se může stát složité aplikace větší možná zahrnují automaticky generované soubory jazyka JavaScript pro webové aplikace, a tak dále. Projekt sady Visual Studio pomáhá spravovat Tato složitost. Projekt ( *.pyproj* souboru) identifikuje všechny zdroje a soubory obsahu přidružené k projektu, obsahuje informace o sestavení pro každý soubor, udržuje informace o integraci se systémy správy zdrojového kódu a pomáhá Uspořádejte aplikace do logické součásti.

![Projekt v Pythonu v Průzkumníku řešení](media/projects-solution-explorer.png)

Kromě toho jsou vždy spravované projekty v sadě Visual Studio *řešení*, který může obsahovat libovolný počet projektů, které může odkazovat navzájem. Například projekt Python může odkazovat na projektu C++, která implementuje modul rozšíření. S tuto relaci sady Visual Studio automaticky sestavení projektu C++ (v případě potřeby) při spuštění ladění projektu Pythonu. (Obecné informace najdete v článku [řešení a projekty v sadě Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).)

Visual Studio poskytuje celou řadu šablon projektů Python rychle nastavit počet struktury aplikace, včetně šablonu pro vytvoření projektu z existujících stromovou strukturu složek a šablonu pro vytvoření projektu vyčistit, prázdný. Zobrazit [šablony projektů](#project-templates) pro index.

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019 podporuje otevření složky obsahující kód Pythonu a spuštění tohoto kódu bez vytváření projektů a souborů řešení sady Visual Studio. Další informace najdete v tématu [rychlý Start: Otevřete a spusťte kód Pythonu ve složce](quickstart-05-python-visual-studio-open-folder.md). Existují však výhody použití souboru projektu, jak je vysvětleno v této části.
::: moniker-end

> [!Tip]
> Bez projektu fungují všechny verze sady Visual Studio dobře s kódem Pythonu. Například můžete otevřít Python soubor samostatně a využívat automatické dokončování, technologie IntelliSense a ladění (kliknutím pravým tlačítkem v editoru a výběr **začínat ladění**). Protože takový kód vždy používá výchozího globálního prostředí, ale může se zobrazit chyby nebo nesprávný dokončování Pokud kód je určená pro jiné prostředí. Kromě toho sada Visual Studio analyzuje všech souborů a balíčků ve složce ze kterého je otevřít jeden soubor, který může spotřebovat významný čas procesoru.
>
> Je jednoduché, chcete-li vytvořit projekt sady Visual Studio z existujícího kódu, jak je popsáno v [vytvoření projektu z existujících souborů](#create-project-from-existing-files).

|   |   |
|---|---|
| ![Ikona filmové kamery pro video](../install/media/video-icon.png "Sledovat video") | [Hluboká podrobně: Použijte správu zdrojového kódu v projektech](https://youtu.be/Aq8eqApnugM) Pythonu (YouTube.com, 8 min 55s). |

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Přidejte soubory, přiřaďte spouštěcí soubor a nastavení prostředí

Při vývoji vaší aplikace, je obvykle potřeba přidat do projektu nové soubory různých typů. Přidáním těchto souborů se provádí tak, že kliknete pravým tlačítkem projekt a vyberete **přidat** > **existující položku** pomocí které můžete procházet pro soubor, který chcete přidat, nebo **přidat**  >  **Nová položka**, která otevře dialogové okno s celou řadu šablon položek. Jak je popsáno na [šablon položek](python-item-templates.md) odkaz, možnosti zahrnují prázdné soubory Pythonu, třída Pythonu, testování částí a různé soubory související s webovými aplikacemi. Můžete prozkoumat tyto možnosti pomocí projektu testů se dozvíte, co je k dispozici ve vaší verzi sady Visual Studio.

Každý projekt Python má jeden přiřazené spouštěcí soubor ukazuje tučné písmo v **Průzkumníka řešení**. Spouštěcí soubor je soubor, který je spuštěn při spuštění ladění (**F5** nebo **ladění** > **spustit ladění**) nebo při spuštění projektu v **Interaktivní** okno (**Shift**+**Alt**+**F5** nebo **ladění**  >  **Provést projekt v interaktivním okně Pythonu**). Pokud ho chcete změnit, klikněte pravým tlačítkem myši na nový soubor a vyberte **nastavit jako položku po spuštění** (nebo **nastavit jako spouštěcí soubor** ve starších verzích sady Visual Studio).

> [!Tip]
> Pokud odeberete vybraný spouštěcí soubor z projektu a nevyberete nový, Visual Studio nezjistí, který soubor Pythonu má začít při pokusu o spuštění projektu. V takovém případě ukazuje chybu; Visual Studio 2017 verze 15.6 a novější starší verze buď otevřít okno výstupu překladač Pythonu s, nebo se zobrazí v okně výstupu se zobrazí, ale zmizí téměř okamžitě. Pokud dojde k některé z těchto projevů, zkontrolujte, že máte přiřazenou spouštěcí soubor.
>
> Pokud chcete nechat otevřené okno výstup z jakéhokoli důvodu, klikněte pravým tlačítkem na projekt, vyberte **vlastnosti**, vyberte **ladění** kartu a pak přidejte `-i` k **argumenty pro interpret**  pole. Tento argument způsobí, že překladač přejde do interaktivního režimu po dokončení programu, a tím udržování okna otevřete dokud nezadáte **Ctrl**+**Z**  >  **Enter** ukončíte.

::: moniker range="vs-2017"
Nový projekt je vždy přidružena výchozí globální prostředí Pythonu. Chcete-li projekt přidružit jiné prostředí (včetně virtuální prostředí), klikněte pravým tlačítkem na **prostředí Pythonu** uzlu v projektu, vyberte **přidat nebo odebrat prostředí Pythonu**, a Vyberte ty, které chcete.
::: moniker-end
::: moniker range=">=vs-2019"
Nový projekt je vždy přidružena výchozí globální prostředí Pythonu. Chcete-li přidružit projekt k jinému prostředí (včetně virtuálních prostředí), klikněte pravým tlačítkem myši na uzel **prostředí Python** v projektu, vyberte možnost **Přidat prostředí..** a vyberte požadované položky. Můžete také použít rozevírací ovládací prvek prostředí na panelu nástrojů k výběru a prostředí nebo k přidání dalšího do projektu.

![Přidání příkazu prostředí na panel nástrojů Pythonu](media/environments/environments-toolbar-2019.png)
::: moniker-end

Pokud chcete změnit aktivní prostředí, klikněte pravým tlačítkem na požadované prostředí v **Průzkumník řešení** a vyberte **aktivovat prostředí** , jak je znázorněno níže. Další informace najdete v tématu [vyberte prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

![Aktivace prostředí k projektu Pythonu](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Šablony projektů

Sada Visual Studio poskytuje několik způsobů, jak nastavit projektu Pythonu, od začátku nebo z existujícího kódu. Chcete-li použít šablonu, vyberte **souboru** > **nový** > **projektu** nabídce příkaz % $n nebo klikněte pravým tlačítkem na řešení v **řešení Průzkumník** a vyberte **přidat** > **nový projekt**, které otevřete **nový projekt** následující dialogové okno. Pokud chcete zobrazit šablony specifické pro Python, vyhledat "Python" nebo vyberte **nainstalováno** > **Python** uzlu:

![Dialogové okno nového projektu s využitím Pythonu šablon](media/projects-new-project-dialog.png)

Následující tabulka shrnuje šablony dostupné v aplikaci Visual Studio 2017 a novějších (ne všechny šablony jsou k dispozici ve všech předchozích verzích):

| Šablona | Popis |
| --- | --- |
| [**Z existujícího kódu Pythonu**](#create-project-from-existing-files) | Vytvoří projekt aplikace Visual Studio z existujícího kódu Pythonu ve struktuře složek.  |
| **Aplikace v Pythonu** | Struktura základního projektu pro novou aplikaci v Pythonu s jeden, prázdný zdrojový soubor. Ve výchozím nastavení, spustí se v konzole překladač výchozího globálního prostředí, které můžete změnit podle projekt [přiřazení do různých prostředí](selecting-a-python-environment-for-a-project.md). |
| [**Cloudové služby Azure**](python-azure-cloud-service-project-template.md) | Projekt pro cloudovou službu Azure napsané v Pythonu. |
| [**Webové projekty**](python-web-application-project-templates.md) | Projekty pro webové aplikace založené na různé architektury, včetně Bottle, Django, Flask. |
| **Aplikace v Ironpythonu** | Podobně jako šablonu aplikace Pythonu, ale používá IronPython ve výchozí povolení .NET spolupráce a pracující v kombinovaném režimu ladění s jazyky rozhraní .NET. |
| **Aplikace WPF v Ironpythonu** | Struktura projektu použití IronPython soubory Windows Presentation Foundation XAML pro uživatelské rozhraní vaší aplikace. Visual Studio poskytuje Návrhář v jazyce XAML, může být použití modelu code-behind napsané v Pythonu a spuštění aplikace bez zobrazení konzoly. |
| **IronPython Silverlight webové stránky** | IronPython projekt, který běží v prohlížeči pomocí technologie Silverlight. Kód aplikace Python je součástí webovou stránku jako skript. Často používaný text značky skriptu stáhne kódu jazyka JavaScript, která inicializuje Ironpythonu běžících v rámci programu Silverlight, ze kterého kódu Pythonu můžete pracovat s modelu DOM. |
| **Formulářové aplikaci Windows Ironpythonu** | Struktura projektu pomocí uživatelského rozhraní, které jsou vytvořené pomocí kódu pomocí Windows Forms Ironpythonu. Aplikace se spouští bez zobrazení konzoly. |
| **Aplikace běžící na pozadí (IoT)** | Podporuje nasazování projektů v Pythonu ke spuštění jako služby na pozadí na zařízeních. Přejděte [centru vývojářů pro Windows IoT](https://dev.windows.com/en-us/iot) Další informace. |
| **Rozšiřující modul Pythonu** | Tato šablona se zobrazí v C++ části vizuál, pokud jste nainstalovali **nativní vývojové nástroje Pythonu** s úlohou Pythonu v aplikaci Visual Studio 2017 nebo novějším (viz [instalace](installing-python-support-in-visual-studio.md)). Poskytuje základní strukturu pro C++ rozšiřující knihovny DLL, podobně jako už uváděli [vytvoření rozšíření C++ pro Python](working-with-c-cpp-python-in-visual-studio.md). |

> [!Note]
> Protože je interpretovaný jazyk Python, projekty v Pythonu v sadě Visual Studio nevytvářejí samostatný spustitelný soubor jako ostatní projekty kompilované jazyka (C#, například). Další informace najdete v tématu [otázek a odpovědí](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Vytvoření projektu z existujících souborů

> [!Important]
> Proces je zde popsáno, ne přesuňte nebo zkopírujte původním zdrojovým souborům. Pokud chcete pracovat s kopií, duplicitní první složku.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Připojené soubory

Propojené soubory jsou soubory, které přesměrují do projektu se ale obvykle se nacházejí mimo složky projektu aplikace. Zobrazují se v **Průzkumník řešení** jako běžné soubory s ikonou zástupce překrytí: ![Ikona propojeného souboru](media/projects-linked-file-icon.png)

Propojené soubory jsou určené v *.pyproj* soubor pomocí `<Compile Include="...">` elementu. Propojené soubory jsou implicitní, pokud používá relativní cestu mimo strukturu adresářů nebo explicitní, pokud používají cest v rámci **Průzkumníka řešení**:

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

Chcete-li přidat existující položku jako odkaz, klikněte pravým tlačítkem na složku v projektu, ve kterém chcete přidat soubor a pak vyberte **přidat** > **existující položku**. V zobrazeném dialogovém okně vyberte soubor a zvolte **přidat jako odkaz** z rozevíracího seznamu na **přidat** tlačítko. Za předpokladu, že neexistují žádné konfliktní soubory, tento příkaz vytvoří odkaz ve vybrané složce. Odkaz není však přidat, pokud již existuje soubor se stejným názvem nebo odkaz na tento soubor v projektu již existuje.

Pokud se pokusíte k odkazování na soubor, který již existuje ve složce projektu se přidá jako normální soubor, nikoli jako odkaz. Chcete-li soubor převést na odkaz, vyberte **souboru** > **uložit jako** k uložení souboru do umístění mimo hierarchii projektu. Visual Studio automaticky převede jej na odkaz. Podobně můžete převést odkaz zpět pomocí **souboru** > **uložit jako** k uložení souboru někde v hierarchii projektu.

Je-li přesunout propojený soubor v **Průzkumníka řešení**, se přesune na odkaz, ale skutečný soubor je poškozena. Podobně odstraněním propojení odebere propojení bez ovlivnění souboru.

Nelze přejmenovat, propojené soubory.

## <a name="references"></a>Odkazy

Podpora přidávání odkazů do projektů a rozšíření, které se zobrazí v části projekty sady Visual Studio **odkazy** uzel v **Průzkumníka řešení**:

![Reference na rozšíření v projektů v Pythonu](media/projects-extension-references.png)

Reference na rozšíření obvykle označují závislostí mezi projekty a se používají k zajištění technologie IntelliSense v době návrhu nebo propojení v době kompilace. Projekty v Pythonu pomocí odkazů na podobným způsobem, ale kvůli dynamické povaze Python se primárně používají v době návrhu k poskytování technologie IntelliSense. Můžete také používají pro nasazení do služby Microsoft Azure Chcete-li nainstalovat další závislosti.

### <a name="extension-modules"></a>Rozšiřující moduly

Odkaz na *.pyd* souboru pro vygenerovaný modul technologie IntelliSense. Visual Studio načte *.pyd* soubor do interpret Pythonu a introspects jeho typy a funkce. Pokusy o také k analýze řetězce doc pro funkce k poskytování Nápověda k podpisu.

Pokud kdykoli dojde k aktualizaci rozšíření modulu na disku, Visual Studio znovu analyzovala modulu na pozadí. Tato akce nemá žádný vliv na chování za běhu, ale některá dokončení nejsou k dispozici, dokud nebude Analýza dokončena.

Můžete také přidat [cesty pro hledání](search-paths.md) ke složce obsahující modul.

### <a name="net-projects"></a>Projekty .NET

Při práci s IronPython, je možné přidat odkazy na sestavení .NET k povolení technologie IntelliSense. Pro projekty .NET ve vašem řešení, klikněte pravým tlačítkem na **odkazy** uzel v projektu v Pythonu, vyberte **přidat odkaz**, vyberte **projekty** kartu a přejděte do požadovaný odebíraný projekt. Pro knihovny DLL, které jste stáhnout samostatně, vyberte **Procházet** kartě místo a přejděte do požadované knihovny DLL.

Protože odkazů v Ironpythonu nejsou k dispozici až do volání `clr.AddReference('<AssemblyName>')` je proveden, je také třeba přidat odpovídající `clr.AddReference` volání do sestavení, obvykle na začátku kódu. Například kód vytvořený pomocí **formulářová aplikace Windows IronPython** šablona projektu v sadě Visual Studio obsahuje dvě volání v horní části souboru:

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
