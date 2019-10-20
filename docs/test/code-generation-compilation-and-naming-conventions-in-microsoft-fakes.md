---
title: 'Napodobeniny Microsoftu: generovat & kód kompilace; zásady vytváření názvů'
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: e29b0b05b836dd4072b704bfd48cfb85cde50927
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665252"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Vytváření, kompilace a konvence pojmenování kódu v Napodobeniny Microsoft

Tento článek popisuje možnosti a problémy v případě napodobeniny generování a kompilace kódu a popisuje konvence pojmenování pro falešné generované typy, členy a parametry.

**Požadavky**

- Visual Studio Enterprise
- .NET Framework projekt

> [!NOTE]
> .NET Standard projekty nejsou podporovány.

## <a name="code-generation-and-compilation"></a>Generování a kompilace kódu

### <a name="configure-code-generation-of-stubs"></a>Konfigurace generování kódu pro zástupné procedury

Generování zástupných typů je konfigurováno v souboru XML s příponou *. falešné* soubory. Rozhraní falešného rozhraní je integrováno do procesu sestavení prostřednictvím vlastních úloh nástroje MSBuild a detekuje tyto soubory v čase sestavení. Generátor falešného kódu zkompiluje typy zástupných procedur do sestavení a přidá odkaz na projekt.

Následující příklad znázorňuje typy zástupných procedur definované v souboru *FileSystem. dll*:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>
```

### <a name="type-filtering"></a>Filtrování typů

Filtry lze nastavit v souboru *. napodobeniny* , aby bylo možné omezit, které typy by měly být podložit. Můžete přidat neohraničený počet jasných, Add, Remove Elements pod elementem StubGeneration a sestavit seznam vybraných typů.

Například následující *. falešné* soubory generují zástupné procedury pro typy v oborech názvů system a System.IO, ale vyloučí jakýkoli typ obsahující "Handle" v systému:

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

Řetězce filtru používají jednoduchou gramatiku k definování způsobu, jakým má být provedeno porovnání:

- Ve výchozím nastavení se u filtrů nerozlišují velká a malá písmena. filtry provádějí porovnání podřetězců:

     `el` odpovídá "Hello"

- Když přidáte `!` na konec filtru, zajistíte tím přesnější porovnávání rozlišovat velká a malá písmena:

     `el!` neodpovídá "Hello"

     `hello!` odpovídá "Hello"

- Přidání `*` na konec filtru zajistí, že se bude shodovat s předponou řetězce:

     `el*` neodpovídá "Hello"

     `he*` odpovídá "Hello"

- Více filtrů v seznamu odděleném středníkem je sloučeno jako disjunkce:

     `el;wo` odpovídá "Hello" a "World"

### <a name="stub-concrete-classes-and-virtual-methods"></a>Konkrétní třídy a virtuální metody se zástupnými procedurami

Ve výchozím nastavení jsou typy zástupných procedur generovány pro všechny nezapečetěné třídy. Je možné omezit typy zástupných procedur na abstraktní třídy prostřednictvím konfiguračního souboru *. napodobeniny* :

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

### <a name="internal-types"></a>Interní typy

Generátor falešného kódu generuje typy překrytí a typy zástupných procedur pro typy, které jsou viditelné pro vygenerované napodobeniny sestavení. Chcete-li zajistit, aby se interní typy překryté sestavení zobrazovaly jako falešné a vaše testovací sestavení, přidejte <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributy do kódu sestavení překryté, který poskytuje viditelnost vygenerovaného falešného sestavení a testovacího sestavení. Tady je příklad:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

**Interní typy v silně pojmenovaných sestaveních**

Pokud je sestavení překryté silně pojmenované a chcete získat přístup k interním typům sestavení:

- Sestavení testu i sestavení napodobeniny musí mít silný název.

- Přidejte veřejné klíče testu a napodobeniny sestavení do atributů **InternalsVisibleToAttribute** v sestaveních překryté. Zde je uvedeno, jak by ukázkové atributy v kódu sestavení překryté vypadaly, když je sestavení překryté silně pojmenované:

    ```csharp
    // FileSystem\AssemblyInfo.cs
    [assembly: InternalsVisibleTo("FileSystem.Fakes",
        PublicKey=<Fakes_assembly_public_key>)]
    [assembly: InternalsVisibleTo("FileSystem.Tests",
        PublicKey=<Test_assembly_public_key>)]
    ```

Pokud je sestavení překryté silně pojmenované, falešné rozhraní automaticky silně podepíše vygenerované napodobeniny sestavení. Musíte silně podepsat testovací sestavení. Viz [sestavení se silným názvem](/dotnet/framework/app-domains/strong-named-assemblies).

Rozhraní falešného rozhraní používá stejný klíč k podepsání všech generovaných sestavení, takže tento fragment lze použít jako výchozí bod pro přidání atributu **InternalsVisibleTo** pro falešné sestavení do vašeho kódu sestavení překryté.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

Můžete zadat jiný veřejný klíč pro sestavení falešného kódu, jako je klíč, který jste vytvořili pro sestavení překryté, zadáním úplné cesty k souboru *. snk* , který obsahuje alternativní klíč jako hodnotu atributu `KeyFile` v `Fakes` \\ @no__t_ 4 prvek souboru *. napodobeniny* . Příklad:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>
```

Pak je nutné použít veřejný klíč alternativního souboru *. snk* jako druhý parametr atributu InternalVisibleTo pro sestavení napodobeniny v překryté kódu sestavení:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

V příkladu výše mohou být hodnoty `Alternate_public_key` a `Test_assembly_public_key` stejné.

### <a name="optimize-build-times"></a>Optimalizace časů sestavení

Kompilace napodobenin sestavení může významně zvýšit čas sestavení. Čas sestavení lze minimalizovat generováním napodobenin sestavení pro sestavení systému .NET a sestavení třetích stran v samostatném centralizovaném projektu. Vzhledem k tomu, že se taková sestavení v počítači zřídka mění, můžete znovu použít vygenerovaná Napodobeninová sestavení v jiných projektech.

Z projektů testování částí přidejte odkaz na zkompilované napodobeniny sestavení, která jsou umístěna pod FakesAssemblies ve složce projektu.

1. Vytvořte novou knihovnu tříd s verzí modulu runtime .NET, která odpovídá vašim testovacím projektům. Pojďme to nazvat k napodobenině. Představte. Odeberte soubor *Class1.cs* z projektu, nepotřebujete.

2. Přidejte odkaz na všechna systémová a sestavení třetích stran, pro která budete potřebovat napodobeniny.

3. Přidejte soubor *. napodobeniny* pro každé sestavení a sestavení.

4. Z testovacího projektu

    - Ujistěte se, že máte odkaz na napodobeninu DLL modulu runtime:

         *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll*

    - Pro každé sestavení, pro které jste vytvořili napodobeniny, přidejte odkaz na odpovídající soubor DLL ve složce *napodobenins. Prebuild\FakesAssemblies* vašeho projektu.

### <a name="avoid-assembly-name-clashing"></a>Vyhnout se konfliktům názvů sestavení

V prostředí týmu sestavení jsou všechny výstupy sestavení sloučeny do jednoho adresáře. Pokud více projektů používá napodobeniny, může se stát, že napodobeniny sestavení z různých verzí jsou navzájem popsány. Například TestProject1 falešné knihovny *mscorlib. dll* z .NET Framework 2,0 a TestProject2 falešné knihovny *mscorlib. dll* pro .NET Framework 4 by měly vracet do *knihovny mscorlib. Napodobeniny. dll* předstírá sestavení.

Chcete-li se tomuto problému vyhnout, je nutné, aby při přidávání souborů s *příponou. napodobeniny* automaticky vytvářely názvy sestavení falešně kvalifikované verze pro neprojektové odkazy. Název sestavení napodobeniny kvalifikované verze vloží číslo verze při vytváření falešného názvu sestavení:

S ohledem na sestavení MyAssembly a verze 1.2.3.4 je název sestavení falešného formátu MyAssembly. 1.2.3.4. napodobeniny.

Tuto verzi můžete změnit nebo odebrat úpravou atributu verze elementu sestavení v *. napodobeniny*:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>
```

## <a name="fakes-naming-conventions"></a>Falešné konvence pojmenování

### <a name="shim-type-and-stub-type-naming-conventions"></a>Zásady pojmenování typu překrytí a zástupných procedur

**Obory názvů**

- . Do oboru názvů se přidá přípona falešného názvu.

   Například obor názvů `System.Fakes` obsahuje překrytí typů systémového oboru názvů.

- Globální. napodobeniny obsahuje typ překrytí prázdného oboru názvů.

  **Názvy typů**

- K názvu typu je přidána předpona Shim pro sestavení názvu typu překrytí.

   Například ShimExample je typ překrytí ukázkového typu.

- K názvu typu je přidána předpona se zástupným kódem pro sestavení názvu typu zástupné procedury.

   Například StubIExample je typ zástupné procedury typu IExample.

  **Argumenty typu a struktury vnořeného typu**

- Argumenty obecného typu se zkopírují.

- Vnořená struktura typu je zkopírována pro typy překrytí.

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a>Zásady pro pojmenovávání vlastností delegáta nebo pole delegáta zástupných procedur

**Základní pravidla** pro pojmenovávání polí od prázdného názvu:

- Název metody je připojen.

- Pokud je název metody explicitní implementací rozhraní, tečky se odeberou.

- Pokud je metoda obecná, `Of`*n* se připojí, kde *n* je počet argumentů obecných metod.

  **Speciální názvy metod** , jako je například getter nebo setter vlastnosti, jsou ošetřeny, jak je popsáno v následující tabulce:

|Pokud je metoda...|Příklad|Název metody se přidal.|
|-|-|-|
|**Konstruktor**|`.ctor`|`Constructor`|
|Statický **konstruktor**|`.cctor`|`StaticConstructor`|
|**Přistupující objekt** s názvem metody složený ze dvou částí oddělených znakem "_" (například getter vlastnosti)|*kind_name* (běžný případ, ale neuplatňuje ECMA)|*NameKind*, kde byly obě části velkými a prohozeny|
||Getter `Prop` vlastnosti|`PropGet`|
||Metoda setter `Prop` vlastností|`PropSet`|
||Přidávání událostí|`Add`|
||Sčítání události|`Remove`|
|**Operátor** složený ze dvou částí|`op_name`|`NameOp`|
|Například: + – operátor|`op_Add`|`AddOp`|
|Pro **operátor převodu**je připojen návratový typ.|`T op_Implicit`|`ImplicitOpT`|

> [!NOTE]
> - **Metody getter a setter indexerů** jsou zpracovány podobně jako vlastnost. Výchozí název indexeru je `Item`.
> - Názvy **typů parametrů** jsou transformované a zřetězené.
> - **Návratový typ** je ignorován, pokud neexistuje nejednoznačnost přetížení. Pokud dojde k přetížení amiguity, je návratový typ připojen na konci názvu.

### <a name="parameter-type-naming-conventions"></a>Zásady vytváření názvů typů parametrů

|Udělil|Připojený řetězec je...|
|-|-|
|**Typ** `T`|T<br /><br /> Dojde k zahození oboru názvů, vnořené struktury a obecného tiky.|
|**Výstupní parametr** `out T`|`TOut`|
|**Parametr ref** `ref T`|`TRef`|
|**Typ pole** `T[]`|`TArray`|
|Typ multidimenzionálního **pole** `T[ , , ]`|`T3`|
|Typ **ukazatele** `T*`|`TPtr`|
|@No__t_1 **obecného typu**|`TOfR1`|
|**Argument obecného typu** `!i` typu `C<TType>`|`Ti`|
|**Argument obecné metody** `!!i` metody `M<MMethod>`|`Mi`|
|@No__t_1 **vnořeného typu**|je připojen `N` a pak `T`|

### <a name="recursive-rules"></a>Rekurzivní pravidla

Následující pravidla se aplikují rekurzivně:

- Vzhledem k tomu, C# že napodobeniny používají ke generování falešných sestavení, jakýkoli znak, který C# by vytvořil neplatný token, je uvozen na "_" (podtržítko).

- Je-li výsledný název v konfliktu s jakýmkoli členem deklarovaného typu, je schéma číslování použito připojením počítadla se dvěma číslicemi počínaje od 01.

## <a name="see-also"></a>Viz také:

- [Izolace testovaného kódu s napodobeninami Microsoftu](../test/isolating-code-under-test-with-microsoft-fakes.md)
