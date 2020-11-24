---
title: 'Napodobeniny Microsoftu: generovat & kód kompilace; zásady vytváření názvů'
description: Seznamte se s možnostmi a problémy v případě napodobenin generování a kompilace kódu, včetně zásad vytváření názvů pro falešné generované typy, členy a parametry.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e3ebb1439c7b8eb958d8e7126ca0197462e89a09
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441630"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Vytváření, kompilace a konvence pojmenování kódu v Napodobeniny Microsoft

Tento článek popisuje možnosti a problémy v případě napodobeniny generování a kompilace kódu a popisuje konvence pojmenování pro falešné generované typy, členy a parametry.

**Požadavky**

- Visual Studio Enterprise
- .NET Framework projekt
::: moniker range=">=vs-2019"
- V sadě Visual Studio 2019 Update 6 je podpora projektu .NET Core a sady SDK předem zobrazená a v Update 8 je ve výchozím nastavení povolená. Další informace najdete v tématu [Microsoft předstírá pro projekty ve stylu .NET Core a SDK](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects).
::: moniker-end

## <a name="code-generation-and-compilation"></a>Generování a kompilace kódu

### <a name="configure-code-generation-of-stubs"></a>Konfigurace generování kódu pro zástupné procedury

Generování zástupných typů je konfigurováno v souboru XML s příponou *. falešné* soubory. Rozhraní falešného rozhraní je integrováno do procesu sestavení prostřednictvím vlastních úloh nástroje MSBuild a detekuje tyto soubory v čase sestavení. Generátor falešného kódu zkompiluje typy zástupných procedur do sestavení a přidá odkaz na projekt.

Následující příklad znázorňuje typy zástupných procedur definované v *FileSystem.dll*:

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

- Přidáním `!` na konec filtru se dá přesně rozlišovat velká a malá písmena:

     `el!` neodpovídá "Hello"

     `hello!` odpovídá "Hello"

- Přidáním `*` na konec filtru se bude shodovat předpona řetězce:

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

Generátor falešného kódu generuje typy překrytí a typy zástupných procedur pro typy, které jsou viditelné pro vygenerované napodobeniny sestavení. Chcete-li zpřístupnit interní typy překryté sestavení falešným a testovacím sestavením, přidejte  <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributy do kódu sestavení překryté, který poskytuje viditelnost vygenerovaného falešného sestavení a testovacího sestavení. Tady je příklad:

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

Můžete zadat jiný veřejný klíč pro sestavení falešného kódu, jako je klíč, který jste vytvořili pro sestavení překryté, zadáním úplné cesty k souboru *. snk* , který obsahuje alternativní klíč jako `KeyFile` hodnotu atributu v `Fakes` \\ `Compilation` prvku souboru *. napodobeniny* . Například:

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

V předchozím příkladu `Alternate_public_key` `Test_assembly_public_key` můžou být hodnoty a.

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

V prostředí týmu sestavení jsou všechny výstupy sestavení sloučeny do jednoho adresáře. Pokud více projektů používá napodobeniny, může se stát, že napodobeniny sestavení z různých verzí jsou navzájem popsány. Například TestProject1 napodobeniny *mscorlib.dll* z .NET Framework 2,0 a TestProject2 napodobeniny *mscorlib.dll* pro .NET Framework 4 by to znamenalo *mscorlib.Fakes.dll* napodobeniny sestavení.

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

**Jmenné prostory**

- . Do oboru názvů se přidá přípona falešného názvu.

   Například `System.Fakes` obor názvů obsahuje typy překrytí pro obor názvů System.

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

- Pokud je metoda obecná, `Of` *n* je připojen, kde *n* je počet argumentů obecných metod.

  **Speciální názvy metod** , jako je například getter nebo setter vlastnosti, jsou ošetřeny, jak je popsáno v následující tabulce:

|Pokud je metoda...|Příklad|Název metody se přidal.|
|-|-|-|
|**Konstruktor**|`.ctor`|`Constructor`|
|Statický **konstruktor**|`.cctor`|`StaticConstructor`|
|**Přistupující objekt** s názvem metody složený ze dvou částí oddělených znakem "_" (například getter vlastnosti)|*kind_name* (běžný případ, ale neuplatňuje ECMA)|*NameKind*, kde byly obě části velkými a prohozeny|
||Getter vlastnost `Prop`|`PropGet`|
||Metoda setter vlastnosti `Prop`|`PropSet`|
||Přidávání událostí|`Add`|
||Sčítání události|`Remove`|
|**Operátor** složený ze dvou částí|`op_name`|`NameOp`|
|Například: + – operátor|`op_Add`|`AddOp`|
|Pro **operátor převodu** je připojen návratový typ.|`T op_Implicit`|`ImplicitOpT`|

> [!NOTE]
> - **Metody getter a setter indexerů** jsou zpracovány podobně jako vlastnost. Výchozím názvem indexeru je `Item` .
> - Názvy **typů parametrů** jsou transformované a zřetězené.
> - **Návratový typ** je ignorován, pokud neexistuje nejednoznačnost přetížení. Pokud dojde k přetížení amiguity, je návratový typ připojen na konci názvu.

### <a name="parameter-type-naming-conventions"></a>Zásady vytváření názvů typů parametrů

|Udělil|Připojený řetězec je...|
|-|-|
|**Typ**`T`|T<br /><br /> Dojde k zahození oboru názvů, vnořené struktury a obecného tiky.|
|**Výstupní parametr**`out T`|`TOut`|
|**Parametr ref**`ref T`|`TRef`|
|**Typ pole**`T[]`|`TArray`|
|**Multidimenzionální typ pole**`T[ , , ]`|`T3`|
|Typ **ukazatele**`T*`|`TPtr`|
|**Obecný typ**`T<R1, ...>`|`TOfR1`|
|**Argument obecného typu** `!i` typu`C<TType>`|`Ti`|
|**Argument obecné metody** `!!i` metody`M<MMethod>`|`Mi`|
|**Vnořený typ**`N.T`|`N` je připojeno, pak `T`|

### <a name="recursive-rules"></a>Rekurzivní pravidla

Následující pravidla se aplikují rekurzivně:

- Vzhledem k tomu, že napodobeniny používají jazyk C# ke generování falešných sestavení, jakýkoli znak, který by vytvořil neplatný token jazyka C#, je uvozen na "_" (podtržítko).

- Je-li výsledný název v konfliktu s jakýmkoli členem deklarovaného typu, je schéma číslování použito připojením počítadla se dvěma číslicemi počínaje od 01.

## <a name="see-also"></a>Viz také

- [Izolace testovaného kódu s napodobeninami Microsoftu](../test/isolating-code-under-test-with-microsoft-fakes.md)
