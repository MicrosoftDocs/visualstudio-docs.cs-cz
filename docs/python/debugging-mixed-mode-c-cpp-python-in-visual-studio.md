---
title: Ve smíšeném režimu ladění pro Python
description: Ladění současně C++ a Python v sadě Visual Studio, včetně krokování mezi prostředími, zobrazení hodnot a vyhodnocení výrazů.
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
ms.sourcegitcommit: 0d8488329263cc0743a89d43f6de863028e982ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/06/2020
ms.locfileid: "75678997"
---
# <a name="debug-python-and-c-together"></a>Společně ladění Pythonu a C++

Většině běžných ladicí programy Python podporu ladění pouze kódu v Pythonu. V praxi však Python se používá ve spojení s C nebo C++ v scénářům, které vyžadují vysoký výkon nebo možnost přímo vyvolat rozhraní API platformy. (Viz [vytvoření rozšíření C++ pro Python](working-with-c-cpp-python-in-visual-studio.md) návod.)

Visual Studio poskytuje integrované, současné ladění ve smíšeném režimu pro Python a nativní C/C++, za předpokladu, že jste vybrali **nástroje Pythonu pro nativní vývoj** možnost **vývoj v jazyce Python** úlohy v instalačním programu sady Visual Studio.

> [!Note]
> Ladění ve smíšeném režimu není k dispozici s nástroji Python Tools for Visual Studio 1.x v sadě Visual Studio 2015 a starší.

Funkce ladění ve smíšeném režimu patří, jak je popsáno v tomto článku:

- Kombinované volání zásobníků
- Krok mezi Python a nativní kód
- Zarážky v obou typech kódu
- Zobrazit Python reprezentace objektů v nativní rámce a naopak
- Ladění v kontextu projektu Pythonu nebo projektu jazyka C++

![Ladění ve smíšeném režimu pro Python v sadě Visual Studio](media/mixed-mode-debugging.png)

|   |   |
|---|---|
| ![ikona filmové kamery pro video](../install/media/video-icon.png "Podívejte se na video") | Úvod do vytváření, testování a ladění nativních modulů jazyka C pomocí sady Visual Studio, naleznete v tématu [podrobně: vytvořit nativní moduly](https://youtu.be/D9RlT06a1EI) (webu youtube.com, 9 min 09s). Video se vztahuje na Visual Studio 2015 a 2017. |

## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Povolit ladění ve smíšeném režimu v projektu Pythonu

1. Klikněte pravým tlačítkem na projekt Python v **Průzkumníka řešení**vyberte **vlastnosti**, vyberte **ladění** kartu a potom vyberte **povolit ladění nativního kódu** . Tato možnost povolí ve smíšeném režimu pro všechny ladicí relace.

    ![Povolení ladění nativního kódu](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Když povolíte ladění nativního kódu, v okně výstupu Pythonu může zmizet ihned po dokončení programu bez získáte obvyklého **stisknutím libovolné klávesy pokračovat** pozastavit. K vynucení pozastavení, přidejte `-i` umožňuje **spustit** > **argumenty pro interpret** pole na **ladění** kartě povolit ladění nativního kódu . Tento argument vloží interpret Pythonu v interaktivním režimu po dokončení kódu, kdy čeká na stisknutí klávesy **Ctrl**+**Z** > **Enter**  ukončíte.

1. Při připojování ladicího programu smíšeného režimu k existujícímu procesu (**ladění** > **připojit k procesu**), použijte **vyberte** tlačítko Otevřít  **Vyberte typ kódu** dialogového okna. Nastavte **ladit tyto typy kódu** možnost a vyberte možnost **nativní** a **Python** v seznamu:

    ![Vyberte typy kódu nativní a Python](media/mixed-mode-debugging-code-type.png)

    Nastavení typu kódu jsou trvalé, takže pokud chcete zakázat ladění v kombinovaném režimu při připojování k jiným procesem později, zrušte **Python** kódu typu.

    Je možné vybrat jiné typy kódu kromě nebo namísto něj **nativní**. Například pokud spravované aplikace hostuje CPython, které v důsledku využívá nativní rozšiřující moduly a chcete ladit všechny tři, můžete zkontrolovat **Python**, **nativní**, a **spravované**společně sjednocené prostředí pro ladění včetně kombinované volání zásobníků a krokování mezi všechny tři moduly runtime.

1. Při zahájení ladění ve smíšeném režimu poprvé, může se zobrazit **vyžaduje symboly Pythonu** dialogového okna (naleznete v tématu [symboly pro ladění ve smíšeném režimu](debugging-symbols-for-mixed-mode-c-cpp-python.md)). Je potřeba nainstalovat symboly pouze jednou pro jakékoli dané prostředí Pythonu. Symboly jsou automaticky zahrnuty, pokud nainstalujete podporu Pythonu prostřednictvím instalačního programu sady Visual Studio (Visual Studio 2017 a novější).

1. K dispozici zdrojový kód pro standardní Python samotné ladění, navštivte [ https://www.python.org/downloads/source/ ](https://www.python.org/downloads/source/), stáhněte archiv odpovídá vaší verzi a rozbalte ho do složky. Můžete pak bodu vás vyzve k sadě Visual Studio na konkrétní soubory v této složce na cokoli, co bod.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>Povolit ladění ve smíšeném režimu v projektu jazyka C/C++

Visual Studio (2017 verze 15,5 a novější) podporuje ladění ve smíšeném režimu z C/C++ Project (například při [vkládání Pythonu do jiné aplikace, jak je popsáno v Python.org](https://docs.python.org/3/extending/embedding.html)). Pokud chcete povolit ladění ve smíšeném režimu, konfigurace projektu jazyka C/C++ ke spuštění **Python/nativní ladění**:

1. Klikněte pravým tlačítkem na projekt C/C++ v **Průzkumníka řešení** a vyberte **vlastnosti**.
1. Vyberte **ladění** kartu, vyberte možnost **Python/nativní ladění** z **ladicí program ke spuštění**a vyberte **OK**.

    ![Výběr ladicího programu Python/nativní v projektu jazyka C/C++](media/mixed-mode-debugging-select-cpp-debugger.png)

> [!Note]
> Pokud nemáte možnost vybrat **ladění v Pythonu/nativní** , musíte nejdřív nainstalovat **nativní vývojové nástroje Pythonu** pomocí instalačního programu vs. Můžete ji najít jako možnost v rámci úlohy vývoje v Pythonu. Další informace najdete v tématu [Instalace podpory Pythonu v aplikaci Visual Studio ve Windows](installing-python-support-in-visual-studio.md).

Pomocí této metody, mějte na paměti, že nelze ladit *py.exe* Spouštěč samostatně, protože vytvoří podřízený *python.exe* proces, který ladicí program nebude připojen k. Pokud chcete spustit *python.exe* přímo s argumenty, změnit **příkaz** možnost **Python/nativní ladění** vlastností (viz předchozí obrázek) Zadejte úplnou cestu k *python.exe*, zadejte argumenty v **argumenty příkazu**.

### <a name="attaching-the-mixed-mode-debugger"></a>Připojování ladicího programu ve smíšeném režimu

Pro všechny předchozí verze sady Visual Studio, s přímým přístupem ve smíšeném režimu je povoleno ladění pouze při spuštění projektu Pythonu v sadě Visual Studio, protože projekty C/C++, použijte jenom nativní ladicí program. Můžete však připojit ladicí program samostatně:

1. Spustit bez ladění projektu jazyka C++ (**ladění** > **spustit bez ladění** nebo **Ctrl**+**F5**) .
1. Vyberte **ladění** > **připojit k procesu**. V dialogovém okně, které se zobrazí, vyberte příslušný proces, pak použijte **vyberte** tlačítko Otevřít **vybrat typ kódu** dialogové okno, ve kterém můžete vybrat **Python**:

    ![Výběr Python jako typ ladění, který při připojování ladicího programu](media/mixed-mode-debugging-attach-type.png)

1. Vyberte **OK** pak zavřete tento dialog **připojit** spuštění ladicího programu.
1. Budete muset představují vhodný pozastavení nebo zpoždění v C++ aplikaci, aby zajistila, že nevolá kód Pythonu, který chcete ladit, než budete mít příležitost dobře se připojit ladicí program.

## <a name="mixed-mode-specific-features"></a>Konkrétní funkce ve smíšeném režimu

- [Kombinované volání zásobníku](#combined-call-stack)
- [Krok mezi Python a nativní kód](#step-between-python-and-native-code)
- [PyObject zobrazení hodnoty v nativním kódu](#pyobject-values-view-in-native-code)
- [Zobrazit nativní hodnoty v kódu Pythonu](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Kombinované volání zásobníku

**Zásobník volání** okno zobrazuje nativní i proloženy přechodů mezi těmito dvěma označené rámce zásobníků Pythonu:

![Zásobník volání kombinované pomocí ladění ve smíšeném režimu](media/mixed-mode-debugging-call-stack.png)

Přechody se zobrazí jako **[externí kód]** , bez zadání směr přechodu je, pokud **nástroje** > **možnosti**  >  **Ladění** > **Obecné** > **povolit volbu pouze vlastní kód** je možnost nastavená.

Dvojitým kliknutím jiné rámce volání stane aktivní a otevře příslušného zdrojového kódu, pokud je to možné. Pokud není k dispozici zdrojový kód, rámce stále se stane aktivní a můžete ho zkontrolovat lokální proměnné.

### <a name="step-between-python-and-native-code"></a>Krok mezi Python a nativní kód

Při použití **Krokovat s vnořením** (**F11**) nebo **Krokovat s Vystoupením** (**Shift**+**F11**) příkazy, ladění ve smíšeném režimu správně zpracovává změny mezi typy kódu. Například když Python volá metodu typu, která je implementována v jazyce C, krokování volání, že metoda zastaví na začátku nativní funkce implementace metody. Podobně když nativní kód volá některé funkce rozhraní API Python, který výsledky v kódu Pythonu vyvolání. Například krokování s vnořením `PyObject_CallObject` na hodnotu funkce, která byla původně definována v Pythonu zastaví na začátku funkce jazyka Python. Krokování Pythonu do nativní je také podporována pro nativní funkce vyvolána z Pythonu pomocí [ctypes](https://docs.python.org/3/library/ctypes.html).

### <a name="pyobject-values-view-in-native-code"></a>PyObject zobrazení hodnoty v nativním kódu

Při aktivním je nativní rámec (C nebo C++) své místní proměnné zobrazí v ladicím programu **lokální** okna. V nativní rozšiřující moduly Pythonu, mnoho z těchto proměnných jsou typu `PyObject` (což je definice typu `_object`), nebo několik dalších základních typů Pythonu (viz seznam níže). V kombinovaném režimu ladění, tyto hodnoty k dispozici další podřízený uzel s názvem **[zobrazení Pythonu]** . Po rozbalení tento uzel zobrazuje reprezentace Python proměnné, shodné s co se zobrazí-li místní proměnná odkazuje na stejný objekt nacházel v rámci Python. Podřízené položky tohoto uzlu se upravovat.

![Zobrazení Pythonu v okně místních hodnot](media/mixed-mode-debugging-python-view.png)

Tuto funkci zakázat, klikněte pravým tlačítkem kamkoli **lokální** okno a přepnout **Python** > **zobrazit uzly zobrazení Pythonu** nabídky:

![Povoluje zobrazení Pythonu v okně místních hodnot](media/mixed-mode-debugging-enable-python-view.png)

C typy, které zobrazují **[zobrazení Pythonu]** uzly (je-li povoleno):

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

**[Zobrazení Pythonu]**  nezobrazí automaticky pro typy vytvořte sami. Při vytváření rozšíření pro Python 3.x, tento nedostatek není obvykle problém, protože jakýkoli objekt nakonec má `ob_base` pole jednoho z typů výše, které způsobí, že **[zobrazení Pythonu]** zobrazit.

Pro jazyk Python 2.x, ale jeho záhlaví pro každý typ objektu obvykle deklaruje jako kolekce vložených polí a neexistuje žádná souvislost mezi vlastní typy vytvořené a `PyObject` na úrovni systému typu v kódu C/C++. Povolit **[zobrazení Pythonu]** Upravit uzly pro vlastní typy, *PythonDkm.natvis* soubor [instalační adresář nástroje Python tools](installing-python-support-in-visual-studio.md#install-locations)a přidat jiný element v XML pro Struktura jazyka C nebo C++ třídy.

Možnost alternativního (a vyšší), je splnění [období 3123](https://www.python.org/dev/peps/pep-3123/) a použít explicitní `PyObject ob_base;` pole spíše než `PyObject_HEAD`, ale které nemusí být vždy možné z důvodů zpětné kompatibility.

### <a name="native-values-view-in-python-code"></a>Zobrazit nativní hodnoty v kódu Pythonu

Podobně jako v předchozí části, můžete povolit **[C++ zobrazení]** nativní hodnoty v **lokální** okno, když je aktivní blok Python. Tato funkce není povolená ve výchozím nastavení, takže zapnete ho kliknutím pravým tlačítkem myši v **lokální** okno a přepnete **Python** > **zobrazit uzly zobrazení C++** nabídky možnost.

![Povolení C++ zobrazení v okně místních hodnot](media/mixed-mode-debugging-enable-cpp-view.png)

**[C++ zobrazení]** uzel poskytuje reprezentaci podkladová struktura jazyka C/C++ pro hodnoty, na co se zobrazí v je nativní rámec stejné. Příklad ukazuje instanci `_longobject` (pro který `PyLongObject` je definice typu) pro Python dlouhé celé číslo který se pokusí odvodit typy pro nativní třídy, které jste vytvořili sami. Podřízené položky tohoto uzlu se upravovat.

![C++ zobrazení v okně místních hodnot](media/mixed-mode-debugging-cpp-view.png)

Pokud je pole podřízeného objektu typu `PyObject`, nebo jednoho z jiných podporované typy, pak má **[zobrazení Pythonu]** reprezentace uzel (pokud jsou povolené tyto reprezentace), což umožňuje přejít objekt grafů where odkazy nejsou přímo zveřejněné Python.

Na rozdíl od **[zobrazení Pythonu]** uzly, které používají metadata objektu Python k určení typu objektu, není žádný podobně spolehlivé mechanismus pro **[C++ zobrazení]** . Obecně řečeno byla přidělena hodnota Pythonu (to znamená, `PyObject` odkaz) není možné spolehlivě zjistit, které struktura jazyka C/C++ se zálohuje. Ladění ve smíšeném režimu se pokusí odhadnout typu zobrazením různých polí typu objektu (například `PyTypeObject` odkazovaná jeho `ob_type` pole), které mají typy ukazatelů na funkci. Pokud jeden z těchto ukazatelů na funkce odkazuje na funkci, která lze vyřešit a má tuto funkci `self` parametr s typem konkrétnější než `PyObject*`, pak tento typ se považuje za základního typu. Například pokud `ob_type->tp_init` bodů zadaný objekt na následující funkce:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

pak ladicí program správně odvodit, jestli je typ C objektu `FobObject`. Pokud není schopen určit přesnější typ z `tp_init`, přesune jiné pole. Pokud nemůže odvodit typ z některého z těchto polí **[C++ zobrazení]** uzel prezentuje jako objekt `PyObject` instance.

Vždy získat užitečný reprezentaci pro vlastní typy vytvořené, je nejlepší a zaregistrujte se aspoň jeden speciální funkce při registraci typ, použijte silného typu `self` parametru. Většina typů splnění tohoto požadavku přirozeně; Pokud to není případ, pak `tp_init` je obvykle nejpohodlnější záznam, který má k tomuto účelu nepoužívat. Fiktivní implementace `tp_init` pro typ, který je k dispozici pouze pokud chcete povolit typ ladicího programu odvození můžete jenom vrací nulu okamžitě, stejně jako v ukázkovém kódu výše.

## <a name="differences-from-standard-python-debugging"></a>Rozdíl oproti standardní ladění Pythonu

Ladění ve smíšeném režimu se liší od [standardní ladicího programu Python](debugging-python-in-visual-studio.md) , zavádí některé další funkce, ale chybí některé funkce související s Pythonu:

- Nepodporované funkce: podmíněné zarážky, **interaktivní ladění** okno a vzdálené ladění napříč platformami.
- **Okamžité** okna: je k dispozici ale s omezenou podmnožinou jeho funkce, včetně všech omezení uvedené tady.
- Podporované verze Pythonu: CPython 2.7 a 3.3 + pouze.
- Prostředí sady Visual Studio: Při použití Pythonu s prostředí sady Visual Studio (například pokud jste nainstalovali pomocí integrovaného instalační program), Visual Studio nedokáže otevřít projekty v jazyce C++ a možnosti úprav souborů C++ je pouze základní textového editoru. Ale ladění jazyka C/C++ a ladění ve smíšeném režimu jsou plně podporované v prostředí se zdrojovým kódem, krokování s vnořením do nativního kódu a C++ vyhodnocení výrazu v oknech ladicího programu.
- Zobrazení a rozbalení objektů: při zobrazení Pythonu objekty v **lokální** a **Watch** ladicího programu nástroje systému windows, kombinovaný režim ladění zobrazuje pouze strukturu objektů. Automaticky se vyhodnotí vlastnosti nebo Zobrazit počítané atributy. Pro kolekce, zobrazuje pouze prvky pro předdefinovanou kolekci typů (`tuple`, `list`, `dict`, `set`). Typy vlastních kolekcí nejsou vizualizovat jako kolekce, pokud jsou zděděny z některé předdefinované kolekce typu.
- Vyhodnocení výrazu: viz níže.

### <a name="expression-evaluation"></a>Vyhodnocení výrazu

Standardní ladicího programu Python umožňuje vyhodnocení libovolné výrazy Pythonu v **Watch** a **okamžité** časová období, pokud se laděný proces je pozastaven v libovolném bodě v kódu, tak dlouho, dokud není blokován vstupně-výstupní operace nebo jiné podobné volání systému. Libovolné výrazy v kombinovaném režimu ladění, může být vyhodnocen pouze v případě, že v kódu Pythonu, zastaví po zarážku, nebo při krokování s vnořením do kódu. Výrazy lze vyhodnotit pouze ve vlákně, na kterém zarážky a krokování operace došlo k chybě.

Při zastavení v nativním kódu nebo v kódu Pythonu, kde výše uvedené podmínky se nedá použít (například po operaci vystoupení, nebo v jiném vlákně), je omezený přístup k místní a globální proměnné v oboru aktuálně vybraného vyhodnocení výrazu rámce, přístup k jejich polí a indexování typů předdefinovaných kolekcí s literály. Například následující výraz může být vyhodnocen v jakýkoli kontext (za předpokladu, že všechny identifikátory odkazovat na existující proměnné a pole typů odpovídající):

```python
foo.bar[0].baz['key']
```

Kombinovaný režim ladění také řeší tyto výrazy odlišně. Všechny operace přístupu ke členům vyhledat pouze pole, které jsou přímo součástí objektu (například záznam v jeho `__dict__` nebo `__slots__`, nebo pole nativní struktury, která je vystavena Python prostřednictvím `tp_members`) a ignorovat jakékoli `__getattr__`, `__getattribute__`nebo popisovač logiku. Podobně, všechny operace indexování Ignorovat `__getitem__`a získat přímo přístup k vnitřní datové struktury kolekcí.

Pro účely konzistence toto schéma rozlišení názvu se používá pro všechny výrazy, které odpovídají omezení pro vyhodnocení výrazu omezené, bez ohledu na to, zda jsou povoleny libovolné výrazy do aktuálního místa stop. K vynucení správné sémantiku Pythonu při Chyba při vyhodnocování plně funkční je k dispozici, použijte výraz v závorkách:

```python
(foo.bar[0].baz['key'])
```
