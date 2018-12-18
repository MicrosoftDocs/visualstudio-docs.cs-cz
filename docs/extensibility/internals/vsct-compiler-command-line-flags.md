---
title: Příznaky příkazového řádku pro kompilátor VSCT | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0cdf74d0c6c77a2c7c22829c8aaa3e238e65703a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744878"
---
# <a name="vsct-compiler-command-line-flags"></a>Příznaky příkazového řádku pro kompilátor VSCT
Kompilátor Visual Studio příkaz tabulky (VSCT) poskytuje přepínače příkazového řádku k zajištění úspěšné kompilaci souborů .vsct.  
  
## <a name="command-line-parameters"></a>Parametry příkazového řádku  
 Chcete-li zobrazit základní VSCT pomoc od [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **příkaz** okno, přejděte na *cestu instalace sady Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ složky a typ:  
  
```  
vsct /?  
```  
  
 Vrátí:  
  
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
>  Znaky - (pomlčka) a / (lomítko) jsou obě přijaté zápis pro ukazování parametry příkazového řádku.  
  
 Přijatelné příznaků a jejich význam jsou.  
  
|Přepínač|Popis|  
|------------|-----------------|  
|-D|Zadejte libovolné další definované symboly.|  
|-I|Značí, že další cesty, které má být použit při řešení odkazů na soubory zahrnutí.|  
|-L|Zadejte <xref:System.Globalization.CultureInfo> název jazykové verze, například "en US".|  
|-E|Generování C# objektů v určeném oboru názvů pro příkaz položky, za nímž následuje [C&#124;H&#124;N]:*filename*kde C = C#, H = hlaviček jazyka C++, N = oboru názvů. Obor názvů se vyžaduje pro jazyk C#.|  
|-v|Podrobný výstup.|  
  
 Přepínač -L instruuje kompilátor, aby vyberte skupinu pro řetězce pro vytvoření .cto binární soubor, který odpovídá daný <xref:System.Globalization.CultureInfo> název jazykové verze. Název zadaná jazyková verze by měl odpovídat atribut Language jednoho nebo víc [Strings – Element](../../extensibility/strings-element.md) v souboru .vsct. Pokud prvek řetězců nemá žádný atribut Language, je zděděno z obsahuje [commandtable – Element](../../extensibility/commandtable-element.md).  
  
 Souboru .vsct může mít více prvků řetězce a každý může mít jiný atribut Language. Globalizace se dosahuje spuštěním kompilátor VSCT více než jednou a změnou přepínač -L pro každý název jazykové verze.  
  
 Pokud daný název jazykové verze přepínačem -L neodpovídá atributu jazyk libovolného elementu řetězce, kompilátor se pokusí jazyk a není v oblasti. Například pokud nelze najít "en US", kompilátor se pokusí "en" místo toho. Pokud se to nepovede zkusí aktuální jazykové verze operačního systému. Pokud se to nepovede zkompiluje prvního prvku řetězce, které nalezne.  
  
 Přepínač -E je možné generovat soubor záhlaví ve stylu jazyka C, který obsahuje symboly, které jsou používány tabulky příkazů nebo ke generování souboru C#, která obsahuje objekty symbolů příkazu.  
  
 -D a - přepínače mají syntaxi Cl.exe C preprocesoru příznaků, které mají stejný název. -D definice, které mají formát X = Y se používají pro rozšiřování založený na formátu XML \<definované > testy v `Condition` atributy. -I cesty zahrnutí slouží k rozpoznání \<zahrnout >, \<Extern > a \<rastrový obrázek > soubor odkazy. Další informace najdete v tématu [VSCT – referenční dokumentace schématu XML](../../extensibility/vsct-xml-schema-reference.md).  
  
 Kompilátor VSCT můžete také dekompilovat dřívější sestavené binární soubor. Chcete-li to provést, zadejte binární soubor pro \<infile >.   Pokud je binární soubor byl vytvořen kompilátor VSCT, bude mít jeho symboly již vložen a bude generovat výstup s symbolické názvy v \<symboly > části výstupu. Pokud je binární soubor se vytvořil parametrem kompilátoru CTC, výstup bude obsahovat skutečné identifikátory GUID a ID. Pokud *.ctsym soubor, který vytvořil aktuální verze Ctc.exe je ve stejné složce jako vstupní binární soubor, symboly načteny z tohoto souboru a použít pro výstup.  
  
## <a name="see-also"></a>Viz také  
 [Tabulky příkazů sady Visual Studio (. Soubory Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referenční dokumentace schématu VSCT XML](../../extensibility/vsct-xml-schema-reference.md)   
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)