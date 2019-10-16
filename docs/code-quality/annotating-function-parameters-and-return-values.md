---
title: Zadávání poznámek k parametrům funkcí a návratovým hodnotám
ms.date: 10/15/2019
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
- _Scanf_format_string_
- _Scanf_s_format_string_
- _Printf_format_string_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: ca1e66defbce50a9119e817155bcc2a98d01af9d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72442407"
---
# <a name="annotating-function-parameters-and-return-values"></a>Zadávání poznámek k parametrům funkcí a návratovým hodnotám
Tento článek popisuje typické použití poznámek pro jednoduché parametry funkcí – skalární objekty a ukazatele na struktury a třídy – a většinu druhů vyrovnávacích pamětí.  Tento článek také ukazuje běžné způsoby použití pro poznámky. Další poznámky, které se vztahují k funkcím, najdete v tématu věnovaném [chování funkcí s poznámkami](../code-quality/annotating-function-behavior.md).

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

     Ukazatel na řetězec zakončený hodnotou null, který se používá jako vstup.  Řetězec musí být platný v předběžném stavu.  Jsou upřednostňovány varianty `PSTR`, které již mají správné poznámky.

- `_Inout_z_`

     Ukazatel na pole znaků zakončené hodnotou null, které bude upraveno.  Musí být platný před a po volání, ale hodnota se předpokládá, že se změnila.  Ukončovací znak null lze přesunout, ale mohou být k dispozici pouze prvky až k původnímu ukončovacímu znaku null.

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Ukazatel na pole, který je čten funkcí.  Pole má velikost `s` prvků, přičemž všechny musí být platné.

     Varianta `_bytes_` dává velikost v bajtech namísto prvků. Tuto hodnotu použijte pouze v případě, že velikost nelze vyjádřit jako prvky.  Například `char` řetězce by používaly variantu `_bytes_` pouze v případě, že je podobná funkce, která používá `wchar_t`.

- `_In_reads_z_(s)`

     Ukazatel na pole, které má ukončenou hodnotu null a má známou velikost. Prvky až do ukončovacího znaku null, nebo `s`, pokud neexistuje ukončovací znak null – musí být platný v předběžném stavu.  Pokud je velikost známá v bajtech, škálovat `s` podle velikosti prvku.

- `_In_reads_or_z_(s)`

     Ukazatel na pole, které je zakončené hodnotou null nebo má známou velikost nebo obojí. Prvky až do ukončovacího znaku null, nebo `s`, pokud neexistuje ukončovací znak null – musí být platný v předběžném stavu.  Pokud je velikost známá v bajtech, škálovat `s` podle velikosti prvku.  (Používá se pro @no__t řady 0)

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Ukazatel na pole `s` prvků (odp. Byte), který bude zapsán funkcí.  Prvky pole nemusí být platné v předběžné verzi a počet prvků, které jsou platné v post-State, není určen.  Pokud existují poznámky k typu parametru, jsou aplikovány v post-State. Zvažte například následující kód.

     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`

     V tomto příkladu volající poskytuje vyrovnávací paměť `size` prvků pro `p1`.  `MyStringCopy` způsobí, že některé z těchto elementů jsou platné. Důležitější je, `_Null_terminated_` anotace v `PWSTR` znamená, že `p1` je v post-State zakončené znakem null.  Tímto způsobem je počet platných prvků stále správně definován, ale konkrétní počet prvků není vyžadován.

     Varianta `_bytes_` dává velikost v bajtech namísto prvků. Tuto hodnotu použijte pouze v případě, že velikost nelze vyjádřit jako prvky.  Například `char` řetězce by používaly variantu `_bytes_` pouze v případě, že je podobná funkce, která používá `wchar_t`.

- `_Out_writes_z_(s)`

     Ukazatel na pole `s` prvků.  Elementy nemusí být platné v předběžném stavu.  V post-State prvky až po ukončovací znak null, který musí být přítomen – musí být platný.  Pokud je velikost známá v bajtech, škálovat `s` podle velikosti prvku.

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Ukazatel na pole, které je ve funkci čteno a zapisováno.  Má velikost `s` prvků a je platná v předběžném stavu a po stavu.

     Varianta `_bytes_` dává velikost v bajtech namísto prvků. Tuto hodnotu použijte pouze v případě, že velikost nelze vyjádřit jako prvky.  Například `char` řetězce by používaly variantu `_bytes_` pouze v případě, že je podobná funkce, která používá `wchar_t`.

- `_Inout_updates_z_(s)`

     Ukazatel na pole, které má ukončenou hodnotu null a má známou velikost. Prvky až do ukončovacího znaku null, který musí být přítomen – musí být platný v představech i po stavu.  Hodnota v příspěvku je považována za odlišnou od hodnoty v předběžném stavu; To zahrnuje umístění ukončovacího znaku null. Pokud je velikost známá v bajtech, škálovat `s` podle velikosti prvku.

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Ukazatel na pole `s` prvků.  Elementy nemusí být platné v předběžném stavu.  V rámci po stavu musí být prvky až @no__t -0-th platné.  Pokud je velikost známá v bajtech, Škálujte `s` a `c` podle velikosti prvku nebo použijte variantu `_bytes_`, která je definována jako:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     Jinými slovy, každý prvek, který existuje ve vyrovnávací paměti až do `s` v předběžném stavu, je platný v příspěvku.  Příklad:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Ukazatel na pole, který je čten a zapisován funkcí.  Má velikost @no__t prvky-0, všechny musí být platné v představech a elementy `c` musí být platné v post-State.

     Varianta `_bytes_` dává velikost v bajtech namísto prvků. Tuto hodnotu použijte pouze v případě, že velikost nelze vyjádřit jako prvky.  Například `char` řetězce by používaly variantu `_bytes_` pouze v případě, že je podobná funkce, která používá `wchar_t`.

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Ukazatel na pole, který je čten a napsán funkcí Size `s` prvků. Definováno jako ekvivalent:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     Jinými slovy, každý prvek, který existuje ve vyrovnávací paměti až do `s` v předběžném stavu, je platný v představovém a následném stavu.

     Varianta `_bytes_` dává velikost v bajtech namísto prvků. Tuto hodnotu použijte pouze v případě, že velikost nelze vyjádřit jako prvky.  Například `char` řetězce by používaly variantu `_bytes_` pouze v případě, že je podobná funkce, která používá `wchar_t`.

- `_In_reads_to_ptr_(p)`

     Ukazatel na pole, pro které se výraz `p` @ no__t-1 @ no__t-2 (tj. `p` minus `_Curr_`), je definován odpovídajícím standardem jazyka.  Prvky před `p` musí být platné v předběžném stavu.

- `_In_reads_to_ptr_z_(p)`

     Ukazatel na pole zakončené hodnotou null, pro které se výraz `p` @ no__t-1 @ no__t-2 (tj. `p` minus `_Curr_`) je definován odpovídajícím standardem jazyka.  Prvky před `p` musí být platné v předběžném stavu.

- `_Out_writes_to_ptr_(p)`

     Ukazatel na pole, pro které se výraz `p` @ no__t-1 @ no__t-2 (tj. `p` minus `_Curr_`), je definován odpovídajícím standardem jazyka.  Prvky před `p` nemusí být platné v představu a musí být platné v post-State.

- `_Out_writes_to_ptr_z_(p)`

     Ukazatel na pole zakončené hodnotou null, pro které se výraz `p` @ no__t-1 @ no__t-2 (tj. `p` minus `_Curr_`) je definován odpovídajícím standardem jazyka.  Prvky před `p` nemusí být platné v představu a musí být platné v post-State.

## <a name="optional-pointer-parameters"></a>Volitelné parametry ukazatele

Když Poznámka parametru ukazatele obsahuje `_opt_`, znamená to, že parametr může mít hodnotu null. Jinak Poznámka vychází z verze, která nezahrnuje `_opt_`. Tady je seznam variant `_opt_` pro parametry ukazatele poznámky:

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

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

  V následující tabulce jsou do názvu poznámky vloženy další podřetězce, aby bylo možné lépe kvalifikovat význam poznámky.  Jednotlivé podřetězce jsou `_z`, `_COM_`, `_buffer_`, `_bytebuffer_` a `_to_`.

> [!IMPORTANT]
> Pokud je rozhraní, které přidáváte, k disznámce COM, použijte ve formuláři modelu COM tyto poznámky. Nepoužívejte anotace COM s žádným jiným typem rozhraní.

**Poznámky a popisy**

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Ouptr_opt_result_maybenull_z_`

   Vrácený ukazatel má anotaci `_Null_terminated_`.

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   Vrácený ukazatel má sémantiku modelu COM, a proto má za předpokladu `_On_failure_`, že vrácený ukazatel je null.

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   Vrácený ukazatel ukazuje na platnou vyrovnávací paměť velikosti `s` prvků nebo bajtů.

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   Vrácený ukazatel ukazuje na vyrovnávací paměť velikosti @no__t 0 prvků nebo bajtů, z nichž první `c` jsou platné.

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

Běžné použití referenčního parametru je pro výstupní parametry.  U jednoduchých výstupních referenčních parametrů – například `int&` – `_Out_` poskytuje správnou sémantiku.  Pokud je však výstupní hodnota ukazatel, například `int *&` – ekvivalentní anotace s ukazateli, jako je `_Outptr_ int **`, neposkytují správnou sémantiku.  Pro stručné vyjádření sémantiky výstupních referenčních parametrů pro typy ukazatelů použijte tyto složené poznámky:

**Poznámky a popisy**

- `_Outref_`

     Výsledek musí být platný v post-State a nemůže mít hodnotu null.

- `_Outref_result_maybenull_`

     Výsledek musí být platný v post-State, ale může mít hodnotu null v post-State.

- `_Outref_result_buffer_(s)`

     Výsledek musí být platný v post-State a nemůže mít hodnotu null. Odkazuje na platnou vyrovnávací paměť velikosti `s` prvků.

- `_Outref_result_bytebuffer_(s)`

     Výsledek musí být platný v post-State a nemůže mít hodnotu null. Odkazuje na platnou velikost vyrovnávací paměti `s` bajtů.

- `_Outref_result_buffer_to_(s, c)`

     Výsledek musí být platný v post-State a nemůže mít hodnotu null. Odkazuje na vyrovnávací paměť prvků `s`, jejichž první `c` jsou platné.

- `_Outref_result_bytebuffer_to_(s, c)`

     Výsledek musí být platný v post-State a nemůže mít hodnotu null. Odkazuje na vyrovnávací paměť `s` bajtů, z nichž první `c` jsou platné.

- `_Outref_result_buffer_all_(s)`

     Výsledek musí být platný v post-State a nemůže mít hodnotu null. Odkazuje na platnou vyrovnávací paměť velikosti `s` platných prvků.

- `_Outref_result_bytebuffer_all_(s)`

     Výsledek musí být platný v post-State a nemůže mít hodnotu null. Odkazuje na platnou vyrovnávací paměť `s` bajtů platných prvků.

- `_Outref_result_buffer_maybenull_(s)`

     Výsledek musí být platný v post-State, ale může mít hodnotu null v post-State. Odkazuje na platnou vyrovnávací paměť velikosti `s` prvků.

- `_Outref_result_bytebuffer_maybenull_(s)`

     Výsledek musí být platný v post-State, ale může mít hodnotu null v post-State. Odkazuje na platnou velikost vyrovnávací paměti `s` bajtů.

- `_Outref_result_buffer_to_maybenull_(s, c)`

     Výsledek musí být platný v post-State, ale může mít hodnotu null v post-State. Odkazuje na vyrovnávací paměť prvků `s`, jejichž první `c` jsou platné.

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     Výsledek musí být platný v post-State, ale ve stavu post může mít hodnotu null. Odkazuje na vyrovnávací paměť `s` bajtů, z nichž první `c` jsou platné.

- `_Outref_result_buffer_all_maybenull_(s)`

     Výsledek musí být platný v post-State, ale ve stavu post může mít hodnotu null. Odkazuje na platnou vyrovnávací paměť velikosti `s` platných prvků.

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     Výsledek musí být platný v post-State, ale ve stavu post může mít hodnotu null. Odkazuje na platnou vyrovnávací paměť `s` bajtů platných prvků.

## <a name="return-values"></a>Návratové hodnoty

Návratová hodnota funkce připomíná parametr `_Out_`, ale je na jiné úrovni de reference a nemusíte považovat koncept ukazatele na výsledek.  Pro následující poznámky je vrácená hodnota objekt s poznámkou – skalární, ukazatel na strukturu nebo ukazatel na vyrovnávací paměť. Tyto poznámky mají stejnou sémantiku jako odpovídající anotace `_Out_`.

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="format-string-parameters"></a>Parametry formátovacího řetězce

- `_Printf_format_string_` označuje, že parametr je formátovací řetězec pro použití ve výrazu `printf`.

     **Příklad**

    ```cpp
    int MyPrintF(_Printf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwprintf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_format_string_` označuje, že parametr je formátovací řetězec pro použití ve výrazu `scanf`.

     **Příklad**

    ```cpp
    int MyScanF(_Scanf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_s_format_string_` označuje, že parametr je formátovací řetězec pro použití ve výrazu `scanf_s`.

     **Příklad**

    ```cpp
    int MyScanF_s(_Scanf_s_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf_s(format, args);
           va_end(args);
           return ret;
    }
    ```

## <a name="other-common-annotations"></a>Další běžné poznámky

**Poznámky a popisy**

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     Parametr, pole nebo výsledek jsou v rozsahu (včetně) od `low` do `hi`.  Ekvivalent `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)`, který se aplikuje na objekt s poznámkami spolu s příslušnými podmínkami předběžného nebo po stavu.

    > [!IMPORTANT]
    > I když názvy obsahují "in" a "out", sémantika `_In_` a `_Out_` se na tyto poznámky **nevztahují** .

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     Hodnota v poznámce je přesně `expr`.  Ekvivalent `_Satisfies_(_Curr_ == expr)`, který se aplikuje na objekt s poznámkami spolu s příslušnými podmínkami předběžného nebo po stavu.

- `_Struct_size_bytes_(size)`

     Platí pro strukturu nebo deklaraci třídy.  Označuje, že platný objekt tohoto typu může být větší než deklarovaný typ, s počtem bajtů předávaných pomocí `size`.  Příklad:

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     Velikost vyrovnávací paměti v bajtech parametru `pM` typu `MyStruct *` je pak provedena:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>Související prostředky

[Blog týmu analýzy kódu](http://go.microsoft.com/fwlink/?LinkId=251197)

## <a name="see-also"></a>Viz také

- [Použití poznámek SAL k snížení míry výskytu závad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Porozumění SAL](../code-quality/understanding-sal.md)
- [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)
- [Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)
- [Zadávání poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md)
- [Určení, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Vnitřní funkce](../code-quality/intrinsic-functions.md)
- [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)
