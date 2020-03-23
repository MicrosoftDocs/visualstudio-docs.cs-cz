---
title: Konfigurace upozornění v jazyce Visual Basic
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33302a4a686d80621cc64ee018371a2d03ea30ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114726"
---
# <a name="configuring-warnings-in-visual-basic"></a>Konfigurace upozornění v jazyce Visual Basic

Kompilátor [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] obsahuje sadu upozornění o kódu, který může způsobit chyby za běhu. Tyto informace můžete použít k zápisu čistší, rychlejší a lepší kód s menším počtem chyb. Například kompilátor vytvoří upozornění, když se uživatel pokusí vyvolat člena nepřiřazené proměnné objektu, vrátit se z `Try` funkce bez nastavení vrácené hodnoty nebo spustit blok s chybami v logice zachytit výjimky.

Někdy kompilátor poskytuje další logiku jménem uživatele tak, aby se uživatel mohl soustředit na daný úkol, spíše než na předvídání možných chyb. V předchozích [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]verzích aplikace **Option Strict** byla použita k omezení další logiky, kterou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilátor poskytuje. Konfigurace upozornění umožňuje omezit tuto logiku podrobnějším způsobem na úrovni jednotlivých upozornění.

Můžete chtít přizpůsobit projekt a vypnout některá upozornění, která nejsou relevantní pro vaši aplikaci, zatímco jiné upozornění změníte na chyby. Tato stránka vysvětluje, jak zapnout a vypnout jednotlivá upozornění.

## <a name="turning-warnings-off-and-on"></a>Vypnutí a zapnutí upozornění
Existují dva různé způsoby konfigurace upozornění: můžete je nakonfigurovat pomocí **Návrháře projektu**nebo můžete použít možnosti kompilátoru **/warnaserror** a **/nowarn.**

Karta **Kompilace** na stránce **Návrhář etablování projektu** umožňuje zapínat a vypínat upozornění. Zaškrtnutím políčka **Zakázat všechna upozornění** zakážete všechna upozornění. Vyberte **možnost Považovat všechna upozornění jako chyby,** chcete-li všechna upozornění považovat za chyby. Některá jednotlivá upozornění lze přepnout jako chybu nebo upozornění podle potřeby v zobrazené tabulce.

**Je-li možnost Strict** nastavena na **vypnuto**, nelze s upozorněními souvisejícími s **možností** přistupovat nezávisle na sobě. Pokud je **možnost Strict** nastavena **na zapnuto**, jsou přidružená upozornění považována za chyby bez ohledu na jejich stav. Pokud **je možnost Strict** nastavena na **vlastní** zadáním `/optionstrict:custom` v kompilátoru příkazového řádku, můžete nezávisle zapnout nebo vypnout upozornění **striktní možnosti.**

Možnost příkazového řádku **/warnaserror** kompilátoru lze také určit, zda jsou upozornění považována za chyby. Do této možnosti můžete přidat seznam oddělený čárkami a určit, která upozornění mají být považována za chyby nebo upozornění pomocí + nebo -. V následující tabulce jsou uvedeny možné možnosti.

|Možnost příkazového řádku|Určuje|
| - |---------------|
|`/warnaserror+`|Považovat všechna upozornění za chyby|
|`/warnsaserror`-|Nepovažovat za upozornění jako chyby. Toto nastavení je výchozí.|
|`/warnaserror+:<warning list` `>`|Považovat konkrétní upozornění za chyby uvedené podle jejich id chyby v seznamu r odděleného čárkami.|
|`/warnaserror-:<warning list>`|Nezacházejte s určitými upozorněními jako s chybami uvedenými podle jejich čísla ID chyby v seznamu oddělených čárkami.|
|`/nowarn`|Neoznamujte varování.|
|`/nowarn:<warning list>`|Nevykazují zadané upozornění, uvedené podle jejich id chyby číslo v seznamu čárka oddělené.|

Seznam upozornění obsahuje čísla ID chyb upozornění, která by měla být považována za chyby, které lze použít s možnostmi příkazového řádku k zapnutí nebo vypnutí určitých upozornění. Pokud seznam upozornění obsahuje neplatné číslo, je hlášena chyba.

## <a name="examples"></a>Příklady
Tato tabulka příkladů argumentů příkazového řádku popisuje, co každý argument dělá.

|Argument|Popis|
|--------------|-----------------|
|`vbc /warnaserror`|Určuje, že všechna upozornění mají být považována za chyby.|
|`vbc /warnaserror:42024`|Určuje, že upozornění 42024 by mělo být považováno za chybu.|
|`vbc /warnaserror:42024,42025`|Určuje, že varování 42024 a 42025 by měly být považovány za chyby.|
|`vbc /nowarn`|Určuje, že by měla být hlášena žádná upozornění.|
|`vbc /nowarn:42024`|Určuje, že upozornění 42024 by nemělo být hlášeno.|
|`vbc /nowarn:42024,42025`|Určuje, že upozornění 42024 a 42025 by neměly být hlášeny.|

## <a name="types-of-warnings"></a>Typy varování
Následuje seznam upozornění, která můžete chtít považovat za chyby.

### <a name="implicit-conversion-warning"></a>Upozornění na implicitní převod
Generováno pro instance implicitnípřevod. Nezahrnují implicitní převody z vnitřního číselného typu na `&` řetězec při použití operátoru. Výchozí nastavení pro nové projekty je vypnuto.

ID: 42016

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Upozornění na vyvolání pozdní vázané metody a rozlišení přetížení
Generováno pro instance pozdní vazby. Výchozí nastavení pro nové projekty je vypnuto.

ID: 42017

### <a name="operands-of-type-object-warnings"></a>Operandy typu "Objekt" upozornění
Generováno při operandech `Object` typu, které by vytvořily chybu s **možností Strict On**. Výchozí nastavení pro nové projekty je zapnuto.

ID: 42018 a 42019

### <a name="declarations-require-as-clause-warnings"></a>Prohlášení vyžadují varování doložky "As"
Generováno, pokud by deklarace proměnné, `As` funkce nebo vlastnosti bez klauzule vytvořila chybu s **možností Strict On**. Proměnné, které nemají přiřazený typ, se považují `Object`za typ . Výchozí nastavení pro nové projekty je zapnuto.

ID: 42020 (deklarace proměnné), 42021 (deklarace funkce) a 42022 (prohlášení o vlastnostech).

### <a name="possible-null-reference-exception-warnings"></a>Možná upozornění na výjimku nulového odkazu
Generováno při použití proměnné před tím, než jí byla přiřazena hodnota. Výchozí nastavení pro nové projekty je zapnuto.

ID: 42104, 42030

### <a name="unused-local-variable-warning"></a>Upozornění na nepoužitou místní proměnnou
Generováno při deklarování místní proměnné, ale nikdy odkazovat. Výchozí nastavení je zapnuto.

ID: 42024

### <a name="access-of-shared-member-through-instance-variable-warning"></a>Přístup sdíleného člena prostřednictvím upozornění proměnné instance
Generováno při přístupu ke sdílenému členu prostřednictvím instance může mít vedlejší účinky nebo při přístupu ke sdílenému členu prostřednictvím proměnné instance není pravá strana výrazu nebo je předávána jako parametr. Výchozí nastavení pro nové projekty je zapnuto.

ID: 42025

### <a name="recursive-operator-or-property-access-warnings"></a>Upozornění na rekurzivní operátor nebo přístup k vlastnostem
Generováno, když tělo rutiny používá stejný operátor nebo vlastnost, ve které je definována. Výchozí nastavení pro nové projekty je zapnuto.

ID: 42004 (operátor), 42026 (vlastnost)

### <a name="function-or-operator-without-return-value-warning"></a>Funkce nebo operátor bez upozornění na vrácenou hodnotu
Generováno, pokud funkce nebo operátor nemá zadanou vrácenou hodnotu. To zahrnuje vynechání `Set` a implicitní místní proměnné se stejným názvem jako funkce. Výchozí nastavení pro nové projekty je zapnuto.

ID: 42105 (funkce), 42016 (operátor)

### <a name="overloads-modifier-used-in-a-module-warning"></a>Modifikátor přetížení použitý v upozornění modulu
Generováno `Overloads` při použití `Module`v . Výchozí nastavení pro nové projekty je zapnuto.

ID: 42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Duplicitní nebo překrývající se upozornění bloků catch
Generováno, `Catch` když je nikdy dosaženo bloku `Catch` z důvodu jeho vztahu k jiným blokům, které byly definovány. Výchozí nastavení pro nové projekty je zapnuto.

ID: 42029, 42031

## <a name="see-also"></a>Viz také

- [Typy chyb](/dotnet/visual-basic/programming-guide/language-features/error-types)
- [Zkuste... Chytit... Prohlášení s konečnou snesení](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)
- [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)
- [/warnasError (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)
- [Stránka kompilace, Návrhář projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](/cpp/preprocessor/compiler-warnings-that-are-off-by-default)
