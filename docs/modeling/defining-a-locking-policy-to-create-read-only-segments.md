---
title: Definování zásady zamykání pro vytváření segmentů jen pro čtení
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0778df98ff5f9665da7220fe40972c9a8f8d8e1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536081"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definování zásady zamykání pro vytváření segmentů jen pro čtení
Rozhraní neměnnosti API sady Visual Studio pro vizualizaci a modelování umožňuje programu uzamknout část nebo celý model DSL (Domain-Specific Language), aby jej bylo možné číst, ale nikoli měnit. Tuto možnost lze použít například k tomu, aby uživatel mohl požádat o přístup k modelu DSL a zkontrolovat ho, aby se v něm změnil originál.

 Kromě toho můžete jako autora DSL definovat *zásady uzamykání.* Zásady zamykání definují, které zámky jsou povolené, nejsou povolené nebo povinné. Když například publikujete DSL, můžete vývojářům třetích stran vyzvat, aby ho rozšířili novými příkazy. Můžete ale také použít zásady uzamykání, které jim zabrání v změně stavu jen pro čtení určených částí modelu.

> [!NOTE]
> Zásady zamykání lze obejít pomocí reflexe. Poskytuje jasné hranice pro vývojáře třetích stran, ale neposkytuje silné zabezpečení.

 Další informace a ukázky jsou k dispozici na webu sady Visual Studio pro [vizualizaci a modelování sady SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) .

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>Nastavení a získání zámků
 Zámky můžete nastavit pro úložiště, na oddíl nebo na jednotlivé prvky. Například tento příkaz zabrání odstranění prvku modelu a zároveň zabrání změně jeho vlastností:

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 Další hodnoty zámku lze použít k zabránění změnám v relacích, vytváření prvků, pohybu mezi oddíly a k přeřazení odkazů v roli.

 Zámky platí pro akce uživatele i pro programový kód. Pokud se programový kód pokusí provést změnu, `InvalidOperationException` bude vyvolána výjimka. Zámky jsou ignorovány v operaci vrácení zpět nebo znovu.

 Můžete zjistit, zda má prvek libovolný zámek v dané sadě pomocí `IsLocked(Locks)` a můžete získat aktuální sadu zámků na elementu pomocí `GetLocks()` .

 Můžete nastavit zámek bez použití transakce. Databáze zámků není součástí úložiště. Pokud nastavíte zámek jako reakci na změnu hodnoty v úložišti, například v OnValueChanged, měli byste povolit změny, které jsou součástí operace vrácení zpět.

 Tyto metody jsou rozšiřující metody, které jsou definovány v <xref:Microsoft.VisualStudio.Modeling.Immutability> oboru názvů.

### <a name="locks-on-partitions-and-stores"></a>Zámky na oddílech a úložištích
 Zámky je také možné použít na oddíly a úložiště. Zámek, který je nastaven u oddílu, se vztahuje na všechny prvky v oddílu. Například následující příkaz zabrání odstranění všech prvků v oddílu bez ohledu na stavy jejich vlastních zámků. Nicméně jiné zámky, jako například, `Locks.Property` mohou být stále nastaveny na jednotlivé prvky:

```csharp
partition.SetLocks(Locks.Delete);
```

 Zámek, který je nastaven na Storu, se vztahuje na všechny jeho prvky bez ohledu na nastavení tohoto zámku oddílů a prvků.

### <a name="using-locks"></a>Použití zámků
 Můžete použít zámky k implementaci schémat, jako jsou následující příklady:

- Zakažte změny u všech elementů a vztahů s výjimkou těch, které reprezentují komentáře. To umožňuje uživatelům přidávat poznámky k modelu beze změny.

- Zakažte změny ve výchozím oddílu, ale Povolte změny v oddílu diagramu. Uživatel může změnit uspořádání diagramu, ale nemůže změnit příslušný model.

- Zakažte změny v úložišti s výjimkou skupiny uživatelů, kteří jsou zaregistrovaní v samostatné databázi. Pro ostatní uživatele je diagram a model určen jen pro čtení.

- Zakažte změny modelu, pokud je vlastnost Boolean diagramu nastavená na hodnotu true. Zadejte příkaz nabídky pro změnu této vlastnosti. To pomáhá zajistit, že uživatelé nedělají žádné změny omylem.

- Zakazuje přidávání a mazání prvků a vztahů konkrétních tříd, ale umožňuje změny vlastností. Tato možnost uživatelům poskytuje pevnou formu, ve které mohou vlastnosti vyplnit.

## <a name="lock-values"></a>Zamknout hodnoty
 Zámky je možné nastavit u úložiště, oddílu nebo jednotlivých ModelElement. Zámky jsou `Flags` výčtem: hodnoty lze kombinovat pomocí ' &#124; '.

- Zámky ModelElement vždy zahrnují zámky jejího oddílu.

- Zámky oddílu vždycky zahrnují zámky ze Storu.

  Nemůžete nastavit zámek na oddíl nebo úložiště a zároveň zakázat zámek u jednotlivého prvku.

|Hodnota|Význam, pokud `IsLocked(Value)` je true|
|-|-|
|Žádné|Bez omezení.|
|Vlastnost|Vlastnosti domény prvků nelze změnit. Toto neplatí pro vlastnosti, které jsou generovány rolí doménové třídy v relaci.|
|Přidat|V oddílu nebo v úložišti nelze vytvořit nové prvky a odkazy.<br /><br /> Neplatí pro `ModelElement` .|
|Přesunout|Element nelze přesunout mezi oddíly, pokud `element.IsLocked(Move)` má hodnotu true, nebo pokud `targetPartition.IsLocked(Move)` má hodnotu true.|
|Odstranit|Element nelze odstranit, je-li tento zámek nastaven na samotném prvku nebo na některé prvky, na které by se rozšířilo odstranění, jako jsou vložené prvky a tvary.<br /><br /> Můžete použít `element.CanDelete()` k zjištění, zda lze prvek odstranit.|
|Změnit pořadí|Řazení odkazů na RolePlayer se nedá změnit.|
|RolePlayer|Sadu odkazů, které jsou nasource v tomto prvku, nelze změnit. Například nové prvky nemohou být vloženy do tohoto elementu. To nemá vliv na odkazy, pro které je tento prvek cílem.<br /><br /> Pokud je tento prvek odkazem, nebude ovlivněn jeho zdroj a cíl.|
|Vše|Bitové nebo jiné hodnoty.|

## <a name="locking-policies"></a>Zásady uzamykání
 Jako autor DSL můžete definovat *zásady zamykání*. Zásady zamykání rozkládají operaci SetLocks (), aby bylo možné zabránit konkrétním zámkům v nastavení nebo pověření, aby bylo možné konkrétní zámky nastavit. Obvykle byste použili zásady uzamykání k tomu, aby uživatelům nebo vývojářům nechtěně contravening zamýšlené použití DSL, a to stejným způsobem, jakým můžete deklarovat proměnnou `private` .

 Můžete také použít zásady uzamykání k nastavení zámků pro všechny elementy závislé na typu elementu. Důvodem je, že `SetLocks(Locks.None)` je vždy volána při prvním vytvoření nebo deserializaci prvku ze souboru.

 Nemůžete však použít zásadu pro změnu zámků v prvku během své životnosti. Pro dosažení tohoto efektu byste měli použít volání na `SetLocks()` .

 Chcete-li definovat zásady zamykání, musíte:

- Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> .

- Přidejte tuto třídu ke službám, které jsou k dispozici prostřednictvím DocData vaší DSL.

### <a name="to-define-a-locking-policy"></a>Definování zásady zamykání
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> má následující definici:

```csharp
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Tyto metody jsou volány, když je provedeno volání do `SetLocks()` úložiště, oddílu nebo ModelElement. V každé metodě máte k dispozici navrhovanou sadu zámků. Navrhovanou sadu můžete vrátit nebo můžete přidat a odečíst zámky.

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

 Chcete-li zajistit, že uživatelé mohou vždy odstraňovat prvky, i když další volání kódu `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Chcete-li zakázat změnu ve všech vlastnostech každého elementu MyClass:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>Zpřístupnění zásad jako služby
 V `DslPackage` projektu přidejte nový soubor, který obsahuje kód, který se podobá následujícímu příkladu:

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
