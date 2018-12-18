---
title: C#fragmenty kódu
ms.date: 06/05/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- snippets [C#]
- code snippets [C#]
- Code Snippet Inserter [C#]
- C#, code snippets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: feec485f752ac13b43310e4afd97bdfaac93ee51
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849161"
---
# <a name="c-code-snippets"></a>C#fragmenty kódu

Fragmenty kódu jsou předdefinované fragmenty kódu, které můžete rychle vkládat do kódu. Například `for` fragment kódu vytvoří prázdnou `for` smyčky. Některé fragmenty kódu jsou příkazu Obklopit s fragmenty kódu, které vám umožní vybrat řádky kódu a klikněte na tlačítko fragment kódu, která zahrnuje vybrané řádky kódu. Například, když vyberete řádků kódu a poté aktivovat `for` fragment kódu vytvoří `for` smyčky s tyto řádky kódu uvnitř smyčka bloku. Fragmenty kódu můžete provést program psaní kódu rychlejší, jednodušší a spolehlivější.

 Můžete vložit fragment kódu do umístění kurzoru nebo vložit obklopit fragmentem kódu kolem vybrané kódu. Vkládací modul fragmentu kódu je vyvolána prostřednictvím **Vložit fragment kódu** nebo **obklopit fragmentem** příkazy na **IntelliSense** nabídce nebo pomocí klávesové zkratky  **CTRL**+**K**,**X** nebo **Ctrl**+**K**,**S** v uvedeném pořadí.

 **Vkládací modul fragmentu kódu** zobrazí název fragment kódu pro všechny fragmenty kódu k dispozici. Vkládací modul fragmentu kódu také zahrnuje vstupní dialogové okno s typem název fragmentu kódu nebo část názvu fragmentu kódu. Vkládací modul fragmentu kódu zvýrazní nejvíce odpovídá názvu fragmentu kódu. Stisknutím klávesy **kartu** kdykoli zrušit Vkládací modul fragmentu kódu, který se aktuálně vybraný fragment kódu vložit. Stisknutím klávesy **Esc** nebo klepnutím na tlačítko myši v editoru kódu se zavřít Vkládací modul fragmentu kódu bez vložení fragmentu kódu.

## <a name="default-code-snippets"></a>Výchozí fragmenty kódu

Ve výchozím nastavení jsou zahrnuty následující fragmenty kódu v sadě Visual Studio pro C#.

|Název (nebo místní)|Popis|Platná umístění pro vložení fragmentu kódu|
| - |-----------------| - |
|#if – direktiva|Vytvoří [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) směrnice a [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif) směrnice.|Kdekoli.|
|#region – direktiva|Vytvoří [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) směrnice a [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) směrnice.|Kdekoli.|
|~|Vytvoří [finalizační metodu](/dotnet/csharp/programming-guide/classes-and-structs/destructors) (destruktor) pro třídu obsahující.|Uvnitř třídy.|
|– atribut|Vytvoří deklaraci pro třídu, která je odvozena z <xref:System.Attribute>.|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|checked|Vytvoří [zaškrtnutí](/dotnet/csharp/language-reference/keywords/checked) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|třída|Vytvoří deklaraci třídy.|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|konstruktoru|Vytvoří konstruktor pro třídu obsahující.|Uvnitř třídy.|
|SH|Vytvoření volání <xref:System.Console.WriteLine%2A>.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|do|Vytvoří [proveďte](/dotnet/csharp/language-reference/keywords/do) `while` smyčky.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|else|Vytvoří [else](/dotnet/csharp/language-reference/keywords/if-else) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|enum|Vytvoří [výčtu](/dotnet/csharp/language-reference/keywords/enum) deklarace.|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|equals|Vytvoří deklarace metody, která přepíše <xref:System.Object.Equals%2A> metody definované v <xref:System.Object> třídy.|Uvnitř třídy nebo struktury.|
|Výjimka|Vytvoří deklaraci pro třídu, která je odvozena z výjimky (<xref:System.Exception> ve výchozím nastavení).|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|pro|Vytvoří [pro](/dotnet/csharp/language-reference/keywords/for) smyčky.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|foreach|Vytvoří [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) smyčky.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|Díky|Vytvoří [pro](/dotnet/csharp/language-reference/keywords/for) smyčky této dekrementuje proměnnou smyčky po každé iteraci.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|if|Vytvoří [Pokud](/dotnet/csharp/language-reference/keywords/if-else) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|Indexer|Vytvoří deklaraci indexeru.|Uvnitř třídy nebo struktury.|
|rozhraní|Vytvoří [rozhraní](/dotnet/csharp/language-reference/keywords/interface) deklarace.|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|vyvolání|Vytvoří blok, který bezpečně vyvolá událost.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|iterátor|Vytvoří iterátor.|Uvnitř třídy nebo struktury.|
|iterindex|Vytvoří "s názvem" páru iterátoru a indexer používající vnořenou třídu.|Uvnitř třídy nebo struktury.|
|lock|Vytvoří [Zámek](/dotnet/csharp/language-reference/keywords/lock-statement) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|mbox|Vytvoření volání <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Možná budete muset přidat odkaz na *System.Windows.Forms.dll*.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|– obor názvů|Vytvoří [obor názvů](/dotnet/csharp/language-reference/keywords/namespace) deklarace.|V oboru názvů (včetně globálního oboru názvů).|
|Prop|Vytvoří [automaticky implementované vlastnosti](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) deklarace.|Uvnitř třídy nebo struktury.|
|propfull|Deklarace vlastnosti se vytvoří `get` a `set` přistupující objekty.|Uvnitř třídy nebo struktury.|
|propg|Vytvoří jen pro čtení [automaticky implementované vlastnosti](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) s privátní `set` přistupujícího objektu.|Uvnitř třídy nebo struktury.|
|Správce bitových kopií|Vytvoří [statické](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int) deklarace metody Main.|Uvnitř třídy nebo struktury.|
|struct |Vytvoří [struktura](/dotnet/csharp/language-reference/keywords/struct) deklarace.|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|svm|Vytvoří [statické](/dotnet/csharp/language-reference/keywords/static) [void](/dotnet/csharp/language-reference/keywords/void) deklarace metody Main.|Uvnitř třídy nebo struktury.|
|– přepínač|Vytvoří [přepnout](/dotnet/csharp/language-reference/keywords/switch) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|Zkuste|Vytvoří [bloku try-catch](/dotnet/csharp/language-reference/keywords/try-catch) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|tryf|Vytvoří [try-finally](/dotnet/csharp/language-reference/keywords/try-finally) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|unchecked|Vytvoří [Nekontrolovaná](/dotnet/csharp/language-reference/keywords/unchecked) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|unsafe|Vytvoří [nebezpečné](/dotnet/csharp/language-reference/keywords/unsafe) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|
|používání|Vytvoří [pomocí](/dotnet/csharp/language-reference/keywords/using-directive) směrnice.|V oboru názvů (včetně globálního oboru názvů).|
|while|Vytvoří [při](/dotnet/csharp/language-reference/keywords/while) smyčky.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|

## <a name="see-also"></a>Viz také:

- [Funkce fragmentu kódu](../ide/code-snippet-functions.md)
- [Fragmenty kódu](../ide/code-snippets.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Postupy: použití příkazu Obklopit s fragmenty kódu](../ide/how-to-use-surround-with-code-snippets.md)