---
title: Ladění v kombinovaném režimu pro Python
description: Současně ladit C++ a Python v sadě Visual Studio, včetně krokování mezi prostředími, zobrazení hodnot a vyhodnocení výrazů.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bc90d659a32c14f92e1eff058dd22d4a17d0b1cb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75678997"
---
# <a name="debug-python-and-c-together"></a>Ladění Pythonu a C++ společně

Většina běžných ladicích programů Pythonu podporuje ladění pouze kódu Pythonu. V praxi se však Python používá ve spojení s C nebo C++ ve scénářích, které vyžadují vysoký výkon nebo schopnost přímo vyvolat platformu API. (Viz [Vytvoření rozšíření C++ pro Python](working-with-c-cpp-python-in-visual-studio.md) pro návod.)

Visual Studio poskytuje integrované, simultánní ladění v kombinovaném režimu pro Python a nativní C/C++za předpokladu, že vyberete možnost **nativních vývojových nástrojů Pythonu** pro úlohu **vývoje Pythonu** v instalačním programu Visual Studia.

> [!Note]
> Ladění ve smíšeném režimu není k dispozici s nástroji Pythonu pro Visual Studio 1.x ve Visual Studiu 2015 a starších.

Funkce ladění ve smíšeném režimu zahrnují následující, jak je vysvětleno v tomto článku:

- Kombinované zásobníky volání
- Krok mezi Pythonem a nativním kódem
- Zarážky v obou typech kódu
- Viz Reprezentace objektů v Pythonu v nativních rámech a naopak
- Ladění v kontextu projektu Pythonu nebo projektu C++

![Ladění v kombinovaném režimu pro Python v sadě Visual Studio](media/mixed-mode-debugging.png)

|   |   |
|---|---|
| ![ikona filmové kamery pro video](../install/media/video-icon.png "Podívejte se na video") | Úvod do vytváření, testování a ladění nativních modulů C pomocí sady Visual Studio najdete [v tématu Podrobné informace: Vytvoření nativních modulů](https://youtu.be/D9RlT06a1EI) (youtube.com, 9 m 09s). Video se vztahuje na Visual Studio 2015 a 2017. |

## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Povolení ladění ve smíšeném režimu v projektu Pythonu

1. Klepněte pravým tlačítkem myši na projekt Pythonu v **Průzkumníku řešení**, vyberte **vlastnosti**, vyberte kartu **Ladění** a pak vyberte **Povolit nativní ladění kódu**. Tato možnost umožňuje smíšený režim pro všechny relace ladění.

    ![Povolení ladění nativního kódu](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Když povolíte ladění nativního kódu, výstupní okno Pythonu může okamžitě zmizet po dokončení programu, aniž by vám obvyklý **Mačkání libovolné klávesy pokračovat** pauza. Chcete-li vynutit `-i` pozastavení, přidejte možnost do pole **Spustit** > **argumenty interpretu** na kartě **Ladění,** když povolíte ladění nativního kódu. Tento argument přepne interpret Pythonu do interaktivního režimu po dokončení kódu, v tomto okamžiku čeká na stisknutí **klávesy Ctrl**+**Z** > **Enter** ukončit.

1. Při připojování ladicího programu ve smíšeném režimu k existujícímu procesu **(Ladění** > **připojení k procesu**) otevřete dialogové okno Vybrat typ **kódu** pomocí tlačítka **Vybrat.** Pak nastavte možnost **Ladit tyto typy kódu** a vyberte v seznamu **nativní** i **Python:**

    ![Výběr typů kódu Nativní a Python](media/mixed-mode-debugging-code-type.png)

    Nastavení typu kódu jsou trvalé, takže pokud chcete zakázat ladění ve smíšeném režimu při pozdějším připojení k jinému procesu, zrušte kód **Pythonu.**

    Je možné vybrat jiné typy kódu kromě nebo **nativní**. Například pokud spravovaná aplikace hostuje CPython, který zase používá nativní rozšiřující moduly a chcete ladit všechny tři, můžete zkontrolovat **Python**, **Native**a **Managed** společně pro jednotné ladění prostředí, včetně kombinované zásobníky volání a krokování mezi všechny tři runtimes.

1. Při prvním spuštění ladění ve smíšeném režimu se může zobrazit dialogové okno **Vyžadováno symboly Pythonu** (viz [Symboly pro ladění ve smíšeném režimu).](debugging-symbols-for-mixed-mode-c-cpp-python.md) Symboly je třeba nainstalovat pouze jednou pro dané prostředí Pythonu. Symboly se automaticky zahrnou, pokud nainstalujete podporu Pythonu prostřednictvím instalačního programu Visual Studia (Visual Studio 2017 a novější).

1. Chcete-li při ladění zpřístupnit zdrojový kód pro samotný [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/)standardní Python, navštivte , stáhněte archiv vhodný pro vaši verzi a extrahujte jej do složky. Potom bod Visual Studio na konkrétní soubory v této složce v libovolném okamžiku, který vás vyzve.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>Povolení ladění ve smíšeném režimu v projektu C/C++

Visual Studio (2017 verze 15.5 a novější) podporuje ladění ve smíšeném režimu z projektu C/C++ (například [při vkládání Pythonu do jiné aplikace, jak je popsáno na python.org](https://docs.python.org/3/extending/embedding.html)). Chcete-li povolit ladění ve smíšeném režimu, nakonfigurujte projekt C/C++ tak, aby spouštěl **ladění Pythonu/Nativního**ladění :

1. Klepněte pravým tlačítkem myši na projekt C/C++ v **Průzkumníku řešení** a vyberte **příkaz Vlastnosti**.
1. Vyberte kartu **Ladění,** vyberte **python/nativní ladění** z **ladicího programu, který chcete spustit**, a vyberte **OK**.

    ![Výběr ladicího programu Python/Native v projektu C/C++](media/mixed-mode-debugging-select-cpp-debugger.png)

> [!Note]
> Pokud nemáte možnost vybrat **Python/Nativní ladění,** musíte nejprve nainstalovat **nativní vývojové nástroje Pythonu** pomocí instalačního programu VS. Najdete ji jako možnost v rámci úlohy vývoje Pythonu. Další informace naleznete v tématu [Jak nainstalovat podporu Pythonu v sadě Visual Studio v systému Windows](installing-python-support-in-visual-studio.md).

Pomocí této metody uvědomte, že nelze ladit *py.exe* launcher sám, protože spouští podřízený *python.exe* proces, který ladicí program nebude připojen. Pokud chcete spustit *python.exe* přímo s argumenty, změňte volbu **Příkaz** ve vlastnostech **Ladění Python/Nativní** (zobrazené na předchozím obrázku) a určete úplnou cestu k *python.exe*, pak zadejte argumenty v **argumentech příkazu**.

### <a name="attaching-the-mixed-mode-debugger"></a>Připojení ladicího programu ve smíšeném režimu

Pro všechny předchozí verze sady Visual Studio přímé ladění ve smíšeném režimu je povoleno pouze při spuštění projektu Pythonu v sadě Visual Studio, protože projekty C/C++ používají pouze nativní ladicí program. Ladicí program však můžete připojit samostatně:

1. Spusťte projekt Jazyka C++ bez ladění (**Ladění** > **start bez ladění** nebo **Ctrl**+**F5**).
1. Vyberte **možnost Připojit k procesu** > **Attach to Process**. V zobrazeném dialogovém okně vyberte příslušný proces a pomocí tlačítka **Vybrat** otevřete dialogové okno **Vybrat typ kódu,** ve kterém můžete vybrat **Python**:

    ![Výběr Pythonu jako typu ladění při připojování ladicího programu](media/mixed-mode-debugging-attach-type.png)

1. Chcete-li tento dialog zavřít, vyberte **OK** a **potom připojit** k zahájení ladicího programu.
1. Možná budete muset zavést vhodné pozastavení nebo zpoždění v aplikaci C++, abyste zajistili, že nezavolá kód Pythonu, který chcete ladit, než budete mít možnost připojit ladicí program.

## <a name="mixed-mode-specific-features"></a>Specifické funkce smíšeného režimu

- [Kombinovaný zásobník volání](#combined-call-stack)
- [Krok mezi Pythonem a nativním kódem](#step-between-python-and-native-code)
- [Zobrazení hodnot PyObject v nativním kódu](#pyobject-values-view-in-native-code)
- [Zobrazení nativních hodnot v kódu Pythonu](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Kombinovaný zásobník volání

Okno **Zásobník volání** zobrazuje prokládané rámce zásobníku i rámce pythonu s prokládanými snímky s přechody označenými mezi těmito dvěma:

![Kombinovaný zásobník volání s laděním v kombinovaném režimu](media/mixed-mode-debugging-call-stack.png)

Přechody se zobrazí jako **[Externí kód]**, bez určení směru přechodu, pokud je**nastavena** > možnost**Možnosti** >  **ladění nástrojů** > **obecné** > **povolit pouze můj kód.**

Poklepáním na libovolný rámec volání je aktivní a pokud je to možné, otevře příslušný zdrojový kód. Pokud zdrojový kód není k dispozici, rámec je stále aktivní a místní proměnné mohou být kontrolovány.

### <a name="step-between-python-and-native-code"></a>Krok mezi Pythonem a nativním kódem

Při použití příkazů **Krok do** (**F11**) nebo **Krok ven** **(Shift**+**F11)** ladicí program správně zpracovává změny mezi typy kódu. Například když Python volá metodu typu, který je implementován v Jazyce C, krokování na volání této metody se zastaví na začátku nativní funkce implementace metody. Podobně při volání nativního kódu některé funkce rozhraní API Pythonu, která má za následek vyvolání kódu Pythonu. Například krokování `PyObject_CallObject` do hodnoty funkce, která byla původně definována v Pythonu, se zastaví na začátku funkce Pythonu. Krokování z Pythonu do nativního je také podporováno pro nativní funkce vyvolané z Pythonu přes [ctypes](https://docs.python.org/3/library/ctypes.html).

### <a name="pyobject-values-view-in-native-code"></a>Zobrazení hodnot PyObject v nativním kódu

Když je aktivní nativní (C nebo C++), jeho místní proměnné se zobrazí v okně **Místní** ladicího programu. V nativních rozšiřujících modulech Pythonu `PyObject` je mnoho z těchto `_object`proměnných typu (což je typedef pro ) nebo několik dalších základních typů Pythonu (viz seznam níže). V ladění ve smíšeném režimu tyto hodnoty představují další podřízený uzel s názvem **[Python view]**. Při rozbalení tento uzel zobrazuje reprezentaci pythonu proměnné, identickou s tím, co byste viděli, pokud byla v rámci Pythonu přítomna místní proměnná odkazující na stejný objekt. Podřízené položky tohoto uzlu lze upravit.

![Zobrazení Pythonu v okně Locals](media/mixed-mode-debugging-python-view.png)

Chcete-li tuto funkci zakázat, klepněte pravým **Python** > tlačítkem myši na libovolné místo v okně **Locals** a přepněte možnost nabídky**Python Show Python View Nodes:**

![Povolení zobrazení Pythonu v okně Locals](media/mixed-mode-debugging-enable-python-view.png)

Typy C, které zobrazují uzly **[Zobrazení Pythonu]** (pokud jsou povoleny):

- `PyObject`
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

**[Zobrazení Pythonu]** se automaticky nezobrazí u typů, které sami vytváříte. Při vytváření rozšíření pro Python 3.x, tento nedostatek obvykle není problém, `ob_base` protože jakýkoli objekt má nakonec pole jednoho z výše uvedených typů, což způsobí, že **[Python zobrazení]** se zobrazí.

Pro Python 2.x však každý typ objektu obvykle deklaruje jeho záhlaví jako kolekci vložkových polí a neexistuje žádné přidružení mezi vlastními typy autorských souborů a `PyObject` na úrovni systému typů v kódu C/C++. Chcete-li povolit uzly **[zobrazení Pythonu]** pro tyto vlastní typy, upravte soubor *PythonDkm.natvis* v [adresáři instalace nástrojů Pythonu](installing-python-support-in-visual-studio.md#install-locations)a přidejte další prvek do XML pro třídu C struct nebo C++.

Alternativní (a lepší) možnost je sledovat [PEP 3123](https://www.python.org/dev/peps/pep-3123/) a používat explicitní `PyObject ob_base;` pole spíše než `PyObject_HEAD`, i když to nemusí být vždy možné z důvodů zpětné kompatibility.

### <a name="native-values-view-in-python-code"></a>Zobrazení nativních hodnot v kódu Pythonu

Podobně jako v předchozí části můžete povolit **[C++ zobrazení]** pro nativní hodnoty v okně **Locals,** když je aktivní rámeček Pythonu. Tato funkce není ve výchozím nastavení povolena, takže ji zapnete kliknutím pravým **Python** > tlačítkem myši v okně **Locals** a přepnutím nabídky Python**Show C++ Zobrazit uzly.**

![Povolení zobrazení jazyka C++ v okně Locals](media/mixed-mode-debugging-enable-cpp-view.png)

Uzel **[C++ view]** poskytuje reprezentaci základní struktury C/C++ pro hodnotu, shodnou s tím, co byste viděli v nativním rámci. Například zobrazuje instanci `_longobject` (pro `PyLongObject` který je typedef) pro Python dlouhé celé číslo a pokusí se odvodit typy pro nativní třídy, které jste vytvořili sami. Podřízené položky tohoto uzlu lze upravit.

![Zobrazení C++ v okně Locals](media/mixed-mode-debugging-cpp-view.png)

Pokud podřízené pole objektu `PyObject`je typu nebo jeden z dalších podporovaných typů, pak má **[Python view]** reprezentace uzlu (pokud jsou povoleny tyto reprezentace), takže je možné procházet objektové grafy, kde odkazy nejsou přímo vystaveny Python.

Na rozdíl od uzlů **[Python view],** které používají metadata objektu Pythonu k určení typu objektu, neexistuje žádný podobně spolehlivý mechanismus pro **[zobrazení C++].** Obecně řečeno, vzhledem k hodnotě `PyObject` Pythonu (to znamená odkaz) není možné spolehlivě určit, která struktura C/C++ ji podporuje. Ladicí program ve smíšeném režimu se pokusí uhodnout tento typ při `PyTypeObject` pohledu na `ob_type` různá pole typu objektu (například odkazovaný jeho polem), které mají typy ukazatelů funkce. Pokud jeden z těchto ukazatelů funkce odkazuje na funkci, kterou `self` lze přeložit, a `PyObject*`tato funkce má parametr s typem specifičtějším než , pak se předpokládá, že tento typ je typ zálohování. Například pokud `ob_type->tp_init` daný objekt odkazuje na následující funkci:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

pak ladicí program může správně odvodit, že `FobObject`typ C objektu je . Pokud není schopen určit přesnější typ `tp_init`z , přesune se do jiných polí. Pokud není schopen odvodit typ z některého z těchto polí, uzel **[C++ view]** představuje objekt jako `PyObject` instanci.

Chcete-li vždy získat užitečnou reprezentaci pro vlastní typy, je nejlepší zaregistrovat alespoň jednu speciální funkci `self` při registraci typu a použít parametr silného typu. Většina typů splnit tento požadavek přirozeně; pokud tomu tak není, `tp_init` pak je obvykle nejvhodnější vstup pro tento účel. Fiktivní implementace `tp_init` pro typ, který je k dispozici pouze pro povolení odvození typu ladicího programu můžete vrátit nulu okamžitě, jako v vzorku výše.

## <a name="differences-from-standard-python-debugging"></a>Rozdíly od standardního ladění Pythonu

Ladicí program ve smíšeném režimu se liší od [standardního ladicího programu Pythonu](debugging-python-in-visual-studio.md) v tom, že zavádí některé další funkce, ale postrádá některé funkce související s Pythonem:

- Nepodporované funkce: podmíněné zarážky, **interaktivní ladění** okna a vzdálené ladění mezi platformami.
- **Okamžité** okno: je k dispozici, ale s omezenou podmnožinou jeho funkčnosti, včetně všech omezení zde uvedených.
- Podporované verze Pythonu: pouze CPython 2.7 a 3.3+.
- Prostředí Visual Studio: Při použití Pythonu s prostředím Visual Studio (například pokud jste jej nainstalovali pomocí integrovaného instalačního programu), Visual Studio nemůže otevřít projekty jazyka C++ a možnosti úprav pro soubory jazyka C++ je pouze základní textový editor. Ladění jazyka C/C++ a ladění ve smíšeném režimu jsou však plně podporovány v prostředí se zdrojovým kódem, krokování do nativního kódu a vyhodnocení výrazu C++ v oknech ladicího programu.
- Zobrazení a rozbalení objektů: Při zobrazení objektů Pythonu v oknech nástroje místní **a** popisný kód **sledování** zobrazuje ladicí program ve smíšeném režimu pouze strukturu objektů. Nevyhoduje automaticky vlastnosti ani nezobrazuje vypočítané atributy. Pro kolekce zobrazuje pouze prvky pro předdefinované`tuple` `list`typy `dict` `set`kolekcí ( , , . ). Vlastní typy kolekcí nejsou vizualizovány jako kolekce, pokud nejsou zděděny z některé hotového typu kolekce.
- Vyhodnocení výrazu: viz níže.

### <a name="expression-evaluation"></a>Vyhodnocení výrazu

Standardní ladicí program Pythonu umožňuje vyhodnocení libovolných výrazů Pythonu v **oknech Watch** a **Immediate,** když je laděný proces pozastaven v libovolném bodě kódu, pokud není blokován v operaci vstupně-v., nebo v jiném podobném systémovém volání. V ladění ve smíšeném režimu lze libovolné výrazy vyhodnotit pouze při zastavení v kódu Pythonu, po zarážky nebo při krokování do kódu. Výrazy lze vyhodnotit pouze ve vlákně, ve kterém došlo k zarážky nebo krokování operace.

Při zastavení v nativním kódu nebo v kódu Pythonu, kde výše uvedené podmínky neplatí (například po operaci step-out nebo v jiném vlákně), vyhodnocení výrazu je omezeno na přístup k místním a globálním proměnným v rozsahu aktuálně vybraného rámec, přístup k jejich pole a indexování předdefinované typy kolekcí s literály. Například následující výraz může být vyhodnocen v libovolném kontextu (za předpokladu, že všechny identifikátory odkazují na existující proměnné a pole vhodných typů):

```python
foo.bar[0].baz['key']
```

Ladicí program ve smíšeném režimu také řeší tyto výrazy odlišně. Všechny operace přístupu členů vyhledávají pouze pole, která jsou přímo `__dict__` součástí `__slots__`objektu (například položka v jeho nebo `tp_members`, nebo `__getattr__` `__getattribute__` pole nativní struktury, která je vystavena Pythonu přes ) a ignorovat všechny nebo deskriptor logiky. Podobně všechny operace indexování `__getitem__`ignorovat a přístup k vnitřní datové struktury kolekcí přímo.

Z důvodu konzistence se toto schéma překladu názvů používá pro všechny výrazy, které odpovídají omezením pro vyhodnocení omezeného výrazu, bez ohledu na to, zda jsou v aktuálním bodu zastavení povoleny libovolné výrazy. Chcete-li vynutit správnou sémantiku Pythonu, když je k dispozici plně vybavený vyhodnocení, uzavřete výraz do závorek:

```python
(foo.bar[0].baz['key'])
```
