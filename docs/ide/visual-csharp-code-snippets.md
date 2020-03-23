---
title: Fragmenty kódu Jazyka C#
ms.date: 06/05/2017
ms.topic: reference
helpviewer_keywords:
- snippets [C#]
- code snippets [C#]
- Code Snippet Inserter [C#]
- C#, code snippets
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d41907a15b7e0b1692dda3f4d678c2b843dfcd03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594159"
---
# <a name="c-code-snippets"></a>Fragmenty kódu Jazyka C#

Fragmenty kódu jsou hotové úryvky kódu, které můžete rychle vložit do kódu. Například fragment `for` kódu vytvoří prázdnou `for` smyčku. Některé fragmenty kódu jsou prostorové s fragmenty kódu, které umožňují vybrat řádky kódu a pak zvolit fragment kódu, který zahrnuje vybrané řádky kódu. Pokud například vyberete řádky kódu a `for` potom aktivujete fragment kódu, vytvoří `for` se smyčka s těmito řádky kódu uvnitř bloku smyčky. Fragmenty kódu mohou usnadnit, usnadnit a spolehlivěji psát programový kód.

Výstřižek kódu můžete vložit do umístění kurzoru nebo vložit fragment kódu surround-with kolem aktuálně vybraného kódu. +Vložení fragmentu kódu je vyvoláno příkazy Vložit fragment kódu nebo **Obklopit** **pomocí** v nabídce **IntelliSense** nebo pomocí klávesových zkratek **Ctrl****K**,**X** nebo **Ctrl**+**K**,**S.**

**Vložení fragmentu kódu** zobrazí název fragmentu kódu pro všechny dostupné fragmenty kódu. Vložení fragmentu kódu obsahuje také vstupní dialogové okno, ve kterém můžete zadat název fragmentu kódu nebo část názvu fragmentu kódu. Vložení fragmentu kódu zvýrazní nejbližší shodu s názvem fragmentu kódu. Stisknutím **klávesy Tab** kdykoli zavřete vloženík fragmentu kódu a vložte aktuálně vybraný fragment kódu. Stisknutím **klávesy Esc** nebo kliknutím myši v editoru kódu se zavře vložení fragmentu kódu bez vložení fragmentu kódu.

## <a name="default-code-snippets"></a>Výchozí fragmenty kódu

Ve výchozím nastavení jsou následující fragmenty kódu zahrnuty v sadě Visual Studio pro c#.

|Jméno (nebo zástupce)|Popis|Platná umístění pro vložení fragmentu|
| - |-----------------| - |
|#if – direktiva|Vytvoří [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) směrnice a [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif) směrnice.|Kdekoli.|
|#region – direktiva|Vytvoří [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) směrnice a [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) směrnice.|Kdekoli.|
|~|Vytvoří [finalizační metodu](/dotnet/csharp/programming-guide/classes-and-structs/destructors) (destruktor) pro obsahující třídu.|Uvnitř třídy.|
|– atribut|Vytvoří deklaraci pro třídu, <xref:System.Attribute>která je odvozena od .|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|checked|Vytvoří [zaškrtnutý](/dotnet/csharp/language-reference/keywords/checked) blok.|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|třída|Vytvoří deklaraci třídy.|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|ctor|Vytvoří konstruktor pro obsahující třídy.|Uvnitř třídy.|
|Cw|Vytvoří volání <xref:System.Console.WriteLine%2A>.|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|do|Vytvoří [do](/dotnet/csharp/language-reference/keywords/do) `while` smyčky.|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|else|Vytvoří blok [else.](/dotnet/csharp/language-reference/keywords/if-else)|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|enum|Vytvoří [deklaraci výčtu.](/dotnet/csharp/language-reference/keywords/enum)|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|equals|Vytvoří deklaraci metody, <xref:System.Object.Equals%2A> která přepíše <xref:System.Object> metodu definovanou ve třídě.|Uvnitř třídy nebo struktury.|
|Výjimka|Vytvoří deklaraci pro třídu, která<xref:System.Exception> je odvozena z výjimky (ve výchozím nastavení).|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|pro|Vytvoří [for](/dotnet/csharp/language-reference/keywords/for) smyčky.|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|foreach|Vytvoří [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) smyčky.|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|forr|Vytvoří [for](/dotnet/csharp/language-reference/keywords/for) smyčky, která sníží proměnnou smyčky po každé iteraci.|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|if|Vytvoří [blok if.](/dotnet/csharp/language-reference/keywords/if-else)|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|Indexer|Vytvoří deklaraci indexeru.|Uvnitř třídy nebo struktury.|
|rozhraní|Vytvoří deklaraci [rozhraní.](/dotnet/csharp/language-reference/keywords/interface)|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|Vyvolat|Vytvoří blok, který bezpečně vyvolá událost.|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|iterátor|Vytvoří iterátor.|Uvnitř třídy nebo struktury.|
|iterindex|Vytvoří "pojmenovaný" iterátor a indexer dvojice pomocí vnořené třídy.|Uvnitř třídy nebo struktury.|
|lock|Vytvoří [blok zámku.](/dotnet/csharp/language-reference/keywords/lock-statement)|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|Mbox|Vytvoří volání <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Je možné, že bude pravděpodobně třeba přidat odkaz na *soubor System.Windows.Forms.dll*.|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|Obor názvů|Vytvoří [deklaraci oboru názvů.](/dotnet/csharp/language-reference/keywords/namespace)|Uvnitř oboru názvů (včetně globálního oboru názvů).|
|Prop|Vytvoří [deklaraci automaticky implementované vlastnosti.](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties)|Uvnitř třídy nebo struktury.|
|propfull|Vytvoří deklaraci `get` vlastnosti s a `set` přistupující mi.|Uvnitř třídy nebo struktury.|
|propg|Vytvoří [automaticky implementovanou vlastnost](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) jen `set` pro čtení s privátním přistupujícím objektem.|Uvnitř třídy nebo struktury.|
|Sim|Vytvoří [statickou](/dotnet/csharp/language-reference/keywords/static) deklaraci metody [Int](/dotnet/csharp/language-reference/keywords/int) Main.|Uvnitř třídy nebo struktury.|
|struct |Vytvoří [deklaraci struktury.](/dotnet/csharp/language-reference/keywords/struct)|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|Svm|Vytvoří [statickou](/dotnet/csharp/language-reference/keywords/static) [deklaraci Metody Main void.](/dotnet/csharp/language-reference/keywords/void)|Uvnitř třídy nebo struktury.|
|switch|Vytvoří [blok přepínače.](/dotnet/csharp/language-reference/keywords/switch)|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|vyzkoušení|Vytvoří blok [try-catch.](/dotnet/csharp/language-reference/keywords/try-catch)|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|tryf|Vytvoří [try-finally](/dotnet/csharp/language-reference/keywords/try-finally) bloku.|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|unchecked|Vytvoří [nezaškrtnutý](/dotnet/csharp/language-reference/keywords/unchecked) blok.|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|unsafe|Vytvoří [nebezpečný](/dotnet/csharp/language-reference/keywords/unsafe) blok.|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|
|using|Vytvoří [using](/dotnet/csharp/language-reference/keywords/using-directive) směrnice.|Uvnitř oboru názvů (včetně globálního oboru názvů).|
|while|Vytvoří [smyčku while.](/dotnet/csharp/language-reference/keywords/while)|Uvnitř metody indexer, přístupový objekt vlastnosti nebo přistupující objekt události.|

## <a name="see-also"></a>Viz také

- [Funkce fragmentu kódu](../ide/code-snippet-functions.md)
- [Fragmenty kódu](../ide/code-snippets.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Postup: Použití úryvků kódu s prostorovým snímkem](../ide/how-to-use-surround-with-code-snippets.md)
