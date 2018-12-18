---
title: Zadávání poznámek k parametrům funkcí a vrácené hodnoty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7886b7a49999890520aaeaf216159647cd9fdf27
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788391"
---
# <a name="annotating-function-parameters-and-return-values"></a>Zadávání poznámek k parametrům funkcí a návratovým hodnotám
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento článek popisuje typické použití poznámek pro jednoduchou funkci parametry – skaláry a ukazatele na třídy a struktury – a většinou druhů vyrovnávací paměti.  Tento článek také popisuje běžné vzory využití pro poznámky. Další poznámky, které se vztahují na funkce, najdete v části [zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)  
  
## <a name="pointer-parameters"></a>Parametry ukazatele  
 Poznámky v následující tabulce když parametr ukazatele je poznámkou, analyzátor hlásí chybu Jestliže je ukazatel null.  To platí pro ukazatele a libovolné položky dat, které ukazuje.  
  
 **Poznámky a popisy**  
  
-   `_In_`  
  
     Označí vstupní parametry, které jsou skaláry, struktury, odkazy na struktury a podobně.  Explicitně může být použita na jednoduché skaláry.  Parametr musí být platné v předběžné stavu a se nezmění.  
  
-   `_Out_`  
  
     Označí výstupní parametry, které jsou skaláry, struktury, odkazy na struktury a podobně.  Nevztahují to na objekt, který nemůže vracet hodnotu – například skaláru, který je předán podle hodnoty.  Parametr nemusí být platné v předběžné stavu, ale musí být platný po stavu.  
  
-   `_Inout_`  
  
     Označí parametr, který se změní podle funkce.  Musí být ve stavu před a po stavu platný, ale předpokládá, že je před a po volání mají různé hodnoty. Musí vyrovnat upravitelné hodnoty.  
  
-   `_In_z_`  
  
     Ukazatel na řetězec zakončený hodnotou null, který se používá jako vstup.  V předběžné stavu musí být platný řetězec.  Varianty `PSTR`, které již mají správnou poznámky, jsou upřednostňované.  
  
-   `_Inout_z_`  
  
     Ukazatel na pole znaků zakončených znakem null, který bude změněn.  Musí být platná před a po volání, ale hodnoty se předpokládá, že jste změnili.  Mohou být přesunuty ukončovacího znaku null, ale můžete získat přístup na pouze elementy až původní ukončovacího znaku null.  
  
-   `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     Ukazatel na pole, která čte funkce.  Je pole o velikosti `s` prvky, které musí být platný.  
  
     `_bytes_` Variant poskytuje velikost v bajtech, ne prvky. Používejte pouze v případě, že velikost nelze vyjádřen jako prvky.  Například `char` by řetězců použijte `_bytes_` variant pouze v případě, že podobný funkce, které používá `wchar_t` by.  
  
-   `_In_reads_z_(s)`  
  
     Ukazatel na pole, které je zakončený hodnotou null a má známou velikost. Prvky až ukončovacího znaku null – nebo `s` Pokud neexistuje žádný ukončovacího znaku null – musí být platné v předběžné stavu.  Pokud je znám velikost v bajtech, škálovat `s` velikost elementu.  
  
-   `_In_reads_or_z_(s)`  
  
     Ukazatel na pole, které je zakončený hodnotou null nebo má známou velikost nebo obojí. Prvky až ukončovacího znaku null – nebo `s` Pokud neexistuje žádný ukončovacího znaku null – musí být platné v předběžné stavu.  Pokud je znám velikost v bajtech, škálovat `s` velikost elementu.  (Použít u `strn` řady.)  
  
-   `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     Ukazatel na pole `s` prvky (odezvy v bajtech), které budou zapsány pomocí funkce.  Prvky pole nemusí být platné v předběžné stavu a počet prvků, které jsou platné po stavu není uvedený.  Pokud jsou poznámky na typ parametru, tato nastavení použijí v po stavu. Zvažte například následující kód.  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     V tomto příkladu obsahuje volající rezervu `size` prvky pro `p1`.  `MyStringCopy` Některé z těchto elementů je platný. Důležitější je `_Null_terminated_` poznámky na `PWSTR` znamená, že `p1` je zakončený hodnotou null v po stavu.  Tímto způsobem je dobře definovaný počet platné prvky, ale počet konkrétní elementu se nevyžaduje.  
  
     `_bytes_` Variant poskytuje velikost v bajtech, ne prvky. Používejte pouze v případě, že velikost nelze vyjádřen jako prvky.  Například `char` by řetězců použijte `_bytes_` variant pouze v případě, že podobný funkce, které používá `wchar_t` by.  
  
-   `_Out_writes_z_(s)`  
  
     Ukazatel na pole `s` elementy.  Elementy nemusí být platné v předběžné stavu.  Po stavu, prvky nahoru až ukončovacího znaku null, která musí být k dispozici – musí být platný.  Pokud je znám velikost v bajtech, škálovat `s` velikost elementu.  
  
-   `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     Ukazatel na pole, která je číst a zapisovat ve funkci.  Jde o velikosti `s` elementy a je platný do stavu před a po stavu.  
  
     `_bytes_` Variant poskytuje velikost v bajtech, ne prvky. Používejte pouze v případě, že velikost nelze vyjádřen jako prvky.  Například `char` by řetězců použijte `_bytes_` variant pouze v případě, že podobný funkce, které používá `wchar_t` by.  
  
-   `_Inout_updates_z_(s)`  
  
     Ukazatel na pole, které je zakončený hodnotou null a má známou velikost. Prvky nahoru až ukončovacího znaku null – které musí být k dispozici – musí být ve stavu před a po stavu platná.  Hodnota v po stavu se předpokládá, že se liší od hodnoty v předběžné stavu; To zahrnuje umístění ukončovacího znaku null. Pokud je znám velikost v bajtech, škálovat `s` velikost elementu.  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Ukazatel na pole `s` elementy.  Elementy nemusí být platné v předběžné stavu.  V prvků až po stavu `c`- tý prvek musí být platný.  Pokud je znám velikost v bajtech, škálovat `s` a `c` Určuje velikost elementu nebo použití `_bytes_` variant, která je definována jako:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Jinými slovy, každý prvek, který existuje ve vyrovnávací paměti až `s` ve stavu před je platná po stavu.  Příklad:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Ukazatel na pole, která je číst a zapsat pomocí funkce.  Jde o velikosti `s` prvky, které musí být platné v předběžné stavu, a `c` elementy musí být platný po stavu.  
  
     `_bytes_` Variant poskytuje velikost v bajtech, ne prvky. Používejte pouze v případě, že velikost nelze vyjádřen jako prvky.  Například `char` by řetězců použijte `_bytes_` variant pouze v případě, že podobný funkce, které používá `wchar_t` by.  
  
-   `_Inout_updates_z_(s)`  
  
     Ukazatel na pole, které je zakončený hodnotou null a má známou velikost. Prvky nahoru až ukončovacího znaku null – které musí být k dispozici – musí být ve stavu před a po stavu platná.  Hodnota v po stavu se předpokládá, že se liší od hodnoty v předběžné stavu; To zahrnuje umístění ukončovacího znaku null. Pokud je znám velikost v bajtech, škálovat `s` velikost elementu.  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Ukazatel na pole `s` elementy.  Elementy nemusí být platné v předběžné stavu.  V prvků až po stavu `c`- tý prvek musí být platný.  Pokud je znám velikost v bajtech, škálovat `s` a `c` Určuje velikost elementu nebo použití `_bytes_` variant, která je definována jako:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Jinými slovy, každý prvek, který existuje ve vyrovnávací paměti až `s` ve stavu před je platná po stavu.  Příklad:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Ukazatel na pole, která je číst a zapsat pomocí funkce.  Jde o velikosti `s` prvky, které musí být platné v předběžné stavu, a `c` elementy musí být platný po stavu.  
  
     `_bytes_` Variant poskytuje velikost v bajtech, ne prvky. Používejte pouze v případě, že velikost nelze vyjádřen jako prvky.  Například `char` by řetězců použijte `_bytes_` variant pouze v případě, že podobný funkce, které používá `wchar_t` by.  
  
-   `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     Ukazatel na pole, která je číst a zapsat pomocí funkce velikost `s` elementy. Definovány jako ekvivalentní:  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     Jinými slovy, každý prvek, který existuje ve vyrovnávací paměti až `s` v předběžné stavu je platný do stavu před a po stavu.  
  
     `_bytes_` Variant poskytuje velikost v bajtech, ne prvky. Používejte pouze v případě, že velikost nelze vyjádřen jako prvky.  Například `char` by řetězců použijte `_bytes_` variant pouze v případě, že podobný funkce, které používá `wchar_t` by.  
  
-   `_In_reads_to_ptr_(p)`  
  
     Ukazatel na pole pro kterou výraz `p` – `_Curr_` (to znamená `p` minus `_Curr_`) je definován na příslušný jazyk standardní.  Prvky před `p` musí být platné v předběžné stavu.  
  
-   `_In_reads_to_ptr_z_(p)`  
  
     Ukazatel na pole zakončené znakem null pro kterou výraz `p` – `_Curr_` (to znamená `p` minus `_Curr_`) je definován na příslušný jazyk standardní.  Prvky před `p` musí být platné v předběžné stavu.  
  
-   `_Out_writes_to_ptr_(p)`  
  
     Ukazatel na pole pro kterou výraz `p` – `_Curr_` (to znamená `p` minus `_Curr_`) je definován na příslušný jazyk standardní.  Prvky před `p` nemusí být platné v předběžné stavu a musí být platný po stavu.  
  
-   `_Out_writes_to_ptr_z_(p)`  
  
     Ukazatel na pole zakončené znakem null pro kterou výraz `p` – `_Curr_` (to znamená `p` minus `_Curr_`) je definován na příslušný jazyk standardní.  Prvky před `p` nemusí být platné v předběžné stavu a musí být platný po stavu.  
  
## <a name="optional-pointer-parameters"></a>Volitelné ukazatele parametry  
 Pokud obsahuje anotaci parametru ukazatel `_opt_`, znamená to, že tento parametr může mít hodnotu null. V opačném případě Poznámka provádí shodná s verzí, který neobsahuje `_opt_`. Tady je seznam `_opt_` varianty ukazatel parametr poznámky:  
  
||||  
|-|-|-|  
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>Výstupní parametry ukazatele  
 Výstupní parametry ukazatele vyžadují zvláštní zápis k rozlišení null-ness na parametr a odkazovala na umístění.  
  
 **Poznámky a popisy**  
  
- `_Outptr_`  
  
   Parametr nemůže mít hodnotu null, a ve stavu po odkazovala na umístění nemůže mít hodnotu null a musí být platný.  
  
- `_Outptr_opt_`  
  
   Parametr může mít hodnotu null, ale po stavu odkazovala na umístění nemůže mít hodnotu null a musí být platný.  
  
- `_Outptr_result_maybenull_`  
  
   Parametr nemůže mít hodnotu null a v po stavu odkazovala na umístění může být null.  
  
- `_Outptr_opt_result_maybenull_`  
  
   Parametr může mít hodnotu null a v po stavu odkazovala na umístění může být null.  
  
  V následující tabulce jsou další podřetězců vloženy do název poznámky další kvalifikovat význam anotace.  Jsou různé podřetězců `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`, a `_to_`.  
  
> [!IMPORTANT]
>  Pokud rozhraní, které jsou zadávání poznámek k modelu COM, formulář modelu COM těchto poznámek. U jiných typů rozhraní nepoužívat COM poznámky.  
  
 **Poznámky a popisy**  
  
- `_Outptr_result_z_`  
  
   `_Outptr_opt_result_z_`  
  
   `_Outptr_result_maybenull_z_`  
  
   `_Ouptr_opt_result_maybenull_z_`  
  
   Vrácený ukazatel `_Null_terminated_` poznámky.  
  
- `_COM_Outptr_`  
  
   `_COM_Outptr_opt_`  
  
   `_COM_Outptr_result_maybenull_`  
  
   `_COM_Outptr_opt_result_maybenull_`  
  
   Vrácenému ukazateli má sémantiku modelu COM a proto má `_On_failure_` po podmínka, vrácený ukazatel je null.  
  
- `_Outptr_result_buffer_(s)`  
  
   `_Outptr_result_bytebuffer_(s)`  
  
   `_Outptr_opt_result_buffer_(s)`  
  
   `_Outptr_opt_result_bytebuffer_(s)`  
  
   Vrácený ukazatel odkazuje na platnou vyrovnávací paměť o velikosti `s` elementy nebo bajtů.  
  
- `_Outptr_result_buffer_to_(s, c)`  
  
   `_Outptr_result_bytebuffer_to_(s, c)`  
  
   `_Outptr_opt_result_buffer_to_(s,c)`  
  
   `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
   Vrácený ukazatel odkazuje na vyrovnávací paměť o velikosti `s` elementy nebo bajtů, z nichž první `c` jsou platné.  
  
  Určité konvence rozhraní předpokládá, že výstupní parametry budou zrušeny při selhání.  S výjimkou výslovně kód v modelu COM jsou upřednostňovanou formuláře v následující tabulce.  Pro kód v modelu COM použijte odpovídající formuláře modelu COM, které jsou uvedené v předchozí části.  
  
  **Poznámky a popisy**  
  
- `_Result_nullonfailure_`  
  
   Upravuje se další poznámky. Výsledek je nastaven na hodnotu null, pokud funkce selže.  
  
- `_Result_zeroonfailure_`  
  
   Upravuje se další poznámky. Výsledek je nastaven na hodnotu nula, pokud funkce selže.  
  
- `_Outptr_result_nullonfailure_`  
  
   Vrácený ukazatel odkazuje na platnou vyrovnávací paměť, pokud je funkce úspěšná, nebo hodnota null, pokud funkce selže. Tato poznámka je povinný parametr.  
  
- `_Outptr_opt_result_nullonfailure_`  
  
   Vrácený ukazatel odkazuje na platnou vyrovnávací paměť, pokud je funkce úspěšná, nebo hodnota null, pokud funkce selže. Tato poznámka je volitelný parametr.  
  
- `_Outref_result_nullonfailure_`  
  
   Vrácený ukazatel odkazuje na platnou vyrovnávací paměť, pokud je funkce úspěšná, nebo hodnota null, pokud funkce selže. Tato poznámka se pro referenční parametr.  
  
## <a name="output-reference-parameters"></a>Výstupní parametry odkazu  
 Běžné použití parametru odkaz je pro výstupní parametry.  Pro jednoduché výstupní parametry odkaz – například `int&`–`_Out_` poskytne tak sémantiku správné.  Ale když výstupní hodnota je ukazatel – například `int *&`– poznámky ekvivalentní ukazatel, jako jsou `_Outptr_ int **` neposkytují správné sémantiku.  Stručně a výstižně express sémantiku odkazu výstupních parametrů pro typy ukazatelů, použijte tyto složené poznámky:  
  
 **Poznámky a popisy**  
  
-   `_Outref_`  
  
     Výsledek musí být platný po stavu a nemůže mít hodnotu null.  
  
-   `_Outref_result_maybenull_`  
  
     Výsledek musí být platný po stavu, ale může být v po stavu hodnotu null.  
  
-   `_Outref_result_buffer_(s)`  
  
     Výsledek musí být platný po stavu a nemůže mít hodnotu null. Odkazuje na platnou vyrovnávací paměť o velikosti `s` elementy.  
  
-   `_Outref_result_bytebuffer_(s)`  
  
     Výsledek musí být platný po stavu a nemůže mít hodnotu null. Odkazuje na platnou vyrovnávací paměť o velikosti `s` bajtů.  
  
-   `_Outref_result_buffer_to_(s, c)`  
  
     Výsledek musí být platný po stavu a nemůže mít hodnotu null. Odkazuje na vyrovnávací paměť `s` prvky, z nichž první `c` jsou platné.  
  
-   `_Outref_result_bytebuffer_to_(s, c)`  
  
     Výsledek musí být platný po stavu a nemůže mít hodnotu null. Odkazuje na vyrovnávací paměť `s` bajtů z nichž první `c` jsou platné.  
  
-   `_Outref_result_buffer_all_(s)`  
  
     Výsledek musí být platný po stavu a nemůže mít hodnotu null. Odkazuje na platnou vyrovnávací paměť o velikosti `s` platné prvky.  
  
-   `_Outref_result_bytebuffer_all_(s)`  
  
     Výsledek musí být platný po stavu a nemůže mít hodnotu null. Odkazuje na platnou vyrovnávací paměť `s` bajtů platné prvky.  
  
-   `_Outref_result_buffer_maybenull_(s)`  
  
     Výsledek musí být platný po stavu, ale může být v po stavu hodnotu null. Odkazuje na platnou vyrovnávací paměť o velikosti `s` elementy.  
  
-   `_Outref_result_bytebuffer_maybenull_(s)`  
  
     Výsledek musí být platný po stavu, ale může být v po stavu hodnotu null. Odkazuje na platnou vyrovnávací paměť o velikosti `s` bajtů.  
  
-   `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     Výsledek musí být platný po stavu, ale může být v po stavu hodnotu null. Odkazuje na vyrovnávací paměť `s` prvky, z nichž první `c` jsou platné.  
  
-   `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     Výsledek musí být platný po stavu, ale může mít hodnotu null v příspěvku stavu. Odkazuje na vyrovnávací paměť `s` bajtů z nichž první `c` jsou platné.  
  
-   `_Outref_result_buffer_all_maybenull_(s)`  
  
     Výsledek musí být platný po stavu, ale může mít hodnotu null v příspěvku stavu. Odkazuje na platnou vyrovnávací paměť o velikosti `s` platné prvky.  
  
-   `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     Výsledek musí být platný po stavu, ale může mít hodnotu null v příspěvku stavu. Odkazuje na platnou vyrovnávací paměť `s` bajtů platné prvky.  
  
## <a name="return-values"></a>Návratové hodnoty  
 Vypadá podobně jako návratovou hodnotu funkce `_Out_` parametr je ale na jiné úrovni de-reference a není nutné vzít v úvahu koncept ukazatel na výsledek.  Pro následující poznámky, vrácená hodnota je objekt s poznámkami – skalární, ukazatel na strukturu nebo ukazatel do vyrovnávací paměti. Tyto poznámky obsahují stejnou sémantiku jako odpovídající `_Out_` poznámky.  
  
|||  
|-|-|  
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|  
  
## <a name="other-common-annotations"></a>Další běžné poznámky  
 **Poznámky a popisy**  
  
-   `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     Parametr, pole nebo výsledek je v rozsahu (včetně) z `low` k `hi`.  Ekvivalentní `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` , která je použita na objekt s poznámkami společně s odpovídající podmínky předem stavu nebo po stavu.  
  
    > [!IMPORTANT]
    >  I když obsahují názvy "v" a "out", sémantika `_In_` a `_Out_` proveďte **není** platí tyto poznámky.  
  
-   `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     S poznámkami hodnota je právě `expr`.  Ekvivalentní `_Satisfies_(_Curr_ == expr)` , která je použita na objekt s poznámkami společně s odpovídající podmínky předem stavu nebo po stavu.  
  
-   `_Struct_size_bytes_(size)`  
  
     Platí pro deklaraci třídy nebo struktury.  Označuje, že platný objekt daného typu může být větší než deklarovaného typu, s počtem bajtů je dán `size`.  Příklad:  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     Velikost vyrovnávací paměti v bajtech parametr `pM` typu `MyStruct *` pak slov za:  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>Související prostředky  
 [Blog týmu analýzy kódu](http://go.microsoft.com/fwlink/?LinkId=251197)  
  
## <a name="see-also"></a>Viz také  
 [Použití poznámek SAL k omezení defektů kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Porozumění SAL](../code-quality/understanding-sal.md)   
 [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)   
 [Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)   
 [Zadávání poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md)   
 [Určení, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Vnitřní funkce](../code-quality/intrinsic-functions.md)   
 [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)



