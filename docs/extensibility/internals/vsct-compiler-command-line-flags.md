---
title: Příznaky příkazového řádku kompilátoru VSCT | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4ee29710049453c3163c366eccf96e257b6028d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703960"
---
# <a name="vsct-compiler-command-line-flags"></a>Příznaky příkazového řádku pro kompilátor VSCT
Kompilátor Visual Studio Command Table (VSCT) poskytuje přepínače příkazového řádku, které zajišťují úspěšnou kompilaci souborů .vsct.

## <a name="command-line-parameters"></a>Parametry příkazového řádku
 Chcete-li zobrazit základní nápovědu v sadě VSCT z okna [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **příkazu,** přejděte na *instalační cestu sady Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ a zadejte:

```
vsct /?
```

 Příkaz vrací:

```
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000

Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]

  -D    Specify any additional preprocessor defines
  -I    Indicate what additional include paths to send to the preprocessor
  -L    Specify the language to use when selecting strings
  -E    Emit C# objects in the specified namespace for command items,
        followed by [L|F|H|N]:<value>
        F = Name of the file to emit (used if -EL is provided)
        L = Name of a language providing a CodeDOM provider
        N = namespace (required if -EL is provided)
        H = C++ header
  -c    Clean build skipping dependency checks
  -v    Verbose output
```

> [!NOTE]
> Znaky - (pomlčka) a / (lomítko) jsou přijímány pro označení parametrů příkazového řádku.

 Přijatelné vlajky a to, co znamenají, jsou následující.

|Přepínač|Popis|
|------------|-----------------|
|-D|Zadejte všechny další definované symboly.|
|-I|Označte další cesty zahrnutí, které by měly být použity při řešení odkazů na soubory.|
|-L|Zadejte <xref:System.Globalization.CultureInfo> název jazykové verze, například "en-US".|
|-E|Vyzařujte objekty Jazyka C# v zadaném oboru názvů pro položky příkazů následovaný [C&#124;H&#124;N]:*název souboru,* kde C = C#, H = hlavička C++, N = obor názvů. Obor názvů je vyžadován pro c#.|
|-v|Podrobný výstup.|

 Přepínač -L instruuje kompilátor, aby vybral skupinu řetězců k vytvoření binárního <xref:System.Globalization.CultureInfo> souboru .cto, který odpovídá danému názvu jazykové verze. Zadaný název jazykové verze by měl odpovídat atributu Language jednoho nebo více [elementů Strings](../../extensibility/strings-element.md) v souboru .vsct. Pokud Strings element nemá žádný atribut Language, je zděděn z obsahující [CommandTable Element](../../extensibility/commandtable-element.md).

 Soubor .vsct může mít více strings prvky a každý může mít jiný atribut Language. Globalizace je dosaženo spuštěním kompilátoru VSCT vícekrát a změnou přepínače -L pro každý název jazykové verze.

 Pokud název jazykové verze daný přepínačem -L neodpovídá atributu Language žádného prvku Strings, kompilátor se pokusí porovnat jazyk a nikoli oblast. Například pokud "en US" nelze nalézt, kompilátor zkusí "en" místo. V opačném případě se pokusí aktuální jazykovou verzi operačního systému. V opačném případě zkompiluje první řetězec prvek, který najde.

 Přepínač -E lze použít k vyzařování souboru záhlaví ve stylu C, který obsahuje symboly, které jsou používány v tabulce příkazů, nebo k vyzařování souboru Jazyka C#, který obsahuje objekty pro symboly příkazů.

 Přepínače -D a -I mají syntaxi příznaků preprocesoru Cl.exe C, které mají stejný název. -D definice, které mají formát X = Y se \<používají pro `Condition` rozšíření XML-založené definované> testy v atributech. -I zahrnout cesty se \<používají k \<řešení Zahrnout \<>, Extern> a Bitmap> soubor odkazy. Další informace naleznete v [odkazu na schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md).

 Kompilátor VSCT může také dekompilovat dříve sestavený binární soubor. Chcete-li to provést, zadejte binární soubor pro \<soubor>.   Pokud binární soubor byl vytvořen kompilátorem VSCT, bude mít své symboly již vložené a bude vyrábět výstup se symbolickými názvy v \<části Symboly> výstupu. Pokud byl binární soubor vytvořen kompilátorem CTC, bude výstup obsahovat skutečné identifikátory GUID a ID. Pokud je soubor *.ctsym, který je vytvořen aktuálními verzemi programu Ctc.exe, ve stejné složce jako binární vstupní soubor, budou symboly načteny z tohoto souboru a použity pro výstup.

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [XML schéma VSCT – referenční informace](../../extensibility/vsct-xml-schema-reference.md)
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
