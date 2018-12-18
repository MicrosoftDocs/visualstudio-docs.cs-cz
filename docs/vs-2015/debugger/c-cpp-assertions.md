---
title: Kontrolní výrazy C / C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3dc4c2a6c4f5b9d4a0e4e1cf0fd0a4a6c9928de6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799753"
---
# <a name="cc-assertions"></a>Kontrolní výrazy jazyka C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Příkaz kontrolní výraz určuje podmínku, která očekáváte, že na hodnotu true na místě v aplikaci. Pokud tato podmínka není splněna, výraz se nezdaří, dojde k přerušení provádění programu a [chyba kontrolního výrazu dialogovému oknu](../debugger/assertion-failed-dialog-box.md) se zobrazí.  

 Jazyk Visual C++ podporuje kontrolní výraz příkazy, které jsou založeny na jaké konstrukty jsou následující:  

- Kontrolní výrazy knihovny MFC pro programy MFC.  

- [ATLASSERT](http://msdn.microsoft.com/library/98e3e0fc-77e2-499b-a6f6-b17a21c6fbd3) pro programy, které používají knihovnu ATL.  

- Kontrolní výrazy CRT pro programy, které používají knihovny run-time C.  

- ANSI [vyhodnocení funkce](http://msdn.microsoft.com/library/a9ca031a-648b-47a6-bdf1-65fc7399dd40) pro programy C/C++.  

  Kontrolní výrazy můžete zachytávat chyby logiky, zkontrolujte výsledky operace a testování chybové stavy, které by měl zpracovat.  

##  <a name="BKMK_In_this_topic"></a> V tomto tématu  
 [Jak fungují kontrolní výrazy](#BKMK_How_assertions_work)  

 [Kontrolní výrazy v sestavení ladění a vydání](#BKMK_Assertions_in_Debug_and_Release_builds)  

 [Vedlejší účinky použití kontrolních výrazů](#BKMK_Side_effects_of_using_assertions)  

 [Kontrolní výrazy CRT](#BKMK_CRT_assertions)  

 [Kontrolní výrazy s MFC](#BKMK_MFC_assertions)  

- [MFC ASSERT_VALID a CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  

- [Omezení AssertValid](#BKMK_Limitations_of_AssertValid)  

  [Použití kontrolních výrazů](#BKMK_Using_assertions)  

- [Zachytávání logické chyby](#BKMK_Catching_logic_errors)  

- [Kontrola výsledků](#BKMK_Checking_results_)  

- [Zjištění neošetřené chyby](#BKMK_Testing_error_conditions_)  

##  <a name="BKMK_How_assertions_work"></a> Jak fungují kontrolní výrazy  
 Pokud ladicí program zastaví z důvodu knihovny run-time kontrolní výraz knihovny MFC nebo knihovny jazyka C, pak pokud zdrojem je k dispozici, ladicí program přejde do bodu ve zdrojovém souboru, kde došlo k chybě kontrolního výrazu. Kontrolní výraz zpráva se zobrazí v obou [okno výstup](../ide/reference/output-window.md) a **chyba kontrolního výrazu** dialogové okno. Můžete zkopírovat zprávu kontrolní výraz **výstup** okno do textového okna, pokud chcete uložit pro pozdější použití. **Výstup** okna může obsahovat další chybové zprávy. Prozkoumejte tyto zprávy opatrně, protože poskytují příčiny na příčinu selhání kontrolního výrazu.  

 Kontrolní výrazy použijte ke zjištění chyby během vývoje. Jako pravidlo použijte jeden výraz pro každý předpokladů. Například pokud budete předpokládat, že argument není NULL, použijte kontrolní výraz k otestování tohoto předpokladu.  

 [V tomto tématu](#BKMK_In_this_topic)  

##  <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Kontrolní výrazy v sestavení ladění a vydání  
 Kontrolní výraz příkazy zkompilovat pouze v případě `_DEBUG` je definována. V opačném případě kompilátor považuje za kontrolní výrazy příkazy null. Proto kontrolní výraz příkazy Uložit bez režie nebo výkonu nákladů v konečné verzi programu a umožňují vyhnout `#ifdef` direktivy.  

##  <a name="BKMK_Side_effects_of_using_assertions"></a> Vedlejší účinky použití kontrolních výrazů  
 Když přidáte kontrolní výrazy do kódu, nezapomeňte že kontrolní výrazy nemají vedlejší účinky. Zvažte například následující výraz, který mění `nM` hodnotu:  

```  
ASSERT(nM++ > 0); // Don't do this!  

```  

 Vzhledem k tomu, `ASSERT` výraz není vyhodnocen ve vydané verzi programu, `nM` budou mít různé hodnoty v ladění a vydání verze. Chcete-li předejít tomuto problému knihovny MFC, můžete použít [OVĚŘTE](http://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96) – makro místo `ASSERT`.  `VERIFY` vyhodnotí výraz ve všech verzích ale nekontroluje výsledek ve vydané verzi.  

 Být zejména opatrní při použití volání funkce v příkazech kontrolní výraz, protože vyhodnocení funkce může mít neočekávané vedlejší účinky.  

```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  

 `VERIFY` volání `myFnctn` v ladění i vydání verze, takže je nepřijatelné využívat. Avšak použití `VERIFY` ukládá režii volání funkce zbytečné ve vydané verzi.  

 [V tomto tématu](#BKMK_In_this_topic)  

##  <a name="BKMK_CRT_assertions"></a> Kontrolní výrazy CRT  
 CRTDBG. Definuje soubor hlaviček H [_ASSERT a _asserte – makra](http://msdn.microsoft.com/library/e98fd2a6-7f5e-4aa8-8fe8-e93490deba36) kontroly kontrolní výraz.  


|   – Makro    |                                             Výsledek                                              |
|------------|-------------------------------------------------------------------------------------------------|
| `_ASSERT`  | Pokud se zadaný výraz nevyhodnotí jako FALSE, souboru název a číslo řádku `_ASSERT`. |
| `_ASSERTE` |      Stejné jako `_ASSERT`, plus řetězcovou reprezentaci výrazu, která byla uplatněna.       |

 `_ASSERTE` je výkonnější, protože zprávy s potvrzením výraz, který je FALSE. To může být, aby bylo možné identifikovat problém bez odkazující na zdrojový kód. Nicméně ladicí verze aplikace bude obsahovat konstantu řetězce pro každý výraz s prohlašovanou pomocí `_ASSERTE`. Pokud budete používat mnoho `_ASSERTE` makra, tyto výrazy řetězec spotřebovávat značné množství paměti. Pokud je to nějaký problém, použijte `_ASSERT` uložit paměti.  

 Při `_DEBUG` je definován, `_ASSERTE` – makro je definovaná následujícím způsobem:  

```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  

 Pokud s potvrzením výraz nevyhodnotí jako FALSE, [_CrtDbgReport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) je volána k hlášení selhání kontrolního výrazu (pomocí dialogového okna zprávy ve výchozím nastavení). Pokud se rozhodnete **opakujte** v dialogovém okně zpráva `_CrtDbgReport` vrátí hodnotu 1 a `_CrtDbgBreak` volá ladicí program prostřednictvím `DebugBreak`.  

### <a name="checking-for-heap-corruption"></a>Vyhledání poškození haldy  
 Následující příklad používá [_CrtCheckMemory](http://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765) ke kontrole poškození haldy:  

```  
_ASSERTE(_CrtCheckMemory());  
```  

### <a name="checking-pointer-validity"></a>Kontrola platnosti ukazatele  
 Následující příklad používá [_crtisvalidpointer –](http://msdn.microsoft.com/library/91c35590-ea5e-450f-a15d-ad8d62ade1fa) k ověření, že rozsah danou paměť je platná pro čtení nebo zápis.  

```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  

 Následující příklad používá [_crtisvalidheappointer –](http://msdn.microsoft.com/library/caf597ce-1b05-4764-9f37-0197a982bec5) ověření ukazatel odkazuje na paměť v lokální haldy (haldy vytvořen a spravován společností této instance knihovny run-time jazyka C – knihovna DLL může mít svoji vlastní instanci knihovny, a proto vlastní haldy, mimo haldy aplikace). Tento kontrolní výraz zachytí není pouze hodnotu null nebo celočíselných adres, ale také ukazatelů na statické proměnné, proměnné zásobníku a další nemístní paměti.  

```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  

### <a name="checking-a-memory-block"></a>Kontrola bloku paměti  
 Následující příklad používá [_crtismemoryblock –](http://msdn.microsoft.com/library/f7cbbc60-3690-4da0-a07b-68fd7f250273) k ověření, že blok paměti v haldě, místní a má platný blok typu.  

```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  

 [V tomto tématu](#BKMK_In_this_topic)  

##  <a name="BKMK_MFC_assertions"></a> Kontrolní výrazy s MFC  
 Definuje MFC [ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) – makro kontroly kontrolní výraz. Definuje také `MFC ASSERT_VALID` a `CObject::AssertValid` metody kontroly vnitřní stav `CObject`-odvozenému objektu.  

 Pokud argument MFC `ASSERT` – makro vyhodnocen jako nula nebo hodnotu NEPRAVDA, makro zastaví provádění programu a zobrazí uživateli výstrahu; v opačném případě pokračuje.  

 Pokud kontrolní výraz selže, zprávy dialogové okno zobrazí název zdrojového souboru a číslo řádku výrazu. Pokud vyberete možnost opakovat v dialogovém okně pole, volání [afxdebugbreak –](http://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30) způsobí spuštění řízení ladicímu programu. V tomto okamžiku můžete prozkoumat zásobník volání a použít jiné zařízení pro ladicí program k určení, proč kontrolní výraz je neplatný. Pokud jste povolili [Just-in-time ladění](../debugger/just-in-time-debugging-in-visual-studio.md)a ladicí program se už běží, dialogové okno můžete spustit ladicí program.  

 Následující příklad ukazuje, jak používat `ASSERT` zkontrolovat návratovou hodnotu funkce:  

```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  

 Můžete použít kontrolní VÝRAZ s [IsKindOf](http://msdn.microsoft.com/library/7c87c748-b7e0-4c6d-9694-6035e62fdfd6) funkce poskytují kontrolu typů argumentů funkce:  

```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  

 `ASSERT` – Makro nevygeneruje žádný kód ve vydané verzi. Pokud potřebujete k vyhodnocení výrazu ve vydané verzi, použijte [OVĚŘTE](http://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96) – makro místo ASSERT.  

###  <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT_VALID a CObject::AssertValid  
 [CObject::AssertValid](http://msdn.microsoft.com/library/534a0744-4ab6-423d-b492-b4058b3d5157) metoda poskytuje vnitřní stav objektu se kontroly za běhu. I když není nutné přepsat `AssertValid` Pokud odvodit třídu z `CObject`, můžete provést vaší třídy spolehlivější tímto způsobem. `AssertValid` na všechny proměnné členů objektu k ověření, že obsahují platné hodnoty by měl provést kontrolní výrazy. Například by měl zkontrolovat, že členské proměnné ukazatele nemají hodnotu NULL.  

 Následující příklad ukazuje, jak deklarovat `AssertValid` funkce:  

```  
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

 Při přepsání `AssertValid`, volat základní třídy verzi `AssertValid` předtím, než provedete vlastní kontroly. Potom pomocí makra ASSERT zkontrolujte členy, které jsou jedinečné pro odvozenou třídu, jak je znázorněno zde:  

```  
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

 Pokud některý z členské proměnné ukládat objekty, můžete použít `ASSERT_VALID` – makro otestovat jejich interní platnosti (pokud jejich třídám přepsat `AssertValid`).  

 Představte si třeba třídu `CMyData`, které obchody [coblist –](http://msdn.microsoft.com/library/80699c93-33d8-4f8b-b8cf-7b58aeab64ca) v jednom z jeho členské proměnné. `CObList` Proměnnou, `m_DataList`, uloží kolekci `CPerson` objekty. Zkrácený deklarace `CMyData` vypadá přibližně takto:  

```  
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

 `AssertValid` Přepsat v `CMyData` vypadá přibližně takto:  

```  
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

 `CMyData` používá `AssertValid` mechanismus pro testování platnosti objektů uložených v jeho datový člen. Přepsání `AssertValid` z `CMyData` vyvolá `ASSERT_VALID` – makro pro vlastní m_pDataList členské proměnné.  

 Testování platnosti nezastaví na této úrovni protože třídu `CObList` také přepisuje `AssertValid`. Toto přepsání provádí další platnosti testování na vnitřní stav seznamu. Díky tomu se platnost testovat na `CMyData` objekt vede k další platnosti testy pro interní stavy uloženou `CObList` objekt seznamu.  

 Některé další práci, můžete přidat testy platnosti pro `CPerson` objektů uložených v seznamu také. Může odvodit třídu `CPersonList` z `CObList` a přepsat `AssertValid`. V přepsání, volání `CObject::AssertValid` a potom iteraci v rámci seznamu volání `AssertValid` na každém `CPerson` objekt uložený v seznamu. `CPerson` Třídy uvedené na začátku tohoto tématu již přepíše `AssertValid`.  

 Jedná se o efektivní mechanismus při sestavení pro ladění. Když následně sestavení pro vydání, mechanismu, který je automaticky vypnutý.  

###  <a name="BKMK_Limitations_of_AssertValid"></a> Omezení AssertValid  
 Kontrolní výraz aktivovaných označuje, že objekt je jednoznačně chybný a zastaví provádění. Však nedostatku kontrolní výraz značí pouze, že nebyly nalezeny žádné potíže, ale objekt není zaručeno, že bezproblémový.  

 [V tomto tématu](#BKMK_In_this_topic)  

##  <a name="BKMK_Using_assertions"></a> Použití kontrolních výrazů  

###  <a name="BKMK_Catching_logic_errors"></a> Zachytávání logické chyby  
 Kontrolní výraz můžete nastavit na podmínku, která musí být splněny podle logiky aplikace. Výraz nemá žádný vliv, pokud dojde k logické chybě.  

 Předpokládejme například, že je budete jen simulovat plynu přenosů v kontejneru a proměnná `numMols` představuje celkový počet přenosů. Toto číslo nemůže být menší než nula, tak může zahrnovat příkazem MFC kontrolního výrazu takto:  

```  
ASSERT(numMols >= 0);  

```  

 Nebo může zahrnovat kontrolní výraz CRT takto:  

```  
_ASSERT(numMols >= 0);  
```  

 Tyto příkazy Neprovádět žádnou akci, pokud váš program pracuje správně. Pokud logická chyba způsobí, že `numMols` být menší než nula, ale výraz zastaví provádění programu a zobrazí [kontrolního výrazu se nezdařilo dialogovému oknu](../debugger/assertion-failed-dialog-box.md).  

 [V tomto tématu](#BKMK_In_this_topic)  

###  <a name="BKMK_Checking_results_"></a> Kontrola výsledků  
 Kontrolní výrazy jsou velmi cennou pomůckou pro testování operace, jejichž výsledky nejsou zřejmé z rychlého vizuální kontrolu.  

 Zvažte například následující kód, který aktualizuje proměnné `iMols` na základě obsahu propojeného seznamu, na které odkazuje `mols`:  

```  
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

 Počet přenosů spočítaných podle `iMols` musí být vždy nižší než celkový počet přenosů, `numMols`. Vizuální kontrolu smyčky není uveden, že to nutně bude v případě, takže příkaz kontrolního výrazu po smyčce slouží k otestování pro tuto podmínku.  

 [V tomto tématu](#BKMK_In_this_topic)  

###  <a name="BKMK_Testing_error_conditions_"></a> Zjištění neošetřené chyby  
 Kontrolní výrazy můžete použít k testování pro chybové podmínky v místě v kódu kde všechny chyby by měl být manipulováno. V následujícím příkladu grafického rutina vrátí kód chyby nebo 0 pro úspěch.  

```  
myErr = myGraphRoutine(a, b);  

/* Code to handle errors and  
   reset myErr if successful */  

ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  

 Pokud kód pro zpracování chyb funguje správně, by měla chyba zpracována a `myErr` resetování na nulu, než je dosaženo kontrolního výrazu. Pokud `myErr` má jinou hodnotu, kontrolní výraz selže, zastaví programu a [kontrolního výrazu se nezdařilo dialogovému oknu](../debugger/assertion-failed-dialog-box.md) se zobrazí.  

 Kontrolní výraz příkazy však nejsou náhradou za kód pro zpracování chyb. Následující příklad ukazuje příkaz kontrolní výraz, který může vést k problémům v konečné verzi kódu:  

```  
myErr = myGraphRoutine(a, b);  

/* No Code to handle errors */  

ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  

 Tento kód závisí na kontrolní výraz příkazu pro zpracování chybového stavu. V důsledku toho libovolný kód chyby vrácený `myGraphRoutine` bude není ošetřená v konečné verzi kódu.  

 [V tomto tématu](#BKMK_In_this_topic)  

## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)   
 [Kontrolní výrazy ve spravovaném kódu](../debugger/assertions-in-managed-code.md)



