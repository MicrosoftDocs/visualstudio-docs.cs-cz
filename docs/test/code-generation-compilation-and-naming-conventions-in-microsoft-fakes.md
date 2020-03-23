---
title: 'Microsoft Fakes: Generovat & kompilační kód; Konvence'
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 155caf50e82f56c1db0b0b0a65a640f252f44063
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589328"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Vytváření, kompilace a konvence pojmenování kódu v Napodobeniny Microsoft

Tento článek popisuje možnosti a problémy v generování a kompilaci kódu Fakes a popisuje konvence pojmenování pro falešné generované typy, členy a parametry.

**Požadavky**

- Visual Studio Enterprise
- Projekt rozhraní .NET Framework

> [!NOTE]
> Standardní projekty .NET nejsou podporovány.

## <a name="code-generation-and-compilation"></a>Generování kódu a kompilace

### <a name="configure-code-generation-of-stubs"></a>Konfigurace generování kódu zástupných procedur

Generování typů se zakázaným inzerováním je konfigurováno v souboru XML, který má příponu *.fakes.* Rozhraní Fakes se integruje do procesu sestavení prostřednictvím vlastních úloh MSBuild a detekuje tyto soubory v době sestavení. Generátor kódu Fakes zkompiluje typy se zakázaným inzerováním do sestavení a přidá odkaz na projekt.

Následující příklad ilustruje typy se zakázaným inzerováním definované v *souboru FileSystem.dll*:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>
```

### <a name="type-filtering"></a>Filtrování typů

Filtry lze nastavit v souboru *.fakes* omezit typy, které by měly být se zakázaným inzerováním. Můžete přidat neomezený počet Clear, Přidat, Odebrat prvky pod StubGeneration element k sestavení seznamu vybraných typů.

Například následující soubor *.fakes* generuje zástupné procedury pro typy v rámci systémových a System.IO oborech názvů, ale vylučuje jakýkoli typ obsahující "Handle" v systému:

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

Řetězce filtrů používají jednoduchou gramatiku k definování způsobu, jakým má být párování provedeno:

- Filtry ve výchozím nastavení nerelimují malá a velká písmena. filtry provádějí párování podřetězců:

     `el`odpovídá "ahoj"

- Přidání `!` na konec filtru z něj činí přesnou shodu rozlišující malá a velká písmena:

     `el!`neodpovídá "ahoj"

     `hello!`odpovídá "ahoj"

- Přidání `*` na konec filtru způsobí, že bude odpovídat předponě řetězce:

     `el*`neodpovídá "ahoj"

     `he*`odpovídá "ahoj"

- Více filtrů v seznamu odděleném středníkem je kombinováno jako disjunkce:

     `el;wo`odpovídá "ahoj" a "svět"

### <a name="stub-concrete-classes-and-virtual-methods"></a>Třídy betonu se zakázaným inzerováním a virtuální metody

Ve výchozím nastavení jsou pro všechny nezapečetěné třídy generovány typy se zakázaným inzerováním. Je možné omezit typy se zakázaným inzerováním na abstraktní třídy prostřednictvím konfiguračního souboru *.fakes:*

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

Generátor kódu Fakes generuje typy překrytí a typy se zakázaným inzerováním pro typy, které jsou viditelné pro generované sestavení Fakes. Chcete-li, aby vnitřní typy shimmed sestavení viditelné Fakes a testovací sestavení, přidejte <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributy shimmed kód sestavení, který poskytuje viditelnost generované fakes sestavení a testovací sestavení. Tady je příklad:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

**Interní typy v silně pojmenovaných sestaveních**

Pokud je shimmed sestava silně pojmenována a chcete získat přístup k interním typům sestavení:

- Sestavení testu i sestavení Fakes musí být silně pojmenovány.

- Přidejte veřejné klíče sestavení test a Fakes do **atributů InternalsVisibleToAttribute** v shimmed sestaveních. Tady je, jak by vypadaly atributy v kódu shimmed assembly, když je sestavení shimmed silně pojmenováno:

    ```csharp
    // FileSystem\AssemblyInfo.cs
    [assembly: InternalsVisibleTo("FileSystem.Fakes",
        PublicKey=<Fakes_assembly_public_key>)]
    [assembly: InternalsVisibleTo("FileSystem.Tests",
        PublicKey=<Test_assembly_public_key>)]
    ```

Pokud je shimmed sestavení silně pojmenováno, rozhraní Fakes automaticky silně podepisuje generované sestavení Fakes. Musíte silně podepsat testovací sestavení. Viz [Sestavení se silným názvem](/dotnet/framework/app-domains/strong-named-assemblies).

Rozhraní Fakes používá stejný klíč k podepsání všech generovaných sestavení, takže tento úryvek můžete použít jako výchozí bod pro přidání atributu **InternalsVisibleTo** pro sestavení fakes do kódu sestavení shimmed.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

Můžete zadat jiný veřejný klíč pro sestavení Fakes, například klíč, který jste vytvořili pro shimmed sestavení, zadáním úplné cesty `KeyFile` k souboru `Fakes` \\ `Compilation` *.snk,* který obsahuje alternativní klíč jako hodnotu atributu v elementu *.fakes* souboru. Například:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>
```

Potom budete muset použít veřejný klíč alternativní *souboru .snk* jako druhý parametr InternalVisibleTo atribut pro fakes sestavení v shimmed kódu sestavení:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

Ve výše uvedeném `Alternate_public_key` příkladu `Test_assembly_public_key` mohou být hodnoty a hodnoty stejné.

### <a name="optimize-build-times"></a>Optimalizace doby sestavení

Kompilace sestavení Fakes může výrazně prodloužit dobu sestavení. Můžete minimalizovat čas sestavení generováním fakes sestavení pro sestavení systému .NET a sestavení třetích stran v samostatném centralizovaném projektu. Vzhledem k tomu, že tato sestavení se v počítači mění jen zřídka, můžete znovu použít generované sestavení Fakes v jiných projektech.

Z projektů testování částí přidejte odkaz na kompilovaná sestavení Fakes, která jsou umístěna pod fakesassemblies ve složce projektu.

1. Vytvořte novou knihovnu tříd s verzí běhu .NET odpovídající testovacím projektům. Nazvěme to Fakes.Prebuild. Odeberte *soubor class1.cs* z projektu, není potřeba.

2. Přidejte odkaz na všechna systémová sestavení a sestavení třetích stran, pro která potřebujete padělky.

3. Přidejte soubor *.fakes* pro každé sestavení a sestavení.

4. Z testovacího projektu

    - Ujistěte se, že máte odkaz na dll runtime Fakes:

         *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll*

    - Pro každé sestavení, pro které jste vytvořili fakes, přidejte odkaz na odpovídající soubor DLL ve složce *Fakes.Prebuild\FakesAssemblies* projektu.

### <a name="avoid-assembly-name-clashing"></a>Vyhněte se kolizím názvů sestavení

V prostředí team buildu jsou všechny výstupy sestavení sloučeny do jednoho adresáře. Pokud více projektů používá fakes, může se stát, že fakes sestavení z různých verzí přepsat navzájem. Například TestProject1 fakes *mscorlib.dll* z rozhraní .NET Framework 2.0 a TestProject2 fakes *mscorlib.dll* pro rozhraní .NET Framework 4 by oba výnos *mscorlib. Fakes.dll* Fakes shromáždění.

Chcete-li se tomuto problému vyhnout, fakes by měl automaticky vytvořit verze kvalifikované Fakes názvy sestavení pro non-projekt odkazy při přidávání *.fakes* soubory. Název sestavení Fakes s kvalifikací verze vloží číslo verze při vytváření názvu sestavení Fakes:

Vzhledem k sestavení MyAssembly a verze 1.2.3.4, fakes název sestavení je MyAssembly.1.2.3.4.Fakes.

Tuto verzi můžete změnit nebo odebrat úpravou atributu Version elementu Assembly v *.fakes*:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>
```

## <a name="fakes-naming-conventions"></a>Falešné konvence pojmenování

### <a name="shim-type-and-stub-type-naming-conventions"></a>Konvencí pojmenování typu překrytí a se zakázaným inzerováním

**Obory názvů**

- . Do oboru názvů je přidána přípona fakes.

   Obor `System.Fakes` názvů například obsahuje překrytí typů systémového oboru názvů.

- Global.Fakes obsahuje překrytí typu prázdného oboru názvů.

  **Názvy typů**

- Předpona překrytí je přidána k názvu typu k vytvoření názvu typu překrytí.

   Například ShimExample je překrytí typu Příklad typu.

- Předpona se zakázaným inzerováním je přidána k názvu typu pro sestavení názvu typu se zakázaným inzerováním.

   Například StubIExample je typ se zakázaným inzerováním typu IExample.

  **Zadejte argumenty a vnořené struktury typů**

- Argumenty obecného typu jsou zkopírovány.

- Vnořená struktura typu je zkopírována pro typy překrytí.

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a>Překrytí vlastností delegáta nebo konvencí pojmenování polí delegáta se zakázaným inzerováním

**Základní pravidla** pro pojmenování polí, počínaje prázdným názvem:

- Název metody je připojen.

- Pokud název metody je explicitní implementace rozhraní, jsou odebrány tečky.

- Pokud je metoda `Of`obecná, *n* je připojen, kde *n* je počet argumentů obecné metody.

  **Názvy speciálních metod,** jako je například vlastnost getter nebo setters jsou považovány za popsané v následující tabulce:

|Pokud je metoda...|Příklad|Připojený název metody|
|-|-|-|
|**Konstruktor**|`.ctor`|`Constructor`|
|Statický **konstruktor**|`.cctor`|`StaticConstructor`|
|**Přistupující objekt** s názvem metody složený ze dvou částí oddělených "_" (například vlastnost getters)|*kind_name* (běžný případ, ale nevymáhaný ECMA)|*NameKind*, kde obě části byly velkými písmeny a vyměnit|
||Getter majetku`Prop`|`PropGet`|
||Seřizovač majetku`Prop`|`PropSet`|
||Zmije událostí|`Add`|
||Odstraňovač událostí|`Remove`|
|**Obsluha** složená ze dvou částí|`op_name`|`NameOp`|
|Například: + operátor|`op_Add`|`AddOp`|
|Pro **operátor převodu**je připojen návratový typ.|`T op_Implicit`|`ImplicitOpT`|

> [!NOTE]
> - **Getters a settery indexery** jsou zpracovány podobně jako vlastnost. Výchozí název indexeru `Item`je .
> - **Názvy typů parametrů** jsou transformovány a zřetězené.
> - **Návratový typ** je ignorován, pokud není přetížení nejednoznačnosti. Pokud je přetížení amiguity, návratový typ je připojen na konci názvu.

### <a name="parameter-type-naming-conventions"></a>Konvence pojmenování typu parametru

|Vzhledem k tomu,|Připojený řetězec je...|
|-|-|
|**Typ**`T`|T<br /><br /> Obor názvů, vnořená struktura a obecné tiky jsou vynechány.|
|**Out parametr**`out T`|`TOut`|
|**Parametr ref**`ref T`|`TRef`|
|**Typ pole**`T[]`|`TArray`|
|**Vícerozměrný** typ pole`T[ , , ]`|`T3`|
|Typ **ukazatele**`T*`|`TPtr`|
|**Obecný typ**`T<R1, ...>`|`TOfR1`|
|**Obecný argument** `!i` typu`C<TType>`|`Ti`|
|Obecný **argument metody** `!!i``M<MMethod>`|`Mi`|
|**Vnořený typ**`N.T`|`N`je připojen, pak`T`|

### <a name="recursive-rules"></a>Rekurzivní pravidla

Následující pravidla se používají rekurzivně:

- Vzhledem k tomu, že Fakes používá C# ke generování sestavení Fakes, jakýkoli znak, který by vytvořil neplatný token jazyka C#, je uvozen na "_" (podtržítko).

- Pokud výsledný název kojí s libovolným členem deklarujícího typu, schéma číslování se používá připojením dvoumístného čítače začínajícího na 01.

## <a name="see-also"></a>Viz také

- [Izolace testovaného kódu pomocí microsoft fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
