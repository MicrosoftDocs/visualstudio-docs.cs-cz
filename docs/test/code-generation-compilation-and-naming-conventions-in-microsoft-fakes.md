---
title: Vytváření, kompilace a konvence pojmenování kódu v Napodobeniny Microsoft
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 7af8fc49896549fd553c8262b04e9d02f76f06e9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058308"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Vytváření, kompilace a konvence pojmenování kódu v Napodobeniny Microsoft

Tento článek popisuje možnosti a problémy v generování kódu rozhraní Fakes a kompilace a popisuje konvence pro falešných generovaných typů, členů a parametrů.

**Požadavky**

-   Visual Studio Enterprise
-   Rozhraní .NET Framework projektu

> [!NOTE]
> Projekty .NET standard teď nejsou podporovány.

## <a name="code-generation-and-compilation"></a>Vytváření a kompilování kódu

### <a name="configure-code-generation-of-stubs"></a>Konfigurace generování provizorního kódu

Generování provizorních typů je nakonfigurovaný v souboru XML, který má *.fakes* příponu souboru. Rámec falešného kódu integruje do procesu sestavení prostřednictvím úkolů MSBuild a tyto soubory detekuje během sestavení. Generátor falešného kódu kompiluje provizorní typy do sestavení a přidá odkaz na projekt.

Následující příklad ilustruje provizorní typy definované v *knihovně FileSystem.dll*:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>
```

### <a name="type-filtering"></a>Filtrování podle typu

Filtry je možné nastavit v *.fakes* soubor omezit typy, které by měla být prázdná. Můžete přidat množství vymazat, přidat a odebrat elementy v prvku StubGeneration pro sestavení seznamu vybraných typů.

Například následující *.fakes* soubor generuje provizorní kód pro typy v oborech názvů System a System.IO, ale vynechá jakýkoli typ obsahující "Handle" v systému:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Clear />
    <Add Namespace="System!" />
    <Add Namespace="System.IO!"/>
    <Remove TypeName="Handle" />
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

Řetězce filtru používají k definování, jak odpovídající by mělo být provedeno jednoduchou gramatiku:

-   Filtry jsou malá a velká písmena ve výchozím nastavení; filtry provádějí porovnání podřetězců:

     `el` odpovídá "hello"

-   Přidání `!` na konec filtrovacího umožňuje přesnou shodu malá a velká písmena:

     `el!` neodpovídá "hello"

     `hello!` odpovídá "hello"

-   Přidání `*` na konec filtrovacího umožňuje porovnání předpony řetězce:

     `el*` neodpovídá "hello"

     `he*` odpovídá "hello"

-   Několik filtrů ve středníkem oddělený seznam zkombinují je vyhodnoceno jako disjunkce:

     `el;wo` odpovídá "hello" a "world"

### <a name="stub-concrete-classes-and-virtual-methods"></a>Zástupná procedura konkrétních tříd a virtuálních metod

Ve výchozím nastavení jsou zástupné typy generovány pro všechny nezapečetěné třídy. Je možné omezit typy zástupných procedur na abstraktní třídy prostřednictvím *.fakes* konfiguračního souboru:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Types>
      <Clear />
      <Add AbstractClasses="true"/>
    </Types>
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

### <a name="internal-types"></a>Vnitřní typy

Generátor falešného kódu generuje typy překrytí a zástupných procedur typy, které jsou pro falešné sestavení viditelné. Chcete-li zviditelnit vnitřní typy překrytého sestavení pro falešné a testovací sestavení, přidejte <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributy do kódu překrytého sestavení, které dává viditelnost generovanému falešnému sestavení a testovacímu sestavení. Tady je příklad:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

 **Vnitřní typy v sestaveních se silným názvem**

 Pokud je překryté sestavení pojmenováno silně a chcete získat přístup k vnitřním typům sestavení:

-   Zkušební sestava i falešné sestavení musí mít silný název.

-   Přidání veřejné klíče testu a sestavení Fakes **InternalsVisibleToAttribute** atributy v překrytých sestaveních. Zde je, jak by vypadal příklad atributů v kódu překrytého sestavení, pokud je překryté sestavení pojmenováno silně:

    ```csharp
    // FileSystem\AssemblyInfo.cs
    [assembly: InternalsVisibleTo("FileSystem.Fakes",
        PublicKey=<Fakes_assembly_public_key>)]
    [assembly: InternalsVisibleTo("FileSystem.Tests",
        PublicKey=<Test_assembly_public_key>)]
    ```

Pokud je překryté sestavení pojmenováno silně, rámec falešného kódu automaticky silně podepíše vygenerované falešné sestavení. Můžete nastavit silný podpis testovacího sestavení. Zobrazit [sestavení se silným názvem](/dotnet/framework/app-domains/strong-named-assemblies).

Rámec falešného kódu používá stejný klíč k podepsání všech generovaných sestavení, takže tento fragment kódu můžete použít jako výchozí bod přidat **InternalsVisibleTo** atribut pro falešné sestavení pro váš překrytý kód sestavení.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

Můžete zadat jiný veřejný klíč pro sestavení Fakes, například klíč jste vytvořili pro překryté sestavení, zadáním úplné cesty k *.snk* soubor, který obsahuje alternativní klíč jako `KeyFile` hodnotu v atributu `Fakes` \\ `Compilation` elementu *.fakes* souboru. Příklad:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>
```

Potom je nutné použít veřejný klíč náhradního *.snk* soubor jako druhý parametr atributu InternalVisibleTo pro sestavení Fakes v kódu překrytého sestavení:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

V příkladu výše hodnoty `Alternate_public_key` a `Test_assembly_public_key` může být stejný.

### <a name="optimize-build-times"></a>Optimalizace doby sestavení

Kompilace falešných sestavení může podstatně prodloužit dobu sestavení. Dobu sestavení lze minimalizovat generováním falešných sestavení pro systémová sestavení technologie .NET a sestavení třetích stran v odděleném centralizovaném projektu. Protože tato sestavení se jen zřídka mění na svém počítači, můžete využít tyto vygenerované napodobeniny sestavení v jiných projektech.

V projektech jednotkových testů přidejte odkaz na kompilovaná falešná sestavení, které jsou umístěné v části fakesassemblies adresáře ve složce projektu.

1.  Vytvořte novou knihovnu tříd s verzí modulu runtime .NET odpovídající testovacímu projektu. Nazvěte ji třeba Fakes.Prebuild. Odeberte *class1.cs* soubor z projektu, není potřeba.

2.  Přidáte odkaz na všechna systémová sestavení a sestavení třetích stran, které potřebujete napodobeniny.

3.  Přidat *.fakes* soubor pro každé sestavení a sestavení.

4.  Z testovacího projektu

    -   Ujistěte se, že budete mít odkaz na napodobeninu knihovny runtime DLL:

         *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll*

    -   Pro každé sestavení, kterou jste vytvořili falešné sestavení, přidejte odkaz na odpovídající soubor knihovny DLL v *fakes.prebuild\fakesassemblies k* složky vašeho projektu.

### <a name="avoid-assembly-name-clashing"></a>Vyhněte se kolidující název sestavení

V prostředí Team Build jsou všechna výstupní sestavení sloučena do jednoho adresáře. Pokud více projektů použít produkt Fakes, může se stát, že sestavení napodobenin z různých verzí navzájem přepisují. Například projekt testproject1 vyžaduje napodobeninu *mscorlib.dll* z rozhraní .NET Framework 2.0 a projekt testproject2 vyžaduje fakes *mscorlib.dll* pro rozhraní .NET Framework 4 mscorlib.fakes.dll k *mscorlib. Fakes.dll* napodobeniny sestavení.

 K tomuto problému vyhnout, napodobeniny automaticky vytvořila verze kvalifikovaný pro reference mimo projekt názvy falešných sestavení při přidávání *.fakes* soubory. Verze kvalifikovaný název sestavení napodobenin vloží číslo verze, když vytváříte název sestavení napodobenin:

 Název sestavení napodobenin zadaný pro sestavení MyAssembly a verzi 1.2.3.4 nazývat MyAssembly.1.2.3.4.Fakes.

 Můžete změnit nebo odebrat tak, že upravíte atribut Version prvku Assembly v této verzi *.fakes*:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>
```

## <a name="fakes-naming-conventions"></a>Konvence pojmenovávání napodobenin

### <a name="shim-type-and-stub-type-naming-conventions"></a>Překrývajících a provizorních zadejte zásady vytváření názvů

 **Obory názvů**

- . Napodobeniny přípona se přidá do oboru názvů.

   Například `System.Fakes` obor názvů obsahuje typy překrytí oboru názvu System.

- Soubor Global.Fakes obsahuje překrývající typ prázdného oboru názvů.

  **Názvy typů**

- Je název typu k vytvoření názvu překrývajícího typu přidána předpona Shim.

   Například typ ShimExample je překrývající typ typu Example.

- Je název typu pro vytvoření názvu provizorního typu přidána předpona stub.

   Například typ StubIExample je provizorním typem typu IExample.

  **Argumenty typů a vnořené struktury typů**

- Argumenty obecného typu jsou zkopírovány.

- Vnořené struktury typů zkopírovány pro typy překrytí.

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a>Vlastností překrývajícího delegáta se zakázaným inzerováním delegáta zásady vytváření názvů polí

**Základní pravidla** pro pojmenovávání polí, počínaje prázdným názvem:

- Je připojen název metody.

- Pokud je název metody explicitní implementací rozhraní, jsou odstraněny tečky.

- Pokud metody je obecný, `Of` *n* připojen kde *n* je počet argumentů obecné metodě.

  **Názvy speciálních metod** jako je například vlastnost getter nebo setter zacházeno podle popisu v následující tabulce:

|Pokud je metoda...|Příklad|Připojený název metody|
|-|-|-|
|A **konstruktor**|`.ctor`|`Constructor`|
|Statický **konstruktor**|`.cctor`|`StaticConstructor`|
|**Přistupující objekt** metodou název se skládá ze dvou částí oddělených "_" (například gettery vlastností)|*kind_name* (běžné velikosti písmen, ale nevynucený podle ECMA)|*NameKind*, kde obě části byly velkými písmeny a Prohodit|
||Metoda getter vlastnosti `Prop`|`PropGet`|
||Metoda setter vlastnosti `Prop`|`PropSet`|
||Přidavač událostí|`Add`|
||Odstraňovač událostí|`Remove`|
|**Operátor** skládá ze dvou částí|`op_name`|`NameOp`|
|Například: + – operátor|`op_Add`|`AddOp`|
|Pro **operátor převodu**, návratový typ přidán.|`T op_Implicit`|`ImplicitOpT`|

> [!NOTE]
> - **Gettery a settery indexerů** je zacházeno podobně jako na vlastnost. Výchozí název indexeru je `Item`.
> - **Typ parametru** názvy jsou transformovány a spojeny.
> - **Návratový typ** se ignoruje, pokud existuje existovala dvojznačnost přetížení. Pokud dojde přetížení amiguity, návratový typ je přidáván na konec názvu.

### <a name="parameter-type-naming-conventions"></a>Konvence pojmenovávání parametrických typů

|Zadaný|Připojený řetězec je...|
|-|-|
|A **typu**`T`|T<br /><br /> Obor názvů, vnořené struktury a obecné tiky jsou vynechány.|
|**Výstupní parametr**`out T`|`TOut`|
|A **parametr ref** `ref T`|`TRef`|
|**Typ pole**`T[]`|`TArray`|
|A **vícerozměrné pole** typu `T[ , , ]`|`T3`|
|A **ukazatel** typu `T*`|`TPtr`|
|A **obecného typu**`T<R1, ...>`|`TOfR1`|
|A **argument obecného typu** `!i` typu `C<TType>`|`Ti`|
|A **argument obecné metody** `!!i` metody `M<MMethod>`|`Mi`|
|A **vnořený typ**`N.T`|`N` je připojeno, pak `T`|

### <a name="recursive-rules"></a>Rekurzivní pravidla

Následující pravidla jsou aplikována rekurzivně:

-   Jelikož napodobeniny používají C# ke generování sestavení Fakes, jakýkoli znak, který vyprodukuje neplatný C# token je převeden na "_" (podtržítko).

-   Jestliže výsledný název koliduje se členem deklarovaného typu, se používá schéma číslování přidáním čítač dvěma číslicemi, začínající od 01.

## <a name="see-also"></a>Viz také:

- [Izolace testovaného kódu pomocí Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
