---
title: Konfigurace upozornění v jazyce Visual Basic | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c3b28bea858c867bd7fae8e1b4045d79d5e4b513
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49297606"
---
# <a name="configuring-warnings-in-visual-basic"></a>Konfigurace upozornění v jazyce Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Kompilátor obsahuje sadu upozornění na kód, který může způsobit chyby za běhu. Tyto informace můžete použít k zápisu čisticí, rychlejší a lepší kód s menším počtem chyb. Například bude kompilátor vytvoření upozornění, když se uživatel pokusí se vyvolat člena nepřiřazený objekt proměnné vrácená z funkce, aniž byste museli nastavovat návratovou hodnotu nebo provést `Try` blok s chyby v logice jak zachytávat výjimky.  
  
 V některých případech kompilátor poskytuje další logiku jménem uživatele, uživatel se mohli zaměřit na daný úkol, nikoli na předvídání možných chyb. V předchozích verzích [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], `Option Strict` byla použita pro omezení další logiku, která [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kompilátor poskytuje. Konfigurace upozornění umožňuje omezit tuto logiku tak podrobnější na úrovni jednotlivých upozornění.  
  
 Můžete přizpůsobit svůj projekt a vypnout upozornění není relevantní pro vaši aplikaci při zapínání další varování k chybám. Tato stránka vysvětluje, jak zapnout a vypnout jednotlivých upozornění.  
  
## <a name="turning-warnings-off-and-on"></a>Zapnutí vypínat a zapínat upozornění  
 Existují dva různé způsoby konfigurace upozornění: je možné nakonfigurovat pomocí **Návrháře projektu**, nebo můžete použít **/warnaserror** a **/nowarn** – možnosti kompilátoru .  
  
 **Kompilaci** karty **Návrháře projektu** stránka umožňuje zapnutí a vypnutí upozornění. Vyberte **zakázat všechna upozornění** zaškrtněte políčko Zakázat všechna upozornění, vyberte **považovat všechna upozornění jako chyby** považovat všechna upozornění jako chyby. Můžou být některé jednotlivých upozornění jako chyby nebo upozornění podle potřeby v zobrazené tabulce.  
  
 Když **Option Strict** je nastavena na **vypnout**, **Option Strict** související upozornění, nemůže být zpracován nezávisle na sobě. Když **Option Strict** je nastavena na **na**související upozornění jsou považována za chyby, bez ohledu na jejich stav není. Když **Option Strict** je nastavena na **vlastní** zadáním `/optionstrict:custom` v kompilátoru příkazového řádku **Option Strict** upozornění můžete zapnout nebo vypnout nezávisle na sobě.  
  
 **/Warnaserror** možnost příkazového řádku pro kompilátor lze také použít k určení, zda upozornění jsou považována za chyby. Čárkou oddělený seznam můžete přidat do této možnosti určíte, která upozornění mají být považována za chyby nebo varování pomocí + nebo -. Následující tabulka obsahuje podrobnosti o dostupných možností.  
  
|Možnost příkazového řádku|Určuje|  
|--------------------------|---------------|  
|`/warnaserror+`|Považovat všechna upozornění jako chyby|  
|`/warnsaserror`-|Není považovat upozornění za chyby. Toto nastavení je výchozí.|  
|`/warnaserror+:<warning list``>`|Zpracovávat specifická upozornění jako chyby, seřazené podle jejich ID číslo chyby v r seznam oddělený čárkami.|  
|`/warnaserror-:<warning list>`|Ne zpracovávat specifická upozornění jako chyby, seřazené podle jejich čísla ID chyby na seznam oddělený čárkami.|  
|`/nowarn`|Neoznamují se upozornění.|  
|`/nowarn:<warning list>`|Neoznamují se zadaným upozornění zobrazeného podle jejich ID číslo chyby v seznam oddělený čárkami.|  
  
 Seznam upozornění obsahuje identifikační čísla upozornění, která mají být považována za chyby, které je možné použít s možností příkazového řádku k zapnutí nebo vypnutí specifická upozornění chyb. Pokud seznam upozornění obsahuje neplatné číslo, dojde k chybě.  
  
## <a name="examples"></a>Příklady  
 Tato tabulka příkladů argumentů příkazového řádku popisuje, co dělá každý argument.  
  
|Argument|Popis|  
|--------------|-----------------|  
|`vbc /warnaserror`|Určuje, že všechna upozornění mají být považována za chyby.|  
|`vbc /warnaserror:42024`|Určuje, že upozornění 42024 by měl být považován za chybu.|  
|`vbc /warnaserror:42024,42025`|Určuje, že upozornění 42024 a 42025 by měla být považována za chyby.|  
|`vbc /nowarn`|Určuje, že by se měly hlásit žádná upozornění.|  
|`vbc /nowarn:42024`|Určuje, že upozornění by neměly být hlášené 42024.|  
|`vbc /nowarn:42024,42025`|Určuje, že by neměly být hlášeny varování 42024 a 42025.|  
  
## <a name="types-of-warnings"></a>Typy upozornění  
 Tady je seznam upozornění, která může být potřeba považovat za chyby.  
  
### <a name="implicit-conversion-warning"></a>Implicitní převod upozornění  
 Vygenerovaný pro instance implicitní převod. Při použití neobsahují implicitní převod z vnitřního číselného typu řetězec `&` operátor. Výchozí pro nové projekty je vypnuté.  
  
 ID: 42016  
  
### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Pozdní vazba volání metody a upozornění rozlišení přetížení  
 Vygenerovaný pro instance třídy pozdní vazby. Výchozí pro nové projekty je vypnuté.  
  
 ID: 42017  
  
### <a name="operands-of-type-object-warnings"></a>Operandy typu Object upozornění  
 Generováno v případě operandy typu `Object` dojít k chybě, která by vytvořila `Option Strict On`. Výchozí pro nové projekty zapnutý.  
  
 ID: 42018 a 42019  
  
### <a name="declarations-require-as-clause-warnings"></a>Deklarace vyžadovat jako upozornění – klauzule  
 Vygeneruje, když proměnné, funkce nebo ve kterém chybí vlastnost deklarace `As` klauzule by vytvořila chybu s `Option Strict On`. Proměnné, které nemají typu přiřazené jsou považovány za typ `Object`. Výchozí pro nové projekty zapnutý.  
  
 ID: 42020 (deklarace proměnné), 42021 (deklarace funkce) a 42022 (deklaraci vlastnosti).  
  
### <a name="possible-null-reference-exception-warnings"></a>Upozornění na výjimky možné odkaz s hodnotou Null  
 Vygeneruje, když nějaká proměnná použije předtím, než jí byla přiřazena hodnota. Výchozí pro nové projekty zapnutý.  
  
 ID: 42104, 42030  
  
### <a name="unused-local-variable-warning"></a>Upozornění pro nepoužívané místní proměnné  
 Vygeneruje, když místní proměnná je deklarovaná, ale nikdy uvedené. Výchozí hodnota je na.  
  
 ID: 42024  
  
### <a name="access-of-shared-member-through-instance-variable-warning"></a>Přístup sdíleného člena prostřednictvím Instance proměnné upozornění  
 Vygeneruje, když přístup sdíleného člena prostřednictvím instance může mít vedlejší účinky, nebo když přístup sdíleného člena prostřednictvím instance proměnné je pravá strana výrazu nebo je právě předaný jako parametr. Výchozí pro nové projekty zapnutý.  
  
 ID: 42025  
  
### <a name="recursive-operator-or-property-access-warnings"></a>Rekurzivní operátor nebo upozornění pro vlastnosti  
 Vygeneruje, když text rutinu používá stejný operátor nebo vlastnosti, které je definováno v. Výchozí pro nové projekty zapnutý.  
  
 ID: 42004 (operátor), 42026 (vlastnost)  
  
### <a name="function-or-operator-without-return-value-warning"></a>Funkce nebo operátor bez návratové hodnoty upozornění  
 Vygeneruje, když funkce nebo operátor nemá návratovou hodnotu zadané. Jedná se o vynechání `Set` implicitní místní proměnné se stejným názvem jako funkce. Výchozí pro nové projekty zapnutý.  
  
 ID: 42105 (funkce), 42016 (operátor)  
  
### <a name="overloads-modifier-used-in-a-module-warning"></a>Modifikátor přetížení použitý v modulu upozornění  
 Generováno v případě `Overloads` je používán `Module`. Výchozí pro nové projekty zapnutý.  
  
 ID: 42028  
  
### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Duplicitní nebo překrývající se upozornění bloky Catch  
 Generován, když `Catch` bloku se nedospělo kvůli jejich vztah k jiné `Catch` bloky, které byly definovány. Výchozí pro nové projekty zapnutý.  
  
 ID: 42029, 42031  
  
## <a name="see-also"></a>Viz také  
 [Dialogové okno výjimky Průvodce nastavením](../debugger/exception-assistant-dialog-box.md)   
 [Typy chyb](http://msdn.microsoft.com/library/3048aabf-8c97-4e13-9150-853769cb5f6f)   
 [Try... Catch... Finally – příkaz](http://msdn.microsoft.com/library/d6488026-ccb3-42b8-a810-0d97b9d6472b)   
 [/ nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83)   
 [/ warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1)   
 [Stránka kompilovat, Návrhář projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Upozornění kompilátoru, která jsou ve výchozím natavení vypnutá](http://msdn.microsoft.com/library/69809cfb-a38a-4035-b154-283a61938df8)





