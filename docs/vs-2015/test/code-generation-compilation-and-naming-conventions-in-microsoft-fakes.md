---
title: Vytváření, kompilace a konvence pojmenování ve Microsoft Fakes kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 20221de4-2a9e-4787-b99a-b5855bb90872
caps.latest.revision: 18
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1de284c8d4fdfe5cb84a474641b880590c2094aa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895317"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Vytváření, kompilace a konvence pojmenování kódu v Napodobeniny Microsoft
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje možnosti a problémy v generování kódu rozhraní Fakes a kompilace a popisuje konvence pro falešných generovaných typů, členů a parametrů.  
  
 **Požadavky**  
  
-   Visual Studio Enterprise  
  
##  <a name="BKMK_In_this_topic"></a> V tomto tématu  
 [Vytváření a kompilování kódu](#BKMK_Code_generation_and_compilation)  
  
- [Konfigurace generování provizorního kódu](#BKMK_Configuring_code_generation_of_stubs) • [filtrování typů](#BKMK_Type_filtering) • [vytváření provizorního kódu konkrétních tříd a virtuálních metodách](#BKMK_Stubbing_concrete_classes_and_virtual_methods) • [vnitřní typy](#BKMK_Internal_types) • [ Optimalizace doby sestavení](#BKMK_Optimizing_build_times) • [kolizi názvů sestavení](#BKMK_Avoiding_assembly_name_clashing)  
  
  [Konvence pojmenovávání napodobenin](#BKMK_Fakes_naming_conventions)  
  
- [Překrývajících a provizorních zadejte zásady vytváření názvů](#BKMK_Shim_type_and_stub_type_naming_conventions) • [překrytí delegáta vlastnost nebo zástupné procedury delegáta pole konvence pojmenování](#BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions) • [parametr typu zásady vytváření názvů](#BKMK_Parameter_type_naming_conventions) • [rekurzivní pravidla](#BKMK_Recursive_rules)  
  
  [Externí prostředky](#BKMK_External_resources)  
  
- [Pokyny](#BKMK_Guidance)  
  
##  <a name="BKMK_Code_generation_and_compilation"></a> Vytváření a kompilování kódu  
  
###  <a name="BKMK_Configuring_code_generation_of_stubs"></a> Konfigurace generování provizorního kódu  
 Generování provizorních typů je nakonfigurovaný v souboru XML, který má příponu souboru .fakes. Rámec falešného kódu integruje do procesu sestavení prostřednictvím úkolů MSBuild a tyto soubory detekuje během sestavení. Generátor falešného kódu kompiluje provizorní typy do sestavení a přidá odkaz na projekt.  
  
 Následující příklad ilustruje provizorní typy definované v knihovně FileSystem.dll:  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
    <Assembly Name="FileSystem"/>  
</Fakes>  
  
```  
  
###  <a name="BKMK_Type_filtering"></a> Filtrování podle typu  
 Filtry lze nastavit v souboru .fakes omezit typy, které by měla být prázdná. Můžete přidat množství vymazat, přidat a odebrat elementy v prvku StubGeneration pro sestavení seznamu vybraných typů.  
  
 Například tento soubor fakes generuje provizorní kód pro typy v oborech názvů System a System.IO, ale vynechá jakýkoli typ obsahující "Handle" v systému:  
  
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
  
-   Přidání `!` filtr na konec filtrovacího řetězce se přesná shoda malá a velká písmena:  
  
     `el!` neodpovídá "hello"  
  
     `hello!` odpovídá "hello"  
  
-   Přidání `*` na konec filtrovacího řetězce se provede porovnání předpony řetězce:  
  
     `el*` neodpovídá "hello"  
  
     `he*` odpovídá "hello"  
  
-   Několik filtrů ve středníkem oddělený seznam zkombinují je vyhodnoceno jako disjunkce:  
  
     `el;wo` odpovídá "hello" a "world"  
  
###  <a name="BKMK_Stubbing_concrete_classes_and_virtual_methods"></a> Vytváření provizorního kódu konkrétních tříd a virtuálních metod  
 Ve výchozím nastavení jsou zástupné typy generovány pro všechny nezapečetěné třídy. Je možné omezit typy zástupných procedur pro abstraktní třídy pomocí konfiguračního souboru .fakes:  
  
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
  
###  <a name="BKMK_Internal_types"></a> Vnitřní typy  
 Generátor falešného kódu bude generovat překrývající a provizorní typy, které jsou pro falešné sestavení viditelné. Chcete-li zviditelnit vnitřní typy překrytého sestavení pro falešné a testovací sestavení, přidejte <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributy do kódu překrytého sestavení, které dává viditelnost generovanému falešnému sestavení a testovacímu sestavení. Tady je příklad:  
  
```csharp  
// FileSystem\AssemblyInfo.cs  
[assembly: InternalsVisibleTo("FileSystem.Fakes")]  
[assembly: InternalsVisibleTo("FileSystem.Tests")]  
```  
  
 **Vnitřní typy v sestaveních se silným názvem**  
  
 Pokud je překryté sestavení pojmenováno silně a chcete, aby přístup k vnitřním typům sestavení:  
  
- Zkušební sestava i falešné sestavení musí mít silný název.  
  
- Je nutné přidat veřejné klíče testu a sestavení Fakes **InternalsVisibleToAttribute** atributy v překrytých sestaveních. Zde je, jak by vypadal náš příklad atributů v kódu překrytého sestavení, pokud je překryté sestavení pojmenováno silně:  
  
  ```csharp  
  // FileSystem\AssemblyInfo.cs  
  [assembly: InternalsVisibleTo("FileSystem.Fakes",  
      PublicKey=<Fakes_assembly_public_key>)]  
  [assembly: InternalsVisibleTo("FileSystem.Tests",  
      PublicKey=<Test_assembly_public_key>)]  
  ```  
  
  Pokud je překryté sestavení pojmenováno silně, rámec falešného kódu automaticky silně podepíše vygenerované falešné sestavení. Můžete nastavit silný podpis testovacího sestavení. Zobrazit [vytváření a používání sestavení se silným názvem](http://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).  
  
  Rámec falešného kódu používá stejný klíč k podepsání všech generovaných sestavení, takže tento fragment kódu můžete použít jako výchozí bod přidat **InternalsVisibleTo** atribut pro falešné sestavení pro váš překrytý kód sestavení.  
  
```csharp  
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]  
```  
  
 Můžete zadat jiný veřejný klíč pro sestavení Fakes, například klíč jste vytvořili pro překryté sestavení, zadáním úplné cesty k **.snk** soubor, který obsahuje alternativní klíč jako `KeyFile` hodnotu v atributu `Fakes` \\ `Compilation` elementu **.fakes** souboru. Příklad:  
  
```xml  
<-- FileSystem.Fakes.fakes -->  
<Fakes ...>  
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />  
</Fakes>  
  
```  
  
 Potom je nutné použít veřejný klíč náhradního **.snk** soubor jako druhý parametr atributu InternalVisibleTo pro sestavení Fakes v kódu překrytého sestavení:  
  
```csharp  
// FileSystem\AssemblyInfo.cs  
[assembly: InternalsVisibleTo("FileSystem.Fakes",  
    PublicKey=<Alternate_public_key>)]  
[assembly: InternalsVisibleTo("FileSystem.Tests",  
    PublicKey=<Test_assembly_public_key>)]  
```  
  
 V příkladu výše hodnoty `Alternate_public_key` a `Test_assembly_public_key` může být stejný.  
  
###  <a name="BKMK_Optimizing_build_times"></a> Optimalizace doby sestavení  
 Kompilace falešných sestavení může podstatně prodloužit dobu sestavení. Dobu sestavení lze minimalizovat generováním falešných sestavení pro systémová sestavení technologie .NET a sestavení třetích stran v odděleném centralizovaném projektu. Protože tato sestavení se jen zřídka mění na svém počítači, můžete využít tyto vygenerované napodobeniny sestavení v jiných projektech.  
  
 V projektech jednotkových testů můžete jednoduše provést odkaz na kompilovaná falešná sestavení, které jsou umístěny v podadresáři fakesassemblies adresáře ve složce projektu.  
  
1.  Vytvořte novou knihovnu tříd s verzí modulu runtime .NET odpovídající testovacímu projektu. Nazvěte ji třeba Fakes.Prebuild. Odstraňte soubor class1.cs z projektu, není potřeba.  
  
2.  Přidáte odkaz na všechna systémová sestavení a sestavení třetích stran, které potřebujete napodobeniny.  
  
3.  Pro každého z těchto sestavení přidejte soubor s příponou .fakes a sestavení.  
  
4.  Z testovacího projektu  
  
    -   Ujistěte se, že budete mít odkaz na napodobeninu knihovny runtime DLL:  
  
         C:\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll  
  
    -   Pro každé sestavení, že jste vytvořili falešné sestavení, přidejte odkaz na odpovídající soubor knihovny DLL ve složce fakes.prebuild\fakesassemblies k projektu.  
  
###  <a name="BKMK_Avoiding_assembly_name_clashing"></a> Kolizi názvů sestavení  
 V prostředí Team Build jsou všechna výstupní sestavení sloučena do jednoho adresáře. V případě více projektů používá falešné třídy může se stát, že napodobeniny sestavení z rozdílných verzí navzájem přepisují. Například projekt testproject1 vyžaduje napodobeninu knihovny mscorlib.dll rozhraní .NET Framework 2.0 a projekt testproject2 vyžaduje napodobeninu knihovny mscorlib.dll rozhraní .NET Framework 4 mscorlib.fakes.dll na mscorlib. Fakes.dll falešné sestavení.  
  
 K tomuto problému vyhnout, napodobeniny automaticky vytvořila verze kvalifikovaný pro reference mimo projekt názvy falešných sestavení při přidávání souborů .fakes. Verze kvalifikovaný název sestavení napodobenin vloží číslo verze, když vytváříte název sestavení napodobenin:  
  
 Název sestavení napodobenin zadaný pro sestavení MyAssembly a verzi 1.2.3.4 nazývat MyAssembly.1.2.3.4.Fakes.  
  
 Můžete změnit nebo odebrat tak, že upravíte atribut Version prvku Assembly v souboru .fakes:  
  
```xml  
attribute of the Assembly element in the .fakes:  
<Fakes ...>  
  <Assembly Name="MyAssembly" Version="1.2.3.4" />  
  ...  
</Fakes>  
  
```  
  
##  <a name="BKMK_Fakes_naming_conventions"></a> Konvence pojmenovávání napodobenin  
  
###  <a name="BKMK_Shim_type_and_stub_type_naming_conventions"></a> Překrývajících a provizorních zadejte zásady vytváření názvů  
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
  
###  <a name="BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions"></a> Vlastností překrývajícího delegáta se zakázaným inzerováním delegáta zásady vytváření názvů polí  
 **Základní pravidla** pro pojmenovávání polí, počínaje prázdným názvem:  
  
- Je připojen název metody.  
  
- Pokud je název metody explicitní implementací rozhraní, jsou odstraněny tečky.  
  
- Pokud metody je obecný, `Of` *n* připojen kde *n* je počet argumentů obecné metodě.  
  
  **Názvy speciálních metod** jako je například vlastnost getter nebo setter zacházeno podle popisu v následující tabulce.  
  
|Pokud je metoda...|Příklad|Připojený název metody|  
|-------------------|-------------|--------------------------|  
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
  
 **Poznámky**  
  
-   **Gettery a settery indexerů** je zacházeno podobně jako na vlastnost. Výchozí název indexeru je `Item`.  
  
-   **Typ parametru** názvy jsou transformovány a spojeny.  
  
-   **Návratový typ** se ignoruje, pokud existuje existovala dvojznačnost přetížení. Pokud je to tento případ, návratový typ je přidáván na konec názvu  
  
###  <a name="BKMK_Parameter_type_naming_conventions"></a> Konvence pojmenovávání parametrických typů  
  
|Zadaný|Připojený řetězec je...|  
|-----------|-------------------------|  
|A **typu**`T`|T<br /><br /> Obor názvů, vnořené struktury a obecné tiky jsou vynechány.|  
|**Výstupní parametr**`out T`|`TOut`|  
|A **parametr ref** `ref T`|`TRef`|  
|**Typ pole**`T[]`|`TArray`|  
|A **vícerozměrné pole** typu `T[ , , ]`|`T3`|  
|A **ukazatel** typu `T*`|`TPtr`|  
|A **obecného typu**`T<R1, …>`|`TOfR1`|  
|A **argument obecného typu** `!i` typu `C<TType>`|`Ti`|  
|A **argument obecné metody** `!!i` metody `M<MMethod>`|`Mi`|  
|A **vnořený typ**`N.T`|`N` je připojeno, pak `T`|  
  
###  <a name="BKMK_Recursive_rules"></a> Rekurzivní pravidla  
 Následující pravidla jsou aplikována rekurzivně:  
  
-   Jelikož napodobeniny používají C# ke generování sestavení Fakes, jakýkoli znak, který vyprodukuje neplatný token jazyka C# je převeden na "_" (podtržítko).  
  
-   Jestliže výsledný název koliduje se členem deklarovaného typu, se používá schéma číslování přidáním čítač dvěma číslicemi, začínající od 01.  
  
##  <a name="BKMK_External_resources"></a> Externí prostředky  
  
###  <a name="BKMK_Guidance"></a> Doprovodné materiály  
 [Testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 2: testování částí: testování uvnitř](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Viz také  
 [Izolace testovaného kódu pomocí zástupného rozhraní Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)



