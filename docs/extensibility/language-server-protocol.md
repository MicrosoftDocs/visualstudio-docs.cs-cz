---
title: Přehled protokolu jazykového serveru | Dokumenty společnosti Microsoft
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3bd5dce3cfb7022a8abb6397dc87b418144cbe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703106"
---
# <a name="language-server-protocol"></a>Protokol jazyka serveru

## <a name="what-is-the-language-server-protocol"></a>Co je protokol language server?

Podpora funkce bohaté úpravy, jako je automatické dokončování zdrojového kódu nebo **přejít na definici** pro programovací jazyk v editoru nebo IDE je tradičně velmi náročné a časově náročné. Obvykle vyžaduje psaní modelu domény (skener, analyzátor, kontrola typu, tvůrce a další) v programovacím jazyce editoru nebo IDE. Například eclipse CDT plugin, který poskytuje podporu pro C/C++ v Eclipse IDE je napsán v Jazyce Java, protože Eclipse IDE sám je napsán v Jazyce Java. Podle tohoto přístupu by to znamenalo implementaci modelu domény C/C++ v typescriptu pro kód sady Visual Studio a modelu samostatné domény v jazyce C# pro visual studio.

Vytváření modelů domén specifických pro jazyk je také mnohem jednodušší, pokud vývojový nástroj může znovu použít existující knihovny specifické pro jazyk. Tyto knihovny jsou však obvykle implementovány v samotném programovacím jazyce (například dobré modely domény C/C++ jsou implementovány v jazyce C/C++). Integrace knihovny C/C++ do editoru napsaného v jazyce TypeScript je technicky možná, ale je těžké ji provést.

### <a name="language-servers"></a>Jazykové servery

Dalším přístupem je spuštění knihovny ve vlastním procesu a použití meziprocesové komunikace k rozhovoru s ní. Zprávy odeslané tam a zpět tvoří protokol. Protokol lsp (Language Server) je produktem standardizace zpráv vyměňovaných mezi vývojovým nástrojem a procesem jazykového serveru. Používání jazykových serverů nebo démonů není nová nebo nová myšlenka. Redaktoři jako Vim a Emacs to dělají již nějakou dobu, aby poskytli sémantickou podporu automatického dokončování. Cílem LSP bylo zjednodušit tyto druhy integrací a poskytnout užitečný rámec pro vystavení jazykových funkcí různým nástrojům.

Společný protokol umožňuje integraci funkcí programovacího jazyka do vývojového nástroje s minimálním problémem opětovným použitím existující implementace modelu domény jazyka. Jazyk server back-end by mohl být napsán v PHP, Python, nebo Java a LSP umožňuje snadno integrovat do různých nástrojů. Protokol pracuje na společné úrovni abstrakce, takže nástroj může nabízet bohaté jazykové služby, aniž by bylo nutné plně pochopit nuance specifické pro základní model domény.

## <a name="how-work-on-the-lsp-started"></a>Jak začala práce na lsp

LSP se vyvíjel v průběhu času a dnes je na verzi 3.0. Začalo to, když koncept jazykového serveru byl zachycen omnisharp poskytnout bohaté funkce pro úpravy pro C#. Zpočátku OmniSharp používá protokol HTTP s datovou částí JSON a byl integrován do několika editorů, včetně [visual studio kód](https://code.visualstudio.com).

Přibližně ve stejnou dobu začala společnost Microsoft pracovat na jazykovém serveru TypeScript s myšlenkou podporovat TypeScript v editorech, jako je Emacs a Sublime Text. V této implementaci editor komunikuje prostřednictvím stdin/stdout s procesem serveru TypeScript a používá datovou část JSON inspirovanou protokolem ladicího programu V8 pro požadavky a odpovědi. Server TypeScript byl integrován do modulu plug-in TypeScript Sublime a vs kód pro bohaté úpravy jazyka TypeScript.

Po integraci dvou různých jazykových serverů začal tým VS Code zkoumat protokol společného jazykového serveru pro editory a IDE. Společný protokol umožňuje poskytovateli jazyka vytvořit jeden jazykový server, který může být spotřebován různými ite. Příjemce jazykového serveru má k implementaci klientské straně protokolu pouze jednou. Výsledkem je win-win situace pro poskytovatele jazyka a příjemce jazyka.

Protokol jazykového serveru byl spuštěn protokolem používaným serverem TypeScript a rozšiřoval jej o další jazykové funkce inspirované rozhraním API jazyka VS Code. Protokol je zálohován json-RPC pro vzdálené vyvolání z důvodu jeho jednoduchosti a existující knihovny.

Tým VS Code prototypoval protokol implementací několika jazykových serverů linter, které reagují na požadavky na lint (scan) soubor a vrátí sadu zjištěných varování a chyb. Cílem bylo lint soubor jako uživatel úpravy v dokumentu, což znamená, že bude mnoho linting žádostí během relace editoru. Mělo smysl udržovat server v provozu, aby pro každého uživatele nebylo nutné spustit nový proces lintingu. Bylo implementováno několik linter serverů, včetně rozšíření ESLint a TSLint společnosti VS Code. Tyto dva linter servery jsou implementovány v TypeScript/JavaScript a spustit na Node.js. Sdílejí knihovnu, která implementuje klientskou a serverovou část protokolu.

## <a name="how-the-lsp-works"></a>Jak LSP funguje

Jazykový server běží ve vlastním procesu a nástroje jako Visual Studio nebo VS Code komunikují se serverem pomocí jazykového protokolu přes JSON-RPC. Další výhodou jazykového serveru pracujícího ve vyhrazeném procesu je, že se vyhnete problémům s výkonem souvisejícím s jedním modelem procesu. Skutečný přenosový kanál může být stdio, sokety, pojmenované kanály nebo uzel ipc, pokud klient i server jsou zapsány v Node.js.

Níže je uveden příklad komunikace nástroje a jazykového serveru během rutinní relace úprav:

![lsp diagram udění](media/lsp-flow-diagram.png)

* **Uživatel otevře soubor (označovaný jako dokument) v nástroji**: Nástroj upozorní jazykový server, že dokument je otevřený ("textDocument/didOpen"). Od této chvíle již není pravda o obsahu dokumentu v systému souborů, ale uchovává nástroj v paměti.

* **Uživatel provede úpravy**: Nástroj upozorní server na změnu dokumentu ("textDocument/didChange") a sémantické informace o programu jsou aktualizovány jazykovým serverem. V takovém případě jazykový server analyzuje tyto informace a upozorní nástroj zjištěnými chybami a upozorněními ("textDocument/publishDiagnostics").

* **Uživatel provede "Přejít na definici" na symbol v editoru**: Nástroj odešle požadavek 'textDocument/definition' se dvěma parametry: (1) identifikátor URI dokumentu a (2) textový postoj, odkud byl iniciován požadavek Přejít na definici na server. Server odpoví identifikátorem URI dokumentu a umístěním definice symbolu uvnitř dokumentu.

* **Uživatel zavře dokument (soubor)**: 'textDocument/didClose' oznámení je odeslána z nástroje, informování jazykový server, že dokument je nyní již v paměti a že aktuální obsah je nyní aktuální v systému souborů.

Tento příklad ilustruje, jak protokol komunikuje s jazykovým serverem na úrovni funkcí editoru, jako je "Přejít na definici", "Najít všechny odkazy". Datové typy používané protokolem jsou editor nebo IDE 'datové typy' jako aktuálně otevřený textový dokument a umístění kurzoru. Datové typy nejsou na úrovni modelu domény programovacího jazyka, který by obvykle poskytoval abstraktní syntaktické stromy a symboly kompilátoru (například vyřešené typy, obory názvů, ...). To výrazně zjednodušuje protokol.

Nyní se podívejme na 'textDocument /definition' požadavek podrobněji. Níže jsou datové části, které jdou mezi klientský nástroj a jazykový server pro "Přejít na definici" požadavek v dokumentu C++.

Toto je požadavek:

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

Toto je odpověď:

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

Při zpětném pohledu je popis datových typů na úrovni editoru spíše než na úrovni modelu programovacího jazyka jedním z důvodů úspěchu protokolu jazykového serveru. Je mnohem jednodušší standardizovat identifikátor URI textového dokumentu nebo pozici kurzoru ve srovnání se standardizací abstraktního stromu syntaxe a symbolů kompilátoru v různých programovacích jazycích.

Když uživatel pracuje s různými jazyky, VS Code obvykle spustí jazykový server pro každý programovací jazyk. Následující příklad ukazuje relaci, kde uživatel pracuje na Java a SASS soubory.

![java a sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Možnosti

Ne každý jazykový server může podporovat všechny funkce definované protokolem. Proto klient a server oznamuje jejich podporované funkce nastavené prostřednictvím 'schopnosti'. Jako příklad server oznamuje, že může zpracovat požadavek 'textDocument/definition', ale nemusí zpracovat požadavek "pracovní prostor/symbol". Podobně mohou klienti oznámit, že jsou schopni poskytnout oznámení o uložení před uložením dokumentu, aby server mohl vypočítat textové úpravy pro automatické formátování upraveného dokumentu.

## <a name="integrating-a-language-server"></a>Integrace jazykového serveru

Skutečná integrace jazykového serveru do určitého nástroje není definována protokolem jazykového serveru a je ponechána implementátorům nástrojů. Některé nástroje integrují jazykové servery obecně tím, že mají rozšíření, které lze spustit a mluvit s jakýmkoli jazykem serveru. Jiné, například VS Code, vytvářejí vlastní rozšíření na jazykový server, takže rozšíření je stále schopno poskytovat některé vlastní jazykové funkce.

Pro zjednodušení implementace jazykových serverů a klientů existují knihovny nebo sady SDK pro klientské a serverové části. Tyto knihovny jsou k dispozici pro různé jazyky. Například je [modul npm klienta jazyka](https://www.npmjs.com/package/vscode-languageclient) pro usnadnění integrace jazykového serveru do rozšíření VS Code a jiného [modulu npm pro](https://www.npmjs.com/package/vscode-languageserver) zápis jazykového serveru pomocí node.js. Toto je aktuální [seznam](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) knihoven podpory.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Použití protokolu Language Server Protocol v sadě Visual Studio

* [Přidání rozšíření Language Server Protocol](adding-an-lsp-extension.md) – Informace o integraci jazykového serveru do sady Visual Studio.
