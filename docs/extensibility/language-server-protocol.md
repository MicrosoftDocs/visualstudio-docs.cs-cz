---
title: Přehled protokolu jazykového serveru | Microsoft Docs
description: Přečtěte si, jak protokol jazykového serveru poskytuje užitečnou architekturu pro vystavení funkcí jazyka pro celou řadu nástrojů.
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5dd212b5f75679b44175d9b160d3e11d2075d6a5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074025"
---
# <a name="language-server-protocol"></a>Protokol jazyka serveru

## <a name="what-is-the-language-server-protocol"></a>Jaký je protokol jazykového serveru?

Podpora bohatých funkcí úprav, jako je automatické dokončování zdrojového kódu, nebo **Přechod na definici** programovacího jazyka v editoru nebo integrovaném vývojovém prostředí (IDE) je tradičně velmi náročná a časově náročná. Obvykle vyžaduje zápis doménového modelu (skener, analyzátor, kontroly typu, tvůrce a další) v programovacím jazyce editoru nebo integrovaného vývojového prostředí (IDE). Například modul plug-in CDT s zatmění, který poskytuje podporu pro C/C++ v integrovaném vývojovém prostředí (IDE), je napsán v jazyce Java, protože samotné integrované vývojové prostředí (IDE) je napsáno Po tomto přístupu by to znamenalo, že implementace doménového modelu C/C++ v kódu TypeScript pro Visual Studio a samostatném doménovém modelu v jazyce C# pro Visual Studio.

Vytváření modelů domén specifických pro jazyk je také mnohem jednodušší, pokud vývojový nástroj může znovu použít stávající knihovny specifické pro jazyk. Tyto knihovny jsou však obvykle implementovány v samotném programovacím jazyce (například správné doménové modely C/C++ jsou implementovány v jazyce C/C++). Integrace knihovny jazyka C/C++ do editoru napsaného v TypeScript je technicky možná, ale je těžká.

### <a name="language-servers"></a>Jazykové servery

Další možností je spustit knihovnu ve vlastním procesu a použít komunikaci mezi procesy. Zprávy, které se odešlou dál, tvoří protokol. Protokol LSP (Language Server Protocol) je produktem standardizace zpráv vyměňovaných mezi vývojovým nástrojem a procesem jazykového serveru. Použití jazykových serverů nebo Demons není novou nebo novou myšlenou. Editory, jako je například systémem VIM a (Emacs), v tuto chvíli prováděly podporu sémantického automatického dokončování. Cílem LSP bylo zjednodušit tyto možnosti sloučení a poskytnout užitečnou architekturu pro vystavení funkcí jazyka pro celou řadu nástrojů.

Pokud máte společný protokol, umožníte integraci funkcí programovacího jazyka do vývojového nástroje s minimálním Fuss, a to tak, že znovu použijete stávající implementaci doménového modelu jazyka. Back-end jazykového serveru může být napsaný v PHP, Pythonu nebo Java a LSP umožňuje snadnou integraci do různých nástrojů. Protokol pracuje na společné úrovni abstrakce, aby nástroj mohl nabízet bohatou jazykovou službu, aniž by bylo nutné plně porozumět drobné odlišnostiům, které jsou specifické pro základní doménový model.

## <a name="how-work-on-the-lsp-started"></a>Jak začít pracovat na LSP

LSP se vyvíjí v průběhu času a dnes je verze 3,0. Začaly se v době, kdy byl koncept serverového serveru převzatý OmniSharp, aby poskytoval funkce pro úpravy s bohatou funkcí pro jazyk C#. Zpočátku OmniSharp použil protokol HTTP s datovou částí JSON a byl integrován do několika editorů, včetně [Visual Studio Code](https://code.visualstudio.com).

V současné době začal Microsoft pracovat na jazykovém serveru TypeScript s nápadem na podporu TypeScript v editorech, jako je (Emacs) a text v podvápně. V této implementaci Editor komunikuje přes STDIN/stdout s procesem serveru TypeScript a používá datovou část JSON nechte inspirovat protokolem V8 debugger pro žádosti a odpovědi. Server TypeScript byl integrovaný do modulu plug-in TypeScript a VS Code pro bohatou úpravu TypeScriptu.

Po integraci dvou různých jazykových serverů začne tým VS Code prozkoumat protokol Common Language Server pro editory a IDEs. Společný protokol umožňuje poskytovateli jazyka vytvořit jeden jazykový Server, který může používat jiné prostředí. Uživatel jazykového serveru musí jenom jednou implementovat stranu klienta protokolu. To vede k situaci win pro poskytovatele jazyka i pro příjemce jazyka.

Protokol jazykového serveru začal protokolem používaným serverem TypeScript a rozbalí ho do dalších funkcí jazyka nechte inspirovat rozhraní API jazyka VS Code. Protokol je zálohovaný pomocí JSON – RPC pro vzdálené vyvolání z důvodu jeho jednoduchosti a existujících knihoven.

Tým VS Code prototyp protokolu implementující několik linter jazykových serverů, které reagují na požadavky na Lint (prohledání) souboru a vracejí sadu zjištěných upozornění a chyb. Cílem bylo Lint soubor jako uživatel v dokumentu, což znamená, že během relace editoru bude existovat spousta linting požadavků. To je vhodné pro udržení serveru v provozu, aby se nový proces linting nemusel spustit pro každou úpravu uživatele. Implementovalo se několik serverů linter, včetně rozšíření ESLint a TSLint pro VS Code. Tyto dva servery linter jsou implementovány v TypeScript/JavaScript a spouštěny na Node.js. Sdílejí knihovnu, která implementuje součást protokolu na straně klienta a serveru.

## <a name="how-the-lsp-works"></a>Princip principu LSP

Jazykový server běží ve vlastním procesu a nástroje, jako je Visual Studio, nebo VS Code komunikovat se serverem pomocí protokolu jazyka přes JSON – RPC. Další výhodou jazykového serveru, který pracuje v rámci vyhrazeného procesu, je vyhnout se problémům s výkonem souvisejícím s modelem jednoho procesu. Samotný transportní kanál může být stdio, Sockets, Named Pipes nebo Node IPC, pokud jsou v Node.js zapsány oba klienti i servery.

Níže je příklad toho, jak nástroj a server jazyka komunikuje během běžné relace úprav:

![Diagram toku LSP](media/lsp-flow-diagram.png)

* **Uživatel otevře soubor (označovaný jako dokument) v nástroji**: nástroj upozorní jazykový Server, že je dokument otevřen (TextDocument/didOpen). Od této chvíle platí, že obsah dokumentu již není v systému souborů, ale je uchováván v paměti.

* **Uživatel provede úpravy**: nástroj upozorní server na změnu dokumentu (TextDocument/didChange) a sémantické informace programu se aktualizují pomocí jazykového serveru. V takovém případě tento jazyk analyzuje tyto informace a upozorní nástroj o zjištěné chyby a upozornění (textDocument/publishDiagnostics).

* **Uživatel spustí "přejít k definici" na symbolu v editoru**: Nástroj odešle požadavek ' textDocument/definition ' se dvěma parametry: (1) identifikátor URI dokumentu a (2) umístění textu, ze kterého byla zahájena žádost o přechod na definici na server. Server odpoví identifikátorem URI dokumentu a umístěním definice symbolu v dokumentu.

* **Uživatel zavírá dokument (soubor)**: z nástroje je odesláno oznámení "TextDocument/didClose", které informuje jazykový Server, že dokument již není v paměti a že aktuální obsah je nyní v systému souborů aktuální.

Tento příklad ukazuje, jak protokol komunikuje s jazykovým serverem na úrovni funkcí editoru, jako je "přejít k definici", "najít všechny odkazy". Datové typy používané protokolem jsou Editor nebo datové typy IDE, jako je aktuálně otevřený textový dokument a pozice kurzoru. Datové typy nejsou na úrovni doménového modelu programovacího jazyka, který by obvykle poskytoval abstraktní stromové struktury syntaxe a symboly kompilátoru (například vyřešené typy, obory názvů,...). Tím se protokol významně zjednodušuje.

Teď se podíváme na požadavek "textDocument/definition" podrobněji. Níže jsou uvedeny datové části, které se procházejí mezi nástrojem klienta a webovým serverem pro požadavek "Přejít na definici" v dokumentu C++.

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

V když, popis datových typů na úrovni editoru, nikoli na úrovni programovacího jazyka, je jedním z důvodů úspěchu protokolu jazykového serveru. Je mnohem jednodušší ke standardizaci identifikátoru URI textového dokumentu nebo pozice kurzoru ve srovnání se standardizací abstraktního stromu syntaxe a symbolů kompilátoru v různých programovacích jazycích.

Když uživatel pracuje s různými jazyky, VS Code obvykle spouští jazykový Server pro každý programovací jazyk. Následující příklad ukazuje relaci, kde uživatel pracuje na souborech Java a SASS.

![Java a Sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Možnosti

Ne všechny jazykové servery můžou podporovat všechny funkce definované protokolem. Proto klient a server oznámí svou podporovanou sadu funkcí prostřednictvím možností možnosti. Například server oznamuje, že může zpracovat požadavek "textDocument/definition", ale nemusí zpracovávat požadavek ' pracovní prostor/symbol '. Obdobně můžou klienti oznámit, že budou moct před uložením dokumentu zadat oznámení o tom, že se mají ukládat. aby mohl server vypočítat textové úpravy pro automatické formátování upravovaného dokumentu.

## <a name="integrating-a-language-server"></a>Integrace jazykového serveru

Vlastní integrace jazykového serveru do konkrétního nástroje není definována protokolem jazykového serveru a je ponechána pro implementátory nástroje. Některé nástroje integrují jazykové servery obecně tím, že mají rozšíření, které může začít a komunikovat s libovolným druhem jazykového serveru. Ostatní, například VS Code, vytvoří vlastní rozšíření na jeden jazykový Server, aby rozšíření stále mohlo poskytovat některé vlastní funkce jazyka.

Pro zjednodušení implementace jazykových serverů a klientů jsou k dispozici knihovny nebo sady SDK pro součásti klienta a serveru. Tyto knihovny jsou k dispozici pro různé jazyky. Například [klientský klientský npm modul](https://www.npmjs.com/package/vscode-languageclient) usnadňuje integraci jazykového serveru do rozšíření vs Code a jiného [modulu npm Language Server](https://www.npmjs.com/package/vscode-languageserver) pro zápis jazykového serveru pomocí Node.js. Toto je aktuální [seznam](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) knihoven podpory.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Použití protokolu jazykového serveru v aplikaci Visual Studio

* [Přidání rozšíření protokolu jazykového serveru](adding-an-lsp-extension.md) – Přečtěte si o integraci jazykových serverů do sady Visual Studio.
