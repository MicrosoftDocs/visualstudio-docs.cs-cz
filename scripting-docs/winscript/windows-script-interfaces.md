---
title: Skriptovací rozhraní Windows | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 141f3f0e60e797a4104c3e276775631f6e9196c5
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835404"
---
# <a name="windows-script-interfaces"></a>Skriptovací rozhraní systému Windows

Skriptovací rozhraní Microsoft Windows poskytují způsob, jak aplikaci přidat skriptování a automatizaci OLE. Hostitelé skriptování, kteří spoléhají na skript Windows, můžou pomocí skriptovacích strojů z různých zdrojů a dodavatelů spravovat skriptování mezi komponentami. Implementace samotného skriptu – jazyk, syntaxe, trvalý formát, spouštěcí model a tak dále, je ponechána na dodavatele skriptu.

Dokumentace ke skriptům Windows je rozdělená do následujících částí:

[Moduly Windows Script Host](../winscript/windows-script-hosts.md)

[Skriptovací stroje systému Windows](../winscript/windows-script-engines.md)

[Přehled ladění aktivních skriptů](../winscript/active-script-debugging-overview.md)

[Přehled profilace aktivních skriptů](../winscript/active-script-profiling-overview.md)

[Referenční dokumentace skriptovacích rozhraní systému Windows](../winscript/reference/windows-script-interfaces-reference.md)

## <a name="windows-script-background"></a>Pozadí skriptu Windows

Skriptovací rozhraní systému Windows spadají do dvou kategorií: hostitelé skriptů Windows a skriptovací stroje Windows. Hostitel vytvoří skriptovací modul a zavolá modul, aby spouštěl skripty. Mezi příklady hostitelů Windows Script patří:

- Microsoft Internet Explorer

- Nástroje pro tvorbu Internetu

- Prostředí

Skriptovací stroje Windows je možné vyvíjet pro jakýkoli jazyk nebo prostředí run-time, včetně:

- Microsoft Visual Basic Scripting Edition (VBScript)

- Perl

- Lispu

Aby bylo možné implementovat hostitele jako flexibilní, je k dispozici obálka OLE Automation pro skript Windows. Nicméně hostitel, který používá tento objekt obálky k vytvoření instance skriptovacího stroje, nemá úroveň kontroly nad prostorem názvů za běhu, trvalým modelem a tak dále, který by používal přímo skript Windows.

Návrh skriptu Windows izoluje prvky rozhraní požadované jenom ve vývojovém prostředí, takže neautoři hostitelů (například prohlížeče a prohlížečů) a skriptovacích strojů (například VBScript) je možné uchovávat jako odlehčené.

## <a name="windows-script-basic-architecture"></a>Architektura Windows Script Basic

Následující ilustrace znázorňuje interakci mezi hostitelem skriptu Windows a skriptovacím strojem Windows.

Postup, který je součástí interakce mezi hostitelem a strojem, je uveden v následujícím seznamu.

1. Vytvořte projekt. Hostitel načte projekt nebo dokument. (Tento krok se nepoužívá pro skript Windows, ale je zde k dispozici pro úplnost.)

2. Vytvořte skriptovací modul Windows. Hostitel volá `CoCreateInstance` Vytvoření nového skriptovacího modulu Windows, který určí identifikátor třídy (CLSID) konkrétního skriptovacího stroje, který se má použít. Například prohlížeč HTML aplikace Internet Explorer přijímá identifikátor třídy skriptovacího stroje pomocí atributu CLSID = \<OBJECT> značky HTML.

3. Načtěte skript. Pokud se obsah skriptu zachová, hostitel zavolá metodu skriptovacího stroje `IPersist*::Load` , aby ho popsal jako úložiště skriptu, Stream nebo kontejner objektů a dat. V opačném případě hostitel používá `IPersist*::InitNew` metodu nebo [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) k vytvoření skriptu s hodnotou null. Hostitel, který udržuje skript jako text, může použít [IActiveScriptParse::P arsescripttext](../winscript/reference/iactivescriptparse-parsescripttext.md) pro zakládání skriptovacího stroje text skriptu po jeho volání `IActiveScriptParse::InitNew` .

4. Přidejte pojmenované položky. Pro každou pojmenovanou položku nejvyšší úrovně (například stránky a formuláře) naimportované do oboru názvů skriptovacího modulu hostitel zavolá metodu [IActiveScript:: AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) , která vytvoří položku v názvovém prostoru modulu. Tento krok není nutný, pokud jsou pojmenované položky nejvyšší úrovně již součástí trvalého stavu skriptu načteného v kroku 3. Hostitel nepoužívá `IActiveScript::AddNamedItem` k přidání pojmenovaných položek (jako jsou ovládací prvky na stránce HTML). místo toho modul nepřímo získá položky podúrovně z položek nejvyšší úrovně pomocí `ITypeInfo` `IDispatch` rozhraní a rozhraní hostitele.

5. Spusťte skript. Hostitel způsobí, že modul spustí spuštění skriptu nastavením příznaku SCRIPTSTATE_CONNECTED v metodě [IActiveScript:: SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) . Toto volání by zřejmě provedlo jakoukoli práci při vytváření skriptovacích strojů, včetně statické vazby, zapojení až k událostem (viz níže), a spouštění kódu způsobem podobným skriptovým `main()` funkcím.

6. Získat informace o položce Pokaždé, když skriptovací stroj potřebuje přidružit symbol k položce nejvyšší úrovně, zavolá metodu [IActiveScriptSite:: GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) , která vrací informace o dané položce.

7. Zapojit události. Před spuštěním vlastního skriptu se skriptovací stroj připojí k událostem všech relevantních objektů prostřednictvím `IConnectionPoint` rozhraní.

8. Vyvolání vlastností a metod. Při spuštění skriptu aplikace skriptovacího stroje realizuje odkazy na metody a vlastnosti v pojmenovaných objektech prostřednictvím `IDispatch::Invoke` nebo jiných standardních mechanismů vazby OLE.

## <a name="windows-script-terms"></a>Windows Script – výrazy

Tento seznam obsahuje definice termínů souvisejících s skriptováním, které jsou použity v tomto dokumentu.

|Pojem|Definice|
|----------|----------------|
|Objekt Code|Instance vytvořená skriptovacím modulem, který je spojen s pojmenovanou položkou, například modul za formulářem v Visual Basic nebo třída C++ přidružená k pojmenované položce. V takovém případě je to objekt modelu COM komponenty OLE (Component Object Model), který podporuje automatizaci OLE, takže hostitel nebo jiná entita bez skriptu může manipulovat s objektem kódu.|
|Pojmenovaná položka|Objekt OLE COM (nejlépe pro něj, který podporuje automatizaci OLE), který hostitel považuje za zajímavého ke skriptu. Mezi příklady patří stránka HTML a prohlížeč ve webovém prohlížeči a dokument a dialogová okna v Microsoft Wordu.|
|Skript|Data, která tvoří program, který skriptovací modul spouští. Skriptem může být jakákoli souvislá spustitelná data, včetně částí textu, bloků `pcode` nebo dokonce spustitelných bajtových kódů specifických pro konkrétní počítač. Hostitel načte skript do skriptovacího stroje přes jedno z `IPersist*` rozhraní nebo prostřednictvím rozhraní [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) .|
|Skriptovací modul|Objekt OLE, který zpracovává skripty. Skriptovací modul implementuje rozhraní [IActiveScript](../winscript/reference/iactivescript.md) a volitelně také rozhraní [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) .|
|Hostitel skriptování|Aplikace nebo program, který vlastní skriptovací stroj Windows. Hostitel implementuje rozhraní [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) a volitelně rozhraní [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md) .|
|Skriptletu|Část skriptu, který je připojen k objektu prostřednictvím rozhraní [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) . Agregovaná kolekce skriptlety je skript.|
|Skriptovací jazyk|Jazyk, ve kterém je vytvořen skript (například VBScript) a sémantika daného jazyka.|