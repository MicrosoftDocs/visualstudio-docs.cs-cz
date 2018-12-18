---
title: Definování zásady zamykání pro vytváření segmentů jen pro čtení
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7f2a22a39b30d6a1910a95d5c30992bbd14dbc9a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828673"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definování zásady zamykání pro vytváření segmentů jen pro čtení
Rozhraní API neměnnosti sady Visual Studio Visualization and Modeling SDK umožňuje aplikaci uzamknout část nebo celý model jazyka specifického pro doménu (DSL), aby ji lze číst, ale nebyl změněn. Tato možnost jen pro čtení může použít, třeba tak, aby uživatel požádat o vaši kolegové mohli opatřit poznámkami a zkontrolujte modelu DSL, ale můžete zakázat možnost měnit původní.

 Kromě toho, jak vytvořit DSL, můžete definovat *uzamčení zásad.* Zásady zamykání definuje zámky, které jsou povolené, nejsou povolené nebo povinné. Například při publikování DSL je vstupní kontroly mohou pobídnout vývojářům třetích stran ho rozšířit pomocí nových příkazů. Ale můžete také použít zásady zamykání a zabrání tak jejich změnu stavu jen pro čtení zadaného součásti modelu.

> [!NOTE]
>  Zásady zamykání může být požadavky propojení obcházeny pomocí operace reflection. Poskytuje jasný hranice pro vývojáře třetích stran, ale neposkytuje silné zabezpečení.

 Další informace a ukázky jsou k dispozici v sadě Visual Studio [Visualization and Modeling SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) webu.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>Nastavení a získání uzamčení
 Zámky můžete nastavit v úložišti, v oddílu nebo na jednotlivý prvek. Tento příkaz například zabránit odstranění prvku modelu a zároveň zabrání jeho vlastnosti mění:

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 Ostatní hodnoty zámek je možné zabránit změnám v relace, vytváření elementu Automat, pohyb mezi oddíly a znovu pořadí odkazy v roli.

 Zámky použít s uživatelskými akcemi a programového kódu. Pokud se pokusí provést změnu, kód programu `InvalidOperationException` bude vyvolána výjimka. Uzamčení se ignorují v operaci vrácení zpět nebo znovu.

 Můžete zjistit, zda má element žádný zámek v dané sadě s použitím `IsLocked(Locks)` a aktuální sadu zámky v elementu lze získat pomocí `GetLocks()`.

 Můžete nastavit zámek bez použití transakcí. Zámek databáze není součástí úložiště. Pokud nastavíte zámku v reakci na změnu hodnoty v úložišti, třeba v OnValueChanged, byste měli povolit změny, které jsou součástí operace vrácení zpět.

 Tyto metody jsou metody rozšíření, které jsou definovány v <xref:Microsoft.VisualStudio.Modeling.Immutability> oboru názvů.

### <a name="locks-on-partitions-and-stores"></a>Zámky na oddíly a úložišť
 Zámky lze také použít na oddíly a úložišti. Zámek, který je nastaven na oddíl se vztahuje na všechny prvky v oddílu. Proto se například následující příkaz zabrání všechny prvky v oddílu odstraňuje, bez ohledu na stavy jejich vlastní zámky. Nicméně, druhý uzamkne, jako `Locks.Property` stále může být nastavena na jednotlivé prvky:

```csharp
partition.SetLocks(Locks.Delete);
```

 Zámek, který je nastaven na Store se vztahuje na všechny prvky, bez ohledu na nastavení tohoto Uzamknout na oddíly a prvky.

### <a name="using-locks"></a>Použití zámků
 Zámky můžete použít k implementaci systémů, jako jsou následující příklady:

-   Zakáže změny na všechny prvky a vztahy s výjimkou těch, které představují komentáře. To umožňuje uživatelům umožňuje anotaci modelu bez provedení změn.

-   Zakáže změny v oddílu výchozí, ale povolit změny v oddílu diagramu. Uživatel může změnit uspořádání diagramu, ale základní model nelze změnit.

-   Zakáže změny Store s výjimkou skupinu uživatelů, kteří jsou registrovány v samostatné databáze. Pro ostatní uživatele jsou v diagramu a modelu jen pro čtení.

-   Zakáže změny modelu, pokud vlastnost typu Boolean diagramu je nastavena na hodnotu true. Zadejte příkaz, který tuto vlastnost změnit. Díky tomu uživatelé, kteří jsou Nedovolte, aby byly změny omylem.

-   Zakažte přidání a odstranění prvků a vztahů určité třídy, ale umožňují změny vlastností. To uživatelům poskytuje pevné formuláře, ve které probírají vlastnosti.

## <a name="lock-values"></a>Zámku hodnoty
 Zámky lze nastavit na Store, oddílu nebo jednotlivé ModelElement. Je na zámků `Flags` výčet: zkombinováním hodnot pomocí "&#124;".

- Zámky ModelElement vždy zahrnovat zámky jeho oddílu.

- Zámky oddílu vždy zahrnovat zámky Store.

  Nelze nastavit zámek na oddíl nebo úložiště a současně zakázat zámek na jednotlivý element.

|Hodnota|To znamená pokud `IsLocked(Value)` má hodnotu true|
|-|-|
|Žádné|Bez omezení.|
|Vlastnost|Vlastnosti domény prvků nelze změnit. To se nevztahuje na vlastnosti, které jsou generovány podle role doménové třídy v relaci.|
|Přidejte|Nelze vytvořit nové prvky a odkazy v oddílu nebo úložiště.<br /><br /> Nevztahuje se na `ModelElement`.|
|Přesunutí|Element nelze přesouvat mezi oddíly, pokud `element.IsLocked(Move)` má hodnotu true, nebo pokud `targetPartition.IsLocked(Move)` má hodnotu true.|
|Odstranit|Element nelze odstranit, pokud je nastavení tohoto uzamknout elementu samotného nebo na některý z prvků, do které by odstranění rozšíření, jako je například vložené prvky a tvary.<br /><br /> Můžete použít `element.CanDelete()` ke zjištění, zda elementu je možné odstranit.|
|Změna pořadí|Řazení odkazy na roleplayer nelze změnit.|
|Aktér role pro doménovou|Sada odkazů, které jsou zdrojem na tento element nejde změnit. Například nové prvky nemůže být vložený, v rámci tohoto elementu. Odkazy, pro které tento element je cílem to nemá vliv.<br /><br /> Pokud tento prvek je odkaz, nejsou ovlivněny její zdroj a cíl.|
|Všechny|Bitový operátor OR ostatní hodnoty.|

## <a name="locking-policies"></a>Zásady uzamčení
 Jako autoři DSL, můžete definovat *uzamčení zásad*. Zásady zamykání moderates operace SetLocks(), takže je může zakázat konkrétní zámky nastavit nebo stanoví, že konkrétní zámků musí být nastavena. Obvykle použijete zásady zamykání na bránit uživatelům nebo vývojářům ze omylem orgán je zamýšlené použití souboru DSL, stejným způsobem, že můžete deklarovat proměnnou `private`.

 Také vám pomůže zásady zamykání nastavit zámky u všech elementů závisí na typu elementu. Důvodem je, že `SetLocks(Locks.None)` je volána vždy, když se element nejprve vytvoří nebo deserializovat ze souboru.

 Nelze však pomocí zásad se liší v průběhu své životnosti zámky u elementu. K dosažení tohoto efektu, byste měli použít volání `SetLocks()`.

 K definování zásady zamykání, budete muset:

-   Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.

-   Přidejte tuto třídu do služby, které jsou k dispozici prostřednictvím DocData tohoto kódu DSL.

### <a name="to-define-a-locking-policy"></a>K definování zásady zamykání
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> obsahuje následující definice:

```csharp
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Tyto metody jsou volány při je provedeno volání `SetLocks()` na Store, oddílu nebo ModelElement. V každé metodě jsou součástí navrhovaných sadu zámky. Může vrátit sadu navrhované nebo můžete sčítání a odečítání zámky.

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

 Abyste měli jistotu, že uživatelé mohou vždy odstranit prvky, i v případě, že volání jiného kódu `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Chcete zakázat změnu v hodnotě vlastnosti každý prvek MyClass:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>Aby vaše zásady dostupný jako služba
 Ve vaší `DslPackage` projektu, přidejte nový soubor, který obsahuje kód, který se podobá následujícímu příkladu:

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
