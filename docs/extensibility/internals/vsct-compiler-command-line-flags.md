---
title: Příznaky Command-Line kompilátoru VSCT | Microsoft Docs
description: Kompilátor příkazového řádku sady Visual Studio poskytuje možnosti příkazového řádku pro zajištění úspěšné kompilace souborů. vsct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ce83df56e1bcfad50fe71da31291b5c43b26c47a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898887"
---
# <a name="vsct-compiler-command-line-flags"></a>Příznaky příkazového řádku pro kompilátor VSCT
Kompilátor sady příkazů sady Visual Studio (VSCT) poskytuje přepínače příkazového řádku, které zajistí úspěšnou kompilaci souborů. vsct.

## <a name="command-line-parameters"></a>Parametry příkazového řádku
 Pokud chcete zobrazit základní VSCTou podporu z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **příkazového** okna, přejděte do složky pro *instalaci sady Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ a zadejte:

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
> Znaky – (pomlčka) a/(lomítko) jsou oba přijímány zápisem pro označení parametrů příkazového řádku.

 Přijatelné příznaky a význam jsou následující.

|Přepínač|Description|
|------------|-----------------|
|– D|Zadejte jakékoli další definované symboly.|
|– I|Určete další zahrnuté cesty, které se mají použít při překladu odkazů na soubory.|
|– L|Zadejte <xref:System.Globalization.CultureInfo> název jazykové verze, například "en-US".|
|-E|Vygeneruje objekty C# v určeném oboru názvů pro položky příkazu, za kterými následuje [C&#124;H&#124;N]:*filename*, kde C = C#, H = záhlaví C++, N = obor názvů. Obor názvů je vyžadován pro jazyk C#.|
|-v|Podrobný výstup.|

 Přepínač-L instruuje kompilátor, aby vybral skupinu řetězců k vytvoření binárního souboru. technický ředitel, který odpovídá danému <xref:System.Globalization.CultureInfo> názvu jazykové verze. Zadaný název jazykové verze by měl odpovídat atributu jazyka jednoho nebo více [elementů řetězce](../../extensibility/strings-element.md) v souboru. vsct. Pokud element řetězce nemá atribut Language, je zděděn z prvku obsahujícího [příkazového](../../extensibility/commandtable-element.md)pole.

 Soubor. vsct může mít více elementů řetězce a každá z nich může mít jiný atribut Language. Globalizaci je dosaženo spuštěním kompilátoru VSCT několikrát a změnou přepínače-L pro každý název jazykové verze.

 Pokud název jazykové verze zadaný přepínačem-L neodpovídá atributu jazyka žádného elementu řetězce, kompilátor se pokusí porovnat s jazykem a nikoli oblastí. Pokud se například nenajde "en-US", kompilátor místo toho zkusí "en". V takovém případě se pokusí o aktuální jazykovou verzi operačního systému. V takovém případě se zkompiluje první nalezený prvek řetězce.

 Přepínač-E lze použít k vygenerování hlavičkového souboru ve stylu jazyka C, který obsahuje symboly, které jsou používány tabulkou příkazu, nebo k vygenerování souboru jazyka C#, který obsahuje objekty pro příkazy příkazů.

 Přepínače-D a-I obsahují syntaxi příznaků preprocesoru Cl.exe C, které mají stejný název. -D definice, které mají formát X = Y, se používají pro rozšíření testů založených na XML \<Defined> v `Condition` atributech. -I se používají cesty k překladu \<Include> \<Extern> a odkazy na \<Bitmap> soubory. Další informace najdete v referenčních informacích ke [schématu XML vsct](../../extensibility/vsct-xml-schema-reference.md).

 Kompilátor VSCT může také dekompilovat dříve sestavený binární soubor. Uděláte to tak, že zadáte binární soubor pro \<infile> .   Pokud byl binární soubor vytvořen kompilátorem VSCT, bude mít již vložené symboly a vytvoří výstup se symbolickými názvy v \<Symbols> části výstupu. Pokud byl binární soubor vytvořen kompilátorem CTC, výstup bude obsahovat skutečné identifikátory GUID a ID. Pokud je soubor *. ctsym, který je vytvořen pomocí aktuální verze Ctc.exe, ve stejné složce jako binární vstupní soubor, symboly budou načteny z tohoto souboru a použity pro výstup.

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [XML schéma VSCT – referenční informace](../../extensibility/vsct-xml-schema-reference.md)
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
