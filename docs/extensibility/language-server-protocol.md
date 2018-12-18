---
title: Přehled protokolu Server Language | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/14/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad0e802bd63a9d489a98eb9f216e6739e378d590
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894856"
---
# <a name="language-server-protocol"></a>Protokol jazyka serveru

## <a name="what-is-the-language-server-protocol"></a>Co je protokol jazyka serveru?

Podpůrné bohaté funkce úprav, jako je zdrojový kód dokončováním automaticky nebo **přejít k definici** pro programovací jazyk v nějakém editoru nebo prostředí IDE je obvykle velmi obtížné a časově náročné. Obvykle se vyžaduje zadání doménový model (skener, analyzátor, kontrolu typu, tvůrce a další) v programovacím jazyce IDE nebo editoru. Například modul plug-in Eclipse CDT, který poskytuje podporu pro C/C++ v integrovaném vývojovém prostředí Eclipse napsané v jazyce Java od integrovaného vývojového prostředí Eclipse, samotného je napsána v jazyce Java. Následující tento přístup, znamená to implementace modelu domény C/C++ v TypeScript pro Visual Studio Code a model v samostatné doméně C# pro sadu Visual Studio.

Vytváření domény jazykově specifické modely jsou také mnohem jednodušší, pokud nástroj pro vývoj můžete znovu použít existující knihovny pro konkrétní jazyky. Tyto knihovny jsou obvykle implementovány v programovacím jazyce (například dobré C/C++ doménu, kterou modely jsou implementovány v jazyce C/C++). Integrace knihovny jazyka C/C++ do editoru napsané v TypeScript je technicky možné ale obtížné provést.

### <a name="language-servers"></a>Jazyk servery

Další možností je spustit knihovny ve svém vlastním procesu a využít meziprocesové komunikace na to. Zprávy odeslané vzájemně tvoří protokol. Protokol jazyka serveru (LSP) je produkt standardizovat zprávy vyměňují mezi proces serveru jazyk a vývojový nástroj. Použití jazyka servery nebo demons není nové nebo nový nápad. Editory jako Vim a Emacs mají byla to nějakou dobu k zajištění podpory sémantický automatické dokončování. Cílem LSP byla pro zjednodušení tyto druhy integrace a poskytují užitečné rámec pro vystavení jazykové funkce pro celou řadu nástrojů.

Společný protokol umožňuje integraci programovacích funkcí jazyka do vývojový nástroj s minimálními fuss opětovným použitím stávající implementaci modelu domény jazyk. Jazyk serveru back endem může být napsaná v PHP, Python nebo Java a LSP umožňuje ji snadno integrovat do různých nástrojů. Protokol pracuje na běžné úroveň abstrakce, tak, aby nástroj může nabídnout bohaté jazykových služeb bez nutnosti abyste úplně pochopili drobné rozdíly specifické pro základní model domény.

## <a name="how-work-on-the-lsp-started"></a>Jak fungují na LSP spuštění

LSP se průběžně vyvíjel a teď je ve verzi 3.0. Spustit při konceptu jazyka serveru se nenačítají omnisharp k poskytování bohatých funkcí pro úpravy pro C#. Na začátku OmniSharp použít protokol HTTP s datovou část JSON a je integrována do několika editory včetně [Visual Studio Code](https://code.visualstudio.com).

Přibližně ve stejnou dobu Microsoft začal pracovat na serveru jazyka TypeScript, za účelem podpory TypeScript v editorech jako (emacs) a Sublime Text. V této implementaci editoru komunikuje přes stdin/stdout pomocí procesu TypeScript serveru a používá INSPIROVANÉ ladicí program protokolu V8 datovou část JSON pro požadavky a odpovědi. TypeScript server integroval do TypeScript Sublime modul plug-in a VS Code pro bohaté úpravy TypeScript.

Po s obslužných rutin integrated dva servery pro jiný jazyk, VS Code tým postupně přišel s novým prostředím běžné protokol jazyka serveru editory a integrovanými vývojovými prostředími. Společný protokol umožňuje poskytovatele jazyka k vytvoření serveru jeden jazyk, který mohou využívat jiné prostředí IDE. Jazyk serveru příjemce má jenom jednou implementace protokolu na straně klienta. Výsledkem win-win situace pro poskytovatele jazyka a jazyk příjemce.

Protokol jazyka serveru začít protokolu používané serverem TypeScript rozšíření s další jazykové funkce INSPIROVANÉ VS Code jazyka rozhraní API. Protokol se zálohuje pomocí JSON-RPC pro vzdálené volání díky jednoduchost a knihovny.

VS Code týmu prototypem. protokol implementací několik serverů linter jazyka, které reagovat na požadavky na lint (kontroly) souboru a vrátit sadu zjištěné upozornění a chyby. Cílem bylo lint soubor jako uživatelské úpravy v dokumentu, což znamená, že během relace editor bude existovat mnoho linting požadavků. To dávalo smysl použít zachovat serveru a spouštění tak, aby nový proces linting nejsou potřeba ke spuštění pro každé uživatelské úpravy. Několik serverů linter byly implementované, včetně VS Code ESLint a TSLint rozšíření. Tyto dva servery linter jsou implementovány v jazyce TypeScript/JavaScript i spustit na Node.js. Sdílení knihovny, který implementuje klientských a serverových součástí protokolu.

## <a name="how-the-lsp-works"></a>Jak funguje LSP

Jazyk serveru běží ve vlastním procesu a nástrojů, jako je Visual Studio nebo VS Code komunikovat se serverem přes JSON-RPC pomocí protokolu jazyka. Další výhodou operační ve vyhrazeném procesu serveru jazyk je předcházet problémům s výkonem související s modelem jednoho procesu. Skutečné přenosový kanál může být buď stdio, sokety, pojmenované kanály nebo uzel ipc Pokud klient i server jsou napsané v Node.js.

Níže je příklad pro nástroj a jazyk serveru komunikaci během rutinu úprav relace:

![Vývojový diagram vrstvy](media/lsp-flow-diagram.png)

* **Uživatel otevře soubor (označované jako dokument) v nástroji**: nástroj oznámí jazyk serveru je otevřený dokument ("textDocument/didOpen"). Od této chvíle pravdivých informací o obsahu dokumentu je už v systému souborů, ale ponechá nástroj v paměti.

* **Uživatel provede změny**: nástroj pošle oznámení serveru o změně dokumentu ("textDocument/didChange") a sémantické informace programu se aktualizuje pomocí jazyka serveru. V takovém případě jazyk serveru tyto informace analyzuje a upozorní nástroj zjištěné chyby a upozornění ("textDocument/publishDiagnostics").

* **Uživatel provede "Přejít k definici" na symbol v editoru**: Nástroj odešle požadavek ' textDocument/definici' se dvěma parametry: (1) identifikátor URI dokumentu a (2) umístění textu, ze kterého byla spuštěna přejít na definici požadavku na server. Server odpoví identifikátor URI dokumentu a umístění definice symbolu v dokumentu.

* **Uživatel nezavře dokument (soubor)**: ' textDocument/didClose' oznámení se odesílá z nástroje informování jazyk serveru, na kterém je dokument nyní již v paměti a které aktuální obsah je nyní aktuální v systému souborů.

Tento příklad ukazuje, jak se protokol komunikuje se serverem nástroje jazyka na úrovni funkce editoru, jako je "Přejít k definici", "Najít všechny odkazy". Datové typy používané v protokolu jsou editoru nebo integrovaného vývojového prostředí datové typy jako otevřený textový dokument a pozici kurzoru. Datové typy, které nejsou na úrovni programovací model domény jazyka, která by obvykle mají stromu abstraktní syntaxe a kompilátoru symboly (například přeložit typy, obory názvů,...). To výrazně zjednodušuje protokolu.

Nyní Pojďme se podívat na žádost "textDocument/definice" podrobněji. V následující tabulce jsou datových částí, které patří mezi nástrojem klienta a serveru jazyk pro požadavek "Přejít k definici" v dokumentu C++.

To je požadavek:

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

Jedná se o odpověď:

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

Když popisující typy dat na úrovni editoru, nikoli na úrovni modelu programovací jazyk je jedním z důvodů pro úspěch protokol jazyka serveru. Je mnohem jednodušší ke standardizaci textový dokument identifikátor URI nebo pozice kurzoru v porovnání s standardizovat abstraktní syntaxe stromu a kompilátoru symboly v různých programovacích jazycích.

Když uživatel pracuje s různými jazyky, VS Code obvykle spouští na serveru jazyk každý programovací jazyk. Následující příklad ukazuje relaci, kde uživatel pracuje na jazyce Java a SASS soubory.

![Java a sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Možnosti

Každý jazyk serveru může podporovat všechny funkce definované v protokolu. Proto se klient a server oznamuje jejich sadu podporovaných funkcí prostřednictvím "funkce". Například server oznamuje, že ho můžou zpracovat žádost o "textDocument/definice", ale to nemusí zpracovat žádost o 'pracovní prostor/symbol'. Podobně můžete klientům oznamujeme, že jsou schopný poskytnout ' Chystáte se uložit' oznámení předtím, než je uložen dokument, aby server dokáže výpočetní textové úpravy automaticky formátovat upravený dokument.

## <a name="integrating-a-language-server"></a>Integrace jazyka serveru

Skutečné integrace jazyk serveru do určitého nástroje není určené protokol jazyka serveru a je ponecháno na implementors nástroj. Některé nástroje integrace jazyka serverů obecně tak, že rozšíření, které lze spustit a obraťte se na jakýkoli druh jazyk serveru. Jiné, jako VS Code, vytvořte vlastní rozšíření na serveru pro jazyk tak, aby je mít pořád povolený a zajistit tak některé funkce vlastních jazykových rozšíření.

Pro zjednodušení implementace jazyka serverů a klientů, existují knihovny nebo sad SDK pro součásti klienta a serveru. Tyto knihovny jsou k dispozici pro různé jazyky. Například neexistuje [modul npm jazyk klienta](https://www.npmjs.com/package/vscode-languageclient) k usnadnění integrace jazyk serveru do rozšíření VS Code a další [modul npm jazyk serveru](https://www.npmjs.com/package/vscode-languageserver) zapsat jazyk serveru pomocí Node.js. Toto je aktuální [seznamu](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) podporu knihoven.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>V sadě Visual Studio pomocí protokol jazyka serveru

* [Přidání rozšíření protokol jazyka serveru](adding-an-lsp-extension.md) – přečtěte si o integraci jazyk serveru do sady Visual Studio.
