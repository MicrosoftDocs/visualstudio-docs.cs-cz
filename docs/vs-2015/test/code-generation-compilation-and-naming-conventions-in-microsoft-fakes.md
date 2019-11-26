---
title: Vytváření, kompilace a konvence pojmenování kódu v Microsoft napodobeniny | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 20221de4-2a9e-4787-b99a-b5855bb90872
caps.latest.revision: 18
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ff1d953dc853beba8ef836b1eab03140ee0b1e0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300397"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Vytváření, kompilace a konvence pojmenování kódu v Napodobeniny Microsoft
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje možnosti a problémy v případě napodobeniny generování a kompilace kódu a popisuje konvence pojmenování pro falešné generované typy, členy a parametry.

 **Požadavky**

- Visual Studio Enterprise

## <a name="BKMK_In_this_topic"></a>V tomto tématu
 [Generování a kompilace kódu](#BKMK_Code_generation_and_compilation)

- [Konfigurace generování kódu pro](#BKMK_Configuring_code_generation_of_stubs) zástupné procedury • [filtrování typů](#BKMK_Type_filtering) • [podkládá konkrétní třídy a virtuální metody](#BKMK_Stubbing_concrete_classes_and_virtual_methods) • [interní typy • interní typy](#BKMK_Internal_types) • [optimalizace časů sestavení](#BKMK_Optimizing_build_times) • [zamezení konfliktu názvů sestavení](#BKMK_Avoiding_assembly_name_clashing)

  [Falešné konvence pojmenování](#BKMK_Fakes_naming_conventions)

- [Typ překrytí a zásady pojmenování typu se zástupnými](#BKMK_Shim_type_and_stub_type_naming_conventions) procedurami [•](#BKMK_Parameter_type_naming_conventions) [vlastnosti delegovaného delegáta nebo pojmenování polí delegáta se zástupnými](#BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions) procedurami [](#BKMK_Recursive_rules)

  [Externí prostředky](#BKMK_External_resources)

- [Pokyny](#BKMK_Guidance)

## <a name="BKMK_Code_generation_and_compilation"></a>Generování a kompilace kódu

### <a name="BKMK_Configuring_code_generation_of_stubs"></a>Konfigurace generování kódu pro zástupné procedury
 Generování zástupných typů je konfigurováno v souboru XML s příponou. falešné soubory. Rámec falešného kódu integruje do procesu sestavení prostřednictvím úkolů MSBuild a tyto soubory detekuje během sestavení. Generátor falešného kódu kompiluje provizorní typy do sestavení a přidá odkaz na projekt.

 Následující příklad znázorňuje typy zástupných procedur definované v souboru FileSystem. dll:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>

```

### <a name="BKMK_Type_filtering"></a>Filtrování typů
 Filtry lze nastavit v souboru. napodobeniny, aby bylo možné omezit, které typy by měly být podložit. Můžete přidat množství vymazat, přidat a odebrat elementy v prvku StubGeneration pro sestavení seznamu vybraných typů.

 Například tento soubor napodobeniny generuje zástupné procedury pro typy v rámci oborů názvů System a System.IO, ale vyloučí jakýkoli typ obsahující "Handle" v systému:

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

- Filtry jsou malá a velká písmena ve výchozím nastavení; filtry provádějí porovnání podřetězců:

     `el` odpovídá "Hello"

- Přidáním `!` na konec filtru se dá přesně rozlišovat velká a malá písmena:

     `el!` neodpovídá "Hello"

     `hello!` odpovídá "Hello"

- Přidání `*` na konec filtru bude odpovídat předponě řetězce:

     `el*` neodpovídá "Hello"

     `he*` odpovídá "Hello"

- Několik filtrů ve středníkem oddělený seznam zkombinují je vyhodnoceno jako disjunkce:

     `el;wo` odpovídá "Hello" a "World"

### <a name="BKMK_Stubbing_concrete_classes_and_virtual_methods"></a>Podkládá konkrétní třídy a virtuální metody
 Ve výchozím nastavení jsou zástupné typy generovány pro všechny nezapečetěné třídy. Je možné omezit typy zástupných procedur na abstraktní třídy prostřednictvím konfiguračního souboru. napodobeniny:

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

### <a name="BKMK_Internal_types"></a>Interní typy
 Generátor falešného kódu bude generovat typy překrytí a typy zástupných procedur pro typy, které jsou viditelné pro vygenerované napodobeniny sestavení. Chcete-li zajistit, aby se interní typy překryté sestavení zobrazovaly jako falešné a vaše testovací sestavení, přidejte <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributy do kódu sestavení překryté, který poskytuje viditelnost vygenerovaného falešného sestavení a testovacího sestavení. Tady je příklad:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

 **Interní typy v silně pojmenovaných sestaveních**

 Pokud je sestavení překryté silně pojmenované a chcete mít přístup k interním typům sestavení:

- Zkušební sestava i falešné sestavení musí mít silný název.

- Je nutné přidat veřejné klíče testu a falešné sestavení do atributů **InternalsVisibleToAttribute** v sestaveních překryté. Tady je postup, jak by naše příklady atributů v kódu sestavení překryté vypadaly, když je sestavení překryté silně pojmenované:

  ```csharp
  // FileSystem\AssemblyInfo.cs
  [assembly: InternalsVisibleTo("FileSystem.Fakes",
      PublicKey=<Fakes_assembly_public_key>)]
  [assembly: InternalsVisibleTo("FileSystem.Tests",
      PublicKey=<Test_assembly_public_key>)]
  ```

  Pokud je sestavení překryté silně pojmenované, rozhraní napodobeniny automaticky silně podepíše vygenerované napodobeniny sestavení. Můžete nastavit silný podpis testovacího sestavení. Viz [vytváření a používání sestavení se silným názvem](https://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).

  Rozhraní falešného rozhraní používá stejný klíč k podepsání všech generovaných sestavení, takže tento fragment lze použít jako výchozí bod pro přidání atributu **InternalsVisibleTo** pro falešné sestavení do vašeho kódu sestavení překryté.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

 Můžete zadat jiný veřejný klíč pro sestavení falešného kódu, jako je klíč, který jste vytvořili pro sestavení překryté, zadáním úplné cesty k souboru **. snk** , který obsahuje alternativní klíč jako hodnotu atributu `KeyFile` v `Fakes`\\`Compilation` prvku souboru **. napodobeniny** . Příklad:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>

```

 Pak je nutné použít veřejný klíč alternativního souboru **. snk** jako druhý parametr atributu InternalVisibleTo pro sestavení napodobeniny v překryté kódu sestavení:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

 V příkladu výše mohou být hodnoty `Alternate_public_key` a `Test_assembly_public_key` stejné.

### <a name="BKMK_Optimizing_build_times"></a>Optimalizace časů sestavení
 Kompilace falešných sestavení může podstatně prodloužit dobu sestavení. Dobu sestavení lze minimalizovat generováním falešných sestavení pro systémová sestavení technologie .NET a sestavení třetích stran v odděleném centralizovaném projektu. Protože tato sestavení se jen zřídka mění na svém počítači, můžete využít tyto vygenerované napodobeniny sestavení v jiných projektech.

 Z projektů testování částí můžete jednoduše přebírat odkaz na zkompilované napodobeniny sestavení, která jsou umístěna pod FakesAssemblies ve složce projektu.

1. Vytvořte novou knihovnu tříd s verzí modulu runtime .NET odpovídající testovacímu projektu. Pojďme to nazvat k napodobenině. Představte. Odeberte soubor class1.cs z projektu, nepotřebujete.

2. Přidáte odkaz na všechna systémová sestavení a sestavení třetích stran, které potřebujete napodobeniny.

3. Přidejte soubor. napodobeniny pro každé sestavení a sestavení.

4. Z testovacího projektu

    - Ujistěte se, že budete mít odkaz na napodobeninu knihovny runtime DLL:

         C:\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll

    - Pro každé sestavení, pro které jste vytvořili napodobeniny, přidejte odkaz na odpovídající soubor DLL ve složce Napodobenins. Prebuild\FakesAssemblies vašeho projektu.

### <a name="BKMK_Avoiding_assembly_name_clashing"></a>Zamezení konfliktu názvů sestavení
 V prostředí Team Build jsou všechna výstupní sestavení sloučena do jednoho adresáře. V případě více projektů, které používají napodobeniny, může dojít k tomu, že napodobeniny sestavení z jiné verze jsou vzájemně přepsány. Například TestProject1 falešné knihovny mscorlib. dll z .NET Framework 2,0 a TestProject2 falešné knihovny mscorlib. dll pro .NET Framework 4 by měly vracet do knihovny mscorlib. Napodobeniny. dll předstírá sestavení.

 Chcete-li se tomuto problému vyhnout, je nutné, aby při přidávání souborů s příponou. napodobeniny automaticky vytvářely názvy sestavení falešně kvalifikované verze pro neprojektové odkazy. Verze kvalifikovaný název sestavení napodobenin vloží číslo verze, když vytváříte název sestavení napodobenin:

 Název sestavení napodobenin zadaný pro sestavení MyAssembly a verzi 1.2.3.4 nazývat MyAssembly.1.2.3.4.Fakes.

 Tuto verzi můžete změnit nebo odebrat úpravou atributu verze elementu sestavení v. napodobeniny:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>

```

## <a name="BKMK_Fakes_naming_conventions"></a>Falešné konvence pojmenování

### <a name="BKMK_Shim_type_and_stub_type_naming_conventions"></a>Zásady pojmenování typu překrytí a zástupných procedur
 **Obory názvů**

- . Napodobeniny přípona se přidá do oboru názvů.

   Například obor názvů `System.Fakes` obsahuje překrytí typů systémového oboru názvů.

- Soubor Global.Fakes obsahuje překrývající typ prázdného oboru názvů.

  **Názvy typů**

- Je název typu k vytvoření názvu překrývajícího typu přidána předpona Shim.

   Například typ ShimExample je překrývající typ typu Example.

- Je název typu pro vytvoření názvu provizorního typu přidána předpona stub.

   Například typ StubIExample je provizorním typem typu IExample.

  **Argumenty typu a struktury vnořeného typu**

- Argumenty obecného typu jsou zkopírovány.

- Vnořené struktury typů zkopírovány pro typy překrytí.

### <a name="BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions"></a>Zásady pro pojmenovávání vlastností delegáta nebo pole delegáta zástupných procedur
 **Základní pravidla** pro pojmenovávání polí od prázdného názvu:

- Je připojen název metody.

- Pokud je název metody explicitní implementací rozhraní, jsou odstraněny tečky.

- Pokud je metoda obecná, `Of`*n* se připojí, kde *n* je počet argumentů obecných metod.

  **Speciální názvy metod** , jako je například getter nebo setter vlastnosti, jsou ošetřeny, jak je popsáno v následující tabulce.

|Pokud je metoda...|Příklad|Připojený název metody|
|-------------------|-------------|--------------------------|
|**Konstruktor**|`.ctor`|`Constructor`|
|Statický **konstruktor**|`.cctor`|`StaticConstructor`|
|**Přistupující objekt** s názvem metody složený ze dvou částí oddělených znakem "_" (například getter vlastnosti)|*kind_name* (běžný případ, ale neuplatňuje ECMA)|*NameKind*, kde byly obě části velkými a prohozeny|
||Getter `Prop` vlastnosti|`PropGet`|
||Metoda setter `Prop` vlastností|`PropSet`|
||Přidavač událostí|`Add`|
||Odstraňovač událostí|`Remove`|
|**Operátor** složený ze dvou částí|`op_name`|`NameOp`|
|Například: + – operátor|`op_Add`|`AddOp`|
|Pro **operátor převodu**je připojen návratový typ.|`T op_Implicit`|`ImplicitOpT`|

 **Poznámky**

- **Metody getter a setter indexerů** jsou zpracovány podobně jako vlastnost. Výchozí název indexeru je `Item`.

- Názvy **typů parametrů** jsou transformované a zřetězené.

- **Návratový typ** je ignorován, pokud neexistuje nejednoznačnost přetížení. V takovém případě se návratový typ připojí na konci názvu.

### <a name="BKMK_Parameter_type_naming_conventions"></a>Zásady vytváření názvů typů parametrů

|Zadaný|Připojený řetězec je...|
|-----------|-------------------------|
|**Typ**`T`|T<br /><br /> Obor názvů, vnořené struktury a obecné tiky jsou vynechány.|
|**Výstupní parametr**`out T`|`TOut`|
|**Parametr ref** `ref T`|`TRef`|
|**Typ pole**`T[]`|`TArray`|
|Typ multidimenzionálního **pole** `T[ , , ]`|`T3`|
|Typ **ukazatele** `T*`|`TPtr`|
|`T<R1, …>` **obecného typu**|`TOfR1`|
|**Argument obecného typu**`!i` typu `C<TType>`|`Ti`|
|**Argument obecné metody**`!!i` metody `M<MMethod>`|`Mi`|
|`N.T` **vnořeného typu**|je připojen `N` a pak `T`|

### <a name="BKMK_Recursive_rules"></a>Rekurzivní pravidla
 Následující pravidla jsou aplikována rekurzivně:

- Jelikož napodobeniny používají C# ke generování sestavení Fakes, jakýkoli znak, který vyprodukuje neplatný C# token je převeden na "_" (podtržítko).

- Jestliže výsledný název koliduje se členem deklarovaného typu, se používá schéma číslování přidáním čítač dvěma číslicemi, začínající od 01.

## <a name="BKMK_External_resources"></a>Externí prostředky

### <a name="BKMK_Guidance"></a>Směrné
 [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 2: testování částí: testování uvnitř](https://go.microsoft.com/fwlink/?LinkID=255188)

## <a name="see-also"></a>Viz také
 [Izolace testovaného kódu pomocí zástupného rozhraní Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)
