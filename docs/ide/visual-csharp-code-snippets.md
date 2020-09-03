---
title: Fragmenty kódu v jazyce C#
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594159"
---
# <a name="c-code-snippets"></a>Fragmenty kódu v jazyce C#

Fragmenty kódu jsou předem připravené fragmenty kódu, které můžete rychle vložit do kódu. Například `for` fragment kódu vytvoří prázdnou `for` smyčku. Některé fragmenty kódu jsou obklopeny – s fragmenty kódu, které umožňují vybrat řádky kódu a pak vybrat fragment kódu, který zahrnuje vybrané řádky kódu. Například když vyberete řádky kódu a pak aktivujete `for` fragment kódu, vytvoří `for` smyčku s těmito řádky kódu uvnitř bloku smyčky. Fragmenty kódu můžou urychlit psaní kódu programu, jednodušší a spolehlivější.

Fragment kódu můžete vložit do umístění kurzoru nebo vložit obklopit s fragmentem kódu kolem aktuálně vybraného kódu. Fragment kódu Inserter je vyvolán prostřednictvím příkazu **Vložit fragment kódu** nebo **obklopit** příkazy v nabídce **IntelliSense** nebo pomocí klávesových zkratek **CTRL** + **K**,**X** nebo **CTRL** + **k**, v**S** tomto pořadí.

**Fragment kódu Inserter** zobrazí název fragmentu kódu pro všechny dostupné fragmenty kódu. Fragment kódu Inserter také obsahuje vstupní dialogové okno, kde můžete zadat název fragmentu kódu nebo část názvu fragmentu kódu. Fragment kódu Inserter zvýrazňuje nejbližší shodu s názvem fragmentu kódu. Stiskem klávesy **TAB** kdykoliv dojde k zavření fragmentu kódu Inserter a vložení aktuálně vybraného fragmentu kódu. Stisknutím klávesy **ESC** nebo kliknutím na myš v editoru kódu zavřete fragment kódu Inserter bez vložení fragmentu kódu.

## <a name="default-code-snippets"></a>Výchozí fragmenty kódu

Ve výchozím nastavení jsou součástí sady Visual Studio pro jazyk C# následující fragmenty kódu.

|Název (nebo zástupce)|Popis|Platná umístění pro vložení fragmentu|
| - |-----------------| - |
|#if – direktiva|Vytvoří direktivu [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) a direktivu [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif) .|Jakékoli.|
|#region – direktiva|Vytvoří direktivu [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) a direktivu [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) .|Jakékoli.|
|~|Vytvoří [finalizační metodu](/dotnet/csharp/programming-guide/classes-and-structs/destructors) (destruktor) pro třídu, která ji obsahuje.|Uvnitř třídy.|
|– atribut|Vytvoří deklaraci pro třídu, která je odvozena z <xref:System.Attribute> .|V oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|checked|Vytvoří [kontrolovaný](/dotnet/csharp/language-reference/keywords/checked) blok.|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|třída|Vytvoří deklaraci třídy.|V oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|ctor|Vytvoří konstruktor pro třídu, která ji obsahuje.|Uvnitř třídy.|
|Skupina|Vytvoří volání <xref:System.Console.WriteLine%2A> .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|do|Vytvoří [do](/dotnet/csharp/language-reference/keywords/do) `while` smyčku do.|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|else|Vytvoří blok [Else](/dotnet/csharp/language-reference/keywords/if-else) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|enum|Vytvoří deklaraci [výčtu](/dotnet/csharp/language-reference/keywords/enum) .|V oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|equals|Vytvoří deklaraci metody, která přepíše <xref:System.Object.Equals%2A> metodu definovanou ve <xref:System.Object> třídě.|Uvnitř třídy nebo struktury.|
|jímka|Vytvoří deklaraci pro třídu, která je odvozena z výjimky ( <xref:System.Exception> ve výchozím nastavení).|V oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|pro|Vytvoří smyčku [for](/dotnet/csharp/language-reference/keywords/for) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|foreach|Vytvoří smyčku [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|forr|Vytvoří smyčku [for](/dotnet/csharp/language-reference/keywords/for) , která po každé iteraci sníží proměnnou smyčky.|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|if|Vytvoří blok [if](/dotnet/csharp/language-reference/keywords/if-else) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|indexer|Vytvoří deklaraci indexeru.|Uvnitř třídy nebo struktury.|
|rozhraní|Vytvoří deklaraci [rozhraní](/dotnet/csharp/language-reference/keywords/interface) .|V oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|Zavolejte|Vytvoří blok, který bezpečně vyvolá událost.|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|iterátor|Vytvoří iterátor.|Uvnitř třídy nebo struktury.|
|iterindex|Vytvoří iterátor "pojmenovaný" a dvojici indexeru pomocí vnořené třídy.|Uvnitř třídy nebo struktury.|
|lock|Vytvoří blok [zámku](/dotnet/csharp/language-reference/keywords/lock-statement) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|mbox|Vytvoří volání <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> . Je možné, že budete muset přidat odkaz na *System.Windows.Forms.dll*.|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|namespace|Vytvoří deklaraci [oboru názvů](/dotnet/csharp/language-reference/keywords/namespace) .|Uvnitř oboru názvů (včetně globálního oboru názvů).|
|Úprava|Vytvoří deklaraci [automaticky implementované vlastnosti](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) .|Uvnitř třídy nebo struktury.|
|propfull|Vytvoří deklaraci vlastnosti s `get` `set` přístupovými objekty a.|Uvnitř třídy nebo struktury.|
|propg|Vytvoří [automaticky implementovanou vlastnost](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) , která je určena jen pro čtení, pomocí privátního `set` přístupového objektu.|Uvnitř třídy nebo struktury.|
|Instalační|Vytvoří [statickou](/dotnet/csharp/language-reference/keywords/static) deklaraci hlavní metody [int](/dotnet/csharp/language-reference/keywords/int) .|Uvnitř třídy nebo struktury.|
|struct|Vytvoří deklaraci [struktury](/dotnet/csharp/language-reference/keywords/struct) .|V oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|svm|Vytvoří [statickou](/dotnet/csharp/language-reference/keywords/static) deklaraci hlavní metody [void](/dotnet/csharp/language-reference/keywords/void) .|Uvnitř třídy nebo struktury.|
|switch|Vytvoří blok [přepínače](/dotnet/csharp/language-reference/keywords/switch) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|vyzkoušení|Vytvoří blok [try-catch](/dotnet/csharp/language-reference/keywords/try-catch) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|tryf|Vytvoří blok [try-finally](/dotnet/csharp/language-reference/keywords/try-finally) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|unchecked|Vytvoří [nekontrolované](/dotnet/csharp/language-reference/keywords/unchecked) bloky.|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|unsafe|Vytvoří [nebezpečný](/dotnet/csharp/language-reference/keywords/unsafe) blok.|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|using|Vytvoří direktivu [using](/dotnet/csharp/language-reference/keywords/using-directive) .|Uvnitř oboru názvů (včetně globálního oboru názvů).|
|while|Vytvoří smyčku [while](/dotnet/csharp/language-reference/keywords/while) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|

## <a name="see-also"></a>Viz také

- [Funkce fragmentu kódu](../ide/code-snippet-functions.md)
- [Fragmenty kódu](../ide/code-snippets.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Postupy: použití příkazu obklopit s fragmenty kódu](../ide/how-to-use-surround-with-code-snippets.md)
