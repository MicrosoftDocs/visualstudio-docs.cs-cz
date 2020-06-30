---
title: Zadávání poznámek k parametrům funkcí a návratovým hodnotám | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 71854388f3fb1c5eaea7d40ed2757af9cecacf1a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543803"
---
# <a name="annotating-function-parameters-and-return-values"></a>Zadávání poznámek k parametrům funkcí a návratovým hodnotám
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento článek popisuje typické použití poznámek pro jednoduché parametry funkcí – skalární objekty a ukazatele na struktury a třídy – a většinu druhů vyrovnávacích pamětí.  Tento článek také ukazuje běžné způsoby použití pro poznámky. Další poznámky, které se vztahují k funkcím, najdete v tématu věnovaném [chování funkcí s poznámkami](../code-quality/annotating-function-behavior.md) .  
  
## <a name="pointer-parameters"></a>Parametry ukazatele  
 Pro poznámky v následující tabulce, pokud je parametr ukazatele označen příznakem, analyzátor ohlásí chybu, pokud má ukazatel hodnotu null.  To platí pro ukazatele a na všechny položky dat, na které se odkazuje.  
  
 **Poznámky a popisy**  
  
- `_In_`  
  
     Přidává poznámky ke vstupním parametrům, které jsou skalární, struktury, ukazatele na struktury a podobně.  Explicitně lze použít na jednoduchých skalárních.  Parametr musí být platný v předběžném stavu a nebude změněn.  
  
- `_Out_`  
  
     Označí výstupní parametry, které jsou skalární, struktury, ukazatele na struktury a jako.  Nepoužívejte u objektu, který nemůže vracet hodnotu, například skalární, která je předána hodnotou.  Parametr nemusí být platný v předběžném stavu, ale musí být platný v rámci post-State.  
  
- `_Inout_`  
  
     Přidá poznámku k parametru, který bude funkcí změněn.  Musí být platný v představovém i následném stavu, ale předpokládá se, že mají jiné hodnoty před a po volání. Musí se použít pro upravitelnou hodnotu.  
  
- `_In_z_`  
  
     Ukazatel na řetězec zakončený hodnotou null, který se používá jako vstup.  Řetězec musí být platný v předběžném stavu.  `PSTR`Jsou upřednostňovány varianty, které již mají správné poznámky.  
  
- `_Inout_z_`  
  
     Ukazatel na pole znaků zakončené hodnotou null, které bude upraveno.  Musí být platný před a po volání, ale hodnota se předpokládá, že se změnila.  Ukončovací znak null lze přesunout, ale mohou být k dispozici pouze prvky až k původnímu ukončovacímu znaku null.  
  
- `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     Ukazatel na pole, který je čten funkcí.  Pole má velikost `s` prvků, přičemž všechny musí být platné.  
  
     `_bytes_`Hodnota variant poskytuje velikost v bajtech namísto prvků. Tuto hodnotu použijte pouze v případě, že velikost nelze vyjádřit jako prvky.  Například `char` řetězce by používaly `_bytes_` variantu pouze v případě, že je podobná funkce, kterou používá `wchar_t` .  
  
- `_In_reads_z_(s)`  
  
     Ukazatel na pole, které má ukončenou hodnotu null a má známou velikost. Prvky až do ukončovacího znaku null, nebo `s` Pokud neexistuje ukončovací znak null – musí být platné v představu.  Pokud je velikost známá v bajtech, Škálujte `s` podle velikosti prvku.  
  
- `_In_reads_or_z_(s)`  
  
     Ukazatel na pole, které je zakončené hodnotou null nebo má známou velikost nebo obojí. Prvky až do ukončovacího znaku null, nebo `s` Pokud neexistuje ukončovací znak null – musí být platné v představu.  Pokud je velikost známá v bajtech, Škálujte `s` podle velikosti prvku.  (Používá se pro `strn` rodinu.)  
  
- `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     Ukazatel na pole `s` prvků (odp. bytes), který bude zapsán funkcí.  Prvky pole nemusí být platné v předběžné verzi a počet prvků, které jsou platné v post-State, není určen.  Pokud existují poznámky k typu parametru, jsou aplikovány v post-State. Zvažte například následující kód.  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     V tomto příkladu volající poskytuje vyrovnávací paměť `size` prvků pro `p1` .  `MyStringCopy`provede některé z těchto elementů platnými. Důležitější je, že `_Null_terminated_` Poznámka na `PWSTR` to znamená, že `p1` ve stavu post je zakončení null.  Tímto způsobem je počet platných prvků stále správně definován, ale konkrétní počet prvků není vyžadován.  
  
     `_bytes_`Hodnota variant poskytuje velikost v bajtech namísto prvků. Tuto hodnotu použijte pouze v případě, že velikost nelze vyjádřit jako prvky.  Například `char` řetězce by používaly `_bytes_` variantu pouze v případě, že je podobná funkce, kterou používá `wchar_t` .  
  
- `_Out_writes_z_(s)`  
  
     Ukazatel na pole `s` prvků.  Elementy nemusí být platné v předběžném stavu.  V post-State prvky až po ukončovací znak null, který musí být přítomen – musí být platný.  Pokud je velikost známá v bajtech, Škálujte `s` podle velikosti prvku.  
  
- `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     Ukazatel na pole, které je ve funkci čteno a zapisováno.  Má velikost `s` elementů a je platný v představovém a následném stavu.  
  
     `_bytes_`Hodnota variant poskytuje velikost v bajtech namísto prvků. Tuto hodnotu použijte pouze v případě, že velikost nelze vyjádřit jako prvky.  Například `char` řetězce by používaly `_bytes_` variantu pouze v případě, že je podobná funkce, kterou používá `wchar_t` .  
  
- `_Inout_updates_z_(s)`  
  
     Ukazatel na pole, které má ukončenou hodnotu null a má známou velikost. Prvky až do ukončovacího znaku null, který musí být přítomen – musí být platný v představech i po stavu.  Hodnota v příspěvku je považována za odlišnou od hodnoty v předběžném stavu; To zahrnuje umístění ukončovacího znaku null. Pokud je velikost známá v bajtech, Škálujte `s` podle velikosti prvku.  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Ukazatel na pole `s` prvků.  Elementy nemusí být platné v předběžném stavu.  V rámci po stavu musí být prvky až do `c` -tém elementu platné.  Pokud je velikost známa v bajtech, rozsahu `s` a `c` velikosti prvku nebo použijte `_bytes_` variantu, která je definována jako:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Jinými slovy, každý prvek, který existuje ve vyrovnávací paměti, až do `s` předběžného stavu, je platný v post-State.  Příklad:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Ukazatel na pole, který je čten a zapisován funkcí.  Má velikost `s` elementů, které musí být platné v předběžném stavu a `c` elementy musí být platné v post-State.  
  
     `_bytes_`Hodnota variant poskytuje velikost v bajtech namísto prvků. Tuto hodnotu použijte pouze v případě, že velikost nelze vyjádřit jako prvky.  Například `char` řetězce by používaly `_bytes_` variantu pouze v případě, že je podobná funkce, kterou používá `wchar_t` .  
  
- `_Inout_updates_z_(s)`  
  
     Ukazatel na pole, které má ukončenou hodnotu null a má známou velikost. Prvky až do ukončovacího znaku null, který musí být přítomen – musí být platný v představech i po stavu.  Hodnota v příspěvku je považována za odlišnou od hodnoty v předběžném stavu; To zahrnuje umístění ukončovacího znaku null. Pokud je velikost známá v bajtech, Škálujte `s` podle velikosti prvku.  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Ukazatel na pole `s` prvků.  Elementy nemusí být platné v předběžném stavu.  V rámci po stavu musí být prvky až do `c` -tém elementu platné.  Pokud je velikost známa v bajtech, rozsahu `s` a `c` velikosti prvku nebo použijte `_bytes_` variantu, která je definována jako:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Jinými slovy, každý prvek, který existuje ve vyrovnávací paměti, až do `s` předběžného stavu, je platný v post-State.  Příklad:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Ukazatel na pole, který je čten a zapisován funkcí.  Má velikost `s` elementů, které musí být platné v předběžném stavu a `c` elementy musí být platné v post-State.  
  
     `_bytes_`Hodnota variant poskytuje velikost v bajtech namísto prvků. Tuto hodnotu použijte pouze v případě, že velikost nelze vyjádřit jako prvky.  Například `char` řetězce by používaly `_bytes_` variantu pouze v případě, že je podobná funkce, kterou používá `wchar_t` .  
  
- `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     Ukazatel na pole, který je čten a napsán funkcí size `s` Elements. Definováno jako ekvivalent:  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     Jinými slovy, každý prvek, který existuje ve vyrovnávací paměti, až do `s` předběžného stavu, je platný v představovém a následném stavu.  
  
     `_bytes_`Hodnota variant poskytuje velikost v bajtech namísto prvků. Tuto hodnotu použijte pouze v případě, že velikost nelze vyjádřit jako prvky.  Například `char` řetězce by používaly `_bytes_` variantu pouze v případě, že je podobná funkce, kterou používá `wchar_t` .  
  
- `_In_reads_to_ptr_(p)`  
  
     Ukazatel na pole, pro které `p` `_Curr_` je výraz (tj. `p` mínus `_Curr_` ) definovaný příslušným jazykem Standard.  Prvky před `p` musí být platné v předběžném stavu.  
  
- `_In_reads_to_ptr_z_(p)`  
  
     Ukazatel na pole zakončené hodnotou null, pro které je výraz `p` `_Curr_` (tj. `p` mínus `_Curr_` ) definovaný příslušným jazykem Standard.  Prvky před `p` musí být platné v předběžném stavu.  
  
- `_Out_writes_to_ptr_(p)`  
  
     Ukazatel na pole, pro které `p` `_Curr_` je výraz (tj. `p` mínus `_Curr_` ) definovaný příslušným jazykem Standard.  Prvky před nemusíte `p` být platné v představech a musí být platné v rámci post-State.  
  
- `_Out_writes_to_ptr_z_(p)`  
  
     Ukazatel na pole zakončené hodnotou null, pro které je výraz `p` `_Curr_` (tj. `p` mínus `_Curr_` ) definovaný příslušným jazykem Standard.  Prvky před nemusíte `p` být platné v představech a musí být platné v rámci post-State.  
  
## <a name="optional-pointer-parameters"></a>Volitelné parametry ukazatele  
 Když Poznámka parametru ukazatele obsahuje `_opt_` , indikuje, že parametr může mít hodnotu null. V opačném případě Poznámka provede stejnou verzi jako verze, která neobsahuje `_opt_` . Tady je seznam `_opt_` variant poznámek k parametrům ukazatele:  
  
`_In_opt_`, `_Out_opt_`, `_Inout_opt_`, `_In_opt_z_`, `_Inout_opt_z_`, `_In_reads_opt_`, `_In_reads_bytes_opt_`, `_In_reads_opt_z_`|`_Out_writes_opt_`, `_Out_writes_opt_z_`, `_Inout_updates_opt_`, `_Inout_updates_bytes_opt_`, `_Inout_updates_opt_z_`, `_Out_writes_to_opt_`, `_Out_writes_bytes_to_opt_`, `_Out_writes_all_opt_`, `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`, `_Inout_updates_bytes_to_opt_`, `_Inout_updates_all_opt_`, `_Inout_updates_bytes_all_opt_`, `_In_reads_to_ptr_opt_`, `_In_reads_to_ptr_opt_z_`, `_Out_writes_to_ptr_opt_`, `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>Parametry výstupního ukazatele  
 Parametry výstupního ukazatele vyžadují zvláštní notaci pro jednoznačné použití hodnoty null-Ness v parametru a nařízeného umístění.  
  
 **Poznámky a popisy**  
  
- `_Outptr_`  
  
   Parametr nemůže mít hodnotu null a v rámci následného stavu nemůže být odkaz na umístění null a musí být platný.  
  
- `_Outptr_opt_`  
  
   Parametr může mít hodnotu null, ale v rámci následného stavu nemůže být odkaz na umístění null a musí být platný.  
  
- `_Outptr_result_maybenull_`  
  
   Parametr nemůže mít hodnotu null a v rámci následného stavu může být odkaz na umístění null.  
  
- `_Outptr_opt_result_maybenull_`  
  
   Parametr může mít hodnotu null a v rámci následného stavu může být odkaz na umístění null.  
  
  V následující tabulce jsou do názvu poznámky vloženy další podřetězce, aby bylo možné lépe kvalifikovat význam poznámky.  Jednotlivé podřetězce jsou `_z` ,,, `_COM_` a `_buffer_` `_bytebuffer_` `_to_` .  
  
> [!IMPORTANT]
> Pokud je rozhraní, které přidáváte, k disznámce COM, použijte ve formuláři modelu COM tyto poznámky. Nepoužívejte anotace COM s žádným jiným typem rozhraní.  
  
 **Poznámky a popisy**  
  
- `_Outptr_result_z_`  
  
   `_Outptr_opt_result_z_`  
  
   `_Outptr_result_maybenull_z_`  
  
   `_Ouptr_opt_result_maybenull_z_`  
  
   Vrácený ukazatel má `_Null_terminated_` anotaci.  
  
- `_COM_Outptr_`  
  
   `_COM_Outptr_opt_`  
  
   `_COM_Outptr_result_maybenull_`  
  
   `_COM_Outptr_opt_result_maybenull_`  
  
   Vrácený ukazatel má sémantiku modelu COM, a proto provede `_On_failure_` následnou podmínku, že vrácený ukazatel má hodnotu null.  
  
- `_Outptr_result_buffer_(s)`  
  
   `_Outptr_result_bytebuffer_(s)`  
  
   `_Outptr_opt_result_buffer_(s)`  
  
   `_Outptr_opt_result_bytebuffer_(s)`  
  
   Vrácený ukazatel ukazuje na platnou vyrovnávací paměť `s` prvků velikosti nebo bajtů.  
  
- `_Outptr_result_buffer_to_(s, c)`  
  
   `_Outptr_result_bytebuffer_to_(s, c)`  
  
   `_Outptr_opt_result_buffer_to_(s,c)`  
  
   `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
   Vrácený ukazatel ukazuje na vyrovnávací paměť `s` prvků velikosti nebo bajtů, z nichž první `c` je platná.  
  
  Některé konvence rozhraní předpokládají, že výstupní parametry jsou nullified při selhání.  S výjimkou explicitního kódu COM jsou upřednostňovány formuláře v následující tabulce.  Pro kód COM použijte odpovídající formuláře modelu COM, které jsou uvedeny v předchozí části.  
  
  **Poznámky a popisy**  
  
- `_Result_nullonfailure_`  
  
   Upraví jiné poznámky. Výsledek je nastaven na hodnotu null, pokud se funkce nezdařila.  
  
- `_Result_zeroonfailure_`  
  
   Upraví jiné poznámky. Výsledek je nastaven na hodnotu nula, pokud se funkce nezdařila.  
  
- `_Outptr_result_nullonfailure_`  
  
   Vrácený ukazatel ukazuje na platnou vyrovnávací paměť, pokud je funkce úspěšná, nebo null, pokud funkce selže. Tato anotace je určena pro nevolitelný parametr.  
  
- `_Outptr_opt_result_nullonfailure_`  
  
   Vrácený ukazatel ukazuje na platnou vyrovnávací paměť, pokud je funkce úspěšná, nebo null, pokud funkce selže. Tato poznámka je pro volitelný parametr.  
  
- `_Outref_result_nullonfailure_`  
  
   Vrácený ukazatel ukazuje na platnou vyrovnávací paměť, pokud je funkce úspěšná, nebo null, pokud funkce selže. Tato poznámka je určena pro parametr odkazu.  
  
## <a name="output-reference-parameters"></a>Výstupní parametry odkazu  
 Běžné použití referenčního parametru je pro výstupní parametry.  V případě jednoduchých výstupních referenčních parametrů – `int&` například `_Out_` poskytuje správnou sémantiku.  Nicméně, pokud výstupní hodnota je ukazatel – například `int *&` ekvivalentní poznámky k ukazateli, jako třeba, `_Outptr_ int **` neposkytují správnou sémantiku.  Pro stručné vyjádření sémantiky výstupních referenčních parametrů pro typy ukazatelů použijte tyto složené poznámky:  
  
 **Poznámky a popisy**  
  
- `_Outref_`  
  
     Výsledek musí být platný v post-State a nemůže mít hodnotu null.  
  
- `_Outref_result_maybenull_`  
  
     Výsledek musí být platný v post-State, ale může mít hodnotu null v post-State.  
  
- `_Outref_result_buffer_(s)`  
  
     Výsledek musí být platný v post-State a nemůže mít hodnotu null. Odkazuje na platnou vyrovnávací paměť `s` prvků Size.  
  
- `_Outref_result_bytebuffer_(s)`  
  
     Výsledek musí být platný v post-State a nemůže mít hodnotu null. Odkazuje na platnou vyrovnávací paměť velikostí `s` bajtů.  
  
- `_Outref_result_buffer_to_(s, c)`  
  
     Výsledek musí být platný v post-State a nemůže mít hodnotu null. Odkazuje na vyrovnávací paměť `s` prvků, z nichž první `c` je platná.  
  
- `_Outref_result_bytebuffer_to_(s, c)`  
  
     Výsledek musí být platný v post-State a nemůže mít hodnotu null. Odkazuje na vyrovnávací paměť `s` bajtů, jejichž první `c` je platná.  
  
- `_Outref_result_buffer_all_(s)`  
  
     Výsledek musí být platný v post-State a nemůže mít hodnotu null. Odkazuje na platnou velikost vyrovnávací paměti `s` platných prvků.  
  
- `_Outref_result_bytebuffer_all_(s)`  
  
     Výsledek musí být platný v post-State a nemůže mít hodnotu null. Odkazuje na platnou vyrovnávací paměť `s` bajtů platných prvků.  
  
- `_Outref_result_buffer_maybenull_(s)`  
  
     Výsledek musí být platný v post-State, ale může mít hodnotu null v post-State. Odkazuje na platnou vyrovnávací paměť `s` prvků Size.  
  
- `_Outref_result_bytebuffer_maybenull_(s)`  
  
     Výsledek musí být platný v post-State, ale může mít hodnotu null v post-State. Odkazuje na platnou vyrovnávací paměť velikostí `s` bajtů.  
  
- `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     Výsledek musí být platný v post-State, ale může mít hodnotu null v post-State. Odkazuje na vyrovnávací paměť `s` prvků, z nichž první `c` je platná.  
  
- `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     Výsledek musí být platný v post-State, ale ve stavu post může mít hodnotu null. Odkazuje na vyrovnávací paměť `s` bajtů, jejichž první `c` je platná.  
  
- `_Outref_result_buffer_all_maybenull_(s)`  
  
     Výsledek musí být platný v post-State, ale ve stavu post může mít hodnotu null. Odkazuje na platnou velikost vyrovnávací paměti `s` platných prvků.  
  
- `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     Výsledek musí být platný v post-State, ale ve stavu post může mít hodnotu null. Odkazuje na platnou vyrovnávací paměť `s` bajtů platných prvků.  
  
## <a name="return-values"></a>Návratové hodnoty  
 Návratová hodnota funkce se podobá `_Out_` parametru, ale je na jiné úrovni de reference a nemusíte považovat koncept ukazatele na výsledek.  Pro následující poznámky je vrácená hodnota objekt s poznámkou – skalární, ukazatel na strukturu nebo ukazatel na vyrovnávací paměť. Tyto poznámky mají stejnou sémantiku jako odpovídající `_Out_` Poznámka.  
  
`_Ret_z_`, `_Ret_writes_(s)`, `_Ret_writes_bytes_(s)`, `_Ret_writes_z_(s)`, `_Ret_writes_to_(s,c)`, `_Ret_writes_maybenull_(s)`, `_Ret_writes_to_maybenull_(s)`, `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`, `_Ret_maybenull_z_`, `_Ret_null_`, `_Ret_notnull_`, `_Ret_writes_bytes_to_`, `_Ret_writes_bytes_maybenull_`, `_Ret_writes_bytes_to_maybenull_`
  
## <a name="other-common-annotations"></a>Další běžné poznámky  
 **Poznámky a popisy**  
  
- `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     Parametr, pole nebo výsledek jsou v rozsahu (včetně) z `low` na `hi` .  Ekvivalent k `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` tomuto objektu s poznámkou se aplikuje spolu s příslušnými podmínkami předběžného nebo po stavu.  
  
    > [!IMPORTANT]
    > I když názvy obsahují "in" a "out", sémantika `_In_` a `_Out_` neplatí pro **not** tyto poznámky.  
  
- `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     Hodnota v poznámce je přesně `expr` .  Ekvivalent k `_Satisfies_(_Curr_ == expr)` tomuto objektu s poznámkou se aplikuje spolu s příslušnými podmínkami předběžného nebo po stavu.  
  
- `_Struct_size_bytes_(size)`  
  
     Platí pro strukturu nebo deklaraci třídy.  Označuje, že platný objekt tohoto typu může být větší než deklarovaný typ, přičemž počet bajtů předávaných `size` .  Příklad:  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     Velikost vyrovnávací paměti v bajtech parametru `pM` typu je pak považována za `MyStruct *` :  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>Související informační zdroje  
 [Blog týmu analýzy kódu](https://blogs.msdn.com/b/codeanalysis/)  
  
## <a name="see-also"></a>Viz také  
 [Použití poznámek SAL k omezení vad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Porozumění SAL](../code-quality/understanding-sal.md)   
 [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)   
 [Přidávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)   
 [Zadávání poznámek k chování při zamykání](../code-quality/annotating-locking-behavior.md)   
 [Určení, kdy a kde se má Poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Vnitřní funkce](../code-quality/intrinsic-functions.md)   
 [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)
