---
title: Per-Monitor zvyšování povědomí o Visual Studio zařízení
titleSuffix: ''
description: Seznamte se s novou podporou rozšiřujících zařízení pro sledování monitorů dostupnou v Visual Studio 2019.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: reference
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 90ec038e8f27407ba08633bacbb5576bee2a7883
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902043"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Per-Monitor zvyšování povědomí o Visual Studio zařízení

Ve verzích před Visual Studio 2019 byl kontext sledování DPI nastavený na systém, a ne na hodnotu DPI pro každý monitor (PMA). Sledování systému mělo za následek zhoršení vizuálního prostředí (např. rozmazaná písma nebo ikony), kdykoli se Visual Studio musel vykreslit na různých monitorech s různými faktory škálování nebo vzdáleně na počítače s různými konfiguracemi zobrazení (např. různé škálování Windows).

Kontext sledování DPI Visual Studio 2019 se nastaví jako PMA, když to prostředí podporuje, což umožňuje, aby se Visual Studio vykresloval podle konfigurace zobrazení, kde je hostované, a ne podle jediné konfigurace definované systémem. Nakonec překládáme do vždy smyšlených uživatelského rozhraní pro povrchové oblasti, které podporují režim PMA.

Další informace o podmínkách a celkovém scénáři prostudování tohoto dokumentu najdete v dokumentaci Vývoj desktopových aplikací s vysokým dpi ve [Windows.](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows)

## <a name="quickstart"></a>Rychlé zprovoznění

- Ujistěte Visual Studio spuštěný v režimu PMA (viz **Povolení PMA).**

- Ověřte, že vaše rozšíření funguje správně v celé sadě běžných scénářů (viz **Testování rozšíření pro problémy s PMA).**

- Pokud zjistíte problémy, můžete tyto problémy diagnostikovat a opravit pomocí strategií a doporučení probíraných v tomto dokumentu. Pro přístup k požadovaným rozhraním API budete také muset do projektu přidat nový balíček NuGet [Microsoft.VisualStudio.DpiAwareness.](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/)

## <a name="enable-pma"></a>Povolení PMA

Pokud chcete pma povolit Visual Studio, je potřeba splnit následující požadavky:

- Aktualizace Windows 10 z dubna 2018 (v1803, RS4) nebo novější
- .NET Framework 4.8 RTM nebo vyšší
- Visual Studio 2019 s povolenou možností [Optimalizovat](../../ide/reference/general-environment-options-dialog-box.md) vykreslování pro obrazovky s různými hustotami pixelů

Po splnění těchto požadavků Visual Studio automaticky povolí režim PMA v celém procesu.

> [!NOTE]
> model Windows Forms obsahu v Visual Studio (například Prohlížeč vlastností) podporuje PMA jenom v případě, že máte Visual Studio 2019 verze 16.1 nebo novější.

## <a name="test-your-extensions-for-pma-issues"></a>Testování rozšíření kvůli problémům s PMA

Visual Studio oficiálně podporuje architektury uživatelského rozhraní WPF, model Windows Forms, Win32 a HTML/JS. Když Visual Studio do režimu PMA, chová se každý zásobník uživatelského rozhraní odlišně. Proto se bez ohledu na rozhraní uživatelského rozhraní doporučuje provést testovací průchod, aby se zajistilo, že veškeré uživatelské rozhraní vyhovuje režimu PMA.

Doporučuje se ověřit následující běžné scénáře:

- Změna faktoru škálování jednoho monitorového prostředí v době, kdy je aplikace spuštěná

  Tento scénář pomáhá testovat, zda uživatelské rozhraní reaguje na dynamickou změnu windows DPI.

- Docking/undocking a laptop where an attached monitor is set to the primary and the attached monitor has a attached monitor has a different scale factor than the laptop while the application is running.

  Tento scénář pomáhá testovat, jestli uživatelské rozhraní reaguje na změnu DPI zobrazení, a také dynamicky přidávají nebo odebrali zobrazení.

- Mít několik monitorů s různými faktory škálování a přesouvat aplikaci mezi nimi.

  Tento scénář pomáhá otestovat, že uživatelské rozhraní reaguje na změnu dpi zobrazení.
    
- Vzdálená komunikace do počítače v případě, že místní a vzdálené počítače mají pro primární monitor různé faktory škálování.

  Tento scénář pomáhá testovat, zda uživatelské rozhraní reaguje na dynamickou změnu windows DPI.

Dobrým předběžným testem, jestli vaše uživatelské rozhraní může mít problémy, je to, jestli kód využívá třídy *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper,* *Microsoft.VisualStudio.PlatformUI.DpiHelper* nebo *VsUI::CDpiHelper.* Tyto staré třídy DpiHelper podporují pouze sledování dpi systému a nebudou vždy správně fungovat, pokud je proces PMA.

Typické použití těchto dpihelperů bude vypadat takto:

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

// Declared via P/Invoke
IntPtr monitor = MonitorFromPoint(screenIntTopRight, MONITOR_DEFAULTTONEARST);
```

V předchozím příkladu je obdélník představující logické meze okna převeden na jednotky zařízení, aby ho bylo možné předat nativní metodě MonitorFromPoint, která očekává souřadnice zařízení, aby bylo možné vrátit přesný ukazatel monitorování.

### <a name="classes-of-issues"></a>Třídy problémů
Pokud je režim PMA povolený pro Visual Studio, může uživatelské rozhraní replikovat problémy několika běžnými způsoby. Většina,pokud ne všechny, může k těmto problémům dojít v některém Visual Studio podporovaných architekturách uživatelského rozhraní. Kromě toho k těmto problémům může dojít také v případě, že se část uživatelského rozhraní hostuje ve scénářích škálování DPI ve smíšeném režimu (další informace najdete v dokumentaci [k](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) Windows). 

#### <a name="win32-window-creation"></a>Vytvoření okna Win32
Při vytváření oken pomocí CreateWindow() nebo CreateWindowEx() je běžným vzorem vytvoření okna v souřadnicích (0,0) (v levém horním rohu primárního zobrazení) a jeho přesunutí na poslední pozici. To však může způsobit, že okno aktivuje zprávu nebo událost změny DPI, což může znovu aktivovat jiné zprávy nebo události uživatelského rozhraní a nakonec vést k nežádoucímu chování nebo vykreslování.

#### <a name="wpf-element-placement"></a>Umístění elementu WPF
Při přesouvání prvků WPF pomocí staré třídy Microsoft.VisualStudio.Utilities.Dpi.DpiHelper nemusí být levá horní souřadnice vypočítána správně vždy, když jsou prvky v ne primárním dpi.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serializace velikosti nebo pozic elementů uživatelského rozhraní
Když se velikost nebo pozice uživatelského rozhraní (pokud je uložená jako jednotky zařízení) obnoví v jiném kontextu DPI, než ve které byl uložen, bude nesprávně umístěna a nastavena jeho velikost. K tomu dochází, protože jednotky zařízení mají inherentní vztah DPI.

#### <a name="incorrect-scaling"></a>Nesprávné škálování
Prvky uživatelského rozhraní vytvořené v primárním dpi se budou správně škálovat, ale když se přesune na zobrazení s jiným dpi, nebudou se znovu škálovat a jejich obsah bude příliš velký nebo příliš malý.

#### <a name="incorrect-bounding"></a>Nesprávné ohraničování
Podobně jako u problému se škálováním prvky uživatelského rozhraní správně vypočítávají své meze v primárním kontextu DPI, ale při přesunu do ne primárního DPI nebudou nové meze správně počítat. Proto je okno obsahu v porovnání s hostitelským uživatelským rozhraním příliš malé nebo příliš velké, což vede k prázdnému prostoru nebo oříznutí.

#### <a name="drag--drop"></a>Přetažení & myší
Kdykoli ve scénářích s nastavením DPI ve smíšeném režimu (například různé prvky uživatelského rozhraní vykreslované v různých režimech sledování DPI) může být přetahování chybně započítáno, takže konečná pozice přetažení skončí nesprávně.

#### <a name="out-of-process-ui"></a>Uživatelské rozhraní mimo proces
Některé uživatelské rozhraní je vytvořeno mimo proces, a pokud je vytváření externího procesu v jiném režimu sledování DPI než Visual Studio, může dojít k některému z předchozích problémů s vykreslováním.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>model Windows Forms nesprávně vykreslené ovládací prvky, obrázky nebo rozložení
Ne všechny typy obsahu model Windows Forms režim PMA. V důsledku toho se může zobrazit problém s vykreslováním s nesprávným rozložením nebo škálováním. Možným řešením je v tomto případě explicitně vykreslit obsah model Windows Forms dpiAwarenessContext s chystým systémem (viz Vynucení ovládacího prvku do konkrétního [objektu DpiAwarenessContext).](#force-a-control-into-a-specific-dpiawarenesscontext)

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>model Windows Forms ovládací prvky nebo se nezobrazují okna
Jednou z hlavních příčin tohoto problému je, že se vývojáři pokoušet o znovu naváděli ovládací prvek nebo okno s jedním objektem DpiAwarenessContext na okno s jiným objektem DpiAwarenessContext.

Následující image ukazují aktuální výchozí omezení **operačního** systému Windows v nadřazených oknech:

![Snímek obrazovky se správným chováním při nadřazení](media/PMA-parenting-behavior.PNG)

> [!Note]
> Toto chování můžete změnit nastavením chování hostování vláken (viz Dpi_Hosting_Behavior [výčtu).](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)

Pokud nastavíte vztah nadřazenosti a podřízené položky mezi nepodporovanými režimy, dojde k selhání a ovládací prvek nebo okno se nemusí vykreslit podle očekávání.

### <a name="diagnose-issues"></a>Diagnostika problémů

Při identifikaci problémů souvisejících s PMA je třeba vzít v úvahu řadu faktorů: 

- Očekává uživatelské rozhraní nebo rozhraní API logické hodnoty nebo hodnoty zařízení?
    - Uživatelské rozhraní WPF a rozhraní API obvykle používají logické hodnoty (ale ne vždy)
    - Uživatelské rozhraní a rozhraní API Systému Win32 obvykle používají hodnoty zařízení.

- Odkud pochází hodnoty?
    - Pokud přijímá hodnoty z jiného uživatelského rozhraní nebo rozhraní API, předává hodnoty zařízení nebo logické hodnoty.
    - Pokud přijímáte hodnoty z více zdrojů, používají nebo očekávají stejné typy hodnot, nebo je potřeba převody směšovat a párovat?

- Používají se konstanty uživatelského rozhraní a v jaké formě se používají?

- Je vlákno ve správném kontextu DPI pro hodnoty, které přijímá?

  Změny umožňující hostování smíšených hodnot DPI by obecně měly umístit cesty kódu do hlavního kontextu, ale práce prováděná mimo hlavní smyčku zpráv nebo tok událostí se může provést v nesprávném kontextu DPI.

- Prochází hodnoty hranice kontextu DPI?

  Přetažení & je běžná situace, kdy souřadnice mohou křížovat kontexty DPI. Okno se pokusí udělat správnou věc, ale v některých případech může uživatelské rozhraní hostitele potřebovat provést konverzní práci, aby se zajistilo párování hranic kontextu.

### <a name="pma-nuget-package"></a>Balíček NuGet PMA
Nové knihovny DpiAwarness najdete v balíčku [NuGet Microsoft.VisualStudio.DpiAwareness.](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/)

### <a name="recommended-tools"></a>Doporučené nástroje
Následující nástroje vám můžou pomoct ladit problémy související s PMA v různých zásobníkech uživatelského rozhraní podporovaných Visual Studio.

#### <a name="snoop"></a>Snoop
Snoop je ladicí nástroj XAML, který má některé další funkce, které integrované nástroje Visual Studio XAML nemají. Kromě toho Snoop nemusí aktivně ladit Visual Studio, aby mohl zobrazit a upravit jeho uživatelské rozhraní WPF. Dva hlavní způsoby, jak může být Snoop užitečný pro diagnostiku problémů s PMA, je pro ověřování souřadnic logického umístění nebo meze velikosti a pro ověření, že uživatelské rozhraní má správné dpi.
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio nástroje XAML
Podobně jako Snoop můžou nástroje XAML v Visual Studio s diagnostikem problémů s PMA. Jakmile najdete pravděpodobnou viníka, můžete nastavit zarážky a pomocí okna Live Visual Tree a oken ladění zkontrolovat hranice uživatelského rozhraní a aktuální hodnotu DPI.

## <a name="strategies-for-fixing-pma-issues"></a>Strategie pro opravu problémů s PMA

### <a name="replace-dpihelper-calls"></a>Nahrazení volání DpiHelper

Ve většině případů oprava problémů s uživatelským rozhraním v režimu PMA nahrazuje volání ve spravovaném kódu starým třídám *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* a *Microsoft.VisualStudio.PlatformUI.DpiHelper* voláními nové třídy *Microsoft.VisualStudio.Utilities.DpiAwareness.* 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

U nativního kódu bude zahrnovat nahrazení volání staré třídy *VsUI::CDpiHelper* voláním nové třídy *VsUI::CDpiAwareness.* 

```cpp
// Remove this kind of use:
int cx = VsUI::DpiHelper::LogicalToDeviceUnitsX(m_cxS);
int cy = VsUI::DpiHelper::LogicalToDeviceUnitsY(m_cyS);

// Replace with this use:
int cx = m_cxS;
int cy = m_cyS;
VsUI::CDpiAwareness::LogicalToDeviceUnitsX(m_hwnd, &cx);
VsUI::CDpiAwareness::LogicalToDeviceUnitsY(m_hwnd, &cy);
```

Nové třídy DpiAwareness a CDpiAwareness nabízejí stejné pomocné prvky převodu jednotek jako třídy DpiHelper, ale vyžadují další vstupní parametr: prvek uživatelského rozhraní, který se použije jako odkaz na operaci převodu. Je důležité si uvědomit, že v nových pomocnách objektech DpiAwareness/CDpiAwareness neexistují pomocníci škálování obrázků, a pokud je to potřeba, měli byste místo toho použít [ImageService.](../image-service-and-catalog.md)

Spravovaná třída DpiAwareness nabízí pomocné prvky pro vizuály WPF, ovládací prvky model Windows Forms a win32 HWND a HMONITORs (ve formátu IntPtr), zatímco nativní třída CDpiAwareness nabízí pomocné objekty HWND a HMONITOR.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Model Windows Forms dialogová okna, okna nebo ovládací prvky zobrazené v nesprávném DpiAwarenessContext
I po úspěšném vytvoření nadřazeného objektu Windows s různými DpiAwarenessContexts (kvůli výchozímu chování Windows) můžou uživatelé dál sledovat problémy s škálováním v případě, že se Windows s jiným škálováním DpiAwarenessContexts liší. Výsledkem je, že uživatelé mohou v uživatelském rozhraní zobrazit zarovnání nebo rozmazaný text nebo problémy s obrázkem.

Řešením je nastavit správný rozsah DpiAwarenessContext pro všechna okna a ovládací prvky v aplikaci.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Dialogová okna nejvyšší úrovně smíšeného režimu (TLMM)
Při vytváření oken nejvyšší úrovně, jako jsou modální dialogy, je důležité se ujistit, že je vlákno ve správném stavu před oknem (a jeho popisovač), který se vytváří. Vlákno může být zavedeno do sledování systému pomocí pomocníka CDpiScope v nativním režimu nebo pomocníka DpiAwareness. EnterDpiScope ve spravovaném počítači. (TLMM by se mělo obecně používat v dialogových oknech, které nejsou WPF nebo Windows.)

### <a name="child-level-mixed-mode-clmm"></a>Smíšený režim úrovně podřízenosti (CLMM)
Ve výchozím nastavení obdrží podřízená okna aktuální kontext sledování DPI vlákna, pokud je vytvořeno bez nadřazeného objektu, nebo kontext sledování DPI nadřazeného objektu, pokud je vytvořen s nadřazeným prvkem. Chcete-li vytvořit podřízený objekt s jiným kontextem sledování DPI od jeho nadřazeného kontextu, vlákno lze umístit do požadovaného kontextu sledování DPI. Potom může být podřízený objekt vytvořen bez nadřazeného objektu a ručně znovu nadřazen do nadřazeného okna.

#### <a name="clmm-issues"></a>Problémy CLMM
Většina práce při výpočtu uživatelského rozhraní, která probíhá v rámci hlavní smyčky pro zasílání zpráv nebo řetěz událostí, by měla být spuštěná v pravém kontextu sledování DPI. Pokud jsou však výpočty souřadnice nebo velikosti provedeny mimo tyto hlavní pracovní postupy (například během úlohy nečinnosti nebo mimo vlákno uživatelského rozhraní, může být aktuální kontext sledování DPI nesprávný, což vede k problémům s chybou v uživatelském rozhraní nebo chybou chybného určení velikosti. Tento problém se obecně vyřeší tím, že se vlákno umístí do správného stavu pro práci s uživatelským rozhraním.
 
#### <a name="opt-out-of-clmm"></a>Odhlásit z CLMM
Pokud se migruje okno nástroje bez WPF, aby plně podporovalo PMA, bude se muset odhlásit z CLMM. K tomu je potřeba implementovat nové rozhraní: IVsDpiAware.

```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```

```cpp
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```

Pro spravované jazyky je nejvhodnější místo pro implementaci tohoto rozhraní ve stejné třídě, která je odvozena od třídy *Microsoft. VisualStudio. Shell. třídy ToolWindowPane*. V jazyce C++ je nejlepší místo pro implementaci tohoto rozhraní ve stejné třídě, která implementuje *IVsWindowPane* z vsshell. h.

Hodnota vrácená vlastností Mode v rozhraní je __VSDPIMODE (a přetypování na objekt uint ve spravovaném):

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- To znamená, že okno nástroje potřebuje zpracovat 96 DPI, Windows bude zpracovávat všechna ostatní dpi. Výsledkem je mírně rozmazaný obsah.
- Systém znamená, že okno nástroje potřebuje pro rozlišení DPI primárního displeje zpracovat DPI. Jakékoli zobrazení s porovnávacím DPI bude vypadat ostře, ale pokud se rozlišení DPI liší nebo se změní během relace, Windows zpracuje měřítko a bude mírně rozmazaný.
- PerMonitor znamená, že okno nástroje musí zpracovat všechny dpi všech displejů a vždy, když se změní DPI.

> [!NOTE]
> Visual Studio podporuje pouze sledování PerMonitorV2, takže hodnota výčtu PerMonitor se překládá na hodnotu Windows DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

#### <a name="force-a-control-into-a-specific-dpiawarenesscontext"></a>Vynucení ovládacího prvku na konkrétní DpiAwarenessContext

Starší uživatelské rozhraní, které není aktualizováno pro podporu režimu PMA, může stále vyžadovat drobné vylepšení, aby fungovalo, když je Visual Studio spuštěno v režimu PMA. Jedna taková oprava zahrnuje ujištění, že se uživatelské rozhraní vytváří ve správném DpiAwarenessContext. K vynucení uživatelského rozhraní do konkrétního DpiAwarenessContext můžete zadat rozsah DPI s následujícím kódem:

```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> Vynucení DpiAwarenessContext funguje jenom v dialogových oknech, které nejsou WPF, a na nejvyšší úrovni. Při vytváření uživatelského rozhraní WPF, které má být hostováno v oknech nástrojů nebo návrhářích, jakmile bude obsah vložen do stromu uživatelského rozhraní WPF, bude převeden na aktuální DpiAwarenessContext procesu.

## <a name="known-issues"></a>Známé problémy

### <a name="windows-forms"></a>Windows Forms

Pro optimalizaci pro nové scénáře se smíšeným režimem model Windows Forms změnit způsob vytváření ovládacích prvků a oken vždy, když jejich nadřazený objekt nebyl explicitně nastaven. Dříve ovládací prvky bez explicitního nadřazeného objektu používaly interní "parkovací okno" jako dočasný nadřazený prvek pro vytvoření ovládacího prvku nebo okna. 

Před rozhraním .NET 4,8 bylo k dispozici jedno "parkovací okno", které získá své DpiAwarenessContext z aktuálního kontextu sledování rozlišení DPI vlákna v čase vytvoření okna. Jakékoli nenadřazené ovládací prvky zdědí stejný DpiAwarenessContext jako zaparkování, když je vytvořen popisovač ovládacího prvku a by měl být nadřízen pro finální/očekávaný nadřízený modul vývojář aplikace. To by způsobilo selhání založené na časování, pokud "zaparkované" okno má vyšší DpiAwarenessContext než konečné nadřazené okno.

Od rozhraní .NET 4,8 je nyní "parkování" okno pro každý DpiAwarenessContext, který byl zjištěn. Dalším významným rozdílem je, že DpiAwarenessContext, který se používá pro ovládací prvek, je uložen do mezipaměti při vytvoření ovládacího prvku, nikoli při vytvoření popisovače. To znamená, že celkové chování je stejné, ale může aktivovat, které z nich se bude vydávat podle časování, do konzistentního problému. Poskytuje také vývojářům aplikací více deterministické chování při psaní kódu uživatelského rozhraní a jeho správnému určení jeho oboru.
