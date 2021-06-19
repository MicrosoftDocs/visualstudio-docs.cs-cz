---
title: Definování zásady zamykání pro vytváření segmentů jen pro čtení
description: Zjistěte, jak můžete definovat zásady pro program, který bude uzamknout část nebo veškerý jazykový model specifický pro doménu (DSL), aby ho bylo možné číst, ale ne změnit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bb8e05ffc030716f32ab7e79233ca9e02ef2e11
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385783"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definování zásady zamykání pro vytváření segmentů jen pro čtení
Rozhraní API neměnnosti sady Visual Studio Visualization and Modeling SDK umožňuje programu uzamknout část nebo veškerý model jazyka specifického pro doménu (DSL), aby ho bylo možné číst, ale ne změnit. Tuto možnost jen pro čtení je možné použít například proto, aby uživatel mohl požádat kolegy o poznámky a zkontrolovat model DSL, ale mohl jim zakázat změnu původního modelu.

 Kromě toho můžete jako autor DSL definovat zásady *uzamykání.* Zásady uzamykání definují, které zámky jsou povolené, nejsou povolené nebo povinné. Například při publikování DSL můžete vyzvat vývojáře třetích stran, aby ho rozšířili o nové příkazy. Můžete ale také použít zásady uzamykání, abyste jim zabránili ve změně stavu jen pro čtení zadaných částí modelu.

> [!NOTE]
> Zásady uzamykání je možné obejít pomocí reflexe. Poskytuje jasnou hranici pro vývojáře třetích stran, ale neposkytuje silné zabezpečení.

 Další informace a ukázky jsou k dispozici na Visual Studio [Visualization and Modeling SDK.](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>Nastavení a získání zámků
 Zámky můžete nastavit pro úložiště, na oddíl nebo na jednotlivém prvku. Tento příkaz například zabrání odstranění prvku modelu a také zabrání změně jeho vlastností:

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 Jiné hodnoty zámku lze použít k tomu, abyste zabránili změnám v relacích, vytváření elementů, přesunu mezi oddíly a změně pořadí odkazů v roli.

 Zámky platí jak pro akce uživatele, tak pro programový kód. Pokud se programový kód pokusí provést změnu, `InvalidOperationException` vyvolá se . Zámky se v operaci Zpět nebo Znovu ignorují.

 Pomocí příkazu můžete zjistit, zda má prvek nějaký zámek v dané sadě, a aktuální sadu zámků u `IsLocked(Locks)` elementu můžete získat pomocí `GetLocks()` .

 Zámek můžete nastavit bez použití transakce. Zamykací databáze není součástí úložiště. Pokud nastavíte zámek v reakci na změnu hodnoty v obchodě, například v OnValueChanged, měli byste povolit změny, které jsou součástí operace Zpět.

 Tyto metody jsou rozšiřující metody, které jsou definovány v oboru <xref:Microsoft.VisualStudio.Modeling.Immutability> názvů .

### <a name="locks-on-partitions-and-stores"></a>Zámky na oddílech a obchodech
 Zámky lze použít také pro oddíly a úložiště. Zámek, který je nastavený u oddílu, se vztahuje na všechny prvky v oddílu. Proto například následující příkaz zabrání odstranění všech prvků v oddílu bez ohledu na stav jejich vlastních zámků. U jednotlivých prvků je ale možné nastavit i další `Locks.Property` zámky, například :

```csharp
partition.SetLocks(Locks.Delete);
```

 Zámek, který je nastavený pro Store, platí pro všechny jeho prvky bez ohledu na nastavení tohoto zámku na oddílech a prvcích.

### <a name="using-locks"></a>Použití zámků
 Zámky můžete použít k implementaci schémat, jako jsou následující příklady:

- Zakážete změny všech prvků a relací s výjimkou těch, které představují komentáře. To umožňuje uživatelům anotovat model beze změny.

- Nepovolte změny ve výchozím oddílu, ale povolte změny v oddílu diagramu. Uživatel může změnit uspořádání diagramu, ale nemůže změnit základní model.

- Zakázat změny ve Storu s výjimkou skupiny uživatelů, kteří jsou zaregistrovaní v samostatné databázi. Pro ostatní uživatele je diagram a model jen pro čtení.

- Zakázat změny modelu, pokud je logická vlastnost diagramu nastavená na hodnotu true. Zadejte příkaz nabídky pro změnu této vlastnosti. To pomáhá zajistit, aby uživatelé neúmyslně nedělděli změny.

- Nepovoluje přidávání a odstraňování prvků a vztahů konkrétních tříd, ale umožňuje změny vlastností. Uživatelé tak mají pevný formulář, ve kterém mohou vyplnit vlastnosti.

## <a name="lock-values"></a>Hodnoty zámku
 Zámky lze nastavit pro Store, Partition nebo jednotlivě ModelElement. Zámky jsou `Flags` výčet: Její hodnoty můžete kombinovat pomocí &#124;.

- Zámky Elementu ModelElement vždy obsahují zámky jeho oddílu.

- Zámky oddílu vždy obsahují zámky úložiště.

  Zámek nelze nastavit pro oddíl nebo úložiště a současně zakázat zámek u jednotlivých prvků.

|Hodnota|To znamená, že `IsLocked(Value)` pokud je true|
|-|-|
|Žádná|Bez omezení.|
|Vlastnost|Vlastnosti domény prvků nelze změnit. To neplatí pro vlastnosti, které jsou generovány rolí třídy domény v relaci.|
|Přidání|Nové elementy a propojení nelze vytvořit v oddílu ani v obchodě.<br /><br /> Nelze použít pro `ModelElement` .|
|Přesunout|Element nelze přesunout mezi oddíly, pokud `element.IsLocked(Move)` je true, nebo pokud `targetPartition.IsLocked(Move)` je true.|
|Odstranit|Prvek nelze odstranit, pokud je tento zámek nastaven na samotný prvek nebo u žádného z prvků, na které by se odstranění rozšíří, například vložené prvky a tvary.<br /><br /> Můžete použít `element.CanDelete()` ke zjištění, zda lze odstranit prvek.|
|Přiobjednání|Řazení odkazů v roleplayeru není možné změnit.|
|RolePlayer|Sadu odkazů, které jsou zdrojem v tomto elementu, nelze změnit. Například nové prvky nelze vložit pod tento prvek. To nemá vliv na odkazy, pro které je tento prvek cílem.<br /><br /> Pokud je tento prvek odkaz, jeho zdroj a cíl nejsou ovlivněny.|
|Vše|Bitový operátor OR ostatních hodnot.|

## <a name="locking-policies"></a>Uzamykání zásad
 Jako autor DSL můžete definovat zásady *uzamykání*. Zásady uzamykání moderuje operaci SetLocks(), abyste mohli zabránit nastavení konkrétních zámků nebo nastavit konkrétní zámky. Obvykle byste pomocí zásady uzamykání odrazovali uživatele nebo vývojáře od náhodného předchytání zamýšleného použití DSL stejným způsobem, jakým deklarujete proměnnou `private` .

 Zásady uzamykání můžete použít také k nastavení zámků na všech prvcích závislých na typu elementu. Je to proto, že je vždy volána při prvním vytvoření nebo `SetLocks(Locks.None)` deserializaci elementu ze souboru.

 Zásady ale nemůžete použít k odlišování zámků u elementu během jeho životnosti. K dosažení tohoto efektu byste měli použít volání `SetLocks()` metody .

 Pokud chcete definovat zásady uzamykání, musíte:

- Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> .

- Přidejte tuto třídu do služeb, které jsou k dispozici prostřednictvím DocData vašeho DSL.

### <a name="to-define-a-locking-policy"></a>Definování zásady uzamykání
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> má následující definici:

```csharp
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Tyto metody jsou volány při volání metody `SetLocks()` pro Store, Partition nebo ModelElement. V každé metodě máte navrhovanou sadu zámků. Navrhovanou sadu můžete vrátit nebo můžete přidat a odečíst zámky.

 Příklad:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  public class MyLockingPolicy : ILockingPolicy
  {
    /// <summary>
    /// Moderate SetLocks(this ModelElement target, Locks locks)
    /// </summary>
    /// <param name="element">target</param>
    /// <param name="proposedLocks">locks</param>
    /// <returns></returns>
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)
    {
      // In my policy, users can never delete an element,
      // and other developers cannot easily change that:
      return proposedLocks | Locks.Delete);
    }
    public Locks RefineLocks(Store store, Locks proposedLocks)
    {
      // Only one user can change this model:
      return Environment.UserName == "aUser"
           ? proposedLocks : Locks.All;
    }
```

 Zajistit, aby uživatelé mohli vždy odstranit elementy, i když volá jiný kód `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Zakázání změny ve všech vlastnostech každého prvku třídy MyClass:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>Nastavení zásad jako služby
 Do projektu `DslPackage` přidejte nový soubor, který obsahuje kód podobný následujícímu příkladu:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  // Override the DocData GetService() for this DSL.
  internal partial class YourDslDocData // Change
  {
    /// <summary>
    /// Custom locking policy cache.
    /// </summary>
    private ILockingPolicy myLockingPolicy = null;

    /// <summary>
    /// Called when a service is requested.
    /// </summary>
    /// <param name="serviceType">Service requested</param>
    /// <returns>Service implementation</returns>
    public override object GetService(System.Type serviceType)
    {
      if (serviceType == typeof(SLockingPolicy)
       || serviceType == typeof(ILockingPolicy))
      {
        if (myLockingPolicy == null)
        {
          myLockingPolicy = new MyLockingPolicy();
        }
        return myLockingPolicy;
      }
      // Request is for some other service.
      return base.GetService(serviceType);
    }
}
```
