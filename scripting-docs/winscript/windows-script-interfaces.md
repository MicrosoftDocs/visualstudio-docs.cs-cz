---
title: Skriptovací rozhraní Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f98e60a82735ae561edf404763e0700f71b3a3d4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905360"
---
# <a name="windows-script-interfaces"></a>Skriptovací rozhraní systému Windows

Skriptovací rozhraní Microsoft Windows umožňují pro aplikace pro přidání skriptování a automatizaci OLE. Hostitelé, kteří využívají skript Windows Scripting můžete skriptovacích strojů z několika zdrojů a dodavatelů spravovat skriptování mezi komponentami. Implementace samotný skript – jazyk, syntaxe, trvalém formátu, spouštěcí model a tak dále, je ponecháno na dodavatele skriptu.

Dokumentace ke službě Windows skriptu je rozdělen do následujících částí:

[Moduly Windows Script Host](../winscript/windows-script-hosts.md)

[Skriptovací stroje systému Windows](../winscript/windows-script-engines.md)

[Přehled ladění aktivních skriptů](../winscript/active-script-debugging-overview.md)

[Přehled profilace aktivních skriptů](../winscript/active-script-profiling-overview.md)

[Referenční dokumentace skriptovacích rozhraní systému Windows](../winscript/reference/windows-script-interfaces-reference.md)

## <a name="windows-script-background"></a>Pozadí skript Windows

Rozhraní Windows skriptů spadají do dvou kategorií: Windows Script Host a moduly Windows Script. Hostitel vytvoří skriptovací stroj a volá na modul na spouštění skriptů. Příklady Windows Script Host:

- Microsoft Internet Explorer

- Internetové nástroje pro tvorbu

- Prostředí

Moduly Windows Script mohou být vytvořeny pro libovolný jazyk nebo běhového prostředí, včetně:

- Microsoft Visual Basic Scripting Edition (VBScript)

- Perl

- Lisp

Chcete-li možné nejpružnější implementace hostitele, je k dispozici automatizace OLE obálky pro skript Windows. Hostitele, který používá tento objekt obálky pro vytvoření instance skriptovací stroj však nemá stupeň kontroly nad obor názvů za běhu, model trvalosti a tak dále, která by jej přímo použít skript Windows.

Skript Windows návrh izoluje prvky rozhraní vyžaduje pouze ve vývojovém prostředí tak, aby nonauthoring hostitele (například s prohlížeči a prohlížeče) a moduly skriptu (například VBScript) můžete uchovávat zjednodušené.

## <a name="windows-script-basic-architecture"></a>Základní architektura Windows Script

Následující obrázek ukazuje interakci mezi Windows Script host a modul skriptu Windows.

V následujícím seznamu jsou uvedeny kroky interakce mezi hostitelem a modul.

1.  Vytvoření projektu. Hostitel načítá projektu nebo dokumentu. (Tento krok není konkrétní do skriptu Windows, ale je zde uveden pro úplnost.)

2.  Vytvořte modul skriptu Windows. Volání hostitele `CoCreateInstance` Pokud chcete vytvořit nový modul skriptu Windows, zadání konkrétní skriptovací stroje používat identifikátor třídy (CLSID). Například ve formátu HTML prohlížeče Internet Explorer obdrží identifikátor třídy skriptovací stroj prostřednictvím identifikátor CLSID = atributu HTML \<objektu > značky.

3.  Načítání skriptu. Pokud byly trvale zaznamenány obsah skriptu, hostitel zavolá skriptovací stroj `IPersist*::Load` metoda informačního kanálu kontejner úložiště, datového proudu nebo vlastnosti skriptu. V opačném případě hostitel používá. buď `IPersist*::InitNew` nebo [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) metodu pro vytvoření skriptu hodnotu null. Hostitele, který udržuje skript jako text můžete použít [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) ke kanálu skriptovací stroj text skriptu po volání `IActiveScriptParse::InitNew`.

4.  Přidáte pojmenovanou položky. Pro každou položku nejvyšší úrovně s názvem (například stránek a formulářů) importovat do oboru názvů skriptovací stroj, volá hostitele [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) metodu pro vytvoření položky v oboru názvů stroje. Tento krok není nutné v případě nejvyšší úrovně s názvem položky jsou již součástí trvalého stavu skriptu načteny v kroku 3. Hostitel nepoužívá `IActiveScript::AddNamedItem` přidat dílčí úkoly s názvem položky (například ovládacích prvků na stránku HTML); místo toho modul nepřímo získá položky z dílčích úkolů z položky nejvyšší úrovně s použitím hostitele `ITypeInfo` a `IDispatch` rozhraní.

5.  Spusťte skript. Hostitel způsobí, že spustíte skript nastavením příznaku SCRIPTSTATE_CONNECTED modulu [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) metody. Toto volání by pravděpodobně provádět každé skriptovací modul konstrukce dílo, včetně statických vazby, zapojování k událostem (viz níže) a spouští kód, tak nějak skriptované `main()` funkce.

6.  Získejte informace o položce. Pokaždé, když skriptovací stroj je potřeba přidružit symbol položku nejvyšší úrovně, které volá [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) metodu, která vrátí informace o dané položky.

7.  Připojení událostí. Před spuštěním vlastního skriptu, skriptovací stroj připojí k události souvisejících objektů prostřednictvím `IConnectionPoint` rozhraní.

8.  Vyvolání vlastnosti a metody. Po spuštění skriptu, skriptovací stroj realizuje odkazy na metody a vlastnosti na pojmenované objekty prostřednictvím `IDispatch::Invoke` nebo jiných mechanismů standardní vazbu OLE.

## <a name="windows-script-terms"></a>Windows Script podmínky

Tento seznam obsahuje definice skriptování souvisejících termínů použitých v tomto dokumentu.

|Termín|Definice|
|----------|----------------|
|Objekt kódu|Instance vytvořené skriptovací stroj, který je přidružen s názvem položky, jako je například modul formuláře v jazyce Visual Basic nebo C++ třídu přidruženou položku s názvem. Pokud možno toto je objekt OLE modelu COM (Component Object), která podporuje automatizace OLE, proto hostitele nebo jiná entita není skriptu můžete upravit objekt kódu.|
|Položka s názvem|Objekt OLE COM (nejlépe podporuje automatizace OLE), že hostitel považuje za zajímavé do skriptu. Mezi příklady patří stránka HTML a prohlížeče v webový prohlížeč, dokument a dialogová okna v aplikaci Microsoft Word.|
|skript|Data, která tvoří program, který spouští skriptovací stroj. Skript může být souvislé spustitelný data, včetně částí textu, bloky `pcode`, nebo dokonce kódy spustitelný bajtů specifické pro počítač. Hostitel načte skript do skriptovací stroj prostřednictvím jednoho z `IPersist*` rozhraní nebo prostřednictvím [IActiveScriptParse –](../winscript/reference/iactivescriptparse.md) rozhraní.|
|Skriptovací stroj|Objekt OLE, který zpracovává skripty. Implementuje skriptovací stroj [IActiveScript –](../winscript/reference/iactivescript.md) a volitelně [IActiveScriptParse –](../winscript/reference/iactivescriptparse.md) rozhraní.|
|Hostitelů skriptování|Aplikace nebo program, který vlastní modul skriptu Windows. Implementuje hostitele [iactivescriptsite –](../winscript/reference/iactivescriptsite.md) a volitelně [iactivescriptsitewindow –](../winscript/reference/iactivescriptsitewindow.md) rozhraní.|
|Skriptlet|Část skriptu, který získá připojen k objektu skrz [IActiveScriptParse –](../winscript/reference/iactivescriptparse.md) rozhraní. Agregační kolekce skriptlety je skript.|
|Skriptovací jazyk|Jazyk, ve kterém je skript, písemné (VBScript, třeba) a sémantika daný jazyk.|