---
title: Konvence pojmenování rozhraní .NET pro soubory EditorConfig
ms.date: 03/31/2020
ms.topic: reference
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4864cc20813bc57b35e315a3b415cb6902e6361
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543994"
---
# <a name="net-naming-conventions-for-editorconfig"></a>Konvence pojmenování rozhraní .NET pro editorConfig

Zásady vytváření názvů se týkají pojmenování prvků kódu, jako jsou třídy, vlastnosti a metody. Můžete například určit, že veřejné členy musí být velkými `_`písmeny nebo že soukromá pole musí začínat . Tato pravidla můžete vynutit zadáním v [souboru .editorconfig](../ide/create-portable-custom-editor-options.md). Porušení pravidel pojmenování se zobrazí buď v **seznamu chyb** nebo jako návrh pod názvem, v závislosti na závažnosti, kterou zvolíte pro pravidlo. Není třeba vytvářet projekt, aby bylo možné zobrazit porušení.

Pro každou konvenci pojmenování je nutné zadat symboly, na které se vztahuje, styl pojmenování a závažnost pro vynucení konvence pomocí vlastností popsaných níže. Pořadí vlastností není důležité.

Chcete-li začít, zvolte název pravidla pojmenování, které budete používat v každé z vlastností, které jsou potřebné k úplnému popisu pravidla. Například `public_members_must_be_capitalized` je dobrý popisný název pravidla pojmenování. Tato stránka bude odkazovat na název, který zvolíte jako **<pojmenováníRuleTitle\> ** v následujících oddílech.

## <a name="symbols"></a>Symboly

Nejprve určete skupinu symbolů, na které chcete použít pravidlo pojmenování. Tato vlastnost má následující formát:

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

Pojmenujte skupinu symbolů nahrazením hodnoty **<symbolTitle\> ** popisným názvem, `public_symbols`například . Hodnotu<**symbolTitle\> ** použijete ve třech názvech vlastností, které popisují, na které symboly je pravidlo použito (druhy symbolů, úrovně usnadnění přístupu a modifikátory).

### <a name="kinds-of-symbols"></a>Druhy symbolů

Chcete-li popsat druh symbolů, na které se má použít pravidlo pojmenování, zadejte vlastnost v následujícím formátu:

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

V následujícím seznamu jsou uvedeny přípustné hodnoty a můžete zadat více hodnot jejich oddělením čárkou.

- \*(Tuto hodnotu použijte k určení všech symbolů)
- namespace
- třída
- struct 
- rozhraní
- enum
- property
- method
- pole
- event
- delegát
- parametr
- type_parameter
- local
- local_function

> [!NOTE] 
> Členové řazené kolekce členů nejsou aktuálně podporovány.

### <a name="accessibility-levels-of-symbols"></a>Úrovně přístupnosti symbolů

Chcete-li popsat úrovně usnadnění symbolů, na které má pravidlo pojmenování platit, zadejte název vlastnosti v následujícím formátu:

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

V následujícím seznamu jsou uvedeny přípustné hodnoty a můžete zadat více hodnot jejich oddělením čárkou.

- \*(tuto hodnotu použijte k určení všech úrovní usnadnění)
- public
- interní nebo přítel
- private
- protected
- chráněné\_vnitřní nebo protected_friend
- privátní\_chráněné
- local

   Úroveň `local` přístupnosti se vztahuje na symboly definované v rámci metody. Je užitečné pro definování konvencí pojmenování pro symboly, jejichž usnadnění přístupu nelze zadat v kódu. Pokud například zadáte `applicable_accessibilities = local` v konvenci`required_modifiers = const`pojmenování konstanty ( ), pravidlo se vztahuje pouze na konstanty definované v rámci metody a nikoli na konstanty definované v typu.

   ```csharp
   class TypeName
   {
     // Constant defined in a type.
     const int X = 3;

     void Method()
     {
       // Constant defined in a method with "local" accessibility.
       const int Y = 4;
     }
   }
   ```

### <a name="symbol-modifiers-optional"></a>Modifikátory symbolů (volitelné)

Chcete-li popsat modifikátory symbolů, na které má pravidlo pojmenování platit, zadejte název vlastnosti v následujícím formátu:

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

V následujícím seznamu jsou uvedeny přípustné hodnoty (oddělte více hodnot čárkou):

- `abstract` nebo `must_inherit`
- `async`
- `const`
- `readonly`
- `static` nebo `shared`

   > [!NOTE]
   > Pokud máte pravidlo pojmenování nebo `static` `shared` symboly, `const` je také použita na symboly, protože jsou implicitně statické. Pokud nechcete, aby `static` se pravidlo `const` pojmenování vztahovalo na `const` symboly, vytvořte samostatné pravidlo pojmenování symbolů.

Pravidlo pojmenování odpovídá podpisům, které mají `required_modifiers` *všechny* modifikátory zadané v . Pokud tuto vlastnost vynechete, použije se výchozí hodnota prázdného seznamu, to znamená, že pro shodu nejsou vyžadovány žádné specifické modifikátory. To znamená, že modifikátory symbolu nemají žádný vliv na to, zda je toto pravidlo použito.

> [!TIP]
> Nezadávejte hodnotu `*` `required_modifiers`pro . Místo toho stačí vynechat `required_modifiers` vlastnost úplně a vaše pravidlo pojmenování se bude vztahovat na jakýkoli druh modifikátoru.

## <a name="style"></a>Styl

Nyní, když jste identifikovali skupinu symbolů, na které chcete použít pravidlo pojmenování, můžete popsat styl pojmenování. Styl může být, že název má určitou předponu nebo určitou příponu nebo že jednotlivá slova v názvu jsou oddělena určitým znakem. Můžete také určit styl velkých písmen. Vlastnost style má následující formát:

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

Pojmenujte styl nahrazením hodnoty **<\> styleTitle** popisným názvem, například `first_word_upper_case_style`. V názvech vlastností, které popisují styl pojmenování (předpona, přípona, znak oddělovač slova a velká písmena), použijete hodnotu **<\> ** styleTitle. K popisu stylu použijte jednu nebo více těchto vlastností.

### <a name="require-a-prefix"></a>Vyžadovat předponu

Chcete-li určit, že názvy symbolů musí začínat určitými znaky, použijte tuto vlastnost:

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>Vyžadovat příponu

Chcete-li určit, že názvy symbolů musí končit určitými znaky, použijte tuto vlastnost:

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>Vyžadovat určitý oddělovač slov

Chcete-li určit, že jednotlivá slova v názvech symbolů musí být oddělena určitým znakem, použijte tuto vlastnost:

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>Vyžadovat styl velkých písmen

Chcete-li určit konkrétní styl velkých písmen pro názvy symbolů, použijte tuto vlastnost:

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

Přípustné hodnoty pro tuto vlastnost jsou:

- pascal_case
- camel_case
- první\_word_upper
- všechny\_horní
- all_lower

> [!NOTE]
> Styl velkých písmen je nutné zadat jako součást stylu pojmenování, jinak může být styl pojmenování ignorován.

## <a name="severity"></a>Severity

Chcete-li popsat závažnost porušení pravidla pojmenování, zadejte vlastnost v následujícím formátu:

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

V následující tabulce jsou uvedeny přípustné hodnoty závažnosti a jejich průměr:

Severity | Účinek
------------ | -------------
Žádná | Pravidlo je zcela potlačeno.
refaktoring nebo tichý | Pokud tento styl není dodržován, nezobrazovat nic uživateli; automaticky generovaný kód však následuje tento styl.
Návrh | Pokud tento styl není dodržován, ukažte uživateli jako návrh jako základní tečky na prvních dvou znacích. Nemá žádný vliv v době kompilace.
upozornění | Pokud tento styl není dodržován, zobrazte upozornění kompilátoru v **seznamu chyb**.
error | Pokud tento styl není dodržen, zobrazte chybu kompilátoru v **seznamu chyb**.

> [!NOTE]
> Není třeba vytvářet projekt, aby bylo možné zobrazit porušení pravidel pojmenování. Zobrazují se jako kód, a to buď v **seznamu chyb,** nebo jako návrh.

## <a name="rule-order"></a>Pořadí pravidel

::: moniker range="vs-2017"

Konvence pojmenování by měly být seřazeny od nejkonkrétnějších až nejméně specifických v souboru EditorConfig. První pravidlo, které lze použít, je jediné pravidlo, které je použito. Pokud však existuje více *vlastností* pravidla se stejným názvem, má přednost naposledy nalezená vlastnost s tímto názvem. Další informace naleznete v [tématu Hierarchie souborů a priorita](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

::: moniker range=">=vs-2019"

Počínaje Visual Studio 2019 verze 16.2, pořadí, ve kterém jsou definována pravidla pojmenování v souboru EditorConfig nezáleží. Místo toho Visual Studio objednávky pravidla pojmenování automaticky podle definice samotných pravidel. [Rozšíření Language Service EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) může analyzovat soubor EditorConfig a sestavy případy, kdy pravidlo řazení v souboru se liší od toho, co kompilátor bude používat za běhu.

Pokud používáte starší verzi sady Visual Studio, konvence pojmenování by měly být seřazeny z nejvíce specifické na nejméně specifické v souboru EditorConfig. První pravidlo, které lze použít, je jediné pravidlo, které je použito. Pokud však existuje více *vlastností* pravidla se stejným názvem, má přednost naposledy nalezená vlastnost s tímto názvem. Další informace naleznete v [tématu Hierarchie souborů a priorita](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

## <a name="default-naming-styles"></a>Výchozí názvové styly

Pokud nezadáte žádná vlastní pravidla pro pojmenování, visual studio použije následující výchozí styly:

- Pro třídy, struktury, výčty, vlastnosti `public`a `private` `internal`události `protected`s `protected_internal` , , , nebo usnadnění přístupu, výchozí styl pojmenování je Pascal případ.

- Pro rozhraní `public`s `private` `internal`, `protected`, `protected_internal` , , nebo usnadnění přístupu je výchozím stylem pojmenování Pascal ův případ s požadovanou předponou **I**.

## <a name="example"></a>Příklad

Následující soubor *.editorconfig* obsahuje konvenci pojmenování, která určuje, že veřejné vlastnosti, metody, pole, události a delegáti musí být velkými písmeny. Všimněte si, že tato konvence pojmenování určuje více druhů symbolů, na které se má pravidlo použít, pomocí čárky k oddělení hodnot.

```ini
# Public members must be capitalized (public_members_must_be_capitalized)
[*.{cs,vb}]
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

Následující snímek obrazovky ukazuje účinek této konvence pojmenování v editoru. Dvě veřejné proměnné byly pojmenovány bez velkých písmen prvního písmene. Jedním z `const`nich je, a jeden je `readonly`. Vzhledem k tomu, `readonly` že pravidlo `readonly` pojmenování se vztahuje pouze na symboly, pouze proměnná zobrazuje návrh pravidla pojmenování.

![Návrh pravidla pojmenování](media/editorconfig-naming-rule-suggestion.png)

Nyní změníme závažnost porušení na `warning`:

```ini
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

Pokud soubor kódu zavřete a znovu otevřete, místo toho, abyste viděli návrh pod porušením názvu, zobrazí se v seznamu chyb zelená vlnovka a upozornění:

![Upozornění na pravidlo pojmenování](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>Viz také

- [Konvence jazyka](editorconfig-language-conventions.md)
- [Konvence formátování](editorconfig-formatting-conventions.md)
- [Roslyn konvence pojmenování](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [Vytvoření možností přenosného vlastního editoru](../ide/create-portable-custom-editor-options.md)
- [Nastavení konvence kódování .NET pro EditorConfig](editorconfig-code-style-settings-reference.md)
