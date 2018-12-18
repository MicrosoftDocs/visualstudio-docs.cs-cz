---
title: Porozumění SAL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 712d99f3839982632e54b622b3512eb611f2bf95
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792812"
---
# <a name="understanding-sal"></a>Porozumění SAL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poznámka jazyk zdrojového kódu Microsoft (SAL) poskytuje sadu poznámky, které můžete použít k popisu, jak funkce používá parametry, předpokladů, které usnadňuje jejich a záruky, které provede po dokončení. Poznámky jsou definována v hlavičkovém souboru `<sal.h>`. Visual Studio analýzy kódu pro jazyk C++ využívá anotací SAL k úpravě jeho analýzy funkce. Další informace o SAL 2.0 k vývoji ovladačů Windows najdete v tématu [poznámky SAL 2.0 pro Windows ovladače](http://go.microsoft.com/fwlink/?LinkId=250979).  
  
 Pouze omezené možnosti pro vývojáře konzistentně vyjádřit záměr a invariance poskytují nativně, C a C++. S použitím poznámky SAL, můžete popsat funkce podrobněji tak, aby vývojáři, kteří jsou jejich používáním můžete lépe pochopit, jak je používat.  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>Co je SAL a proč ji používat?  
 Jednoduše řečeno, je SAL levný způsob, jak nechat kompilátor, aby váš kód vyhledat.  
  
### <a name="sal-makes-code-more-valuable"></a>Poznámky SAL díky kódu Hodnotnějšímu  
 SAL usnadňuje návrh kódu pomohou lépe porozumět, lidé i nástroje Analýza kódu. Podívejte se například, která zobrazuje funkce modulu runtime jazyka C `memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 Zjistit, co tato funkce dělá? Pokud funkce je implementovaná nebo názvem, se musí zajistit správnost program udržovat určité vlastnosti. Právě pohledem na deklarace, jako je například v příkladu, nevíte, co jsou. Bez poznámek SAL je nutné spoléhají na dokumentaci nebo komentáře ke kódu. Tady je dokumentaci MSDN pro `memcpy` říká:  
  
> "Kopie počet bajtů src na cíl. Pokud se zdrojový a cílový překrývají, chování memcpy není definováno. Memmove použijte ke zpracování překrývající se oblasti.   
> **Poznámka k zabezpečení:** Ujistěte se, že cílová vyrovnávací paměť je stejný velké nebo větší než zdrojové vyrovnávací paměti. Další informace najdete v tématu předcházení přetečení vyrovnávací paměti."  
  
 Dokumentace obsahuje několik bitů informace, které naznačují, že váš kód musí udržovat určité vlastnosti zajistit správnost programu:  
  
- `memcpy` kopie `count` bajtů ze zdrojové vyrovnávací paměti pro cílové vyrovnávací paměti.  
  
- Cílová vyrovnávací paměť musí být přinejmenším stejně velká jako zdrojové vyrovnávací paměti.  
  
  Kompilátor nemůže však přečíst dokumentaci nebo neformální poznámky. Nebude vědět, že existuje vztah mezi dvěma vyrovnávací paměti a `count`, a to také nelze uhodnout efektivně o relaci. Poznámky SAL může přehlednějším týkající se vlastností a provádění funkce, jak je znázorněno zde:  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Všimněte si, že tyto poznámky se podobají informace v dokumentaci MSDN, ale jsou stručnější a řídí se sémantického modelu. Při čtení tento kód můžete rychle pochopit vlastnosti této funkce a o tom, aby se zabránilo problémům zabezpečení přetečení vyrovnávací paměti. Ještě lepší sémantické vzory, které poskytuje SAL zlepšují efektivitu automatizované kód analytické nástroje v rané fázi zjišťování potenciálních chyb. Představte si, že někdo zapíše tento chybový provádění `wmemcpy`:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 Tato implementace obsahuje běžnou chybou vypnuto po druhém. Naštěstí kódu Autor zahrnuté anotace SAL velikost vyrovnávací paměti – nástroj pro analýzu kódu může zachytávat chyby díky analýze tuto funkci samostatně.  
  
### <a name="sal-basics"></a>Základy SAL  
 Poznámky SAL definuje čtyři základní typy parametrů, které jsou rozděleny do kategorií pomocí využití vzoru.  
  
|Kategorie|Parametr poznámky|Popis|  
|--------------|--------------------------|-----------------|  
|**Vstup pro MS DTC volal funkci**|`_In_`|Data je předán do volané funkce a je zpracováván jako jen pro čtení.|  
|**Vstup pro MS DTC volal funkci a výstup do volajícího**|`_Inout_`|Využitelná data je předán do funkce a potenciálně se mění.|  
|**Výstup do volajícího**|`_Out_`|Volající pouze místo pro zápis do volané funkce. Volaná funkce zapíše data do tohoto místa.|  
|**Výstup z ukazatele na volající**|`_Outptr_`|Stejně jako **výstup volajícímu**. Hodnota, která je vrácena volanou funkcí je ukazatel.|  
  
 Tyto čtyři základní anotace více jako explicitní jde nastavit různými způsoby. Ve výchozím nastavení, parametry s poznámkami ukazatele se předpokládá, že bude vyžadovat –, musí mít hodnotu NULL pro funkci proběhla úspěšně. Nejčastěji používané varianta basic poznámky označuje, že ukazatel parametr je nepovinný, pokud je hodnota NULL, funkce může být přesto úspěšné dělat svou práci.  
  
 Tato tabulka ukazuje, jak rozlišovat mezi povinných a volitelných parametrů:  
  
||Jsou vyžadovány parametry|Parametry jsou volitelné|  
|-|-----------------------------|-----------------------------|  
|**Vstup pro MS DTC volal funkci**|`_In_`|`_In_opt_`|  
|**Vstup pro MS DTC volal funkci a výstup do volajícího**|`_Inout_`|`_Inout_opt_`|  
|**Výstup do volajícího**|`_Out_`|`_Out_opt_`|  
|**Výstup z ukazatele na volající**|`_Outptr_`|`_Outptr_opt_`|  
  
 Tyto poznámky identifikovat možné Neinicializovaný hodnoty a formální a přesné způsobem používá neplatný ukazatel s hodnotou null. Předání hodnotou NULL pro požadovaný parametr může způsobit selhání nebo to může způsobit "selhání" Chyba kódu má být vrácen. V obou případech funkce nemůže být úspěšná při provádění svých úloh.  
  
## <a name="sal-examples"></a>Příklady SAL  
 Tato část ukazuje příklady kódu pro základní poznámky SAL.  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Najít chyby pomocí nástroje analýzy kódu sady Visual Studio  
 V příkladech se používá nástroj analýzy kódu sady Visual Studio společně s anotací SAL k vyhledání vad kódu. Tady je postup, který.  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Použití nástrojů pro analýzu kódu sady Visual Studio a SAL  
  
1. V sadě Visual Studio otevřete projekt C++ obsahující poznámky SAL.  
  
2. V panelu nabídky zvolte **sestavení**, **spustit analýzu kódu na řešení**.  
  
    Vezměte v úvahu \_v\_ příklad v této části. Je-li spustit analýzu kódu na ni, toto upozornění se zobrazí:  
  
   > **C6387 Neplatná hodnota parametru**   
   > 'pinta' může být '0': to nedrží se specifikací pro funkci "InCallee".  
  
### <a name="example-the-in-annotation"></a>Příklad: \_v\_ poznámky  
 `_In_` Anotace označuje, že:  
  
-   Parametr musí být platná a se nezmění.  
  
-   Funkce přečte pouze z vyrovnávací paměti jedním prvkem.  
  
-   Volající musí poskytnout vyrovnávací paměti a inicializujte ji.  
  
-   `_In_` Určuje "jen pro čtení". Běžná chyba spočívá v použití `_In_` pro parametr, který by měl mít `_Inout_` anotace místo.  
  
-   `_In_` je povoleno, ale ignoruje Analyzer na typech bez ukazatele skaláry.  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 Pokud používáte analýzy kódu sady Visual Studio v tomto příkladu, ověří, že volající předat inicializované vyrovnávací paměti pro nenulový ukazatel `pInt`. V takovém případě `pInt` ukazatele nesmí mít hodnotu NULL.  
  
### <a name="example-the-inopt-annotation"></a>Příklad: \_In_opt\_ poznámky  
 `_In_opt_` je stejný jako `_In_`, s tím rozdílem, že vstupní parametr může mít hodnotu NULL, a proto se funkce by měla vyhledávat to.  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Analýzy kódu sady Visual Studio ověří, že funkce zjišťuje NULL dříve, než přistupuje k vyrovnávací paměti.  
  
### <a name="example-the-out-annotation"></a>Příklad: \_si\_ poznámky  
 `_Out_` podporuje běžný scénář, ve kterém je předáno NENULOVÝ ukazatel, který odkazuje na vyrovnávací paměť elementu a funkce inicializuje přidělenou elementu. Volající nemá inicializace vyrovnávací paměti před voláním; Volaná funkce, že inicializovat ji ještě před jeho vrácením.  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 Visual Studio nástroj pro analýzu kódu ověřuje, že volající předá NENULOVÝ ukazatel do vyrovnávací paměti pro `pInt` a že vyrovnávací paměť je inicializován pomocí funkce ještě před jeho vrácením.  
  
### <a name="example-the-outopt-annotation"></a>Příklad: \_Out_opt\_ poznámky  
 `_Out_opt_` je stejný jako `_Out_`, s tím rozdílem, že tento parametr může mít hodnotu NULL, a proto se funkce by měla vyhledávat to.  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Analýzy kódu sady Visual Studio ověří, že tato funkce zkontroluje NULL před `pInt` se přistoupit přes ukazatel a pokud `pInt` nemá hodnotu NULL, že vyrovnávací paměť je inicializován pomocí funkce ještě před jeho vrácením.  
  
### <a name="example-the-inout-annotation"></a>Příklad: \_vstup\_ poznámky  
 `_Inout_` je používaná k anotaci ukazatel parametrem, který může změnit funkci. Ukazatel musí odkazovat na platný inicializovaná data před voláním, a i v případě, že se změní, musí mít platnou hodnotu stále při návratu. Poznámka Určuje, že funkce mohou volně číst a zapisovat do vyrovnávací paměti na jeden element. Volající musí poskytnout vyrovnávací paměti a inicializujte ji.  
  
> [!NOTE]
>  Stejně jako `_Out_`, `_Inout_` musí vyrovnat upravitelné hodnoty.  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // ‘pInt’ should not be NULL  
}  
  
```  
  
 Analýzy kódu sady Visual Studio ověří, že volající předat inicializované vyrovnávací paměti pro NENULOVÝ ukazatel `pInt`a zda před vrácení, `pInt` stále nemá hodnotu NULL a vyrovnávací paměť je inicializován.  
  
### <a name="example-the-inoutopt-annotation"></a>Příklad: \_Inout_opt\_ poznámky  
 `_Inout_opt_` je stejný jako `_Inout_`, s tím rozdílem, že vstupní parametr může mít hodnotu NULL, a proto se funkce by měla vyhledávat to.  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Analýzy kódu sady Visual Studio ověří, že tato funkce zkontroluje NULL před přístupem ke vyrovnávací paměť a pokud `pInt` nemá hodnotu NULL, že vyrovnávací paměť je inicializován pomocí funkce ještě před jeho vrácením.  
  
### <a name="example-the-outptr-annotation"></a>Příklad: \_Outptr\_ poznámky  
 `_Outptr_` slouží k přidání poznámek ke parametr, který se má vrátit ukazatel.  Parametr samotný nemůže být NULL a volané funkce vrací jinou hodnotu než NULL ukazatel v něm a tento ukazatel odkazuje na inicializovaná data.  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 Analýzy kódu sady Visual Studio ověří, že volající předá bez NULOVÉHO ukazatele `*pInt`, a že vyrovnávací paměť je inicializován pomocí funkce ještě před jeho vrácením.  
  
### <a name="example-the-outptropt-annotation"></a>Příklad: \_Outptr_opt\_ poznámky  
 `_Outptr_opt_` je stejný jako `_Outptr_`, s tím rozdílem, že se jedná o volitelný parametr – volající může předat ukazatel s hodnotou NULL pro parametr.  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Analýzy kódu sady Visual Studio ověří, že tato funkce zkontroluje NULL před `*pInt` se přistoupit přes ukazatel, a že vyrovnávací paměť je inicializován pomocí funkce ještě před jeho vrácením.  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>Příklad: \_úspěch\_ poznámky v kombinaci s \_navýšení kapacity\_  
 Poznámky můžete použít pro většinu objektů.  Zejména může opatřit poznámkami celé funkce.  Jednou z vlastnosti Nejobvyklejšími funkce je, že ho úspěch nebo neúspěch. Ale stejně jako přidružení mezi vyrovnávací paměť a velikost, nelze C/C++ express funkce úspěch nebo neúspěch. S použitím `_Success_` poznámky, můžete napsat, jaké úspěch pro funkci bude vypadat takto.  Parametr `_Success_` poznámky je právě výraz, že pokud je hodnota true označuje, že funkce byla úspěšná. Výraz může být cokoli, co dokáže zpracovat analyzátor poznámky. Účinky poznámky po vrácení funkce se vztahují jenom když funkce úspěšná. Tento příklad ukazuje, jak `_Success_` komunikuje s `_Out_` udělat správné věci. Můžete použít klíčové slovo `return` představující vrácenou hodnotu.  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 `_Out_` Anotace způsobí, že Visual Studio Code Analysis k ověření, že volající předá NENULOVÝ ukazatel do vyrovnávací paměti pro `pInt`, a že vyrovnávací paměť je inicializován pomocí funkce ještě před jeho vrácením.  
  
## <a name="sal-best-practice"></a>Osvědčeným postupem SAL  
  
### <a name="adding-annotations-to-existing-code"></a>Přidání poznámky do existujícího kódu  
 Poznámky SAL je výkonné technologie, která vám může pomoct vylepšit zabezpečení a spolehlivost vašeho kódu. Poté, co zjistíte SAL, můžete použít nové dovednosti pro každodenní práci. V novém kódu můžete na základě SAL specifikace záměrné v celém; ve starším kódu můžete přidat poznámky postupně a tím zvýšit výhody při každé aktualizaci.  
  
 Již je anotována Microsoft veřejné záhlaví. Doporučujeme proto, že ve vašich projektech můžete nejprve opatřit poznámkami listový uzel funkce a funkce, které volají rozhraní API systému Win32 k využívat výhod.  
  
### <a name="when-do-i-annotate"></a>Když poznámky?  
 Tady jsou některé pokyny:  
  
- Označí všechny parametry ukazatele.  
  
- Přidání poznámek ke poznámky rozsah hodnot, tak, aby analýza kódu můžete zajistit bezpečnost vyrovnávací paměti a ukazatele.  
  
- Přidat poznámku zamykání pravidla a zamykání vedlejší účinky. Další informace najdete v tématu [zadávání poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md).  
  
- Přidat poznámku vlastnosti ovladače a další vlastnosti specifické pro doménu.  
  
  Nebo můžete opatřit poznámkami všechny parametry, aby vaše záměru vymazat v průběhu a usnadňují zkontrolujte, že jsme udělali poznámky.  
  
## <a name="related-resources"></a>Související prostředky  
 [Blog týmu analýzy kódu](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>Viz také  
 [Použití poznámek SAL k omezení defektů kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)   
 [Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)   
 [Zadávání poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md)   
 [Určení, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)



