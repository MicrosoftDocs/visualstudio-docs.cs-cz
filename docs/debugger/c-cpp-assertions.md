---
title: Kontrolní výrazy jazyka C/C++ | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: f7ac27b46252582b3982082a2a9a90a09223574f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72911609"
---
# <a name="cc-assertions"></a>Kontrolní výrazy jazyka C/C++
Příkaz kontrolního výrazu Určuje podmínku, kterou očekáváte, že bude platit v bodě programu. Pokud tato podmínka není pravdivá, kontrolní výraz se nezdařil, provádění programu je přerušeno a zobrazí se [dialogové okno kontrolní výraz selhal](../debugger/assertion-failed-dialog-box.md) .

Visual Studio podporuje příkazy kontrolního výrazu jazyka C++, které jsou založeny na následujících konstrukcích:

- Kontrolní výrazy MFC pro programy MFC.

- [ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) pro programy, které používají ATL.

- Kontrolní výrazy CRT pro programy, které používají knihovnu run-time jazyka C.

- [Funkce kontrolního výrazu](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) ANSI pro ostatní programy C/C++.

  Můžete použít kontrolní výrazy k zachycení logických chyb, kontrole výsledků operace a podmínek testování chyb, které by měly být zpracovány.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> V tomto tématu
[Jak fungují kontrolní výrazy](#BKMK_How_assertions_work)

[Kontrolní výrazy v sestaveních pro ladění a vydání](#BKMK_Assertions_in_Debug_and_Release_builds)

[Vedlejší účinky použití kontrolních výrazů](#BKMK_Side_effects_of_using_assertions)

[Kontrolní výrazy CRT](#BKMK_CRT_assertions)

[Kontrolní výrazy MFC](#BKMK_MFC_assertions)

- [MFC ASSERT_VALID a CObject:: AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)

- [Omezení AssertValid](#BKMK_Limitations_of_AssertValid)

  [Použití kontrolních výrazů](#BKMK_Using_assertions)

- [Zachycení chyb logiky](#BKMK_Catching_logic_errors)

- [Kontrola výsledků](#BKMK_Checking_results_)

- [Hledají se neošetřené chyby.](#BKMK_Testing_error_conditions_)

## <a name="how-assertions-work"></a><a name="BKMK_How_assertions_work"></a> Jak fungují kontrolní výrazy
Pokud se ladicí program zastaví z důvodu kontrolního výrazu běhové knihovny MFC nebo C, pak ladicí program přejde do bodu ve zdrojovém souboru, kde došlo k kontrolnímu výrazu. Zpráva kontrolního výrazu se zobrazí jak v [okně výstup](../ide/reference/output-window.md) , tak v dialogovém okně **kontrolního výrazu se nezdařilo** . Můžete zkopírovat zprávu kontrolního výrazu z okna **výstup** do textového okna, pokud ho chcete uložit pro pozdější použití. Okno **výstup** může obsahovat také další chybové zprávy. Pečlivě zkontrolujte tyto zprávy, protože poskytují zprávy o příčině selhání kontrolního výrazu.

Použijte kontrolní výrazy k detekci chyb během vývoje. Jako pravidlo použijte jeden kontrolní výraz pro každý předpoklad. Například pokud předpokládáte, že argument není NULL, použijte k otestování tohoto předpokladu kontrolní výraz.

[V tomto tématu](#BKMK_In_this_topic)

## <a name="assertions-in-debug-and-release-builds"></a><a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Kontrolní výrazy v sestaveních pro ladění a vydání
Příkazy kontrolního výrazu lze zkompilovat pouze v případě `_DEBUG` , že je definován. V opačném případě kompilátor považuje kontrolní výrazy za příkazy null. Proto příkazy kontrolního výrazu nedovolují žádné režijní náklady ani náklady na výkon v konečném programu pro vydávání verzí a umožňují vyhnout se `#ifdef` direktivám using.

## <a name="side-effects-of-using-assertions"></a><a name="BKMK_Side_effects_of_using_assertions"></a> Vedlejší účinky použití kontrolních výrazů
Pokud přidáte kontrolní výrazy do kódu, ujistěte se, že kontrolní výrazy nemají vedlejší účinky. Zvažte například následující výraz, který upraví `nM` hodnotu:

```cpp
ASSERT(nM++ > 0); // Don't do this!
```

Vzhledem k tomu `ASSERT` , že výraz není vyhodnocen v prodejní verzi programu, `nM` budou mít v ladicích a vydaných verzích jiné hodnoty. Chcete-li se tomuto problému v knihovně MFC vyhnout, můžete použít makro [ověřit](/cpp/mfc/reference/diagnostic-services#verify) místo `ASSERT` . `VERIFY` vyhodnotí výraz ve všech verzích, ale nevrátí výsledek ve vydané verzi.

Buďte obzvláště opatrní při použití volání funkcí v příkazech kontrolního výrazu, protože vyhodnocení funkce může mít neočekávané vedlejší účinky.

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects
VERIFY ( myFnctn(0)==1 ) // safe
```

`VERIFY` volá `myFnctn` obě verze ladění i verze, takže je přijatelné použít. Nicméně použití `VERIFY` působí režii zbytečného volání funkce ve vydané verzi.

[V tomto tématu](#BKMK_In_this_topic)

## <a name="crt-assertions"></a><a name="BKMK_CRT_assertions"></a> Kontrolní výrazy CRT
SOUBORU Crtdbg. Soubor hlaviček H definuje [makra _ASSERT a _ASSERTE](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) pro kontrolu kontrolního výrazu.

| Podokně | Výsledek |
|------------| - |
| `_ASSERT` | Pokud se zadaný výraz vyhodnotí jako FALSE, název souboru a číslo řádku `_ASSERT` . |
| `_ASSERTE` | Stejné jako `_ASSERT` , plus řetězcové vyjádření výrazu, který byl uplatněn. |

`_ASSERTE` je výkonnější, protože oznamuje výraz, který je vyměněn jako nepravdivý. To může být dostačující k identifikaci problému bez odkazování na zdrojový kód. Ladicí verze vaší aplikace však bude obsahovat řetězcovou konstantu pro každý výraz s kontrolními výrazy `_ASSERTE` . Pokud použijete mnoho `_ASSERTE` maker, tyto řetězcové výrazy zabírají značnou velikost paměti. Pokud se to ukáže jako problém, použijte `_ASSERT` k uložení paměti.

Když `_DEBUG` je definováno, `_ASSERTE` makro je definováno následujícím způsobem:

```cpp
#define _ASSERTE(expr) \
    do { \
        if (!(expr) && (1 == _CrtDbgReport( \
            _CRT_ASSERT, __FILE__, __LINE__, #expr))) \
            _CrtDbgBreak(); \
    } while (0)
```

Pokud je výraz ASSERT vyhodnocen jako FALSE, je volána [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) k hlášení selhání kontrolního výrazu (pomocí dialogového okna zprávy ve výchozím nastavení). Pokud v dialogovém okně zpráva kliknete na tlačítko **Opakovat** , `_CrtDbgReport` vrátí hodnotu 1 a `_CrtDbgBreak` volání ladicího programu prostřednictvím `DebugBreak` .

### <a name="checking-for-heap-corruption"></a>Kontroluje se poškození haldy.
Následující příklad používá [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory) ke kontrole poškození haldy:

```cpp
_ASSERTE(_CrtCheckMemory());
```

### <a name="checking-pointer-validity"></a>Kontroluje se platnost ukazatele.
Následující příklad používá [_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer) k ověření, že daný rozsah paměti je platný pro čtení nebo zápis.

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );
```

Následující příklad používá [_CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer) k ověření ukazatele na paměť v lokální haldě (halda vytvořená a spravovaná touto instancí knihovny run-time jazyka C – knihovna DLL může mít svou vlastní instanci knihovny, a proto vlastní haldu, mimo haldu aplikace). Tento kontrolní výraz zachytí pouze adresy null nebo mimo rozsah, ale také ukazatele na statické proměnné, proměnné zásobníku a jakoukoli jinou nemístní paměť.

```cpp
_ASSERTE(_CrtIsValidPointer( myData );
```

### <a name="checking-a-memory-block"></a>Kontrola bloku paměti
Následující příklad používá [_CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock) k ověření, zda je blok paměti v místní haldě a má platný typ bloku.

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));
```

[V tomto tématu](#BKMK_In_this_topic)

## <a name="mfc-assertions"></a><a name="BKMK_MFC_assertions"></a> Kontrolní výrazy MFC
MFC definuje makro [kontrolního](https://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) výrazu pro kontrolu kontrolního výrazu. Definuje také `MFC ASSERT_VALID` `CObject::AssertValid` metody a pro kontrolu vnitřního stavu `CObject` objektu odvozeného.

Pokud je argument `ASSERT` makra MFC vyhodnocen jako nula nebo false, makro zastaví spuštění programu a upozorní uživatele. v opačném případě pokračuje v provádění.

V případě neúspěchu kontrolního výrazu se zobrazí dialogové okno zpráva s názvem zdrojového souboru a číslem řádku kontrolního výrazu. Pokud v dialogovém okně kliknete na tlačítko Opakovat, volání [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) způsobí přerušení provádění do ladicího programu. V tomto okamžiku můžete prostudovat zásobník volání a použít další pomůcky ladicího programu k určení příčiny selhání kontrolního výrazu. Pokud jste povolili [ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md)a ladicí program ještě nebyl spuštěn, dialogové okno může spustit ladicí program.

Následující příklad ukazuje, jak použít `ASSERT` ke kontrole návratové hodnoty funkce:

```cpp
int x = SomeFunc(y);
ASSERT(x >= 0);   //  Assertion fails if x is negative
```

Můžete použít ASSERT s funkcí [IsKindOf](/cpp/mfc/reference/cobject-class#iskindof) k poskytnutí kontroly typu argumentů funkce:

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );
```

`ASSERT`Makro negeneruje ve vydané verzi žádný kód. Pokud potřebujete vyhodnotit výraz ve vydané verzi, použijte místo výrazu ASSERT makro [verify](https://msdn.microsoft.com/library/s8c29sw2.aspx#verify) .

### <a name="mfc-assert_valid-and-cobjectassertvalid"></a><a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT_VALID a CObject:: AssertValid
Metoda [CObject:: AssertValid](/cpp/mfc/reference/cobject-class#assertvalid) zajišťuje kontroly vnitřního stavu objektu v době běhu. I když při `AssertValid` odvozování třídy z nelze přepsat třídu `CObject` , je možné ji provést lépe spolehlivější. `AssertValid` by měla být provedena kontrolní výrazy pro všechny členské proměnné objektu pro ověření, že obsahují platné hodnoty. Například by měla kontrolovat, že proměnné členů ukazatele nejsou NULL.

Následující příklad ukazuje, jak deklarovat `AssertValid` funkci:

```cpp
class CPerson : public CObject
{
protected:
    CString m_strName;
    float   m_salary;
public:
#ifdef _DEBUG
    // Override
    virtual void AssertValid() const;
#endif
    // ...
};
```

Pokud přepíšete `AssertValid` , `AssertValid` před provedením vlastních kontrol volejte verzi základní třídy. Pak použijte makro ASSERT pro kontrolu členů, které jsou jedinečné pro vaši odvozenou třídu, jak je znázorněno zde:

```cpp
#ifdef _DEBUG
void CPerson::AssertValid() const
{
    // Call inherited AssertValid first.
    CObject::AssertValid();

    // Check CPerson members...
    // Must have a name.
    ASSERT( !m_strName.IsEmpty());
    // Must have an income.
    ASSERT( m_salary > 0 );
}
#endif
```

Pokud některý z vašich členských proměnných ukládá objekty, můžete použít `ASSERT_VALID` makro k otestování své vnitřní platnosti (pokud jejich třídy přepisují `AssertValid` ).

Zvažte například třídu `CMyData` , která ukládá [CObList](/cpp/mfc/reference/coblist-class) do jedné z jeho členských proměnných. `CObList`Proměnná `m_DataList` ukládá kolekci `CPerson` objektů. Zkrácená deklarace vypadá takto `CMyData` :

```cpp
class CMyData : public CObject
{
    // Constructor and other members ...
    protected:
        CObList* m_pDataList;
    // Other declarations ...
    public:
#ifdef _DEBUG
        // Override:
        virtual void AssertValid( ) const;
#endif
    // And so on ...
};
```

`AssertValid`Přepsání v `CMyData` takovém případě vypadá takto:

```cpp
#ifdef _DEBUG
void CMyData::AssertValid( ) const
{
    // Call inherited AssertValid.
    CObject::AssertValid( );
    // Check validity of CMyData members.
    ASSERT_VALID( m_pDataList );
    // ...
}
#endif
```

`CMyData` používá `AssertValid` mechanismus k otestování platnosti objektů uložených ve svém datovém členu. Překrytí `AssertValid` `CMyData` vyvolá `ASSERT_VALID` makro pro vlastní m_pDataList členskou proměnnou.

Testování platnosti se na této úrovni nezastaví, protože třída `CObList` také přepisuje `AssertValid` . Toto přepsání provede další testování platnosti v interním stavu seznamu. Proto test platnosti `CMyData` objektu vede k dalším testům platnosti pro vnitřní stavy objektu uloženého `CObList` seznamu.

S nějakou další prací můžete přidat testy platnosti pro `CPerson` objekty uložené v seznamu také. Mohli byste odvodit třídu `CPersonList` z `CObList` a přepsat `AssertValid` . V přepsání byste volali `CObject::AssertValid` a pak proopakovali seznam, a to voláním `AssertValid` na každý `CPerson` objekt uložený v seznamu. `CPerson`Třída zobrazená na začátku tohoto tématu již Přepisuje `AssertValid` .

Toto je účinný mechanismus při sestavování pro ladění. Při následném sestavení pro vydanou verzi je mechanismus automaticky vypnut.

### <a name="limitations-of-assertvalid"></a><a name="BKMK_Limitations_of_AssertValid"></a> Omezení AssertValid
Aktivovaný kontrolní výraz indikuje, že objekt je jednoznačně špatný a spuštění se zastaví. Chybějící kontrolní výraz však indikuje pouze, že nebyl nalezen žádný problém, ale objekt není zaručený jako dobrý.

[V tomto tématu](#BKMK_In_this_topic)

## <a name="using-assertions"></a><a name="BKMK_Using_assertions"></a> Použití kontrolních výrazů

### <a name="catching-logic-errors"></a><a name="BKMK_Catching_logic_errors"></a> Zachycení chyb logiky
Můžete nastavit kontrolní výraz pro podmínku, která musí být pravdivá podle logiky programu. Kontrolní výraz nemá žádný vliv, pokud dojde k chybě logiky.

Předpokládejme například, že simulujete molekuly plynu v kontejneru a proměnná `numMols` představuje celkový počet molekul. Toto číslo nemůže být menší než nula, takže můžete zahrnout příkaz kontrolního výrazu MFC takto:

```cpp
ASSERT(numMols >= 0);
```

Nebo můžete zahrnout kontrolní výraz CRT podobný tomuto:

```cpp
_ASSERT(numMols >= 0);
```

Tyto příkazy nedělají nic, pokud program funguje správně. Pokud však chyba logiky `numMols` bude menší než nula, kontrolní výraz zastaví provádění programu a zobrazí [dialogové okno neúspěšného kontrolního výrazu](../debugger/assertion-failed-dialog-box.md).

[V tomto tématu](#BKMK_In_this_topic)

### <a name="checking-results"></a><a name="BKMK_Checking_results_"></a> Kontrola výsledků
Kontrolní výrazy jsou cenné pro testovací operace, jejichž výsledky nejsou zjevnější od rychlé kontroly vizuálu.

Zvažte například následující kód, který aktualizuje proměnnou na `iMols` základě obsahu propojeného seznamu, na který odkazuje `mols` :

```cpp
/* This code assumes that type has overloaded the != operator
 with const char *
It also assumes that H2O is somewhere in that linked list.
Otherwise we'll get an access violation... */
while (mols->type != "H2O")
{
    iMols += mols->num;
    mols = mols->next;
}
ASSERT(iMols<=numMols); // MFC version
_ASSERT(iMols<=numMols); // CRT version
```

Počet molekul počítaných pomocí `iMols` musí být vždy menší nebo roven celkovému počtu molekul, `numMols` . Vizuální kontrola smyčky neukazuje, že se jedná o tento případ, takže se použije příkaz kontrolního výrazu po smyčce k otestování této podmínky.

[V tomto tématu](#BKMK_In_this_topic)

### <a name="finding-unhandled-errors"></a><a name="BKMK_Testing_error_conditions_"></a> Hledají se neošetřené chyby.
Kontrolní výrazy můžete použít k otestování chybových podmínek v určitém bodě v kódu, kde byly zpracovány případné chyby. V následujícím příkladu grafická rutina vrátí chybový kód nebo nula pro úspěch.

```cpp
myErr = myGraphRoutine(a, b);

/* Code to handle errors and
   reset myErr if successful */

ASSERT(!myErr); -- MFC version
_ASSERT(!myErr); -- CRT version
```

Pokud kód pro zpracování chyb funguje správně, měla by být chyba zpracována a `myErr` nastavena na nulu před dosažením kontrolního výrazu. Pokud `myErr` má jinou hodnotu, kontrolní výraz se nezdařil, program se zastaví a zobrazí se [dialogové okno kontrolní výraz selhal](../debugger/assertion-failed-dialog-box.md) .

Příkazy kontrolního výrazu nejsou náhradou za kód pro zpracování chyb, ale. Následující příklad ukazuje příkaz kontrolního výrazu, který může vést k problémům v konečném kódu verze:

```cpp
myErr = myGraphRoutine(a, b);

/* No Code to handle errors */

ASSERT(!myErr); // Don't do this!
_ASSERT(!myErr); // Don't do this, either!
```

Tento kód spoléhá na příkaz kontrolního výrazu, který zpracovává chybový stav. V důsledku toho bude veškerý chybový kód vrácený `myGraphRoutine` v konečném kódu verze nezpracován.

[V tomto tématu](#BKMK_In_this_topic)

## <a name="see-also"></a>Viz také

- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Kontrolní výrazy ve spravovaném kódu](../debugger/assertions-in-managed-code.md)