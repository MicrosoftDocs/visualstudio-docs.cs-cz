---
title: Konvence vytváření názvů .NET pro soubory EditorConfig
ms.date: 08/07/2019
ms.topic: reference
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 644c73dea58936773acde98ccc535dfc61979288
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251692"
---
# <a name="net-naming-conventions-for-editorconfig"></a>Konvence vytváření názvů .NET pro EditorConfig

Konvence pojmenování se týkají názvů prvků kódu, jako jsou třídy, vlastnosti a metody. Například můžete určit, že veřejné členy musí být velkými písmeny nebo že asynchronní metody musí končit "Async". Tato pravidla můžete vyhovět zadáním v [souboru. editorconfig](../ide/create-portable-custom-editor-options.md). Porušení pravidel pojmenování se zobrazují buď v **Seznam chyb** , nebo jako návrh pod názvem, v závislosti na závažnosti, kterou zvolíte pro pravidlo. Není nutné sestavovat projekt, aby bylo možné zobrazit porušení.

Pro každou konvenci pojmenování musíte zadat symboly, na které se vztahuje, styl pojmenování a závažnost pro vynucování konvence, a to pomocí vlastností popsaných níže. Pořadí vlastností není důležité.

Začněte tím, že zvolíte název pravidla pro pojmenování, které použijete v každé vlastnosti, které jsou potřeba k úplnému popisu pravidla. Například `public_members_must_be_capitalized` je dobrý popisný název pravidla pojmenování. Tato stránka bude odkazovat na název, který jste zvolili jako **< namingRuleTitle\>**  v následujících oddílech.

## <a name="symbols"></a>Symboly

Nejprve Identifikujte skupinu symbolů, na které se má pravidlo pojmenování použít. Tato vlastnost má následující formát:

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

Zadejte název skupiny symbolů tak, že nahradíte hodnotu **< symbolTitle\>**  s popisným `public_symbols`názvem, například. Hodnotu **< symbolTitle\>**  použijete ve třech názvech vlastností, které popisují, na které symboly se pravidlo aplikuje (typy symbolů, úrovně přístupnosti a modifikátory).

### <a name="kinds-of-symbols"></a>Druhy symbolů

Chcete-li popsat druh symbolů pro použití pravidla pojmenování, určete vlastnost v následujícím formátu:

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

V následujícím seznamu jsou uvedeny možné hodnoty a můžete zadat více hodnot tak, že je oddělíte čárkami.

- \*(tuto hodnotu použijte k určení všech symbolů.)
- – obor názvů
- třída
- struct
- rozhraní
- enum
- property
- – metoda
- pole
- event
- delegát
- parametr
- type_parameter
- local
- local_function

### <a name="accessibility-levels-of-symbols"></a>Úrovně přístupnosti symbolů

Chcete-li popsat úrovně přístupnosti symbolů, na které má pravidlo pojmenování platit, zadejte název vlastnosti v následujícím formátu:

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

V následujícím seznamu jsou uvedeny možné hodnoty a můžete zadat více hodnot tak, že je oddělíte čárkami.

- \*(tuto hodnotu použijte k určení všech úrovní přístupnosti)
- public
- interní nebo přítel
- private
- protected
- chráněná\_interní nebo protected_friend
- soukromé\_chráněné
- local

   Úroveň `local` přístupnosti se vztahuje na symboly definované v rámci metody. Je užitečné pro definování konvencí pojmenování pro symboly, jejichž přístupnost nejde zadat v kódu. Například pokud zadáte `applicable_accessibilities = local` v konvenci pojmenování konstant (`required_modifiers = const`), pravidlo se vztahuje pouze na konstanty definované v rámci metody a nikoli na ty, které jsou definovány v typu.

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

### <a name="symbol-modifiers-optional"></a>Modifikátory symbolů (nepovinné)

Chcete-li popsat modifikátory symbolů, na které má pravidlo pojmenování platit, zadejte název vlastnosti v následujícím formátu:

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

V následujícím seznamu jsou uvedeny povolené hodnoty (oddělené více hodnot čárkami):

- `abstract` Nebo `must_inherit`
- `async`
- `const`
- `readonly`
- `static` Nebo `shared`

   > [!NOTE]
   > Pokud máte pravidlo pojmenování pro `static` nebo `shared` symboly, použije se také na `const` symboly, protože jsou implicitně statické. Pokud nechcete `static` , aby pravidlo pro pojmenování `const` pro symboly bylo použito, vytvořte pro `const` symboly samostatné pravidlo pojmenování.

Pravidlo pojmenování odpovídá podpisům, které mají *všechny* modifikátory `required_modifiers`určené v. Pokud tuto vlastnost vynecháte, použije se výchozí hodnota prázdného seznamu, to znamená, že pro shodu nejsou vyžadovány žádné konkrétní modifikátory. To znamená, že modifikátory symbolu nemají žádný vliv na to, zda je toto pravidlo použito nebo ne.

> [!TIP]
> Nezadávejte hodnotu `*` pro `required_modifiers`. Místo toho stačí zcela vynechat `required_modifiers` vlastnost a vaše pravidlo pojmenování bude platit pro libovolný druh modifikátoru.

## <a name="style"></a>Styl

Teď, když jste identifikovali skupinu symbolů pro použití pravidla pojmenování, můžete popsat styl pojmenování. Styl může být, že název má určitou předponu nebo určitou příponu nebo že jednotlivá slova v názvu jsou oddělená určitým znakem. Můžete také zadat styl velkých a malých písmen. Vlastnost Style má následující formát:

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

Zadejte název Style tak, že nahradíte hodnotu **<\> styleTitle** s popisným `first_word_upper_case_style`názvem, například. Hodnotu **< styleTitle\>**  použijete v názvech vlastností, které popisují styl pojmenování (předpona, přípona, znak oddělovače slov a velká písmena). Pomocí jedné nebo více z těchto vlastností popište svůj styl.

### <a name="require-a-prefix"></a>Vyžadovat předponu

Chcete-li určit, že názvy symbolů musí začínat určitými znaky, použijte tuto vlastnost:

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>Vyžadovat příponu

Chcete-li určit, že názvy symbolů musí končit určitými znaky, použijte tuto vlastnost:

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>Vyžadovat určitý oddělovač slov

Chcete-li určit, že jednotlivá slova v názvech symbolů musí být oddělena určitým znakem, použijte tuto vlastnost:

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>Vyžadovat styl psaní velkých písmen

Pro určení konkrétního stylu velkých a malých písmen pro názvy symbolů použijte tuto vlastnost:

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

Povolené hodnoty pro tuto vlastnost jsou:

- pascal_case
- camel_case
- první\_word_upper
- všechna\_Velká
- all_lower

> [!NOTE]
> Jako součást stylu pojmenování musíte zadat styl s velkými písmeny, jinak se styl pojmenování může ignorovat.

## <a name="severity"></a>severity

Chcete-li popsat závažnost porušení pravidla pojmenování, určete vlastnost v následujícím formátu:

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

Následující tabulka uvádí povolené hodnoty závažnosti a jejich význam:

severity | Efekt
------------ | -------------
žádná | Pravidlo je zcela potlačené.
refaktoring nebo tichá | Pokud se tento styl nesleduje, nezobrazujte na uživateli žádné údaje. Nicméně automaticky generovaný kód se řídí tímto stylem.
návrhů | Pokud se tento styl nesleduje, zobrazte ho uživateli jako návrh, jako základní tečky na prvních dvou znacích. Nemá žádný vliv na čas kompilace.
upozornění | Pokud se tento styl nesleduje, zobrazte v **Seznam chyb**upozornění kompilátoru.
error | Pokud se tento styl nesleduje, zobrazte v **Seznam chyb**chybu kompilátoru.

> [!NOTE]
> Nemusíte sestavovat projekt, aby bylo možné zobrazit porušení pravidel pojmenování. Zobrazí se jako upravený kód, a to buď v **Seznam chyb** , nebo jako návrh.

## <a name="rule-order"></a>Pořadí pravidel

::: moniker range="vs-2017"

Konvence pojmenování by se měly seřadit od nejvíce specifických po nejméně specifické v souboru EditorConfig. První pravidlo, které se dá použít, je jediné použité pravidlo. Pokud však existuje více *vlastností* pravidla se stejným názvem, má přednost vlastnost naposledy Nalezeno s tímto názvem. Další informace najdete v tématu [hierarchie souborů a Priorita](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

::: moniker range=">=vs-2019"

Počínaje verzí Visual Studio 2019 verze 16,2 je pořadí, ve kterém jsou pravidla pro pojmenování definována v souboru EditorConfig, nezáleží. Místo toho Visual Studio řadí pravidla pojmenování automaticky podle definice samotných pravidel. [Rozšíření služby EditorConfig Language](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) může analyzovat soubory EditorConfig a sestavy, kde pořadí pravidel v souboru se liší od toho, co kompilátor použije za běhu.

Pokud používáte starší verzi sady Visual Studio, zásady vytváření názvů by se měly seřadit od nejvíce specifických po nejméně specifické v souboru EditorConfig. První pravidlo, které se dá použít, je jediné použité pravidlo. Pokud však existuje více *vlastností* pravidla se stejným názvem, má přednost vlastnost naposledy Nalezeno s tímto názvem. Další informace najdete v tématu [hierarchie souborů a Priorita](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

## <a name="default-naming-styles"></a>Výchozí styly názvů

Pokud nezadáte žádná vlastní pravidla pojmenování, Visual Studio použije následující výchozí styly:

- Pro třídy, struktury `public`, výčty, vlastnosti a události s, `private`, `internal` `protected`, nebo `protected_internal` přístupnost je výchozím stylem pojmenování velká písmena jazyka Pascal.

- Pro rozhraní s `public`, `private`, `internal` ,`protected` nebo`protected_internal` přístupnost je výchozím stylem pojmenování znak písma Pascal s požadovanou předponou **I**.

## <a name="example"></a>Příklad

Následující soubor *. editorconfig* obsahuje zásady vytváření názvů, které určují, že veřejné vlastnosti, metody, pole, události a Delegáti musí být velkými písmeny. Všimněte si, že tato konvence vytváření názvů určuje více druhů symbolů pro použití pravidla, a to pomocí čárky pro oddělení hodnot.

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

Následující snímek obrazovky ukazuje účinek této zásady vytváření názvů v editoru. Dvě veřejné proměnné byly pojmenovány bez velkých písmen prvního písmene. Jedna je `const`a `readonly`jedna z nich. Vzhledem k tomu, že pravidlo pojmenování platí jenom `readonly` pro `readonly` symboly, zobrazuje se návrh pravidla pojmenování jenom v této proměnné.

![Návrh pravidla pojmenování](media/editorconfig-naming-rule-suggestion.png)

Teď změníte závažnost narušení na `warning`:

```ini
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

Pokud soubor kódu zavřete a znovu otevřete, místo zobrazení návrhu pod porušením názvu se zobrazí zelená vlnovka a upozornění v **Seznam chyb**:

![Upozornění pravidla pojmenování](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>Viz také:

- [Jazykové konvence](editorconfig-language-conventions.md)
- [Konvence formátování](editorconfig-formatting-conventions.md)
- [Roslyn zásady vytváření názvů](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [Vytvoření možností přenosného vlastního editoru](../ide/create-portable-custom-editor-options.md)
- [EditorConfig nastavení konvence psaní kódu .NET](editorconfig-code-style-settings-reference.md)
