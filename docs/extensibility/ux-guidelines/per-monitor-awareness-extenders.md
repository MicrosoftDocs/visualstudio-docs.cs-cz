---
title: Zvýšení povědomí o podpoře pro rozšířené služby sady Visual Studio pro jednotlivé monitory
titleSuffix: ''
description: Přečtěte si o novém podpoře rozšířené podpory pro monitorování pro jednotlivé monitory, které jsou k dispozici v aplikaci Visual Studio 2019.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: conceptual
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 09ec5d82251fa4598096fca8a59c9a1fd29e3f27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "69585371"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Zvýšení povědomí o podpoře pro rozšířené služby sady Visual Studio pro jednotlivé monitory

Verze před sadou Visual Studio 2019 měly svůj kontext sledování DPI nastavený na systém, nikoli rozlišení DPI na monitoru (PMA). Výsledkem sledování systému bylo zhoršení vizuálního prostředí (např. rozmazaných písem nebo ikon), kdykoli se Visual Studio muselo vykreslovat mezi monitory s různými faktory škálování nebo vzdáleně v počítačích s různými konfiguracemi displeje (například s různými škálováními Windows).

Kontext sledování DPI v sadě Visual Studio 2019 je nastaven jako PMA, když ho prostředí podporuje, což umožňuje, aby se sada Visual Studio vykreslila v závislosti na konfiguraci displeje, kde je hostovaná, a ne v jednom systémem definované konfiguraci. Nakonec se přeloží na vždy ostřené uživatelské rozhraní pro oblasti Surface, které podporují režim PMA.

Další informace o pojmech a celkovém scénáři popsaných v tomto dokumentu najdete v dokumentaci pro [vývoj desktopových aplikací s vysokým rozlišením DPI v dokumentaci Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) .

## <a name="quickstart"></a>Rychlé zprovoznění

- Zajistěte, aby v režimu PMA běžela aplikace Visual Studio (viz **Povolení PMA**).

- Ověřte, že rozšíření funguje správně v rámci sady běžných scénářů (viz **testování vašich rozšíření pro problémy PMA**).

- Pokud zjistíte problémy, můžete k jejich diagnostikování a opravě použít strategie/doporučení popsaná v tomto dokumentu. Také budete muset přidat nový balíček NuGet [Microsoft. VisualStudio. DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) do vašeho projektu pro přístup k požadovaným rozhraním API.

## <a name="enable-pma"></a>Povolit PMA

Chcete-li povolit PMA v aplikaci Visual Studio, je třeba splnit následující požadavky:

- Windows 10 duben 2018 Update (v1803, RS4) nebo novější
- .NET Framework 4,8 RTM nebo vyšší
- Visual Studio 2019 s povolenou možností [optimalizovat vykreslování pro obrazovky s různou hustotou pixelů](../../ide/reference/general-environment-options-dialog-box.md)

Po splnění těchto požadavků Visual Studio automaticky povolí režim PMA napříč procesem.

> [!NOTE]
> Model Windows Forms obsah v aplikaci Visual Studio (například prohlížeč vlastností) podporuje PMA pouze v případě, že máte Visual Studio 2019 verze 16,1 nebo novější.

## <a name="test-your-extensions-for-pma-issues"></a>Testování rozšíření pro problémy s PMA

Visual Studio oficiálně podporuje architektury uživatelského rozhraní WPF, model Windows Forms, Win32 a HTML/JS. Když je sada Visual Studio přepnuta do režimu PMA, každý zásobník uživatelského rozhraní se chová jinak. Bez ohledu na architekturu uživatelského rozhraní se proto doporučuje provést test Pass, aby bylo zajištěno, že veškeré uživatelské rozhraní bude kompatibilní s režimem PMA.

Doporučuje se ověřit následující běžné scénáře:

- Změna faktoru škálování jednoho monitorovaného prostředí, když je aplikace spuštěná.

  Tento scénář pomáhá otestovat, že uživatelské rozhraní reaguje na změnu rozlišení DPI pro dynamickou systém Windows.

- Ukotvení/odkování přenosného počítače, kde je připojené monitorování nastaveno na primární a připojené monitorování má jiný faktor škálování než přenosný počítač, když je aplikace spuštěná.

  Tento scénář pomáhá otestovat, že uživatelské rozhraní reaguje na změnu rozlišení DPI a že se dynamicky přidávají nebo odebírají zobrazení.

- Máte několik monitorů s různými faktory škálování a mezi nimi přesunete aplikaci.

  Tento scénář pomáhá otestovat, že uživatelské rozhraní reaguje na změnu rozlišení DPI.
    
- Vzdálená komunikace v počítači, pokud mají místní a vzdálené počítače různé faktory škálování pro primární monitorování.

  Tento scénář pomáhá otestovat, že uživatelské rozhraní reaguje na změnu rozlišení DPI pro dynamickou systém Windows.

Dobrý předběžný test na to, jestli vaše uživatelské rozhraní může mít problémy, je, jestli kód používá třídy *Microsoft. VisualStudio. Utilities. dpi. DpiHelper*, *Microsoft. VisualStudio. PlatformUI. DpiHelper*nebo *vsui nebyla rozpoznána:: CDpiHelper* . Tyto staré třídy DpiHelper podporují pouze systémové sledování DPI a při PMA procesu vždy nefungují správně.

Typické použití těchto DpiHelpers bude vypadat takto:

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

V předchozím příkladu je obdélník reprezentující logické hranice okna převeden na jednotky zařízení, aby jej bylo možné předat nativní metodě MonitorFromPoint, která očekává souřadnice zařízení, aby vracela přesný ukazatel monitorování.

### <a name="classes-of-issues"></a>Třídy problémů
Když je pro Visual Studio povolený režim PMA, uživatelské rozhraní může replikovat problémy několika běžnými způsoby. Většina, pokud k těmto problémům dojde, se může vyskytnout v rámci podporovaných rozhraní .NET studia pro sadu Visual Studio. K těmto potížím může také docházet, když je část uživatelského rozhraní hostována ve scénářích škály DPI ve smíšeném režimu (Další informace najdete v [dokumentaci](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) k systému Windows). 

#### <a name="win32-window-creation"></a>Vytvoření okna Win32
Při vytváření oken pomocí funkce CreateWindow () nebo CreateWindowEx () je běžným vzorem vytvoření okna v souřadnicích (0, 0) (horní nebo levý roh primárního zobrazení) a jeho přesunutí na poslední pozici. Nicméně to může způsobit, že okno spustí zprávu nebo událost se změněnou hodnotou DPI, která může znovu aktivovat jiné zprávy uživatelského rozhraní nebo události a nakonec vést k neočekávanému chování nebo vykreslování.

#### <a name="wpf-element-placement"></a>Umístění elementu WPF
Při přesunu prvků WPF pomocí starého rozhraní Microsoft. VisualStudio. Utilities. dpi. DpiHelper se souřadnice v levém horním rohu nemusí správně vypočítat, pokud jsou prvky na neprimárním typu DPI.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serializace velikostí a umístění prvků uživatelského rozhraní
Pokud je velikost nebo pozice uživatelského rozhraní (Pokud je uložená jako jednotky zařízení) obnovena v jiném kontextu DPI, než bylo uloženo v, bude umístění a velikost nesprávně umístěna. K tomu dochází, protože jednotky zařízení mají vlastní vztah DPI.

#### <a name="incorrect-scaling"></a>Nesprávné škálování
Prvky uživatelského rozhraní vytvořené na primárním DPI se budou škálovat správně, ale když se přesunou na obrazovku s jiným DPI, nemění se jejich škálování a jejich obsah je moc velký nebo moc malý.

#### <a name="incorrect-bounding"></a>Nesprávné ohraničování
Podobně jako při potížích s škálováním prvky uživatelského rozhraní počítají jejich meze správně v primárním kontextu DPI, ale při přesunu na neprimární DPI nebudou nové meze vypočítány správně. V takovém případě je okno obsahu příliš malé nebo příliš velké v porovnání s hostujícím uživatelským rozhraním, které má za následek prázdné místo nebo oříznutí.

#### <a name="drag--drop"></a>Přetažení &
Vždy, když jsou scénáře DPI ve smíšeném režimu (například různé prvky uživatelského rozhraní, které se vykreslují v různých režimech sledování DPI), mohou být souřadnice přetažení nesprávně vypočítány, což vede k nesprávnému ukončení konečné pozice odkládací složky.

#### <a name="out-of-process-ui"></a>Uživatelské rozhraní mimo procesy
Některé uživatelské rozhraní se vytvořilo mimo proces a pokud je vytvoření externího procesu v jiném režimu sledování DPI než Visual Studio, může to vést k některému z předchozích problémů vykreslování.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Nesprávně generované ovládací prvky, obrázky nebo zobrazení model Windows Forms
Ne všechen model Windows Forms obsah podporuje režim PMA. V důsledku toho se může zobrazit problém vykreslování s nesprávným rozložením nebo škálováním. V tomto případě je možné, že v tomto případě výslovně vykreslíte model Windows Forms obsah v části "systémově závislé" DpiAwarenessContext ( [vynutíte si ovládací prvek pro konkrétní DpiAwarenessContext](#force-a-control-into-a-specific-dpiawarenesscontext)).

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Nezobrazení ovládacích prvků model Windows Forms nebo oken
Jedním z hlavních příčin tohoto problému jsou vývojáři, kteří se pokoušejí znovu vytvořit nadřazený ovládací prvek nebo okno s jedním DpiAwarenessContext do okna s jiným DpiAwarenessContext.

Následující obrázky znázorňují aktuální **výchozí** omezení operačního systému Windows v nadřazených oknech:

![Snímek obrazovky se správným chováním nadřazeného objektu](media/PMA-parenting-behavior.PNG)

> [!Note]
> Toto chování můžete změnit nastavením chování hostování vlákna (informace o [Dpi_Hosting_Behavior výčtu](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)).

V důsledku toho, pokud nastavíte vztah nadřazenosti-podřízenosti mezi nepodporovanými režimy, selže a ovládací prvek nebo okno nebude možné vykreslit podle očekávání.

### <a name="diagnose-issues"></a>Diagnostika problémů

Při identifikaci problémů souvisejících s PMA je potřeba vzít v úvahu mnoho faktorů: 

- Očekává uživatelské rozhraní nebo rozhraní API logické hodnoty nebo hodnoty zařízení?
    - Uživatelské rozhraní a rozhraní API WPF obvykle používají logické hodnoty (ale ne vždycky).
    - Rozhraní Win32 UI a rozhraní API obvykle používají hodnoty zařízení.

- Kde jsou hodnoty přicházející?
    - Pokud přijímáte hodnoty z jiného uživatelského rozhraní nebo rozhraní API, předává zařízení nebo logické hodnoty.
    - Pokud jsou přijímány hodnoty z více zdrojů, všechny používají/očekávají stejné typy hodnot, nebo je nutné převody spojit a porovnat?

- Používají se konstanty uživatelského rozhraní a na kterých formulářích jsou?

- Je vlákno ve správném kontextu DPI pro hodnoty, které přijímá?

  Změny, které umožňují smíšené hostování přes DPI, by měly obecně vkládat cesty kódu do správného kontextu, ale práce prováděná mimo hlavní smyčku zpráv nebo tok událostí se může provádět v nesprávném kontextu DPI.

- Jsou hranice kontextu mezi jednotlivými rozlišeními mezi DPI?

  Přetažení & je běžné situaci, kdy souřadnice mohou překračovat kontexty DPI. Okno se pokusí provést správnou věc, ale v některých případech může být nutné, aby uživatelské rozhraní hostitele mohlo provést převod, aby se zajistilo, že se shodují hranice kontextu.

### <a name="pma-nuget-package"></a>Balíček NuGet PMA
Nové knihovny DpiAwarness lze nalézt v balíčku NuGet [Microsoft. VisualStudio. DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) .

### <a name="recommended-tools"></a>Doporučené nástroje
Následující nástroje mohou přispět k ladění problémů souvisejících s PMA napříč některými různými zásobníky uživatelského rozhraní, které podporuje Visual Studio.

#### <a name="snoop"></a>Sledování
Snoop je ladicí nástroj XAML, který obsahuje některé další funkce, které integrované nástroje Visual Studio XAML nemají. Snoop navíc nemusí aktivně ladit Visual Studio, aby bylo možné zobrazit a vylepšit jeho uživatelské rozhraní WPF. Dva hlavní způsoby ověřování pro modul Snoop mohou být užitečné pro diagnostiku problémů PMA je pro ověřování souřadnic logických umístění nebo mezí velikosti a pro ověření uživatelského rozhraní má správné rozlišení DPI.
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio – nástroje XAML
Podobně jako monitorování, mohou nástroje XAML v aplikaci Visual Studio pomáhat s diagnostikou PMA problémů. Po nalezení pravděpodobná příčinou můžete nastavit zarážky a použít okno živého vizuálního stromu stejně jako okna ladění, chcete-li zkontrolovat hranice uživatelského rozhraní a aktuální DPI.

## <a name="strategies-for-fixing-pma-issues"></a>Strategie pro řešení problémů s PMA

### <a name="replace-dpihelper-calls"></a>Nahradit volání DpiHelper

Ve většině případů je možné opravit problémy uživatelského rozhraní v režimu PMA a nahradit volání ve spravovaném kódu na staré třídy *Microsoft. VisualStudio. Utilities. dpi. DpiHelper* a *Microsoft. VisualStudio. PlatformUI. DpiHelper* s voláním do nové pomocné třídy *Microsoft. VisualStudio. Utilities. DpiAwareness* . 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

V případě nativního kódu bude mít za následek nahrazení volání staré třídy *vsui nebyla rozpoznána:: CDpiHelper* s voláními nové třídy *Vsui nebyla rozpoznána:: CDpiAwareness* . 

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

Nové třídy DpiAwareness a CDpiAwareness nabízejí stejné pomocníky převodu jednotek jako třídy DpiHelper, ale vyžadují další vstupní parametr: prvek uživatelského rozhraní, který se použije jako odkaz pro operaci převodu. Je důležité si uvědomit, že v nových pomocníkech DpiAwareness/CDpiAwareness neexistují a v případě potřeby by měl být místo toho použit [ImageService](../image-service-and-catalog.md) .

Spravovaná třída DpiAwareness nabízí nápovědu pro vizuály WPF, model Windows Forms ovládací prvky a Win32 HWND a HMONITORs (jak ve formě IntPtr), zatímco nativní třída CDpiAwareness nabízí pomocníky HWND a HMONITOR.

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
