---
title: Ladění ve smíšeném režimu pro Python
description: Současně ladit C++ a Python v aplikaci Visual Studio, včetně krokování mezi prostředími, zobrazením hodnot a vyhodnocování výrazů.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 0b55a0bbeee7c5a8c38a0df61db0a1b17ae5e033
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238657"
---
# <a name="debug-python-and-c-together"></a>Ladění Pythonu a C++ společně

Většina běžných ladicích programů Pythonu podporuje ladění pouze kódu Pythonu. V praxi se ale Python používá ve spojení s C nebo C++ ve scénářích, které vyžadují vysoký výkon nebo schopnost přímo vyvolat rozhraní API platformy. (Podrobné pokyny najdete v tématu [Vytvoření rozšíření C++ pro Python](working-with-c-cpp-python-in-visual-studio.md) .)

Visual Studio poskytuje integrované a souběžné ladění ve smíšeném režimu pro Python a nativní jazyky C/C++ za předpokladu, že vyberete možnost **nativní vývojové nástroje Pythonu** pro úlohu vývoje v jazyce **Python** v instalačním programu sady Visual Studio.

> [!Note]
> Ladění ve smíšeném režimu není k dispozici v Python Tools for Visual Studio 1. x v aplikaci Visual Studio 2015 a starší.

Mezi funkce ladění ve smíšeném režimu patří následující, jak je vysvětleno v tomto článku:

- Kombinované zásobníky volání
- Krok mezi Pythonem a nativním kódem
- Zarážky v obou typech kódu
- Viz reprezentace objektů Pythonu v nativních rámečcích a naopak.
- Ladění v rámci kontextu projektu Python nebo projektu C++

![Ladění ve smíšeném režimu pro Python v aplikaci Visual Studio](media/mixed-mode-debugging.png)

![ikona filmové kamery pro video](../install/media/video-icon.png "Přehrát video") Úvod k sestavování, testování a ladění nativních modulů jazyka C v aplikaci Visual Studio naleznete v tématu [hluboká podrobně: vytváření nativních modulů](https://youtu.be/D9RlT06a1EI) (YouTube.com, 9 min 09s). Video se vztahuje i na Visual Studio 2015 i 2017.


## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Povolit ladění ve smíšeném režimu v projektu Pythonu

1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt Pythonu, vyberte **vlastnosti**, vyberte kartu **ladění** a pak vyberte **Povolit ladění nativního kódu**. Tato možnost povolí smíšený režim pro všechny relace ladění.

    ![Povolení ladění nativního kódu](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Pokud povolíte ladění nativního kódu, okno výstupu Pythonu se může okamžitě po dokončení programu zmizet, aniž by to mělo za normální **stisknutí klávesy pro pokračování** . Chcete-li vynutit pozastavení, přidejte `-i` možnost do **Run**  >  pole**argumenty Run interpretu** na kartě **ladění** , když povolíte ladění nativního kódu. Tento argument vloží interpret Pythonu do interaktivního režimu po dokončení kódu, a v takovém případě počká na stisknutí klávesy **CTRL** + **Z**klávesy  >  **ENTER** k ukončení.

1. Při připojování ladicího programu smíšeného režimu ke stávajícímu**procesu (**  >  **připojit k procesu**) použijte tlačítko **Vybrat** a otevřete dialogové okno **Vybrat typ kódu** . Pak nastavte možnost **ladit tyto typy kódu** a v seznamu vyberte jak **nativní** , tak **Python** :

    ![Výběr nativních typů kódu a kódů Pythonu](media/mixed-mode-debugging-code-type.png)

    Nastavení typu kódu jsou trvalá, takže pokud chcete zakázat ladění v kombinovaném režimu při pozdějším připojení k jinému procesu, vymažte typ kódu **Python** .

    Je možné vybrat další typy kódu kromě, nebo namísto **nativního**. Například pokud spravovaná aplikace hostuje CPython, která zase používá nativní rozšiřující moduly, a chcete všechny tři ladit, můžete v rámci sjednoceného ladění, včetně kombinovaných zásobníků volání a rozkrokování mezi všemi třemi moduly runtime, zaškrtnout společné prostředí **Python**, **nativní**a **spravované** .

1. Při prvním spuštění ladění ve smíšeném režimu se může zobrazit dialogové okno **požadované symboly Pythonu** (viz [symboly pro ladění ve smíšeném režimu](debugging-symbols-for-mixed-mode-c-cpp-python.md)). Pro každé dané prostředí Pythonu je třeba nainstalovat symboly pouze jednou. Symboly jsou automaticky zahrnuty, pokud nainstalujete podporu Pythonu prostřednictvím instalačního programu sady Visual Studio (Visual Studio 2017 a novější).

1. Chcete-li, aby byl zdrojový kód pro standardní Python dostupný při ladění, navštivte [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/) , Stáhněte si archiv odpovídající vaší verzi a extrahujte ji do složky. Pak budete aplikaci Visual Studio ukazovat na konkrétní soubory v dané složce v jakémkoli okamžiku, kdy vás vyzve.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>Povolit ladění v kombinovaném režimu v projektu C/C++

Visual Studio (2017 verze 15,5 a novější) podporuje ladění ve smíšeném režimu z projektu C/C++ (například při [vkládání Pythonu do jiné aplikace, jak je popsáno v Python.org](https://docs.python.org/3/extending/embedding.html)). Chcete-li povolit ladění ve smíšeném režimu, nakonfigurujte projekt C/C++ tak, aby spouštěl jazyk **Python/nativní ladění**:

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt C/C++ a vyberte **vlastnosti**.
1. Vyberte kartu **ladění** , pro spuštění vyberte **Python/nativní ladění** z **ladicího programu**a vyberte **OK**.

    ![Výběr ladicího programu Python/nativní v projektu jazyka C/C++](media/mixed-mode-debugging-select-cpp-debugger.png)

> [!Note]
> Pokud nemáte možnost vybrat **ladění v Pythonu/nativní** , musíte nejdřív nainstalovat **nativní vývojové nástroje Pythonu** pomocí instalačního programu vs. Můžete ji najít jako možnost v rámci úlohy vývoje v Pythonu. Další informace najdete v tématu [Instalace podpory Pythonu v aplikaci Visual Studio ve Windows](installing-python-support-in-visual-studio.md).

Pomocí této metody mějte na paměti, že nemůžete ladit samotnou spouštěcí službu *py.exe* , protože vytvoří podřízený proces *python.exe* , ke kterému ladicí program nebude připojen. Pokud chcete spustit *python.exe* přímo s argumenty, změňte možnost **příkazu** ve vlastnostech **ladění Python/Native** (zobrazené na předchozím obrázku) a zadejte úplnou cestu k *python.exe*a pak zadejte argumenty v **argumentech příkazů**.

### <a name="attaching-the-mixed-mode-debugger"></a>Připojuje se ladicí program smíšeného režimu.

Pro všechny předchozí verze sady Visual Studio je přímé ladění v kombinovaném režimu povoleno pouze při spuštění projektu v jazyce Python v aplikaci Visual Studio, protože projekty C/C++ používají pouze nativní ladicí program. Ladicí program je však možné připojit samostatně:

1. Spusťte projekt C++ bez ladění (**ladění**  >  **začněte bez ladění** nebo **CTRL** + **F5**).
1. Vyberte **ladit**  >  **připojit k procesu**. V zobrazeném dialogovém okně vyberte příslušný proces a pak pomocí tlačítka **Vybrat** otevřete dialog **Vybrat typ kódu** , ve kterém můžete vybrat **Python**:

    ![Výběr Pythonu jako typu ladění při připojení ladicího programu](media/mixed-mode-debugging-attach-type.png)

1. Výběrem **OK** zavřete toto dialogové okno a pak se **Připojte** ke spuštění ladicího programu.
1. V aplikaci C++ možná budete muset zavést vhodné pozastavení nebo zpoždění, abyste zajistili, že nevolají kód Pythonu, který chcete ladit, předtím, než budete mít možnost připojit ladicí program.

## <a name="mixed-mode-specific-features"></a>Funkce specifické pro smíšený režim

- [Kombinovaný zásobník volání](#combined-call-stack)
- [Krok mezi Pythonem a nativním kódem](#step-between-python-and-native-code)
- [Zobrazení hodnot PyObject v nativním kódu](#pyobject-values-view-in-native-code)
- [Zobrazení nativních hodnot v kódu Pythonu](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Kombinovaný zásobník volání

Okno **zásobník volání** zobrazuje prokládaný rámec zásobníku zásobníku v Pythonu, s přechody označenými mezi tyto dvě:

![Kombinovaný zásobník volání s laděním ve smíšeném režimu](media/mixed-mode-debugging-call-stack.png)

Přechody se zobrazí jako **[externí kód]** bez určení směru přechodu, pokud **Tools**  >  **Options**  >  **Debugging**  >  je nastavena možnost nástroje ladění**Obecné**  >  **povolení pouze můj kód** .

Dvojím kliknutím na libovolný rámec volání je aktivní a otevře se odpovídající zdrojový kód, pokud je to možné. Pokud není zdrojový kód k dispozici, je snímek stále aktivní a místní proměnné lze kontrolovat.

### <a name="step-between-python-and-native-code"></a>Krok mezi Pythonem a nativním kódem

Při použití příkazů **Krokovat** s vnořením (**F11**) nebo **Krok ven** (**SHIFT** + **F11**) správně zpracovává ladicí program kombinovaného režimu změny mezi typy kódu. Například když Python volá metodu typu, který je implementován v jazyce C, krokování volání této metody zastaví na začátku nativní funkce implementující metodu. Podobně, pokud nativní kód volá určitou funkci Python API, která vede k vyvolání kódu Pythonu. Například krokování `PyObject_CallObject` na hodnotu funkce, která byla původně definována v Pythonu, zaniká na začátku funkce jazyka Python. Pro nativní funkce vyvolané z Pythonu prostřednictvím [ctypes](https://docs.python.org/3/library/ctypes.html)se podporuje taky krokování z Pythonu na nativní.

### <a name="pyobject-values-view-in-native-code"></a>Zobrazení hodnot PyObject v nativním kódu

Když je aktivní rámec (C nebo C++) aktivní, jeho místní proměnné se zobrazí v okně **místní** ladicí program. V nativních rozšiřujících modulech Pythonu je mnoho z těchto proměnných typu `PyObject` (což je definice TypeDef pro `_object` ) nebo několik dalších základních typů Pythonu (viz seznam níže). V ladění ve smíšeném režimu tyto hodnoty prezentují další podřízený uzel označený **[zobrazení Python]**. Když je rozbalený, tento uzel zobrazuje reprezentace proměnné v jazyce Python, která je shodná s tím, co se vám ukáže, zda se v rámci Pythonu objevila místní proměnná odkazující na stejný objekt. Podřízené objekty tohoto uzlu jsou editovatelné.

![Zobrazení Pythonu v okně místních hodnot](media/mixed-mode-debugging-python-view.png)

Chcete-li tuto funkci zakázat, klikněte pravým tlačítkem myši kdekoli v okně **místní** hodnoty **Python**a přepněte  >  možnost nabídky Zobrazit**uzly zobrazení** v Pythonu:

![Povolení zobrazení v Pythonu v okně místních hodnot](media/mixed-mode-debugging-enable-python-view.png)

Typy jazyka C, které zobrazují **[zobrazení Python]** uzly (Pokud je povoleno):

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

**[Zobrazení Python]** se automaticky nezobrazuje pro typy, které sami vytváříte. Při vytváření rozšíření pro Python 3. x to není obvykle problém, protože libovolný objekt má nakonec `ob_base` pole jednoho z výše uvedených typů, což způsobuje, že se zobrazí **[zobrazení Python]** .

Pro Python 2. x však každý typ objektu obvykle deklaruje své záhlaví jako kolekci vložených polí a neexistuje žádné přidružení mezi vlastními vytvořenými typy a `PyObject` na úrovni systému typu v kódu C/C++. Chcete-li pro tyto vlastní typy povolit uzly **[zobrazení Pythonu]** , upravte soubor *PythonDkm. Natvis* v [instalačním adresáři nástrojů Pythonu](installing-python-support-in-visual-studio.md#install-locations)a přidejte další prvek do XML pro vaši strukturu jazyka C nebo třídu C++.

Alternativná (a lepší) možnost je sledovat [PEP 3123](https://www.python.org/dev/peps/pep-3123/) a místo toho použít explicitní `PyObject ob_base;` pole, ale `PyObject_HEAD` nemusí být vždy možné z důvodů zpětné kompatibility.

### <a name="native-values-view-in-python-code"></a>Zobrazení nativních hodnot v kódu Pythonu

Podobně jako v předchozí části můžete povolit **[zobrazení C++]** pro nativní hodnoty v okně **místních** hodnot, když je aktivní rámec Pythonu. Tato funkce není ve výchozím nastavení povolená, takže ji zapnete kliknutím pravým tlačítkem myši v okně **místní** hodnoty a přepnutím možnosti nabídky Zobrazit **Python**  >  **uzly zobrazení C++** v Pythonu.

![Povolení zobrazení C++ v okně místních hodnot](media/mixed-mode-debugging-enable-cpp-view.png)

Uzel **[zobrazení C++]** poskytuje reprezentaci základní struktury C/C++ pro hodnotu shodnou s tím, co se v nativním rámci zobrazuje. Například ukazuje instanci `_longobject` (pro kterou `PyLongObject` je definice typedef) pro dlouhé celé číslo Pythonu a snaží se odvodit typy pro nativní třídy, které jste vytvořili sami. Podřízené objekty tohoto uzlu jsou editovatelné.

![Zobrazení C++ v okně místních hodnot](media/mixed-mode-debugging-cpp-view.png)

Pokud je podřízené pole objektu typu `PyObject` nebo jeden z ostatních podporovaných typů, pak má uzel reprezentace **[zobrazení v Pythonu]** (pokud jsou tyto reprezentace povoleny), což umožňuje procházet grafy objektů, ve kterých nejsou odkazy přímo vystaveny Pythonu.

Na rozdíl od **[zobrazení Python]** uzly, které používají metadata objektu Python k určení typu objektu, neexistuje podobně spolehlivý mechanismus pro **[zobrazení C++]**. Obecně řečeno, s ohledem na hodnotu Pythonu (to znamená `PyObject` odkaz), není možné spolehlivě určit, která struktura C/C++ ho zálohuje. Ladicí program se smíšeným režimem se pokusí tento typ odhadnout zobrazením různých polí typu objektu (například `PyTypeObject` odkazovaná pomocí `ob_type` pole), který má typy ukazatelů na funkce. Pokud jeden z těchto ukazatelů na funkci odkazuje na funkci, která může být vyřešena, a tato funkce má `self` parametr s typem konkrétnějším, než `PyObject*` je tento typ považován za typ zálohování. Například pokud `ob_type->tp_init` určitý objekt odkazuje na následující funkci:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

ladicí program pak může správně odvodit, že typ C objektu je `FobObject` . Pokud není možné určit přesnější typ z `tp_init` , přesune se do jiných polí. Pokud není možné odvodit typ z některého z těchto polí, uzel **[zobrazení C++]** prezentuje objekt jako `PyObject` instanci.

Chcete-li vždy získat užitečnou reprezentaci pro vlastní vytvořené typy, je vhodné zaregistrovat alespoň jednu speciální funkci při registraci typu a použít parametr silného typu `self` . Většina typů splní tento požadavek přirozeně; Pokud tomu tak není, `tp_init` je obvykle nejvhodnější položka, která se má pro tento účel použít. Fiktivní implementace `tp_init` pro typ, který je přítomen výhradně pro povolení odvození typu ladicího programu, může vracet pouze nulu ihned, jako v ukázce kódu výše.

## <a name="differences-from-standard-python-debugging"></a>Rozdíly oproti standardnímu ladění v Pythonu

Ladicí program ve smíšeném režimu se liší od [standardního ladicího programu v Pythonu](debugging-python-in-visual-studio.md) , který zavádí některé další funkce, ale nemá některé funkce související s Pythonem:

- Nepodporované funkce: podmíněné zarážky, **ladění interaktivního** okna a vzdálené ladění pro různé platformy.
- **Okamžité** okno: je k dispozici, ale s omezeným podmnožinou jeho funkcí včetně všech omezení uvedených tady.
- Podporované verze Pythonu: jenom CPython 2,7 a 3.3 +.
- Prostředí sady Visual Studio: při použití Pythonu s prostředím Visual Studio (například pokud jste ho nainstalovali pomocí integrovaného instalačního programu), Visual Studio nemůže otevřít projekty C++ a prostředí pro úpravy pro soubory C++ je pouze základní textový editor. Ladění C/C++ a ladění v kombinovaném režimu jsou však plně podporovány v prostředí se zdrojovým kódem, krokování do nativního kódu a vyhodnocení výrazu jazyka C++ v oknech ladicího programu.
- Zobrazení a rozbalování objektů: při zobrazení objektů v jazyce Python v oknech nástrojů **místní** a **sledovacího** ladicího programu se v ladicím programu smíšeného režimu zobrazí pouze struktura objektů. Neprovádí automaticky vyhodnocení vlastností ani nezobrazuje počítané atributy. Pro kolekce se zobrazí pouze prvky pro předdefinované typy kolekcí ( `tuple` , `list` , `dict` , `set` ). Vlastní typy kolekcí nejsou rozvizuálněelné jako kolekce, pokud nejsou děděny z nějakého předdefinovaného typu kolekce.
- Vyhodnocení výrazu: viz níže.

### <a name="expression-evaluation"></a>Vyhodnocení výrazu

Standardní ladicí program Python umožňuje vyhodnocování libovolných výrazů Pythonu v **kukátk** a **okamžitých** oknech v případě, že je laděný proces pozastaven v jakémkoli bodě kódu, pokud není zablokovaný v vstupně-výstupních operacích nebo podobném systémovém volání. V ladění ve smíšeném režimu lze libovolné výrazy vyhodnotit pouze v případě, že jsou v kódu Pythonu, po zarážce nebo při krokování do kódu. Výrazy lze vyhodnotit pouze ve vlákně, ve kterém došlo k zarážce nebo operaci krokování.

Když se zastaví v nativním kódu nebo v kódu Pythonu, kde se výše uvedené podmínky nevztahují (například po operaci krokování nebo v jiném vlákně), vyhodnocení výrazu je omezené na přístup k místním a globálním proměnným v oboru aktuálně vybraného rámce, přístupu k jejich polím a indexování předdefinovaných typů kolekcí s literály. Například následující výraz může být vyhodnocen v jakémkoli kontextu (za předpokladu, že všechny identifikátory odkazují na existující proměnné a pole příslušných typů):

```python
foo.bar[0].baz['key']
```

Ladicí program smíšeného režimu také tyto výrazy vyřeší odlišně. Všechny operace přístupu členů vyhledávají pouze pole, která jsou přímo součástí objektu (například zadání v jeho `__dict__` nebo `__slots__` nebo poli nativní struktury, která je k dispozici v Pythonu prostřednictvím `tp_members` ), a ignorujte všechny `__getattr__` `__getattribute__` nebo logiku deskriptoru. Podobně se všechny operace indexování ignorují `__getitem__` a mají přímý přístup k vnitřním datovým strukturám kolekcí.

Pro účely konzistence se toto schéma překladu IP adres používá pro všechny výrazy, které odpovídají omezením pro vyhodnocení omezeného výrazu, bez ohledu na to, jestli jsou v aktuálním bodě zastavení povolené libovolné výrazy. Pokud chcete vynutit správnou sémantiku Pythonu, když je dostupný kompletní vyhodnocovací filtr, uveďte výraz v závorkách:

```python
(foo.bar[0].baz['key'])
```
